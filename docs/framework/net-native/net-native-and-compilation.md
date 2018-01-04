---
title: .NET Yerel ve Derleme
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e38ae4f3-3e3d-42c3-a4b8-db1aa9d84f85
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d86d8a740aa0597a21c6665ee722f4a601dec9bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="net-native-and-compilation"></a>.NET Yerel ve Derleme
Windows 8.1 uygulamaları ve.NET Framework belirli bir programlama dilinde yazılmıştır ve Ara dile (IL) derlenmiş hedef Windows Masaüstü uygulamaları. Çalışma zamanında bir yöntem ilk kez yalnızca yürütülmeden önce IL yerel makine için yerel koda derlemek için tam zamanında (JIT) derleyici sorumludur. Buna karşılık, .NET yerel araç zinciri, kaynak kodu için yerel kodu derleme zamanında dönüştürür. Bu konu, .NET Framework uygulamaları için kullanılabilir diğer derleme teknolojileriyle .NET yerel karşılaştırır ve ayrıca neden .NET ile kodda oluşan özel durumlar derlenip anlamanıza yardımcı olabilir yerel kod .NET Native'nasıl üreten bir pratik genel bakış sağlar Yerel JIT derlenmiş kodda gerçekleşmez.  
  
## <a name="net-native-generating-native-binaries"></a>.NET yerel: yerel ikili dosyaları oluşturma  
 Hedef .NET Framework ve değil derlenmiş, .NET yerel araç zinciri kullanarak bir uygulama aşağıdakileri içeren, uygulama derlemenizi oluşur:  
  
-   [Meta veri](../../../docs/standard/metadata-and-self-describing-components.md) derleme, bağımlılıkları, içerdiği türleri ve üyeleri açıklar. Meta verilerini yansıma ve geç bağlama erişim ve bazı durumlarda da derleyici ve derleme araçları tarafından kullanılır.  
  
-   Uygulama kodu. Bu Ara dile (IL) işlem kodları oluşur. Çalışma zamanında tam zamanında (JIT) derleyici, hedef platformu için yerel kod çevirir.  
  
 Ana uygulama derlemenizi ek olarak, bir uygulama aşağıdaki mevcut olması gerekir:  
  
-   Tüm ek sınıf kitaplıkları veya uygulamanız tarafından gerekli olan üçüncü taraf derlemeler. Bu derlemeler benzer şekilde tüm tür üyeleri uygulayan IL yanı sıra, derleme, kendi türleri ve üyeleri açıklayan meta veriler içerir.  
  
-   .NET Framework sınıf kitaplığı. Bu, .NET Framework yüklemesi ile yerel sistemde yüklü derlemelerin koleksiyonudur. .NET Framework Sınıf Kitaplığı'nda derlemelerin meta verileri ve uygulama kodu eksiksiz bir kümesini içerir.  
  
-   Ortak dil çalışma zamanı. Bir koleksiyon gibi hizmetleri yükleniyor derleme gerçekleştirmek dinamik bağlantı kitaplıkları'nın, bellek yönetimi ve çöp toplama, özel durum işleme, tam zamanında derleme, remoting ve birlikte çalışma budur. Sınıf kitaplığı gibi çalışma zamanı yerel sistem .NET Framework yüklemesinin bir parçası olarak yüklenir.  
  
 Tüm ortak dil çalışma zamanı, yanı sıra meta verileri ve uygulamaya özgü derlemeler, üçüncü taraf derlemeler ve sistem derlemeler içindeki tüm türler için IL uygulamanın başarıyla yürütmek için mevcut olması gerektiğini unutmayın.  
  
## <a name="net-native-and-just-in-time-compilation"></a>.NET yerel ve yalnızca saat derleme  
 .NET yerel araç zinciri giriş C# veya Visual Basic derleyici tarafından oluşturulan Windows mağazası uygulaması olabilir. Diğer bir deyişle, bir Windows mağazası uygulaması derleme dili derleyici sona erdiğinde .NET yerel araç zinciri yürütme başlar.  
  
