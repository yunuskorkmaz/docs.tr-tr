---
ms.openlocfilehash: d1ddba72ce25c5e01025d916d52f785b5a1a9e71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901609"
---
### <a name="hosting-generic-host-restricts-startup-constructor-injection"></a>Barındırma: Genel ana bilgisayar Başlangıç yapıcı enjeksiyonu kısıtlar

Genel ana bilgisayar tarafından `Startup` sınıf yapıcı enjeksiyonu `IWebHostEnvironment`için `IConfiguration`destekleyen tek tür , `IHostEnvironment`ve . Kullanan `WebHost` uygulamalar etkilenmez.

#### <a name="change-description"></a>Açıklamayı değiştir

Core 3.0ASP.NETönce, yapıcı enjeksiyon `Startup` sınıfın oluşturucusundaki rasgele tipler için kullanılabilir. Core 3.0ASP.NET, web yığını genel ana bilgisayar kitaplığı üzerine yeniden platformlandı. Şablonların *Program.cs* dosyasındaki değişikliği görebilirsiniz:

**ASP.NET Çekirdek 2.x:**

<https://github.com/dotnet/aspnetcore/blob/5cb615fcbe8559e49042e93394008077e30454c0/src/Templating/src/Microsoft.DotNet.Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L20-L22>

**ASP.NET Çekirdek 3.0:**

<https://github.com/dotnet/aspnetcore/blob/b1ca2c1155da3920f0df5108b9fedbe82efaa11c/src/ProjectTemplates/Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L19-L24>

`Host`uygulamayı oluşturmak için bir bağımlılık enjeksiyonu (DI) kapsayıcıkullanır. `WebHost`iki kapsayıcı kullanır: biri ana bilgisayar için, diğeri uygulama için. Sonuç olarak, `Startup` oluşturucu artık özel hizmet enjeksiyondestekler. Sadece `IHostEnvironment` `IWebHostEnvironment`, `IConfiguration` , ve enjekte edilebilir. Bu değişiklik, tek ton hizmetinin yinelenen oluşturulması gibi DI sorunlarını önler.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, web yığınını genel ana bilgisayar kitaplığı üzerine yeniden platformlandırmanın bir sonucudur.

#### <a name="recommended-action"></a>Önerilen eylem

Hizmetleri yöntem `Startup.Configure` imzasına enjekte edin. Örnek:

```csharp
public void Configure(IApplicationBuilder app, IOptions<MyOptions> options)
```

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
