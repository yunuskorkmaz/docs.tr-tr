---
title: Tanılama araçlarına genel bakış-.NET Core
description: .NET Core uygulamalarını tanılamak için kullanılabilen araçlara ve tekniklere genel bakış.
ms.date: 12/17/2019
ms.topic: overview
ms.openlocfilehash: 0a78ec6c88f5323104277cddea4480a5e13b4e41
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715576"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a>.NET Core 'da hangi tanılama araçları kullanılabilir?

Yazılım her zaman beklediği gibi davranmaz, ancak .NET Core bu sorunları hızlı ve etkili bir şekilde tanılamanıza yardımcı olacak araçlar ve API 'Lere sahiptir.

Bu makale, ihtiyacınız olan çeşitli araçları bulmanıza yardımcı olur.

## <a name="managed-debuggers"></a>Yönetilen hata ayıklayıcıları

[Yönetilen hata defterleri](managed-debuggers.md) , programla etkileşime girebilmeniz için izin verir. Duraklatma, artımlı yürütme, İnceleme ve sürdürme kodunuzun davranışı hakkında fikir verir. Hata ayıklayıcı, kolayca yeniden oluşturabileceğiniz işlevsel sorunları tanılamaya yönelik ilk seçenektir.

## <a name="logging-and-tracing"></a>Günlüğe kaydetme ve izleme

[Günlüğe kaydetme ve izleme](logging-tracing.md) ilgili teknikler. Günlük dosyaları oluşturmak için kodu işaretleme bölümüne başvururlar. Dosyalar, bir programın yaptığı ayrıntıları kaydeder. Bu ayrıntılar, en karmaşık sorunları tanılamak için kullanılabilir. Zaman damgalarıyla birleştirildiğinde, bu teknikler performans araştırmaları açısından de değerlidir.

## <a name="unit-testing"></a>Birim testi

[Birim testi](../testing/index.md) , yüksek kaliteli yazılımların sürekli tümleştirilmesine ve dağıtımına yönelik temel bir bileşendir. Birim testleri, bir şeyi kesen bir erken uyarı sağlayacak şekilde tasarlanmıştır.

## <a name="net-core-dotnet-diagnostic-global-tools"></a>.NET Core DotNet tanılama küresel araçları

### <a name="dotnet-counters"></a>dotnet-counters

[DotNet sayaçları](dotnet-counters.md) , ilk düzey sistem durumu izleme ve performans araştırması için bir performans izleme aracıdır. <xref:System.Diagnostics.Tracing.EventCounter> API 'SI aracılığıyla yayınlanan performans sayacı değerlerini sunar. Örneğin, CPU kullanımı gibi şeyleri veya .NET Core uygulamanızda oluşturulan özel durumların oranını hızlıca izleyebilirsiniz.

### <a name="dotnet-dump"></a>dotnet-dump

[DotNet-dump](dotnet-dump.md) Aracı, yerel bir hata ayıklayıcı olmadan Windows ve Linux temel dökümlerinin toplanması ve çözümlenmesi için bir yoldur.

### <a name="dotnet-trace"></a>dotnet-trace

.NET Core, tanılama verilerinin açığa çıkarılabileceği `EventPipe` olarak adlandırılan öğeleri içerir. [DotNet-Trace](dotnet-trace.md) Aracı, uygulamanızın yavaş çalışan uygulamaların yavaşlamasına neden olması gereken senaryolarda yardımcı olabilecek, uygulamanızda ilgi çekici profil oluşturma verilerini kullanmanıza olanak tanır.

## <a name="net-core-diagnostics-tutorials"></a>.NET Core tanılama öğreticileri

### <a name="debug-a-memory-leak"></a>Bellek sızıntısı hatalarını ayıklama

[Öğretici:](debug-memory-leak.md) Bellek sızıntısını bulma adım bir bellek sızıntısı. Sızıntı [-Counters](dotnet-counters.md) Aracı, sızıntıyı doğrulamak için kullanılır ve sızıntı sorunlarını tanılamak için [DotNet-dump](dotnet-dump.md) aracı kullanılır.
