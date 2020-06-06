---
title: Çalışma Zamanı Yönerge Öğeleri
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
ms.openlocfilehash: c900516382c8e526a6b0021bb2b681486283f3ab
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128164"
---
# <a name="runtime-directive-elements"></a><span data-ttu-id="0adc3-102">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="0adc3-102">Runtime Directive Elements</span></span>
<span data-ttu-id="0adc3-103">Çalışma zamanı yönergeleri (RD. xml) dosya biçimi aşağıdaki çalışma zamanı yönerge öğelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="0adc3-103">The runtime directives (rd.xml) file format supports the following runtime directive elements.</span></span> <span data-ttu-id="0adc3-104">Hiyerarşik bir gösterim için bkz. [çalışma zamanı yönergeleri (RD. xml) yapılandırma dosyası başvurusu](runtime-directives-rd-xml-configuration-file-reference.md) .</span><span class="sxs-lookup"><span data-stu-id="0adc3-104">See [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md) for a hierarchical representation.</span></span>  
  
 [\<Application>](application-element-net-native.md)  
 <span data-ttu-id="0adc3-105">, Uygulama tarafından kullanılan tüm türlere çalışma zamanı yansıtma ilkesi uygular ve uygulama genelinde türler için bir kapsayıcı görevi görür ve meta verileri çalışma zamanında yansıma için kullanılabilir olan üyeleri yazın.</span><span class="sxs-lookup"><span data-stu-id="0adc3-105">Applies runtime reflection policy to all types used by the app, and serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="0adc3-106">Bu, öğesinin bir alt [\<Directives>](directives-element-net-native.md) öğesidir.</span><span class="sxs-lookup"><span data-stu-id="0adc3-106">This is a child of the [\<Directives>](directives-element-net-native.md) element.</span></span>  
  
 [\<Assembly>](assembly-element-net-native.md)  
 <span data-ttu-id="0adc3-107">Çalışma zamanı ilkesini derlemedeki tüm türlere uygular.</span><span class="sxs-lookup"><span data-stu-id="0adc3-107">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="0adc3-108">Bu, ve öğelerinin bir alt [\<Application>](application-element-net-native.md) öğesidir [\<Library>](library-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="0adc3-108">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [\<AttributeImplies>](attributeimplies-element-net-native.md)  
 <span data-ttu-id="0adc3-109">Kapsayan [\<Type>](type-element-net-native.md) yönergesi bir öznitelik ise, bu özniteliğin uygulandığı kod öğelerine çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="0adc3-109">If its containing [\<Type>](type-element-net-native.md) directive is an attribute, applies runtime policy to code elements to which that attribute is applied.</span></span>  
  
 [\<Directives>](directives-element-net-native.md)  
 <span data-ttu-id="0adc3-110">.NET Native için her çalışma zamanı yönergeleri dosyasında kök öğe.</span><span class="sxs-lookup"><span data-stu-id="0adc3-110">The root element in every runtime directives file for .NET Native.</span></span> <span data-ttu-id="0adc3-111">Alt öğeleri [\<Application>](application-element-net-native.md) ve ' dir [\<Library>](library-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="0adc3-111">Its child elements are [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md).</span></span>  
  
 [\<Event>](event-element-net-native.md)  
 <span data-ttu-id="0adc3-112">Bir olaya çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="0adc3-112">Applies runtime policy to an event.</span></span> <span data-ttu-id="0adc3-113">Bu, ve öğelerinin bir alt [\<Type>](type-element-net-native.md) öğesidir [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="0adc3-113">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<Field>](field-element-net-native.md)  
 <span data-ttu-id="0adc3-114">Çalışma zamanı ilkesini bir alana uygular.</span><span class="sxs-lookup"><span data-stu-id="0adc3-114">Applies runtime policy to a field.</span></span> <span data-ttu-id="0adc3-115">Bu, ve öğelerinin bir alt [\<Type>](type-element-net-native.md) öğesidir [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="0adc3-115">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<GenericParameter>](genericparameter-element-net-native.md)  
 <span data-ttu-id="0adc3-116">Bir genel türün veya yöntemin parametre türüne çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="0adc3-116">Applies runtime policy to the parameter type of a generic type or method.</span></span>  
  
 [\<ImpliesType>](impliestype-element-net-native.md)  
 <span data-ttu-id="0adc3-117">Bu ilke kapsayan tür veya yönteme uygulanmışsa, bir türe çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="0adc3-117">Applies runtime policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
 [\<Library>](library-element-net-native.md)  
 <span data-ttu-id="0adc3-118">Çalışma zamanı ilkesini derlemedeki tüm türlere uygular.</span><span class="sxs-lookup"><span data-stu-id="0adc3-118">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="0adc3-119">Bu, ve öğelerinin bir alt [\<Application>](application-element-net-native.md) öğesidir [\<Library>](library-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="0adc3-119">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [\<Method>](method-element-net-native.md)  
 <span data-ttu-id="0adc3-120">Bir yönteme çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="0adc3-120">Applies runtime policy to a method.</span></span> <span data-ttu-id="0adc3-121">Bu, ve öğelerinin bir alt [\<Type>](type-element-net-native.md) öğesidir [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="0adc3-121">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<MethodInstantiation>](methodinstantiation-element-net-native.md)  
 <span data-ttu-id="0adc3-122">Oluşturulan genel metoda çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="0adc3-122">Applies runtime policy to a constructed generic method.</span></span> <span data-ttu-id="0adc3-123">Bu, ve öğelerinin bir alt [\<Type>](type-element-net-native.md) öğesidir [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="0adc3-123">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<Namespace>](namespace-element-net-native.md)  
 <span data-ttu-id="0adc3-124">Çalışma alanı ilkesini bir ad alanındaki tüm türlere uygular.</span><span class="sxs-lookup"><span data-stu-id="0adc3-124">Applies runtime policy to all the types in a namespace.</span></span>  
  
 [\<Parameter>](parameter-element-net-native.md)  
 <span data-ttu-id="0adc3-125">Bir yönteme geçirilen bağımsız değişkenin türüne çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="0adc3-125">Applies runtime policy to the type of the argument passed to a method.</span></span>  
  
 [\<Property>](property-element-net-native.md)  
 <span data-ttu-id="0adc3-126">Çalışma zamanı ilkesini bir özelliğe uygular.</span><span class="sxs-lookup"><span data-stu-id="0adc3-126">Applies runtime policy to a property.</span></span> <span data-ttu-id="0adc3-127">Bu, ve öğelerinin bir alt [\<Type>](type-element-net-native.md) öğesidir [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="0adc3-127">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<Subtypes>](subtypes-element-net-native.md)  
 <span data-ttu-id="0adc3-128">Çalışma zamanı ilkesini, kapsayan türden devralınan tüm sınıflara uygular.</span><span class="sxs-lookup"><span data-stu-id="0adc3-128">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
 [\<Type>](type-element-net-native.md)  
 <span data-ttu-id="0adc3-129">Bir türe çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="0adc3-129">Applies runtime policy to a type.</span></span>  
  
 [\<TypeInstantiation>](typeinstantiation-element-net-native.md)  
 <span data-ttu-id="0adc3-130">Oluşturulan genel bir türe çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="0adc3-130">Applies runtime policy to a constructed generic type.</span></span>  
  
 [\<TypeParameter>](typeparameter-element-net-native.md)  
 <span data-ttu-id="0adc3-131">Yönteme geçirilen bir bağımsız değişkenle temsil edilen türe çalışma zamanı ilkesi uygular <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="0adc3-131">Applies runtime policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0adc3-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0adc3-132">See also</span></span>

- [<span data-ttu-id="0adc3-133">RD. xml yapılandırma dosyası başvurusu</span><span class="sxs-lookup"><span data-stu-id="0adc3-133">rd.xml Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
