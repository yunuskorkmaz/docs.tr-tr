---
title: XML Değeri Özelliği (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionValue
helpviewer_keywords:
- Value property [Visual Basic]
- Visual Basic code, accessing XML
- XML axis [Visual Basic], Value
- XML Value property [Visual Basic]
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
ms.openlocfilehash: 9edf95c7cedced55ab2441baf51b7c2052e4654c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942989"
---
# <a name="xml-value-property-visual-basic"></a><span data-ttu-id="ace70-102">XML Değeri Özelliği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ace70-102">XML Value Property (Visual Basic)</span></span>
<span data-ttu-id="ace70-103">Bir <xref:System.Xml.Linq.XElement> nesne koleksiyonunun ilk öğesinin değerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="ace70-103">Provides access to the value of the first element of a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ace70-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ace70-104">Syntax</span></span>  
  
```  
object.Value  
```  
  
## <a name="parts"></a><span data-ttu-id="ace70-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="ace70-105">Parts</span></span>  
  
|<span data-ttu-id="ace70-106">Terim</span><span class="sxs-lookup"><span data-stu-id="ace70-106">Term</span></span>|<span data-ttu-id="ace70-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="ace70-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="ace70-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="ace70-108">Required.</span></span> <span data-ttu-id="ace70-109"><xref:System.Xml.Linq.XElement> Nesne koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ace70-109">Collection of <xref:System.Xml.Linq.XElement> objects.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="ace70-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ace70-110">Return Value</span></span>  
 <span data-ttu-id="ace70-111">Koleksiyonun `String` ilk öğesinin değerini içeren bir veya `Nothing` koleksiyon boşsa.</span><span class="sxs-lookup"><span data-stu-id="ace70-111">A `String` that contains the value of the first element of the collection, or `Nothing` if the collection is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ace70-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ace70-112">Remarks</span></span>  
 <span data-ttu-id="ace70-113">Özelliği <xref:System.Xml.Linq.XElement.Value%2A> , bir <xref:System.Xml.Linq.XElement> nesne koleksiyonundaki ilk öğenin değerine erişmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="ace70-113">The <xref:System.Xml.Linq.XElement.Value%2A> property makes it easy to access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="ace70-114">Bu özellik önce koleksiyonun en az bir nesne içerip içermediğini denetler.</span><span class="sxs-lookup"><span data-stu-id="ace70-114">This property first checks whether the collection contains at least one object.</span></span> <span data-ttu-id="ace70-115">Koleksiyon boşsa, bu özellik döndürür `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="ace70-115">If the collection is empty, this property returns `Nothing`.</span></span> <span data-ttu-id="ace70-116">Aksi takdirde, bu özellik koleksiyondaki ilk öğenin <xref:System.Xml.Linq.XElement.Value%2A> özelliğinin değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="ace70-116">Otherwise, this property returns the value of the <xref:System.Xml.Linq.XElement.Value%2A> property of the first element in the collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ace70-117">Bir xml özniteliğinin değerine '\@' tanımlayıcısını kullanarak eriştiğinizde, öznitelik değeri bir `String` olarak döndürülür ve <xref:System.Xml.Linq.XAttribute.Value%2A> özelliği açıkça belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ace70-117">When you access the value of an XML attribute using the '\@' identifier, the attribute value is returned as a `String` and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="ace70-118">Bir koleksiyondaki diğer öğelere erişmek için XML uzantısı Indexer özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ace70-118">To access other elements in a collection, you can use the XML extension indexer property.</span></span> <span data-ttu-id="ace70-119">Daha fazla bilgi için bkz. [uzantı Dizin Oluşturucu özelliği](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).</span><span class="sxs-lookup"><span data-stu-id="ace70-119">For more information, see [Extension Indexer Property](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).</span></span>  
  
## <a name="inheritance"></a><span data-ttu-id="ace70-120">Devralma</span><span class="sxs-lookup"><span data-stu-id="ace70-120">Inheritance</span></span>  
 <span data-ttu-id="ace70-121">Çoğu kullanıcının uygulaması <xref:System.Collections.Generic.IEnumerable%601>ve bu bölümü yoksayması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ace70-121">Most users will not have to implement <xref:System.Collections.Generic.IEnumerable%601>, and can therefore ignore this section.</span></span>  
  
 <span data-ttu-id="ace70-122">Özelliği, uygulayan `IEnumerable(Of XElement)`türler için bir genişletme özelliğidir. <xref:System.Xml.Linq.XElement.Value%2A></span><span class="sxs-lookup"><span data-stu-id="ace70-122">The <xref:System.Xml.Linq.XElement.Value%2A> property is an extension property for types that implement `IEnumerable(Of XElement)`.</span></span> <span data-ttu-id="ace70-123">Bu uzantı özelliğinin bağlaması uzantı yöntemlerinin bağlaması gibidir: bir tür arabirimlerden birini uygular ve "Value" adlı bir özellik tanımlıyorsa, bu özellik uzantı özelliğine göre önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ace70-123">The binding of this extension property is like the binding of extension methods: if a type implements one of the interfaces and defines a property that has the name "Value", that property has precedence over the extension property.</span></span> <span data-ttu-id="ace70-124">Diğer bir deyişle, bu <xref:System.Xml.Linq.XElement.Value%2A> özellik, uygulayan `IEnumerable(Of XElement)`bir sınıfta yeni bir özellik tanımlayarak geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="ace70-124">In other words, this <xref:System.Xml.Linq.XElement.Value%2A> property can be overridden by defining a new property in a class that implements `IEnumerable(Of XElement)`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ace70-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="ace70-125">Example</span></span>  
 <span data-ttu-id="ace70-126">Aşağıdaki örnek, bir <xref:System.Xml.Linq.XElement.Value%2A> <xref:System.Xml.Linq.XElement> nesne koleksiyonundaki ilk düğüme erişmek için özelliğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ace70-126">The following example shows how to use the <xref:System.Xml.Linq.XElement.Value%2A> property to access the first node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="ace70-127">Örnek, `phone` `contact` nesnesinde olan adlı tüm alt düğümlerin koleksiyonunu almak için alt eksen özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ace70-127">The example uses the child axis property to get the collection of all child nodes named `phone` that are in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#15)]  
  
 <span data-ttu-id="ace70-128">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="ace70-128">This code displays the following text:</span></span>  
  
 `Phone number: 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="ace70-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="ace70-129">Example</span></span>  
 <span data-ttu-id="ace70-130">Aşağıdaki örnek bir <xref:System.Xml.Linq.XAttribute> nesne koleksiyonundan bir XML özniteliği değerinin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ace70-130">The following example shows how to get the value of an XML attribute from a collection of <xref:System.Xml.Linq.XAttribute> objects.</span></span> <span data-ttu-id="ace70-131">Örnek, tüm `type` `phone` öğelerin öznitelik değerini göstermek için öznitelik ekseni özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ace70-131">The example uses the attribute axis property to display the value of the `type` attribute for all of the `phone` elements.</span></span>  
  
 [!code-vb[VbXMLSamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#16)]  
  
 <span data-ttu-id="ace70-132">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="ace70-132">This code displays the following text:</span></span>  
  
 `home`  
  
 `work`  
  
## <a name="see-also"></a><span data-ttu-id="ace70-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ace70-133">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="ace70-134">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="ace70-134">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="ace70-135">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="ace70-135">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="ace70-136">Visual Basic XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="ace70-136">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="ace70-137">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="ace70-137">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="ace70-138">Extension Indexer Özelliği</span><span class="sxs-lookup"><span data-stu-id="ace70-138">Extension Indexer Property</span></span>](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)
- [<span data-ttu-id="ace70-139">XML Alt Axis Özelliği</span><span class="sxs-lookup"><span data-stu-id="ace70-139">XML Child Axis Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="ace70-140">XML Özniteliği Axis Özelliği</span><span class="sxs-lookup"><span data-stu-id="ace70-140">XML Attribute Axis Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
