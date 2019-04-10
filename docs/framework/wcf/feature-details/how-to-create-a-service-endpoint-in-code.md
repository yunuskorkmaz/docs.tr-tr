---
title: 'Nasıl yapılır: Kod İçinde Hizmet Uç Noktası Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3fbb22fa-2930-48b8-b437-def1de87c6a0
ms.openlocfilehash: 65d26c0b9a41a6825108b73f822add4d91400055
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302536"
---
# <a name="how-to-create-a-service-endpoint-in-code"></a>Nasıl yapılır: Kod İçinde Hizmet Uç Noktası Oluşturma
Bu örnekte, bir `ICalculator` anlaşma hesaplayıcı hizmeti için tanımlanan, hizmet içinde uygulanan `CalculatorService` sınıf ve onun uç noktası burada belirtilen hizmetini kullanmalısınız kod içinde tanımlanan <xref:System.ServiceModel.BasicHttpBinding> sınıfı.  
  
 Yapılandırma yerine kesin kod bağlama ve adres bilgilerini bildirimli olarak belirtmek için genellikle en iyi uygulamadır. Bağlamalarında ve adreslerinde dağıtılan bir hizmette hizmet geliştirilen kullandığı olanlardan genellikle farklı olduğundan uç noktaları kodda tanımlama genellikle pratik değildir. Daha genel olarak, bağlama tutulması ve adresleme bilgilerini kodunun dışında yeniden derleyin veya uygulama yeniden dağıtmaya gerek kalmadan değiştirmek için bunları sağlar.  
  
#### <a name="to-create-a-service-endpoint-in-code"></a>Kod içinde hizmet uç noktası oluşturmak için  
  
1. Hizmet sözleşmesini tanımlayan arabirimi oluşturun.  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[c_HowTo_CodeServiceBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2. 1. adımda tanımlanan hizmet sözleşmesini uygulayın.  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[c_HowTo_CodeServiceBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3. Barındırma uygulamada, hizmet ve hizmetle birlikte kullanılacak bağlama için temel adresi oluşturun.  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[c_HowTo_CodeServiceBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4. Konak ve çağrı oluşturma <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29> ya da bir ana bilgisayar için hizmet uç noktası eklemek için diğer aşırı yüklemeleri.  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#6)]
     [!code-vb[c_HowTo_CodeServiceBinding#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#6)]  
  
     Kod içinde bağlama belirtilebilir, ancak çalışma zamanı tarafından sağlanan varsayılan uç noktalarını kullanacak şekilde, bas adresi oluşturucuya oluştururken geçirmek <xref:System.ServiceModel.ServiceHost>ve çağırmayın <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>.  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#7)]
     [!code-vb[c_HowTo_CodeServiceBinding#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#7)]  
  
     Varsayılan uç noktaları hakkında daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Kodda Hizmet Bağlama Belirtme](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md)
