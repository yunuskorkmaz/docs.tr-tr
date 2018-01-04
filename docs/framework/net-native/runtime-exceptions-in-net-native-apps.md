---
title: ".NET yerel uygulamalar çalışma zamanı özel durumları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cea4901eca45a4b02e3eeb9fa8a3ac2a9efa3484
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="runtime-exceptions-in-net-native-apps"></a>.NET yerel uygulamalar çalışma zamanı özel durumları
Hata ayıklama ve yayın yapılandırmaları tamamen farklı olduğundan, Evrensel Windows platformu uygulamanızın kendi hedef platformlarda yayın derlemeleri test etmek önemlidir. Varsayılan olarak, uygulamanızı derlemeye .NET çekirdeği çalışma zamanı hata ayıklama yapılandırmasını kullanır, ancak sürüm yapılandırmasında uygulamanızı yerel koda derlemek için .NET yerel kullanır.  
  
> [!IMPORTANT]
>  Yapılacağı hakkında bilgi için [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [Missingınteropdataexception](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), ve [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) görebilirsiniz özel durumlar Uygulamanızı yayın sürümlerini test edilirken karşılaşırsanız bkz "4. adım: el ile eksik meta veri çözümleme: içinde [Başlarken](../../../docs/framework/net-native/getting-started-with-net-native.md) konu yanı [yansıma ve .NET yerel](../../../docs/framework/net-native/reflection-and-net-native.md) ve [ Çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
## <a name="debug-and-release-builds"></a>Hata ayıklama ve yayın derlemeleri  
 Hata ayıklama derlemesi .NET çekirdeği çalışma zamanı karşı yürütüldüğünde, onu yerel koda derlenmiş değil. Bu genellikle, uygulamanızın kullanılabilir çalışma zamanı tarafından sağlanan hizmetlerin tümünü sağlar.  
  
 Diğer taraftan, yayın derlemesi Hedef platformlar için yerel koda derlenen, dış çalışma zamanları ve kitaplıkları çoğu bağımlılıkları kaldırır ve yoğun bir şekilde kod en yüksek performans için en iyi duruma getirir.  
  
 Ne zaman .NET yerel kullanarak derlenmiş sürüm derlemeleri hata ayıklama:  
  
-   Hata ayıklama araçları normal .NET farklı .NET yerel hata ayıklama altyapısı kullanın.  
  
-   Yürütülebilir dosyanın boyutunu mümkün olduğunca çok azdır. .NET yerel bir yürütülebilir dosya boyutunu azaltır, yollardan biridir önemli ölçüde çalışma zamanı özel durum iletileri, daha ayrıntılı olarak ele alınan bir konu kırpma tarafından [çalışma zamanı özel durum iletilerini](#Messages) bölümü.  
  
-   Kodunuzu yoğun getirilmiştir. Bunun anlamı, satır içi kullanım mümkün olduğunca kullanılır. (Satır içi kullanım kodu dış yordamlarından yordamı çağrılırken taşır.)   .NET yerel özelleştirilmiş bir çalışma zamanı sağlar ve agresif satır içi kullanım etkiler hata ayıklama sırasında görüntülenen çağrı yığınını uygulayan, olgu.  Daha fazla bilgi için bkz: [çalışma zamanının çağrı yığını](#CallStack) bölümü.  
  
> [!NOTE]
>  Hata ayıklama ve yayın derlemeleri denetleme veya işaretleyerek .NET yerel araç zinciri ile derlenen olup olmadığını kontrol edebilirsiniz **olan .NET yerel araç zinciri derleme** kutusu.   Ancak, Windows mağazası uygulamanızı .NET yerel araç zinciri ile üretim sürümü her zaman derlenir unutmayın.  
  
<a name="Messages"></a>   
## <a name="runtime-exception-messages"></a>Çalışma zamanı özel durum iletileri  
 Uygulama yürütülebilir boyutu en aza indirmek için .NET yerel özel durum iletilerinin tam metin içermez. Sonuç olarak, çalışma zamanı özel durumları yayın derlemelerde oluşturulan özel durum iletilerinin tam metin görüntülenmeyebilir. Bunun yerine, metin, daha fazla bilgi için izlemek için bir bağlantı ile birlikte bir alt dizenin oluşabilir. Örneğin, özel durum bilgisi olarak görünebilir:  
  
```  
Exception thrown: '$16_System.AggregateException' in Unknown Module.  
  
Additional information: AggregateException_ctor_DefaultMessage  
  
If there is a handler for this exception, the program may be safely continued.  
```  
  
 Hata ayıklama derlemesi tam özel durum iletisi gerekiyorsa, bunun yerine çalıştırın. Örneğin, yayın derlemesi önceki özel durum bilgileri hata ayıklama derlemesi şu şekilde görünebilir:  
  
```  
Exception thrown: 'System.AggregateException' in NativeApp.exe.  
  
Additional information: Value does not fall within the expected range.  
```  
  
<a name="CallStack"></a>   
## <a name="runtime-call-stack"></a>Çalışma zamanı çağrı yığını  
 Satır içi kullanım ve diğer iyileştirmeler nedeniyle .NET yerel araç zinciri tarafından derlenen bir uygulama tarafından görüntülenen çağrı yığını açıkça bir çalışma zamanı özel yoluna belirlemenize yardımcı olmayabilir.  
  
 Tam yığını almak için hata ayıklama derlemesi çalıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET yerel Windows Evrensel uygulamaları hata ayıklama](http://blogs.msdn.com/b/visualstudioalm/archive/2015/07/29/debugging-net-native-windows-universal-apps.aspx)  
 [Başlarken](../../../docs/framework/net-native/getting-started-with-net-native.md)
