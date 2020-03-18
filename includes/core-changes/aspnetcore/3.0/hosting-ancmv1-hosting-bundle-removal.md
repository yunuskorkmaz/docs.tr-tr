---
ms.openlocfilehash: 82103d82a6f68c62f3532608718bc71b0ba126bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901985"
---
### <a name="hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle"></a>Hosting: AspNetCoreModule V1 Windows Hosting Paketi kaldırıldı

Core 3.0 ASP.NET başlayarak, Windows Hosting Paketi AspNetCoreModule (ANCM) V1 içermez.

ANCM V2, ANCM OutOfProcess ile geriye doğru uyumludur ve ASP.NET Core 3.0 uygulamalarıyla kullanılması önerilir.

Tartışma için [dotnet/aspnetcore#7095'e](https://github.com/dotnet/aspnetcore/issues/7095)bakın.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış

ANCM V1, Windows Barındırma Paketi'ne dahildir.

#### <a name="new-behavior"></a>Yeni davranış

ANCM V1, Windows Barındırma Paketi'ne dahil değildir.

#### <a name="reason-for-change"></a>Değişiklik nedeni

ANCM V2, ANCM OutOfProcess ile geriye doğru uyumludur ve ASP.NET Core 3.0 uygulamalarıyla kullanılması önerilir.

#### <a name="recommended-action"></a>Önerilen eylem

ASP.NET Core 3.0 uygulamalarıyla ANCM V2 kullanın.

ANCM V1 gerekirse, ASP.NET Core 2.1 veya 2.2 Windows Hosting Paketi kullanılarak yüklenebilir.

Bu değişiklik, Core 3.0 uygulamaları ASP.NET kıracak:

- Açıkça ILE ANCM V1 kullanarak `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`tercih etti.
- Özel bir *web.config* `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`dosyası var.

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
