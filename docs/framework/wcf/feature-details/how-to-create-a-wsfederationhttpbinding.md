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
ms.openlocfilehash: 9728c908331d5eabcff04d094e7fcbe42f636963
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911215"
---
# <a name="how-to-create-a-wsfederationhttpbinding"></a>Nasıl yapılır: WSFederationHttpBinding Oluşturma

Windows Communication Foundation (WCF) ' de, <xref:System.ServiceModel.WSFederationHttpBinding> Sınıf ([\<WSFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ), Federasyon hizmetini açığa çıkarmak için bir mekanizma sağlar. Diğer bir deyişle, istemcilerin güvenlik belirteci hizmeti tarafından verilen bir güvenlik belirtecini kullanarak kimlik doğrulaması yapmasını gerektiren bir hizmettir. Bu konuda, hem kodda hem de yapılandırmada <xref:System.ServiceModel.WSFederationHttpBinding> bir nasıl ayarlanacağı gösterilmektedir. Bağlama oluşturulduktan sonra, bu bağlamayı kullanmak için bir uç nokta ayarlayabilirsiniz.

 Temel adımlar aşağıdaki şekilde özetlenmiştir:

1. Bir güvenlik modu seçin. , <xref:System.ServiceModel.WSFederationHttpBinding> Birden `Message`fazla atlama arasında bile ileti düzeyinde uçtan uca güvenlik sağlayan, ve `TransportWithMessageCredential`istemcisinin ve hizmetin üzerinden doğrudan bağlantı yapabildiği durumlarda daha iyi performans sağlayan destekler. 'Dir.

    > [!NOTE]
    > Ayrıca güvenlik modu olarak da desteklenir `None`. <xref:System.ServiceModel.WSFederationHttpBinding> Bu mod güvenli değildir ve yalnızca hata ayıklama amacıyla sağlanır. Bir hizmet uç noktası, güvenlik modu olarak <xref:System.ServiceModel.WSFederationHttpBinding> `None`ayarlanmış ile ile dağıtılırsa, elde edilen istemci bağlama ( [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)tarafından oluşturulan), bir <xref:System.ServiceModel.WSHttpBinding> güvenlik modu `None`.

     Sistem tarafından sağlanmış diğer bağlamalardan farklı olarak, kullanırken `WSFederationHttpBinding`istemci kimlik bilgisi türü seçmek gerekli değildir. Bunun nedeni, istemci kimlik bilgisi türünün her zaman verilen bir belirteç olmasından kaynaklanır. WCF, belirtilen bir verenin belirtecini alır ve istemcinin kimliğini doğrulamak için bu belirteci hizmete sunar.

2. Federasyon istemcilerinde, <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> özelliği güvenlik belirteci hizmetinin URL 'si olarak ayarlayın. <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> Öğesini güvenlik belirteci hizmeti ile iletişim kurmak için kullanılacak bağlamaya ayarlayın.

3. İsteğe bağlı. <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> Özelliği bir belirteç türünün Tekdüzen Kaynak tanımlayıcısı (URI) olarak ayarlayın. Federasyon Hizmetleri 'nde hizmetin beklediği belirteç türünü belirtin. Federasyon istemcilerinde, güvenlik belirteci hizmeti 'nden istemci isteklerini belirten belirteç türünü belirtin.

     Hiçbir belirteç türü belirtilmemişse, istemcileri belirteç türü URI 'SI olmayan WS-Trust Istek güvenlik belirteçleri (RSTs) oluşturur ve hizmetler varsayılan olarak güvenlik onayları biçimlendirme dili (SAML) 1,1 belirtecini kullanarak istemci kimlik doğrulaması bekler.

     SAML 1,1 belirtecinin `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`URI 'si.

