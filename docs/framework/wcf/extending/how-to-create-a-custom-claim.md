---
title: 'Nasıl yapılır: Özel Beyan Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: 3ee707ae4e2a7dafeb7cb42d6d56eeece8f23306
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33804865"
---
# <a name="how-to-create-a-custom-claim"></a><span data-ttu-id="05a0e-102">Nasıl yapılır: Özel Beyan Oluşturma</span><span class="sxs-lookup"><span data-stu-id="05a0e-102">How to: Create a Custom Claim</span></span>
<span data-ttu-id="05a0e-103">Windows Communication Foundation (WCF) kimlik modeli altyapısı oluşturmak için bir dizi yerleşik talep türleri ve yardımcı işlevleri haklarıyla sağlar <xref:System.IdentityModel.Claims.Claim> bu türleri ve hakları ile örnekleri.</span><span class="sxs-lookup"><span data-stu-id="05a0e-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) provides a set of built-in claim types and rights with the helper functions for creating <xref:System.IdentityModel.Claims.Claim> instances with those types and rights.</span></span> <span data-ttu-id="05a0e-104">Bu yerleşik talepler varsayılan olarak, WCF destekleyen istemci kimlik bilgisi türlerinde bulunan model bilgisi için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="05a0e-104">These built-in claims are designed to model information found in client credential types that WCF supports by default.</span></span> <span data-ttu-id="05a0e-105">Çoğu durumda, yerleşik talep yeterlidir; Ancak bazı uygulamalar özel talep gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="05a0e-105">In many cases, the built-in claims are sufficient; however some applications may require custom claims.</span></span> <span data-ttu-id="05a0e-106">Bir talep talep türünü, talep geçerli olduğu için kaynak ve sağ diğer bir deyişle sürülen bu kaynak oluşur.</span><span class="sxs-lookup"><span data-stu-id="05a0e-106">A claim consists of the claim type, the resource for which the claim applies to and the right that is asserted over that resource.</span></span> <span data-ttu-id="05a0e-107">Bu konuda bir özel talep oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="05a0e-107">This topic describes how to create a custom claim.</span></span>  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a><span data-ttu-id="05a0e-108">Temel veri türüne göre özel bir talep oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="05a0e-108">To create a custom claim that is based on a primitive data type</span></span>  
  
1.  <span data-ttu-id="05a0e-109">Talep türü, kaynak değeri ve sağa geçirerek özel beyan oluşturma <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="05a0e-109">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1.  <span data-ttu-id="05a0e-110">Talep türü için benzersiz bir değer karar verin.</span><span class="sxs-lookup"><span data-stu-id="05a0e-110">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="05a0e-111">Talep türü benzersiz bir dize tanımlayıcısı değil.</span><span class="sxs-lookup"><span data-stu-id="05a0e-111">The claim type is a unique string identifier.</span></span> <span data-ttu-id="05a0e-112">Talep türü için kullanılan dize tanımlayıcı benzersiz olduğundan emin olun özel talep tasarımcının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="05a0e-112">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="05a0e-113">WCF tarafından tanımlanan talep türlerinin listesi için bkz: <xref:System.IdentityModel.Claims.ClaimTypes> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="05a0e-113">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2.  <span data-ttu-id="05a0e-114">Basit veri türü ve kaynak için değer seçin.</span><span class="sxs-lookup"><span data-stu-id="05a0e-114">Choose the primitive data type and value for the resource.</span></span>  
  
         <span data-ttu-id="05a0e-115">Bir kaynak bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="05a0e-115">A resource is an object.</span></span> <span data-ttu-id="05a0e-116">Kaynak CLR türü bir primitive gibi olabilir <xref:System.String> veya <xref:System.Int32>, veya serializable bir tür.</span><span class="sxs-lookup"><span data-stu-id="05a0e-116">The CLR type of the resource can be a primitive, such as <xref:System.String> or <xref:System.Int32>, or any serializable type.</span></span> <span data-ttu-id="05a0e-117">WCF tarafından serileştirilmiş talep çeşitli noktalarda, çünkü kaynak CLR türü seri hale getirilebilir, olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="05a0e-117">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="05a0e-118">İlkel türler seri hale getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="05a0e-118">Primitive types are serializable.</span></span>  
  
    3.  <span data-ttu-id="05a0e-119">WCF veya özel bir hak için benzersiz bir değer tarafından tanımlanan bir hak seçin.</span><span class="sxs-lookup"><span data-stu-id="05a0e-119">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="05a0e-120">Bir hak benzersiz bir dize tanımlayıcısı değil.</span><span class="sxs-lookup"><span data-stu-id="05a0e-120">A right is a unique string identifier.</span></span> <span data-ttu-id="05a0e-121">WCF tarafından tanımlanan haklar tanımlanan <xref:System.IdentityModel.Claims.Rights> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="05a0e-121">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="05a0e-122">Hakkını kullanılan dize tanımlayıcı benzersiz olduğundan emin olun özel talep tasarımcının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="05a0e-122">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="05a0e-123">Aşağıdaki kod örneği, bir talep türüyle bir özel talep oluşturur `http://example.org/claims/simplecustomclaim`, adlı bir kaynak için `Driver's License`ile <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> doğru.</span><span class="sxs-lookup"><span data-stu-id="05a0e-123">The following code example creates a custom claim with a claim type of `http://example.org/claims/simplecustomclaim`, for a resource named `Driver's License`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a><span data-ttu-id="05a0e-124">Basit olmayan veri türüne göre özel bir talep oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="05a0e-124">To create a custom claim that is based on a non-primitive data type</span></span>  
  
