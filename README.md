import java.util.*;

public class Main {
    
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int T = scanner.nextInt(); // number of test cases
        for (int t = 0; t < T; t++) {
            int N = scanner.nextInt(); // size of array
            int[] arr = new int[N];
            for (int i = 0; i < N; i++) {
                arr[i] = scanner.nextInt();
            }
            printNextGreaterElement(arr);
        }
        scanner.close();
    }

    public static void printNextGreaterElement(int[] arr) {
        Stack<Integer> stack = new Stack<>();
        Map<Integer, Integer> map = new HashMap<>();
        
        for (int i = 0; i < arr.length; i++) {
            while (!stack.isEmpty() && arr[i] > arr[stack.peek()]) {
                map.put(stack.pop(), arr[i]);
            }
            stack.push(i);
        }
        
        while (!stack.isEmpty()) {
            map.put(stack.pop(), -1);
        }
        
        for (int i = 0; i < arr.length; i++) {
            System.out.println(arr[i] + "," + map.get(i));
        }
    }
}
