# ConcurrentProgramming

## 프로세스
- 존재론적으로 물질에는 사물과 프로세스가 있다.
- 사물은 공간상에서의 넓이를 갖지만 시간적인 넓이는 갖지 않는 것이며,프로세스는 공간과 시간의 넓이를 모두 갖는 것이다.
- 축구공은 특정한 시점에 존재하는 사물,축구게임은 특정한 시점에 경기의 일부만 존재하는 시간적인 넓이를 가진 프로세스

1.실행전상테 - 2.실행상태 - 3.대기상태 - 4.종료상태
## 대기 상태로 전이하는 3가지
- 데이터가 도착하기를 기다린다.데이터가 없으면 계산을 할수 없기 때문에
- 계산 리소스의 확보를 기다린다.리소스를 사용할수 있을떄까지 대기상태
- 자발적으로 대기 상태로 진입,아무것도 할필요가 없을떄
## 동시성
- 2개이상의 프로세스가 동시에 계산을 진행하는 상태
- 일반적으로 하나의 프로세스를 다룰수 있는 OS를 싱글태스크,여러개 멀티태스크

## 스레드
- 소속된 OS프로세스의 가상 메모리 공간과 시스템 자원을 공유
## 병렬성
- 동시성은 2개이상의 프로세스가 동시에 계산중인상태
- 병렬성은 여러 프로세스가 동시에 계산을 실행하는 상태
- 태스크병렬성,데이터병렬성,인스트럭션 레벨 병렬성

## 태스크병렬성
- 여러 태스크가 동시에 실행되는것을 의미(프러세스)
## 데이터병렬성
- 데이터를 여러개로 나눠서 병렬로 처리하는 방법
- 벡터연산:연산기 4대라면 각 계산을 4대연산기에서 따로


## 소유권 대여와 데이터 경합
- 불변대여 &를 사용해서 값을 빌리면 불편 레퍼런스
- &mut 키워드를 사용하면 가변 레퍼런스


std::thread::spawn	기본적인 멀티스레드 실행
Arc<Mutex<T>>	데이터를 공유하면서 안전하게 변경
std::sync::mpsc	메시지 패싱으로 스레드 간 통신
rayon	데이터 병렬 처리
tokio, async-std	비동기 방식 (멀티스레드와 다름)



## 멀티스레드
- 운영체제의 스레드를 직접 사용
- std::thread사용 Os의 스레드를 만들고 실행
- cpu코어 활용
- Arc<Mutex<T>>같은 동기화 활용
- 단순하 CPU병렬 작업애 효과적

## 비동기(async/tokio)
- 논 블로킹 방식으로 동작
- OS스레드 사용하지 않고 Task 단위로 만들고 실행
- async함수는 즉시 실행되지 않고 실행 가능한 작업으로 준비
- await 를 만나면 다른 작업 실행하면서 기다림

## Rayon(데이터 병렬 처리)
- CPU코어를 최대로 활용
- std::thread보다 간단하게 CPU 병렬처리


CPU 병렬 연산 → Rayon
→ 대량의 데이터를 병렬로 처리할 때 (map, reduce 같은 작업)
네트워크, 파일 입출력 병렬 처리 → async/await (tokio)
→ 대량의 HTTP 요청, DB 쿼리, 파일 입출력 작업
제어가 필요한 일반적인 멀티스레드 → std::thread
→ 특정한 OS 스레드 제어가 필요하거나 직접 관리해야 할 때


