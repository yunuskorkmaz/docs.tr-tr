---
title: "Extension Indexer Özelliği (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 99d14b6e54a59ffc904a9e786c22498d23ee8ab6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="extension-indexer-property-visual-basic"></a><span data-ttu-id="d0189-102">Extension Indexer Özelliği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0189-102">Extension Indexer Property (Visual Basic)</span></span>
<span data-ttu-id="d0189-103">Bir koleksiyondaki tek tek öğelere erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0189-103">Provides access to individual elements in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0189-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0189-104">Syntax</span></span>  
  
```  
object(index)  
```  
  
## <a name="parts"></a><span data-ttu-id="d0189-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="d0189-105">Parts</span></span>  
  
|<span data-ttu-id="d0189-106">Terim</span><span class="sxs-lookup"><span data-stu-id="d0189-106">Term</span></span>|<span data-ttu-id="d0189-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="d0189-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="d0189-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d0189-108">Required.</span></span> <span data-ttu-id="d0189-109">Sorgulanabilir bir koleksiyon.</span><span class="sxs-lookup"><span data-stu-id="d0189-109">A queryable collection.</span></span> <span data-ttu-id="d0189-110">Diğer bir deyişle, uygulayan koleksiyondan <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="d0189-110">That is, a collection that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>|  
|<span data-ttu-id="d0189-111">(</span><span class="sxs-lookup"><span data-stu-id="d0189-111">(</span></span>|<span data-ttu-id="d0189-112">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d0189-112">Required.</span></span> <span data-ttu-id="d0189-113">Dizin Oluşturucu özelliği başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0189-113">Denotes the start of the indexer property.</span></span>|  
|`index`|<span data-ttu-id="d0189-114">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d0189-114">Required.</span></span> <span data-ttu-id="d0189-115">Koleksiyonun bir öğesi sıfır tabanlı konumu belirten bir tamsayı ifade.</span><span class="sxs-lookup"><span data-stu-id="d0189-115">An integer expression that specifies the zero-based position of an element of the collection.</span></span>|  
|<span data-ttu-id="d0189-116">)</span><span class="sxs-lookup"><span data-stu-id="d0189-116">)</span></span>|<span data-ttu-id="d0189-117">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d0189-117">Required.</span></span> <span data-ttu-id="d0189-118">Dizin Oluşturucu özelliği sonunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0189-118">Denotes the end of the indexer property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="d0189-119">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d0189-119">Return Value</span></span>  
 <span data-ttu-id="d0189-120">Koleksiyonun belirtilen konumda nesnesinden veya `Nothing` dizini aralık dışında olması durumunda.</span><span class="sxs-lookup"><span data-stu-id="d0189-120">The object from the specified location in the collection, or `Nothing` if the index is out of range.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0189-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d0189-121">Remarks</span></span>  
 <span data-ttu-id="d0189-122">Extension Indexer özelliği ayrı ayrı öğeler bir koleksiyondaki erişmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0189-122">You can use the extension indexer property to access individual elements in a collection.</span></span> <span data-ttu-id="d0189-123">Bu dizin oluşturucu özelliği, genellikle XML eksen özellikleri Çıkışta kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d0189-123">This indexer property is typically used on the output of XML axis properties.</span></span> <span data-ttu-id="d0189-124">XML descendent axis özellikleri ve XML alt koleksiyonları dönmek <xref:System.Xml.Linq.XElement> nesneleri veya bir öznitelik değeri.</span><span class="sxs-lookup"><span data-stu-id="d0189-124">The XML child and XML descendent axis properties return collections of <xref:System.Xml.Linq.XElement> objects or an attribute value.</span></span>  
  
 <span data-ttu-id="d0189-125">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Derleyici çağrıları uzantı dizin oluşturucu özellikleri dönüştürür `ElementAtOrDefault` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d0189-125">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler converts extension indexer properties to calls to the `ElementAtOrDefault` method.</span></span> <span data-ttu-id="d0189-126">Bir dizi dizin oluşturucu aksine `ElementAtOrDefault` yöntemi döndürür `Nothing` dizini aralık dışında olması durumunda.</span><span class="sxs-lookup"><span data-stu-id="d0189-126">Unlike an array indexer, the `ElementAtOrDefault` method returns `Nothing` if the index is out of range.</span></span> <span data-ttu-id="d0189-127">Bu davranış, bir koleksiyondaki öğe sayısını kolayca belirleyemezsiniz yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="d0189-127">This behavior is useful when you cannot easily determine the number of elements in a collection.</span></span>  
  
 <span data-ttu-id="d0189-128">Uzantı özelliği uygulamak koleksiyonlar için bu dizin oluşturucu özelliği benzer <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Linq.IQueryable%601>: yalnızca koleksiyon bir dizin oluşturucu veya varsayılan bir özellik yoksa kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d0189-128">This indexer property is like an extension property for collections that implement <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>: it is used only if the collection does not have an indexer or a default property.</span></span>  
  
 <span data-ttu-id="d0189-129">Bir koleksiyonu ilk öğe değerini erişmek için <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute> nesneleri, XML kullanabileceğiniz `Value` özelliği.</span><span class="sxs-lookup"><span data-stu-id="d0189-129">To access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, you can use the XML `Value` property.</span></span> <span data-ttu-id="d0189-130">Daha fazla bilgi için bkz: [XML değeri özelliği](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="d0189-130">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0189-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="d0189-131">Example</span></span>  
 <span data-ttu-id="d0189-132">Aşağıdaki örnek uzantı dizin oluşturucu koleksiyonu ikinci alt düğümünde erişmek için nasıl kullanılacağını gösterir <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="d0189-132">The following example shows how to use the extension indexer to access the second child node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="d0189-133">Koleksiyon adlı tüm alt öğeleri alır child axis özelliği kullanılarak erişilir `phone` içinde `contact` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="d0189-133">The collection is accessed by using the child axis property, which gets all child elements named `phone` in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#24](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/extension-indexer-property_1.vb)]  
  
 <span data-ttu-id="d0189-134">Bu kod, aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="d0189-134">This code displays the following text:</span></span>  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a><span data-ttu-id="d0189-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d0189-135">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 [<span data-ttu-id="d0189-136">XML eksen özellikleri</span><span class="sxs-lookup"><span data-stu-id="d0189-136">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [<span data-ttu-id="d0189-137">XML değişmez değerleri</span><span class="sxs-lookup"><span data-stu-id="d0189-137">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="d0189-138">Visual Basic'de XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="d0189-138">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="d0189-139">XML değeri özelliği</span><span class="sxs-lookup"><span data-stu-id="d0189-139">XML Value Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
