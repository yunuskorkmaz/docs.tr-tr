---
title: Extension Indexer Özelliği (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
ms.openlocfilehash: 660cebadc78d260350f2849f7f4926f9cef7c8d2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582193"
---
# <a name="extension-indexer-property-visual-basic"></a><span data-ttu-id="a84fd-102">Extension Indexer Özelliği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a84fd-102">Extension Indexer Property (Visual Basic)</span></span>
<span data-ttu-id="a84fd-103">Bir koleksiyondaki tek tek öğelere erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="a84fd-103">Provides access to individual elements in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a84fd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a84fd-104">Syntax</span></span>  
  
```vb  
object(index)  
```  
  
## <a name="parts"></a><span data-ttu-id="a84fd-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="a84fd-105">Parts</span></span>  
  
|<span data-ttu-id="a84fd-106">Terim</span><span class="sxs-lookup"><span data-stu-id="a84fd-106">Term</span></span>|<span data-ttu-id="a84fd-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="a84fd-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="a84fd-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="a84fd-108">Required.</span></span> <span data-ttu-id="a84fd-109">Sorgulanabilir bir koleksiyon.</span><span class="sxs-lookup"><span data-stu-id="a84fd-109">A queryable collection.</span></span> <span data-ttu-id="a84fd-110">Diğer bir deyişle, <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Linq.IQueryable%601> uygulayan bir koleksiyon.</span><span class="sxs-lookup"><span data-stu-id="a84fd-110">That is, a collection that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>|  
|<span data-ttu-id="a84fd-111">(</span><span class="sxs-lookup"><span data-stu-id="a84fd-111">(</span></span>|<span data-ttu-id="a84fd-112">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="a84fd-112">Required.</span></span> <span data-ttu-id="a84fd-113">Dizin Oluşturucu özelliğinin başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a84fd-113">Denotes the start of the indexer property.</span></span>|  
|`index`|<span data-ttu-id="a84fd-114">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="a84fd-114">Required.</span></span> <span data-ttu-id="a84fd-115">Koleksiyonun bir öğesinin sıfır tabanlı konumunu belirten bir tamsayı ifadesi.</span><span class="sxs-lookup"><span data-stu-id="a84fd-115">An integer expression that specifies the zero-based position of an element of the collection.</span></span>|  
|<span data-ttu-id="a84fd-116">)</span><span class="sxs-lookup"><span data-stu-id="a84fd-116">)</span></span>|<span data-ttu-id="a84fd-117">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="a84fd-117">Required.</span></span> <span data-ttu-id="a84fd-118">Dizin Oluşturucu özelliğinin sonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a84fd-118">Denotes the end of the indexer property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="a84fd-119">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a84fd-119">Return Value</span></span>  
 <span data-ttu-id="a84fd-120">Koleksiyonda belirtilen konumdan nesne veya dizin Aralık dışında `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="a84fd-120">The object from the specified location in the collection, or `Nothing` if the index is out of range.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a84fd-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a84fd-121">Remarks</span></span>  
 <span data-ttu-id="a84fd-122">Bir koleksiyondaki tek tek öğelere erişmek için uzantı Indexer özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a84fd-122">You can use the extension indexer property to access individual elements in a collection.</span></span> <span data-ttu-id="a84fd-123">Bu Indexer özelliği genellikle XML ekseni özelliklerinin çıkışında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a84fd-123">This indexer property is typically used on the output of XML axis properties.</span></span> <span data-ttu-id="a84fd-124">XML Child ve XML alt öğe ekseni özellikleri <xref:System.Xml.Linq.XElement> nesnelerinin veya bir öznitelik değerinin koleksiyonlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="a84fd-124">The XML child and XML descendent axis properties return collections of <xref:System.Xml.Linq.XElement> objects or an attribute value.</span></span>  
  
 <span data-ttu-id="a84fd-125">Visual Basic derleyici, uzantı Dizin Oluşturucu özelliklerini `ElementAtOrDefault` yöntemine yapılan çağrılara dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="a84fd-125">The Visual Basic compiler converts extension indexer properties to calls to the `ElementAtOrDefault` method.</span></span> <span data-ttu-id="a84fd-126">Dizi Indexer 'ın aksine, Dizin aralık dışında `ElementAtOrDefault` yöntemi `Nothing` döndürür.</span><span class="sxs-lookup"><span data-stu-id="a84fd-126">Unlike an array indexer, the `ElementAtOrDefault` method returns `Nothing` if the index is out of range.</span></span> <span data-ttu-id="a84fd-127">Bu davranış, bir koleksiyondaki öğe sayısını kolayca belirleyene zaman yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="a84fd-127">This behavior is useful when you cannot easily determine the number of elements in a collection.</span></span>  
  
 <span data-ttu-id="a84fd-128">Bu Indexer özelliği <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Linq.IQueryable%601> uygulayan koleksiyonlar için bir uzantı özelliği gibidir: yalnızca koleksiyonda bir Dizin Oluşturucu veya varsayılan özellik yoksa kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a84fd-128">This indexer property is like an extension property for collections that implement <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>: it is used only if the collection does not have an indexer or a default property.</span></span>  
  
 <span data-ttu-id="a84fd-129">@No__t_0 veya <xref:System.Xml.Linq.XAttribute> nesneleri koleksiyonundaki ilk öğenin değerine erişmek için XML `Value` özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a84fd-129">To access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, you can use the XML `Value` property.</span></span> <span data-ttu-id="a84fd-130">Daha fazla bilgi için bkz. [XML Value özelliği](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="a84fd-130">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a84fd-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="a84fd-131">Example</span></span>  
 <span data-ttu-id="a84fd-132">Aşağıdaki örnek, bir <xref:System.Xml.Linq.XElement> nesneleri koleksiyonundaki ikinci alt düğüme erişmek için uzantı dizin oluşturucunun nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a84fd-132">The following example shows how to use the extension indexer to access the second child node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="a84fd-133">Koleksiyona, `contact` nesnesinde `phone` adlı tüm alt öğeleri alan alt eksen özelliği kullanılarak erişilir.</span><span class="sxs-lookup"><span data-stu-id="a84fd-133">The collection is accessed by using the child axis property, which gets all child elements named `phone` in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#24)]  
  
 <span data-ttu-id="a84fd-134">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="a84fd-134">This code displays the following text:</span></span>  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a><span data-ttu-id="a84fd-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a84fd-135">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="a84fd-136">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="a84fd-136">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="a84fd-137">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="a84fd-137">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="a84fd-138">Visual Basic XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="a84fd-138">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="a84fd-139">XML Value Özelliği</span><span class="sxs-lookup"><span data-stu-id="a84fd-139">XML Value Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
