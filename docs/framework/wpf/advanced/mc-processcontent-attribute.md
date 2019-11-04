---
title: mc:ProcessContent Özniteliği
ms.date: 03/30/2017
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
ms.openlocfilehash: dde304cc2b9db9cb01f9264ca1359b8979512cfa
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458785"
---
# <a name="mcprocesscontent-attribute"></a><span data-ttu-id="584d6-102">mc:ProcessContent Özniteliği</span><span class="sxs-lookup"><span data-stu-id="584d6-102">mc:ProcessContent Attribute</span></span>
<span data-ttu-id="584d6-103">En üst öğe, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisi tarafından, [mc: Ignorable özniteliği](mc-ignorable-attribute.md)belirtilirken yok sayılsa bile, hangi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öğelerinin hala ilgili üst öğeler tarafından işlenmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="584d6-103">Specifies which [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements should still have content processed by relevant parent elements, even if the immediate parent element may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor due to specifying [mc:Ignorable Attribute](mc-ignorable-attribute.md).</span></span> <span data-ttu-id="584d6-104">`mc:ProcessContent` özniteliği, hem özel ad alanı eşlemesi hem de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sürümü oluşturma için biçimlendirme uyumluluğunu destekler.</span><span class="sxs-lookup"><span data-stu-id="584d6-104">The `mc:ProcessContent` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="584d6-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="584d6-105">XAML Attribute Usage</span></span>  
  
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
  
## <a name="xaml-values"></a><span data-ttu-id="584d6-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="584d6-106">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="584d6-107">*ıgnorableprefix*</span><span class="sxs-lookup"><span data-stu-id="584d6-107">*ignorablePrefix*</span></span>|<span data-ttu-id="584d6-108">XML 1,0 belirtimine göre geçerli herhangi bir ön ek dizesi.</span><span class="sxs-lookup"><span data-stu-id="584d6-108">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="584d6-109">*ıgnorableuri*</span><span class="sxs-lookup"><span data-stu-id="584d6-109">*ignorableUri*</span></span>|<span data-ttu-id="584d6-110">XML 1,0 belirtimine göre bir ad alanı atamak için geçerli bir URI.</span><span class="sxs-lookup"><span data-stu-id="584d6-110">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="584d6-111">*Thiselementcanbeyoksayıldı*</span><span class="sxs-lookup"><span data-stu-id="584d6-111">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="584d6-112">Temel alınan tür çözümlenemiyorsa, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] işlemci uygulamaları tarafından yoksayılabilir bir öğe.</span><span class="sxs-lookup"><span data-stu-id="584d6-112">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
|<span data-ttu-id="584d6-113">*içeriði*</span><span class="sxs-lookup"><span data-stu-id="584d6-113">*[content]*</span></span>|<span data-ttu-id="584d6-114">*Thiselementcanbeyoksayıldı* , yoksayılabilir olarak işaretlenmiş.</span><span class="sxs-lookup"><span data-stu-id="584d6-114">*ThisElementCanBeIgnored* is marked ignorable.</span></span> <span data-ttu-id="584d6-115">İşlemci bu öğeyi yok saysa, *[Content]* *nesne*tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="584d6-115">If the processor ignores that element, *[content]* is processed by *object*.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="584d6-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="584d6-116">Remarks</span></span>  
 <span data-ttu-id="584d6-117">Varsayılan olarak, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisi yoksayılan bir öğe içindeki içeriği yoksayar.</span><span class="sxs-lookup"><span data-stu-id="584d6-117">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="584d6-118">`mc:ProcessContent`tarafından belirli bir öğe belirtebilirsiniz ve bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisi yoksayılan öğe içindeki içeriği işlemeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="584d6-118">You can specify a specific element by `mc:ProcessContent`, and a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will continue to process the content within the ignored element.</span></span> <span data-ttu-id="584d6-119">Bu, genellikle içerik birkaç etiket içinde iç içe ise, en az biri yoksayılabilir ve en az bir tane yok sayılabilir olmayan bir şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="584d6-119">This would typically be used if the content is nested within several tags, at least one of which is ignorable and at least one of which is not ignorable.</span></span>  
  
 <span data-ttu-id="584d6-120">Öznitelikte bir boşluk ayırıcısı kullanılarak birden çok önek belirtilebilir, örneğin: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.</span><span class="sxs-lookup"><span data-stu-id="584d6-120">Multiple prefixes may be specified in the attribute, using a space separator, for example: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.</span></span>  
  
 <span data-ttu-id="584d6-121">`http://schemas.openxmlformats.org/markup-compatibility/2006` ad alanı, SDK 'nın bu alanı içinde belgelenmeyen diğer öğeleri ve öznitelikleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="584d6-121">The `http://schemas.openxmlformats.org/markup-compatibility/2006` namespace defines other elements and attributes that are not documented within this area of the SDK.</span></span> <span data-ttu-id="584d6-122">Daha fazla bilgi için bkz. [XML biçimlendirme uyumluluğu belirtimi](https://go.microsoft.com/fwlink/?LinkId=73824).</span><span class="sxs-lookup"><span data-stu-id="584d6-122">For more information, see [XML Markup Compatibility Specification](https://go.microsoft.com/fwlink/?LinkId=73824).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="584d6-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="584d6-123">See also</span></span>

- [<span data-ttu-id="584d6-124">mc:Ignorable Özniteliği</span><span class="sxs-lookup"><span data-stu-id="584d6-124">mc:Ignorable Attribute</span></span>](mc-ignorable-attribute.md)
- [<span data-ttu-id="584d6-125">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="584d6-125">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
