---
title: 'Nasıl yapılır: Güvenlik Belirteci Hizmeti Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 98e82101-4cff-4bb8-a220-f7abed3556e5
ms.openlocfilehash: 5926216135429d235593aaf77ee0d29b0bacd8fa
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50036508"
---
# <a name="how-to-create-a-security-token-service"></a>Nasıl yapılır: Güvenlik Belirteci Hizmeti Oluşturma
Güvenlik belirteci hizmeti WS-Trust belirtiminde tanımlanan Protokolü uygular. Bu protokol, ileti biçimleri ve ileti verme, yenileme, iptal etme ve doğrulama güvenlik belirteçleri için exchange desenleri tanımlar. Belirli bir güvenlik belirteci hizmeti bir veya daha fazla bu yetenekleri sağlar. Bu konuda en sık karşılaşılan bir senaryodur arar: uygulama belirteci verme.  
  
## <a name="issuing-tokens"></a>Belirteç  
 WS-Trust tanımlar göre ileti formatları `RequestSecurityToken` XML Şeması Tanım Dili (XSD) şema öğesi ve `RequestSecurityTokenResponse` belirteç yayınında gerçekleştirmek için XSD şema öğesi. Ayrıca, ilişkili eylem Tekdüzen Kaynak Tanımlayıcıları (URI'lar) tanımlar. URI ile ilişkili eylem `RequestSecurityToken` ileti `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue`. URI ile ilişkili eylem `RequestSecurityTokenResponse` ileti `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue`.  
  
### <a name="request-message-structure"></a>İstek iletisi yapısı  
 Sorun istek iletisi yapısı genellikle şu öğelerden oluşur:  
  
-   Bir istek türü URI değeri olan `http://schemas.xmlsoap.org/ws/2005/02/trust/Issue`.
  
-   Belirteç türü URI. Güvenlik onaylama işaretleme dili (SAML) 1.1 belirteçler için bu URI değeri `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`.  
  
-   Verilen belirteçle ilişkili olmasını anahtarında bit sayısını belirten bir anahtar boyutu değer.  
  
-   Anahtar türü URI. Simetrik anahtarlar için bu URI değeri `http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey`.  
  
 Ayrıca, diğer öğeleri birkaç mevcut olabilir:  
  
-   İstemci tarafından sağlanan anahtar malzemesi.  
  
-   Verilen belirteç kullanılacak hedef hizmeti gösteren kapsam bilgileri.  
  
 Güvenlik belirteci hizmeti bilgileri sorunu istek iletisinde kullanır sorunu yanıt iletisi oluşturur.  
  
## <a name="response-message-structure"></a>Yanıt iletisi yapısı  
 Sorunu yanıt iletisi yapısı genellikle şu öğelerden oluşur;  
  
-   Verilen güvenlik belirteci, örneğin, bir SAML 1.1 onayı.  
  
-   Güvenlik belirteciyle ilişkili düzeltme belirteci. Simetrik anahtarlar için bu genellikle bir şifrelenmiş anahtar malzemesi biçimidir.  
  
-   Verilen güvenlik belirteci başvurular. Genellikle, güvenlik belirteci hizmeti verilen belirteç, belirtecin sonraki iletilerinde mevcut olmadığında kullanılabilir istemci ve başka tarafından gönderilen bir sonraki ileti görüntülendiğinde, kullanılabilecek bir başvuru döndürür.  
  
 Ayrıca, diğer öğeleri birkaç mevcut olabilir:  
  
-   Güvenlik belirteci hizmeti tarafından sağlanan anahtar malzemesi.  
  
-   Paylaşılan anahtar hesaplamak için gereken algoritma.  
  
-   Verilen belirteç ömrü çalıştırın.  
  
## <a name="processing-request-messages"></a>İstek iletilerini işleme  
 Güvenlik belirteci hizmeti, istek iletisinin çeşitli parçaları inceleme ve istek karşılayan bir belirteci verebilir sağlayarak sorunu isteği işler. Verilmesi için belirteci oluşturur önce güvenlik belirteci hizmeti aşağıdakileri belirlemelisiniz:  
  
-   İstek verilmesi için bir belirteç için gerçekten bir istektir.  
  
-   Güvenlik belirteci hizmeti istenen belirteç türünü destekler.  
  
-   İstek sahibinin istekte bulunma yetkisine sahiptir.  
  
-   Güvenlik belirteci hizmeti sahibinin beklentilerini anahtar malzemesi ile ilgili.  
  
 Bir belirteç oluşturmak, iki önemli parçaları, belirteç imzalamak için hangi anahtar ve paylaşılan anahtar ile şifreleme için hangi anahtarı tanımlamış olursunuz. Belirteç, böylece istemci, hizmeti belirleyebilirsiniz hedef hizmet için belirteç gösterdiğinde belirteç güvendiği bir güvenlik belirteci hizmeti tarafından verilmiş imzalanması gerekir. Anahtar malzemesi hedef hizmeti, anahtar malzemesi şifresini çözebilir yolla şifrelenmiş gerekir.  
  
 SAML onaylama işlemi imzalama oluşturmanız gerekir bir <xref:System.IdentityModel.Tokens.SigningCredentials> örneği. Bu sınıf için oluşturucu aşağıdakileri yapar:  
  
-   A <xref:System.IdentityModel.Tokens.SecurityKey> SAML onaylaması imzalamak için kullanılacak anahtarı.  
  
-   Kullanılacak imza algoritmasını tanımlayan bir dize.  
  
-   Kullanmak için bir Özet algoritması tanımlayan bir dize.  
  
-   İsteğe bağlı olarak, bir <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> onaylama imzalamak için kullanılacak anahtarı tanımlar.  
  
 [!code-csharp[c_CreateSTS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#1)]
 [!code-vb[c_CreateSTS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#1)]  
  
 Paylaşılan anahtar şifreleme anahtar malzemesi çıkarır ve hedef hizmet paylaşılan anahtarın şifresini çözmek için kullanabileceğiniz bir anahtarla şifreleme içerir. Genellikle hedef hizmetin ortak anahtarı kullanılır.  
  
 [!code-csharp[c_CreateSTS#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#2)]
 [!code-vb[c_CreateSTS#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#2)]  
  
 Ayrıca, bir <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> için şifrelenmiş anahtarı gereklidir.  
  
 [!code-csharp[c_CreateSTS#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#3)]
 [!code-vb[c_CreateSTS#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#3)]  
  
 Bu <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> ardından oluşturmak için kullanılan bir `SamlSubject` parçası olarak `SamlToken`.  
  
 [!code-csharp[c_CreateSTS#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#4)]
 [!code-vb[c_CreateSTS#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#4)]  
  
 Daha fazla bilgi için [Federasyon örneği](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
## <a name="creating-response-messages"></a>Yanıt iletilerini oluşturma  
 Güvenlik belirteci hizmeti sorunu isteği işler ve düzeltme anahtarıyla birlikte verilmesi için belirteci oluşturur sonra yanıt iletisi oluşturulması, en az istenen belirteci, düzeltme belirteci ve verilen belirteç başvuruları dahil olmak üzere gerekir. Verilen belirteç genellikle bir <xref:System.IdentityModel.Tokens.SamlSecurityToken> oluşturulan <xref:System.IdentityModel.Tokens.SamlAssertion>, aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-csharp[c_CreateSTS#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#5)]
 [!code-vb[c_CreateSTS#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#5)]  
  
 Burada güvenlik belirteci hizmeti sağlayan bir paylaşılan anahtar malzemesi durumda düzeltme belirteci oluşturarak oluşturulan bir <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>.  
  
 [!code-csharp[c_CreateSTS#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#6)]
 [!code-vb[c_CreateSTS#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#6)]  
  
 Paylaşılan anahtar için anahtar malzemesi istemci hem de güvenlik belirteci hizmeti sağladığınızda, düzeltme belirteci oluşturmak nasıl hakkında daha fazla bilgi için bkz. [Federasyon örneği](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
 Verilen belirteç başvuruları örneklerini oluşturarak oluşturulur <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> sınıfı.  
  
 [!code-csharp[c_CreateSTS#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#7)]
 [!code-vb[c_CreateSTS#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#7)]  
  
 Bu çeşitli değerleri, ardından istemciye döndürülen yanıt iletisine serileştirilir.  
  
## <a name="example"></a>Örnek  
 Güvenlik belirteci hizmeti için tam kod için bkz: [Federasyon örneği](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IdentityModel.Tokens.SigningCredentials>  
 <xref:System.IdentityModel.Tokens.SecurityKey>  
 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
 <xref:System.IdentityModel.Tokens.SamlAssertion>  
 <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>  
 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause>  
 [Federasyon Örneği](../../../../docs/framework/wcf/samples/federation-sample.md)
