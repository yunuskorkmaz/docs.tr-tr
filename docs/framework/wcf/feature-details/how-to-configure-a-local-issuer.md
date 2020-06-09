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
ms.openlocfilehash: 7da3cd34d0840eea48c9ef0bb89fb6580b87623b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601250"
---
# <a name="how-to-configure-a-local-issuer"></a>Nasıl yapılır: Yerel Yayımlayan Yapılandırma

Bu konu, bir istemcinin verilen belirteçler için yerel bir veren kullanmak üzere nasıl yapılandırılacağını açıklamaktadır.

Genellikle, bir istemci federe bir hizmetle iletişim kurduğunda, hizmet istemcinin federasyon hizmetinde kimliğini doğrulamak için kullanacağı belirteci vermesi beklenen güvenlik belirteci hizmetinin adresini belirtir. Belirli durumlarda, istemci *yerel bir veren*kullanmak üzere yapılandırılmış olabilir.

Windows Communication Foundation (WCF), Federasyon bağlamasının veren adresinin veya olduğu durumlarda yerel bir veren kullanır `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` `null` . Bu gibi durumlarda, öğesini <xref:System.ServiceModel.Description.ClientCredentials> yerel veren adresiyle ve bu veren ile iletişim kurmak için kullanılacak bağlama ile yapılandırmanız gerekir.

> [!NOTE]
> <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> `ClientCredentials` Sınıfının özelliği olarak ayarlandıysa `true` , yerel bir veren adresi belirtilmez ve [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) veya diğer Federasyon bağlaması tarafından belirtilen veren adresi, veya ise, `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self` `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` `null` Windows CardSpace veren kullanılır.

## <a name="to-configure-the-local-issuer-in-code"></a>Kod içinde yerel sertifikayı yapılandırmak için

1. Türünde değişken oluşturma<xref:System.ServiceModel.Security.IssuedTokenClientCredential>

2. Değişkenini sınıfının özelliğinden döndürülen örneğe ayarlayın <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> `ClientCredentials` . Bu örnek, <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> istemcisinin özelliği (öğesinden devralınmış <xref:System.ServiceModel.ClientBase%601> ) veya özelliği tarafından döndürülür <xref:System.ServiceModel.ChannelFactory.Credentials%2A> <xref:System.ServiceModel.ChannelFactory> :

     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]

3. Özelliğini, <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> <xref:System.ServiceModel.EndpointAddress> yerel veren 'in adresiyle, oluşturucunun bir bağımsız değişkeni olarak yeni bir örneğine ayarlayın.

     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]

     Alternatif olarak, <xref:System.Uri> Oluşturucu için bağımsız değişken olarak yeni bir örnek oluşturun.

     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]

     `addressHeaders`Parametresi <xref:System.ServiceModel.Channels.AddressHeader> , gösterildiği gibi bir örnek dizisidir.

     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]

4. Özelliğini kullanarak yerel veren için bağlamayı ayarlayın <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> .

     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]

5. İsteğe bağlı. Özelliği tarafından döndürülen koleksiyona böyle davranışlar ekleyerek yerel veren için yapılandırılmış uç nokta davranışları ekleyin <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> .

     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]

## <a name="to-configure-the-local-issuer-in-configuration"></a>Yapılandırmada yerel sertifikayı yapılandırmak için

1. Bir [\<localIssuer>](../../configure-apps/file-schema/wcf/localissuer.md) [\<issuedToken>](../../configure-apps/file-schema/wcf/issuedtoken.md) [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) uç nokta davranışında öğesinin bir alt öğesi olan öğesinin bir alt öğesi olarak bir öğesi oluşturun.

2. Özniteliği, `address` belirteç isteklerini kabul edecek yerel veren adresi olarak ayarlayın.

3. `binding`Ve özniteliklerini, `bindingConfiguration` yerel veren uç noktasıyla iletişim kurarken kullanılacak uygun bağlamaya başvuran değerlere ayarlayın.

4. İsteğe bağlı. [\<identity>](../../configure-apps/file-schema/wcf/identity.md)Öğesini <> öğesinin bir alt öğesi olarak ayarlayın `localIssuer` ve yerel veren için kimlik bilgilerini belirtin.

5. İsteğe bağlı. [\<headers>](../../configure-apps/file-schema/wcf/headers.md)Öğesini <> öğesinin bir alt öğesi olarak ayarlayın `localIssuer` ve yerel sertifikayı vereni doğru bir şekilde ele almak için gereken ek üstbilgileri belirtin.

## <a name="net-framework-security"></a>.NET Framework Güvenliği

Belirli bir bağlama için bir veren adresi ve bağlama belirtilirse, bu bağlamayı kullanan uç noktalar için yerel veren kullanılmaz. Her zaman yerel vereni kullanması beklenen istemciler böyle bir bağlamayı kullanmamalıdır veya veren adresinin olması için bağlamayı değiştirdiklerinden emin olmalıdır `null` .

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma](how-to-configure-credentials-on-a-federation-service.md)
- [Nasıl yapılır: Federe İstemci Oluşturma](how-to-create-a-federated-client.md)
- [Nasıl yapılır: WSFederationHttpBinding Oluşturma](how-to-create-a-wsfederationhttpbinding.md)
