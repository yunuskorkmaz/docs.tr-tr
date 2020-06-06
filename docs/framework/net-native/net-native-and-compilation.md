---
title: .NET Yerel ve Derleme
ms.date: 03/30/2017
ms.assetid: e38ae4f3-3e3d-42c3-a4b8-db1aa9d84f85
ms.openlocfilehash: cf5c9f05b2f2cb4ca15e4add5b53bc9bdca757a3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128252"
---
# <a name="net-native-and-compilation"></a>.NET Yerel ve Derleme

The.NET Framework 'Ü hedefleyen Windows 8.1 uygulamalar ve Windows Masaüstü uygulamaları belirli bir programlama dilinde yazılır ve ara dil (IL) olarak derlenir. Çalışma zamanında tam zamanında (JıT) derleyici, bir yöntemin ilk kez yürütülmeden önce yerel makinenin yerel kodunda Il 'yi derlerken sorumludur. Buna karşılık .NET Native araç zinciri, derleme zamanında kaynak kodu yerel koda dönüştürür. Bu konu, .NET Framework uygulamalar için kullanılabilen diğer derleme teknolojileriyle .NET Native karşılaştırılır ve ayrıca, .NET Native ile derlenen kodda oluşan özel durumların JıT kodlu kodda gerçekleşmediğini anlamanıza yardımcı olabilecek, .NET Native yerel kod üretmesine yönelik pratik bir genel bakış sunar.

## <a name="net-native-generating-native-binaries"></a>.NET Native: yerel ikili dosyalar oluşturma

.NET Framework hedefleyen ve .NET Native araç zinciri kullanılarak derlenmediği bir uygulama, aşağıdakiler de dahil olmak üzere uygulama derlemenizin oluşur:

- Derlemeyi, onun bağımlılıklarını, içerdiği türleri ve üyelerini açıklayan [meta veriler](../../standard/metadata-and-self-describing-components.md) . Meta veriler, yansıma ve geç bağlantılı erişim için ve bazı durumlarda derleyici ve derleme araçlarının yanı sıra kullanılır.

- Uygulama kodu. Bu, ara dil (IL) opkodlardan oluşur. Çalışma zamanında, tam zamanında (JıT) derleyici, hedef platform için yerel koda dönüştürür.

 Ana uygulama derlemenizin yanı sıra, bir uygulama aşağıdakilerin bulunmasını gerektirir:

- Uygulamanız için gerekli olan tüm ek sınıf kitaplıkları veya üçüncü taraf derlemeleri. Bu derlemeler benzer şekilde derlemeyi, türlerini ve üyelerini açıklayan meta verileri ve tüm tür üyelerini uygulayan Il 'yi içerir.

- .NET Framework sınıf kitaplığı. Bu, .NET Framework yüklemesiyle yerel sisteme yüklenmiş derlemelerin bir koleksiyonudur. .NET Framework sınıf kitaplığına dahil olan derlemeler, tüm meta veri ve uygulama kodu kümesini içerir.

- Ortak dil çalışma zamanı. Bu, derleme yükleme, bellek yönetimi ve çöp toplama, özel durum işleme, tam zamanında derleme, uzaktan iletişim ve birlikte çalışma gibi hizmetleri gerçekleştiren dinamik bağlantı kitaplıkları koleksiyonudur. Sınıf kitaplığı gibi, çalışma zamanı, .NET Framework yüklemesinin bir parçası olarak yerel sisteme yüklenir.

Uygulamanın başarıyla yürütülmesi için tüm ortak dil çalışma zamanının ve uygulamaya özel derlemelerde, üçüncü taraf derlemelerde ve sistem derlemelerinin tüm türlerin meta verileri ve Il 'nin mevcut olması gerektiğini unutmayın.

## <a name="net-native-and-just-in-time-compilation"></a>.NET Native ve tam zamanında derleme

.NET Native araç zinciri girişi, C# veya Visual Basic Derleyicisi tarafından oluşturulan Windows Mağazası uygulamasıdır. Diğer bir deyişle, dil derleyicisi bir Windows Mağazası uygulamasının derlemesini tamamladığında .NET Native araç zinciri yürütmeye başlar.

