---
title: "mc:ProcessContent Özniteliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1fe43e2450c35d976db7a188f854f7864f298afc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="mcprocesscontent-attribute"></a><span data-ttu-id="b72db-102">mc:ProcessContent Özniteliği</span><span class="sxs-lookup"><span data-stu-id="b72db-102">mc:ProcessContent Attribute</span></span>
<span data-ttu-id="b72db-103">Belirten [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öğeleri hala olmalıdır ilgili üst öğeler tarafından işlenen İçerik en yakın üst öğe tarafından yoksayılabilir olsa bile bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] belirtme nedeniyle İşlemci [mc: yoksayılabilir özniteliği](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) .</span><span class="sxs-lookup"><span data-stu-id="b72db-103">Specifies which [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements should still have content processed by relevant parent elements, even if the immediate parent element may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor due to specifying [mc:Ignorable Attribute](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md).</span></span> <span data-ttu-id="b72db-104">`mc:ProcessContent` Özniteliği, hem hem de özel ad alanı eşlemesi için biçimlendirme uyumluluğunu destekler [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sürüm oluşturma.</span><span class="sxs-lookup"><span data-stu-id="b72db-104">The `mc:ProcessContent` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="b72db-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="b72db-105">XAML Attribute Usage</span></span>  
  
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
  
## <a name="xaml-values"></a><span data-ttu-id="b72db-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="b72db-106">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b72db-107">*ignorablePrefix*</span><span class="sxs-lookup"><span data-stu-id="b72db-107">*ignorablePrefix*</span></span>|<span data-ttu-id="b72db-108">XML 1.0 belirtimi başına herhangi geçerli önek dizesi.</span><span class="sxs-lookup"><span data-stu-id="b72db-108">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="b72db-109">*ignorableUri*</span><span class="sxs-lookup"><span data-stu-id="b72db-109">*ignorableUri*</span></span>|<span data-ttu-id="b72db-110">XML 1.0 belirtimi başına bir ad atamak için geçerli bir URI.</span><span class="sxs-lookup"><span data-stu-id="b72db-110">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="b72db-111">*ThisElementCanBeIgnored*</span><span class="sxs-lookup"><span data-stu-id="b72db-111">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="b72db-112">Tarafından göz ardı edilebilir bir öğe [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] temel alınan tür çözümlenemiyorsa işlemcisi uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="b72db-112">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
|<span data-ttu-id="b72db-113">*[content]*</span><span class="sxs-lookup"><span data-stu-id="b72db-113">*[content]*</span></span>|<span data-ttu-id="b72db-114">*ThisElementCanBeIgnored* yoksayılabilir olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="b72db-114">*ThisElementCanBeIgnored* is marked ignorable.</span></span> <span data-ttu-id="b72db-115">Bu öğe işlemci yoksayar, *[content]* tarafından işlenen *nesne*.</span><span class="sxs-lookup"><span data-stu-id="b72db-115">If the processor ignores that element, *[content]* is processed by *object*.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b72db-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b72db-116">Remarks</span></span>  
 <span data-ttu-id="b72db-117">Varsayılan olarak, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci yoksayılan öğe içindeki içeriği yoksayar.</span><span class="sxs-lookup"><span data-stu-id="b72db-117">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="b72db-118">Belirli bir öğeyi belirtebilirsiniz `mc:ProcessContent`ve bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci yoksayılan öğe içinde içeriği işlemeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="b72db-118">You can specify a specific element by `mc:ProcessContent`, and a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will continue to process the content within the ignored element.</span></span> <span data-ttu-id="b72db-119">İçeriği en az biri yoksayılabilir olan ve en az biri yoksayılabilir değil birkaç etiket içinde iç içe ise, bu genellikle kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b72db-119">This would typically be used if the content is nested within several tags, at least one of which is ignorable and at least one of which is not ignorable.</span></span>  
  
 <span data-ttu-id="b72db-120">Birden çok önekleri alan ayırıcı örneğin kullanarak özniteliği belirtilebilir: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.</span><span class="sxs-lookup"><span data-stu-id="b72db-120">Multiple prefixes may be specified in the attribute, using a space separator, for example: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.</span></span>  
  
 <span data-ttu-id="b72db-121">[!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] Ad alanını tanımlayan diğer öğeleri ve bu alanda belgelenmemiş öznitelikleri [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b72db-121">The [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] namespace defines other elements and attributes that are not documented within this area of the [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span></span> <span data-ttu-id="b72db-122">Daha fazla bilgi için bkz: [XML Biçimlendirmesi Uyumluluk Belirtimi](http://go.microsoft.com/fwlink/?LinkId=73824).</span><span class="sxs-lookup"><span data-stu-id="b72db-122">For more information, see [XML Markup Compatibility Specification](http://go.microsoft.com/fwlink/?LinkId=73824).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b72db-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b72db-123">See Also</span></span>  
 [<span data-ttu-id="b72db-124">mc:Ignorable Özniteliği</span><span class="sxs-lookup"><span data-stu-id="b72db-124">mc:Ignorable Attribute</span></span>](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)  
 [<span data-ttu-id="b72db-125">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="b72db-125">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
