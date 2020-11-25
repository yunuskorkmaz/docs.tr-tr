---
title: 'Son değişiklik: Directory. Packages. props dosyaları varsayılan olarak içeri aktarılır'
description: NuGet. props dosyalarının, proje klasöründe bulunursa, dizin. Packages. props adlı bir dosyayı otomatik olarak içeri aktardığından, .NET 5,0 ' deki Son değişiklik hakkında bilgi edinin.
ms.date: 09/17/2020
ms.openlocfilehash: ee8a2999b801e81750d96a0bc985e3c8169224a9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761458"
---
# <a name="directorypackagesprops-files-is-imported-by-default"></a>Directory. Packages. props dosyaları varsayılan olarak içeri aktarılır

NuGet *. props* dosyaları, proje klasöründe veya üst öğelerinden birinde bulunursa, *Directory. Packages. props* adlı bir dosyayı otomatik olarak içeri aktarır.

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, proje dosyanızda *Directory. Packages. props* adlı bir dosyanız olabilir ve derleme zamanında NuGet *. props* dosyası tarafından otomatik olarak içeri aktarılmaz.

.NET 5,0 ' den başlayarak, bu tür bir dosya proje klasöründe veya üst öğelerinden herhangi biri *varsa otomatik olarak içeri aktarılır.* Proje klasörünüzde bu adı taşıyan bir dosyanız varsa, bu otomatik içeri aktarma yapı davranışını değiştirebilir. Örneğin, dosya içeri aktarılır, ancak daha önce değil veya içe aktarıldıysanız içeri aktarma sırası değişebilir.

## <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, NuGet için [Merkezi paket sürümü oluşturmayı](https://github.com/NuGet/Home/wiki/Centrally-managing-NuGet-package-versions) desteklemek üzere yapılmıştır.

## <a name="recommended-action"></a>Önerilen eylem

Otomatik olarak içeri aktarılmaması gerekiyorsa, var olan *Dizin. Packages. props* dosyasını yeniden adlandırın.

## <a name="affected-apis"></a>Etkilenen API’ler

YOK

<!--

### Affected APIs

Not detectable via API analysis.

### Category

MSBuild

-->
