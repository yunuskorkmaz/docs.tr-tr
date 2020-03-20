---
title: 'Nasıl yapılır: Özel Beyan Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: e78f577e0fd3473575fab998e55616936212ebb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185612"
---
# <a name="how-to-create-a-custom-claim"></a><span data-ttu-id="1c425-102">Nasıl yapılır: Özel Beyan Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1c425-102">How to: Create a Custom Claim</span></span>
<span data-ttu-id="1c425-103">Windows Communication Foundation'daki (WCF) Kimlik Modeli altyapısı, bu tür ve haklara sahip <xref:System.IdentityModel.Claims.Claim> örnekler oluşturmak için yardımcı işlevlerle birlikte yerleşik talep türleri ve hakları kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1c425-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) provides a set of built-in claim types and rights with the helper functions for creating <xref:System.IdentityModel.Claims.Claim> instances with those types and rights.</span></span> <span data-ttu-id="1c425-104">Bu yerleşik talepler, WCF'nin varsayılan olarak desteklediği istemci kimlik bilgisi türlerinde bulunan bilgileri modellemek üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1c425-104">These built-in claims are designed to model information found in client credential types that WCF supports by default.</span></span> <span data-ttu-id="1c425-105">Çoğu durumda, yerleşik talepler yeterlidir; ancak bazı uygulamalar özel talepler gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="1c425-105">In many cases, the built-in claims are sufficient; however some applications may require custom claims.</span></span> <span data-ttu-id="1c425-106">Talep, talep türünden, talebin geçerli olduğu kaynaktan ve bu kaynak üzerinde öne sürülenen haktan oluşur.</span><span class="sxs-lookup"><span data-stu-id="1c425-106">A claim consists of the claim type, the resource for which the claim applies to and the right that is asserted over that resource.</span></span> <span data-ttu-id="1c425-107">Bu konu, özel bir talep oluşturma nın nasıl açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1c425-107">This topic describes how to create a custom claim.</span></span>  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a><span data-ttu-id="1c425-108">İlkel bir veri türünü temel alan özel bir talep oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1c425-108">To create a custom claim that is based on a primitive data type</span></span>  
  
1. <span data-ttu-id="1c425-109">Talep türünü, kaynak değerini ve hakkı <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> oluşturucuya geçirerek özel bir talep oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1c425-109">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1. <span data-ttu-id="1c425-110">Talep türü için benzersiz bir değer belirleyin.</span><span class="sxs-lookup"><span data-stu-id="1c425-110">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="1c425-111">Talep türü benzersiz bir dize tanımlayıcısır.</span><span class="sxs-lookup"><span data-stu-id="1c425-111">The claim type is a unique string identifier.</span></span> <span data-ttu-id="1c425-112">Talep türü için kullanılan dize tanımlayıcısının benzersiz olduğundan emin olmak özel talep tasarımcısının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="1c425-112">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="1c425-113">WCF tarafından tanımlanan talep türlerinin listesi için <xref:System.IdentityModel.Claims.ClaimTypes> sınıfa bakın.</span><span class="sxs-lookup"><span data-stu-id="1c425-113">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2. <span data-ttu-id="1c425-114">Kaynak için ilkel veri türünü ve değerini seçin.</span><span class="sxs-lookup"><span data-stu-id="1c425-114">Choose the primitive data type and value for the resource.</span></span>  
  
         <span data-ttu-id="1c425-115">Kaynak bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="1c425-115">A resource is an object.</span></span> <span data-ttu-id="1c425-116">Kaynağın CLR türü, herhangi bir serileştirilebilir <xref:System.Int32>tür gibi <xref:System.String> ilkel olabilir.</span><span class="sxs-lookup"><span data-stu-id="1c425-116">The CLR type of the resource can be a primitive, such as <xref:System.String> or <xref:System.Int32>, or any serializable type.</span></span> <span data-ttu-id="1c425-117">Talepler WCF tarafından çeşitli noktalarda seri hale getirildığından, kaynağın CLR türü serileştirilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1c425-117">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="1c425-118">İlkel türleri serileştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="1c425-118">Primitive types are serializable.</span></span>  
  
    3. <span data-ttu-id="1c425-119">WCF tarafından tanımlanan bir hakkı veya özel bir hak için benzersiz bir değer seçin.</span><span class="sxs-lookup"><span data-stu-id="1c425-119">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="1c425-120">Sağ, benzersiz bir dize tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="1c425-120">A right is a unique string identifier.</span></span> <span data-ttu-id="1c425-121">WCF tarafından tanımlanan haklar <xref:System.IdentityModel.Claims.Rights> sınıfta tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="1c425-121">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="1c425-122">Sağ için kullanılan dize tanımlayıcısının benzersiz olmasını sağlamak özel talep tasarımcısının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="1c425-122">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="1c425-123">Aşağıdaki kod `http://example.org/claims/simplecustomclaim`örneği, adlı `Driver's License`bir kaynak için ve <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> hakkı olan bir talep türüyle özel bir talep oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1c425-123">The following code example creates a custom claim with a claim type of `http://example.org/claims/simplecustomclaim`, for a resource named `Driver's License`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a><span data-ttu-id="1c425-124">İlkel olmayan bir veri türünü temel alan özel bir talep oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1c425-124">To create a custom claim that is based on a non-primitive data type</span></span>  
  
