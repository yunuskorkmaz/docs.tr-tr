---
ms.openlocfilehash: be1fad236dd3eed047b010e93285aec8bc607b61
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394335"
---
### <a name="hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced"></a>Barındırma: ıhostingenvironment ve ıapplicationlifetime türleri artık kullanılmıyor ve değiştirilmiş olarak işaretlendi

Var olan `IHostingEnvironment` ve `IApplicationLifetime` türlerini değiştirmek için yeni türler sunulmuştur.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

@No__t-2 ve `Microsoft.AspNetCore.Hosting` ' ten iki farklı `IHostingEnvironment` ve `IApplicationLifetime` türü vardı.

#### <a name="new-behavior"></a>Yeni davranış

Eski türler kullanım dışı olarak işaretlendi ve yeni türlerle değiştirildi.

#### <a name="reason-for-change"></a>Değişiklik nedeni

@No__t-0 ASP.NET Core 2,1 ' de tanıtıldığında, `IHostingEnvironment` ve `IApplicationLifetime` gibi bazı türler `Microsoft.AspNetCore.Hosting` ' ten kopyalandı. Bazı ASP.NET Core 3,0 değişiklikleri, uygulamaların hem `Microsoft.Extensions.Hosting` hem de `Microsoft.AspNetCore.Hosting` ad alanlarını içermesini sağlar. Bu yinelenen türlerin herhangi bir kullanımı, her iki ad alanına de başvuruluyorsa "belirsiz başvuru" derleyici hatasına neden olur.

#### <a name="recommended-action"></a>Önerilen eylem

Eski türlerin tüm kullanımları, Yeni tanıtılan türlerle aşağıda gösterildiği gibi değiştirilmiştir:

**Kullanılmayan türler (uyarı):**

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

Yeni `IHostEnvironment` `IsDevelopment` ve `IsProduction` uzantı yöntemleri `Microsoft.Extensions.Hosting` ad alanıdır. Bu ad alanının projenize eklenmesi gerekebilir.

#### <a name="category"></a>Kategori

ASP.NET Core

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
