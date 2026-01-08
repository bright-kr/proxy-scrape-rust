[![Promo](https://brightdata.co.kr/static/github_promo_15.png?md5=105367-daeb786e)](https://brightdata.co.kr/?promo=github15) 

# proxy-scrape-rust
プロキシ 서버를 통한 Webスクレイピング 사용을 시연하는 기본 API Rust 프로그램입니다

이 프로젝트는 [Web Scraping in Rust](https://brightdata.co.kr/blog/how-tos/web-scraping-with-rust)에서 プロキシ 서버를 설정하는 방법을 시연합니다. プロキシ는 Webスクレイピング 중에 해당 IPアドレス를 사용하여 디지털 신원을 보호하고, IP 차단 및 지리적 차단(geoblocking)을 우회합니다.

이 리포지토리는 [Rust Proxy Servers](https://brightdata.co.kr/blog/how-tos/rust-proxy-servers) 문서를 기반으로 실행할 수 있는 다양한 프로그램을 포함합니다:
- basic: 데이터 가져오기 및 파싱의 기본 사용법을 보여줍니다
- basic_proxy: 기본 プロキシ를 사용하여 데이터를 スクレイピング하는 방법을 보여줍니다 (nginx 서버 설정 및 [nginx.conf](nginx.conf) 파일로 구성 업데이트가 필요합니다)
- rotating_proxy: ローテーティングプロキシ를 사용하여 데이터를 スクレイピング하는 방법을 보여줍니다 (nginx 서버 설정 및 [nginx.conf](nginx.conf) 파일로 구성 업데이트가 필요합니다)
- brightdata_proxy: Bright Data プロキシ를 사용하여 데이터를 スクレイピング하는 방법을 보여줍니다 ([Bright Data proxy configuration](#bright-data-proxy-configuration)이 필요합니다)

## Prerequisites
- Rust 및 Cargo (설치 가이드: [Rustup](https://rustup.rs/))
- Nginx (설치 가이드: [nginx](https://nginx.org/en/docs/install.html))

## Setup
1. 리포지토리를 클론합니다: `git clone git@github.com:bright-kr/proxy-scrape-rust.git`
2. 프로젝트 디렉터리로 이동합니다: `cd proxy-scrape-rust`
3. 의존성을 설치합니다: `cargo build`

## Running the Scraper
Cargo를 사용하여 스크레이퍼를 실행합니다:
```bash
cargo run
```
또는 다음 중 하나를 실행합니다
```bash
cargo run --bin (basic|basic_proxy|rotating_proxy|brightdata_proxy)
```
## Dependencies
이 프로젝트는 효과적으로 작동하기 위해 여러 외부 라이브러리를 활용합니다. 아래는 주요 의존성입니다:

### 1. Scraper
[Scraper](https://crates.io/crates/scraper)는 CSS selector를 기반으로 HTML 문서를 파싱하기 위한 Rust crate입니다. 이는 HTML5 사양을 준수하는 `html5ever` 라이브러리를 활용하여 견고하고 효율적인 파싱 기능을 보장합니다. 이 라이브러리는 HTML 콘텐츠에서 데이터를 추출하는 데 필수적이며, Webスクレイピング 작업에 적합합니다.

### 2. Reqwest
[Reqwest](https://crates.io/crates/reqwest)는 Rust용으로 인체공학적으로 설계된 배터리 포함형 HTTP Client입니다. 동기 및 비동기 リクエスト를 모두 지원하며 JSON 및 스트리밍 レスポンス와 같은 기능을 포함합니다. 이 라이브러리는 네트워크 リクエスト를 수행하는 과정을 단순화하고, 다양한 HTTP 관련 작업을 효율적으로 처리합니다.

### 3. Tokio
[Tokio](https://crates.io/crates/tokio)는 Rust로 비동기 애플리케이션을 작성하기 위한 이벤트 기반의 논블로킹 I/O 플랫폼입니다. 이는 Rust의 async/await 기능을 기반으로 구축되어 확장 가능하고 고성능 애플리케이션을 쉽게 작성할 수 있습니다. Tokio는 특히 네트워크 서비스에서 同時接続 작업을 다룰 때 비동기 작업과 타이머를 관리하는 데 중요합니다.

이러한 의존성을 사용하는 방법에 대한 자세한 정보와 예시는 각 문서에서 확인하시기 바랍니다.

## Bright Data proxy configuration
프로젝트를 실행하려면 유효한 プロキシ 서버가 필요합니다. [Bright Data](https://brightdata.co.kr/)와 같은 제공업체에서 プロキシ 서버 세부 정보를 얻을 수 있습니다. プロキシ 서버 세부 정보를 확보한 후, 적절한 プロキシ 구성으로 `main.rs` 파일을 업데이트하십시오.

## Contributing
기여를 환영합니다! 문제를 발견했거나 개선 제안이 있으시면 이슈를 열거나 pull request를 제출해 주십시오.

## License
이 프로젝트는 MIT License에 따라 라이선스가 부여됩니다. 자세한 내용은 [LICENSE](LICENSE) 파일을 참조하십시오.