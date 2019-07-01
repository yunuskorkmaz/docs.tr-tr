---
title: 'Nasıl yapılır: Yerel Yayımlayan Yapılandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 15263371-514e-4ea6-90fb-14b4939154cd
ms.openlocfilehash: 98d4c01bf2b84a6379eca5d0e1d5dbee68dc7cdd
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487145"
---
# <a name="how-to-configure-a-local-issuer"></a>Nasıl yapılır: Yerel Yayımlayan Yapılandırma
Bu konuda verilen belirteçleri yerel yayımlayan kullanmak için bir istemciyi nasıl yapılandıracağınız açıklanmaktadır.  
  
 Genellikle, bir istemci bir Federasyon Hizmeti ile iletişim kurduğunda, hizmet istemci belirteci vermek için beklenen belirteç hizmeti, federe hizmete kendi kimliğini doğrulamak için kullanacağı güvenlik adresini belirtir. Belirli durumlarda istemci kullanmak için yapılandırılabilir bir *yerel yayımlayan*.  
  
 Windows Communication Foundation (WCF) kullanan yerel yayımlayan bir federe bağlama veren adresini olduğu durumlarda `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` veya `null`. Bu gibi durumlarda, yapılandırmanız gereken <xref:System.ServiceModel.Description.ClientCredentials> adresiyle yerel dağıtımcının ve bağlama bu veren ile iletişim kurmak için kullanılacak.  
  
> [!NOTE]
>  Varsa <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> özelliği `ClientCredentials` sınıf ayarlanmış `true`yerel yayımlayan adresi belirtilmedi ve veren adresi tarafından belirtilen [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) veya diğer Federe bağlama `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self`, `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous`, veya `null`, Windows CardSpace veren kullanılır.  
  
### <a name="to-configure-the-local-issuer-in-code"></a>Kodu yerel yayımlayan yapılandırma  
  
1. Türünde bir değişken oluşturma <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
2. Öğesinden döndürülen örneği için değişkeni ayarlayın <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> özelliği `ClientCredentials` sınıfı. Bu örnek tarafından döndürülen <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> özelliği istemcinin (devralınan <xref:System.ServiceModel.ClientBase%601>) veya <xref:System.ServiceModel.ChannelFactory.Credentials%2A> özelliği <xref:System.ServiceModel.ChannelFactory>:  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
3. Ayarlama <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> özelliğine yeni bir örneğini <xref:System.ServiceModel.EndpointAddress>, oluşturucusuna bağımsız değişken olarak yerel dağıtımcının adresine sahip.  
  
     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]  
  
     Alternatif olarak, yeni bir oluşturma <xref:System.Uri> oluşturucusuna bağımsız değişken olarak örneği.  
  
     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]  
  
     `addressHeaders` Parametresi, bir dizi <xref:System.ServiceModel.Channels.AddressHeader> gösterildiği gibi örnekler.  
  
     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]  
  
4. Kullanarak yerel sertifika verenin bağlamasını ayarlamak <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> özelliği.  
  
     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]  
  
5. İsteğe bağlı. Tarafından döndürülen bir koleksiyonda gibi davranışları ekleyerek yapılandırılmış uç nokta davranışları için yerel dağıtımcının ekleme <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> özelliği.  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-local-issuer-in-configuration"></a>Yerel yayımlayan yapılandırma yapılandırmak için  
  
1. Oluşturma bir [ \<localIssuer >](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md) öğesi alt öğesi olarak [ \<IssuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) kendisi bir alt öğesi olan öğeyi [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) öğesinde bir uç nokta davranışı.  
  
2. Ayarlama `address` belirteci isteklerini kabul edecek yerel dağıtımcının adresine özniteliği.  
  
3. Ayarlama `binding` ve `bindingConfiguration` öznitelikleri değerlerine başvuran yerel veren uç noktası ile iletişim kurarken kullanması için uygun bağlama.  
  
4. İsteğe bağlı. Ayarlama [ \<kimlik >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) öğesi alt öğesi olarak <`localIssuer`> öğesi ve yerel dağıtımcının için kimlik bilgilerini belirtin.  
  
5. İsteğe bağlı. Ayarlama [ \<üstbilgiler >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) öğesi alt öğesi olarak <`localIssuer`> öğesi ve yerel dağıtımcının doğru bir şekilde çözmek için gerekli ek üstbilgi belirtin.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Belirli bir bağlama için bir veren adresi ve bağlama belirtilirse, yerel sertifika verenin bu bağlamayı kullanan uç noktaları için kullanılmaz unutmayın. Böyle bir bağlamanın kullanmayın veya veren adresi böylece bunlar bağlama değiştirme her zaman yerel dağıtımcının kullanmayı düşündüğünüz istemcileri sağlamak `null`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Federe bir hizmette kimlik bilgilerini yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Nasıl yapılır: Federe istemci oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Nasıl yapılır: WSFederationHttpBinding oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
