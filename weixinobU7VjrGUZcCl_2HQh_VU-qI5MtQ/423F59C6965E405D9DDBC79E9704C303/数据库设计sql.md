 

##### 根据子章节，查询书本
```
SELECT
	* 
FROM
	book_detail 
WHERE
	book_id = ( SELECT book_id FROM book_chapter WHERE chapter_id = 2 )
```

##### 根据书本查询所有章节
```
SELECT
	* 
FROM
	book_chapter 
WHERE
	where book_id = 1
```


##### 根据某个子章节查询章节路径
```
SELECT
	tree_path 
FROM
	book_chapter 
WHERE
	chapter_id = 2
```

##### 根据某个指定章节查询所有子节点
```
SELECT
	* 
FROM
	book_chapter 
WHERE
	tree_path LIKE ( SELECT tree_path FROM book_chapter WHERE chapter_id = 2 ) 
	OR tree_path LIKE CONCAT( ( SELECT tree_path FROM book_chapter WHERE chapter_id = 2 ), "/%" )
```
