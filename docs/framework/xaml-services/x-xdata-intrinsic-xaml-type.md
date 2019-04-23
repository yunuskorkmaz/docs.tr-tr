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
ms.openlocfilehash: c8044bc341ded6ef7b03bbdf701e724654460d54
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125165"
---
# <a name="xxdata-intrinsic-xaml-type"></a><span data-ttu-id="c09da-102">x:XData İç XAML Türü</span><span class="sxs-lookup"><span data-stu-id="c09da-102">x:XData Intrinsic XAML Type</span></span>
<span data-ttu-id="c09da-103">XAML üretim içinde XML veri Adaları yerleşimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c09da-103">Enables placement of XML data islands within a XAML production.</span></span> <span data-ttu-id="c09da-104">XML öğeleri içinde `x:XData` veya herhangi bir XAML ad acting varsayılan XAML ad alanı bir parçası olmaları durumunda gibi XAML işlemcileri tarafından değerlendirilmesi gerektiğini değil.</span><span class="sxs-lookup"><span data-stu-id="c09da-104">XML elements within `x:XData` should not be treated by XAML processors as if they are a part of the acting default XAML namespace or any other XAML namespace.</span></span> <span data-ttu-id="c09da-105">`x:XData` rastgele iyi biçimlendirilmiş bir XML içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c09da-105">`x:XData` can contain arbitrary well-formed XML.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="c09da-106">XAML Nesne Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="c09da-106">XAML Object Element Usage</span></span>  
  
```  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="c09da-107">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="c09da-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`elementDataRoot`|<span data-ttu-id="c09da-108">Kapalı bir veri adası tek kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="c09da-108">The single root element of the enclosed data island.</span></span> <span data-ttu-id="c09da-109">En son Tüketiciler için tek bir kök olmayan XML geçersiz olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="c09da-109">For most eventual consumers, XML that does not have a single root is considered invalid.</span></span> <span data-ttu-id="c09da-110">Özellikle, tek bir kök gereklidir `x:XData` bir XML veri kaynağı olarak WPF veya XML kaynakları için veri bağlama kullanan diğer pek çok teknoloji yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="c09da-110">In particular, a single root is required if the `x:XData` is intended as an XML data source for WPF or many other technologies that use XML sources for data binding.</span></span>|  
|`[elementData]`|<span data-ttu-id="c09da-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c09da-111">Optional.</span></span> <span data-ttu-id="c09da-112">XML verileri temsil eder XML.</span><span class="sxs-lookup"><span data-stu-id="c09da-112">XML that represents the XML data.</span></span> <span data-ttu-id="c09da-113">Öğeleri herhangi bir sayıda öğe verileri yer alabilir ve iç içe öğeleri diğer öğeler yer alabilir. Ancak, XML'in genel kurallar uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c09da-113">Any number of elements can be contained as element data and nested elements can be contained in other elements; however, the general rules of XML apply.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c09da-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c09da-114">Remarks</span></span>  
 <span data-ttu-id="c09da-115">XML öğeleri içinde bir `x:XData` nesne tüm olası ad alanlarını ve önekleri içeren XMLDOM verilerdeki, yeniden bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c09da-115">The XML elements within an `x:XData` object can re-declare all possible namespaces and prefixes of the containing XMLDOM within the data.</span></span>  
  
 <span data-ttu-id="c09da-116">XML verilerini için programlı erişim ve `x:XData` iç XAML türü .NET Framework XAML hizmetlerinde içinde olası <xref:System.Windows.Markup.XData> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c09da-116">Programmatic access to XML data and the `x:XData` intrinsic XAML type is possible in .NET Framework XAML Services through the <xref:System.Windows.Markup.XData> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="c09da-117">WPF kullanım notları</span><span class="sxs-lookup"><span data-stu-id="c09da-117">WPF Usage Notes</span></span>  
 <span data-ttu-id="c09da-118">`x:XData` Nesne öncelikle bir alt nesnesi olarak kullanılan bir <xref:System.Windows.Data.XmlDataProvider>, ya da alternatif olarak, alt nesnesi olarak <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> özelliği (XAML içinde bu genellikle özellik öğesi sözdizimine ifade edilir).</span><span class="sxs-lookup"><span data-stu-id="c09da-118">The `x:XData` object is primarily used as a child object of an <xref:System.Windows.Data.XmlDataProvider>, or alternatively, as the child object of the <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> property (in XAML, this is typically expressed in property element syntax).</span></span>  
  
 <span data-ttu-id="c09da-119">Verileri, genellikle yeni bir varsayılan XML ad (boş dize olarak ayarlanmış) olmasını veri adası içinde temel XML ad alanı tanımlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="c09da-119">The data should typically redefine the base XML namespace within the data island to be a new default XML namespace (set to an empty string).</span></span> <span data-ttu-id="c09da-120">Çünkü basit veri Adaları için bu en kolayıdır <xref:System.Windows.Data.Binding.XPath%2A> başvuru ve verilere bağlamak için kullanılan ifadeler önekleri ekleme önlemek.</span><span class="sxs-lookup"><span data-stu-id="c09da-120">This is easiest for simple data islands because the <xref:System.Windows.Data.Binding.XPath%2A> expressions that are used to reference and bind to the data can avoid inclusion of prefixes.</span></span> <span data-ttu-id="c09da-121">Daha karmaşık veri Adaları verileri birden çok ön eklerini tanımlayın ve kök XML ad alanı için belirli bir önek kullanın.</span><span class="sxs-lookup"><span data-stu-id="c09da-121">More complex data islands might define multiple prefixes for the data and use a specific prefix for the XML namespace at the root.</span></span> <span data-ttu-id="c09da-122">Bu durumda, tüm <xref:System.Windows.Data.Binding.XPath%2A> başvuruyor, uygun ad alanı eşlemeli önek içermelidir.</span><span class="sxs-lookup"><span data-stu-id="c09da-122">In this case, all <xref:System.Windows.Data.Binding.XPath%2A> expression references should include the appropriate namespace-mapped prefix.</span></span> <span data-ttu-id="c09da-123">Daha fazla bilgi için [Data Binding Overview](../wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c09da-123">For more information, see [Data Binding Overview](../wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="c09da-124">Teknik olarak `x:XData` içeriğini türünde herhangi bir özelliği kullanılabilir <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="c09da-124">Technically, `x:XData` can be used as the content of any property of type <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="c09da-125">Ancak, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> yalnızca tanınmış bir uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="c09da-125">However, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> is the only prominent implementation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c09da-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c09da-126">See also</span></span>

- <xref:System.Windows.Data.XmlDataProvider>
- [<span data-ttu-id="c09da-127">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c09da-127">Data Binding Overview</span></span>](../wpf/data/data-binding-overview.md)
- [<span data-ttu-id="c09da-128">İşaretleme Uzantısı Bağlama</span><span class="sxs-lookup"><span data-stu-id="c09da-128">Binding Markup Extension</span></span>](../wpf/advanced/binding-markup-extension.md)
