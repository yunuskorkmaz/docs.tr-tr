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
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 8ff6969095a49dcae8b1d59b5b0ab28a8af24274
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33499482"
---
# <a name="how-to-examine-the-security-context"></a><span data-ttu-id="68e83-102">Nasıl Yapılır: Güvenlik Bağlamını İnceleme</span><span class="sxs-lookup"><span data-stu-id="68e83-102">How to: Examine the Security Context</span></span>
<span data-ttu-id="68e83-103">Windows Communication Foundation (WCF) hizmetlerini programlama, hizmet güvenlik bağlamı, istemci kimlik bilgileri ve hizmeti ile kimlik doğrulaması için kullanılan talep ayrıntılarını belirlemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="68e83-103">When programming Windows Communication Foundation (WCF) services, the service security context enables you to determine details about the client credentials and claims used to authenticate with the service.</span></span> <span data-ttu-id="68e83-104">Bu özellikleri kullanarak yapılır <xref:System.ServiceModel.ServiceSecurityContext> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="68e83-104">This is done by using the properties of the <xref:System.ServiceModel.ServiceSecurityContext> class.</span></span>  
  
 <span data-ttu-id="68e83-105">Örneğin, kullanarak geçerli istemci kimliğini almak <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> veya <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="68e83-105">For example, you can retrieve the identity of the current client by using the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> or the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property.</span></span> <span data-ttu-id="68e83-106">İstemci anonim olup olmadığını belirlemek için <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="68e83-106">To determine whether the client is anonymous, use the <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> property.</span></span>  
  
 <span data-ttu-id="68e83-107">Hangi taleplerin istemci adına Taleplerde koleksiyonu üzerinden yineleme tarafından gerçekleştirilen belirleyebilirsiniz <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="68e83-107">You can also determine what claims are being made on behalf of the client by iterating through the collection of claims in the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
### <a name="to-get-the-current-security-context"></a><span data-ttu-id="68e83-108">Geçerli güvenlik bağlamı almak için</span><span class="sxs-lookup"><span data-stu-id="68e83-108">To get the current security context</span></span>  
  
-   <span data-ttu-id="68e83-109">Statik özelliğe erişmek <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> geçerli güvenlik bağlamı alınamadı.</span><span class="sxs-lookup"><span data-stu-id="68e83-109">Access the static property <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> to get the current security context.</span></span> <span data-ttu-id="68e83-110">Başvurusu geçerli bağlamdan özelliklerinden herhangi birini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="68e83-110">Examine any of the properties of the current context from the reference.</span></span>  
  
### <a name="to-determine-the-identity-of-the-caller"></a><span data-ttu-id="68e83-111">Arayanın Kimliği belirlemek için</span><span class="sxs-lookup"><span data-stu-id="68e83-111">To determine the identity of the caller</span></span>  
  
1.  <span data-ttu-id="68e83-112">Değerini yazdırma <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> ve <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="68e83-112">Print the value of the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> properties.</span></span>  
  
### <a name="to-parse-the-claims-of-a-caller"></a><span data-ttu-id="68e83-113">Çağıran talep ayrıştırılamıyor</span><span class="sxs-lookup"><span data-stu-id="68e83-113">To parse the claims of a caller</span></span>  
  
1.  <span data-ttu-id="68e83-114">Geçerli dönmek <xref:System.IdentityModel.Policy.AuthorizationContext> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="68e83-114">Return the current <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span> <span data-ttu-id="68e83-115">Kullanım <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> geçerli hizmet güvenlik bağlamı dönün ve sonra dönmek için özellik `AuthorizationContext` kullanarak <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="68e83-115">Use the <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> property to return the current service security context, then return the `AuthorizationContext` using the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
2.  <span data-ttu-id="68e83-116">Koleksiyonu ayrıştırma <xref:System.IdentityModel.Claims.ClaimSet> tarafından döndürülen nesne <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> özelliği <xref:System.IdentityModel.Policy.AuthorizationContext> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="68e83-116">Parse the collection of <xref:System.IdentityModel.Claims.ClaimSet> objects returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68e83-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="68e83-117">Example</span></span>  
 <span data-ttu-id="68e83-118">Aşağıdaki örnek değerleri yazdırır <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> ve <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> geçerli güvenlik bağlamı özelliklerini ve <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> özelliği, talebi kaynak değerini ve <xref:System.IdentityModel.Claims.Claim.Right%2A> geçerli güvenlik her bir talep özelliği bağlamı.</span><span class="sxs-lookup"><span data-stu-id="68e83-118">The following example prints the values of the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> properties of the current security context and the <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> property, the resource value of the claim, and the <xref:System.IdentityModel.Claims.Claim.Right%2A> property of every claim in the current security context.</span></span>  
  
 [!code-csharp[c_PrincipalPermissionAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#4)]
 [!code-vb[c_PrincipalPermissionAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="68e83-119">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="68e83-119">Compiling the Code</span></span>  
 <span data-ttu-id="68e83-120">Kod şu ad alanlarından kullanır:</span><span class="sxs-lookup"><span data-stu-id="68e83-120">The code uses the following namespaces:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.IdentityModel.Policy>  
  
-   <xref:System.IdentityModel.Claims>  
  
## <a name="see-also"></a><span data-ttu-id="68e83-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="68e83-121">See Also</span></span>  
 [<span data-ttu-id="68e83-122">Hizmetleri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="68e83-122">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 [<span data-ttu-id="68e83-123">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="68e83-123">Service Identity and Authentication</span></span>](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
