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
ms.openlocfilehash: 1cfcca524e5dd2b0c1560eb7600795766e2db1d6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598963"
---
# <a name="how-to-create-a-security-token-service"></a>Nasıl yapılır: Güvenlik Belirteci Hizmeti Oluşturma
Bir güvenlik belirteci hizmeti, WS-Trust belirtiminde tanımlanan protokolü uygular. Bu protokol, güvenlik belirteçlerini verme, yenileme, iptal etme ve doğrulama için İleti biçimlerini ve ileti değişim düzenlerini tanımlar. Verilen bir güvenlik belirteci hizmeti bu yeteneklerden bir veya daha fazlasını sağlar. Bu konu, en yaygın senaryoya bakar: belirteç verme uygulama.  
  
## <a name="issuing-tokens"></a>Belirteçleri verme  
 WS-Trust, `RequestSecurityToken` XML şeması tanım dili (xsd) şema öğesine ve `RequestSecurityTokenResponse` belirteç verme işlemini gerçekleştirmek için xsd şema öğesine göre İleti biçimlerini tanımlar. Ayrıca, ilişkili eylem Tekdüzen Kaynak tanımlayıcılarını (URI) tanımlar. İletiyle ilişkili eylem URI 'si `RequestSecurityToken` `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue` . İletiyle ilişkili eylem URI 'si `RequestSecurityTokenResponse` `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue` .  
  
### <a name="request-message-structure"></a>Ileti yapısı iste  
 Sorun isteği ileti yapısı, genellikle aşağıdaki öğelerden oluşur:  
  
- Değerine sahip bir istek türü URI 'SI `http://schemas.xmlsoap.org/ws/2005/02/trust/Issue` .
  
- Belirteç türü URI 'SI. Güvenlik onaylama işlemi biçimlendirme dili (SAML) 1,1 belirteçleri için, bu URI 'nin değeri `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1` .  
  
- Verilen belirteçle ilişkilendirilecek anahtardaki bit sayısını gösteren bir anahtar boyutu değeri.  
  
- Anahtar türü URI 'SI. Simetrik anahtarlar için bu URI 'nin değeri `http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey` .  
  
 Ayrıca, diğer birkaç öğe bulunabilir:  
  
- İstemci tarafından sunulan anahtar malzemeler.  
  
- Verilen belirtecin kullanacağı hedef hizmeti gösteren kapsam bilgileri.  
  
 Güvenlik belirteci hizmeti, sorun yanıt iletisini oluştururken sorun isteği iletisindeki bilgileri kullanır.  
  
## <a name="response-message-structure"></a>Yanıt Iletisi yapısı  
 Sorun yanıt iletisi yapısı, genellikle aşağıdaki öğelerden oluşur;  
  
- Verilen güvenlik belirteci, örneğin bir SAML 1,1 onayı.  
  
- Güvenlik belirteciyle ilişkili bir kanıt belirteci. Simetrik anahtarlar için bu genellikle önemli malzemenin şifreli bir biçimidir.  
  
- Verilen güvenlik belirtecine başvurular. Genellikle, güvenlik belirteci hizmeti, verilen belirteç istemci tarafından gönderilen sonraki bir iletide göründüğünde ve sonraki iletilerde belirteç mevcut olmadığında kullanılabilecek bir başvuru döndürür.  
  
 Ayrıca, diğer birkaç öğe bulunabilir:  
  
- Güvenlik belirteci hizmeti tarafından sunulan anahtar malzemeler.  
  
- Paylaşılan anahtarı hesaplamak için gereken algoritma.  
  
- Verilen belirtecin ömür bilgileri.  
  
## <a name="processing-request-messages"></a>Istek Iletilerini işleme  
 Güvenlik belirteci hizmeti, istek iletisinin çeşitli parçalarını inceleyerek ve isteği karşılayan bir belirteç yayımlayabilmesini sağlayarak sorun isteğini işler. Güvenlik belirteci hizmeti, verilecek belirteci oluşturmadan önce aşağıdakileri belirlemeli olmalıdır:  
  
- İstek aslında belirtecin verilme isteği olur.  
  
- Güvenlik belirteci hizmeti, istenen belirteç türünü destekler.  
  
- İstek sahibi isteği yapmak için yetkilendirildi.  
  
