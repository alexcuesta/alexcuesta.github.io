---
layout: post
title: "Go: Basic HTTP"
category: programming
tags:
  - go
---

I have created a go-learning project to refresh my knowledge about this language. I created a roadmap with the topics I want to learn. I will push it to Github when it's ready.

My first topic is the basics of HTTP in Go. Super basic stuff. However, in the smallest things we can find the greatest insights.

When handling HTTP requests and responses, it is important to know what exactly we are handling. In this function, for example:

```go
func handler(w http.ResponseWriter, r *http.Request) {
    fmt.Fprintf(w, "Hi, I love %s,  size of w interface:( %T, %v)\n", r.URL.Path[1:], w, w)
}
```

* w is an Interface. What is being passed? Go passes a tuple (value, type) as [explained in Tour of Go about Interfaces](https://go.dev/tour/methods/11)

* r is a pointer to a [Request struct](https://pkg.go.dev/net/http#Request). Why is this a pointer and not a value? To avoid copying large data structures to the stack.




