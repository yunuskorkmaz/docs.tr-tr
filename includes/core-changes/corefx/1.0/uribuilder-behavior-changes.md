---
ms.openlocfilehash: b3cc04d5675ea63a0a6b967e293da8a1bd79830d
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595694"
---
### <a name="uribuilder-properties-no-longer-prepend-leading-characters"></a>UriBuilder özellikleri artık önde gelen karakterlerin önüne alınmaz

<xref:System.UriBuilder.Fragment?displayProperty=nameWithType>Artık önde gelen `#` bir karakter önüne alınmaz ve <xref:System.UriBuilder.Query?displayProperty=nameWithType> bir tane zaten varsa öndeki `?` bir karakter artık yer almıyor.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework ' de, <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> ve <xref:System.UriBuilder.Query?displayProperty=nameWithType> özellikleri sırasıyla, depolanan değere `#` göre `?` veya karakter başına her zaman eklenir. Bu davranış, dize zaten bu `#` önde `?` gelen karakterlerden birini içeriyorsa depolanan değerde birden çok ya da karakter oluşmasına neden olabilir. Örneğin, değeri <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> olabilir `##main`.

.NET Core 1,0 ' den itibaren, bu özellikler, `#` dizenin başlangıcında zaten varsa `?` saklanan değere artık veya karakterleri içermez.

#### <a name="version-introduced"></a>Sunulan sürüm

1.0

#### <a name="recommended-action"></a>Önerilen eylem

Artık özellik değerlerini ayarlarken bu öndeki karakterlerin hiçbirini açıkça kaldırmanız gerekmez. Bu, özellikle de öndeki `#` veya `?` eklediğiniz her seferinde kaldırmak zorunda olmadığınız için değerleri eklerken kullanışlıdır.

Örneğin, aşağıdaki kod parçacığı .NET Framework ve .NET Core arasındaki davranış farkını gösterir.

```csharp
var builder = new UriBuilder();
builder.Query = "one=1";
builder.Query += "&two=2";
builder.Query += "&three=3";
builder.Query += "&four=4";

Console.WriteLine(builder.Query);
```

- .NET Framework, çıktı olur `????one=1&two=2&three=3&four=4`.
- .NET Core 'da çıkış `?one=1&two=2&three=3&four=4`.

#### <a name="category"></a>Kategori

Core .NET kitaplıkları

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.UriBuilder.Fragment?displayProperty=fullName>
- <xref:System.UriBuilder.Query?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.UriBuilder.Fragment`
- `T:System.UriBuilder.Query`

-->
