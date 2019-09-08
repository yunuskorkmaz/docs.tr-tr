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
ms.openlocfilehash: 29254bd661e72b926b21695ccb646480c53b5475
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797103"
---
# <a name="how-to-compare-claims"></a><span data-ttu-id="1a140-102">Nasıl yapılır: Talepleri Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="1a140-102">How to: Compare Claims</span></span>

<span data-ttu-id="1a140-103">Windows Communication Foundation (WCF) içindeki kimlik modeli altyapısı, yetkilendirme denetimi gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1a140-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) is used to perform authorization checking.</span></span> <span data-ttu-id="1a140-104">Bu nedenle, ortak bir görev, yetkilendirme bağlamındaki talepleri, istenen eylemi gerçekleştirmek veya istenen kaynağa erişmek için gereken taleplerle karşılaştırmaktır.</span><span class="sxs-lookup"><span data-stu-id="1a140-104">As such, a common task is to compare claims in the authorization context to the claims required to perform the requested action or access the requested resource.</span></span> <span data-ttu-id="1a140-105">Bu konuda, yerleşik ve özel talep türleri dahil olmak üzere taleplerin nasıl karşılaştırılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1a140-105">This topic describes how to compare claims, including built-in and custom claim types.</span></span> <span data-ttu-id="1a140-106">Kimlik modeli altyapısı hakkında daha fazla bilgi için bkz. [kimlik modeliyle talepleri ve Yetkilendirmeyi Yönetme](../feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span><span class="sxs-lookup"><span data-stu-id="1a140-106">For more information about the Identity Model infrastructure, see [Managing Claims and Authorization with the Identity Model](../feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span></span>

<span data-ttu-id="1a140-107">Talep karşılaştırması, bir talebin (tür, sağ ve kaynak) üç parçasını başka bir talepteki aynı bölümlere göre karşılaştırarak eşit olup olmadığını görmenizi içerir.</span><span class="sxs-lookup"><span data-stu-id="1a140-107">Claim comparison involves comparing the three parts of a claim (type, right, and resource) against the same parts in another claim to see if they are equal.</span></span> <span data-ttu-id="1a140-108">Aşağıdaki örnekte bakın.</span><span class="sxs-lookup"><span data-stu-id="1a140-108">See the following example.</span></span>

