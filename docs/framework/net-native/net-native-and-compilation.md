---
title: .NET Yerel ve Derleme
ms.date: 03/30/2017
ms.assetid: e38ae4f3-3e3d-42c3-a4b8-db1aa9d84f85
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd02320f9b899f339efa149838547fd05d1b4079
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61867165"
---
# <a name="net-native-and-compilation"></a>.NET Yerel ve Derleme
Windows 8.1 uygulamaları ve.NET Framework belirli bir programlama diliyle yazılmış ve Ara dile (IL) derlenir hedefleyen Windows Masaüstü uygulamaları. Çalışma zamanında, just-ın-time (JIT) derleyici ilk kez bir yöntem yalnızca yürütülmeden önce IL yerel makine için yerel koda derlemek için sorumludur. Buna karşılık, .NET Native araç zinciri, kaynak kodu için yerel kod derleme zamanında dönüştürür. Bu konu, .NET Framework uygulamaları için kullanılabilir diğer derleme teknolojileriyle .NET Native karşılaştırır ve ayrıca neden kodda oluşan özel durumlar, .NET ile derlenmiş anlamanıza yardımcı olabilecek yerel kod .NET Native'nasıl üretir genel ile ilgili pratik bir bakış sağlar Yerel, JIT olarak derlenmiş kodda gerçekleşmez.  
  
## <a name="net-native-generating-native-binaries"></a>.NET yerel: Yerel ikili dosyaları oluşturma  
 .NET Framework hedefleyen ve değil derlendiğinde, .NET Native araç zinciri kullanarak bir uygulama aşağıdakileri içeren uygulama derlemenin oluşur:  
  
- [Meta veri](../../../docs/standard/metadata-and-self-describing-components.md) derleme, bağımlılıkları, içerdiği türlerini ve üyelerini açıklar. Meta veriler, yansıma ve geç bağlama erişimi ve bazı durumlarda da derleyicisi ve derleme araçları tarafından kullanılır.  
  
- Uygulama kodu. Bu Ara dil (IL) işlem oluşur. Çalışma zamanında, just-ın-time (JIT) derleyici, hedef platform için yerel koda çevirir.  
  
 Ek olarak, ana uygulama derlemesine, bir uygulama aşağıdaki mevcut olması gerekir:  
  
- Tüm ek sınıf kitaplıkları veya uygulamanızın gerektirdiği üçüncü taraf derlemeler. Bu derlemeler benzer şekilde tüm tür üyeleri uygulayan IL yanı sıra, derleme, türlerinin ve üyelerinin açıklayan meta veriler içerir.  
  
- .NET Framework sınıf kitaplığı. .NET Framework yüklemesi ile yerel sistemde yüklü bir bütünleştirilmiş kod koleksiyonunu budur. .NET Framework sınıf kitaplığında bulunan derlemeler meta veri ve uygulama kodu eksiksiz bir kümesini içerir.  
  
- Ortak dil çalışma zamanı. Derleme yükleme gibi hizmetleri gerçekleştirmek dinamik bağlantı kitaplıkları koleksiyonunu, bellek yönetimi ve çöp toplama, özel durum işleme, just-in-time derleme, uzaktan iletişim ve birlikte çalışabilirliği budur. Sınıf kitaplığı gibi çalışma zamanını yerel sistem .NET Framework yüklemesinin bir parçası olarak yüklenir.  
  
 Tüm ortak dil çalışma zamanı, yanı sıra meta veri ve IL tüm türleri için uygulamaya özgü derlemelerini, üçüncü taraf derlemeler ve sistem derlemeleri uygulama başarıyla yürütmek mevcut olması gerektiğini unutmayın.  
  
## <a name="net-native-and-just-in-time-compilation"></a>.NET native ve tam zamanında derleme  
 Windows mağazası uygulaması tarafından oluşturulan giriştir .NET Native araç zinciri için C# veya Visual Basic Derleyicisi. Diğer bir deyişle, dil derleyici bir Windows Store uygulaması derleme tamamlandığında .NET Native araç zinciri yürütmeyi başlatır.  
  
