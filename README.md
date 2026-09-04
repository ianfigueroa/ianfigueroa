# Ian Figueroa

Software engineering student at UPRM (B.S. expected 2030) building low-latency market-data systems and reproducible quant / ML research. Every number below reproduces from a clean clone of the linked repo.

---

## Projects

### [Titan](https://github.com/ianfigueroa/Titan) - low-latency market-data engine
C++20 service that ingests Binance Futures depth/trade streams, keeps a live order book with sequence-gap detection and REST snapshot resync, and broadcasts VWAP, trade-flow, and whale alerts over WebSocket. Lock-free SPSC queue between network and engine threads (~220M events/s, ~4.5 ns handoff, `benchmarks/bench_spsc_throughput.cpp`); 140 GoogleTest cases.
`C++20` `Boost.Beast` `Lock-free` `WebSockets` `CMake`

### [TapeFlow](https://github.com/ianfigueroa/TapeFlow) - real-time trading terminal
Dual-mode terminal that switches between live Binance data and a local C++ simulation engine behind one TypeScript adapter. Price-time-priority limit order book (over 2M mixed orders/s, ~4M/s add-only, `cpp-engine/benchmarks/bench_orderbook.cpp`), a from-scratch RFC 6455 WebSocket server, paper trading with 7 risk controls, and a 4-type anomaly detector.
`C++20` `TypeScript` `React` `WebSockets`

### [options-risk-engine](https://github.com/ianfigueroa/options-risk-engine) - options analytics platform
C++20 pricing/risk core (10K Black-Scholes prices in ~1.4 ms single-threaded) exposed through pybind11, a 15-endpoint FastAPI service, and a React dashboard. Black-Scholes, binomial, and Monte-Carlo pricers cross-checked to converge (binomial within 0.075% of closed form over 110 contracts, registered as a CTest), full Greeks, implied vol, vol surfaces, portfolio aggregation, delta hedging with transaction costs.
`C++20` `Python` `pybind11` `FastAPI` `React`

### [FinLLM](https://github.com/ianfigueroa/FinLLM) - RAG over SEC filings with an eval harness
Local-first retrieval-augmented QA over 10-Ks: hybrid dense + BM25 retrieval, section-aware reranking, citation validation, three-statement parsing. The eval harness (34 labeled questions over 4 real 10-Ks, ~3K chunks) holds 100% citation validity and caught a reranking change that lowered numeric-fact hit@5 from 0.62 to 0.47 before it shipped.
`Python` `RAG` `BM25` `Evals`

### [DeepLOB-Research](https://github.com/ianfigueroa/DeepLOB-Research) - cost-aware LOB forecasting harness
Eight model classes (logistic, XGBoost, MLP, DeepLOB, TCN, Transformer-LOB, TLOB, S4D) in PyTorch, scored under purged walk-forward and combinatorial purged CV with an event-driven backtest (fees, slippage, latency, deflated Sharpe, adversarial validation). Result: none of 24 model/dataset runs kept positive net PnL after 1 bp fees. 130 tests.
`Python` `PyTorch` `XGBoost` `Quant research`

### [reasoning-model](https://github.com/ianfigueroa/reasoning-model) - test-time compute on a 1.5B LLM
QLoRA SFT of Qwen2.5-1.5B on s1K reasoning traces on one 8 GB GPU, plus budget forcing, self-consistency, and tool-integrated reasoning at inference. Found and fixed an eval-harness bug that understated the GSM8K baseline by 40 points; the ablation shows the s1 effect does not reproduce at 1.5B, and 87% GSM8K comes from the right base model and prompt.
`Python` `PyTorch` `PEFT` `Evals`

### [Arb-Scanner](https://github.com/ianfigueroa/Arb-Scanner) - multi-chain DEX arbitrage scanner
Async Rust scanner over 20+ pools on Ethereum, Arbitrum, Base, and Polygon: 3-hop paths every block with exact Uniswap V2 math, a marginal-price V3 approximation, on-chain Curve quotes, gas-aware ROI, SQLite crash recovery, and backoff reconnects. 90 tests.
`Rust` `Tokio` `SQLite` `DeFi`

---

<p>
  <a href="https://linkedin.com/in/ian-figueroa1">LinkedIn</a> ·
  <a href="mailto:ian.figueroa6@upr.edu">ian.figueroa6@upr.edu</a>
</p>
