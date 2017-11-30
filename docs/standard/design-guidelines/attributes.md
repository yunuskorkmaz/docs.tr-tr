---
title: Attributes1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 86fa2556e6b8fb82e31a7d4753354aa2dff627ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="attributes"></a><span data-ttu-id="34134-102">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="34134-102">Attributes</span></span>
<span data-ttu-id="34134-103"><xref:System.Attribute?displayProperty=nameWithType>bir taban sınıf özel öznitelikleri tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="34134-103"><xref:System.Attribute?displayProperty=nameWithType> is a base class used to define custom attributes.</span></span>  
  
 <span data-ttu-id="34134-104">Derlemeler, türleri, üyeleri ve parametreler gibi programlama öğeleri ile eklenen ek açıklamaları öznitelikleridir.</span><span class="sxs-lookup"><span data-stu-id="34134-104">Attributes are annotations that can be added to programming elements such as assemblies, types, members, and parameters.</span></span> <span data-ttu-id="34134-105">Bunlar derlemesi meta verilerde depolanır ve yansıma API'lerini kullanarak çalışma zamanında erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="34134-105">They are stored in the metadata of the assembly and can be accessed at runtime using the reflection APIs.</span></span> <span data-ttu-id="34134-106">Örneğin, Framework tanımlar <xref:System.ObsoleteAttribute>, hangi uygulanabilir tür veya üye onaylanmaz belirtmek için bir tür veya üye.</span><span class="sxs-lookup"><span data-stu-id="34134-106">For example, the Framework defines the <xref:System.ObsoleteAttribute>, which can be applied to a type or a member to indicate that the type or member has been deprecated.</span></span>  
  
 <span data-ttu-id="34134-107">Öznitelikler için öznitelik ilgili ek veri taşımak bir veya daha fazla özelliklere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="34134-107">Attributes can have one or more properties that carry additional data related to the attribute.</span></span> <span data-ttu-id="34134-108">Örneğin, `ObsoleteAttribute` sürümde hakkında ek bilgi taşımak, bir tür veya üye kullanımdan ve eski API değiştirerek yeni API açıklaması.</span><span class="sxs-lookup"><span data-stu-id="34134-108">For example, `ObsoleteAttribute` could carry additional information about the release in which a type or a member got deprecated and the description of the new APIs replacing the obsolete API.</span></span>  
  
 <span data-ttu-id="34134-109">Öznitelik uygulandığında bir özniteliğin bazı özellikler belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="34134-109">Some properties of an attribute must be specified when the attribute is applied.</span></span> <span data-ttu-id="34134-110">Konumsal Oluşturucusu parametre olarak temsil edilir çünkü bunlar gerekli özellikleri veya gerekli bağımsız olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="34134-110">These are referred to as the required properties or required arguments, because they are represented as positional constructor parameters.</span></span> <span data-ttu-id="34134-111">Örneğin, <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> özelliği <xref:System.Diagnostics.ConditionalAttribute> gerekli bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="34134-111">For example, the <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> property of the <xref:System.Diagnostics.ConditionalAttribute> is a required property.</span></span>  
  
 <span data-ttu-id="34134-112">Mutlaka öznitelik olduğunda uygulanır belirtilmesi gerekmez özellikleri isteğe bağlı özellikleri (veya isteğe bağlı bağımsız değişkenler) adı verilir.</span><span class="sxs-lookup"><span data-stu-id="34134-112">Properties that do not necessarily have to be specified when the attribute is applied are called optional properties (or optional arguments).</span></span> <span data-ttu-id="34134-113">Bunlar ayarlanabilir özellikleri tarafından gösterilir.</span><span class="sxs-lookup"><span data-stu-id="34134-113">They are represented by settable properties.</span></span> <span data-ttu-id="34134-114">Derleyicileri bir öznitelik uygulandığında bu özellikleri ayarlamak için özel bir sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="34134-114">Compilers provide special syntax to set these properties when an attribute is applied.</span></span> <span data-ttu-id="34134-115">Örneğin, <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> özelliği, isteğe bağlı bir bağımsız değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="34134-115">For example, the <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property represents an optional argument.</span></span>  
  
 <span data-ttu-id="34134-116">**✓ YAPMAK** "Özniteliği" soneki ile özel öznitelik sınıfları adı</span><span class="sxs-lookup"><span data-stu-id="34134-116">**✓ DO** name custom attribute classes with the suffix "Attribute."</span></span>  
  
 <span data-ttu-id="34134-117">**✓ YAPMAK** uygulamak <xref:System.AttributeUsageAttribute> özel öznitelikleri için.</span><span class="sxs-lookup"><span data-stu-id="34134-117">**✓ DO** apply the <xref:System.AttributeUsageAttribute> to custom attributes.</span></span>  
  
 <span data-ttu-id="34134-118">**✓ YAPMAK** isteğe bağlı bağımsız değişkeni için ayarlanabilir özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="34134-118">**✓ DO** provide settable properties for optional arguments.</span></span>  
  
 <span data-ttu-id="34134-119">**✓ YAPMAK** yalnızca get özellikler için gerekli bağımsız değişkenleri sağlayın.</span><span class="sxs-lookup"><span data-stu-id="34134-119">**✓ DO** provide get-only properties for required arguments.</span></span>  
  
 <span data-ttu-id="34134-120">**✓ YAPMAK** gerekli bağımsız değişkenleri karşılık gelen özellikleri başlatmak için Oluşturucusu parametreleri sağlayın.</span><span class="sxs-lookup"><span data-stu-id="34134-120">**✓ DO** provide constructor parameters to initialize properties corresponding to required arguments.</span></span> <span data-ttu-id="34134-121">Her bir parametreyi aynı adı karşılık gelen özelliği (ile farklı büyük/küçük harf rağmen) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="34134-121">Each parameter should have the same name (although with different casing) as the corresponding property.</span></span>  
  
 <span data-ttu-id="34134-122">**KAÇININ x** Oluşturucu parametreleri için isteğe bağlı bağımsız değişkenleri karşılık gelen özellikleri başlatmak için sağlama.</span><span class="sxs-lookup"><span data-stu-id="34134-122">**X AVOID** providing constructor parameters to initialize properties corresponding to the optional arguments.</span></span>  
  
 <span data-ttu-id="34134-123">Diğer bir deyişle, hem bir oluşturucu hem de ayarlayıcı ile ayarlayabileceğiniz özellikleri yok.</span><span class="sxs-lookup"><span data-stu-id="34134-123">In other words, do not have properties that can be set with both a constructor and a setter.</span></span> <span data-ttu-id="34134-124">Bu kılavuz, hangi bağımsız değişkenler isteğe bağlıdır ve hangi gereklidir ve aynı işi yapmanın iki yolu belirlemeyi önler çok açık hale getirir.</span><span class="sxs-lookup"><span data-stu-id="34134-124">This guideline makes very explicit which arguments are optional and which are required, and avoids having two ways of doing the same thing.</span></span>  
  
 <span data-ttu-id="34134-125">**KAÇININ x** özel öznitelik oluşturucuların aşırı yüklemesi.</span><span class="sxs-lookup"><span data-stu-id="34134-125">**X AVOID** overloading custom attribute constructors.</span></span>  
  
 <span data-ttu-id="34134-126">Açıkça sadece bir oluşturucuya sahip kullanıcıya hangi bağımsız değişkenler zorunludur ve isteğe bağlı olduğu iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="34134-126">Having only one constructor clearly communicates to the user which arguments are required and which are optional.</span></span>  
  
 <span data-ttu-id="34134-127">**✓ YAPMAK** özel öznitelik sınıfları, mümkünse korumaya.</span><span class="sxs-lookup"><span data-stu-id="34134-127">**✓ DO** seal custom attribute classes, if possible.</span></span> <span data-ttu-id="34134-128">Bu öznitelik için araması hızlandırır.</span><span class="sxs-lookup"><span data-stu-id="34134-128">This makes the look-up for the attribute faster.</span></span>  
  
 <span data-ttu-id="34134-129">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="34134-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="34134-130">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="34134-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34134-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="34134-131">See Also</span></span>  
 [<span data-ttu-id="34134-132">Framework tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="34134-132">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="34134-133">Kullanım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="34134-133">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
