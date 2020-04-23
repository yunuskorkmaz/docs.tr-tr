---
title: x:XData İç XAML Türü
ms.date: 03/30/2017
f1_keywords:
- x:XData
- XData
- xXData
helpviewer_keywords:
- XAML [XAML Services], x:XData directive element
- XData in XAML [XAML Services]
- x:XData XAML directive element [XAML Services]
ms.assetid: 7ce209c2-621b-4977-b643-565f7e663534
ms.openlocfilehash: b7f0954158988db107feb4a6c51ba81d5db11dcb
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071544"
---
# <a name="xxdata-intrinsic-xaml-type"></a><span data-ttu-id="c21a6-102">x:XData İç XAML Türü</span><span class="sxs-lookup"><span data-stu-id="c21a6-102">x:XData Intrinsic XAML Type</span></span>
<span data-ttu-id="c21a6-103">XML veri adalarının XAML üretimi içinde yerleştirilmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c21a6-103">Enables placement of XML data islands within a XAML production.</span></span> <span data-ttu-id="c21a6-104">İçerdeki `x:XData` XML öğeleri XAML işlemciler tarafından varsayılan XAML ad alanının veya başka bir XAML ad alanının bir parçasıymuş gibi ele alınmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="c21a6-104">XML elements within `x:XData` should not be treated by XAML processors as if they are a part of the acting default XAML namespace or any other XAML namespace.</span></span> <span data-ttu-id="c21a6-105">`x:XData`rasgele iyi biçimlendirilmiş XML içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c21a6-105">`x:XData` can contain arbitrary well-formed XML.</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="c21a6-106">XAML Nesne Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="c21a6-106">XAML Object Element Usage</span></span>

```xaml
<x:XData>
  <elementDataRoot>
    [elementData]
  </elementDataRoot>
</x:XData>
```

## <a name="xaml-values"></a><span data-ttu-id="c21a6-107">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="c21a6-107">XAML Values</span></span>

|||
|-|-|
|`elementDataRoot`|<span data-ttu-id="c21a6-108">Kapalı veri adasının tek kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="c21a6-108">The single root element of the enclosed data island.</span></span> <span data-ttu-id="c21a6-109">Çoğu nihai tüketici için, tek bir köke sahip olmayan XML geçersiz kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="c21a6-109">For most eventual consumers, XML that does not have a single root is considered invalid.</span></span> <span data-ttu-id="c21a6-110">Özellikle, WPF veya veri `x:XData` bağlama için XML kaynaklarını kullanan diğer birçok teknoloji için XML veri kaynağı olarak tasarlanmıştırsa, tek bir kök gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c21a6-110">In particular, a single root is required if the `x:XData` is intended as an XML data source for WPF or many other technologies that use XML sources for data binding.</span></span>|
|`[elementData]`|<span data-ttu-id="c21a6-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c21a6-111">Optional.</span></span> <span data-ttu-id="c21a6-112">XML verilerini temsil eden XML.</span><span class="sxs-lookup"><span data-stu-id="c21a6-112">XML that represents the XML data.</span></span> <span data-ttu-id="c21a6-113">Eleman verileri ve iç içe öğeler diğer öğelerde bulunabilir gibi elemanların herhangi bir sayı bulunabilir; ancak, XML genel kuralları geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c21a6-113">Any number of elements can be contained as element data and nested elements can be contained in other elements; however, the general rules of XML apply.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c21a6-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c21a6-114">Remarks</span></span>

<span data-ttu-id="c21a6-115">Bir `x:XData` nesneiçindeki XML öğeleri, veriler içinde xmldom içeren tüm olası ad alanlarını ve öneklerini yeniden bildirebilir.</span><span class="sxs-lookup"><span data-stu-id="c21a6-115">The XML elements within an `x:XData` object can re-declare all possible namespaces and prefixes of the containing XMLDOM within the data.</span></span>

