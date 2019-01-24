---
title: '&lt;Bağlama&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 666183d6-4d1f-45c7-ac64-bdf93ee8f36f
ms.openlocfilehash: fb4fafda31205e2ce5efd01ab265fcacfa70bdf6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539200"
---
# <a name="ltbindinggt"></a>&lt;Bağlama&gt;
Kullanabileceğiniz `binding` farklı yapılandırma öğesi Windows Communication Foundation (WCF) tarafından sağlanan bağlamaları önceden tanımlanmış.  
  
## <a name="system-provided-binding"></a>Sistem tarafından sağlanan bir bağlamayı  
 Sistem tarafından sağlanan bağlamalar WCF Mesajlaşma yığını karmaşıklığını gizler. Sistem tarafından sağlanan bağlamalar kullanan uygulamalar, yığını üzerinde tam denetim gerektirmez. Her sistem tarafından sağlanan bir bağlamayı üzerinde kullanıma sunulan öznitelikleri olanlardır çoğu kullanım senaryosu bağlamanın adreslerin uygun.  
  
 Her sistem tarafından sağlanan bir bağlamayı yapılandırma bölümü yapılandırmak için kullanılan birkaç yapılandırmaları tanımlayabilirsiniz. Her yapılandırma, benzersiz bir ad tarafından tanımlanır.  
  
 Öğeler veya öznitelikleri için sistem tarafından sağlanan bir bağlamayı eklemek mümkün değildir. Bunu yapmak için bu konunun "Özel bağlama" bölümünde açıklandığı gibi özel bir bağlama uygulamalıdır. Sistem tarafından sağlanan mükemmel bir şekilde bağlama taklit eder ve kullanıcı uygulaması üzerinde denetime sahip ister birkaç ayar ekleyen özel bir bağlama tanımlamak mümkündür.  
  
## <a name="custom-binding"></a>Özel Bağlama  
 Özel bağlamalar WCF Mesajlaşma yığını üzerinde tam denetim sağlar. Tek bir bağlama yığında göründükleri sırayla yığın öğeler için yapılandırma öğeleri belirterek ileti yığın tanımlar. Her öğe tanımlar ve bir öğe yığınının yapılandırır. Bir ve yalnızca bir olmalıdır `transport` her özel bir bağlama öğesi. Bu öğe Mesajlaşma yığını eksik.  
  
 Öğeleri yığında görünme sırasını çünkü bu işlem iletiyi uygulanma sırası önemlidir. Önerilen yığın öğelerin sırasını aşağıda verilmiştir:  
  
1.  İşlemler (isteğe bağlı)  
  
2.  Güvenilir Mesajlaşma (isteğe bağlı)  
  
3.  Güvenlik (isteğe bağlı)  
  
4.  Kodlayıcı  
  
5.  Taşıma  
  
 Özel bağlamalar tarafından tanımlanır, `name` özniteliği.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- [Bağlamalar](../../../docs/framework/wcf/bindings.md)
- [Özel Bağlamalar](../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
