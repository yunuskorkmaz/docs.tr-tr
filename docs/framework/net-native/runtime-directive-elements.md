---
title: Çalışma Zamanı Yönerge Öğeleri
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
ms.openlocfilehash: c900516382c8e526a6b0021bb2b681486283f3ab
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128164"
---
# <a name="runtime-directive-elements"></a><span data-ttu-id="13e10-102">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="13e10-102">Runtime Directive Elements</span></span>
<span data-ttu-id="13e10-103">Çalışma zamanı yönergeleri (RD. xml) dosya biçimi aşağıdaki çalışma zamanı yönerge öğelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="13e10-103">The runtime directives (rd.xml) file format supports the following runtime directive elements.</span></span> <span data-ttu-id="13e10-104">Hiyerarşik bir gösterim için bkz. [çalışma zamanı yönergeleri (RD. xml) yapılandırma dosyası başvurusu](runtime-directives-rd-xml-configuration-file-reference.md) .</span><span class="sxs-lookup"><span data-stu-id="13e10-104">See [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md) for a hierarchical representation.</span></span>  
  
 [<span data-ttu-id="13e10-105">\<uygulama ></span><span class="sxs-lookup"><span data-stu-id="13e10-105">\<Application></span></span>](application-element-net-native.md)  
 <span data-ttu-id="13e10-106">, Uygulama tarafından kullanılan tüm türlere çalışma zamanı yansıtma ilkesi uygular ve uygulama genelinde türler için bir kapsayıcı görevi görür ve meta verileri çalışma zamanında yansıma için kullanılabilir olan üyeleri yazın.</span><span class="sxs-lookup"><span data-stu-id="13e10-106">Applies runtime reflection policy to all types used by the app, and serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="13e10-107">Bu, [\<yönergelerinin >](directives-element-net-native.md) öğesinin bir alt öğesidir.</span><span class="sxs-lookup"><span data-stu-id="13e10-107">This is a child of the [\<Directives>](directives-element-net-native.md) element.</span></span>  
  
 [<span data-ttu-id="13e10-108">Derleme > \<</span><span class="sxs-lookup"><span data-stu-id="13e10-108">\<Assembly></span></span>](assembly-element-net-native.md)  
 <span data-ttu-id="13e10-109">Çalışma zamanı ilkesini derlemedeki tüm türlere uygular.</span><span class="sxs-lookup"><span data-stu-id="13e10-109">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="13e10-110">Bu, [\<uygulama >](application-element-net-native.md) ve [\<kitaplığı >](library-element-net-native.md) öğelerinin bir alt öğesidir.</span><span class="sxs-lookup"><span data-stu-id="13e10-110">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="13e10-111">\<Attribute></span><span class="sxs-lookup"><span data-stu-id="13e10-111">\<AttributeImplies></span></span>](attributeimplies-element-net-native.md)  
 <span data-ttu-id="13e10-112">Kendi kapsayıcı [\<türü >](type-element-net-native.md) yönergesi bir öznitelik ise, bu özniteliğin uygulandığı kod öğelerine çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="13e10-112">If its containing [\<Type>](type-element-net-native.md) directive is an attribute, applies runtime policy to code elements to which that attribute is applied.</span></span>  
  
 [<span data-ttu-id="13e10-113">\<yönergeler ></span><span class="sxs-lookup"><span data-stu-id="13e10-113">\<Directives></span></span>](directives-element-net-native.md)  
 <span data-ttu-id="13e10-114">.NET Native için her çalışma zamanı yönergeleri dosyasında kök öğe.</span><span class="sxs-lookup"><span data-stu-id="13e10-114">The root element in every runtime directives file for .NET Native.</span></span> <span data-ttu-id="13e10-115">Alt öğeleri [\<uygulama >](application-element-net-native.md) ve [\<kitaplığı >](library-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="13e10-115">Its child elements are [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md).</span></span>  
  
 [<span data-ttu-id="13e10-116">\<olayı ></span><span class="sxs-lookup"><span data-stu-id="13e10-116">\<Event></span></span>](event-element-net-native.md)  
 <span data-ttu-id="13e10-117">Bir olaya çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="13e10-117">Applies runtime policy to an event.</span></span> <span data-ttu-id="13e10-118">Bu, [\<türü >](type-element-net-native.md) ve [\<typeörneklemesi >](typeinstantiation-element-net-native.md) öğeleri için bir alt öğesidir.</span><span class="sxs-lookup"><span data-stu-id="13e10-118">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="13e10-119">\<alan ></span><span class="sxs-lookup"><span data-stu-id="13e10-119">\<Field></span></span>](field-element-net-native.md)  
 <span data-ttu-id="13e10-120">Çalışma zamanı ilkesini bir alana uygular.</span><span class="sxs-lookup"><span data-stu-id="13e10-120">Applies runtime policy to a field.</span></span> <span data-ttu-id="13e10-121">Bu, [\<türü >](type-element-net-native.md) ve [\<typeörneklemesi >](typeinstantiation-element-net-native.md) öğeleri için bir alt öğesidir.</span><span class="sxs-lookup"><span data-stu-id="13e10-121">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="13e10-122">\<GenericParameter ></span><span class="sxs-lookup"><span data-stu-id="13e10-122">\<GenericParameter></span></span>](genericparameter-element-net-native.md)  
 <span data-ttu-id="13e10-123">Bir genel türün veya yöntemin parametre türüne çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="13e10-123">Applies runtime policy to the parameter type of a generic type or method.</span></span>  
  
 [<span data-ttu-id="13e10-124">\<ımpliestype ></span><span class="sxs-lookup"><span data-stu-id="13e10-124">\<ImpliesType></span></span>](impliestype-element-net-native.md)  
 <span data-ttu-id="13e10-125">Bu ilke kapsayan tür veya yönteme uygulanmışsa, bir türe çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="13e10-125">Applies runtime policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
 [<span data-ttu-id="13e10-126">\<kitaplığı ></span><span class="sxs-lookup"><span data-stu-id="13e10-126">\<Library></span></span>](library-element-net-native.md)  
 <span data-ttu-id="13e10-127">Çalışma zamanı ilkesini derlemedeki tüm türlere uygular.</span><span class="sxs-lookup"><span data-stu-id="13e10-127">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="13e10-128">Bu, [\<uygulama >](application-element-net-native.md) ve [\<kitaplığı >](library-element-net-native.md) öğelerinin bir alt öğesidir.</span><span class="sxs-lookup"><span data-stu-id="13e10-128">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="13e10-129">\<yöntemi ></span><span class="sxs-lookup"><span data-stu-id="13e10-129">\<Method></span></span>](method-element-net-native.md)  
 <span data-ttu-id="13e10-130">Bir yönteme çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="13e10-130">Applies runtime policy to a method.</span></span> <span data-ttu-id="13e10-131">Bu, [\<türü >](type-element-net-native.md) ve [\<typeörneklemesi >](typeinstantiation-element-net-native.md) öğeleri için bir alt öğesidir.</span><span class="sxs-lookup"><span data-stu-id="13e10-131">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="13e10-132">\<Methodörneklemesi ></span><span class="sxs-lookup"><span data-stu-id="13e10-132">\<MethodInstantiation></span></span>](methodinstantiation-element-net-native.md)  
 <span data-ttu-id="13e10-133">Oluşturulan genel metoda çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="13e10-133">Applies runtime policy to a constructed generic method.</span></span> <span data-ttu-id="13e10-134">Bu, [\<türü >](type-element-net-native.md) ve [\<typeörneklemesi >](typeinstantiation-element-net-native.md) öğeleri için bir alt öğesidir.</span><span class="sxs-lookup"><span data-stu-id="13e10-134">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="13e10-135">\<ad alanı ></span><span class="sxs-lookup"><span data-stu-id="13e10-135">\<Namespace></span></span>](namespace-element-net-native.md)  
 <span data-ttu-id="13e10-136">Çalışma alanı ilkesini bir ad alanındaki tüm türlere uygular.</span><span class="sxs-lookup"><span data-stu-id="13e10-136">Applies runtime policy to all the types in a namespace.</span></span>  
  
 [<span data-ttu-id="13e10-137">\<parametresi ></span><span class="sxs-lookup"><span data-stu-id="13e10-137">\<Parameter></span></span>](parameter-element-net-native.md)  
 <span data-ttu-id="13e10-138">Bir yönteme geçirilen bağımsız değişkenin türüne çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="13e10-138">Applies runtime policy to the type of the argument passed to a method.</span></span>  
  
 [<span data-ttu-id="13e10-139">\<Özellik ></span><span class="sxs-lookup"><span data-stu-id="13e10-139">\<Property></span></span>](property-element-net-native.md)  
 <span data-ttu-id="13e10-140">Çalışma zamanı ilkesini bir özelliğe uygular.</span><span class="sxs-lookup"><span data-stu-id="13e10-140">Applies runtime policy to a property.</span></span> <span data-ttu-id="13e10-141">Bu, [\<türü >](type-element-net-native.md) ve [\<typeörneklemesi >](typeinstantiation-element-net-native.md) öğeleri için bir alt öğesidir.</span><span class="sxs-lookup"><span data-stu-id="13e10-141">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="13e10-142">\<alt türleri ></span><span class="sxs-lookup"><span data-stu-id="13e10-142">\<Subtypes></span></span>](subtypes-element-net-native.md)  
 <span data-ttu-id="13e10-143">Çalışma zamanı ilkesini, kapsayan türden devralınan tüm sınıflara uygular.</span><span class="sxs-lookup"><span data-stu-id="13e10-143">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
 [<span data-ttu-id="13e10-144">\<türü ></span><span class="sxs-lookup"><span data-stu-id="13e10-144">\<Type></span></span>](type-element-net-native.md)  
 <span data-ttu-id="13e10-145">Bir türe çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="13e10-145">Applies runtime policy to a type.</span></span>  
  
 [<span data-ttu-id="13e10-146">\<Typeörneklemesi ></span><span class="sxs-lookup"><span data-stu-id="13e10-146">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)  
 <span data-ttu-id="13e10-147">Oluşturulan genel bir türe çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="13e10-147">Applies runtime policy to a constructed generic type.</span></span>  
  
 [<span data-ttu-id="13e10-148">\<TypeParameter ></span><span class="sxs-lookup"><span data-stu-id="13e10-148">\<TypeParameter></span></span>](typeparameter-element-net-native.md)  
 <span data-ttu-id="13e10-149">Bir yönteme geçirilen <xref:System.Type> bağımsız değişkeniyle temsil edilen türe çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="13e10-149">Applies runtime policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13e10-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13e10-150">See also</span></span>

- [<span data-ttu-id="13e10-151">RD. xml yapılandırma dosyası başvurusu</span><span class="sxs-lookup"><span data-stu-id="13e10-151">rd.xml Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
