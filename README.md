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


 
