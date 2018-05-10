---
title: 'Nasıl yapılır: Sistem Tarafından Sağlanan Bir Bağlamayı Özelleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8b97862-e8bb-470d-8b96-07733c21fe26
ms.openlocfilehash: 04b81689d7d625d519a0a9fc8b1fa6df3df16ada
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-customize-a-system-provided-binding"></a>Nasıl yapılır: Sistem Tarafından Sağlanan Bir Bağlamayı Özelleştirme
Windows Communication Foundation (WCF) temel alınan bağlama öğeleri özelliklerden bazıları, ancak tüm özellikleri yapılandırmanıza olanak tanıyan çeşitli sistem tarafından sağlanan bağlamaları içerir. Bu konu, özelliklerin özel bağlama oluşturma için bağlama öğeleri nasıl ayarlanacağını gösterir.  
  
 Doğrudan oluşturmak ve bağlama öğeleri sistem tarafından sağlanan bağlamalar kullanmadan yapılandırma hakkında daha fazla bilgi için bkz: [özel bağlamaları](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
 Oluşturma ve özel bağlamaları genişletme hakkında daha fazla bilgi için bkz: [bağlamaları genişletme](../../../../docs/framework/wcf/extending/extending-bindings.md).  
  
 WCF'de tüm bağlamaları, oluşur *bağlama öğeleri*. Her bağlama öğesi türetilen <xref:System.ServiceModel.Channels.BindingElement> sınıfı. Sistem tarafından sağlanan bağlamalar gibi <xref:System.ServiceModel.BasicHttpBinding> oluşturun ve kendi bağlama öğeleri yapılandırın. Bu konu erişmek ve doğrudan bağlamada sunulmaz Bu bağlama öğeleri özelliklerini değiştirmek nasıl gösterir; Özellikle, <xref:System.ServiceModel.BasicHttpBinding> sınıfı.  
  
 Tek tek bağlama öğeleri tarafından temsil edilen bir koleksiyonda bulunan <xref:System.ServiceModel.Channels.BindingElementCollection> sınıfı ve bu sırada eklenir: işlem akış, güvenilir oturum, güvenlik, bileşik çift yönlü, tek yönlü, akış güvenliği, ileti kodlama ve taşıma. Listelenen tüm bağlama öğeleri her bağlama gerekli olduğunu unutmayın. Kullanıcı tanımlı bağlama öğeleri bu bağlama öğesi koleksiyonda da görüntülenebilir ve daha önce açıklandığı gibi aynı sırada görünmesi gerekir. Örneğin, kullanıcı tanımlı bir aktarım bağlama öğesi koleksiyonun son öğesi olması gerekir.  
  
 <xref:System.ServiceModel.BasicHttpBinding> Sınıfı üç bağlama öğeleri içerir:  
  
1.  Ya da bağlama öğesi, isteğe bağlı bir güvenlik <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> HTTP taşıma (ileti düzeyi güvenlik) ile kullanılan sınıf veya <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> Aktarım Katmanı Güvenliği de HTTPS aktarımı durumda sağladığında kullanılan sınıfı kullanılır.  
  
2.  Bağlama öğesi, ya da gerekli ileti Kodlayıcı <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> veya <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>.  
  
3.  Bağlama öğesi, ya da gerekli bir aktarım <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, veya <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.  
  
 Bu örnekte biz bağlama örneği oluşturun, oluşturun bir *özel bağlama* kendisinden özel bağlama bağlama öğeleri inceleyin ve biz HTTP bağlama öğesi bulduğunuzda ayarlarız kendi `KeepAliveEnabled` özelliğine`false`. `KeepAliveEnabled` Doğrudan özellik gösterilmez `BasicHttpBinding`, bağlama öğesi aşağı gidin ve bu özelliği ayarlamak için özel bağlama oluşturmanız gerekir.  
  
### <a name="to-modify-a-system-provided-binding"></a>Sistem tarafından sağlanan bir bağlamayı değiştirmek için  
  
1.  Bir örneğini oluşturmak <xref:System.ServiceModel.BasicHttpBinding> sınıfı ve ileti düzeyi kendi güvenlik modunu ayarlama.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#1)]
     [!code-vb[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#1)]  
  
2.  Özel bağlama bağlamayı ve oluşturun bir <xref:System.ServiceModel.Channels.BindingElementCollection> özel bağlamanın özelliklerinden biri sınıfından.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#2)]
     [!code-vb[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#2)]  
  
3.  Döngü <xref:System.ServiceModel.Channels.BindingElementCollection> sınıfı ve ne zaman bulduğunuz <xref:System.ServiceModel.Channels.HttpTransportBindingElement> sınıfı, Ayarla kendi <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> özelliğine `false`.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#3)]
     [!code-vb[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#3)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Özel Bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md)
