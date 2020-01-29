---
title: Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu
ms.date: 03/30/2017
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
ms.openlocfilehash: e74d34693446cca645003a9f93bc1777849e3182
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738412"
---
# <a name="runtime-directives-rdxml-configuration-file-reference"></a><span data-ttu-id="6f9f0-102">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="6f9f0-102">Runtime Directives (rd.xml) Configuration File Reference</span></span>

<span data-ttu-id="6f9f0-103">Çalışma zamanı yönergeleri (. RD. xml) dosyası, belirtilen program öğelerinin yansıma için kullanılabilir olup olmadığını belirten bir XML yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-103">A runtime directives (.rd.xml) file is an XML configuration file that specifies whether designated program elements are available for reflection.</span></span> <span data-ttu-id="6f9f0-104">Çalışma zamanı yönergeleri dosyasına bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="6f9f0-104">Here’s an example of a runtime directives file:</span></span>

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

## <a name="the-structure-of-a-runtime-directives-file"></a><span data-ttu-id="6f9f0-105">Çalışma zamanı yönergeleri dosyasının yapısı</span><span class="sxs-lookup"><span data-stu-id="6f9f0-105">The structure of a runtime directives file</span></span>

<span data-ttu-id="6f9f0-106">Çalışma zamanı yönergeleri dosyası `http://schemas.microsoft.com/netfx/2013/01/metadata` ad alanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-106">The runtime directives file uses the `http://schemas.microsoft.com/netfx/2013/01/metadata` namespace.</span></span>

<span data-ttu-id="6f9f0-107">Kök öğesi, [yönergeleri](directives-element-net-native.md) öğesidir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-107">The root element is the [Directives](directives-element-net-native.md) element.</span></span> <span data-ttu-id="6f9f0-108">Aşağıdaki yapıda gösterildiği gibi sıfır veya daha fazla [kitaplık](library-element-net-native.md) öğesi ve sıfır veya bir [uygulama](application-element-net-native.md) öğesi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-108">It can contain zero or more [Library](library-element-net-native.md) elements, and zero or one [Application](application-element-net-native.md) element, as shown in the following structure.</span></span> <span data-ttu-id="6f9f0-109">[Uygulama](application-element-net-native.md) öğesinin öznitelikleri, uygulama genelinde çalışma zamanı yansıma ilkesi tanımlayabilir veya alt öğeler için bir kapsayıcı olarak görev yapabilir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-109">The attributes of the [Application](application-element-net-native.md) element can define application-wide runtime reflection policy, or it can serve as a container for child elements.</span></span> <span data-ttu-id="6f9f0-110">Öte yandan [kitaplık](library-element-net-native.md) öğesi yalnızca bir kapsayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-110">The [Library](library-element-net-native.md) element, on the other hand, is simply a container.</span></span> <span data-ttu-id="6f9f0-111">[Uygulama](application-element-net-native.md) ve [kitaplık](library-element-net-native.md) öğelerinin alt öğeleri, yansıma için kullanılabilen türleri, yöntemleri, alanları, özellikleri ve olayları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-111">The children of the [Application](application-element-net-native.md) and [Library](library-element-net-native.md) elements define the types, methods, fields, properties, and events that are available for reflection.</span></span>

<span data-ttu-id="6f9f0-112">Başvuru bilgileri için aşağıdaki yapıdaki öğeleri seçin veya [çalışma zamanı yönerge öğelerini](runtime-directive-elements.md)görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-112">For reference information, choose elements from the following structure or see [Runtime Directive Elements](runtime-directive-elements.md).</span></span> <span data-ttu-id="6f9f0-113">Aşağıdaki hiyerarşide üç nokta özyinelemeli bir yapıyı işaret ediyor.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-113">In the following hierarchy, the ellipsis marks a recursive structure.</span></span> <span data-ttu-id="6f9f0-114">Köşeli ayraçlar içindeki bilgiler, bu öğenin isteğe bağlı veya gerekli olduğunu ve kullanılıp kullanılmadığını, kaç örneğe (bir veya daha fazla) izin verildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-114">The information in brackets indicates whether that element is optional or required, and if it is used, how many instances (one or many) are allowed.</span></span>

