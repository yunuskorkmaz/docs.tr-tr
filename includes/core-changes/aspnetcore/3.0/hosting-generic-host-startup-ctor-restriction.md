---
ms.openlocfilehash: be9a79f6ead3e72d7ffaade758704f0c1e2477f0
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394306"
---
### <a name="hosting-generic-host-restricts-startup-constructor-injection"></a>Barındırma: genel ana bilgisayar, başlangıç Oluşturucu ekleme işlemini kısıtlar

Genel ana bilgisayarın `Startup` sınıf oluşturucu ekleme için desteklediği tek türler `IHostEnvironment`, `IWebHostEnvironment` ve `IConfiguration` ' tür. @No__t-0 kullanan uygulamalar etkilenmemiştir.

#### <a name="change-description"></a>Açıklamayı Değiştir

ASP.NET Core 3,0 ' dan önce, Oluşturucu Ekleme `Startup` sınıfının oluşturucusunda rastgele türler için kullanılabilir. ASP.NET Core 3,0 ' de, Web yığını genel ana bilgisayar kitaplığı üzerine oluşturulmuştur. Şablonların *program.cs* dosyasında değişikliği görebilirsiniz:

**ASP.NET Core 2. x:**

<https://github.com/aspnet/AspNetCore/blob/5cb615fcbe8559e49042e93394008077e30454c0/src/Templating/src/Microsoft.DotNet.Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L20-L22>

**ASP.NET Core 3,0:**

<https://github.com/aspnet/AspNetCore/blob/b1ca2c1155da3920f0df5108b9fedbe82efaa11c/src/ProjectTemplates/Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L19-L24>

`Host`, uygulamayı derlemek için bir bağımlılık ekleme (dı) kapsayıcısı kullanır. `WebHost` iki kapsayıcı kullanır: biri konak ve uygulama için bir tane. Sonuç olarak, `Startup` Oluşturucusu artık özel hizmet ekleme işlemini desteklememektedir. Yalnızca `IHostEnvironment`, `IWebHostEnvironment` ve `IConfiguration` eklenebilir. Bu değişiklik, tek bir hizmetin yinelenen olarak oluşturulması gibi diğer sorunları önler.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, Web yığınını genel ana bilgisayar kitaplığı üzerinde oluşturan bir sonucudur.

#### <a name="recommended-action"></a>Önerilen eylem

@No__t-0 Yöntem imzasına hizmet ekleme. Örneğin:

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
