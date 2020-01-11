---
ms.openlocfilehash: 1e081c9f37fbd7ab754ce44ba89d7aa5cabfc219
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901749"
---
### <a name="mvc-precompilation-tool-deprecated"></a>MVC: ön derleme aracı kullanım dışı

ASP.NET Core 1,1 ' de, Razor dosyalarının ( *. cshtml* dosyaları) yayımlama zamanı derlemesi için destek eklemek üzere `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (MVC ön derleme aracı) paketi sunulmuştur. ASP.NET Core 2,1 ' de, [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) , ön derleme aracının özelliklerini genişletmek üzere sunulmuştur. Razor SDK, Razor dosyalarının derleme ve yayımlama zamanı derlemesi için destek eklendi. SDK, uygulama başlatma zamanında geliştirirken derleme zamanında *. cshtml* dosyalarının doğruluğunu doğrular. Razor SDK varsayılan olarak açık olur ve kullanmaya başlamak için herhangi bir hareket gerekmez.

ASP.NET Core 3,0 ' de, ASP.NET Core 1,1-Era MVC prederlemesini kaldırma aracı kaldırılmıştır. Önceki paket sürümleri, düzeltme eki sürümünde önemli hata ve güvenlik düzeltmeleri almaya devam edecektir.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

`Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` paketi, MVC Razor görünümlerini önceden derlemek için kullanıldı.

#### <a name="new-behavior"></a>Yeni davranış

Razor SDK, bu işlevselliği yerel olarak destekler. `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` paketi artık güncelleştirilmedi.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Razor SDK daha fazla işlevsellik sağlar ve derleme zamanında *. cshtml* dosyalarının doğruluğunu doğrular. SDK Ayrıca uygulama başlatma süresini geliştirir.

#### <a name="recommended-action"></a>Önerilen eylem

ASP.NET Core 2,1 veya sonraki bir sürümü kullananlar için, [Razor SDK 'sında](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0)ön derleme için yerel desteği kullanmak üzere güncelleştirin. Hatalar veya eksik özellikler Razor SDK 'ya geçişi engelliyorsa, [DotNet/aspnetcore](https://github.com/dotnet/aspnetcore/issues)' da bir sorun açın.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok.

<!-- 

### Affected APIs

Not detectable via API analysis

-->