> [!TIP]
>  .NET yerel girdisi IL ve Yönetilen derlemeler için yazılan meta veriler olduğundan, ön derleme veya derleme sonrası olayları kullanarak veya MSBuild proje dosyası değiştirerek hala özel kod oluşturma veya diğer özel işlemler'i gerçekleştirebilirsiniz.  
>   
>  Ancak, IL değiştirebilir ve böylece bir uygulamanın IL çözümleme .NET araç zinciri önlemek araç kategorisine desteklenmez. Obfuscators, bu tür en önemli araçlardır.  
  
 .NET yerel araç zinciri, bir uygulama IL yerel koda dönüştürülmesi sırasında aşağıdaki gibi işlemleri gerçekleştirir:  
  
-   Belirli kod yollarının yansıma ve meta verileri statik yerel kod ile dayanan kodunu değiştirir. Örneğin, bir değer türü geçersiz <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> yöntemi, varsayılan eşitlik için test yansıma almak için kullanır <xref:System.Reflection.FieldInfo> değer tür alanları temsil eden nesneler sonra iki örnek alan değerlerini karşılaştırır. Yerel koda derlerken .NET yerel araç zinciri yansıma kodu ve meta verileri statik bir alan değerleri karşılaştırma ile değiştirir.  
  
-   Mümkünse, tüm meta veriler ortadan kaldırmak çalışır.  
  
-   Bu son uygulama derlemelerde uygulama tarafından gerçekten çağrılan uygulama kodunu içerir. Bu özellikle, üçüncü taraf kitaplıklar ve .NET Framework sınıf kitaplığı kodu de etkiler. Sonuç olarak, artık bir uygulama, üçüncü taraf kitaplıklar ya da tam .NET Framework sınıf kitaplığı bağlıdır; Bunun yerine, üçüncü taraf ve .NET Framework sınıf kitaplıkları kodda uygulamada sunulmuştur.  
  
-   Tam CLR öncelikle atık toplayıcı içeren bir işlenmiş çalışma zamanı ile değiştirir. İşlenmiş çalışma zamanı uygulamada ve yalnızca birkaç yüz kilobayt cinsinden boyutu olan mrt100_app.dll adlı bir kitaplık içinde bulunur. Statik bağlama gereken birçok ortak dil çalışma zamanı tarafından gerçekleştirilen hizmetler için attığından mümkündür.  
  
    > [!NOTE]
    >  .NET yerel standart ortak dil çalışma zamanı aynı atık toplayıcı kullanır. .NET yerel atık toplayıcı arka plan çöp toplama varsayılan olarak etkindir. Çöp toplama hakkında daha fazla bilgi için bkz: [çöp toplama Temelleri](../../../docs/standard/garbage-collection/fundamentals.md).  
  
> [!IMPORTANT]
>  .NET yerel bir yerel uygulamayı tüm uygulamaya derler. Bu sınıf kitaplığı yerel koda içerir ve böylece bağımsız olarak yönetilen koddan çağrılabilir tek bir derleme derlemek izin vermez.  
  
 .NET yerel araç zinciri tarafından üretilen sonuç uygulama projesi dizininizin hata ayıklama veya yayın dizininde ilc.out adlı bir dizin yazılır. Aşağıdaki dosyaları içerir:  
  
-   *\<Uygulamaadı >*.exe, yalnızca aktarımları için özel bir denetim bir saplama yürütülebilir `Main` olarak dışa  *\<uygulamaadı >*.dll.  
  
-   *\<Uygulamaadı >*.dll, bir Windows dinamik bağlantı tüm uygulama kodu içeren kitaplığı yanı sıra .NET Framework sınıf kitaplığı ve bir bağımlılığı olan herhangi bir üçüncü taraf kitaplıklarından kod.  Uygulamanızı Windows ile birlikte çalışmak için ve seri hale getirmek için gerekli kod nesneleri gibi destek kodu da içerir.  
  
-   mrt100_app.dll, atık toplama gibi çalışma zamanı hizmetleri sağlayan işlenmiş bir çalışma zamanı.  
  
 Tüm bağımlılıkları yakalanır uygulamanın APPX bildirimi tarafından.  Uygulama exe, dll ve mrt100_app.dll, ek olarak, doğrudan appx paketinde paketlendi, bu iki daha fazla dosya içerir:  
  
-   msvcr140_app.dll, mrt100_app.dll tarafından kullanılan C çalışma zamanı (CRT) Kitaplığı'nı tıklatın. Paket framework başvuru dahil edilir.  
  
