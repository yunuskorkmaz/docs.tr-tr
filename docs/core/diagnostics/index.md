---
title: Tanılama araçlarına genel bakış-.NET Core
description: .NET Core uygulamalarını tanılamak için kullanılabilen araçlara ve tekniklere genel bakış.
ms.date: 07/16/2020
ms.topic: overview
ms.openlocfilehash: 9836ea11e7f17d6ed6e04bcba8bc0ed851bb368f
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105290"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a>.NET Core 'da hangi tanılama araçları kullanılabilir?

Yazılım her zaman beklediği gibi davranmaz, ancak .NET Core bu sorunları hızlı ve etkili bir şekilde tanılamanıza yardımcı olacak araçlar ve API 'Lere sahiptir.

Bu makale, ihtiyacınız olan çeşitli araçları bulmanıza yardımcı olur.

## <a name="managed-debuggers"></a>Yönetilen hata ayıklayıcıları

[Yönetilen hata defterleri](managed-debuggers.md) , programla etkileşime girebilmeniz için izin verir. Duraklatma, artımlı yürütme, İnceleme ve sürdürme kodunuzun davranışı hakkında fikir verir. Hata ayıklayıcı, kolayca yeniden oluşturabileceğiniz işlevsel sorunları tanılamaya yönelik ilk seçenektir.

## <a name="logging-and-tracing"></a>Günlüğe kaydetme ve izleme

[Günlüğe kaydetme ve izleme](logging-tracing.md) ilgili teknikler. Günlük dosyaları oluşturmak için kodu işaretleme bölümüne başvururlar. Dosyalar, bir programın yaptığı ayrıntıları kaydeder. Bu ayrıntılar, en karmaşık sorunları tanılamak için kullanılabilir. Zaman damgalarıyla birleştirildiğinde, bu teknikler performans araştırmaları açısından de değerlidir.

## <a name="metrics"></a>Ölçümler

[Eventcounters](event-counters.md) , performans sorunlarını belirlemek ve izlemek için ölçümler yazmanıza izin verir. Ölçümler, izlemeye kıyasla daha düşük performans yükü sağlar ve her zaman açık performans izleme için daha uygun hale gelir. .NET çalışma zamanı ve kitaplıkları, izleyebildiğiniz birkaç [iyi bilinen EventCounters](available-counters.md) yayımlar.

## <a name="unit-testing"></a>Birim testi

[Birim testi](../testing/index.md) , yüksek kaliteli yazılımların sürekli tümleştirilmesine ve dağıtımına yönelik temel bir bileşendir. Birim testleri, bir şeyi kesen bir erken uyarı sağlayacak şekilde tasarlanmıştır.

## <a name="dumps"></a>Dökümler

[Döküm](./dumps.md) , oluşturma sırasında işlemin anlık görüntüsünü içeren bir dosyadır. Bunlar, hata ayıklama amacıyla uygulamanızın durumunu incelemek için yararlı olabilir.

## <a name="symbols"></a>Simgeleri

[Semboller](./symbols.md) , kaynak kodu ile derleyici tarafından üretilen ikili arasında bir eşlemedir. Bunlar genellikle .NET hata ayıklayıcıları tarafından kaynak satır numaralarını, yerel değişken adlarını ve diğer tanılama bilgileri türlerini çözümlemek için kullanılır.

## <a name="collect-diagnostics-in-containers"></a>Kapsayıcılarda tanılama toplama

Kapsayıcısız Linux ortamlarında kullanılan aynı tanılama araçları, [kapsayıcılarda tanılamayı toplamak](diagnostics-in-containers.md)için de kullanılabilir. Araçların bir Docker kapsayıcısında çalıştığından emin olmak için birkaç kullanım değişikliği yapmanız gerekir.

## <a name="net-core-diagnostic-global-tools"></a>.NET Core tanılama küresel Araçlar

### <a name="dotnet-counters"></a>dotnet-counters

[DotNet sayaçları](dotnet-counters.md) , ilk düzey sistem durumu izleme ve performans araştırması için bir performans izleme aracıdır. API aracılığıyla yayınlanan performans sayacı değerlerini sunar <xref:System.Diagnostics.Tracing.EventCounter> . Örneğin, CPU kullanımı gibi şeyleri veya .NET Core uygulamanızda oluşturulan özel durumların oranını hızlıca izleyebilirsiniz.

### <a name="dotnet-dump"></a>dotnet-dump

