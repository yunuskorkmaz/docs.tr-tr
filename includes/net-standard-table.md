---
ms.openlocfilehash: 9e95db8a1530fabd30b5344c87728b9210c0ad69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74802836"
---
| .NET Standard              | [1.0]  | [1.1]  | [1.2] | [1.3] | [1.4] | [1.5]              | [1.6]              | [2.0]               | [2.1] |
|----------------------------|--------|--------|-------|-------|-------|--------------------|--------------------|---------------------|---------------------
| .NET Core                  | 1.0    | 1.0    | 1.0   | 1.0   | 1.0   | 1.0                | 1.0                | 2,0                 | 3,0 |
| .NET Çerçeve <sup>1</sup>| 4,5    | 4,5    | 4.5.1 | 4.6   | 4.6.1 | 4.6.1 <sup>2</sup> | 4.6.1 <sup>2</sup> | 4.6.1 <sup>2</sup>  | N/A<sup>3</sup> |
| Mono                       | 4.6    | 4.6    | 4.6   | 4.6   | 4.6   | 4.6                | 4.6                | 5,4                 | 6.4 |
| Xamarin.iOS                | 10.0   | 10.0   | 10.0  | 10.0  | 10.0  | 10.0               | 10.0               | 10.14               | 12.16 |
| Xamarin.Mac                | 3,0    | 3,0    | 3,0   | 3,0   | 3,0   | 3,0                | 3,0                | 3.8                 | 5.16 |
| Xamarin.Android            | 7.0    | 7.0    | 7.0   | 7.0   | 7.0   | 7.0                | 7.0                | 8.0                 | 10.0 |
| Evrensel Windows Platformu | 10.0   | 10.0   | 10.0  | 10.0  | 10.0  | 10.0.16299         | 10.0.16299         | 10.0.16299          | TBD |
| Unity                      | 2018.1 | 2018.1 | 2018.1| 2018.1| 2018.1| 2018.1             |  2018.1            | 2018.1              | TBD |

<sup>1.NET Framework için listelenen sürümler .NET Core 2.0 SDK ve daha sonraki araç sürümleri için geçerlidir. Eski sürümler .NET Standart 1.5 ve üzeri için farklı bir eşleme kullanabilmektedir. Visual Studio 2017'ye veya daha sonraki bir sürüme yükseltemiyorsanız [Visual Studio 2015 için .NET Core araçları](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md) için araç lama indirebilirsiniz.</sup>

<sup>2 Burada listelenen sürümler, NuGet'in belirli bir .NET Standart kitaplığı için kullanıp kullanmayacağını belirlemek için kullandığı kuralları temsil ediyor. NuGet .NET Framework 4.6.1'i .NET Standard 1.5 ile 2.0 arasında destekleyen olarak kabul etse de, .NET Framework 4.6.1 projelerinden bu sürümler için oluşturulmuş .NET Standart kitaplıklarının tüketilmesiyle ilgili çeşitli sorunlar vardır. Bu tür kitaplıkları kullanması gereken .NET Framework projeleri için , .NET Framework 4.7.2 veya daha yüksek bir hedefe proje yükseltmenizi öneririz.</sup>

<sup>3 .NET Framework ,NET Standart 2.1 veya sonraki sürümleri desteklemez. Daha fazla bilgi için [.NET Standart 2.1 duyurusuna](https://devblogs.microsoft.com/dotnet/announcing-net-standard-2-1/)bakın.</sup>

- Sütunlar .NET Standart sürümlerini temsil ediyor. Her üstbilgi hücresi, .NET Standard'ın bu sürümüne hangi API'lerin eklendiğine dair belgeye bağlantıdır.
- Satırlar farklı .NET uygulamalarını temsil eder.
- Her hücredeki sürüm numarası, .NET Standart sürümünü hedeflemek için ihtiyacınız olan uygulamanın *en az* sürümünü gösterir.
- Etkileşimli bir tablo için [.NET Standart sürümlerine](https://dotnet.microsoft.com/platform/dotnet-standard#versions)bakın.

[1.0]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.0.md
[1.1]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.1.md
[1.2]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.2.md
[1.3]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.3.md
[1.4]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.4.md
[1.5]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.5.md
[1.6]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.6.md
[2.0]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.0.md
[2.1]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.1.md
