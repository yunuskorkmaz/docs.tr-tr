---
title: Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu
ms.date: 03/30/2017
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
ms.openlocfilehash: f4c51dc269775d14d395cb464b3787cc987e086d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128137"
---
# <a name="runtime-directives-rdxml-configuration-file-reference"></a><span data-ttu-id="ae8fc-102">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="ae8fc-102">Runtime Directives (rd.xml) Configuration File Reference</span></span>

<span data-ttu-id="ae8fc-103">Çalışma zamanı yönergeleri (. RD. xml) dosyası, belirtilen program öğelerinin yansıma için kullanılabilir olup olmadığını belirten bir XML yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-103">A runtime directives (.rd.xml) file is an XML configuration file that specifies whether designated program elements are available for reflection.</span></span> <span data-ttu-id="ae8fc-104">Çalışma zamanı yönergeleri dosyasına bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ae8fc-104">Here’s an example of a runtime directives file:</span></span>

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

## <a name="the-structure-of-a-runtime-directives-file"></a><span data-ttu-id="ae8fc-105">Çalışma zamanı yönergeleri dosyasının yapısı</span><span class="sxs-lookup"><span data-stu-id="ae8fc-105">The structure of a runtime directives file</span></span>

<span data-ttu-id="ae8fc-106">Çalışma zamanı yönergeleri dosyası `http://schemas.microsoft.com/netfx/2013/01/metadata` ad alanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-106">The runtime directives file uses the `http://schemas.microsoft.com/netfx/2013/01/metadata` namespace.</span></span>

<span data-ttu-id="ae8fc-107">Kök öğesi, [yönergeleri](directives-element-net-native.md) öğesidir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-107">The root element is the [Directives](directives-element-net-native.md) element.</span></span> <span data-ttu-id="ae8fc-108">Aşağıdaki yapıda gösterildiği gibi sıfır veya daha fazla [kitaplık](library-element-net-native.md) öğesi ve sıfır veya bir [uygulama](application-element-net-native.md) öğesi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-108">It can contain zero or more [Library](library-element-net-native.md) elements, and zero or one [Application](application-element-net-native.md) element, as shown in the following structure.</span></span> <span data-ttu-id="ae8fc-109">[Uygulama](application-element-net-native.md) öğesinin öznitelikleri, uygulama genelinde çalışma zamanı yansıma ilkesi tanımlayabilir veya alt öğeler için bir kapsayıcı olarak görev yapabilir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-109">The attributes of the [Application](application-element-net-native.md) element can define application-wide runtime reflection policy, or it can serve as a container for child elements.</span></span> <span data-ttu-id="ae8fc-110">Öte yandan [kitaplık](library-element-net-native.md) öğesi yalnızca bir kapsayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-110">The [Library](library-element-net-native.md) element, on the other hand, is simply a container.</span></span> <span data-ttu-id="ae8fc-111">[Uygulama](application-element-net-native.md) ve [kitaplık](library-element-net-native.md) öğelerinin alt öğeleri, yansıma için kullanılabilen türleri, yöntemleri, alanları, özellikleri ve olayları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-111">The children of the [Application](application-element-net-native.md) and [Library](library-element-net-native.md) elements define the types, methods, fields, properties, and events that are available for reflection.</span></span>

<span data-ttu-id="ae8fc-112">Başvuru bilgileri için aşağıdaki yapıdaki öğeleri seçin veya [çalışma zamanı yönerge öğelerini](runtime-directive-elements.md)görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-112">For reference information, choose elements from the following structure or see [Runtime Directive Elements](runtime-directive-elements.md).</span></span> <span data-ttu-id="ae8fc-113">Aşağıdaki hiyerarşide üç nokta özyinelemeli bir yapıyı işaret ediyor.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-113">In the following hierarchy, the ellipsis marks a recursive structure.</span></span> <span data-ttu-id="ae8fc-114">Köşeli ayraçlar içindeki bilgiler, bu öğenin isteğe bağlı veya gerekli olduğunu ve kullanılıp kullanılmadığını, kaç örneğe (bir veya daha fazla) izin verildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-114">The information in brackets indicates whether that element is optional or required, and if it is used, how many instances (one or many) are allowed.</span></span>

