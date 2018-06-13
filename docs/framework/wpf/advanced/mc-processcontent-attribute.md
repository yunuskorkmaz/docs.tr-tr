---
title: mc:ProcessContent Özniteliği
ms.date: 03/30/2017
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
ms.openlocfilehash: 2e93734b8ab4aefca080736db3a512f272625271
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545259"
---
# <a name="mcprocesscontent-attribute"></a><span data-ttu-id="47698-102">mc:ProcessContent Özniteliği</span><span class="sxs-lookup"><span data-stu-id="47698-102">mc:ProcessContent Attribute</span></span>
<span data-ttu-id="47698-103">Belirten [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öğeleri hala olmalıdır ilgili üst öğeler tarafından işlenen İçerik en yakın üst öğe tarafından yoksayılabilir olsa bile bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] belirtme nedeniyle İşlemci [mc: yoksayılabilir özniteliği](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) .</span><span class="sxs-lookup"><span data-stu-id="47698-103">Specifies which [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements should still have content processed by relevant parent elements, even if the immediate parent element may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor due to specifying [mc:Ignorable Attribute](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md).</span></span> <span data-ttu-id="47698-104">`mc:ProcessContent` Özniteliği, hem hem de özel ad alanı eşlemesi için biçimlendirme uyumluluğunu destekler [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sürüm oluşturma.</span><span class="sxs-lookup"><span data-stu-id="47698-104">The `mc:ProcessContent` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="47698-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="47698-105">XAML Attribute Usage</span></span>  
  
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
  
## <a name="xaml-values"></a><span data-ttu-id="47698-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="47698-106">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="47698-107">*ignorablePrefix*</span><span class="sxs-lookup"><span data-stu-id="47698-107">*ignorablePrefix*</span></span>|<span data-ttu-id="47698-108">XML 1.0 belirtimi başına herhangi geçerli önek dizesi.</span><span class="sxs-lookup"><span data-stu-id="47698-108">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="47698-109">*ignorableUri*</span><span class="sxs-lookup"><span data-stu-id="47698-109">*ignorableUri*</span></span>|<span data-ttu-id="47698-110">XML 1.0 belirtimi başına bir ad atamak için geçerli bir URI.</span><span class="sxs-lookup"><span data-stu-id="47698-110">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="47698-111">*ThisElementCanBeIgnored*</span><span class="sxs-lookup"><span data-stu-id="47698-111">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="47698-112">Tarafından göz ardı edilebilir bir öğe [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] temel alınan tür çözümlenemiyorsa işlemcisi uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="47698-112">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
|<span data-ttu-id="47698-113">*[content]*</span><span class="sxs-lookup"><span data-stu-id="47698-113">*[content]*</span></span>|<span data-ttu-id="47698-114">*ThisElementCanBeIgnored* yoksayılabilir olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="47698-114">*ThisElementCanBeIgnored* is marked ignorable.</span></span> <span data-ttu-id="47698-115">Bu öğe işlemci yoksayar, *[content]* tarafından işlenen *nesne*.</span><span class="sxs-lookup"><span data-stu-id="47698-115">If the processor ignores that element, *[content]* is processed by *object*.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47698-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="47698-116">Remarks</span></span>  
 <span data-ttu-id="47698-117">Varsayılan olarak, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci yoksayılan öğe içindeki içeriği yoksayar.</span><span class="sxs-lookup"><span data-stu-id="47698-117">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="47698-118">Belirli bir öğeyi belirtebilirsiniz `mc:ProcessContent`ve bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci yoksayılan öğe içinde içeriği işlemeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="47698-118">You can specify a specific element by `mc:ProcessContent`, and a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will continue to process the content within the ignored element.</span></span> <span data-ttu-id="47698-119">İçeriği en az biri yoksayılabilir olan ve en az biri yoksayılabilir değil birkaç etiket içinde iç içe ise, bu genellikle kullanılır.</span><span class="sxs-lookup"><span data-stu-id="47698-119">This would typically be used if the content is nested within several tags, at least one of which is ignorable and at least one of which is not ignorable.</span></span>  
  
 <span data-ttu-id="47698-120">Birden çok önekleri alan ayırıcı örneğin kullanarak özniteliği belirtilebilir: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.</span><span class="sxs-lookup"><span data-stu-id="47698-120">Multiple prefixes may be specified in the attribute, using a space separator, for example: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.</span></span>  
  
 <span data-ttu-id="47698-121">[!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] Ad alanını tanımlayan diğer öğeleri ve bu alanda belgelenmemiş öznitelikleri [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span><span class="sxs-lookup"><span data-stu-id="47698-121">The [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] namespace defines other elements and attributes that are not documented within this area of the [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span></span> <span data-ttu-id="47698-122">Daha fazla bilgi için bkz: [XML Biçimlendirmesi Uyumluluk Belirtimi](http://go.microsoft.com/fwlink/?LinkId=73824).</span><span class="sxs-lookup"><span data-stu-id="47698-122">For more information, see [XML Markup Compatibility Specification](http://go.microsoft.com/fwlink/?LinkId=73824).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47698-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="47698-123">See Also</span></span>  
 [<span data-ttu-id="47698-124">mc:Ignorable Özniteliği</span><span class="sxs-lookup"><span data-stu-id="47698-124">mc:Ignorable Attribute</span></span>](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)  
 [<span data-ttu-id="47698-125">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="47698-125">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
