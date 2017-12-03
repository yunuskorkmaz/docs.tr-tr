---
title: "&lt;bağlama&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 666183d6-4d1f-45c7-ac64-bdf93ee8f36f
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eefa3145f50ffa24c1b3cf895c9e5097adb5e9d9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltbindinggt"></a>&lt;bağlama&gt;
Kullanabileceğiniz `binding` öğesi farklı türlerde yapılandırmak için Windows Communication Foundation (WCF) tarafından sağlanan bağlamaları önceden tanımlanmış.  
  
## <a name="system-provided-binding"></a>Sistem tarafından sağlanan bağlama  
 Sistem tarafından sağlanan bağlamalar WCF ileti yığını karmaşıklığını gizleyin. Sistem tarafından sağlanan bağlamalar kullanan uygulamalar yığın üzerinde tam denetim gerektirmez. Her sistem tarafından sağlanan bir bağlamayı üzerinde gösterilen öznitelikleri olanlardır en uygun kullanım senaryosu için bağlama adresleri.  
  
 Her sistem tarafından sağlanan bir bağlamayı yapılandırma bölümü bağlama yapılandırmak için kullanılan birkaç yapılandırmaları tanımlayabilirsiniz. Her yapılandırma benzersiz bir ad tarafından tanımlanır.  
  
 Öğe veya öznitelik sistem tarafından sağlanan bir bağlamayı eklemek mümkün değildir. Bunu yapmak için bu konunun "Özel bağlama" bölümünde açıklandığı gibi özel bağlama uygulamanız gerekir. Sistem tarafından sağlanan mükemmel bağlama taklit eder ve kullanıcı uygulaması üzerinde denetime sahip olmasını istiyor birkaç ayar ekleyen özel bir bağlama tanımlamak mümkündür.  
  
## <a name="custom-binding"></a>Özel Bağlama  
 Özel bağlamalar WCF ileti yığın üzerinde tam denetim sağlar. Tek bir bağlama yığında göründükleri sırada yığını öğeleri için yapılandırma öğeleri belirterek ileti yığını tanımlar. Her öğe tanımlar ve bir öğe yığınının yapılandırır. Yalnızca tek olmalıdır `transport` her özel bağlama öğesinde. Bu öğe Mesajlaşma yığını eksik.  
  
 Öğeleri yığında görünme sırasını işlemleri iletiye uygulanma sırası olduğundan önemlidir. Önerilen yığını öğelerin sırasını aşağıda verilmiştir:  
  
1.  İşlemler (isteğe bağlı)  
  
2.  Güvenilir Mesajlaşma (isteğe bağlı)  
  
3.  Güvenlik (isteğe bağlı)  
  
4.  Kodlayıcı  
  
5.  Taşıma  
  
 Özel bağlamalar tanımlanır kendi `name` özniteliği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 [Bağlamaları](../../../docs/framework/wcf/bindings.md)  
 [Özel bağlamalar](../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