<span data-ttu-id="ae8fc-115">[Yönergeler](directives-element-net-native.md) [1:1] [uygulama](application-element-net-native.md) [0:1] [derleme](assembly-element-net-native.md) [0: d] [ad alanı](namespace-element-net-native.md) [0: d].</span><span class="sxs-lookup"><span data-stu-id="ae8fc-115">[Directives](directives-element-net-native.md) [1:1] [Application](application-element-net-native.md) [0:1] [Assembly](assembly-element-net-native.md) [0:M] [Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="ae8fc-116">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-116">.</span></span> <span data-ttu-id="ae8fc-117">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-117">.</span></span>
<span data-ttu-id="ae8fc-118">[0: d] [yazın](type-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="ae8fc-118">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="ae8fc-119">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-119">.</span></span> <span data-ttu-id="ae8fc-120">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-120">.</span></span>
<span data-ttu-id="ae8fc-121">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: a].</span><span class="sxs-lookup"><span data-stu-id="ae8fc-121">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="ae8fc-122">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-122">.</span></span> <span data-ttu-id="ae8fc-123">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-123">.</span></span>
<span data-ttu-id="ae8fc-124">[Ad alanı](namespace-element-net-native.md) [0: d] [ad alanı](namespace-element-net-native.md) [0: d].</span><span class="sxs-lookup"><span data-stu-id="ae8fc-124">[Namespace](namespace-element-net-native.md) [0:M] [Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="ae8fc-125">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-125">.</span></span> <span data-ttu-id="ae8fc-126">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-126">.</span></span>
<span data-ttu-id="ae8fc-127">[0: d] [yazın](type-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="ae8fc-127">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="ae8fc-128">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-128">.</span></span> <span data-ttu-id="ae8fc-129">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-129">.</span></span>
<span data-ttu-id="ae8fc-130">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: a].</span><span class="sxs-lookup"><span data-stu-id="ae8fc-130">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="ae8fc-131">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-131">.</span></span> <span data-ttu-id="ae8fc-132">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-132">.</span></span>
<span data-ttu-id="ae8fc-133">[[0](type-element-net-native.md) : d] alt [türleri](subtypes-element-net-native.md) (kapsayan tür alt sınıfları) [o:1] [türü](type-element-net-native.md) [0: ı].</span><span class="sxs-lookup"><span data-stu-id="ae8fc-133">[Type](type-element-net-native.md) [0:M] [Subtypes](subtypes-element-net-native.md) (subclasses of the containing type) [O:1] [Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="ae8fc-134">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-134">.</span></span> <span data-ttu-id="ae8fc-135">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-135">.</span></span>
<span data-ttu-id="ae8fc-136">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: a].</span><span class="sxs-lookup"><span data-stu-id="ae8fc-136">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="ae8fc-137">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-137">.</span></span> <span data-ttu-id="ae8fc-138">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-138">.</span></span>
<span data-ttu-id="ae8fc-139">[Attributemethod](attributeimplies-element-net-native.md) (tür bir öznitelik) [O:1] [genericparameter](genericparameter-element-net-native.md) [0: d] [metot](method-element-net-native.md) [0: ı] [parametre](parameter-element-net-native.md) [0: d] [typeparameter](typeparameter-element-net-native.md) [0: ı] [genericparameter](genericparameter-element-net-native.md) [0: d] [methodörneklemesi](methodinstantiation-element-net-native.md) ( oluşturulan genel yöntem) [0: d] [özellik](property-element-net-native.md) [0: d] [alan](field-element-net-native.md) [0: d] [olay](event-element-net-native.md) [0: d] [typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: d] [tür](type-element-net-native.md) [0: d].</span><span class="sxs-lookup"><span data-stu-id="ae8fc-139">[AttributeImplies](attributeimplies-element-net-native.md) (containing type is an attribute) [O:1] [GenericParameter](genericparameter-element-net-native.md) [0:M] [Method](method-element-net-native.md) [0:M] [Parameter](parameter-element-net-native.md) [0:M] [TypeParameter](typeparameter-element-net-native.md) [0:M] [GenericParameter](genericparameter-element-net-native.md) [0:M] [MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M] [Property](property-element-net-native.md) [0:M] [Field](field-element-net-native.md) [0:M] [Event](event-element-net-native.md) [0:M] [TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] [Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="ae8fc-140">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-140">.</span></span> <span data-ttu-id="ae8fc-141">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-141">.</span></span>
<span data-ttu-id="ae8fc-142">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: a].</span><span class="sxs-lookup"><span data-stu-id="ae8fc-142">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="ae8fc-143">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-143">.</span></span> <span data-ttu-id="ae8fc-144">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-144">.</span></span>
<span data-ttu-id="ae8fc-145">[Yöntem](method-element-net-native.md) [0: d] [parametre](parameter-element-net-native.md) [0: d] [typeparameter](typeparameter-element-net-native.md) [0: d] [Genericparameter](genericparameter-element-net-native.md) [0: d] [Methodörneklemesi](methodinstantiation-element-net-native.md) (oluşturulmuş genel yöntem) [0: d] [özellik](property-element-net-native.md) [0: d] [alan](field-element-net-native.md) [0: d] [olay](event-element-net-native.md) [0: d] [ Kitaplık](library-element-net-native.md) [0: d] [bütünleştirilmiş kod](assembly-element-net-native.md) [0: d] [ad alanı](namespace-element-net-native.md) [0: d].</span><span class="sxs-lookup"><span data-stu-id="ae8fc-145">[Method](method-element-net-native.md) [0:M] [Parameter](parameter-element-net-native.md) [0:M] [TypeParameter](typeparameter-element-net-native.md) [0:M] [GenericParameter](genericparameter-element-net-native.md) [0:M] [MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M] [Property](property-element-net-native.md) [0:M] [Field](field-element-net-native.md) [0:M] [Event](event-element-net-native.md) [0:M] [Library](library-element-net-native.md) [0:M] [Assembly](assembly-element-net-native.md) [0:M] [Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="ae8fc-146">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-146">.</span></span> <span data-ttu-id="ae8fc-147">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-147">.</span></span>
<span data-ttu-id="ae8fc-148">[0: d] [yazın](type-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="ae8fc-148">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="ae8fc-149">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-149">.</span></span> <span data-ttu-id="ae8fc-150">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-150">.</span></span>
<span data-ttu-id="ae8fc-151">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: a].</span><span class="sxs-lookup"><span data-stu-id="ae8fc-151">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="ae8fc-152">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-152">.</span></span> <span data-ttu-id="ae8fc-153">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-153">.</span></span>
<span data-ttu-id="ae8fc-154">[Ad alanı](namespace-element-net-native.md) [0: d] [ad alanı](namespace-element-net-native.md) [0: d].</span><span class="sxs-lookup"><span data-stu-id="ae8fc-154">[Namespace](namespace-element-net-native.md) [0:M] [Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="ae8fc-155">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-155">.</span></span> <span data-ttu-id="ae8fc-156">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-156">.</span></span>
<span data-ttu-id="ae8fc-157">[0: d] [yazın](type-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="ae8fc-157">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="ae8fc-158">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-158">.</span></span> <span data-ttu-id="ae8fc-159">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-159">.</span></span>
<span data-ttu-id="ae8fc-160">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: a].</span><span class="sxs-lookup"><span data-stu-id="ae8fc-160">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="ae8fc-161">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-161">.</span></span> <span data-ttu-id="ae8fc-162">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-162">.</span></span>
<span data-ttu-id="ae8fc-163">[[0](type-element-net-native.md) : d] alt [türleri](subtypes-element-net-native.md) (kapsayan tür alt sınıfları) [o:1] [türü](type-element-net-native.md) [0: ı].</span><span class="sxs-lookup"><span data-stu-id="ae8fc-163">[Type](type-element-net-native.md) [0:M] [Subtypes](subtypes-element-net-native.md) (subclasses of the containing type) [O:1] [Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="ae8fc-164">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-164">.</span></span> <span data-ttu-id="ae8fc-165">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-165">.</span></span>
<span data-ttu-id="ae8fc-166">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: a].</span><span class="sxs-lookup"><span data-stu-id="ae8fc-166">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="ae8fc-167">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-167">.</span></span> <span data-ttu-id="ae8fc-168">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-168">.</span></span>
<span data-ttu-id="ae8fc-169">[Attributemethod](attributeimplies-element-net-native.md) (tür bir öznitelik) [O:1] [genericparameter](genericparameter-element-net-native.md) [0: d] [yöntemi](method-element-net-native.md) [0: d] [methodörneklemesi](methodinstantiation-element-net-native.md) (oluşturulmuş genel yöntem) [0: d] [özellik](property-element-net-native.md) [0: d] [alan](field-element-net-native.md) [0: ı] [olay](event-element-net-native.md) [0 : N] [Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: d] [tür](type-element-net-native.md) [0: d].</span><span class="sxs-lookup"><span data-stu-id="ae8fc-169">[AttributeImplies](attributeimplies-element-net-native.md) (containing type is an attribute) [O:1] [GenericParameter](genericparameter-element-net-native.md) [0:M] [Method](method-element-net-native.md) [0:M] [MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M] [Property](property-element-net-native.md) [0:M] [Field](field-element-net-native.md) [0:M] [Event](event-element-net-native.md) [0:M] [TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] [Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="ae8fc-170">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-170">.</span></span> <span data-ttu-id="ae8fc-171">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-171">.</span></span>
<span data-ttu-id="ae8fc-172">[Typeörneklemesi](typeinstantiation-element-net-native.md) (oluşturulmuş genel tür) [0: a].</span><span class="sxs-lookup"><span data-stu-id="ae8fc-172">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="ae8fc-173">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-173">.</span></span> <span data-ttu-id="ae8fc-174">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-174">.</span></span>
<span data-ttu-id="ae8fc-175">[Yöntem](method-element-net-native.md) [0: d] [methodörneklemesi](methodinstantiation-element-net-native.md) (oluşturulmuş genel yöntem) [0: d] [özellik](property-element-net-native.md) [0: d] [alan](field-element-net-native.md) [0: d] [olay](event-element-net-native.md) [0: d]</span><span class="sxs-lookup"><span data-stu-id="ae8fc-175">[Method](method-element-net-native.md) [0:M] [MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M] [Property](property-element-net-native.md) [0:M] [Field](field-element-net-native.md) [0:M] [Event](event-element-net-native.md) [0:M]</span></span>

<span data-ttu-id="ae8fc-176">[Uygulama](application-element-net-native.md) öğesinin hiç özniteliği olamaz veya [çalışma zamanı yönergesinde ve ilke bölümünde](#Directives)ele alınan ilke özniteliklerine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-176">The [Application](application-element-net-native.md) element can have no attributes, or it can have the policy attributes discussed in the [Runtime directive and policy section](#Directives).</span></span>

<span data-ttu-id="ae8fc-177">Bir [kitaplık](library-element-net-native.md) öğesi, dosya uzantısı olmadan bir kitaplığın veya derlemenin adını belirten tek bir özniteliğe sahiptir `Name`.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-177">A [Library](library-element-net-native.md) element has a single attribute, `Name`, that specifies the name of a library or assembly, without its file extension.</span></span> <span data-ttu-id="ae8fc-178">Örneğin, aşağıdaki [kitaplık](library-element-net-native.md) öğesi Extensions. dll adlı bir derleme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-178">For example, the following [Library](library-element-net-native.md) element applies to an assembly named Extensions.dll.</span></span>

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

## <a name="runtime-directives-and-policy"></a><span data-ttu-id="ae8fc-179">Çalışma zamanı yönergeleri ve ilkesi</span><span class="sxs-lookup"><span data-stu-id="ae8fc-179">Runtime directives and policy</span></span>

<span data-ttu-id="ae8fc-180">[Uygulama](application-element-net-native.md) öğesinin kendisi ve [kitaplık](library-element-net-native.md) ve [uygulama](application-element-net-native.md) öğeleri Express ilkesinin alt öğeleri; diğer bir deyişle, bir uygulamanın bir program öğesine yansıma uygulayabileceği şekilde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-180">The [Application](application-element-net-native.md) element itself and the child elements of the [Library](library-element-net-native.md) and [Application](application-element-net-native.md) elements express policy; that is, they define the way in which an app can apply reflection to a program element.</span></span> <span data-ttu-id="ae8fc-181">İlke türü, öğesinin bir özniteliği tarafından tanımlanır (örneğin, `Serialize`).</span><span class="sxs-lookup"><span data-stu-id="ae8fc-181">The policy type is defined by an attribute of the element (for example, `Serialize`).</span></span> <span data-ttu-id="ae8fc-182">İlke değeri özniteliğin değeri (örneğin, `Serialize="Required"`) tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-182">The policy value is defined by the attribute’s value (for example, `Serialize="Required"`).</span></span>

<span data-ttu-id="ae8fc-183">Bir öğenin özniteliği tarafından belirtilen herhangi bir ilke, bu ilke için bir değer belirtmeyen tüm alt öğeler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-183">Any policy specified by an attribute of an element applies to all child elements that don’t specify a value for that policy.</span></span> <span data-ttu-id="ae8fc-184">Örneğin, bir ilke bir [tür](type-element-net-native.md) öğesiyle belirtilmişse, bu ilke, bir ilkenin açıkça belirtilmediği tüm içerilen türler ve Üyeler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-184">For example, if a policy is specified by a [Type](type-element-net-native.md) element, that policy applies to all contained types and members for which a policy is not explicitly specified.</span></span>

<span data-ttu-id="ae8fc-185">[Uygulama](application-element-net-native.md), [derleme](assembly-element-net-native.md), [attributeby](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), alt [türler](subtypes-element-net-native.md)ve [tür](type-element-net-native.md) öğeleri tarafından ifade edilen ilke, ayrı Üyeler için ifade edilebilir ilkeden farklıdır ( [Yöntemi](method-element-net-native.md), [özelliği](property-element-net-native.md), [alanı](field-element-net-native.md)ve [olay](event-element-net-native.md) öğeleri).</span><span class="sxs-lookup"><span data-stu-id="ae8fc-185">The policy that can be expressed by the [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md), and [Type](type-element-net-native.md) elements differs from the policy that can be expressed for individual members (by the [Method](method-element-net-native.md), [Property](property-element-net-native.md), [Field](field-element-net-native.md), and [Event](event-element-net-native.md) elements).</span></span>

### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a><span data-ttu-id="ae8fc-186">Derlemeler, ad alanları ve türler için ilke belirtme</span><span class="sxs-lookup"><span data-stu-id="ae8fc-186">Specifying policy for assemblies, namespaces, and types</span></span>

<span data-ttu-id="ae8fc-187">[Uygulama](application-element-net-native.md), [derleme](assembly-element-net-native.md), [attributeme](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), alt [türleri](subtypes-element-net-native.md)ve [tür](type-element-net-native.md) öğeleri aşağıdaki ilke türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="ae8fc-187">The [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md), and [Type](type-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="ae8fc-188">`Activate`.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-188">`Activate`.</span></span> <span data-ttu-id="ae8fc-189">Örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-189">Controls runtime access to constructors, to enable activation of instances.</span></span>

- <span data-ttu-id="ae8fc-190">`Browse`.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-190">`Browse`.</span></span> <span data-ttu-id="ae8fc-191">Program öğeleri hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-191">Controls querying for information about program elements but does not enable any runtime access.</span></span>

- <span data-ttu-id="ae8fc-192">`Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-192">`Dynamic`.</span></span> <span data-ttu-id="ae8fc-193">Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-193">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>

- <span data-ttu-id="ae8fc-194">`Serialize`.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-194">`Serialize`.</span></span> <span data-ttu-id="ae8fc-195">Tür örneklerinin, Newtonsoft JSON serileştirici gibi üçüncü taraf kitaplıklara serileştirilmesi ve serileştirilmesi için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-195">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and serialized by third-party libraries such as the Newtonsoft JSON serializer.</span></span>

- <span data-ttu-id="ae8fc-196">`DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-196">`DataContractSerializer`.</span></span> <span data-ttu-id="ae8fc-197"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfını kullanan serileştirme için ilkeyi denetler.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-197">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="ae8fc-198">`DataContractJsonSerializer`.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-198">`DataContractJsonSerializer`.</span></span> <span data-ttu-id="ae8fc-199"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfını kullanan JSON serileştirme için ilkeyi denetler.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-199">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="ae8fc-200">`XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-200">`XmlSerializer`.</span></span> <span data-ttu-id="ae8fc-201"><xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfını kullanan XML serileştirme ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-201">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="ae8fc-202">`MarshalObject`.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-202">`MarshalObject`.</span></span> <span data-ttu-id="ae8fc-203">WinRT ve COM 'a başvuru türlerini hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-203">Controls policy for marshaling reference types to WinRT and COM.</span></span>

- <span data-ttu-id="ae8fc-204">`MarshalDelegate`.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-204">`MarshalDelegate`.</span></span> <span data-ttu-id="ae8fc-205">Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-205">Controls policy for marshaling delegate types as function pointers to native code.</span></span>

- <span data-ttu-id="ae8fc-206">`MarshalStructure`.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-206">`MarshalStructure` .</span></span> <span data-ttu-id="ae8fc-207">Yapıları yerel koda hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-207">Controls policy for marshaling structures to native code.</span></span>

<span data-ttu-id="ae8fc-208">Bu ilke türleriyle ilişkili ayarlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ae8fc-208">The settings associated with these policy types are:</span></span>

- <span data-ttu-id="ae8fc-209">`All`.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-209">`All`.</span></span> <span data-ttu-id="ae8fc-210">Araç zincirinin kaldıramayan tüm türler ve Üyeler için ilkeyi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-210">Enable the policy for all types and members that the tool chain does not remove.</span></span>

- <span data-ttu-id="ae8fc-211">`Auto`.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-211">`Auto`.</span></span> <span data-ttu-id="ae8fc-212">Varsayılan davranışı kullanın.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-212">Use the default behavior.</span></span> <span data-ttu-id="ae8fc-213">(İlke belirtilmeden, ilke geçersiz kılınmadıkça (örneğin, bir üst öğe), bu ilke `Auto` ayarlamaya eşdeğerdir.)</span><span class="sxs-lookup"><span data-stu-id="ae8fc-213">(Not specifying a policy is equivalent to setting that policy to `Auto` unless that policy is overridden, for example by a parent element.)</span></span>

- <span data-ttu-id="ae8fc-214">`Excluded`.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-214">`Excluded`.</span></span> <span data-ttu-id="ae8fc-215">Program öğesi için ilkeyi devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-215">Disable the policy for the program element.</span></span>

- <span data-ttu-id="ae8fc-216">`Public`.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-216">`Public`.</span></span> <span data-ttu-id="ae8fc-217">Araç zinciri üyenin gereksiz olduğunu belirlerse ve bu nedenle uygulamayı kaldırmadığı müddetçe ortak türler veya Üyeler için ilkeyi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-217">Enable the policy for public types or members unless the tool chain determines that the member is unnecessary and therefore removes it.</span></span> <span data-ttu-id="ae8fc-218">(İkinci durumda, üyenin tutulduğundan ve yansıma özelliklerine sahip olduğundan emin olmak için `Required Public` kullanmanız gerekir.)</span><span class="sxs-lookup"><span data-stu-id="ae8fc-218">(In the latter case, you must use `Required Public` to ensure that the member is kept and has reflection capabilities.)</span></span>

- <span data-ttu-id="ae8fc-219">`PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-219">`PublicAndInternal`.</span></span> <span data-ttu-id="ae8fc-220">Araç zinciri onları kaldırmazsa ortak ve iç türler veya Üyeler için ilkeyi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-220">Enable the policy for public and internal types or members if the tool chain doesn't remove them.</span></span>

- <span data-ttu-id="ae8fc-221">`Required Public`.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-221">`Required Public`.</span></span> <span data-ttu-id="ae8fc-222">Ortak türleri ve üyeleri, kullanıldıkları ve kullanılmayacağı gibi tutmak ve ilke için etkinleştirmek üzere araç zinciri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-222">Require the tool chain to keep public types and members whether or not they are used, and enable the policy for them.</span></span>

- <span data-ttu-id="ae8fc-223">`Required PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-223">`Required PublicAndInternal`.</span></span> <span data-ttu-id="ae8fc-224">Araç zincirinin hem ortak hem de iç türleri ve üyeleri, kullanılmalarına bakılmaksızın ve bunları kendileri için etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-224">Require the tool chain to keep both public and internal types and members whether or not they are used, and enable the policy for them.</span></span>

- <span data-ttu-id="ae8fc-225">`Required All`.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-225">`Required All`.</span></span> <span data-ttu-id="ae8fc-226">Araç zincirinin tüm türleri ve üyeleri kullanıp kullanmadığını ve bunların kullanılmadığını ve ilke için etkin olmasını gerektir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-226">Require the tool chain to keep all types and members whether or not they are used, and enable the policy for them.</span></span>

<span data-ttu-id="ae8fc-227">Örneğin, aşağıdaki çalışma zamanı yönergeleri dosyası, veri sınıfları. dll dosyasındaki tüm türler ve Üyeler için ilkeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-227">For example, the following runtime directives file defines policy for all types and members in the assembly DataClasses.dll.</span></span> <span data-ttu-id="ae8fc-228">Tüm ortak özelliklerin serileştirilmesi için yansıma kullanımını, tüm türler ve tür üyeleri için gözatmayı etkinleştirmek, tüm türler için etkinleştirmeyi etkinleştirmek (`Dynamic` özniteliği nedeniyle) ve tüm genel türler ve Üyeler için yansıma etkinleştirmek için yansıma imkanı sunar.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-228">It enables reflection for serialization of all public properties, enables browsing for all types and type members, enables activation for all types (because of the `Dynamic` attribute), and enables reflection for all public types and members.</span></span>

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

### <a name="specifying-policy-for-members"></a><span data-ttu-id="ae8fc-229">Üyeler için ilke belirtme</span><span class="sxs-lookup"><span data-stu-id="ae8fc-229">Specifying policy for members</span></span>

<span data-ttu-id="ae8fc-230">[Özellik](property-element-net-native.md) ve [alan](field-element-net-native.md) öğeleri aşağıdaki ilke türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="ae8fc-230">The [Property](property-element-net-native.md) and [Field](field-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="ae8fc-231">`Browse`-Bu üye hakkında bilgi sorgulama denetimleri, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-231">`Browse` - Controls querying for information about this member but does not enable any runtime access.</span></span>

- <span data-ttu-id="ae8fc-232">`Dynamic`-dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-232">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="ae8fc-233">Ayrıca, kapsayan tür hakkındaki bilgileri sorgulamayı denetler.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-233">Also controls querying for information about the containing type.</span></span>

- <span data-ttu-id="ae8fc-234">`Serialize`-tür örneklerinin, Newtonsoft JSON serileştirici gibi kitaplıklar tarafından serileştirilmesi ve seri durumdan çıkarılmakta olması için üyeye çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-234">`Serialize` - Controls runtime access to the member to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span> <span data-ttu-id="ae8fc-235">Bu ilke oluşturucular, alanlar ve özelliklere uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-235">This policy can be applied to constructors, fields, and properties.</span></span>

<span data-ttu-id="ae8fc-236">[Yöntemi](method-element-net-native.md) ve [olay](event-element-net-native.md) öğeleri aşağıdaki ilke türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="ae8fc-236">The [Method](method-element-net-native.md) and [Event](event-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="ae8fc-237">`Browse`-Bu üye hakkında bilgi sorgulama denetimleri, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-237">`Browse` - Controls querying for information about this member but doesn’t enable any runtime access.</span></span>

- <span data-ttu-id="ae8fc-238">`Dynamic`-dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-238">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="ae8fc-239">Ayrıca, kapsayan tür hakkındaki bilgileri sorgulamayı denetler.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-239">Also controls querying for information about the containing type.</span></span>

 <span data-ttu-id="ae8fc-240">Bu ilke türleriyle ilişkili ayarlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ae8fc-240">The settings associated with these policy types are:</span></span>

- <span data-ttu-id="ae8fc-241">`Auto`-varsayılan davranışı kullanın.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-241">`Auto` - Use the default behavior.</span></span> <span data-ttu-id="ae8fc-242">(İlke belirtmeksizin, bir öğe geçersiz kılınmadığı takdirde bu ilkenin `Auto` ayarlanmasına eşdeğerdir.)</span><span class="sxs-lookup"><span data-stu-id="ae8fc-242">(Not specifying a policy is equivalent to setting that policy to `Auto` unless something overrides it.)</span></span>

- <span data-ttu-id="ae8fc-243">`Excluded`-üyenin meta verilerini hiçbir şekilde eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-243">`Excluded` - Never include metadata for the member.</span></span>

- <span data-ttu-id="ae8fc-244">`Included`-üst tür çıktıda varsa ilkeyi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-244">`Included` - Enable the policy if the parent type is present in the output.</span></span>

- <span data-ttu-id="ae8fc-245">`Required`-araç zincirinin, kullanılmamış gibi görünse bile bu üyeyi tutması gerekir ve ilkeyi etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-245">`Required` - Require the tool chain to keep this member even if appears to be unused, and enable policy for it.</span></span>

## <a name="runtime-directives-file-semantics"></a><span data-ttu-id="ae8fc-246">Çalışma zamanı yönergeleri dosya semantiği</span><span class="sxs-lookup"><span data-stu-id="ae8fc-246">Runtime directives file semantics</span></span>

<span data-ttu-id="ae8fc-247">İlke, hem daha yüksek hem de alt düzey öğeler için eşzamanlı olarak tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-247">Policy can be defined simultaneously for both higher-level and lower-level elements.</span></span> <span data-ttu-id="ae8fc-248">Örneğin, ilke bir derleme için ve bu derlemede yer alan bazı türler için tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-248">For example, policy can be defined for an assembly, and for some of the types contained in that assembly.</span></span> <span data-ttu-id="ae8fc-249">Belirli bir alt düzey öğe gösterilmediğinden, üst öğesinin ilkesini devralır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-249">If a particular lower-level element is not represented, it inherits the policy of its parent.</span></span> <span data-ttu-id="ae8fc-250">Örneğin, bir `Assembly` öğesi varsa ancak `Type` öğeler yoksa, `Assembly` öğesinde belirtilen ilke derlemedeki her tür için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-250">For example, if an `Assembly` element is present but `Type` elements are not, the policy specified in the `Assembly` element applies to each type in the assembly.</span></span> <span data-ttu-id="ae8fc-251">Aynı program öğesine aynı zamanda birden çok öğe ilke uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-251">Multiple elements can also apply policy to the same program element.</span></span> <span data-ttu-id="ae8fc-252">Örneğin, ayrı [derleme](assembly-element-net-native.md) öğeleri aynı derleme için aynı ilke öğesini farklı şekilde tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-252">For example, separate [Assembly](assembly-element-net-native.md) elements might define the same policy element for the same assembly differently.</span></span> <span data-ttu-id="ae8fc-253">Aşağıdaki bölümlerde, belirli bir türün ilkesinin bu durumlarda nasıl çözümlendiğini açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-253">The following sections explain how the policy for a particular type is resolved in those cases.</span></span>

<span data-ttu-id="ae8fc-254">Genel bir türün veya yöntemin [tür](type-element-net-native.md) veya [Yöntem](method-element-net-native.md) öğesi, kendi ilkesi olmayan tüm örneklemelerde ilkesini uygular.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-254">A [Type](type-element-net-native.md) or [Method](method-element-net-native.md) element of a generic type or method applies its policy to all instantiations that do not have their own policy.</span></span> <span data-ttu-id="ae8fc-255">Örneğin, <xref:System.Collections.Generic.List%601> ilkesini belirten `Type` bir öğesi, belirli bir oluşturulan genel tür için (`List<Int32>`gibi) bir `TypeInstantiation` öğesi tarafından geçersiz kılınmadığı sürece, bu genel türün oluşturulan tüm örnekleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-255">For example, a `Type` element that specifies policy for <xref:System.Collections.Generic.List%601> applies to all constructed instances of that generic type, unless it's overridden for a particular constructed generic type (such as a `List<Int32>`) by a `TypeInstantiation` element.</span></span> <span data-ttu-id="ae8fc-256">Aksi takdirde, öğeleri adlı program öğesi için ilkeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-256">Otherwise, elements define policy for the program element named.</span></span>

<span data-ttu-id="ae8fc-257">Bir öğe belirsiz olduğunda, motor eşleşme arar ve tam eşleşme bulursa onu kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-257">When an element is ambiguous, the engine looks for matches, and if it finds an exact match, it will use it.</span></span> <span data-ttu-id="ae8fc-258">Birden çok eşleşme bulunursa bir uyarı veya hata olur.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-258">If it finds multiple matches, there will be a warning or error.</span></span>

### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a><span data-ttu-id="ae8fc-259">İki yönergeler aynı program öğesine ilke uygualıyorsa</span><span class="sxs-lookup"><span data-stu-id="ae8fc-259">If two directives apply policy to the same program element</span></span>

<span data-ttu-id="ae8fc-260">Farklı çalışma zamanı yönergeleri dosyalarındaki iki öğe aynı program öğesi (bir derleme veya tür gibi) için aynı ilke türünü farklı değerlere ayarlamaya çalışıyorsa, çakışma aşağıdaki gibi çözümlenir:</span><span class="sxs-lookup"><span data-stu-id="ae8fc-260">If two elements in different runtime directives files try to set the same policy type for the same program element (such as an assembly or type) to different values, the conflict is resolved as follows:</span></span>

1. <span data-ttu-id="ae8fc-261">`Excluded` öğesi varsa önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-261">If the `Excluded` element is present, it has precedence.</span></span>

2. <span data-ttu-id="ae8fc-262">`Required` `Required`değil önceliğe sahip.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-262">`Required` has precedence over not `Required`.</span></span>

3. <span data-ttu-id="ae8fc-263">`All`, `Public`öncelikli olan `PublicAndInternal`önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-263">`All` has precedence over `PublicAndInternal`, which has precedence over `Public`.</span></span>

4. <span data-ttu-id="ae8fc-264">Herhangi bir açık ayar `Auto`önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-264">Any explicit setting has precedence over `Auto`.</span></span>

<span data-ttu-id="ae8fc-265">Örneğin, tek bir proje aşağıdaki iki çalışma zamanı yönergeleri dosyasını içeriyorsa, DataClasses. dll için serileştirme ilkesi hem `Required Public` hem de `All`olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-265">For example, if a single project includes the following two runtime directives files, the serialization policy for DataClasses.dll is set to both `Required Public` and `All`.</span></span> <span data-ttu-id="ae8fc-266">Bu durumda, serileştirme ilkesi `Required All`olarak çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-266">In this case, the serialization policy would be resolved as `Required All`.</span></span>

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

<span data-ttu-id="ae8fc-267">Ancak, tek bir çalışma zamanı yönergeleri dosyasında iki yönergesi aynı program öğesi için aynı ilke türünü ayarlamaya çalışırsanız, XML şeması tanım aracında bir hata iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-267">However, if two directives in a single runtime directives file try to set the same policy type for the same program element, the XML Scheme Definition tool displays an error message.</span></span>

### <a name="if-child-and-parent-elements-apply-the-same-policy-type"></a><span data-ttu-id="ae8fc-268">Alt ve üst öğeler aynı ilke türünü uygualıyorsa</span><span class="sxs-lookup"><span data-stu-id="ae8fc-268">If child and parent elements apply the same policy type</span></span>

<span data-ttu-id="ae8fc-269">Alt öğeler, `Excluded` ayarı da dahil olmak üzere üst öğelerini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-269">Child elements override their parent elements, including the `Excluded` setting.</span></span> <span data-ttu-id="ae8fc-270">Geçersiz kılma, `Auto`belirtmek istediğiniz ana nedendir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-270">Overriding is the main reason you would want to specify `Auto`.</span></span>

<span data-ttu-id="ae8fc-271">Aşağıdaki örnekte, `DataClasses.ViewModels` olmayan `DataClasses` her şey için serileştirme ilkesi ayarı `Required Public`ve hem `DataClasses` hem de `DataClasses.ViewModels` içindeki her şey `All`olur.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-271">In the following example, the serialization policy setting for everything in `DataClasses` that’s not in `DataClasses.ViewModels` would be `Required Public`, and everything that's in both `DataClasses` and `DataClasses.ViewModels` would be `All`.</span></span>

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

### <a name="if-open-generics-and-instantiated-elements-apply-the-same-policy-type"></a><span data-ttu-id="ae8fc-272">Açık genel türler ve örneklenmiş öğeler aynı ilke türünü uygular</span><span class="sxs-lookup"><span data-stu-id="ae8fc-272">If open generics and instantiated elements apply the same policy type</span></span>

<span data-ttu-id="ae8fc-273">Aşağıdaki örnekte, `Dictionary<int,int>` `Browse` ilkesine yalnızca altyapının, bu bileşene `Browse` ilkesi (Aksi takdirde varsayılan davranış) izin vermek için başka bir nedeni varsa atanır; <xref:System.Collections.Generic.Dictionary%602> diğer tüm örneklemelerinden tüm üyeleri gözatılabilir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-273">In the following example, `Dictionary<int,int>` is assigned the `Browse` policy only if the engine has another reason to give it the `Browse` policy (which would otherwise be the default behavior); every other instantiation of <xref:System.Collections.Generic.Dictionary%602> will have all of its members browsable.</span></span>

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

### <a name="how-policy-is-inferred"></a><span data-ttu-id="ae8fc-274">İlke nasıl algılanır</span><span class="sxs-lookup"><span data-stu-id="ae8fc-274">How policy is inferred</span></span>

<span data-ttu-id="ae8fc-275">Her ilke türünün, bu ilke türü varlığının diğer yapıları nasıl etkilediğini tespit eden farklı kurallar kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-275">Each policy type has a different set of rules that determine how the presence of that policy type affects other constructs.</span></span>

#### <a name="the-effect-of-browse-policy"></a><span data-ttu-id="ae8fc-276">Tarayıcı ilkesinin etkisi</span><span class="sxs-lookup"><span data-stu-id="ae8fc-276">The effect of Browse policy</span></span>

<span data-ttu-id="ae8fc-277">`Browse` ilkesinin bir türe uygulanması aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="ae8fc-277">Applying the `Browse` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="ae8fc-278">Türün temel türü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-278">The base type of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="ae8fc-279">Tür bir genel ise, türün örneklenmemiş sürümü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-279">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="ae8fc-280">Tür bir temsilciyiyise, türdeki `Invoke` yöntemi `Dynamic` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-280">If the type is a delegate, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="ae8fc-281">Türün her arabirimi `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-281">Each interface of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="ae8fc-282">Türe uygulanan her bir özniteliğin türü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-282">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="ae8fc-283">Tür geneldir ise, her kısıtlama türü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-283">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="ae8fc-284">Tür geneldir ise, türün örneklendiği türler `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-284">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="ae8fc-285">`Browse` ilkesinin bir yönteme uygulanması aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="ae8fc-285">Applying the `Browse` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="ae8fc-286">Yöntemin her bir parametre türü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-286">Each parameter type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="ae8fc-287">Metodun dönüş türü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-287">The return type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="ae8fc-288">Yöntemin kapsayan türü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-288">The containing type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="ae8fc-289">Yöntem örneklenmiş genel bir yöntem ise, örneklenmemiş genel yöntem `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-289">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="ae8fc-290">Yöntemine uygulanan her bir özniteliğin türü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-290">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="ae8fc-291">Yöntem geneldir ise, her kısıtlama türü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-291">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="ae8fc-292">Yöntem genel ise, yöntemin örneklendiği türler `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-292">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="ae8fc-293">`Browse` ilkesinin bir alana uygulanması aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="ae8fc-293">Applying the `Browse` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="ae8fc-294">Alana uygulanan her bir özniteliğin türü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-294">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="ae8fc-295">Alanın türü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-295">The type of the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="ae8fc-296">Alanın ait olduğu tür `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-296">The type to which the field belongs is marked with the `Browse` policy.</span></span>

#### <a name="the-effect-of-dynamic-policy"></a><span data-ttu-id="ae8fc-297">Dinamik ilkenin etkisi</span><span class="sxs-lookup"><span data-stu-id="ae8fc-297">The effect of Dynamic policy</span></span>

<span data-ttu-id="ae8fc-298">`Dynamic` ilkesinin bir türe uygulanması aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="ae8fc-298">Applying the `Dynamic` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="ae8fc-299">Türün temel türü `Dynamic` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-299">The base type of the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="ae8fc-300">Tür bir genel ise, türün örneklenmemiş sürümü `Dynamic` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-300">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="ae8fc-301">Tür bir temsilci türü ise, türdeki `Invoke` yöntemi `Dynamic` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-301">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="ae8fc-302">Türün her arabirimi `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-302">Each interface of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="ae8fc-303">Türe uygulanan her bir özniteliğin türü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-303">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="ae8fc-304">Tür geneldir ise, her kısıtlama türü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-304">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="ae8fc-305">Tür geneldir ise, türün örneklendiği türler `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-305">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="ae8fc-306">`Dynamic` ilkesinin bir yönteme uygulanması aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="ae8fc-306">Applying the `Dynamic` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="ae8fc-307">Yöntemin her bir parametre türü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-307">Each parameter type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="ae8fc-308">Metodun dönüş türü `Dynamic` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-308">The return type of the method is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="ae8fc-309">Yöntemin kapsayan türü `Dynamic` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-309">The containing type of the method is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="ae8fc-310">Yöntem örneklenmiş genel bir yöntem ise, örneklenmemiş genel yöntem `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-310">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="ae8fc-311">Yöntemine uygulanan her bir özniteliğin türü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-311">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="ae8fc-312">Yöntem geneldir ise, her kısıtlama türü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-312">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="ae8fc-313">Yöntem genel ise, yöntemin örneklendiği türler `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-313">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>

- <span data-ttu-id="ae8fc-314">Yöntemi `MethodInfo.Invoke`tarafından çağrılabilir ve temsilci oluşturma <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>tarafından mümkün hale gelir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-314">The method can be invoked by `MethodInfo.Invoke`, and delegate creation becomes possible by <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="ae8fc-315">`Dynamic` ilkesinin bir alana uygulanması aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="ae8fc-315">Applying the `Dynamic` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="ae8fc-316">Alana uygulanan her bir özniteliğin türü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-316">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="ae8fc-317">Alanın türü `Dynamic` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-317">The type of the field is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="ae8fc-318">Alanın ait olduğu tür `Dynamic` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-318">The type to which the field belongs is marked with the `Dynamic` policy.</span></span>

#### <a name="the-effect-of-activation-policy"></a><span data-ttu-id="ae8fc-319">Etkinleştirme ilkesinin etkisi</span><span class="sxs-lookup"><span data-stu-id="ae8fc-319">The effect of Activation policy</span></span>

<span data-ttu-id="ae8fc-320">Etkinleştirme ilkesini bir türe uygulamak aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="ae8fc-320">Applying the Activation policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="ae8fc-321">Tür bir genel ise, türün örneklenmemiş sürümü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-321">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="ae8fc-322">Tür bir temsilci türü ise, türdeki `Invoke` yöntemi `Dynamic` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-322">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="ae8fc-323">Türün oluşturucuları `Activation` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-323">Constructors of the type are marked with the `Activation` policy.</span></span>

<span data-ttu-id="ae8fc-324">`Activation` ilkesinin bir yönteme uygulanması aşağıdaki ilke değişikliğini içerir:</span><span class="sxs-lookup"><span data-stu-id="ae8fc-324">Applying the `Activation` policy to a method involves the following policy change:</span></span>

- <span data-ttu-id="ae8fc-325">Oluşturucu <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> ve <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> yöntemlerle çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-325">The constructor can be invoked by the <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> and <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="ae8fc-326">Yöntemler için `Activation` ilkesi yalnızca oluşturucuları etkiler.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-326">For methods, the `Activation` policy affects constructors only.</span></span>

<span data-ttu-id="ae8fc-327">`Activation` ilkesinin bir alana uygulanması etkisizdir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-327">Applying the `Activation` policy to a field has no effect.</span></span>

#### <a name="the-effect-of-serialize-policy"></a><span data-ttu-id="ae8fc-328">Seri hale getirme ilkesinin etkisi</span><span class="sxs-lookup"><span data-stu-id="ae8fc-328">The effect of Serialize policy</span></span>

<span data-ttu-id="ae8fc-329">`Serialize` ilkesi, yaygın yansıma tabanlı serileştiricilerin kullanımını sunar.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-329">The `Serialize` policy enables the use of common reflection-based serializers.</span></span> <span data-ttu-id="ae8fc-330">Ancak, Microsoft dışı serileştiricilerin tam yansıma erişimi desenleri Microsoft tarafından bilinmediğinden, bu ilke tamamen etkili olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-330">However, because the exact reflection access patterns of non-Microsoft serializers are not known to Microsoft, this policy may not be entirely effective.</span></span>

<span data-ttu-id="ae8fc-331">`Serialize` ilkesinin bir türe uygulanması aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="ae8fc-331">Applying the `Serialize` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="ae8fc-332">Türün temel türü `Serialize` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-332">The base type of the type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="ae8fc-333">Tür bir genel ise, türün örneklenmemiş sürümü `Browse` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-333">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="ae8fc-334">Tür bir temsilci türü ise, türdeki `Invoke` yöntemi `Dynamic` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-334">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="ae8fc-335">Tür bir sabit listesi ise, türün bir dizisi `Serialize` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-335">If the type is an enumeration, an array of the type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="ae8fc-336">Tür <xref:System.Collections.Generic.IEnumerable%601>uygularsa, `T` `Serialize` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-336">If the type implements <xref:System.Collections.Generic.IEnumerable%601>, `T` is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="ae8fc-337">Tür <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>veya <xref:System.Collections.Generic.IReadOnlyList%601>, `T[]` ve <xref:System.Collections.Generic.List%601> `Serialize` ilkeyle işaretlenir. ancak, arabirim türünün hiçbir üyesi `Serialize` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-337">If the type is <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>, or <xref:System.Collections.Generic.IReadOnlyList%601>, then `T[]` and <xref:System.Collections.Generic.List%601> marked with the `Serialize` policy., but no members of the interface type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="ae8fc-338">Tür <xref:System.Collections.Generic.List%601>ise, türün hiçbir üyesi `Serialize` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-338">If the type is <xref:System.Collections.Generic.List%601>, no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="ae8fc-339">Tür <xref:System.Collections.Generic.IDictionary%602>ise, <xref:System.Collections.Generic.Dictionary%602> `Serialize` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-339">If the type is <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> is marked with the `Serialize` policy.</span></span> <span data-ttu-id="ae8fc-340">Ancak türdeki hiçbir üye `Serialize` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-340">but no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="ae8fc-341">Tür <xref:System.Collections.Generic.Dictionary%602>ise, türün hiçbir üyesi `Serialize` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-341">If the type is <xref:System.Collections.Generic.Dictionary%602>, no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="ae8fc-342">Tür <xref:System.Collections.Generic.IDictionary%602>uygularsa `TKey` ve `TValue` `Serialize` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-342">If the type implements <xref:System.Collections.Generic.IDictionary%602>, `TKey` and `TValue` are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="ae8fc-343">Her bir Oluşturucu, her özellik erişimcisi ve her bir alan `Serialize` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-343">Each constructor, each property accessor, and each field is marked with the `Serialize` policy.</span></span>

<span data-ttu-id="ae8fc-344">`Serialize` ilkesinin bir yönteme uygulanması aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="ae8fc-344">Applying the `Serialize` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="ae8fc-345">Kapsayan tür `Serialize` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-345">The containing type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="ae8fc-346">Metodun dönüş türü `Serialize` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-346">The return type of the method is marked with the `Serialize` policy.</span></span>

<span data-ttu-id="ae8fc-347">`Serialize` ilkesinin bir alana uygulanması aşağıdaki ilke değişikliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="ae8fc-347">Applying the `Serialize` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="ae8fc-348">Kapsayan tür `Serialize` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-348">The containing type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="ae8fc-349">Alanın türü `Serialize` ilkesiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-349">The type of the field is marked with the `Serialize` policy.</span></span>

#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserializer-policies"></a><span data-ttu-id="ae8fc-350">XmlSerializer, DataContractSerializer ve DataContractJsonSerializer ilkelerinin etkisi</span><span class="sxs-lookup"><span data-stu-id="ae8fc-350">The effect of XmlSerializer, DataContractSerializer, and DataContractJsonSerializer policies</span></span>

<span data-ttu-id="ae8fc-351">Yansıma tabanlı serileştiriciler için tasarlanan `Serialize` ilkesinin aksine, .NET Native araç zinciri tarafından bilinen serileştiriciler kümesini etkinleştirmek için <xref:System.Xml.Serialization.XmlSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer>ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ilkeleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-351">Unlike the `Serialize` policy, which is intended for reflection-based serializers, the <xref:System.Xml.Serialization.XmlSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer>, and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> policies are used to enable a set of serializers that are known to the .NET Native tool chain.</span></span> <span data-ttu-id="ae8fc-352">Bu serileştiriciler yansıma kullanılarak uygulanmaz, ancak çalışma zamanında seri hale getirilebildiğiniz türler kümesi, yansıma \ olan türler gibi benzer şekilde belirlenir.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-352">These serializers are not implemented by using reflection, but the set of types that can be serialized at run time is determined in a similar manner as types that are reflectable.</span></span>

<span data-ttu-id="ae8fc-353">Bu ilkelerin bir türe uygulanması, türün eşleşen serileştirici ile serileştirilmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-353">Applying one of these policies to a type enables the type to be serialized with the matching serializer.</span></span> <span data-ttu-id="ae8fc-354">Ayrıca, serileştirme altyapısının serileştirilmesi gereken şekilde statik olarak belirleyebilmesi için herhangi bir tür de serileştirilebilir olur.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-354">Also, any types that the serialization engine can statically determine as needing serialization will also be serializable.</span></span>

<span data-ttu-id="ae8fc-355">Bu ilkelerin Yöntemler veya alanlar üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-355">These policies have no effect on methods or fields.</span></span>

<span data-ttu-id="ae8fc-356">Daha fazla bilgi için [Windows mağazası uygulamanızı .NET Native geçirme](migrating-your-windows-store-app-to-net-native.md)konusunun "Serileştiricilerle ilgili farklılıklar" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-356">For more information, see the "Differences in Serializers" section in [Migrating Your Windows Store App to .NET Native](migrating-your-windows-store-app-to-net-native.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ae8fc-357">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae8fc-357">See also</span></span>

- [<span data-ttu-id="ae8fc-358">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="ae8fc-358">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="ae8fc-359">Yansıma ve .NET Native</span><span class="sxs-lookup"><span data-stu-id="ae8fc-359">Reflection and .NET Native</span></span>](reflection-and-net-native.md)
