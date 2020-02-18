# Learn Go

# Demo1 - Hello World
https://play.golang.org/p/mHIEl2BLCxl

```
package main

import (
	"fmt"
)

func main() {
	fmt.Println("Hello World!")
}
```

# Demo2 - String Variables
https://play.golang.org/p/dkiM_uDsmjV

```
package main

import (
	"fmt"
)

var (
	Name1 string = "global1"
	Name2 string = "global2" 
)

var var1, var2 string = "local1", "local2"

func main() {
	var name1 string
	var name2 string = "CloudAcademy"
	name3 := "DevOps 2020"
	name4 := name2 + " " + name3

	fmt.Println(name1) //prints empty string
	name1 = "Blah"
	fmt.Println(name1) //prints Blah

	fmt.Println(name2)
	fmt.Println(name3)
	fmt.Println(name4)
	
	fmt.Printf("%v -- %v\n", name2, name3)	
	
	fmt.Println(Name1, Name2, var1, var2)
}
```

# Demo3 - Integer Variables
https://play.golang.org/p/22RthR5k6nH

```
package main

import (
	"fmt"
)

func main() {
	var count1 int
	var count2 int = 100
	count3 := 200
	count4 := count2 + count3

	fmt.Println(count1) //prints 0
	count1 = 10
	fmt.Println(count1) //prints 10

	fmt.Println(count2)
	fmt.Println(count3)
	fmt.Println(count4)
	
	count3++
	count4--
	
	fmt.Println(count3)
	fmt.Println(count4)	
}
```

# Demo4 - Boolean Variables
https://play.golang.org/p/laJJ0IhK94V

```
package main

import (
	"fmt"
)

func main() {
	var isBig bool //defaults to false
	var isFast, hasFourWheels bool = false, true

    	fmt.Println(isBig)
    	fmt.Println(isFast)
	fmt.Println(hasFourWheels)
	
	fmt.Println(!hasFourWheels)	
	fmt.Println(isFast && hasFourWheels)
    	fmt.Println(isFast || hasFourWheels)
	
	if !isFast {
		fmt.Println("its slow!")
	}
	
	if hasFourWheels {
		fmt.Println("its a car!")
	}
}
```

# Demo5 - Constants
https://play.golang.org/p/wbNrNsk2YPd

```
package main

import (
	"fmt"
)

//const maxValue //compile error

const population int = 10000

func main() {	
	const name = "CloudAcademy"
	
	//name = "Blah" //compile error
	
	if true {
		const color = "red"

		fmt.Println(population)
		fmt.Println(name)
	}
	
	//fmt.Println(color) //compile error
}
```

# Demo6 - Control Flow - If
https://play.golang.org/p/Fh4P5owNjvZ

```
package main

import (
	"fmt"
)

func main() {
	var population int = 5500

	if population < 5000 {
		fmt.Println("small")
	} else if population >= 5000 && population < 7000 {
		fmt.Println("medium")
	} else {
		fmt.Println("large")
	}
	
	if toggle := true; toggle {
		fmt.Println("its on!")
	}
}
```

# Demo7 - Control Flow - For
https://play.golang.org/p/VFlocHBszR9

```
package main

import "fmt"

func main() {
	x := 0
	y := 0

	for {
		if x++; x > 2 {
			fmt.Println(x)
			break
		}
	}

	for y < 3 {
		fmt.Println(y)
		y++
	}

	for z := 0; z < 10; z++ {
	 	if z < 8 {
			continue
		}
		fmt.Println(z)
	}
}
```

# Demo8 - Control Flow - Switch
https://play.golang.org/p/fQVXeX4JPKR

```
package main

import (
	"fmt"
)

func main() {
	switch signal := 1; signal {
	case 0:
		fmt.Println("reg")
	case 1:
		fmt.Println("orange")
	case 2:
		fmt.Println("green")
	}

	var score int = 63

	switch {
	case score <= 25:
		fmt.Println("beginner")
	case score <= 75:
		fmt.Println("pro")
	default:
		fmt.Println("expert")
	}
}
```

# Demo9 - Arrays
https://play.golang.org/p/RbQu19MJ3Rl

