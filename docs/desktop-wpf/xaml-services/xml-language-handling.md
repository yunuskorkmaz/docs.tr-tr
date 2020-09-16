---
title: XAML'de xml:lang İşleme
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: 92d1eda62ff394df54d9607bab46d9950681e603
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548214"
---
# <a name="xmllang-handling-in-xaml"></a><span data-ttu-id="b8132-102">XAML'de xml:lang İşleme</span><span class="sxs-lookup"><span data-stu-id="b8132-102">xml:lang Handling in XAML</span></span>

<span data-ttu-id="b8132-103">`xml:lang`Özniteliği, XML içindeki bir öğe için dil ve kültür bilgilerini BILDIREN xml tanımlı bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="b8132-103">The `xml:lang` attribute is an XML-defined attribute that declares the language and culture information for an element in XML.</span></span> <span data-ttu-id="b8132-104">Özniteliğin bu anlamı XAML 'de devam ediyor; Ancak bazı ek konular geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b8132-104">This same meaning of the attribute persists in XAML; however, some additional considerations apply.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="b8132-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="b8132-105">XAML Attribute Usage</span></span>

```xaml
<object xml:lang="rfc3066lang" />
```

## <a name="xaml-values"></a><span data-ttu-id="b8132-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="b8132-106">XAML Values</span></span>

|||
|-|-|
|<span data-ttu-id="b8132-107">*rfc3066lang*</span><span class="sxs-lookup"><span data-stu-id="b8132-107">*rfc3066lang*</span></span>|<span data-ttu-id="b8132-108">[RFC 3066](https://www.ietf.org/rfc/rfc3066.txt) standbundan türetilmiş ve bir dil ya da dil bölgesi tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="b8132-108">A string that is derived from the [RFC 3066](https://www.ietf.org/rfc/rfc3066.txt) standard and identifies either a language or a language-region.</span></span> <span data-ttu-id="b8132-109">İkinci olduğunda, dil ve bölge tek bir tire ile ayrılır.</span><span class="sxs-lookup"><span data-stu-id="b8132-109">When it is the latter, the language and region are separated by a single hyphen.</span></span> <span data-ttu-id="b8132-110"><xref:System.Windows.Markup.XmlLanguage>Değerler ve biçim hakkında daha fazla bilgi için bkz..</span><span class="sxs-lookup"><span data-stu-id="b8132-110">See <xref:System.Windows.Markup.XmlLanguage> for more information about the values and format.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b8132-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b8132-111">Remarks</span></span>

<span data-ttu-id="b8132-112">İçindeki özniteliği için tanımı, `xml:lang` [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] `xml:lang` XML IÇIN World Wide Web Konsorsiyumu (W3C) tarafından bir "özel öznitelik" olarak tanımlanan öğesinden türetilir.</span><span class="sxs-lookup"><span data-stu-id="b8132-112">The definition for the `xml:lang` attribute in [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] is derived from `xml:lang` as defined as a "special attribute" by the World Wide Web Consortium (W3C) for XML.</span></span> <span data-ttu-id="b8132-113">Dil ve kültür bilgileri, uygulamalarına bağlı olarak, öğelere göre farklı yollarla işlenir; Ancak, [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] özniteliği için varsayılan işlem yoktur `xml:lang` .</span><span class="sxs-lookup"><span data-stu-id="b8132-113">Language and culture information is potentially processed in different ways by elements, depending on their implementations; however, there is no default [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processing of the `xml:lang` attribute.</span></span>

<span data-ttu-id="b8132-114">Özniteliğin varsayılan değeri, `xml:lang` öznitelik düzeyindeki boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="b8132-114">The default value of the `xml:lang` attribute is an empty string at the attribute level.</span></span>

<span data-ttu-id="b8132-115">Öznitelik `xml:lang` etkileri ve öznitelik değeri, değerler üzerinde işlem yapan sistemler tarafından yorumlandığında, genellikle alt öğelere işlenir `xml:lang` .</span><span class="sxs-lookup"><span data-stu-id="b8132-115">The `xml:lang` attribute effects and the value of the attribute are generally perpetuated to child elements, when interpreted by systems that act on `xml:lang` values.</span></span>

<span data-ttu-id="b8132-116">.NET XAML Hizmetleri 'nin XAML yazarları tarafından yorumlanırken bir `xml:lang` değer, <xref:System.Windows.Markup.XmlLanguage> <xref:System.Globalization.CultureInfo> temel alınan nesne gösteriminde oluşturabilir veya nesneleri oluşturabilir; ancak, bu davranış, için belirtilen değerin `xml:lang` Bu sınıflar için geçerli bir oluşturma olup olmamasına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b8132-116">When interpreted by XAML writers of .NET XAML Services, an `xml:lang` value can create <xref:System.Windows.Markup.XmlLanguage> or <xref:System.Globalization.CultureInfo> objects in the underlying object representation; however, that behavior depends on whether the value specified for `xml:lang` is a valid construction for those classes.</span></span>

<span data-ttu-id="b8132-117">Çerçeveler `xml:lang` , özelliğine uygulayarak çerçeve tanımlı özellikler ve XML 'nin anlamı arasında ilişkiler oluşturabilir <xref:System.Windows.Markup.XmlLangPropertyAttribute> .</span><span class="sxs-lookup"><span data-stu-id="b8132-117">Frameworks can create associations between framework-defined properties and the meaning of `xml:lang` in XML by applying <xref:System.Windows.Markup.XmlLangPropertyAttribute> to the property.</span></span>

## <a name="wpf-usage-nodes"></a><span data-ttu-id="b8132-118">WPF kullanım düğümleri</span><span class="sxs-lookup"><span data-stu-id="b8132-118">WPF Usage Nodes</span></span>

<span data-ttu-id="b8132-119">Ya da türetilmiş sınıfları olan öğeler için <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement> , <xref:System.Windows.FrameworkElement.Language%2A> özniteliği yerine eşdeğer bağımlılık özelliğini kullanabilirsiniz `xml:lang` .</span><span class="sxs-lookup"><span data-stu-id="b8132-119">For elements that are derived classes of <xref:System.Windows.FrameworkElement> or <xref:System.Windows.FrameworkContentElement>, you can use the equivalent <xref:System.Windows.FrameworkElement.Language%2A> dependency property instead of the `xml:lang` attribute.</span></span> <span data-ttu-id="b8132-120">Varsayılan olarak, <xref:System.Windows.FrameworkElement.Language%2A> özelliği, özelliği aracılığıyla veya özniteliği işlenerek, aksi durumda ayarlanmamışsa "en-US" kullanır `xml:lang` .</span><span class="sxs-lookup"><span data-stu-id="b8132-120">By default, the <xref:System.Windows.FrameworkElement.Language%2A> property uses "en-US" if it is not otherwise set, either through the property or through processing the `xml:lang` attribute.</span></span>

## <a name="see-also"></a><span data-ttu-id="b8132-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8132-121">See also</span></span>

- [<span data-ttu-id="b8132-122">WPF için Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="b8132-122">Globalization for WPF</span></span>](/dotnet/desktop/wpf/advanced/globalization-for-wpf)
