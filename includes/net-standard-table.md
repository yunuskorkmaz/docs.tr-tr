| .NET Standard              | [1.0]  | [1.1]  | [1.2] | [1.3] | [1.4] | [1.5]              | [1.6]              | [2.0]               |
|----------------------------|--------|--------|-------|-------|-------|--------------------|--------------------|---------------------|
| .NET Core                  | 1.0    | 1.0    | 1.0   | 1.0   | 1.0   | 1.0                | 1.0                | 2,0                 |
| .NET framework <sup>1</sup>| 4,5    | 4,5    | 4.5.1 | 4.6   | 4.6.1 | 4.6.1 <sup>2</sup> | 4.6.1 <sup>2</sup> | 4.6.1 <sup>2</sup>  |
| Mono                       | 4.6    | 4.6    | 4.6   | 4.6   | 4.6   | 4.6                | 4.6                | 5,4                 |
| Xamarin.iOS                | 10.0   | 10.0   | 10.0  | 10.0  | 10.0  | 10.0               | 10.0               | 10.14               |
| Xamarin.Mac                | 3.0    | 3.0    | 3.0   | 3.0   | 3.0   | 3.0                | 3.0                | 3.8                 |
| Xamarin.Android            | 7.0    | 7.0    | 7.0   | 7.0   | 7.0   | 7.0                | 7.0                | 8.0                 |
| Evrensel Windows Platformu | 10.0   | 10.0   | 10.0  | 10.0  | 10.0  | 10.0.16299         | 10.0.16299         | 10.0.16299          |
| Unity                      | 2018.1 | 2018.1 | 2018.1| 2018.1| 2018.1| 2018.1             |  2018.1            | 2018.1              |

<sup>1 .NET Framework için listelenen sürümleri, .NET Core 2.0 SDK'sını ve Araçları'nın sonraki sürümleri için geçerlidir. Eski sürümleri ve üzeri için .NET standart 1.5 farklı bir eşlemeyle kullanılır. Yapabilecekleriniz [Visual Studio 2015 için .NET Core araçları için araç kullanımı indir](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md) , Visual Studio 2017'ye yükseltemezsiniz.</sup>

<sup>2 burada listelenen sürümlerinde, belirli bir .NET Standard kitaplığı geçerli olup olmadığını belirlemek için NuGet kullandığı kurallarını temsil eder. NuGet 2.0 .NET standart 1.5 destekleyen olarak .NET Framework 4.6.1 olarak kabul eder, ancak .NET Framework 4.6.1 projelerinden sürümler için oluşturulmuş .NET standart kitaplıkları kullanma ile birkaç sorun vardır. Bu tür kitaplıklarını kullanması gereken .NET Framework projeleri için proje hedef .NET Framework 4.7.2 yükseltme olan öneririz veya üzeri.</sup>

- Sütunlar .NET Standard sürümleri temsil eder. Her üst bilgi hücresini hangi API'ler .NET Standard'ın bu sürümünde eklenen gösteren bir belgeye bir bağlantıdır.
- Satırları, farklı .NET uygulamalarını temsil eder.
- Her hücredeki sürüm numarasını gösterir *minimum* , .NET Standard sürümünü hedeflemek için ihtiyaç duyacağınız uygulama sürümü.
- Etkileşimli bir tablo için bkz: [.NET Standard sürümleri](https://immo.landwerth.net/netstandard-versions/#).

[1.0]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.0.md
[1.1]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.1.md
[1.2]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.2.md
[1.3]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.3.md
[1.4]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.4.md
[1.5]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.5.md
[1.6]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.6.md
[2.0]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.0.md
