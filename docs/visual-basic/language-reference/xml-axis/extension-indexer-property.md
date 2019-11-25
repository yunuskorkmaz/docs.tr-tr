---
title: Extension Indexer Özelliği
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
ms.openlocfilehash: 5f91dc8a6b1a0d82daa4891cf826c16e2716839f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352694"
---
# <a name="extension-indexer-property-visual-basic"></a><span data-ttu-id="d9723-102">Extension Indexer Özelliği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9723-102">Extension Indexer Property (Visual Basic)</span></span>
<span data-ttu-id="d9723-103">Provides access to individual elements in a collection.</span><span class="sxs-lookup"><span data-stu-id="d9723-103">Provides access to individual elements in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9723-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9723-104">Syntax</span></span>  
  
```vb  
object(index)  
```  
  
## <a name="parts"></a><span data-ttu-id="d9723-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="d9723-105">Parts</span></span>  
  
|<span data-ttu-id="d9723-106">Terim</span><span class="sxs-lookup"><span data-stu-id="d9723-106">Term</span></span>|<span data-ttu-id="d9723-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="d9723-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="d9723-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d9723-108">Required.</span></span> <span data-ttu-id="d9723-109">A queryable collection.</span><span class="sxs-lookup"><span data-stu-id="d9723-109">A queryable collection.</span></span> <span data-ttu-id="d9723-110">That is, a collection that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="d9723-110">That is, a collection that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>|  
|<span data-ttu-id="d9723-111">(</span><span class="sxs-lookup"><span data-stu-id="d9723-111">(</span></span>|<span data-ttu-id="d9723-112">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d9723-112">Required.</span></span> <span data-ttu-id="d9723-113">Denotes the start of the indexer property.</span><span class="sxs-lookup"><span data-stu-id="d9723-113">Denotes the start of the indexer property.</span></span>|  
|`index`|<span data-ttu-id="d9723-114">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d9723-114">Required.</span></span> <span data-ttu-id="d9723-115">An integer expression that specifies the zero-based position of an element of the collection.</span><span class="sxs-lookup"><span data-stu-id="d9723-115">An integer expression that specifies the zero-based position of an element of the collection.</span></span>|  
|<span data-ttu-id="d9723-116">)</span><span class="sxs-lookup"><span data-stu-id="d9723-116">)</span></span>|<span data-ttu-id="d9723-117">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d9723-117">Required.</span></span> <span data-ttu-id="d9723-118">Denotes the end of the indexer property.</span><span class="sxs-lookup"><span data-stu-id="d9723-118">Denotes the end of the indexer property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="d9723-119">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d9723-119">Return Value</span></span>  
 <span data-ttu-id="d9723-120">The object from the specified location in the collection, or `Nothing` if the index is out of range.</span><span class="sxs-lookup"><span data-stu-id="d9723-120">The object from the specified location in the collection, or `Nothing` if the index is out of range.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9723-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d9723-121">Remarks</span></span>  
 <span data-ttu-id="d9723-122">You can use the extension indexer property to access individual elements in a collection.</span><span class="sxs-lookup"><span data-stu-id="d9723-122">You can use the extension indexer property to access individual elements in a collection.</span></span> <span data-ttu-id="d9723-123">This indexer property is typically used on the output of XML axis properties.</span><span class="sxs-lookup"><span data-stu-id="d9723-123">This indexer property is typically used on the output of XML axis properties.</span></span> <span data-ttu-id="d9723-124">The XML child and XML descendent axis properties return collections of <xref:System.Xml.Linq.XElement> objects or an attribute value.</span><span class="sxs-lookup"><span data-stu-id="d9723-124">The XML child and XML descendent axis properties return collections of <xref:System.Xml.Linq.XElement> objects or an attribute value.</span></span>  
  
 <span data-ttu-id="d9723-125">The Visual Basic compiler converts extension indexer properties to calls to the `ElementAtOrDefault` method.</span><span class="sxs-lookup"><span data-stu-id="d9723-125">The Visual Basic compiler converts extension indexer properties to calls to the `ElementAtOrDefault` method.</span></span> <span data-ttu-id="d9723-126">Unlike an array indexer, the `ElementAtOrDefault` method returns `Nothing` if the index is out of range.</span><span class="sxs-lookup"><span data-stu-id="d9723-126">Unlike an array indexer, the `ElementAtOrDefault` method returns `Nothing` if the index is out of range.</span></span> <span data-ttu-id="d9723-127">This behavior is useful when you cannot easily determine the number of elements in a collection.</span><span class="sxs-lookup"><span data-stu-id="d9723-127">This behavior is useful when you cannot easily determine the number of elements in a collection.</span></span>  
  
 <span data-ttu-id="d9723-128">This indexer property is like an extension property for collections that implement <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>: it is used only if the collection does not have an indexer or a default property.</span><span class="sxs-lookup"><span data-stu-id="d9723-128">This indexer property is like an extension property for collections that implement <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>: it is used only if the collection does not have an indexer or a default property.</span></span>  
  
 <span data-ttu-id="d9723-129">To access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, you can use the XML `Value` property.</span><span class="sxs-lookup"><span data-stu-id="d9723-129">To access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, you can use the XML `Value` property.</span></span> <span data-ttu-id="d9723-130">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="d9723-130">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9723-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="d9723-131">Example</span></span>  
 <span data-ttu-id="d9723-132">The following example shows how to use the extension indexer to access the second child node in a collection of <xref:System.Xml.Linq.XElement> objects.</span><span class="sxs-lookup"><span data-stu-id="d9723-132">The following example shows how to use the extension indexer to access the second child node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="d9723-133">The collection is accessed by using the child axis property, which gets all child elements named `phone` in the `contact` object.</span><span class="sxs-lookup"><span data-stu-id="d9723-133">The collection is accessed by using the child axis property, which gets all child elements named `phone` in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#24)]  
  
 <span data-ttu-id="d9723-134">This code displays the following text:</span><span class="sxs-lookup"><span data-stu-id="d9723-134">This code displays the following text:</span></span>  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a><span data-ttu-id="d9723-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9723-135">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="d9723-136">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="d9723-136">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="d9723-137">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="d9723-137">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="d9723-138">Creating XML in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d9723-138">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="d9723-139">XML Value Özelliği</span><span class="sxs-lookup"><span data-stu-id="d9723-139">XML Value Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
