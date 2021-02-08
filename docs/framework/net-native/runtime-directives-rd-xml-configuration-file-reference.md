---
description: 'Hakkında daha fazla bilgi edinin: çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu'
title: Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu
ms.date: 03/30/2017
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
ms.openlocfilehash: 9c995bd831f01e47c651d015895398e1ad42633d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802001"
---
# <a name="runtime-directives-rdxml-configuration-file-reference"></a><span data-ttu-id="f77fd-103">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="f77fd-103">Runtime Directives (rd.xml) Configuration File Reference</span></span>

<span data-ttu-id="f77fd-104">Çalışma zamanı yönergeleri (.rd.xml) dosyası, belirtilen program öğelerinin yansıma için kullanılabilir olup olmadığını belirten bir XML yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="f77fd-104">A runtime directives (.rd.xml) file is an XML configuration file that specifies whether designated program elements are available for reflection.</span></span> <span data-ttu-id="f77fd-105">Çalışma zamanı yönergeleri dosyasına bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f77fd-105">Here’s an example of a runtime directives file:</span></span>

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

## <a name="the-structure-of-a-runtime-directives-file"></a><span data-ttu-id="f77fd-106">Çalışma zamanı yönergeleri dosyasının yapısı</span><span class="sxs-lookup"><span data-stu-id="f77fd-106">The structure of a runtime directives file</span></span>

<span data-ttu-id="f77fd-107">Çalışma zamanı yönergeleri dosyası `http://schemas.microsoft.com/netfx/2013/01/metadata` ad alanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="f77fd-107">The runtime directives file uses the `http://schemas.microsoft.com/netfx/2013/01/metadata` namespace.</span></span>

<span data-ttu-id="f77fd-108">Kök öğesi, [yönergeleri](directives-element-net-native.md) öğesidir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-108">The root element is the [Directives](directives-element-net-native.md) element.</span></span> <span data-ttu-id="f77fd-109">Aşağıdaki yapıda gösterildiği gibi sıfır veya daha fazla [kitaplık](library-element-net-native.md) öğesi ve sıfır veya bir [uygulama](application-element-net-native.md) öğesi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-109">It can contain zero or more [Library](library-element-net-native.md) elements, and zero or one [Application](application-element-net-native.md) element, as shown in the following structure.</span></span> <span data-ttu-id="f77fd-110">[Uygulama](application-element-net-native.md) öğesinin öznitelikleri, uygulama genelinde çalışma zamanı yansıma ilkesi tanımlayabilir veya alt öğeler için bir kapsayıcı olarak görev yapabilir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-110">The attributes of the [Application](application-element-net-native.md) element can define application-wide runtime reflection policy, or it can serve as a container for child elements.</span></span> <span data-ttu-id="f77fd-111">Öte yandan [kitaplık](library-element-net-native.md) öğesi yalnızca bir kapsayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="f77fd-111">The [Library](library-element-net-native.md) element, on the other hand, is simply a container.</span></span> <span data-ttu-id="f77fd-112">[Uygulama](application-element-net-native.md) ve [kitaplık](library-element-net-native.md) öğelerinin alt öğeleri, yansıma için kullanılabilen türleri, yöntemleri, alanları, özellikleri ve olayları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f77fd-112">The children of the [Application](application-element-net-native.md) and [Library](library-element-net-native.md) elements define the types, methods, fields, properties, and events that are available for reflection.</span></span>

<span data-ttu-id="f77fd-113">Başvuru bilgileri için aşağıdaki yapıdaki öğeleri seçin veya [çalışma zamanı yönerge öğelerini](runtime-directive-elements.md)görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="f77fd-113">For reference information, choose elements from the following structure or see [Runtime Directive Elements](runtime-directive-elements.md).</span></span> <span data-ttu-id="f77fd-114">Aşağıdaki hiyerarşide üç nokta özyinelemeli bir yapıyı işaret ediyor.</span><span class="sxs-lookup"><span data-stu-id="f77fd-114">In the following hierarchy, the ellipsis marks a recursive structure.</span></span> <span data-ttu-id="f77fd-115">Köşeli ayraçlar içindeki bilgiler, bu öğenin isteğe bağlı veya gerekli olduğunu ve kullanılıp kullanılmadığını, kaç örneğe (bir veya daha fazla) izin verildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-115">The information in brackets indicates whether that element is optional or required, and if it is used, how many instances (one or many) are allowed.</span></span>