<span data-ttu-id="c21a6-116">XML verilerine ve `x:XData` içsel XAML türüne programlı erişim .NET XAML Services'da <xref:System.Windows.Markup.XData> sınıf aracılığıyla mümkündür.</span><span class="sxs-lookup"><span data-stu-id="c21a6-116">Programmatic access to XML data and the `x:XData` intrinsic XAML type is possible in .NET XAML Services through the <xref:System.Windows.Markup.XData> class.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="c21a6-117">WPF Kullanım Notları</span><span class="sxs-lookup"><span data-stu-id="c21a6-117">WPF Usage Notes</span></span>

<span data-ttu-id="c21a6-118">Nesne `x:XData` öncelikle bir <xref:System.Windows.Data.XmlDataProvider>alt nesne olarak kullanılır , veya alternatif olarak, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> özelliğin alt nesnesi olarak (XAML, bu genellikle özellik öğesi sözdizimi ifade edilir).</span><span class="sxs-lookup"><span data-stu-id="c21a6-118">The `x:XData` object is primarily used as a child object of an <xref:System.Windows.Data.XmlDataProvider>, or alternatively, as the child object of the <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> property (in XAML, this is typically expressed in property element syntax).</span></span>

<span data-ttu-id="c21a6-119">Veriler genellikle veri adasındaki temel XML ad alanını yeni bir varsayılan XML ad alanı (boş bir dize olarak ayarlanmış) olarak yeniden tanımlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="c21a6-119">The data should typically redefine the base XML namespace within the data island to be a new default XML namespace (set to an empty string).</span></span> <span data-ttu-id="c21a6-120">Bu basit veri adaları için <xref:System.Windows.Data.Binding.XPath%2A> en kolayıdır, çünkü verilere başvurmak ve bağlamak için kullanılan ifadeler öneklerin eklenmesini önleyebilir.</span><span class="sxs-lookup"><span data-stu-id="c21a6-120">This is easiest for simple data islands because the <xref:System.Windows.Data.Binding.XPath%2A> expressions that are used to reference and bind to the data can avoid inclusion of prefixes.</span></span> <span data-ttu-id="c21a6-121">Daha karmaşık veri adaları veriler için birden çok önek tanımlayabilir ve kökteki XML ad alanı için belirli bir önek kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="c21a6-121">More complex data islands might define multiple prefixes for the data and use a specific prefix for the XML namespace at the root.</span></span> <span data-ttu-id="c21a6-122">Bu durumda, <xref:System.Windows.Data.Binding.XPath%2A> tüm ifade başvuruları uygun ad alanı eşlenen öneki içermelidir.</span><span class="sxs-lookup"><span data-stu-id="c21a6-122">In this case, all <xref:System.Windows.Data.Binding.XPath%2A> expression references should include the appropriate namespace-mapped prefix.</span></span> <span data-ttu-id="c21a6-123">Daha fazla bilgi için bkz: [Veri Bağlama Genel Bakışı.](../data/data-binding-overview.md)</span><span class="sxs-lookup"><span data-stu-id="c21a6-123">For more information, see [Data Binding Overview](../data/data-binding-overview.md).</span></span>

<span data-ttu-id="c21a6-124">Teknik olarak, `x:XData` türü <xref:System.Xml.Serialization.IXmlSerializable>herhangi bir özelliğin içeriği olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c21a6-124">Technically, `x:XData` can be used as the content of any property of type <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="c21a6-125">Ancak, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> tek önemli uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="c21a6-125">However, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> is the only prominent implementation.</span></span>

## <a name="see-also"></a><span data-ttu-id="c21a6-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c21a6-126">See also</span></span>

- <xref:System.Windows.Data.XmlDataProvider>
- [<span data-ttu-id="c21a6-127">Veri Bağlama Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c21a6-127">Data Binding Overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="c21a6-128">Biçimlendirme Uzantısı Bağlama</span><span class="sxs-lookup"><span data-stu-id="c21a6-128">Binding Markup Extension</span></span>](../../framework/wpf/advanced/binding-markup-extension.md)
