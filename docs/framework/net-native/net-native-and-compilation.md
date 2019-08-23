---
title: .NET Yerel ve Derleme
ms.date: 03/30/2017
ms.assetid: e38ae4f3-3e3d-42c3-a4b8-db1aa9d84f85
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1cb53818d0e12d625b0609a80b4d8473713525d0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941639"
---
# <a name="net-native-and-compilation"></a>.NET Yerel ve Derleme
The.NET Framework 'Ü hedefleyen Windows 8.1 uygulamalar ve Windows Masaüstü uygulamaları belirli bir programlama dilinde yazılır ve ara dil (IL) olarak derlenir. Çalışma zamanında tam zamanında (JıT) derleyici, bir yöntemin ilk kez yürütülmeden önce yerel makinenin yerel kodunda Il 'yi derlerken sorumludur. Buna karşılık .NET Native araç zinciri, derleme zamanında kaynak kodu yerel koda dönüştürür. Bu konu, .NET Framework uygulamalar için kullanılabilen diğer derleme teknolojileriyle .NET Native karşılaştırır ve ayrıca .NET Native, .NET ile derlenen kodda oluşan özel durumların neden olduğunu anlamanıza yardımcı olabilecek yerel kod oluşturma konusunda pratik bir genel bakış sunar. Yerel olarak JıT derlenmiş kodda oluşmaz.  
  
## <a name="net-native-generating-native-binaries"></a>.NET Native: Yerel ikililer oluşturuluyor  
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
>  .NET Native girişi, yönetilen derlemelere yazılan Il ve meta veriler olduğundan, oluşturma öncesi veya oluşturma sonrası olayları kullanarak ya da MSBuild proje dosyasını değiştirerek özel kod oluşturma veya diğer özel işlemleri de yapabilirsiniz.  
>   
>  Bununla birlikte, Il 'yi değiştiren araç kategorileri ve bu nedenle .NET araç zincirinin bir uygulamanın Il 'yi analiz etmelerini engelleme desteklenmez. Bu türün en önemli araçları, belirsizleyiciler.  
  
 Bir uygulamayı Il 'den yerel koda dönüştürme sırasında .NET Native araç zinciri aşağıdakiler gibi işlemleri gerçekleştirir:  
  
- Belirli kod yolları için, statik yerel kodla yansıma ve meta verileri temel alan kodu değiştirir. Örneğin, bir değer türü <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> yöntemi geçersiz kılmıyorsa, eşitlik için varsayılan test, değer türünün alanlarını temsil eden nesneleri almak <xref:System.Reflection.FieldInfo> için yansıma kullanır, ardından iki örnek için alan değerlerini karşılaştırır. Yerel koda derlerken .NET Native araç zinciri, alan değerlerinin statik bir karşılaştırması ile yansıma kodu ve meta verileri değiştirir.  
  
- Mümkün olduğunda, tüm meta verileri ortadan kaldırmaya çalışır.  
  
- Son uygulama derlemelerinin yalnızca uygulama tarafından çağrılan uygulama kodunu içerir. Bu özellikle, üçüncü taraf kitaplıklardaki ve .NET Framework sınıf kitaplığındaki kodu etkiler. Sonuç olarak, bir uygulama artık üçüncü taraf kitaplıklara veya tam .NET Framework sınıf kitaplığına bağlı değildir; Bunun yerine, üçüncü taraf ve .NET Framework sınıf kitaplıklarının kodu artık uygulama için yereldir.  
  
- Tam CLR 'yi, birincil olarak çöp toplayıcıyı içeren bir yeniden düzenlenmiş çalışma zamanına koyar. Yeniden düzenlenmiş çalışma zamanı, uygulamada yerel olan mrt100_app. dll adlı bir kitaplıkta bulunur ve yalnızca birkaç yüz kilobayt boyutunda. Statik bağlama, ortak dil çalışma zamanı tarafından gerçekleştirilen birçok hizmetin gereksinimini ortadan kaldırdığı için bu mümkündür.  
  
    > [!NOTE]
    > .NET Native, standart ortak dil çalışma zamanıyla aynı atık toplayıcıyı kullanır. Çöp toplayıcı .NET Native, arka plan atık toplama varsayılan olarak etkindir. Çöp toplama hakkında daha fazla bilgi için bkz. [çöp toplamanın temelleri](../../standard/garbage-collection/fundamentals.md).  
  
> [!IMPORTANT]
> .NET Native tüm uygulamayı yerel bir uygulamaya derler. Yönetilen koddan bağımsız olarak çağrılabilmesi için yerel koda bir sınıf kitaplığı içeren tek bir derlemeyi derlemenize izin vermez.  
  
 .NET Native araç zinciri tarafından üretilen elde edilen uygulama, proje dizininizin hata ayıklama veya yayınlama dizininde ILC. out adlı bir dizine yazılır. Aşağıdaki dosyalardan oluşur:  
  
- AppName >. exe, yalnızca  *\<AppName >* . dll içindeki özel `Main` bir dışarı aktarmaya denetimi aktaran bir saplama yürütülebiliri.  *\<*  
  
- AppName >. dll, tüm uygulama kodunuzu içeren bir Windows dinamik bağlantı kitaplığı ve .NET Framework sınıf kitaplığından ve bir bağımlılığı olan herhangi bir üçüncü taraf kütüphanesinden kod içerir.  *\<*  Ayrıca, Windows ile birlikte çalışmak ve uygulamanızdaki nesneleri serileştirmek için gereken kod gibi destek kodunu da içerir.  
  
