# studytemplates

# Intent

Towards the end of September, 2022, I receiced a LinkedIn message from Google recruiter for an upcoming Software Engineering role based in Nairobi. 
I wasn't actively looking for new job opportunities at the time, and so you'd guess I wasn't 'Leetcode-ing' much. After a call with my recuiter we decided to
that I take 3 months for preparation. He shared few materials, and could as well check up on me once in awhile to know i was progressing with the preparation.

During my studies, I came to notice something I never noticed before during my previous preparations. Templates. I used to struggle solving Leetcode problems 
in time even when i already solved other related problems before. For me to effectively solve a given set of problem, I had to visit them regularly to keep the
partern fresh in my memomry. Even though the strategy worked somehow, we can both agree that its not only time consuming but its an ineffective way of studying. 
 
Having a general approach i.e template can reduce the amount spent for coding your solution. 
I decided to follow though while documenting various reusable templates for given sets of problems. I remain work in progress, but I will continue documenting 
templates 

# Sliding Window 

###  1. Shrinkable window

```

  int start = 0, end = 0, length = 0;
  
  for(; end < n; end++){
  
    /*
    CODE Block for valid condition
    
    */
    
    
    while( /* condition not true */){
      start++
    }
  
    length = max(length, end-start+1)
  
  }
```

Links to solutions solved with the template 

[Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/solutions/3392671/java-sliding-window-two-pointers-beats-9881-4ms/) 

[Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/solutions/3392443/java-sliding-window-beats-9996-3ms/)

