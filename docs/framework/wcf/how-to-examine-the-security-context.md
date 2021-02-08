---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: güvenlik bağlamını Inceleme'
title: 'Nasıl yapılır: Güvenlik Bağlamını İnceleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ServiceSecurityContext class
- WCF, security
- Claimset class
ms.assetid: 389b5a57-4175-4bc0-ada0-fc750d51149f
ms.openlocfilehash: e82491a877cf1f741767c91d1e7c304ba7676e6c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779406"
---
# <a name="how-to-examine-the-security-context"></a>Nasıl yapılır: Güvenlik Bağlamını İnceleme

Windows Communication Foundation (WCF) Hizmetleri programlamada, hizmet güvenlik bağlamı, hizmette kimlik doğrulaması yapmak için kullanılan istemci kimlik bilgileri ve talepler hakkındaki ayrıntıları belirlemenizi sağlar. Bu, sınıfının özellikleri kullanılarak yapılır <xref:System.ServiceModel.ServiceSecurityContext> .  
  
 Örneğin, veya özelliğini kullanarak geçerli istemcinin kimliğini elde edebilirsiniz <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> . İstemcinin anonim olup olmadığını anlamak için <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> özelliğini kullanın.  
  
 Ayrıca, özelliğindeki talepler koleksiyonunda yineleme yaparak istemci adına hangi taleplerin yapıldığını da belirleyebilirsiniz <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> .  
  
### <a name="to-get-the-current-security-context"></a>Geçerli güvenlik bağlamını almak için  
  
- <xref:System.ServiceModel.ServiceSecurityContext.Current%2A>Geçerli güvenlik bağlamını almak için statik özelliğe erişin. Geçerli bağlamın özelliklerinden herhangi birini başvuruya göre inceleyin.  
  
### <a name="to-determine-the-identity-of-the-caller"></a>Arayanın kimliğini belirleme  
  
1. <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A>Ve özelliklerinin değerini yazdırın <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> .  
  
### <a name="to-parse-the-claims-of-a-caller"></a>Bir arayanın taleplerini ayrıştırmak için  
  
1. Geçerli sınıfı döndürün <xref:System.IdentityModel.Policy.AuthorizationContext> . <xref:System.ServiceModel.ServiceSecurityContext.Current%2A>Özelliğini kullanarak geçerli hizmet güvenlik bağlamını döndürün, sonra `AuthorizationContext` özelliğini kullanarak öğesini döndürün <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> .  
  
2. <xref:System.IdentityModel.Claims.ClaimSet>Sınıfının özelliği tarafından döndürülen nesne koleksiyonunu ayrıştırın <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> <xref:System.IdentityModel.Policy.AuthorizationContext> .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> geçerli güvenlik bağlamının ve <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> özelliğinin değerlerini, talebin kaynak değerini ve <xref:System.IdentityModel.Claims.Claim.Right%2A> geçerli güvenlik bağlamındaki her talebin özelliğini yazdırır.  
  
 [!code-csharp[c_PrincipalPermissionAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#4)]
 [!code-vb[c_PrincipalPermissionAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#4)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  

 Kod aşağıdaki ad alanlarını kullanır:  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.IdentityModel.Policy>  
  
- <xref:System.IdentityModel.Claims>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmetleri Güvenli Hale Getirme](securing-services.md)
- [Kimlik Doğrulama ile Hizmet Kimliği](./feature-details/service-identity-and-authentication.md)
