---
title: XAML'de xml:lang İşleme
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: b5a06adbb7cb874bc09899118f13b91fbec7a85e
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071446"
---
# <a name="xmllang-handling-in-xaml"></a><span data-ttu-id="7303f-102">XAML'de xml:lang İşleme</span><span class="sxs-lookup"><span data-stu-id="7303f-102">xml:lang Handling in XAML</span></span>

<span data-ttu-id="7303f-103">Öznitelik, `xml:lang` XML'deki bir öğenin dil ve kültür bilgilerini bildiren XML tanımlı bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="7303f-103">The `xml:lang` attribute is an XML-defined attribute that declares the language and culture information for an element in XML.</span></span> <span data-ttu-id="7303f-104">Özniteliğin bu aynı anlamı XAML'de devam eder; ancak, bazı ek hususlar geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7303f-104">This same meaning of the attribute persists in XAML; however, some additional considerations apply.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="7303f-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="7303f-105">XAML Attribute Usage</span></span>

```xaml
<object xml:lang="rfc3066lang" />
```

## <a name="xaml-values"></a><span data-ttu-id="7303f-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="7303f-106">XAML Values</span></span>

|||
|-|-|
|<span data-ttu-id="7303f-107">*rfc3066lang*</span><span class="sxs-lookup"><span data-stu-id="7303f-107">*rfc3066lang*</span></span>|<span data-ttu-id="7303f-108">[RFC 3066](https://www.ietf.org/rfc/rfc3066.txt) standardından türetilen ve bir dili veya dil bölgesini tanımlayan dize.</span><span class="sxs-lookup"><span data-stu-id="7303f-108">A string that is derived from the [RFC 3066](https://www.ietf.org/rfc/rfc3066.txt) standard and identifies either a language or a language-region.</span></span> <span data-ttu-id="7303f-109">Ne zaman ikincisi, dil ve bölge tek bir tire ile ayrılır.</span><span class="sxs-lookup"><span data-stu-id="7303f-109">When it is the latter, the language and region are separated by a single hyphen.</span></span> <span data-ttu-id="7303f-110">Değerler <xref:System.Windows.Markup.XmlLanguage> ve biçim hakkında daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="7303f-110">See <xref:System.Windows.Markup.XmlLanguage> for more information about the values and format.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7303f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7303f-111">Remarks</span></span>

<span data-ttu-id="7303f-112">Özellik teki `xml:lang` öznitelik [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] tanımı, `xml:lang` XML için World Wide Web Konsorsiyumu (W3C) tarafından "özel öznitelik" olarak tanımlanan türetilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7303f-112">The definition for the `xml:lang` attribute in [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] is derived from `xml:lang` as defined as a "special attribute" by the World Wide Web Consortium (W3C) for XML.</span></span> <span data-ttu-id="7303f-113">Dil ve kültür bilgileri, uygulamalarına bağlı olarak, öğeler tarafından potansiyel olarak farklı şekillerde işlenir; ancak, öznitelik [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] hiçbir varsayılan `xml:lang` işleme yoktur.</span><span class="sxs-lookup"><span data-stu-id="7303f-113">Language and culture information is potentially processed in different ways by elements, depending on their implementations; however, there is no default [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processing of the `xml:lang` attribute.</span></span>

<span data-ttu-id="7303f-114">Öznitelik varsayılan `xml:lang` değeri öznitelik düzeyinde boş bir dize.</span><span class="sxs-lookup"><span data-stu-id="7303f-114">The default value of the `xml:lang` attribute is an empty string at the attribute level.</span></span>

<span data-ttu-id="7303f-115">Öznitelik `xml:lang` efektleri ve öznitelik değeri genellikle alt öğelere, değerler üzerinde `xml:lang` hareket sistemleri tarafından yorumlandığında sürdürülür.</span><span class="sxs-lookup"><span data-stu-id="7303f-115">The `xml:lang` attribute effects and the value of the attribute are generally perpetuated to child elements, when interpreted by systems that act on `xml:lang` values.</span></span>

<span data-ttu-id="7303f-116">.NET XAML Services'In XAML yazarları `xml:lang` tarafından yorumlandığında, bir değer temel nesne gösteriminde oluşturabilir <xref:System.Windows.Markup.XmlLanguage> veya <xref:System.Globalization.CultureInfo> nesneleroluşturabilir; ancak, bu davranış, belirtilen `xml:lang` değerin bu sınıflar için geçerli bir yapı olup olmadığına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7303f-116">When interpreted by XAML writers of .NET XAML Services, an `xml:lang` value can create <xref:System.Windows.Markup.XmlLanguage> or <xref:System.Globalization.CultureInfo> objects in the underlying object representation; however, that behavior depends on whether the value specified for `xml:lang` is a valid construction for those classes.</span></span>

<span data-ttu-id="7303f-117">Çerçeveler, özellik için uygulayarak `xml:lang` <xref:System.Windows.Markup.XmlLangPropertyAttribute> çerçeve tanımlı özellikleri ve XML içinde anlamı arasında ilişkiler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7303f-117">Frameworks can create associations between framework-defined properties and the meaning of `xml:lang` in XML by applying <xref:System.Windows.Markup.XmlLangPropertyAttribute> to the property.</span></span>

## <a name="wpf-usage-nodes"></a><span data-ttu-id="7303f-118">WPF Kullanım Düğümleri</span><span class="sxs-lookup"><span data-stu-id="7303f-118">WPF Usage Nodes</span></span>

<span data-ttu-id="7303f-119">Türemiş sınıflar <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>, öznitelik yerine <xref:System.Windows.FrameworkElement.Language%2A> eşdeğer bağımlılık özelliği `xml:lang` kullanabilirsiniz öğeler için.</span><span class="sxs-lookup"><span data-stu-id="7303f-119">For elements that are derived classes of <xref:System.Windows.FrameworkElement> or <xref:System.Windows.FrameworkContentElement>, you can use the equivalent <xref:System.Windows.FrameworkElement.Language%2A> dependency property instead of the `xml:lang` attribute.</span></span> <span data-ttu-id="7303f-120">Varsayılan olarak, <xref:System.Windows.FrameworkElement.Language%2A> özellik, özellik aracılığıyla veya özniteliği işleyerek `xml:lang` başka türlü ayarlanmazsa "en-US" kullanır.</span><span class="sxs-lookup"><span data-stu-id="7303f-120">By default, the <xref:System.Windows.FrameworkElement.Language%2A> property uses "en-US" if it is not otherwise set, either through the property or through processing the `xml:lang` attribute.</span></span>

## <a name="see-also"></a><span data-ttu-id="7303f-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7303f-121">See also</span></span>

- [<span data-ttu-id="7303f-122">WPF için Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="7303f-122">Globalization for WPF</span></span>](../../framework/wpf/advanced/globalization-for-wpf.md)
