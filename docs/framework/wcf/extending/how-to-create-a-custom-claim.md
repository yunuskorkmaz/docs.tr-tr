---
title: 'Nasıl yapılır: Özel Talep Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: 1892e910a86e01b7b2ee0f6a2403ad7af4688808
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857785"
---
# <a name="how-to-create-a-custom-claim"></a>Nasıl yapılır: Özel Talep Oluşturma
Windows Communication Foundation (WCF) kimlik modeli altyapısı oluşturmak için bir dizi yerleşik talep türleri ve yardımcı işlevlerini haklarıyla sağlar <xref:System.IdentityModel.Claims.Claim> örnekleriyle bu türleri ve hakları. Bu yerleşik talepler, model bilgileri varsayılan olarak WCF destekleyen istemci kimlik bilgisi türlerinde bulunan şekilde tasarlanmıştır. Çoğu durumda, yerleşik talep yeterlidir; Ancak bazı uygulamalar, özel talepler gerektirebilir. Bir talep talep türünü, talep için geçerli olduğu için kaynak ve doğrudan diğer bir deyişle olarak onaylanan bu kaynak üzerinde oluşur. Bu konuda bir özel talep oluşturma işlemini açıklar.  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a>Bir temel veri türüne göre özel bir talep oluşturmak için  
  
1. Talep türü, kaynak değeri ve sağa geçirerek özel talep oluşturma <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> Oluşturucusu.  
  
    1. Talep türü için benzersiz bir değer karar verin.  
  
         Talep türünü bir benzersiz tanımlayıcıdır. Talep türü için kullanılan dize tanımlayıcı benzersiz olduğundan emin olun özel talep tasarımcının sorumluluğundadır. WCF tarafından tanımlanan talep türlerinin bir listesi için bkz. <xref:System.IdentityModel.Claims.ClaimTypes> sınıfı.  
  
    2. Basit veri türü ve kaynak için bir değer seçin.  
  
         Bir kaynak bir nesnedir. Kaynak CLR türü gibi basit bir tür olabilir <xref:System.String> veya <xref:System.Int32>, veya serializable bir tür. WCF tarafından talep çeşitli noktalarda serileştirilme şeklini çünkü kaynak CLR türü seri hale getirilebilir, olması gerekir. İlkel türler seri hale getirilebilir.  
  
    3. WCF veya özel bir hak için benzersiz bir değer tarafından tanımlanan bir sağ seçin.  
  
         Bir hak benzersiz dize bir tanımlayıcıdır. WCF tarafından tanımlanan hakları tanımlanan <xref:System.IdentityModel.Claims.Rights> sınıfı.  
  
         Sağa için kullanılan dize tanımlayıcı benzersiz olduğundan emin olun özel talep tasarımcının sorumluluğundadır.  
  
         Aşağıdaki kod örneği, bir talep türü ile özel bir talep oluşturur `http://example.org/claims/simplecustomclaim`, adlı bir kaynak için `Driver's License`ile <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> doğru.  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a>Bir basit olmayan veri türüne göre özel bir talep oluşturmak için  
  
1. Talep türü, kaynak değeri ve sağa geçirerek özel talep oluşturma <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> Oluşturucusu.  
  
    1. Talep türü için benzersiz bir değer karar verin.  
  
         Talep türünü bir benzersiz tanımlayıcıdır. Talep türü için kullanılan dize tanımlayıcı benzersiz olduğundan emin olun özel talep tasarımcının sorumluluğundadır. WCF tarafından tanımlanan talep türlerinin bir listesi için bkz. <xref:System.IdentityModel.Claims.ClaimTypes> sınıfı.  
  
    2. Seçin veya kaynak için serileştirilebilir bir temel olmayan türde tanımlayın.  
  
         Bir kaynak bir nesnedir. WCF tarafından talep çeşitli noktalarda serileştirilme şeklini çünkü kaynak CLR türü seri hale getirilebilir, olması gerekir. İlkel türler, zaten seri hale getirilebilir.  
  
         Yeni bir tür tanımlandığında, uygulama <xref:System.Runtime.Serialization.DataContractAttribute> sınıfa. Ayrıca uygulama <xref:System.Runtime.Serialization.DataMemberAttribute> talep bir parçası olarak seri hale gerek yeni türün tüm üyeleri için özniteliği.  
  
         Aşağıdaki kod örneğinde adlı bir özel kaynak türünü tanımlayan `MyResourceType`.  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)] 
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]        
  
    3. WCF veya özel bir hak için benzersiz bir değer tarafından tanımlanan bir sağ seçin.  
  
         Bir hak benzersiz dize bir tanımlayıcıdır. WCF tarafından tanımlanan hakları tanımlanan <xref:System.IdentityModel.Claims.Rights> sınıfı.  
  
         Sağa için kullanılan dize tanımlayıcı benzersiz olduğundan emin olun özel talep tasarımcının sorumluluğundadır.  
  
         Aşağıdaki kod örneği, bir talep türü ile özel bir talep oluşturur `http://example.org/claims/complexcustomclaim`, özel kaynak türü `MyResourceType`ile <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> doğru.  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)] 
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]     
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, ilkel olmayan kaynak türü ile bir özel talep ilkel kaynak türü ile ve özel talep oluşturma işlemini gösterir.  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
