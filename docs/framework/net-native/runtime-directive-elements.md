---
description: 'Daha fazla bilgi edinin: çalışma zamanı yönerge öğeleri'
title: Çalışma Zamanı Yönerge Öğeleri
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
ms.openlocfilehash: 74ff6c7d782f48106e37b99187770d8e82926be4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738435"
---
# <a name="runtime-directive-elements"></a><span data-ttu-id="28149-103">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="28149-103">Runtime Directive Elements</span></span>

<span data-ttu-id="28149-104">Çalışma zamanı yönergeleri (rd.xml) dosya biçimi aşağıdaki çalışma zamanı yönerge öğelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="28149-104">The runtime directives (rd.xml) file format supports the following runtime directive elements.</span></span> <span data-ttu-id="28149-105">Hiyerarşik bir gösterim için bkz. [çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](runtime-directives-rd-xml-configuration-file-reference.md) .</span><span class="sxs-lookup"><span data-stu-id="28149-105">See [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md) for a hierarchical representation.</span></span>  
  
 [\<Application>](application-element-net-native.md)  
 <span data-ttu-id="28149-106">, Uygulama tarafından kullanılan tüm türlere çalışma zamanı yansıtma ilkesi uygular ve uygulama genelinde türler için bir kapsayıcı görevi görür ve meta verileri çalışma zamanında yansıma için kullanılabilir olan üyeleri yazın.</span><span class="sxs-lookup"><span data-stu-id="28149-106">Applies runtime reflection policy to all types used by the app, and serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="28149-107">Bu, öğesinin bir alt [\<Directives>](directives-element-net-native.md) öğesidir.</span><span class="sxs-lookup"><span data-stu-id="28149-107">This is a child of the [\<Directives>](directives-element-net-native.md) element.</span></span>  
  
 [\<Assembly>](assembly-element-net-native.md)  
 <span data-ttu-id="28149-108">Çalışma zamanı ilkesini derlemedeki tüm türlere uygular.</span><span class="sxs-lookup"><span data-stu-id="28149-108">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="28149-109">Bu, ve öğelerinin bir alt [\<Application>](application-element-net-native.md) öğesidir [\<Library>](library-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="28149-109">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [\<AttributeImplies>](attributeimplies-element-net-native.md)  
 <span data-ttu-id="28149-110">Kapsayan [\<Type>](type-element-net-native.md) yönergesi bir öznitelik ise, bu özniteliğin uygulandığı kod öğelerine çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="28149-110">If its containing [\<Type>](type-element-net-native.md) directive is an attribute, applies runtime policy to code elements to which that attribute is applied.</span></span>  
  
 [\<Directives>](directives-element-net-native.md)  
 <span data-ttu-id="28149-111">.NET Native için her çalışma zamanı yönergeleri dosyasında kök öğe.</span><span class="sxs-lookup"><span data-stu-id="28149-111">The root element in every runtime directives file for .NET Native.</span></span> <span data-ttu-id="28149-112">Alt öğeleri [\<Application>](application-element-net-native.md) ve ' dir [\<Library>](library-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="28149-112">Its child elements are [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md).</span></span>  
  
 [\<Event>](event-element-net-native.md)  
 <span data-ttu-id="28149-113">Bir olaya çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="28149-113">Applies runtime policy to an event.</span></span> <span data-ttu-id="28149-114">Bu, ve öğelerinin bir alt [\<Type>](type-element-net-native.md) öğesidir [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="28149-114">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<Field>](field-element-net-native.md)  
 <span data-ttu-id="28149-115">Çalışma zamanı ilkesini bir alana uygular.</span><span class="sxs-lookup"><span data-stu-id="28149-115">Applies runtime policy to a field.</span></span> <span data-ttu-id="28149-116">Bu, ve öğelerinin bir alt [\<Type>](type-element-net-native.md) öğesidir [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="28149-116">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<GenericParameter>](genericparameter-element-net-native.md)  
 <span data-ttu-id="28149-117">Bir genel türün veya yöntemin parametre türüne çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="28149-117">Applies runtime policy to the parameter type of a generic type or method.</span></span>  
  
 [\<ImpliesType>](impliestype-element-net-native.md)  
 <span data-ttu-id="28149-118">Bu ilke kapsayan tür veya yönteme uygulanmışsa, bir türe çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="28149-118">Applies runtime policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
 [\<Library>](library-element-net-native.md)  
 <span data-ttu-id="28149-119">Çalışma zamanı ilkesini derlemedeki tüm türlere uygular.</span><span class="sxs-lookup"><span data-stu-id="28149-119">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="28149-120">Bu, ve öğelerinin bir alt [\<Application>](application-element-net-native.md) öğesidir [\<Library>](library-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="28149-120">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [\<Method>](method-element-net-native.md)  
 <span data-ttu-id="28149-121">Bir yönteme çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="28149-121">Applies runtime policy to a method.</span></span> <span data-ttu-id="28149-122">Bu, ve öğelerinin bir alt [\<Type>](type-element-net-native.md) öğesidir [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="28149-122">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<MethodInstantiation>](methodinstantiation-element-net-native.md)  
 <span data-ttu-id="28149-123">Oluşturulan genel metoda çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="28149-123">Applies runtime policy to a constructed generic method.</span></span> <span data-ttu-id="28149-124">Bu, ve öğelerinin bir alt [\<Type>](type-element-net-native.md) öğesidir [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="28149-124">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<Namespace>](namespace-element-net-native.md)  
 <span data-ttu-id="28149-125">Çalışma alanı ilkesini bir ad alanındaki tüm türlere uygular.</span><span class="sxs-lookup"><span data-stu-id="28149-125">Applies runtime policy to all the types in a namespace.</span></span>  
  
 [\<Parameter>](parameter-element-net-native.md)  
 <span data-ttu-id="28149-126">Bir yönteme geçirilen bağımsız değişkenin türüne çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="28149-126">Applies runtime policy to the type of the argument passed to a method.</span></span>  
  
 [\<Property>](property-element-net-native.md)  
 <span data-ttu-id="28149-127">Çalışma zamanı ilkesini bir özelliğe uygular.</span><span class="sxs-lookup"><span data-stu-id="28149-127">Applies runtime policy to a property.</span></span> <span data-ttu-id="28149-128">Bu, ve öğelerinin bir alt [\<Type>](type-element-net-native.md) öğesidir [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="28149-128">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<Subtypes>](subtypes-element-net-native.md)  
 <span data-ttu-id="28149-129">Çalışma zamanı ilkesini, kapsayan türden devralınan tüm sınıflara uygular.</span><span class="sxs-lookup"><span data-stu-id="28149-129">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
 [\<Type>](type-element-net-native.md)  
 <span data-ttu-id="28149-130">Bir türe çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="28149-130">Applies runtime policy to a type.</span></span>  
  
 [\<TypeInstantiation>](typeinstantiation-element-net-native.md)  
 <span data-ttu-id="28149-131">Oluşturulan genel bir türe çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="28149-131">Applies runtime policy to a constructed generic type.</span></span>  
  
 [\<TypeParameter>](typeparameter-element-net-native.md)  
 <span data-ttu-id="28149-132">Yönteme geçirilen bir bağımsız değişkenle temsil edilen türe çalışma zamanı ilkesi uygular <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="28149-132">Applies runtime policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28149-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28149-133">See also</span></span>

- [<span data-ttu-id="28149-134"> Yapılandırma dosyası başvurusunurd.xml</span><span class="sxs-lookup"><span data-stu-id="28149-134">rd.xml Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
