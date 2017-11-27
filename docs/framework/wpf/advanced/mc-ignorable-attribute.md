---
title: "mc:Ignorable Özniteliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mc XML namespace prefix [WPF]
- mc:Ignorable attribute
- XML [WPF], mc namespace prefix
- XAML [WPF], mc:Ignorable attribute
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: acd9a6ef-b7ca-4146-abb6-60f3b366e9ec
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3be5949ee26fbb21d913a7aefe2664202c5bef38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="mcignorable-attribute"></a><span data-ttu-id="2fccb-102">mc:Ignorable Özniteliği</span><span class="sxs-lookup"><span data-stu-id="2fccb-102">mc:Ignorable Attribute</span></span>
<span data-ttu-id="2fccb-103">Belirten [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] biçimlendirme dosyasında karşılaşılan ad alanı öneklerini dikkate tarafından bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci.</span><span class="sxs-lookup"><span data-stu-id="2fccb-103">Specifies which [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace prefixes encountered in a markup file may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="2fccb-104">`mc:Ignorable` Özniteliği, hem hem de özel ad alanı eşlemesi için biçimlendirme uyumluluğunu destekler [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sürüm oluşturma.</span><span class="sxs-lookup"><span data-stu-id="2fccb-104">The `mc:Ignorable` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage-single-prefix"></a><span data-ttu-id="2fccb-105">XAML öznitelik kullanımı (tek önek)</span><span class="sxs-lookup"><span data-stu-id="2fccb-105">XAML Attribute Usage (Single Prefix)</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-attribute-usage-two-prefixes"></a><span data-ttu-id="2fccb-106">XAML öznitelik kullanımı (iki önek)</span><span class="sxs-lookup"><span data-stu-id="2fccb-106">XAML Attribute Usage (Two Prefixes)</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix1="ignorableUri"  
  xmlns:ignorablePrefix2="ignorableUri2"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix1 ignorablePrefix2"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="2fccb-107">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="2fccb-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2fccb-108">*ignorablePrefix, ignorablePrefix1, vb.*</span><span class="sxs-lookup"><span data-stu-id="2fccb-108">*ignorablePrefix, ignorablePrefix1, etc.*</span></span>|<span data-ttu-id="2fccb-109">XML 1.0 belirtimi başına herhangi geçerli önek dizesi.</span><span class="sxs-lookup"><span data-stu-id="2fccb-109">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="2fccb-110">*ignorableUri*</span><span class="sxs-lookup"><span data-stu-id="2fccb-110">*ignorableUri*</span></span>|<span data-ttu-id="2fccb-111">XML 1.0 belirtimi başına bir ad atamak için geçerli bir URI.</span><span class="sxs-lookup"><span data-stu-id="2fccb-111">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="2fccb-112">*ThisElementCanBeIgnored*</span><span class="sxs-lookup"><span data-stu-id="2fccb-112">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="2fccb-113">Tarafından göz ardı edilebilir bir öğe [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] temel alınan tür çözümlenemiyorsa işlemcisi uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="2fccb-113">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2fccb-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2fccb-114">Remarks</span></span>  
 <span data-ttu-id="2fccb-115">`mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] Ad alanı öneki olan eşlenirken kullanmak için önerilen öneki kuralı [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uyumluluk ad alanı [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2fccb-115">The `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace prefix is the recommended prefix convention to use when mapping the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] compatibility namespace [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)].</span></span>  
  
 <span data-ttu-id="2fccb-116">Öğeleri veya burada öğesi adının öneki bölümü olarak tanımlandığında öznitelikleri `mc:Ignorable` tarafından işlendiğinde hata oluşturmaz bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci.</span><span class="sxs-lookup"><span data-stu-id="2fccb-116">Elements or attributes where the prefix portion of the element name are identified as `mc:Ignorable` will not raise errors when processed by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="2fccb-117">Bir temel alınan tür veya programlama yapı bu öznitelik çözümlenemedi, o öğeye göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="2fccb-117">If that attribute could not be resolved to an underlying type or programming construct, then that element is ignored.</span></span> <span data-ttu-id="2fccb-118">Ancak yoksayılan öğelerin işlenmeyen o öğenin yan etkileri olan ek öğe gereksinimleri için ek ayrıştırma hataları oluşturabilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2fccb-118">Note however that ignored elements might still generate additional parsing errors for additional element requirements that are side effects of that element not being processed.</span></span> <span data-ttu-id="2fccb-119">Örneğin, belirli bir öğenin içerik modeli belirtilen alt öğe içinde olup olmadığını ancak tam olarak bir alt öğe gerektirebilir bir `mc:Ignorable` öneki ve belirtilen alt öğe bir türe çözümlenemedi sonra [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci olabilir bir hata oluştur.</span><span class="sxs-lookup"><span data-stu-id="2fccb-119">For instance, a particular element content model might require exactly one child element, but if the specified child element was in an `mc:Ignorable` prefix, and the specified child element could not be resolved to a type, then the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor might raise an error.</span></span>  
  
 <span data-ttu-id="2fccb-120">`mc:Ignorable`yalnızca ad alanı tanımlayıcı dizelere eşlemeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="2fccb-120">`mc:Ignorable` only applies to namespace mappings to identifier strings.</span></span> <span data-ttu-id="2fccb-121">`mc:Ignorable`ad alanı eşlemesi belirtmek derlemeye uygulanmaz bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] ad alanı ve bir derleme (veya varsayılan derleme gibi geçerli yürütülebilir).</span><span class="sxs-lookup"><span data-stu-id="2fccb-121">`mc:Ignorable` does not apply to namespace mappings into assemblies, which specify a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] namespace and an assembly (or default to the current executable as the assembly).</span></span>  
  
 <span data-ttu-id="2fccb-122">Uyguluyorsanız bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci, işlemci uygulamanız gerekir değil Yükselt ayrıştırma veya herhangi bir öğe veya olarak tanımlanan bir önek nitelenen öznitelik türü çözümlenmek hatalarda işlem `mc:Ignorable`.</span><span class="sxs-lookup"><span data-stu-id="2fccb-122">If you are implementing a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor, your processor implementation must not raise parsing or processing errors on type resolution for any element or attribute that is qualified by a prefix that is identified as `mc:Ignorable`.</span></span> <span data-ttu-id="2fccb-123">Ancak, işlemci uygulamanız yüklenemiyor veya daha önce verilen bir alt öğe örneği gibi işlenmesi başarısız olan bir öğenin ikincil sonucunda oluşan özel durumlar ortaya çıkarabilir.</span><span class="sxs-lookup"><span data-stu-id="2fccb-123">But your processor implementation can still raise exceptions that are a secondary result of an element failing to load or be processed, such as the one-child element example given earlier.</span></span>  
  
 <span data-ttu-id="2fccb-124">Varsayılan olarak, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci yoksayılan öğe içindeki içeriği yoksayar.</span><span class="sxs-lookup"><span data-stu-id="2fccb-124">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="2fccb-125">Bununla birlikte, ek bir öznitelik belirtebilirsiniz [mc: ProcessContent özniteliği](../../../../docs/framework/wpf/advanced/mc-processcontent-attribute.md)sonraki kullanılabilir üst öğe tarafından yoksayılan öğe içindeki içeriğin sürekli işlenmesini gerektirmek için.</span><span class="sxs-lookup"><span data-stu-id="2fccb-125">However, you can specify an additional attribute, [mc:ProcessContent Attribute](../../../../docs/framework/wpf/advanced/mc-processcontent-attribute.md), to require continued processing of content within an ignored element by the next available parent element.</span></span>  
  
 <span data-ttu-id="2fccb-126">Birden çok ön eklerin bir veya daha fazla boşluk karakterleri ayırıcı olarak örneğin kullanarak özniteliği belirtilebilir: `mc:Ignorable="ignore1 ignore2"`.</span><span class="sxs-lookup"><span data-stu-id="2fccb-126">Multiple prefixes can be specified in the attribute, using one or more whitespace characters as the separator, for example: `mc:Ignorable="ignore1 ignore2"`.</span></span>  
  
 <span data-ttu-id="2fccb-127">[!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] Ad alanını tanımlayan diğer öğeleri ve bu alanda belgelenmemiş öznitelikleri [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2fccb-127">The [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] namespace defines other elements and attributes that are not documented within this area of the [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span></span> <span data-ttu-id="2fccb-128">Daha fazla bilgi için bkz: [XML Biçimlendirmesi Uyumluluk Belirtimi](http://go.microsoft.com/fwlink/?LinkId=73824).</span><span class="sxs-lookup"><span data-stu-id="2fccb-128">For more information, see [XML Markup Compatibility Specification](http://go.microsoft.com/fwlink/?LinkId=73824).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fccb-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2fccb-129">See Also</span></span>  
 <xref:System.Windows.Markup.XamlReader>  
 [<span data-ttu-id="2fccb-130">PresentationOptions: Freeze özniteliği</span><span class="sxs-lookup"><span data-stu-id="2fccb-130">PresentationOptions:Freeze Attribute</span></span>](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)  
 [<span data-ttu-id="2fccb-131">XAML genel bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="2fccb-131">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="2fccb-132">WPF belgeleri</span><span class="sxs-lookup"><span data-stu-id="2fccb-132">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)
