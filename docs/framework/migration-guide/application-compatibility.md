---
title: .NET Framework'te Uygulama Uyumluluğu
ms.date: 05/19/2017
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1939666b3dd271959c418e3d714b177e170fcd04
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54595987"
---
# <a name="application-compatibility-in-the-net-framework"></a>.NET Framework'te Uygulama Uyumluluğu

## <a name="introduction"></a>Giriş
Uyumluluk, her bir .NET yayının çok önemli bir hedeftir. Uyumluluk sağlar her sürümü eklenebilir, böylece önceki sürümleri çalışmaya devam eder. Öte yandan, (güvenlik sorunlarını gidermek, performansı artırmak veya hataları düzeltmek için) önceki işlev değişiklikleri mevcut kod veya sonraki bir sürümünü altında çalışan uygulamalara uyumluluk sorunlarına neden olabilir. .NET Framework yeniden hedefleme değişiklikleri ve çalışma zamanı değişiklikleri algılar. Yeniden hedefleme değişiklikleri, ancak sonraki bir sürümü üzerinde çalışan belirli bir .NET Framework sürümünü hedefleyen uygulamaları etkiler. Çalışma zamanı değişiklikleri, belirli bir sürümü üzerinde çalışan tüm uygulamaları etkiler.

Her bir uygulama tarafından belirtilen .NET Framework'ün belirli bir sürümünü hedefler:

* Visual Studio'da hedef Framework'ü tanımlama.
* Hedef Çerçeve proje dosyasında belirtme.
* Uygulama bir <xref:System.Runtime.Versioning.TargetFrameworkAttribute> kaynak koduna.

Hangi hedef değerinden daha yeni bir sürümü üzerinde çalışırken, .NET Framework quirked davranışı hedeflenen sürümün taklit etmek için kullanır. Diğer bir deyişle, uygulama Framework'ün daha yeni sürümlerde çalışır, ancak daha eski bir sürümünde çalışıyorsa gibi davranır. .NET Framework sürümleri arasındaki uyumluluk sorunları birçoğu bu quirking modeliyle azalır. .NET Framework sürümü, bir uygulama hedefleri kodun çalıştığı uygulama etki alanı için giriş derleme hedef sürümünü göre belirlenir. Tüm ek derlemeler hedefleyen uygulama etki alanı, .NET Framework sürümü yüklendi. Örneğin, yürütülebilir bir dosya söz konusu olduğunda, yürütülebilir hedefleri çerçevedir, tüm derlemeleri, uygulama etki alanı altında çalıştırılacağı uyumluluk modu.

## <a name="runtime-changes"></a>{1&gt;Çalışma zamanı değişiklikleri&lt;1}

Çalışma zamanı sorunlarına bir makinede yeni bir çalışma zamanı yerleştirilir ve aynı ikili dosyaları çalıştırın, ancak farklı bir davranış görülür ortaya çıkan olanlardır. Bir ikili için .NET Framework 4.0 derlenmişse 4.5 veya sonraki sürümlerinde .NET Framework 4.0 uyumluluk modunda çalışır. 4.5 etkileyen değişiklikler birçoğu 4.0 için derlenmiş bir ikili etkilemez. Bu, uygulama etki alanına özgü ve giriş bütünleştirilmiş kodun ayarlarına bağlıdır.

## <a name="retargeting-changes"></a>Yeniden hedefleme değişiklikleri

Yeniden hedefleme sorunları 4.0 hedef bütünleştirilmiş 4.5 hedefine artık ayarlandığında ortaya çıkan olanlardır. Artık derleme yeni özelliklerin yanı sıra eski özelliklere olası uyumluluk sorunları olarak kabul eder. Yeniden, bu giriş derlemesi tarafından şekilde belirlenmiştir derleme kullanan bir konsol uygulaması ya da derlemeye başvuran Web sitesidir.

## <a name="net-compatibility-diagnostics"></a>.NET uyumluluğu tanılama

.NET uyumluluğu tanılama Roslyn tabanlı Çözümleyicileri, .NET Framework sürümleri arasındaki uygulama uyumluluk sorunlarını tanımlamaya yardımcı olan. Belirli bir geçiş için yalnızca bir alt uygulanır ancak bu liste tüm kullanılabilir Çözümleyicileri içerir. Hangi sorunlarını planlanan geçiş için geçerlidir ve yalnızca bu belirir Çözümleyicileri belirler.

Her sorun, aşağıdaki bilgileri içerir:

-   Önceki bir sürümden değişikliklerin açıklaması.

-   Nasıl değişiklik müşteriler ve herhangi bir geçici çözüm sürümler arasında uyumluluğu korumak kullanılabilir olup etkiler.

-   Ne kadar önemli olduğunu değişikliği'nin bir değerlendirme. Bir uyumluluk sorununu kategorilere ayrılabilir gibi:

    |   |   |
    |---|---|
    |Ana|Çok sayıda uygulamayı etkileyen veya kod değişikliği gerektiren önemli bir değişiklik.|
    |İkincil|Az sayıda uygulamayı etkileyen veya az miktarda kod değişikliği gerektiren bir değişiklik.|
    |Uç durum|Bir değişiklik belirli, genel olmayan senaryolar altında uygulamaları etkiler.|
    |Geçirgen|Bir değişiklik ile uygulamanın geliştiricisi veya kullanıcısı üzerinde fark edilebilir etkisi.|

-   Sürüm değişikliği framework ilk görüntülendiğinde gösterir. Bazı değişiklikler belirli bir sürümünde sunulan ve sonraki bir sürümde geri; Bu da gösterilir.

-   Değişiklik türü:

    |   |   |
    |---|---|
    |Yeniden Hedefleme|Bu değişiklik, .NET Framework'ün yeni bir sürümünü hedefleyecek şekilde derlenen uygulamaları etkiler.|
    |Çalışma zamanı|Bu değişiklik, .NET Framework'ün önceki bir sürümünü hedefler, ancak daha sonraki bir sürümü üzerinde çalışan mevcut bir uygulamayı etkiler.|

-   Etkilenen API'leri, varsa.

-   Kullanılabilir tanılama kimlikleri

## <a name="usage"></a>Kullanım
Başlamak için aşağıdaki uyumluluk değişiklik türünü seçin:

* [Yeniden Hedefleme Değişiklikleri](./retargeting/index.md)
* [Çalışma Zamanı Değişiklikleri](./runtime/index.md)


## <a name="see-also"></a>Ayrıca bkz.

- [Sürümler ve Bağımlılıklar](../../../docs/framework/migration-guide/versions-and-dependencies.md)
- [Yenilikler](../../../docs/framework/whats-new/index.md)
- [Sınıf Kitaplığında Artık Kullanılmayanlar](../../../docs/framework/whats-new/whats-obsolete.md)
