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
ms.openlocfilehash: 40950614892ddfd4eb24194f0389e057a5a13378
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272950"
---
# <a name="how-to-examine-the-security-context"></a><span data-ttu-id="bdb1b-102">Nasıl yapılır: Güvenlik Bağlamını İnceleme</span><span class="sxs-lookup"><span data-stu-id="bdb1b-102">How to: Examine the Security Context</span></span>

<span data-ttu-id="bdb1b-103">Windows Communication Foundation (WCF) Hizmetleri programlamada, hizmet güvenlik bağlamı, hizmette kimlik doğrulaması yapmak için kullanılan istemci kimlik bilgileri ve talepler hakkındaki ayrıntıları belirlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="bdb1b-103">When programming Windows Communication Foundation (WCF) services, the service security context enables you to determine details about the client credentials and claims used to authenticate with the service.</span></span> <span data-ttu-id="bdb1b-104">Bu, sınıfının özellikleri kullanılarak yapılır <xref:System.ServiceModel.ServiceSecurityContext> .</span><span class="sxs-lookup"><span data-stu-id="bdb1b-104">This is done by using the properties of the <xref:System.ServiceModel.ServiceSecurityContext> class.</span></span>  
  
 <span data-ttu-id="bdb1b-105">Örneğin, veya özelliğini kullanarak geçerli istemcinin kimliğini elde edebilirsiniz <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> .</span><span class="sxs-lookup"><span data-stu-id="bdb1b-105">For example, you can retrieve the identity of the current client by using the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> or the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property.</span></span> <span data-ttu-id="bdb1b-106">İstemcinin anonim olup olmadığını anlamak için <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="bdb1b-106">To determine whether the client is anonymous, use the <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> property.</span></span>  
  
 <span data-ttu-id="bdb1b-107">Ayrıca, özelliğindeki talepler koleksiyonunda yineleme yaparak istemci adına hangi taleplerin yapıldığını da belirleyebilirsiniz <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> .</span><span class="sxs-lookup"><span data-stu-id="bdb1b-107">You can also determine what claims are being made on behalf of the client by iterating through the collection of claims in the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
### <a name="to-get-the-current-security-context"></a><span data-ttu-id="bdb1b-108">Geçerli güvenlik bağlamını almak için</span><span class="sxs-lookup"><span data-stu-id="bdb1b-108">To get the current security context</span></span>  
  
- <span data-ttu-id="bdb1b-109"><xref:System.ServiceModel.ServiceSecurityContext.Current%2A>Geçerli güvenlik bağlamını almak için statik özelliğe erişin.</span><span class="sxs-lookup"><span data-stu-id="bdb1b-109">Access the static property <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> to get the current security context.</span></span> <span data-ttu-id="bdb1b-110">Geçerli bağlamın özelliklerinden herhangi birini başvuruya göre inceleyin.</span><span class="sxs-lookup"><span data-stu-id="bdb1b-110">Examine any of the properties of the current context from the reference.</span></span>  
  
### <a name="to-determine-the-identity-of-the-caller"></a><span data-ttu-id="bdb1b-111">Arayanın kimliğini belirleme</span><span class="sxs-lookup"><span data-stu-id="bdb1b-111">To determine the identity of the caller</span></span>  
  
1. <span data-ttu-id="bdb1b-112"><xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A>Ve özelliklerinin değerini yazdırın <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> .</span><span class="sxs-lookup"><span data-stu-id="bdb1b-112">Print the value of the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> properties.</span></span>  
  
### <a name="to-parse-the-claims-of-a-caller"></a><span data-ttu-id="bdb1b-113">Bir arayanın taleplerini ayrıştırmak için</span><span class="sxs-lookup"><span data-stu-id="bdb1b-113">To parse the claims of a caller</span></span>  
  
1. <span data-ttu-id="bdb1b-114">Geçerli sınıfı döndürün <xref:System.IdentityModel.Policy.AuthorizationContext> .</span><span class="sxs-lookup"><span data-stu-id="bdb1b-114">Return the current <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span> <span data-ttu-id="bdb1b-115"><xref:System.ServiceModel.ServiceSecurityContext.Current%2A>Özelliğini kullanarak geçerli hizmet güvenlik bağlamını döndürün, sonra `AuthorizationContext` özelliğini kullanarak öğesini döndürün <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> .</span><span class="sxs-lookup"><span data-stu-id="bdb1b-115">Use the <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> property to return the current service security context, then return the `AuthorizationContext` using the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
2. <span data-ttu-id="bdb1b-116"><xref:System.IdentityModel.Claims.ClaimSet>Sınıfının özelliği tarafından döndürülen nesne koleksiyonunu ayrıştırın <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> <xref:System.IdentityModel.Policy.AuthorizationContext> .</span><span class="sxs-lookup"><span data-stu-id="bdb1b-116">Parse the collection of <xref:System.IdentityModel.Claims.ClaimSet> objects returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdb1b-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="bdb1b-117">Example</span></span>  

 <span data-ttu-id="bdb1b-118">Aşağıdaki örnek, <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> geçerli güvenlik bağlamının ve <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> özelliğinin değerlerini, talebin kaynak değerini ve <xref:System.IdentityModel.Claims.Claim.Right%2A> geçerli güvenlik bağlamındaki her talebin özelliğini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="bdb1b-118">The following example prints the values of the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> properties of the current security context and the <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> property, the resource value of the claim, and the <xref:System.IdentityModel.Claims.Claim.Right%2A> property of every claim in the current security context.</span></span>  
  
 [!code-csharp[c_PrincipalPermissionAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#4)]
 [!code-vb[c_PrincipalPermissionAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bdb1b-119">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="bdb1b-119">Compiling the Code</span></span>  

 <span data-ttu-id="bdb1b-120">Kod aşağıdaki ad alanlarını kullanır:</span><span class="sxs-lookup"><span data-stu-id="bdb1b-120">The code uses the following namespaces:</span></span>  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.IdentityModel.Policy>  
  
- <xref:System.IdentityModel.Claims>  
  
## <a name="see-also"></a><span data-ttu-id="bdb1b-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bdb1b-121">See also</span></span>

- [<span data-ttu-id="bdb1b-122">Hizmetleri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="bdb1b-122">Securing Services</span></span>](securing-services.md)
- [<span data-ttu-id="bdb1b-123">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="bdb1b-123">Service Identity and Authentication</span></span>](./feature-details/service-identity-and-authentication.md)
