---
description: 'Daha fazla bilgi edinin: XML değeri özelliği (Visual Basic)'
title: XML Value Özelliği
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionValue
helpviewer_keywords:
- Value property [Visual Basic]
- Visual Basic code, accessing XML
- XML axis [Visual Basic], Value
- XML Value property [Visual Basic]
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
ms.openlocfilehash: 49762c1fcc0059472a5be11726aa344a001807ea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768772"
---
# <a name="xml-value-property-visual-basic"></a><span data-ttu-id="d0248-103">XML Değeri Özelliği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0248-103">XML Value Property (Visual Basic)</span></span>

<span data-ttu-id="d0248-104">Bir nesne koleksiyonunun ilk öğesinin değerine erişim sağlar <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="d0248-104">Provides access to the value of the first element of a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>

## <a name="syntax"></a><span data-ttu-id="d0248-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d0248-105">Syntax</span></span>

```vb
object.Value
```

## <a name="parts"></a><span data-ttu-id="d0248-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="d0248-106">Parts</span></span>

|<span data-ttu-id="d0248-107">Süre</span><span class="sxs-lookup"><span data-stu-id="d0248-107">Term</span></span>|<span data-ttu-id="d0248-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="d0248-108">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="d0248-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d0248-109">Required.</span></span> <span data-ttu-id="d0248-110">Nesne koleksiyonu <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="d0248-110">Collection of <xref:System.Xml.Linq.XElement> objects.</span></span>|  

## <a name="return-value"></a><span data-ttu-id="d0248-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d0248-111">Return Value</span></span>

 <span data-ttu-id="d0248-112">`String`Koleksiyonun ilk öğesinin değerini içeren bir veya `Nothing` Koleksiyon boşsa.</span><span class="sxs-lookup"><span data-stu-id="d0248-112">A `String` that contains the value of the first element of the collection, or `Nothing` if the collection is empty.</span></span>

