---
title: 'Nasıl yapılır: Özel Beyan Oluşturma'
description: WCF 'de özel talep oluşturmayı öğrenin. WCF, çeşitli yerleşik talepleri destekler ve bazı uygulamalar özel talepler gerektirebilir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: 89f2b1359b48b71720db6ff38f27883745cfe612
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247552"
---
# <a name="how-to-create-a-custom-claim"></a><span data-ttu-id="4c202-104">Nasıl yapılır: Özel Beyan Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4c202-104">How to: Create a Custom Claim</span></span>
<span data-ttu-id="4c202-105">Windows Communication Foundation (WCF) içindeki kimlik modeli altyapısı, <xref:System.IdentityModel.Claims.Claim> Bu tür ve haklara sahip örnekler oluşturmak için yardımcı işlevlerle birlikte yerleşik talep türleri ve haklar kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4c202-105">The Identity Model infrastructure in Windows Communication Foundation (WCF) provides a set of built-in claim types and rights with the helper functions for creating <xref:System.IdentityModel.Claims.Claim> instances with those types and rights.</span></span> <span data-ttu-id="4c202-106">Bu yerleşik talepler, WCF 'nin varsayılan olarak desteklediği istemci kimlik bilgileri türlerinde bulunan bilgileri modellemek üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4c202-106">These built-in claims are designed to model information found in client credential types that WCF supports by default.</span></span> <span data-ttu-id="4c202-107">Birçok durumda, yerleşik talepler yeterlidir; Ancak bazı uygulamalar özel talepler gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="4c202-107">In many cases, the built-in claims are sufficient; however some applications may require custom claims.</span></span> <span data-ttu-id="4c202-108">Talep türü, talebin uygulandığı kaynak ve söz konusu kaynak üzerinde bir hak olan talep türünden oluşur.</span><span class="sxs-lookup"><span data-stu-id="4c202-108">A claim consists of the claim type, the resource for which the claim applies to and the right that is asserted over that resource.</span></span> <span data-ttu-id="4c202-109">Bu konu başlığı altında, özel bir talebin nasıl oluşturulacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4c202-109">This topic describes how to create a custom claim.</span></span>  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a><span data-ttu-id="4c202-110">Temel bir veri türünü temel alan özel bir talep oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4c202-110">To create a custom claim that is based on a primitive data type</span></span>  
  
1. <span data-ttu-id="4c202-111">Talep türünü, kaynak değerini ve hakkını oluşturucuya geçirerek özel bir talep oluşturun <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> .</span><span class="sxs-lookup"><span data-stu-id="4c202-111">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1. <span data-ttu-id="4c202-112">Talep türü için benzersiz bir değer belirleyin.</span><span class="sxs-lookup"><span data-stu-id="4c202-112">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="4c202-113">Talep türü benzersiz bir dize tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="4c202-113">The claim type is a unique string identifier.</span></span> <span data-ttu-id="4c202-114">Bu, talep türü için kullanılan dize tanımlayıcısının benzersiz olduğundan emin olmak için özel talep tasarımcısının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="4c202-114">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="4c202-115">WCF tarafından tanımlanan talep türlerinin bir listesi için, <xref:System.IdentityModel.Claims.ClaimTypes> sınıfına bakın.</span><span class="sxs-lookup"><span data-stu-id="4c202-115">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2. <span data-ttu-id="4c202-116">Kaynağın temel veri türünü ve değerini seçin.</span><span class="sxs-lookup"><span data-stu-id="4c202-116">Choose the primitive data type and value for the resource.</span></span>  
  
         <span data-ttu-id="4c202-117">Kaynak bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="4c202-117">A resource is an object.</span></span> <span data-ttu-id="4c202-118">Kaynağın CLR türü veya gibi bir temel olabilir veya <xref:System.String> <xref:System.Int32> ya da serileştirilebilir herhangi bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="4c202-118">The CLR type of the resource can be a primitive, such as <xref:System.String> or <xref:System.Int32>, or any serializable type.</span></span> <span data-ttu-id="4c202-119">Talepler WCF tarafından farklı noktalarda serileştirildiği için kaynağın CLR türü seri hale getirilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4c202-119">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="4c202-120">İlkel türler seri hale getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="4c202-120">Primitive types are serializable.</span></span>  
  
    3. <span data-ttu-id="4c202-121">WCF tarafından tanımlanan bir sağ veya özel bir hak için benzersiz bir değer seçin.</span><span class="sxs-lookup"><span data-stu-id="4c202-121">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="4c202-122">Sağ, benzersiz bir dize tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="4c202-122">A right is a unique string identifier.</span></span> <span data-ttu-id="4c202-123">WCF tarafından tanımlanan haklar <xref:System.IdentityModel.Claims.Rights> sınıfında tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4c202-123">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="4c202-124">Sağ tarafta kullanılan dize tanımlayıcısının benzersiz olduğundan emin olmak için özel talep tasarımcısının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="4c202-124">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="4c202-125">Aşağıdaki kod örneği, `http://example.org/claims/simplecustomclaim` , adlı bir kaynak `Driver's License` ve sağ ile bir talep türü ile özel bir talep oluşturur <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> .</span><span class="sxs-lookup"><span data-stu-id="4c202-125">The following code example creates a custom claim with a claim type of `http://example.org/claims/simplecustomclaim`, for a resource named `Driver's License`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a><span data-ttu-id="4c202-126">İlkel olmayan bir veri türünü temel alan özel bir talep oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4c202-126">To create a custom claim that is based on a non-primitive data type</span></span>  
  
