---
title: XAML'de xml:lang İşleme
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: b3f236b2378d6af78f034856e3ba0f7a9e17993c
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837148"
---
# <a name="xmllang-handling-in-xaml"></a><span data-ttu-id="94f26-102">XAML'de xml:lang İşleme</span><span class="sxs-lookup"><span data-stu-id="94f26-102">xml:lang Handling in XAML</span></span>
<span data-ttu-id="94f26-103">`xml:lang` özniteliği, XML içindeki bir öğe için dil ve kültür bilgilerini bildiren XML tanımlı bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="94f26-103">The `xml:lang` attribute is an XML-defined attribute that declares the language and culture information for an element in XML.</span></span> <span data-ttu-id="94f26-104">Özniteliğin bu anlamı XAML 'de devam ediyor; Ancak bazı ek konular geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="94f26-104">This same meaning of the attribute persists in XAML; however, some additional considerations apply.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="94f26-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="94f26-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object xml:lang="rfc3066lang" />  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="94f26-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="94f26-106">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="94f26-107">*rfc3066lang*</span><span class="sxs-lookup"><span data-stu-id="94f26-107">*rfc3066lang*</span></span>|<span data-ttu-id="94f26-108">[RFC 3066](https://www.ietf.org/rfc/rfc3066.txt) standbundan türetilmiş ve bir dil ya da dil bölgesi tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="94f26-108">A string that is derived from the [RFC 3066](https://www.ietf.org/rfc/rfc3066.txt) standard and identifies either a language or a language-region.</span></span> <span data-ttu-id="94f26-109">İkinci olduğunda, dil ve bölge tek bir tire ile ayrılır.</span><span class="sxs-lookup"><span data-stu-id="94f26-109">When it is the latter, the language and region are separated by a single hyphen.</span></span> <span data-ttu-id="94f26-110">Değerler ve biçim hakkında daha fazla bilgi için bkz. <xref:System.Windows.Markup.XmlLanguage>.</span><span class="sxs-lookup"><span data-stu-id="94f26-110">See <xref:System.Windows.Markup.XmlLanguage> for more information about the values and format.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94f26-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="94f26-111">Remarks</span></span>  
 <span data-ttu-id="94f26-112">[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] `xml:lang` özniteliğinin tanımı, XML için World Wide Web Konsorsiyumu (W3C) tarafından bir "özel öznitelik" olarak tanımlanan `xml:lang` türetilir.</span><span class="sxs-lookup"><span data-stu-id="94f26-112">The definition for the `xml:lang` attribute in [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] is derived from `xml:lang` as defined as a "special attribute" by the World Wide Web Consortium (W3C) for XML.</span></span> <span data-ttu-id="94f26-113">Dil ve kültür bilgileri, uygulamalarına bağlı olarak, öğelere göre farklı yollarla işlenir; Ancak, `xml:lang` özniteliğinde varsayılan [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] işleme yoktur.</span><span class="sxs-lookup"><span data-stu-id="94f26-113">Language and culture information is potentially processed in different ways by elements, depending on their implementations; however, there is no default [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processing of the `xml:lang` attribute.</span></span>  
  
 <span data-ttu-id="94f26-114">`xml:lang` özniteliğin varsayılan değeri, öznitelik düzeyindeki boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="94f26-114">The default value of the `xml:lang` attribute is an empty string at the attribute level.</span></span>  
  
 <span data-ttu-id="94f26-115">`xml:lang` öznitelik etkileri ve öznitelik değeri, `xml:lang` değerler üzerinde işlem gören sistemler tarafından yorumlandığında genellikle alt öğelere işlenir.</span><span class="sxs-lookup"><span data-stu-id="94f26-115">The `xml:lang` attribute effects and the value of the attribute are generally perpetuated to child elements, when interpreted by systems that act on `xml:lang` values.</span></span>  
  
 <span data-ttu-id="94f26-116">.NET Framework XAML hizmetlerinin XAML yazarları tarafından yorumlanırken, `xml:lang` bir değer temel alınan nesne gösteriminde <xref:System.Windows.Markup.XmlLanguage> veya <xref:System.Globalization.CultureInfo> nesneleri oluşturabilir; Ancak, bu davranış, `xml:lang` için belirtilen değerin bu sınıflar için geçerli bir oluşturma olup olmamasına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="94f26-116">When interpreted by XAML writers of .NET Framework XAML Services, an `xml:lang` value can create <xref:System.Windows.Markup.XmlLanguage> or <xref:System.Globalization.CultureInfo> objects in the underlying object representation; however, that behavior depends on whether the value specified for `xml:lang` is a valid construction for those classes.</span></span>  
  
 <span data-ttu-id="94f26-117">Çerçeveler, özelliğe <xref:System.Windows.Markup.XmlLangPropertyAttribute> uygulayarak çerçeve tanımlı özellikler ve XML 'deki `xml:lang` anlamı arasında ilişkiler oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="94f26-117">Frameworks can create associations between framework-defined properties and the meaning of `xml:lang` in XML by applying <xref:System.Windows.Markup.XmlLangPropertyAttribute> to the property.</span></span>  
  
## <a name="wpf-usage-nodes"></a><span data-ttu-id="94f26-118">WPF kullanım düğümleri</span><span class="sxs-lookup"><span data-stu-id="94f26-118">WPF Usage Nodes</span></span>  
 <span data-ttu-id="94f26-119"><xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>türetilmiş sınıfları olan öğeler için `xml:lang` özniteliği yerine eşdeğer <xref:System.Windows.FrameworkElement.Language%2A> bağımlılık özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94f26-119">For elements that are derived classes of <xref:System.Windows.FrameworkElement> or <xref:System.Windows.FrameworkContentElement>, you can use the equivalent <xref:System.Windows.FrameworkElement.Language%2A> dependency property instead of the `xml:lang` attribute.</span></span> <span data-ttu-id="94f26-120">Varsayılan olarak, <xref:System.Windows.FrameworkElement.Language%2A> özelliği, başka bir şekilde ayarlanmamışsa, özelliği aracılığıyla veya `xml:lang` özniteliği işlenerek "en-US" kullanır.</span><span class="sxs-lookup"><span data-stu-id="94f26-120">By default, the <xref:System.Windows.FrameworkElement.Language%2A> property uses "en-US" if it is not otherwise set, either through the property or through processing the `xml:lang` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94f26-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94f26-121">See also</span></span>

- [<span data-ttu-id="94f26-122">WPF için Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="94f26-122">Globalization for WPF</span></span>](../wpf/advanced/globalization-for-wpf.md)
