# 정렬 알고리즘 성능평가  

## 201901701 이종웅  

---  

### 성능 평가  
성능 평가의 경우   
```java
long start = System.currentTimeMillis();  
long end = System.currentTimeMillis();  
System.out.println("수행시간 : "+ (end-start)+ "ms");  
```  
을 사용해 수행시간으로 성능 평가를 하였습니다.  

### 버블 정렬 (Bubble Sort)  

```java
public class bubblesort {
    public static void main(String[] args){
        long start = System.currentTimeMillis();
        int[] a = {5,3,4,2,1};

        for(int i = 0; i< a.length-1; i++) {
            for (int j = 0; j < a.length - i - 1; j++) {
                if(a[j]>a[j+1]) {              //현재 원소가 다음 원소보다 클 경우 서로 원소의 위치를 교환
                    int b = a[j];
                    a[j] = a[j+1];
                    a[j+1] = b;

                }
            }
        }
        for(int i=0; i < a.length; i++) {
            System.out.print(a[i]);
            long end = System.currentTimeMillis();
            System.out.println("수행시간 : "+ (end-start)+ "ms");
        }
    }
}
```  

### 버블 정렬 RUN 결과  
```java  
1수행시간 : 0ms
2수행시간 : 13ms
3수행시간 : 13ms
4수행시간 : 13ms
5수행시간 : 13ms

Process finished with exit code 0
```  
버블 정렬 배열의 경우 5,3,4,2,1로 시작하여 이웃하는 숫자를 비교하여 작은 수를 앞쪽으로 이동시키는 과정을 반복하였습니다.
즉, 결과적으로 1,2,3,4,5이 나왔고, 오름차순으로 정렬되었습니다.  

### 선택 정렬 (Selection Sort)
```java
public class selectionsort {
    public static void main(String[] args){
        long start = System.currentTimeMillis();
        int[] a = {5,3,4,2,1};
        int min, temp;
        for(int i=0; i<a.length-1; i++){   // 위치를 선택해준다.
            min = i;
            for(int j=i+1; j<a.length; j++){ // i+1번째 원소부터 선택한 위치의 값과 비교를 시작한다.
                if(a[min]>a[j]){   //오름차순이므로 현재 선택한 자리에 있는 값보다 순회하고 있는 값이 작으면,
                    min = j;       //위치를 갱신해준다.
                }
            }
            temp = a[min];   //i+1번째 원소부터 선택한 위치의 값과 비교가 끝난 뒤 min에 처음 선택한 위치에
            a[min] = a[i];   //들어가야하는 값의 위치를 가지고 있으므로 서로 교환해준다.
            a[i] = temp;
        }
        for(int i=0; i < a.length; i++) {
            System.out.print(a[i]);

            long end = System.currentTimeMillis();
            System.out.println("수행시간 : "+ (end-start)+ "ms");
        }
    }
}
```  

### 선택 정렬 RUN 결과  
```java  
1수행시간 : 0ms
2수행시간 : 16ms
3수행시간 : 16ms
4수행시간 : 16ms
5수행시간 : 16ms

Process finished with exit code 0
```  
입력 배열 전체에서 최소값인 1을 선택하여 배열 0번 원소와 자리를 바꾸고, 0다음인 1번에 다음 최소값을 선택하여 배열 1번 원소와 자리를 바꾸게됩니다.  


### 삽입 정렬 (Insertion Sort)
```java
public class insertionsort {
    public static void main(String[] args){
        long start = System.currentTimeMillis();
        int[] a = {5,3,4,2,1};

        for(int i=1; i<a.length; i++){
            for(int j= i; j>0; j--){
                if(a[j-1] > a[j]) {  // 비교대상이 큰 경우 오른쪽으로 밀어낸다.
                    int temp = a[j-1];
                    a[j-1] = a[j];
                    a[j] = temp;
                }
            }
        }
        for(int i=0; i < a.length; i++) {
            System.out.print(a[i]);
            long end = System.currentTimeMillis();
            System.out.println("수행시간 : "+ (end-start)+ "ms");
        }
    }
}
```

### 삽입 정렬 RUN 결과
```java
1수행시간 : 0ms
2수행시간 : 14ms
3수행시간 : 14ms
4수행시간 : 14ms
5수행시간 : 14ms

Process finished with exit code 0
```
정렬되지 않은 부분의 가장 왼쪽 원소를 정렬된 부분의 적절한 위치에 삽입하여 정렬되도록 하는 과정을 반복합니다. 비교대상이 큰 경우 오른쪽으로 밀어내게 됩니다.  

### 쉘 정렬 (Shell Sort)
```java
public class shellsort {
    public static void main(String[] args){
        long start = System.currentTimeMillis();
        int[] a = {5,3,4,2,1};

        for(int gap=a.length/2; gap>0; gap/=2){ // gap 값을 반으로 줄인다.
            if(gap%2==0){  // gap이 짝수일 경우 홀수로 만든다.
                gap++;
            }
            for(int i=gap; i<a.length; i++){ //gap 설정을 통한 부분 리스트
                int element = a[i], j=i;
                while(j>=gap && a[j-gap]>element){ //부분 리스트 삽입 정렬
                    a[j] = a[j-gap];
                    j-=gap;
                }
                a[j] = element;
            }
        }
        for(int i=0; i < a.length; i++) {
            System.out.print(a[i]);
            long end = System.currentTimeMillis();
            System.out.println("수행시간 : "+ (end-start)+ "ms");
        }
    }
}
```
### 쉘 정렬 RUN 결과
```java
1수행시간 : 0ms
2수행시간 : 18ms
3수행시간 : 18ms
4수행시간 : 18ms
5수행시간 : 18ms

Process finished with exit code 0
```  
배열 뒷부분의 작은 숫자를 앞부분으로 빠르게 이동시키고, 동시에 앞부분의 큰 숫자는 뒷부분으로 이동시키고, 가장 마지막에는 삽입 정렬을 수행하게 됩니다.

### 버블, 선택, 삽입, 쉘 정렬 RUN 결과
모두 오름차순으로 정렬이 되었습니다.
성능 비교 결과, 총합 버블 = 52ms, 선택 = 64ms, 삽입 = 56ms, 쉘 = 72ms

버블 > 삽입 > 선택 > 쉘 정렬 순으로 버블이 가장 빠른 성능이 나오는 것을 알 수 있었습니다.