4. İsteğe bağlı. Federasyon Hizmetleri 'nde, <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A> özelliği bir güvenlik belirteci hizmetinin meta veri URL 'si olarak ayarlayın. Meta veri uç noktası, hizmet istemcilerinin meta verileri yayımlayacak şekilde yapılandırıldıysa uygun bir bağlama/uç nokta çifti seçmesini sağlar. Meta verileri yayımlama hakkında daha fazla bilgi için bkz. [meta verileri yayımlama](publishing-metadata.md).

 Ayrıca, verilen belirteçte bir kanıt anahtarı olarak kullanılan anahtar türü, istemci ile hizmet arasında kullanılacak algoritma paketi, hizmet kimlik bilgisini anlaşma veya açık bir şekilde belirtme konusunda verilen belirtecin ve istemcinin güvenlik belirteci hizmetine gönderdiği isteğe eklenmesi gereken ek XML öğelerini içermesini bekler.

> [!NOTE]
> Özelliği yalnızca `SecurityMode` öğesine`Message`ayarlandığındageçerlidir. `NegotiateServiceCredential` `SecurityMode` Olarak ayarlanırsa`TransportWithMessageCredential`, özelliği`NegotiateServiceCredential` yok sayılır.

## <a name="to-configure-a-wsfederationhttpbinding-in-code"></a>Kodda bir WSFederationHttpBinding yapılandırmak için

1. Öğesinin bir örneğini oluşturun <xref:System.ServiceModel.WSFederationHttpBinding>.

2. Özelliğini gereken şekilde veya<xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>gerektiği şekilde ayarlayın. <xref:System.ServiceModel.WSFederationHttpSecurityMode> <xref:System.ServiceModel.WSFederationHttpSecurity.Mode%2A> Dışında <xref:System.ServiceModel.Security.SecurityAlgorithmSuite.Basic256%2A> bir algoritma paketi gerekliyse, <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.AlgorithmSuite%2A> özelliğini öğesinden <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>alınan bir değere ayarlayın.

3. <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> Özelliği uygun şekilde ayarlayın.

4. Özelliğini veya <xref:System.IdentityModel.Tokens.SecurityKeyType> olarak`SymmetricKey` ayarlayın. <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A>`AsymmetricKey` gerektiği gibi.

5. <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> Özelliği uygun değere ayarlayın. Değer ayarlanmamışsa, WCF varsayılan olarak `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`, SAML 1,1 belirteçlerini gösterir.

6. Yerel veren belirtilmemişse istemcisinde gereklidir; hizmet üzerinde isteğe bağlı. Güvenlik belirteci <xref:System.ServiceModel.EndpointAddress> hizmetinin adresini ve kimlik bilgilerini içeren bir oluşturun ve <xref:System.ServiceModel.EndpointAddress> örneği <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> özelliğine atayın.

7. Yerel veren belirtilmemişse istemcisinde gereklidir; hizmette kullanılmıyor. İçin bir <xref:System.ServiceModel.Channels.Binding> <xref:System.ServiceModel.Channels.Binding> oluşturun<xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> ve örneği özelliğine atayın. `SecurityTokenService`

8. İstemcide kullanılmıyor; hizmet üzerinde isteğe bağlı. Güvenlik belirteci <xref:System.ServiceModel.EndpointAddress> hizmetinin meta verileri için bir örnek oluşturun ve bunu `IssuerMetadataAddress` özelliğine atayın.

9. Hem istemcide hem de hizmette isteğe bağlıdır. Özelliği tarafından döndürülen koleksiyona bir veya <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement> daha fazla örnek oluşturun ve ekleyin. <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>

10. Hem istemcide hem de hizmette isteğe bağlıdır. Özelliği tarafından döndürülen koleksiyona bir veya <xref:System.Xml.XmlElement> daha fazla örnek oluşturun ve ekleyin. <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>

## <a name="to-create-a-federated-endpoint-in-configuration"></a>Yapılandırmada bir Federasyon uç noktası oluşturmak için

1. Uygulama yapılandırma [dosyasındaki \<Bindings >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) öğesinin alt öğesi olarak bir [ \<WSFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) oluşturun.

