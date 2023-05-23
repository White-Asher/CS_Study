# 1. 시간복잡도

복잡도는 알고리즘의 성능을 나타내는 척도이다. <br>
복답도는 시간복잡도와 공간 복잡도로 나뉠 수 있다.
- 시간복잡도 : 알고리즘을 위해 필요한 연산의 횟수
- 공간복잡도 : 알고리즘을 위해 필요한 메모리의 양

효율적인 알고리즘을 사용한다 할 때 보통 시간복잡도와 공간복잡도는 일종의 거래 관계가 성립한다. <br> 
메모리가 조금 더 많이 사용하는 대신에 반복되는 연산을 생략하거나 더 많은 정보를 관리하면서 계산의 복잡도를 줄일 수 있다. <br>
이 때 메모리를 더 소모하는 대신에 얻을 수 있는 시간적 이점이 매우 큰 경우가 있다. <br>
DP 가 이러한 예이다. 


## 시간복잡도 표현법

### Big O Noration(빅-오 표기법) --- O(N)

- 가장 많이 쓰이는 표기법으로 알고리즘 실행시간의 상한을 나타낸 표기법 (최악의 경우) 
- 𝒇,𝒈는 음수값을 갖지 않는 함수, 𝒏≥𝒏_𝟎인 모든 자연수 𝒏 에  대해 𝒇(𝒏)≤𝒄∙𝒈(𝒏)이 되는 양의 정수 𝒄 와 𝒏 이 존재할 때의 표기는 다음과 같음 -> 𝒇(𝒏)=𝑶(𝒈(𝒏)) 

### Ω(오메가)표기법 --  Ω(N)
오메가 표기법은 알고리즘 실행시간의 하한을 나타낸 표기법 (최상의 경우)

### Θ(세타)표기법 --- Θ(N)
세타 표기법은 알고리즘 실행시간의 평균시간을 나타낸 표기법(평균의 경우)

## 복잡도 간의 관계

![](./%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98_4%EC%A3%BC%EC%B0%A8_White-Asher_Asset/2023-05-24-00-46-35.png)

![](./%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98_4%EC%A3%BC%EC%B0%A8_White-Asher_Asset/2023-05-24-00-47-39.png)

![](./%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98_4%EC%A3%BC%EC%B0%A8_White-Asher_Asset/2023-05-24-00-48-04.png)

# 2. 정렬

## 선택정렬(Selection sort)
가장작은 데이터를 찾은 후에 맨 앞에 있는 데이터와 바꾸고, 그 다음으로 가장 작은 데이터를 찾은 후 두번째 데이터와 바꾼다. <br>
가장 낮은 값이 맨 앞부터 정렬되며 전체 배열들이 정렬 될 때까지 이 과정을 계속 반복하여 정렬하는 과정을 선택정렬이라고 한다. <br>
선택정렬은 구현이 간단하지만, 시간 복잡도가 (N^2 + N) / 2 이다. 즉 빅오표기법으로 O(N^2) 이다. <br>
선택정렬은 기본 정렬 라이브러리를 포함해 다른 알고리즘과 비교했을 때 매우 비효율적이다. 

