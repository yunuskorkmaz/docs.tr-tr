---
title: 'Son değişiklik: Directory. Packages. props dosyaları varsayılan olarak içeri aktarılır'
description: .NET 5 ' teki son değişiklik hakkında bilgi edinmek için NuGet. props dosyalarının, proje klasöründe bulunursa dizin. Packages. props adlı bir dosyayı otomatik olarak içeri aktardığını öğrenin.
ms.date: 09/17/2020
ms.openlocfilehash: a031d9b2bd832be06dedb20495c24075d1239b02
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256588"
---
# <a name="directorypackagesprops-files-is-imported-by-default"></a>Directory. Packages. props dosyaları varsayılan olarak içeri aktarılır

NuGet *. props* dosyaları, proje klasöründe veya üst öğelerinden birinde bulunursa, *Directory. Packages. props* adlı bir dosyayı otomatik olarak içeri aktarır.

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, proje dosyanızda *Directory. Packages. props* adlı bir dosyanız olabilir ve derleme zamanında NuGet *. props* dosyası tarafından otomatik olarak içeri aktarılmaz.

.NET 5 ' den başlayarak, bu tür *bir dosya proje* klasöründe veya üst öğelerinden herhangi biri varsa otomatik olarak içeri aktarılır. Proje klasörünüzde bu adı taşıyan bir dosyanız varsa, bu otomatik içeri aktarma yapı davranışını değiştirebilir. Örneğin, dosya içeri aktarılır, ancak daha önce değil veya içe aktarıldıysanız içeri aktarma sırası değişebilir.

## <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, NuGet için [Merkezi paket sürümü oluşturmayı](https://github.com/NuGet/Home/wiki/Centrally-managing-NuGet-package-versions) desteklemek üzere yapılmıştır.

## <a name="recommended-action"></a>Önerilen eylem

Otomatik olarak içeri aktarılmaması gerekiyorsa, var olan *Dizin. Packages. props* dosyasını yeniden adlandırın.

## <a name="affected-apis"></a>Etkilenen API’ler

Yok

<!--

### Affected APIs

Not detectable via API analysis.

### Category

MSBuild

-->
