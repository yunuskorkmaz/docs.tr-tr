---
title: "Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
caps.latest.revision: "27"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f452a32b209c30175f95aec7a8a90e0783c10086
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="runtime-directives-rdxml-configuration-file-reference"></a><span data-ttu-id="8e486-102">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="8e486-102">Runtime Directives (rd.xml) Configuration File Reference</span></span>
<span data-ttu-id="8e486-103">Çalışma zamanı yönergeleri (. rd.xml) atanan program öğeleri yansıma için kullanılabilir olup olmadığını belirten bir XML yapılandırma dosyasını bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="8e486-103">A runtime directives (.rd.xml) file is an XML configuration file that specifies whether designated program elements are available for reflection.</span></span> <span data-ttu-id="8e486-104">Aşağıda, bir çalışma zamanı yönergeleri dosyası örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="8e486-104">Here’s an example of a runtime directives file:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
<Application>  
  <Namespace Name="Contoso.Cloud.AppServices" Serialize="Required Public" />  
  <Namespace Name="ContosoClient.ViewModels" Serialize="Required Public" />  
  <Namespace Name="ContosoClient.DataModel" Serialize="Required Public" />  
  <Namespace Name="Contoso.Reader.UtilityLib" Serialize="Required Public" />  
  
  <Namespace Name="System.Collections.ObjectModel" >  
    <TypeInstantiation Name="ObservableCollection"   
          Arguments="ContosoClient.DataModel.ProductItem" Serialize="Public" />  
    <TypeInstantiation Name="ReadOnlyObservableCollection"   
          Arguments="ContosoClient.DataModel.ProductGroup" Serialize="Public" />  
  </Namespace>  
