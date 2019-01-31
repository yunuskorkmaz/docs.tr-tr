---
title: <bindings>
ms.date: 03/30/2017
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: 4a952ff5a8dd39a5615aa17f15229557bbd0f41f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257310"
---
# <a name="bindings"></a>\<bağlamaları >
Bu bölümde, standart ve özel bağlamalar koleksiyonunu tutar. Her Giriş bir `binding` kendi benzersiz tarafından tanımlanabilir öğesi `name`. Hizmetlerini kullanan bağlamaları bağlayarak kullanarak `name`. İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip. Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="system-provided-binding"></a>Sistem tarafından sağlanan bir bağlamayı  
 Sistem tarafından sağlanan bağlamalar WCF Mesajlaşma yığını karmaşıklığını gizler. Sistem tarafından sağlanan bağlamalar kullanan uygulamalar, yığını üzerinde tam denetim gerektirmez. Her sistem tarafından sağlanan bir bağlamayı üzerinde kullanıma sunulan öznitelikleri olanlardır çoğu kullanım senaryosu bağlamanın adreslerin uygun.  
  
 Her sistem tarafından sağlanan bir bağlamayı yapılandırma bölümü yapılandırmak için kullanılan birkaç yapılandırmaları tanımlayabilirsiniz. Her yapılandırma, benzersiz bir ad tarafından tanımlanır.  
  
 Öğeler veya öznitelikleri için sistem tarafından sağlanan bir bağlamayı eklemek mümkün değildir. Bunu yapmak için bu konunun "Özel bağlama" bölümünde açıklandığı gibi özel bir bağlama uygulamalıdır. Sistem tarafından sağlanan mükemmel bir şekilde bağlama taklit eder ve kullanıcı uygulaması üzerinde denetime sahip ister birkaç ayar ekleyen özel bir bağlama tanımlamak mümkündür.  
  
 Sistem tarafından sağlanan bağlamalar bir listesi için bkz. [System-Provided bağlamaları](../../../../../docs/framework/wcf/system-provided-bindings.md).  
  
## <a name="custom-binding"></a>Özel Bağlama  
 Özel bağlamalar WCF Mesajlaşma yığını üzerinde tam denetim sağlar. Tek bir bağlama yığında göründükleri sırayla yığın öğeler için yapılandırma öğeleri belirterek ileti yığın tanımlar. Her öğe tanımlar ve bir öğe yığınının yapılandırır. Bir ve yalnızca bir olmalıdır `transport` her özel bir bağlama öğesi. Bu öğe Mesajlaşma yığını eksik.  
  
 Öğeleri yığında görünme sırasını çünkü bu işlem iletiyi uygulanma sırası önemlidir. Gerekli yığın öğelerin sırasını aşağıda verilmiştir:  
  
1.  İşlemler (isteğe bağlı)  
  
2.  Güvenilir Mesajlaşma (isteğe bağlı)  
  
3.  Güvenlik (isteğe bağlı)  
  
4.  Kodlayıcı  
  
5.  Taşıma  
  
 Özel bağlamalar tarafından tanımlanır, `name` özniteliği. Özel bağlamalar hakkında daha fazla bilgi için bkz. [özel bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)
- [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [\<bağlama >](../../../../../docs/framework/misc/binding.md)