- Güvenlik belirteci hizmeti, önemli malzemelere göre isteyenin beklentilerini karşılayabilir.  
  
 Belirteç oluşturmak için gereken iki önemli bölüm, belirteci hangi anahtarın imzalandığını ve paylaşılan anahtarın hangi anahtarla şifreleneceğini belirler. İstemci belirteci hedef hizmete sunduğunda, bu hizmetin, belirtecin güvendiği bir güvenlik belirteci hizmeti tarafından verildiğini belirleyebilmesi için belirtecin imzalanması gerekir. Ana malzemenin, hedef hizmetin bu ana malzemenin şifresini çözebilmeleri için bu şekilde şifrelenmesi gerekir.  
  
 SAML onayını imzalamak bir örnek oluşturmayı içerir <xref:System.IdentityModel.Tokens.SigningCredentials> . Bu sınıf için Oluşturucu şunları alır:  
  
- <xref:System.IdentityModel.Tokens.SecurityKey>SAML onaylama işlemi imzalamak için kullanılacak anahtar için A.  
  
- Kullanılacak imza algoritmasını tanımlayan bir dize.  
  
- Kullanılacak özet algoritmasını tanımlayan bir dize.  
  
- İsteğe bağlı olarak, <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> onay imzalamak için kullanılacak anahtarı tanımlayan bir.  
  
 [!code-csharp[c_CreateSTS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#1)]
 [!code-vb[c_CreateSTS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#1)]  
  
 Paylaşılan anahtarı şifrelemek, anahtar malzemesini almayı ve hedef hizmetin paylaşılan anahtarın şifresini çözmek için kullanabileceği bir anahtarla şifrelemeyi içerir. Genellikle, hedef hizmetin ortak anahtarı kullanılır.  
  
 [!code-csharp[c_CreateSTS#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#2)]
 [!code-vb[c_CreateSTS#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#2)]  
  
 Buna ek olarak, <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> şifreli anahtar için bir de gereklidir.  
  
 [!code-csharp[c_CreateSTS#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#3)]
 [!code-vb[c_CreateSTS#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#3)]  
  
 Bu <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> daha sonra öğesinin bir parçası olarak oluşturmak için kullanılır `SamlSubject` `SamlToken` .  
  
 [!code-csharp[c_CreateSTS#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#4)]
 [!code-vb[c_CreateSTS#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#4)]  
  
 Daha fazla bilgi için bkz. [Federasyon örneği](../samples/federation-sample.md).  
  
## <a name="creating-response-messages"></a>Yanıt Iletileri oluşturma  
 Güvenlik belirteci hizmeti, sorun isteğini işlediğinde ve düzeltme anahtarıyla birlikte verilecek belirteci oluşturduktan sonra, en azından istenen belirteç, kanıt belirteci ve verilen belirteç başvuruları dahil olmak üzere yanıt iletisinin oluşturulması gerekir. Verilen belirteç genellikle <xref:System.IdentityModel.Tokens.SamlSecurityToken> , <xref:System.IdentityModel.Tokens.SamlAssertion> Aşağıdaki örnekte gösterildiği gibi öğesinden oluşturulur.  
  
 [!code-csharp[c_CreateSTS#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#5)]
 [!code-vb[c_CreateSTS#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#5)]  
  
 Güvenlik belirteci hizmetinin paylaşılan anahtar malzemesini sağladığı durumda, düzeltme belirteci bir oluşturarak oluşturulur <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken> .  
  
 [!code-csharp[c_CreateSTS#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#6)]
 [!code-vb[c_CreateSTS#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#6)]  
  
 İstemci ve güvenlik belirteci hizmeti her ikisi de paylaşılan anahtar için anahtar malzeme sağladığınızda kanıt belirtecinin nasıl oluşturulacağı hakkında daha fazla bilgi için bkz. [Federasyon örneği](../samples/federation-sample.md).  
  
 Verilen belirteç başvuruları, sınıfının örnekleri oluşturularak oluşturulur <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> .  
  
 [!code-csharp[c_CreateSTS#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#7)]
 [!code-vb[c_CreateSTS#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#7)]  
  
 Daha sonra bu çeşitli değerler istemciye döndürülen yanıt iletisine serileştirilir.  
  
## <a name="example"></a>Örnek  
 Bir güvenlik belirteci hizmeti için tam kod için bkz. [Federasyon örneği](../samples/federation-sample.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Tokens.SigningCredentials>
- <xref:System.IdentityModel.Tokens.SecurityKey>
- <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>
- <xref:System.IdentityModel.Tokens.SamlSecurityToken>
- <xref:System.IdentityModel.Tokens.SamlAssertion>
- <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>
- <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause>
- [Federasyon Örneği](../samples/federation-sample.md)