```
package main

import "fmt"

func main() {
	var arr1[4]int //init with 0s
	arr2 := [...]int{3, 1, 5, 10, 100} //compiler infers size of array
	fmt.Println(arr1)
	fmt.Println(arr2) 

	fmt.Println(len(arr1)) //4
	fmt.Println(len(arr2)) //5
	
	for _, value := range arr2 {
		fmt.Println(value)
	}
	
	arr1[0] = 10 //setting
	// arr1[4] = 1 // compile error - out of bounds
	
	fmt.Println(arr1)
	fmt.Println(arr1[0]) //getting
	
	//multidimensional
	arr3 := [2][2]string{
		{"a1", "a2"},
		{"b1", "b2"},	//trailing comma is mandatory
	}
		
	fmt.Println(arr3)
}
```

# Demo10 - Slices
https://play.golang.org/p/HhYSSY0HsUP

```
package main

import "fmt"

func main() {
	arr1 := [6]int{1, 3, 5, 7, 11, 13}
	slice1 := []int{1, 3, 5, 7, 11, 13}
	slice2 := slice1[1:2]
	var slice3 = make([]int, 2,3)
	
	fmt.Println(arr1)
	fmt.Println(slice1)
	fmt.Println(slice2)
	fmt.Println(slice3)
	
	slice3 = slice1[1:4]
		
	fmt.Println(slice3)
	fmt.Println(len(slice3))
	
	slice1 = append(slice1, 200, 300, 400)
	fmt.Println(slice1)
	
	slice2 = append(slice2, []int{7, 8, 9}...)
	fmt.Println(slice2)
	
	copyslice := make([]int, len(slice1))
    	copy(copyslice, slice1)
	fmt.Println(copyslice)
}
```

# Demo11 - Maps
https://play.golang.org/p/m4Rb7FMlMWm

```
package main

import "fmt"

type player struct {
	id int
	rank int
}

func main() {
	map1 := make(map[string]string)
	map1["key1"] = "value1"
	map1["key2"] = "value2"
	map1["key3"] = "value3"
	fmt.Println(map1)

	value1 := map1["key1"]
	fmt.Println(value1)

	//map1["key1"] = 10 //compile error
	map1["key1"] = "value1.1"
	delete(map1, "key2")
	map1["newkey"] = "value4"
	fmt.Println(map1)

	team := map[string]player{"John": {3, 10}, "Bob": {14, 11}}

	fmt.Println(team)
}
```

# Demo12 - Range
https://play.golang.org/p/dkcKKqVsPAz

```
package main

import "fmt"

type player struct {
	id   int
	rank int
}

func main() {	
	bytes := []int{67, 108, 111, 117, 100, 65, 99, 97, 100, 101, 109, 121}
	for idx, value := range bytes {
		fmt.Print(string(value))
		if len(bytes)-1 == idx {
			fmt.Println()
		} 
	}

	team := map[string]player{"John": {3, 10}, "Bob": {14, 11}}
	fmt.Println(team)

	for key, value := range team {
		fmt.Printf("%s -> %d\n", key, value)
	}

	for _, value := range team {
		fmt.Println(value)
	}

	for key := range team {
		fmt.Println("key:", key)
	}
}
```

# Demo13 - Functions1
https://play.golang.org/p/M3uE4qcghof

```
package main

import "fmt"

func sum(num1 int, num2 int) int {
	result := num1 + num2
	return result
}

func minus(num1, num2 int) (result int) {
	result = num1 - num2
	return
}

func main() {
	fmt.Println(sum(1, 2))
	fmt.Println(minus(10, 2))

	result := func(num1 int, num2 int) int {
		sum := sum(num1, num2)
		minus := minus(num1, num2)
		return sum * minus
	}(5, 3)

	fmt.Println(result)
}
```

# Demo14 - Functions2
https://play.golang.org/p/s6oqvLIt0Fu

```
package main

import "fmt"

func displayCount(id int, letters ...string) {
	count := 0
	for range letters {
		count++
	}

	//display id, letters count, letters type, and letters content
	fmt.Printf("%d - %d - %T - %s\n", id, count, letters, letters)
}

func main() {
	displayCount(1, "c", "l", "o", "u", "d")
	displayCount(2, "a", "c", "a", "d", "e", "m", "y")
	
	cloud := []string{"d", "e", "v", "o", "p", "s"}
	displayCount(3, cloud...)
}
```

# Demo15 - Functions3
https://play.golang.org/p/4m7ycYNhgHW

```
package main

import "fmt"
import "errors"

func divide(num1 int, num2 int) (int, error) {
	if num2 == 0 {
		return 0, errors.New("division by zero not allowed")
	} else {
		return (num1 / num2), nil
	}
}

func main() {	
	if result, err := divide(10, 2); err != nil {
		fmt.Println(err)
	} else {
		fmt.Println(result)
	}
}
```

