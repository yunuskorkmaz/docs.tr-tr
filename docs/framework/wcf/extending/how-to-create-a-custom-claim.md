---
title: 'Nasıl yapılır: Özel Beyan Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: e78f577e0fd3473575fab998e55616936212ebb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185612"
---
# <a name="how-to-create-a-custom-claim"></a>Nasıl yapılır: Özel Beyan Oluşturma
Windows Communication Foundation'daki (WCF) Kimlik Modeli altyapısı, bu tür ve haklara sahip <xref:System.IdentityModel.Claims.Claim> örnekler oluşturmak için yardımcı işlevlerle birlikte yerleşik talep türleri ve hakları kümesi sağlar. Bu yerleşik talepler, WCF'nin varsayılan olarak desteklediği istemci kimlik bilgisi türlerinde bulunan bilgileri modellemek üzere tasarlanmıştır. Çoğu durumda, yerleşik talepler yeterlidir; ancak bazı uygulamalar özel talepler gerektirebilir. Talep, talep türünden, talebin geçerli olduğu kaynaktan ve bu kaynak üzerinde öne sürülenen haktan oluşur. Bu konu, özel bir talep oluşturma nın nasıl açıklanmaktadır.  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a>İlkel bir veri türünü temel alan özel bir talep oluşturmak için  
  
1. Talep türünü, kaynak değerini ve hakkı <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> oluşturucuya geçirerek özel bir talep oluşturun.  
  
    1. Talep türü için benzersiz bir değer belirleyin.  
  
         Talep türü benzersiz bir dize tanımlayıcısır. Talep türü için kullanılan dize tanımlayıcısının benzersiz olduğundan emin olmak özel talep tasarımcısının sorumluluğundadır. WCF tarafından tanımlanan talep türlerinin listesi için <xref:System.IdentityModel.Claims.ClaimTypes> sınıfa bakın.  
  
    2. Kaynak için ilkel veri türünü ve değerini seçin.  
  
         Kaynak bir nesnedir. Kaynağın CLR türü, herhangi bir serileştirilebilir <xref:System.Int32>tür gibi <xref:System.String> ilkel olabilir. Talepler WCF tarafından çeşitli noktalarda seri hale getirildığından, kaynağın CLR türü serileştirilebilir olmalıdır. İlkel türleri serileştirilebilir.  
  
    3. WCF tarafından tanımlanan bir hakkı veya özel bir hak için benzersiz bir değer seçin.  
  
         Sağ, benzersiz bir dize tanımlayıcısıdır. WCF tarafından tanımlanan haklar <xref:System.IdentityModel.Claims.Rights> sınıfta tanımlanır.  
  
         Sağ için kullanılan dize tanımlayıcısının benzersiz olmasını sağlamak özel talep tasarımcısının sorumluluğundadır.  
  
         Aşağıdaki kod `http://example.org/claims/simplecustomclaim`örneği, adlı `Driver's License`bir kaynak için ve <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> hakkı olan bir talep türüyle özel bir talep oluşturur.  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a>İlkel olmayan bir veri türünü temel alan özel bir talep oluşturmak için  
  
1. Talep türünü, kaynak değerini ve hakkı <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> oluşturucuya geçirerek özel bir talep oluşturun.  
  
    1. Talep türü için benzersiz bir değer belirleyin.  
  
         Talep türü benzersiz bir dize tanımlayıcısır. Talep türü için kullanılan dize tanımlayıcısının benzersiz olduğundan emin olmak özel talep tasarımcısının sorumluluğundadır. WCF tarafından tanımlanan talep türlerinin listesi için <xref:System.IdentityModel.Claims.ClaimTypes> sınıfa bakın.  
  
    2. Kaynak için seri olarak yazılabilir ilkel olmayan bir tür seçin veya tanımlayın.  
  
         Kaynak bir nesnedir. Talepler WCF tarafından çeşitli noktalarda seri hale getirildığından, kaynağın CLR türü serileştirilebilir olmalıdır. İlkel türleri zaten serileştirilebilir.  
  
         Yeni bir tür tanımlandığında, <xref:System.Runtime.Serialization.DataContractAttribute> sınıfa uygulayın. Ayrıca, <xref:System.Runtime.Serialization.DataMemberAttribute> talebin bir parçası olarak serileştirilmesi gereken yeni türün tüm üyelerine özniteliği uygulayın.  
  
         Aşağıdaki kod örneği adlı `MyResourceType`özel bir kaynak türü tanımlar.  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)]
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]
  
    3. WCF tarafından tanımlanan bir hakkı veya özel bir hak için benzersiz bir değer seçin.  
  
         Sağ, benzersiz bir dize tanımlayıcısıdır. WCF tarafından tanımlanan haklar <xref:System.IdentityModel.Claims.Rights> sınıfta tanımlanır.  
  
         Sağ için kullanılan dize tanımlayıcısının benzersiz olmasını sağlamak özel talep tasarımcısının sorumluluğundadır.  
  
         Aşağıdaki kod `http://example.org/claims/complexcustomclaim`örneği, bir talep türü , özel bir kaynak `MyResourceType`türü ve <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> sağ ile özel bir talep oluşturur.  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)]
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, ilkel bir kaynak türüyle özel bir talep ve ilkel olmayan bir kaynak türüne sahip özel bir talep oluşturmanın nasıl yapılacağını gösterir.  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)
