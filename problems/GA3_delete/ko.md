승현이의 하드 디스크에는 파일이 너무 많습니다.(?) 매일 이를 못마땅해하던 승현이는 드디어 오늘, 파일들을 정리하려고 합니다.

이 하드디스크의 파일 구조는 계층 트리 구조로, `N`개의 파일과 `M`개의 디렉토리로 구성되어 있습니다.

<center>

![그림 1](https://s3.ap-northeast-2.amazonaws.com/oj.uz/old/GA3_delete/image1.png?dl=1)

</center>

* **파일** : 위 그림에서 **사각형**으로 표현되어 있으며, `0`부터 `N - 1`까지의 번호가 붙어 있습니다.
* **디렉토리** : ***파일 또는 디렉토리를 포함***할 수 있으며, ***<u>디렉토리는 파일이 아닙니다</u>***. 디렉토리 역시 `0`부터 `M - 1`까지의 번호가 붙어 있습니다. 위 그림에서 **원**으로 표현되어 있습니다. 예로 들어, 3번 디렉토리는 2, 3, 4번 파일을 포함하고, 4번 디렉토리는 6번 파일과 5번 디렉토리(총 3개의 파일)를 포함합니다.
* **반드시 0번 디렉토리는 루트 디렉토리입니다.** 

안타깝게도, 파일을 삭제하는 명령어는 아래 2가지밖에 없습니다.

* **`del_file n`** : `n`번 파일을 삭제합니다. (단, `n`은 `0` 이상 `N - 1` 이하의 정수)
* **`del_dir d`** : `d`번 디렉토리를 삭제합니다. (단, `d`은 `0` 이상 `M - 1` 이하의 정수) 당연하지만, <u>**`d`번 디렉토리를 삭제한 이후 `d`번 디렉토리의 하위 파일 또는 디렉토리를 삭제할 수 없습니다.**</u>

예로 들어 위 그림에서 `"del_dir 4"` 명령어를 실행하면, 4번 디렉토리 하위의 모든 파일 또는 디렉토리(여기서는 6번, 7번, 8번 파일과 4번, 5번 디렉토리)가 삭제됩니다. 

승현이는 자신의 하드 디스크에서 **정확히 `K`개의 파일** (<span style='color:#ff0000; text-decoration: underline'>디렉토리는 파일이 아닙니다!</span>)을 삭제하려고 합니다. 명령어는 사람이 직접 입력해야 하기 때문에, 승현이는 얼마나 많은 시간을 들일지 미리 예상하려고 합니다.(?) 예로, 위 그림에서 `K = 4`라고 가정하면 `"del_dir 4", "del_file 5"` 와 같이 2번의 명령어로 4개의 파일을 삭제할 수 있으며, 이 경우보다 더 적은 명령어 수로 4개의 파일을 삭제할 수 없습니다.

승현이의 하드 디스크 구조가 주어질 때, `K`개의 파일을 삭제하기 위해 사용해야 할 최소한의 명령어 수를 구하는 프로그램을 작성하세요.

### 해야 할 일

당신은 승현이가 입력해야 할 최소한의 명령어 수를 반환하는 함수 `DeletePlan(N, M, K, A, B)`를 작성해야 합니다.

* **`N`** : 승현이의 하드 디스크에 있는 파일의 개수
* **`M`** : 승현이의 하드 디스크에 있는 디렉토리의 개수
* **`K`** : 삭제해야 할 파일의 개수(<span style='color:#ff0000; text-decoration: underline'>디렉토리는 파일이 아닙니다!</span>)
* **`A`** : 임의의 `i(0 ≤ i ≤ N - 1)`에 대해 `i`번 파일의 부모 디렉토리는 `A[i]`번 디렉토리입니다.
* **`B`** : 임의의 `i(1 ≤ i ≤ M - 1)`에 대해 `i`번 디렉토리의 부모 디렉토리는 `B[i]`번 디렉토리입니다. 단, 0번 폴더는 루트 디렉토리이므로, `B[0] = -1`입니다.

<!--

각 명령어를 실행하기 위해 아래 함수를 호출해야 합니다.

* **`DelFile(f)`** : `"del_file f"` 명령어를 실행합니다.
* **`DelDir(d)`** : `"del_dir f"` 명령어를 실행합니다.

!-->

### 서브태스크

#### 서브태스크 1 (15점)

* `1 ≤ K ≤ 5, N = 5, M = 2`

#### 서브태스크 2 (25점)

* `1 ≤ K ≤ N ≤ 300, 1 ≤ M ≤ 100`

#### 서브태스크 3 (35점)

* `1 ≤ K ≤ N ≤ 2 000, 1 ≤ M ≤ 1 000`

#### 서브태스크 4 (45점)

* `1 ≤ K ≤ N ≤ 10 000, 1 ≤ M ≤ 3 000`

### 구현 시 유의사항

#### 채점 환경

* 프로그램의 최대 실행 시간은 1.5초입니다. 채점 프로그램 부분의 실행 시간이 0.3초를 넘지 않음이 보장되어 있습니다.
* 메모리 제한은 256MB이며, 스택 메모리 역시 여기에 포함됩니다.

#### 인터페이스

**<u>[여기](https://s3.ap-northeast-2.amazonaws.com/oj.uz/old/GA3_delete/grader.zip)</u>**를 클릭하시면 문제 해결에 필요한 인터페이스가 제공됩니다. 이 인터페이스는 실제 채점 환경에서 사용되는 것과 같습니다. 이를 설명하면 아래와 같습니다.

* 작성해야 할 파일: `delete.c` 또는 `delete.cpp`
* 견본 채점 프로그램: `grader.c` 또는 `grader.cpp`
* 컴파일 쉘: `compile_c.sh` 또는 `compile_cpp.sh`
* 예제 입출력: `example.in`, `example.out` (위 그림을 표현한 파일입니다)

견본 채점 프로그램은 표준 입력(stdin)으로 입력을 받으며, 그 양식은 아래와 같습니다.

* 1번째 줄: `N, M, K`가 공백을 사이로 두고 입력됩니다.
* 2번째 줄: `A[0], A[1], .., A[N - 1]`이 공백을 사이로 두고 입력됩니다.
* 3번째 줄: `B[0], B[1], .., B[M - 1]`이 공백을 사이로 두고 입력됩니다.

견본 채점 프로그램은 표준 출력(stdout)으로 한 줄에 `DeletePlan` 함수의 반환값을 출력합니다.