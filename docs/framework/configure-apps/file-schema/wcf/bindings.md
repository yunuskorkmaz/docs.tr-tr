---
title: "&lt;bağlamaları&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b729141055f67f1d37cadfa4422417fe2d73139e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltbindingsgt"></a>&lt;bağlamaları&gt;
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
 [Bağlamaları](../../../../../docs/framework/wcf/bindings.md)  
 [Özel bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)