## <a name="remarks"></a><span data-ttu-id="d0248-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d0248-113">Remarks</span></span>

 <span data-ttu-id="d0248-114"><xref:System.Xml.Linq.XElement.Value%2A>Özelliği, bir nesne koleksiyonundaki ilk öğenin değerine erişmeyi kolaylaştırır <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="d0248-114">The <xref:System.Xml.Linq.XElement.Value%2A> property makes it easy to access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="d0248-115">Bu özellik önce koleksiyonun en az bir nesne içerip içermediğini denetler.</span><span class="sxs-lookup"><span data-stu-id="d0248-115">This property first checks whether the collection contains at least one object.</span></span> <span data-ttu-id="d0248-116">Koleksiyon boşsa, bu özellik döndürür `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="d0248-116">If the collection is empty, this property returns `Nothing`.</span></span> <span data-ttu-id="d0248-117">Aksi takdirde, bu özellik <xref:System.Xml.Linq.XElement.Value%2A> koleksiyondaki ilk öğenin özelliğinin değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="d0248-117">Otherwise, this property returns the value of the <xref:System.Xml.Linq.XElement.Value%2A> property of the first element in the collection.</span></span>

> [!NOTE]
> <span data-ttu-id="d0248-118">Bir XML özniteliğinin değerine ' \@ ' tanımlayıcısını kullanarak eriştiğinizde, öznitelik değeri bir olarak döndürülür `String` ve özelliği açıkça belirtmeniz gerekmez <xref:System.Xml.Linq.XAttribute.Value%2A> .</span><span class="sxs-lookup"><span data-stu-id="d0248-118">When you access the value of an XML attribute using the '\@' identifier, the attribute value is returned as a `String` and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>

 <span data-ttu-id="d0248-119">Bir koleksiyondaki diğer öğelere erişmek için XML uzantısı Indexer özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0248-119">To access other elements in a collection, you can use the XML extension indexer property.</span></span> <span data-ttu-id="d0248-120">Daha fazla bilgi için bkz. [uzantı Dizin Oluşturucu özelliği](extension-indexer-property.md).</span><span class="sxs-lookup"><span data-stu-id="d0248-120">For more information, see [Extension Indexer Property](extension-indexer-property.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="d0248-121">Devralma</span><span class="sxs-lookup"><span data-stu-id="d0248-121">Inheritance</span></span>

 <span data-ttu-id="d0248-122">Çoğu kullanıcının uygulaması <xref:System.Collections.Generic.IEnumerable%601> ve bu bölümü yoksayması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d0248-122">Most users will not have to implement <xref:System.Collections.Generic.IEnumerable%601>, and can therefore ignore this section.</span></span>

 <span data-ttu-id="d0248-123"><xref:System.Xml.Linq.XElement.Value%2A>Özelliği, uygulayan türler için bir genişletme özelliğidir `IEnumerable(Of XElement)` .</span><span class="sxs-lookup"><span data-stu-id="d0248-123">The <xref:System.Xml.Linq.XElement.Value%2A> property is an extension property for types that implement `IEnumerable(Of XElement)`.</span></span> <span data-ttu-id="d0248-124">Bu uzantı özelliğinin bağlaması uzantı yöntemlerinin bağlaması gibidir: bir tür arabirimlerden birini uygular ve "Value" adlı bir özellik tanımlıyorsa, bu özellik uzantı özelliğine göre önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d0248-124">The binding of this extension property is like the binding of extension methods: if a type implements one of the interfaces and defines a property that has the name "Value", that property has precedence over the extension property.</span></span> <span data-ttu-id="d0248-125">Diğer bir deyişle, bu <xref:System.Xml.Linq.XElement.Value%2A> özellik, uygulayan bir sınıfta yeni bir özellik tanımlayarak geçersiz kılınabilir `IEnumerable(Of XElement)` .</span><span class="sxs-lookup"><span data-stu-id="d0248-125">In other words, this <xref:System.Xml.Linq.XElement.Value%2A> property can be overridden by defining a new property in a class that implements `IEnumerable(Of XElement)`.</span></span>

## <a name="example"></a><span data-ttu-id="d0248-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="d0248-126">Example</span></span>

 <span data-ttu-id="d0248-127">Aşağıdaki örnek, <xref:System.Xml.Linq.XElement.Value%2A> bir nesne koleksiyonundaki ilk düğüme erişmek için özelliğinin nasıl kullanılacağını gösterir <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="d0248-127">The following example shows how to use the <xref:System.Xml.Linq.XElement.Value%2A> property to access the first node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="d0248-128">Örnek, nesnesinde olan adlı tüm alt düğümlerin koleksiyonunu almak için alt eksen özelliğini kullanır `phone` `contact` .</span><span class="sxs-lookup"><span data-stu-id="d0248-128">The example uses the child axis property to get the collection of all child nodes named `phone` that are in the `contact` object.</span></span>

 [!code-vb[VbXMLSamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#15)]

 <span data-ttu-id="d0248-129">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="d0248-129">This code displays the following text:</span></span>

 `Phone number: 206-555-0144`

## <a name="example"></a><span data-ttu-id="d0248-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="d0248-130">Example</span></span>

 <span data-ttu-id="d0248-131">Aşağıdaki örnek bir nesne koleksiyonundan bir XML özniteliği değerinin nasıl alınacağını gösterir <xref:System.Xml.Linq.XAttribute> .</span><span class="sxs-lookup"><span data-stu-id="d0248-131">The following example shows how to get the value of an XML attribute from a collection of <xref:System.Xml.Linq.XAttribute> objects.</span></span> <span data-ttu-id="d0248-132">Örnek, tüm öğelerin öznitelik değerini göstermek için öznitelik ekseni özelliğini kullanır `type` `phone` .</span><span class="sxs-lookup"><span data-stu-id="d0248-132">The example uses the attribute axis property to display the value of the `type` attribute for all of the `phone` elements.</span></span>

 [!code-vb[VbXMLSamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#16)]

 <span data-ttu-id="d0248-133">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="d0248-133">This code displays the following text:</span></span>

 ```console
 home
 work
```

## <a name="see-also"></a><span data-ttu-id="d0248-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0248-134">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="d0248-135">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="d0248-135">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="d0248-136">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="d0248-136">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="d0248-137">Visual Basic'de XML Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d0248-137">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="d0248-138">Uzantı Metotları</span><span class="sxs-lookup"><span data-stu-id="d0248-138">Extension Methods</span></span>](../../programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="d0248-139">Extension Indexer Özelliği</span><span class="sxs-lookup"><span data-stu-id="d0248-139">Extension Indexer Property</span></span>](extension-indexer-property.md)
- [<span data-ttu-id="d0248-140">XML Alt Axis Özelliği</span><span class="sxs-lookup"><span data-stu-id="d0248-140">XML Child Axis Property</span></span>](xml-child-axis-property.md)
- [<span data-ttu-id="d0248-141">XML Özniteliği Axis Özelliği</span><span class="sxs-lookup"><span data-stu-id="d0248-141">XML Attribute Axis Property</span></span>](xml-attribute-axis-property.md)
