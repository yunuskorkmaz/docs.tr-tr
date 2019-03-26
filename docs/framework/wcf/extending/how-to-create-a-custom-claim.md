---
title: 'Nasıl yapılır: Özel talep oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: bb7b4c06b87c8c214a6f3ed99a89707ccd0d626e
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58464313"
---
# <a name="how-to-create-a-custom-claim"></a><span data-ttu-id="01f48-102">Nasıl yapılır: Özel talep oluşturma</span><span class="sxs-lookup"><span data-stu-id="01f48-102">How to: Create a Custom Claim</span></span>
<span data-ttu-id="01f48-103">Windows Communication Foundation (WCF) kimlik modeli altyapısı oluşturmak için bir dizi yerleşik talep türleri ve yardımcı işlevlerini haklarıyla sağlar <xref:System.IdentityModel.Claims.Claim> örnekleriyle bu türleri ve hakları.</span><span class="sxs-lookup"><span data-stu-id="01f48-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) provides a set of built-in claim types and rights with the helper functions for creating <xref:System.IdentityModel.Claims.Claim> instances with those types and rights.</span></span> <span data-ttu-id="01f48-104">Bu yerleşik talepler, model bilgileri varsayılan olarak WCF destekleyen istemci kimlik bilgisi türlerinde bulunan şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="01f48-104">These built-in claims are designed to model information found in client credential types that WCF supports by default.</span></span> <span data-ttu-id="01f48-105">Çoğu durumda, yerleşik talep yeterlidir; Ancak bazı uygulamalar, özel talepler gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="01f48-105">In many cases, the built-in claims are sufficient; however some applications may require custom claims.</span></span> <span data-ttu-id="01f48-106">Bir talep talep türünü, talep için geçerli olduğu için kaynak ve doğrudan diğer bir deyişle olarak onaylanan bu kaynak üzerinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="01f48-106">A claim consists of the claim type, the resource for which the claim applies to and the right that is asserted over that resource.</span></span> <span data-ttu-id="01f48-107">Bu konuda bir özel talep oluşturma işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="01f48-107">This topic describes how to create a custom claim.</span></span>  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a><span data-ttu-id="01f48-108">Bir temel veri türüne göre özel bir talep oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="01f48-108">To create a custom claim that is based on a primitive data type</span></span>  
  
1.  <span data-ttu-id="01f48-109">Talep türü, kaynak değeri ve sağa geçirerek özel talep oluşturma <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="01f48-109">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1.  <span data-ttu-id="01f48-110">Talep türü için benzersiz bir değer karar verin.</span><span class="sxs-lookup"><span data-stu-id="01f48-110">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="01f48-111">Talep türünü bir benzersiz tanımlayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="01f48-111">The claim type is a unique string identifier.</span></span> <span data-ttu-id="01f48-112">Talep türü için kullanılan dize tanımlayıcı benzersiz olduğundan emin olun özel talep tasarımcının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="01f48-112">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="01f48-113">WCF tarafından tanımlanan talep türlerinin bir listesi için bkz. <xref:System.IdentityModel.Claims.ClaimTypes> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="01f48-113">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2.  <span data-ttu-id="01f48-114">Basit veri türü ve kaynak için bir değer seçin.</span><span class="sxs-lookup"><span data-stu-id="01f48-114">Choose the primitive data type and value for the resource.</span></span>  
  
         <span data-ttu-id="01f48-115">Bir kaynak bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="01f48-115">A resource is an object.</span></span> <span data-ttu-id="01f48-116">Kaynak CLR türü gibi basit bir tür olabilir <xref:System.String> veya <xref:System.Int32>, veya serializable bir tür.</span><span class="sxs-lookup"><span data-stu-id="01f48-116">The CLR type of the resource can be a primitive, such as <xref:System.String> or <xref:System.Int32>, or any serializable type.</span></span> <span data-ttu-id="01f48-117">WCF tarafından talep çeşitli noktalarda serileştirilme şeklini çünkü kaynak CLR türü seri hale getirilebilir, olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="01f48-117">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="01f48-118">İlkel türler seri hale getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="01f48-118">Primitive types are serializable.</span></span>  
  
    3.  <span data-ttu-id="01f48-119">WCF veya özel bir hak için benzersiz bir değer tarafından tanımlanan bir sağ seçin.</span><span class="sxs-lookup"><span data-stu-id="01f48-119">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="01f48-120">Bir hak benzersiz dize bir tanımlayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="01f48-120">A right is a unique string identifier.</span></span> <span data-ttu-id="01f48-121">WCF tarafından tanımlanan hakları tanımlanan <xref:System.IdentityModel.Claims.Rights> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="01f48-121">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="01f48-122">Sağa için kullanılan dize tanımlayıcı benzersiz olduğundan emin olun özel talep tasarımcının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="01f48-122">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="01f48-123">Aşağıdaki kod örneği, bir talep türü ile özel bir talep oluşturur `http://example.org/claims/simplecustomclaim`, adlı bir kaynak için `Driver's License`ile <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> doğru.</span><span class="sxs-lookup"><span data-stu-id="01f48-123">The following code example creates a custom claim with a claim type of `http://example.org/claims/simplecustomclaim`, for a resource named `Driver's License`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a><span data-ttu-id="01f48-124">Bir basit olmayan veri türüne göre özel bir talep oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="01f48-124">To create a custom claim that is based on a non-primitive data type</span></span>  
  