# Demo16 - Functions4
https://play.golang.org/p/bF6tTSjD9Hj

```
package main

import "fmt"

func extend(val string) func() string {
	i := 0
	return func() string {
		i++
		return val[:i]
	}
}

func main() {
	ca := "cloudacademy"
	
	word := extend(ca)

	for i := 0; i < len(ca); i++ {
		fmt.Println(word())
	}
}
```

# Demo17 - Structs
https://play.golang.org/p/JVqtTjr-paO

```
package main

import "fmt"

type person struct {
	firstname string
	surname   string
}

type lecture struct {
	name       string
	instructor person
	duration   int //seconds
}

func main() {
	lectures := []lecture{
		lecture{"Structs", person{"Jeremy", "Cook"}, 300},
		lecture{"Pointers", person{"Jeremy", "Cook"}, 300},
		lecture{"Functions", person{"Jeremy", "Cook"}, 300},
	}

	for _, lecture := range lectures {
		name := lecture.name
		instructor := fmt.Sprintf("%s %s",
			lecture.instructor.firstname,
			lecture.instructor.surname)
		duration := lecture.duration

		fmt.Printf("Lecture: '%s', Author: %s, Duration: %d secs\n", name, instructor, duration)
	}

}
```

# Demo18 - Pointers1
https://play.golang.org/p/9E__12qzYLx

```
package main

import "fmt"

func main() {
	var num1 int = 100
	var num2 int = 200
	var str1 string = "blah"

	var ptr1 *int = &num1
	//var ptr1 *int = &str1 //compile error

	fmt.Printf("mem address of num1 is %p\n", &num1)
	fmt.Printf("mem address of num2 is %p\n", &num2)
	fmt.Printf("mem address of str1 is %p\n", &str1)

	fmt.Printf("ptr1 points to mem address %p\n", ptr1)

	*ptr1 = 101
	fmt.Println(num1)

	ptr1 = &num2
	fmt.Printf("ptr1 points to mem address %p\n", ptr1)
	fmt.Println(*ptr1)
	
	ptr2 := new(int)
	ptr2 = ptr1
	fmt.Println(*ptr2)
}
```

# Demo19 - Pointers2
https://play.golang.org/p/pjvwKMhfoFq

```
package main

import "fmt"

func notString(msg string) {
	msg = fmt.Sprintf("not%s", msg)
}

func notStringPtr(msg *string) {
	*msg = fmt.Sprintf("not%s", *msg)
}

func main() {
	message := "cloudacademy"

	notString(message)
	fmt.Println(message)

	notStringPtr(&message)
	fmt.Println(message)
}
```

# Demo20 - Methods - Structs
https://play.golang.org/p/L8p6DdQAukd

```
package main

import "fmt"

type person struct {
	firstname string
	surname   string
	age       int
}

func (p *person) fullname() string {
	return p.firstname + " " + p.surname
}

func (p *person) canDrive() bool {
	if p.age >= 20 {
		return true
	} else {
		return false
	}
}

func (p *person) updateAge(newAge int) {
	p.age = newAge
}

func main() {
	person1 := person{"John", "Doe", 40}
	person2 := person{"Mark", "Doe", 19}

	fmt.Printf("%s can drive: %t\n", person1.fullname(), person1.canDrive())
	fmt.Printf("%s can drive: %t\n", person2.fullname(), person2.canDrive())
	
	person2.updateAge(person2.age + 1) //marks birthday
	fmt.Println(person2.age)

	fmt.Printf("%s can drive: %t\n", person2.fullname(), person2.canDrive())
}
```

# Demo21 - Methods - Non-Struct
https://play.golang.org/p/QCfTXx7TywI

```
package main

import "fmt"
import "strings"

type upstring string

func (msg upstring) up() string {
	s := string(msg)
	return strings.ToUpper(s)
}

func main() {
	message := upstring("cloudacademy")
	fmt.Println(message.up())
}
```

# Demo22 - Interfaces
https://play.golang.org/p/pbd99cSr9zA

```
package main

import "fmt"

type device interface {
	turnOn() string
}

type iphone struct {
	name string
	model string
}

type imac struct {
	name string
	model string
}

func (phone iphone) turnOn() string {
	return "iOS starting up..."
}

func (mac imac) turnOn() string {
	return "macOS starting up..."
}

func main() {
	dev1 := iphone{"iPhone", "11 Pro"}
	dev2 := imac{"iMac", "27 5k Retina"}
	
	devices := []device{dev1, dev2}

	for _, dev := range devices {
		fmt.Println(dev.turnOn())
	}
}
```

