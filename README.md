public class Main {
    public static void main(String[] args) {
        int[][] grid = {
                {1, 1, 0, 0, 0},
                {1, 0, 0, 1, 1},
                {0, 0, 0, 1, 0},
                {1, 1, 0, 0, 0}
        };

        countIslands(grid);
    }

    public static void countIslands(int[][] grid) {
        boolean[] visited = new boolean[grid.length];
        Deque<Integer> stack = new ArrayDeque<>();
        int count = 0;

        visited[0] = true;
        stack.push(0);

        while (!stack.isEmpty()) {
            int node = stack.pop();
            System.out.print(node + " ");

            for (int row = 0; row < grid.length; row++) {
                if (grid[node][row] == 1 && !visited[row]) {
                    visited[row] = true;
                    stack.push(row);
                    count++;
                }
            }

        }
        for(int i = 0; i < grid.length; i++){
            if(!visited[i]){
                System.out.print(i + " ");
                for(int j = 0; j < grid[i].length; j++){
                    if (grid[i][j] == 1 && !visited[j]) {
                        visited[j] = true;
                        count++;
                    }
                }
            }
        }
        System.out.println("\nNumber of Islands: " + count);
    }
}
