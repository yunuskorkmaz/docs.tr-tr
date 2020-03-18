---
ms.openlocfilehash: be1fad236dd3eed047b010e93285aec8bc607b61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394335"
---
### <a name="hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced"></a>Hosting: IHostingEnvironment ve IApplicationLifetime türleri eski işaretlenmiş ve değiştirildi

Varolan ve `IHostingEnvironment` `IApplicationLifetime` türleri değiştirmek için yeni türler tanıtıldı.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış

İki farklı `IHostingEnvironment` ve `IApplicationLifetime` türleri `Microsoft.Extensions.Hosting` `Microsoft.AspNetCore.Hosting`vardı ve .

#### <a name="new-behavior"></a>Yeni davranış

Eski türler eski olarak işaretlenmiş ve yeni türlerle değiştirilmiştir.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Core `Microsoft.Extensions.Hosting` 2.1ASP.NET de sunulduğunda, bazı `IHostingEnvironment` `IApplicationLifetime` türleri gibi `Microsoft.AspNetCore.Hosting`ve kopyalandı . Bazı ASP.NET Core 3.0 değişiklikleri uygulamaların `Microsoft.Extensions.Hosting` `Microsoft.AspNetCore.Hosting` hem ad alanlarını hem de ad alanlarını içermesine neden olur. Bu yinelenen türlerin herhangi bir kullanımı, her iki ad alanı başvurulduğunda bir "belirsiz başvuru" derleyici hatasına neden olur.

#### <a name="recommended-action"></a>Önerilen eylem

Aşağıdaki gibi yeni tanıtılan türleri ile eski türlerin herhangi bir kullanımları değiştirildi:

**Eski türleri (uyarı):**

- <xref:Microsoft.Extensions.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.EnvironmentName?displayProperty=nameWithType>

**Yeni türler:**

- <xref:Microsoft.Extensions.Hosting.IHostEnvironment?displayProperty=nameWithType>
- `Microsoft.AspNetCore.Hosting.IWebHostEnvironment : IHostEnvironment`
- <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.Environments?displayProperty=nameWithType>

Yeni `IHostEnvironment` `IsDevelopment` ve `IsProduction` uzantı yöntemleri `Microsoft.Extensions.Hosting` ad alanındadır. Bu ad alanının projenize eklenmesi gerekebilir.

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:Microsoft.AspNetCore.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostingEnvironment?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Hosting.EnvironmentName`
- `T:Microsoft.AspNetCore.Hosting.IApplicationLifetime`
- `T:Microsoft.AspNetCore.Hosting.IHostingEnvironment`
- `T:Microsoft.Extensions.Hosting.EnvironmentName`
- `T:Microsoft.Extensions.Hosting.IApplicationLifetime`
- `T:Microsoft.Extensions.Hosting.IHostingEnvironment`

-->