1. <span data-ttu-id="1c425-125">Talep türünü, kaynak değerini ve hakkı <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> oluşturucuya geçirerek özel bir talep oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1c425-125">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1. <span data-ttu-id="1c425-126">Talep türü için benzersiz bir değer belirleyin.</span><span class="sxs-lookup"><span data-stu-id="1c425-126">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="1c425-127">Talep türü benzersiz bir dize tanımlayıcısır.</span><span class="sxs-lookup"><span data-stu-id="1c425-127">The claim type is a unique string identifier.</span></span> <span data-ttu-id="1c425-128">Talep türü için kullanılan dize tanımlayıcısının benzersiz olduğundan emin olmak özel talep tasarımcısının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="1c425-128">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="1c425-129">WCF tarafından tanımlanan talep türlerinin listesi için <xref:System.IdentityModel.Claims.ClaimTypes> sınıfa bakın.</span><span class="sxs-lookup"><span data-stu-id="1c425-129">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2. <span data-ttu-id="1c425-130">Kaynak için seri olarak yazılabilir ilkel olmayan bir tür seçin veya tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="1c425-130">Choose or define a serializable non-primitive type for the resource.</span></span>  
  
         <span data-ttu-id="1c425-131">Kaynak bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="1c425-131">A resource is an object.</span></span> <span data-ttu-id="1c425-132">Talepler WCF tarafından çeşitli noktalarda seri hale getirildığından, kaynağın CLR türü serileştirilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1c425-132">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="1c425-133">İlkel türleri zaten serileştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="1c425-133">Primitive types are already serializable.</span></span>  
  
         <span data-ttu-id="1c425-134">Yeni bir tür tanımlandığında, <xref:System.Runtime.Serialization.DataContractAttribute> sınıfa uygulayın.</span><span class="sxs-lookup"><span data-stu-id="1c425-134">When a new type is defined, apply the <xref:System.Runtime.Serialization.DataContractAttribute> to the class.</span></span> <span data-ttu-id="1c425-135">Ayrıca, <xref:System.Runtime.Serialization.DataMemberAttribute> talebin bir parçası olarak serileştirilmesi gereken yeni türün tüm üyelerine özniteliği uygulayın.</span><span class="sxs-lookup"><span data-stu-id="1c425-135">Also apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the all members of the new type that need to be serialized as part of the claim.</span></span>  
  
         <span data-ttu-id="1c425-136">Aşağıdaki kod örneği adlı `MyResourceType`özel bir kaynak türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1c425-136">The following code example defines a custom resource type named `MyResourceType`.</span></span>  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)]
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]
  
    3. <span data-ttu-id="1c425-137">WCF tarafından tanımlanan bir hakkı veya özel bir hak için benzersiz bir değer seçin.</span><span class="sxs-lookup"><span data-stu-id="1c425-137">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="1c425-138">Sağ, benzersiz bir dize tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="1c425-138">A right is a unique string identifier.</span></span> <span data-ttu-id="1c425-139">WCF tarafından tanımlanan haklar <xref:System.IdentityModel.Claims.Rights> sınıfta tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="1c425-139">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="1c425-140">Sağ için kullanılan dize tanımlayıcısının benzersiz olmasını sağlamak özel talep tasarımcısının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="1c425-140">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="1c425-141">Aşağıdaki kod `http://example.org/claims/complexcustomclaim`örneği, bir talep türü , özel bir kaynak `MyResourceType`türü ve <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> sağ ile özel bir talep oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1c425-141">The following code example creates a custom claim with a claim type of `http://example.org/claims/complexcustomclaim`, a custom resource type of `MyResourceType`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)]
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]
  
## <a name="example"></a><span data-ttu-id="1c425-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="1c425-142">Example</span></span>  
 <span data-ttu-id="1c425-143">Aşağıdaki kod örneği, ilkel bir kaynak türüyle özel bir talep ve ilkel olmayan bir kaynak türüne sahip özel bir talep oluşturmanın nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1c425-143">The following code example demonstrates how to create a custom claim with a primitive resource type and a custom claim with a non-primitive resource type.</span></span>  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="1c425-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c425-144">See also</span></span>

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="1c425-145">Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme</span><span class="sxs-lookup"><span data-stu-id="1c425-145">Managing Claims and Authorization with the Identity Model</span></span>](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)
