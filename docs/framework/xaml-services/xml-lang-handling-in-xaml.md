---
title: XAML'de xml:lang İşleme
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: 886f4063fa8c793fdce93431a29219cf86078593
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562030"
---
# <a name="xmllang-handling-in-xaml"></a><span data-ttu-id="38f14-102">XAML'de xml:lang İşleme</span><span class="sxs-lookup"><span data-stu-id="38f14-102">xml:lang Handling in XAML</span></span>
<span data-ttu-id="38f14-103">`xml:lang` Özniteliği bir [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)]-XML'deki bir öğenin dil ve kültür bilgilerini bildiren tanımlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="38f14-103">The `xml:lang` attribute is an [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)]-defined attribute that declares the language and culture information for an element in XML.</span></span> <span data-ttu-id="38f14-104">Bu öznitelik ile aynı anlamı XAML'de devam ederse; Ancak, bazı ek hususlar geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="38f14-104">This same meaning of the attribute persists in XAML; however, some additional considerations apply.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="38f14-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="38f14-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object xml:lang="rfc3066lang" />  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="38f14-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="38f14-106">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="38f14-107">*rfc3066lang*</span><span class="sxs-lookup"><span data-stu-id="38f14-107">*rfc3066lang*</span></span>|<span data-ttu-id="38f14-108">Türetilen bir dize [RFC 3066](http://go.microsoft.com/fwlink/?LinkId=132454) standart ve bir dil veya dil bölge tanımlar.</span><span class="sxs-lookup"><span data-stu-id="38f14-108">A string that is derived from the [RFC 3066](http://go.microsoft.com/fwlink/?LinkId=132454) standard and identifies either a language or a language-region.</span></span> <span data-ttu-id="38f14-109">İkincisi, bölge ve dil tek bir çizgi ile ayrılır.</span><span class="sxs-lookup"><span data-stu-id="38f14-109">When it is the latter, the language and region are separated by a single hyphen.</span></span> <span data-ttu-id="38f14-110">Bkz: <xref:System.Windows.Markup.XmlLanguage> değerler ve biçimi hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="38f14-110">See <xref:System.Windows.Markup.XmlLanguage> for more information about the values and format.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38f14-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="38f14-111">Remarks</span></span>  
 <span data-ttu-id="38f14-112">Tanımı `xml:lang` özniteliğini [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] türetildiği `xml:lang` "özel özniteliği" tarafından tanımlanan [!INCLUDE[TLA#tla_w3c](../../../includes/tlasharptla-w3c-md.md)] için [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="38f14-112">The definition for the `xml:lang` attribute in [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] is derived from `xml:lang` as defined as a "special attribute" by the [!INCLUDE[TLA#tla_w3c](../../../includes/tlasharptla-w3c-md.md)] for [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)].</span></span> <span data-ttu-id="38f14-113">Dil ve kültür bilgilerini potansiyel olarak kendi uygulamalarını bağlı olarak öğeler tarafından farklı şekillerde işlenir; Ancak, varsayılan yok [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] işlenmesi `xml:lang` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="38f14-113">Language and culture information is potentially processed in different ways by elements, depending on their implementations; however, there is no default [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processing of the `xml:lang` attribute.</span></span>  
  
 <span data-ttu-id="38f14-114">Varsayılan değer olan `xml:lang` boş bir dize özniteliği düzeyinde bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="38f14-114">The default value of the `xml:lang` attribute is an empty string at the attribute level.</span></span>  
  
 <span data-ttu-id="38f14-115">`xml:lang` Özniteliği etkiler ve öznitelik değeri genellikle perpetuated alt öğelerine hareket sistemler tarafından yorumlanan zaman `xml:lang` değerleri.</span><span class="sxs-lookup"><span data-stu-id="38f14-115">The `xml:lang` attribute effects and the value of the attribute are generally perpetuated to child elements, when interpreted by systems that act on `xml:lang` values.</span></span>  
  
 <span data-ttu-id="38f14-116">.NET Framework XAML hizmetlerinde XAML yazarlar tarafından yorumlanan olduğunda bir `xml:lang` değeri oluşturabilir <xref:System.Windows.Markup.XmlLanguage> veya <xref:System.Globalization.CultureInfo> temel nesneleri nesne gösterimi; ancak, bu davranışı bağlıdır içinbelirtilendeğer`xml:lang`bu sınıfların geçerli bir yapıdır.</span><span class="sxs-lookup"><span data-stu-id="38f14-116">When interpreted by XAML writers of .NET Framework XAML Services, an `xml:lang` value can create <xref:System.Windows.Markup.XmlLanguage> or <xref:System.Globalization.CultureInfo> objects in the underlying object representation; however, that behavior depends on whether the value specified for `xml:lang` is a valid construction for those classes.</span></span>  
  
 <span data-ttu-id="38f14-117">Çerçeveler framework tarafından tanımlanan özellikler ve anlamını arasındaki ilişkilendirmeleri oluşturma `xml:lang` uygulayarak XML <xref:System.Windows.Markup.XmlLangPropertyAttribute> özelliğine.</span><span class="sxs-lookup"><span data-stu-id="38f14-117">Frameworks can create associations between framework-defined properties and the meaning of `xml:lang` in XML by applying <xref:System.Windows.Markup.XmlLangPropertyAttribute> to the property.</span></span>  
  
## <a name="wpf-usage-nodes"></a><span data-ttu-id="38f14-118">WPF kullanım düğümler</span><span class="sxs-lookup"><span data-stu-id="38f14-118">WPF Usage Nodes</span></span>  
 <span data-ttu-id="38f14-119">Türetilmiş sınıflar, öğeleri için <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>, eşdeğer kullanabilirsiniz <xref:System.Windows.FrameworkElement.Language%2A> yerine bağımlılık özelliği `xml:lang` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="38f14-119">For elements that are derived classes of <xref:System.Windows.FrameworkElement> or <xref:System.Windows.FrameworkContentElement>, you can use the equivalent <xref:System.Windows.FrameworkElement.Language%2A> dependency property instead of the `xml:lang` attribute.</span></span> <span data-ttu-id="38f14-120">Varsayılan olarak, <xref:System.Windows.FrameworkElement.Language%2A> özelliği "en-US" kullanır, aksi takdirde, özellik veya işlem aracılığıyla ayarlanmamışsa `xml:lang` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="38f14-120">By default, the <xref:System.Windows.FrameworkElement.Language%2A> property uses "en-US" if it is not otherwise set, either through the property or through processing the `xml:lang` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38f14-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="38f14-121">See Also</span></span>  
 [<span data-ttu-id="38f14-122">WPF için Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="38f14-122">Globalization for WPF</span></span>](../../../docs/framework/wpf/advanced/globalization-for-wpf.md)
