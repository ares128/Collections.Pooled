``` ini

BenchmarkDotNet=v0.11.3, OS=Windows 10.0.17763.288 (1809/October2018Update/Redstone5)
Intel Core i7-6700HQ CPU 2.60GHz (Skylake), 1 CPU, 8 logical and 4 physical cores
.NET Core SDK=3.0.100-preview-009812
  [Host] : .NET Core 2.2.1 (CoreCLR 4.6.27207.03, CoreFX 4.6.27207.03), 64bit RyuJIT
  Core   : .NET Core 2.2.1 (CoreCLR 4.6.27207.03, CoreFX 4.6.27207.03), 64bit RyuJIT

Job=Core  Runtime=Core  

```
|      Method |     N |          Mean |         Error |        StdDev | Ratio | RatioSD | Gen 0/1k Op | Gen 1/1k Op | Gen 2/1k Op | Allocated Memory/Op |
|------------ |------ |--------------:|--------------:|--------------:|------:|--------:|------------:|------------:|------------:|--------------------:|
|   **Dict_Ctor** |     **0** |      **51.78 us** |     **1.0257 us** |     **1.6852 us** |  **1.00** |    **0.00** |    **114.6240** |           **-** |           **-** |           **352.27 KB** |
| Pooled_Ctor |     0 |      53.85 us |     0.3998 us |     0.3739 us |  1.03 |    0.03 |    126.0986 |           - |           - |           387.49 KB |
|             |       |               |               |               |       |         |             |             |             |                     |
|   **Dict_Ctor** |  **1024** |   **5,654.07 us** |   **112.0177 us** |   **157.0332 us** |  **1.00** |    **0.00** |  **44203.1250** |           **-** |           **-** |        **136573.38 KB** |
| Pooled_Ctor |  1024 |   1,360.45 us |    26.5733 us |    26.0986 us |  0.24 |    0.01 |    125.0000 |           - |           - |           387.49 KB |
|             |       |               |               |               |       |         |             |             |             |                     |
|   **Dict_Ctor** |  **4096** |  **57,574.39 us** |   **798.0005 us** |   **746.4501 us** |  **1.00** |    **0.00** | **166888.8889** | **166888.8889** | **166888.8889** |        **599908.36 KB** |
| Pooled_Ctor |  4096 |   4,068.74 us |     7.7625 us |     6.8812 us |  0.07 |    0.00 |    125.0000 |           - |           - |           387.49 KB |
|             |       |               |               |               |       |         |             |             |             |                     |
|   **Dict_Ctor** | **16384** | **152,831.09 us** | **2,883.3070 us** | **2,697.0471 us** |  **1.00** |    **0.00** | **563500.0000** | **563500.0000** | **563500.0000** |       **2160550.76 KB** |
| Pooled_Ctor | 16384 |  11,889.84 us |    86.1532 us |    71.9419 us |  0.08 |    0.00 |    125.0000 |           - |           - |           387.49 KB |