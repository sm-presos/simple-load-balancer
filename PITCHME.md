##  ** Simple Loadbalancer ** 
#### in Golang, by smazumder

---?color=linear-gradient(180deg, white 25%, black 75%)
@snap[west span-35 text-07]
Load Balancers have different strategies for distributing the load across a set of backends.
@snapend
@snap[north-east span-60]
@box[bg-purple text-white](Round Robin # distribute load equally, assumes all backends have the same processing power.)
@snapend
@snap[east span-60]
@box[bg-orange text-white](Weighted Round Robin #Additional weights can be given considering the backend’s processing power.)
@snapend
@snap[south-east span-60]
@box[bg-pink text-white](Least Connections #Load is distributed to the servers with least active connections.)
@snapend

---?color=linear-gradient(180deg, white 25%, black 75%)
@title[Customize Slide Layout]

@snap[text-black text-10]
 Main structs for SimpleLoadBalancer
@snapend

```golang
   // Store information about the backend endpoints
    type Backend struct {
    Url             *url.URL
    Alive            bool
    mux             sync.RWMutex
    ReverseProxy    *httputil.ReverseProxy
   }

   const (
    Attempts  int = iota
    Retry
   )   

  // Tracks all the backend endpoints in a slice and has
  // a counter variable
   type ServerPool struct {
      backends    []*Backend
      current     uint64
  }
````
---

@title[Features]

@snap[west]
- Auto-discover backend services using DNS SRV records (common technique in container world)
- Allocate different load following SRV priority and weight
- Pooling TCP connections to backends (reusable)
- Encrypt public traffic with TLS (HTTPS)
- For fun: benchmark it against other popular LBs (in Go)
@snapend
---

@snap[north-east span-100 text-pink text-06]
Let your code do the talking!
@snapend

```sql zoom-18
CREATE TABLE "topic" (
    "id" serial NOT NULL PRIMARY KEY,
    "forum_id" integer NOT NULL,
    "subject" varchar(255) NOT NULL
);
ALTER TABLE "topic"
ADD CONSTRAINT forum_id
FOREIGN KEY ("forum_id")
REFERENCES "forum" ("id");
```

@snap[south span-100 text-gray text-08]
@[1-5](You can step-and-ZOOM into fenced-code blocks, source files, and Github GIST.)
@[6,7, zoom-13](Using GitPitch live code presenting with optional annotations.)
@[8-9, zoom-12](This means no more switching between your slide deck and IDE on stage.)
@snapend


---?image=assets/img/code.jpg&opacity=60&position=left&size=45% 100%

@snap[east span-50 text-center]
## Now It's **Your** Turn
@snapend

@snap[south-east span-50 text-center text-06]
[Download GitPitch Desktop @fa[external-link]](https://gitpitch.com/docs/getting-started/tutorial/)
@snapend

