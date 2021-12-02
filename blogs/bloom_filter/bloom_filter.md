# [02-12-2021] Bloom Filter

Landed into this amazing blog [post](https://michaelnielsen.org/ddi/how-to-crawl-a-quarter-billion-webpages-in-40-hours/) where author explains about crawling a quater billion webpage in 40 hours

In this post author used Bloom Filter to capture if web page is already crawled.


##### What is bloom filter?
- Given an input bloom filter returns if the input is present or not. Or rather bloom filter may return if the key is present or not. This is because bloom filter can return false postivie. More on this later in the post
* In this particular use case where author wanted to store all the web pages already craweled, he is using bloom filter to figure it out.
- Advantage: You dont need lot space to store data, you can have a inmemory datastore. Size of the datastore is known prior in case of bloom filter

##### How does bloom filter works

[Working](/blogs/bloom_filter/Working.png)