# Demo23 - Interfaces with Pointer based Receivers
https://play.golang.org/p/bE6VdTNCuNu

```
package main

import "fmt"
import "strings"

type device interface {
	turnOn() string
	update(version float32)
}

type iphone struct {
	name    string
	model   string
	version float32
}

type imac struct {
	name    string
	model   string
	version float32
}

func (phone iphone) turnOn() string {
	return "iOS starting up..."
}

func (mac imac) turnOn() string {
	return "macOS starting up..."
}

func (phone *iphone) update(version float32) {
	phone.version = version
}

func (mac *imac) update(version float32) {
	mac.version = version
}

func main() {
	dev1 := iphone{"iPhone", "11 Pro", 13.1}
	dev2 := imac{"iMac", "27 5k Retina", 10.15}

	devices := []device{&dev1, &dev2}

	for _, dev := range devices {
		if strings.Contains(dev.turnOn(), "iOS") {
			dev.update(14.0)
		} else if strings.Contains(dev.turnOn(), "macOS") {
			dev.update(11.00)
		}
	}
	
	fmt.Println(dev1)
	fmt.Println(dev2)	
}
```

# Demo24 - Errors
https://play.golang.org/p/LskHt_O2E16

```
package main

import "fmt"
import "errors"
import "math"

func circleArea(radius float32) (float32, error) {
	if radius < 0 {
		return 0, errors.New("radius should be positive value")
	} else {
		return math.Pi * radius * radius, nil
	}
}

func main() {
	area1, _ := circleArea(3)
	fmt.Println(area1)

	if area2, err := circleArea(-3); err != nil {
		fmt.Println(err)
	} else {
		fmt.Println(area2)
	}
}
```

# Demo25 - Defer
https://play.golang.org/p/kkyusUwavPD

```
package main

import "fmt"

func doSomething(msg string) {
	fmt.Println(msg)
}

func system() int {
	fmt.Println("system started...")

	defer doSomething("cleanup")
	defer doSomething("stop")
	
	fmt.Println("system finished!")

	return 1
}

func main() {
	data := system()
	fmt.Println(data)
}
```

# Demo26 - Panic/Recover
https://play.golang.org/p/9_Te0w76C2N

```
package main

import "fmt"

func system() int {
	fmt.Println("system started...")	

	defer func(msg string) {
		if r := recover(); r != nil {
			fmt.Println("recovered")	
		}
		fmt.Println(msg)
	}("blah")

	var data []int
	var x = data[0] //causes runtime spanic!
	x++
	
	fmt.Println("system finished!")

	return 1
}

func main() {
	data := system()
	fmt.Println(data)
	
	panic("die!") //exits program with non-zero code
}
```

# Demo27 - Goroutine1
https://play.golang.org/p/8acvr_AJdgx

```
package main

import (
	"fmt"
	"math/rand"
	"time"
)

func pause() {
	n := rand.Intn(3) // n will be between 0 and 3
	time.Sleep(time.Duration(n) * time.Second)
}

func doSomething(msg string) {
	pause()
	fmt.Println(msg)
}

func main() {
	rand.Seed(time.Now().Unix())

	doSomething("sync1")

	go doSomething("async1")
	go doSomething("async2")
	go doSomething("async3")

	doSomething("sync2")
	
	time.Sleep(time.Second * 10)
}
```

# Demo28 - Goroutine2
https://play.golang.org/p/OjARMSo9w30

```
package main

import (
	"fmt"
	"sync"
)

func main() {
	var wg sync.WaitGroup
	
	wg.Add(1)
	go func(msg string) {
		defer wg.Done()
		fmt.Println(msg)
	}("cloud")

	wg.Add(1)
	go func(msg string) {
		defer wg.Done()
		fmt.Println(msg)
	}("academy")

	wg.Wait()
}
```

# Demo29 - Channels
https://play.golang.org/p/YJuyrFDWd_r

```
package main

import "fmt"

func main() {
	msgChan := make(chan string)

	go func() {	
		msgChan <- "Cloud"
		msgChan <- "Academy"
		msgChan <- "2020"
	}()

	msg1 := <-msgChan
	msg2 := <-msgChan
	msg3 := <-msgChan
	
	fmt.Println(msg1, msg2, msg3)
}
```

# Demo30 - Channel Buffers
https://play.golang.org/p/m4U5yWf6yKu

