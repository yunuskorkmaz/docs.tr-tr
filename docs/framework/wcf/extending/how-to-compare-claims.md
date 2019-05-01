---
title: 'Nasıl yapılır: Talepleri Karşılaştırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], comparing
- claims [WCF]
ms.assetid: 0c4ec84d-53df-408f-8953-9bc437f56c28
ms.openlocfilehash: 932ad347730b35a936e040e116e5aa6af36cd3dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857773"
---
# <a name="how-to-compare-claims"></a><span data-ttu-id="9a89c-102">Nasıl yapılır: Talepleri Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="9a89c-102">How to: Compare Claims</span></span>
<span data-ttu-id="9a89c-103">Windows Communication Foundation (WCF) kimlik modeli altyapısı, yetkilendirme denetimi gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9a89c-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) is used to perform authorization checking.</span></span> <span data-ttu-id="9a89c-104">Bu nedenle, genel istenen eylemi gerçekleştirmek veya istenen kaynağa erişim için gerekli talep için talep yetkilendirme bağlamında karşılaştırılacak bir görevdir.</span><span class="sxs-lookup"><span data-stu-id="9a89c-104">As such, a common task is to compare claims in the authorization context to the claims required to perform the requested action or access the requested resource.</span></span> <span data-ttu-id="9a89c-105">Bu konu, yerleşik ve özel talep türleri dahil olmak üzere, talep Karşılaştırılacak açıklar.</span><span class="sxs-lookup"><span data-stu-id="9a89c-105">This topic describes how to compare claims, including built-in and custom claim types.</span></span> <span data-ttu-id="9a89c-106">Kimlik modeli altyapısı hakkında daha fazla bilgi için bkz. [yönetme beyanlar ve yetkilendirmeyi kimlik modeliyle](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span><span class="sxs-lookup"><span data-stu-id="9a89c-106">For more information about the Identity Model infrastructure, see [Managing Claims and Authorization with the Identity Model](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span></span>  
  
 <span data-ttu-id="9a89c-107">Bir talep (tür, sağa ve kaynak) eşit olup olmadığını görmek için başka bir talep aynı bölümlerinde karşı üç parçaları karşılaştırmak talep karşılaştırma gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9a89c-107">Claim comparison involves comparing the three parts of a claim (type, right, and resource) against the same parts in another claim to see if they are equal.</span></span> <span data-ttu-id="9a89c-108">Aşağıdaki örnekte bakın.</span><span class="sxs-lookup"><span data-stu-id="9a89c-108">See the following example.</span></span>  
  
 [!code-csharp[c_CustomClaimComparison#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#9)]
 [!code-vb[c_CustomClaimComparison#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#9)]  
  
 <span data-ttu-id="9a89c-109">Her iki talepler bir talep türüne sahip <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, sağ <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>ve bir kaynak dizesinin "kişi".</span><span class="sxs-lookup"><span data-stu-id="9a89c-109">Both claims have a claim type of <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, a right of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>, and a resource of the string "someone".</span></span> <span data-ttu-id="9a89c-110">Talepler, talep tüm üç bölümden eşit olarak eşit olur.</span><span class="sxs-lookup"><span data-stu-id="9a89c-110">As all three parts of the claim are equal, the claims themselves are equal.</span></span>  
  
 <span data-ttu-id="9a89c-111">Yerleşik talep türleri kullanılarak karşılaştırılır <xref:System.IdentityModel.Claims.Claim.Equals%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9a89c-111">The built-in claim types are compared using the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="9a89c-112">Talep özgü karşılaştırma kodu gerektiğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9a89c-112">Claim-specific comparison code is used where necessary.</span></span> <span data-ttu-id="9a89c-113">Örneğin, aşağıdaki iki kullanıcı asıl adı (UPN) talep verilen:</span><span class="sxs-lookup"><span data-stu-id="9a89c-113">For example, given the following two user principal name (UPN) claims:</span></span>  
  
 [!code-csharp[c_CustomClaimComparison#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#4)]
 [!code-vb[c_CustomClaimComparison#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#4)]  
  
 <span data-ttu-id="9a89c-114">Karşılaştırma kodu <xref:System.IdentityModel.Claims.Claim.Equals%2A> yöntemi döndürür `true`olduğunu varsayarak `example\someone` aynı etki alanı kullanıcısı olarak tanımlayan "someone@example.com".</span><span class="sxs-lookup"><span data-stu-id="9a89c-114">the comparison code in the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method returns `true`, assuming `example\someone` identifies the same domain user as "someone@example.com".</span></span>  
  
 <span data-ttu-id="9a89c-115">Özel talep türleri de karşılaştırılabilir kullanarak <xref:System.IdentityModel.Claims.Claim.Equals%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9a89c-115">Custom claim types can also be compared using the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="9a89c-116">Bununla birlikte, burada tarafından döndürülen tür durumlarda <xref:System.IdentityModel.Claims.Claim.Resource%2A> talep özelliği bir temel türü dışında bir şey olduğunda <xref:System.IdentityModel.Claims.Claim.Equals%2A> döndürür `true` tarafından döndürülen değerlerin yalnızca, `Resource` özellikleri göreeşit<xref:System.IdentityModel.Claims.Claim.Equals%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9a89c-116">However, in cases where the type returned by the <xref:System.IdentityModel.Claims.Claim.Resource%2A> property of the claim is something other than a primitive type, the <xref:System.IdentityModel.Claims.Claim.Equals%2A> returns `true` only if the values returned by the `Resource` properties are equal according to the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="9a89c-117">Burada bu uygun olmaması durumunda, özel bir tür tarafından döndürülen `Resource` özelliği geçersiz kılmalıdır <xref:System.IdentityModel.Claims.Claim.Equals%2A> ve <xref:System.Object.GetHashCode%2A> özel işlemleri gereklidir gerçekleştirmek için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="9a89c-117">In cases where this is not appropriate, the custom type returned by the `Resource` property should override the <xref:System.IdentityModel.Claims.Claim.Equals%2A> and <xref:System.Object.GetHashCode%2A> methods to perform whatever custom processing is necessary.</span></span>  
  
### <a name="comparing-built-in-claims"></a><span data-ttu-id="9a89c-118">Yerleşik talepleri karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="9a89c-118">Comparing built-in claims</span></span>  
  
1. <span data-ttu-id="9a89c-119">Verilen iki örneğini <xref:System.IdentityModel.Claims.Claim> sınıfı, kullanın <xref:System.IdentityModel.Claims.Claim.Equals%2A> aşağıdaki kodda gösterildiği gibi karşılaştırma yapmak.</span><span class="sxs-lookup"><span data-stu-id="9a89c-119">Given two instances of the <xref:System.IdentityModel.Claims.Claim> class, use the <xref:System.IdentityModel.Claims.Claim.Equals%2A> to make the comparison, as shown in the following code.</span></span>  
  
     [!code-csharp[c_CustomClaimComparison#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#5)]
     [!code-vb[c_CustomClaimComparison#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#5)]  
  
### <a name="comparing-custom-claims-with-primitive-resource-types"></a><span data-ttu-id="9a89c-120">Özel talepler temel kaynak türleri ile karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="9a89c-120">Comparing custom claims with primitive resource types</span></span>  
  
1. <span data-ttu-id="9a89c-121">Temel kaynak türleri ile özel talepler için karşılaştırma yerleşik talepler olduğu gibi aşağıdaki kodda gösterildiği şekilde gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="9a89c-121">For custom claims with primitive resource types, comparison can be performed as for built-in claims, as shown in the following code.</span></span>  
  
     [!code-csharp[c_CustomClaimComparison#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#6)]
     [!code-vb[c_CustomClaimComparison#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#6)]  
  
2. <span data-ttu-id="9a89c-122">Özel talepler yapısı veya temel sınıf kaynak türleri, kaynak türü'ı geçersiz kılmalıdır için <xref:System.IdentityModel.Claims.Claim.Equals%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9a89c-122">For custom claims with structure or class based resource types, the resource type should override the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span>  
  
3. <span data-ttu-id="9a89c-123">İlk denetleyin olmadığını `obj` parametresi `null`ve bu durumda, dönüş `false`.</span><span class="sxs-lookup"><span data-stu-id="9a89c-123">First check whether the `obj` parameter is `null`, and if so, return `false`.</span></span>  
  
     [!code-csharp[c_CustomClaimComparison#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#7)]
     [!code-vb[c_CustomClaimComparison#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#7)]  
  
4. <span data-ttu-id="9a89c-124">Sonraki çağrı <xref:System.Object.ReferenceEquals%2A> ve `this` ve `obj` parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="9a89c-124">Next call <xref:System.Object.ReferenceEquals%2A> and pass `this` and `obj` as parameters.</span></span> <span data-ttu-id="9a89c-125">Döndürürse `true`, ardından dönüş `true`.</span><span class="sxs-lookup"><span data-stu-id="9a89c-125">If it returns `true`, then return `true`.</span></span>  
  
     [!code-csharp[c_CustomClaimComparison#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#8)]
     [!code-vb[c_CustomClaimComparison#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#8)]  
  
5. <span data-ttu-id="9a89c-126">Sonraki deneme atamak `obj` sınıf türünün yerel bir değişkene.</span><span class="sxs-lookup"><span data-stu-id="9a89c-126">Next attempt to assign `obj` to a local variable of the class type.</span></span> <span data-ttu-id="9a89c-127">Bu başarısız olursa, başvurudur `null`.</span><span class="sxs-lookup"><span data-stu-id="9a89c-127">If this fails, the reference is `null`.</span></span> <span data-ttu-id="9a89c-128">Bu gibi durumlarda, iade `false`.</span><span class="sxs-lookup"><span data-stu-id="9a89c-128">In such cases, return `false`.</span></span>  
  
6. <span data-ttu-id="9a89c-129">Sağlanan talep geçerli talep doğru karşılaştırma için gereken özel bir karşılaştırma yapar.</span><span class="sxs-lookup"><span data-stu-id="9a89c-129">Perform the custom comparison necessary to correctly compare the current claim to the provided claim.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a89c-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="9a89c-130">Example</span></span>  
 <span data-ttu-id="9a89c-131">Aşağıdaki örnek, talep kaynak ilkel olmayan türü olduğu bir özel talep karşılaştırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a89c-131">The following example shows a comparison of custom claims where the claim resource is a non-primitive type.</span></span>  
  
 [!code-csharp[c_CustomClaimComparison#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#0)]
 [!code-vb[c_CustomClaimComparison#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="9a89c-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a89c-132">See also</span></span>

- [<span data-ttu-id="9a89c-133">Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme</span><span class="sxs-lookup"><span data-stu-id="9a89c-133">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [<span data-ttu-id="9a89c-134">Nasıl yapılır: Özel talep oluşturma</span><span class="sxs-lookup"><span data-stu-id="9a89c-134">How to: Create a Custom Claim</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
