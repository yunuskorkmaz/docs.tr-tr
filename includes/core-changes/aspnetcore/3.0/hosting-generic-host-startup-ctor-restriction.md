---
ms.openlocfilehash: d1ddba72ce25c5e01025d916d52f785b5a1a9e71
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901609"
---
### <a name="hosting-generic-host-restricts-startup-constructor-injection"></a>Barındırma: genel ana bilgisayar, başlangıç Oluşturucu ekleme işlemini kısıtlar

Genel ana bilgisayarın `Startup` sınıf oluşturucu ekleme için desteklediği tek tür `IHostEnvironment`, `IWebHostEnvironment`ve `IConfiguration`. `WebHost` kullanan uygulamalar etkilenmemiştir.

#### <a name="change-description"></a>Açıklamayı Değiştir

ASP.NET Core 3,0 ' dan önce, Oluşturucu Ekleme `Startup` sınıfının oluşturucusunda rastgele türler için kullanılabilir. ASP.NET Core 3,0 ' de, Web yığını genel ana bilgisayar kitaplığı üzerine oluşturulmuştur. Şablonların *program.cs* dosyasında değişikliği görebilirsiniz:

**ASP.NET Core 2. x:**

<https://github.com/dotnet/aspnetcore/blob/5cb615fcbe8559e49042e93394008077e30454c0/src/Templating/src/Microsoft.DotNet.Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L20-L22>

**ASP.NET Core 3,0:**

<https://github.com/dotnet/aspnetcore/blob/b1ca2c1155da3920f0df5108b9fedbe82efaa11c/src/ProjectTemplates/Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L19-L24>

`Host`, uygulamayı derlemek için bir bağımlılık ekleme (dı) kapsayıcısı kullanır. `WebHost` iki kapsayıcı kullanır: biri konak ve uygulama için bir tane. Sonuç olarak, `Startup` Oluşturucusu artık özel hizmet ekleme işlemini desteklememektedir. Yalnızca `IHostEnvironment`, `IWebHostEnvironment`ve `IConfiguration` eklenebilir. Bu değişiklik, tek bir hizmetin yinelenen olarak oluşturulması gibi diğer sorunları önler.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, Web yığınını genel ana bilgisayar kitaplığı üzerinde oluşturan bir sonucudur.

#### <a name="recommended-action"></a>Önerilen eylem

`Startup.Configure` yöntemi imzasına hizmet ekleme. Örneğin:

```csharp
public void Configure(IApplicationBuilder app, IOptions<MyOptions> options)
```

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok.

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
