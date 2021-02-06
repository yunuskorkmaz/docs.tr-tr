---
description: 'Daha fazla bilgi edinin: nasıl yapılır: talepleri karşılaştırma'
title: 'Nasıl yapılır: Talepleri Karşılaştırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], comparing
- claims [WCF]
ms.assetid: 0c4ec84d-53df-408f-8953-9bc437f56c28
ms.openlocfilehash: c2088ad3992852bdc12e7bcd71d5f3598a237b45
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653855"
---
# <a name="how-to-compare-claims"></a><span data-ttu-id="ea9d4-103">Nasıl yapılır: Talepleri Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="ea9d4-103">How to: Compare Claims</span></span>

<span data-ttu-id="ea9d4-104">Windows Communication Foundation (WCF) içindeki kimlik modeli altyapısı, yetkilendirme denetimi gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ea9d4-104">The Identity Model infrastructure in Windows Communication Foundation (WCF) is used to perform authorization checking.</span></span> <span data-ttu-id="ea9d4-105">Bu nedenle, ortak bir görev, yetkilendirme bağlamındaki talepleri, istenen eylemi gerçekleştirmek veya istenen kaynağa erişmek için gereken taleplerle karşılaştırmaktır.</span><span class="sxs-lookup"><span data-stu-id="ea9d4-105">As such, a common task is to compare claims in the authorization context to the claims required to perform the requested action or access the requested resource.</span></span> <span data-ttu-id="ea9d4-106">Bu konuda, yerleşik ve özel talep türleri dahil olmak üzere taleplerin nasıl karşılaştırılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ea9d4-106">This topic describes how to compare claims, including built-in and custom claim types.</span></span> <span data-ttu-id="ea9d4-107">Kimlik modeli altyapısı hakkında daha fazla bilgi için bkz. [kimlik modeliyle talepleri ve Yetkilendirmeyi Yönetme](../feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span><span class="sxs-lookup"><span data-stu-id="ea9d4-107">For more information about the Identity Model infrastructure, see [Managing Claims and Authorization with the Identity Model](../feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span></span>

<span data-ttu-id="ea9d4-108">Talep karşılaştırması, bir talebin (tür, sağ ve kaynak) üç parçasını başka bir talepteki aynı bölümlere göre karşılaştırarak eşit olup olmadığını görmenizi içerir.</span><span class="sxs-lookup"><span data-stu-id="ea9d4-108">Claim comparison involves comparing the three parts of a claim (type, right, and resource) against the same parts in another claim to see if they are equal.</span></span> <span data-ttu-id="ea9d4-109">Aşağıdaki örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="ea9d4-109">See the following example.</span></span>

[!code-csharp[c_CustomClaimComparison#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#9)]
[!code-vb[c_CustomClaimComparison#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#9)]

<span data-ttu-id="ea9d4-110">Her iki talep da bir talep türüne <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A> , sağına <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> ve "birisi" dizesinin bir kaynağına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ea9d4-110">Both claims have a claim type of <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, a right of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>, and a resource of the string "someone".</span></span> <span data-ttu-id="ea9d4-111">Talebin her üç bölümü de eşitse, talepler eşittir.</span><span class="sxs-lookup"><span data-stu-id="ea9d4-111">As all three parts of the claim are equal, the claims themselves are equal.</span></span>

<span data-ttu-id="ea9d4-112">Yerleşik talep türleri, yöntemi kullanılarak karşılaştırılır <xref:System.IdentityModel.Claims.Claim.Equals%2A> .</span><span class="sxs-lookup"><span data-stu-id="ea9d4-112">The built-in claim types are compared using the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="ea9d4-113">Gerektiğinde talebe özgü karşılaştırma kodu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ea9d4-113">Claim-specific comparison code is used where necessary.</span></span> <span data-ttu-id="ea9d4-114">Örneğin, aşağıdaki iki Kullanıcı asıl adı (UPN) talebi verildiğinde:</span><span class="sxs-lookup"><span data-stu-id="ea9d4-114">For example, given the following two user principal name (UPN) claims:</span></span>

[!code-csharp[c_CustomClaimComparison#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#4)]
[!code-vb[c_CustomClaimComparison#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#4)]

<span data-ttu-id="ea9d4-115">yöntemdeki karşılaştırma kodu, <xref:System.IdentityModel.Claims.Claim.Equals%2A> `true` `example\someone` aynı etki alanı kullanıcısını "" ile tanımlar, kabul edilir someone@example.com .</span><span class="sxs-lookup"><span data-stu-id="ea9d4-115">the comparison code in the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method returns `true`, assuming `example\someone` identifies the same domain user as "someone@example.com".</span></span>

<span data-ttu-id="ea9d4-116">Özel talep türleri, yöntemi kullanılarak da karşılaştırılabilir <xref:System.IdentityModel.Claims.Claim.Equals%2A> .</span><span class="sxs-lookup"><span data-stu-id="ea9d4-116">Custom claim types can also be compared using the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="ea9d4-117">Ancak, talebin özelliği tarafından döndürülen türün <xref:System.IdentityModel.Claims.Claim.Resource%2A> ilkel bir tür dışında bir şey olduğu durumlarda, <xref:System.IdentityModel.Claims.Claim.Equals%2A> `true` yalnızca özellikler tarafından döndürülen değerler `Resource` yönteme göre eşitse döndürülür <xref:System.IdentityModel.Claims.Claim.Equals%2A> .</span><span class="sxs-lookup"><span data-stu-id="ea9d4-117">However, in cases where the type returned by the <xref:System.IdentityModel.Claims.Claim.Resource%2A> property of the claim is something other than a primitive type, the <xref:System.IdentityModel.Claims.Claim.Equals%2A> returns `true` only if the values returned by the `Resource` properties are equal according to the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="ea9d4-118">Bunun uygun olmadığı durumlarda, özelliği tarafından döndürülen özel tür `Resource` , <xref:System.IdentityModel.Claims.Claim.Equals%2A> <xref:System.Object.GetHashCode%2A> gerekli tüm özel işlemleri gerçekleştirmek için ve yöntemlerini geçersiz kılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ea9d4-118">In cases where this is not appropriate, the custom type returned by the `Resource` property should override the <xref:System.IdentityModel.Claims.Claim.Equals%2A> and <xref:System.Object.GetHashCode%2A> methods to perform whatever custom processing is necessary.</span></span>

## <a name="comparing-built-in-claims"></a><span data-ttu-id="ea9d4-119">Yerleşik talepler karşılaştırılıyor</span><span class="sxs-lookup"><span data-stu-id="ea9d4-119">Comparing built-in claims</span></span>

1. <span data-ttu-id="ea9d4-120">Sınıfının iki örneği verildiğinde, <xref:System.IdentityModel.Claims.Claim> <xref:System.IdentityModel.Claims.Claim.Equals%2A> aşağıdaki kodda gösterildiği gibi, karşılaştırmayı yapmak için öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ea9d4-120">Given two instances of the <xref:System.IdentityModel.Claims.Claim> class, use the <xref:System.IdentityModel.Claims.Claim.Equals%2A> to make the comparison, as shown in the following code.</span></span>

     [!code-csharp[c_CustomClaimComparison#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#5)]
     [!code-vb[c_CustomClaimComparison#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#5)]

### <a name="comparing-custom-claims-with-primitive-resource-types"></a><span data-ttu-id="ea9d4-121">Özel talepleri basit kaynak türleriyle karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="ea9d4-121">Comparing custom claims with primitive resource types</span></span>

1. <span data-ttu-id="ea9d4-122">Temel kaynak türleriyle özel talepler için, aşağıdaki kodda gösterildiği gibi, karşılaştırma yerleşik talepler için olarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ea9d4-122">For custom claims with primitive resource types, comparison can be performed as for built-in claims, as shown in the following code.</span></span>

     [!code-csharp[c_CustomClaimComparison#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#6)]
     [!code-vb[c_CustomClaimComparison#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#6)]

2. <span data-ttu-id="ea9d4-123">Yapı veya sınıf tabanlı kaynak türleriyle özel talepler için, kaynak türü yöntemi geçersiz kılmalıdır <xref:System.IdentityModel.Claims.Claim.Equals%2A> .</span><span class="sxs-lookup"><span data-stu-id="ea9d4-123">For custom claims with structure or class based resource types, the resource type should override the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span>

3. <span data-ttu-id="ea9d4-124">Önce parametrenin olup olmadığını denetleyin `obj` `null` ve varsa döndürün `false` .</span><span class="sxs-lookup"><span data-stu-id="ea9d4-124">First check whether the `obj` parameter is `null`, and if so, return `false`.</span></span>

     [!code-csharp[c_CustomClaimComparison#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#7)]
     [!code-vb[c_CustomClaimComparison#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#7)]

4. <span data-ttu-id="ea9d4-125">Sonraki çağrı <xref:System.Object.ReferenceEquals%2A> ve geçiş `this` `obj` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="ea9d4-125">Next call <xref:System.Object.ReferenceEquals%2A> and pass `this` and `obj` as parameters.</span></span> <span data-ttu-id="ea9d4-126">Dönerse `true` geri döndürün `true` .</span><span class="sxs-lookup"><span data-stu-id="ea9d4-126">If it returns `true`, then return `true`.</span></span>

     [!code-csharp[c_CustomClaimComparison#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#8)]
     [!code-vb[c_CustomClaimComparison#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#8)]

5. <span data-ttu-id="ea9d4-127">Daha sonra `obj` sınıf türünün yerel değişkenine atamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="ea9d4-127">Next attempt to assign `obj` to a local variable of the class type.</span></span> <span data-ttu-id="ea9d4-128">Bu başarısız olursa, başvuru olur `null` .</span><span class="sxs-lookup"><span data-stu-id="ea9d4-128">If this fails, the reference is `null`.</span></span> <span data-ttu-id="ea9d4-129">Böyle durumlarda, döndürün `false` .</span><span class="sxs-lookup"><span data-stu-id="ea9d4-129">In such cases, return `false`.</span></span>

6. <span data-ttu-id="ea9d4-130">Geçerli talebi belirtilen talebe doğru bir şekilde karşılaştırmak için gereken özel karşılaştırmayı gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="ea9d4-130">Perform the custom comparison necessary to correctly compare the current claim to the provided claim.</span></span>

## <a name="example"></a><span data-ttu-id="ea9d4-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="ea9d4-131">Example</span></span>

<span data-ttu-id="ea9d4-132">Aşağıdaki örnek, talep kaynağının basit olmayan bir tür olduğu özel talepler karşılaştırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ea9d4-132">The following example shows a comparison of custom claims where the claim resource is a non-primitive type.</span></span>

[!code-csharp[c_CustomClaimComparison#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#0)]
[!code-vb[c_CustomClaimComparison#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#0)]

## <a name="see-also"></a><span data-ttu-id="ea9d4-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea9d4-133">See also</span></span>

- [<span data-ttu-id="ea9d4-134">Kimlik Modeliyle Beyanlar ve Yetkilendirmeyi Yönetme</span><span class="sxs-lookup"><span data-stu-id="ea9d4-134">Managing Claims and Authorization with the Identity Model</span></span>](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [<span data-ttu-id="ea9d4-135">Nasıl yapılır: Özel Talep Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ea9d4-135">How to: Create a Custom Claim</span></span>](how-to-create-a-custom-claim.md)
