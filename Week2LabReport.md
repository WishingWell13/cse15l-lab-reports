#### Failure inducing input:
```
@Test
  public void testReversedLongArr() {
    int[] input1 = { 5, 9, 13};
    assertArrayEquals(new int[]{ 13, 9, 5}, ArrayExamples.reversed(input1));
  }

```
