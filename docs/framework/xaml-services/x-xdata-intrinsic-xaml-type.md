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
ms.openlocfilehash: c5f729837b9bb52ca7d232ca66b58e283a2bcefc
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053705"
---
# <a name="xxdata-intrinsic-xaml-type"></a><span data-ttu-id="54878-102">x:XData İç XAML Türü</span><span class="sxs-lookup"><span data-stu-id="54878-102">x:XData Intrinsic XAML Type</span></span>
<span data-ttu-id="54878-103">Bir XAML üretimi içinde XML veri Adaları yerleştirmesini mümkün bir şekilde sunar.</span><span class="sxs-lookup"><span data-stu-id="54878-103">Enables placement of XML data islands within a XAML production.</span></span> <span data-ttu-id="54878-104">İçindeki `x:XData` XML öğeleri, işlem gören varsayılan xaml ad alanının veya diğer xaml ad alanının bir parçası gibi XAML işlemcileri tarafından değerlendirilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="54878-104">XML elements within `x:XData` should not be treated by XAML processors as if they are a part of the acting default XAML namespace or any other XAML namespace.</span></span> <span data-ttu-id="54878-105">`x:XData`Rastgele düzgün biçimlendirilmiş XML içerebilir.</span><span class="sxs-lookup"><span data-stu-id="54878-105">`x:XData` can contain arbitrary well-formed XML.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="54878-106">XAML Nesne Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="54878-106">XAML Object Element Usage</span></span>  
  
```xaml  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="54878-107">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="54878-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`elementDataRoot`|<span data-ttu-id="54878-108">İliştirilmiş veri Adası 'nin tek kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="54878-108">The single root element of the enclosed data island.</span></span> <span data-ttu-id="54878-109">En son tüketiciler için, tek bir köküne sahip olmayan XML geçersiz olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="54878-109">For most eventual consumers, XML that does not have a single root is considered invalid.</span></span> <span data-ttu-id="54878-110">Özellikle, WPF için bir XML veri kaynağı veya veri `x:XData` bağlama için xml kaynakları kullanan diğer teknolojiler için tasarlanan tek bir kök gereklidir.</span><span class="sxs-lookup"><span data-stu-id="54878-110">In particular, a single root is required if the `x:XData` is intended as an XML data source for WPF or many other technologies that use XML sources for data binding.</span></span>|  
|`[elementData]`|<span data-ttu-id="54878-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="54878-111">Optional.</span></span> <span data-ttu-id="54878-112">XML verilerini temsil eden XML.</span><span class="sxs-lookup"><span data-stu-id="54878-112">XML that represents the XML data.</span></span> <span data-ttu-id="54878-113">Herhangi bir sayıda öğe öğe verisi, iç içe yerleştirilmiş öğeler ise diğer öğelerde bulunabilir; Ancak, XML 'nin genel kuralları geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="54878-113">Any number of elements can be contained as element data and nested elements can be contained in other elements; however, the general rules of XML apply.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54878-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="54878-114">Remarks</span></span>  
 <span data-ttu-id="54878-115">Bir `x:XData` nesne içindeki XML öğeleri, veri içinde bulunan XMLDOM 'ın tüm olası ad alanlarını ve öneklerini yeniden bildirebilir.</span><span class="sxs-lookup"><span data-stu-id="54878-115">The XML elements within an `x:XData` object can re-declare all possible namespaces and prefixes of the containing XMLDOM within the data.</span></span>  
  
 <span data-ttu-id="54878-116">XML verilerine ve `x:XData` içsel xaml türüne programlı erişim, <xref:System.Windows.Markup.XData> sınıf aracılığıyla .NET Framework XAML hizmetlerinde mümkündür.</span><span class="sxs-lookup"><span data-stu-id="54878-116">Programmatic access to XML data and the `x:XData` intrinsic XAML type is possible in .NET Framework XAML Services through the <xref:System.Windows.Markup.XData> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="54878-117">WPF kullanım notları</span><span class="sxs-lookup"><span data-stu-id="54878-117">WPF Usage Notes</span></span>  
 <span data-ttu-id="54878-118">Nesne öncelikle bir <xref:System.Windows.Data.XmlDataProvider>alt nesne olarak veya alternatif olarak <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> özelliğin alt nesnesi olarak kullanılır (XAML 'de, bu genellikle özellik öğesi söz diziminde ifade edilir). `x:XData`</span><span class="sxs-lookup"><span data-stu-id="54878-118">The `x:XData` object is primarily used as a child object of an <xref:System.Windows.Data.XmlDataProvider>, or alternatively, as the child object of the <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> property (in XAML, this is typically expressed in property element syntax).</span></span>  
  
 <span data-ttu-id="54878-119">Veriler genellikle veri Adası içindeki temel XML ad alanını yeni bir varsayılan XML ad alanı olacak şekilde (boş bir dizeye ayarlanır) yeniden tanımlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="54878-119">The data should typically redefine the base XML namespace within the data island to be a new default XML namespace (set to an empty string).</span></span> <span data-ttu-id="54878-120">Bu, basit veri Adaları için en kolay yoldur <xref:System.Windows.Data.Binding.XPath%2A> çünkü verilere başvurmak ve bağlanmak için kullanılan ifadeler ön eklerin dahil edilmesini önleyebilir.</span><span class="sxs-lookup"><span data-stu-id="54878-120">This is easiest for simple data islands because the <xref:System.Windows.Data.Binding.XPath%2A> expressions that are used to reference and bind to the data can avoid inclusion of prefixes.</span></span> <span data-ttu-id="54878-121">Daha karmaşık veri Adaları, veriler için birden çok önek tanımlayabilir ve kökte XML ad alanı için belirli bir önek kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="54878-121">More complex data islands might define multiple prefixes for the data and use a specific prefix for the XML namespace at the root.</span></span> <span data-ttu-id="54878-122">Bu durumda, tüm <xref:System.Windows.Data.Binding.XPath%2A> ifade başvuruları uygun ad alanı eşlemeli öneki içermelidir.</span><span class="sxs-lookup"><span data-stu-id="54878-122">In this case, all <xref:System.Windows.Data.Binding.XPath%2A> expression references should include the appropriate namespace-mapped prefix.</span></span> <span data-ttu-id="54878-123">Daha fazla bilgi için bkz. [veri bağlamaya genel bakış](../wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="54878-123">For more information, see [Data Binding Overview](../wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="54878-124">Teknik olarak `x:XData` , türünde <xref:System.Xml.Serialization.IXmlSerializable>herhangi bir özelliğin içeriği olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="54878-124">Technically, `x:XData` can be used as the content of any property of type <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="54878-125">Ancak, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> tek belirgin uygulama.</span><span class="sxs-lookup"><span data-stu-id="54878-125">However, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> is the only prominent implementation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54878-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54878-126">See also</span></span>

- <xref:System.Windows.Data.XmlDataProvider>
- [<span data-ttu-id="54878-127">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="54878-127">Data Binding Overview</span></span>](../wpf/data/data-binding-overview.md)
- [<span data-ttu-id="54878-128">İşaretleme Uzantısı Bağlama</span><span class="sxs-lookup"><span data-stu-id="54878-128">Binding Markup Extension</span></span>](../wpf/advanced/binding-markup-extension.md)
