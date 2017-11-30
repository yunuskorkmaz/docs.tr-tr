---
title: "Nasıl yapılır: WSFederationHttpBinding Oluşturma"
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
ms.assetid: e54897d7-aa6c-46ec-a278-b2430c8c2e10
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3314519e89a78f188d78a5e5af641d7c87ee1c46
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-wsfederationhttpbinding"></a>Nasıl yapılır: WSFederationHttpBinding Oluşturma
İçinde [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], <xref:System.ServiceModel.WSFederationHttpBinding> sınıfı ([\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) yapılandırmasında) Federasyon Hizmeti gösterme için bir mekanizma sağlar. Diğer bir deyişle, istemcilerin bir güvenlik belirteci hizmeti tarafından verilen bir güvenlik belirteci kullanarak kimlik doğrulaması gerektiren bir hizmeti. Bu konu nasıl ayarlanacağını gösterir bir <xref:System.ServiceModel.WSFederationHttpBinding> kod ve yapılandırma. Bağlama oluşturulduktan sonra bu bağlamayı kullanmak için uç nokta ayarlamayı ayarlayabilirsiniz.  
  
 Temel adımlar aşağıda belirtilen:  
  
1.  Güvenlik modu seçin. <xref:System.ServiceModel.WSFederationHttpBinding> Destekleyen `Message`, hatta birden çok atlama arasında uçtan uca güvenlik ileti düzeyinde sağlar ve `TransportWithMessageCredential`, burada istemci ve hizmet yapabilir doğrudan bir bağlantı üzerinden durumlarda daha iyi performans sağlar HTTPS.  
  
    > [!NOTE]
    >  <xref:System.ServiceModel.WSFederationHttpBinding> De destekler `None` güvenlik modu. Bu mod, güvenli olmayan ve hata ayıklama amacıyla yalnızca sağlanır. Hizmet uç noktası ile dağıtılırsa bir <xref:System.ServiceModel.WSFederationHttpBinding> ayarlamak, güvenlik modu ile `None`, bağlama elde edilen istemci (tarafından oluşturulan [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)) olan bir <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> bir güvenlik modu ile `None`.  
  
     Diğer sistem tarafından sağlanan bağlamalar kullanırken bir istemci kimlik bilgisi türü seçmek ise gerekli değildir `WSFederationHttpBinding`. İstemci kimlik bilgisi türü her zaman verilen bir belirteç olmasıdır. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Belirtilen vereni uygulamasından bir belirteç alır ve istemci kimlik doğrulaması için hizmet belirtecini gösterir.  
  
2.  Federasyon istemcilerde ayarlamak <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> güvenlik belirteci hizmeti URL'sini özelliği. Ayarlama <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> güvenlik belirteci hizmeti ile iletişim kurmak için kullanılacak bağlama için.  
  
3.  İsteğe bağlı. Ayarlama <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> özelliği için Tekdüzen Kaynak Tanımlayıcısı (URI) bir simge türü. Federasyon hizmet, hizmet bekliyor belirteç türü belirtin. Federasyon istemcilerde güvenlik belirteci hizmeti gelen istemci isteklerini belirteç türü belirtin.  
  
     Belirteç tür belirtilmedi, istemciler bir belirteç olmadan türü URI WS-Trust isteği güvenlik belirteçleri (RSTs) oluşturmak ve istemci kimlik doğrulaması varsayılan olarak bir güvenlik onaylar biçimlendirme dili (SAML) 1.1 belirteci kullanarak Hizmetleri beklediğiniz.  
  
     SAML 1.1 belirteç URI'sini "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" dir.  
  
4.  İsteğe bağlı. Federasyon hizmetlerinde ayarlamak <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A> bir güvenlik belirteci hizmeti meta veri URL'sini özelliği. Hizmet meta veri yayımlama için yapılandırılmışsa, uygun bağlama/uç noktanın çifti seçmek istemcilerin hizmetinin meta veri uç noktası sağlar. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]bkz: meta verileri yayımlama [meta veri yayımlama](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
 Verilen belirteç, istemci ile hizmet arasında kullanılacak algoritma paketini kanıtını bir anahtar olarak kullanılan anahtar türü de dahil olmak üzere diğer özellikleri de ayarlayabilirsiniz anlaşma veya hizmet kimlik bilgilerini açıkça belirtmek için herhangi bir özel hizmet talepleri olup olmadığını Verilen belirteç içeren ve güvenlik belirteci hizmeti istemci gönderir isteğine eklenmesi gereken ek XML öğeleri bekliyor.  
  
> [!NOTE]
>  `NegotiateServiceCredential` Özelliği, yalnızca ilgili ne zaman `SecurityMode` ayarlanır `Message`. Varsa `SecurityMode` ayarlanır `TransportWithMessageCredential`, sonra `NegotiateServiceCredential` özelliği yoksayılır.  
  
### <a name="to-configure-a-wsfederationhttpbinding-in-code"></a>Kodda bir WSFederationHttpBinding yapılandırmak için  
  
1.  Bir örneğini oluşturmak <xref:System.ServiceModel.WSFederationHttpBinding>.  
  
2.  Ayarlama <xref:System.ServiceModel.WSFederationHttpSecurity.Mode%2A> özelliğine <xref:System.ServiceModel.WSFederationHttpSecurityMode> veya <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message> gerektiği gibi. Dışında bir algoritma paketini varsa <xref:System.ServiceModel.Security.SecurityAlgorithmSuite.Basic256%2A> gereklidir ayarlamak <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.AlgorithmSuite%2A> alınan bir değer özelliğine <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.  
  
3.  Ayarlama <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> uygun şekilde özelliği.  
  
4.  Ayarlama <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> özelliğine <xref:System.IdentityModel.Tokens.SecurityKeyType> `SymmetricKey` veya.`AsymmetricKey` gerektiği şekilde.  
  