- <span data-ttu-id="6f9f0-115">[Yönergeler](directives-element-net-native.md) [1:1]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-115">[Directives](directives-element-net-native.md) [1:1]</span></span>
  - <span data-ttu-id="6f9f0-116">[Uygulama](application-element-net-native.md) [0:1]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-116">[Application](application-element-net-native.md) [0:1]</span></span>
    - <span data-ttu-id="6f9f0-117">[Derleme](assembly-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-117">[Assembly](assembly-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="6f9f0-118">[Ad alanı](namespace-element-net-native.md) [0: d].</span><span class="sxs-lookup"><span data-stu-id="6f9f0-118">[Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="6f9f0-119">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-119">.</span></span> <span data-ttu-id="6f9f0-120">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-120">.</span></span>
      - <span data-ttu-id="6f9f0-121">[0: d] [yazın](type-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="6f9f0-121">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="6f9f0-122">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-122">.</span></span> <span data-ttu-id="6f9f0-123">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-123">.</span></span>
      - <span data-ttu-id="6f9f0-124">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: a].</span><span class="sxs-lookup"><span data-stu-id="6f9f0-124">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="6f9f0-125">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-125">.</span></span> <span data-ttu-id="6f9f0-126">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-126">.</span></span>
    - <span data-ttu-id="6f9f0-127">[Ad alanı](namespace-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-127">[Namespace](namespace-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="6f9f0-128">[Ad alanı](namespace-element-net-native.md) [0: d].</span><span class="sxs-lookup"><span data-stu-id="6f9f0-128">[Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="6f9f0-129">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-129">.</span></span> <span data-ttu-id="6f9f0-130">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-130">.</span></span>
      - <span data-ttu-id="6f9f0-131">[0: d] [yazın](type-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="6f9f0-131">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="6f9f0-132">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-132">.</span></span> <span data-ttu-id="6f9f0-133">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-133">.</span></span>
      - <span data-ttu-id="6f9f0-134">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: a].</span><span class="sxs-lookup"><span data-stu-id="6f9f0-134">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="6f9f0-135">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-135">.</span></span> <span data-ttu-id="6f9f0-136">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-136">.</span></span>
    - <span data-ttu-id="6f9f0-137">[Tür](type-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-137">[Type](type-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="6f9f0-138">Alt [türler](subtypes-element-net-native.md) (kapsayan türün alt sınıfları) [o:1]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-138">[Subtypes](subtypes-element-net-native.md) (subclasses of the containing type) [O:1]</span></span>
      - <span data-ttu-id="6f9f0-139">[0: d] [yazın](type-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="6f9f0-139">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="6f9f0-140">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-140">.</span></span> <span data-ttu-id="6f9f0-141">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-141">.</span></span>
      - <span data-ttu-id="6f9f0-142">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: a].</span><span class="sxs-lookup"><span data-stu-id="6f9f0-142">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="6f9f0-143">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-143">.</span></span> <span data-ttu-id="6f9f0-144">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-144">.</span></span>
      - <span data-ttu-id="6f9f0-145">[Attributeme](attributeimplies-element-net-native.md) (tür içeren bir öznitelik) [o:1]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-145">[AttributeImplies](attributeimplies-element-net-native.md) (containing type is an attribute) [O:1]</span></span>
      - <span data-ttu-id="6f9f0-146">[Genericparameter](genericparameter-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-146">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="6f9f0-147">[Yöntem](method-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-147">[Method](method-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="6f9f0-148">[Parametre](parameter-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-148">[Parameter](parameter-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="6f9f0-149">[Typeparameter](typeparameter-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-149">[TypeParameter](typeparameter-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="6f9f0-150">[Genericparameter](genericparameter-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-150">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="6f9f0-151">[Methodörneklemesi](methodinstantiation-element-net-native.md) (oluşturulmuş genel yöntem) [0: a]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-151">[MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>
      - <span data-ttu-id="6f9f0-152">[Özellik](property-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-152">[Property](property-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="6f9f0-153">[Alan](field-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-153">[Field](field-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="6f9f0-154">[Olay](event-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-154">[Event](event-element-net-native.md) [0:M]</span></span>
    - <span data-ttu-id="6f9f0-155">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: d]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-155">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>
      - <span data-ttu-id="6f9f0-156">[0: d] [yazın](type-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="6f9f0-156">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="6f9f0-157">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-157">.</span></span> <span data-ttu-id="6f9f0-158">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-158">.</span></span>
      - <span data-ttu-id="6f9f0-159">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: a].</span><span class="sxs-lookup"><span data-stu-id="6f9f0-159">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="6f9f0-160">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-160">.</span></span> <span data-ttu-id="6f9f0-161">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-161">.</span></span>
      - <span data-ttu-id="6f9f0-162">[Yöntem](method-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-162">[Method](method-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="6f9f0-163">[Parametre](parameter-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-163">[Parameter](parameter-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="6f9f0-164">[Typeparameter](typeparameter-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-164">[TypeParameter](typeparameter-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="6f9f0-165">[Genericparameter](genericparameter-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-165">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="6f9f0-166">[Methodörneklemesi](methodinstantiation-element-net-native.md) (oluşturulmuş genel yöntem) [0: a]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-166">[MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>
      - <span data-ttu-id="6f9f0-167">[Özellik](property-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-167">[Property](property-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="6f9f0-168">[Alan](field-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-168">[Field](field-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="6f9f0-169">[Olay](event-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-169">[Event](event-element-net-native.md) [0:M]</span></span>
  - <span data-ttu-id="6f9f0-170">[Kitaplık](library-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-170">[Library](library-element-net-native.md) [0:M]</span></span>
    - <span data-ttu-id="6f9f0-171">[Derleme](assembly-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-171">[Assembly](assembly-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="6f9f0-172">[Ad alanı](namespace-element-net-native.md) [0: d].</span><span class="sxs-lookup"><span data-stu-id="6f9f0-172">[Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="6f9f0-173">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-173">.</span></span> <span data-ttu-id="6f9f0-174">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-174">.</span></span>
      - <span data-ttu-id="6f9f0-175">[0: d] [yazın](type-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="6f9f0-175">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="6f9f0-176">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-176">.</span></span> <span data-ttu-id="6f9f0-177">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-177">.</span></span>
      - <span data-ttu-id="6f9f0-178">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: a].</span><span class="sxs-lookup"><span data-stu-id="6f9f0-178">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="6f9f0-179">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-179">.</span></span> <span data-ttu-id="6f9f0-180">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-180">.</span></span>
    - <span data-ttu-id="6f9f0-181">[Ad alanı](namespace-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-181">[Namespace](namespace-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="6f9f0-182">[Ad alanı](namespace-element-net-native.md) [0: d].</span><span class="sxs-lookup"><span data-stu-id="6f9f0-182">[Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="6f9f0-183">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-183">.</span></span> <span data-ttu-id="6f9f0-184">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-184">.</span></span>
      - <span data-ttu-id="6f9f0-185">[0: d] [yazın](type-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="6f9f0-185">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="6f9f0-186">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-186">.</span></span> <span data-ttu-id="6f9f0-187">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-187">.</span></span>
      - <span data-ttu-id="6f9f0-188">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: a].</span><span class="sxs-lookup"><span data-stu-id="6f9f0-188">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="6f9f0-189">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-189">.</span></span> <span data-ttu-id="6f9f0-190">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-190">.</span></span>
    - <span data-ttu-id="6f9f0-191">[Tür](type-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-191">[Type](type-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="6f9f0-192">Alt [türler](subtypes-element-net-native.md) (kapsayan türün alt sınıfları) [o:1]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-192">[Subtypes](subtypes-element-net-native.md) (subclasses of the containing type) [O:1]</span></span>
      - <span data-ttu-id="6f9f0-193">[0: d] [yazın](type-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="6f9f0-193">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="6f9f0-194">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-194">.</span></span> <span data-ttu-id="6f9f0-195">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-195">.</span></span>
      - <span data-ttu-id="6f9f0-196">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: a].</span><span class="sxs-lookup"><span data-stu-id="6f9f0-196">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="6f9f0-197">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-197">.</span></span> <span data-ttu-id="6f9f0-198">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-198">.</span></span>
      - <span data-ttu-id="6f9f0-199">[Attributeme](attributeimplies-element-net-native.md) (tür içeren bir öznitelik) [o:1]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-199">[AttributeImplies](attributeimplies-element-net-native.md) (containing type is an attribute) [O:1]</span></span>
      - <span data-ttu-id="6f9f0-200">[Genericparameter](genericparameter-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-200">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="6f9f0-201">[Yöntem](method-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-201">[Method](method-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="6f9f0-202">[Methodörneklemesi](methodinstantiation-element-net-native.md) (oluşturulmuş genel yöntem) [0: a]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-202">[MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>
      - <span data-ttu-id="6f9f0-203">[Özellik](property-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-203">[Property](property-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="6f9f0-204">[Alan](field-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-204">[Field](field-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="6f9f0-205">[Olay](event-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-205">[Event](event-element-net-native.md) [0:M]</span></span>
    - <span data-ttu-id="6f9f0-206">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: d]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-206">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>
      - <span data-ttu-id="6f9f0-207">[0: d] [yazın](type-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="6f9f0-207">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="6f9f0-208">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-208">.</span></span> <span data-ttu-id="6f9f0-209">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-209">.</span></span>
      - <span data-ttu-id="6f9f0-210">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: a].</span><span class="sxs-lookup"><span data-stu-id="6f9f0-210">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="6f9f0-211">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-211">.</span></span> <span data-ttu-id="6f9f0-212">.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-212">.</span></span>
      - <span data-ttu-id="6f9f0-213">[Yöntem](method-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-213">[Method](method-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="6f9f0-214">[Methodörneklemesi](methodinstantiation-element-net-native.md) (oluşturulmuş genel yöntem) [0: a]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-214">[MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>
      - <span data-ttu-id="6f9f0-215">[Özellik](property-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-215">[Property](property-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="6f9f0-216">[Alan](field-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-216">[Field](field-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="6f9f0-217">[Olay](event-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="6f9f0-217">[Event](event-element-net-native.md) [0:M]</span></span>

<span data-ttu-id="6f9f0-218">[Uygulama](application-element-net-native.md) öğesinin hiç özniteliği olamaz veya [çalışma zamanı yönergesinde ve ilke bölümünde](#Directives)ele alınan ilke özniteliklerine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-218">The [Application](application-element-net-native.md) element can have no attributes, or it can have the policy attributes discussed in the [Runtime directive and policy section](#Directives).</span></span>

<span data-ttu-id="6f9f0-219">Bir [kitaplık](library-element-net-native.md) öğesi, dosya uzantısı olmadan bir kitaplığın veya derlemenin adını belirten tek bir özniteliğe sahiptir `Name`.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-219">A [Library](library-element-net-native.md) element has a single attribute, `Name`, that specifies the name of a library or assembly, without its file extension.</span></span> <span data-ttu-id="6f9f0-220">Örneğin, aşağıdaki [kitaplık](library-element-net-native.md) öğesi Extensions. dll adlı bir derleme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-220">For example, the following [Library](library-element-net-native.md) element applies to an assembly named Extensions.dll.</span></span>

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

## <a name="runtime-directives-and-policy"></a><span data-ttu-id="6f9f0-221">Çalışma zamanı yönergeleri ve ilkesi</span><span class="sxs-lookup"><span data-stu-id="6f9f0-221">Runtime directives and policy</span></span>

<span data-ttu-id="6f9f0-222">[Uygulama](application-element-net-native.md) öğesinin kendisi ve [kitaplık](library-element-net-native.md) ve [uygulama](application-element-net-native.md) öğeleri Express ilkesinin alt öğeleri; diğer bir deyişle, bir uygulamanın bir program öğesine yansıma uygulayabileceği şekilde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-222">The [Application](application-element-net-native.md) element itself and the child elements of the [Library](library-element-net-native.md) and [Application](application-element-net-native.md) elements express policy; that is, they define the way in which an app can apply reflection to a program element.</span></span> <span data-ttu-id="6f9f0-223">İlke türü, öğesinin bir özniteliği tarafından tanımlanır (örneğin, `Serialize`).</span><span class="sxs-lookup"><span data-stu-id="6f9f0-223">The policy type is defined by an attribute of the element (for example, `Serialize`).</span></span> <span data-ttu-id="6f9f0-224">İlke değeri özniteliğin değeri (örneğin, `Serialize="Required"`) tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-224">The policy value is defined by the attribute’s value (for example, `Serialize="Required"`).</span></span>

<span data-ttu-id="6f9f0-225">Bir öğenin özniteliği tarafından belirtilen herhangi bir ilke, bu ilke için bir değer belirtmeyen tüm alt öğeler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-225">Any policy specified by an attribute of an element applies to all child elements that don’t specify a value for that policy.</span></span> <span data-ttu-id="6f9f0-226">Örneğin, bir ilke bir [tür](type-element-net-native.md) öğesiyle belirtilmişse, bu ilke, bir ilkenin açıkça belirtilmediği tüm içerilen türler ve Üyeler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-226">For example, if a policy is specified by a [Type](type-element-net-native.md) element, that policy applies to all contained types and members for which a policy is not explicitly specified.</span></span>

<span data-ttu-id="6f9f0-227">[Uygulama](application-element-net-native.md), [derleme](assembly-element-net-native.md), [attributeby](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), alt [türler](subtypes-element-net-native.md)ve [tür](type-element-net-native.md) öğeleri tarafından Ifade edilen ilke, ayrı Üyeler Için ifade edilebilir ilkeden farklıdır ( [Yöntem](method-element-net-native.md), [özellik](property-element-net-native.md), [alan](field-element-net-native.md)ve [olay](event-element-net-native.md) öğeleri tarafından).</span><span class="sxs-lookup"><span data-stu-id="6f9f0-227">The policy that can be expressed by the [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md), and [Type](type-element-net-native.md) elements differs from the policy that can be expressed for individual members (by the [Method](method-element-net-native.md), [Property](property-element-net-native.md), [Field](field-element-net-native.md), and [Event](event-element-net-native.md) elements).</span></span>

### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a><span data-ttu-id="6f9f0-228">Derlemeler, ad alanları ve türler için ilke belirtme</span><span class="sxs-lookup"><span data-stu-id="6f9f0-228">Specifying policy for assemblies, namespaces, and types</span></span>

<span data-ttu-id="6f9f0-229">[Uygulama](application-element-net-native.md), [derleme](assembly-element-net-native.md), [attributeme](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), alt [türleri](subtypes-element-net-native.md)ve [tür](type-element-net-native.md) öğeleri aşağıdaki ilke türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="6f9f0-229">The [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md), and [Type](type-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="6f9f0-230">`Activate`.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-230">`Activate`.</span></span> <span data-ttu-id="6f9f0-231">Örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-231">Controls runtime access to constructors, to enable activation of instances.</span></span>

- <span data-ttu-id="6f9f0-232">`Browse`.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-232">`Browse`.</span></span> <span data-ttu-id="6f9f0-233">Program öğeleri hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-233">Controls querying for information about program elements but does not enable any runtime access.</span></span>

- <span data-ttu-id="6f9f0-234">`Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-234">`Dynamic`.</span></span> <span data-ttu-id="6f9f0-235">Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-235">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>

- <span data-ttu-id="6f9f0-236">`Serialize`.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-236">`Serialize`.</span></span> <span data-ttu-id="6f9f0-237">Tür örneklerinin, Newtonsoft JSON serileştirici gibi üçüncü taraf kitaplıklara serileştirilmesi ve serileştirilmesi için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-237">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and serialized by third-party libraries such as the Newtonsoft JSON serializer.</span></span>

- <span data-ttu-id="6f9f0-238">`DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-238">`DataContractSerializer`.</span></span> <span data-ttu-id="6f9f0-239"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfını kullanan serileştirme için ilkeyi denetler.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-239">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="6f9f0-240">`DataContractJsonSerializer`.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-240">`DataContractJsonSerializer`.</span></span> <span data-ttu-id="6f9f0-241"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfını kullanan JSON serileştirme için ilkeyi denetler.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-241">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="6f9f0-242">`XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-242">`XmlSerializer`.</span></span> <span data-ttu-id="6f9f0-243"><xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfını kullanan XML serileştirme ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-243">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="6f9f0-244">`MarshalObject`.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-244">`MarshalObject`.</span></span> <span data-ttu-id="6f9f0-245">WinRT ve COM 'a başvuru türlerini hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-245">Controls policy for marshaling reference types to WinRT and COM.</span></span>

- <span data-ttu-id="6f9f0-246">`MarshalDelegate`.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-246">`MarshalDelegate`.</span></span> <span data-ttu-id="6f9f0-247">Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-247">Controls policy for marshaling delegate types as function pointers to native code.</span></span>

- <span data-ttu-id="6f9f0-248">`MarshalStructure` .</span><span class="sxs-lookup"><span data-stu-id="6f9f0-248">`MarshalStructure` .</span></span> <span data-ttu-id="6f9f0-249">Yapıları yerel koda hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-249">Controls policy for marshaling structures to native code.</span></span>

<span data-ttu-id="6f9f0-250">Bu ilke türleriyle ilişkili ayarlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6f9f0-250">The settings associated with these policy types are:</span></span>

- <span data-ttu-id="6f9f0-251">`All`.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-251">`All`.</span></span> <span data-ttu-id="6f9f0-252">Araç zincirinin kaldıramayan tüm türler ve Üyeler için ilkeyi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-252">Enable the policy for all types and members that the tool chain does not remove.</span></span>

- <span data-ttu-id="6f9f0-253">`Auto`.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-253">`Auto`.</span></span> <span data-ttu-id="6f9f0-254">Varsayılan davranışı kullanın.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-254">Use the default behavior.</span></span> <span data-ttu-id="6f9f0-255">(İlke belirtilmeden, ilke geçersiz kılınmadıkça (örneğin, bir üst öğe), bu ilke `Auto` ayarlamaya eşdeğerdir.)</span><span class="sxs-lookup"><span data-stu-id="6f9f0-255">(Not specifying a policy is equivalent to setting that policy to `Auto` unless that policy is overridden, for example by a parent element.)</span></span>

- <span data-ttu-id="6f9f0-256">`Excluded`.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-256">`Excluded`.</span></span> <span data-ttu-id="6f9f0-257">Program öğesi için ilkeyi devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-257">Disable the policy for the program element.</span></span>

- <span data-ttu-id="6f9f0-258">`Public`.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-258">`Public`.</span></span> <span data-ttu-id="6f9f0-259">Araç zinciri üyenin gereksiz olduğunu belirlerse ve bu nedenle uygulamayı kaldırmadığı müddetçe ortak türler veya Üyeler için ilkeyi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-259">Enable the policy for public types or members unless the tool chain determines that the member is unnecessary and therefore removes it.</span></span> <span data-ttu-id="6f9f0-260">(İkinci durumda, üyenin tutulduğundan ve yansıma özelliklerine sahip olduğundan emin olmak için `Required Public` kullanmanız gerekir.)</span><span class="sxs-lookup"><span data-stu-id="6f9f0-260">(In the latter case, you must use `Required Public` to ensure that the member is kept and has reflection capabilities.)</span></span>

- <span data-ttu-id="6f9f0-261">`PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-261">`PublicAndInternal`.</span></span> <span data-ttu-id="6f9f0-262">Araç zinciri onları kaldırmazsa ortak ve iç türler veya Üyeler için ilkeyi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-262">Enable the policy for public and internal types or members if the tool chain doesn't remove them.</span></span>

- <span data-ttu-id="6f9f0-263">`Required Public`.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-263">`Required Public`.</span></span> <span data-ttu-id="6f9f0-264">Ortak türleri ve üyeleri, kullanıldıkları ve kullanılmayacağı gibi tutmak ve ilke için etkinleştirmek üzere araç zinciri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-264">Require the tool chain to keep public types and members whether or not they are used, and enable the policy for them.</span></span>

- <span data-ttu-id="6f9f0-265">`Required PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-265">`Required PublicAndInternal`.</span></span> <span data-ttu-id="6f9f0-266">Araç zincirinin hem ortak hem de iç türleri ve üyeleri, kullanılmalarına bakılmaksızın ve bunları kendileri için etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-266">Require the tool chain to keep both public and internal types and members whether or not they are used, and enable the policy for them.</span></span>

- <span data-ttu-id="6f9f0-267">`Required All`.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-267">`Required All`.</span></span> <span data-ttu-id="6f9f0-268">Araç zincirinin tüm türleri ve üyeleri kullanıp kullanmadığını ve bunların kullanılmadığını ve ilke için etkin olmasını gerektir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-268">Require the tool chain to keep all types and members whether or not they are used, and enable the policy for them.</span></span>

<span data-ttu-id="6f9f0-269">Örneğin, aşağıdaki çalışma zamanı yönergeleri dosyası, veri sınıfları. dll dosyasındaki tüm türler ve Üyeler için ilkeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-269">For example, the following runtime directives file defines policy for all types and members in the assembly DataClasses.dll.</span></span> <span data-ttu-id="6f9f0-270">Tüm ortak özelliklerin serileştirilmesi için yansıma kullanımını, tüm türler ve tür üyeleri için gözatmayı etkinleştirmek, tüm türler için etkinleştirmeyi etkinleştirmek (`Dynamic` özniteliği nedeniyle) ve tüm genel türler ve Üyeler için yansıma etkinleştirmek için yansıma imkanı sunar.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-270">It enables reflection for serialization of all public properties, enables browsing for all types and type members, enables activation for all types (because of the `Dynamic` attribute), and enables reflection for all public types and members.</span></span>

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

### <a name="specifying-policy-for-members"></a><span data-ttu-id="6f9f0-271">Üyeler için ilke belirtme</span><span class="sxs-lookup"><span data-stu-id="6f9f0-271">Specifying policy for members</span></span>

<span data-ttu-id="6f9f0-272">[Özellik](property-element-net-native.md) ve [alan](field-element-net-native.md) öğeleri aşağıdaki ilke türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="6f9f0-272">The [Property](property-element-net-native.md) and [Field](field-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="6f9f0-273">`Browse`-Bu üye hakkında bilgi sorgulama denetimleri, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-273">`Browse` - Controls querying for information about this member but does not enable any runtime access.</span></span>

- <span data-ttu-id="6f9f0-274">`Dynamic`-dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-274">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="6f9f0-275">Ayrıca, kapsayan tür hakkındaki bilgileri sorgulamayı denetler.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-275">Also controls querying for information about the containing type.</span></span>

- <span data-ttu-id="6f9f0-276">`Serialize`-tür örneklerinin, Newtonsoft JSON serileştirici gibi kitaplıklar tarafından serileştirilmesi ve seri durumdan çıkarılmakta olması için üyeye çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-276">`Serialize` - Controls runtime access to the member to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span> <span data-ttu-id="6f9f0-277">Bu ilke oluşturucular, alanlar ve özelliklere uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-277">This policy can be applied to constructors, fields, and properties.</span></span>

<span data-ttu-id="6f9f0-278">[Yöntemi](method-element-net-native.md) ve [olay](event-element-net-native.md) öğeleri aşağıdaki ilke türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="6f9f0-278">The [Method](method-element-net-native.md) and [Event](event-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="6f9f0-279">`Browse`-Bu üye hakkında bilgi sorgulama denetimleri, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-279">`Browse` - Controls querying for information about this member but doesn’t enable any runtime access.</span></span>

- <span data-ttu-id="6f9f0-280">`Dynamic`-dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-280">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="6f9f0-281">Ayrıca, kapsayan tür hakkındaki bilgileri sorgulamayı denetler.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-281">Also controls querying for information about the containing type.</span></span>

 <span data-ttu-id="6f9f0-282">Bu ilke türleriyle ilişkili ayarlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6f9f0-282">The settings associated with these policy types are:</span></span>

- <span data-ttu-id="6f9f0-283">`Auto`-varsayılan davranışı kullanın.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-283">`Auto` - Use the default behavior.</span></span> <span data-ttu-id="6f9f0-284">(İlke belirtmeksizin, bir öğe geçersiz kılınmadığı takdirde bu ilkenin `Auto` ayarlanmasına eşdeğerdir.)</span><span class="sxs-lookup"><span data-stu-id="6f9f0-284">(Not specifying a policy is equivalent to setting that policy to `Auto` unless something overrides it.)</span></span>

- <span data-ttu-id="6f9f0-285">`Excluded`-üyenin meta verilerini hiçbir şekilde eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-285">`Excluded` - Never include metadata for the member.</span></span>

- <span data-ttu-id="6f9f0-286">`Included`-üst tür çıktıda varsa ilkeyi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-286">`Included` - Enable the policy if the parent type is present in the output.</span></span>

- <span data-ttu-id="6f9f0-287">`Required`-araç zincirinin, kullanılmamış gibi görünse bile bu üyeyi tutması gerekir ve ilkeyi etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-287">`Required` - Require the tool chain to keep this member even if appears to be unused, and enable policy for it.</span></span>

## <a name="runtime-directives-file-semantics"></a><span data-ttu-id="6f9f0-288">Çalışma zamanı yönergeleri dosya semantiği</span><span class="sxs-lookup"><span data-stu-id="6f9f0-288">Runtime directives file semantics</span></span>

<span data-ttu-id="6f9f0-289">İlke, hem daha yüksek hem de alt düzey öğeler için eşzamanlı olarak tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-289">Policy can be defined simultaneously for both higher-level and lower-level elements.</span></span> <span data-ttu-id="6f9f0-290">Örneğin, ilke bir derleme için ve bu derlemede yer alan bazı türler için tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-290">For example, policy can be defined for an assembly, and for some of the types contained in that assembly.</span></span> <span data-ttu-id="6f9f0-291">Belirli bir alt düzey öğe gösterilmediğinden, üst öğesinin ilkesini devralır.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-291">If a particular lower-level element is not represented, it inherits the policy of its parent.</span></span> <span data-ttu-id="6f9f0-292">Örneğin, bir `Assembly` öğesi varsa ancak `Type` öğeler yoksa, `Assembly` öğesinde belirtilen ilke derlemedeki her tür için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-292">For example, if an `Assembly` element is present but `Type` elements are not, the policy specified in the `Assembly` element applies to each type in the assembly.</span></span> <span data-ttu-id="6f9f0-293">Aynı program öğesine aynı zamanda birden çok öğe ilke uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-293">Multiple elements can also apply policy to the same program element.</span></span> <span data-ttu-id="6f9f0-294">Örneğin, ayrı [derleme](assembly-element-net-native.md) öğeleri aynı derleme için aynı ilke öğesini farklı şekilde tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-294">For example, separate [Assembly](assembly-element-net-native.md) elements might define the same policy element for the same assembly differently.</span></span> <span data-ttu-id="6f9f0-295">Aşağıdaki bölümlerde, belirli bir türün ilkesinin bu durumlarda nasıl çözümlendiğini açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-295">The following sections explain how the policy for a particular type is resolved in those cases.</span></span>

<span data-ttu-id="6f9f0-296">Genel bir türün veya yöntemin [tür](type-element-net-native.md) veya [Yöntem](method-element-net-native.md) öğesi, kendi ilkesi olmayan tüm örneklemelerde ilkesini uygular.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-296">A [Type](type-element-net-native.md) or [Method](method-element-net-native.md) element of a generic type or method applies its policy to all instantiations that do not have their own policy.</span></span> <span data-ttu-id="6f9f0-297">Örneğin, <xref:System.Collections.Generic.List%601> ilkesini belirten `Type` bir öğesi, belirli bir oluşturulan genel tür için (`List<Int32>`gibi) bir `TypeInstantiation` öğesi tarafından geçersiz kılınmadığı sürece, bu genel türün oluşturulan tüm örnekleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-297">For example, a `Type` element that specifies policy for <xref:System.Collections.Generic.List%601> applies to all constructed instances of that generic type, unless it's overridden for a particular constructed generic type (such as a `List<Int32>`) by a `TypeInstantiation` element.</span></span> <span data-ttu-id="6f9f0-298">Aksi takdirde, öğeleri adlı program öğesi için ilkeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-298">Otherwise, elements define policy for the program element named.</span></span>

<span data-ttu-id="6f9f0-299">Bir öğe belirsiz olduğunda, motor eşleşme arar ve tam eşleşme bulursa onu kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-299">When an element is ambiguous, the engine looks for matches, and if it finds an exact match, it will use it.</span></span> <span data-ttu-id="6f9f0-300">Birden çok eşleşme bulunursa bir uyarı veya hata olur.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-300">If it finds multiple matches, there will be a warning or error.</span></span>

### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a><span data-ttu-id="6f9f0-301">İki yönergeler aynı program öğesine ilke uygualıyorsa</span><span class="sxs-lookup"><span data-stu-id="6f9f0-301">If two directives apply policy to the same program element</span></span>

<span data-ttu-id="6f9f0-302">Farklı çalışma zamanı yönergeleri dosyalarındaki iki öğe aynı program öğesi (bir derleme veya tür gibi) için aynı ilke türünü farklı değerlere ayarlamaya çalışıyorsa, çakışma aşağıdaki gibi çözümlenir:</span><span class="sxs-lookup"><span data-stu-id="6f9f0-302">If two elements in different runtime directives files try to set the same policy type for the same program element (such as an assembly or type) to different values, the conflict is resolved as follows:</span></span>

1. <span data-ttu-id="6f9f0-303">`Excluded` öğesi varsa önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-303">If the `Excluded` element is present, it has precedence.</span></span>

2. <span data-ttu-id="6f9f0-304">`Required` `Required`değil önceliğe sahip.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-304">`Required` has precedence over not `Required`.</span></span>

3. <span data-ttu-id="6f9f0-305">`All`, `Public`öncelikli olan `PublicAndInternal`önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-305">`All` has precedence over `PublicAndInternal`, which has precedence over `Public`.</span></span>

4. <span data-ttu-id="6f9f0-306">Herhangi bir açık ayar `Auto`önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-306">Any explicit setting has precedence over `Auto`.</span></span>

<span data-ttu-id="6f9f0-307">Örneğin, tek bir proje aşağıdaki iki çalışma zamanı yönergeleri dosyasını içeriyorsa, DataClasses. dll için serileştirme ilkesi hem `Required Public` hem de `All`olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-307">For example, if a single project includes the following two runtime directives files, the serialization policy for DataClasses.dll is set to both `Required Public` and `All`.</span></span> <span data-ttu-id="6f9f0-308">Bu durumda, serileştirme ilkesi `Required All`olarak çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-308">In this case, the serialization policy would be resolved as `Required All`.</span></span>

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

<span data-ttu-id="6f9f0-309">Ancak, tek bir çalışma zamanı yönergeleri dosyasında iki yönergesi aynı program öğesi için aynı ilke türünü ayarlamaya çalışırsanız, XML şeması tanım aracında bir hata iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-309">However, if two directives in a single runtime directives file try to set the same policy type for the same program element, the XML Scheme Definition tool displays an error message.</span></span>

### <a name="if-child-and-parent-elements-apply-the-same-policy-type"></a><span data-ttu-id="6f9f0-310">Alt ve üst öğeler aynı ilke türünü uygualıyorsa</span><span class="sxs-lookup"><span data-stu-id="6f9f0-310">If child and parent elements apply the same policy type</span></span>

<span data-ttu-id="6f9f0-311">Alt öğeler, `Excluded` ayarı da dahil olmak üzere üst öğelerini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-311">Child elements override their parent elements, including the `Excluded` setting.</span></span> <span data-ttu-id="6f9f0-312">Geçersiz kılma, `Auto`belirtmek istediğiniz ana nedendir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-312">Overriding is the main reason you would want to specify `Auto`.</span></span>

<span data-ttu-id="6f9f0-313">Aşağıdaki örnekte, `DataClasses.ViewModels` olmayan `DataClasses` her şey için serileştirme ilkesi ayarı `Required Public`ve hem `DataClasses` hem de `DataClasses.ViewModels` içindeki her şey `All`olur.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-313">In the following example, the serialization policy setting for everything in `DataClasses` that’s not in `DataClasses.ViewModels` would be `Required Public`, and everything that's in both `DataClasses` and `DataClasses.ViewModels` would be `All`.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public" >
         <Namespace Name="DataClasses.ViewModels" Serialize="All" />
      </Assembly>
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

### <a name="if-open-generics-and-instantiated-elements-apply-the-same-policy-type"></a><span data-ttu-id="6f9f0-314">Açık genel türler ve örneklenmiş öğeler aynı ilke türünü uygular</span><span class="sxs-lookup"><span data-stu-id="6f9f0-314">If open generics and instantiated elements apply the same policy type</span></span>

<span data-ttu-id="6f9f0-315">Aşağıdaki örnekte, `Dictionary<int,int>` `Browse` ilkesine yalnızca altyapının, bu bileşene `Browse` ilkesi (Aksi takdirde varsayılan davranış) izin vermek için başka bir nedeni varsa atanır; <xref:System.Collections.Generic.Dictionary%602> diğer tüm örneklemelerinden tüm üyeleri gözatılabilir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-315">In the following example, `Dictionary<int,int>` is assigned the `Browse` policy only if the engine has another reason to give it the `Browse` policy (which would otherwise be the default behavior); every other instantiation of <xref:System.Collections.Generic.Dictionary%602> will have all of its members browsable.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public" >
         <Namespace Name="DataClasses.ViewModels" Serialize="All" />
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

### <a name="how-policy-is-inferred"></a><span data-ttu-id="6f9f0-316">İlke nasıl algılanır</span><span class="sxs-lookup"><span data-stu-id="6f9f0-316">How policy is inferred</span></span>

<span data-ttu-id="6f9f0-317">Her ilke türünün, bu ilke türü varlığının diğer yapıları nasıl etkilediğini tespit eden farklı kurallar kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-317">Each policy type has a different set of rules that determine how the presence of that policy type affects other constructs.</span></span>

#### <a name="the-effect-of-browse-policy"></a><span data-ttu-id="6f9f0-318">Tarayıcı ilkesinin etkisi</span><span class="sxs-lookup"><span data-stu-id="6f9f0-318">The effect of Browse policy</span></span>

<span data-ttu-id="6f9f0-319">`Browse` ilkesinin bir türe uygulanması aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="6f9f0-319">Applying the `Browse` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="6f9f0-320">Türün temel türü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-320">The base type of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="6f9f0-321">Tür bir genel ise, türün örneklenmemiş sürümü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-321">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="6f9f0-322">Tür bir temsilciyiyise, türdeki `Invoke` yöntemi `Dynamic` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-322">If the type is a delegate, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="6f9f0-323">Türün her arabirimi `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-323">Each interface of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="6f9f0-324">Türe uygulanan her bir özniteliğin türü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-324">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="6f9f0-325">Tür geneldir ise, her kısıtlama türü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-325">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="6f9f0-326">Tür geneldir ise, türün örneklendiği türler `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-326">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="6f9f0-327">`Browse` ilkesinin bir yönteme uygulanması aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="6f9f0-327">Applying the `Browse` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="6f9f0-328">Yöntemin her bir parametre türü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-328">Each parameter type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="6f9f0-329">Metodun dönüş türü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-329">The return type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="6f9f0-330">Yöntemin kapsayan türü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-330">The containing type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="6f9f0-331">Yöntem örneklenmiş genel bir yöntem ise, örneklenmemiş genel yöntem `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-331">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="6f9f0-332">Yöntemine uygulanan her bir özniteliğin türü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-332">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="6f9f0-333">Yöntem geneldir ise, her kısıtlama türü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-333">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="6f9f0-334">Yöntem genel ise, yöntemin örneklendiği türler `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-334">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="6f9f0-335">`Browse` ilkesinin bir alana uygulanması aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="6f9f0-335">Applying the `Browse` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="6f9f0-336">Alana uygulanan her bir özniteliğin türü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-336">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="6f9f0-337">Alanın türü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-337">The type of the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="6f9f0-338">Alanın ait olduğu tür `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-338">The type to which the field belongs is marked with the `Browse` policy.</span></span>

#### <a name="the-effect-of-dynamic-policy"></a><span data-ttu-id="6f9f0-339">Dinamik ilkenin etkisi</span><span class="sxs-lookup"><span data-stu-id="6f9f0-339">The effect of Dynamic policy</span></span>

<span data-ttu-id="6f9f0-340">`Dynamic` ilkesinin bir türe uygulanması aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="6f9f0-340">Applying the `Dynamic` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="6f9f0-341">Türün temel türü `Dynamic` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-341">The base type of the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="6f9f0-342">Tür bir genel ise, türün örneklenmemiş sürümü `Dynamic` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-342">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="6f9f0-343">Tür bir temsilci türü ise, türdeki `Invoke` yöntemi `Dynamic` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-343">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="6f9f0-344">Türün her arabirimi `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-344">Each interface of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="6f9f0-345">Türe uygulanan her bir özniteliğin türü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-345">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="6f9f0-346">Tür geneldir ise, her kısıtlama türü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-346">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="6f9f0-347">Tür geneldir ise, türün örneklendiği türler `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-347">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="6f9f0-348">`Dynamic` ilkesinin bir yönteme uygulanması aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="6f9f0-348">Applying the `Dynamic` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="6f9f0-349">Yöntemin her bir parametre türü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-349">Each parameter type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="6f9f0-350">Metodun dönüş türü `Dynamic` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-350">The return type of the method is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="6f9f0-351">Yöntemin kapsayan türü `Dynamic` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-351">The containing type of the method is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="6f9f0-352">Yöntem örneklenmiş genel bir yöntem ise, örneklenmemiş genel yöntem `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-352">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="6f9f0-353">Yöntemine uygulanan her bir özniteliğin türü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-353">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="6f9f0-354">Yöntem geneldir ise, her kısıtlama türü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-354">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="6f9f0-355">Yöntem genel ise, yöntemin örneklendiği türler `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-355">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>

- <span data-ttu-id="6f9f0-356">Yöntemi `MethodInfo.Invoke`tarafından çağrılabilir ve temsilci oluşturma <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>tarafından mümkün hale gelir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-356">The method can be invoked by `MethodInfo.Invoke`, and delegate creation becomes possible by <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="6f9f0-357">`Dynamic` ilkesinin bir alana uygulanması aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="6f9f0-357">Applying the `Dynamic` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="6f9f0-358">Alana uygulanan her bir özniteliğin türü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-358">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="6f9f0-359">Alanın türü `Dynamic` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-359">The type of the field is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="6f9f0-360">Alanın ait olduğu tür `Dynamic` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-360">The type to which the field belongs is marked with the `Dynamic` policy.</span></span>

#### <a name="the-effect-of-activation-policy"></a><span data-ttu-id="6f9f0-361">Etkinleştirme ilkesinin etkisi</span><span class="sxs-lookup"><span data-stu-id="6f9f0-361">The effect of Activation policy</span></span>

<span data-ttu-id="6f9f0-362">Etkinleştirme ilkesini bir türe uygulamak aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="6f9f0-362">Applying the Activation policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="6f9f0-363">Tür bir genel ise, türün örneklenmemiş sürümü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-363">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="6f9f0-364">Tür bir temsilci türü ise, türdeki `Invoke` yöntemi `Dynamic` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-364">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="6f9f0-365">Türün oluşturucuları `Activation` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-365">Constructors of the type are marked with the `Activation` policy.</span></span>

<span data-ttu-id="6f9f0-366">`Activation` ilkesinin bir yönteme uygulanması aşağıdaki ilke değişikliğini içerir:</span><span class="sxs-lookup"><span data-stu-id="6f9f0-366">Applying the `Activation` policy to a method involves the following policy change:</span></span>

- <span data-ttu-id="6f9f0-367">Oluşturucu <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> ve <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> yöntemlerle çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-367">The constructor can be invoked by the <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> and <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="6f9f0-368">Yöntemler için `Activation` ilkesi yalnızca oluşturucuları etkiler.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-368">For methods, the `Activation` policy affects constructors only.</span></span>

<span data-ttu-id="6f9f0-369">`Activation` ilkesinin bir alana uygulanması etkisizdir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-369">Applying the `Activation` policy to a field has no effect.</span></span>

#### <a name="the-effect-of-serialize-policy"></a><span data-ttu-id="6f9f0-370">Seri hale getirme ilkesinin etkisi</span><span class="sxs-lookup"><span data-stu-id="6f9f0-370">The effect of Serialize policy</span></span>

<span data-ttu-id="6f9f0-371">`Serialize` ilkesi, yaygın yansıma tabanlı serileştiricilerin kullanımını sunar.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-371">The `Serialize` policy enables the use of common reflection-based serializers.</span></span> <span data-ttu-id="6f9f0-372">Ancak, Microsoft dışı serileştiricilerin tam yansıma erişimi desenleri Microsoft tarafından bilinmediğinden, bu ilke tamamen etkili olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-372">However, because the exact reflection access patterns of non-Microsoft serializers are not known to Microsoft, this policy may not be entirely effective.</span></span>

<span data-ttu-id="6f9f0-373">`Serialize` ilkesinin bir türe uygulanması aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="6f9f0-373">Applying the `Serialize` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="6f9f0-374">Türün temel türü `Serialize` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-374">The base type of the type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="6f9f0-375">Tür bir genel ise, türün örneklenmemiş sürümü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-375">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="6f9f0-376">Tür bir temsilci türü ise, türdeki `Invoke` yöntemi `Dynamic` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-376">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="6f9f0-377">Tür bir sabit listesi ise, türün bir dizisi `Serialize` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-377">If the type is an enumeration, an array of the type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="6f9f0-378">Tür <xref:System.Collections.Generic.IEnumerable%601>uygularsa, `T` `Serialize` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-378">If the type implements <xref:System.Collections.Generic.IEnumerable%601>, `T` is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="6f9f0-379">Tür <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>veya <xref:System.Collections.Generic.IReadOnlyList%601>, `T[]` ve <xref:System.Collections.Generic.List%601> `Serialize` ilkeyle işaretlenir. ancak, arabirim türünün hiçbir üyesi `Serialize` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-379">If the type is <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>, or <xref:System.Collections.Generic.IReadOnlyList%601>, then `T[]` and <xref:System.Collections.Generic.List%601> marked with the `Serialize` policy., but no members of the interface type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="6f9f0-380">Tür <xref:System.Collections.Generic.List%601>ise, türün hiçbir üyesi `Serialize` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-380">If the type is <xref:System.Collections.Generic.List%601>, no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="6f9f0-381">Tür <xref:System.Collections.Generic.IDictionary%602>ise, <xref:System.Collections.Generic.Dictionary%602> `Serialize` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-381">If the type is <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> is marked with the `Serialize` policy.</span></span> <span data-ttu-id="6f9f0-382">Ancak türdeki hiçbir üye `Serialize` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-382">but no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="6f9f0-383">Tür <xref:System.Collections.Generic.Dictionary%602>ise, türün hiçbir üyesi `Serialize` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-383">If the type is <xref:System.Collections.Generic.Dictionary%602>, no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="6f9f0-384">Tür <xref:System.Collections.Generic.IDictionary%602>uygularsa `TKey` ve `TValue` `Serialize` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-384">If the type implements <xref:System.Collections.Generic.IDictionary%602>, `TKey` and `TValue` are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="6f9f0-385">Her bir Oluşturucu, her özellik erişimcisi ve her bir alan `Serialize` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-385">Each constructor, each property accessor, and each field is marked with the `Serialize` policy.</span></span>

<span data-ttu-id="6f9f0-386">`Serialize` ilkesinin bir yönteme uygulanması aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="6f9f0-386">Applying the `Serialize` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="6f9f0-387">Kapsayan tür `Serialize` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-387">The containing type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="6f9f0-388">Metodun dönüş türü `Serialize` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-388">The return type of the method is marked with the `Serialize` policy.</span></span>

<span data-ttu-id="6f9f0-389">`Serialize` ilkesinin bir alana uygulanması aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="6f9f0-389">Applying the `Serialize` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="6f9f0-390">Kapsayan tür `Serialize` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-390">The containing type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="6f9f0-391">Alanın türü `Serialize` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-391">The type of the field is marked with the `Serialize` policy.</span></span>

#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserializer-policies"></a><span data-ttu-id="6f9f0-392">XmlSerializer, DataContractSerializer ve DataContractJsonSerializer ilkelerinin etkisi</span><span class="sxs-lookup"><span data-stu-id="6f9f0-392">The effect of XmlSerializer, DataContractSerializer, and DataContractJsonSerializer policies</span></span>

<span data-ttu-id="6f9f0-393">Yansıma tabanlı serileştiriciler için tasarlanan `Serialize` ilkesinin aksine, .NET Native araç zinciri tarafından bilinen serileştiriciler kümesini etkinleştirmek için <xref:System.Xml.Serialization.XmlSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer>ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ilkeleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-393">Unlike the `Serialize` policy, which is intended for reflection-based serializers, the <xref:System.Xml.Serialization.XmlSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer>, and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> policies are used to enable a set of serializers that are known to the .NET Native tool chain.</span></span> <span data-ttu-id="6f9f0-394">Bu serileştiriciler yansıma kullanılarak uygulanmaz, ancak çalışma zamanında seri hale getirilebildiğiniz türler kümesi, yansıma \ olan türler gibi benzer şekilde belirlenir.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-394">These serializers are not implemented by using reflection, but the set of types that can be serialized at run time is determined in a similar manner as types that are reflectable.</span></span>

<span data-ttu-id="6f9f0-395">Bu ilkelerin bir türe uygulanması, türün eşleşen serileştirici ile serileştirilmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-395">Applying one of these policies to a type enables the type to be serialized with the matching serializer.</span></span> <span data-ttu-id="6f9f0-396">Ayrıca, serileştirme altyapısının serileştirilmesi gereken şekilde statik olarak belirleyebilmesi için herhangi bir tür de serileştirilebilir olur.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-396">Also, any types that the serialization engine can statically determine as needing serialization will also be serializable.</span></span>

<span data-ttu-id="6f9f0-397">Bu ilkelerin Yöntemler veya alanlar üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-397">These policies have no effect on methods or fields.</span></span>

<span data-ttu-id="6f9f0-398">Daha fazla bilgi için [Windows mağazası uygulamanızı .NET Native geçirme](migrating-your-windows-store-app-to-net-native.md)konusunun "Serileştiricilerle ilgili farklılıklar" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-398">For more information, see the "Differences in Serializers" section in [Migrating Your Windows Store App to .NET Native](migrating-your-windows-store-app-to-net-native.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6f9f0-399">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f9f0-399">See also</span></span>

- [<span data-ttu-id="6f9f0-400">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="6f9f0-400">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="6f9f0-401">Yansıma ve .NET Native</span><span class="sxs-lookup"><span data-stu-id="6f9f0-401">Reflection and .NET Native</span></span>](reflection-and-net-native.md)
