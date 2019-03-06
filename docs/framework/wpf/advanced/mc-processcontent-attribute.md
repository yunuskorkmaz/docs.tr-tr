---
title: mc:ProcessContent Özniteliği
ms.date: 03/30/2017
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
ms.openlocfilehash: a9af18d1fac9101a75ac16918adf8e86ef7d2ba4
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357384"
---
# <a name="mcprocesscontent-attribute"></a><span data-ttu-id="044c6-102">mc:ProcessContent Özniteliği</span><span class="sxs-lookup"><span data-stu-id="044c6-102">mc:ProcessContent Attribute</span></span>
<span data-ttu-id="044c6-103">Belirten [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öğeleri hala olmalıdır içeriği ilgili üst öğeler tarafından işlenen en yakın üst öğe tarafından gözardı edilebilir olsa bile bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] belirtme nedeniyle İşlemci [mc: Ignorable özniteliği](mc-ignorable-attribute.md) .</span><span class="sxs-lookup"><span data-stu-id="044c6-103">Specifies which [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements should still have content processed by relevant parent elements, even if the immediate parent element may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor due to specifying [mc:Ignorable Attribute](mc-ignorable-attribute.md).</span></span> <span data-ttu-id="044c6-104">`mc:ProcessContent` Özniteliği işaretleme uyumluluk destekler ve özel ad alanı eşlemesi için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sürüm oluşturma.</span><span class="sxs-lookup"><span data-stu-id="044c6-104">The `mc:ProcessContent` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="044c6-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="044c6-105">XAML Attribute Usage</span></span>  
  
```  
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
  
## <a name="xaml-values"></a><span data-ttu-id="044c6-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="044c6-106">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="044c6-107">*ignorablePrefix*</span><span class="sxs-lookup"><span data-stu-id="044c6-107">*ignorablePrefix*</span></span>|<span data-ttu-id="044c6-108">XML 1.0 belirtimi başına herhangi geçerli bir önek dizesi.</span><span class="sxs-lookup"><span data-stu-id="044c6-108">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="044c6-109">*ignorableUri*</span><span class="sxs-lookup"><span data-stu-id="044c6-109">*ignorableUri*</span></span>|<span data-ttu-id="044c6-110">XML 1.0 belirtimi başına bir ad atamak için geçerli bir URI.</span><span class="sxs-lookup"><span data-stu-id="044c6-110">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="044c6-111">*ThisElementCanBeIgnored*</span><span class="sxs-lookup"><span data-stu-id="044c6-111">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="044c6-112">Tarafından göz ardı edilebilir öğenin [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] işlemcisi uygulamaları, temel alınan türü çözümlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="044c6-112">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
|<span data-ttu-id="044c6-113">*[content]*</span><span class="sxs-lookup"><span data-stu-id="044c6-113">*[content]*</span></span>|<span data-ttu-id="044c6-114">*ThisElementCanBeIgnored* yoksayılabilir olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="044c6-114">*ThisElementCanBeIgnored* is marked ignorable.</span></span> <span data-ttu-id="044c6-115">Bu öğe işlemci yoksayar, *[content]* tarafından işlenen *nesne*.</span><span class="sxs-lookup"><span data-stu-id="044c6-115">If the processor ignores that element, *[content]* is processed by *object*.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="044c6-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="044c6-116">Remarks</span></span>  
 <span data-ttu-id="044c6-117">Varsayılan olarak, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci yoksayılan öğe içindeki içeriği yoksayar.</span><span class="sxs-lookup"><span data-stu-id="044c6-117">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="044c6-118">Belirli bir öğeyi belirtebilirsiniz `mc:ProcessContent`ve [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci yoksayılan öğe içinde içerik işlemeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="044c6-118">You can specify a specific element by `mc:ProcessContent`, and a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will continue to process the content within the ignored element.</span></span> <span data-ttu-id="044c6-119">İçeriği en az biri Ignorable olan ve en az biri Ignorable değil birkaç etiket içinde iç içe ise, bu genellikle kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="044c6-119">This would typically be used if the content is nested within several tags, at least one of which is ignorable and at least one of which is not ignorable.</span></span>  
  
 <span data-ttu-id="044c6-120">Alan ayırıcı, örneğin kullanarak özniteliğinde birden çok ön ekleri belirtilebilir: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.</span><span class="sxs-lookup"><span data-stu-id="044c6-120">Multiple prefixes may be specified in the attribute, using a space separator, for example: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.</span></span>  
  
 <span data-ttu-id="044c6-121">[!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] Diğer öğeleri ve bu alanı içinde belgelenmeyen öznitelikleri ad alanını tanımlayan [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span><span class="sxs-lookup"><span data-stu-id="044c6-121">The [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] namespace defines other elements and attributes that are not documented within this area of the [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span></span> <span data-ttu-id="044c6-122">Daha fazla bilgi için [XML işaretleme Uyumluluk Belirtimi](https://go.microsoft.com/fwlink/?LinkId=73824).</span><span class="sxs-lookup"><span data-stu-id="044c6-122">For more information, see [XML Markup Compatibility Specification](https://go.microsoft.com/fwlink/?LinkId=73824).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="044c6-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="044c6-123">See also</span></span>
- [<span data-ttu-id="044c6-124">mc:Ignorable Özniteliği</span><span class="sxs-lookup"><span data-stu-id="044c6-124">mc:Ignorable Attribute</span></span>](mc-ignorable-attribute.md)
- [<span data-ttu-id="044c6-125">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="044c6-125">XAML Overview (WPF)</span></span>](xaml-overview-wpf.md)
