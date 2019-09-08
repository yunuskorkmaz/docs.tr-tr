---
title: 'Nasıl yapılır: Özel Talep Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: 399aba1a6ad70ae37355f529a291ab2f604af03f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797081"
---
# <a name="how-to-create-a-custom-claim"></a><span data-ttu-id="cba91-102">Nasıl yapılır: Özel Talep Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cba91-102">How to: Create a Custom Claim</span></span>
<span data-ttu-id="cba91-103">Windows Communication Foundation (WCF) içindeki kimlik modeli altyapısı, bu tür ve haklara sahip örnekler oluşturmak <xref:System.IdentityModel.Claims.Claim> için yardımcı işlevlerle birlikte yerleşik talep türleri ve haklar kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="cba91-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) provides a set of built-in claim types and rights with the helper functions for creating <xref:System.IdentityModel.Claims.Claim> instances with those types and rights.</span></span> <span data-ttu-id="cba91-104">Bu yerleşik talepler, WCF 'nin varsayılan olarak desteklediği istemci kimlik bilgileri türlerinde bulunan bilgileri modellemek üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="cba91-104">These built-in claims are designed to model information found in client credential types that WCF supports by default.</span></span> <span data-ttu-id="cba91-105">Birçok durumda, yerleşik talepler yeterlidir; Ancak bazı uygulamalar özel talepler gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="cba91-105">In many cases, the built-in claims are sufficient; however some applications may require custom claims.</span></span> <span data-ttu-id="cba91-106">Talep türü, talebin uygulandığı kaynak ve söz konusu kaynak üzerinde bir hak olan talep türünden oluşur.</span><span class="sxs-lookup"><span data-stu-id="cba91-106">A claim consists of the claim type, the resource for which the claim applies to and the right that is asserted over that resource.</span></span> <span data-ttu-id="cba91-107">Bu konu başlığı altında, özel bir talebin nasıl oluşturulacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cba91-107">This topic describes how to create a custom claim.</span></span>  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a><span data-ttu-id="cba91-108">Temel bir veri türünü temel alan özel bir talep oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="cba91-108">To create a custom claim that is based on a primitive data type</span></span>  
  
1. <span data-ttu-id="cba91-109">Talep türünü, kaynak değerini ve hakkını <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> oluşturucuya geçirerek özel bir talep oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cba91-109">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1. <span data-ttu-id="cba91-110">Talep türü için benzersiz bir değer belirleyin.</span><span class="sxs-lookup"><span data-stu-id="cba91-110">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="cba91-111">Talep türü benzersiz bir dize tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="cba91-111">The claim type is a unique string identifier.</span></span> <span data-ttu-id="cba91-112">Bu, talep türü için kullanılan dize tanımlayıcısının benzersiz olduğundan emin olmak için özel talep tasarımcısının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="cba91-112">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="cba91-113">WCF tarafından tanımlanan talep türlerinin bir listesi için, <xref:System.IdentityModel.Claims.ClaimTypes> sınıfına bakın.</span><span class="sxs-lookup"><span data-stu-id="cba91-113">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2. <span data-ttu-id="cba91-114">Kaynağın temel veri türünü ve değerini seçin.</span><span class="sxs-lookup"><span data-stu-id="cba91-114">Choose the primitive data type and value for the resource.</span></span>  
  
         <span data-ttu-id="cba91-115">Kaynak bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="cba91-115">A resource is an object.</span></span> <span data-ttu-id="cba91-116">Kaynağın clr türü <xref:System.String> veya <xref:System.Int32>gibi bir temel olabilir veya ya da serileştirilebilir herhangi bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="cba91-116">The CLR type of the resource can be a primitive, such as <xref:System.String> or <xref:System.Int32>, or any serializable type.</span></span> <span data-ttu-id="cba91-117">Talepler WCF tarafından farklı noktalarda serileştirildiği için kaynağın CLR türü seri hale getirilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cba91-117">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="cba91-118">İlkel türler seri hale getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="cba91-118">Primitive types are serializable.</span></span>  
  
    3. <span data-ttu-id="cba91-119">WCF tarafından tanımlanan bir sağ veya özel bir hak için benzersiz bir değer seçin.</span><span class="sxs-lookup"><span data-stu-id="cba91-119">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="cba91-120">Sağ, benzersiz bir dize tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="cba91-120">A right is a unique string identifier.</span></span> <span data-ttu-id="cba91-121">WCF tarafından tanımlanan haklar <xref:System.IdentityModel.Claims.Rights> sınıfında tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="cba91-121">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="cba91-122">Sağ tarafta kullanılan dize tanımlayıcısının benzersiz olduğundan emin olmak için özel talep tasarımcısının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="cba91-122">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="cba91-123">Aşağıdaki kod örneği,, adlı `http://example.org/claims/simplecustomclaim` `Driver's License`bir kaynak ve <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> sağ ile bir talep türü ile özel bir talep oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cba91-123">The following code example creates a custom claim with a claim type of `http://example.org/claims/simplecustomclaim`, for a resource named `Driver's License`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a><span data-ttu-id="cba91-124">İlkel olmayan bir veri türünü temel alan özel bir talep oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="cba91-124">To create a custom claim that is based on a non-primitive data type</span></span>  
  
