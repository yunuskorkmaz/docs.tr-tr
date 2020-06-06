---
title: <bindings>
ms.date: 01/22/2018
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: fe8f620668e35183890b8bba1f254a74c962f8d3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139669"
---
# \<bindings>

`bindings`Windows Communication Foundation (WCF) için standart ve özel bağlamaların bir koleksiyonunu yapılandırmak için öğesini kullanabilirsiniz. Her giriş, `binding` benzersiz tarafından tanımlanabilecek bir öğedir `name` . Hizmetler, kullanarak bağlama yoluyla bağlamaları kullanır `name` . .NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir. Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.

## <a name="system-provided-bindings"></a>Sistem tarafından sağlanmış bağlamalar

Sistem tarafından sağlanmış bağlamalar, WCF mesajlaşma yığınının karmaşıklığını gizler. Sistem tarafından belirtilen bağlamaları kullanan uygulamalar, yığın üzerinde tam denetim gerektirmez. Sistem tarafından sunulan her bağlamada sunulan öznitelikler, bağlama adresleri kullanım senaryosuna en uygun olanlardır.

Her sistem tarafından sağlanmış bağlamanın yapılandırma bölümü, bağlamayı yapılandırmak için kullanılan birkaç yapılandırmayı tanımlayabilir. Her yapılandırma benzersiz bir ad ile tanımlanır.

Sistem tarafından sağlanmış bir bağlamaya öğe veya öznitelik eklemek mümkün değildir. Bunu yapmak için [Özel Bağlamalar](#custom-bindings) bölümünde açıklandığı gibi özel bir bağlama uygulamalısınız. Sistem tarafından sağlanmış bağlamayı kusursuz bir şekilde taklit eden özel bir bağlama tanımlayabilir ve Kullanıcı uygulamasının denetimini sağlamak istediği birkaç ayarı ekler.  

Sistem tarafından sunulan bağlamaların listesi için bkz. [sistem tarafından sunulan bağlamalar](../../../wcf/system-provided-bindings.md).

## <a name="custom-bindings"></a>Özel Bağlamalar

Özel Bağlamalar, WCF mesajlaşma yığını üzerinde tam denetim sağlar. Tek bir bağlama yığın öğeleri için yapılandırma öğelerini yığında göründükleri sırada belirterek ileti yığınını tanımlar. Her öğe, yığının bir öğesini tanımlar ve yapılandırır. Her özel bağlamada tek bir ve yalnızca bir `transport` öğe olmalıdır. Bu öğe olmadan mesajlaşma yığını tamamlanmamıştır.

Öğelerin yığında görünme sırası önemli olduğundan, bu işlem, bu, işlemde hangi sırada görünecek? Stack öğelerinin gereken sırası şunlardır:  

1. İşlemler (isteğe bağlı)  

2. Güvenilir Mesajlaşma (isteğe bağlı)  

3. Güvenlik (isteğe bağlı)  

4. Kodlayıcısı  

5. Aktarım  

 Özel Bağlamalar özniteliği tarafından tanımlanır `name` . Özel Bağlamalar hakkında daha fazla bilgi için bkz. [Özel Bağlamalar](../../../wcf/extending/custom-bindings.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.BindingsSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>
- [Bağlamalar](../../../wcf/bindings.md)
- [Özel Bağlamalar](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