[!code-csharp[c_CustomClaimComparison#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#9)]
[!code-vb[c_CustomClaimComparison#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#9)]

<span data-ttu-id="1a140-109">Her iki talep da bir talep türüne <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>sağına ve "birisi" dizesinin bir kaynağına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1a140-109">Both claims have a claim type of <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, a right of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>, and a resource of the string "someone".</span></span> <span data-ttu-id="1a140-110">Talebin her üç bölümü de eşitse, talepler eşittir.</span><span class="sxs-lookup"><span data-stu-id="1a140-110">As all three parts of the claim are equal, the claims themselves are equal.</span></span>

<span data-ttu-id="1a140-111">Yerleşik talep türleri, <xref:System.IdentityModel.Claims.Claim.Equals%2A> yöntemi kullanılarak karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="1a140-111">The built-in claim types are compared using the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="1a140-112">Gerektiğinde talebe özgü karşılaştırma kodu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1a140-112">Claim-specific comparison code is used where necessary.</span></span> <span data-ttu-id="1a140-113">Örneğin, aşağıdaki iki Kullanıcı asıl adı (UPN) talebi verildiğinde:</span><span class="sxs-lookup"><span data-stu-id="1a140-113">For example, given the following two user principal name (UPN) claims:</span></span>

[!code-csharp[c_CustomClaimComparison#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#4)]
[!code-vb[c_CustomClaimComparison#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#4)]

<span data-ttu-id="1a140-114"><xref:System.IdentityModel.Claims.Claim.Equals%2A> `example\someone` yöntemdeki karşılaştırma kodu, aynı etki alanı kullanıcısını "someone@example.com" ile tanımlar ,kabuledilir.`true`</span><span class="sxs-lookup"><span data-stu-id="1a140-114">the comparison code in the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method returns `true`, assuming `example\someone` identifies the same domain user as "someone@example.com".</span></span>

<span data-ttu-id="1a140-115">Özel talep türleri, <xref:System.IdentityModel.Claims.Claim.Equals%2A> yöntemi kullanılarak da karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="1a140-115">Custom claim types can also be compared using the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="1a140-116">Ancak, talebin <xref:System.IdentityModel.Claims.Claim.Resource%2A> özelliği tarafından döndürülen türün ilkel bir tür <xref:System.IdentityModel.Claims.Claim.Equals%2A> dışında bir şey olduğu durumlarda, yalnızca `Resource` Özellikler tarafından döndürülen değerler şuna göre `true` eşitse,döndürür.<xref:System.IdentityModel.Claims.Claim.Equals%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1a140-116">However, in cases where the type returned by the <xref:System.IdentityModel.Claims.Claim.Resource%2A> property of the claim is something other than a primitive type, the <xref:System.IdentityModel.Claims.Claim.Equals%2A> returns `true` only if the values returned by the `Resource` properties are equal according to the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="1a140-117">Bunun uygun olmadığı durumlarda, `Resource` özelliği tarafından döndürülen özel tür, <xref:System.IdentityModel.Claims.Claim.Equals%2A> gerekli tüm özel işlemleri gerçekleştirmek için ve <xref:System.Object.GetHashCode%2A> yöntemlerini geçersiz kılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1a140-117">In cases where this is not appropriate, the custom type returned by the `Resource` property should override the <xref:System.IdentityModel.Claims.Claim.Equals%2A> and <xref:System.Object.GetHashCode%2A> methods to perform whatever custom processing is necessary.</span></span>

## <a name="comparing-built-in-claims"></a><span data-ttu-id="1a140-118">Yerleşik talepler karşılaştırılıyor</span><span class="sxs-lookup"><span data-stu-id="1a140-118">Comparing built-in claims</span></span>

1. <span data-ttu-id="1a140-119"><xref:System.IdentityModel.Claims.Claim> Sınıfının iki örneği verildiğinde, aşağıdaki kodda gösterildiği gibi <xref:System.IdentityModel.Claims.Claim.Equals%2A> , karşılaştırmayı yapmak için öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1a140-119">Given two instances of the <xref:System.IdentityModel.Claims.Claim> class, use the <xref:System.IdentityModel.Claims.Claim.Equals%2A> to make the comparison, as shown in the following code.</span></span>

     [!code-csharp[c_CustomClaimComparison#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#5)]
     [!code-vb[c_CustomClaimComparison#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#5)]

### <a name="comparing-custom-claims-with-primitive-resource-types"></a><span data-ttu-id="1a140-120">Özel talepleri basit kaynak türleriyle karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="1a140-120">Comparing custom claims with primitive resource types</span></span>

1. <span data-ttu-id="1a140-121">Temel kaynak türleriyle özel talepler için, aşağıdaki kodda gösterildiği gibi, karşılaştırma yerleşik talepler için olarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="1a140-121">For custom claims with primitive resource types, comparison can be performed as for built-in claims, as shown in the following code.</span></span>

     [!code-csharp[c_CustomClaimComparison#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#6)]
     [!code-vb[c_CustomClaimComparison#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#6)]

2. <span data-ttu-id="1a140-122">Yapı veya sınıf tabanlı kaynak türleriyle özel talepler için, kaynak türü <xref:System.IdentityModel.Claims.Claim.Equals%2A> yöntemi geçersiz kılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1a140-122">For custom claims with structure or class based resource types, the resource type should override the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span>

3. <span data-ttu-id="1a140-123">Önce `obj` `false`parametrenin olupolmadığınıdenetleyinvevarsadöndürün.`null`</span><span class="sxs-lookup"><span data-stu-id="1a140-123">First check whether the `obj` parameter is `null`, and if so, return `false`.</span></span>

     [!code-csharp[c_CustomClaimComparison#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#7)]
     [!code-vb[c_CustomClaimComparison#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#7)]

4. <span data-ttu-id="1a140-124">Sonraki çağrı <xref:System.Object.ReferenceEquals%2A> `this` ve`obj` geçiş parametreleri.</span><span class="sxs-lookup"><span data-stu-id="1a140-124">Next call <xref:System.Object.ReferenceEquals%2A> and pass `this` and `obj` as parameters.</span></span> <span data-ttu-id="1a140-125">Dönerse `true`geri döndürün `true`.</span><span class="sxs-lookup"><span data-stu-id="1a140-125">If it returns `true`, then return `true`.</span></span>

     [!code-csharp[c_CustomClaimComparison#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#8)]
     [!code-vb[c_CustomClaimComparison#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#8)]

5. <span data-ttu-id="1a140-126">Daha sonra sınıf türünün `obj` yerel değişkenine atamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="1a140-126">Next attempt to assign `obj` to a local variable of the class type.</span></span> <span data-ttu-id="1a140-127">Bu başarısız olursa, başvuru olur `null`.</span><span class="sxs-lookup"><span data-stu-id="1a140-127">If this fails, the reference is `null`.</span></span> <span data-ttu-id="1a140-128">Böyle durumlarda, döndürün `false`.</span><span class="sxs-lookup"><span data-stu-id="1a140-128">In such cases, return `false`.</span></span>

6. <span data-ttu-id="1a140-129">Geçerli talebi belirtilen talebe doğru bir şekilde karşılaştırmak için gereken özel karşılaştırmayı gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="1a140-129">Perform the custom comparison necessary to correctly compare the current claim to the provided claim.</span></span>

## <a name="example"></a><span data-ttu-id="1a140-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="1a140-130">Example</span></span>

<span data-ttu-id="1a140-131">Aşağıdaki örnek, talep kaynağının basit olmayan bir tür olduğu özel talepler karşılaştırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1a140-131">The following example shows a comparison of custom claims where the claim resource is a non-primitive type.</span></span>

[!code-csharp[c_CustomClaimComparison#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#0)]
[!code-vb[c_CustomClaimComparison#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#0)]

## <a name="see-also"></a><span data-ttu-id="1a140-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a140-132">See also</span></span>

- [<span data-ttu-id="1a140-133">Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme</span><span class="sxs-lookup"><span data-stu-id="1a140-133">Managing Claims and Authorization with the Identity Model</span></span>](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [<span data-ttu-id="1a140-134">Nasıl yapılır: Özel talep oluşturma</span><span class="sxs-lookup"><span data-stu-id="1a140-134">How to: Create a Custom Claim</span></span>](how-to-create-a-custom-claim.md)
