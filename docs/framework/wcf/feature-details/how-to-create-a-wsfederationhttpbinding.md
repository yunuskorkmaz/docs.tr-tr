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
ms.openlocfilehash: c3ce90c74ae61dfcbfc0b05fc17b25fe0118e071
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141699"
---
# <a name="how-to-create-a-wsfederationhttpbinding"></a>Nasıl yapılır: WSFederationHttpBinding Oluşturma

Windows Communication Foundation (WCF) ' de, <xref:System.ServiceModel.WSFederationHttpBinding> sınıfı ([\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) yapılandırma), Federasyon hizmetini açığa çıkarmak için bir mekanizma sağlar. Diğer bir deyişle, istemcilerin güvenlik belirteci hizmeti tarafından verilen bir güvenlik belirtecini kullanarak kimlik doğrulaması yapmasını gerektiren bir hizmettir. Bu konuda, hem kod hem de yapılandırmada <xref:System.ServiceModel.WSFederationHttpBinding> ayarlama gösterilmektedir. Bağlama oluşturulduktan sonra, bu bağlamayı kullanmak için bir uç nokta ayarlayabilirsiniz.

 Temel adımlar aşağıdaki şekilde özetlenmiştir:

1. Bir güvenlik modu seçin. <xref:System.ServiceModel.WSFederationHttpBinding>, ileti düzeyinde bile uçtan uca güvenlik sağlayan `Message`destekler, bu da birden fazla atlama ve `TransportWithMessageCredential`istemcinin ve hizmetin HTTPS üzerinden doğrudan bağlantı yapmasına olanak tanıyan daha iyi performans sağlar.

    > [!NOTE]
    > <xref:System.ServiceModel.WSFederationHttpBinding> ayrıca güvenlik modu olarak `None` destekler. Bu mod güvenli değildir ve yalnızca hata ayıklama amacıyla sağlanır. Bir hizmet uç noktası, güvenlik modu `None`olarak ayarlanmış bir <xref:System.ServiceModel.WSFederationHttpBinding> ile dağıtılırsa, elde edilen istemci bağlama ( [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)tarafından oluşturulan), `None`güvenlik modu olan bir <xref:System.ServiceModel.WSHttpBinding>.

     Sistem tarafından sağlanmış diğer bağlamalardan farklı olarak, `WSFederationHttpBinding`kullanırken istemci kimlik bilgisi türü seçmek gerekli değildir. Bunun nedeni, istemci kimlik bilgisi türünün her zaman verilen bir belirteç olmasından kaynaklanır. WCF, belirtilen bir verenin belirtecini alır ve istemcinin kimliğini doğrulamak için bu belirteci hizmete sunar.

2. Federasyon istemcilerinde <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> özelliğini güvenlik belirteci hizmetinin URL 'SI olarak ayarlayın. Güvenlik belirteci hizmeti ile iletişim kurmak için kullanılacak bağlamaya <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> ayarlayın.

3. İsteğe bağlı. <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> özelliğini bir belirteç türünün Tekdüzen Kaynak tanımlayıcısı (URI) olarak ayarlayın. Federasyon Hizmetleri 'nde hizmetin beklediği belirteç türünü belirtin. Federasyon istemcilerinde, güvenlik belirteci hizmeti 'nden istemci isteklerini belirten belirteç türünü belirtin.

     Hiçbir belirteç türü belirtilmemişse, istemcileri belirteç türü URI 'SI olmayan WS-Trust Istek güvenlik belirteçleri (RSTs) oluşturur ve hizmetler varsayılan olarak güvenlik onayları biçimlendirme dili (SAML) 1,1 belirtecini kullanarak istemci kimlik doğrulaması bekler.

     SAML 1,1 belirtecinin URI 'SI `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`.