```
package main

import "time"

func main() {
	size := 3
	var buffChan = make(chan int, size)

	//reader
	go func() {
		for {
			_ = <-buffChan
			time.Sleep(time.Second)
		}
	}()

	//writer
	writer := func() {
		for i := 1; i <= 10; i++ {
			buffChan <- i
			println(i)
		}
	}

	writer()
}
```

# Demo 31 - Channel Directions
https://play.golang.org/p/onPjCfofMay

```
package main

import (
	"fmt"
	"time"
)

func in(channel chan<- string, msg string) {
 	channel <- msg
}

func out(channel <-chan string) {
	for {
		fmt.Println(<-channel)
	}
}

func main() {
	channel := make(chan string, 1)

	go out(channel)

	for i := 0; i < 10; i++ {
		in(channel, fmt.Sprintf("cloudacademy - %d", i))
	}

	time.Sleep(time.Second * 10) //crude
}
```

# Demo 32 - Channel Select
https://play.golang.org/p/csPU3qa80Gl

```
package main

import "fmt"
import "math/rand"
import "time"

func pause() {
	n := rand.Intn(5) // n will be between 0 and 5
	time.Sleep(time.Duration(n) * time.Second)
}

func func1(c chan<- string) {
	for {
		pause()
		c <- "cloud"
	}
}

func func2(c chan<- string) {
	for {
		pause()
		c <- "academy"
	}
}

func main() {
	rand.Seed(time.Now().Unix())

	chan1 := make(chan string)
	chan2 := make(chan string)

	go func1(chan1)
	go func2(chan2)

	for {
		select {
		case msg1 := <-chan1:
			fmt.Println(msg1)
		case msg2 := <-chan2:
			fmt.Println(msg2)
		}
	}
}
```

# Demo 33 - Channel Timeout
https://play.golang.org/p/Zovrizw2ovR

```
package main

import "fmt"
import "time"

func main() {
	channel := make(chan string)

	go func(channel chan string) {
		time.Sleep(5 * time.Second)
		channel <- "cloudacademy"

	}(channel)

	select {
	case msg1 := <-channel:
		fmt.Println(msg1)
	case <-time.After(2 * time.Second):
		fmt.Println("Timeout!")
	}
}
```

# Demo 34 - Channel Close
https://play.golang.org/p/A5PbNcJ9xM0

```
package main

import (
	"bytes"
	"fmt"
)

func process(work <-chan string, fin chan<- string) {
	var b bytes.Buffer
	for {		
		if msg, closed := <-work; closed {
			fmt.Printf("%s received...\n", msg)
			b.WriteString(msg)
		} else {
			fmt.Println("channel closed")
			fin <- b.String()
			return
		}
	}
}

func main() {
	work := make(chan string, 3)
	fin := make(chan string)

	go process(work, fin)

	word := "cloudacademy"

	for j := 0; j < len(word); j++ {
		letter := string(word[j])
		work <- letter
		fmt.Printf("%s sent...\n", letter)
	}

	close(work)
	
	fmt.Printf("result: %s", <-fin)
}
```

# Demo 35 - Channel Range
https://play.golang.org/p/-tvLMccbwgy

```
package main

import "fmt"

func squares() func() int {
    var x int
    return func() int {
        x++
        return x * x
    }
}

func main() {
	f := squares()
	squares := make(chan int, 20)

	for i := f(); i <= 100; i = f() {
		squares <- i
	}

	close(squares)

	for elem := range squares {
		fmt.Println(elem)
	}

}
```

# Demo36 - Type Assertions - TypeSwitch
https://play.golang.org/p/a94y6GfO24R

```
package main

import "fmt"

type cloud interface {
	launch() string
}

type aws struct {
	computeSvcName string
}

type azure struct {
	computeSvcName string
}

func (cloud aws) launch() string {
	return fmt.Sprintf("%s launching instance...", cloud.computeSvcName)
}

func (cloud azure) launch() string {
	return fmt.Sprintf("%s launching virtual machine...", cloud.computeSvcName)
}

func compute(cloud interface{}) {
	switch cloudplatform := cloud.(type) {
	case aws:
		aws := cloud.(aws) //casting
		fmt.Printf("AWS: %s -> %s\n", aws, cloudplatform.launch()) //polymorphism
		break
	case azure:
		azure := cloud.(azure) //casting
		fmt.Printf("Azure: %s -> %s\n", azure, cloudplatform.launch()) //polymorphism
		break
	}
}

func main() {
	var clouds []cloud = []cloud{
		aws{"ec2"}, azure{"vm"},
	}

	for _, cloud := range clouds {
		compute(cloud)
	}

}
```