[Subarray Product Less Than K](https://leetcode.com/problems/subarray-product-less-than-k/solutions/3396821/java-sliding-window-beats-97-48/)

[Max Consecutive Ones III](https://leetcode.com/problems/max-consecutive-ones-iii/solutions/3396842/java-sliding-window-beats-99-94-2ms/)

###   2. Non Shrinkable Window

```

  int start = 0, end = 0, length = 0;
  
  for(; end < n; end++){
  
    /*
    CODE Block for valid condition. When max win not reached yet
    
    */
    
    
    if( /* condition not true */){
      start++
    }
  
    length = max(length, end-start+1)
  
  }
```




#  Prefix Sum

These set of problems are solved in linear time using a pre culculated, running sum. Generally, Hashmap is used to calculate the running `sum`
Can be confusing on when to use as they are related to Sliding window. 
Question format 
  - k diff
  - How many subarrays with K
  - How many pairs
  
  
 #### 1 How many subarrays | K diff
 
 
 ```
 
 Map<Integer, Integer> map = new HashMap<>(); // Keeping frequency counter of seen key
 
 map.put(0, 1); //Edge case . to take care of when the 0th num is part of the running sum
 
 int  res = 0;
 
 for(int num: nums){
    // key CODE eg, running sum
    
    res += map.getOrDefault(key, 0); // add freq to the result if we have seen 'key' in our map before, otherwise 0
    map.put(key, map.getOrDefault(key, 0)+1);
 }
 
 
 ```
 
 [560. Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/description/)
 
 [974. Subarray Sums Divisible by K](https://leetcode.com/problems/subarray-sums-divisible-by-k/description/)
 
 
 
  
 #### 2 How many pairs
 
 
  
 ```
 
 Map<Integer, Integer> map = new HashMap<>(); // Keeping frequency counter of seen key
  
 int  res = 0;
 
 for(int num: nums){
    // key CODE eg, running sum query
    
    res += map.getOrDefault(key, 0); // add freq to the result if we have seen 'key' in our map before, otherwise 0
    map.put(key, map.getOrDefault(key, 0)+1);
 }
 
 ```
Example of problems 

[2364. Count Number of Bad Pairs](https://leetcode.com/problems/count-number-of-bad-pairs/description/)

[1814. Count Nice Pairs in an Array](https://leetcode.com/problems/count-nice-pairs-in-an-array/description/)

[2001. Number of Pairs of Interchangeable Rectangles](https://leetcode.com/problems/number-of-pairs-of-interchangeable-rectangles/)


```
2001. Number of Pairs of Interchangeable Rectangles

You are given n rectangles represented by a 0-indexed 2D integer array rectangles, where rectangles[i] = [widthi, heighti] denotes the width and height of the ith rectangle.

Two rectangles i and j (i < j) are considered interchangeable if they have the same width-to-height ratio. More formally, two rectangles are interchangeable if widthi/heighti == widthj/heightj (using decimal division, not integer division).

Return the number of pairs of interchangeable rectangles in rectangles.

 

Example 1:

Input: rectangles = [[4,8],[3,6],[10,20],[15,30]]
Output: 6
Explanation: The following are the interchangeable pairs of rectangles by index (0-indexed):
- Rectangle 0 with rectangle 1: 4/8 == 3/6.
- Rectangle 0 with rectangle 2: 4/8 == 10/20.
- Rectangle 0 with rectangle 3: 4/8 == 15/30.
- Rectangle 1 with rectangle 2: 3/6 == 10/20.
- Rectangle 1 with rectangle 3: 3/6 == 15/30.
- Rectangle 2 with rectangle 3: 10/20 == 15/30.
Example 2:

Input: rectangles = [[4,5],[7,8]]
Output: 0
Explanation: There are no interchangeable pairs of rectangles.
```

```
  public long interchangeableRectangles(int[][] rect) {
        Map<Double, Integer> map = new HashMap<>();
        long pairs= 0;

        for(int [] dim: rect ){
            double ration = dim[0]/(double)dim[1];
            pairs += map.getOrDefault(ration, 0);
            map.put(ration, map.getOrDefault(ration, 0)+1);
        }
        return pairs;
        
    }
```
 

# Monotonic Stack

Monotonic means some kind of natural ordering, either non-decreasing or non-increasing. Monotonic stack is a stack data structure with items that are either strictly increasing or decreasing.

The set of problems that **query** the **next greater*** or **next smaller** can be efficiently solved using monostack ds. 

#### Problem form
 - Range of Query in an array 
 - Next greater / Next smaller
 - Minima/Maxima situation
 
 
 
```
- For greater problems, use a monotonically increasing stack (from top to bottom).
- For smaller problems, use a monotonically decreasing stack (from top to bottom).
- For next problems, backwardly iterate through the list and push elements into the stack.
- For previous problems, forwardly iterate through the list.
- For problems with a circular list, iterate through the list twice.
```

### General Template

```



  for(int i = 0; i < n; i++ ){
  
     while(!stack.isEmpty() &&  // Condition that breakes the sequence )
        stack.pop() // maintain the monotony of the stack. 
        
     // add/calculate to result
     
      stack.push(i / A[i])
  } 
  
  
  

```
### Example

[496. Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/solutions/3430335/java-monotonic-stack/)


```
The next greater element of some element x in an array is the first greater element that is to the right of x in the same array.

You are given two distinct 0-indexed integer arrays nums1 and nums2, where nums1 is a subset of nums2.

For each 0 <= i < nums1.length, find the index j such that nums1[i] == nums2[j] and determine the next greater element of nums2[j] in nums2. If there is no next greater element, then the answer for this query is -1.

Return an array ans of length nums1.length such that ans[i] is the next greater element as described above.

 

Example 1:

Input: nums1 = [4,1,2], nums2 = [1,3,4,2]
Output: [-1,3,-1]
Explanation: The next greater element for each value of nums1 is as follows:
- 4 is underlined in nums2 = [1,3,4,2]. There is no next greater element, so the answer is -1.
- 1 is underlined in nums2 = [1,3,4,2]. The next greater element is 3.
- 2 is underlined in nums2 = [1,3,4,2]. There is no next greater element, so the answer is -1

```


#### Solution

As we move from backwards, keep in stack, strictly increasing items in stack. The peek will be the next greate item of the ith value


```
   public int[] nextGreaterElement(int[] nums1, int[] nums2) {

        Map<Integer, Integer> indices = new HashMap<>();
        for(int i = 0; i < nums1.length; i++)
            indices.put(nums1[i], i);

        Stack<Integer> stack = new Stack<>();

        for(int i = nums2.length-1; i > -1; i--){
            while(!stack.isEmpty() && nums2[i] >= stack.peek())
                stack.pop();
            
            if(indices.containsKey(nums2[i]))
                nums1[indices.get(nums2[i])] =  stack.isEmpty() ? -1 : stack.peek();

            stack.push(nums2[i]);

        }
       
        return nums1;
    }
```

#### Other problems

[503. Next Greater Element II](https://leetcode.com/problems/next-greater-element-ii/description/)



 
