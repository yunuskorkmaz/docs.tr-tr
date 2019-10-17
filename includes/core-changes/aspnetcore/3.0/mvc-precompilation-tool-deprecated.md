---
ms.openlocfilehash: 641233df165a1c2208a2185f2b6e99077f9a59d3
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394170"
---
### <a name="mvc-precompilation-tool-deprecated"></a>MVC: ön derleme aracı kullanım dışı

ASP.NET Core 1,1 ' de, Razor dosyalarının ( *. cshtml* dosyaları) yayımlama zamanı derlemesi için destek eklemek üzere `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (MVC ön derleme aracı) paketi sunulmuştur. ASP.NET Core 2,1 ' de, [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) , ön derleme aracının özelliklerini genişletmek üzere sunulmuştur. Razor SDK, Razor dosyalarının derleme ve yayımlama zamanı derlemesi için destek eklendi. SDK, uygulama başlatma zamanında geliştirirken derleme zamanında *. cshtml* dosyalarının doğruluğunu doğrular. Razor SDK varsayılan olarak açık olur ve kullanmaya başlamak için herhangi bir hareket gerekmez.

ASP.NET Core 3,0 ' de, ASP.NET Core 1,1-Era MVC prederlemesini kaldırma aracı kaldırılmıştır. Önceki paket sürümleri, düzeltme eki sürümünde önemli hata ve güvenlik düzeltmeleri almaya devam edecektir. 

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

@No__t-0 paketi, MVC Razor görünümlerini önceden derlemek için kullanıldı.

#### <a name="new-behavior"></a>Yeni davranış

Razor SDK, bu işlevselliği yerel olarak destekler. @No__t-0 paketi artık güncelleştirilmemiş.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Razor SDK daha fazla işlevsellik sağlar ve derleme zamanında *. cshtml* dosyalarının doğruluğunu doğrular. SDK Ayrıca uygulama başlatma süresini geliştirir.

#### <a name="recommended-action"></a>Önerilen eylem

ASP.NET Core 2,1 veya sonraki bir sürümü kullananlar için, [Razor SDK 'sında](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0)ön derleme için yerel desteği kullanmak üzere güncelleştirin. Hatalar veya eksik özellikler Razor SDK 'ya geçişi engelliyorsa, [ASPNET/AspNetCore](https://github.com/aspnet/AspNetCore/issues)yolunda bir sorun açın.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok.

<!-- 

### Affected APIs

Not detectable via API analysis

-->
