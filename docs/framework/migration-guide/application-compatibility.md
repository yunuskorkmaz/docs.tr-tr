---
title: Çalışma zamanı ve yeniden hedefleme değişiklikleri-.NET Framework
description: .NET Framework 'de uygulama uyumluluğu ve başka bir sürüme geçiş yaparken çalışma zamanı ve yeniden hedefleme değişikliklerinin nasıl etkilendiğine ilişkin bilgi edinin.
ms.date: 10/29/2019
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
ms.openlocfilehash: 26f36dd34c6c5ecae8fc5ab373ff60d9e56f8245
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475495"
---
# <a name="application-compatibility-in-the-net-framework"></a>.NET Framework uygulama uyumluluğu

Uyumluluk, her bir .NET sürümünün önemli bir hedefidir. Uyumluluk, her sürümün eklenebilir olmasını sağlar, bu nedenle önceki sürümler çalışmaya devam edecektir. Öte yandan, önceki işlevlerde yapılan değişiklikler (örneğin, performansı artırmak, güvenlik sorunlarını gidermek veya hataları gidermek için), mevcut koddaki veya sonraki bir sürümde çalışan mevcut uygulamalarda uyumluluk sorunlarına neden olabilir.

Her uygulama .NET Framework belirli bir sürümünü hedefler:

- Visual Studio 'da hedef çerçeve tanımlama.
- Hedef Framework bir proje dosyasında belirtiliyor.
- <xref:System.Runtime.Versioning.TargetFrameworkAttribute>Kaynak koda uygulama.

.NET Framework bir sürümünden diğerine geçiş yaparken göz önünde bulundurmanız gereken iki tür değişiklik vardır:

- [Çalışma zamanı değişiklikleri](#runtime-changes)
- [Yeniden hedefleme değişiklikleri](#retargeting-changes)

## <a name="runtime-changes"></a>Çalışma zamanı değişiklikleri

Çalışma zamanı sorunları, bir makineye yeni bir çalışma zamanı yerleştirildiğinde ve uygulamanın davranış değiştiğinde ortaya çıkabilecek olanlardır. Hedefe göre daha yeni bir sürümde çalışırken, .NET Framework, eski hedeflenen sürümü taklit etmek için *olağandışı* davranışı kullanır. Uygulama daha yeni bir sürümde çalışır, ancak eski sürümde çalışıyor gibi davranır. .NET Framework sürümleri arasındaki uyumluluk sorunlarının birçoğu, bu olağandışı model aracılığıyla azaltıldığında. Örneğin, bir ikili dosya .NET Framework 4,0 için derlenmişse, ancak .NET Framework 4,5 veya sonraki bir sürüme sahip bir makinede çalışıyorsa, .NET Framework 4,0 uyumluluk modunda çalışır. Bu, sonraki sürümdeki birçok değişikliğin ikilisini etkilemediği anlamına gelir.

Uygulamanın hedeflediği .NET Framework sürümü, kodun çalıştığı uygulama etki alanı için giriş derlemesinin hedef sürümü tarafından belirlenir. Bu uygulama etki alanında yüklü olan tüm ek derlemeler bu sürümü hedefleyin. Örneğin, yürütülebilir dosya durumunda, yürütülebilir dosyanın hedeflediği sürüm, bu uygulama etki alanındaki tüm derlemeler altında çalışır.

Ortamınıza uygulanan çalışma zamanı değişikliklerinin bir listesini görmek için, şu anda hedeflediğiniz .NET Framework sürümünü ve ardından geçirmek istediğiniz sürümü seçin:

[!INCLUDE[versionselector](../../../includes/migration-guide/runtime/versionselector.md)]

## <a name="retargeting-changes"></a>Yeniden hedefleme değişiklikleri

Yeniden hedefleme değişiklikleri, bir derleme daha yeni bir sürümü hedeflemek için yeniden derleniyorsa ortaya çıkabilecek olanlardır. Daha yeni bir sürümü hedeflemek, derlemenin yeni özelliklerin yanı sıra eski özellikler için olası uyumluluk sorunlarını kabul etmesinin anlamına gelir.

Ortamınız için geçerli olan yeniden hedefleme değişikliklerinin listesini görmek için, şu anda hedeflendiği .NET Framework sürümünü ve ardından geçiş yapmak istediğiniz sürümü seçin:

[!INCLUDE[versionselector](../../../includes/migration-guide/retargeting/versionselector.md)]

## <a name="impact-classification"></a>Etki sınıflandırması

Çalışma zamanı ve yeniden hedefleme değişikliklerini tanımlayan konularda, örneğin, [4.7.2 ' den 4,8 ' e geçiş Için yeniden hedefleme değişiklikleri](retargeting/4.7.2-4.8.md), tek tek öğeler aşağıdaki şekilde beklenen etkilerden sınıflandırılmaktadır:

**Leri**\
Çok sayıda uygulamayı etkileyen veya kodun önemli bir şekilde değiştirilmesini gerektiren önemli bir değişiklik.

**Bazı**\
Az sayıda uygulamayı etkileyen veya küçük bir kod değişikliği gerektiren bir değişiklik.

**Kenar durumu**\
Uygulamaları, yaygın olmayan çok özel senaryolar altında etkileyen bir değişiklik.

**Gerçekletir**\
Uygulamanın geliştiricisi veya kullanıcısı üzerinde belirgin bir etkiye sahip olmayan bir değişiklik. Bu değişiklik nedeniyle uygulamada bir düzenleme yapılması gerekmez.

## <a name="see-also"></a>Ayrıca bkz.

- [Sürümler ve bağımlılıklar](versions-and-dependencies.md)
- [Yenilikler](../whats-new/index.md)
- [Artık kullanılmıyor](../whats-new/whats-obsolete.md)