4. İsteğe bağlı. Federasyon Hizmetleri 'nde, <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A> özelliğini bir güvenlik belirteci hizmetinin meta veri URL 'SI olarak ayarlayın. Meta veri uç noktası, hizmet istemcilerinin meta verileri yayımlayacak şekilde yapılandırıldıysa uygun bir bağlama/uç nokta çifti seçmesini sağlar. Meta verileri yayımlama hakkında daha fazla bilgi için bkz. [meta verileri yayımlama](publishing-metadata.md).

 Ayrıca, verilen belirteçte bir kanıt anahtarı olarak kullanılan anahtar türü, istemci ile hizmet arasında kullanılacak algoritma paketi, hizmet kimlik bilgisini anlaşma veya açık bir şekilde belirtme konusunda verilen belirtecin ve istemcinin güvenlik belirteci hizmetine gönderdiği isteğe eklenmesi gereken ek XML öğelerini içermesini bekler.

> [!NOTE]
> `NegotiateServiceCredential` özelliği yalnızca `SecurityMode` `Message`olarak ayarlandığında geçerlidir. `SecurityMode` `TransportWithMessageCredential`olarak ayarlanırsa `NegotiateServiceCredential` özelliği yok sayılır.

## <a name="to-configure-a-wsfederationhttpbinding-in-code"></a>Kodda bir WSFederationHttpBinding yapılandırmak için

1. <xref:System.ServiceModel.WSFederationHttpBinding>bir örneğini oluşturun.

2. <xref:System.ServiceModel.WSFederationHttpSecurity.Mode%2A> özelliğini <xref:System.ServiceModel.WSFederationHttpSecurityMode> veya <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message> gereken şekilde ayarlayın. <xref:System.ServiceModel.Security.SecurityAlgorithmSuite.Basic256%2A> dışında bir algoritma paketi gerekliyse, <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.AlgorithmSuite%2A> özelliğini <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>alınan bir değer olarak ayarlayın.

3. <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> özelliğini uygun şekilde ayarlayın.

4. <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> özelliğini <xref:System.IdentityModel.Tokens.SecurityKeyType>`SymmetricKey` veya olarak ayarlayın.`AsymmetricKey` gerektiği gibi.

5. <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> özelliğini uygun değer olarak ayarlayın. Değer ayarlanmamışsa, WCF varsayılan olarak `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`SAML 1,1 belirteçlerini gösterir.

6. Yerel veren belirtilmemişse istemcisinde gereklidir; hizmet üzerinde isteğe bağlı. Güvenlik belirteci hizmetinin adresini ve kimlik bilgilerini içeren bir <xref:System.ServiceModel.EndpointAddress> oluşturun ve <xref:System.ServiceModel.EndpointAddress> örneğini <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> özelliğine atayın.

7. Yerel veren belirtilmemişse istemcisinde gereklidir; hizmette kullanılmıyor. `SecurityTokenService` için bir <xref:System.ServiceModel.Channels.Binding> oluşturun ve <xref:System.ServiceModel.Channels.Binding> örneğini <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> özelliğine atayın.

8. İstemcide kullanılmıyor; hizmet üzerinde isteğe bağlı. Güvenlik belirteci hizmetinin meta verileri için bir <xref:System.ServiceModel.EndpointAddress> örneği oluşturun ve `IssuerMetadataAddress` özelliğine atayın.

9. Hem istemcide hem de hizmette isteğe bağlıdır. <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A> özelliği tarafından döndürülen koleksiyona bir veya daha fazla <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement> örneği oluşturun ve ekleyin.

10. Hem istemcide hem de hizmette isteğe bağlıdır. <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A> özelliği tarafından döndürülen koleksiyona bir veya daha fazla <xref:System.Xml.XmlElement> örneği oluşturun ve ekleyin.

## <a name="to-create-a-federated-endpoint-in-configuration"></a>Yapılandırmada bir Federasyon uç noktası oluşturmak için

1. Uygulama yapılandırma dosyasındaki [\<bindings >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) öğesinin bir alt öğesi olarak bir [\<WSFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) oluşturun.

