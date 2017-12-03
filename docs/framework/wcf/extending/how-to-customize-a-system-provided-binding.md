---
title: "Nasıl yapılır: Sistem Tarafından Sağlanan Bir Bağlamayı Özelleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: f8b97862-e8bb-470d-8b96-07733c21fe26
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c46886879d19d612827b94821e0105c68c437c56
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-customize-a-system-provided-binding"></a>Nasıl yapılır: Sistem Tarafından Sağlanan Bir Bağlamayı Özelleştirme
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]temel bağlama öğeleri özelliklerden bazıları, ancak tüm özellikleri yapılandırmanıza olanak tanıyan çeşitli sistem tarafından sağlanan bağlamaları içerir. Bu konu, özelliklerin özel bağlama oluşturma için bağlama öğeleri nasıl ayarlanacağını gösterir.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]doğrudan oluşturmak ve bağlama öğeleri sistem tarafından sağlanan bağlamalar kullanmadan yapılandırmak bkz: nasıl [özel bağlamaları](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]bkz: oluşturma ve özel bağlamaları genişletme [bağlamaları genişletme](../../../../docs/framework/wcf/extending/extending-bindings.md).  
  
 İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tüm bağlamaları, oluşur *bağlama öğeleri*. Her bağlama öğesi türetilen <xref:System.ServiceModel.Channels.BindingElement> sınıfı. Sistem tarafından sağlanan bağlamalar gibi <xref:System.ServiceModel.BasicHttpBinding> oluşturun ve kendi bağlama öğeleri yapılandırın. Bu konu erişmek ve doğrudan bağlamada sunulmaz Bu bağlama öğeleri özelliklerini değiştirmek nasıl gösterir; Özellikle, <xref:System.ServiceModel.BasicHttpBinding> sınıfı.  
  
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
 [Özel bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md)