1. <span data-ttu-id="4c202-127">Talep türünü, kaynak değerini ve hakkını oluşturucuya geçirerek özel bir talep oluşturun <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> .</span><span class="sxs-lookup"><span data-stu-id="4c202-127">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1. <span data-ttu-id="4c202-128">Talep türü için benzersiz bir değer belirleyin.</span><span class="sxs-lookup"><span data-stu-id="4c202-128">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="4c202-129">Talep türü benzersiz bir dize tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="4c202-129">The claim type is a unique string identifier.</span></span> <span data-ttu-id="4c202-130">Bu, talep türü için kullanılan dize tanımlayıcısının benzersiz olduğundan emin olmak için özel talep tasarımcısının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="4c202-130">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="4c202-131">WCF tarafından tanımlanan talep türlerinin bir listesi için, <xref:System.IdentityModel.Claims.ClaimTypes> sınıfına bakın.</span><span class="sxs-lookup"><span data-stu-id="4c202-131">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2. <span data-ttu-id="4c202-132">Kaynak için seri hale getirilebilir bir temel olmayan tür seçin veya tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="4c202-132">Choose or define a serializable non-primitive type for the resource.</span></span>  
  
         <span data-ttu-id="4c202-133">Kaynak bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="4c202-133">A resource is an object.</span></span> <span data-ttu-id="4c202-134">Talepler WCF tarafından farklı noktalarda serileştirildiği için kaynağın CLR türü seri hale getirilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4c202-134">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="4c202-135">İlkel türler zaten serileştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="4c202-135">Primitive types are already serializable.</span></span>  
  
         <span data-ttu-id="4c202-136">Yeni bir tür tanımlandığında, <xref:System.Runtime.Serialization.DataContractAttribute> sınıfını sınıfına uygulayın.</span><span class="sxs-lookup"><span data-stu-id="4c202-136">When a new type is defined, apply the <xref:System.Runtime.Serialization.DataContractAttribute> to the class.</span></span> <span data-ttu-id="4c202-137">Ayrıca, <xref:System.Runtime.Serialization.DataMemberAttribute> talebin bir parçası olarak serileştirilmesi gereken yeni türün tüm üyelerine özniteliğini uygular.</span><span class="sxs-lookup"><span data-stu-id="4c202-137">Also apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the all members of the new type that need to be serialized as part of the claim.</span></span>  
  
         <span data-ttu-id="4c202-138">Aşağıdaki kod örneği adlı özel bir kaynak türünü tanımlar `MyResourceType` .</span><span class="sxs-lookup"><span data-stu-id="4c202-138">The following code example defines a custom resource type named `MyResourceType`.</span></span>  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)]
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]
  
    3. <span data-ttu-id="4c202-139">WCF tarafından tanımlanan bir sağ veya özel bir hak için benzersiz bir değer seçin.</span><span class="sxs-lookup"><span data-stu-id="4c202-139">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="4c202-140">Sağ, benzersiz bir dize tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="4c202-140">A right is a unique string identifier.</span></span> <span data-ttu-id="4c202-141">WCF tarafından tanımlanan haklar <xref:System.IdentityModel.Claims.Rights> sınıfında tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4c202-141">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="4c202-142">Sağ tarafta kullanılan dize tanımlayıcısının benzersiz olduğundan emin olmak için özel talep tasarımcısının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="4c202-142">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="4c202-143">Aşağıdaki kod örneği, bir talep türü `http://example.org/claims/complexcustomclaim` , özel kaynak türü `MyResourceType` ve sağ ile özel bir talep oluşturur <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> .</span><span class="sxs-lookup"><span data-stu-id="4c202-143">The following code example creates a custom claim with a claim type of `http://example.org/claims/complexcustomclaim`, a custom resource type of `MyResourceType`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)]
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]
  
## <a name="example"></a><span data-ttu-id="4c202-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="4c202-144">Example</span></span>  
 <span data-ttu-id="4c202-145">Aşağıdaki kod örneği, temel olmayan bir kaynak türü ile bir basit kaynak türüne ve özel talebe sahip özel bir talebin nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="4c202-145">The following code example demonstrates how to create a custom claim with a primitive resource type and a custom claim with a non-primitive resource type.</span></span>  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="4c202-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c202-146">See also</span></span>

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="4c202-147">Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme</span><span class="sxs-lookup"><span data-stu-id="4c202-147">Managing Claims and Authorization with the Identity Model</span></span>](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)
