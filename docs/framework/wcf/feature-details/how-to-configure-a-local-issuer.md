---
title: "Nasıl yapılır: Yerel Yayımlayan Yapılandırma"
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
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 15263371-514e-4ea6-90fb-14b4939154cd
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 90edf0735d890e0abc1560de5a7f523ee2faa7c8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-configure-a-local-issuer"></a>Nasıl yapılır: Yerel Yayımlayan Yapılandırma
Bu konu, istemciyi yerel yayımlayan verilen belirteçleri kullanacak şekilde yapılandırmak açıklar.  
  
 Genellikle, bir istemci bir Federasyon Hizmeti ile iletişim kurduğunda, hizmet istemci belirteci vermek için beklenen belirteci hizmeti kendisini Federasyon Hizmeti için kimlik doğrulaması için kullanacağınız güvenlik adresini belirtir. Belirli durumlarda, istemci kullanmak için yapılandırılabilir bir *yerel yayımlayan*.  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Yerel yayımlayan bir federe bağlama veren adresini http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous olduğu durumlarda kullanır veya `null`. Böyle durumlarda, yapılandırmalısınız <xref:System.ServiceModel.Description.ClientCredentials> adresi bu veren ile iletişim kurmak için kullanılacak yerel yayımlayan ve bağlama ile.  
  
> [!NOTE]
>  Varsa <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> özelliği `ClientCredentials` sınıfı ayarlanmış `true`, yerel veren adresi belirtilmedi ve veren adresi tarafından belirtilen [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) veya diğer Federe bağlama olduğu http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self, http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous, veya `null`, sonra Windows [!INCLUDE[infocard](../../../../includes/infocard-md.md)] veren kullanılır.  
  
### <a name="to-configure-the-local-issuer-in-code"></a>Yerel yayımlayan yapılandırma  
  
1.  Türünde bir değişken oluşturma<xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
2.  Döndürülen örneğine değişkenini <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> özelliği `ClientCredentials` sınıfı. Bu örnek tarafından döndürülen <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> özelliği istemcinin (devralınan <xref:System.ServiceModel.ClientBase%601>) veya <xref:System.ServiceModel.ChannelFactory.Credentials%2A> özelliği <xref:System.ServiceModel.ChannelFactory>:  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
3.  Ayarlama <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> yeni bir örneğini özelliğine <xref:System.ServiceModel.EndpointAddress>, oluşturucuya bağımsız değişken olarak yerel verenin adresine sahip.  
  
     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]  
  
     Alternatif olarak, yeni bir oluşturun <xref:System.Uri> oluşturucu bağımsız değişken olarak örneği.  
  
     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]  
  
     `addressHeaders` Parametredir bir dizi <xref:System.ServiceModel.Channels.AddressHeader> gösterildiği gibi örnekleri.  
  
     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]  
  
4.  Kullanarak yerel yayımlayan için bağlama ayarlamak <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> özelliği.  
  
     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]  
  
5.  İsteğe bağlı. Yapılandırılmış uç noktası davranışları yerel vericisi gibi davranışları tarafından döndürülen koleksiyonuna ekleyerek <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> özelliği.  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-local-issuer-in-configuration"></a>Yerel yayımlayan yapılandırma yapılandırmak için  
  
1.  Oluşturma bir [ \<localIssuer >](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md) öğesi bir alt öğesi olarak [ \<IssuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) kendisini bir alt öğesi olan öğeyi [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) bir uç noktası davranışı öğesinde.  
  
2.  Ayarlama `address` belirteç istekleri kabul edecek yerel yayımlayan adresine özniteliği.  
  
3.  Ayarlama `binding` ve `bindingConfiguration` öznitelikleri yerel yayımlayan bitiş noktası ile iletişim kurarken kullanmak üzere uygun bağlama başvuru değerleri.  
  
4.  İsteğe bağlı. Ayarlama [ \<kimliği >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) öğesi bir alt öğesi olarak <`localIssuer`> öğesi ve yerel veren kimlik bilgilerini belirtin.  
  
5.  İsteğe bağlı. Ayarlama [ \<üstbilgiler >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) öğesi bir alt öğesi olarak <`localIssuer`> öğesi ve doğru yerel yayımlayan değinmek için gerekli ek üstbilgi belirtin.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bir veren adresi ve bağlama için belirtilen bir bağlama belirtilirse, yerel yayımlayan bu bağlamayı kullanan uç noktaları için kullanılıp kullanılmadığını unutmayın. Her zaman yerel yayımlayan kullanmayı düşündüğünüz istemcileri sağlamak veren adresi böylece bunlar bağlama değiştirmek veya böyle bir bağlama kullanmayın `null`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: federe bir hizmette kimlik bilgilerini yapılandırın](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [Nasıl yapılır: federe istemci oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Nasıl yapılır: WSFederationHttpBinding oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
