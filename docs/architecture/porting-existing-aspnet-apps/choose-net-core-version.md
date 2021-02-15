---
title: Doğru .NET Core sürümünü seçin
description: Hangi .NET Core sürümünün hedefleyeceğini nasıl belirlemelisiniz?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 401eead986ee8b67ed15be609d0b5d228773312d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488923"
---
# <a name="choose-the-right-net-core-version"></a>Doğru .NET Core sürümünü seçin

Hedeflenecek bir .NET Core sürümü seçerken çoğu kuruluşun en büyük değerlendirmesi, destek yaşam döngüsüyle belirlenir. Uzun süreli destek (LTS) yayınları daha az sıklıkla sevk eder, ancak geçerli (LTS olmayan) sürümlerden daha uzun bir destek penceresi vardır. Şu anda, LTS yayınları her yıl göndermek üzere zamanlandı. Müşteriler hangi yayınların hedeflemesini seçebilir ve aynı makinede .NET Core 'un farklı sürümlerini yan yana yükleyebilir. LTS yayınları yaşam döngüsünün tamamında yalnızca kritik ve uyumlu düzeltmeler alacaktır. Geçerli yayınlar aynı düzeltmeleri alacak ve ayrıca uyumlu yenilikler ve özelliklerle de güncelleştirilecektir. LTS yayınları, ilk yayımlandıktan üç yıl sonra desteklenir. Geçerli yayınlar, sonraki bir geçerli veya LTS sürümünden sonraki üç ay boyunca desteklenir.

Büyük bir .NET Framework uygulamasını bugün .NET Core 'a geçirmeyi isteyen çoğu müşteri, daha önce .NET Core 'un önceki bir sürümüne geçiş yapmadıklarından, büyük olasılıkla kararlı bir hedef arıyor. Bu durumda, geçiş için hedeflenecek en iyi .NET Core sürümü, geçerli LTS sürümü olan .NET Core 3,1 ' dir. .NET Core 3,1 desteği Aralık 2022 ' de sona erer. Sonraki planlı LTS sürümü .NET 6,0, Kasım 2021 ' de kullanıma sunulacaktır.

.NET Core 3,1 ' den .NET 5,0 ' e (sonraki sürüm) güncelleştirme, .NET Framework 'den .NET Core 'a kadar çok daha az çaba gerektirir. Bu nedenle, çoğu müşterinin önerisi öncelikle .NET Core 3,1 ' e yükseltilmeye yöneliktir. Ardından, sonraki güncelleştirmenin güncel sürüme (.NET 5,0) mi yoksa daha sonra yükseltmeden önce bir sonraki LTS sürümü (.NET 6,0) beklemeniz mi gerektiğine karar verin.

Bu kitapta .NET Framework uygulamalar .NET Core 3,1 ' e yükseltilecektir.

## <a name="references"></a>Başvurular

[.NET Core ve .NET 5 destek Ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)

>[!div class="step-by-step"]
>[Önceki](migrate-aspnet-core-2-1.md) 
> [Sonraki](incremental-migration-strategies.md)
