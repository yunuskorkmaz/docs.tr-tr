---
title: <bindings>
ms.date: 01/22/2018
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: 1292bc38ce1e542086edac5539c1b29e619e2a32
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926380"
---
# <a name="bindings"></a>\<bağlama >

Windows Communication Foundation (WCF) `bindings` için standart ve özel bağlamaların bir koleksiyonunu yapılandırmak için öğesini kullanabilirsiniz. Her giriş, benzersiz `binding` `name`tarafından tanımlanabilecek bir öğedir. Hizmetler, `name`kullanarak bağlama yoluyla bağlamaları kullanır. İle [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak, bağlamaların ve davranışların bir ada sahip olması gerekmez. Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.  
  
## <a name="system-provided-bindings"></a>Sistem tarafından sağlanmış bağlamalar
 
 Sistem tarafından sağlanmış bağlamalar, WCF mesajlaşma yığınının karmaşıklığını gizler. Sistem tarafından belirtilen bağlamaları kullanan uygulamalar, yığın üzerinde tam denetim gerektirmez. Sistem tarafından sunulan her bağlamada sunulan öznitelikler, bağlama adresleri kullanım senaryosuna en uygun olanlardır.  
  
 Her sistem tarafından sağlanmış bağlamanın yapılandırma bölümü, bağlamayı yapılandırmak için kullanılan birkaç yapılandırmayı tanımlayabilir. Her yapılandırma benzersiz bir ad ile tanımlanır.  
  
 Sistem tarafından sağlanmış bir bağlamaya öğe veya öznitelik eklemek mümkün değildir. Bunu yapmak için [Özel Bağlamalar](#custom-bindings) bölümünde açıklandığı gibi özel bir bağlama uygulamalısınız. Sistem tarafından sağlanmış bağlamayı kusursuz bir şekilde taklit eden özel bir bağlama tanımlayabilir ve Kullanıcı uygulamasının denetimini sağlamak istediği birkaç ayarı ekler.  
  
 Sistem tarafından sunulan bağlamaların listesi için bkz. [sistem tarafından sunulan bağlamalar](../../../wcf/system-provided-bindings.md).  
  
## <a name="custom-bindings"></a>Özel Bağlamalar

 Özel Bağlamalar, WCF mesajlaşma yığını üzerinde tam denetim sağlar. Tek bir bağlama yığın öğeleri için yapılandırma öğelerini yığında göründükleri sırada belirterek ileti yığınını tanımlar. Her öğe, yığının bir öğesini tanımlar ve yapılandırır. Her özel bağlamada tek bir ve yalnızca `transport` bir öğe olmalıdır. Bu öğe olmadan mesajlaşma yığını tamamlanmamıştır.  
  
 Öğelerin yığında görünme sırası önemli olduğundan, bu işlem, bu, işlemde hangi sırada görünecek? Stack öğelerinin gereken sırası şunlardır:  
  
1. İşlemler (isteğe bağlı)  
  
2. Güvenilir Mesajlaşma (isteğe bağlı)  
  
3. Güvenlik (isteğe bağlı)  
  
4. Kodlayıcısı  
  
5. Aktarım  
  
 Özel bağlamalar `name` özniteliği tarafından tanımlanır. Özel Bağlamalar hakkında daha fazla bilgi için bkz. [Özel Bağlamalar](../../../wcf/extending/custom-bindings.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.BindingsSection?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>  
- [Bağlamalar](../../../wcf/bindings.md)  
- [Özel Bağlamalar](../../../wcf/extending/custom-bindings.md)  
- [\<customBinding >](custombinding.md)  
- [\<bağlama >](../../../misc/binding.md)
