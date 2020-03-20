---
title: .NET Native Uygulamalarında Çalışma Zamanı Özel Durumları
ms.date: 03/30/2017
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
ms.openlocfilehash: 12df2ef7bf6e86a60dfa4c130f35969e72ac5211
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180944"
---
# <a name="runtime-exceptions-in-net-native-apps"></a>.NET Native Uygulamalarında Çalışma Zamanı Özel Durumları
Hata ayıklama ve sürüm yapılandırmaları tamamen farklı olduğundan, Evrensel Windows Platformu uygulamanızın sürüm yapılarını hedef platformlarında sınamak önemlidir. Varsayılan olarak, hata ayıklama yapılandırması uygulamanızı derlemek için .NET Core çalışma zamanını kullanır, ancak sürüm yapılandırması uygulamanızı yerel koda derlemek için .NET Native kullanır.  
  
> [!IMPORTANT]
> [EksikMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md)ve Uygulamanızın sürüm sürümlerini test ederken karşılaşabileceğiniz [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) özel durumları ile ilgili bilgi için bkz: "Adım 4: Eksik meta verileri el ile çözmek: [Başlangıç](getting-started-with-net-native.md) konusunun yanı sıra [Yansıma ve .NET Yerli](reflection-and-net-native.md) ve Çalışma Zamanı [Direktifleri (rd.xml) Yapılandırma Dosya Başvurusu.](runtime-directives-rd-xml-configuration-file-reference.md)  
  
## <a name="debug-and-release-builds"></a>Hata ayıklama ve sürüm yapılarını  
 Hata ayıklama yapısı .NET Core çalışma süresine karşı yürütüldüğünde, yerel kodiçin derlenmemiştir. Bu, normalde çalışma zamanı tarafından sağlanan tüm hizmetleri uygulamanız için kullanılabilir hale getirir.  
  
 Diğer taraftan, sürüm yapısı hedef platformları için yerel koda derler, dış çalışma sürelerine ve kitaplıklara olan bağımlılıkların çoğunu kaldırır ve maksimum performans için kodu yoğun bir şekilde optimize eder.  
  
 .NET Native kullanılarak derlenen sürüm yapılarını hata ayıklama yaptığınızda:  
  
- Normal .NET hata ayıklama araçlarından farklı olan .NET Yerel hata ayıklama altyapısını kullanırsınız.  
  
- Çalıştırılabilir boyutunu mümkün olduğunca azalır. .NET Native'in yürütülebilir boyutu azaltma yollarından biri, [Çalışma Zamanı özel durum iletileri](#Messages) bölümünde daha ayrıntılı olarak tartışılan bir konu olan çalışma zamanı özel durum iletilerini önemli ölçüde kırpmaktır.  
  
- Kodunuz ağır şekilde optimize edildi. Bu, inlining mümkün olduğunda kullanıldığı anlamına gelir. (Inlining kodu dış yordamlardan arama yordamına taşır.)   .NET Native'in özel bir çalışma süresi sağlaması ve agresif ara çizgi sini uygulamaları hata ayıklama yaparken görüntülenen çağrı yığınını etkiler.  Daha fazla bilgi için [Runtime arama yığını](#CallStack) bölümüne bakın.  
  
> [!NOTE]
> Hata ayıklama ve sürüm yapılarının .NET Native araç zinciriyle derlenip derlenmediğini,.NET **Native araç zinciri kutusuyla Derleme'yi** denetleyerek veya denetlemeyi denetleyerek denetleyebilirsiniz.   Ancak, Windows Mağazası'nın uygulamanızın üretim sürümünü her zaman .NET Native araç zinciriyle derlemeyeceğini unutmayın.  
  
<a name="Messages"></a>
## <a name="runtime-exception-messages"></a>Çalışma zamanı özel durum iletileri  
 Uygulama yürütülebilir boyutunu en aza indirmek için ,NET Native özel durum iletilerinin tam metnini içermez. Sonuç olarak, sürüm yapılarında atılan çalışma zamanı özel durumları özel durum iletilerinin tam metnini görüntülemeyebilir. Bunun yerine, metin daha fazla bilgi için takip etmek için bir bağlantı ile birlikte bir alt dize oluşabilir. Örneğin, özel durum bilgileri aşağıdaki gibi görünebilir:  
  
```output
Exception thrown: '$16_System.AggregateException' in Unknown Module.  
  
Additional information: AggregateException_ctor_DefaultMessage  
  
If there is a handler for this exception, the program may be safely continued.  
```  
  
 Tam özel durum iletisi gerekiyorsa, bunun yerine hata ayıklama yapıçalıştırın. Örneğin, sürüm yapısındaki önceki özel durum bilgileri hata ayıklama yapısında aşağıdaki gibi görünebilir:  
  
```output
Exception thrown: 'System.AggregateException' in NativeApp.exe.  
  
Additional information: Value does not fall within the expected range.  
```  
  
<a name="CallStack"></a>
## <a name="runtime-call-stack"></a>Çalışma zamanı arama yığını  
 İçe doğru astarlama ve diğer optimizasyonlar nedeniyle,.NET Native araç zinciri tarafından derlenen bir uygulama tarafından görüntülenen çağrı yığını, çalışma zamanı özel duruma giden yolu net bir şekilde belirlemenize yardımcı olmayabilir.  
  
 Tam yığını almak için hata ayıklama yapısını çalıştırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Native Windows Universal Apps Hata Ayıklama](https://devblogs.microsoft.com/devops/debugging-net-native-windows-universal-apps/)
- [Başlarken](getting-started-with-net-native.md)
