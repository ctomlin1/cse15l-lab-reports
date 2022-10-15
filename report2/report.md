# Week 3 Lab Report
## Part 1

```
ArrayList<String> list = new ArrayList<>();
public String handleRequest(URI url) {
    if (url.getPath().contains("/add")) {
        String[] parameters = url.getQuery().split("=");
        if(!parameters[0].equals("s")) return "error";
        if(list.contains(parameters[1])) return "error: item already in list";
        list.add(parameters[1]);
        return "added \"" + parameters[1] + "\" to the list";
    } else if(url.getPath().contains("/search")) {
        String[] parameters = url.getQuery().split("=");
        if(!parameters[0].equals("s")) return "error";
        String ret = "";
        for(String s : list) {
            if(s.contains(parameters[1])) {
                ret += s + " ";
            }
        }
        return ret;
    }
    return "error";
}
```
1. The handleRequest method is called with the url "localhost:4000/add?s=anewstringtoadd". The string "anewstringtoadd" is added to list, which was previously empty. ![](https://ctomlin1.github.io/cse15l-lab-reports/report2/add1.png)
2. The handleRequest method is called again with the url "localhost:4000/add?s=pineapple". The string "pineapple" is added to list, which now contains the strings "anewstringtoadd" and "apple". ![](https://ctomlin1.github.io/cse15l-lab-reports/report2/add2.png)
3. The handleRequest method is called again with the url "localhost:4000/search?s=app". The string `ret` is created, then each string in the list containing the substring "app" is added to `ret`. ![](https://ctomlin1.github.io/cse15l-lab-reports/report2/query.png)

## Part 2
1. - Failure-inducing input:
        ```
        @Test
            public void testAverageWithoutLowest() {
                double[] input3 = {1.5, 1.5, 2.5};
                assertEquals(2.0, ArrayExamples.averageWithoutLowest(input3), 0);
            }
        ```
    - Symptom: `expected:<2.0> but was:<1.25>`
    - Bug: If there were multiple values equal to the lowest value, the faulty code would remove all of them instead of just one. To fix this, we can simply add all of the values then subtract the lowest.
    - The array in the example above contains two doubles of the lowest value of 1.5. They are both subtracted from the total, resulting in a calculated average of 1.25.
    ---
2. - Failure-inducing input:
        ```
        @Test
            public void testFilter() {
                List<String> list1 = new ArrayList<>();
                list1.add("A");
                list1.add("a");
                list1.add("B");
                list1.add("b");
                List<String> expected1 = new ArrayList<>();
                expected1.add("A");
                expected1.add("a");
                assertEquals(expected1, ListExamples.filter(list1, new AFinder()));
            }
        ```
   - Symptom: `expected:<[A, a]> but was:<[a, A]>`
   - Bug: New entries to the list should be added to the end instead of the front
   - The actual output was in the reverse order of the expected output because the second value `a` was added to the front of the list instead of the back.