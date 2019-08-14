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
ms.openlocfilehash: 0028a0522447588ee0fb183b5b2f93d334a7b2b2
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972076"
---
# <a name="how-to-configure-a-local-issuer"></a>Nasıl yapılır: Yerel Yayımlayan Yapılandırma

Bu konu, bir istemcinin verilen belirteçler için yerel bir veren kullanmak üzere nasıl yapılandırılacağını açıklamaktadır.

Genellikle, bir istemci federe bir hizmetle iletişim kurduğunda, hizmet istemcinin federasyon hizmetinde kimliğini doğrulamak için kullanacağı belirteci vermesi beklenen güvenlik belirteci hizmetinin adresini belirtir. Belirli durumlarda, istemci *yerel bir veren*kullanmak üzere yapılandırılmış olabilir.

Windows Communication Foundation (WCF), Federasyon bağlamasının veren adresinin veya `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` `null`olduğu durumlarda yerel bir veren kullanır. Bu gibi durumlarda, <xref:System.ServiceModel.Description.ClientCredentials> öğesini yerel veren adresiyle ve bu veren ile iletişim kurmak için kullanılacak bağlama ile yapılandırmanız gerekir.

> [!NOTE]
> Sınıfının özelliği olarak ayarlandıysa`true`, yerel bir veren adresi belirtilmez ve [ \<WSFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) veya diğer Federasyon bağlamasıyla belirtilen veren adresi <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> `ClientCredentials` `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self` ,`http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous`, veya ise `null`, Windows CardSpace veren kullanılır.

## <a name="to-configure-the-local-issuer-in-code"></a>Kod içinde yerel sertifikayı yapılandırmak için

1. Türünde değişken oluşturma<xref:System.ServiceModel.Security.IssuedTokenClientCredential>

2. Değişkenini <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> `ClientCredentials` sınıfının özelliğinden döndürülen örneğe ayarlayın. <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> Bu örnek, istemcisinin özelliği (öğesinden <xref:System.ServiceModel.ClientBase%601>devralınmış) <xref:System.ServiceModel.ChannelFactory>veya <xref:System.ServiceModel.ChannelFactory.Credentials%2A> özelliği tarafından döndürülür:

     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]

3. Özelliğini, yerel veren 'in adresiyle <xref:System.ServiceModel.EndpointAddress>, oluşturucunun bir bağımsız değişkeni olarak yeni bir örneğine ayarlayın. <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A>

     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]

     Alternatif olarak, Oluşturucu için <xref:System.Uri> bağımsız değişken olarak yeni bir örnek oluşturun.

     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]

     Parametresi, gösterildiği gibi bir <xref:System.ServiceModel.Channels.AddressHeader> örnek dizisidir. `addressHeaders`

     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]

4. <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> Özelliğini kullanarak yerel veren için bağlamayı ayarlayın.

     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]

5. İsteğe bağlı. <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> Özelliği tarafından döndürülen koleksiyona böyle davranışlar ekleyerek yerel veren için yapılandırılmış uç nokta davranışları ekleyin.

     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]

## <a name="to-configure-the-local-issuer-in-configuration"></a>Yapılandırmada yerel sertifikayı yapılandırmak için

1. Bir uç nokta [davranışında \<ClientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) öğesinin bir alt öğesi olan [ \<IssuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) öğesinin bir alt öğesi olarak bir [ \<LocalIssuer >](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md) öğesi oluşturun.

2. Özniteliği, `address` belirteç isteklerini kabul edecek yerel veren adresi olarak ayarlayın.

3. `binding` Ve`bindingConfiguration` özniteliklerini, yerel veren uç noktasıyla iletişim kurarken kullanılacak uygun bağlamaya başvuran değerlere ayarlayın.

4. İsteğe bağlı. Identity > öğesini <`localIssuer`> öğesinin bir alt öğesi olarak ayarlayın ve yerel veren için kimlik bilgilerini belirtin. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)

5. İsteğe bağlı. `localIssuer` [Üst > bilgileri < > öğesinin bir alt öğesi olarak ayarlayın ve yerel sertifikayı vereni doğru bir şekilde ele almak için gereken ek üstbilgileri belirtin. \<](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)

## <a name="net-framework-security"></a>.NET Framework Güvenliği

Belirli bir bağlama için bir veren adresi ve bağlama belirtilirse, bu bağlamayı kullanan uç noktalar için yerel veren kullanılmaz. Her zaman yerel vereni kullanması beklenen istemciler böyle bir bağlamayı kullanmamalıdır veya veren adresinin olması `null`için bağlamayı değiştirdiklerinden emin olmalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Federasyon Hizmeti kimlik bilgilerini yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Nasıl yapılır: Federe Istemci oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Nasıl yapılır: WSFederationHttpBinding oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
