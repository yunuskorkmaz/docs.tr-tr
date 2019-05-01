---
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
ms.openlocfilehash: c6c36641463a45b79d437ae3910bbe7474d425cb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61929304"
---
# <a name="how-to-examine-the-security-context"></a>Nasıl yapılır: Güvenlik Bağlamını İnceleme
Windows Communication Foundation (WCF) hizmetlerini programlama, hizmet güvenlik bağlamı hizmeti ile kimlik doğrulaması için kullanılan talep ve istemci kimlik bilgileri hakkındaki ayrıntıları belirlemenizi sağlar. Bu özellikleri kullanılarak yapılır <xref:System.ServiceModel.ServiceSecurityContext> sınıfı.  
  
 Kullanarak geçerli istemci kimliğini gibi alabilirsiniz <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> veya <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> özelliği. İstemci anonim olup olmadığını belirlemek için <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> özelliği.  
  
 Taleplerde koleksiyonu ile Yinelem yaparak istemci adına hangi talepleri yapılmıştır belirleyebilirsiniz <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> özelliği.  
  
### <a name="to-get-the-current-security-context"></a>Geçerli güvenlik bağlamı almak için  
  
- Statik özellik erişim <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> geçerli güvenlik bağlamı alınamıyor. Geçerli bağlamın iş başvurusundan özelliklerinden herhangi birini inceleyin.  
  
### <a name="to-determine-the-identity-of-the-caller"></a>Arayan kimliğini belirlemek için  
  
1. Değerini yazdırmak <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> ve <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> özellikleri.  
  
### <a name="to-parse-the-claims-of-a-caller"></a>Çağıran talepleri ayrıştırılamıyor  
  
1. Geçerli dönüş <xref:System.IdentityModel.Policy.AuthorizationContext> sınıfı. Kullanım <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> geçerli hizmet güvenlik bağlamı döndürür ve döndürmek için özellik `AuthorizationContext` kullanarak <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> özelliği.  
  
2. Koleksiyonu ayrıştırma <xref:System.IdentityModel.Claims.ClaimSet> tarafından döndürülen nesne <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> özelliği <xref:System.IdentityModel.Policy.AuthorizationContext> sınıfı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek değerlerini yazdırır <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> ve <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> geçerli güvenlik bağlamı özelliklerini ve <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> özelliği, talep kaynak değerini ve <xref:System.IdentityModel.Claims.Claim.Right%2A> geçerli güvenlik her talep özelliği bağlamı.  
  
 [!code-csharp[c_PrincipalPermissionAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#4)]
 [!code-vb[c_PrincipalPermissionAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#4)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Aşağıdaki ad kodunu kullanır:  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.IdentityModel.Policy>  
  
- <xref:System.IdentityModel.Claims>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmetleri Güvenli Hale Getirme](../../../docs/framework/wcf/securing-services.md)
- [Kimlik Doğrulama ile Hizmet Kimliği](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
