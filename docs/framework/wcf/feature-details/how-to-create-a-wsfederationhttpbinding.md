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
ms.openlocfilehash: 16b93126157ff129d5e0b815bc951873e7fa760d
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46525545"
---
# <a name="how-to-create-a-wsfederationhttpbinding"></a>Nasıl yapılır: WSFederationHttpBinding Oluşturma

Windows Communication Foundation (WCF) <xref:System.ServiceModel.WSFederationHttpBinding> sınıfı ([\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) yapılandırmasında) Federasyon Hizmeti açığa çıkarmak için bir mekanizma sağlar. Diğer bir deyişle, istemcilerin bir güvenlik belirteci hizmeti tarafından verilen bir güvenlik belirteci kullanarak kimlik doğrulaması gerektiren bir hizmet. Bu konu nasıl ayarlanacağını gösterir. bir <xref:System.ServiceModel.WSFederationHttpBinding> hem kod hem de yapılandırma. Bağlama oluşturulduktan sonra bu bağlama kullanılacak uç nokta ayarlamayı ayarlayabilirsiniz.

 Temel adımlar aşağıda ana hatlarıyla:

1. Güvenlik modu seçin. <xref:System.ServiceModel.WSFederationHttpBinding> Destekler `Message`, hatta birden fazla atlama arasında uçtan uca güvenlik ileti düzeyinde sağlar ve `TransportWithMessageCredential`, burada istemciyi ve hizmeti yapabilir doğrudan bir bağlantı üzerinden durumlarda daha iyi performans sağlar HTTPS.

    > [!NOTE]
    > <xref:System.ServiceModel.WSFederationHttpBinding> Da destekler `None` güvenlik modu olarak. Bu modu güvenli değildir ve hata ayıklama amacıyla yalnızca sağlanır. Hizmet uç noktası ile dağıtılırsa bir <xref:System.ServiceModel.WSFederationHttpBinding> ayarlamak kendi güvenlik moduyla `None`, sonuçta elde edilen istemci bağlama (tarafından oluşturulan [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)) olan bir <xref:System.ServiceModel.WSHttpBinding> ile bir güvenlik modu `None`.

     Diğer sistem tarafından sağlanan bağlamalar kullanırken bir istemci kimlik bilgileri türünü seçmek gerekli değildir `WSFederationHttpBinding`. İstemci kimlik bilgisi türü her zaman verilen bir belirteç olduğundan budur. WCF belirtilen verenden bir belirteç alır ve hizmete istemcinin kimliğini doğrulamak için bu belirteci sunar.

2. Federasyon istemcilerde ayarlamak <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> özelliğini güvenlik belirteci hizmeti URL'si. Ayarlama <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> güvenlik belirteci hizmeti ile iletişim kurmak için kullanılacak bağlama için.

3. İsteğe bağlı. Ayarlama <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> özelliği için Tekdüzen Kaynak Tanımlayıcısı (URI) simge türü. Federasyon Hizmetleri için hizmet bekliyor belirteç türü belirtin. Federasyon istemcilerde istemci isteklerini güvenlik belirteci Hizmeti'nden belirteç türü belirtin.

     Hiçbir belirteç türü belirtilirse, istemciler, bir belirteç türü URI WS-Trust istek güvenlik belirteçleri (RSTs) oluşturmak ve istemci kimlik doğrulaması varsayılan olarak güvenlik onaylama işaretleme dili (SAML) 1.1 belirteciyle Hizmetleri beklerler.

     SAML 1.1 belirteci için URI `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`.

4. İsteğe bağlı. Federasyon Hizmetleri üzerinde <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A> güvenlik belirteci hizmeti meta verileri URL'sine özelliği. Hizmet meta verileri yayımlama için yapılandırılmışsa, bir uygun bağlama/uç noktanın çifti seçmek, istemciler hizmeti meta veri uç noktası sağlar. Meta veri yayımlama hakkında daha fazla bilgi için bkz: [meta veri yayımlama](publishing-metadata.md).

 Verilen belirteç, istemci ile hizmet arasında kullanılacak algoritması paketi kavram anahtar olarak kullanılan anahtar türü gibi diğer özellikleri de ayarlayabilirsiniz anlaşma veya açıkça hizmeti kimlik bilgileri belirtmek için herhangi bir belirli hizmet talep olup olmadığını Verilen belirteç içeren ve güvenlik belirteci hizmeti için istemcinin gönderdiği isteğine eklenmesi gereken ek XML öğeleri bekliyor.

> [!NOTE]
>  `NegotiateServiceCredential` Özelliği, yalnızca uygun olduğunda `SecurityMode` ayarlanır `Message`. Varsa `SecurityMode` ayarlanır `TransportWithMessageCredential`, ardından `NegotiateServiceCredential` özelliği yok sayılır.

## <a name="to-configure-a-wsfederationhttpbinding-in-code"></a>WSFederationHttpBinding kodda yapılandırmak için

1. Bir örneğini oluşturmak <xref:System.ServiceModel.WSFederationHttpBinding>.

2. Ayarlama <xref:System.ServiceModel.WSFederationHttpSecurity.Mode%2A> özelliğini <xref:System.ServiceModel.WSFederationHttpSecurityMode> veya <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message> gerektiğinde. Bir algoritma paketini dışında <xref:System.ServiceModel.Security.SecurityAlgorithmSuite.Basic256%2A> gereklidir ayarlamak <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.AlgorithmSuite%2A> alındığı bir değere <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.

3. Ayarlama <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> uygun şekilde özelliği.

4. Ayarlama <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> özelliğini <xref:System.IdentityModel.Tokens.SecurityKeyType> `SymmetricKey` veya.`AsymmetricKey` gerektiğinde.

