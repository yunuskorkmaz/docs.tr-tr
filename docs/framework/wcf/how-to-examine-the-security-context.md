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
# <a name="how-to-examine-the-security-context"></a><span data-ttu-id="b673e-102">Nasıl Yapılır: Güvenlik Bağlamını İnceleme</span><span class="sxs-lookup"><span data-stu-id="b673e-102">How to: Examine the Security Context</span></span>
<span data-ttu-id="b673e-103">Windows Communication Foundation (WCF) Hizmetleri programlamada, hizmet güvenlik bağlamı, hizmette kimlik doğrulaması yapmak için kullanılan istemci kimlik bilgileri ve talepler hakkındaki ayrıntıları belirlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b673e-103">When programming Windows Communication Foundation (WCF) services, the service security context enables you to determine details about the client credentials and claims used to authenticate with the service.</span></span> <span data-ttu-id="b673e-104">Bu, <xref:System.ServiceModel.ServiceSecurityContext> sınıfının özellikleri kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="b673e-104">This is done by using the properties of the <xref:System.ServiceModel.ServiceSecurityContext> class.</span></span>  
  
 <span data-ttu-id="b673e-105">Örneğin, <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> veya <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> özelliğini kullanarak geçerli istemcinin kimliğini alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b673e-105">For example, you can retrieve the identity of the current client by using the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> or the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property.</span></span> <span data-ttu-id="b673e-106">İstemcinin anonim olup olmadığını anlamak için <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b673e-106">To determine whether the client is anonymous, use the <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> property.</span></span>  
  
 <span data-ttu-id="b673e-107">Ayrıca, <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> özelliğindeki talepler koleksiyonunda yineleme yaparak istemci adına hangi taleplerin yapıldığını da belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b673e-107">You can also determine what claims are being made on behalf of the client by iterating through the collection of claims in the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
### <a name="to-get-the-current-security-context"></a><span data-ttu-id="b673e-108">Geçerli güvenlik bağlamını almak için</span><span class="sxs-lookup"><span data-stu-id="b673e-108">To get the current security context</span></span>  
  
- <span data-ttu-id="b673e-109">Geçerli güvenlik bağlamını almak için <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> statik özelliğine erişin.</span><span class="sxs-lookup"><span data-stu-id="b673e-109">Access the static property <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> to get the current security context.</span></span> <span data-ttu-id="b673e-110">Geçerli bağlamın özelliklerinden herhangi birini başvuruya göre inceleyin.</span><span class="sxs-lookup"><span data-stu-id="b673e-110">Examine any of the properties of the current context from the reference.</span></span>  
  
### <a name="to-determine-the-identity-of-the-caller"></a><span data-ttu-id="b673e-111">Arayanın kimliğini belirleme</span><span class="sxs-lookup"><span data-stu-id="b673e-111">To determine the identity of the caller</span></span>  
  
1. <span data-ttu-id="b673e-112">@No__t-0 ve <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> özelliklerinin değerini yazdırın.</span><span class="sxs-lookup"><span data-stu-id="b673e-112">Print the value of the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> properties.</span></span>  
  
### <a name="to-parse-the-claims-of-a-caller"></a><span data-ttu-id="b673e-113">Bir arayanın taleplerini ayrıştırmak için</span><span class="sxs-lookup"><span data-stu-id="b673e-113">To parse the claims of a caller</span></span>  
  
1. <span data-ttu-id="b673e-114">Geçerli <xref:System.IdentityModel.Policy.AuthorizationContext> sınıfını döndürün.</span><span class="sxs-lookup"><span data-stu-id="b673e-114">Return the current <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span> <span data-ttu-id="b673e-115">Geçerli hizmet güvenlik bağlamını döndürmek için <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> özelliğini kullanın, ardından <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> özelliğini kullanarak `AuthorizationContext` ' i döndürün.</span><span class="sxs-lookup"><span data-stu-id="b673e-115">Use the <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> property to return the current service security context, then return the `AuthorizationContext` using the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
2. <span data-ttu-id="b673e-116">@No__t-2 sınıfının <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> özelliği tarafından döndürülen <xref:System.IdentityModel.Claims.ClaimSet> nesnelerinin koleksiyonunu ayrıştırın.</span><span class="sxs-lookup"><span data-stu-id="b673e-116">Parse the collection of <xref:System.IdentityModel.Claims.ClaimSet> objects returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b673e-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="b673e-117">Example</span></span>  
 <span data-ttu-id="b673e-118">Aşağıdaki örnek geçerli güvenlik bağlamının <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> ve <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> özelliklerinin ve <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> özelliğinin, talebin kaynak değerinin ve geçerli güvenlik bağlamındaki her talebin <xref:System.IdentityModel.Claims.Claim.Right%2A> özelliğinin değerlerini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="b673e-118">The following example prints the values of the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> properties of the current security context and the <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> property, the resource value of the claim, and the <xref:System.IdentityModel.Claims.Claim.Right%2A> property of every claim in the current security context.</span></span>  
  
 [!code-csharp[c_PrincipalPermissionAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#4)]
 [!code-vb[c_PrincipalPermissionAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b673e-119">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="b673e-119">Compiling the Code</span></span>  
 <span data-ttu-id="b673e-120">Kod aşağıdaki ad alanlarını kullanır:</span><span class="sxs-lookup"><span data-stu-id="b673e-120">The code uses the following namespaces:</span></span>  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.IdentityModel.Policy>  
  
- <xref:System.IdentityModel.Claims>  
  
## <a name="see-also"></a><span data-ttu-id="b673e-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b673e-121">See also</span></span>

- [<span data-ttu-id="b673e-122">Hizmetleri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="b673e-122">Securing Services</span></span>](securing-services.md)
- [<span data-ttu-id="b673e-123">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="b673e-123">Service Identity and Authentication</span></span>](./feature-details/service-identity-and-authentication.md)
