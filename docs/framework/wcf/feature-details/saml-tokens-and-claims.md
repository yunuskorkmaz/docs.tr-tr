---
title: SAML Belirteçleri ve Talepleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
- issued tokens
- SAML token
ms.assetid: 930b6e34-9eab-4e95-826c-4e06659bb977
ms.openlocfilehash: 7037daf299d7c750ab398c21c1d7ccb541620701
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943068"
---
# <a name="saml-tokens-and-claims"></a>SAML Belirteçleri ve Talepleri
Güvenlik onayları biçimlendirme dili (SAML) *belirteçleri* , taleplerin XML temsilleridir. Varsayılan olarak, Federasyon güvenlik senaryolarında Windows Communication Foundation (WCF) SAML belirteçlerinin kullanımları *verilen belirteçlerdir*.  
  
 SAML belirteçleri, başka bir varlık hakkında bir varlık tarafından yapılan talep kümeleri olan deyimleri taşır. Örneğin, Federasyon güvenlik senaryolarında, deyimler sistemdeki bir kullanıcı hakkında bir güvenlik belirteci hizmeti tarafından yapılır. Güvenlik belirteci hizmeti, belirteç içinde yer alan deyimlerin bütünlüğünü belirtmek için SAML belirtecini imzalar. Ayrıca, SAML belirteci, SAML belirtecinin kullanıcısına bilgi sahibi olan şifreleme anahtarı malzemesiyle ilişkilendirilir. Bu kanıt, SAML belirtecinin aslında söz konusu kullanıcıya verildiği bağlı olan tarafı karşılar. Örneğin, tipik bir senaryoda:  
  
1. İstemci bir güvenlik belirteci hizmetinden bir SAML belirteci ister ve bu güvenlik belirteci hizmetinde Windows kimlik bilgilerini kullanarak kimlik doğrulaması ister.  
  
2. Güvenlik belirteci hizmeti istemciye bir SAML belirteci yayınlar. SAML belirteci, güvenlik belirteci hizmetiyle ilişkili bir sertifikayla imzalanır ve hedef hizmet için şifrelenmiş bir düzeltme anahtarı içerir.  
  
3. İstemci Ayrıca *prova anahtarının*bir kopyasını alır. İstemci daha sonra SAML belirtecini uygulama hizmetine ( *bağlı olan taraf*) gösterir ve iletiyi bu kanıt anahtarıyla imzalar.  
  
4. SAML belirtecinin üzerindeki imza, bağlı olan tarafa güvenlik belirteci hizmetinin belirteci vermesini söyler. Kanıt anahtarıyla oluşturulan ileti imzası, bağlı olan tarafa belirtecin istemciye verildiğini söyler.  
  
## <a name="from-claims-to-samlattributes"></a>Taleplerden SamlAttributes 'e  
 WCF 'de, SAML belirteçlerdeki deyimler nesneler <xref:System.IdentityModel.Tokens.SamlAttribute> <xref:System.IdentityModel.Claims.Claim> <xref:System.IdentityModel.Claims.Claim.Right%2A> <xref:System.IdentityModel.Claims.Claim> olarak modellenir, ancak nesne bir özelliğine <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> sahip ve <xref:System.IdentityModel.Claims.Claim.Resource%2A> özelliği yazın <xref:System.String>. Örneğin:  
  
 [!code-csharp[c_CreateSTS#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#8)]
 [!code-vb[c_CreateSTS#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#8)]  
  
> [!NOTE]
> Bir güvenlik belirteci hizmeti tarafından verildiğinde veya istemciler tarafından kimlik doğrulamanın bir parçası olarak sunulduklarında, SAML belirteçleri iletilerde serileştirildiklerinde, en büyük ileti boyutu kotasının SAML belirtecini barındırmak için yeterince büyük olması gerekir ve diğer ileti bölümleri. Normal durumlarda, varsayılan ileti boyutu kotaları yeterlidir. Ancak, yüzlerce talep içerdiğinden SAML belirtecinin büyük olduğu durumlarda, serileştirilmiş belirtece uyum sağlamak için kotaları artırmanız gerekebilir. Daha fazla bilgi için bkz. [veriler Için güvenlik konuları](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).  
  
## <a name="from-samlattributes-to-claims"></a>SamlAttributes 'dan talepler 'e  
 İletilerde SAML belirteçleri alındığında, SAML belirtecindeki çeşitli deyimler öğesine yerleştirilmiş <xref:System.IdentityModel.Policy.IAuthorizationPolicy> <xref:System.IdentityModel.Policy.AuthorizationContext>nesnelere açılır. Her SAML deyimindeki talepler <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> <xref:System.IdentityModel.Policy.AuthorizationContext> öğesinin özelliği tarafından döndürülür ve kullanıcının kimlik doğrulaması ve yetkilendirilip yetkilendirilmeyeceğini tespit etmek üzere incelenebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Policy.AuthorizationContext>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- <xref:System.IdentityModel.Claims.ClaimSet>
- [Federasyon](../../../../docs/framework/wcf/feature-details/federation.md)
- [Nasıl yapılır: Federe Istemci oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Nasıl yapılır: Federasyon Hizmeti kimlik bilgilerini yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [Talepler ve Belirteçler](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)
- [Talep Oluşturma ve Kaynak Değerleri](../../../../docs/framework/wcf/feature-details/claim-creation-and-resource-values.md)
- [Nasıl yapılır: Özel talep oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