2. WSFederationHttpBinding > alt öğesi `name`olarakbir [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesi oluşturun ve özniteliği uygun bir değere ayarlayın. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)

3. Bağlama > `<security>` öğesinin alt [öğesi olarak bir öğe oluşturun. \<](../../../../docs/framework/misc/binding.md)

4. Öğesinde özniteliğini, gereken şekilde`TransportWithMessageCredential`veyadeğerineayarlayın. `Message` `mode` `<security>`

5. Öğesinin alt `<message>` `<security>` öğesi olarak bir öğe oluşturun.

6. İsteğe bağlı. Öğesi için`<message>` uygun bir değer içeren özniteliğiniayarlayın.`algorithmSuite` Varsayılan, `Basic256` değeridir.

7. İsteğe bağlı. Asimetrik bir kanıt anahtarı gerekliyse, `issuedKeyType` `<message>` öğesinin özniteliğini olarak `AsymmetricKey`ayarlayın. Varsayılan, `SymmetricKey` değeridir.

8. İsteğe bağlı. `<message>` Öğesinde `issuedTokenType` özniteliğini ayarlayın.

9. Yerel veren belirtilmemişse istemcisinde gereklidir; hizmet üzerinde isteğe bağlı. Öğesinin alt `<issuer>` `<message>` öğesi olarak bir öğesi oluşturun.

10. `address` Özniteliğini`<issuer>` öğesine ayarlayın ve güvenlik belirteci hizmetinin belirteç isteklerini kabul ettiği adresi belirtin.

11. İsteğe bağlı. Bir `<identity>` alt öğe ekleyin ve güvenlik belirteci hizmetinin kimliğini belirtin

12. Daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](service-identity-and-authentication.md).

13. Yerel veren belirtilmemişse istemcisinde gereklidir; hizmette kullanılmıyor. Güvenlik belirteci hizmeti ile iletişim kurmak için kullanılabilen bağlamalar bölümünde [ bağlama>öğesioluşturun.\<](../../../../docs/framework/misc/binding.md) Bağlama oluşturma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Yapılandırmada](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)bir hizmet bağlaması belirtin.

14. `binding` Öğesinin ve`bindingConfiguration` özniteliklerini ayarlayarak, önceki adımda oluşturulan bağlamayı belirtin. `<issuer>`

15. İstemcide kullanılmıyor; hizmet üzerinde isteğe bağlı. `<issuerMetadata>` <`message`> Öğesinin alt öğesi olarak bir öğe oluşturun. Ardından, `<issuerMetadata>` öğesindeki bir `address` özniteliğinde, güvenlik belirteci hizmetinin meta verilerini yayımlayacağınız adresi belirtin. İsteğe bağlı olarak, `<identity>` bir alt öğe ekleyin ve güvenlik belirteci hizmetinin kimliğini belirtin.

16. Hem istemcide hem de hizmette isteğe bağlıdır. Öğesinin alt `<claimTypeRequirements>` `<message>` öğesi olarak bir öğesi ekleyin. `<claimTypeRequirements>` Öğeye [ \<Add >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md) öğeleri ekleyerek`claimType` ve talep türünü özniteliğiyle belirterek hizmetin bağımlı olduğu zorunlu ve isteğe bağlı talepler belirtin. `isOptional` Özniteliği ayarlayarak belirli bir talebin gerekli veya isteğe bağlı olup olmadığını belirtin.

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, bir `WSFederationHttpBinding` imperatively ayarlamaya yönelik kodu gösterir.

[!code-csharp[c_FederationBinding#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_federationbinding/cs/source.cs#2)]
[!code-vb[c_FederationBinding#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_federationbinding/vb/source.vb#2)]

## <a name="see-also"></a>Ayrıca bkz.

- [Federasyon](federation.md)
- [Federasyon Örneği](../../../../docs/framework/wcf/samples/federation-sample.md)
- [Nasıl yapılır: Bir WSFederationHttpBinding üzerindeki güvenli oturumları devre dışı bırakma](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
