---
title: "Satır İçi Stil ve Şablonları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inline templates [WPF]
- styles [WPF], inline
- templates [WPF], inline
- inline styles [WPF]
ms.assetid: 69a1a3f9-acb5-4e2c-9c43-2e376c055ac4
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2acb455db8f8bdc5a95bfd2462b651cebbb692c3
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="inline-styles-and-templates"></a><span data-ttu-id="ee26c-102">Satır İçi Stil ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="ee26c-102">Inline Styles and Templates</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="ee26c-103">sağlar <xref:System.Windows.Style> ve şablon nesneleri (<xref:System.Windows.FrameworkTemplate> alt sınıfların) kaynaklarında bir öğeyi görsel görünümünü tanımlamak için bir yol kullanılabilmesi için birden çok kez kullanabilmek.</span><span class="sxs-lookup"><span data-stu-id="ee26c-103"> provides <xref:System.Windows.Style> objects and template objects (<xref:System.Windows.FrameworkTemplate> subclasses) as a way to define the visual appearance of an element in resources, so that they can be used multiple times.</span></span> <span data-ttu-id="ee26c-104">Bu nedenle, öznitelikleri [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] türleri yararlanma <xref:System.Windows.Style> ve <xref:System.Windows.FrameworkTemplate> neredeyse her zaman kaynak referans varolan stilleri ve şablonları olarak yerine satır içi yenilerini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="ee26c-104">For this reason, attributes in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that take the types <xref:System.Windows.Style> and <xref:System.Windows.FrameworkTemplate> almost always make resource references to existing styles and templates rather than define new ones inline.</span></span>  
  
## <a name="limitations-of-inline-styles-and-templates"></a><span data-ttu-id="ee26c-105">Satır içi stilleri ve şablonları sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="ee26c-105">Limitations of Inline Styles and Templates</span></span>  
 <span data-ttu-id="ee26c-106">İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], stil ve şablon özellikler teknik olarak ayarlanabilir iki yoldan biriyle.</span><span class="sxs-lookup"><span data-stu-id="ee26c-106">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], style and template properties can technically be set in one of two ways.</span></span> <span data-ttu-id="ee26c-107">İçindeki kaynak, örneğin tanımlanmış bir stil başvurmak için öznitelik sözdizimini kullanabilirsiniz `<` *nesne*`Style="{StaticResource`*myResourceKey*`}" .../>`.</span><span class="sxs-lookup"><span data-stu-id="ee26c-107">You can use attribute syntax to reference a style that was defined within a resource, for example `<`*object*`Style="{StaticResource`*myResourceKey*`}" .../>`.</span></span> <span data-ttu-id="ee26c-108">Veya örneği için bir stil satır içi tanımlamak için özellik öğesi sözdizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="ee26c-108">Or you can use property element syntax to define a style inline, for instance:</span></span>  
  
 <span data-ttu-id="ee26c-109">`<`*nesne*`>`</span><span class="sxs-lookup"><span data-stu-id="ee26c-109">`<` *object* `>`</span></span>  
  
 <span data-ttu-id="ee26c-110">`<`*nesne*`.Style>`</span><span class="sxs-lookup"><span data-stu-id="ee26c-110">`<` *object* `.Style>`</span></span>  
  
 <span data-ttu-id="ee26c-111">`<` `Style`  `.../>`</span><span class="sxs-lookup"><span data-stu-id="ee26c-111">`<` `Style`  `.../>`</span></span>  
  
 <span data-ttu-id="ee26c-112">`</`*nesne*`.Style>`</span><span class="sxs-lookup"><span data-stu-id="ee26c-112">`</` *object* `.Style>`</span></span>  
  
 <span data-ttu-id="ee26c-113">`</`*nesne*`>`</span><span class="sxs-lookup"><span data-stu-id="ee26c-113">`</` *object* `>`</span></span>  
  
 <span data-ttu-id="ee26c-114">Öznitelik kullanımı çok daha yaygındır.</span><span class="sxs-lookup"><span data-stu-id="ee26c-114">The attribute usage is much more common.</span></span> <span data-ttu-id="ee26c-115">Satır içi olarak tanımlanan ve kaynaklar içinde tanımlanmamış bir stil yalnızca içeren öğesine mutlaka kapsamlıdır ve anahtar kaynağı yoktur çünkü kolayca yeniden kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ee26c-115">A style that is defined inline and not defined in resources is necessarily scoped to the containing element only, and cannot be re-used as easily because it has no resource key.</span></span> <span data-ttu-id="ee26c-116">Genel olarak kaynak tanımlı bir stil çok yönlü ve kullanışlı ve genel mantığıyla daha fazla [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] biçimlendirmede tasarımından program mantığı kodda ayırma modeli ilkesini programlama.</span><span class="sxs-lookup"><span data-stu-id="ee26c-116">In general a resource-defined style is more versatile and useful, and is more in keeping with the general [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] programming model principle of separating program logic in code from design in markup.</span></span>  
  
 <span data-ttu-id="ee26c-117">Genellikle, yalnızca söz konusu konumda stil veya şablonu kullanmak istediğiniz olsa bile bir stil veya şablon satır içi ayarlamak için bir neden yoktur.</span><span class="sxs-lookup"><span data-stu-id="ee26c-117">Usually there is no reason to set a style or template inline, even if you only intend to use that style or template in that location.</span></span> <span data-ttu-id="ee26c-118">Stil veya şablon alabilen öğelerin çoğu içerik özelliğini ve içerik modeli de destekler.</span><span class="sxs-lookup"><span data-stu-id="ee26c-118">Most elements that can take a style or template also support a content property and a content model.</span></span> <span data-ttu-id="ee26c-119">Hangi mantıksal ağacının yalnızca kullanıyorsanız stil veya şablon aracılığıyla bir kez oluşturun, yalnızca o içerik özelliği doğrudan biçimlendirme eşdeğer alt öğeleri doldurmak daha kolay olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ee26c-119">If you are only using whatever logical tree you create through styling or templating once, it would be even easier to just fill that content property with the equivalent child elements in direct markup.</span></span> <span data-ttu-id="ee26c-120">Bu stil ve şablon mekanizmalarını birlikte atlar.</span><span class="sxs-lookup"><span data-stu-id="ee26c-120">This would bypass the style and template mechanisms altogether.</span></span>  
  
 <span data-ttu-id="ee26c-121">Nesne döndüren biçimlendirme uzantıları tarafından etkinleştirilmiş diğer sözdizimleri de stil ve şablonlar için mümkündür.</span><span class="sxs-lookup"><span data-stu-id="ee26c-121">Other syntaxes enabled by markup extensions that return an object are also possible for styles and templates.</span></span> <span data-ttu-id="ee26c-122">Olası senaryolar sahip olan iki uzantı şunlardır [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) ve <xref:System.Windows.Data.Binding>.</span><span class="sxs-lookup"><span data-stu-id="ee26c-122">Two such extensions that have possible scenarios include [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) and <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee26c-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ee26c-123">See Also</span></span>  
 [<span data-ttu-id="ee26c-124">Stil ve şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="ee26c-124">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