> [!TIP]
> .NET Native girişi, yönetilen derlemelere yazılan Il ve meta veriler olduğundan, oluşturma öncesi veya oluşturma sonrası olayları kullanarak ya da MSBuild proje dosyasını değiştirerek özel kod oluşturma veya diğer özel işlemleri de yapabilirsiniz.
>
> Bununla birlikte, Il 'yi değiştiren araç kategorileri ve bu nedenle .NET araç zincirinin bir uygulamanın Il 'yi analiz etmelerini engelleme desteklenmez. Bu türün en önemli araçları, belirsizleyiciler.

Bir uygulamayı Il 'den yerel koda dönüştürme sırasında .NET Native araç zinciri aşağıdakiler gibi işlemleri gerçekleştirir:

- Belirli kod yolları için, statik yerel kodla yansıma ve meta verileri temel alan kodu değiştirir. Örneğin, bir değer türü yöntemi geçersiz kılmıyorsa <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> , eşitlik için varsayılan test, <xref:System.Reflection.FieldInfo> değer türünün alanlarını temsil eden nesneleri almak için yansıma kullanır, ardından iki örnek için alan değerlerini karşılaştırır. Yerel koda derlerken .NET Native araç zinciri, alan değerlerinin statik bir karşılaştırması ile yansıma kodu ve meta verileri değiştirir.

- Mümkün olduğunda, tüm meta verileri ortadan kaldırmaya çalışır.

- Son uygulama derlemelerinin yalnızca uygulama tarafından çağrılan uygulama kodunu içerir. Bu özellikle, üçüncü taraf kitaplıklardaki ve .NET Framework sınıf kitaplığındaki kodu etkiler. Sonuç olarak, bir uygulama artık üçüncü taraf kitaplıklara veya tam .NET Framework sınıf kitaplığına bağlı değildir; Bunun yerine, üçüncü taraf ve .NET Framework sınıf kitaplıklarının kodu artık uygulama için yereldir.

- Tam CLR 'yi, birincil olarak çöp toplayıcıyı içeren bir yeniden düzenlenmiş çalışma zamanına koyar. Yeniden düzenlenmiş çalışma zamanı, uygulamada yerel olan mrt100_app. dll adlı bir kitaplıkta bulunur ve yalnızca birkaç yüz kilobayt boyutunda. Statik bağlama, ortak dil çalışma zamanı tarafından gerçekleştirilen birçok hizmetin gereksinimini ortadan kaldırdığı için bu mümkündür.

  > [!NOTE]
  > .NET Native, standart ortak dil çalışma zamanıyla aynı atık toplayıcıyı kullanır. Çöp toplayıcı .NET Native, arka plan atık toplama varsayılan olarak etkindir. Çöp toplama hakkında daha fazla bilgi için bkz. [çöp toplamanın temelleri](../../standard/garbage-collection/fundamentals.md).

> [!IMPORTANT]
> .NET Native tüm uygulamayı yerel bir uygulamaya derler. Yönetilen koddan bağımsız olarak çağrılabilmesi için yerel koda bir sınıf kitaplığı içeren tek bir derlemeyi derlemenize izin vermez.

.NET Native araç zinciri tarafından üretilen elde edilen uygulama, proje dizininizin hata ayıklama veya yayınlama dizininde ILC. out adlı bir dizine yazılır. Aşağıdaki dosyalardan oluşur:

- *\<appName>*. exe, denetimi yalnızca. dll içindeki özel bir dışarı aktarmaya aktaran bir saplama yürütülebiliri `Main` *\<appName>* .

- *\<appName>*. dll, tüm uygulama kodunuzu içeren bir Windows dinamik bağlantı kitaplığı ve .NET Framework sınıf kitaplığından kod ve bir bağımlılığı olan tüm üçüncü taraf kitaplıkları.  Ayrıca, Windows ile birlikte çalışmak ve uygulamanızdaki nesneleri serileştirmek için gereken kod gibi destek kodunu da içerir.

- çöp toplama gibi çalışma zamanı hizmetleri sağlayan bir yeniden düzenlenmiş çalışma zamanı olan mrt100_app. dll.

 Tüm bağımlılıklar, uygulamanın APPX bildirimi tarafından yakalanır.  Doğrudan appx paketinde paketlenmiş uygulama exe, dll ve mrt100_app. dll ' ye ek olarak, bu iki dosya içerir:

- mrt100_app. dll tarafından kullanılan C çalışma zamanı (CRT) kitaplığı msvcr140_app. dll. Bu, paketteki bir çerçeve başvurusuyla birlikte bulunur.