> [!TIP]
>  .NET Native girişi Yönetilen derlemeler için yazılan meta veri ve IL olduğundan, derleme öncesi veya derleme sonrası olayları kullanarak veya MSBuild proje dosyasını değiştirerek hala özel kod oluşturma veya başka özel işlemler'i gerçekleştirebilirsiniz.  
>   
>  Ancak, IL değiştiren ve böylece uygulamanın IL çözümleme gelen .NET araç zincirinizi önlemek araç kategorisine desteklenmez. Obfuscators, bu tür en önemli araçlardır.  
  
 .NET Native araç zinciri, yerel kod için IL bir uygulama dönüştürme sırasında aşağıdaki gibi işlemleri gerçekleştirir:  
  
- Belirli kod yolları, yansıma ve meta verileri statik yerel kodla dayanan kodu değiştirir. Örneğin, bir değer türü geçersiz <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> yöntemi, varsayılan eşitlik için test yansıma almak için kullanır <xref:System.Reflection.FieldInfo> değer tür alanları temsil eden nesneleri, ardından iki örneği alan değerlerini karşılaştırır. Yerel kod için derleme yaparken, .NET Native araç zinciri yansıma kod ve meta verileri statik alan değerlerini karşılaştırması ile değiştirir.  
  
- Mümkünse, tüm meta verileri ortadan kaldırmak çalışır.  
  
- Bu son uygulama derlemeleri, uygulama tarafından gerçekte çağrılan uygulama kodunu içerir. Bu, özellikle kod üçüncü taraf kitaplıkları ve .NET Framework sınıf kitaplığındaki etkiler. Sonuç olarak, artık bir uygulama, üçüncü taraf kitaplıklar ya da tam .NET Framework sınıf kitaplığı bağlıdır; Bunun yerine, üçüncü taraf ve .NET Framework sınıf kitaplıkları şimdi uygulamada kodudur.  
  
- Tam CLR çöp toplayıcı öncelikli olarak içeren bir UIMap'e yeniden işlenmiş çalışma zamanı ile değiştirir. Uygulamada ve yalnızca birkaç yüz kilobayt cinsinden boyutu mrt100_app.dll adlı bir kitaplıkta UIMap'e yeniden işlenmiş çalışma zamanı bulunamadı. Statik bağlama ortak dil çalışma zamanı tarafından gerçekleştirilen hizmetlere yönelik ihtiyacı ortadan kaldırdığından mümkündür.  
  
    > [!NOTE]
    >  .NET yerel standart ortak dil çalışma zamanı aynı çöp toplayıcı kullanır. .NET Native atık toplayıcısı'nda, arka plan çöp toplama, varsayılan olarak etkindir. Çöp toplama hakkında daha fazla bilgi için bkz: [çöp toplamanın Temelleri](../../../docs/standard/garbage-collection/fundamentals.md).  
  
> [!IMPORTANT]
>  .NET native, yerel bir uygulama için tüm bir uygulamayı derler. Bu, yerel koda bir sınıf kitaplığı içerir ve böylece bağımsız olarak yönetilen koddan çağrılabilir tek bir derleme olarak derlemek izin vermez.  
  
 .NET Native araç zinciri tarafından üretilen sonuç uygulamayı hata ayıklama veya sürüm dizininde, proje dizininizin ilc.out adlı bir dizin yazılır. Bunu, aşağıdaki dosyalardan oluşur:  
  
- *\<appName >*.exe, yalnızca aktarımları için özel bir denetim bir saplama yürütülebilir `Main` olarak dışa  *\<uygulamaadı >*.dll.  
  
- *\<appName >*.dll, Windows dinamik bağlantı kitaplığı tüm uygulama kodunuzu içeren yanı sıra kodu .NET Framework sınıf kitaplığı ve bağımlılığa sahip herhangi bir üçüncü taraf kitaplıklar.  Uygulamanızı Windows ile çalışmak için ve seri hale getirmek için gereken kod nesneleri gibi destek kodunu da içerir.  
  
- mrt100_app.dll, atık toplama gibi çalışma zamanı hizmetleri sağlayan UIMap'e yeniden işlenmiş bir çalışma zamanı'nı tıklatın.  
  
 Tüm bağımlılıkları yakalanan tarafından uygulamanın APPX bildirimi.  Uygulama exe, dll ve mrt100_app.dll, ek olarak, appx paketi doğrudan paket, bu iki daha fazla dosya içerir:  
  
- msvcr140_app.dll, mrt100_app.dll tarafından kullanılan C çalışma zamanı (CRT) Kitaplığı'nı tıklatın. Paket framework başvuru olarak dahil edilir.  
  
