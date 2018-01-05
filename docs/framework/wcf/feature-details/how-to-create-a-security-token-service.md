---
title: "Nasıl yapılır: Güvenlik Belirteci Hizmeti Oluşturma"
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
ms.assetid: 98e82101-4cff-4bb8-a220-f7abed3556e5
caps.latest.revision: "12"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 53ae64af0612cb905a2342491761b1e27ef19c06
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-security-token-service"></a>Nasıl yapılır: Güvenlik Belirteci Hizmeti Oluşturma
Bir güvenlik belirteci hizmeti WS-Trust belirtimine tanımlanan protokolünü uygular. Bu protokol, ileti biçimleri ve verme, yenileme, iptal etme ve doğrulama güvenlik belirteçleri için ileti exchange desenleri tanımlar. Verilen güvenlik belirteci hizmeti bir veya daha fazla bu yetenekleri sağlar. Bu konuda en yaygın bir senaryo arar: belirteci verme uygulama.  
  
## <a name="issuing-tokens"></a>Belirteç  
 WS-Trust tanımlayan temel ileti formatları `RequestSecurityToken` XML Şeması Tanım Dili (XSD) şema öğesi ve `RequestSecurityTokenResponse` belirteci verme gerçekleştirmek için XSD şema öğesi. Ayrıca, ilişkili eylem Tekdüzen Kaynak Tanımlayıcıları (URI'ler) tanımlar. URI ile ilişkili eylem `RequestSecurityToken` iletisidir http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue. URI ile ilişkili eylem `RequestSecurityTokenResponse` iletisidir http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue.  
  
### <a name="request-message-structure"></a>İstek iletisi yapısı  
 Sorunu istek iletisi yapısı genellikle aşağıdaki öğelerden oluşur:  
  
-   Bir talep türü URI değeri http://schemas.xmlsoap.org/ws/2005/02/trust/Issue.  
  
-   Belirteç türü URI. Güvenlik onaylar biçimlendirme dili (SAML) 1.1 belirteçler için bu URI http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1 değeri.  
  
-   Verilen belirteciyle ilişkilendirilmesi anahtarındaki bit sayısını gösteren bir anahtar boyutu değeri.  
  
-   Anahtar türü URI. Simetrik anahtarlar için http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey bu URI değeri.  
  
 Ayrıca, diğer öğeleri birkaç mevcut olabilir:  
  
-   İstemci tarafından sağlanan anahtar malzemesi.  
  
-   Verilen belirteç kullanılacak hedef hizmete gösterir kapsam bilgileri.  
  
 Sorun yanıt iletisi yapılandırdığında güvenlik belirteci hizmeti sorunu istek iletisinde bilgileri kullanır.  
  
## <a name="response-message-structure"></a>Yanıt iletisi yapısı  
 Sorun yanıt iletisi yapısı genellikle aşağıdaki öğelerden oluşur;  
  
-   Verilen güvenlik belirteci, örneğin, bir SAML 1.1 onaylama işlemi.  
  
-   Güvenlik belirteci ile ilişkili düzeltme belirteci. Simetrik anahtarlar için bu genellikle bir şifrelenmiş anahtar malzemesi biçimidir.  
  
-   Verilen güvenlik belirteci başvurular. Genellikle, güvenlik belirteci hizmeti verilen belirteç, belirtecin sonraki iletilerinde mevcut olmadığında kullanılabilir istemci ve başka tarafından gönderilen bir sonraki ileti görüntülendiğinde, kullanılabilecek bir başvuru döndürür.  
  
 Ayrıca, diğer öğeleri birkaç mevcut olabilir:  
  
-   Güvenlik belirteci hizmeti tarafından sağlanan anahtar malzemesi.  
  
-   Paylaşılan anahtar işlem için gereken algoritması.  
  
-   Verilen belirteç ömrü bilgileri.  
  
## <a name="processing-request-messages"></a>İstek iletilerini işleme  
 Güvenlik belirteci hizmeti, istek iletisi çeşitli parçaları incelenerek ve istek karşılayan bir belirteç verebilir sağlayarak sorunu isteğini işler. Güvenlik belirteci hizmeti verilmesi için belirteci oluşturur önce aşağıdaki belirlemeniz gerekir:  
  
-   Gerçekten verilmesi için bir belirteç isteği isteğidir.  
  
-   Güvenlik belirteci hizmeti istenen belirteç türü destekler.  
  
-   İstek sahibinin istekte yetkisine sahiptir.  
  
-   Güvenlik belirteci hizmeti anahtar malzemesi göre sahibinin beklentilerine uygun.  
  
 Bir belirteç oluşturmak, iki önemli parçaları, belirteç ile imzalamak için hangi anahtar ve paylaşılan anahtar ile şifrelemek için hangi anahtar tanımlamış olursunuz. Belirteç, böylece istemci hizmeti, belirleyebilir hedef hizmete belirtece gösterdiğinde belirtecin güvenilen bir güvenlik belirteci hizmeti tarafından verilmiş imzalanması gerekiyor. Hedef hizmet bu anahtar malzeme şifresini çözebilir şekilde şifrelenecek anahtar malzemesi gerekir.  
  
 SAML onayı imzalama içerir oluşturma bir <xref:System.IdentityModel.Tokens.SigningCredentials> örneği. Bu sınıf oluşturucusu aşağıdakileri yapar:  
  
-   A <xref:System.IdentityModel.Tokens.SecurityKey> SAML onayı imzalamak için kullanılacak anahtar.  
  
-   Kullanmak için imza algoritması tanımlayan bir dize.  
  
-   Kullanmak için Özet algoritması tanımlayan bir dize.  
  
-   İsteğe bağlı olarak, bir <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> onaylama imzalamak için kullanılan anahtarı tanımlar.  
  
 [!code-csharp[c_CreateSTS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#1)]
 [!code-vb[c_CreateSTS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#1)]  
  
 Paylaşılan anahtar şifreleme anahtar malzemesi alma ve hedef hizmete paylaşılan anahtarın şifresini çözmek için kullanabileceğiniz bir anahtarla şifreleme içerir. Genellikle, hedef hizmeti ortak anahtarını kullanılır.  
  
 [!code-csharp[c_CreateSTS#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#2)]
 [!code-vb[c_CreateSTS#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#2)]  
  
 Ayrıca, bir <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> için şifrelenmiş anahtar gereklidir.  
  
 [!code-csharp[c_CreateSTS#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#3)]
 [!code-vb[c_CreateSTS#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#3)]  
  
 Bu <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> sonra oluşturmak için kullanılan bir `SamlSubject` parçası olarak `SamlToken`.  
  
 [!code-csharp[c_CreateSTS#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#4)]
 [!code-vb[c_CreateSTS#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#4)]  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Federasyon örnek](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
## <a name="creating-response-messages"></a>Yanıt iletilerini oluşturma  
 Güvenlik belirteci hizmeti sorunu isteği işler ve kanıt anahtarı ile birlikte verilen belirteç oluşturur sonra yanıt iletisi oluşturulması için en az istenen belirteci, düzeltme belirteci ve verilen belirteç başvuruları dahil olmak üzere gerekir. Verilen belirteç genellikle olan bir <xref:System.IdentityModel.Tokens.SamlSecurityToken> oluşturulan <xref:System.IdentityModel.Tokens.SamlAssertion>, aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-csharp[c_CreateSTS#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#5)]
 [!code-vb[c_CreateSTS#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#5)]  
  
 Nereye güvenlik belirteci hizmeti sağlayan paylaşılan anahtar malzemesi durumda düzeltme belirteci oluşturarak oluşturulan bir <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>.  
  
 [!code-csharp[c_CreateSTS#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#6)]
 [!code-vb[c_CreateSTS#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#6)]  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]İstemci ve güvenlik belirteci hem de hizmet verdiğinizde düzeltme belirteci oluşturmak nasıl paylaşılan anahtar için anahtar malzemesi sağlamak, bkz: [Federasyon örnek](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
 Verilen belirteç başvuruları örneklerini oluşturma tarafından oluşturulan <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> sınıfı.  
  
 [!code-csharp[c_CreateSTS#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#7)]
 [!code-vb[c_CreateSTS#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#7)]  
  
 Bu çeşitli değerleri, ardından istemciye döndürülen yanıt iletisine serileştirilir.  
  
## <a name="example"></a>Örnek  
 Bir güvenlik belirteci hizmeti için tam kodu için bkz: [Federasyon örnek](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IdentityModel.Tokens.SigningCredentials>  
 <xref:System.IdentityModel.Tokens.SecurityKey>  
 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
 <xref:System.IdentityModel.Tokens.SamlAssertion>  
 <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>  
 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause>  
 [Federasyon Örneği](../../../../docs/framework/wcf/samples/federation-sample.md)
