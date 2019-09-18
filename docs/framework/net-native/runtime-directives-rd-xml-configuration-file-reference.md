---
title: Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu
ms.date: 03/30/2017
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: adfc0ae6d9bdae333daacee525c7775acd5a8029
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049134"
---
# <a name="runtime-directives-rdxml-configuration-file-reference"></a><span data-ttu-id="f7ca6-102">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="f7ca6-102">Runtime Directives (rd.xml) Configuration File Reference</span></span>

<span data-ttu-id="f7ca6-103">Çalışma zamanı yönergeleri (. RD. xml) dosyası, belirtilen program öğelerinin yansıma için kullanılabilir olup olmadığını belirten bir XML yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-103">A runtime directives (.rd.xml) file is an XML configuration file that specifies whether designated program elements are available for reflection.</span></span> <span data-ttu-id="f7ca6-104">Çalışma zamanı yönergeleri dosyasına bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f7ca6-104">Here’s an example of a runtime directives file:</span></span>

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

## <a name="the-structure-of-a-runtime-directives-file"></a><span data-ttu-id="f7ca6-105">Çalışma zamanı yönergeleri dosyasının yapısı</span><span class="sxs-lookup"><span data-stu-id="f7ca6-105">The structure of a runtime directives file</span></span>

<span data-ttu-id="f7ca6-106">Çalışma zamanı yönergeleri dosyası `http://schemas.microsoft.com/netfx/2013/01/metadata` ad alanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-106">The runtime directives file uses the `http://schemas.microsoft.com/netfx/2013/01/metadata` namespace.</span></span>

<span data-ttu-id="f7ca6-107">Kök öğesi, [yönergeleri](directives-element-net-native.md) öğesidir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-107">The root element is the [Directives](directives-element-net-native.md) element.</span></span> <span data-ttu-id="f7ca6-108">Aşağıdaki yapıda gösterildiği gibi sıfır veya daha fazla [kitaplık](library-element-net-native.md) öğesi ve sıfır veya bir [uygulama](application-element-net-native.md) öğesi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-108">It can contain zero or more [Library](library-element-net-native.md) elements, and zero or one [Application](application-element-net-native.md) element, as shown in the following structure.</span></span> <span data-ttu-id="f7ca6-109">[Uygulama](application-element-net-native.md) öğesinin öznitelikleri, uygulama genelinde çalışma zamanı yansıma ilkesi tanımlayabilir veya alt öğeler için bir kapsayıcı olarak görev yapabilir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-109">The attributes of the [Application](application-element-net-native.md) element can define application-wide runtime reflection policy, or it can serve as a container for child elements.</span></span> <span data-ttu-id="f7ca6-110">Öte yandan [kitaplık](library-element-net-native.md) öğesi yalnızca bir kapsayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-110">The [Library](library-element-net-native.md) element, on the other hand, is simply a container.</span></span> <span data-ttu-id="f7ca6-111">[Uygulama](application-element-net-native.md) ve [kitaplık](library-element-net-native.md) öğelerinin alt öğeleri, yansıma için kullanılabilen türleri, yöntemleri, alanları, özellikleri ve olayları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-111">The children of the [Application](application-element-net-native.md) and [Library](library-element-net-native.md) elements define the types, methods, fields, properties, and events that are available for reflection.</span></span>

<span data-ttu-id="f7ca6-112">Başvuru bilgileri için aşağıdaki yapıdaki öğeleri seçin veya [çalışma zamanı yönerge öğelerini](runtime-directive-elements.md)görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-112">For reference information, choose elements from the following structure or see [Runtime Directive Elements](runtime-directive-elements.md).</span></span> <span data-ttu-id="f7ca6-113">Aşağıdaki hiyerarşide üç nokta özyinelemeli bir yapıyı işaret ediyor.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-113">In the following hierarchy, the ellipsis marks a recursive structure.</span></span> <span data-ttu-id="f7ca6-114">Köşeli ayraçlar içindeki bilgiler, bu öğenin isteğe bağlı veya gerekli olduğunu ve kullanılıp kullanılmadığını, kaç örneğe (bir veya daha fazla) izin verildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-114">The information in brackets indicates whether that element is optional or required, and if it is used, how many instances (one or many) are allowed.</span></span>

