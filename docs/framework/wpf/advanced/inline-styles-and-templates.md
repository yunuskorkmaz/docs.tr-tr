---
title: Satır İçi Stil ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- inline templates [WPF]
- styles [WPF], inline
- templates [WPF], inline
- inline styles [WPF]
ms.assetid: 69a1a3f9-acb5-4e2c-9c43-2e376c055ac4
ms.openlocfilehash: b88ef444283f4e1e85009c59b39f3cc41965d300
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460011"
---
# <a name="inline-styles-and-templates"></a><span data-ttu-id="6aa4a-102">Satır İçi Stil ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="6aa4a-102">Inline Styles and Templates</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="6aa4a-103">, kaynakların birden çok kez kullanılabilmesi için, kaynaklardaki bir öğenin görsel görünümünü tanımlamanın bir yolu olarak <xref:System.Windows.Style> nesneleri ve şablon nesneleri (<xref:System.Windows.FrameworkTemplate> alt sınıfları) sağlar.</span><span class="sxs-lookup"><span data-stu-id="6aa4a-103">provides <xref:System.Windows.Style> objects and template objects (<xref:System.Windows.FrameworkTemplate> subclasses) as a way to define the visual appearance of an element in resources, so that they can be used multiple times.</span></span> <span data-ttu-id="6aa4a-104">Bu nedenle, <xref:System.Windows.Style> ve <xref:System.Windows.FrameworkTemplate> türlerini alan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öznitelikleri neredeyse her zaman satır içi yenilerini tanımlamak yerine var olan stillere ve şablonlara kaynak başvuruları yapabilir.</span><span class="sxs-lookup"><span data-stu-id="6aa4a-104">For this reason, attributes in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that take the types <xref:System.Windows.Style> and <xref:System.Windows.FrameworkTemplate> almost always make resource references to existing styles and templates rather than define new ones inline.</span></span>  
  
## <a name="limitations-of-inline-styles-and-templates"></a><span data-ttu-id="6aa4a-105">Satır Içi stiller ve şablonların sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="6aa4a-105">Limitations of Inline Styles and Templates</span></span>  
 <span data-ttu-id="6aa4a-106">[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], stil ve Şablon Özellikleri Teknik olarak iki şekilde ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="6aa4a-106">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], style and template properties can technically be set in one of two ways.</span></span> <span data-ttu-id="6aa4a-107">Kaynak içinde tanımlanmış bir stile başvurmak için öznitelik sözdizimini kullanabilirsiniz; Örneğin, `<`*nesnesi* *myresourcekey*`}" .../>``Style="{StaticResource`.</span><span class="sxs-lookup"><span data-stu-id="6aa4a-107">You can use attribute syntax to reference a style that was defined within a resource, for example `<`*object*`Style="{StaticResource`*myResourceKey*`}" .../>`.</span></span> <span data-ttu-id="6aa4a-108">Ya da bir stil satır içi tanımlamak için özellik öğesi sözdizimini kullanabilirsiniz, örneğin:</span><span class="sxs-lookup"><span data-stu-id="6aa4a-108">Or you can use property element syntax to define a style inline, for instance:</span></span>  
  
 <span data-ttu-id="6aa4a-109">*nesne* `>` `<`</span><span class="sxs-lookup"><span data-stu-id="6aa4a-109">`<` *object* `>`</span></span>  
  
 <span data-ttu-id="6aa4a-110">*nesne* `.Style>` `<`</span><span class="sxs-lookup"><span data-stu-id="6aa4a-110">`<` *object* `.Style>`</span></span>  
  
 <span data-ttu-id="6aa4a-111">`<` `Style``.../>`</span><span class="sxs-lookup"><span data-stu-id="6aa4a-111">`<` `Style`  `.../>`</span></span>  
  
 <span data-ttu-id="6aa4a-112">*nesne* `.Style>` `</`</span><span class="sxs-lookup"><span data-stu-id="6aa4a-112">`</` *object* `.Style>`</span></span>  
  
 <span data-ttu-id="6aa4a-113">*nesne* `>` `</`</span><span class="sxs-lookup"><span data-stu-id="6aa4a-113">`</` *object* `>`</span></span>  
  
 <span data-ttu-id="6aa4a-114">Öznitelik kullanımı çok daha yaygındır.</span><span class="sxs-lookup"><span data-stu-id="6aa4a-114">The attribute usage is much more common.</span></span> <span data-ttu-id="6aa4a-115">Satır içi tanımlanmış ve kaynaklarda tanımlanmamış bir stil, yalnızca kapsayan öğe kapsamına alınır ve kaynak anahtarı olmadığından kolayca yeniden kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6aa4a-115">A style that is defined inline and not defined in resources is necessarily scoped to the containing element only, and cannot be re-used as easily because it has no resource key.</span></span> <span data-ttu-id="6aa4a-116">Genel olarak kaynak tanımlı bir stil daha kullanışlıdır ve yararlı olur ve kod içindeki program mantığını biçimlendirme içinde tasarlamadan ayırmak için genel [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] programlama modeli ilkesiyle birlikte tutulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6aa4a-116">In general a resource-defined style is more versatile and useful, and is more in keeping with the general [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] programming model principle of separating program logic in code from design in markup.</span></span>  
  
 <span data-ttu-id="6aa4a-117">Genellikle, söz konusu stili veya şablonu yalnızca o konumda kullanmak istiyorsanız bile, bir stil veya şablon satır içi ayarlamak için bir neden yoktur.</span><span class="sxs-lookup"><span data-stu-id="6aa4a-117">Usually there is no reason to set a style or template inline, even if you only intend to use that style or template in that location.</span></span> <span data-ttu-id="6aa4a-118">Stil veya şablon alan çoğu öğe, içerik özelliğini ve bir içerik modelini de destekler.</span><span class="sxs-lookup"><span data-stu-id="6aa4a-118">Most elements that can take a style or template also support a content property and a content model.</span></span> <span data-ttu-id="6aa4a-119">Yalnızca stil veya şablon oluşturma aracılığıyla oluşturduğunuz herhangi bir mantıksal ağacı kullanıyorsanız, doğrudan biçimlendirme içindeki bu içerik özelliğini yalnızca eşdeğer alt öğelerle doldurmanız daha da kolay olur.</span><span class="sxs-lookup"><span data-stu-id="6aa4a-119">If you are only using whatever logical tree you create through styling or templating once, it would be even easier to just fill that content property with the equivalent child elements in direct markup.</span></span> <span data-ttu-id="6aa4a-120">Bu, stili ve şablon mekanizmalarını tamamen atlar.</span><span class="sxs-lookup"><span data-stu-id="6aa4a-120">This would bypass the style and template mechanisms altogether.</span></span>  
  
 <span data-ttu-id="6aa4a-121">Bir nesne döndüren biçimlendirme uzantıları tarafından etkinleştirilen diğer sözdizimleri, stiller ve şablonlar için de mümkündür.</span><span class="sxs-lookup"><span data-stu-id="6aa4a-121">Other syntaxes enabled by markup extensions that return an object are also possible for styles and templates.</span></span> <span data-ttu-id="6aa4a-122">Olası senaryolara sahip iki uzantı de [TemplateBinding](templatebinding-markup-extension.md) ve <xref:System.Windows.Data.Binding>içerir.</span><span class="sxs-lookup"><span data-stu-id="6aa4a-122">Two such extensions that have possible scenarios include [TemplateBinding](templatebinding-markup-extension.md) and <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aa4a-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6aa4a-123">See also</span></span>

- [<span data-ttu-id="6aa4a-124">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6aa4a-124">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
