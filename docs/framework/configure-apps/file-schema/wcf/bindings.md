---
title: '&lt;Bağlamaları&gt;'
ms.date: 03/30/2017
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: 76ebd7c317bf5f0aa1ec02d4014235df232314f0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltbindingsgt"></a>&lt;Bağlamaları&gt;
Bu bölümde, standart ve özel bağlamaları koleksiyonu tutar. Her Giriş bir `binding` kendi benzersiz tanımlanabilir öğesi `name`. Hizmetlerini kullanan bağlamaları bağlayarak kullanarak `name`. İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları olmayan bir adı olması için gereklidir. Varsayılan yapılandırma ve adsız bağlamalar ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="system-provided-binding"></a>Sistem tarafından sağlanan bağlama  
 Sistem tarafından sağlanan bağlamalar WCF ileti yığını karmaşıklığını gizleyin. Sistem tarafından sağlanan bağlamalar kullanan uygulamalar yığın üzerinde tam denetim gerektirmez. Her sistem tarafından sağlanan bir bağlamayı üzerinde gösterilen öznitelikleri olanlardır en uygun kullanım senaryosu için bağlama adresleri.  
  
 Her sistem tarafından sağlanan bir bağlamayı yapılandırma bölümü bağlama yapılandırmak için kullanılan birkaç yapılandırmaları tanımlayabilirsiniz. Her yapılandırma benzersiz bir ad tarafından tanımlanır.  
  
 Öğe veya öznitelik sistem tarafından sağlanan bir bağlamayı eklemek mümkün değildir. Bunu yapmak için bu konunun "Özel bağlama" bölümünde açıklandığı gibi özel bağlama uygulamanız gerekir. Sistem tarafından sağlanan mükemmel bağlama taklit eder ve kullanıcı uygulaması üzerinde denetime sahip olmasını istiyor birkaç ayar ekleyen özel bir bağlama tanımlamak mümkündür.  
  
 Sistem tarafından sağlanan bağlamalar listesi için bkz: [System-Provided bağlamaları](../../../../../docs/framework/wcf/system-provided-bindings.md).  
  
## <a name="custom-binding"></a>Özel Bağlama  
 Özel bağlamalar WCF ileti yığın üzerinde tam denetim sağlar. Tek bir bağlama yığında göründükleri sırada yığını öğeleri için yapılandırma öğeleri belirterek ileti yığını tanımlar. Her öğe tanımlar ve bir öğe yığınının yapılandırır. Yalnızca tek olmalıdır `transport` her özel bağlama öğesinde. Bu öğe Mesajlaşma yığını eksik.  
  
 Öğeleri yığında görünme sırasını işlemleri iletiye uygulanma sırası olduğundan önemlidir. Gerekli yığını öğelerin sırasını aşağıda verilmiştir:  
  
1.  İşlemler (isteğe bağlı)  
  
2.  Güvenilir Mesajlaşma (isteğe bağlı)  
  
3.  Güvenlik (isteğe bağlı)  
  
4.  Kodlayıcı  
  
5.  Taşıma  
  
 Özel bağlamalar tanımlanır kendi `name` özniteliği. Özel bağlama hakkında daha fazla bilgi için bkz: [özel bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)