<span data-ttu-id="f7ca6-115">[Yönergeler](directives-element-net-native.md) [ [1:1] [] [](application-element-net-native.md) 0:1] [derlemesi](assembly-element-net-native.md) [0: d] [ad alanı](namespace-element-net-native.md) [0: a].</span><span class="sxs-lookup"><span data-stu-id="f7ca6-115">[Directives](directives-element-net-native.md) [1:1] [Application](application-element-net-native.md) [0:1] [Assembly](assembly-element-net-native.md) [0:M] [Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="f7ca6-116">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-116">.</span></span> <span data-ttu-id="f7ca6-117">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-117">.</span></span>
<span data-ttu-id="f7ca6-118">[Tür](type-element-net-native.md) [0: a].</span><span class="sxs-lookup"><span data-stu-id="f7ca6-118">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="f7ca6-119">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-119">.</span></span> <span data-ttu-id="f7ca6-120">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-120">.</span></span>
<span data-ttu-id="f7ca6-121">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulan genel tür) [0: a].</span><span class="sxs-lookup"><span data-stu-id="f7ca6-121">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="f7ca6-122">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-122">.</span></span> <span data-ttu-id="f7ca6-123">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-123">.</span></span>
<span data-ttu-id="f7ca6-124">[Ad alanı](namespace-element-net-native.md) [0: a] [Ad alanı](namespace-element-net-native.md) [0: a].</span><span class="sxs-lookup"><span data-stu-id="f7ca6-124">[Namespace](namespace-element-net-native.md) [0:M] [Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="f7ca6-125">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-125">.</span></span> <span data-ttu-id="f7ca6-126">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-126">.</span></span>
<span data-ttu-id="f7ca6-127">[Tür](type-element-net-native.md) [0: a].</span><span class="sxs-lookup"><span data-stu-id="f7ca6-127">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="f7ca6-128">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-128">.</span></span> <span data-ttu-id="f7ca6-129">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-129">.</span></span>
<span data-ttu-id="f7ca6-130">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulan genel tür) [0: a].</span><span class="sxs-lookup"><span data-stu-id="f7ca6-130">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="f7ca6-131">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-131">.</span></span> <span data-ttu-id="f7ca6-132">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-132">.</span></span>
<span data-ttu-id="f7ca6-133">[Tür](type-element-net-native.md) [0: a] Alt [türler](subtypes-element-net-native.md) (kapsayan türün alt sınıfları) [O:1] [Tür](type-element-net-native.md) [0: a].</span><span class="sxs-lookup"><span data-stu-id="f7ca6-133">[Type](type-element-net-native.md) [0:M] [Subtypes](subtypes-element-net-native.md) (subclasses of the containing type) [O:1] [Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="f7ca6-134">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-134">.</span></span> <span data-ttu-id="f7ca6-135">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-135">.</span></span>
<span data-ttu-id="f7ca6-136">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulan genel tür) [0: a].</span><span class="sxs-lookup"><span data-stu-id="f7ca6-136">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="f7ca6-137">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-137">.</span></span> <span data-ttu-id="f7ca6-138">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-138">.</span></span>
<span data-ttu-id="f7ca6-139">[Attributewith](attributeimplies-element-net-native.md) (içeren tür bir öznitelik) [O:1] [Genericparameter](genericparameter-element-net-native.md) [0: a] [Yöntemi](method-element-net-native.md) [0: a] [Parametre](parameter-element-net-native.md) [0: a] [Typeparameter](typeparameter-element-net-native.md) [0: a] [Genericparameter](genericparameter-element-net-native.md) [0: a] [Methodörneklemesi](methodinstantiation-element-net-native.md) (oluşturulmuş genel yöntem) [0: a] [Özelliği](property-element-net-native.md) [0: a] [Alan](field-element-net-native.md) [0: a] [Olay](event-element-net-native.md) [0: a] [Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulan genel tür) [0: a] [Tür](type-element-net-native.md) [0: a].</span><span class="sxs-lookup"><span data-stu-id="f7ca6-139">[AttributeImplies](attributeimplies-element-net-native.md) (containing type is an attribute) [O:1] [GenericParameter](genericparameter-element-net-native.md) [0:M] [Method](method-element-net-native.md) [0:M] [Parameter](parameter-element-net-native.md) [0:M] [TypeParameter](typeparameter-element-net-native.md) [0:M] [GenericParameter](genericparameter-element-net-native.md) [0:M] [MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M] [Property](property-element-net-native.md) [0:M] [Field](field-element-net-native.md) [0:M] [Event](event-element-net-native.md) [0:M] [TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] [Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="f7ca6-140">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-140">.</span></span> <span data-ttu-id="f7ca6-141">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-141">.</span></span>
<span data-ttu-id="f7ca6-142">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulan genel tür) [0: a].</span><span class="sxs-lookup"><span data-stu-id="f7ca6-142">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="f7ca6-143">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-143">.</span></span> <span data-ttu-id="f7ca6-144">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-144">.</span></span>
<span data-ttu-id="f7ca6-145">[Yöntemi](method-element-net-native.md) [0: a] [Parametre](parameter-element-net-native.md) [0: a] [Typeparameter](typeparameter-element-net-native.md) [0: a] [Genericparameter](genericparameter-element-net-native.md) [0: a] [Methodörneklemesi](methodinstantiation-element-net-native.md) (oluşturulmuş genel yöntem) [0: a] [Özelliği](property-element-net-native.md) [0: a] [Alan](field-element-net-native.md) [0: a] [Olay](event-element-net-native.md) [0: a] [Kitaplığı](library-element-net-native.md) [0: a] [Derleme](assembly-element-net-native.md) [0: a] [Ad alanı](namespace-element-net-native.md) [0: a].</span><span class="sxs-lookup"><span data-stu-id="f7ca6-145">[Method](method-element-net-native.md) [0:M] [Parameter](parameter-element-net-native.md) [0:M] [TypeParameter](typeparameter-element-net-native.md) [0:M] [GenericParameter](genericparameter-element-net-native.md) [0:M] [MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M] [Property](property-element-net-native.md) [0:M] [Field](field-element-net-native.md) [0:M] [Event](event-element-net-native.md) [0:M] [Library](library-element-net-native.md) [0:M] [Assembly](assembly-element-net-native.md) [0:M] [Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="f7ca6-146">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-146">.</span></span> <span data-ttu-id="f7ca6-147">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-147">.</span></span>
<span data-ttu-id="f7ca6-148">[Tür](type-element-net-native.md) [0: a].</span><span class="sxs-lookup"><span data-stu-id="f7ca6-148">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="f7ca6-149">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-149">.</span></span> <span data-ttu-id="f7ca6-150">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-150">.</span></span>
<span data-ttu-id="f7ca6-151">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulan genel tür) [0: a].</span><span class="sxs-lookup"><span data-stu-id="f7ca6-151">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="f7ca6-152">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-152">.</span></span> <span data-ttu-id="f7ca6-153">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-153">.</span></span>
<span data-ttu-id="f7ca6-154">[Ad alanı](namespace-element-net-native.md) [0: a] [Ad alanı](namespace-element-net-native.md) [0: a].</span><span class="sxs-lookup"><span data-stu-id="f7ca6-154">[Namespace](namespace-element-net-native.md) [0:M] [Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="f7ca6-155">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-155">.</span></span> <span data-ttu-id="f7ca6-156">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-156">.</span></span>
<span data-ttu-id="f7ca6-157">[Tür](type-element-net-native.md) [0: a].</span><span class="sxs-lookup"><span data-stu-id="f7ca6-157">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="f7ca6-158">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-158">.</span></span> <span data-ttu-id="f7ca6-159">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-159">.</span></span>
<span data-ttu-id="f7ca6-160">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulan genel tür) [0: a].</span><span class="sxs-lookup"><span data-stu-id="f7ca6-160">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="f7ca6-161">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-161">.</span></span> <span data-ttu-id="f7ca6-162">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-162">.</span></span>
<span data-ttu-id="f7ca6-163">[Tür](type-element-net-native.md) [0: a] Alt [türler](subtypes-element-net-native.md) (kapsayan türün alt sınıfları) [O:1] [Tür](type-element-net-native.md) [0: a].</span><span class="sxs-lookup"><span data-stu-id="f7ca6-163">[Type](type-element-net-native.md) [0:M] [Subtypes](subtypes-element-net-native.md) (subclasses of the containing type) [O:1] [Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="f7ca6-164">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-164">.</span></span> <span data-ttu-id="f7ca6-165">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-165">.</span></span>
<span data-ttu-id="f7ca6-166">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulan genel tür) [0: a].</span><span class="sxs-lookup"><span data-stu-id="f7ca6-166">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="f7ca6-167">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-167">.</span></span> <span data-ttu-id="f7ca6-168">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-168">.</span></span>
<span data-ttu-id="f7ca6-169">[Attributewith](attributeimplies-element-net-native.md) (içeren tür bir öznitelik) [O:1] [Genericparameter](genericparameter-element-net-native.md) [0: a] [Yöntemi](method-element-net-native.md) [0: a] [Methodörneklemesi](methodinstantiation-element-net-native.md) (oluşturulmuş genel yöntem) [0: a] [Özelliği](property-element-net-native.md) [0: a] [Alan](field-element-net-native.md) [0: a] [Olay](event-element-net-native.md) [0: a] [Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulan genel tür) [0: a] [Tür](type-element-net-native.md) [0: a].</span><span class="sxs-lookup"><span data-stu-id="f7ca6-169">[AttributeImplies](attributeimplies-element-net-native.md) (containing type is an attribute) [O:1] [GenericParameter](genericparameter-element-net-native.md) [0:M] [Method](method-element-net-native.md) [0:M] [MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M] [Property](property-element-net-native.md) [0:M] [Field](field-element-net-native.md) [0:M] [Event](event-element-net-native.md) [0:M] [TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] [Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="f7ca6-170">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-170">.</span></span> <span data-ttu-id="f7ca6-171">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-171">.</span></span>
<span data-ttu-id="f7ca6-172">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulan genel tür) [0: a].</span><span class="sxs-lookup"><span data-stu-id="f7ca6-172">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="f7ca6-173">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-173">.</span></span> <span data-ttu-id="f7ca6-174">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-174">.</span></span>
<span data-ttu-id="f7ca6-175">[Yöntemi](method-element-net-native.md) [0: a] [Methodörneklemesi](methodinstantiation-element-net-native.md) (oluşturulmuş genel yöntem) [0: a] [Özelliği](property-element-net-native.md) [0: a] [Alan](field-element-net-native.md) [0: a] [Olay](event-element-net-native.md) [0: a]</span><span class="sxs-lookup"><span data-stu-id="f7ca6-175">[Method](method-element-net-native.md) [0:M] [MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M] [Property](property-element-net-native.md) [0:M] [Field](field-element-net-native.md) [0:M] [Event](event-element-net-native.md) [0:M]</span></span>