[DotNet-dump](dotnet-dump.md) Aracı, yerel bir hata ayıklayıcı olmadan Windows ve Linux temel dökümlerinin toplanması ve çözümlenmesi için bir yoldur.

### <a name="dotnet-gcdump"></a>dotnet-gcdump

[DotNet-gcdump](dotnet-gcdump.md) Aracı, canlı .net işlemlerinin GC (çöp toplayıcısı) dökümlerini toplamanın bir yoludur.

### <a name="dotnet-trace"></a>dotnet-trace

.NET Core, `EventPipe` Tanılama verilerinin sunulmasına ilişkin ne DENlerin dahil olduğunu içerir. [DotNet-Trace](dotnet-trace.md) Aracı, uygulamanızın yavaş çalışan uygulamaların yavaşlamasına neden olması gereken senaryolarda yardımcı olabilecek, uygulamanızda ilgi çekici profil oluşturma verilerini kullanmanıza olanak tanır.

### <a name="dotnet-symbol"></a>dotnet-symbol

[DotNet-symbol](dotnet-symbol.md) dosyaları indirir (semboller, dac/DBI, ana bilgisayar dosyaları vb.) temel döküm veya mini döküm açmak için gereklidir. Farklı bir makinede yakalanan bir döküm dosyasında hata ayıklaması yapmak için semboller ve modüller gerekiyorsa bu aracı kullanın.

### <a name="dotnet-sos"></a>dotnet-sos

[DotNet-sos](dotnet-sos.md) , Linux ve MacOS 'A ( [WinDbg/CDB](/windows-hardware/drivers/debugger/debugger-download-tools)kullanıyorsanız Windows 'a) [sos hata ayıklama uzantısını](sos-debugging-extension.md) yükleme.

### <a name="perfcollect"></a>PerfCollect

[PerfCollect](trace-perfcollect-lttng.md) , `perf` `LTTng` Linux dağıtımları üzerinde çalışan .NET uygulamalarının daha ayrıntılı bir performans analiziyle birlikte izlemeleri toplamak için kullanabileceğiniz bir bash betiğinden oluşur.

## <a name="net-core-diagnostics-tutorials"></a>.NET Core tanılama öğreticileri

### <a name="debug-a-memory-leak"></a>Bellek sızıntısında hata ayıklama

[Öğretici:](debug-memory-leak.md) Bellek sızıntısını bulma adım bir bellek sızıntısı. Sızıntı [-Counters](dotnet-counters.md) Aracı, sızıntıyı doğrulamak için kullanılır ve sızıntı sorunlarını tanılamak için [DotNet-dump](dotnet-dump.md) aracı kullanılır.

### <a name="debug-high-cpu-usage"></a>Yüksek CPU kullanımı hatasını ayıklama

[Öğretici: hata ayıklama yüksek CPU](debug-highcpu.md) kullanımı, yüksek CPU kullanımını araştırmanıza yardımcı olur. Yüksek CPU kullanımını onaylamak için [DotNet-Counters](dotnet-counters.md) aracını kullanır. Daha sonra, CPU kullanım profilini toplamak ve görüntülemek için [Performans Analizi yardımcı programı ( `dotnet-trace` ) veya Linux için izleme](dotnet-trace.md) 'yi kullanma konusunda size kılavuzluk eder `perf` .

### <a name="debug-deadlock"></a>Çıkmaz hatasını ayıklama

[Öğretici: hata ayıklama kilitlenmesi](debug-deadlock.md) , iş parçacıklarını ve kilitleri araştırmak için [DotNet-dump](dotnet-dump.md) aracının nasıl kullanılacağını gösterir.

### <a name="debug-a-stackoverflow"></a>StackOverflow hata ayıklama

[Öğretici: StackOverflow hata ayıklama bir](debug-stackoverflow.md) Linux 'ta bir hata ayıklamanın nasıl yapılacağını gösterir <xref:System.StackOverflowException> .

### <a name="debug-linux-dumps"></a>Linux dökümlerinin hatasını ayıklama

[Linux dökümlerinde hata ayıklama](debug-linux-dumps.md) , Linux üzerinde dökümleri nasıl toplayacağınızı ve analiz edeceğinizi açıklar.

### <a name="measure-performance-using-eventcounters"></a>EventCounters kullanarak performansı ölçme

[Öğretici: .net 'Teki eventcounters kullanılarak performansı ölçmek](event-counter-perf.md) , <xref:System.Diagnostics.Tracing.EventCounter> .net uygulamanızda performansı ölçmek için API 'yi nasıl kullanacağınızı gösterir.