</Application>  
</Directives>  
```  
  
## <a name="the-structure-of-a-runtime-directives-file"></a><span data-ttu-id="8e486-105">Bir çalışma zamanı yönergeleri dosyasının yapısı</span><span class="sxs-lookup"><span data-stu-id="8e486-105">The structure of a runtime directives file</span></span>  
 <span data-ttu-id="8e486-106">Çalışma zamanı yönergeleri kullanan dosya `http://schemas.microsoft.com/netfx/2013/01/metadata` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="8e486-106">The runtime directives file uses the `http://schemas.microsoft.com/netfx/2013/01/metadata` namespace.</span></span>  
  
 <span data-ttu-id="8e486-107">Kök öğe [yönergeleri](../../../docs/framework/net-native/directives-element-net-native.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-107">The root element is the [Directives](../../../docs/framework/net-native/directives-element-net-native.md) element.</span></span> <span data-ttu-id="8e486-108">Sıfır veya daha fazla içerebilir [Kitaplığı](../../../docs/framework/net-native/library-element-net-native.md) öğeleri ve sıfır veya bir [uygulama](../../../docs/framework/net-native/application-element-net-native.md) aşağıdaki yapısında gösterildiği gibi öğesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-108">It can contain zero or more [Library](../../../docs/framework/net-native/library-element-net-native.md) elements, and zero or one [Application](../../../docs/framework/net-native/application-element-net-native.md) element, as shown in the following structure.</span></span> <span data-ttu-id="8e486-109">Özniteliklerini [uygulama](../../../docs/framework/net-native/application-element-net-native.md) öğesi, uygulama genelinde çalışma zamanı yansıma ilkesi tanımlayabilirsiniz ya da alt öğeleri için bir kapsayıcı olarak hizmet verebilir.</span><span class="sxs-lookup"><span data-stu-id="8e486-109">The attributes of the [Application](../../../docs/framework/net-native/application-element-net-native.md) element can define application-wide runtime reflection policy, or it can serve as a container for child elements.</span></span> <span data-ttu-id="8e486-110">[Kitaplığı](../../../docs/framework/net-native/library-element-net-native.md) öğesi, diğer yandan, yalnızca bir kapsayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-110">The [Library](../../../docs/framework/net-native/library-element-net-native.md) element, on the other hand, is simply a container.</span></span> <span data-ttu-id="8e486-111">Alt [uygulama](../../../docs/framework/net-native/application-element-net-native.md) ve [Kitaplığı](../../../docs/framework/net-native/library-element-net-native.md) öğeleri türleri, yöntemleri, alanlar, özellikleri ve yansıma için kullanılabilir olan olayları tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="8e486-111">The children of the [Application](../../../docs/framework/net-native/application-element-net-native.md) and [Library](../../../docs/framework/net-native/library-element-net-native.md) elements define the types, methods, fields, properties, and events that are available for reflection.</span></span>  
  
 <span data-ttu-id="8e486-112">Başvuru bilgileri için aşağıdaki yapısından öğeleri seçin veya bkz [çalışma zamanı yönerge öğeleri](../../../docs/framework/net-native/runtime-directive-elements.md).</span><span class="sxs-lookup"><span data-stu-id="8e486-112">For reference information, choose elements from the following structure or see [Runtime Directive Elements](../../../docs/framework/net-native/runtime-directive-elements.md).</span></span> <span data-ttu-id="8e486-113">Aşağıdaki hiyerarşi içinde üç nokta özyinelemeli yapısı işaretler.</span><span class="sxs-lookup"><span data-stu-id="8e486-113">In the following hierarchy, the ellipsis marks a recursive structure.</span></span> <span data-ttu-id="8e486-114">Bu öğe, isteğe bağlı veya gerekli olup olmadığı ve varsa kullanılır, bilgi köşeli gösterir (bir veya daha çok) kaç tane izin verilir.</span><span class="sxs-lookup"><span data-stu-id="8e486-114">The information in brackets indicates whether that element is optional or required, and if it is used, how many instances (one or many) are allowed.</span></span>  
  
 <span data-ttu-id="8e486-115">[Yönergeleri](../../../docs/framework/net-native/directives-element-net-native.md) [1:1]</span><span class="sxs-lookup"><span data-stu-id="8e486-115">[Directives](../../../docs/framework/net-native/directives-element-net-native.md) [1:1]</span></span>  
 <span data-ttu-id="8e486-116">[Uygulama](../../../docs/framework/net-native/application-element-net-native.md) [0:1]</span><span class="sxs-lookup"><span data-stu-id="8e486-116">[Application](../../../docs/framework/net-native/application-element-net-native.md) [0:1]</span></span>  
 <span data-ttu-id="8e486-117">[Derleme](../../../docs/framework/net-native/assembly-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-117">[Assembly](../../../docs/framework/net-native/assembly-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-118">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-118">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-119">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-119">.</span></span> <span data-ttu-id="8e486-120">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-120">.</span></span> <span data-ttu-id="8e486-121">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-121">.</span></span>  
 <span data-ttu-id="8e486-122">[Tür](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-122">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-123">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-123">.</span></span> <span data-ttu-id="8e486-124">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-124">.</span></span> <span data-ttu-id="8e486-125">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-125">.</span></span>  
 <span data-ttu-id="8e486-126">[Typeınstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (genel tür oluşturulan) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-126">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="8e486-127">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-127">.</span></span> <span data-ttu-id="8e486-128">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-128">.</span></span> <span data-ttu-id="8e486-129">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-129">.</span></span>  
 <span data-ttu-id="8e486-130">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-130">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-131">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-131">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-132">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-132">.</span></span> <span data-ttu-id="8e486-133">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-133">.</span></span> <span data-ttu-id="8e486-134">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-134">.</span></span>  
 <span data-ttu-id="8e486-135">[Tür](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-135">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-136">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-136">.</span></span> <span data-ttu-id="8e486-137">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-137">.</span></span> <span data-ttu-id="8e486-138">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-138">.</span></span>  
 <span data-ttu-id="8e486-139">[Typeınstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (genel tür oluşturulan) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-139">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="8e486-140">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-140">.</span></span> <span data-ttu-id="8e486-141">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-141">.</span></span> <span data-ttu-id="8e486-142">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-142">.</span></span>  
 <span data-ttu-id="8e486-143">[Tür](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-143">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-144">[Alt türleri](../../../docs/framework/net-native/subtypes-element-net-native.md) (kapsayan tür alt sınıflarının) [O:1]</span><span class="sxs-lookup"><span data-stu-id="8e486-144">[Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md) (subclasses of the containing type) [O:1]</span></span>  
 <span data-ttu-id="8e486-145">[Tür](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-145">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-146">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-146">.</span></span> <span data-ttu-id="8e486-147">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-147">.</span></span> <span data-ttu-id="8e486-148">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-148">.</span></span>  
 <span data-ttu-id="8e486-149">[Typeınstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (genel tür oluşturulan) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-149">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="8e486-150">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-150">.</span></span> <span data-ttu-id="8e486-151">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-151">.</span></span> <span data-ttu-id="8e486-152">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-152">.</span></span>  
 <span data-ttu-id="8e486-153">[Attributeımplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) (bir özniteliği olan türünü içeren) [O:1]</span><span class="sxs-lookup"><span data-stu-id="8e486-153">[AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) (containing type is an attribute) [O:1]</span></span>  
 <span data-ttu-id="8e486-154">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-154">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-155">[Yöntem](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-155">[Method](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-156">[Parametre](../../../docs/framework/net-native/parameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-156">[Parameter](../../../docs/framework/net-native/parameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-157">[TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-157">[TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-158">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-158">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-159">[Methodınstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (genel yöntem oluşturulan) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-159">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>  
 <span data-ttu-id="8e486-160">[Özellik](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-160">[Property](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-161">[Alan](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-161">[Field](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-162">[Olay](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-162">[Event](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-163">[Typeınstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (genel tür oluşturulan) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-163">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="8e486-164">[Tür](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-164">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-165">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-165">.</span></span> <span data-ttu-id="8e486-166">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-166">.</span></span> <span data-ttu-id="8e486-167">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-167">.</span></span>  
 <span data-ttu-id="8e486-168">[Typeınstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (genel tür oluşturulan) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-168">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="8e486-169">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-169">.</span></span> <span data-ttu-id="8e486-170">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-170">.</span></span> <span data-ttu-id="8e486-171">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-171">.</span></span>  
 <span data-ttu-id="8e486-172">[Yöntem](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-172">[Method](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-173">[Parametre](../../../docs/framework/net-native/parameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-173">[Parameter](../../../docs/framework/net-native/parameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-174">[TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-174">[TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-175">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-175">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-176">[Methodınstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (genel yöntem oluşturulan) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-176">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>  
 <span data-ttu-id="8e486-177">[Özellik](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-177">[Property](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-178">[Alan](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-178">[Field](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-179">[Olay](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-179">[Event](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-180">[Kitaplık](../../../docs/framework/net-native/library-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-180">[Library](../../../docs/framework/net-native/library-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-181">[Derleme](../../../docs/framework/net-native/assembly-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-181">[Assembly](../../../docs/framework/net-native/assembly-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-182">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-182">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-183">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-183">.</span></span> <span data-ttu-id="8e486-184">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-184">.</span></span> <span data-ttu-id="8e486-185">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-185">.</span></span>  
 <span data-ttu-id="8e486-186">[Tür](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-186">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-187">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-187">.</span></span> <span data-ttu-id="8e486-188">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-188">.</span></span> <span data-ttu-id="8e486-189">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-189">.</span></span>  
 <span data-ttu-id="8e486-190">[Typeınstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (genel tür oluşturulan) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-190">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="8e486-191">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-191">.</span></span> <span data-ttu-id="8e486-192">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-192">.</span></span> <span data-ttu-id="8e486-193">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-193">.</span></span>  
 <span data-ttu-id="8e486-194">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-194">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-195">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-195">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-196">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-196">.</span></span> <span data-ttu-id="8e486-197">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-197">.</span></span> <span data-ttu-id="8e486-198">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-198">.</span></span>  
 <span data-ttu-id="8e486-199">[Tür](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-199">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-200">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-200">.</span></span> <span data-ttu-id="8e486-201">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-201">.</span></span> <span data-ttu-id="8e486-202">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-202">.</span></span>  
 <span data-ttu-id="8e486-203">[Typeınstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (genel tür oluşturulan) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-203">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="8e486-204">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-204">.</span></span> <span data-ttu-id="8e486-205">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-205">.</span></span> <span data-ttu-id="8e486-206">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-206">.</span></span>  
 <span data-ttu-id="8e486-207">[Tür](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-207">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-208">[Alt türleri](../../../docs/framework/net-native/subtypes-element-net-native.md) (kapsayan tür alt sınıflarının) [O:1]</span><span class="sxs-lookup"><span data-stu-id="8e486-208">[Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md) (subclasses of the containing type) [O:1]</span></span>  
 <span data-ttu-id="8e486-209">[Tür](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-209">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-210">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-210">.</span></span> <span data-ttu-id="8e486-211">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-211">.</span></span> <span data-ttu-id="8e486-212">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-212">.</span></span>  
 <span data-ttu-id="8e486-213">[Typeınstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (genel tür oluşturulan) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-213">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="8e486-214">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-214">.</span></span> <span data-ttu-id="8e486-215">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-215">.</span></span> <span data-ttu-id="8e486-216">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-216">.</span></span>  
 <span data-ttu-id="8e486-217">[Attributeımplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) (bir özniteliği olan türünü içeren) [O:1]</span><span class="sxs-lookup"><span data-stu-id="8e486-217">[AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) (containing type is an attribute) [O:1]</span></span>  
 <span data-ttu-id="8e486-218">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-218">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-219">[Yöntem](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-219">[Method](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-220">[Methodınstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (genel yöntem oluşturulan) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-220">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>  
 <span data-ttu-id="8e486-221">[Özellik](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-221">[Property](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-222">[Alan](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-222">[Field](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-223">[Olay](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-223">[Event](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-224">[Typeınstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (genel tür oluşturulan) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-224">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="8e486-225">[Tür](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-225">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-226">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-226">.</span></span> <span data-ttu-id="8e486-227">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-227">.</span></span> <span data-ttu-id="8e486-228">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-228">.</span></span>  
 <span data-ttu-id="8e486-229">[Typeınstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (genel tür oluşturulan) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-229">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="8e486-230">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-230">.</span></span> <span data-ttu-id="8e486-231">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-231">.</span></span> <span data-ttu-id="8e486-232">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e486-232">.</span></span>  
 <span data-ttu-id="8e486-233">[Yöntem](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-233">[Method](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-234">[Methodınstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (genel yöntem oluşturulan) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-234">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>  
 <span data-ttu-id="8e486-235">[Özellik](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-235">[Property](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-236">[Alan](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-236">[Field](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="8e486-237">[Olay](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="8e486-237">[Event](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span></span>  
  
 <span data-ttu-id="8e486-238">[Uygulama](../../../docs/framework/net-native/application-element-net-native.md) öğesi özniteliklere sahip olabilir veya ele İlkesi özniteliklerini sağlayabilirsiniz [çalışma zamanı yönerge ve ilke bölümü](#Directives).</span><span class="sxs-lookup"><span data-stu-id="8e486-238">The [Application](../../../docs/framework/net-native/application-element-net-native.md) element can have no attributes, or it can have the policy attributes discussed in the [Runtime directive and policy section](#Directives).</span></span>  
  
 <span data-ttu-id="8e486-239">A [Kitaplığı](../../../docs/framework/net-native/library-element-net-native.md) öğeye sahip tek bir öznitelik `Name`, bir kitaplık veya dosya uzantısı olmadan derleme adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8e486-239">A [Library](../../../docs/framework/net-native/library-element-net-native.md) element has a single attribute, `Name`, that specifies the name of a library or assembly, without its file extension.</span></span> <span data-ttu-id="8e486-240">Örneğin, aşağıdaki [Kitaplığı](../../../docs/framework/net-native/library-element-net-native.md) öğesi Extensions.dll adlı bir derleme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8e486-240">For example, the following [Library](../../../docs/framework/net-native/library-element-net-native.md) element applies to an assembly named Extensions.dll.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
     <!-- Child elements go here -->    
  </Application>  
  <Library Name="Extensions">  
     <!-- Child elements go here -->    
  </Library>  
</Directives>  
```  
  
<a name="Directives"></a>   
## <a name="runtime-directives-and-policy"></a><span data-ttu-id="8e486-241">Çalışma zamanı yönergeleri ve ilke</span><span class="sxs-lookup"><span data-stu-id="8e486-241">Runtime directives and policy</span></span>  
 <span data-ttu-id="8e486-242">[Uygulama](../../../docs/framework/net-native/application-element-net-native.md) öğenin kendisi ve alt öğeleri [Kitaplığı](../../../docs/framework/net-native/library-element-net-native.md) ve [uygulama](../../../docs/framework/net-native/application-element-net-native.md) öğeleri express İlkesi; diğer bir deyişle, bunlar uygulama uygulayabileceğiniz biçimini tanımlayın Yansıma bir program öğesi için.</span><span class="sxs-lookup"><span data-stu-id="8e486-242">The [Application](../../../docs/framework/net-native/application-element-net-native.md) element itself and the child elements of the [Library](../../../docs/framework/net-native/library-element-net-native.md) and [Application](../../../docs/framework/net-native/application-element-net-native.md) elements express policy; that is, they define the way in which an app can apply reflection to a program element.</span></span> <span data-ttu-id="8e486-243">İlke türü bir öğe özniteliği tarafından tanımlanan (örneğin, `Serialize`).</span><span class="sxs-lookup"><span data-stu-id="8e486-243">The policy type is defined by an attribute of the element (for example, `Serialize`).</span></span> <span data-ttu-id="8e486-244">Bir ilke değeri özniteliğinin değeri tarafından tanımlanır (örneğin, `Serialize="Required"`).</span><span class="sxs-lookup"><span data-stu-id="8e486-244">The policy value is defined by the attribute’s value (for example, `Serialize="Required"`).</span></span>  
  
 <span data-ttu-id="8e486-245">Bu ilke için bir değer belirtmezseniz tüm alt öğeleri öğenin bir özniteliği tarafından belirtilen herhangi bir ilke uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8e486-245">Any policy specified by an attribute of an element applies to all child elements that don’t specify a value for that policy.</span></span> <span data-ttu-id="8e486-246">Örneğin, bir ilke tarafından belirtilen bir [türü](../../../docs/framework/net-native/type-element-net-native.md) içerdiği tüm türleri ve üyeleri için bir ilke açıkça belirtilmedi için ilke geçerli öğe.</span><span class="sxs-lookup"><span data-stu-id="8e486-246">For example, if a policy is specified by a [Type](../../../docs/framework/net-native/type-element-net-native.md) element, that policy applies to all contained types and members for which a policy is not explicitly specified.</span></span>  
  
 <span data-ttu-id="8e486-247">Tarafından ifade İlkesi [uygulama](../../../docs/framework/net-native/application-element-net-native.md), [derleme](../../../docs/framework/net-native/assembly-element-net-native.md), [Attributeımplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md), [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md), [ Alt türleri](../../../docs/framework/net-native/subtypes-element-net-native.md), ve [türü](../../../docs/framework/net-native/type-element-net-native.md) öğeleri tek tek üyeleri için ifade İlkesi farklıdır (tarafından [yöntemi](../../../docs/framework/net-native/method-element-net-native.md), [özelliği](../../../docs/framework/net-native/property-element-net-native.md), [Alan](../../../docs/framework/net-native/field-element-net-native.md), ve [olay](../../../docs/framework/net-native/event-element-net-native.md) öğeleri).</span><span class="sxs-lookup"><span data-stu-id="8e486-247">The policy that can be expressed by the [Application](../../../docs/framework/net-native/application-element-net-native.md), [Assembly](../../../docs/framework/net-native/assembly-element-net-native.md), [AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md), [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md), [Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md), and [Type](../../../docs/framework/net-native/type-element-net-native.md) elements differs from the policy that can be expressed for individual members (by the [Method](../../../docs/framework/net-native/method-element-net-native.md), [Property](../../../docs/framework/net-native/property-element-net-native.md), [Field](../../../docs/framework/net-native/field-element-net-native.md), and [Event](../../../docs/framework/net-native/event-element-net-native.md) elements).</span></span>  
  
### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a><span data-ttu-id="8e486-248">Derlemeler, ad alanları ve türler için ilkesini belirtme</span><span class="sxs-lookup"><span data-stu-id="8e486-248">Specifying policy for assemblies, namespaces, and types</span></span>  
 <span data-ttu-id="8e486-249">[Uygulama](../../../docs/framework/net-native/application-element-net-native.md), [derleme](../../../docs/framework/net-native/assembly-element-net-native.md), [Attributeımplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md), [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md), [Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md)ve [ Tür](../../../docs/framework/net-native/type-element-net-native.md) öğeleri aşağıdaki ilke türlerinden destekler:</span><span class="sxs-lookup"><span data-stu-id="8e486-249">The [Application](../../../docs/framework/net-native/application-element-net-native.md), [Assembly](../../../docs/framework/net-native/assembly-element-net-native.md), [AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md), [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md), [Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md), and [Type](../../../docs/framework/net-native/type-element-net-native.md) elements support the following policy types:</span></span>  
  
-   <span data-ttu-id="8e486-250">`Activate`.</span><span class="sxs-lookup"><span data-stu-id="8e486-250">`Activate`.</span></span> <span data-ttu-id="8e486-251">Örneklerinin etkinleştirmesi Oluşturucular, çalışma zamanı erişimi kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="8e486-251">Controls runtime access to constructors, to enable activation of instances.</span></span>  
  
-   <span data-ttu-id="8e486-252">`Browse`.</span><span class="sxs-lookup"><span data-stu-id="8e486-252">`Browse`.</span></span> <span data-ttu-id="8e486-253">Program öğeleri hakkında bilgi için sorgulama kontrol eder, ancak herhangi bir çalışma zamanı erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="8e486-253">Controls querying for information about program elements but does not enable any runtime access.</span></span>  
  
-   <span data-ttu-id="8e486-254">`Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="8e486-254">`Dynamic`.</span></span> <span data-ttu-id="8e486-255">Dinamik programlama etkinleştirmek için Oluşturucular, yöntemleri, alanları, özellikleri ve olayları dahil tüm tür üyeleri, çalışma zamanı erişimi kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="8e486-255">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>  
  
-   <span data-ttu-id="8e486-256">`Serialize`.</span><span class="sxs-lookup"><span data-stu-id="8e486-256">`Serialize`.</span></span> <span data-ttu-id="8e486-257">Oluşturucular, alanları ve seri hale getirilmiş ve üçüncü taraf kitaplıklar gibi Newtonsoft JSON seri hale getirici tarafından seri türü örnekleri etkinleştirmek için özellikleri, çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="8e486-257">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and serialized by third-party libraries such as the Newtonsoft JSON serializer.</span></span>  
  
-   <span data-ttu-id="8e486-258">`DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="8e486-258">`DataContractSerializer`.</span></span> <span data-ttu-id="8e486-259">Denetimleri kullanan serileştirme için ilke <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8e486-259">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>  
  
-   <span data-ttu-id="8e486-260">`DataContractJsonSerializer`.</span><span class="sxs-lookup"><span data-stu-id="8e486-260">`DataContractJsonSerializer`.</span></span> <span data-ttu-id="8e486-261">Denetimleri kullanan JSON serileştirmesi için ilke <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8e486-261">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>  
  
-   <span data-ttu-id="8e486-262">`XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="8e486-262">`XmlSerializer`.</span></span> <span data-ttu-id="8e486-263">Denetimleri kullanan XML serileştirme için ilke <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8e486-263">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>  
  
-   <span data-ttu-id="8e486-264">`MarshalObject`.</span><span class="sxs-lookup"><span data-stu-id="8e486-264">`MarshalObject`.</span></span> <span data-ttu-id="8e486-265">Başvuru türleri WinRT ve COM hazırlama için ilke denetler</span><span class="sxs-lookup"><span data-stu-id="8e486-265">Controls policy for marshaling reference types to WinRT and COM.</span></span>  
  
-   <span data-ttu-id="8e486-266">`MarshalDelegate`.</span><span class="sxs-lookup"><span data-stu-id="8e486-266">`MarshalDelegate`.</span></span> <span data-ttu-id="8e486-267">Yerel kod için işlev işaretçileri olarak temsilci türleri hazırlama için ilke denetler.</span><span class="sxs-lookup"><span data-stu-id="8e486-267">Controls policy for marshaling delegate types as function pointers to native code.</span></span>  
  
-   <span data-ttu-id="8e486-268">`MarshalStructure` .</span><span class="sxs-lookup"><span data-stu-id="8e486-268">`MarshalStructure` .</span></span> <span data-ttu-id="8e486-269">Yerel kod yapılara hazırlama için ilke denetler.</span><span class="sxs-lookup"><span data-stu-id="8e486-269">Controls policy for marshaling structures to native code.</span></span>  
  
 <span data-ttu-id="8e486-270">Bu ilke türleri ile ilişkili ayarları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8e486-270">The settings associated with these policy types are:</span></span>  
  
-   <span data-ttu-id="8e486-271">`All`.</span><span class="sxs-lookup"><span data-stu-id="8e486-271">`All`.</span></span> <span data-ttu-id="8e486-272">Tüm türleri ve araç zinciri kaldırmıyor üyeleri için ilkeyi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="8e486-272">Enable the policy for all types and members that the tool chain does not remove.</span></span>  
  
-   <span data-ttu-id="8e486-273">`Auto`.</span><span class="sxs-lookup"><span data-stu-id="8e486-273">`Auto`.</span></span> <span data-ttu-id="8e486-274">Varsayılan davranışını kullanın.</span><span class="sxs-lookup"><span data-stu-id="8e486-274">Use the default behavior.</span></span> <span data-ttu-id="8e486-275">(Bir ilke belirtmeden Bu ilke ayarını için eşdeğer `Auto` Bu ilke, örneğin bir üst öğe tarafından geçersiz kılınmadığı sürece.)</span><span class="sxs-lookup"><span data-stu-id="8e486-275">(Not specifying a policy is equivalent to setting that policy to `Auto` unless that policy is overridden, for example by a parent element.)</span></span>  
  
-   <span data-ttu-id="8e486-276">`Excluded`.</span><span class="sxs-lookup"><span data-stu-id="8e486-276">`Excluded`.</span></span> <span data-ttu-id="8e486-277">Bir program öğesi için ilke devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="8e486-277">Disable the policy for the program element.</span></span>  
  
-   <span data-ttu-id="8e486-278">`Public`.</span><span class="sxs-lookup"><span data-stu-id="8e486-278">`Public`.</span></span> <span data-ttu-id="8e486-279">Araç zinciri üye gerekli değildir ve bu nedenle kaldırır belirler sürece genel türleri veya üyeleri için ilke etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="8e486-279">Enable the policy for public types or members unless the tool chain determines that the member is unnecessary and therefore removes it.</span></span> <span data-ttu-id="8e486-280">(İkinci durumda, kullanmalısınız `Required Public` sağlamak üye tutulur ve yansıma özellikleri vardır.)</span><span class="sxs-lookup"><span data-stu-id="8e486-280">(In the latter case, you must use `Required Public` to ensure that the member is kept and has reflection capabilities.)</span></span>  
  
-   <span data-ttu-id="8e486-281">`PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="8e486-281">`PublicAndInternal`.</span></span> <span data-ttu-id="8e486-282">Araç zinciri bunları kaldırmaz, ortak ve iç türleri veya üyeleri için ilke etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="8e486-282">Enable the policy for public and internal types or members if the tool chain doesn't remove them.</span></span>  
  
-   <span data-ttu-id="8e486-283">`Required Public`.</span><span class="sxs-lookup"><span data-stu-id="8e486-283">`Required Public`.</span></span> <span data-ttu-id="8e486-284">Genel türler ve desteklemediğini kullanılan üyeler tutmak için araç zinciri gerektirir ve bunlar için ilkeyi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="8e486-284">Require the tool chain to keep public types and members whether or not they are used, and enable the policy for them.</span></span>  
  
-   <span data-ttu-id="8e486-285">`Required PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="8e486-285">`Required PublicAndInternal`.</span></span> <span data-ttu-id="8e486-286">Genel ve iç türleri ve desteklemediğini kullanılan üyeler tutmak için araç zinciri gerektirir ve bunlar için ilkeyi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="8e486-286">Require the tool chain to keep both public and internal types and members whether or not they are used, and enable the policy for them.</span></span>  
  
-   <span data-ttu-id="8e486-287">`Required All`.</span><span class="sxs-lookup"><span data-stu-id="8e486-287">`Required All`.</span></span> <span data-ttu-id="8e486-288">Tüm türleri ve desteklemediğini kullanılan üyeler tutmak için araç zinciri gerektirir ve bunlar için ilkeyi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="8e486-288">Require the tool chain to keep all types and members whether or not they are used, and enable the policy for them.</span></span>  
  
 <span data-ttu-id="8e486-289">Örneğin, şu çalışma zamanı yönergeleri dosya İlkesi tüm türleri ve üyeleri için derleme DataClasses.dll tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8e486-289">For example, the following runtime directives file defines policy for all types and members in the assembly DataClasses.dll.</span></span> <span data-ttu-id="8e486-290">Tüm ortak özellikler, tüm türleri ve tür üyeleri için gözatma etkinleştirir serileştirmek tüm türler için etkinleştirme sağlar yansıma sağlar (nedeniyle `Dynamic` özniteliği) ve yansıma tüm genel türleri ve üyeleri için etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="8e486-290">It enables reflection for serialization of all public properties, enables browsing for all types and type members, enables activation for all types (because of the `Dynamic` attribute), and enables reflection for all public types and members.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="Required Public"   
                Browse="All" Activate="PublicAndInternal"   
                Dynamic="Public"  />  
   </Application>  
   <Library Name="UtilityLibrary">  
     <!-- Child elements go here -->    
   </Library>  
</Directives>  
```  
  
### <a name="specifying-policy-for-members"></a><span data-ttu-id="8e486-291">Üyeler için ilkesini belirtme</span><span class="sxs-lookup"><span data-stu-id="8e486-291">Specifying policy for members</span></span>  
 <span data-ttu-id="8e486-292">[Özelliği](../../../docs/framework/net-native/property-element-net-native.md) ve [alan](../../../docs/framework/net-native/field-element-net-native.md) öğeleri aşağıdaki ilke türlerinden destekler:</span><span class="sxs-lookup"><span data-stu-id="8e486-292">The [Property](../../../docs/framework/net-native/property-element-net-native.md) and [Field](../../../docs/framework/net-native/field-element-net-native.md) elements support the following policy types:</span></span>  
  
-   <span data-ttu-id="8e486-293">`Browse`-Denetimleri bu üye hakkında bilgi için sorgulama ancak herhangi bir çalışma zamanı erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="8e486-293">`Browse` - Controls querying for information about this member but does not enable any runtime access.</span></span>  
  
-   <span data-ttu-id="8e486-294">`Dynamic`-Dinamik programlama etkinleştirmek için Oluşturucular, yöntemleri, alanları, özellikleri ve olayları dahil tüm tür üyeleri, çalışma zamanı erişimi kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="8e486-294">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="8e486-295">Ayrıca, kapsayan tür hakkında bilgi için sorgulama denetler.</span><span class="sxs-lookup"><span data-stu-id="8e486-295">Also controls querying for information about the containing type.</span></span>  
  
-   <span data-ttu-id="8e486-296">`Serialize`-Sıralanabilir ve kitaplıklar gibi Newtonsoft JSON seri hale getirici tarafından seri türü örnekleri etkinleştirmek için üye çalışma zamanı erişimi kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="8e486-296">`Serialize` - Controls runtime access to the member to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span> <span data-ttu-id="8e486-297">Bu ilke, Oluşturucular, alanlar ve özellikler için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="8e486-297">This policy can be applied to constructors, fields, and properties.</span></span>  
  
 <span data-ttu-id="8e486-298">[Yöntemi](../../../docs/framework/net-native/method-element-net-native.md) ve [olay](../../../docs/framework/net-native/event-element-net-native.md) öğeleri aşağıdaki ilke türlerinden destekler:</span><span class="sxs-lookup"><span data-stu-id="8e486-298">The [Method](../../../docs/framework/net-native/method-element-net-native.md) and [Event](../../../docs/framework/net-native/event-element-net-native.md) elements support the following policy types:</span></span>  
  
-   <span data-ttu-id="8e486-299">`Browse`-Denetimleri bu üye hakkında bilgi için sorgulama ancak herhangi bir çalışma zamanı erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="8e486-299">`Browse` - Controls querying for information about this member but doesn’t enable any runtime access.</span></span>  
  
-   <span data-ttu-id="8e486-300">`Dynamic`-Dinamik programlama etkinleştirmek için Oluşturucular, yöntemleri, alanları, özellikleri ve olayları dahil tüm tür üyeleri, çalışma zamanı erişimi kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="8e486-300">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="8e486-301">Ayrıca, kapsayan tür hakkında bilgi için sorgulama denetler.</span><span class="sxs-lookup"><span data-stu-id="8e486-301">Also controls querying for information about the containing type.</span></span>  
  
 <span data-ttu-id="8e486-302">Bu ilke türleri ile ilişkili ayarları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8e486-302">The settings associated with these policy types are:</span></span>  
  
-   <span data-ttu-id="8e486-303">`Auto`-Varsayılan davranışını kullanın.</span><span class="sxs-lookup"><span data-stu-id="8e486-303">`Auto` - Use the default behavior.</span></span> <span data-ttu-id="8e486-304">(Bir ilke belirtmeden Bu ilke ayarını için eşdeğer `Auto` bir şey geçersiz kılmadıkça.)</span><span class="sxs-lookup"><span data-stu-id="8e486-304">(Not specifying a policy is equivalent to setting that policy to `Auto` unless something overrides it.)</span></span>  
  
-   <span data-ttu-id="8e486-305">`Excluded`-Hiç üye için meta verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="8e486-305">`Excluded` - Never include metadata for the member.</span></span>  
  
-   <span data-ttu-id="8e486-306">`Included`-Üst tür çıktıda varsa, ilke etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="8e486-306">`Included` - Enable the policy if the parent type is present in the output.</span></span>  
  
-   <span data-ttu-id="8e486-307">`Required`-Bu üye tutmak için araç zinciri gerektiren bile görünüyor kullanılmayan ve ilke için etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="8e486-307">`Required` - Require the tool chain to keep this member even if appears to be unused, and enable policy for it.</span></span>  
  
## <a name="runtime-directives-file-semantics"></a><span data-ttu-id="8e486-308">Çalışma zamanı yönergeleri dosya semantiği</span><span class="sxs-lookup"><span data-stu-id="8e486-308">Runtime directives file semantics</span></span>  
 <span data-ttu-id="8e486-309">İlke için üst düzey ve alt düzey öğeleri eşzamanlı olarak tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="8e486-309">Policy can be defined simultaneously for both higher-level and lower-level elements.</span></span> <span data-ttu-id="8e486-310">Örneğin, ilke bir derlemenin ve bu derleme içinde yer alan türlerinden bazıları için tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="8e486-310">For example, policy can be defined for an assembly, and for some of the types contained in that assembly.</span></span> <span data-ttu-id="8e486-311">Belirli bir alt düzey öğesinin temsil edilmeyen, kendi üst ilkesini devralır.</span><span class="sxs-lookup"><span data-stu-id="8e486-311">If a particular lower-level element is not represented, it inherits the policy of its parent.</span></span> <span data-ttu-id="8e486-312">Örneğin, varsa bir `Assembly` öğe varsa ancak `Type` öğeleri olmayan, ilke içinde belirtilen `Assembly` derlemesinde her türünü öğesi uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8e486-312">For example, if an `Assembly` element is present but `Type` elements are not, the policy specified in the `Assembly` element applies to each type in the assembly.</span></span> <span data-ttu-id="8e486-313">Birden çok öğe aynı program öğesi için ilke geçerli olabilir.</span><span class="sxs-lookup"><span data-stu-id="8e486-313">Multiple elements can also apply policy to the same program element.</span></span> <span data-ttu-id="8e486-314">Örneğin, ayrı [derleme](../../../docs/framework/net-native/assembly-element-net-native.md) öğeleri tanımlamak aynı ilke öğesi için aynı bütünleştirilmiş kodda farklı.</span><span class="sxs-lookup"><span data-stu-id="8e486-314">For example, separate [Assembly](../../../docs/framework/net-native/assembly-element-net-native.md) elements might define the same policy element for the same assembly differently.</span></span> <span data-ttu-id="8e486-315">Aşağıdaki bölümler, belirli bir tür için ilke bu gibi durumlarda nasıl çözümleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="8e486-315">The following sections explain how the policy for a particular type is resolved in those cases.</span></span>  
  
 <span data-ttu-id="8e486-316">A [türü](../../../docs/framework/net-native/type-element-net-native.md) veya [yöntemi](../../../docs/framework/net-native/method-element-net-native.md) öğesi genel türü veya yöntemi kendi ilke olmayan tüm örneklemesi kendi ilke uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8e486-316">A [Type](../../../docs/framework/net-native/type-element-net-native.md) or [Method](../../../docs/framework/net-native/method-element-net-native.md) element of a generic type or method applies its policy to all instantiations that do not have their own policy.</span></span> <span data-ttu-id="8e486-317">Örneğin, bir `Type` ilkesini belirtir öğesi <xref:System.Collections.Generic.List%601> belirli bir genel tür oluşturulan için kılınmadığı sürece genel bu türdeki tüm oluşturulan örnekleri için geçerlidir (gibi bir `List<Int32>`) tarafından bir `TypeInstantiation` öğesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-317">For example, a `Type` element that specifies policy for <xref:System.Collections.Generic.List%601> applies to all constructed instances of that generic type, unless it's overridden for a particular constructed generic type (such as a `List<Int32>`) by a `TypeInstantiation` element.</span></span> <span data-ttu-id="8e486-318">Aksi takdirde, öğeleri adlı bir program öğesi için bir ilke tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="8e486-318">Otherwise, elements define policy for the program element named.</span></span>  
  
 <span data-ttu-id="8e486-319">Bir öğenin belirsiz olduğunda, altyapı eşleşmeleri arar ve tam bir eşleşme bulursa, onu kullanır.</span><span class="sxs-lookup"><span data-stu-id="8e486-319">When an element is ambiguous, the engine looks for matches, and if it finds an exact match, it will use it.</span></span> <span data-ttu-id="8e486-320">Birden çok eşleşme bulursa, bir uyarı veya hata olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="8e486-320">If it finds multiple matches, there will be a warning or error.</span></span>  
  
### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a><span data-ttu-id="8e486-321">İki yönergeleri aynı program öğesi için ilke uygularsanız</span><span class="sxs-lookup"><span data-stu-id="8e486-321">If two directives apply policy to the same program element</span></span>  
 <span data-ttu-id="8e486-322">Farklı çalışma zamanı yönergeleri dosyalarındaki iki öğe aynı ilke türü (örneğin, bir derleme veya tür) aynı program öğesi için farklı bir değere ayarlamaya çalışırsanız, çakışma gibi çözümlendi:</span><span class="sxs-lookup"><span data-stu-id="8e486-322">If two elements in different runtime directives files try to set the same policy type for the same program element (such as an assembly or type) to different values, the conflict is resolved as follows:</span></span>  
  
1.  <span data-ttu-id="8e486-323">Varsa `Excluded` öğesi mevcutsa, önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8e486-323">If the `Excluded` element is present, it has precedence.</span></span>  
  
2.  <span data-ttu-id="8e486-324">`Required`önceliğe sahip üstünde değil `Required`.</span><span class="sxs-lookup"><span data-stu-id="8e486-324">`Required` has precedence over not `Required`.</span></span>  
  
3.  <span data-ttu-id="8e486-325">`All`üzerinden önceliğe sahip `PublicAndInternal`, üzerinden önceliği olan `Public`.</span><span class="sxs-lookup"><span data-stu-id="8e486-325">`All` has precedence over `PublicAndInternal`, which has precedence over `Public`.</span></span>  
  
4.  <span data-ttu-id="8e486-326">Açık herhangi bir ayar üzerinden önceliğe sahip `Auto`.</span><span class="sxs-lookup"><span data-stu-id="8e486-326">Any explicit setting has precedence over `Auto`.</span></span>  
  
 <span data-ttu-id="8e486-327">Tek bir proje aşağıdaki iki çalışma zamanı yönergeleri dosyalar içeriyorsa, örneğin, serileştirme ilke DataClasses.dll için her iki ayarlanmışsa `Required Public` ve `All`.</span><span class="sxs-lookup"><span data-stu-id="8e486-327">For example, if a single project includes the following two runtime directives files, the serialization policy for DataClasses.dll is set to both `Required Public` and `All`.</span></span> <span data-ttu-id="8e486-328">Bu durumda, serileştirme ilke olarak çözümlenmiş olacaktır `Required All`.</span><span class="sxs-lookup"><span data-stu-id="8e486-328">In this case, the serialization policy would be resolved as `Required All`.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="Required Public"/>  
   </Application>  
   <Library Name="DataClasses">  
      <!-- any other elements -->  
   </Library>  
</Directives>  
```  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="All" />  
   </Application>  
   <Library Name="DataClasses">  
      <!-- any other elements -->  
   </Library>  
</Directives>  
```  
  
 <span data-ttu-id="8e486-329">Ancak, bir tek çalışma zamanı yönergeleri dosyasında iki yönergeleri aynı program öğesi için aynı ilke türü ayarlamaya çalışırsanız, XML Şeması tanımı aracı bir hata iletisi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8e486-329">However, if two directives in a single runtime directives file try to set the same policy type for the same program element, the XML Scheme Definition tool displays an error message.</span></span>  
  
### <a name="if-child-and-parent-elements-apply-the-same-policy-type"></a><span data-ttu-id="8e486-330">Alt ve üst öğeleri aynı ilke türü uygularsanız</span><span class="sxs-lookup"><span data-stu-id="8e486-330">If child and parent elements apply the same policy type</span></span>  
 <span data-ttu-id="8e486-331">Alt öğeler de dahil olmak üzere kendi üst öğeler geçersiz kılma `Excluded` ayarı.</span><span class="sxs-lookup"><span data-stu-id="8e486-331">Child elements override their parent elements, including the `Excluded` setting.</span></span> <span data-ttu-id="8e486-332">Geçersiz kılma olduğunu belirtmek için isteyeceğiniz ana nedeni `Auto`.</span><span class="sxs-lookup"><span data-stu-id="8e486-332">Overriding is the main reason you would want to specify `Auto`.</span></span>  
  
 <span data-ttu-id="8e486-333">Aşağıdaki örnekte, her şeyi için seri hale getirme ilkesini `DataClasses` olmayan içinde `DataClasses.ViewModels` olacaktır `Required Public`ve ikisi de olan her şeyi `DataClasses` ve `DataClasses.ViewModels` olacaktır `All`.</span><span class="sxs-lookup"><span data-stu-id="8e486-333">In the following example, the serialization policy setting for everything in `DataClasses` that’s not in `DataClasses.ViewModels` would be `Required Public`, and everything that's in both `DataClasses` and `DataClasses.ViewModels` would be `All`.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="Required Public" >  
         <Namespace Name="DataClasses.ViewModels" Seralize="All" />  
      </Assembly>  
   </Appliction>  
   <Library Name="DataClasses">  
      <!-- any other elements -->  
   </Library>  
</Directives>  
```  
  
### <a name="if-open-generics-and-instantiated-elements-apply-the-same-policy-type"></a><span data-ttu-id="8e486-334">Açık genel türler ve oluşturulan öğeleri aynı ilke türü uygulanacaksa</span><span class="sxs-lookup"><span data-stu-id="8e486-334">If open generics and instantiated elements apply the same policy type</span></span>  
 <span data-ttu-id="8e486-335">Aşağıdaki örnekte, `Dictionary<int,int>` atanan `Browse` yalnızca altyapısı onu vermek için başka bir neden varsa İlkesi `Browse` (Aksi takdirde varsayılan davranışı olur) ilkesini; sayısı her bir örneklemesi <xref:System.Collections.Generic.Dictionary%602> sahip olur üyeleri göz atılamaz.</span><span class="sxs-lookup"><span data-stu-id="8e486-335">In the following example, `Dictionary<int,int>` is assigned the `Browse` policy only if the engine has another reason to give it the `Browse` policy (which would otherwise be the default behavior); every other instantiation of <xref:System.Collections.Generic.Dictionary%602> will have all of its members browsable.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="Required Public" >  
         <Namespace Name="DataClasses.ViewModels" Seralize="All" />  
      </Assembly>  
      <Namespace Name="DataClasses.Generics" />  
      <Type Name="Dictionary" Browse="All" />  
      <TypeInstantiation Name="Dictionary"   
                         Arguments="System.Int32,System.Int32" Browse="Auto" />  
   </Application>  
   <Library Name="DataClasses">  
      <!-- any other elements -->  
   </Library>  
</Directives>  
```  
  
### <a name="how-policy-is-inferred"></a><span data-ttu-id="8e486-336">İlke nasıl algılanır</span><span class="sxs-lookup"><span data-stu-id="8e486-336">How policy is inferred</span></span>  
 <span data-ttu-id="8e486-337">Her ilke türünün farklı bir diğer yapıların Bu ilke türü varlığını nasıl etkilediğini belirlemek kural kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="8e486-337">Each policy type has a different set of rules that determine how the presence of that policy type affects other constructs.</span></span>  
  
#### <a name="the-effect-of-browse-policy"></a><span data-ttu-id="8e486-338">Gözat ilkesinin etkisini</span><span class="sxs-lookup"><span data-stu-id="8e486-338">The effect of Browse policy</span></span>  
 <span data-ttu-id="8e486-339">Uygulama `Browse` ilke türü için aşağıdaki ilke değişiklikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="8e486-339">Applying the `Browse` policy to a type involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="8e486-340">Türünün temel türü ile işaretlenmiş `Browse` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-340">The base type of the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="8e486-341">Bir oluşturulmuş genel türündeyse türü dizilerine sürümü ile işaretlenmiş `Browse` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-341">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="8e486-342">Türü bir delegate ise `Invoke` türünün yöntemi ile işaretlenmiş `Dynamic` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-342">If the type is a delegate, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="8e486-343">Her bir arabirime türü ile işaretlenmiş `Browse` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-343">Each interface of the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="8e486-344">Türü için uygulanan her bir öznitelik türü ile işaretlenmiş `Browse` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-344">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="8e486-345">Tür genel ise, her kısıtlama türü ile işaretlenmiş `Browse` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-345">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="8e486-346">Tür genel ise, türü örneği türleri ile işaretlenmiş `Browse` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-346">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>  
  
 <span data-ttu-id="8e486-347">Uygulama `Browse` ilke için bir yöntem aşağıdaki ilke değişiklikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="8e486-347">Applying the `Browse` policy to a method involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="8e486-348">Yöntem her parametre türü ile işaretlenmiş `Browse` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-348">Each parameter type of the method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="8e486-349">Yöntemin dönüş türünü işaretlenmiş `Browse` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-349">The return type of the method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="8e486-350">Yöntem içeren tür ile işaretlenmiş `Browse` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-350">The containing type of the method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="8e486-351">Yöntemi bir oluşturulmuş genel yöntem ise, dizilerine genel yöntem ile işaretlenmiş `Browse` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-351">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="8e486-352">Yöntemine uygulanan her bir öznitelik türü ile işaretlenmiş `Browse` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-352">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="8e486-353">Metodu genel ise, her kısıtlama türü ile işaretlenmiş `Browse` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-353">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="8e486-354">Metodu genel ise, yöntemi örneği türleri ile işaretlenir `Browse` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-354">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>  
  
 <span data-ttu-id="8e486-355">Uygulama `Browse` bir alana ilke aşağıdaki ilke değişiklikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="8e486-355">Applying the `Browse` policy to a field involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="8e486-356">Alana uygulanan her bir öznitelik türü ile işaretlenmiş `Browse` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-356">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="8e486-357">Alanın türü ile işaretlenmiş `Browse` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-357">The type of the field is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="8e486-358">Alanın ait olduğu tür ile işaretlenmiş `Browse` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-358">The type to which the field belongs is marked with the `Browse` policy.</span></span>  
  
#### <a name="the-effect-of-dynamic-policy"></a><span data-ttu-id="8e486-359">Dinamik ilkesinin etkisini</span><span class="sxs-lookup"><span data-stu-id="8e486-359">The effect of Dynamic policy</span></span>  
 <span data-ttu-id="8e486-360">Uygulama `Dynamic` ilke türü için aşağıdaki ilke değişiklikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="8e486-360">Applying the `Dynamic` policy to a type involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="8e486-361">Türünün temel türü ile işaretlenmiş `Dynamic` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-361">The base type of the type is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="8e486-362">Bir oluşturulmuş genel türündeyse türü dizilerine sürümü ile işaretlenmiş `Dynamic` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-362">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="8e486-363">Tür bir temsilci türü ise `Invoke` türünün yöntemi ile işaretlenmiş `Dynamic` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-363">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="8e486-364">Her bir arabirime türü ile işaretlenmiş `Browse` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-364">Each interface of the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="8e486-365">Türü için uygulanan her bir öznitelik türü ile işaretlenmiş `Browse` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-365">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="8e486-366">Tür genel ise, her kısıtlama türü ile işaretlenmiş `Browse` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-366">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="8e486-367">Tür genel ise, türü örneği türleri ile işaretlenmiş `Browse` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-367">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>  
  
 <span data-ttu-id="8e486-368">Uygulama `Dynamic` ilke için bir yöntem aşağıdaki ilke değişiklikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="8e486-368">Applying the `Dynamic` policy to a method involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="8e486-369">Yöntem her parametre türü ile işaretlenmiş `Browse` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-369">Each parameter type of the method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="8e486-370">Yöntemin dönüş türünü işaretlenmiş `Dynamic` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-370">The return type of the method is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="8e486-371">Yöntem içeren tür ile işaretlenmiş `Dynamic` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-371">The containing type of the method is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="8e486-372">Yöntemi bir oluşturulmuş genel yöntem ise, dizilerine genel yöntem ile işaretlenmiş `Browse` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-372">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="8e486-373">Yöntemine uygulanan her bir öznitelik türü ile işaretlenmiş `Browse` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-373">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="8e486-374">Metodu genel ise, her kısıtlama türü ile işaretlenmiş `Browse` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-374">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="8e486-375">Metodu genel ise, yöntemi örneği türleri ile işaretlenir `Browse` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-375">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="8e486-376">Yöntemi tarafından çağrılan `MethodInfo.Invoke`, ve temsilci oluşturma tarafından mümkün hale <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8e486-376">The method can be invoked by `MethodInfo.Invoke`, and delegate creation becomes possible by <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="8e486-377">Uygulama `Dynamic` bir alana ilke aşağıdaki ilke değişiklikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="8e486-377">Applying the `Dynamic` policy to a field involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="8e486-378">Alana uygulanan her bir öznitelik türü ile işaretlenmiş `Browse` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-378">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="8e486-379">Alanın türü ile işaretlenmiş `Dynamic` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-379">The type of the field is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="8e486-380">Alanın ait olduğu tür ile işaretlenmiş `Dynamic` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-380">The type to which the field belongs is marked with the `Dynamic` policy.</span></span>  
  
#### <a name="the-effect-of-activation-policy"></a><span data-ttu-id="8e486-381">Etkinleştirme ilkesinin etkisini</span><span class="sxs-lookup"><span data-stu-id="8e486-381">The effect of Activation policy</span></span>  
 <span data-ttu-id="8e486-382">Bir türe etkinleştirme İlkesi uygulama aşağıdaki ilke değişiklikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="8e486-382">Applying the Activation policy to a type involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="8e486-383">Bir oluşturulmuş genel türündeyse türü dizilerine sürümü ile işaretlenmiş `Browse` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-383">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="8e486-384">Tür bir temsilci türü ise `Invoke` türünün yöntemi ile işaretlenmiş `Dynamic` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-384">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="8e486-385">Oluşturucular türü ile işaretlenmiş `Activation` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-385">Constructors of the type are marked with the `Activation` policy.</span></span>  
  
 <span data-ttu-id="8e486-386">Uygulama `Activation` ilke için bir yöntem aşağıdaki ilke değişikliğini içerir:</span><span class="sxs-lookup"><span data-stu-id="8e486-386">Applying the `Activation` policy to a method involves the following policy change:</span></span>  
  
-   <span data-ttu-id="8e486-387">Oluşturucusu tarafından çağrılan <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> ve <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="8e486-387">The constructor can be invoked by the <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> and <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="8e486-388">Yöntemleri için `Activation` ilke yalnızca oluşturucular etkiler.</span><span class="sxs-lookup"><span data-stu-id="8e486-388">For methods, the `Activation` policy affects constructors only.</span></span>  
  
 <span data-ttu-id="8e486-389">Uygulama `Activation` bir alana İlkesi etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="8e486-389">Applying the `Activation` policy to a field has no effect.</span></span>  
  
#### <a name="the-effect-of-serialize-policy"></a><span data-ttu-id="8e486-390">Serileştirme ilkesinin etkisini</span><span class="sxs-lookup"><span data-stu-id="8e486-390">The effect of Serialize policy</span></span>  
 <span data-ttu-id="8e486-391">`Serialize` İlkesi ortak yansıma tabanlı serileştiricileri kullanımını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="8e486-391">The `Serialize` policy enables the use of common reflection-based serializers.</span></span> <span data-ttu-id="8e486-392">Ancak, Microsoft dışı serileştiricileri tam yansıma erişim desenlerini Microsoft'a bilinmiyor olduğundan, bu ilkeyi tamamen etkili olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="8e486-392">However, because the exact reflection access patterns of non-Microsoft serializers are not known to Microsoft, this policy may not be entirely effective.</span></span>  
  
 <span data-ttu-id="8e486-393">Uygulama `Serialize` ilke türü için aşağıdaki ilke değişiklikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="8e486-393">Applying the `Serialize` policy to a type involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="8e486-394">Türünün temel türü ile işaretlenmiş `Serialize` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-394">The base type of the type is marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="8e486-395">Bir oluşturulmuş genel türündeyse türü dizilerine sürümü ile işaretlenmiş `Browse` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-395">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="8e486-396">Tür bir temsilci türü ise `Invoke` türünün yöntemi ile işaretlenmiş `Dynamic` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-396">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="8e486-397">Bir numaralandırma türü ise, bir dizi türü ile işaretlenmiş `Serialize` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-397">If the type is an enumeration, an array of the type is marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="8e486-398">Türü uyguluyorsa <xref:System.Collections.Generic.IEnumerable%601>, `T` ile işaretlenen `Serialize` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-398">If the type implements <xref:System.Collections.Generic.IEnumerable%601>, `T` is marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="8e486-399">Tür ise <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>, veya <xref:System.Collections.Generic.IReadOnlyList%601>, ardından `T[]` ve <xref:System.Collections.Generic.List%601> ile işaretlenen `Serialize` ilkenin ancak hiçbir arabirim türü üyeleri ileişaretlenmiş`Serialize`ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-399">If the type is <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>, or <xref:System.Collections.Generic.IReadOnlyList%601>, then `T[]` and <xref:System.Collections.Generic.List%601> marked with the `Serialize` policy., but no members of the interface type are marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="8e486-400">Tür ise <xref:System.Collections.Generic.List%601>, hiçbir üye türü işaretlenir `Serialize` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-400">If the type is <xref:System.Collections.Generic.List%601>, no members of the type are marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="8e486-401">Tür ise <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> ile işaretlenen `Serialize` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-401">If the type is <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> is marked with the `Serialize` policy.</span></span> <span data-ttu-id="8e486-402">ancak hiçbir üye türü işaretlenir `Serialize` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-402">but no members of the type are marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="8e486-403">Tür ise <xref:System.Collections.Generic.Dictionary%602>, hiçbir üye türü işaretlenir `Serialize` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-403">If the type is <xref:System.Collections.Generic.Dictionary%602>, no members of the type are marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="8e486-404">Türü uyguluyorsa <xref:System.Collections.Generic.IDictionary%602>, `TKey` ve `TValue` işaretlenir `Serialize` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-404">If the type implements <xref:System.Collections.Generic.IDictionary%602>, `TKey` and `TValue` are marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="8e486-405">Her oluşturucusu, her özellik erişimcisini ve her bir alan ile işaretlenmiş `Serialize` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-405">Each constructor, each property accessor, and each field is marked with the `Serialize` policy.</span></span>  
  
 <span data-ttu-id="8e486-406">Uygulama `Serialize` ilke için bir yöntem aşağıdaki ilke değişiklikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="8e486-406">Applying the `Serialize` policy to a method involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="8e486-407">İçeren türü ile işaretlenmiş `Serialize` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-407">The containing type is marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="8e486-408">Yöntemin dönüş türünü işaretlenmiş `Serialize` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-408">The return type of the method is marked with the `Serialize` policy.</span></span>  
  
 <span data-ttu-id="8e486-409">Uygulama `Serialize` bir alana ilke aşağıdaki ilke değişiklikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="8e486-409">Applying the `Serialize` policy to a field involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="8e486-410">İçeren türü ile işaretlenmiş `Serialize` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-410">The containing type is marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="8e486-411">Alanın türü ile işaretlenmiş `Serialize` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="8e486-411">The type of the field is marked with the `Serialize` policy.</span></span>  
  
#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserialier-policies"></a><span data-ttu-id="8e486-412">XmlSerializer, DataContractSerializer ve DataContractJsonSerialier ilkelerinin etkisini</span><span class="sxs-lookup"><span data-stu-id="8e486-412">The effect of XmlSerializer, DataContractSerializer, and DataContractJsonSerialier policies</span></span>  
 <span data-ttu-id="8e486-413">Aksine `Serialize` yansıma tabanlı serileştiricileri için tasarlanmıştır, ilke `XmlSerializer`, `DataContractSerializer`, ve `DataContractJsonSerializer` bilinen serileştiricileri kümesi etkinleştirmek için kullanılan ilkeleri [!INCLUDE[net_native](../../../includes/net-native-md.md)] araç zinciri.</span><span class="sxs-lookup"><span data-stu-id="8e486-413">Unlike the `Serialize` policy, which is intended for reflection-based serializers, the `XmlSerializer`, `DataContractSerializer`, and `DataContractJsonSerializer` policies are used to enable a set of serializers that are known to the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain.</span></span> <span data-ttu-id="8e486-414">Yansıma kullanarak bu serileştiricileri uygulanmaz, ancak çalışma zamanında seri hale getirilebilir türler kümesi benzer bir şekilde reflectable türleri olarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="8e486-414">These serializers are not implemented by using reflection, but the set of types that can be serialized at run time is determined in a similar manner as types that are reflectable.</span></span>  
  
 <span data-ttu-id="8e486-415">Bu ilkeler birini türüne uygulama türü ile eşleşen seri hale getirici serileştirilmesi etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="8e486-415">Applying one of these policies to a type enables the type to be serialized with the matching serializer.</span></span> <span data-ttu-id="8e486-416">Ayrıca, serileştirme motoruna statik olarak serileştirme gerek olarak belirleyebilirsiniz türleri de seri hale getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8e486-416">Also, any types that the serialization engine can statically determine as needing serialization will also be serializable.</span></span>  
  
 <span data-ttu-id="8e486-417">Bu ilkeler yöntemleri veya alanlar üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="8e486-417">These policies have no effect on methods or fields.</span></span>  
  
 <span data-ttu-id="8e486-418">Daha fazla bilgi için "Serileştiricileri farklar" bölümüne bakın [geçirme Windows mağazası uygulamanızı .NET yerele](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="8e486-418">For more information, see the "Differences in Serializers" section in [Migrating Your Windows Store App to .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e486-419">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8e486-419">See Also</span></span>  
 [<span data-ttu-id="8e486-420">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="8e486-420">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="8e486-421">Yansıma ve .NET Native</span><span class="sxs-lookup"><span data-stu-id="8e486-421">Reflection and .NET Native</span></span>](../../../docs/framework/net-native/reflection-and-net-native.md)
