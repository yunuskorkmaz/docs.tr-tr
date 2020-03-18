---
ms.openlocfilehash: 1e081c9f37fbd7ab754ce44ba89d7aa5cabfc219
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901749"
---
### <a name="mvc-precompilation-tool-deprecated"></a>MVC: Precompilation aracı amortismana

Core 1.1ASP.NETde, `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (MVC precompilation aracı) paketi Razor dosyalarının yayımlama zamanı derlemesi *(.cshtml* dosyaları) için destek eklemek için tanıtıldı. Core 2.1ASP.NET [de, Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) precompilation aracının özellikleri üzerine genişletmek için tanıtıldı. Razor SDK, Razor dosyalarının oluşturma ve yayımlama zamanı derlemesi için destek ekledi. SDK, *.cshtml* dosyalarının oluşturma zamanında doğruluğunu doğrularken, uygulama başlangıç zamanında iyileşir. Razor SDK varsayılan olarak açıktır ve kullanmaya başlamak için herhangi bir hareket gerekmez.

Core 3.0ASP.NETde, ASP.NET Core 1.1-era MVC precompilation aracı kaldırıldı. Önceki paket sürümleri yama sürümünde önemli hata ve güvenlik düzeltmeleri almaya devam edecektir.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış

Paket, `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` MVC Razor görünümlerini önceden derlemek için kullanılmıştır.

#### <a name="new-behavior"></a>Yeni davranış

Razor SDK bu işlevselliği doğal olarak destekler. Paket `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` artık güncelleştirdeğil.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Razor SDK daha fazla işlevsellik sağlar ve *.cshtml* dosyalarının oluşturma sırasındaki doğruluğunu doğrular. SDK ayrıca uygulama başlangıç süresini de iyileştirir.

#### <a name="recommended-action"></a>Önerilen eylem

Core 2.1 veya daha ASP.NET kullanıcıları [için, Razor SDK'da](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0)precompilation için yerel desteği kullanmak üzere güncelleştirin. Hatalar veya eksik özellikler Razor SDK'ya geçişi engelliyorsa, [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues)adresinde bir sorun açın.

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

None

<!-- 

### Affected APIs

Not detectable via API analysis

-->
