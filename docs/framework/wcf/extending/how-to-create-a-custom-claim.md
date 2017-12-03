---
title: "Nasıl yapılır: Özel Beyan Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f0cc23d5b6720d78afdc1acd50a2b84b76b977e9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-custom-claim"></a><span data-ttu-id="e3b11-102">Nasıl yapılır: Özel Beyan Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e3b11-102">How to: Create a Custom Claim</span></span>
<span data-ttu-id="e3b11-103">Kimlik modeli altyapısında [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] oluşturmak için bir dizi yerleşik talep türlerini ve hakları ile yardımcı işlevleri sağlar <xref:System.IdentityModel.Claims.Claim> bu türleri ve hakları ile örnekleri.</span><span class="sxs-lookup"><span data-stu-id="e3b11-103">The Identity Model infrastructure in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] provides a set of built-in claim types and rights with the helper functions for creating <xref:System.IdentityModel.Claims.Claim> instances with those types and rights.</span></span> <span data-ttu-id="e3b11-104">Bu yerleşik talepler bulunan model bilgisi için tasarlanmış kimlik bilgisi istemcisinde türleri [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] varsayılan olarak destekler.</span><span class="sxs-lookup"><span data-stu-id="e3b11-104">These built-in claims are designed to model information found in client credential types that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] supports by default.</span></span> <span data-ttu-id="e3b11-105">Çoğu durumda, yerleşik talep yeterlidir; Ancak bazı uygulamalar özel talep gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="e3b11-105">In many cases, the built-in claims are sufficient; however some applications may require custom claims.</span></span> <span data-ttu-id="e3b11-106">Bir talep talep türünü, talep geçerli olduğu için kaynak ve sağ diğer bir deyişle sürülen bu kaynak oluşur.</span><span class="sxs-lookup"><span data-stu-id="e3b11-106">A claim consists of the claim type, the resource for which the claim applies to and the right that is asserted over that resource.</span></span> <span data-ttu-id="e3b11-107">Bu konuda bir özel talep oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="e3b11-107">This topic describes how to create a custom claim.</span></span>  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a><span data-ttu-id="e3b11-108">Temel veri türüne göre özel bir talep oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e3b11-108">To create a custom claim that is based on a primitive data type</span></span>  
  
1.  <span data-ttu-id="e3b11-109">Talep türü, kaynak değeri ve sağa geçirerek özel beyan oluşturma <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="e3b11-109">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1.  <span data-ttu-id="e3b11-110">Talep türü için benzersiz bir değer karar verin.</span><span class="sxs-lookup"><span data-stu-id="e3b11-110">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="e3b11-111">Talep türü benzersiz bir dize tanımlayıcısı değil.</span><span class="sxs-lookup"><span data-stu-id="e3b11-111">The claim type is a unique string identifier.</span></span> <span data-ttu-id="e3b11-112">Talep türü için kullanılan dize tanımlayıcı benzersiz olduğundan emin olun özel talep tasarımcının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="e3b11-112">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="e3b11-113">Tarafından tanımlanan talep türleri listesini [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], bkz: <xref:System.IdentityModel.Claims.ClaimTypes> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e3b11-113">For a list of claim types that are defined by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2.  <span data-ttu-id="e3b11-114">Basit veri türü ve kaynak için değer seçin.</span><span class="sxs-lookup"><span data-stu-id="e3b11-114">Choose the primitive data type and value for the resource.</span></span>  
  
         <span data-ttu-id="e3b11-115">Bir kaynak bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="e3b11-115">A resource is an object.</span></span> <span data-ttu-id="e3b11-116">Kaynak CLR türü bir primitive gibi olabilir <xref:System.String> veya <xref:System.Int32>, veya serializable bir tür.</span><span class="sxs-lookup"><span data-stu-id="e3b11-116">The CLR type of the resource can be a primitive, such as <xref:System.String> or <xref:System.Int32>, or any serializable type.</span></span> <span data-ttu-id="e3b11-117">Talep tarafından çeşitli noktalarında serileştirilir çünkü kaynak CLR türü seri hale getirilebilir, olmalıdır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e3b11-117">The CLR type of the resource must be serializable, because claims are serialized at various points by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="e3b11-118">İlkel türler seri hale getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="e3b11-118">Primitive types are serializable.</span></span>  
  
    3.  <span data-ttu-id="e3b11-119">Tarafından tanımlanan bir hak seçin [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] veya özel bir hak için benzersiz bir değer.</span><span class="sxs-lookup"><span data-stu-id="e3b11-119">Choose a right that is defined by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="e3b11-120">Bir hak benzersiz bir dize tanımlayıcısı değil.</span><span class="sxs-lookup"><span data-stu-id="e3b11-120">A right is a unique string identifier.</span></span> <span data-ttu-id="e3b11-121">Tarafından tanımlanan haklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tanımlanan <xref:System.IdentityModel.Claims.Rights> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e3b11-121">The rights that are defined by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="e3b11-122">Hakkını kullanılan dize tanımlayıcı benzersiz olduğundan emin olun özel talep tasarımcının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="e3b11-122">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="e3b11-123">Aşağıdaki kod örneği, bir talep türüyle bir özel talep oluşturur `http://example.org/claims/simplecustomclaim`, adlı bir kaynak için `Driver's License`ile <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> doğru.</span><span class="sxs-lookup"><span data-stu-id="e3b11-123">The following code example creates a custom claim with a claim type of `http://example.org/claims/simplecustomclaim`, for a resource named `Driver's License`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a><span data-ttu-id="e3b11-124">Basit olmayan veri türüne göre özel bir talep oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e3b11-124">To create a custom claim that is based on a non-primitive data type</span></span>  
  
