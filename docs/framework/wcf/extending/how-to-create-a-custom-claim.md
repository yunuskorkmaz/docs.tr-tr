---
title: 'Nasıl yapılır: Özel Talep Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: 399aba1a6ad70ae37355f529a291ab2f604af03f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797081"
---
# <a name="how-to-create-a-custom-claim"></a>Nasıl yapılır: Özel Talep Oluşturma
Windows Communication Foundation (WCF) içindeki kimlik modeli altyapısı, bu tür ve haklara sahip örnekler oluşturmak <xref:System.IdentityModel.Claims.Claim> için yardımcı işlevlerle birlikte yerleşik talep türleri ve haklar kümesi sağlar. Bu yerleşik talepler, WCF 'nin varsayılan olarak desteklediği istemci kimlik bilgileri türlerinde bulunan bilgileri modellemek üzere tasarlanmıştır. Birçok durumda, yerleşik talepler yeterlidir; Ancak bazı uygulamalar özel talepler gerektirebilir. Talep türü, talebin uygulandığı kaynak ve söz konusu kaynak üzerinde bir hak olan talep türünden oluşur. Bu konu başlığı altında, özel bir talebin nasıl oluşturulacağı açıklanmaktadır.  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a>Temel bir veri türünü temel alan özel bir talep oluşturmak için  
  
1. Talep türünü, kaynak değerini ve hakkını <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> oluşturucuya geçirerek özel bir talep oluşturun.  
  
    1. Talep türü için benzersiz bir değer belirleyin.  
  
         Talep türü benzersiz bir dize tanımlayıcısıdır. Bu, talep türü için kullanılan dize tanımlayıcısının benzersiz olduğundan emin olmak için özel talep tasarımcısının sorumluluğundadır. WCF tarafından tanımlanan talep türlerinin bir listesi için, <xref:System.IdentityModel.Claims.ClaimTypes> sınıfına bakın.  
  
    2. Kaynağın temel veri türünü ve değerini seçin.  
  
         Kaynak bir nesnedir. Kaynağın clr türü <xref:System.String> veya <xref:System.Int32>gibi bir temel olabilir veya ya da serileştirilebilir herhangi bir tür olabilir. Talepler WCF tarafından farklı noktalarda serileştirildiği için kaynağın CLR türü seri hale getirilebilir olmalıdır. İlkel türler seri hale getirilebilir.  
  
    3. WCF tarafından tanımlanan bir sağ veya özel bir hak için benzersiz bir değer seçin.  
  
         Sağ, benzersiz bir dize tanımlayıcısıdır. WCF tarafından tanımlanan haklar <xref:System.IdentityModel.Claims.Rights> sınıfında tanımlanmıştır.  
  
         Sağ tarafta kullanılan dize tanımlayıcısının benzersiz olduğundan emin olmak için özel talep tasarımcısının sorumluluğundadır.  
  
         Aşağıdaki kod örneği,, adlı `http://example.org/claims/simplecustomclaim` `Driver's License`bir kaynak ve <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> sağ ile bir talep türü ile özel bir talep oluşturur.  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a>İlkel olmayan bir veri türünü temel alan özel bir talep oluşturmak için  
  
1. Talep türünü, kaynak değerini ve hakkını <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> oluşturucuya geçirerek özel bir talep oluşturun.  
  
    1. Talep türü için benzersiz bir değer belirleyin.  
  
         Talep türü benzersiz bir dize tanımlayıcısıdır. Bu, talep türü için kullanılan dize tanımlayıcısının benzersiz olduğundan emin olmak için özel talep tasarımcısının sorumluluğundadır. WCF tarafından tanımlanan talep türlerinin bir listesi için, <xref:System.IdentityModel.Claims.ClaimTypes> sınıfına bakın.  
  
    2. Kaynak için seri hale getirilebilir bir temel olmayan tür seçin veya tanımlayın.  
  
         Kaynak bir nesnedir. Talepler WCF tarafından farklı noktalarda serileştirildiği için kaynağın CLR türü seri hale getirilebilir olmalıdır. İlkel türler zaten serileştirilebilir.  
  
         Yeni bir tür tanımlandığında, <xref:System.Runtime.Serialization.DataContractAttribute> sınıfını sınıfına uygulayın. Ayrıca, <xref:System.Runtime.Serialization.DataMemberAttribute> talebin bir parçası olarak serileştirilmesi gereken yeni türün tüm üyelerine özniteliğini uygular.  
  
         Aşağıdaki kod örneği adlı `MyResourceType`özel bir kaynak türünü tanımlar.  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)] 
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]        
  
    3. WCF tarafından tanımlanan bir sağ veya özel bir hak için benzersiz bir değer seçin.  
  
         Sağ, benzersiz bir dize tanımlayıcısıdır. WCF tarafından tanımlanan haklar <xref:System.IdentityModel.Claims.Rights> sınıfında tanımlanmıştır.  
  
         Sağ tarafta kullanılan dize tanımlayıcısının benzersiz olduğundan emin olmak için özel talep tasarımcısının sorumluluğundadır.  
  
         Aşağıdaki kod örneği, bir talep türü `http://example.org/claims/complexcustomclaim`, özel kaynak `MyResourceType`türü ve <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> sağ ile özel bir talep oluşturur.  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)] 
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]     
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, temel olmayan bir kaynak türü ile bir basit kaynak türüne ve özel talebe sahip özel bir talebin nasıl oluşturulacağını göstermektedir.  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)
