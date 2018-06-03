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
ms.openlocfilehash: 31d14a8ef6a4b17eea1b9160e811bb92946d775b
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2018
ms.locfileid: "34728647"
---
# <a name="application-compatibility-in-the-net-framework"></a>.NET Framework'te Uygulama Uyumluluğu

## <a name="introduction"></a>Giriş
Uyumluluk her .NET sürüm çok önemli hedefidir. Uyumluluk her sürümü olmasını sağlar eklenebilir, bu nedenle önceki sürümleri hala çalışır. Diğer taraftan, (performansı, güvenlik sorunları gidermek veya hataları düzeltmek için) önceki işlevsellik değişiklikleri var olan kodu veya sonraki bir sürümünü altında çalışan uygulamalara uyumluluk sorunlarına neden olabilir. .NET Framework yeniden hedefleme değişiklikleri ve çalışma zamanı değişiklikleri algılar. Yeniden hedefleme değişiklikleri belirli bir .NET Framework sürümünü hedef ancak sonraki bir sürümünde çalışan uygulamaları etkiler. Çalışma zamanı değişiklikleri belirli bir sürümünde çalışan tüm uygulamaları etkiler.

Her uygulama belirli bir sürümü tarafından belirtilen .NET Framework'ün hedefler:

* Bir hedef framework Visual Studio'da tanımlama.
* Hedef Framework'ü bir proje dosyasında belirtme.
* Uygulama bir <xref:System.Runtime.Versioning.TargetFrameworkAttribute> kaynak koduna.

Ne hedeflenen daha yeni bir sürümü üzerinde çalışırken, .NET Framework hedeflenen sürümün taklit etmek üzere quirked davranışı kullanır. Diğer bir deyişle, uygulama Framework sürümü çalıştırın, ancak eski sürümünde çalışıyorsa gibi davranır. .NET Framework sürümleri arasındaki uyumluluk sorunları çoğunu bu quirking modeli aracılığıyla azalır. .NET Framework sürümünü, bir uygulama hedefleri girişi bütünleştirilmiş kodun çalışan uygulama etki alanı için hedef sürümü tarafından belirlenir. Tüm ek derlemeler uygulama etki alanı hedefleyen, .NET Framework sürümü yüklü. Örneğin, yürütülebilir olması durumunda çalıştırılabilir hedefleri çerçevedir, tüm derlemelerde AppDomain altında çalışacağı uyumluluk modu.

## <a name="runtime-changes"></a>{1&gt;Çalışma zamanı değişiklikleri&lt;1}

Çalışma zamanı sorunlarına yeni bir çalışma zamanı bir makinede yerleştirilir ve aynı ikili dosyaları çalıştırın, ancak farklı bir davranış görülen ortaya olanlardır. Bir ikili .NET Framework 4.0 için derlenmiş ise .NET Framework 4.0 uyumluluk modunda 4.5 veya sonraki sürümlerinde çalışır. 4.5 etkileyen değişiklikler çoğunu 4.0 için derlenmiş bir ikili etkilemez. Bu uygulama etki alanına özgü ve giriş derleme ayarlarına bağlıdır.

## <a name="retargeting-changes"></a>Yeniden hedefleme değişiklikleri

Yeniden hedefleme sorunları 4.0 hedefleyen bir derlemeyi artık hedef 4.5 ayarlandığında ortaya çıkan olanlardır. Artık derleme yeni özelliklerin yanı sıra eski özelliklerin olası uyumluluk sorunlarına içine kabul eder. Yeniden, bu girdi derlemesi tarafından böylece dikte edilir derleme kullanan konsol uygulaması veya bütünleştirilmiş koduna başvuruyor Web sitesi.

## <a name="net-compatibility-diagnostics"></a>.NET uyumluluğu tanılama

.NET uyumluluğu tanılama Roslyn destekli çözümleyiciler, .NET Framework sürümleri arasında uygulama uyumluluğu sorunları tanımlamaya yardımcı olan. Yalnızca bir alt özel tüm geçiş uygulanacak rağmen bu liste tüm kullanılabilir çözümleyiciler içerir. Çözümleyiciler hangi sorunların planlanan geçiş için geçerlidir ve yalnızca bu belirir belirler.

Her sorun aşağıdaki bilgileri içerir:

-   Önceki bir sürümden nelerin değiştiğini açıklaması.

-   Nasıl değişiklik müşteriler ve herhangi bir geçici çözüm sürümleri arasında uyumluluğu korumak kullanılabilir olup etkiler.

-   Değişikliğin ne kadar önemli olduğunu'nin bir değerlendirme. Uygulama uyumluluk sorunu kategorilere gibi:

    |   |   |
    |---|---|
    |Ana|Çok sayıda uygulamaları etkiler veya önemli kodunun değiştirilmesini gerektirir önemli bir değişiklik.|
    |Küçük|Az sayıda uygulamaları etkiler veya ikincil kodunun değiştirilmesini gerektiren bir değişiklik.|
    |Uç durum|Uygulamalar belirli, genel olarak görülmez senaryoları altında etkileyen bir değişiklik.|
    |Geçirgen|Bir değişiklik uygulama geliştiricisi veya kullanıcı belirgin hiçbir etkisi olmadan.|

-   Sürüm değişikliği ilk framework görüntülendiğinde gösterir. Bazı değişiklikler belirli bir sürümünde sunulan ve bir sonraki sürümde geri; Bu da gösterilir.

-   Değişiklik türü:

    |   |   |
    |---|---|
    |Yeniden hedefleme|Değişiklik yeni bir .NET Framework sürümünü hedefleyecek şekilde derlenir uygulamaları etkiler.|
    |Çalışma zamanı|Bu değişiklik, .NET Framework'ün önceki bir sürümünü hedefleyen ancak sonraki bir sürümünü çalıştıran mevcut bir uygulamayı etkiler.|

-   Etkilenen API'leri, varsa.

-   Kullanılabilir tanılama kimlikleri

## <a name="usage"></a>Kullanım
Başlamak için aşağıdaki uyumluluk değişiklik türünü seçin:

* [Yeniden Hedefleme Değişiklikleri](./retargeting/index.md)
* [Çalışma Zamanı Değişiklikleri](./runtime/index.md)


## <a name="see-also"></a>Ayrıca Bkz.

* [Sürümler ve Bağımlılıklar](../../../docs/framework/migration-guide/versions-and-dependencies.md)
* [Yenilikler](../../../docs/framework/whats-new/index.md)
* [Sınıf Kitaplığında Artık Kullanılmayanlar](../../../docs/framework/whats-new/whats-obsolete.md)