- <span data-ttu-id="f77fd-116">[Yönergeler](directives-element-net-native.md) [1:1]</span><span class="sxs-lookup"><span data-stu-id="f77fd-116">[Directives](directives-element-net-native.md) [1:1]</span></span>
  - <span data-ttu-id="f77fd-117">[Uygulama](application-element-net-native.md) [0:1]</span><span class="sxs-lookup"><span data-stu-id="f77fd-117">[Application](application-element-net-native.md) [0:1]</span></span>
    - <span data-ttu-id="f77fd-118">[Derleme](assembly-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="f77fd-118">[Assembly](assembly-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="f77fd-119">[Ad alanı](namespace-element-net-native.md) [0: d].</span><span class="sxs-lookup"><span data-stu-id="f77fd-119">[Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="f77fd-120">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-120">.</span></span> <span data-ttu-id="f77fd-121">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-121">.</span></span>
      - <span data-ttu-id="f77fd-122">[0: d] [yazın](type-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="f77fd-122">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="f77fd-123">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-123">.</span></span> <span data-ttu-id="f77fd-124">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-124">.</span></span>
      - <span data-ttu-id="f77fd-125">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: a].</span><span class="sxs-lookup"><span data-stu-id="f77fd-125">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="f77fd-126">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-126">.</span></span> <span data-ttu-id="f77fd-127">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-127">.</span></span>
    - <span data-ttu-id="f77fd-128">[Ad alanı](namespace-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="f77fd-128">[Namespace](namespace-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="f77fd-129">[Ad alanı](namespace-element-net-native.md) [0: d].</span><span class="sxs-lookup"><span data-stu-id="f77fd-129">[Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="f77fd-130">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-130">.</span></span> <span data-ttu-id="f77fd-131">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-131">.</span></span>
      - <span data-ttu-id="f77fd-132">[0: d] [yazın](type-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="f77fd-132">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="f77fd-133">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-133">.</span></span> <span data-ttu-id="f77fd-134">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-134">.</span></span>
      - <span data-ttu-id="f77fd-135">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: a].</span><span class="sxs-lookup"><span data-stu-id="f77fd-135">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="f77fd-136">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-136">.</span></span> <span data-ttu-id="f77fd-137">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-137">.</span></span>
    - <span data-ttu-id="f77fd-138">[Tür](type-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="f77fd-138">[Type](type-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="f77fd-139">Alt [türler](subtypes-element-net-native.md) (kapsayan türün alt sınıfları) [o:1]</span><span class="sxs-lookup"><span data-stu-id="f77fd-139">[Subtypes](subtypes-element-net-native.md) (subclasses of the containing type) [O:1]</span></span>
      - <span data-ttu-id="f77fd-140">[0: d] [yazın](type-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="f77fd-140">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="f77fd-141">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-141">.</span></span> <span data-ttu-id="f77fd-142">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-142">.</span></span>
      - <span data-ttu-id="f77fd-143">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: a].</span><span class="sxs-lookup"><span data-stu-id="f77fd-143">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="f77fd-144">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-144">.</span></span> <span data-ttu-id="f77fd-145">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-145">.</span></span>
      - <span data-ttu-id="f77fd-146">[Attributeme](attributeimplies-element-net-native.md) (tür içeren bir öznitelik) [o:1]</span><span class="sxs-lookup"><span data-stu-id="f77fd-146">[AttributeImplies](attributeimplies-element-net-native.md) (containing type is an attribute) [O:1]</span></span>
      - <span data-ttu-id="f77fd-147">[Genericparameter](genericparameter-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="f77fd-147">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="f77fd-148">[Yöntem](method-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="f77fd-148">[Method](method-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="f77fd-149">[Parametre](parameter-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="f77fd-149">[Parameter](parameter-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="f77fd-150">[Typeparameter](typeparameter-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="f77fd-150">[TypeParameter](typeparameter-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="f77fd-151">[Genericparameter](genericparameter-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="f77fd-151">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="f77fd-152">[Methodörneklemesi](methodinstantiation-element-net-native.md) (oluşturulmuş genel yöntem) [0: a]</span><span class="sxs-lookup"><span data-stu-id="f77fd-152">[MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>
      - <span data-ttu-id="f77fd-153">[Özellik](property-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="f77fd-153">[Property](property-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="f77fd-154">[Alan](field-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="f77fd-154">[Field](field-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="f77fd-155">[Olay](event-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="f77fd-155">[Event](event-element-net-native.md) [0:M]</span></span>
    - <span data-ttu-id="f77fd-156">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: d]</span><span class="sxs-lookup"><span data-stu-id="f77fd-156">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>
      - <span data-ttu-id="f77fd-157">[0: d] [yazın](type-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="f77fd-157">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="f77fd-158">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-158">.</span></span> <span data-ttu-id="f77fd-159">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-159">.</span></span>
      - <span data-ttu-id="f77fd-160">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: a].</span><span class="sxs-lookup"><span data-stu-id="f77fd-160">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="f77fd-161">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-161">.</span></span> <span data-ttu-id="f77fd-162">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-162">.</span></span>
      - <span data-ttu-id="f77fd-163">[Yöntem](method-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="f77fd-163">[Method](method-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="f77fd-164">[Parametre](parameter-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="f77fd-164">[Parameter](parameter-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="f77fd-165">[Typeparameter](typeparameter-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="f77fd-165">[TypeParameter](typeparameter-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="f77fd-166">[Genericparameter](genericparameter-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="f77fd-166">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="f77fd-167">[Methodörneklemesi](methodinstantiation-element-net-native.md) (oluşturulmuş genel yöntem) [0: a]</span><span class="sxs-lookup"><span data-stu-id="f77fd-167">[MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>
      - <span data-ttu-id="f77fd-168">[Özellik](property-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="f77fd-168">[Property](property-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="f77fd-169">[Alan](field-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="f77fd-169">[Field](field-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="f77fd-170">[Olay](event-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="f77fd-170">[Event](event-element-net-native.md) [0:M]</span></span>
  - <span data-ttu-id="f77fd-171">[Kitaplık](library-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="f77fd-171">[Library](library-element-net-native.md) [0:M]</span></span>
    - <span data-ttu-id="f77fd-172">[Derleme](assembly-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="f77fd-172">[Assembly](assembly-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="f77fd-173">[Ad alanı](namespace-element-net-native.md) [0: d].</span><span class="sxs-lookup"><span data-stu-id="f77fd-173">[Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="f77fd-174">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-174">.</span></span> <span data-ttu-id="f77fd-175">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-175">.</span></span>
      - <span data-ttu-id="f77fd-176">[0: d] [yazın](type-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="f77fd-176">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="f77fd-177">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-177">.</span></span> <span data-ttu-id="f77fd-178">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-178">.</span></span>
      - <span data-ttu-id="f77fd-179">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: a].</span><span class="sxs-lookup"><span data-stu-id="f77fd-179">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="f77fd-180">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-180">.</span></span> <span data-ttu-id="f77fd-181">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-181">.</span></span>
    - <span data-ttu-id="f77fd-182">[Ad alanı](namespace-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="f77fd-182">[Namespace](namespace-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="f77fd-183">[Ad alanı](namespace-element-net-native.md) [0: d].</span><span class="sxs-lookup"><span data-stu-id="f77fd-183">[Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="f77fd-184">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-184">.</span></span> <span data-ttu-id="f77fd-185">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-185">.</span></span>
      - <span data-ttu-id="f77fd-186">[0: d] [yazın](type-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="f77fd-186">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="f77fd-187">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-187">.</span></span> <span data-ttu-id="f77fd-188">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-188">.</span></span>
      - <span data-ttu-id="f77fd-189">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: a].</span><span class="sxs-lookup"><span data-stu-id="f77fd-189">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="f77fd-190">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-190">.</span></span> <span data-ttu-id="f77fd-191">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-191">.</span></span>
    - <span data-ttu-id="f77fd-192">[Tür](type-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="f77fd-192">[Type](type-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="f77fd-193">Alt [türler](subtypes-element-net-native.md) (kapsayan türün alt sınıfları) [o:1]</span><span class="sxs-lookup"><span data-stu-id="f77fd-193">[Subtypes](subtypes-element-net-native.md) (subclasses of the containing type) [O:1]</span></span>
      - <span data-ttu-id="f77fd-194">[0: d] [yazın](type-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="f77fd-194">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="f77fd-195">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-195">.</span></span> <span data-ttu-id="f77fd-196">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-196">.</span></span>
      - <span data-ttu-id="f77fd-197">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: a].</span><span class="sxs-lookup"><span data-stu-id="f77fd-197">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="f77fd-198">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-198">.</span></span> <span data-ttu-id="f77fd-199">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-199">.</span></span>
      - <span data-ttu-id="f77fd-200">[Attributeme](attributeimplies-element-net-native.md) (tür içeren bir öznitelik) [o:1]</span><span class="sxs-lookup"><span data-stu-id="f77fd-200">[AttributeImplies](attributeimplies-element-net-native.md) (containing type is an attribute) [O:1]</span></span>
      - <span data-ttu-id="f77fd-201">[Genericparameter](genericparameter-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="f77fd-201">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="f77fd-202">[Yöntem](method-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="f77fd-202">[Method](method-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="f77fd-203">[Methodörneklemesi](methodinstantiation-element-net-native.md) (oluşturulmuş genel yöntem) [0: a]</span><span class="sxs-lookup"><span data-stu-id="f77fd-203">[MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>
      - <span data-ttu-id="f77fd-204">[Özellik](property-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="f77fd-204">[Property](property-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="f77fd-205">[Alan](field-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="f77fd-205">[Field](field-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="f77fd-206">[Olay](event-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="f77fd-206">[Event](event-element-net-native.md) [0:M]</span></span>
    - <span data-ttu-id="f77fd-207">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: d]</span><span class="sxs-lookup"><span data-stu-id="f77fd-207">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>
      - <span data-ttu-id="f77fd-208">[0: d] [yazın](type-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="f77fd-208">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="f77fd-209">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-209">.</span></span> <span data-ttu-id="f77fd-210">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-210">.</span></span>
      - <span data-ttu-id="f77fd-211">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: a].</span><span class="sxs-lookup"><span data-stu-id="f77fd-211">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="f77fd-212">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-212">.</span></span> <span data-ttu-id="f77fd-213">.</span><span class="sxs-lookup"><span data-stu-id="f77fd-213">.</span></span>
      - <span data-ttu-id="f77fd-214">[Yöntem](method-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="f77fd-214">[Method](method-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="f77fd-215">[Methodörneklemesi](methodinstantiation-element-net-native.md) (oluşturulmuş genel yöntem) [0: a]</span><span class="sxs-lookup"><span data-stu-id="f77fd-215">[MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>
      - <span data-ttu-id="f77fd-216">[Özellik](property-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="f77fd-216">[Property](property-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="f77fd-217">[Alan](field-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="f77fd-217">[Field](field-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="f77fd-218">[Olay](event-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="f77fd-218">[Event](event-element-net-native.md) [0:M]</span></span>

<span data-ttu-id="f77fd-219">[Uygulama](application-element-net-native.md) öğesinin hiç özniteliği olamaz veya [çalışma zamanı yönergesinde ve ilke bölümünde](#Directives)ele alınan ilke özniteliklerine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-219">The [Application](application-element-net-native.md) element can have no attributes, or it can have the policy attributes discussed in the [Runtime directive and policy section](#Directives).</span></span>

<span data-ttu-id="f77fd-220">Bir [kitaplık](library-element-net-native.md) öğesi, `Name` dosya uzantısı olmadan bir kitaplığın veya derlemenin adını belirten tek bir özniteliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-220">A [Library](library-element-net-native.md) element has a single attribute, `Name`, that specifies the name of a library or assembly, without its file extension.</span></span> <span data-ttu-id="f77fd-221">Örneğin, aşağıdaki [kitaplık](library-element-net-native.md) öğesi Extensions.dll adlı bir derleme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-221">For example, the following [Library](library-element-net-native.md) element applies to an assembly named Extensions.dll.</span></span>

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

## <a name="runtime-directives-and-policy"></a><span data-ttu-id="f77fd-222">Çalışma zamanı yönergeleri ve ilkesi</span><span class="sxs-lookup"><span data-stu-id="f77fd-222">Runtime directives and policy</span></span>

<span data-ttu-id="f77fd-223">[Uygulama](application-element-net-native.md) öğesinin kendisi ve [kitaplık](library-element-net-native.md) ve [uygulama](application-element-net-native.md) öğeleri Express ilkesinin alt öğeleri; diğer bir deyişle, bir uygulamanın bir program öğesine yansıma uygulayabileceği şekilde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f77fd-223">The [Application](application-element-net-native.md) element itself and the child elements of the [Library](library-element-net-native.md) and [Application](application-element-net-native.md) elements express policy; that is, they define the way in which an app can apply reflection to a program element.</span></span> <span data-ttu-id="f77fd-224">İlke türü, öğesinin bir özniteliği tarafından tanımlanır (örneğin, `Serialize` ).</span><span class="sxs-lookup"><span data-stu-id="f77fd-224">The policy type is defined by an attribute of the element (for example, `Serialize`).</span></span> <span data-ttu-id="f77fd-225">İlke değeri özniteliğin değeri (örneğin,) tarafından tanımlanır `Serialize="Required"` .</span><span class="sxs-lookup"><span data-stu-id="f77fd-225">The policy value is defined by the attribute’s value (for example, `Serialize="Required"`).</span></span>

<span data-ttu-id="f77fd-226">Bir öğenin özniteliği tarafından belirtilen herhangi bir ilke, bu ilke için bir değer belirtmeyen tüm alt öğeler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-226">Any policy specified by an attribute of an element applies to all child elements that don’t specify a value for that policy.</span></span> <span data-ttu-id="f77fd-227">Örneğin, bir ilke bir [tür](type-element-net-native.md) öğesiyle belirtilmişse, bu ilke, bir ilkenin açıkça belirtilmediği tüm içerilen türler ve Üyeler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-227">For example, if a policy is specified by a [Type](type-element-net-native.md) element, that policy applies to all contained types and members for which a policy is not explicitly specified.</span></span>

<span data-ttu-id="f77fd-228">[Uygulama](application-element-net-native.md), [derleme](assembly-element-net-native.md), [attributeby](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), alt [türler](subtypes-element-net-native.md)ve [tür](type-element-net-native.md) öğeleri tarafından Ifade edilen ilke, ayrı Üyeler Için ifade edilebilir ilkeden farklıdır ( [Yöntem](method-element-net-native.md), [özellik](property-element-net-native.md), [alan](field-element-net-native.md)ve [olay](event-element-net-native.md) öğeleri tarafından).</span><span class="sxs-lookup"><span data-stu-id="f77fd-228">The policy that can be expressed by the [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md), and [Type](type-element-net-native.md) elements differs from the policy that can be expressed for individual members (by the [Method](method-element-net-native.md), [Property](property-element-net-native.md), [Field](field-element-net-native.md), and [Event](event-element-net-native.md) elements).</span></span>

### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a><span data-ttu-id="f77fd-229">Derlemeler, ad alanları ve türler için ilke belirtme</span><span class="sxs-lookup"><span data-stu-id="f77fd-229">Specifying policy for assemblies, namespaces, and types</span></span>

<span data-ttu-id="f77fd-230">[Uygulama](application-element-net-native.md), [derleme](assembly-element-net-native.md), [attributeme](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), alt [türleri](subtypes-element-net-native.md)ve [tür](type-element-net-native.md) öğeleri aşağıdaki ilke türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="f77fd-230">The [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md), and [Type](type-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="f77fd-231">`Activate`.</span><span class="sxs-lookup"><span data-stu-id="f77fd-231">`Activate`.</span></span> <span data-ttu-id="f77fd-232">Örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="f77fd-232">Controls runtime access to constructors, to enable activation of instances.</span></span>

- <span data-ttu-id="f77fd-233">`Browse`.</span><span class="sxs-lookup"><span data-stu-id="f77fd-233">`Browse`.</span></span> <span data-ttu-id="f77fd-234">Program öğeleri hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="f77fd-234">Controls querying for information about program elements but does not enable any runtime access.</span></span>

- <span data-ttu-id="f77fd-235">`Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="f77fd-235">`Dynamic`.</span></span> <span data-ttu-id="f77fd-236">Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="f77fd-236">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>

- <span data-ttu-id="f77fd-237">`Serialize`.</span><span class="sxs-lookup"><span data-stu-id="f77fd-237">`Serialize`.</span></span> <span data-ttu-id="f77fd-238">Tür örneklerinin, Newtonsoft JSON serileştirici gibi üçüncü taraf kitaplıklara serileştirilmesi ve serileştirilmesi için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="f77fd-238">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and serialized by third-party libraries such as the Newtonsoft JSON serializer.</span></span>

- <span data-ttu-id="f77fd-239">`DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="f77fd-239">`DataContractSerializer`.</span></span> <span data-ttu-id="f77fd-240">Sınıfını kullanan serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f77fd-240">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="f77fd-241">`DataContractJsonSerializer`.</span><span class="sxs-lookup"><span data-stu-id="f77fd-241">`DataContractJsonSerializer`.</span></span> <span data-ttu-id="f77fd-242">Sınıfını kullanan JSON serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f77fd-242">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="f77fd-243">`XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="f77fd-243">`XmlSerializer`.</span></span> <span data-ttu-id="f77fd-244">Sınıfını kullanan XML serileştirme ilkesini denetler <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f77fd-244">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="f77fd-245">`MarshalObject`.</span><span class="sxs-lookup"><span data-stu-id="f77fd-245">`MarshalObject`.</span></span> <span data-ttu-id="f77fd-246">WinRT ve COM 'a başvuru türlerini hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="f77fd-246">Controls policy for marshaling reference types to WinRT and COM.</span></span>

- <span data-ttu-id="f77fd-247">`MarshalDelegate`.</span><span class="sxs-lookup"><span data-stu-id="f77fd-247">`MarshalDelegate`.</span></span> <span data-ttu-id="f77fd-248">Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="f77fd-248">Controls policy for marshaling delegate types as function pointers to native code.</span></span>

- <span data-ttu-id="f77fd-249">`MarshalStructure` .</span><span class="sxs-lookup"><span data-stu-id="f77fd-249">`MarshalStructure` .</span></span> <span data-ttu-id="f77fd-250">Yapıları yerel koda hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="f77fd-250">Controls policy for marshaling structures to native code.</span></span>

<span data-ttu-id="f77fd-251">Bu ilke türleriyle ilişkili ayarlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f77fd-251">The settings associated with these policy types are:</span></span>

- <span data-ttu-id="f77fd-252">`All`.</span><span class="sxs-lookup"><span data-stu-id="f77fd-252">`All`.</span></span> <span data-ttu-id="f77fd-253">Araç zincirinin kaldıramayan tüm türler ve Üyeler için ilkeyi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="f77fd-253">Enable the policy for all types and members that the tool chain does not remove.</span></span>

- <span data-ttu-id="f77fd-254">`Auto`.</span><span class="sxs-lookup"><span data-stu-id="f77fd-254">`Auto`.</span></span> <span data-ttu-id="f77fd-255">Varsayılan davranışı kullanın.</span><span class="sxs-lookup"><span data-stu-id="f77fd-255">Use the default behavior.</span></span> <span data-ttu-id="f77fd-256">(İlke belirtilmemeksizin `Auto` , ilke geçersiz kılınmadıkça, örneğin bir üst öğe ile, bu ilkeyi ayarlamaya eşdeğerdir.)</span><span class="sxs-lookup"><span data-stu-id="f77fd-256">(Not specifying a policy is equivalent to setting that policy to `Auto` unless that policy is overridden, for example by a parent element.)</span></span>

- <span data-ttu-id="f77fd-257">`Excluded`.</span><span class="sxs-lookup"><span data-stu-id="f77fd-257">`Excluded`.</span></span> <span data-ttu-id="f77fd-258">Program öğesi için ilkeyi devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="f77fd-258">Disable the policy for the program element.</span></span>

- <span data-ttu-id="f77fd-259">`Public`.</span><span class="sxs-lookup"><span data-stu-id="f77fd-259">`Public`.</span></span> <span data-ttu-id="f77fd-260">Araç zinciri üyenin gereksiz olduğunu belirlerse ve bu nedenle uygulamayı kaldırmadığı müddetçe ortak türler veya Üyeler için ilkeyi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="f77fd-260">Enable the policy for public types or members unless the tool chain determines that the member is unnecessary and therefore removes it.</span></span> <span data-ttu-id="f77fd-261">(İkinci durumda, `Required Public` üyenin tutulduğundan ve yansıma özelliklerine sahip olduğundan emin olmak için kullanmanız gerekir.)</span><span class="sxs-lookup"><span data-stu-id="f77fd-261">(In the latter case, you must use `Required Public` to ensure that the member is kept and has reflection capabilities.)</span></span>

- <span data-ttu-id="f77fd-262">`PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="f77fd-262">`PublicAndInternal`.</span></span> <span data-ttu-id="f77fd-263">Araç zinciri onları kaldırmazsa ortak ve iç türler veya Üyeler için ilkeyi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="f77fd-263">Enable the policy for public and internal types or members if the tool chain doesn't remove them.</span></span>

- <span data-ttu-id="f77fd-264">`Required Public`.</span><span class="sxs-lookup"><span data-stu-id="f77fd-264">`Required Public`.</span></span> <span data-ttu-id="f77fd-265">Ortak türleri ve üyeleri, kullanıldıkları ve kullanılmayacağı gibi tutmak ve ilke için etkinleştirmek üzere araç zinciri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-265">Require the tool chain to keep public types and members whether or not they are used, and enable the policy for them.</span></span>

- <span data-ttu-id="f77fd-266">`Required PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="f77fd-266">`Required PublicAndInternal`.</span></span> <span data-ttu-id="f77fd-267">Araç zincirinin hem ortak hem de iç türleri ve üyeleri, kullanılmalarına bakılmaksızın ve bunları kendileri için etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="f77fd-267">Require the tool chain to keep both public and internal types and members whether or not they are used, and enable the policy for them.</span></span>

- <span data-ttu-id="f77fd-268">`Required All`.</span><span class="sxs-lookup"><span data-stu-id="f77fd-268">`Required All`.</span></span> <span data-ttu-id="f77fd-269">Araç zincirinin tüm türleri ve üyeleri kullanıp kullanmadığını ve bunların kullanılmadığını ve ilke için etkin olmasını gerektir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-269">Require the tool chain to keep all types and members whether or not they are used, and enable the policy for them.</span></span>

<span data-ttu-id="f77fd-270">Örneğin, aşağıdaki çalışma zamanı yönergeleri dosyası DataClasses.dll derlemedeki tüm türler ve Üyeler için ilkeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f77fd-270">For example, the following runtime directives file defines policy for all types and members in the assembly DataClasses.dll.</span></span> <span data-ttu-id="f77fd-271">Tüm ortak özelliklerin serileştirilmesi için yansıma kullanımını, tüm türler ve tür üyeleri için gözatmayı etkinleştirmek, tüm türler için etkinleştirmeyi etkinleştirmek ( `Dynamic` özniteliği nedeniyle) ve tüm genel türler ve Üyeler için yansıma 'yi etkinleştirmek.</span><span class="sxs-lookup"><span data-stu-id="f77fd-271">It enables reflection for serialization of all public properties, enables browsing for all types and type members, enables activation for all types (because of the `Dynamic` attribute), and enables reflection for all public types and members.</span></span>

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

### <a name="specifying-policy-for-members"></a><span data-ttu-id="f77fd-272">Üyeler için ilke belirtme</span><span class="sxs-lookup"><span data-stu-id="f77fd-272">Specifying policy for members</span></span>

<span data-ttu-id="f77fd-273">[Özellik](property-element-net-native.md) ve [alan](field-element-net-native.md) öğeleri aşağıdaki ilke türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="f77fd-273">The [Property](property-element-net-native.md) and [Field](field-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="f77fd-274">`Browse` -Bu üye hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="f77fd-274">`Browse` - Controls querying for information about this member but does not enable any runtime access.</span></span>

- <span data-ttu-id="f77fd-275">`Dynamic` -Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="f77fd-275">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="f77fd-276">Ayrıca, kapsayan tür hakkındaki bilgileri sorgulamayı denetler.</span><span class="sxs-lookup"><span data-stu-id="f77fd-276">Also controls querying for information about the containing type.</span></span>

- <span data-ttu-id="f77fd-277">`Serialize` -Tür örneklerinin, Newtonsoft JSON serileştirici gibi kitaplıklar tarafından serileştirilmesi ve seri durumdan çıkarılmakta olması için üyeye çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="f77fd-277">`Serialize` - Controls runtime access to the member to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span> <span data-ttu-id="f77fd-278">Bu ilke oluşturucular, alanlar ve özelliklere uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-278">This policy can be applied to constructors, fields, and properties.</span></span>

<span data-ttu-id="f77fd-279">[Yöntemi](method-element-net-native.md) ve [olay](event-element-net-native.md) öğeleri aşağıdaki ilke türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="f77fd-279">The [Method](method-element-net-native.md) and [Event](event-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="f77fd-280">`Browse` -Bu üye hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="f77fd-280">`Browse` - Controls querying for information about this member but doesn’t enable any runtime access.</span></span>

- <span data-ttu-id="f77fd-281">`Dynamic` -Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="f77fd-281">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="f77fd-282">Ayrıca, kapsayan tür hakkındaki bilgileri sorgulamayı denetler.</span><span class="sxs-lookup"><span data-stu-id="f77fd-282">Also controls querying for information about the containing type.</span></span>

 <span data-ttu-id="f77fd-283">Bu ilke türleriyle ilişkili ayarlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f77fd-283">The settings associated with these policy types are:</span></span>

- <span data-ttu-id="f77fd-284">`Auto` -Varsayılan davranışı kullanın.</span><span class="sxs-lookup"><span data-stu-id="f77fd-284">`Auto` - Use the default behavior.</span></span> <span data-ttu-id="f77fd-285">(Bir ilke belirtmeksizin, bir `Auto` öğe geçersiz kılınmadığı takdirde bu ilkeyi ayarlamaya eşdeğerdir.)</span><span class="sxs-lookup"><span data-stu-id="f77fd-285">(Not specifying a policy is equivalent to setting that policy to `Auto` unless something overrides it.)</span></span>

- <span data-ttu-id="f77fd-286">`Excluded` -Üyenin meta verilerini hiçbir şekilde eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="f77fd-286">`Excluded` - Never include metadata for the member.</span></span>

- <span data-ttu-id="f77fd-287">`Included` -Üst tür çıktıda varsa ilkeyi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="f77fd-287">`Included` - Enable the policy if the parent type is present in the output.</span></span>

- <span data-ttu-id="f77fd-288">`Required` -Araç zincirinin, kullanılmamış gibi görünse bile bu üyeyi tutması gerekir ve ilkeyi etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-288">`Required` - Require the tool chain to keep this member even if appears to be unused, and enable policy for it.</span></span>

## <a name="runtime-directives-file-semantics"></a><span data-ttu-id="f77fd-289">Çalışma zamanı yönergeleri dosya semantiği</span><span class="sxs-lookup"><span data-stu-id="f77fd-289">Runtime directives file semantics</span></span>

<span data-ttu-id="f77fd-290">İlke, hem daha yüksek hem de alt düzey öğeler için eşzamanlı olarak tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-290">Policy can be defined simultaneously for both higher-level and lower-level elements.</span></span> <span data-ttu-id="f77fd-291">Örneğin, ilke bir derleme için ve bu derlemede yer alan bazı türler için tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-291">For example, policy can be defined for an assembly, and for some of the types contained in that assembly.</span></span> <span data-ttu-id="f77fd-292">Belirli bir alt düzey öğe gösterilmediğinden, üst öğesinin ilkesini devralır.</span><span class="sxs-lookup"><span data-stu-id="f77fd-292">If a particular lower-level element is not represented, it inherits the policy of its parent.</span></span> <span data-ttu-id="f77fd-293">Örneğin, bir `Assembly` öğe mevcutsa ancak `Type` öğeler yoksa, öğesinde belirtilen ilke `Assembly` derlemedeki her tür için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-293">For example, if an `Assembly` element is present but `Type` elements are not, the policy specified in the `Assembly` element applies to each type in the assembly.</span></span> <span data-ttu-id="f77fd-294">Aynı program öğesine aynı zamanda birden çok öğe ilke uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-294">Multiple elements can also apply policy to the same program element.</span></span> <span data-ttu-id="f77fd-295">Örneğin, ayrı [derleme](assembly-element-net-native.md) öğeleri aynı derleme için aynı ilke öğesini farklı şekilde tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-295">For example, separate [Assembly](assembly-element-net-native.md) elements might define the same policy element for the same assembly differently.</span></span> <span data-ttu-id="f77fd-296">Aşağıdaki bölümlerde, belirli bir türün ilkesinin bu durumlarda nasıl çözümlendiğini açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f77fd-296">The following sections explain how the policy for a particular type is resolved in those cases.</span></span>

<span data-ttu-id="f77fd-297">Genel bir türün veya yöntemin [tür](type-element-net-native.md) veya [Yöntem](method-element-net-native.md) öğesi, kendi ilkesi olmayan tüm örneklemelerde ilkesini uygular.</span><span class="sxs-lookup"><span data-stu-id="f77fd-297">A [Type](type-element-net-native.md) or [Method](method-element-net-native.md) element of a generic type or method applies its policy to all instantiations that do not have their own policy.</span></span> <span data-ttu-id="f77fd-298">Örneğin, `Type` ilkesini belirten bir öğe, belirli bir <xref:System.Collections.Generic.List%601> oluşturulan genel tür için geçersiz kılınmadığı sürece (örneğin, bir `List<Int32>` öğesi tarafından), bu genel türün tüm oluşturulan örneklerine uygulanır `TypeInstantiation` .</span><span class="sxs-lookup"><span data-stu-id="f77fd-298">For example, a `Type` element that specifies policy for <xref:System.Collections.Generic.List%601> applies to all constructed instances of that generic type, unless it's overridden for a particular constructed generic type (such as a `List<Int32>`) by a `TypeInstantiation` element.</span></span> <span data-ttu-id="f77fd-299">Aksi takdirde, öğeleri adlı program öğesi için ilkeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f77fd-299">Otherwise, elements define policy for the program element named.</span></span>

<span data-ttu-id="f77fd-300">Bir öğe belirsiz olduğunda, motor eşleşme arar ve tam eşleşme bulursa onu kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="f77fd-300">When an element is ambiguous, the engine looks for matches, and if it finds an exact match, it will use it.</span></span> <span data-ttu-id="f77fd-301">Birden çok eşleşme bulunursa bir uyarı veya hata olur.</span><span class="sxs-lookup"><span data-stu-id="f77fd-301">If it finds multiple matches, there will be a warning or error.</span></span>

### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a><span data-ttu-id="f77fd-302">İki yönergeler aynı program öğesine ilke uygualıyorsa</span><span class="sxs-lookup"><span data-stu-id="f77fd-302">If two directives apply policy to the same program element</span></span>

<span data-ttu-id="f77fd-303">Farklı çalışma zamanı yönergeleri dosyalarındaki iki öğe aynı program öğesi (bir derleme veya tür gibi) için aynı ilke türünü farklı değerlere ayarlamaya çalışıyorsa, çakışma aşağıdaki gibi çözümlenir:</span><span class="sxs-lookup"><span data-stu-id="f77fd-303">If two elements in different runtime directives files try to set the same policy type for the same program element (such as an assembly or type) to different values, the conflict is resolved as follows:</span></span>

1. <span data-ttu-id="f77fd-304">`Excluded`Öğe varsa, önceliğe sahip olur.</span><span class="sxs-lookup"><span data-stu-id="f77fd-304">If the `Excluded` element is present, it has precedence.</span></span>

2. <span data-ttu-id="f77fd-305">`Required` , öğesinden önceliklidir `Required` .</span><span class="sxs-lookup"><span data-stu-id="f77fd-305">`Required` has precedence over not `Required`.</span></span>

3. <span data-ttu-id="f77fd-306">`All` önceliğe sahip olan `PublicAndInternal` , önceliği olan `Public` .</span><span class="sxs-lookup"><span data-stu-id="f77fd-306">`All` has precedence over `PublicAndInternal`, which has precedence over `Public`.</span></span>

4. <span data-ttu-id="f77fd-307">Herhangi bir açık ayar önceliklidir `Auto` .</span><span class="sxs-lookup"><span data-stu-id="f77fd-307">Any explicit setting has precedence over `Auto`.</span></span>

<span data-ttu-id="f77fd-308">Örneğin, tek bir proje aşağıdaki iki çalışma zamanı yönergeleri dosyasını içeriyorsa, DataClasses.dll için serileştirme ilkesi hem hem de olarak ayarlanır `Required Public` `All` .</span><span class="sxs-lookup"><span data-stu-id="f77fd-308">For example, if a single project includes the following two runtime directives files, the serialization policy for DataClasses.dll is set to both `Required Public` and `All`.</span></span> <span data-ttu-id="f77fd-309">Bu durumda, serileştirme ilkesi olarak çözümlenir `Required All` .</span><span class="sxs-lookup"><span data-stu-id="f77fd-309">In this case, the serialization policy would be resolved as `Required All`.</span></span>

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

<span data-ttu-id="f77fd-310">Ancak, tek bir çalışma zamanı yönergeleri dosyasında iki yönergesi aynı program öğesi için aynı ilke türünü ayarlamaya çalışırsanız, XML şeması tanım aracında bir hata iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-310">However, if two directives in a single runtime directives file try to set the same policy type for the same program element, the XML Scheme Definition tool displays an error message.</span></span>

### <a name="if-child-and-parent-elements-apply-the-same-policy-type"></a><span data-ttu-id="f77fd-311">Alt ve üst öğeler aynı ilke türünü uygualıyorsa</span><span class="sxs-lookup"><span data-stu-id="f77fd-311">If child and parent elements apply the same policy type</span></span>

<span data-ttu-id="f77fd-312">Alt öğeler, ayarı da dahil olmak üzere üst öğelerini geçersiz kılar `Excluded` .</span><span class="sxs-lookup"><span data-stu-id="f77fd-312">Child elements override their parent elements, including the `Excluded` setting.</span></span> <span data-ttu-id="f77fd-313">Geçersiz kılma, belirtmek istediğiniz ana nedendir `Auto` .</span><span class="sxs-lookup"><span data-stu-id="f77fd-313">Overriding is the main reason you would want to specify `Auto`.</span></span>

<span data-ttu-id="f77fd-314">Aşağıdaki örnekte, içinde olmayan her şey için serileştirme ilkesi ayarı `DataClasses` `DataClasses.ViewModels` , ve `Required Public` her ikisinde de olan her şey olacaktır `DataClasses` `DataClasses.ViewModels` `All` .</span><span class="sxs-lookup"><span data-stu-id="f77fd-314">In the following example, the serialization policy setting for everything in `DataClasses` that’s not in `DataClasses.ViewModels` would be `Required Public`, and everything that's in both `DataClasses` and `DataClasses.ViewModels` would be `All`.</span></span>

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

### <a name="if-open-generics-and-instantiated-elements-apply-the-same-policy-type"></a><span data-ttu-id="f77fd-315">Açık genel türler ve örneklenmiş öğeler aynı ilke türünü uygular</span><span class="sxs-lookup"><span data-stu-id="f77fd-315">If open generics and instantiated elements apply the same policy type</span></span>

<span data-ttu-id="f77fd-316">Aşağıdaki örnekte, `Dictionary<int,int>` `Browse` ilke yalnızca altyapının ilkeyi vermesi için başka bir nedeniniz varsa `Browse` (Aksi takdirde varsayılan davranış olur), ' ın her bir örneği için <xref:System.Collections.Generic.Dictionary%602> tüm üyeleri göz atılamaz olur.</span><span class="sxs-lookup"><span data-stu-id="f77fd-316">In the following example, `Dictionary<int,int>` is assigned the `Browse` policy only if the engine has another reason to give it the `Browse` policy (which would otherwise be the default behavior); every other instantiation of <xref:System.Collections.Generic.Dictionary%602> will have all of its members browsable.</span></span>

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

### <a name="how-policy-is-inferred"></a><span data-ttu-id="f77fd-317">İlke nasıl algılanır</span><span class="sxs-lookup"><span data-stu-id="f77fd-317">How policy is inferred</span></span>

<span data-ttu-id="f77fd-318">Her ilke türünün, bu ilke türü varlığının diğer yapıları nasıl etkilediğini tespit eden farklı kurallar kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="f77fd-318">Each policy type has a different set of rules that determine how the presence of that policy type affects other constructs.</span></span>

#### <a name="the-effect-of-browse-policy"></a><span data-ttu-id="f77fd-319">Tarayıcı ilkesinin etkisi</span><span class="sxs-lookup"><span data-stu-id="f77fd-319">The effect of Browse policy</span></span>

<span data-ttu-id="f77fd-320">`Browse`İlkeyi bir türe uygulamak aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="f77fd-320">Applying the `Browse` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="f77fd-321">Türün temel türü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-321">The base type of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f77fd-322">Tür bir genel ise, türün örneklenmemiş sürümü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-322">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f77fd-323">Tür bir `Invoke` temsilciyise, türdeki yöntem `Dynamic` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-323">If the type is a delegate, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="f77fd-324">Türün her arabirimi `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-324">Each interface of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f77fd-325">Türe uygulanan her bir özniteliğin türü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-325">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f77fd-326">Tür geneldir ise, her kısıtlama türü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-326">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f77fd-327">Tür geneldir ise, türün örneklendiği türler `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-327">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="f77fd-328">`Browse`İlkeyi bir yönteme uygulamak aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="f77fd-328">Applying the `Browse` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="f77fd-329">Yöntemin her bir parametre türü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-329">Each parameter type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f77fd-330">Metodun dönüş türü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-330">The return type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f77fd-331">Yöntemin kapsayan türü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-331">The containing type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f77fd-332">Yöntem, örneklenmiş genel bir yöntem ise, örneklenmiş genel yöntem `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-332">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f77fd-333">Yöntemine uygulanan her bir özniteliğin türü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-333">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f77fd-334">Yöntem geneldir ise, her kısıtlama türü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-334">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f77fd-335">Yöntem genel ise, yöntemin örneklendiği türler `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-335">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="f77fd-336">`Browse`İlkeyi bir alana uygulamak aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="f77fd-336">Applying the `Browse` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="f77fd-337">Alana uygulanan her bir özniteliğin türü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-337">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f77fd-338">Alanın türü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-338">The type of the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f77fd-339">Alanın ait olduğu tür `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-339">The type to which the field belongs is marked with the `Browse` policy.</span></span>

#### <a name="the-effect-of-dynamic-policy"></a><span data-ttu-id="f77fd-340">Dinamik ilkenin etkisi</span><span class="sxs-lookup"><span data-stu-id="f77fd-340">The effect of Dynamic policy</span></span>

<span data-ttu-id="f77fd-341">`Dynamic`İlkeyi bir türe uygulamak aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="f77fd-341">Applying the `Dynamic` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="f77fd-342">Türün temel türü `Dynamic` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-342">The base type of the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="f77fd-343">Tür bir genel ise, türün örneklenmemiş sürümü `Dynamic` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-343">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="f77fd-344">Tür bir temsilci türü ise, `Invoke` türdeki yöntem `Dynamic` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-344">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="f77fd-345">Türün her arabirimi `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-345">Each interface of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f77fd-346">Türe uygulanan her bir özniteliğin türü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-346">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f77fd-347">Tür geneldir ise, her kısıtlama türü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-347">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f77fd-348">Tür geneldir ise, türün örneklendiği türler `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-348">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="f77fd-349">`Dynamic`İlkeyi bir yönteme uygulamak aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="f77fd-349">Applying the `Dynamic` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="f77fd-350">Yöntemin her bir parametre türü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-350">Each parameter type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f77fd-351">Metodun dönüş türü `Dynamic` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-351">The return type of the method is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="f77fd-352">Yöntemin kapsayan türü `Dynamic` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-352">The containing type of the method is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="f77fd-353">Yöntem, örneklenmiş genel bir yöntem ise, örneklenmiş genel yöntem `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-353">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f77fd-354">Yöntemine uygulanan her bir özniteliğin türü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-354">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f77fd-355">Yöntem geneldir ise, her kısıtlama türü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-355">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f77fd-356">Yöntem genel ise, yöntemin örneklendiği türler `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-356">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f77fd-357">Yöntemi tarafından çağrılabilir `MethodInfo.Invoke` ve temsilci oluşturma tarafından mümkün hale gelir <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f77fd-357">The method can be invoked by `MethodInfo.Invoke`, and delegate creation becomes possible by <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="f77fd-358">`Dynamic`İlkeyi bir alana uygulamak aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="f77fd-358">Applying the `Dynamic` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="f77fd-359">Alana uygulanan her bir özniteliğin türü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-359">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f77fd-360">Alanın türü `Dynamic` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-360">The type of the field is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="f77fd-361">Alanın ait olduğu tür `Dynamic` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-361">The type to which the field belongs is marked with the `Dynamic` policy.</span></span>

#### <a name="the-effect-of-activation-policy"></a><span data-ttu-id="f77fd-362">Etkinleştirme ilkesinin etkisi</span><span class="sxs-lookup"><span data-stu-id="f77fd-362">The effect of Activation policy</span></span>

<span data-ttu-id="f77fd-363">Etkinleştirme ilkesini bir türe uygulamak aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="f77fd-363">Applying the Activation policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="f77fd-364">Tür bir genel ise, türün örneklenmemiş sürümü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-364">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f77fd-365">Tür bir temsilci türü ise, `Invoke` türdeki yöntem `Dynamic` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-365">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="f77fd-366">Türün oluşturucuları `Activation` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-366">Constructors of the type are marked with the `Activation` policy.</span></span>

<span data-ttu-id="f77fd-367">`Activation`İlkeyi bir yönteme uygulamak aşağıdaki ilke değişikliğini içerir:</span><span class="sxs-lookup"><span data-stu-id="f77fd-367">Applying the `Activation` policy to a method involves the following policy change:</span></span>

- <span data-ttu-id="f77fd-368">Oluşturucu <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> ve yöntemleri tarafından çağrılabilir <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f77fd-368">The constructor can be invoked by the <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> and <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="f77fd-369">Yöntemler için, `Activation` ilke yalnızca oluşturucuları etkiler.</span><span class="sxs-lookup"><span data-stu-id="f77fd-369">For methods, the `Activation` policy affects constructors only.</span></span>

<span data-ttu-id="f77fd-370">`Activation`İlkeyi bir alana uygulamak hiçbir etkiye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-370">Applying the `Activation` policy to a field has no effect.</span></span>

#### <a name="the-effect-of-serialize-policy"></a><span data-ttu-id="f77fd-371">Seri hale getirme ilkesinin etkisi</span><span class="sxs-lookup"><span data-stu-id="f77fd-371">The effect of Serialize policy</span></span>

<span data-ttu-id="f77fd-372">`Serialize`İlke, yaygın yansıma tabanlı serileştiricilerin kullanımını sunar.</span><span class="sxs-lookup"><span data-stu-id="f77fd-372">The `Serialize` policy enables the use of common reflection-based serializers.</span></span> <span data-ttu-id="f77fd-373">Ancak, Microsoft dışı serileştiricilerin tam yansıma erişimi desenleri Microsoft tarafından bilinmediğinden, bu ilke tamamen etkili olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-373">However, because the exact reflection access patterns of non-Microsoft serializers are not known to Microsoft, this policy may not be entirely effective.</span></span>

<span data-ttu-id="f77fd-374">`Serialize`İlkeyi bir türe uygulamak aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="f77fd-374">Applying the `Serialize` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="f77fd-375">Türün temel türü `Serialize` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-375">The base type of the type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="f77fd-376">Tür bir genel ise, türün örneklenmemiş sürümü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-376">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f77fd-377">Tür bir temsilci türü ise, `Invoke` türdeki yöntem `Dynamic` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-377">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="f77fd-378">Tür bir sabit listesi ise, bir tür dizisi `Serialize` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-378">If the type is an enumeration, an array of the type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="f77fd-379">Türü uygularsa <xref:System.Collections.Generic.IEnumerable%601> `T` `Serialize` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-379">If the type implements <xref:System.Collections.Generic.IEnumerable%601>, `T` is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="f77fd-380">Türü,,, <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.Generic.IList%601> <xref:System.Collections.Generic.ICollection%601> <xref:System.Collections.Generic.IReadOnlyCollection%601> , veya <xref:System.Collections.Generic.IReadOnlyList%601> , `T[]` <xref:System.Collections.Generic.List%601> `Serialize` ilkesiyle işaretlenir., ancak arabirim türünün hiçbir üyesi `Serialize` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-380">If the type is <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>, or <xref:System.Collections.Generic.IReadOnlyList%601>, then `T[]` and <xref:System.Collections.Generic.List%601> marked with the `Serialize` policy., but no members of the interface type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="f77fd-381">Tür ise, bu <xref:System.Collections.Generic.List%601> tür hiçbir üye `Serialize` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-381">If the type is <xref:System.Collections.Generic.List%601>, no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="f77fd-382">Tür ise <xref:System.Collections.Generic.IDictionary%602> <xref:System.Collections.Generic.Dictionary%602> `Serialize` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-382">If the type is <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> is marked with the `Serialize` policy.</span></span> <span data-ttu-id="f77fd-383">Ancak, türdeki hiçbir üye `Serialize` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-383">but no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="f77fd-384">Tür ise, bu <xref:System.Collections.Generic.Dictionary%602> tür hiçbir üye `Serialize` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-384">If the type is <xref:System.Collections.Generic.Dictionary%602>, no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="f77fd-385">Türü uygularsa <xref:System.Collections.Generic.IDictionary%602> `TKey` ve `TValue` `Serialize` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-385">If the type implements <xref:System.Collections.Generic.IDictionary%602>, `TKey` and `TValue` are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="f77fd-386">Her bir Oluşturucu, her özellik erişimcisi ve her bir alan `Serialize` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-386">Each constructor, each property accessor, and each field is marked with the `Serialize` policy.</span></span>

<span data-ttu-id="f77fd-387">`Serialize`İlkeyi bir yönteme uygulamak aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="f77fd-387">Applying the `Serialize` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="f77fd-388">Kapsayan tür `Serialize` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-388">The containing type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="f77fd-389">Metodun dönüş türü `Serialize` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-389">The return type of the method is marked with the `Serialize` policy.</span></span>

<span data-ttu-id="f77fd-390">`Serialize`İlkeyi bir alana uygulamak aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="f77fd-390">Applying the `Serialize` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="f77fd-391">Kapsayan tür `Serialize` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-391">The containing type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="f77fd-392">Alanın türü `Serialize` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-392">The type of the field is marked with the `Serialize` policy.</span></span>

#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserializer-policies"></a><span data-ttu-id="f77fd-393">XmlSerializer, DataContractSerializer ve DataContractJsonSerializer ilkelerinin etkisi</span><span class="sxs-lookup"><span data-stu-id="f77fd-393">The effect of XmlSerializer, DataContractSerializer, and DataContractJsonSerializer policies</span></span>

<span data-ttu-id="f77fd-394">`Serialize`Yansıma tabanlı serileştiriciler için tasarlanan ilkenin aksine,, <xref:System.Xml.Serialization.XmlSerializer> <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ilkeleri .NET Native araç zinciri tarafından bilinen bir seri hale getiriciler kümesini etkinleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f77fd-394">Unlike the `Serialize` policy, which is intended for reflection-based serializers, the <xref:System.Xml.Serialization.XmlSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer>, and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> policies are used to enable a set of serializers that are known to the .NET Native tool chain.</span></span> <span data-ttu-id="f77fd-395">Bu serileştiriciler yansıma kullanılarak uygulanmaz, ancak çalışma zamanında seri hale getirilebildiğiniz türler kümesi, yansıma \ olan türler gibi benzer şekilde belirlenir.</span><span class="sxs-lookup"><span data-stu-id="f77fd-395">These serializers are not implemented by using reflection, but the set of types that can be serialized at run time is determined in a similar manner as types that are reflectable.</span></span>

<span data-ttu-id="f77fd-396">Bu ilkelerin bir türe uygulanması, türün eşleşen serileştirici ile serileştirilmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f77fd-396">Applying one of these policies to a type enables the type to be serialized with the matching serializer.</span></span> <span data-ttu-id="f77fd-397">Ayrıca, serileştirme altyapısının serileştirilmesi gereken şekilde statik olarak belirleyebilmesi için herhangi bir tür de serileştirilebilir olur.</span><span class="sxs-lookup"><span data-stu-id="f77fd-397">Also, any types that the serialization engine can statically determine as needing serialization will also be serializable.</span></span>

<span data-ttu-id="f77fd-398">Bu ilkelerin Yöntemler veya alanlar üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="f77fd-398">These policies have no effect on methods or fields.</span></span>

<span data-ttu-id="f77fd-399">Daha fazla bilgi için [Windows mağazası uygulamanızı .NET Native geçirme](migrating-your-windows-store-app-to-net-native.md)konusunun "Serileştiricilerle ilgili farklılıklar" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f77fd-399">For more information, see the "Differences in Serializers" section in [Migrating Your Windows Store App to .NET Native](migrating-your-windows-store-app-to-net-native.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f77fd-400">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f77fd-400">See also</span></span>

- [<span data-ttu-id="f77fd-401">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="f77fd-401">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="f77fd-402">Yansıma ve .NET Yerel</span><span class="sxs-lookup"><span data-stu-id="f77fd-402">Reflection and .NET Native</span></span>](reflection-and-net-native.md)
