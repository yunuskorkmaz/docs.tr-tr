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
ms.openlocfilehash: 56f0ebccc1bd46a26b5247ac2668e963cbeac828
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106481"
---
# <a name="application-compatibility-in-the-net-framework"></a>.NET Framework'te Uygulama Uyumluluğu

## <a name="introduction"></a>Giriş
Uyumluluk, her bir .NET sürümünün çok önemli bir hedefidir. Uyumluluk, her sürümün eklenebilir olmasını sağlar, bu nedenle önceki sürümler çalışmaya devam edecektir. Öte yandan, önceki işlevlerde yapılan değişiklikler (performansı artırmak, güvenlik sorunlarını gidermek veya hataları gidermek için), mevcut koddaki veya sonraki bir sürümde çalışan mevcut uygulamalarda uyumluluk sorunlarına neden olabilir. .NET Framework yeniden hedefleme değişikliklerini ve çalışma zamanı değişikliklerini tanır. Yeniden hedefleme değişiklikleri, .NET Framework belirli bir sürümünü hedefleyen, ancak sonraki bir sürümde çalışan uygulamaları etkiler. Çalışma zamanı değişiklikleri, belirli bir sürümde çalışan tüm uygulamaları etkiler.

Her uygulama, tarafından belirtilebilen .NET Framework belirli bir sürümünü hedefler:

- Visual Studio 'da hedef çerçeve tanımlama.
- Hedef Framework bir proje dosyasında belirtiliyor.
- <xref:System.Runtime.Versioning.TargetFrameworkAttribute> Kaynak koda uygulama.

Hedeflenenden daha yeni bir sürümde çalışırken, .NET Framework, eski hedeflenen sürümü taklit etmek için olağandışı davranışı kullanır. Diğer bir deyişle, uygulama Framework 'ün daha yeni bir sürümünde çalışır, ancak eski sürümde çalışıyor gibi davranır. .NET Framework sürümleri arasındaki uyumluluk sorunlarının birçoğu, bu olağandışı model aracılığıyla azaltıldığında. Uygulamanın hedeflediği .NET Framework sürümü, kodun üzerinde çalıştığı uygulama etki alanı için giriş derlemesinin hedef sürümüne göre belirlenir. Bu uygulama etki alanı hedefine yüklenen ve .NET Framework sürümü olan tüm ek derlemeler. Örneğin, yürütülebilir dosya olması durumunda, çalıştırılabilir hedef çerçeve, uygulama etki alanındaki tüm derlemeler altında çalışır.

## <a name="runtime-changes"></a>{1&gt;Çalışma zamanı değişiklikleri&lt;1}

Çalışma zamanı sorunları, bir makineye yeni bir çalışma zamanı yerleştirildiğinde ve aynı ikililerin çalıştırılmasından, ancak farklı davranışların görüldüğünde ortaya çıkan olanlardır. .NET Framework 4,0 için bir ikili derlenmişse, 4,5 veya sonraki sürümlerde .NET Framework 4,0 uyumluluk modunda çalıştırılır. 4,5 ' i etkileyen birçok değişikliğin birçoğu, 4,0 için derlenen ikiliyi etkilemez. Bu, AppDomain 'e özeldir ve giriş derlemesinin ayarlarına bağlıdır.

## <a name="retargeting-changes"></a>Yeniden hedefleme değişiklikleri

Yeniden hedefleme sorunları, 4,0 hedefleyen bir derleme artık Target 4,5 olarak ayarlandığında ortaya çıkan sorunlardır. Artık derleme, yeni özelliklerin yanı sıra eski özelliklere yönelik olası uyumluluk sorunlarını da giderir. Bu, giriş derlemesi tarafından belirlenir, bu nedenle derlemeyi kullanan konsol uygulaması veya derlemeye başvuran web sitesi.

## <a name="net-compatibility-diagnostics"></a>.NET uyumluluk tanılaması

.NET uyumluluk Tanılaması, .NET Framework sürümleri arasındaki uygulama uyumluluk sorunlarını belirlemenize yardımcı olan Roslyn destekli çözümleyiciler. Bu liste tüm çözümleyiciler içerir, ancak belirli bir geçişe yalnızca bir alt küme uygulanacaktır. Çözümleyiciler, planlı geçiş için geçerli olan sorunları tespit eder ve yalnızca bunları yüzey olarak görür.

Her sorun aşağıdaki bilgileri içerir:

- Önceki sürümden nelerin değiştiğini açıklama.

- Değişikliğin müşterileri nasıl etkilediği ve sürümler arasında uyumluluğu korumak için herhangi bir geçici çözüm olup olmadığı.

- Değişikliğin ne kadar önemli olduğunu gösteren bir değerlendirme. Uygulama uyumluluğu sorunu şöyle kategorize edilir:

    |   |   |
    |---|---|
    |Ana|Çok sayıda uygulamayı etkileyen veya kodun önemli bir şekilde değiştirilmesini gerektiren önemli bir değişiklik.|
    |İkincil|Az sayıda uygulamayı etkileyen veya küçük bir kod değişikliği gerektiren bir değişiklik.|
    |Uç durum|Uygulamaları çok özel, yaygın olmayan senaryolar altında etkileyen bir değişiklik.|
    |Geçirgen|Uygulamanın geliştiricisi veya kullanıcısı üzerinde belirgin bir etkiye sahip olmayan bir değişiklik.|

- Sürüm, değişikliğin çerçevede ilk kez göründüğünü gösterir. Bazı değişiklikler belirli bir sürümde tanıtılmıştır ve sonraki bir sürümde geri döndürülür; Bu da belirtilir.

- Değişiklik türü:

    |   |   |
    |---|---|
    |Yeniden Hedefleme|Değişiklik, .NET Framework yeni bir sürümünü hedeflemek için yeniden derlenen uygulamaları etkiler.|
    |Çalışma zamanı|Değişiklik, .NET Framework önceki bir sürümünü hedefleyen, ancak sonraki bir sürümde çalışan mevcut bir uygulamayı etkiler.|

- Varsa, etkilenen API 'ler.

- Kullanılabilir tanılamaların kimlikleri

## <a name="usage"></a>Kullanım
Başlamak için, aşağıdaki uyumluluk değişikliği türünü seçin:

- [Yeniden Hedefleme Değişiklikleri](./retargeting/index.md)
- [Çalışma Zamanı Değişiklikleri](./runtime/index.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Sürümler ve Bağımlılıklar](../../../docs/framework/migration-guide/versions-and-dependencies.md)
- [Yenilikler](../../../docs/framework/whats-new/index.md)
- [Sınıf Kitaplığında Artık Kullanılmayanlar](../../../docs/framework/whats-new/whats-obsolete.md)