5.  Ayarlama <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> uygun değere özelliği. Herhangi bir değer ayarlarsanız, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] SAML 1.1 belirteçleri gösteren varsayılanlara "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1".  
  
6.  Hiçbir yerel yayımlayan belirtilmişse, istemcide gerekli; hizmet üzerinde isteğe bağlı. Oluşturma bir <xref:System.ServiceModel.EndpointAddress> güvenlik belirteci hizmeti ve ata adresi ve kimlik bilgilerini içeren <xref:System.ServiceModel.EndpointAddress> için örnek <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> özelliği.  
  
7.  Hiçbir yerel yayımlayan belirtilmişse, istemcide gerekli; hizmette kullanılmaz. Oluşturma bir <xref:System.ServiceModel.Channels.Binding> için `SecurityTokenService` ve Ata <xref:System.ServiceModel.Channels.Binding> için örnek <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> özelliği.  
  
8.  İstemcide kullanılmaz; hizmet üzerinde isteğe bağlı. Oluşturma bir <xref:System.ServiceModel.EndpointAddress> örneği güvenlik belirteci hizmeti meta verileri için ve atayın `IssuerMetadataAddress` özelliği.  
  
9. Hem istemci hem de hizmet isteğe bağlı. Oluşturma ve bir veya daha fazla ekleme <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement> tarafından döndürülen koleksiyon örneklerine <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A> özelliği.  
  
10. Hem istemci hem de hizmet isteğe bağlı. Oluşturma ve bir veya daha fazla ekleme <xref:System.Xml.XmlElement> tarafından döndürülen koleksiyon örneklerine <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A> özelliği.  
  
### <a name="to-create-a-federated-endpoint-in-configuration"></a>Federe bir uç nokta yapılandırması oluşturmak için  
  
1.  Oluşturma bir [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) bir alt öğesi olarak [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) uygulama yapılandırma dosyasında öğesi.  
  
2.  Oluşturma bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesi bir alt öğesi olarak [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ve `name` öznitelik için uygun bir değer.  
  
3.  Oluşturma bir `<security>` öğesi bir alt öğesi olarak [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesi.  
  
4.  Ayarlama `mode` özniteliği `<security>` değerini öğesine `Message` veya `TransportWithMessageCredential`, gerektiği gibi.  
  
5.  Oluşturma bir `<message>` öğesi bir alt öğesi olarak `<security>` öğesi.  
  
6.  İsteğe bağlı. Ayarlama `algorithmSuite` özniteliği `<message>` uygun bir değere sahip öğe. Varsayılan, `Basic256` değeridir.  
  
7.  İsteğe bağlı. Asimetrik kanıt anahtarı gerekli ise `issuedKeyType` özniteliği `<message>` öğesine `AsymmetricKey`. Varsayılan, `SymmetricKey` değeridir.  
  
8.  İsteğe bağlı. Ayarlama `issuedTokenType` özniteliği `<message>` öğesi.  
  
9. Hiçbir yerel yayımlayan belirtilmişse, istemcide gerekli; hizmet üzerinde isteğe bağlı. Oluşturma bir `<issuer>` öğesi bir alt öğesi olarak `<message>` öğesi.  
  
10. Ayarlama `address` özniteliğini `<issuer>` öğesi ve güvenlik belirteci hizmeti belirteç isteklerini kabul adresi belirtin.  
  
11. İsteğe bağlı. Ekleme bir `<identity>` alt öğesi ve güvenlik belirteci hizmeti kimliğini belirtin  
  
12. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Hizmet kimlik ve kimlik doğrulama](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
13. Hiçbir yerel yayımlayan belirtilmişse, istemcide gerekli; hizmette kullanılmaz. Oluşturma bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) güvenlik belirteci hizmeti ile iletişim kurmak için kullanılan bağlamaları bölümünde öğesi. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]bir bağlama bkz [nasıl yapılır: yapılandırmada hizmet bağlama belirtme](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
14. Ayarlayarak önceki adımda oluşturduğunuz bağlama belirtme `binding` ve `bindingConfiguration` özniteliklerini `<issuer>` öğesi.  
  
15. İstemcide kullanılmaz; hizmet üzerinde isteğe bağlı. Oluşturma bir `<issuerMetadata>` öğesi bir alt öğesi olarak <`message`> öğesi. Ardından bir `address` özniteliği `<issuerMetadata>` öğesi, güvenlik belirteci hizmeti olduğu meta verilerini yayımlamak için adresini belirtin. İsteğe bağlı olarak ekleyin bir `<identity>` alt öğesi ve güvenlik belirteci hizmeti kimliğini belirtin.  
  
16. Hem istemci hem de hizmet isteğe bağlı. Ekleme bir `<claimTypeRequirements>` öğesi bir alt öğesi olarak `<message>` öğesi. Gerekli ve isteğe bağlı talepleri belirtmek ekleyerek hizmet dayanan [ \<Ekle >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md) öğelerine `<claimTypeRequirements>` öğesi ve talep belirterek türünü `claimType` özniteliği. Belirli bir talep ayarlayarak gerekli veya isteğe bağlı olup olmadığını belirtin `isOptional` özniteliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği ayarlamak için kod gösterir bir `WSFederationHttpBinding` imperatively.  
  
 [!code-csharp[c_FederationBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federationbinding/cs/source.cs#2)] 
 [!code-vb[c_FederationBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federationbinding/vb/source.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Federasyon](../../../../docs/framework/wcf/feature-details/federation.md)  
 [Federasyon örneği](../../../../docs/framework/wcf/samples/federation-sample.md)  
 [Nasıl yapılır: Güvenli WSFederationHttpBinding gücenli oturumlarını devre dışı bırak](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
