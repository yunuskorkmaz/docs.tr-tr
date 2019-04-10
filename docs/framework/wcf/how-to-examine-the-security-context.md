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
ms.openlocfilehash: 063d9e334575170c632eb49aef527b14a6d164b2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207116"
---
# <a name="how-to-examine-the-security-context"></a><span data-ttu-id="da605-102">Nasıl yapılır: Güvenlik Bağlamını İnceleme</span><span class="sxs-lookup"><span data-stu-id="da605-102">How to: Examine the Security Context</span></span>
<span data-ttu-id="da605-103">Windows Communication Foundation (WCF) hizmetlerini programlama, hizmet güvenlik bağlamı hizmeti ile kimlik doğrulaması için kullanılan talep ve istemci kimlik bilgileri hakkındaki ayrıntıları belirlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="da605-103">When programming Windows Communication Foundation (WCF) services, the service security context enables you to determine details about the client credentials and claims used to authenticate with the service.</span></span> <span data-ttu-id="da605-104">Bu özellikleri kullanılarak yapılır <xref:System.ServiceModel.ServiceSecurityContext> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="da605-104">This is done by using the properties of the <xref:System.ServiceModel.ServiceSecurityContext> class.</span></span>  
  
 <span data-ttu-id="da605-105">Kullanarak geçerli istemci kimliğini gibi alabilirsiniz <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> veya <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="da605-105">For example, you can retrieve the identity of the current client by using the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> or the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property.</span></span> <span data-ttu-id="da605-106">İstemci anonim olup olmadığını belirlemek için <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="da605-106">To determine whether the client is anonymous, use the <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> property.</span></span>  
  
 <span data-ttu-id="da605-107">Taleplerde koleksiyonu ile Yinelem yaparak istemci adına hangi talepleri yapılmıştır belirleyebilirsiniz <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="da605-107">You can also determine what claims are being made on behalf of the client by iterating through the collection of claims in the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
### <a name="to-get-the-current-security-context"></a><span data-ttu-id="da605-108">Geçerli güvenlik bağlamı almak için</span><span class="sxs-lookup"><span data-stu-id="da605-108">To get the current security context</span></span>  
  
-   <span data-ttu-id="da605-109">Statik özellik erişim <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> geçerli güvenlik bağlamı alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="da605-109">Access the static property <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> to get the current security context.</span></span> <span data-ttu-id="da605-110">Geçerli bağlamın iş başvurusundan özelliklerinden herhangi birini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="da605-110">Examine any of the properties of the current context from the reference.</span></span>  
  
### <a name="to-determine-the-identity-of-the-caller"></a><span data-ttu-id="da605-111">Arayan kimliğini belirlemek için</span><span class="sxs-lookup"><span data-stu-id="da605-111">To determine the identity of the caller</span></span>  
  
1.  <span data-ttu-id="da605-112">Değerini yazdırmak <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> ve <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="da605-112">Print the value of the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> properties.</span></span>  
  
### <a name="to-parse-the-claims-of-a-caller"></a><span data-ttu-id="da605-113">Çağıran talepleri ayrıştırılamıyor</span><span class="sxs-lookup"><span data-stu-id="da605-113">To parse the claims of a caller</span></span>  
  
1.  <span data-ttu-id="da605-114">Geçerli dönüş <xref:System.IdentityModel.Policy.AuthorizationContext> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="da605-114">Return the current <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span> <span data-ttu-id="da605-115">Kullanım <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> geçerli hizmet güvenlik bağlamı döndürür ve döndürmek için özellik `AuthorizationContext` kullanarak <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="da605-115">Use the <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> property to return the current service security context, then return the `AuthorizationContext` using the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
2.  <span data-ttu-id="da605-116">Koleksiyonu ayrıştırma <xref:System.IdentityModel.Claims.ClaimSet> tarafından döndürülen nesne <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> özelliği <xref:System.IdentityModel.Policy.AuthorizationContext> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="da605-116">Parse the collection of <xref:System.IdentityModel.Claims.ClaimSet> objects returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da605-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="da605-117">Example</span></span>  
 <span data-ttu-id="da605-118">Aşağıdaki örnek değerlerini yazdırır <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> ve <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> geçerli güvenlik bağlamı özelliklerini ve <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> özelliği, talep kaynak değerini ve <xref:System.IdentityModel.Claims.Claim.Right%2A> geçerli güvenlik her talep özelliği bağlamı.</span><span class="sxs-lookup"><span data-stu-id="da605-118">The following example prints the values of the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> properties of the current security context and the <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> property, the resource value of the claim, and the <xref:System.IdentityModel.Claims.Claim.Right%2A> property of every claim in the current security context.</span></span>  
  
 [!code-csharp[c_PrincipalPermissionAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#4)]
 [!code-vb[c_PrincipalPermissionAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="da605-119">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="da605-119">Compiling the Code</span></span>  
 <span data-ttu-id="da605-120">Aşağıdaki ad kodunu kullanır:</span><span class="sxs-lookup"><span data-stu-id="da605-120">The code uses the following namespaces:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.IdentityModel.Policy>  
  
-   <xref:System.IdentityModel.Claims>  
  
## <a name="see-also"></a><span data-ttu-id="da605-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da605-121">See also</span></span>

- [<span data-ttu-id="da605-122">Hizmetleri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="da605-122">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)
- [<span data-ttu-id="da605-123">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="da605-123">Service Identity and Authentication</span></span>](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
