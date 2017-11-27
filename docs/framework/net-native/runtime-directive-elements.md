---
title: "Çalışma Zamanı Yönerge Öğeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3143c6b78749f3339e7e7195b551b5a5c31fad12
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="runtime-directive-elements"></a><span data-ttu-id="b45df-102">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="b45df-102">Runtime Directive Elements</span></span>
<span data-ttu-id="b45df-103">Çalışma zamanı yönergeleri (rd.xml) dosya biçimi şu çalışma zamanı yönerge öğeleri destekler.</span><span class="sxs-lookup"><span data-stu-id="b45df-103">The runtime directives (rd.xml) file format supports the following runtime directive elements.</span></span> <span data-ttu-id="b45df-104">Bkz: [çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) hiyerarşik bir gösterim için.</span><span class="sxs-lookup"><span data-stu-id="b45df-104">See [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) for a hierarchical representation.</span></span>  
  
 [<span data-ttu-id="b45df-105">\<Uygulama ></span><span class="sxs-lookup"><span data-stu-id="b45df-105">\<Application></span></span>](../../../docs/framework/net-native/application-element-net-native.md)  
 <span data-ttu-id="b45df-106">Çalışma zamanı yansıma ilke uygulama tarafından kullanılan tüm türleri için geçerlidir ve uygulama genelinde türleri ve tür üyeleri olan meta verilerini yansıma çalışma zamanında yüklenebilir için kapsayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="b45df-106">Applies runtime reflection policy to all types used by the app, and serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="b45df-107">Bu bir alt öğesi değil [ \<yönergeleri >](../../../docs/framework/net-native/directives-element-net-native.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="b45df-107">This is a child of the [\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md) element.</span></span>  
  
 [<span data-ttu-id="b45df-108">\<Derleme ></span><span class="sxs-lookup"><span data-stu-id="b45df-108">\<Assembly></span></span>](../../../docs/framework/net-native/assembly-element-net-native.md)  
 <span data-ttu-id="b45df-109">Derlemedeki tüm türleri runnntime ilke uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b45df-109">Applies runnntime policy to all the types in an assembly.</span></span> <span data-ttu-id="b45df-110">Bu bir alt öğesi değil [ \<uygulama >](../../../docs/framework/net-native/application-element-net-native.md) ve [ \<kitaplığı >](../../../docs/framework/net-native/library-element-net-native.md) öğeleri.</span><span class="sxs-lookup"><span data-stu-id="b45df-110">This is a child of the [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) and [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="b45df-111">\<Attributeımplies ></span><span class="sxs-lookup"><span data-stu-id="b45df-111">\<AttributeImplies></span></span>](../../../docs/framework/net-native/attributeimplies-element-net-native.md)  
 <span data-ttu-id="b45df-112">Varsa, içeren [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) yönergesi bir özniteliktir, çalışma zamanı İlkesi bu öznitelik uygulanan kod öğelere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b45df-112">If its containing [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) directive is an attribute, applies runtime policy to code elements to which that attribute is applied.</span></span>  
  
 [<span data-ttu-id="b45df-113">\<Yönergeleri ></span><span class="sxs-lookup"><span data-stu-id="b45df-113">\<Directives></span></span>](../../../docs/framework/net-native/directives-element-net-native.md)  
 <span data-ttu-id="b45df-114">Her çalışma zamanı yönergeleri dosyasının kök öğesinin [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b45df-114">The root element in every runtime directives file for [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="b45df-115">Alt öğeleri olan [ \<uygulama >](../../../docs/framework/net-native/application-element-net-native.md) ve [ \<kitaplığı >](../../../docs/framework/net-native/library-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="b45df-115">Its child elements are [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) and [\<Library>](../../../docs/framework/net-native/library-element-net-native.md).</span></span>  
  
 [<span data-ttu-id="b45df-116">\<Olay ></span><span class="sxs-lookup"><span data-stu-id="b45df-116">\<Event></span></span>](../../../docs/framework/net-native/event-element-net-native.md)  
 <span data-ttu-id="b45df-117">Çalışma zamanı İlkesi bir olay için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b45df-117">Applies runtime policy to an event.</span></span> <span data-ttu-id="b45df-118">Bu bir alt öğesi değil [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) ve [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğeleri.</span><span class="sxs-lookup"><span data-stu-id="b45df-118">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="b45df-119">\<Alanı ></span><span class="sxs-lookup"><span data-stu-id="b45df-119">\<Field></span></span>](../../../docs/framework/net-native/field-element-net-native.md)  
 <span data-ttu-id="b45df-120">Çalışma zamanı İlkesi bir alan için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b45df-120">Applies runtime policy to a field.</span></span> <span data-ttu-id="b45df-121">Bu bir alt öğesi değil [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) ve [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğeleri.</span><span class="sxs-lookup"><span data-stu-id="b45df-121">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="b45df-122">\<GenericParameter ></span><span class="sxs-lookup"><span data-stu-id="b45df-122">\<GenericParameter></span></span>](../../../docs/framework/net-native/genericparameter-element-net-native.md)  
 <span data-ttu-id="b45df-123">Çalışma zamanı İlkesi genel türü veya yöntemi parametresinin türü için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b45df-123">Applies runtime policy to the parameter type of a generic type or method.</span></span>  
  
 [<span data-ttu-id="b45df-124">\<Impliestype ></span><span class="sxs-lookup"><span data-stu-id="b45df-124">\<ImpliesType></span></span>](../../../docs/framework/net-native/impliestype-element-net-native.md)  
 <span data-ttu-id="b45df-125">Bu ilkeyi içeren türü veya yöntemi uygulanmışsa, çalışma zamanı İlkesi bir türü için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b45df-125">Applies runtime policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
 [<span data-ttu-id="b45df-126">\<Kitaplık ></span><span class="sxs-lookup"><span data-stu-id="b45df-126">\<Library></span></span>](../../../docs/framework/net-native/library-element-net-native.md)  
 <span data-ttu-id="b45df-127">Çalışma zamanı İlkesi derleme içindeki tüm türler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b45df-127">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="b45df-128">Bu bir alt öğesi değil [ \<uygulama >](../../../docs/framework/net-native/application-element-net-native.md) ve [ \<kitaplığı >](../../../docs/framework/net-native/library-element-net-native.md) öğeleri.</span><span class="sxs-lookup"><span data-stu-id="b45df-128">This is a child of the [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) and [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="b45df-129">\<Yöntem ></span><span class="sxs-lookup"><span data-stu-id="b45df-129">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)  
 <span data-ttu-id="b45df-130">Çalışma zamanı ilke için bir yöntem uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b45df-130">Applies runtime policy to a method.</span></span> <span data-ttu-id="b45df-131">Bu bir alt öğesi değil [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) ve [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğeleri.</span><span class="sxs-lookup"><span data-stu-id="b45df-131">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="b45df-132">\<Methodınstantiation ></span><span class="sxs-lookup"><span data-stu-id="b45df-132">\<MethodInstantiation></span></span>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)  
 <span data-ttu-id="b45df-133">Çalışma zamanı İlkesi oluşturulan genel yöntem için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b45df-133">Applies runtime policy to a constructed generic method.</span></span> <span data-ttu-id="b45df-134">Bu bir alt öğesi değil [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) ve [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğeleri.</span><span class="sxs-lookup"><span data-stu-id="b45df-134">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="b45df-135">\<Namespace ></span><span class="sxs-lookup"><span data-stu-id="b45df-135">\<Namespace></span></span>](../../../docs/framework/net-native/namespace-element-net-native.md)  
 <span data-ttu-id="b45df-136">Çalışma zamanı İlkesi, bir ad alanı içindeki tüm türler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b45df-136">Applies runtime policy to all the types in a namespace.</span></span>  
  
 [<span data-ttu-id="b45df-137">\<Parametresi ></span><span class="sxs-lookup"><span data-stu-id="b45df-137">\<Parameter></span></span>](../../../docs/framework/net-native/parameter-element-net-native.md)  
 <span data-ttu-id="b45df-138">Çalışma zamanı İlkesi bir yönteme geçirilen bağımsız değişken türü için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b45df-138">Applies runtime policy to the type of the argument passed to a method.</span></span>  
  
 [<span data-ttu-id="b45df-139">\<Özellik ></span><span class="sxs-lookup"><span data-stu-id="b45df-139">\<Property></span></span>](../../../docs/framework/net-native/property-element-net-native.md)  
 <span data-ttu-id="b45df-140">Çalışma zamanı İlkesi bir özellik için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b45df-140">Applies runtime policy to a property.</span></span> <span data-ttu-id="b45df-141">Bu bir alt öğesi değil [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) ve [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğeleri.</span><span class="sxs-lookup"><span data-stu-id="b45df-141">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="b45df-142">\<Subtypes ></span><span class="sxs-lookup"><span data-stu-id="b45df-142">\<Subtypes></span></span>](../../../docs/framework/net-native/subtypes-element-net-native.md)  
 <span data-ttu-id="b45df-143">Çalışma zamanı ilkesi içeren türünden devralınan tüm sınıflar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b45df-143">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
 [<span data-ttu-id="b45df-144">\<Türü ></span><span class="sxs-lookup"><span data-stu-id="b45df-144">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)  
 <span data-ttu-id="b45df-145">Çalışma zamanı ilke türü için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b45df-145">Applies runtime policy to a type.</span></span>  
  
 [<span data-ttu-id="b45df-146">\<Typeınstantiation ></span><span class="sxs-lookup"><span data-stu-id="b45df-146">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)  
 <span data-ttu-id="b45df-147">Çalışma zamanı İlkesi oluşturulmuş bir genel türü için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b45df-147">Applies runtime policy to a constructed generic type.</span></span>  
  
 [<span data-ttu-id="b45df-148">\<TypeParameter ></span><span class="sxs-lookup"><span data-stu-id="b45df-148">\<TypeParameter></span></span>](../../../docs/framework/net-native/typeparameter-element-net-native.md)  
 <span data-ttu-id="b45df-149">Tarafından temsil edilen türü çalışma zamanı ilkenin uygulandığı bir <xref:System.Type> yöntemi için bağımsız değişken geçirildi.</span><span class="sxs-lookup"><span data-stu-id="b45df-149">Applies runtime policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b45df-150">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b45df-150">See Also</span></span>  
 [<span data-ttu-id="b45df-151">RD.XML yapılandırma dosyası başvurusu</span><span class="sxs-lookup"><span data-stu-id="b45df-151">rd.xml Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