- mrt100. dll. Bu kitaplık mrt100_app. dll ' nin performansını iyileştirebilen işlevleri içerir, ancak devamsızlığı mrt100_app. dll ' nin çalışmasını engellemez. Varsa, yerel makinedeki system32 dizininden yüklenir.

.NET Native araç zinciri uygulama kodunu uygulamanıza bağlar çünkü yalnızca uygulamanızın bu kodu çağırdığından emin olduğunu biliyorsa, aşağıdaki senaryolarda gereken meta veriler veya uygulama kodu uygulamanıza dahil olmayabilir:

- Yansıması.

- Dinamik veya geç bağlantılı çağrı.

- Serileştirme ve seri durumdan çıkarma.

- COM birlikte çalışma.

Gerekli meta veriler veya uygulama kodu çalışma zamanında yoksa, .NET Native çalışma zamanı bir özel durum oluşturur. Bu özel durumları engelleyebilir ve .NET Native araç zincirinin, bir [çalışma zamanı yönergeleri dosyası](runtime-directives-rd-xml-configuration-file-reference.md)kullanarak gerekli meta verileri ve uygulama kodunu içerdiğinden emin olabilirsiniz. meta verileri veya uygulama kodu çalışma zamanında kullanılabilir olması gereken program öğelerini atayan bir XML dosyası ve bunlara bir çalışma zamanı İlkesi atar. Aşağıda, .NET Native araç zinciri tarafından derlenen bir Windows Mağazası projesine eklenen varsayılan çalışma zamanı yönergeleri dosyası verilmiştir:

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
    <Assembly Name="*Application*" Dynamic="Required All" />
  </Application>
</Directives>
```

Bu, tüm türlerinin ve tüm üyelerinin tüm üyelerini, yansıma ve dinamik çağrı için uygulama paketinizdeki tüm Derlemeleriyle birlikte sunar. Ancak, .NET Framework sınıf kitaplığı derlemelerindeki türlerin yansıma veya dinamik etkinleştirmesini etkinleştirmez. Çoğu durumda, bu yeterlidir.

## <a name="net-native-and-ngen"></a>.NET Native ve NGEN

[(Yerel görüntü Oluşturucu](../tools/ngen-exe-native-image-generator.md) (NGen) derlemeleri yerel koda derler ve yerel bilgisayardaki yerel görüntü önbelleğine yüklenir. Ancak, .NET Native gibi .NET Native yerel kod üretse de, bazı önemli yollarla farklıdır:

- Belirli bir yöntem için kullanılabilir yerel görüntü yoksa, NGEN, Jtıve koda geri döner. Bu, yerel görüntülerin, NGEN 'in JıT derlemesine geri dönmesi gereken olayda meta verileri ve Il 'yi eklemeye devam etmesi gerektiği anlamına gelir. Buna karşılık .NET Native yalnızca yerel görüntüler üretir ve JıT derlemesine geri dönmemektedir. Sonuç olarak, yalnızca bazı yansıma, serileştirme ve birlikte çalışma senaryoları için gereken meta veriler korunmalıdır.

- NGEN, derleme yükleme, uzaktan iletişim, birlikte çalışma, bellek yönetimi, çöp toplama ve gerektiğinde JıT derleme gibi hizmetler için tam ortak dil çalışma zamanına güvenmeye devam etmektedir. .NET Native, bu hizmetlerin çoğu gereksiz (JıT derleme) veya derleme zamanında çözümlenir ve uygulama derlemesinde birleştirilir. En önemlisi çöp toplama olan kalan hizmetler, mrt100_app. dll adlı yeniden düzenlenmiş çalışma zamanına çok daha küçük bir çalışma zamanına dahildir.

- NGEN görüntüleri kırılacak şekilde eğilimlidir. Örneğin, bir bağımlılık için bir düzeltme eki veya değişiklik genellikle onu kullanan derlemelerin de yeniden NGENed içeren olmasını gerektirir. Bu, özellikle .NET Framework sınıf kitaplığındaki sistem derlemelerinin bir doğrudur. Buna karşılık .NET Native, uygulamaların birbirinden bağımsız olarak sunulmasını sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- [Meta veriler ve kendi kendine açıklama bileşenleri](../../standard/metadata-and-self-describing-components.md)
- [.NET Native içinde (Channel 9 Videosu)](https://channel9.msdn.com/Shows/Going+Deep/Inside-NET-Native)
- [Yansıma ve .NET Yerel](reflection-and-net-native.md)
- [.NET Yerel Genel Sorun Giderme](net-native-general-troubleshooting.md)
