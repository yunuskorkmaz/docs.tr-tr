---
title: 'Nasıl yapılır: Sistem Tarafından Sağlanan Bir Bağlamayı Özelleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8b97862-e8bb-470d-8b96-07733c21fe26
ms.openlocfilehash: cee570bdc9d7bf6debfc4ec226e91f3fd79a01dd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095158"
---
# <a name="how-to-customize-a-system-provided-binding"></a>Nasıl yapılır: Sistem Tarafından Sağlanan Bir Bağlamayı Özelleştirme
Windows Communication Foundation (WCF) bazı temel alınan bağlama öğeleri özelliklerini ancak özelliklerin tümü yapılandırmanıza olanak sağlayan birkaç sistem tarafından sağlanan bağlamalar içerir. Bu konuda, bir özel bağlamayı oluşturmak için bağlama öğelerinin özelliklerini ayarlamak gösterilmiştir.  
  
 Doğrudan oluşturma ve bağlama öğeleri sistem tarafından sağlanan bağlamalar kullanmadan yapılandırma hakkında daha fazla bilgi için bkz. [özel bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
 Oluşturma ve özel bağlamalar genişletme hakkında daha fazla bilgi için bkz. [bağlamaları genişletme](../../../../docs/framework/wcf/extending/extending-bindings.md).  
  
 WCF'de tüm bağlamaları, oluşur *bağlama öğelerinin*. Her bağlama öğesi türetildiği <xref:System.ServiceModel.Channels.BindingElement> sınıfı. Sistem tarafından sağlanan bağlamalar gibi <xref:System.ServiceModel.BasicHttpBinding> oluşturun ve kendi bağlama öğelerini yapılandırın. Bu konuda erişmek ve bunları doğrudan binding üstündeki gösterilmez Bu bağlama öğeleri özelliklerini değiştirmek gösterilmektedir; Özellikle, <xref:System.ServiceModel.BasicHttpBinding> sınıfı.  
  
 Tek tek bağlama öğeleri tarafından temsil edilen bir koleksiyonda bulunan <xref:System.ServiceModel.Channels.BindingElementCollection> sınıfı ve bu sırada eklenir: İşlem akışını, güvenilir oturum, güvenlik, bileşik bir çift yönlü, tek yönlü, Stream güvenlik, ileti kodlama ve taşıma. Listelenen tüm bağlama öğelerini her bağlamanın gerekli olduğunu unutmayın. Kullanıcı tanımlı bağlama öğeleri de bu bağlama öğesi koleksiyonda görünebilir ve daha önce açıklandığı gibi aynı sırada yer almalıdır. Örneğin, bir kullanıcı tarafından tanımlanan aktarım bağlama öğesi koleksiyonun son öğesine olması gerekir.  
  
 <xref:System.ServiceModel.BasicHttpBinding> Sınıfı üç bağlama öğeleri içerir:  
  
1.  Ya da bağlama öğesi, isteğe bağlı bir güvenlik <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> HTTP taşıma (ileti düzeyi güvenliği) ile kullanılan bir sınıfı veya <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> Aktarım Katmanı Güvenliği de HTTPS aktarımı durumda sağladığında kullanılan sınıfı kullanılır.  
  
2.  Ya da bağlama öğesi, gerekli ileti Kodlayıcı <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> veya <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>.  
  
3.  Bağlama öğesi, ya da gerekli bir aktarım <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, veya <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.  
  
 Bu örnekte biz bağlama öğesinin bir örneğini oluşturur, oluşturun bir *özel bağlama* kendisinden özel bağlamaya ait bağlama öğelerini incelemek ve HTTP bağlama öğesi bulduğunuzda, biz ayarlarız kendi `KeepAliveEnabled` özelliğini`false`. `KeepAliveEnabled` Özelliği doğrudan gösterilmese `BasicHttpBinding`, biz bağlama öğesi aşağı gidin ve bu özelliği ayarlamak için özel bir bağlama oluşturmanız gerekir.  
  
### <a name="to-modify-a-system-provided-binding"></a>Sistem tarafından sağlanan bir bağlamayı değiştirmek için  
  
1.  Bir örneğini oluşturmak <xref:System.ServiceModel.BasicHttpBinding> sınıfı ve ileti düzeyi, güvenlik modunu ayarlama.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#1)]
     [!code-vb[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#1)]  
  
2.  Özel bağlama bağlamayı oluşturup oluşturmak bir <xref:System.ServiceModel.Channels.BindingElementCollection> özel bağlama özellikleri birinden sınıfı.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#2)]
     [!code-vb[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#2)]  
  
3.  Döngü <xref:System.ServiceModel.Channels.BindingElementCollection> sınıfı ve ne zaman bulduğunuz <xref:System.ServiceModel.Channels.HttpTransportBindingElement> sınıfı olarak ayarlayın, <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> özelliğini `false`.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#3)]
     [!code-vb[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Özel Bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md)
