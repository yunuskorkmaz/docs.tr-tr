---
title: Çalışma süresi ve değişiklikleri yeniden hedefleme - .NET Framework
ms.date: 10/29/2019
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
ms.openlocfilehash: c46f781d495b87a4f24e77935df7c4814c8567ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73196705"
---
# <a name="application-compatibility-in-the-net-framework"></a>.NET Çerçevesi'nde uygulama uyumluluğu

Uyumluluk her .NET sürümü için önemli bir hedeftir. Uyumluluk, her sürümün katkı maddesi olmasını sağlar, böylece önceki sürümler çalışmaya devam eder. Diğer taraftan, önceki işlevlerde yapılan değişiklikler (örneğin, performansı artırmak, güvenlik sorunlarını gidermek veya hataları gidermek için) varolan kodda veya daha sonraki bir sürüm altında çalışan varolan uygulamalarda uyumluluk sorunlarına neden olabilir.

Her uygulama .NET Framework'ün belirli bir sürümünü şu şekilde hedefler:

- Visual Studio'da bir hedef çerçevesi tanımlama.
- Proje dosyasında hedef çerçevenin belirtilmesi.
- Kaynak koduna a <xref:System.Runtime.Versioning.TargetFrameworkAttribute> uygulama.

.NET Framework'ün bir sürümünden diğerine geçiş yaparken göz önünde bulundurulması gereken iki tür değişiklik vardır:

- [Çalışma zamanı değişiklikleri](#runtime-changes)
- [Değişiklikleri yeniden hedefleme](#retargeting-changes)

## <a name="runtime-changes"></a>Çalışma zamanı değişiklikleri

Çalışma zamanı sorunları, bir makineye yeni bir çalışma zamanı yerleştirildiğinde ve uygulamanın davranış değişiklikleri olduğunda ortaya çıkan sorunlardır. .NET Framework, hedeflenenden daha yeni bir sürümde çalışırken, eski hedeflenen sürümü taklit etmek için *tuhaf davranışları* kullanır. Uygulama yeni sürümde çalışır, ancak eski sürümde çalışıyormuş gibi davranır. .NET Framework sürümleri arasındaki uyumluluk sorunlarının çoğu bu tuhafmodel aracılığıyla azaltılır. Örneğin, .NET Framework 4.0 için bir ikili derlenmişse ancak .NET Framework 4.5 veya sonraki bir makinede çalışıyorsa, .NET Framework 4.0 uyumluluk modunda çalışır. Bu, sonraki sürümdeki değişikliklerin çoğunun ikiliyi etkilemeyeceği anlamına gelir.

.NET Framework'ün bir uygulamanın hedeflenebelirlediği sürümü, kodun çalıştığı uygulama etki alanı için giriş derlemesinin hedef sürümü tarafından belirlenir. Bu uygulama etki alanına yüklenen tüm ek derlemeler bu sürümü hedeflemektedir. Örneğin, yürütülebilir bir durumda, yürütülebilir hedeflerin sürümü, bu uygulama etki alanında çalışan tüm derlemeler uyumluluk modudur.

Ortamınız için geçerli olan çalışma zamanı değişikliklerinin listesini görmek için, şu anda hedeflemekte olduğunuz .NET Framework sürümünü ve daha sonra geçiş yapmak istediğiniz sürümü seçin:

[!INCLUDE[versionselector](../../../includes/migration-guide/runtime/versionselector.md)]

## <a name="retargeting-changes"></a>Yeniden hedefleme değişiklikleri

Yeniden hedefleme değişiklikleri, derleme yeni bir sürümü hedeflemek üzere yeniden derlendiğinde ortaya çıkan değişikliklerdir. Daha yeni bir sürümü hedeflemek, derlemenin eski özellikler için olası uyumluluk sorunlarının yanı sıra yeni özellikleri de seçmesi anlamına gelir.

Ortamınız için geçerli olan yeniden hedefleme değişikliklerinin listesini görmek için, şu anda hedeflemekte olduğunuz .NET Framework sürümünü ve daha sonra geçiş yapmak istediğiniz sürümü seçin:

[!INCLUDE[versionselector](../../../includes/migration-guide/retargeting/versionselector.md)]

## <a name="impact-classification"></a>Etki sınıflandırması

Çalışma zamanı ve değişiklikleri yeniden hedeflemeyi açıklayan konularda, örneğin, [4,7.2'den 4,8'e geçiş için değişiklikleri yeniden hedeflemek,](retargeting/4.7.2-4.8.md)tek tek öğeler beklenen etkilerine göre aşağıdaki gibi sınıflandırılır:

**Büyük**\
Çok sayıda uygulamayı etkileyen veya önemli ölçüde kod değişikliği gerektiren önemli bir değişiklik.

**Küçük**\
Az sayıda uygulamayı etkileyen veya kodda küçük değişiklikler gerektiren bir değişiklik.

**Kenar kılıfı**\
Yaygın olmayan çok özel senaryolar altında uygulamaları etkileyen bir değişiklik.

**Şeffaf**\
Uygulamanın geliştiricisi veya kullanıcısı üzerinde gözle görülür bir etkisi olmayan bir değişiklik. Bu değişiklik nedeniyle uygulamada bir düzenleme yapılması gerekmez.

## <a name="see-also"></a>Ayrıca bkz.

- [Sürümler ve bağımlılıklar](versions-and-dependencies.md)
- [Yenilikler](../whats-new/index.md)
- [Ne eski](../whats-new/whats-obsolete.md)
