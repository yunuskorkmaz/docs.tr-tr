---
title: Teşhis araçlarına genel bakış - .NET Core
description: .NET Core uygulamalarını tanılamak için kullanılabilen araç ve tekniklere genel bakış.
ms.date: 12/17/2019
ms.topic: overview
ms.openlocfilehash: 0a78ec6c88f5323104277cddea4480a5e13b4e41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399051"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a>.NET Core'da hangi tanılama araçları mevcuttur?

Yazılım her zaman beklediğiniz gibi şekilde değil, ancak .NET Core'un bu sorunları hızlı ve etkili bir şekilde tanılamanıza yardımcı olacak araçları ve API'leri vardır.

Bu makalede, ihtiyacınız olan çeşitli araçları bulmanıza yardımcı olur.

## <a name="managed-debuggers"></a>Yönetilen hata ayıklayıcıları

[Yönetilen hata ayıklayıcıları,](managed-debuggers.md) programınızla etkileşimkurmanızı sağlar. Duraklatma, aşamalı olarak yürütme, inceleme ve devam etme, kodunuzu davranış hakkında bilgi verir. Hata ayıklama, kolayca çoğaltılabilen işlevsel sorunları tanılamak için ilk tercihtir.

## <a name="logging-and-tracing"></a>Günlüğe kaydetme ve izleme

[Günlük ve izleme](logging-tracing.md) ile ilgili tekniklerdir. Günlük dosyaları oluşturmak için enstrümanting koduna başvururlar. Dosyalar, bir programın ne yaptığının ayrıntılarını kaydeder. Bu ayrıntılar en karmaşık sorunları tanılamak için kullanılabilir. Zaman damgaları ile kombine edildiğinde, bu teknikler performans araştırmalarında da değerlidir.

## <a name="unit-testing"></a>Birim testi

[Birim testi,](../testing/index.md) sürekli tümleştirme ve yüksek kaliteli yazılım dağıtımının önemli bir bileşenidir. Birim testleri, bir şeyi kırdığınızda size erken uyarı vermek için tasarlanmıştır.

## <a name="net-core-dotnet-diagnostic-global-tools"></a>.NET Core dotnet diagnostik Global Araçlar

### <a name="dotnet-counters"></a>dotnet-counters

[dotnet sayaçları](dotnet-counters.md) birinci düzey sistem durumu izleme ve performans araştırması için bir performans izleme aracıdır. <xref:System.Diagnostics.Tracing.EventCounter> API üzerinden yayınlanan performans sayacı değerlerini gözlemler. Örneğin, CPU kullanımı veya .NET Core uygulamanızda atılan özel durumlar oranı gibi şeyleri hızla izleyebilirsiniz.

### <a name="dotnet-dump"></a>dotnet-dump

[Dotnet-dump](dotnet-dump.md) aracı, windows ve Linux çekirdek dökümlerini yerel bir hata ayıklama olmadan toplamanın ve analiz etmenin bir yoludur.

### <a name="dotnet-trace"></a>dotnet-trace

.NET Core, tanılama `EventPipe` verilerinin hangi aracılığıyla açığa çıkarılana ne denir. [Dotnet izleme](dotnet-trace.md) aracı, uygulamanızın yavaş çalışmasını neden olan senaryolarda yardımcı olabilecek ilginç profil oluşturma verilerini uygulamanızdan tüketmenize olanak tanır.

## <a name="net-core-diagnostics-tutorials"></a>.NET Core tanılama öğreticileri

### <a name="debug-a-memory-leak"></a>Bellek sızıntısında hata ayıklama

[Öğretici: Hata ayıklama bir bellek sızıntısı](debug-memory-leak.md) bulma yoluyla yürür. [Dotnet sayaçları](dotnet-counters.md) aracı sızıntıyı doğrulamak için kullanılır ve sızıntıyı teşhis etmek için [dotnet-dump](dotnet-dump.md) aracı kullanılır.