# Demo37 - Empty Interface
https://play.golang.org/p/RbGCSElwj9X

```
package main

import "fmt"

type company struct {
	name string
}

func main() {
	var a, b, c, d interface{}

	a = 42
	b = "blah"
	c = true
	d = company{"cloudadacademy"}

	func(list ...interface{}) {
		for _, v := range list {
			fmt.Printf("%v, %T\n", v, v)
		}

	}(a, b, c, d)
}
```

# Demo38 - Type Assertions
https://play.golang.org/p/8QVbrPMxwh4

```
package main

import "fmt"

type company struct {
	name string
}

func main() {
	var x interface{} = company{"CloudAcademy"}

	c1 := x.(company)
	fmt.Println(c1)

	if c2, ok := x.(company); ok {
		fmt.Println(c2, ok)
	}

	//n := x.(int); n++ //runtime panic
}
```

# Demo39 - Scope 1
https://play.golang.org/p/8S4HuOfI8SI

```
-- util.go --
package main

var x int = 11

-- main.go --
package main

import "fmt"

func print(id int, x int) {
	fmt.Printf("%d: x=%d\n", id, x)
}

func main() {
	print(1, x)
	
	x := 2

	print(2, x)

	func(x int){
		print(3, x)
		if x := 3; x < 10 {
			//x := 100
			print(4, x)
		}
		print(5, x)
	}(5)
	
	print(6, x)
}
```

# Demo40 - Imports
https://play.golang.org/p/_ewOM7JU8_K

```
package main

import (
	"fmt"
	"strings"
	"github.com/google/uuid"
)

import "strconv"
import m "math"

func main() {
	name := "cloudacademy"
	
	fmt.Println(strings.ToUpper(name))
	fmt.Println(uuid.New())
	f, _ := strconv.ParseFloat("3.1415", 64)
	fmt.Println(f)
	fmt.Println(m.Round(f))
}
```

# Demo41 - Exports/Imports
https://play.golang.org/p/Kmvd8-dNXMh

```
-- go.mod --
module github.com/cloudacademy/go/mod/demo

-- util/x.go --
package util

const X int = 100 //exported
const x int = 200 //unexported

//exported
func GetX() int {
	return x
}

//unexported
func getX() int {
	return x
}

-- main.go --
package main

import (
	"github.com/cloudacademy/go/mod/demo/util"
	"fmt"
)

func main() {
	fmt.Println(util.X)
	//fmt.Println(util.x) //compile failure - unexported

	fmt.Println(util.GetX())
	//fmt.Println(util.getX()) //compile failure - unexported

}
```

# Demo42 - Package Visibility
https://play.golang.org/p/2xzo2Ho9XiU

```
-- go.mod --
module github.com/cloudacademy/go/mod/demo

-- util/x.go --
package util

const X int = 100 //exported
const x int = 200 //unexported

//exported
func GetX() int {
	return x
}

//exported
func GetXY() int {
	return x * getY() //visible due to being in same package
}

-- util/y.go --
package util

const y int = 300 //unexported

//unexported
func getY() int {
	return y
}

-- main.go --
package main

import (
	"github.com/cloudacademy/go/mod/demo/util"
	"fmt"
)

func main() {
	fmt.Println(util.GetXY())
	
	//fmt.Println(util.getY()) //compile failure - unexported
}
```

# Demo43 - Modules1
https://play.golang.org/p/PZlq49vz59r

```
-- go.mod --
module github.com/cloudacademy/go

require github.com/google/uuid v1.1.1

-- util/x.go --
package util

const x int = 100 //unexported

//exported
func GetX() int {
	return x
}

-- util/y.go --
package util

const y int = 200 //unexported

//exported
func GetY() int {
	return y
}

-- math/calc.go --
package math

import "github.com/google/uuid"

//exported
func Add(num1 int, num2 int) int {
	return num1 + num2
}

func GetUuid() uuid.UUID {
	return uuid.New()
}

-- main.go --
package main

import (
	"fmt"
	"github.com/cloudacademy/go/util"
	"github.com/cloudacademy/go/math"
)

func main() {
	x := util.GetX()
	y := util.GetY()

	fmt.Println(x)
	fmt.Println(y)

	sum := math.Add(x, y)
	uuid := math.GetUuid()

	fmt.Println(sum)
	fmt.Println(uuid)
}
```
