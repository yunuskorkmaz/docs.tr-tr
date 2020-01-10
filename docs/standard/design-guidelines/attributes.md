---
title: '{1&gt;{2&gt;Öznitelikler&lt;2}&lt;1}'
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
ms.openlocfilehash: ff38cfdc228fd1eae1ace734ed2688c62c66499a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709562"
---
# <a name="attributes"></a><span data-ttu-id="ed978-102">{1&gt;{2&gt;Öznitelikler&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="ed978-102">Attributes</span></span>
<span data-ttu-id="ed978-103"><xref:System.Attribute?displayProperty=nameWithType>, özel öznitelikler tanımlamak için kullanılan bir temel sınıftır.</span><span class="sxs-lookup"><span data-stu-id="ed978-103"><xref:System.Attribute?displayProperty=nameWithType> is a base class used to define custom attributes.</span></span>  
  
 <span data-ttu-id="ed978-104">Öznitelikler, derlemeler, türler, Üyeler ve parametreler gibi programlama öğelerine eklenebilen ek açıklamalardır.</span><span class="sxs-lookup"><span data-stu-id="ed978-104">Attributes are annotations that can be added to programming elements such as assemblies, types, members, and parameters.</span></span> <span data-ttu-id="ed978-105">Bunlar derlemenin meta verilerinde depolanır ve yansıma API 'Leri kullanılarak çalışma zamanında erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="ed978-105">They are stored in the metadata of the assembly and can be accessed at runtime using the reflection APIs.</span></span> <span data-ttu-id="ed978-106">Örneğin, çerçeve tür veya üyenin kullanım dışı olduğunu göstermek için bir türe veya üyeye uygulanabilen <xref:System.ObsoleteAttribute>tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ed978-106">For example, the Framework defines the <xref:System.ObsoleteAttribute>, which can be applied to a type or a member to indicate that the type or member has been deprecated.</span></span>  
  
 <span data-ttu-id="ed978-107">Öznitelikler, özniteliğiyle ilgili ek verileri taşıyan bir veya daha fazla özelliğe sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="ed978-107">Attributes can have one or more properties that carry additional data related to the attribute.</span></span> <span data-ttu-id="ed978-108">Örneğin, `ObsoleteAttribute`, bir tür veya üyenin kullanım dışı aldığı sürüm ve eski API 'YI değiştiren yeni API 'lerin açıklaması hakkında ek bilgiler taşıyabilir.</span><span class="sxs-lookup"><span data-stu-id="ed978-108">For example, `ObsoleteAttribute` could carry additional information about the release in which a type or a member got deprecated and the description of the new APIs replacing the obsolete API.</span></span>  
  
 <span data-ttu-id="ed978-109">Özniteliği uygulandığında bir özniteliğin bazı özelliklerinin belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed978-109">Some properties of an attribute must be specified when the attribute is applied.</span></span> <span data-ttu-id="ed978-110">Bunlar, konumsal Oluşturucu parametreleri olarak temsil edildiği için gereken özellikler veya gerekli bağımsız değişkenler olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="ed978-110">These are referred to as the required properties or required arguments, because they are represented as positional constructor parameters.</span></span> <span data-ttu-id="ed978-111">Örneğin, <xref:System.Diagnostics.ConditionalAttribute> <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> özelliği gerekli bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="ed978-111">For example, the <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> property of the <xref:System.Diagnostics.ConditionalAttribute> is a required property.</span></span>  
  
 <span data-ttu-id="ed978-112">Özniteliği uygulandığında belirtilmesi gereken özellikler isteğe bağlı Özellikler (veya isteğe bağlı bağımsız değişkenler) olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="ed978-112">Properties that do not necessarily have to be specified when the attribute is applied are called optional properties (or optional arguments).</span></span> <span data-ttu-id="ed978-113">Bunlar ayarlanabilir özelliklerle temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="ed978-113">They are represented by settable properties.</span></span> <span data-ttu-id="ed978-114">Derleyiciler, bir öznitelik uygulandığında bu özellikleri ayarlamak için özel söz dizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed978-114">Compilers provide special syntax to set these properties when an attribute is applied.</span></span> <span data-ttu-id="ed978-115">Örneğin <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> özelliği, isteğe bağlı bir bağımsız değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ed978-115">For example, the <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property represents an optional argument.</span></span>  
  
 <span data-ttu-id="ed978-116">**✓ DO** "Özniteliği" soneki ile özel öznitelik sınıfları adı</span><span class="sxs-lookup"><span data-stu-id="ed978-116">**✓ DO** name custom attribute classes with the suffix "Attribute."</span></span>  
  
 <span data-ttu-id="ed978-117">**✓ DO** uygulamak <xref:System.AttributeUsageAttribute> özel öznitelikleri için.</span><span class="sxs-lookup"><span data-stu-id="ed978-117">**✓ DO** apply the <xref:System.AttributeUsageAttribute> to custom attributes.</span></span>  
  
 <span data-ttu-id="ed978-118">**✓ DO** isteğe bağlı bağımsız değişkeni için ayarlanabilir özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed978-118">**✓ DO** provide settable properties for optional arguments.</span></span>  
  
 <span data-ttu-id="ed978-119">**✓ DO** yalnızca get özellikler için gerekli bağımsız değişkenleri sağlayın.</span><span class="sxs-lookup"><span data-stu-id="ed978-119">**✓ DO** provide get-only properties for required arguments.</span></span>  
  
 <span data-ttu-id="ed978-120">**✓ DO** gerekli bağımsız değişkenleri karşılık gelen özellikleri başlatmak için Oluşturucusu parametreleri sağlayın.</span><span class="sxs-lookup"><span data-stu-id="ed978-120">**✓ DO** provide constructor parameters to initialize properties corresponding to required arguments.</span></span> <span data-ttu-id="ed978-121">Her parametrenin karşılık gelen özellik olarak aynı ada sahip olması gerekir (büyük/küçük harfe karşın).</span><span class="sxs-lookup"><span data-stu-id="ed978-121">Each parameter should have the same name (although with different casing) as the corresponding property.</span></span>  
  
 <span data-ttu-id="ed978-122">**X AVOID** Oluşturucu parametreleri için isteğe bağlı bağımsız değişkenleri karşılık gelen özellikleri başlatmak için sağlama.</span><span class="sxs-lookup"><span data-stu-id="ed978-122">**X AVOID** providing constructor parameters to initialize properties corresponding to the optional arguments.</span></span>  
  
 <span data-ttu-id="ed978-123">Diğer bir deyişle, hem Oluşturucu hem de ayarlayıcı ile ayarlanabilir özellikleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="ed978-123">In other words, do not have properties that can be set with both a constructor and a setter.</span></span> <span data-ttu-id="ed978-124">Bu kılavuz, hangi bağımsız değişkenlerin isteğe bağlı ve gerekli olduğunu ve aynı şeyi yapmanın iki yolu olmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="ed978-124">This guideline makes very explicit which arguments are optional and which are required, and avoids having two ways of doing the same thing.</span></span>  
  
 <span data-ttu-id="ed978-125">**X AVOID** özel öznitelik oluşturucuların aşırı yüklemesi.</span><span class="sxs-lookup"><span data-stu-id="ed978-125">**X AVOID** overloading custom attribute constructors.</span></span>  
  
 <span data-ttu-id="ed978-126">Yalnızca bir oluşturucunun, bağımsız değişkenlerin gerekli olduğu ve isteğe bağlı olduğu kullanıcıya açıkça iletişim kurduğu.</span><span class="sxs-lookup"><span data-stu-id="ed978-126">Having only one constructor clearly communicates to the user which arguments are required and which are optional.</span></span>  
  
 <span data-ttu-id="ed978-127">**✓ DO** özel öznitelik sınıfları, mümkünse korumaya.</span><span class="sxs-lookup"><span data-stu-id="ed978-127">**✓ DO** seal custom attribute classes, if possible.</span></span> <span data-ttu-id="ed978-128">Bu, özniteliğe yönelik arama işlemini daha hızlı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="ed978-128">This makes the look-up for the attribute faster.</span></span>  
  
 <span data-ttu-id="ed978-129">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="ed978-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="ed978-130">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="ed978-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed978-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed978-131">See also</span></span>

- [<span data-ttu-id="ed978-132">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="ed978-132">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="ed978-133">Kullanım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="ed978-133">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