- çöp toplama gibi çalışma zamanı hizmetleri sağlayan bir yeniden düzenlenmiş çalışma zamanı olan mrt100_app. dll.  
  
 Tüm bağımlılıklar, uygulamanın APPX bildirimi tarafından yakalanır.  Doğrudan appx paketinde paketlenmiş uygulama exe, dll ve mrt100_app. dll ' ye ek olarak, bu iki dosya içerir:  
  
- msvcr140_app. dll, mrt100_app. dll tarafından kullanılan C çalışma zamanı (CRT) kitaplığı. Bu, paketteki bir çerçeve başvurusuyla birlikte bulunur.  
  
- mrt100. dll. Bu kitaplık, mrt100_app. dll ' nin performansını iyileştirebilecek işlevleri içerir, ancak devamsızlığı mrt100_app. dll ' nin çalışmasına engel olmaz. Varsa, yerel makinedeki system32 dizininden yüklenir.  
  
 .NET Native araç zinciri uygulama kodunu uygulamanıza bağlar çünkü yalnızca uygulamanızın bu kodu çağırdığından emin olduğunu biliyorsa, aşağıdaki senaryolarda gereken meta veriler veya uygulama kodu uygulamanıza dahil olmayabilir:  
  
- Yansıması.  
  
- Dinamik veya geç bağlantılı çağrı.  
  
- Serileştirme ve seri durumdan çıkarma.  
  
- COM birlikte çalışma.  
  
 Gerekli meta veriler veya uygulama kodu çalışma zamanında yoksa, .NET Native çalışma zamanı bir özel durum oluşturur. Bu özel durumları engelleyebilir ve .NET Native araç zincirinin, meta verileri veya uygulama olan program öğelerini atayan bir XML dosyası olan bir [çalışma zamanı yönergeleri dosyası](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)kullanarak gerekli meta verileri ve uygulama kodunu içerdiğinden emin olabilirsiniz. kod çalışma zamanında kullanılabilir olmalıdır ve bunlara bir çalışma zamanı İlkesi atar. Aşağıda, .NET Native araç zinciri tarafından derlenen bir Windows Mağazası projesine eklenen varsayılan çalışma zamanı yönergeleri dosyası verilmiştir:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
    <Assembly Name="*Application*" Dynamic="Required All" />  
  </Application>  
</Directives>  
```  
  
 Bu, tüm türlerinin ve tüm üyelerinin tüm üyelerini, yansıma ve dinamik çağrı için uygulama paketinizdeki tüm Derlemeleriyle birlikte sunar. Ancak, .NET Framework sınıf kitaplığı derlemelerindeki türlerin yansıma veya dinamik etkinleştirmesini etkinleştirmez. Çoğu durumda, bu yeterlidir.  
  
## <a name="net-native-and-ngen"></a>.NET Native ve NGEN  
 [(Yerel görüntü Oluşturucu](../../../docs/framework/tools/ngen-exe-native-image-generator.md) (NGen) derlemeleri yerel koda derler ve yerel bilgisayardaki yerel görüntü önbelleğine yüklenir. Ancak, .NET Native gibi .NET Native yerel kod üretse de, bazı önemli yollarla farklıdır:  
  
- Belirli bir yöntem için kullanılabilir yerel görüntü yoksa, NGEN, Jtıve koda geri döner. Bu, yerel görüntülerin, NGEN 'in JıT derlemesine geri dönmesi gereken olayda meta verileri ve Il 'yi eklemeye devam etmesi gerektiği anlamına gelir. Buna karşılık .NET Native yalnızca yerel görüntüler üretir ve JıT derlemesine geri dönmemektedir. Sonuç olarak, yalnızca bazı yansıma, serileştirme ve birlikte çalışma senaryoları için gereken meta veriler korunmalıdır.  
  
- NGEN, derleme yükleme, uzaktan iletişim, birlikte çalışma, bellek yönetimi, çöp toplama ve gerektiğinde JıT derleme gibi hizmetler için tam ortak dil çalışma zamanına güvenmeye devam etmektedir. .NET Native, bu hizmetlerin çoğu gereksiz (JıT derleme) veya derleme zamanında çözümlenir ve uygulama derlemesinde birleştirilir. En önemlisi çöp toplama olan kalan hizmetler, mrt100_app. dll adında çok daha küçük bir yeniden düzenlenmiş çalışma zamanına dahildir.  
  
- NGEN görüntüleri kırılacak şekilde eğilimlidir. Örneğin, bir bağımlılık için bir düzeltme eki veya değişiklik genellikle onu kullanan derlemelerin de yeniden NGENed içeren olmasını gerektirir. Bu, özellikle .NET Framework sınıf kitaplığındaki sistem derlemelerinin bir doğrudur. Buna karşılık .NET Native, uygulamaların birbirinden bağımsız olarak sunulmasını sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veriler ve Kendiliğinden Açıklayıcı Bileşenler](../../standard/metadata-and-self-describing-components.md)
- [.NET Native içinde (Channel 9 Videosu)](https://channel9.msdn.com/Shows/Going+Deep/Inside-NET-Native)
- [Yansıma ve .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)
- [.NET Native Genel Sorun Giderme](../../../docs/framework/net-native/net-native-general-troubleshooting.md)