<span data-ttu-id="f7ca6-176">[Uygulama](application-element-net-native.md) öğesinin hiç özniteliği olamaz veya [çalışma zamanı yönergesinde ve ilke bölümünde](#Directives)ele alınan ilke özniteliklerine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-176">The [Application](application-element-net-native.md) element can have no attributes, or it can have the policy attributes discussed in the [Runtime directive and policy section](#Directives).</span></span>

<span data-ttu-id="f7ca6-177">Bir [kitaplık](library-element-net-native.md) öğesi, dosya uzantısı olmadan bir `Name`kitaplığın veya derlemenin adını belirten tek bir özniteliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-177">A [Library](library-element-net-native.md) element has a single attribute, `Name`, that specifies the name of a library or assembly, without its file extension.</span></span> <span data-ttu-id="f7ca6-178">Örneğin, aşağıdaki [kitaplık](library-element-net-native.md) öğesi Extensions. dll adlı bir derleme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-178">For example, the following [Library](library-element-net-native.md) element applies to an assembly named Extensions.dll.</span></span>

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

## <a name="runtime-directives-and-policy"></a><span data-ttu-id="f7ca6-179">Çalışma zamanı yönergeleri ve ilkesi</span><span class="sxs-lookup"><span data-stu-id="f7ca6-179">Runtime directives and policy</span></span>

<span data-ttu-id="f7ca6-180">[Uygulama](application-element-net-native.md) öğesinin kendisi ve [kitaplık](library-element-net-native.md) ve [uygulama](application-element-net-native.md) öğeleri Express ilkesinin alt öğeleri; diğer bir deyişle, bir uygulamanın bir program öğesine yansıma uygulayabileceği şekilde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-180">The [Application](application-element-net-native.md) element itself and the child elements of the [Library](library-element-net-native.md) and [Application](application-element-net-native.md) elements express policy; that is, they define the way in which an app can apply reflection to a program element.</span></span> <span data-ttu-id="f7ca6-181">İlke türü, öğesinin bir özniteliği tarafından tanımlanır (örneğin, `Serialize`).</span><span class="sxs-lookup"><span data-stu-id="f7ca6-181">The policy type is defined by an attribute of the element (for example, `Serialize`).</span></span> <span data-ttu-id="f7ca6-182">İlke değeri özniteliğin değeri (örneğin, `Serialize="Required"`) tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-182">The policy value is defined by the attribute’s value (for example, `Serialize="Required"`).</span></span>

<span data-ttu-id="f7ca6-183">Bir öğenin özniteliği tarafından belirtilen herhangi bir ilke, bu ilke için bir değer belirtmeyen tüm alt öğeler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-183">Any policy specified by an attribute of an element applies to all child elements that don’t specify a value for that policy.</span></span> <span data-ttu-id="f7ca6-184">Örneğin, bir ilke bir [tür](type-element-net-native.md) öğesiyle belirtilmişse, bu ilke, bir ilkenin açıkça belirtilmediği tüm içerilen türler ve Üyeler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-184">For example, if a policy is specified by a [Type](type-element-net-native.md) element, that policy applies to all contained types and members for which a policy is not explicitly specified.</span></span>

<span data-ttu-id="f7ca6-185">[Uygulama](application-element-net-native.md), [derleme](assembly-element-net-native.md), [attributeby](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), alt [türler](subtypes-element-net-native.md)ve [tür](type-element-net-native.md) öğeleri tarafından ifade edilen ilke, ayrı Üyeler için ifade edilebilir ilkeden farklıdır ( [Yöntemi](method-element-net-native.md), [özelliği](property-element-net-native.md), [alanı](field-element-net-native.md)ve [olay](event-element-net-native.md) öğeleri).</span><span class="sxs-lookup"><span data-stu-id="f7ca6-185">The policy that can be expressed by the [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md), and [Type](type-element-net-native.md) elements differs from the policy that can be expressed for individual members (by the [Method](method-element-net-native.md), [Property](property-element-net-native.md), [Field](field-element-net-native.md), and [Event](event-element-net-native.md) elements).</span></span>

### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a><span data-ttu-id="f7ca6-186">Derlemeler, ad alanları ve türler için ilke belirtme</span><span class="sxs-lookup"><span data-stu-id="f7ca6-186">Specifying policy for assemblies, namespaces, and types</span></span>

<span data-ttu-id="f7ca6-187">[Uygulama](application-element-net-native.md), [derleme](assembly-element-net-native.md), [attributeme](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), alt [türleri](subtypes-element-net-native.md)ve [tür](type-element-net-native.md) öğeleri aşağıdaki ilke türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="f7ca6-187">The [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md), and [Type](type-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="f7ca6-188">`Activate`.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-188">`Activate`.</span></span> <span data-ttu-id="f7ca6-189">Örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-189">Controls runtime access to constructors, to enable activation of instances.</span></span>

- <span data-ttu-id="f7ca6-190">`Browse`.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-190">`Browse`.</span></span> <span data-ttu-id="f7ca6-191">Program öğeleri hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-191">Controls querying for information about program elements but does not enable any runtime access.</span></span>

- <span data-ttu-id="f7ca6-192">`Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-192">`Dynamic`.</span></span> <span data-ttu-id="f7ca6-193">Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-193">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>

- <span data-ttu-id="f7ca6-194">`Serialize`.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-194">`Serialize`.</span></span> <span data-ttu-id="f7ca6-195">Tür örneklerinin, Newtonsoft JSON serileştirici gibi üçüncü taraf kitaplıklara serileştirilmesi ve serileştirilmesi için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-195">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and serialized by third-party libraries such as the Newtonsoft JSON serializer.</span></span>

- <span data-ttu-id="f7ca6-196">`DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-196">`DataContractSerializer`.</span></span> <span data-ttu-id="f7ca6-197"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> Sınıfını kullanan serileştirme için ilkeyi denetler.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-197">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="f7ca6-198">`DataContractJsonSerializer`.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-198">`DataContractJsonSerializer`.</span></span> <span data-ttu-id="f7ca6-199"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> Sınıfını kullanan JSON serileştirme için ilkeyi denetler.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-199">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="f7ca6-200">`XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-200">`XmlSerializer`.</span></span> <span data-ttu-id="f7ca6-201"><xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> Sınıfını kullanan XML serileştirme ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-201">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="f7ca6-202">`MarshalObject`.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-202">`MarshalObject`.</span></span> <span data-ttu-id="f7ca6-203">WinRT ve COM 'a başvuru türlerini hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-203">Controls policy for marshaling reference types to WinRT and COM.</span></span>

- <span data-ttu-id="f7ca6-204">`MarshalDelegate`.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-204">`MarshalDelegate`.</span></span> <span data-ttu-id="f7ca6-205">Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-205">Controls policy for marshaling delegate types as function pointers to native code.</span></span>

- <span data-ttu-id="f7ca6-206">`MarshalStructure` .</span><span class="sxs-lookup"><span data-stu-id="f7ca6-206">`MarshalStructure` .</span></span> <span data-ttu-id="f7ca6-207">Yapıları yerel koda hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-207">Controls policy for marshaling structures to native code.</span></span>

<span data-ttu-id="f7ca6-208">Bu ilke türleriyle ilişkili ayarlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f7ca6-208">The settings associated with these policy types are:</span></span>

- <span data-ttu-id="f7ca6-209">`All`.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-209">`All`.</span></span> <span data-ttu-id="f7ca6-210">Araç zincirinin kaldıramayan tüm türler ve Üyeler için ilkeyi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-210">Enable the policy for all types and members that the tool chain does not remove.</span></span>

- <span data-ttu-id="f7ca6-211">`Auto`.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-211">`Auto`.</span></span> <span data-ttu-id="f7ca6-212">Varsayılan davranışı kullanın.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-212">Use the default behavior.</span></span> <span data-ttu-id="f7ca6-213">(İlke belirtilmemeksizin, ilke geçersiz `Auto` kılınmadıkça, örneğin bir üst öğe ile, bu ilkeyi ayarlamaya eşdeğerdir.)</span><span class="sxs-lookup"><span data-stu-id="f7ca6-213">(Not specifying a policy is equivalent to setting that policy to `Auto` unless that policy is overridden, for example by a parent element.)</span></span>

- <span data-ttu-id="f7ca6-214">`Excluded`.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-214">`Excluded`.</span></span> <span data-ttu-id="f7ca6-215">Program öğesi için ilkeyi devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-215">Disable the policy for the program element.</span></span>

- <span data-ttu-id="f7ca6-216">`Public`.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-216">`Public`.</span></span> <span data-ttu-id="f7ca6-217">Araç zinciri üyenin gereksiz olduğunu belirlerse ve bu nedenle uygulamayı kaldırmadığı müddetçe ortak türler veya Üyeler için ilkeyi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-217">Enable the policy for public types or members unless the tool chain determines that the member is unnecessary and therefore removes it.</span></span> <span data-ttu-id="f7ca6-218">(İkinci durumda, üyenin tutulduğundan ve yansıma özelliklerine `Required Public` sahip olduğundan emin olmak için kullanmanız gerekir.)</span><span class="sxs-lookup"><span data-stu-id="f7ca6-218">(In the latter case, you must use `Required Public` to ensure that the member is kept and has reflection capabilities.)</span></span>

- <span data-ttu-id="f7ca6-219">`PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-219">`PublicAndInternal`.</span></span> <span data-ttu-id="f7ca6-220">Araç zinciri onları kaldırmazsa ortak ve iç türler veya Üyeler için ilkeyi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-220">Enable the policy for public and internal types or members if the tool chain doesn't remove them.</span></span>

- <span data-ttu-id="f7ca6-221">`Required Public`.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-221">`Required Public`.</span></span> <span data-ttu-id="f7ca6-222">Ortak türleri ve üyeleri, kullanıldıkları ve kullanılmayacağı gibi tutmak ve ilke için etkinleştirmek üzere araç zinciri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-222">Require the tool chain to keep public types and members whether or not they are used, and enable the policy for them.</span></span>

- <span data-ttu-id="f7ca6-223">`Required PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-223">`Required PublicAndInternal`.</span></span> <span data-ttu-id="f7ca6-224">Araç zincirinin hem ortak hem de iç türleri ve üyeleri, kullanılmalarına bakılmaksızın ve bunları kendileri için etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-224">Require the tool chain to keep both public and internal types and members whether or not they are used, and enable the policy for them.</span></span>

- <span data-ttu-id="f7ca6-225">`Required All`.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-225">`Required All`.</span></span> <span data-ttu-id="f7ca6-226">Araç zincirinin tüm türleri ve üyeleri kullanıp kullanmadığını ve bunların kullanılmadığını ve ilke için etkin olmasını gerektir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-226">Require the tool chain to keep all types and members whether or not they are used, and enable the policy for them.</span></span>

<span data-ttu-id="f7ca6-227">Örneğin, aşağıdaki çalışma zamanı yönergeleri dosyası, veri sınıfları. dll dosyasındaki tüm türler ve Üyeler için ilkeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-227">For example, the following runtime directives file defines policy for all types and members in the assembly DataClasses.dll.</span></span> <span data-ttu-id="f7ca6-228">Tüm ortak özelliklerin serileştirilmesi için yansıma kullanımını, tüm türler ve tür üyeleri için gözatmayı etkinleştirmek, tüm türler için etkinleştirmeyi etkinleştirmek ( `Dynamic` özniteliği nedeniyle) ve tüm genel türler ve Üyeler için yansıma 'yi etkinleştirmek.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-228">It enables reflection for serialization of all public properties, enables browsing for all types and type members, enables activation for all types (because of the `Dynamic` attribute), and enables reflection for all public types and members.</span></span>

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

### <a name="specifying-policy-for-members"></a><span data-ttu-id="f7ca6-229">Üyeler için ilke belirtme</span><span class="sxs-lookup"><span data-stu-id="f7ca6-229">Specifying policy for members</span></span>

<span data-ttu-id="f7ca6-230">[Özellik](property-element-net-native.md) ve [alan](field-element-net-native.md) öğeleri aşağıdaki ilke türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="f7ca6-230">The [Property](property-element-net-native.md) and [Field](field-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="f7ca6-231">`Browse`-Bu üye hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-231">`Browse` - Controls querying for information about this member but does not enable any runtime access.</span></span>

- <span data-ttu-id="f7ca6-232">`Dynamic`-Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-232">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="f7ca6-233">Ayrıca, kapsayan tür hakkındaki bilgileri sorgulamayı denetler.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-233">Also controls querying for information about the containing type.</span></span>

- <span data-ttu-id="f7ca6-234">`Serialize`-Tür örneklerinin, Newtonsoft JSON serileştirici gibi kitaplıklar tarafından serileştirilmesi ve seri durumdan çıkarılmakta olması için üyeye çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-234">`Serialize` - Controls runtime access to the member to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span> <span data-ttu-id="f7ca6-235">Bu ilke oluşturucular, alanlar ve özelliklere uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-235">This policy can be applied to constructors, fields, and properties.</span></span>

<span data-ttu-id="f7ca6-236">[Yöntemi](method-element-net-native.md) ve [olay](event-element-net-native.md) öğeleri aşağıdaki ilke türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="f7ca6-236">The [Method](method-element-net-native.md) and [Event](event-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="f7ca6-237">`Browse`-Bu üye hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-237">`Browse` - Controls querying for information about this member but doesn’t enable any runtime access.</span></span>

- <span data-ttu-id="f7ca6-238">`Dynamic`-Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-238">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="f7ca6-239">Ayrıca, kapsayan tür hakkındaki bilgileri sorgulamayı denetler.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-239">Also controls querying for information about the containing type.</span></span>

 <span data-ttu-id="f7ca6-240">Bu ilke türleriyle ilişkili ayarlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f7ca6-240">The settings associated with these policy types are:</span></span>

- <span data-ttu-id="f7ca6-241">`Auto`-Varsayılan davranışı kullanın.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-241">`Auto` - Use the default behavior.</span></span> <span data-ttu-id="f7ca6-242">(Bir ilke belirtmeksizin, bir öğe geçersiz `Auto` kılınmadığı takdirde bu ilkeyi ayarlamaya eşdeğerdir.)</span><span class="sxs-lookup"><span data-stu-id="f7ca6-242">(Not specifying a policy is equivalent to setting that policy to `Auto` unless something overrides it.)</span></span>

- <span data-ttu-id="f7ca6-243">`Excluded`-Üyenin meta verilerini hiçbir şekilde eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-243">`Excluded` - Never include metadata for the member.</span></span>

- <span data-ttu-id="f7ca6-244">`Included`-Üst tür çıktıda varsa ilkeyi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-244">`Included` - Enable the policy if the parent type is present in the output.</span></span>

- <span data-ttu-id="f7ca6-245">`Required`-Araç zincirinin, kullanılmamış gibi görünse bile bu üyeyi tutması gerekir ve ilkeyi etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-245">`Required` - Require the tool chain to keep this member even if appears to be unused, and enable policy for it.</span></span>

## <a name="runtime-directives-file-semantics"></a><span data-ttu-id="f7ca6-246">Çalışma zamanı yönergeleri dosya semantiği</span><span class="sxs-lookup"><span data-stu-id="f7ca6-246">Runtime directives file semantics</span></span>

<span data-ttu-id="f7ca6-247">İlke, hem daha yüksek hem de alt düzey öğeler için eşzamanlı olarak tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-247">Policy can be defined simultaneously for both higher-level and lower-level elements.</span></span> <span data-ttu-id="f7ca6-248">Örneğin, ilke bir derleme için ve bu derlemede yer alan bazı türler için tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-248">For example, policy can be defined for an assembly, and for some of the types contained in that assembly.</span></span> <span data-ttu-id="f7ca6-249">Belirli bir alt düzey öğe gösterilmediğinden, üst öğesinin ilkesini devralır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-249">If a particular lower-level element is not represented, it inherits the policy of its parent.</span></span> <span data-ttu-id="f7ca6-250">Örneğin, bir `Assembly` öğe mevcutsa ancak `Type` öğeler yoksa, `Assembly` öğesinde belirtilen ilke derlemedeki her tür için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-250">For example, if an `Assembly` element is present but `Type` elements are not, the policy specified in the `Assembly` element applies to each type in the assembly.</span></span> <span data-ttu-id="f7ca6-251">Aynı program öğesine aynı zamanda birden çok öğe ilke uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-251">Multiple elements can also apply policy to the same program element.</span></span> <span data-ttu-id="f7ca6-252">Örneğin, ayrı [derleme](assembly-element-net-native.md) öğeleri aynı derleme için aynı ilke öğesini farklı şekilde tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-252">For example, separate [Assembly](assembly-element-net-native.md) elements might define the same policy element for the same assembly differently.</span></span> <span data-ttu-id="f7ca6-253">Aşağıdaki bölümlerde, belirli bir türün ilkesinin bu durumlarda nasıl çözümlendiğini açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-253">The following sections explain how the policy for a particular type is resolved in those cases.</span></span>

<span data-ttu-id="f7ca6-254">Genel bir türün veya yöntemin [tür](type-element-net-native.md) veya [Yöntem](method-element-net-native.md) öğesi, kendi ilkesi olmayan tüm örneklemelerde ilkesini uygular.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-254">A [Type](type-element-net-native.md) or [Method](method-element-net-native.md) element of a generic type or method applies its policy to all instantiations that do not have their own policy.</span></span> <span data-ttu-id="f7ca6-255">Örneğin, `Type` `List<Int32>`ilkesini belirten bir öğe, belirli bir oluşturulan genel tür için geçersiz kılınmadığı sürece (örneğin, bir `TypeInstantiation` öğesi tarafından), bu genel türün tüm oluşturulan örneklerine uygulanır.<xref:System.Collections.Generic.List%601></span><span class="sxs-lookup"><span data-stu-id="f7ca6-255">For example, a `Type` element that specifies policy for <xref:System.Collections.Generic.List%601> applies to all constructed instances of that generic type, unless it's overridden for a particular constructed generic type (such as a `List<Int32>`) by a `TypeInstantiation` element.</span></span> <span data-ttu-id="f7ca6-256">Aksi takdirde, öğeleri adlı program öğesi için ilkeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-256">Otherwise, elements define policy for the program element named.</span></span>

<span data-ttu-id="f7ca6-257">Bir öğe belirsiz olduğunda, motor eşleşme arar ve tam eşleşme bulursa onu kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-257">When an element is ambiguous, the engine looks for matches, and if it finds an exact match, it will use it.</span></span> <span data-ttu-id="f7ca6-258">Birden çok eşleşme bulunursa bir uyarı veya hata olur.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-258">If it finds multiple matches, there will be a warning or error.</span></span>

### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a><span data-ttu-id="f7ca6-259">İki yönergeler aynı program öğesine ilke uygualıyorsa</span><span class="sxs-lookup"><span data-stu-id="f7ca6-259">If two directives apply policy to the same program element</span></span>

<span data-ttu-id="f7ca6-260">Farklı çalışma zamanı yönergeleri dosyalarındaki iki öğe aynı program öğesi (bir derleme veya tür gibi) için aynı ilke türünü farklı değerlere ayarlamaya çalışıyorsa, çakışma aşağıdaki gibi çözümlenir:</span><span class="sxs-lookup"><span data-stu-id="f7ca6-260">If two elements in different runtime directives files try to set the same policy type for the same program element (such as an assembly or type) to different values, the conflict is resolved as follows:</span></span>

1. <span data-ttu-id="f7ca6-261">`Excluded` Öğe varsa, önceliğe sahip olur.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-261">If the `Excluded` element is present, it has precedence.</span></span>

2. <span data-ttu-id="f7ca6-262">`Required`, öğesinden önceliklidir `Required`.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-262">`Required` has precedence over not `Required`.</span></span>

3. <span data-ttu-id="f7ca6-263">`All`önceliğe sahip `Public`olan `PublicAndInternal`, önceliği olan.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-263">`All` has precedence over `PublicAndInternal`, which has precedence over `Public`.</span></span>

4. <span data-ttu-id="f7ca6-264">Herhangi bir açık ayar önceliklidir `Auto`.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-264">Any explicit setting has precedence over `Auto`.</span></span>

<span data-ttu-id="f7ca6-265">Örneğin, tek bir proje aşağıdaki iki çalışma zamanı yönergeleri dosyasını içeriyorsa, DataClasses. dll serileştirme ilkesi hem hem de `Required Public` `All`olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-265">For example, if a single project includes the following two runtime directives files, the serialization policy for DataClasses.dll is set to both `Required Public` and `All`.</span></span> <span data-ttu-id="f7ca6-266">Bu durumda, serileştirme ilkesi olarak `Required All`çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-266">In this case, the serialization policy would be resolved as `Required All`.</span></span>

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

<span data-ttu-id="f7ca6-267">Ancak, tek bir çalışma zamanı yönergeleri dosyasında iki yönergesi aynı program öğesi için aynı ilke türünü ayarlamaya çalışırsanız, XML şeması tanım aracında bir hata iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-267">However, if two directives in a single runtime directives file try to set the same policy type for the same program element, the XML Scheme Definition tool displays an error message.</span></span>

### <a name="if-child-and-parent-elements-apply-the-same-policy-type"></a><span data-ttu-id="f7ca6-268">Alt ve üst öğeler aynı ilke türünü uygualıyorsa</span><span class="sxs-lookup"><span data-stu-id="f7ca6-268">If child and parent elements apply the same policy type</span></span>

<span data-ttu-id="f7ca6-269">Alt öğeler, `Excluded` ayarı da dahil olmak üzere üst öğelerini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-269">Child elements override their parent elements, including the `Excluded` setting.</span></span> <span data-ttu-id="f7ca6-270">Geçersiz kılma, belirtmek `Auto`istediğiniz ana nedendir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-270">Overriding is the main reason you would want to specify `Auto`.</span></span>

<span data-ttu-id="f7ca6-271">Aşağıdaki örnekte `DataClasses` , içinde `DataClasses.ViewModels` `Required Public`olmayan her şey için serileştirme ilkesi ayarı `DataClasses.ViewModels` , ve her ikisinde `DataClasses` de olan `All`her şey olacaktır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-271">In the following example, the serialization policy setting for everything in `DataClasses` that’s not in `DataClasses.ViewModels` would be `Required Public`, and everything that's in both `DataClasses` and `DataClasses.ViewModels` would be `All`.</span></span>

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

### <a name="if-open-generics-and-instantiated-elements-apply-the-same-policy-type"></a><span data-ttu-id="f7ca6-272">Açık genel türler ve örneklenmiş öğeler aynı ilke türünü uygular</span><span class="sxs-lookup"><span data-stu-id="f7ca6-272">If open generics and instantiated elements apply the same policy type</span></span>

<span data-ttu-id="f7ca6-273">Aşağıdaki `Dictionary<int,int>` örnekte, `Browse` ilke yalnızca altyapının `Browse` ilkeyi vermesi için başka bir nedeni varsa (Aksi takdirde varsayılan davranış olur), öğesinin <xref:System.Collections.Generic.Dictionary%602> her bir örneği üyelerine gözatılabilir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-273">In the following example, `Dictionary<int,int>` is assigned the `Browse` policy only if the engine has another reason to give it the `Browse` policy (which would otherwise be the default behavior); every other instantiation of <xref:System.Collections.Generic.Dictionary%602> will have all of its members browsable.</span></span>

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

### <a name="how-policy-is-inferred"></a><span data-ttu-id="f7ca6-274">İlke nasıl algılanır</span><span class="sxs-lookup"><span data-stu-id="f7ca6-274">How policy is inferred</span></span>

<span data-ttu-id="f7ca6-275">Her ilke türünün, bu ilke türü varlığının diğer yapıları nasıl etkilediğini tespit eden farklı kurallar kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-275">Each policy type has a different set of rules that determine how the presence of that policy type affects other constructs.</span></span>

#### <a name="the-effect-of-browse-policy"></a><span data-ttu-id="f7ca6-276">Tarayıcı ilkesinin etkisi</span><span class="sxs-lookup"><span data-stu-id="f7ca6-276">The effect of Browse policy</span></span>

<span data-ttu-id="f7ca6-277">`Browse` İlkeyi bir türe uygulamak aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="f7ca6-277">Applying the `Browse` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="f7ca6-278">Türün temel türü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-278">The base type of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f7ca6-279">Tür bir genel ise, türün örneklenmemiş sürümü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-279">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f7ca6-280">Tür bir `Invoke` temsilciyise, türdeki yöntem `Dynamic` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-280">If the type is a delegate, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="f7ca6-281">Türün her arabirimi `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-281">Each interface of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f7ca6-282">Türe uygulanan her bir özniteliğin türü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-282">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f7ca6-283">Tür geneldir ise, her kısıtlama türü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-283">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f7ca6-284">Tür geneldir ise, türün örneklendiği türler `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-284">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="f7ca6-285">`Browse` İlkeyi bir yönteme uygulamak aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="f7ca6-285">Applying the `Browse` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="f7ca6-286">Yöntemin her bir parametre türü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-286">Each parameter type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f7ca6-287">Metodun dönüş türü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-287">The return type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f7ca6-288">Yöntemin kapsayan türü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-288">The containing type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f7ca6-289">Yöntem, örneklenmiş genel bir yöntem ise, örneklenmiş genel yöntem `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-289">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f7ca6-290">Yöntemine uygulanan her bir özniteliğin türü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-290">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f7ca6-291">Yöntem geneldir ise, her kısıtlama türü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-291">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f7ca6-292">Yöntem genel ise, yöntemin örneklendiği türler `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-292">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="f7ca6-293">`Browse` İlkeyi bir alana uygulamak aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="f7ca6-293">Applying the `Browse` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="f7ca6-294">Alana uygulanan her bir özniteliğin türü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-294">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f7ca6-295">Alanın türü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-295">The type of the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f7ca6-296">Alanın ait olduğu tür `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-296">The type to which the field belongs is marked with the `Browse` policy.</span></span>

#### <a name="the-effect-of-dynamic-policy"></a><span data-ttu-id="f7ca6-297">Dinamik ilkenin etkisi</span><span class="sxs-lookup"><span data-stu-id="f7ca6-297">The effect of Dynamic policy</span></span>

<span data-ttu-id="f7ca6-298">`Dynamic` İlkeyi bir türe uygulamak aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="f7ca6-298">Applying the `Dynamic` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="f7ca6-299">Türün temel türü `Dynamic` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-299">The base type of the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="f7ca6-300">Tür bir genel ise, türün örneklenmemiş sürümü `Dynamic` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-300">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="f7ca6-301">Tür bir temsilci türü ise, `Invoke` türdeki yöntem `Dynamic` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-301">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="f7ca6-302">Türün her arabirimi `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-302">Each interface of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f7ca6-303">Türe uygulanan her bir özniteliğin türü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-303">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f7ca6-304">Tür geneldir ise, her kısıtlama türü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-304">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f7ca6-305">Tür geneldir ise, türün örneklendiği türler `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-305">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="f7ca6-306">`Dynamic` İlkeyi bir yönteme uygulamak aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="f7ca6-306">Applying the `Dynamic` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="f7ca6-307">Yöntemin her bir parametre türü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-307">Each parameter type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f7ca6-308">Metodun dönüş türü `Dynamic` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-308">The return type of the method is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="f7ca6-309">Yöntemin kapsayan türü `Dynamic` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-309">The containing type of the method is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="f7ca6-310">Yöntem, örneklenmiş genel bir yöntem ise, örneklenmiş genel yöntem `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-310">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f7ca6-311">Yöntemine uygulanan her bir özniteliğin türü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-311">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f7ca6-312">Yöntem geneldir ise, her kısıtlama türü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-312">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f7ca6-313">Yöntem genel ise, yöntemin örneklendiği türler `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-313">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f7ca6-314">Yöntemi tarafından `MethodInfo.Invoke`çağrılabilir ve temsilci oluşturma tarafından <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>mümkün hale gelir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-314">The method can be invoked by `MethodInfo.Invoke`, and delegate creation becomes possible by <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="f7ca6-315">`Dynamic` İlkeyi bir alana uygulamak aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="f7ca6-315">Applying the `Dynamic` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="f7ca6-316">Alana uygulanan her bir özniteliğin türü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-316">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f7ca6-317">Alanın türü `Dynamic` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-317">The type of the field is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="f7ca6-318">Alanın ait olduğu tür `Dynamic` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-318">The type to which the field belongs is marked with the `Dynamic` policy.</span></span>

#### <a name="the-effect-of-activation-policy"></a><span data-ttu-id="f7ca6-319">Etkinleştirme ilkesinin etkisi</span><span class="sxs-lookup"><span data-stu-id="f7ca6-319">The effect of Activation policy</span></span>

<span data-ttu-id="f7ca6-320">Etkinleştirme ilkesini bir türe uygulamak aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="f7ca6-320">Applying the Activation policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="f7ca6-321">Tür bir genel ise, türün örneklenmemiş sürümü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-321">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f7ca6-322">Tür bir temsilci türü ise, `Invoke` türdeki yöntem `Dynamic` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-322">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="f7ca6-323">Türün oluşturucuları `Activation` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-323">Constructors of the type are marked with the `Activation` policy.</span></span>

<span data-ttu-id="f7ca6-324">`Activation` İlkeyi bir yönteme uygulamak aşağıdaki ilke değişikliğini içerir:</span><span class="sxs-lookup"><span data-stu-id="f7ca6-324">Applying the `Activation` policy to a method involves the following policy change:</span></span>

- <span data-ttu-id="f7ca6-325">Oluşturucu <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> ve<xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> yöntemleri tarafından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-325">The constructor can be invoked by the <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> and <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="f7ca6-326">Yöntemler için, `Activation` ilke yalnızca oluşturucuları etkiler.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-326">For methods, the `Activation` policy affects constructors only.</span></span>

<span data-ttu-id="f7ca6-327">`Activation` İlkeyi bir alana uygulamak hiçbir etkiye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-327">Applying the `Activation` policy to a field has no effect.</span></span>

#### <a name="the-effect-of-serialize-policy"></a><span data-ttu-id="f7ca6-328">Seri hale getirme ilkesinin etkisi</span><span class="sxs-lookup"><span data-stu-id="f7ca6-328">The effect of Serialize policy</span></span>

<span data-ttu-id="f7ca6-329">`Serialize` İlke, yaygın yansıma tabanlı serileştiricilerin kullanımını sunar.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-329">The `Serialize` policy enables the use of common reflection-based serializers.</span></span> <span data-ttu-id="f7ca6-330">Ancak, Microsoft dışı serileştiricilerin tam yansıma erişimi desenleri Microsoft tarafından bilinmediğinden, bu ilke tamamen etkili olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-330">However, because the exact reflection access patterns of non-Microsoft serializers are not known to Microsoft, this policy may not be entirely effective.</span></span>

<span data-ttu-id="f7ca6-331">`Serialize` İlkeyi bir türe uygulamak aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="f7ca6-331">Applying the `Serialize` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="f7ca6-332">Türün temel türü `Serialize` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-332">The base type of the type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="f7ca6-333">Tür bir genel ise, türün örneklenmemiş sürümü `Browse` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-333">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="f7ca6-334">Tür bir temsilci türü ise, `Invoke` türdeki yöntem `Dynamic` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-334">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="f7ca6-335">Tür bir sabit listesi ise, bir tür dizisi `Serialize` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-335">If the type is an enumeration, an array of the type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="f7ca6-336">Türü uygularsa <xref:System.Collections.Generic.IEnumerable%601> `T` `Serialize` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-336">If the type implements <xref:System.Collections.Generic.IEnumerable%601>, `T` is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="f7ca6-337"><xref:System.Collections.Generic.IEnumerable%601>Tür ,<xref:System.Collections.Generic.IReadOnlyList%601> ,,<xref:System.Collections.Generic.List%601> , veya olarak ilkeile`Serialize` işaretlenmişse., ancak arabirim türünün hiçbir üyesi `T[]` <xref:System.Collections.Generic.IList%601> <xref:System.Collections.Generic.ICollection%601> <xref:System.Collections.Generic.IReadOnlyCollection%601> `Serialize`ilke.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-337">If the type is <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>, or <xref:System.Collections.Generic.IReadOnlyList%601>, then `T[]` and <xref:System.Collections.Generic.List%601> marked with the `Serialize` policy., but no members of the interface type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="f7ca6-338">Tür ise <xref:System.Collections.Generic.List%601>, bu tür hiçbir üye `Serialize` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-338">If the type is <xref:System.Collections.Generic.List%601>, no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="f7ca6-339">Tür ise <xref:System.Collections.Generic.IDictionary%602> <xref:System.Collections.Generic.Dictionary%602> ilkeyle işaretlenir`Serialize` .</span><span class="sxs-lookup"><span data-stu-id="f7ca6-339">If the type is <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> is marked with the `Serialize` policy.</span></span> <span data-ttu-id="f7ca6-340">Ancak, türdeki hiçbir üye `Serialize` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-340">but no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="f7ca6-341">Tür ise <xref:System.Collections.Generic.Dictionary%602>, bu tür hiçbir üye `Serialize` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-341">If the type is <xref:System.Collections.Generic.Dictionary%602>, no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="f7ca6-342">Türü <xref:System.Collections.Generic.IDictionary%602> `TKey` uygularsa ve`TValue`ilkeyleişaretlenir. `Serialize`</span><span class="sxs-lookup"><span data-stu-id="f7ca6-342">If the type implements <xref:System.Collections.Generic.IDictionary%602>, `TKey` and `TValue` are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="f7ca6-343">Her bir Oluşturucu, her özellik erişimcisi ve her bir alan `Serialize` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-343">Each constructor, each property accessor, and each field is marked with the `Serialize` policy.</span></span>

<span data-ttu-id="f7ca6-344">`Serialize` İlkeyi bir yönteme uygulamak aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="f7ca6-344">Applying the `Serialize` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="f7ca6-345">Kapsayan tür `Serialize` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-345">The containing type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="f7ca6-346">Metodun dönüş türü `Serialize` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-346">The return type of the method is marked with the `Serialize` policy.</span></span>

<span data-ttu-id="f7ca6-347">`Serialize` İlkeyi bir alana uygulamak aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="f7ca6-347">Applying the `Serialize` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="f7ca6-348">Kapsayan tür `Serialize` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-348">The containing type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="f7ca6-349">Alanın türü `Serialize` ilkeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-349">The type of the field is marked with the `Serialize` policy.</span></span>

#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserializer-policies"></a><span data-ttu-id="f7ca6-350">XmlSerializer, DataContractSerializer ve DataContractJsonSerializer ilkelerinin etkisi</span><span class="sxs-lookup"><span data-stu-id="f7ca6-350">The effect of XmlSerializer, DataContractSerializer, and DataContractJsonSerializer policies</span></span>

<span data-ttu-id="f7ca6-351">Yansıma tabanlı serileştiriciler <xref:System.Xml.Serialization.XmlSerializer> <xref:System.Runtime.Serialization.DataContractSerializer>için tasarlanan <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ilkenin aksine,, ve ilkeleri .NET Native araç zinciri tarafından bilinen bir seri hale getiriciler kümesini etkinleştirmek için kullanılır. `Serialize`</span><span class="sxs-lookup"><span data-stu-id="f7ca6-351">Unlike the `Serialize` policy, which is intended for reflection-based serializers, the <xref:System.Xml.Serialization.XmlSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer>, and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> policies are used to enable a set of serializers that are known to the .NET Native tool chain.</span></span> <span data-ttu-id="f7ca6-352">Bu serileştiriciler yansıma kullanılarak uygulanmaz, ancak çalışma zamanında seri hale getirilebildiğiniz türler kümesi, yansıma \ olan türler gibi benzer şekilde belirlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-352">These serializers are not implemented by using reflection, but the set of types that can be serialized at run time is determined in a similar manner as types that are reflectable.</span></span>

<span data-ttu-id="f7ca6-353">Bu ilkelerin bir türe uygulanması, türün eşleşen serileştirici ile serileştirilmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-353">Applying one of these policies to a type enables the type to be serialized with the matching serializer.</span></span> <span data-ttu-id="f7ca6-354">Ayrıca, serileştirme altyapısının serileştirilmesi gereken şekilde statik olarak belirleyebilmesi için herhangi bir tür de serileştirilebilir olur.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-354">Also, any types that the serialization engine can statically determine as needing serialization will also be serializable.</span></span>

<span data-ttu-id="f7ca6-355">Bu ilkelerin Yöntemler veya alanlar üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-355">These policies have no effect on methods or fields.</span></span>

<span data-ttu-id="f7ca6-356">Daha fazla bilgi için [Windows mağazası uygulamanızı .NET Native geçirme](migrating-your-windows-store-app-to-net-native.md)konusunun "Serileştiricilerle ilgili farklılıklar" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-356">For more information, see the "Differences in Serializers" section in [Migrating Your Windows Store App to .NET Native](migrating-your-windows-store-app-to-net-native.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f7ca6-357">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7ca6-357">See also</span></span>

- [<span data-ttu-id="f7ca6-358">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="f7ca6-358">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="f7ca6-359">Yansıma ve .NET Native</span><span class="sxs-lookup"><span data-stu-id="f7ca6-359">Reflection and .NET Native</span></span>](reflection-and-net-native.md)
