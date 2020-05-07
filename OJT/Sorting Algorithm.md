####   Sorting Algorithm

- 선택 정렬 (Selection Sort)

- 버블 정렬 (Bubble Sort)
- 퀵 정렬 (Quick Sort)

~~~~java
package Day2;


public class Sort {

	public static void main(String[] args) {
		
		int []array = {67, 34, 1, 56, 4, 88, 9, 19, 22, 13, 2};
		for ( int i = 0 ; i<array.length; i++) {
			quick(array, 0, array.length-1);
			System.out.println(array[i]);
		}
	}
	// selection (오름차순) 
	private static void selection(int[] array, int length) {
		int min;
		int temp;
		for( int i = 0; i < length-1; i++) {
			min = i;
			for( int j = i + 1; j < length; j++ ) {
				if(array[j] < array[min]) {
					min = j;
				}
				temp = array[i];
				array[i] = array[min];
				array[min] = temp;
			}
		}
	}
	// bubble (오름차순)
	private static void bubble(int[] array, int length) {
		int temp;
		for ( int i = 0; i < array.length-1; i++) {
			for (int j = 0; j < array.length-i-1; j++) {
				if(array[j] > array[j+1]) {
					temp = array[j];
					array[j] = array[j+1];
					array[j+1] = temp;
				}
			}
		}
	}
	
	// Quick 
	// partion 부분과 quicksort 함수를 만들어 사용.
	
	//partion
	private static int partition(int[] array, int left, int right) {
		
		int pivot = array[(left+right)/2];
		while(left < right) {
			while ((array[left] < pivot) && (left < right))
				left++;
			while ((array[right] > pivot) && (left < right))
				right--;
			if( left < right) {
				int temp = array[left];
				array[left] = array[right];
				array[right] = temp;
			}
		}
		return left;
	}
	
	private static void quick(int array[], int left, int right) {
		if( left < right ) {
			int pivotNewIndex = partition(array, left, right);
			
			quick(array, left, pivotNewIndex - 1 );
			quick(array, pivotNewIndex + 1, right );
			
		}
	}
}

~~~~

