---
title: "Nasıl Yapılır: Güvenlik Bağlamını İnceleme"
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
- ServiceSecurityContext class
- WCF, security
- Claimset class
ms.assetid: 389b5a57-4175-4bc0-ada0-fc750d51149f
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 4d6852a3162b3a8666c711d455e72517a91c4477
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-examine-the-security-context"></a>Nasıl Yapılır: Güvenlik Bağlamını İnceleme
Programlama zaman [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Hizmetleri, hizmet güvenlik bağlamı, istemci kimlik bilgileri ve hizmeti ile kimlik doğrulaması için kullanılan talep ayrıntılarını belirlemenize olanak sağlar. Bu özellikleri kullanarak yapılır <xref:System.ServiceModel.ServiceSecurityContext> sınıfı.  
  
 Örneğin, kullanarak geçerli istemci kimliğini almak <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> veya <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> özelliği. İstemci anonim olup olmadığını belirlemek için <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> özelliği.  
  
 Hangi taleplerin istemci adına Taleplerde koleksiyonu üzerinden yineleme tarafından gerçekleştirilen belirleyebilirsiniz <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> özelliği.  
  
### <a name="to-get-the-current-security-context"></a>Geçerli güvenlik bağlamı almak için  
  
-   Statik özelliğe erişmek <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> geçerli güvenlik bağlamı alınamadı. Başvurusu geçerli bağlamdan özelliklerinden herhangi birini inceleyin.  
  
### <a name="to-determine-the-identity-of-the-caller"></a>Arayanın Kimliği belirlemek için  
  
1.  Değerini yazdırma <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> ve <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> özellikleri.  
  
### <a name="to-parse-the-claims-of-a-caller"></a>Çağıran talep ayrıştırılamıyor  
  
1.  Geçerli dönmek <xref:System.IdentityModel.Policy.AuthorizationContext> sınıfı. Kullanım <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> geçerli hizmet güvenlik bağlamı dönün ve sonra dönmek için özellik `AuthorizationContext` kullanarak <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> özelliği.  
  
2.  Koleksiyonu ayrıştırma <xref:System.IdentityModel.Claims.ClaimSet> tarafından döndürülen nesne <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> özelliği <xref:System.IdentityModel.Policy.AuthorizationContext> sınıfı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek değerleri yazdırır <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> ve <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> geçerli güvenlik bağlamı özelliklerini ve <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> özelliği, talebi kaynak değerini ve <xref:System.IdentityModel.Claims.Claim.Right%2A> geçerli güvenlik her bir talep özelliği bağlamı.  
  
 [!code-csharp[c_PrincipalPermissionAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#4)]
 [!code-vb[c_PrincipalPermissionAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#4)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Kod şu ad alanlarından kullanır:  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.IdentityModel.Policy>  
  
-   <xref:System.IdentityModel.Claims>  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hizmetleri Güvenli Hale Getirme](../../../docs/framework/wcf/securing-services.md)  
 [Kimlik Doğrulama ile Hizmet Kimliği](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
