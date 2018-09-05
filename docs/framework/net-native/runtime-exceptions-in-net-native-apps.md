---
title: .NET Native uygulamalarında çalışma zamanı özel durumları
ms.date: 03/30/2017
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: efb16c1e947cd832da88b53a3522a5928e77ae06
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43501717"
---
# <a name="runtime-exceptions-in-net-native-apps"></a>.NET Native uygulamalarında çalışma zamanı özel durumları
Hata ayıklama ve yayın yapılandırmaları tamamen farklı olduğundan kendi Hedef platformlar üzerinde Evrensel Windows platformu uygulamanızın sürüm derlemeleri test etmek önemlidir. Varsayılan olarak, uygulamanızı derlemek için .NET Core çalışma zamanı hata ayıklama yapılandırması kullanır, ancak sürüm yapılandırmasını yerel kod için uygulamanızı derlemek için .NET Native kullanır.  
  
> [!IMPORTANT]
>  İşlemleri ile ilgili daha fazla bilgi için [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [Missingınteropdataexception](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), ve [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) olabilir, özel durumlar Yayın sürümleri uygulamanızı test ederken karşılaşırsanız, bkz: "4. adım: meta veriler eksik el ile çözümlemeniz: içinde [Başlarken](../../../docs/framework/net-native/getting-started-with-net-native.md) konu, yanı [yansıma ve .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md) ve [ Çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
## <a name="debug-and-release-builds"></a>Hata ayıklama ve yayın derlemeleri  
 Hata ayıklama derlemesini .NET Core çalışma zamanı karşı yürütüldüğünde, yerel koda derlenmedi. Bu, normalde uygulamanıza kullanılabilir çalışma zamanı tarafından sağlanan tüm hizmetleri sağlar.  
  
 Öte yandan, sürüm yapısı, Hedef platformlar için yerel koda derleyen, dış çalışma zamanları ve kitaplıkları çoğu bağımlılıkları kaldırır ve yoğun bir şekilde kod en yüksek performans için en iyi duruma getirir.  
  
 .NET Native ile derlenmiş sürüm yapıları için hata ayıklaması yaptığınızda:  
  
-   .NET normal hata ayıklama araçları farklı .NET yerel hata ayıklama altyapısı kullanırsınız.  
  
-   Yürütülebilir dosyanızın boyutunu mümkün olduğunca azaltılır. .NET Native yürütülebilir bir dosya boyutunu azaltır, yollardan biridir önemli ölçüde daha ayrıntılı olarak ele alınan bir konu olan çalışma zamanı özel durum iletileri kırpma tarafından [çalışma zamanı özel durum iletileri](#Messages) bölümü.  
  
-   Kodunuzu son derece iyileştirilmiştir. Yani bu satır içi kullanım, mümkün olduğunda kullanılır. (Satır içi kod dış rutinleri çağıran yordam taşır.)   .NET Native özelleştirilmiş bir çalışma zamanı sağlar ve agresif inlining'i etkiler görüntülenen hata ayıklama sırasında çağrı yığınını uygulayan, olgu.  Daha fazla bilgi için [çalışma zamanının çağrı yığınındaki](#CallStack) bölümü.  
  
> [!NOTE]
>  Hata ayıklama ve yayın derlemeleri denetleme veya işaretini .NET yerel araç zinciriyle derlenmiş olup olmadığını kontrol edebilirsiniz **.NET yerel araç zinciriyle derle** kutusu.   Ancak, Windows Store, uygulamanızın .NET Native araç zinciri ile üretim sürümü her zaman derleyeceği unutmayın.  
  
<a name="Messages"></a>   
## <a name="runtime-exception-messages"></a>Çalışma zamanı özel durum iletileri  
 Uygulama yürütülebilir boyutu en aza indirmek için .NET Native özel durum iletilerinin tam metin içermez. Sonuç olarak, sürüm yapılarında durum çalışma zamanı özel durumları, özel durum iletilerinin tam metin görüntülenmeyebilir. Bunun yerine, metni daha fazla bilgi için izlemek için bir bağlantı ile birlikte bir alt dizenin oluşabilir. Örneğin, özel durum bilgilerini olarak görünebilir:  
  
```  
Exception thrown: '$16_System.AggregateException' in Unknown Module.  
  
Additional information: AggregateException_ctor_DefaultMessage  
  
If there is a handler for this exception, the program may be safely continued.  
```  
  
 Hata ayıklama derlemesini, bunun yerine tam özel durum iletisi gerekirse çalıştırın. Örneğin, önceki sürüm yapısı özel durum bilgileri gibi hata ayıklama derlemesinde görünebilir:  
  
```  
Exception thrown: 'System.AggregateException' in NativeApp.exe.  
  
Additional information: Value does not fall within the expected range.  
```  
  
<a name="CallStack"></a>   
## <a name="runtime-call-stack"></a>Çalışma zamanı çağrı yığını  
 Satır içi kullanım ve diğer iyileştirmeler nedeniyle, çağrı yığınını .NET Native araç zinciri tarafından derlenmiş bir uygulama tarafından görüntülenen çalışma zamanı özel yoluna açıkça tanımlamak için yardımcı olabilir değil.  
  
 Tam yığın almak için hata ayıklama derlemesini çalıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET yerel Windows Evrensel uygulamaları hata ayıklama](https://blogs.msdn.com/b/visualstudioalm/archive/2015/07/29/debugging-net-native-windows-universal-apps.aspx)  
 [Başlarken](../../../docs/framework/net-native/getting-started-with-net-native.md)