1. <span data-ttu-id="cba91-125">Talep türünü, kaynak değerini ve hakkını <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> oluşturucuya geçirerek özel bir talep oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cba91-125">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1. <span data-ttu-id="cba91-126">Talep türü için benzersiz bir değer belirleyin.</span><span class="sxs-lookup"><span data-stu-id="cba91-126">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="cba91-127">Talep türü benzersiz bir dize tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="cba91-127">The claim type is a unique string identifier.</span></span> <span data-ttu-id="cba91-128">Bu, talep türü için kullanılan dize tanımlayıcısının benzersiz olduğundan emin olmak için özel talep tasarımcısının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="cba91-128">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="cba91-129">WCF tarafından tanımlanan talep türlerinin bir listesi için, <xref:System.IdentityModel.Claims.ClaimTypes> sınıfına bakın.</span><span class="sxs-lookup"><span data-stu-id="cba91-129">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2. <span data-ttu-id="cba91-130">Kaynak için seri hale getirilebilir bir temel olmayan tür seçin veya tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="cba91-130">Choose or define a serializable non-primitive type for the resource.</span></span>  
  
         <span data-ttu-id="cba91-131">Kaynak bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="cba91-131">A resource is an object.</span></span> <span data-ttu-id="cba91-132">Talepler WCF tarafından farklı noktalarda serileştirildiği için kaynağın CLR türü seri hale getirilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cba91-132">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="cba91-133">İlkel türler zaten serileştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="cba91-133">Primitive types are already serializable.</span></span>  
  
         <span data-ttu-id="cba91-134">Yeni bir tür tanımlandığında, <xref:System.Runtime.Serialization.DataContractAttribute> sınıfını sınıfına uygulayın.</span><span class="sxs-lookup"><span data-stu-id="cba91-134">When a new type is defined, apply the <xref:System.Runtime.Serialization.DataContractAttribute> to the class.</span></span> <span data-ttu-id="cba91-135">Ayrıca, <xref:System.Runtime.Serialization.DataMemberAttribute> talebin bir parçası olarak serileştirilmesi gereken yeni türün tüm üyelerine özniteliğini uygular.</span><span class="sxs-lookup"><span data-stu-id="cba91-135">Also apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the all members of the new type that need to be serialized as part of the claim.</span></span>  
  
         <span data-ttu-id="cba91-136">Aşağıdaki kod örneği adlı `MyResourceType`özel bir kaynak türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cba91-136">The following code example defines a custom resource type named `MyResourceType`.</span></span>  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)] 
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]        
  
    3. <span data-ttu-id="cba91-137">WCF tarafından tanımlanan bir sağ veya özel bir hak için benzersiz bir değer seçin.</span><span class="sxs-lookup"><span data-stu-id="cba91-137">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="cba91-138">Sağ, benzersiz bir dize tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="cba91-138">A right is a unique string identifier.</span></span> <span data-ttu-id="cba91-139">WCF tarafından tanımlanan haklar <xref:System.IdentityModel.Claims.Rights> sınıfında tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="cba91-139">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="cba91-140">Sağ tarafta kullanılan dize tanımlayıcısının benzersiz olduğundan emin olmak için özel talep tasarımcısının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="cba91-140">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="cba91-141">Aşağıdaki kod örneği, bir talep türü `http://example.org/claims/complexcustomclaim`, özel kaynak `MyResourceType`türü ve <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> sağ ile özel bir talep oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cba91-141">The following code example creates a custom claim with a claim type of `http://example.org/claims/complexcustomclaim`, a custom resource type of `MyResourceType`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)] 
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]     
  
## <a name="example"></a><span data-ttu-id="cba91-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="cba91-142">Example</span></span>  
 <span data-ttu-id="cba91-143">Aşağıdaki kod örneği, temel olmayan bir kaynak türü ile bir basit kaynak türüne ve özel talebe sahip özel bir talebin nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="cba91-143">The following code example demonstrates how to create a custom claim with a primitive resource type and a custom claim with a non-primitive resource type.</span></span>  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="cba91-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cba91-144">See also</span></span>

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="cba91-145">Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme</span><span class="sxs-lookup"><span data-stu-id="cba91-145">Managing Claims and Authorization with the Identity Model</span></span>](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)
