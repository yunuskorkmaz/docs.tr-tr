---
title: Attributes1
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 493ac709123c67311ba570894fb324ae7148bfae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574640"
---
# <a name="attributes"></a><span data-ttu-id="5e472-102">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5e472-102">Attributes</span></span>
<span data-ttu-id="5e472-103"><xref:System.Attribute?displayProperty=nameWithType> bir taban sınıf özel öznitelikleri tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5e472-103"><xref:System.Attribute?displayProperty=nameWithType> is a base class used to define custom attributes.</span></span>  
  
 <span data-ttu-id="5e472-104">Derlemeler, türleri, üyeleri ve parametreler gibi programlama öğeleri ile eklenen ek açıklamaları öznitelikleridir.</span><span class="sxs-lookup"><span data-stu-id="5e472-104">Attributes are annotations that can be added to programming elements such as assemblies, types, members, and parameters.</span></span> <span data-ttu-id="5e472-105">Bunlar derlemesi meta verilerde depolanır ve yansıma API'lerini kullanarak çalışma zamanında erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="5e472-105">They are stored in the metadata of the assembly and can be accessed at runtime using the reflection APIs.</span></span> <span data-ttu-id="5e472-106">Örneğin, Framework tanımlar <xref:System.ObsoleteAttribute>, hangi uygulanabilir tür veya üye onaylanmaz belirtmek için bir tür veya üye.</span><span class="sxs-lookup"><span data-stu-id="5e472-106">For example, the Framework defines the <xref:System.ObsoleteAttribute>, which can be applied to a type or a member to indicate that the type or member has been deprecated.</span></span>  
  
 <span data-ttu-id="5e472-107">Öznitelikler için öznitelik ilgili ek veri taşımak bir veya daha fazla özelliklere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="5e472-107">Attributes can have one or more properties that carry additional data related to the attribute.</span></span> <span data-ttu-id="5e472-108">Örneğin, `ObsoleteAttribute` sürümde hakkında ek bilgi taşımak, bir tür veya üye kullanımdan ve eski API değiştirerek yeni API açıklaması.</span><span class="sxs-lookup"><span data-stu-id="5e472-108">For example, `ObsoleteAttribute` could carry additional information about the release in which a type or a member got deprecated and the description of the new APIs replacing the obsolete API.</span></span>  
  
 <span data-ttu-id="5e472-109">Öznitelik uygulandığında bir özniteliğin bazı özellikler belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="5e472-109">Some properties of an attribute must be specified when the attribute is applied.</span></span> <span data-ttu-id="5e472-110">Konumsal Oluşturucusu parametre olarak temsil edilir çünkü bunlar gerekli özellikleri veya gerekli bağımsız olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="5e472-110">These are referred to as the required properties or required arguments, because they are represented as positional constructor parameters.</span></span> <span data-ttu-id="5e472-111">Örneğin, <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> özelliği <xref:System.Diagnostics.ConditionalAttribute> gerekli bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="5e472-111">For example, the <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> property of the <xref:System.Diagnostics.ConditionalAttribute> is a required property.</span></span>  
  
 <span data-ttu-id="5e472-112">Mutlaka öznitelik olduğunda uygulanır belirtilmesi gerekmez özellikleri isteğe bağlı özellikleri (veya isteğe bağlı bağımsız değişkenler) adı verilir.</span><span class="sxs-lookup"><span data-stu-id="5e472-112">Properties that do not necessarily have to be specified when the attribute is applied are called optional properties (or optional arguments).</span></span> <span data-ttu-id="5e472-113">Bunlar ayarlanabilir özellikleri tarafından gösterilir.</span><span class="sxs-lookup"><span data-stu-id="5e472-113">They are represented by settable properties.</span></span> <span data-ttu-id="5e472-114">Derleyicileri bir öznitelik uygulandığında bu özellikleri ayarlamak için özel bir sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e472-114">Compilers provide special syntax to set these properties when an attribute is applied.</span></span> <span data-ttu-id="5e472-115">Örneğin, <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> özelliği, isteğe bağlı bir bağımsız değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5e472-115">For example, the <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property represents an optional argument.</span></span>  
  
 <span data-ttu-id="5e472-116">**✓ YAPMAK** "Özniteliği" soneki ile özel öznitelik sınıfları adı</span><span class="sxs-lookup"><span data-stu-id="5e472-116">**✓ DO** name custom attribute classes with the suffix "Attribute."</span></span>  
  
 <span data-ttu-id="5e472-117">**✓ YAPMAK** uygulamak <xref:System.AttributeUsageAttribute> özel öznitelikleri için.</span><span class="sxs-lookup"><span data-stu-id="5e472-117">**✓ DO** apply the <xref:System.AttributeUsageAttribute> to custom attributes.</span></span>  
  
 <span data-ttu-id="5e472-118">**✓ YAPMAK** isteğe bağlı bağımsız değişkeni için ayarlanabilir özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e472-118">**✓ DO** provide settable properties for optional arguments.</span></span>  
  
 <span data-ttu-id="5e472-119">**✓ YAPMAK** yalnızca get özellikler için gerekli bağımsız değişkenleri sağlayın.</span><span class="sxs-lookup"><span data-stu-id="5e472-119">**✓ DO** provide get-only properties for required arguments.</span></span>  
  
 <span data-ttu-id="5e472-120">**✓ YAPMAK** gerekli bağımsız değişkenleri karşılık gelen özellikleri başlatmak için Oluşturucusu parametreleri sağlayın.</span><span class="sxs-lookup"><span data-stu-id="5e472-120">**✓ DO** provide constructor parameters to initialize properties corresponding to required arguments.</span></span> <span data-ttu-id="5e472-121">Her bir parametreyi aynı adı karşılık gelen özelliği (ile farklı büyük/küçük harf rağmen) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5e472-121">Each parameter should have the same name (although with different casing) as the corresponding property.</span></span>  
  
 <span data-ttu-id="5e472-122">**KAÇININ x** Oluşturucu parametreleri için isteğe bağlı bağımsız değişkenleri karşılık gelen özellikleri başlatmak için sağlama.</span><span class="sxs-lookup"><span data-stu-id="5e472-122">**X AVOID** providing constructor parameters to initialize properties corresponding to the optional arguments.</span></span>  
  
 <span data-ttu-id="5e472-123">Diğer bir deyişle, hem bir oluşturucu hem de ayarlayıcı ile ayarlayabileceğiniz özellikleri yok.</span><span class="sxs-lookup"><span data-stu-id="5e472-123">In other words, do not have properties that can be set with both a constructor and a setter.</span></span> <span data-ttu-id="5e472-124">Bu kılavuz, hangi bağımsız değişkenler isteğe bağlıdır ve hangi gereklidir ve aynı işi yapmanın iki yolu belirlemeyi önler çok açık hale getirir.</span><span class="sxs-lookup"><span data-stu-id="5e472-124">This guideline makes very explicit which arguments are optional and which are required, and avoids having two ways of doing the same thing.</span></span>  
  
 <span data-ttu-id="5e472-125">**KAÇININ x** özel öznitelik oluşturucuların aşırı yüklemesi.</span><span class="sxs-lookup"><span data-stu-id="5e472-125">**X AVOID** overloading custom attribute constructors.</span></span>  
  
 <span data-ttu-id="5e472-126">Açıkça sadece bir oluşturucuya sahip kullanıcıya hangi bağımsız değişkenler zorunludur ve isteğe bağlı olduğu iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="5e472-126">Having only one constructor clearly communicates to the user which arguments are required and which are optional.</span></span>  
  
 <span data-ttu-id="5e472-127">**✓ YAPMAK** özel öznitelik sınıfları, mümkünse korumaya.</span><span class="sxs-lookup"><span data-stu-id="5e472-127">**✓ DO** seal custom attribute classes, if possible.</span></span> <span data-ttu-id="5e472-128">Bu öznitelik için araması hızlandırır.</span><span class="sxs-lookup"><span data-stu-id="5e472-128">This makes the look-up for the attribute faster.</span></span>  
  
 <span data-ttu-id="5e472-129">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="5e472-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="5e472-130">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="5e472-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e472-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5e472-131">See Also</span></span>  
 [<span data-ttu-id="5e472-132">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="5e472-132">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="5e472-133">Kullanım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="5e472-133">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
