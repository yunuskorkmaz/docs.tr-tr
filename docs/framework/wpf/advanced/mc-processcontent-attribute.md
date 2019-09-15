---
title: mc:ProcessContent Özniteliği
ms.date: 03/30/2017
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
ms.openlocfilehash: e625d99cdb30368a798b4829d103f8f26b2c9274
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991860"
---
# <a name="mcprocesscontent-attribute"></a><span data-ttu-id="5dfc9-102">mc:ProcessContent Özniteliği</span><span class="sxs-lookup"><span data-stu-id="5dfc9-102">mc:ProcessContent Attribute</span></span>
<span data-ttu-id="5dfc9-103">En üst [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öğe, [mc: Ignorable özniteliği](mc-ignorable-attribute.md)belirtildiğinde bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci tarafından yoksayılabilir olsa bile, hangi öğelerin ilgili üst öğeler tarafından işlenmesi gereken içeriğe sahip olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5dfc9-103">Specifies which [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements should still have content processed by relevant parent elements, even if the immediate parent element may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor due to specifying [mc:Ignorable Attribute](mc-ignorable-attribute.md).</span></span> <span data-ttu-id="5dfc9-104">Öznitelik `mc:ProcessContent` , hem özel ad alanı eşlemesi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] hem de sürüm oluşturma için biçimlendirme uyumluluğunu destekler.</span><span class="sxs-lookup"><span data-stu-id="5dfc9-104">The `mc:ProcessContent` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="5dfc9-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="5dfc9-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...  
  mc:ProcessContent="ignorablePrefix:ThisElementCanBeIgnored"  
>  
    <ignorablePrefix:ThisElementCanBeIgnored>  
        [content]  
    </ignorablePrefix:ThisElementCanBeIgnored>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="5dfc9-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="5dfc9-106">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5dfc9-107">*ıgnorableprefix*</span><span class="sxs-lookup"><span data-stu-id="5dfc9-107">*ignorablePrefix*</span></span>|<span data-ttu-id="5dfc9-108">XML 1,0 belirtimine göre geçerli herhangi bir ön ek dizesi.</span><span class="sxs-lookup"><span data-stu-id="5dfc9-108">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="5dfc9-109">*ıgnorableuri*</span><span class="sxs-lookup"><span data-stu-id="5dfc9-109">*ignorableUri*</span></span>|<span data-ttu-id="5dfc9-110">XML 1,0 belirtimine göre bir ad alanı atamak için geçerli bir URI.</span><span class="sxs-lookup"><span data-stu-id="5dfc9-110">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="5dfc9-111">*Thiselementcanbeyoksayıldı*</span><span class="sxs-lookup"><span data-stu-id="5dfc9-111">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="5dfc9-112">Temel alınan tür çözümlenemiyorsa, işlemci [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] uygulamaları tarafından yoksayılabilir bir öğe.</span><span class="sxs-lookup"><span data-stu-id="5dfc9-112">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
|<span data-ttu-id="5dfc9-113">*içeriði*</span><span class="sxs-lookup"><span data-stu-id="5dfc9-113">*[content]*</span></span>|<span data-ttu-id="5dfc9-114">*Thiselementcanbeyoksayıldı* , yoksayılabilir olarak işaretlenmiş.</span><span class="sxs-lookup"><span data-stu-id="5dfc9-114">*ThisElementCanBeIgnored* is marked ignorable.</span></span> <span data-ttu-id="5dfc9-115">İşlemci bu öğeyi yok saysa, *[Content]* *nesne*tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="5dfc9-115">If the processor ignores that element, *[content]* is processed by *object*.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5dfc9-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5dfc9-116">Remarks</span></span>  
 <span data-ttu-id="5dfc9-117">Varsayılan olarak, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci yoksayılan bir öğe içindeki içeriği yoksayar.</span><span class="sxs-lookup"><span data-stu-id="5dfc9-117">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="5dfc9-118">Tarafından `mc:ProcessContent`belirli bir öğe belirtebilirsiniz ve bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci, yoksayılan öğe içindeki içeriği işlemeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="5dfc9-118">You can specify a specific element by `mc:ProcessContent`, and a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will continue to process the content within the ignored element.</span></span> <span data-ttu-id="5dfc9-119">Bu, genellikle içerik birkaç etiket içinde iç içe ise, en az biri yoksayılabilir ve en az bir tane yok sayılabilir olmayan bir şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5dfc9-119">This would typically be used if the content is nested within several tags, at least one of which is ignorable and at least one of which is not ignorable.</span></span>  
  
 <span data-ttu-id="5dfc9-120">Öznitelikte bir boşluk ayırıcısı kullanılarak birden çok önek belirtilebilir, örneğin: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.</span><span class="sxs-lookup"><span data-stu-id="5dfc9-120">Multiple prefixes may be specified in the attribute, using a space separator, for example: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.</span></span>  
  
 <span data-ttu-id="5dfc9-121">Ad `http://schemas.openxmlformats.org/markup-compatibility/2006` alanı, SDK 'nın bu alanı içinde belgelenmeyen diğer öğeleri ve öznitelikleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5dfc9-121">The `http://schemas.openxmlformats.org/markup-compatibility/2006` namespace defines other elements and attributes that are not documented within this area of the SDK.</span></span> <span data-ttu-id="5dfc9-122">Daha fazla bilgi için bkz. [XML biçimlendirme uyumluluğu belirtimi](https://go.microsoft.com/fwlink/?LinkId=73824).</span><span class="sxs-lookup"><span data-stu-id="5dfc9-122">For more information, see [XML Markup Compatibility Specification](https://go.microsoft.com/fwlink/?LinkId=73824).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dfc9-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5dfc9-123">See also</span></span>

- [<span data-ttu-id="5dfc9-124">mc:Ignorable Özniteliği</span><span class="sxs-lookup"><span data-stu-id="5dfc9-124">mc:Ignorable Attribute</span></span>](mc-ignorable-attribute.md)
- [<span data-ttu-id="5dfc9-125">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="5dfc9-125">XAML Overview (WPF)</span></span>](xaml-overview-wpf.md)