- mrt100.dll. Yokluğu mrt100_app.dll çalışmasını engellemez, ancak bu kitaplığı mrt100_app.dll, performansı artırabilir işlevleri içerir. Varsa, yerel makinede system32 dizininden yüklenir.  
  
 Yalnızca uygulamanızı aslında bu kodu çağırır bilir, .NET Native araç zinciri uygulama kodu uygulamanıza bağlantılar nedeniyle meta veriler ya da aşağıdaki senaryolarda gerekli uygulama kodunu uygulamanızla birlikte olmayabilir:  
  
- Yansıma.  
  
- Dinamik ya da geç bağlanan çağırma.  
  
- Serileştirme ve seri durumundan çıkarma.  
  
- COM birlikte çalışma.  
  
 Gerekli meta veriler veya uygulama kodu yoksa çalışma zamanında .NET yerel çalışma zamanı bir özel durum oluşturur. Bu özel durumları engellemek ve .NET Native araç zinciri kullanarak gerekli meta verileri ve uygulama kodu içerdiğinden emin bir [çalışma zamanı yönergeleri dosyası](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md), olan meta verileri program öğelerini belirten bir XML dosyası veya uygulama kodu çalışma zamanında kullanılabilir olması gerekir ve bunlara bir çalışma zamanı ilkesini atar. .NET Native araç zinciri tarafından derlenmiş bir Windows Store projesi eklenir varsayılan çalışma zamanı yönergeleri dosyası aşağıda verilmiştir:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
    <Assembly Name="*Application*" Dynamic="Required All" />  
  </Application>  
</Directives>  
```  
  
 Bu, tüm üyeleri, uygulama paketinizle yansıma ve dinamik çağrı için tüm derlemelerde yanı sıra tüm türleri sağlar. Bununla birlikte, yansıma ve .NET Framework sınıf kitaplığı bütünleştirilmiş kodlar içindeki türleri dinamik etkinleştirme etkinleştirmez. Çoğu durumda, bu yeterlidir.  
  
## <a name="net-native-and-ngen"></a>.NET native ve NGEN  
 [(Yerel Görüntü Oluşturucu](../../../docs/framework/tools/ngen-exe-native-image-generator.md) (NGEN) bütünleştirilmiş kodları yerel koda derleyen ve yerel bilgisayarda yerel görüntü önbelleğine yükler. NGEN, .NET Native gibi yerel kod üretir olsa da, ancak bunu .NET Native bazı önemli fark vardır:  
  
- Belirli bir yöntem için hiçbir yerel görüntü varsa, NGEN JITing koda geri döner. Başka bir deyişle, yerel görüntüler NGEN JIT derlemesine geri döner gerekiyor durumunda olay meta veri ve IL içerecek şekilde devam etmelidir. Buna karşılık, .NET Native yalnızca yerel görüntüler oluşturur ve JIT derlemesine geri karşılık gelmiyor. Sonuç olarak, yalnızca bazı yansıma, seri hale getirme ve birlikte çalışabilirlik senaryolarında gerekli meta veriler korunmalıdır.  
  
- Derleme yükleme, uzak hizmet, birlikte çalışma, bellek yönetimi, çöp toplama gibi hizmetler için tam ortak dil çalışma zamanı kullanan NGEN devam eder ve gerekirse, JIT derlemesi. .NET Native bu hizmetlerin çoğu ya da gereksiz (JIT) olan veya oluşturma zamanında çözümlendi ve uygulama derlemeye dahil. Çöp toplama en önemli olan, kalan hizmet mrt100_app.dll adlı bir çok daha küçük, işlenmiş çalışma zamanında dahil edilir.  
  
- NGEN görüntülerinin, kırılgan olma eğilimindedir. Örneğin, bir düzeltme veya bir bağımlılık değişikliği genellikle kullanılmakta olan derlemeleri de yeniden NGENed olmasını gerektirir. Bu, özellikle .NET Framework Sınıf Kitaplığı'nda system derlemeleri geçerlidir. Buna karşılık, .NET Native uygulamaların birbirinden bağımsız olarak sunulabilir izin verir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veriler ve Kendiliğinden Açıklayıcı Bileşenler](../../../docs/standard/metadata-and-self-describing-components.md)
- [İçinde .NET yerel (kanal 9 videosu)](https://channel9.msdn.com/Shows/Going+Deep/Inside-NET-Native)
- [Yansıma ve .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)
- [.NET Native Genel Sorun Giderme](../../../docs/framework/net-native/net-native-general-troubleshooting.md)
