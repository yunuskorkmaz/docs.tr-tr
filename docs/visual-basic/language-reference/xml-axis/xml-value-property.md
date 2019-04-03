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
ms.openlocfilehash: 1c7aa1cc32bc1c5ef637f7a606db7e695f1dfaee
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821957"
---
# <a name="xml-value-property-visual-basic"></a><span data-ttu-id="42a19-102">XML Değeri Özelliği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42a19-102">XML Value Property (Visual Basic)</span></span>
<span data-ttu-id="42a19-103">Koleksiyonunu ilk öğenin değerini erişim sağlayan <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="42a19-103">Provides access to the value of the first element of a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42a19-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="42a19-104">Syntax</span></span>  
  
```  
object.Value  
```  
  
## <a name="parts"></a><span data-ttu-id="42a19-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="42a19-105">Parts</span></span>  
  
|<span data-ttu-id="42a19-106">Terim</span><span class="sxs-lookup"><span data-stu-id="42a19-106">Term</span></span>|<span data-ttu-id="42a19-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="42a19-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="42a19-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="42a19-108">Required.</span></span> <span data-ttu-id="42a19-109">Koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="42a19-109">Collection of <xref:System.Xml.Linq.XElement> objects.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="42a19-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="42a19-110">Return Value</span></span>  
 <span data-ttu-id="42a19-111">A `String` koleksiyonun ilk öğenin değerini içeren veya `Nothing` koleksiyonu boş ise.</span><span class="sxs-lookup"><span data-stu-id="42a19-111">A `String` that contains the value of the first element of the collection, or `Nothing` if the collection is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42a19-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="42a19-112">Remarks</span></span>  
 <span data-ttu-id="42a19-113"><xref:System.Xml.Linq.XElement.Value%2A> Özelliği bir koleksiyondaki ilk öğenin değere erişmek kolaylaştırır <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="42a19-113">The <xref:System.Xml.Linq.XElement.Value%2A> property makes it easy to access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="42a19-114">Bu özellik, ilk koleksiyon en az bir nesne içerip içermediğini denetler.</span><span class="sxs-lookup"><span data-stu-id="42a19-114">This property first checks whether the collection contains at least one object.</span></span> <span data-ttu-id="42a19-115">Bu özellik koleksiyonu boş ise döndürür `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="42a19-115">If the collection is empty, this property returns `Nothing`.</span></span> <span data-ttu-id="42a19-116">Aksi takdirde, bu özellik değerini döndürür <xref:System.Xml.Linq.XElement.Value%2A> koleksiyondaki ilk öğenin özellik.</span><span class="sxs-lookup"><span data-stu-id="42a19-116">Otherwise, this property returns the value of the <xref:System.Xml.Linq.XElement.Value%2A> property of the first element in the collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="42a19-117">Kullanarak bir XML özniteliği değeri eriştiğinizde '\@' tanımlayıcısı, öznitelik değeri olarak döndürülür bir `String` ve açıkça belirtmeniz gerekmez <xref:System.Xml.Linq.XAttribute.Value%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="42a19-117">When you access the value of an XML attribute using the '\@' identifier, the attribute value is returned as a `String` and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="42a19-118">Bir koleksiyondaki diğer öğelere erişmek için XML uzantı dizin oluşturucu özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42a19-118">To access other elements in a collection, you can use the XML extension indexer property.</span></span> <span data-ttu-id="42a19-119">Daha fazla bilgi için [Extension Indexer özelliği](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).</span><span class="sxs-lookup"><span data-stu-id="42a19-119">For more information, see [Extension Indexer Property](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).</span></span>  
  
## <a name="inheritance"></a><span data-ttu-id="42a19-120">Devralma</span><span class="sxs-lookup"><span data-stu-id="42a19-120">Inheritance</span></span>  
 <span data-ttu-id="42a19-121">Çoğu kullanıcı uygulamak zorunda <xref:System.Collections.Generic.IEnumerable%601>ve bu nedenle bu bölüm yoksayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42a19-121">Most users will not have to implement <xref:System.Collections.Generic.IEnumerable%601>, and can therefore ignore this section.</span></span>  
  
 <span data-ttu-id="42a19-122"><xref:System.Xml.Linq.XElement.Value%2A> Özelliği uygulayan türler için bir uzantı özelliği `IEnumerable(Of XElement)`.</span><span class="sxs-lookup"><span data-stu-id="42a19-122">The <xref:System.Xml.Linq.XElement.Value%2A> property is an extension property for types that implement `IEnumerable(Of XElement)`.</span></span> <span data-ttu-id="42a19-123">Uzantı yöntemleri bağlama gibi bağlamadır bu uzantı özelliğinin: Bu özellik bir tür arabirimlerinden birini uygular ve "Value" adına sahip bir özelliğini tanımlar, uzantı özelliği önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="42a19-123">The binding of this extension property is like the binding of extension methods: if a type implements one of the interfaces and defines a property that has the name "Value", that property has precedence over the extension property.</span></span> <span data-ttu-id="42a19-124">Diğer bir deyişle, bu <xref:System.Xml.Linq.XElement.Value%2A> özelliği, yeni bir özelliği uygulayan bir sınıf tanımlayarak kılınabilir `IEnumerable(Of XElement)`.</span><span class="sxs-lookup"><span data-stu-id="42a19-124">In other words, this <xref:System.Xml.Linq.XElement.Value%2A> property can be overridden by defining a new property in a class that implements `IEnumerable(Of XElement)`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42a19-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="42a19-125">Example</span></span>  
 <span data-ttu-id="42a19-126">Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Xml.Linq.XElement.Value%2A> koleksiyonunu ilk düğüm erişmek için özelliği <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="42a19-126">The following example shows how to use the <xref:System.Xml.Linq.XElement.Value%2A> property to access the first node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="42a19-127">Örnek child axis özelliği adlı tüm alt düğümleri koleksiyonu almak için kullanır. `phone` bulunan `contact` nesne.</span><span class="sxs-lookup"><span data-stu-id="42a19-127">The example uses the child axis property to get the collection of all child nodes named `phone` that are in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#15)]  
  
 <span data-ttu-id="42a19-128">Bu kod, aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="42a19-128">This code displays the following text:</span></span>  
  
 `Phone number: 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="42a19-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="42a19-129">Example</span></span>  
 <span data-ttu-id="42a19-130">Aşağıdaki örnek koleksiyonundan bir XML özniteliği değeri almak nasıl gösterir <xref:System.Xml.Linq.XAttribute> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="42a19-130">The following example shows how to get the value of an XML attribute from a collection of <xref:System.Xml.Linq.XAttribute> objects.</span></span> <span data-ttu-id="42a19-131">Örnek attribute axis özelliği değerini görüntülemek için kullanır. `type` özniteliği için tüm `phone` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="42a19-131">The example uses the attribute axis property to display the value of the `type` attribute for all of the `phone` elements.</span></span>  
  
 [!code-vb[VbXMLSamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#16)]  
  
 <span data-ttu-id="42a19-132">Bu kod, aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="42a19-132">This code displays the following text:</span></span>  
  
 `home`  
  
 `work`  
  
## <a name="see-also"></a><span data-ttu-id="42a19-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42a19-133">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="42a19-134">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="42a19-134">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="42a19-135">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="42a19-135">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="42a19-136">Visual Basic'de XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="42a19-136">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="42a19-137">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="42a19-137">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="42a19-138">Extension Indexer Özelliği</span><span class="sxs-lookup"><span data-stu-id="42a19-138">Extension Indexer Property</span></span>](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)
- [<span data-ttu-id="42a19-139">XML Alt Axis Özelliği</span><span class="sxs-lookup"><span data-stu-id="42a19-139">XML Child Axis Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="42a19-140">XML Özniteliği Axis Özelliği</span><span class="sxs-lookup"><span data-stu-id="42a19-140">XML Attribute Axis Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
