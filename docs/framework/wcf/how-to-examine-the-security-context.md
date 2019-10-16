---
title: 'Nasıl Yapılır: Güvenlik Bağlamını İnceleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ServiceSecurityContext class
- WCF, security
- Claimset class
ms.assetid: 389b5a57-4175-4bc0-ada0-fc750d51149f
ms.openlocfilehash: 328d47a583a4f047fd54589a82d339de2cb1a16f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320986"
---
# <a name="how-to-examine-the-security-context"></a>Nasıl Yapılır: Güvenlik Bağlamını İnceleme
Windows Communication Foundation (WCF) Hizmetleri programlamada, hizmet güvenlik bağlamı, hizmette kimlik doğrulaması yapmak için kullanılan istemci kimlik bilgileri ve talepler hakkındaki ayrıntıları belirlemenizi sağlar. Bu, <xref:System.ServiceModel.ServiceSecurityContext> sınıfının özellikleri kullanılarak yapılır.  
  
 Örneğin, <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> veya <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> özelliğini kullanarak geçerli istemcinin kimliğini alabilirsiniz. İstemcinin anonim olup olmadığını anlamak için <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> özelliğini kullanın.  
  
 Ayrıca, <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> özelliğindeki talepler koleksiyonunda yineleme yaparak istemci adına hangi taleplerin yapıldığını da belirleyebilirsiniz.  
  
### <a name="to-get-the-current-security-context"></a>Geçerli güvenlik bağlamını almak için  
  
- Geçerli güvenlik bağlamını almak için <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> statik özelliğine erişin. Geçerli bağlamın özelliklerinden herhangi birini başvuruya göre inceleyin.  
  
### <a name="to-determine-the-identity-of-the-caller"></a>Arayanın kimliğini belirleme  
  
1. @No__t-0 ve <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> özelliklerinin değerini yazdırın.  
  
### <a name="to-parse-the-claims-of-a-caller"></a>Bir arayanın taleplerini ayrıştırmak için  
  
1. Geçerli <xref:System.IdentityModel.Policy.AuthorizationContext> sınıfını döndürün. Geçerli hizmet güvenlik bağlamını döndürmek için <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> özelliğini kullanın, ardından <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> özelliğini kullanarak `AuthorizationContext` ' i döndürün.  
  
2. @No__t-2 sınıfının <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> özelliği tarafından döndürülen <xref:System.IdentityModel.Claims.ClaimSet> nesnelerinin koleksiyonunu ayrıştırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek geçerli güvenlik bağlamının <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> ve <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> özelliklerinin ve <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> özelliğinin, talebin kaynak değerinin ve geçerli güvenlik bağlamındaki her talebin <xref:System.IdentityModel.Claims.Claim.Right%2A> özelliğinin değerlerini yazdırır.  
  
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
