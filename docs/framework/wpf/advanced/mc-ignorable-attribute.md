---
title: mc:Ignorable Özniteliği
ms.date: 03/30/2017
helpviewer_keywords:
- mc XML namespace prefix [WPF]
- mc:Ignorable attribute
- XML [WPF], mc namespace prefix
- XAML [WPF], mc:Ignorable attribute
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: acd9a6ef-b7ca-4146-abb6-60f3b366e9ec
ms.openlocfilehash: b68909d94ad8cc5bba75b2c520db82c5ccf1b922
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206181"
---
# <a name="mcignorable-attribute"></a><span data-ttu-id="46381-102">mc:Ignorable Özniteliği</span><span class="sxs-lookup"><span data-stu-id="46381-102">mc:Ignorable Attribute</span></span>
<span data-ttu-id="46381-103">Bir biçimlendirme dosyasında karşılaşılan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] adalanıöneklerinebirişlemcitarafındanyoksayılacağınıbelirtir.[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46381-103">Specifies which [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace prefixes encountered in a markup file may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="46381-104">Öznitelik `mc:Ignorable` , hem özel ad alanı eşlemesi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] hem de sürüm oluşturma için biçimlendirme uyumluluğunu destekler.</span><span class="sxs-lookup"><span data-stu-id="46381-104">The `mc:Ignorable` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage-single-prefix"></a><span data-ttu-id="46381-105">XAML öznitelik kullanımı (tek ön ek)</span><span class="sxs-lookup"><span data-stu-id="46381-105">XAML Attribute Usage (Single Prefix)</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-attribute-usage-two-prefixes"></a><span data-ttu-id="46381-106">XAML öznitelik kullanımı (Iki ön ek)</span><span class="sxs-lookup"><span data-stu-id="46381-106">XAML Attribute Usage (Two Prefixes)</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix1="ignorableUri"  
  xmlns:ignorablePrefix2="ignorableUri2"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix1 ignorablePrefix2"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="46381-107">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="46381-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="46381-108">*ıgnorableprefix, ignorablePrefix1, vb.*</span><span class="sxs-lookup"><span data-stu-id="46381-108">*ignorablePrefix, ignorablePrefix1, etc.*</span></span>|<span data-ttu-id="46381-109">XML 1,0 belirtimine göre geçerli herhangi bir ön ek dizesi.</span><span class="sxs-lookup"><span data-stu-id="46381-109">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="46381-110">*ıgnorableuri*</span><span class="sxs-lookup"><span data-stu-id="46381-110">*ignorableUri*</span></span>|<span data-ttu-id="46381-111">XML 1,0 belirtimine göre bir ad alanı atamak için geçerli bir URI.</span><span class="sxs-lookup"><span data-stu-id="46381-111">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="46381-112">*Thiselementcanbeyoksayıldı*</span><span class="sxs-lookup"><span data-stu-id="46381-112">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="46381-113">Temel alınan tür çözümlenemiyorsa, işlemci [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] uygulamaları tarafından yoksayılabilir bir öğe.</span><span class="sxs-lookup"><span data-stu-id="46381-113">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46381-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="46381-114">Remarks</span></span>  
 <span data-ttu-id="46381-115">Ad alanı ön eki, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uyumluluk ad alanını `http://schemas.openxmlformats.org/markup-compatibility/2006`eşlerken kullanılacak önerilen önek kuralıdır. `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46381-115">The `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace prefix is the recommended prefix convention to use when mapping the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] compatibility namespace `http://schemas.openxmlformats.org/markup-compatibility/2006`.</span></span>  
  
 <span data-ttu-id="46381-116">Öğe adının `mc:Ignorable` önek kısmının, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcinin işlendiği sırada hata oluşturmayacağını, öğe veya öznitelikler.</span><span class="sxs-lookup"><span data-stu-id="46381-116">Elements or attributes where the prefix portion of the element name are identified as `mc:Ignorable` will not raise errors when processed by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="46381-117">Bu öznitelik, temel alınan bir tür veya programlama yapısına çözümlenemiyorsa, bu öğe yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="46381-117">If that attribute could not be resolved to an underlying type or programming construct, then that element is ignored.</span></span> <span data-ttu-id="46381-118">Ancak yoksayılan öğelerin, bu öğenin işlenmediği yan etkileri olan ek öğe gereksinimleri için ek ayrıştırma hataları ürettiğine de devam edebileceğine unutmayın.</span><span class="sxs-lookup"><span data-stu-id="46381-118">Note however that ignored elements might still generate additional parsing errors for additional element requirements that are side effects of that element not being processed.</span></span> <span data-ttu-id="46381-119">Örneğin, belirli bir öğe içerik modeli tam olarak bir alt öğe gerektirebilir, ancak belirtilen alt öğe `mc:Ignorable` bir ön ekse ve belirtilen alt öğe bir tür [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] olarak çözümlenemiyorsa, işlemci bir hata oluştur.</span><span class="sxs-lookup"><span data-stu-id="46381-119">For instance, a particular element content model might require exactly one child element, but if the specified child element was in an `mc:Ignorable` prefix, and the specified child element could not be resolved to a type, then the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor might raise an error.</span></span>  
  
 <span data-ttu-id="46381-120">`mc:Ignorable`yalnızca tanımlayıcı dizelerine ad alanı eşlemeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="46381-120">`mc:Ignorable` only applies to namespace mappings to identifier strings.</span></span> <span data-ttu-id="46381-121">`mc:Ignorable`, bir CLR ad alanı ve derleme (veya varsayılan olarak geçerli yürütülebilir dosya için derleme) belirten derlemelerdeki ad alanı eşlemeleri için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="46381-121">`mc:Ignorable` does not apply to namespace mappings into assemblies, which specify a CLR namespace and an assembly (or default to the current executable as the assembly).</span></span>  
  
 <span data-ttu-id="46381-122">Bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci uygularsınız, işlemci uygulamanız, olarak `mc:Ignorable`tanımlanan bir ön ek tarafından nitelenen herhangi bir öğe veya öznitelik için tür çözünürlüğünde ayrıştırma veya işleme hatalarını yükseltmemelidir.</span><span class="sxs-lookup"><span data-stu-id="46381-122">If you are implementing a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor, your processor implementation must not raise parsing or processing errors on type resolution for any element or attribute that is qualified by a prefix that is identified as `mc:Ignorable`.</span></span> <span data-ttu-id="46381-123">Ancak işlemci uygulamanız, daha önce verilen tek alt öğe örneği gibi, yükleme veya işleme başarısız olan bir öğenin ikincil sonucu olan özel durumları yine de oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="46381-123">But your processor implementation can still raise exceptions that are a secondary result of an element failing to load or be processed, such as the one-child element example given earlier.</span></span>  
  
 <span data-ttu-id="46381-124">Varsayılan olarak, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci yoksayılan bir öğe içindeki içeriği yoksayar.</span><span class="sxs-lookup"><span data-stu-id="46381-124">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="46381-125">Ancak, bir sonraki kullanılabilir üst öğe tarafından yoksayılan bir öğe içinde içeriğin sürekli işlenmesini gerektirmek için, [mc: ProcessContent özniteliği](mc-processcontent-attribute.md)ek özniteliğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46381-125">However, you can specify an additional attribute, [mc:ProcessContent Attribute](mc-processcontent-attribute.md), to require continued processing of content within an ignored element by the next available parent element.</span></span>  
  
 <span data-ttu-id="46381-126">Bir veya daha fazla boşluk karakteri ayırıcı olarak kullanılarak özniteliğinde birden çok önek belirtilebilir, örneğin: `mc:Ignorable="ignore1 ignore2"`.</span><span class="sxs-lookup"><span data-stu-id="46381-126">Multiple prefixes can be specified in the attribute, using one or more white-space characters as the separator, for example: `mc:Ignorable="ignore1 ignore2"`.</span></span>  

 <span data-ttu-id="46381-127">Ad `http://schemas.openxmlformats.org/markup-compatibility/2006` alanı, SDK 'nın bu alanı içinde belgelenmeyen diğer öğeleri ve öznitelikleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="46381-127">The `http://schemas.openxmlformats.org/markup-compatibility/2006` namespace defines other elements and attributes that are not documented within this area of the SDK.</span></span> <span data-ttu-id="46381-128">Daha fazla bilgi için bkz. [XML biçimlendirme uyumluluğu belirtimi](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).</span><span class="sxs-lookup"><span data-stu-id="46381-128">For more information, see [XML Markup Compatibility Specification](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46381-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46381-129">See also</span></span>

- <xref:System.Windows.Markup.XamlReader>
- [<span data-ttu-id="46381-130">PresentationOptions:Freeze Özniteliği</span><span class="sxs-lookup"><span data-stu-id="46381-130">PresentationOptions:Freeze Attribute</span></span>](presentationoptions-freeze-attribute.md)
- [<span data-ttu-id="46381-131">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="46381-131">XAML Overview (WPF)</span></span>](xaml-overview-wpf.md)
- [<span data-ttu-id="46381-132">WPF'deki Belgeler</span><span class="sxs-lookup"><span data-stu-id="46381-132">Documents in WPF</span></span>](documents-in-wpf.md)
