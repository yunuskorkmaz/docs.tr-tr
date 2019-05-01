---
title: Öznitelikler
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
author: KrzysztofCwalina
ms.openlocfilehash: 6d4cc6615b7f7346e9c8fc2a7264025f318c8a3d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785573"
---
# <a name="attributes"></a><span data-ttu-id="f9bdd-102">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f9bdd-102">Attributes</span></span>
<span data-ttu-id="f9bdd-103"><xref:System.Attribute?displayProperty=nameWithType> bir temel sınıf özel öznitelikler tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f9bdd-103"><xref:System.Attribute?displayProperty=nameWithType> is a base class used to define custom attributes.</span></span>  
  
 <span data-ttu-id="f9bdd-104">Derlemeleri, türleri, üyeler ve parametreler gibi programlama öğelerine eklenebilir ek açıklamaları öznitelikleridir.</span><span class="sxs-lookup"><span data-stu-id="f9bdd-104">Attributes are annotations that can be added to programming elements such as assemblies, types, members, and parameters.</span></span> <span data-ttu-id="f9bdd-105">Bunlar, derlemenin meta verilerde depolanan ve yansıma API'leri kullanarak çalışma zamanında erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="f9bdd-105">They are stored in the metadata of the assembly and can be accessed at runtime using the reflection APIs.</span></span> <span data-ttu-id="f9bdd-106">Örneğin, Framework tanımlar <xref:System.ObsoleteAttribute>, hangi uygulanabilir türe veya üyeye onaylanmaz belirtmek için bir tür veya üye.</span><span class="sxs-lookup"><span data-stu-id="f9bdd-106">For example, the Framework defines the <xref:System.ObsoleteAttribute>, which can be applied to a type or a member to indicate that the type or member has been deprecated.</span></span>  
  
 <span data-ttu-id="f9bdd-107">Öznitelikleri, öznitelik için ilgili ek veri taşıyan bir veya daha fazla özelliklere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="f9bdd-107">Attributes can have one or more properties that carry additional data related to the attribute.</span></span> <span data-ttu-id="f9bdd-108">Örneğin, `ObsoleteAttribute` sürümde hakkında ek bilgi gerçekleştirmek bir tür veya üye kullanımdan ve eski API değiştirerek yeni API'leri açıklaması.</span><span class="sxs-lookup"><span data-stu-id="f9bdd-108">For example, `ObsoleteAttribute` could carry additional information about the release in which a type or a member got deprecated and the description of the new APIs replacing the obsolete API.</span></span>  
  
 <span data-ttu-id="f9bdd-109">Bazı özellikler bir özniteliğin öznitelik uygulandığı zaman belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f9bdd-109">Some properties of an attribute must be specified when the attribute is applied.</span></span> <span data-ttu-id="f9bdd-110">Konumsal Oluşturucu parametresi olarak temsil edilir çünkü bunlar için gerekli özellikler veya gerekli bağımsız adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f9bdd-110">These are referred to as the required properties or required arguments, because they are represented as positional constructor parameters.</span></span> <span data-ttu-id="f9bdd-111">Örneğin, <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> özelliği <xref:System.Diagnostics.ConditionalAttribute> gerekli bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="f9bdd-111">For example, the <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> property of the <xref:System.Diagnostics.ConditionalAttribute> is a required property.</span></span>  
  
 <span data-ttu-id="f9bdd-112">Mutlaka öznitelik uygulandığında belirtilmesi gerekmez özellikleri, isteğe bağlı özellikleri (veya isteğe bağlı bağımsız değişkenler) adı verilir.</span><span class="sxs-lookup"><span data-stu-id="f9bdd-112">Properties that do not necessarily have to be specified when the attribute is applied are called optional properties (or optional arguments).</span></span> <span data-ttu-id="f9bdd-113">Bunlar, ayarlanabilir özelliklerin tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="f9bdd-113">They are represented by settable properties.</span></span> <span data-ttu-id="f9bdd-114">Derleyiciler, bir öznitelik uygulandığında, bu özellikleri ayarlamak için özel bir sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f9bdd-114">Compilers provide special syntax to set these properties when an attribute is applied.</span></span> <span data-ttu-id="f9bdd-115">Örneğin, <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> özelliği, isteğe bağlı bir bağımsız değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f9bdd-115">For example, the <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property represents an optional argument.</span></span>  
  
 <span data-ttu-id="f9bdd-116">**✓ DO** "Özniteliği" soneki ile özel öznitelik sınıfları adı</span><span class="sxs-lookup"><span data-stu-id="f9bdd-116">**✓ DO** name custom attribute classes with the suffix "Attribute."</span></span>  
  
 <span data-ttu-id="f9bdd-117">**✓ DO** uygulamak <xref:System.AttributeUsageAttribute> özel öznitelikleri için.</span><span class="sxs-lookup"><span data-stu-id="f9bdd-117">**✓ DO** apply the <xref:System.AttributeUsageAttribute> to custom attributes.</span></span>  
  
 <span data-ttu-id="f9bdd-118">**✓ DO** isteğe bağlı bağımsız değişkeni için ayarlanabilir özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="f9bdd-118">**✓ DO** provide settable properties for optional arguments.</span></span>  
  
 <span data-ttu-id="f9bdd-119">**✓ DO** yalnızca get özellikler için gerekli bağımsız değişkenleri sağlayın.</span><span class="sxs-lookup"><span data-stu-id="f9bdd-119">**✓ DO** provide get-only properties for required arguments.</span></span>  
  
 <span data-ttu-id="f9bdd-120">**✓ DO** gerekli bağımsız değişkenleri karşılık gelen özellikleri başlatmak için Oluşturucusu parametreleri sağlayın.</span><span class="sxs-lookup"><span data-stu-id="f9bdd-120">**✓ DO** provide constructor parameters to initialize properties corresponding to required arguments.</span></span> <span data-ttu-id="f9bdd-121">Her parametre karşılık gelen özellik olarak (farklı büyük/küçük harf olsa da ile) aynı adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f9bdd-121">Each parameter should have the same name (although with different casing) as the corresponding property.</span></span>  
  
 <span data-ttu-id="f9bdd-122">**X AVOID** Oluşturucu parametreleri için isteğe bağlı bağımsız değişkenleri karşılık gelen özellikleri başlatmak için sağlama.</span><span class="sxs-lookup"><span data-stu-id="f9bdd-122">**X AVOID** providing constructor parameters to initialize properties corresponding to the optional arguments.</span></span>  
  
 <span data-ttu-id="f9bdd-123">Diğer bir deyişle, bir oluşturucu hem de ayarlayıcı ile ayarlanabilir özellikleri yok.</span><span class="sxs-lookup"><span data-stu-id="f9bdd-123">In other words, do not have properties that can be set with both a constructor and a setter.</span></span> <span data-ttu-id="f9bdd-124">Bu kılavuz, hangi bağımsız değişken isteğe bağlıdır ve gerekli olan ve aynı şeyi yapmanın iki yolu zorunluluğunu ortadan çok açık hale getirir.</span><span class="sxs-lookup"><span data-stu-id="f9bdd-124">This guideline makes very explicit which arguments are optional and which are required, and avoids having two ways of doing the same thing.</span></span>  
  
 <span data-ttu-id="f9bdd-125">**X AVOID** özel öznitelik oluşturucuların aşırı yüklemesi.</span><span class="sxs-lookup"><span data-stu-id="f9bdd-125">**X AVOID** overloading custom attribute constructors.</span></span>  
  
 <span data-ttu-id="f9bdd-126">Açıkça yalnızca bir oluşturucuya sahip kullanıcıya hangi bağımsız değişkenleri gereklidir ve isteğe bağlı olduğu iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="f9bdd-126">Having only one constructor clearly communicates to the user which arguments are required and which are optional.</span></span>  
  
 <span data-ttu-id="f9bdd-127">**✓ DO** özel öznitelik sınıfları, mümkünse korumaya.</span><span class="sxs-lookup"><span data-stu-id="f9bdd-127">**✓ DO** seal custom attribute classes, if possible.</span></span> <span data-ttu-id="f9bdd-128">Bu öznitelik için arama daha hızlı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f9bdd-128">This makes the look-up for the attribute faster.</span></span>  
  
 <span data-ttu-id="f9bdd-129">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="f9bdd-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="f9bdd-130">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*</span><span class="sxs-lookup"><span data-stu-id="f9bdd-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9bdd-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9bdd-131">See also</span></span>

- [<span data-ttu-id="f9bdd-132">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="f9bdd-132">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="f9bdd-133">Kullanım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="f9bdd-133">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