1.  <span data-ttu-id="e3b11-125">Talep türü, kaynak değeri ve sağa geçirerek özel beyan oluşturma <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="e3b11-125">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1.  <span data-ttu-id="e3b11-126">Talep türü için benzersiz bir değer karar verin.</span><span class="sxs-lookup"><span data-stu-id="e3b11-126">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="e3b11-127">Talep türü benzersiz bir dize tanımlayıcısı değil.</span><span class="sxs-lookup"><span data-stu-id="e3b11-127">The claim type is a unique string identifier.</span></span> <span data-ttu-id="e3b11-128">Talep türü için kullanılan dize tanımlayıcı benzersiz olduğundan emin olun özel talep tasarımcının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="e3b11-128">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="e3b11-129">Tarafından tanımlanan talep türleri listesini [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], bkz: <xref:System.IdentityModel.Claims.ClaimTypes> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e3b11-129">For a list of claim types that are defined by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2.  <span data-ttu-id="e3b11-130">Seçin veya kaynak için serileştirilebilir bir basit olmayan türünü tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="e3b11-130">Choose or define a serializable non-primitive type for the resource.</span></span>  
  
         <span data-ttu-id="e3b11-131">Bir kaynak bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="e3b11-131">A resource is an object.</span></span> <span data-ttu-id="e3b11-132">Talep tarafından çeşitli noktalarında serileştirilir çünkü kaynak CLR türü seri hale getirilebilir, olmalıdır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e3b11-132">The CLR type of the resource must be serializable, because claims are serialized at various points by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="e3b11-133">İlkel türler zaten seri hale getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="e3b11-133">Primitive types are already serializable.</span></span>  
  
         <span data-ttu-id="e3b11-134">Yeni bir tür tanımlandığında, uygulama <xref:System.Runtime.Serialization.DataContractAttribute> sınıfa.</span><span class="sxs-lookup"><span data-stu-id="e3b11-134">When a new type is defined, apply the <xref:System.Runtime.Serialization.DataContractAttribute> to the class.</span></span> <span data-ttu-id="e3b11-135">Ayrıca uygulama <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği talep bir parçası olarak serileştirilmesi gereken yeni türü tüm üyeleri.</span><span class="sxs-lookup"><span data-stu-id="e3b11-135">Also apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the all members of the new type that need to be serialized as part of the claim.</span></span>  
  
         <span data-ttu-id="e3b11-136">Aşağıdaki kod örneğinde adlı bir özel kaynak türünü tanımlayan `MyResourceType`.</span><span class="sxs-lookup"><span data-stu-id="e3b11-136">The following code example defines a custom resource type named `MyResourceType`.</span></span>  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)] 
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]        
  
    3.  <span data-ttu-id="e3b11-137">Tarafından tanımlanan bir hak seçin [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] veya özel bir hak için benzersiz bir değer.</span><span class="sxs-lookup"><span data-stu-id="e3b11-137">Choose a right that is defined by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="e3b11-138">Bir hak benzersiz bir dize tanımlayıcısı değil.</span><span class="sxs-lookup"><span data-stu-id="e3b11-138">A right is a unique string identifier.</span></span> <span data-ttu-id="e3b11-139">Tarafından tanımlanan haklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tanımlanan <xref:System.IdentityModel.Claims.Rights> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e3b11-139">The rights that are defined by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="e3b11-140">Hakkını kullanılan dize tanımlayıcı benzersiz olduğundan emin olun özel talep tasarımcının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="e3b11-140">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="e3b11-141">Aşağıdaki kod örneği, bir talep türüyle bir özel talep oluşturur `http://example.org/claims/complexcustomclaim`, bir özel kaynak türü `MyResourceType`ile <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> doğru.</span><span class="sxs-lookup"><span data-stu-id="e3b11-141">The following code example creates a custom claim with a claim type of `http://example.org/claims/complexcustomclaim`, a custom resource type of `MyResourceType`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)] 
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]     
  
## <a name="example"></a><span data-ttu-id="e3b11-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="e3b11-142">Example</span></span>  
 <span data-ttu-id="e3b11-143">Aşağıdaki kod örneğinde ilkel kaynak türüne sahip bir özel talep ve bir özel talep basit olmayan kaynak türü ile nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e3b11-143">The following code example demonstrates how to create a custom claim with a primitive resource type and a custom claim with a non-primitive resource type.</span></span>  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="e3b11-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e3b11-144">See Also</span></span>  
 <xref:System.IdentityModel.Claims.Claim>  
 <xref:System.IdentityModel.Claims.Rights>  
 <xref:System.IdentityModel.Claims.ClaimTypes>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [<span data-ttu-id="e3b11-145">Beyanlar ve yetkilendirmeyi kimlik modeliyle yönetme</span><span class="sxs-lookup"><span data-stu-id="e3b11-145">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [<span data-ttu-id="e3b11-146">Beyanlar ve yetkilendirmeyi kimlik modeliyle yönetme</span><span class="sxs-lookup"><span data-stu-id="e3b11-146">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
