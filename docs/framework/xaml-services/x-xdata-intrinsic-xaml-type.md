---
title: "x:XData İç XAML Türü"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- x:XData
- XData
- xXData
helpviewer_keywords:
- XAML [XAML Services], x:XData directive element
- XData in XAML [XAML Services]
- x:XData XAML directive element [XAML Services]
ms.assetid: 7ce209c2-621b-4977-b643-565f7e663534
caps.latest.revision: "17"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ec46d0363e5b10d3bd3bd3f9c8f4d3694abc1c8d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="xxdata-intrinsic-xaml-type"></a><span data-ttu-id="83d8a-102">x:XData İç XAML Türü</span><span class="sxs-lookup"><span data-stu-id="83d8a-102">x:XData Intrinsic XAML Type</span></span>
<span data-ttu-id="83d8a-103">XAML üretim içinde XML veri Adaları yerleşimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="83d8a-103">Enables placement of XML data islands within a XAML production.</span></span> <span data-ttu-id="83d8a-104">XML öğeleri içinde `x:XData` hareket varsayılan XAML ad uzayı parçası veya diğer bir XAML ad olmaları durumunda gibi XAML işlemcileri tarafından değerlendirilmelidir değil.</span><span class="sxs-lookup"><span data-stu-id="83d8a-104">XML elements within `x:XData` should not be treated by XAML processors as if they are a part of the acting default XAML namespace or any other XAML namespace.</span></span> <span data-ttu-id="83d8a-105">`x:XData`rastgele doğru biçimlendirilmiş XML içerebilir.</span><span class="sxs-lookup"><span data-stu-id="83d8a-105">`x:XData` can contain arbitrary well-formed XML.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="83d8a-106">XAML Nesne Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="83d8a-106">XAML Object Element Usage</span></span>  
  
```  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="83d8a-107">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="83d8a-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`elementDataRoot`|<span data-ttu-id="83d8a-108">Kapalı veri adası tek bir kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="83d8a-108">The single root element of the enclosed data island.</span></span> <span data-ttu-id="83d8a-109">En son Tüketiciler için tek bir kök olmayan XML geçersiz olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="83d8a-109">For most eventual consumers, XML that does not have a single root is considered invalid.</span></span> <span data-ttu-id="83d8a-110">Özellikle, tek bir kök gerekli ise `x:XData` bir XML veri kaynağı olarak WPF veya XML kaynakları için veri bağlamayı kullanan diğer pek çok teknoloji yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="83d8a-110">In particular, a single root is required if the `x:XData` is intended as an XML data source for WPF or many other technologies that use XML sources for data binding.</span></span>|  
|`[elementData]`|<span data-ttu-id="83d8a-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="83d8a-111">Optional.</span></span> <span data-ttu-id="83d8a-112">XML verilerini temsil eden XML.</span><span class="sxs-lookup"><span data-stu-id="83d8a-112">XML that represents the XML data.</span></span> <span data-ttu-id="83d8a-113">Öğeleri herhangi bir sayıda öğe verileri bulunabilir ve iç içe geçmiş öğe diğer öğeleri bulunabilir; Ancak, XML genel kurallar uygulanır.</span><span class="sxs-lookup"><span data-stu-id="83d8a-113">Any number of elements can be contained as element data and nested elements can be contained in other elements; however, the general rules of XML apply.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83d8a-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="83d8a-114">Remarks</span></span>  
 <span data-ttu-id="83d8a-115">XML öğeleri içinde bir `x:XData` nesne tüm olası ad alanlarını ve öneklerini içeren XMLDOM verileri içinde yeniden bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83d8a-115">The XML elements within an `x:XData` object can re-declare all possible namespaces and prefixes of the containing XMLDOM within the data.</span></span>  
  
 <span data-ttu-id="83d8a-116">XML verileri programlı olarak erişim ve `x:XData` iç XAML türü olan .NET Framework XAML Hizmetleri aracılığıyla, olası <xref:System.Windows.Markup.XData> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="83d8a-116">Programmatic access to XML data and the `x:XData` intrinsic XAML type is possible in .NET Framework XAML Services through the <xref:System.Windows.Markup.XData> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="83d8a-117">WPF kullanım notları</span><span class="sxs-lookup"><span data-stu-id="83d8a-117">WPF Usage Notes</span></span>  
 <span data-ttu-id="83d8a-118">`x:XData` Nesnesi bir alt nesne olarak birincil olarak kullanılan bir <xref:System.Windows.Data.XmlDataProvider>, veya alternatif olarak, alt nesne <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> özelliği (XAML içinde bu genellikle özellik öğesi sözdiziminde ifade edilir).</span><span class="sxs-lookup"><span data-stu-id="83d8a-118">The `x:XData` object is primarily used as a child object of an <xref:System.Windows.Data.XmlDataProvider>, or alternatively, as the child object of the <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> property (in XAML, this is typically expressed in property element syntax).</span></span>  
  
 <span data-ttu-id="83d8a-119">Genellikle veri temel XML ad alanı (boş bir dize olarak ayarlayın) yeni bir varsayılan XML ad alanı olmasını veri adası içinde yeniden tanımlamanız.</span><span class="sxs-lookup"><span data-stu-id="83d8a-119">The data should typically redefine the base XML namespace within the data island to be a new default XML namespace (set to an empty string).</span></span> <span data-ttu-id="83d8a-120">Basit veri çünkü Adaları için bu en kolayıdır <xref:System.Windows.Data.Binding.XPath%2A> başvuru ve veri bağlamak için kullanılan ifadeleri önekleri ekleme özen gösterin.</span><span class="sxs-lookup"><span data-stu-id="83d8a-120">This is easiest for simple data islands because the <xref:System.Windows.Data.Binding.XPath%2A> expressions that are used to reference and bind to the data can avoid inclusion of prefixes.</span></span> <span data-ttu-id="83d8a-121">Daha karmaşık veri Adaları verileri birden çok ön eklerini tanımlayın ve XML ad alanı kökünde için belirli bir ön ekini kullanın.</span><span class="sxs-lookup"><span data-stu-id="83d8a-121">More complex data islands might define multiple prefixes for the data and use a specific prefix for the XML namespace at the root.</span></span> <span data-ttu-id="83d8a-122">Bu durumda, tüm <xref:System.Windows.Data.Binding.XPath%2A> ifade başvuruları uygun ad alanı eşlenen önek içermelidir.</span><span class="sxs-lookup"><span data-stu-id="83d8a-122">In this case, all <xref:System.Windows.Data.Binding.XPath%2A> expression references should include the appropriate namespace-mapped prefix.</span></span> <span data-ttu-id="83d8a-123">Daha fazla bilgi için bkz: [veri bağlama genel bakış](../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="83d8a-123">For more information, see [Data Binding Overview](../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="83d8a-124">Teknik olarak `x:XData` türü herhangi bir özelliği içeriği olarak kullanılan <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="83d8a-124">Technically, `x:XData` can be used as the content of any property of type <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="83d8a-125">Ancak, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> yalnızca belirgin uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="83d8a-125">However, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> is the only prominent implementation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83d8a-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="83d8a-126">See Also</span></span>  
 <xref:System.Windows.Data.XmlDataProvider>  
 [<span data-ttu-id="83d8a-127">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="83d8a-127">Data Binding Overview</span></span>](../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="83d8a-128">İşaretleme Uzantısı Bağlama</span><span class="sxs-lookup"><span data-stu-id="83d8a-128">Binding Markup Extension</span></span>](../../../docs/framework/wpf/advanced/binding-markup-extension.md)