2. [\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) alt öğesi olarak bir [\<bağlama >](../../configure-apps/file-schema/wcf/bindings.md) öğesi oluşturun ve `name` özniteliğini uygun bir değere ayarlayın.

3. [\<binding >](../../configure-apps/file-schema/wcf/bindings.md) öğesinin alt öğesi olarak bir `<security>` öğesi oluşturun.

4. `<security>` öğesindeki `mode` özniteliğini, gerektiği gibi `Message` veya `TransportWithMessageCredential`bir değere ayarlayın.

5. `<security>` öğesinin alt öğesi olarak bir `<message>` öğesi oluşturun.

6. İsteğe bağlı. `<message>` öğesindeki `algorithmSuite` özniteliğini uygun bir değerle ayarlayın. Varsayılan, `Basic256` değeridir.

7. İsteğe bağlı. Asimetrik bir kanıt anahtarı gerekliyse, `<message>` öğesinin `issuedKeyType` özniteliğini `AsymmetricKey`olarak ayarlayın. Varsayılan, `SymmetricKey` değeridir.

8. İsteğe bağlı. `<message>` öğesindeki `issuedTokenType` özniteliğini ayarlayın.

9. Yerel veren belirtilmemişse istemcisinde gereklidir; hizmet üzerinde isteğe bağlı. `<message>` öğesinin alt öğesi olarak bir `<issuer>` öğesi oluşturun.

10. `address` özniteliğini `<issuer>` öğesi olarak ayarlayın ve güvenlik belirteci hizmetinin belirteç isteklerini kabul ettiği adresi belirtin.

11. İsteğe bağlı. Bir `<identity>` alt öğesi ekleyin ve güvenlik belirteci hizmetinin kimliğini belirtin

12. Daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](service-identity-and-authentication.md).

13. Yerel veren belirtilmemişse istemcisinde gereklidir; hizmette kullanılmıyor. Güvenlik belirteci hizmetiyle iletişim kurmak için kullanılabilecek bağlamalar bölümünde bir [\<bağlama >](../../configure-apps/file-schema/wcf/bindings.md) öğesi oluşturun. Bağlama oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: yapılandırmada hizmet bağlaması belirtme](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).

14. `<issuer>` öğesinin `binding` ve `bindingConfiguration` özniteliklerini ayarlayarak, önceki adımda oluşturulan bağlamayı belirtin.

15. İstemcide kullanılmıyor; hizmet üzerinde isteğe bağlı. `message`> öğesinin alt öğesi olarak bir `<issuerMetadata>` öğesi oluşturun. Ardından, `<issuerMetadata>` öğesindeki bir `address` özniteliğinde, güvenlik belirteci hizmetinin meta verilerini yayımlayacağınız adresi belirtin. İsteğe bağlı olarak, bir `<identity>` alt öğesi ekleyin ve güvenlik belirteci hizmetinin kimliğini belirtin.

16. Hem istemcide hem de hizmette isteğe bağlıdır. `<message>` öğesinin alt öğesi olarak bir `<claimTypeRequirements>` öğesi ekleyin. `<claimTypeRequirements>` öğesine [> öğe\<](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md) ekleyerek ve `claimType` özniteliğiyle talep türünü belirterek hizmetin bağımlı olduğu zorunlu ve isteğe bağlı talepler belirtin. `isOptional` özniteliğini ayarlayarak belirli bir talebin gerekli veya isteğe bağlı olup olmadığını belirtin.

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, bir `WSFederationHttpBinding` imperatively ayarlamaya yönelik kodu gösterir.

[!code-csharp[c_FederationBinding#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_federationbinding/cs/source.cs#2)]
[!code-vb[c_FederationBinding#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_federationbinding/vb/source.vb#2)]

## <a name="see-also"></a>Ayrıca bkz.

- [Federasyon](federation.md)
- [Federasyon Örneği](../../../../docs/framework/wcf/samples/federation-sample.md)
- [Nasıl yapılır: WSFederationHttpBinding Güvenli Oturumlarını Devre Dışı Bırakma](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