![](https://blog.kakaocdn.net/dn/Uwn2b/btrBF5yMTWv/6vXewtvKfdfHnuyf1p0HcK/img.gif)

```java
import java.util.Arrays;

public class SelectSort {
    public static void main(String[] args) {
        int[] array = new int[]{22, 50, 17, 25, 18, 32, 33, 44, 29, 8};

        for (int i = 0; i < array.length; i++) {
            int minIndex = i;
            for (int j = i + 1; j < array.length; j++) {
                if(array[minIndex] > array[j]){
                    minIndex = j;
                }
            }
            int temp = array[minIndex];
            array[minIndex] = array[i];
            array[i] = temp;
        }
        System.out.println(Arrays.toString(array));
    }
}

// 결과
// [8, 17, 18, 22, 25, 29, 32, 33, 44, 50]
```

## 버블정렬 (Bubble sort)

1. 버블정렬은 i(처음에는 0번째 인덱스) 인덱스부터 i+1(인접한 인덱스)와 값을 비교한다. 
2. i 인덱스가 크다면 i+1인덱스와 위치를 바꾼다. 
3. i+1인덱스가 크면 다음 인덱스와 인접 인덱스를 비교한다. 
4. 2-3 과정을 한번 반복하면 맨 마지막 인덱스에 리스트 중 가장 큰 값이 정렬된다. 
5. 4 과정을 계속 반복하면 가장 큰 값부터 마지막 인덱스부터 처음 인덱스까지 오름차순 정렬된다. 

버블 정렬은 선택정렬과 마찬가지로 전체를 비교하기 때문에 시간복잡도는 O(N^2) 이다.<br>

![](https://blog.kakaocdn.net/dn/bVAqoD/btrBJMxIEWL/II73nbjQumxJnoMkFmkAu0/img.gif)

```java
import java.util.Arrays;

public class BubbleSort {
    public static void main(String[] args) {
        int[] array = new int[]{34, 6, 41, 16, 38, 36, 28, 19, 45, 43, 49};

        for (int i = 0; i < array.length; i++) {
            for (int j = 0; j < array.length - i - 1; j++) {
                // 현재 인덱스의 값이 다음 인덱스의 값보다 클 경우 실행
                if(array[j] > array[j + 1]){
                    int temp = array[j + 1];
                    array[j + 1] = array[j];
                    array[j] = temp;
                }
            }
        }
        System.out.println(Arrays.toString(array));
    }
}

// 출력
// [6, 16, 19, 28, 34, 36, 38, 41, 43, 45, 49]
```

### 삽입 정렬 (Insertion sort)

삽입정렬은 탐색하고 있는 현재 위치에서 맨 처음 배열까지 비교하여 자신이 들어갈 위치를 찾아 그 위치에 해당 값을 삽입하는 알고리즘이다.  
1. 두번째 인덱스(i) 부터 시작하며 첫번째 인덱스(i-1)와 값을 비교한다. 
2. 두번째 인덱스(i)가 첫번째 인덱스(i-1)보다 작다면 두번째 인덱스(i) 를 첫번째 인덱스 앞에 정렬한다. 
3. i를 1씩 증가시키면서 첫번째 인덱스와 i-1 인덱스 사이의 배열 중에서 현재 i인덱스의 값이 들어갈 곳을 찾는다. 
4. 해당 인덱스 위치에 값을 삽입한다. 
5. 맨 끝 인덱스까지 같은 과정을 반복하면 삽입 정렬의 연산이 끝난다.

![](https://blog.kakaocdn.net/dn/btAv42/btrBFHLHqaA/PEChPPyKwSaGMtKRoSfIuK/img.gif)

삽입정렬은 선택정렬에 비해 구현 난이도는 높지만 선택 정렬에 비해 실행 시간 측면에서 더 효율적이다. <br>
삽입정렬은 데이터가 거의 정렬 되어있을 때 훨씬 효율적이다. <br>
삽입정렬의 시간복잡도는 O(N^2) 이다. 삽입 정렬은 리스트에서 데이터가 거의 정렬되어 있는 상태라면 최선의 경우에 O(N)의 시간복잡도를 가진다. <br>
삽입정렬은 퀵 정렬과 비교했을 때 삽입정렬이 보통 비효율적이지만 데이터가 거의 정렬된 상태라면 삽입정렬을 이용하는 것이 시간복잡도 측면에서 이득을 볼 수 있다. <br>

```java
import java.util.Arrays;

public class InsertSort {
    public static void main(String[] args) {
        int[] array = new int[]{3, 44, 38, 5, 47, 15, 36, 26, 27, 2, 46, 4, 19, 50, 48};

        for (int i = 1; i < array.length; i++) {
            for (int j = i; j >= 1; j--) {
                if(array[j] < array[j-1]){
                    int temp = array[j-1];
                    array[j-1] = array[j];
                    array[j] = temp;
                } else break;
            }
        }
        System.out.println(Arrays.toString(array));
    }
}
// 출력
// [2, 3, 4, 5, 15, 19, 26, 27, 36, 38, 44, 46, 47, 48, 50]
```

## 퀵 정렬 (Quick sort)
기준 데이터를 설정하고 그 기준보다 작은 데이터와 큰 데이터를 서로 바꿔서 정렬하는 방법.
```
퀵 정렬에는 피봇(Pivot)이라는 개념이 사용된다. 
피봇은 한 마디로 정렬 될 기준 원소를 뜻한다. 
피봇 선택 방법에 따라 퀵 정렬의 성능이 달라질 수 있다. 
최적의 피봇 선택이 어려우므로 임의 선택을 해야 한다. 
보통 배열의 첫 번째 값이나 중앙 값을 선택한다. 퀵 정렬의 동작방식은 다음과 같다. 
가령 예를 들어 배열 [5, 6, 1, 4, 2, 3, 7]이 있고, 피봇을 임의로 4를 선택했다 가정하자. 
이후 4를 기준으로 작은 것은 왼쪽으로 큰 것은 오른쪽으로 보내 [1, 2, 3] < 4 < [5, 6, 7]를 생성한다. 
다시 왼쪽에서부터 임의의 피봇 2를 설정하여 [1] < 2 < [3]을 생성하고 
오른쪽에선 임의의 피봇 6를 설정하여 [5] < 6 < [7]로 나눈다. 
만약 배열 길이가 1이 된다면 가장 정렬 완료된 것이므로 분할된 배열을 합쳐 줌으로써 정렬을 마친다. 
- 출처: https://roytravel.tistory.com/328 - 
```

이 포스트에서 퀵 정렬은 호어 분할 방식을 기준으로 퀵 정렬을 정의한다. 자세한 동작방식은 아래와같다. 

1. 기준 데이터인 축(Pivot)을 정한다.
2. 축(Pivot)은 리스트에서 첫번째 값으로 정한다. 
3. low는 오른쪽으로, high는 왼쪽으로 이동하게 되는데 이 때
4. 피벗으로 설정한 첫번째 인덱스를 제외하고 두번째 인덱스와 마지막 인덱스의 값을 서로 비교한다
5. 만약 두 인덱스가 피벗값을 기준으로 low인덱스가 피벗값보다 높고 high인덱스가 피벗값 보다 낮다면 두 인덱스를 교환한다.
6. 교환하면 low를 오른쪽으로 한칸, high를 왼쪽으로 한칸 옮기고 pivot값을 기준으로 두 인덱스를 비교한다. 
7. 만약 low는 pivot보다 큰 수를 만나거나 pivot을 만나면 멈추고, 
8. high는 pivot보다 작은 수를 만나거나 pivot을 만나면 멈춘다.
9. 위의 과정을 low가 high의 오른쪽에 올때까지 반복한다. 
10. low와 pivot 값을 바꾼다.
11. pivot기준으로 작은 리스트들과 pivot기준으로 큰 리스트들로 구분된다.
12. 1-10 연산을 두 리스트에 반복한다. 

![](./%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98_4%EC%A3%BC%EC%B0%A8_White-Asher_Asset/2023-05-23-22-33-40.png)

이미지 출처: https://gmlwjd9405.github.io/2018/05/10/algorithm-quick-sort.html


퀵 정렬의 평균 시간복잡도는 O(NlogN)이다. 최악의 경우 O(N^2)이다 <br>
퀵정렬은 데이터가 무작위로 정렬되어 있는경우 빠르게 동작할 확률이 높다 <br>
앞서 pivot을 가장 왼쪽 데이터로 삼을 때 이미 데이터가 정렬되어 있는 경우 매우 느리게 동작한다. <br>
기준이되는 pivot 값을 랜덤으로 하거나 중간값으로 한다. <br>
즉, pivot을 어떻게 설정하느냐에 따라 성능의 편차가 심하다. <br>

```java
import java.util.*;

public class Main {

    public static void quickSort(int[] arr, int start, int end) {
        if (start >= end) return; // 원소가 1개인 경우 종료
        int pivot = start; // 피벗은 첫 번째 원소
        int left = start + 1;
        int right = end;
        while (left <= right) {
            // 피벗보다 큰 데이터를 찾을 때까지 반복
            while (left <= end && arr[left] <= arr[pivot]) left++;
            // 피벗보다 작은 데이터를 찾을 때까지 반복
            while (right > start && arr[right] >= arr[pivot]) right--;
            // 엇갈렸다면 작은 데이터와 피벗을 교체
            if (left > right) {
                int temp = arr[pivot];
                arr[pivot] = arr[right];
                arr[right] = temp;
            }
            // 엇갈리지 않았다면 작은 데이터와 큰 데이터를 교체
            else {
                int temp = arr[left];
                arr[left] = arr[right];
                arr[right] = temp;
            }
        }
        // 분할 이후 왼쪽 부분과 오른쪽 부분에서 각각 정렬 수행
        quickSort(arr, start, right - 1);
        quickSort(arr, right + 1, end);
    }

    public static void main(String[] args) {
        int n = 10;
        int[] arr = {7, 5, 9, 0, 3, 1, 6, 2, 4, 8};

        quickSort(arr, 0, n - 1);

        for(int i = 0; i < n; i++) {
            System.out.print(arr[i] + " ");
        }
    }

}
```

## 병합 정렬 (Quick sort)

![](https://blog.kakaocdn.net/dn/c89fIk/btr0NIxtE3I/FIuZwmMulXRHSoalYfbWj0/img.gif)

퀵 정렬과 함께 두 개의 알고리즘이 사용된다는 측면에서 공통점을 가진다. <br>
차이점은 퀵 정렬이 피봇 선택 이후 피봇 기준으로 대소를 비교하는 반면, 병합 정렬은 배열을 원소가 하나만 남을 때 까지 계속 이분할 한 다음, 대소관계를 고려하여 다시 재배열 하며 원래 크기의 배열로 병합한다 <br>
시간 복잡도의 경우 최선, 평균, 최악 모두 O(NlogN) 이며 공간 복잡도의 경우 정렬된 원소를 담을 배열이 하나 필요로 하므로 O(N) 이다.  <br>



TopDown.java
```java
import java.util.Arrays;

public class MergeSort_TopDown {

    public static void main(String[] args) {
        int[] array = new int[]{7, 5, 9, 0, 3, 1, 6, 2, 4, 8};
        mergeSort(array);
        System.out.println(Arrays.toString(array));
    }

    // 합치는 과정에서 정렬하여 원소를 담을 임시 배열
    private static int[] sorted;

    public static void mergeSort(int[] arr) {
        sorted = new int[arr.length];
        mergeSort(arr, 0, arr.length - 1);
        sorted = null;
    }

    // Top-Down 방식 구현
    private static void mergeSort(int[] arr, int left, int right) {
        /*
         * left == right 즉, 부분리스트가 1개의 원소만 갖고 있는 경우
         * 더 이상 쪼갤 수 없으므로 return 함
         */
        if (left == right) return;
        int mid = (left + right) / 2; // 절반 위치
        
        mergeSort(arr, left, mid); // 절반 중 왼쪽 부분리스트(left ~ mid)
        mergeSort(arr, mid+1, right); // 절반 중 오른쪽 부분리스트(mid+1 ~ right)
        
        merge(arr, left, mid, right); // 병합 작업
    }

    /**
     *
     * @param arr : 정렬할 배열
     * @param left : 배열의 시작점
     * @param mid : 배열의 중간점
     * @param right : 배열의 끝점
     */
    private static void merge(int[] arr, int left, int mid, int right) {
        int leftStart = left; // 왼쪽 부분리스트 시작점
        int rightStart = mid + 1; // 오른쪽 부분리스트의 시작점
        int index = left; // 채워넣을 배열의 인덱스

        while (leftStart <= mid && rightStart <= right) {
            /*
            왼쪽 부분리스트 leftStart 번째 원소가 오른쪽 부분리스트 rightStart 번째 원소보다 작거나 같을 경우
            왼쪽의 leftStart 번째 원소를 새 배열에 넣고 leftStart 과 index 를 1 증가시킨다.
             */
            if (arr[leftStart] <= arr[rightStart]) {
                sorted[index] = arr[leftStart];
                index++;
                leftStart++;
            }
            /*
            오른쪽 부분리스트 rightStart 원소가 왼쪽 부분리스트 leftStart 번째 원소보다 작거나 같을 경우
            오른쪽의 rightStart 번째 원소를 새 배열에 넣고 rightStart 과 index 를 1 증가시킨다.
             */
            else {
                sorted[index] = arr[rightStart];
                index++;
                rightStart++;
            }
        }

        /*
        왼쪽 부분리스트가 먼저 모두 새 배열에 채워졌을 경우 (leftStart > mid)
		 = 오른쪽 부분리스트 원소가 아직 남아있을 경우
		 오른쪽 부분리스트의 나머지 원소들을 새 배열에 채워준다.
         */
        if (leftStart > mid) {
            while (rightStart <= right) {
                sorted[index] = arr[rightStart];
                index++;
                rightStart++;
            }
        }

        /*
        오른쪽 부분리스트가 먼저 모두 새 배열에 채워졌을 경우 (rightSide > right)
        = 왼쪽 부분리스트 원소가 아직 남아있을 경우
        왼쪽 부분리스트의 나머지 원소들을 새 배열에 채워준다.
         */
        else {
            while (leftStart <= mid) {
                sorted[index] = arr[leftStart];
                index++;
                leftStart++;
            }
        }

        /*
        정렬된 새 배열을 기존의 배열에 복사하여 옮겨준다.
         */
        for (int i = left; i <= right; i++) {
            arr[i] = sorted[i];
        }

    }
}
```

BottomUp.java
```java
import java.util.Arrays;

public class MergeSort_BottomUp {

    public static void main(String[] args) {
        int[] array = new int[]{7, 5, 9, 0, 3, 1, 6, 2, 4, 8};
        mergeSort(array);
        System.out.println(Arrays.toString(array));
    }

    // 합치는 과정에서 정렬하여 원소를 담을 임시 배열
    private static int[] sorted;

    public static void mergeSort(int[] arr) {
        sorted = new int[arr.length];
        mergeSort(arr, 0, arr.length - 1);
        sorted = null;
    }

    // Bottom-Up 방식 구현
    private static void mergeSort(int[] arr, int left, int right) {
        /*
        1 - 2 - 4 - 8 - ... 식으로 1부터 서브리스트를 나누는 기준을 두 배씩 늘린다.

        두 부분리스트을 순서대로 병합해준다.
        예를들어 현재 부분리스트의 크기가 1(size=1)일 때
        왼쪽 부분리스트(low ~ mid)와 오른쪽 부분리스트(mid + 1 ~ high)를 생각하면
        왼쪽 부분리스트는 low = mid = 0 이고,
        오른쪽 부분리스트는 mid + 1부터 low + (2 * size) - 1 = 1 이 된다.

        이 때 high 가 배열의 인덱스를 넘어갈 수 있으므로 right 와 둘 중 작은 값이
        병합되도록 해야한다.
         */
        for (int size = 1; size <= right ; size += size) {
            for(int i = 0; i <= right - size; i += (2 * size)) {
                int low = i;
                int mid = i + size - 1;
                int high = Math.min(i + (2 * size) - 1, right);
                merge(arr, low, mid, high);		// 병합작업
            }
        }
    }

    /**
     *
     * @param arr : 정렬할 배열
     * @param left : 배열의 시작점
     * @param mid : 배열의 중간점
     * @param right : 배열의 끝점
     */
    private static void merge(int[] arr, int left, int mid, int right) {
        int leftStart = left; // 왼쪽 부분리스트 시작점
        int rightStart = mid + 1; // 오른쪽 부분리스트의 시작점
        int index = left; // 채워넣을 배열의 인덱스

        while (leftStart <= mid && rightStart <= right) {
            /*
            왼쪽 부분리스트 leftStart 번째 원소가 오른쪽 부분리스트 rightStart 번째 원소보다 작거나 같을 경우
            왼쪽의 leftStart 번째 원소를 새 배열에 넣고 leftStart 과 index 를 1 증가시킨다.
             */
            if (arr[leftStart] <= arr[rightStart]) {
                sorted[index] = arr[leftStart];
                index++;
                leftStart++;
            }
            /*
            오른쪽 부분리스트 rightStart 원소가 왼쪽 부분리스트 leftStart 번째 원소보다 작거나 같을 경우
            오른쪽의 rightStart 번째 원소를 새 배열에 넣고 rightStart 과 index 를 1 증가시킨다.
             */
            else {
                sorted[index] = arr[rightStart];
                index++;
                rightStart++;
            }
        }

        /*
        왼쪽 부분리스트가 먼저 모두 새 배열에 채워졌을 경우 (leftStart > mid)
		 = 오른쪽 부분리스트 원소가 아직 남아있을 경우
		 오른쪽 부분리스트의 나머지 원소들을 새 배열에 채워준다.
         */
        if (leftStart > mid) {
            while (rightStart <= right) {
                sorted[index] = arr[rightStart];
                index++;
                rightStart++;
            }
        }

        /*
        오른쪽 부분리스트가 먼저 모두 새 배열에 채워졌을 경우 (rightSide > right)
        = 왼쪽 부분리스트 원소가 아직 남아있을 경우
        왼쪽 부분리스트의 나머지 원소들을 새 배열에 채워준다.
         */
        else {
            while (leftStart <= mid) {
                sorted[index] = arr[leftStart];
                index++;
                leftStart++;
            }
        }

        /*
        정렬된 새 배열을 기존의 배열에 복사하여 옮겨준다.
         */
        for (int i = left; i <= right; i++) {
            arr[i] = sorted[i];
        }

    }
}
```

대부분의 경우 정렬 과정은 최대한 재귀는 피하여 구현하는게 일반적이기 때문에 Bottom-Up 으로 구현하는 것이 좋다.



## 계수 정렬 (Counting sort)
특정한 조건이 부합할 때만 사용할 수 있지만 매우 빠른 정렬 알고리즘이다. 

계수정렬은 별도의 리스트를 선언하고 그 안에 정렬에 대한 정보를 담는다는 특징이 있다. 

![](https://blog.kakaocdn.net/dn/dQdjbi/btrBGNrF5uE/AaOdeOTxfpcklzAD9XKfY0/img.gif)

1. 계수 정렬은 먼저 가장 큰 데이터와 가장 작은 데이터의 범위가 모두 담길 수 있는 리스트를 생성한다 
2. 위의 예시에서 1부터 9까지 정렬범위이므로 크기가 9인 리스트를 선언하고 리스트의 값들을 0으로 초기화한다
3. 이후 리스트를 순회하면서 해당 원소가 등장하면 1,2 과정에서 생성한 리스트 인덱스의 값을 1 증가시킨다.
4. 이후 1,2 과정에서 생성한 리스트의 인덱스 X 원소 값 을 차례로 출력하면된다.
5. 예시에서 1을 가르키는 인덱스가 값이 2가 저장되어있으므로 1을 두번 출력, 2는 7번 출력... 반복해서 출력하는 방식이다.

```java
public class CountingSort {
    public static void main(String[] args) {
        int[] arr = {7, 5, 9, 0, 3, 1, 6, 2, 9, 1, 4, 8, 0, 5, 2, 2};
        int[] countArr = new int[arr.length];

        for (int j : arr) {
            countArr[j] += 1; // 각 데이터에 해당하는 인덱스의 값 증가
        }
        for (int i = 0; i < arr.length; i++) { // 배열에 기록된 정렬 정보 확인
            for (int j = 0; j < countArr[i]; j++) {
                System.out.print(i + " "); // 띄어쓰기를 기준으로 등장한 횟수만큼 인덱스 출력
            }
        }
    }
}
```

## 각 알고리즘 별 시간 복잡도와 평균 정렬 속도

![](./%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98_4%EC%A3%BC%EC%B0%A8_White-Asher_Asset/2023-05-23-22-43-49.png)

# 3. 재귀

재귀 알고리즘은 함수가 자기 자신을 호출하는 것을 허용하는 알고리즘이다. <br>
주어진 문제를 더 작은 부분 문제로 분할하고, 각 부분 문제를 해결하여 원래 문제를 해결하는 분할 정복(Divide and Conquer) 방법으로 볼 수 있다. 

재귀알고리즘은 다음과 같은 구조를 갖는다. 

기저 조건(Base case): 재귀 호출을 중단하는 조건이다. 기저 조건에 도달하면 더 이상 재귀 호출을 수행하지 않고, 결과값을 반환하거나 처리한다.

재귀 호출(Recursive call): 함수 내부에서 자기 자신을 호출하는 부분이다. 이 부분은 원래의 문제를 더 작은 부분 문제로 분할하는 역할을 한다. 재귀 호출은 주어진 문제를 해결하기 위해 동일한 함수를 반복적으로 호출한다.

문제의 분할과 병합: 재귀 호출에 의해 문제가 더 작은 부분 문제로 분할되고, 각 부분 문제가 재귀적으로 해결된 후에는 이를 병합하여 원래 문제의 해를 얻는다. 이 과정은 작은 문제들의 해를 이용하여 전체 문제의 해를 구하는 것을 의미한다.

재귀 알고리즘은 재귀 호출을 이용하여 문제를 해결하기 때문에, 문제를 해결하는 과정에서 중복된 연산이 발생할 수 있다. 따라서 중복된 연산을 효율적으로 피하기 위해 메모이제이션(Memoization) 기법을 사용하는 것이 좋다. 메모이제이션은 한 번 계산한 값을 저장하여 재사용하는 방식으로, 동일한 입력에 대한 연산을 다시 수행하지 않고 기존에 계산한 값을 반환한다.

다음의 피보나치를 예로 들어 설명하고자 한다. 피보나치의 정의는 다음과 같다. 

![](2023-05-23-23-42-58.png)

피보나치의 수를 구한다고 가정할 때 다음과 같이 나타낼 수 있다. (예시에서는 fib(5))

![](2023-05-23-23-43-25.png)

피보나치 수열은 재귀함수 형태로 표현된다.
```
f(0) = 1
f(1) = 1
f(n) = f(n-1) + f(n-2) when n > 1
```

재귀함수 방식으로 계산하게 된다면 비효율적인 계산을 하게된다.
```java
import java.util.Scanner;
 
public class Fibo {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		System.out.println(fibo(sc.nextInt()));
	}
	
	static int fibo(int n) {
		if(n == 0) {
			return 0;
		}
		else if(n == 1 || n == 2) {
			return 1;
		}
		else {
			return fibo(n-1) + fibo(n-2);
		}
	}
}
```

왜냐하면 재귀함수 방식으로 계산하면 피보나치 수 5를 구할 때 총 15번의 함수 호출을 해야 하는데 피보나치의 수를 100, 또는 1000.. 같이 피보나치의 수가 높아질 수록 수많은 함수 호출과 연산을 수행하여야 한다. <br>
(fib(1)(2)...(n-1)까지의 연산결과를 알고있음에도...)
이는 매우 비효율적이다 이때 시간복잡도는 O(2^N)이다..<br>
이를 해결하기 위해 동적계획법 이라는 알고리즘 설계 기법이 나온 것이다.

# 4. DP

동적 계획법(Dynamic Programming)은 큰 문제를 작은 부분 문제로 나누어 해결하는 알고리즘 기법이다. <br>
동적 계획법은 부분 문제의 해를 계산하고, 이를 저장하여 중복 계산을 피하며 효율적으로 문제를 해결하는 방법이다.

동적 계획법은 다음과 같은 과정을 통해 문제를 해결한다.

1. 문제를 작은 부분 문제로 분할한다. 이때, 부분 문제는 중복되어야 하며 최적 부분 구조를 가져야 한다.
2. 부분 문제의 해를 계산하고 저장한다. 이를 통해 중복 계산을 피한다. 부분 문제의 해는 배열, 테이블 등을 이용하여 저장한다.
3. 작은 부분 문제의 해를 이용하여 큰 문제의 해를 구한다. 이때, 최적 부분 구조를 활용하여 문제의 최적해를 도출한다.

그래서 재귀함수를 이용해 다이나믹 프로그래밍 소스 코드를 작성하는 방법을,
큰 문제를 해결하기 위해 작은 문제를 호출한다고 하여 탑다운 방식이라고 말한다. <br>
반면에 단순히 반복문을 이용하여 소스코드를 작성하는 경우 작은 문제부터 차근차근 답을 도출한다고 하여 보텀업 방식이라고 말한다. 

## Top-Down

Top-down은  큰 문제부터 시작해서 계속 작은 문제로 분할해 가면서 푸는 것 이다.<br>
fibo(4)를 구하는 큰 문제는 fibo(3), fibo(2)를 구하는 작은 문제로 나눌 수 있고 fibo(3)은 fibo(2), fibo(1)을 구하는 더 작은 문제로 나눌 수 있다. <br>
이를 다음과 같이 구현할 수 있다.

```java
public class FiboDP {
	public static int[] memo;
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		memo = new int[n+1];
		System.out.println(fibo(n));
	}
	
	public static int fibo(int i) {
		if (i == 0) {
			return 0;
		} else if (i == 1 || i == 2){
			return 1;
		} 
		
		if(memo[i] != 0) {
			return memo[i];
		}
		
		memo[i] = fibo(i-1) + fibo(i-2);
		return memo[i];
	}
}
```

## Bottom-up
작은 문제부터 시작해서 작은 문제를 점점 쌓아 큰 문제를 푸는 것이다. <br>
첫 번째 피보나치 수와 두 번째 피보나치 수를 구하면 세 번째 피보나치 수를 구할 수 있고, 두 번째, 세 번째 피보나치 수를 구하면 네 번째 피보나치 수를 구할 수 있다. <br>

```java
import java.util.Scanner;
 
public class FiboDP2 {
	public static int[] memo;
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		memo = new int[n+1];
		
		if(n == 0) {
			memo[0] = 0;
		} else if(n == 1) {
			memo[1] = 1;
		} else if(n == 2) {
			memo[2] = 1;
		} else {
			memo[0] = 0;
			memo[1] = 1;
			memo[2] = 1;
			for (int i = 3; i < n+1; i++) {
				memo[i] = memo[i-1] + memo[i-2];
			}
		}
 
		System.out.println(memo[n]);
	}
}
```

# 5. DFS, BFS, 백트래킹


# 6. 그래프 심화 (벨만포드, 다익스트라, 플로이드 와샬)


# 7. MST


# 8. 분할정복, 이분탐색


## 분할정복

## 이분탐색

- 이진탐색은 정렬되어 있는 데이터에서 탐색범위를 절반씩 좁혀가며 데이터를 탐색하는 방법이다.
- 이진 탐색은 시작점, 끝점, 중간점의 위치 변수 3개를 이용한다.
- 찾으려는 데이터와 중간점 위치에 있는 데이터를 반복적으로 비교해서 원하는 데이터를 찾는다. 
- 단계마다 탐색범위를 2로 나누어 시간복잡도는 O(logN) 이다. (log₂에 비례함)
- 이진탐색을 구현하는 방법은 재귀함수를 이용하거나, 반복문을 이용한다
- 이진탐색 문제는 탐색 범위가 큰 상황에서 탐색을 가정하는 문제가 많으므로 탐색범위가 2천만을 넘어가면 사용하는 것을 권장

![](https://blog.kakaocdn.net/dn/cqFVeT/btrBNcRtsjt/esnkUBGuMHTchpG20Sx5Y0/img.gif)

### 재귀함수를 이용한 이분탐색

```java
import java.util.*;

public class Main {

    // 이진 탐색 소스코드 구현(재귀 함수)
    public static int binarySearch(int[] arr, int target, int start, int end) {
        if (start > end) return -1;
        int mid = (start + end) / 2;
        // 찾은 경우 중간점 인덱스 반환
        if (arr[mid] == target) return mid;
        // 중간점의 값보다 찾고자 하는 값이 작은 경우 왼쪽 확인
        else if (arr[mid] > target) return binarySearch(arr, target, start, mid - 1);
        // 중간점의 값보다 찾고자 하는 값이 큰 경우 오른쪽 확인
        else return binarySearch(arr, target, mid + 1, end);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        // 원소의 개수(n)와 찾고자 하는 값(target)을 입력받기 
        int n = sc.nextInt();
        int target = sc.nextInt();

        // 전체 원소 입력받기 
        int[] arr = new int[n];
        for (int i = 0; i < n; i++) {
            arr[i] = sc.nextInt();
        }

        // 이진 탐색 수행 결과 출력 
        int result = binarySearch(arr, target, 0, n - 1);
        if (result == -1) {
            System.out.println("원소가 존재하지 않습니다.");
        }
        else {
            System.out.println(result + 1);
        }
    }

}
```

### 반복문을 이용한 이분 탐색

```java
public class Main {

    // 이진 탐색 소스코드 구현(반복문)
    public static int binarySearch(int[] arr, int target, int start, int end) {
        while (start <= end) {
            int mid = (start + end) / 2;
            // 찾은 경우 중간점 인덱스 반환
            if (arr[mid] == target) return mid;
            // 중간점의 값보다 찾고자 하는 값이 작은 경우 왼쪽 확인
            else if (arr[mid] > target) end = mid - 1;
            // 중간점의 값보다 찾고자 하는 값이 큰 경우 오른쪽 확인
            else start = mid + 1; 
        }
        return -1;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        // 원소의 개수(n)와 찾고자 하는 값(target)을 입력받기 
        int n = sc.nextInt();
        int target = sc.nextInt();

        // 전체 원소 입력받기 
        int[] arr = new int[n];
        for (int i = 0; i < n; i++) {
            arr[i] = sc.nextInt();
        }

        // 이진 탐색 수행 결과 출력 
        int result = binarySearch(arr, target, 0, n - 1);
        if (result == -1) {
            System.out.println("원소가 존재하지 않습니다.");
        }
        else {
            System.out.println(result + 1);
        }
    }

}
```

# 9. 그리디



# 10. 투포인터 



참고한 곳
- https://coding-factory.tistory.com/615
- https://www.digitalocean.com/community/tutorials/js-bubble-selection-insertion-sort
- http://www-scf.usc.edu/~zhan468/public/Notes/sorting.html
- https://devbin.kr/2020/algorithm-sort-algorithm-%EC%A0%95%EB%A0%AC-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98/
- https://jbhs7014.tistory.com/180
- 이것이 취업을 위한 코딩테스트다 with 파이썬 - 나동빈 https://roytravel.tistory.com/328
- https://st-lab.tistory.com/233
