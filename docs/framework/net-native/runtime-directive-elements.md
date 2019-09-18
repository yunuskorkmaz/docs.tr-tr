---
title: Çalışma Zamanı Yönerge Öğeleri
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 062f13ad92f37bb7ae29ed34dcf88f99f98e7612
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049267"
---
# <a name="runtime-directive-elements"></a><span data-ttu-id="af399-102">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="af399-102">Runtime Directive Elements</span></span>
<span data-ttu-id="af399-103">Çalışma zamanı yönergeleri (RD. xml) dosya biçimi aşağıdaki çalışma zamanı yönerge öğelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="af399-103">The runtime directives (rd.xml) file format supports the following runtime directive elements.</span></span> <span data-ttu-id="af399-104">Hiyerarşik bir gösterim için bkz. [çalışma zamanı yönergeleri (RD. xml) yapılandırma dosyası başvurusu](runtime-directives-rd-xml-configuration-file-reference.md) .</span><span class="sxs-lookup"><span data-stu-id="af399-104">See [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md) for a hierarchical representation.</span></span>  
  
 [<span data-ttu-id="af399-105">\<Uygulama ></span><span class="sxs-lookup"><span data-stu-id="af399-105">\<Application></span></span>](application-element-net-native.md)  
 <span data-ttu-id="af399-106">, Uygulama tarafından kullanılan tüm türlere çalışma zamanı yansıtma ilkesi uygular ve uygulama genelinde türler için bir kapsayıcı görevi görür ve meta verileri çalışma zamanında yansıma için kullanılabilir olan üyeleri yazın.</span><span class="sxs-lookup"><span data-stu-id="af399-106">Applies runtime reflection policy to all types used by the app, and serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="af399-107">Bu, [ \<yönergelerin >](directives-element-net-native.md) öğesinin bir alt öğesidir.</span><span class="sxs-lookup"><span data-stu-id="af399-107">This is a child of the [\<Directives>](directives-element-net-native.md) element.</span></span>  
  
 [<span data-ttu-id="af399-108">\<Bütünleştirilmiş kod ></span><span class="sxs-lookup"><span data-stu-id="af399-108">\<Assembly></span></span>](assembly-element-net-native.md)  
 <span data-ttu-id="af399-109">Çalışma zamanı ilkesini derlemedeki tüm türlere uygular.</span><span class="sxs-lookup"><span data-stu-id="af399-109">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="af399-110">Bu, [ \<uygulama >](application-element-net-native.md) ve [ \<kitaplık >](library-element-net-native.md) öğelerinin bir alt öğesidir.</span><span class="sxs-lookup"><span data-stu-id="af399-110">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="af399-111">\<Attribute></span><span class="sxs-lookup"><span data-stu-id="af399-111">\<AttributeImplies></span></span>](attributeimplies-element-net-native.md)  
 <span data-ttu-id="af399-112">Kapsayan tür > yönergesi bir öznitelik ise, bu özniteliğin uygulandığı kod öğelerine çalışma zamanı ilkesi uygular. [ \<](type-element-net-native.md)</span><span class="sxs-lookup"><span data-stu-id="af399-112">If its containing [\<Type>](type-element-net-native.md) directive is an attribute, applies runtime policy to code elements to which that attribute is applied.</span></span>  
  
 [<span data-ttu-id="af399-113">\<Yönergeler ></span><span class="sxs-lookup"><span data-stu-id="af399-113">\<Directives></span></span>](directives-element-net-native.md)  
 <span data-ttu-id="af399-114">.NET Native için her çalışma zamanı yönergeleri dosyasında kök öğe.</span><span class="sxs-lookup"><span data-stu-id="af399-114">The root element in every runtime directives file for .NET Native.</span></span> <span data-ttu-id="af399-115">Alt öğeleri [ \<uygulama >](application-element-net-native.md) ve [ \<kitaplık >](library-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="af399-115">Its child elements are [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md).</span></span>  
  
 [<span data-ttu-id="af399-116">\<Olay ></span><span class="sxs-lookup"><span data-stu-id="af399-116">\<Event></span></span>](event-element-net-native.md)  
 <span data-ttu-id="af399-117">Bir olaya çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="af399-117">Applies runtime policy to an event.</span></span> <span data-ttu-id="af399-118">Bu, [ \<türü >](type-element-net-native.md) ve [ \<typeörneklemesi >](typeinstantiation-element-net-native.md) öğeleri için bir alt öğesidir.</span><span class="sxs-lookup"><span data-stu-id="af399-118">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="af399-119">\<Alan ></span><span class="sxs-lookup"><span data-stu-id="af399-119">\<Field></span></span>](field-element-net-native.md)  
 <span data-ttu-id="af399-120">Çalışma zamanı ilkesini bir alana uygular.</span><span class="sxs-lookup"><span data-stu-id="af399-120">Applies runtime policy to a field.</span></span> <span data-ttu-id="af399-121">Bu, [ \<türü >](type-element-net-native.md) ve [ \<typeörneklemesi >](typeinstantiation-element-net-native.md) öğeleri için bir alt öğesidir.</span><span class="sxs-lookup"><span data-stu-id="af399-121">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="af399-122">\<GenericParameter ></span><span class="sxs-lookup"><span data-stu-id="af399-122">\<GenericParameter></span></span>](genericparameter-element-net-native.md)  
 <span data-ttu-id="af399-123">Bir genel türün veya yöntemin parametre türüne çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="af399-123">Applies runtime policy to the parameter type of a generic type or method.</span></span>  
  
 [<span data-ttu-id="af399-124">\<Impliestype ></span><span class="sxs-lookup"><span data-stu-id="af399-124">\<ImpliesType></span></span>](impliestype-element-net-native.md)  
 <span data-ttu-id="af399-125">Bu ilke kapsayan tür veya yönteme uygulanmışsa, bir türe çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="af399-125">Applies runtime policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
 [<span data-ttu-id="af399-126">\<Kitaplık ></span><span class="sxs-lookup"><span data-stu-id="af399-126">\<Library></span></span>](library-element-net-native.md)  
 <span data-ttu-id="af399-127">Çalışma zamanı ilkesini derlemedeki tüm türlere uygular.</span><span class="sxs-lookup"><span data-stu-id="af399-127">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="af399-128">Bu, [ \<uygulama >](application-element-net-native.md) ve [ \<kitaplık >](library-element-net-native.md) öğelerinin bir alt öğesidir.</span><span class="sxs-lookup"><span data-stu-id="af399-128">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="af399-129">\<Yöntem ></span><span class="sxs-lookup"><span data-stu-id="af399-129">\<Method></span></span>](method-element-net-native.md)  
 <span data-ttu-id="af399-130">Bir yönteme çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="af399-130">Applies runtime policy to a method.</span></span> <span data-ttu-id="af399-131">Bu, [ \<türü >](type-element-net-native.md) ve [ \<typeörneklemesi >](typeinstantiation-element-net-native.md) öğeleri için bir alt öğesidir.</span><span class="sxs-lookup"><span data-stu-id="af399-131">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="af399-132">\<Methodörneklemesi ></span><span class="sxs-lookup"><span data-stu-id="af399-132">\<MethodInstantiation></span></span>](methodinstantiation-element-net-native.md)  
 <span data-ttu-id="af399-133">Oluşturulan genel metoda çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="af399-133">Applies runtime policy to a constructed generic method.</span></span> <span data-ttu-id="af399-134">Bu, [ \<türü >](type-element-net-native.md) ve [ \<typeörneklemesi >](typeinstantiation-element-net-native.md) öğeleri için bir alt öğesidir.</span><span class="sxs-lookup"><span data-stu-id="af399-134">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="af399-135">\<Ad alanı ></span><span class="sxs-lookup"><span data-stu-id="af399-135">\<Namespace></span></span>](namespace-element-net-native.md)  
 <span data-ttu-id="af399-136">Çalışma alanı ilkesini bir ad alanındaki tüm türlere uygular.</span><span class="sxs-lookup"><span data-stu-id="af399-136">Applies runtime policy to all the types in a namespace.</span></span>  
  
 [<span data-ttu-id="af399-137">\<Parametre ></span><span class="sxs-lookup"><span data-stu-id="af399-137">\<Parameter></span></span>](parameter-element-net-native.md)  
 <span data-ttu-id="af399-138">Bir yönteme geçirilen bağımsız değişkenin türüne çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="af399-138">Applies runtime policy to the type of the argument passed to a method.</span></span>  
  
 [<span data-ttu-id="af399-139">\<Özellik ></span><span class="sxs-lookup"><span data-stu-id="af399-139">\<Property></span></span>](property-element-net-native.md)  
 <span data-ttu-id="af399-140">Çalışma zamanı ilkesini bir özelliğe uygular.</span><span class="sxs-lookup"><span data-stu-id="af399-140">Applies runtime policy to a property.</span></span> <span data-ttu-id="af399-141">Bu, [ \<türü >](type-element-net-native.md) ve [ \<typeörneklemesi >](typeinstantiation-element-net-native.md) öğeleri için bir alt öğesidir.</span><span class="sxs-lookup"><span data-stu-id="af399-141">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="af399-142">\<Alt türler ></span><span class="sxs-lookup"><span data-stu-id="af399-142">\<Subtypes></span></span>](subtypes-element-net-native.md)  
 <span data-ttu-id="af399-143">Çalışma zamanı ilkesini, kapsayan türden devralınan tüm sınıflara uygular.</span><span class="sxs-lookup"><span data-stu-id="af399-143">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
 [<span data-ttu-id="af399-144">\<Tür ></span><span class="sxs-lookup"><span data-stu-id="af399-144">\<Type></span></span>](type-element-net-native.md)  
 <span data-ttu-id="af399-145">Bir türe çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="af399-145">Applies runtime policy to a type.</span></span>  
  
 [<span data-ttu-id="af399-146">\<Typeörneklemesi ></span><span class="sxs-lookup"><span data-stu-id="af399-146">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)  
 <span data-ttu-id="af399-147">Oluşturulan genel bir türe çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="af399-147">Applies runtime policy to a constructed generic type.</span></span>  
  
 [<span data-ttu-id="af399-148">\<TypeParameter ></span><span class="sxs-lookup"><span data-stu-id="af399-148">\<TypeParameter></span></span>](typeparameter-element-net-native.md)  
 <span data-ttu-id="af399-149">Yönteme geçirilen bir <xref:System.Type> bağımsız değişkenle temsil edilen türe çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="af399-149">Applies runtime policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af399-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af399-150">See also</span></span>

- [<span data-ttu-id="af399-151">RD. xml yapılandırma dosyası başvurusu</span><span class="sxs-lookup"><span data-stu-id="af399-151">rd.xml Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
