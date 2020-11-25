---
ms.openlocfilehash: be1fad236dd3eed047b010e93285aec8bc607b61
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032755"
---
### <a name="hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced"></a>Barındırma: ıhostingenvironment ve ıapplicationlifetime türleri artık kullanılmıyor ve değiştirilmiş olarak işaretlendi

Var olan ve türlerin yerini alacak yeni türler `IHostingEnvironment` sunuldu `IApplicationLifetime` .

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="old-behavior"></a>Eski davranış

`IHostingEnvironment` `IApplicationLifetime` Ve ' den iki farklı tür vardı `Microsoft.Extensions.Hosting` `Microsoft.AspNetCore.Hosting` .

#### <a name="new-behavior"></a>Yeni davranış

Eski türler kullanım dışı olarak işaretlendi ve yeni türlerle değiştirildi.

#### <a name="reason-for-change"></a>Değişiklik nedeni

`Microsoft.Extensions.Hosting`ASP.NET Core 2,1 ' de tanıtıldığında, `IHostingEnvironment` ve ' `IApplicationLifetime` den kopyalanan bazı türler `Microsoft.AspNetCore.Hosting` . Bazı ASP.NET Core 3,0 değişiklikleri, uygulamaların hem hem de ad alanlarını içermesine neden olur `Microsoft.Extensions.Hosting` `Microsoft.AspNetCore.Hosting` . Bu yinelenen türlerin herhangi bir kullanımı, her iki ad alanına de başvuruluyorsa "belirsiz başvuru" derleyici hatasına neden olur.

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

New `IHostEnvironment` `IsDevelopment` ve `IsProduction` extension yöntemleri `Microsoft.Extensions.Hosting` ad alanıdır. Bu ad alanının projenize eklenmesi gerekebilir.

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
