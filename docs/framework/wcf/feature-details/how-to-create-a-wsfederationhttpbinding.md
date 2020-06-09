---
title: 'Nasıl yapılır: WSFederationHttpBinding Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: e54897d7-aa6c-46ec-a278-b2430c8c2e10
ms.openlocfilehash: ccc28c46e8be0b835cf08d372ef85b8a66e989ef
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595446"
---
# <a name="how-to-create-a-wsfederationhttpbinding"></a>Nasıl yapılır: WSFederationHttpBinding Oluşturma

Windows Communication Foundation (WCF) ' de, <xref:System.ServiceModel.WSFederationHttpBinding> Sınıf ( [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) yapılandırmada), Federasyon hizmetini açığa çıkarmak için bir mekanizma sağlar. Diğer bir deyişle, istemcilerin güvenlik belirteci hizmeti tarafından verilen bir güvenlik belirtecini kullanarak kimlik doğrulaması yapmasını gerektiren bir hizmettir. Bu konuda, hem kodda hem de yapılandırmada bir nasıl ayarlanacağı gösterilmektedir <xref:System.ServiceModel.WSFederationHttpBinding> . Bağlama oluşturulduktan sonra, bu bağlamayı kullanmak için bir uç nokta ayarlayabilirsiniz.

 Temel adımlar aşağıdaki şekilde özetlenmiştir:

1. Bir güvenlik modu seçin. , <xref:System.ServiceModel.WSFederationHttpBinding> `Message` Birden fazla atlama arasında bile ileti düzeyinde uçtan uca güvenlik sağlayan, ve `TransportWithMessageCredential` ISTEMCISININ ve hizmetin https üzerinden doğrudan bağlantı yapabildiği durumlarda daha iyi performans sağlayan destekler.

    > [!NOTE]
    > <xref:System.ServiceModel.WSFederationHttpBinding>Ayrıca `None` güvenlik modu olarak da desteklenir. Bu mod güvenli değildir ve yalnızca hata ayıklama amacıyla sağlanır. Bir hizmet uç noktası, <xref:System.ServiceModel.WSFederationHttpBinding> güvenlik modu olarak ayarlanmış ile bir ile dağıtılırsa `None` , elde edilen istemci bağlama ( [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)tarafından oluşturulan), <xref:System.ServiceModel.WSHttpBinding> güvenlik modudur `None` .

     Sistem tarafından sağlanmış diğer bağlamalardan farklı olarak, kullanırken istemci kimlik bilgisi türü seçmek gerekli değildir `WSFederationHttpBinding` . Bunun nedeni, istemci kimlik bilgisi türünün her zaman verilen bir belirteç olmasından kaynaklanır. WCF, belirtilen bir verenin belirtecini alır ve istemcinin kimliğini doğrulamak için bu belirteci hizmete sunar.

2. Federasyon istemcilerinde, <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> özelliği güvenlik belirteci hizmetinin URL 'si olarak ayarlayın. Öğesini <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> güvenlik belirteci hizmeti ile iletişim kurmak için kullanılacak bağlamaya ayarlayın.

3. İsteğe bağlı. <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A>Özelliği bir belirteç türünün Tekdüzen Kaynak tanımlayıcısı (URI) olarak ayarlayın. Federasyon Hizmetleri 'nde hizmetin beklediği belirteç türünü belirtin. Federasyon istemcilerinde, güvenlik belirteci hizmeti 'nden istemci isteklerini belirten belirteç türünü belirtin.

     Hiçbir belirteç türü belirtilmemişse, istemcileri belirteç türü URI 'SI olmayan WS-Trust Istek güvenlik belirteçleri (RSTs) oluşturur ve hizmetler varsayılan olarak güvenlik onayları biçimlendirme dili (SAML) 1,1 belirtecini kullanarak istemci kimlik doğrulaması bekler.

     SAML 1,1 belirtecinin URI 'SI `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1` .