-   mrt100.dll. Yokluğu mrt100_app.dll çalışmasını engellemez rağmen bu kitaplığı mrt100_app.dll, performansı artırabilir işlevler içerir. Varsa, yerel makinede system32 dizininden yüklenir.  
  
 Yalnızca uygulamanızı gerçekte bu kodu çağırır bilirse, .NET yerel araç zinciri uygulama kodu uygulamanıza bağlar. olduğundan meta veriler veya aşağıdaki senaryolarda gerekli uygulama kodu ile uygulamanızı dahil edilmemiş olabilir:  
  
-   Yansıma.  
  
-   Dinamik veya geç bağlama çağırma.  
  
-   Seri hale getirme ve seri durumdan çıkarma.  
  
-   COM birlikte çalışma.  
  
 Gerekli meta veri veya uygulama kodu olmazsa çalışma zamanında .NET yerel çalışma zamanı özel durum oluşturur. Bu özel durumları önleme ve kullanarak .NET yerel araç zinciri gerekli meta veri ve uygulama kodu içerdiğinden emin olmak bir [çalışma zamanı yönergeleri dosya](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md), program öğeleri, meta veri atar bir XML dosyası veya uygulama kodu çalışma zamanında kullanılabilir olmalı ve bir çalışma zamanı İlkesi bunlara atar. .NET yerel araç zinciri tarafından derlenen bir Windows mağazası projeye eklenen varsayılan çalışma zamanı yönergeleri dosya verilmiştir:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
    <Assembly Name="*Application*" Dynamic="Required All" />  
  </Application>  
</Directives>  
```  
  
 Bu, tüm üyeleri, yansıma ve dinamik çağırma için uygulama paketi tüm derlemelerde yanı sıra tüm türleri sağlar. Ancak, yansıma veya .NET Framework sınıf kitaplığı derlemelerde türlerinin dinamik etkinleştirme etkinleştirmez. Çoğu durumda bu yeterlidir.  
  
## <a name="net-native-and-ngen"></a>.NET yerel ve NGEN  
 [(Yerel Görüntü Oluşturucu](../../../docs/framework/tools/ngen-exe-native-image-generator.md) (NGEN) derlemeler yerel koda derlenen ve yerel bilgisayarda yerel görüntü önbelleği yükler. .NET yerel gibi NGEN yerel kod üretmez rağmen ancak bunu .NET yerel bazı önemli yönlerden farklıdır:  
  
-   Belirli bir yöntem için yerel bir görüntü varsa, NGEN JITing kodu geri döner. Başka bir deyişle, yerel görüntüler NGEN JIT derleme geri gerekiyor gerektiğinde, meta verileri ve IL dahil olmak üzere devam etmelisiniz. Buna karşılık, .NET yerel yalnızca yerel görüntüler üretir ve JIT derleme için geri dönüş değil. Sonuç olarak, yalnızca bazı yansıma, seri hale getirme ve birlikte çalışabilirlik senaryoları için gerekli meta veriler korunmalıdır.  
  
-   Tam ortak dil çalışma zamanı derlemesi yüklenirken, remoting, birlikte çalışabilirlik, bellek yönetimi, atık toplama gibi hizmetler için Bel NGEN devam eder ve gerekirse, JIT derleme. .NET yerel bu hizmetleri çoğunu ya da gereksiz (JIT derleme) olan veya derleme zamanında çözümlendi ve uygulama derlemede birleştirilmiş. Çöp toplama en önemli olan, kalan Hizmetleri mrt100_app.dll adlı bir çok daha küçük, işlenmiş çalışma zamanı'nda bulunur.  
  
-   NGEN görüntüleri kırılacak olma eğilimindedir. Örneğin, bir düzeltme eki veya bir bağımlılık değişiklik genellikle kullanmak derlemeler de yeniden NGENed olmasını gerektirir. Bu, özellikle sistem derlemelerin .NET Framework Sınıf Kitaplığı'nda geçerlidir. Buna karşılık, .NET yerel uygulamalarının birbirinden bağımsız olarak yük sunulması olanak sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Veriler ve Kendiliğinden Açıklayıcı Bileşenler](../../../docs/standard/metadata-and-self-describing-components.md)  
 [İç .NET yerel (kanal 9 Video)](http://channel9.msdn.com/Shows/Going+Deep/Inside-NET-Native)  
 [Yansıma ve .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)  
 [.NET Native Genel Sorun Giderme](../../../docs/framework/net-native/net-native-general-troubleshooting.md)
