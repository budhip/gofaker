# gofaker

Struct Data Fake Generator

Faker  will generate you a fake data based on your Struct.


## Getting Started

#### Download

```shell
go get -u github.com/budhip/gofaker
```
# Example

---

 - Using Struct's tag:  [WithStructTag.md](/WithStructTag.md)
 - Custom Struct's tag (define your own faker data): [CustomFaker.md](/CustomFaker.md)
 - Without struct's tag: [WithoutTag.md](/WithoutTag.md)
 - Single Fake Data Function: [SingleFakeData.md](/SingleFakeData.md)

## Benchmark

---

Bench To Generate Fake Data
#### Without Tag
```bash
BenchmarkFakerDataNOTTagged-4             500000              3049 ns/op             488 B/op         20 allocs/op
```

#### Using Tag
```bash
 BenchmarkFakerDataTagged-4                100000             17470 ns/op             380 B/op         26 allocs/op
```

### MUST KNOW

---

The Struct Field must PUBLIC.<br>
Support Only For :

* int  int8  int16  int32  int64
* []int  []int8  []int16  []int32  []int64
* bool []bool
* string []string
* float32 float64 []float32 []float64
* Nested Struct Field
* time.Time []time.Time

## Limitation

---

Unfortunately this library has some limitation
* It does not support private fields. Make sure your structs fields you intend to generate fake data for are public, it would otherwise trigger a panic. You can however omit fields using a tag skip `faker:"-"` on your private fields.
* It does not support the `interface{}` data type. How could we generate anything without knowing its data type?
* It does not support the `map[interface{}]interface{}, map[any_type]interface{}, map[interface{}]any_type` data types. Once again, we cannot generate values for an unknown data type.
* Custom types are not fully supported. However some custom types are already supported: we are still investigating how to do this the correct way. For now, if you use `faker`, it's safer not to use any custom types in order to avoid panics.
