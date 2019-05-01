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
ms.openlocfilehash: 04517e5089f55c2d2b08a492439026d33ed9069d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991082"
---
# <a name="saml-tokens-and-claims"></a>SAML Belirteçleri ve Talepleri
Güvenlik onaylama işaretleme dili (SAML) *belirteçleri* talep XML temsillerini olan. Varsayılan olarak, SAML belirteçlerini Windows Communication Foundation (WCF) kullanan güvenlik federe senaryolarda olan *verilen belirteçler*.  
  
 SAML belirteçlerini başka bir varlık ile ilgili bir varlık tarafından yapılan talep kümesi olan deyimleri taşır. Örneğin, güvenlik federe senaryolarda, sistemde bulunan bir kullanıcı ile ilgili bir güvenlik belirteci hizmeti tarafından deyimleri yapılır. Güvenlik belirteci hizmeti belirtecinde yer alan ifadeleri belki belirtmek için SAML belirteci imzalar. Buna ek olarak, SAML belirteci SAML belirtecinin kullanıcı bilgisi kanıtlar şifreleme anahtar malzemesi ile ilişkilidir. Bu kavram, bağlı olan taraf SAML belirteci olan aslında, o kullanıcıya verilen karşılar. Örneğin, tipik bir senaryoda:  
  
1. Bir istemci, bu güvenlik belirteci hizmeti için Windows kimlik bilgilerini kullanarak kimlik doğrulaması, bir güvenlik belirteci Hizmeti'nden bir SAML belirteci ister.  
  
2. Güvenlik belirteci hizmeti istemciye bir SAML belirteci verir. SAML belirtecindeki güvenlik belirteci hizmeti ile ilişkili bir sertifika ile imzalanmış ve şifrelenmiş hedef hizmet için bir düzeltme anahtar içeriyor.  
  
3. İstemci ayrıca bir kopyasını alır *kanıt anahtarı*. İstemci uygulama hizmeti SAML belirtecine ardından sunar ( *bağlı olan taraf*) ve ileti kavram anahtarla imzalar.  
  
4. SAML belirtecindeki üzerinden imzası, bağlı olan taraf güvenlik belirteci hizmeti belirteci veren söyler. Sağlama anahtarı ile oluşturulan ileti imzası, belirteci istemciye verildiğini bağlı olan taraf söyler.  
  
## <a name="from-claims-to-samlattributes"></a>Gelen talepler için SamlAttributes  
 WCF'de, SAML belirteçlerini deyimlerinde olarak modellenir <xref:System.IdentityModel.Tokens.SamlAttribute> doğrudan doldurulabilir nesneleri <xref:System.IdentityModel.Claims.Claim> sağlanan nesnelerini <xref:System.IdentityModel.Claims.Claim> nesnesinin bir <xref:System.IdentityModel.Claims.Claim.Right%2A> özelliği <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> ve <xref:System.IdentityModel.Claims.Claim.Resource%2A> özelliği olduğu tür <xref:System.String>. Örneğin:  
  
 [!code-csharp[c_CreateSTS#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#8)]
 [!code-vb[c_CreateSTS#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#8)]  
  
> [!NOTE]
>  SAML belirteçlerini, iletileri bir güvenlik belirteci hizmeti tarafından çıkarıldığında veya hizmetleri için istemciler tarafından kimlik doğrulaması bir parçası olarak sunulduklarında serileştirildiği zaman, en büyük ileti boyutu kotası SAML belirteci uyum sağlamak için yeterince büyük olması gerekir ve diğer ileti bölümleri. Normal durumlarda, varsayılan ileti boyutu kotası yeterlidir. Ancak, talep yüzlerce içerdiğinden SAML belirteci büyük olduğu durumlarda, serileştirilmiş belirteci uyum sağlamak için kotaları artırma gerekebilir. Daha fazla bilgi için [veriler için güvenlik konuları](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).  
  
## <a name="from-samlattributes-to-claims"></a>SamlAttributes talepler için  
 SAML belirteçlerini iletilerinde alındığında, SAML belirtecindeki çeşitli deyimleri içinde açık olduğundan <xref:System.IdentityModel.Policy.IAuthorizationPolicy> içine yerleştirilen nesneleri <xref:System.IdentityModel.Policy.AuthorizationContext>. Talepleri her SAML deyiminden tarafından döndürülen <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> özelliği <xref:System.IdentityModel.Policy.AuthorizationContext> ve kimliğini doğrulamak ve kullanıcıya yetki verilip verilmeyeceğine karar vermek için incelenebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Policy.AuthorizationContext>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- <xref:System.IdentityModel.Claims.ClaimSet>
- [Federasyon](../../../../docs/framework/wcf/feature-details/federation.md)
- [Nasıl yapılır: Federe istemci oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Nasıl yapılır: Federe bir hizmette kimlik bilgilerini yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [Talepler ve Belirteçler](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)
- [Talep Oluşturma ve Kaynak Değerleri](../../../../docs/framework/wcf/feature-details/claim-creation-and-resource-values.md)
- [Nasıl yapılır: Özel talep oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