4. İsteğe bağlı. Federasyon Hizmetleri 'nde, <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A> özelliği bir güvenlik belirteci hizmetinin meta veri URL 'si olarak ayarlayın. Meta veri uç noktası, hizmet istemcilerinin meta verileri yayımlayacak şekilde yapılandırıldıysa uygun bir bağlama/uç nokta çifti seçmesini sağlar. Meta verileri yayımlama hakkında daha fazla bilgi için bkz. [meta verileri yayımlama](publishing-metadata.md).

 Ayrıca, verilen belirteçte bir kanıt anahtarı olarak kullanılan anahtar türü, istemci ile hizmet arasında kullanılacak algoritma paketi, hizmet kimlik bilgisini anlaşma ya da açık bir şekilde belirtme, hizmetin verilen belirtecin içermesini ve istemcinin güvenlik belirteci hizmetine gönderdiği isteğe eklenmesi gereken ek XML öğelerini de içeren diğer özellikleri de ayarlayabilirsiniz.

> [!NOTE]
> `NegotiateServiceCredential`Özelliği yalnızca `SecurityMode` öğesine ayarlandığında geçerlidir `Message` . `SecurityMode`Olarak ayarlanırsa `TransportWithMessageCredential` , `NegotiateServiceCredential` özelliği yok sayılır.

## <a name="to-configure-a-wsfederationhttpbinding-in-code"></a>Kodda bir WSFederationHttpBinding yapılandırmak için

1. <xref:System.ServiceModel.WSFederationHttpBinding> nesnesinin bir örneğini oluşturun.

2. <xref:System.ServiceModel.WSFederationHttpSecurity.Mode%2A>Özelliğini <xref:System.ServiceModel.WSFederationHttpSecurityMode> gereken şekilde veya gerektiği <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message> şekilde ayarlayın. Dışında bir algoritma paketi <xref:System.ServiceModel.Security.SecurityAlgorithmSuite.Basic256%2A> gerekliyse, <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.AlgorithmSuite%2A> özelliğini öğesinden alınan bir değere ayarlayın <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> .

3. <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A>Özelliği uygun şekilde ayarlayın.

4. <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A>Özelliğini veya olarak ayarlayın <xref:System.IdentityModel.Tokens.SecurityKeyType> `SymmetricKey` .`AsymmetricKey` gerektiği gibi.

5. <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A>Özelliği uygun değere ayarlayın. Değer ayarlanmamışsa, WCF varsayılan olarak `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1` , SAML 1,1 belirteçlerini gösterir.

6. Yerel veren belirtilmemişse istemcisinde gereklidir; hizmet üzerinde isteğe bağlı. <xref:System.ServiceModel.EndpointAddress>Güvenlik belirteci hizmetinin adresini ve kimlik bilgilerini içeren bir oluşturun ve <xref:System.ServiceModel.EndpointAddress> örneği <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> özelliğine atayın.

7. Yerel veren belirtilmemişse istemcisinde gereklidir; hizmette kullanılmıyor. İçin bir oluşturun <xref:System.ServiceModel.Channels.Binding> `SecurityTokenService` ve <xref:System.ServiceModel.Channels.Binding> örneği özelliğine atayın <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> .

8. İstemcide kullanılmıyor; hizmet üzerinde isteğe bağlı. <xref:System.ServiceModel.EndpointAddress>Güvenlik belirteci hizmetinin meta verileri için bir örnek oluşturun ve bunu `IssuerMetadataAddress` özelliğine atayın.

9. Hem istemcide hem de hizmette isteğe bağlıdır. <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>Özelliği tarafından döndürülen koleksiyona bir veya daha fazla örnek oluşturun ve ekleyin <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A> .

10. Hem istemcide hem de hizmette isteğe bağlıdır. <xref:System.Xml.XmlElement>Özelliği tarafından döndürülen koleksiyona bir veya daha fazla örnek oluşturun ve ekleyin <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A> .

## <a name="to-create-a-federated-endpoint-in-configuration"></a>Yapılandırmada bir Federasyon uç noktası oluşturmak için

1. [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) Uygulama yapılandırma dosyasında öğesinin alt öğesi olarak oluşturun.