1.  <span data-ttu-id="05a0e-125">Talep türü, kaynak değeri ve sağa geçirerek özel beyan oluşturma <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="05a0e-125">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1.  <span data-ttu-id="05a0e-126">Talep türü için benzersiz bir değer karar verin.</span><span class="sxs-lookup"><span data-stu-id="05a0e-126">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="05a0e-127">Talep türü benzersiz bir dize tanımlayıcısı değil.</span><span class="sxs-lookup"><span data-stu-id="05a0e-127">The claim type is a unique string identifier.</span></span> <span data-ttu-id="05a0e-128">Talep türü için kullanılan dize tanımlayıcı benzersiz olduğundan emin olun özel talep tasarımcının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="05a0e-128">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="05a0e-129">WCF tarafından tanımlanan talep türlerinin listesi için bkz: <xref:System.IdentityModel.Claims.ClaimTypes> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="05a0e-129">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2.  <span data-ttu-id="05a0e-130">Seçin veya kaynak için serileştirilebilir bir basit olmayan türünü tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="05a0e-130">Choose or define a serializable non-primitive type for the resource.</span></span>  
  
         <span data-ttu-id="05a0e-131">Bir kaynak bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="05a0e-131">A resource is an object.</span></span> <span data-ttu-id="05a0e-132">WCF tarafından serileştirilmiş talep çeşitli noktalarda, çünkü kaynak CLR türü seri hale getirilebilir, olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="05a0e-132">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="05a0e-133">İlkel türler zaten seri hale getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="05a0e-133">Primitive types are already serializable.</span></span>  
  
         <span data-ttu-id="05a0e-134">Yeni bir tür tanımlandığında, uygulama <xref:System.Runtime.Serialization.DataContractAttribute> sınıfa.</span><span class="sxs-lookup"><span data-stu-id="05a0e-134">When a new type is defined, apply the <xref:System.Runtime.Serialization.DataContractAttribute> to the class.</span></span> <span data-ttu-id="05a0e-135">Ayrıca uygulama <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği talep bir parçası olarak serileştirilmesi gereken yeni türü tüm üyeleri.</span><span class="sxs-lookup"><span data-stu-id="05a0e-135">Also apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the all members of the new type that need to be serialized as part of the claim.</span></span>  
  
         <span data-ttu-id="05a0e-136">Aşağıdaki kod örneğinde adlı bir özel kaynak türünü tanımlayan `MyResourceType`.</span><span class="sxs-lookup"><span data-stu-id="05a0e-136">The following code example defines a custom resource type named `MyResourceType`.</span></span>  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)] 
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]        
  
    3.  <span data-ttu-id="05a0e-137">WCF veya özel bir hak için benzersiz bir değer tarafından tanımlanan bir hak seçin.</span><span class="sxs-lookup"><span data-stu-id="05a0e-137">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="05a0e-138">Bir hak benzersiz bir dize tanımlayıcısı değil.</span><span class="sxs-lookup"><span data-stu-id="05a0e-138">A right is a unique string identifier.</span></span> <span data-ttu-id="05a0e-139">WCF tarafından tanımlanan haklar tanımlanan <xref:System.IdentityModel.Claims.Rights> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="05a0e-139">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="05a0e-140">Hakkını kullanılan dize tanımlayıcı benzersiz olduğundan emin olun özel talep tasarımcının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="05a0e-140">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="05a0e-141">Aşağıdaki kod örneği, bir talep türüyle bir özel talep oluşturur `http://example.org/claims/complexcustomclaim`, bir özel kaynak türü `MyResourceType`ile <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> doğru.</span><span class="sxs-lookup"><span data-stu-id="05a0e-141">The following code example creates a custom claim with a claim type of `http://example.org/claims/complexcustomclaim`, a custom resource type of `MyResourceType`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)] 
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]     
  
## <a name="example"></a><span data-ttu-id="05a0e-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="05a0e-142">Example</span></span>  
 <span data-ttu-id="05a0e-143">Aşağıdaki kod örneğinde ilkel kaynak türüne sahip bir özel talep ve bir özel talep basit olmayan kaynak türü ile nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="05a0e-143">The following code example demonstrates how to create a custom claim with a primitive resource type and a custom claim with a non-primitive resource type.</span></span>  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="05a0e-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="05a0e-144">See Also</span></span>  
 <xref:System.IdentityModel.Claims.Claim>  
 <xref:System.IdentityModel.Claims.Rights>  
 <xref:System.IdentityModel.Claims.ClaimTypes>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [<span data-ttu-id="05a0e-145">Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme</span><span class="sxs-lookup"><span data-stu-id="05a0e-145">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [<span data-ttu-id="05a0e-146">Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme</span><span class="sxs-lookup"><span data-stu-id="05a0e-146">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
