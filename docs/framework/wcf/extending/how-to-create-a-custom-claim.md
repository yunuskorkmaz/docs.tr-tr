---
title: "Nasıl yapılır: Özel Beyan Oluşturma"
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
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e1e85d1815d1fbde25e1963a54cce8f02f5344a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-custom-claim"></a>Nasıl yapılır: Özel Beyan Oluşturma
Kimlik modeli altyapısında [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] oluşturmak için bir dizi yerleşik talep türlerini ve hakları ile yardımcı işlevleri sağlar <xref:System.IdentityModel.Claims.Claim> bu türleri ve hakları ile örnekleri. Bu yerleşik talepler bulunan model bilgisi için tasarlanmış kimlik bilgisi istemcisinde türleri [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] varsayılan olarak destekler. Çoğu durumda, yerleşik talep yeterlidir; Ancak bazı uygulamalar özel talep gerektirebilir. Bir talep talep türünü, talep geçerli olduğu için kaynak ve sağ diğer bir deyişle sürülen bu kaynak oluşur. Bu konuda bir özel talep oluşturmayı açıklar.  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a>Temel veri türüne göre özel bir talep oluşturmak için  
  
1.  Talep türü, kaynak değeri ve sağa geçirerek özel beyan oluşturma <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> Oluşturucusu.  
  
    1.  Talep türü için benzersiz bir değer karar verin.  
  
         Talep türü benzersiz bir dize tanımlayıcısı değil. Talep türü için kullanılan dize tanımlayıcı benzersiz olduğundan emin olun özel talep tasarımcının sorumluluğundadır. Tarafından tanımlanan talep türleri listesini [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], bkz: <xref:System.IdentityModel.Claims.ClaimTypes> sınıfı.  
  
    2.  Basit veri türü ve kaynak için değer seçin.  
  
         Bir kaynak bir nesnedir. Kaynak CLR türü bir primitive gibi olabilir <xref:System.String> veya <xref:System.Int32>, veya serializable bir tür. Talep tarafından çeşitli noktalarında serileştirilir çünkü kaynak CLR türü seri hale getirilebilir, olmalıdır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. İlkel türler seri hale getirilebilir.  
  
    3.  Tarafından tanımlanan bir hak seçin [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] veya özel bir hak için benzersiz bir değer.  
  
         Bir hak benzersiz bir dize tanımlayıcısı değil. Tarafından tanımlanan haklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tanımlanan <xref:System.IdentityModel.Claims.Rights> sınıfı.  
  
         Hakkını kullanılan dize tanımlayıcı benzersiz olduğundan emin olun özel talep tasarımcının sorumluluğundadır.  
  
         Aşağıdaki kod örneği, bir talep türüyle bir özel talep oluşturur `http://example.org/claims/simplecustomclaim`, adlı bir kaynak için `Driver's License`ile <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> doğru.  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a>Basit olmayan veri türüne göre özel bir talep oluşturmak için  
  
1.  Talep türü, kaynak değeri ve sağa geçirerek özel beyan oluşturma <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> Oluşturucusu.  
  
    1.  Talep türü için benzersiz bir değer karar verin.  
  
         Talep türü benzersiz bir dize tanımlayıcısı değil. Talep türü için kullanılan dize tanımlayıcı benzersiz olduğundan emin olun özel talep tasarımcının sorumluluğundadır. Tarafından tanımlanan talep türleri listesini [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], bkz: <xref:System.IdentityModel.Claims.ClaimTypes> sınıfı.  
  
    2.  Seçin veya kaynak için serileştirilebilir bir basit olmayan türünü tanımlayın.  
  
         Bir kaynak bir nesnedir. Talep tarafından çeşitli noktalarında serileştirilir çünkü kaynak CLR türü seri hale getirilebilir, olmalıdır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. İlkel türler zaten seri hale getirilebilir.  
  
         Yeni bir tür tanımlandığında, uygulama <xref:System.Runtime.Serialization.DataContractAttribute> sınıfa. Ayrıca uygulama <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği talep bir parçası olarak serileştirilmesi gereken yeni türü tüm üyeleri.  
  
         Aşağıdaki kod örneğinde adlı bir özel kaynak türünü tanımlayan `MyResourceType`.  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)] 
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]        
  
    3.  Tarafından tanımlanan bir hak seçin [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] veya özel bir hak için benzersiz bir değer.  
  
         Bir hak benzersiz bir dize tanımlayıcısı değil. Tarafından tanımlanan haklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tanımlanan <xref:System.IdentityModel.Claims.Rights> sınıfı.  
  
         Hakkını kullanılan dize tanımlayıcı benzersiz olduğundan emin olun özel talep tasarımcının sorumluluğundadır.  
  
         Aşağıdaki kod örneği, bir talep türüyle bir özel talep oluşturur `http://example.org/claims/complexcustomclaim`, bir özel kaynak türü `MyResourceType`ile <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> doğru.  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)] 
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]     
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde ilkel kaynak türüne sahip bir özel talep ve bir özel talep basit olmayan kaynak türü ile nasıl oluşturulacağını gösterir.  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IdentityModel.Claims.Claim>  
 <xref:System.IdentityModel.Claims.Rights>  
 <xref:System.IdentityModel.Claims.ClaimTypes>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [Beyanlar ve yetkilendirmeyi kimlik modeliyle yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [Beyanlar ve yetkilendirmeyi kimlik modeliyle yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