2. [\<binding>](../../configure-apps/file-schema/wcf/bindings.md)Alt öğesi olarak bir öğesi oluşturun [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ve `name` özniteliği uygun bir değere ayarlayın.

3. Öğesinin `<security>` alt öğesi olarak bir öğe oluşturun [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) .

4. `mode`Öğesinde özniteliğini, `<security>` `Message` gereken şekilde veya değerine ayarlayın `TransportWithMessageCredential` .

5. Öğesinin `<message>` alt öğesi olarak bir öğe oluşturun `<security>` .

6. İsteğe bağlı. `algorithmSuite` `<message>` Öğesi için uygun bir değer içeren özniteliğini ayarlayın. Varsayılan değer: `Basic256`.

7. İsteğe bağlı. Asimetrik bir kanıt anahtarı gerekliyse, `issuedKeyType` `<message>` öğesinin özniteliğini olarak ayarlayın `AsymmetricKey` . Varsayılan değer: `SymmetricKey`.

8. İsteğe bağlı. `issuedTokenType`Öğesinde özniteliğini ayarlayın `<message>` .

9. Yerel veren belirtilmemişse istemcisinde gereklidir; hizmet üzerinde isteğe bağlı. Öğesinin `<issuer>` alt öğesi olarak bir öğesi oluşturun `<message>` .

10. `address`Özniteliğini `<issuer>` öğesine ayarlayın ve güvenlik belirteci hizmetinin belirteç isteklerini kabul ettiği adresi belirtin.

11. İsteğe bağlı. Bir `<identity>` alt öğe ekleyin ve güvenlik belirteci hizmetinin kimliğini belirtin

12. Daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](service-identity-and-authentication.md).

13. Yerel veren belirtilmemişse istemcisinde gereklidir; hizmette kullanılmıyor. [\<binding>](../../configure-apps/file-schema/wcf/bindings.md)Bağlamalar bölümünde güvenlik belirteci hizmeti ile iletişim kurmak için kullanılabilecek bir öğe oluşturun. Bağlama oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: yapılandırmada hizmet bağlaması belirtme](../how-to-specify-a-service-binding-in-configuration.md).

14. Öğesinin ve özniteliklerini ayarlayarak, önceki adımda oluşturulan bağlamayı belirtin `binding` `bindingConfiguration` `<issuer>` .

15. İstemcide kullanılmıyor; hizmet üzerinde isteğe bağlı. `<issuerMetadata>`<> öğesinin alt öğesi olarak bir öğe oluşturun `message` . Ardından, öğesindeki bir `address` özniteliğinde `<issuerMetadata>` , güvenlik belirteci hizmetinin meta verilerini yayımlayacağınız adresi belirtin. İsteğe bağlı olarak, bir `<identity>` alt öğe ekleyin ve güvenlik belirteci hizmetinin kimliğini belirtin.

16. Hem istemcide hem de hizmette isteğe bağlıdır. Öğesinin `<claimTypeRequirements>` alt öğesi olarak bir öğesi ekleyin `<message>` . Öğeye öğe ekleyerek [\<add>](../../configure-apps/file-schema/wcf/add-of-claimtyperequirements.md) `<claimTypeRequirements>` ve öznitelik ile talep türünü belirterek hizmetin bağımlı olduğu zorunlu ve isteğe bağlı talepler belirtin `claimType` . Özniteliği ayarlayarak belirli bir talebin gerekli veya isteğe bağlı olup olmadığını belirtin `isOptional` .

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, bir imperatively ayarlamaya yönelik kodu gösterir `WSFederationHttpBinding` .

[!code-csharp[c_FederationBinding#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_federationbinding/cs/source.cs#2)]
[!code-vb[c_FederationBinding#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_federationbinding/vb/source.vb#2)]

## <a name="see-also"></a>Ayrıca bkz.

- [Federasyon](federation.md)
- [Federasyon Örneği](../samples/federation-sample.md)
- [Nasıl yapılır: WSFederationHttpBinding Güvenli Oturumlarını Devre Dışı Bırakma](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
