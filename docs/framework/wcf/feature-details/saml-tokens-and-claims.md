---
title: "SAML Belirteçleri ve Talepleri"
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
- issued tokens
- SAML token
ms.assetid: 930b6e34-9eab-4e95-826c-4e06659bb977
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a2b35ba4da503663a2bb92597ed193c408e7c99b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="saml-tokens-and-claims"></a>SAML Belirteçleri ve Talepleri
Güvenlik onaylar biçimlendirme dili (SAML) *belirteçleri* talep XML gösterimlerini şunlardır. Varsayılan olarak, SAML belirteçlerini [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] federe güvenlik senaryolarda kullanımları *verilen belirteçler*.  
  
 SAML belirteçleri başka bir varlık hakkında bir varlık tarafından yapılan talepleri kümeleridir deyimleri taşır. Örneğin, Federasyon güvenlik senaryolarda, sistemde bir kullanıcıyla ilgili bir güvenlik belirteci hizmeti tarafından deyimleri yapılır. Güvenlik belirteci hizmeti belirtecinde yer alan deyimleri belki belirtmek için SAML belirteci imzalar. Ayrıca, SAML belirteci SAML belirteci kullanıcı bilgisi kanıtlar şifreleme anahtar malzemesi ile ilişkilidir. SAML belirteci olduğu, bağlı olan taraf aslında, o kullanıcıya verilen bu kanıt karşılar. Örneğin, tipik bir senaryoda:  
  
1.  Bir istemci, bu güvenlik belirteci hizmeti Windows kimlik bilgilerini kullanarak kimlik doğrulaması, bir güvenlik belirteci Hizmeti'nden bir SAML belirtecine ister.  
  
2.  Güvenlik belirteci hizmeti istemciye bir SAML belirteci verir. SAML belirteci güvenlik belirteci hizmeti ile ilişkili bir sertifikayla imzalanmış ve hedef hizmet için şifrelenmiş bir kanıt anahtarı içerir.  
  
3.  İstemci ayrıca bir kopyasını alır *kanıt anahtarı*. İstemci uygulama hizmeti SAML belirtecine sonra sunar ( *bağlı olan taraf*) ve ileti bu kanıtını anahtarıyla imzalar.  
  
4.  SAML belirteci üzerinden imza, güvenlik belirteci hizmeti belirteç verilen bağlı olan taraf söyler. Kanıt anahtarı ile oluşturulan ileti imzası, belirteci istemciye verilmiş bağlı olan taraf söyler.  
  
## <a name="from-claims-to-samlattributes"></a>SamlAttributes talepleri  
 İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], SAML belirteçlerini deyimlerinde olarak modellenir <xref:System.IdentityModel.Tokens.SamlAttribute> doğrudan doldurulmuş nesneleri <xref:System.IdentityModel.Claims.Claim> sağlanan nesnelerini <xref:System.IdentityModel.Claims.Claim> nesnesi bir <xref:System.IdentityModel.Claims.Claim.Right%2A> özelliği <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> ve <xref:System.IdentityModel.Claims.Claim.Resource%2A> özellik türüdür <xref:System.String>. Örneğin:  
  
 [!code-csharp[c_CreateSTS#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#8)]
 [!code-vb[c_CreateSTS#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#8)]  
  
> [!NOTE]
>  SAML belirteçleri iletilerinde, bir güvenlik belirteci hizmeti tarafından verildiğinde veya hizmetleri için istemciler tarafından kimlik doğrulaması bir parçası olarak sunulduklarında serileştirildiği zaman maksimum ileti boyutu kotası SAML belirteci karşılamak için yeterli büyüklükte olması gerekir ve diğer ileti bölümleri. Normal durumlarda, varsayılan ileti boyutu kotalarını yeterlidir. Ancak, talep yüzlerce içerdiğinden bir SAML belirtecine büyük olduğu durumlarda, serileştirilmiş belirteci uyum sağlamak için kotaları artırma gerekebilir. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Veriler için güvenlik konuları](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).  
  
## <a name="from-samlattributes-to-claims"></a>Talepler için SamlAttributes  
 SAML belirteçleri iletilerinde alındığında SAML belirteci çeşitli deyimlerinde içine açık olan <xref:System.IdentityModel.Policy.IAuthorizationPolicy> içine yerleştirilen nesneleri <xref:System.IdentityModel.Policy.AuthorizationContext>. Talepleri her SAML ifadesi tarafından döndürülen <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> özelliği <xref:System.IdentityModel.Policy.AuthorizationContext> ve kimlik doğrulama ve kullanıcı yetkilendirme yazılıp yazılmayacağını incelenebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IdentityModel.Policy.AuthorizationContext>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 <xref:System.IdentityModel.Claims.ClaimSet>  
 [Federasyon](../../../../docs/framework/wcf/feature-details/federation.md)  
 [Nasıl yapılır: Federe İstemci Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [Talepler ve Belirteçler](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)  
 [Talep Oluşturma ve Kaynak Değerleri](../../../../docs/framework/wcf/feature-details/claim-creation-and-resource-values.md)  
 [Nasıl yapılır: Özel Talep Oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
