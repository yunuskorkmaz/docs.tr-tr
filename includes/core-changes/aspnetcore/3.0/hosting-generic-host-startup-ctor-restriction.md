---
ms.openlocfilehash: d1ddba72ce25c5e01025d916d52f785b5a1a9e71
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032747"
---
### <a name="hosting-generic-host-restricts-startup-constructor-injection"></a>Barındırma: genel ana bilgisayar, başlangıç Oluşturucu ekleme işlemini kısıtlar

Genel ana bilgisayarın sınıf oluşturucu ekleme için desteklediği tek türler `Startup` `IHostEnvironment` , ve ' dir `IWebHostEnvironment` `IConfiguration` . Kullanan uygulamalar `WebHost` etkilenmemiştir.

#### <a name="change-description"></a>Açıklamayı Değiştir

ASP.NET Core 3,0 ' den önce, Oluşturucu Ekleme, sınıfın oluşturucusunda rastgele türler için kullanılabilir `Startup` . ASP.NET Core 3,0 ' de, Web yığını genel ana bilgisayar kitaplığı üzerine oluşturulmuştur. Şablonların *program.cs* dosyasında değişikliği görebilirsiniz:

**ASP.NET Core 2. x:**

<https://github.com/dotnet/aspnetcore/blob/5cb615fcbe8559e49042e93394008077e30454c0/src/Templating/src/Microsoft.DotNet.Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L20-L22>

**ASP.NET Core 3,0:**

<https://github.com/dotnet/aspnetcore/blob/b1ca2c1155da3920f0df5108b9fedbe82efaa11c/src/ProjectTemplates/Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L19-L24>

`Host` , uygulamayı derlemek için bir bağımlılık ekleme (dı) kapsayıcısını kullanır. `WebHost` iki kapsayıcıyı kullanır: biri konak ve uygulama için bir tane. Sonuç olarak, `Startup` Oluşturucu artık özel hizmet ekleme işlemini desteklememektedir. Yalnızca `IHostEnvironment` , `IWebHostEnvironment` ve eklenebilir `IConfiguration` . Bu değişiklik, tek bir hizmetin yinelenen olarak oluşturulması gibi diğer sorunları önler.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, Web yığınını genel ana bilgisayar kitaplığı üzerinde oluşturan bir sonucudur.

#### <a name="recommended-action"></a>Önerilen eylem

Yöntem imzasına hizmet ekleme `Startup.Configure` . Örnek:

```csharp
public void Configure(IApplicationBuilder app, IOptions<MyOptions> options)
```

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
