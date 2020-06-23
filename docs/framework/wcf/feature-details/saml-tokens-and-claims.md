---
title: SAML Belirteçleri ve Talepleri
description: WFC 'nin, başka bir varlık hakkında bir varlık tarafından yapılan talepler kümesi olan deyimleri taşımak için SAML belirteçlerini nasıl kullandığını öğrenin.
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
ms.openlocfilehash: c054e594af69def96879852a5145675b3123614a
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244952"
---
# <a name="saml-tokens-and-claims"></a>SAML Belirteçleri ve Talepleri
Güvenlik onayları biçimlendirme dili (SAML) *belirteçleri* , taleplerin XML temsilleridir. Varsayılan olarak, Federasyon güvenlik senaryolarında Windows Communication Foundation (WCF) SAML belirteçlerinin kullanımları *verilen belirteçlerdir*.  
  
 SAML belirteçleri, başka bir varlık hakkında bir varlık tarafından yapılan talep kümeleri olan deyimleri taşır. Örneğin, Federasyon güvenlik senaryolarında, deyimler sistemdeki bir kullanıcı hakkında bir güvenlik belirteci hizmeti tarafından yapılır. Güvenlik belirteci hizmeti, belirteç içinde yer alan deyimlerin bütünlüğünü belirtmek için SAML belirtecini imzalar. Ayrıca, SAML belirteci, SAML belirtecinin kullanıcısına bilgi sahibi olan şifreleme anahtarı malzemesiyle ilişkilendirilir. Bu kanıt, SAML belirtecinin aslında söz konusu kullanıcıya verildiği bağlı olan tarafı karşılar. Örneğin, tipik bir senaryoda:  
  
1. İstemci bir güvenlik belirteci hizmetinden bir SAML belirteci ister ve bu güvenlik belirteci hizmetinde Windows kimlik bilgilerini kullanarak kimlik doğrulaması ister.  
  
2. Güvenlik belirteci hizmeti istemciye bir SAML belirteci yayınlar. SAML belirteci, güvenlik belirteci hizmetiyle ilişkili bir sertifikayla imzalanır ve hedef hizmet için şifrelenmiş bir düzeltme anahtarı içerir.  
  
3. İstemci Ayrıca *prova anahtarının*bir kopyasını alır. İstemci daha sonra SAML belirtecini uygulama hizmetine ( *bağlı olan taraf*) gösterir ve iletiyi bu kanıt anahtarıyla imzalar.  
  
4. SAML belirtecinin üzerindeki imza, bağlı olan tarafa güvenlik belirteci hizmetinin belirteci vermesini söyler. Kanıt anahtarıyla oluşturulan ileti imzası, bağlı olan tarafa belirtecin istemciye verildiğini söyler.  
  
## <a name="from-claims-to-samlattributes"></a>Taleplerden SamlAttributes 'e  
 WCF 'de, SAML belirteçlerdeki deyimler nesneler olarak modellenir, <xref:System.IdentityModel.Tokens.SamlAttribute> Bu da <xref:System.IdentityModel.Claims.Claim> <xref:System.IdentityModel.Claims.Claim> nesnenin bir <xref:System.IdentityModel.Claims.Claim.Right%2A> özelliği <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> ve <xref:System.IdentityModel.Claims.Claim.Resource%2A> özelliği türünde olması <xref:System.String> şartıyla doğrudan nesnelerden doldurulabilirler. Örneğin:  
  
 [!code-csharp[c_CreateSTS#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#8)]
 [!code-vb[c_CreateSTS#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#8)]  
  
> [!NOTE]
> Bir güvenlik belirteci hizmeti tarafından verildiğinde veya istemciler tarafından kimlik doğrulamanın bir parçası olarak sunulduklarında, SAML belirteçleri iletilerde serileştirildiklerinde, en büyük ileti boyutu kotasının SAML belirtecini ve diğer ileti parçalarını karşılayacak kadar büyük olması gerekir. Normal durumlarda, varsayılan ileti boyutu kotaları yeterlidir. Ancak, yüzlerce talep içerdiğinden SAML belirtecinin büyük olduğu durumlarda, serileştirilmiş belirtece uyum sağlamak için kotaları artırmanız gerekebilir. Daha fazla bilgi için bkz. [veriler Için güvenlik konuları](security-considerations-for-data.md).  
  
## <a name="from-samlattributes-to-claims"></a>SamlAttributes 'dan talepler 'e  
 İletilerde SAML belirteçleri alındığında, SAML belirtecindeki çeşitli deyimler öğesine <xref:System.IdentityModel.Policy.IAuthorizationPolicy> yerleştirilmiş nesnelere açılır <xref:System.IdentityModel.Policy.AuthorizationContext> . Her SAML deyimindeki talepler <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> öğesinin özelliği tarafından döndürülür <xref:System.IdentityModel.Policy.AuthorizationContext> ve kullanıcının kimlik doğrulaması ve yetkilendirilip yetkilendirilmeyeceğini tespit etmek üzere incelenebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Policy.AuthorizationContext>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- <xref:System.IdentityModel.Claims.ClaimSet>
- [Federasyon](federation.md)
- [Nasıl yapılır: Federe İstemci Oluşturma](how-to-create-a-federated-client.md)
- [Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma](how-to-configure-credentials-on-a-federation-service.md)
- [Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme](managing-claims-and-authorization-with-the-identity-model.md)
- [Talepler ve Belirteçler](claims-and-tokens.md)
- [Beyan Oluşturma ve Kaynak Değerleri](claim-creation-and-resource-values.md)
- [Nasıl yapılır: Özel Beyan Oluşturma](../extending/how-to-create-a-custom-claim.md)
