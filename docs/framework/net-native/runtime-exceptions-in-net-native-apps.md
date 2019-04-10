---
title: .NET Native Uygulamalarında Çalışma Zamanı Özel Durumları
ms.date: 03/30/2017
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06e07c41d398c0792094b4481a38c69b2ba73004
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208286"
---
# <a name="runtime-exceptions-in-net-native-apps"></a>.NET Native Uygulamalarında Çalışma Zamanı Özel Durumları
Hata ayıklama ve yayın yapılandırmaları tamamen farklı olduğundan kendi Hedef platformlar üzerinde Evrensel Windows platformu uygulamanızın sürüm derlemeleri test etmek önemlidir. Varsayılan olarak, uygulamanızı derlemek için .NET Core çalışma zamanı hata ayıklama yapılandırması kullanır, ancak sürüm yapılandırmasını yerel kod için uygulamanızı derlemek için .NET Native kullanır.  
  
> [!IMPORTANT]
>  İşlemleri ile ilgili daha fazla bilgi için [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [Missingınteropdataexception](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), ve [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) olabilir, özel durumlar Yayın sürümleri uygulamanızı test ederken karşılaşırsanız, bkz: "4. adım: Meta veriler eksik elle Çözümle: içinde [Başlarken](../../../docs/framework/net-native/getting-started-with-net-native.md) konu yanı [yansıma ve .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md) ve [çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET yerel Windows Evrensel uygulamaları hata ayıklama](https://devblogs.microsoft.com/devops/debugging-net-native-windows-universal-apps/)
- [Başlarken](../../../docs/framework/net-native/getting-started-with-net-native.md)
