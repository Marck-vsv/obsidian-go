###### Go (or Golang) is a high-level general purpose programming language with a high performance, which makes it mostly a good choice for:

* Web Development
* Cloud & Network
* DevOps
* CLIs

---

###### Go main aspects

1. Binary executable
	* It doesn't need a runtime interpreter, so a binary can be far slimmer than a nest of directories and sub-directories, which is good for containerisation and orchestration performance.
	* There is no additional runtime need for execution as it's machine code, therefore a binary executable can perform and recover easily
	
2. Minimalist
	* If you already know the basics, you will notice that the language is not overly complex or 'impressive'. It does just enough to get your problem solved.
	
3. Garbage collection
	* Since go is a higher-level language with automatic memory management without intervention you can focus on the more important aspects of your code without worrying much about performance, not everybody like this feature, but we're talking about productivity here.
	
4. Testing and benchmarking
	* Go has plenty of built-in tools for unit-testing and/or benchmarking, so you will likely get familiar with testing and benchmarking setups when collaborating with teams in projects.
	
5. Concurrency
	* There is a good variety of options for dealing with concurrency in Go, such as Goroutine, Channel, Mutex, Waitgroup etc... encouraging patterns that allow parts of your codebase to talk to each other efficiently.
	
6. Low boilerplate
	* Go requires almost no boilerplate code to create substantial applications.
	
7. Networking
	* Go has a dedicated Networking API aimed at network programming built into it's standard library, being part of the external sub-repositories that belong to the Go project.
