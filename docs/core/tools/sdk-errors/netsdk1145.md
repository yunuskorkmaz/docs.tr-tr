---
title: 'NETSDK1145: hedefleme veya apphost paketi eksik'
description: NuGet paketi geri yüklemesi desteklenmediğinden hedefleme paketinin sorunu nasıl çözümlenir?
author: wli3
ms.topic: error-reference
ms.date: 09/14/2020
f1_keywords:
- NETSDK1145
ms.openlocfilehash: c343952582cafb63eae388fd216769e6c67d4741
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91805326"
---
# <a name="netsdk1145-targeting-or-apphost-pack-missing"></a>NETSDK1145: hedefleme veya apphost paketi eksik

**Bu makale şu şekilde geçerlidir:** ✔️ .NET 5.0.100 SDK ve sonraki sürümleri

.NET SDK hatası NETSDK1145 hata verdiği zaman, hedefleme veya apphost paketi yüklenmez ve NuGet paketi geri yükleme desteklenmez. Bu, genellikle C++/CLı projeleri için Visual Studio 'ya dahil olandan daha yeni bir SDK olma nedeniyle oluşur. Visual Studio 'Yu yükseltin, belirli bir SDK sürümü belirtiyorsa _global.json 'u_ kaldırın ve daha yeni SDK 'yı kaldırın. Alternatif olarak, hedefleme veya apphost sürümünü geçersiz kılabilirsiniz. Hata iletisinden paket dizini altında bulunan sürümü bulun ve projenin hedef çerçevesiyle eşleşir. Aşağıdakileri projeye ekleyin:

Apphost paketi için

```xml
<ItemGroup>
  <KnownAppHostPack Update="@(KnownAppHostPack)">
    <AppHostPackVersion Condition="'%(TargetFramework)' == 'TARGETFRAMEWORK'">EXISTINGVERSION</AppHostPackVersion>
  </KnownAppHostPack>
</ItemGroup>
```

Hedefleme paketi için

```xml
<ItemGroup>
  <KnownAppHostPack Update="@(KnownAppHostPack)">
    <AppHostPackVersion Condition="'%(TargetFramework)' == 'TARGETFRAMEWORK'">EXISTINGVERSION</AppHostPackVersion>
  </KnownAppHostPack>
</ItemGroup>
```
