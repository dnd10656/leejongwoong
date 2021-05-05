# 정렬 알고리즘 성능평가  

## 201901701 이종웅  

---  

### 버블 정렬 (Bubble Sort)  

```java
public class bubblesort {
    public static void main(String[] args){
        long start = System.currentTimeMillis();
        int[] a = {5,3,4,2,1};

        for(int i = 0; i< a.length-1; i++) {
            for (int j = 0; j < a.length - i - 1; j++) {
                if(a[j]>a[j+1]) {
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
![버블정렬 성능평가](file:///C:/Users/Administrator/Desktop/bubblesort.PNG)