1.  <span data-ttu-id="01f48-125">Talep türü, kaynak değeri ve sağa geçirerek özel talep oluşturma <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="01f48-125">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1.  <span data-ttu-id="01f48-126">Talep türü için benzersiz bir değer karar verin.</span><span class="sxs-lookup"><span data-stu-id="01f48-126">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="01f48-127">Talep türünü bir benzersiz tanımlayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="01f48-127">The claim type is a unique string identifier.</span></span> <span data-ttu-id="01f48-128">Talep türü için kullanılan dize tanımlayıcı benzersiz olduğundan emin olun özel talep tasarımcının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="01f48-128">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="01f48-129">WCF tarafından tanımlanan talep türlerinin bir listesi için bkz. <xref:System.IdentityModel.Claims.ClaimTypes> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="01f48-129">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2.  <span data-ttu-id="01f48-130">Seçin veya kaynak için serileştirilebilir bir temel olmayan türde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="01f48-130">Choose or define a serializable non-primitive type for the resource.</span></span>  
  
         <span data-ttu-id="01f48-131">Bir kaynak bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="01f48-131">A resource is an object.</span></span> <span data-ttu-id="01f48-132">WCF tarafından talep çeşitli noktalarda serileştirilme şeklini çünkü kaynak CLR türü seri hale getirilebilir, olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="01f48-132">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="01f48-133">İlkel türler, zaten seri hale getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="01f48-133">Primitive types are already serializable.</span></span>  
  
         <span data-ttu-id="01f48-134">Yeni bir tür tanımlandığında, uygulama <xref:System.Runtime.Serialization.DataContractAttribute> sınıfa.</span><span class="sxs-lookup"><span data-stu-id="01f48-134">When a new type is defined, apply the <xref:System.Runtime.Serialization.DataContractAttribute> to the class.</span></span> <span data-ttu-id="01f48-135">Ayrıca uygulama <xref:System.Runtime.Serialization.DataMemberAttribute> talep bir parçası olarak seri hale gerek yeni türün tüm üyeleri için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="01f48-135">Also apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the all members of the new type that need to be serialized as part of the claim.</span></span>  
  
         <span data-ttu-id="01f48-136">Aşağıdaki kod örneğinde adlı bir özel kaynak türünü tanımlayan `MyResourceType`.</span><span class="sxs-lookup"><span data-stu-id="01f48-136">The following code example defines a custom resource type named `MyResourceType`.</span></span>  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)] 
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]        
  
    3.  <span data-ttu-id="01f48-137">WCF veya özel bir hak için benzersiz bir değer tarafından tanımlanan bir sağ seçin.</span><span class="sxs-lookup"><span data-stu-id="01f48-137">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="01f48-138">Bir hak benzersiz dize bir tanımlayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="01f48-138">A right is a unique string identifier.</span></span> <span data-ttu-id="01f48-139">WCF tarafından tanımlanan hakları tanımlanan <xref:System.IdentityModel.Claims.Rights> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="01f48-139">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="01f48-140">Sağa için kullanılan dize tanımlayıcı benzersiz olduğundan emin olun özel talep tasarımcının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="01f48-140">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="01f48-141">Aşağıdaki kod örneği, bir talep türü ile özel bir talep oluşturur `http://example.org/claims/complexcustomclaim`, özel kaynak türü `MyResourceType`ile <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> doğru.</span><span class="sxs-lookup"><span data-stu-id="01f48-141">The following code example creates a custom claim with a claim type of `http://example.org/claims/complexcustomclaim`, a custom resource type of `MyResourceType`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)] 
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]     
  
## <a name="example"></a><span data-ttu-id="01f48-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="01f48-142">Example</span></span>  
 <span data-ttu-id="01f48-143">Aşağıdaki kod örneği, ilkel olmayan kaynak türü ile bir özel talep ilkel kaynak türü ile ve özel talep oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="01f48-143">The following code example demonstrates how to create a custom claim with a primitive resource type and a custom claim with a non-primitive resource type.</span></span>  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="01f48-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01f48-144">See also</span></span>
- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="01f48-145">Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme</span><span class="sxs-lookup"><span data-stu-id="01f48-145">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