5. Ayarlama <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> özelliğini uygun değer. Herhangi bir değer ayarlarsanız, WCF varsayılan `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`, SAML 1.1 belirteçlerini gösterir.

6. Hiçbir yerel yayımlayan belirtilirse istemcide gerekli; İsteğe bağlı hizmeti. Oluşturma bir <xref:System.ServiceModel.EndpointAddress> güvenlik belirteci hizmeti ve ata adresini ve kimlik bilgilerini içeren <xref:System.ServiceModel.EndpointAddress> için örnek <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> özelliği.

7. Hiçbir yerel yayımlayan belirtilirse istemcide gerekli; hizmette kullanılmaz. Oluşturma bir <xref:System.ServiceModel.Channels.Binding> için `SecurityTokenService` ve atama <xref:System.ServiceModel.Channels.Binding> için örnek <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> özelliği.

8. İstemcide kullanılmaz; İsteğe bağlı hizmeti. Oluşturma bir <xref:System.ServiceModel.EndpointAddress> atayın ve örnek güvenlik belirteci hizmeti meta veriler için `IssuerMetadataAddress` özelliği.

9. Hem istemci hem de hizmet isteğe bağlı. Oluşturma ve bir veya daha fazla ekleme <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement> tarafından döndürülen bir koleksiyonda örneklerine <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A> özelliği.

10. Hem istemci hem de hizmet isteğe bağlı. Oluşturma ve bir veya daha fazla ekleme <xref:System.Xml.XmlElement> tarafından döndürülen bir koleksiyonda örneklerine <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A> özelliği.

## <a name="to-create-a-federated-endpoint-in-configuration"></a>Yapılandırmada bir Federasyon uç noktası oluşturmak için

1. Oluşturma bir [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) bir alt öğesi olarak [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) uygulama yapılandırma dosyasında öğesi.

2. Oluşturma bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesi alt öğesi olarak [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ayarlayıp `name` özniteliği için uygun bir değer.

3. Oluşturma bir `<security>` öğesi alt öğesi olarak [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesi.

4. Ayarlama `mode` özniteliği `<security>` öğe değerini `Message` veya `TransportWithMessageCredential`gerektirdiği gibi.

5. Oluşturma bir `<message>` öğesi alt öğesi olarak `<security>` öğesi.

6. İsteğe bağlı. Ayarlama `algorithmSuite` özniteliği `<message>` uygun bir değere sahip öğe. Varsayılan, `Basic256` değeridir.

7. İsteğe bağlı. Asimetrik sağlama anahtar gerekli değilse, `issuedKeyType` özniteliği `<message>` öğesine `AsymmetricKey`. Varsayılan, `SymmetricKey` değeridir.

8. İsteğe bağlı. Ayarlama `issuedTokenType` özniteliği `<message>` öğesi.

9. Hiçbir yerel yayımlayan belirtilirse istemcide gerekli; İsteğe bağlı hizmeti. Oluşturma bir `<issuer>` öğesi alt öğesi olarak `<message>` öğesi.

10. Ayarlama `address` özniteliğini `<issuer>` öğesi ve güvenlik belirteci hizmeti belirteci isteklerini kabul adresini belirtin.

11. İsteğe bağlı. Ekleme bir `<identity>` alt öğesi ve güvenlik belirteci hizmeti kimliğini belirtin

12. Daha fazla bilgi için [kimlik doğrulama ile hizmet kimliği](service-identity-and-authentication.md).

13. Hiçbir yerel yayımlayan belirtilirse istemcide gerekli; hizmette kullanılmaz. Oluşturma bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesinde bir güvenlik belirteci hizmeti ile iletişim kurmak için kullanılan bağlamalar bölümü. Bir bağlama oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: yapılandırmada hizmet bağlaması belirtme](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).

14. Ayarlayarak önceki adımda oluşturduğunuz bağlama belirtme `binding` ve `bindingConfiguration` özniteliklerini `<issuer>` öğesi.

15. İstemcide kullanılmaz; İsteğe bağlı hizmeti. Oluşturma bir `<issuerMetadata>` öğesi alt öğesi olarak <`message`> öğesi. Ardından bir `address` özniteliği `<issuerMetadata>` öğesi, hangi güvenlik belirteci hizmeti meta verilerini yayımlamak için adresini belirtin. İsteğe bağlı olarak, ekleme bir `<identity>` alt öğesi ve güvenlik belirteci hizmeti kimliğini belirtin.

16. Hem istemci hem de hizmet isteğe bağlı. Ekleme bir `<claimTypeRequirements>` öğesi alt öğesi olarak `<message>` öğesi. Gerekli ve isteğe bağlı talepleri belirtmek ekleyerek hizmet dayanan [ \<Ekle >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md) öğelerine `<claimTypeRequirements>` öğesi ve talep belirtme türünü `claimType` özniteliği. Belirli bir talep ayarlayarak gerekli veya isteğe bağlı olup olmadığını belirtin `isOptional` özniteliği.

## <a name="example"></a>Örnek

Aşağıdaki kod örneği ayarlamak için kod gösterir bir `WSFederationHttpBinding` kesin.

[!code-csharp[c_FederationBinding#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_federationbinding/cs/source.cs#2)]
[!code-vb[c_FederationBinding#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_federationbinding/vb/source.vb#2)]

## <a name="see-also"></a>Ayrıca bkz.

- [Federasyon](federation.md)
- [Federasyon Örneği](../../../../docs/framework/wcf/samples/federation-sample.md)
- [Nasıl yapılır: WSFederationHttpBinding Güvenli Oturumlarını Devre Dışı Bırakma](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)