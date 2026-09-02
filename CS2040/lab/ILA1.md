# In Lab Assignment 1, pea soup and pancakes

## Pseudocode

Since there are only 2 print statements, restaurant name if there is pea soup and pancakes, or anywhere is fine i guess if all the restaurants do not have both. Can just return early once we found the first restaurant with both menus.

```text
get num restaurants
for i in range(num):
    get num menu
    get name
    pea flag = false
    pan flag = false
    for j in range(num menu):
        get menu
        if menu is pea soup, pea flag is true
        if menu is pancakes, pan flag is true
        if both flags are true, print name and return

print anywhere is fine i guess
```

## Java code

```java
import java.io.*;

public class ILA1 {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int n = Integer.parseInt(br.readLine());

        for (int i = 0; i < n; i++) {
            int k = Integer.parseInt(br.readLine());
            String restaurant = br.readLine();

            boolean pea = false;
            boolean pancakes = false;

            for (int j = 0; j < k; j++) {
                String menu = br.readLine();
                if (menu.equals("pea soup")) pea = true;
                if (menu.equals("pancakes")) pancakes = true;
                if (pea && pancakes) {
                    System.out.println(restaurant);
                    return;
                }
            }
        }
        System.out.println("Anywhere is fine I guess");
    }
}
```