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
ms.openlocfilehash: 2b0719320db5843d5d010bfbd70e551646e3ded9
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43533397"
---
# <a name="xml-value-property-visual-basic"></a><span data-ttu-id="ebaad-102">XML Değeri Özelliği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ebaad-102">XML Value Property (Visual Basic)</span></span>
<span data-ttu-id="ebaad-103">Koleksiyonunu ilk öğenin değerini erişim sağlayan <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="ebaad-103">Provides access to the value of the first element of a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebaad-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ebaad-104">Syntax</span></span>  
  
```  
object.Value  
```  
  
## <a name="parts"></a><span data-ttu-id="ebaad-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="ebaad-105">Parts</span></span>  
  
|<span data-ttu-id="ebaad-106">Terim</span><span class="sxs-lookup"><span data-stu-id="ebaad-106">Term</span></span>|<span data-ttu-id="ebaad-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="ebaad-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="ebaad-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="ebaad-108">Required.</span></span> <span data-ttu-id="ebaad-109">Koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="ebaad-109">Collection of <xref:System.Xml.Linq.XElement> objects.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="ebaad-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ebaad-110">Return Value</span></span>  
 <span data-ttu-id="ebaad-111">A `String` koleksiyonun ilk öğenin değerini içeren veya `Nothing` koleksiyonu boş ise.</span><span class="sxs-lookup"><span data-stu-id="ebaad-111">A `String` that contains the value of the first element of the collection, or `Nothing` if the collection is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ebaad-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ebaad-112">Remarks</span></span>  
 <span data-ttu-id="ebaad-113"><xref:System.Xml.Linq.XElement.Value%2A> Özelliği bir koleksiyondaki ilk öğenin değere erişmek kolaylaştırır <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="ebaad-113">The <xref:System.Xml.Linq.XElement.Value%2A> property makes it easy to access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="ebaad-114">Bu özellik, ilk koleksiyon en az bir nesne içerip içermediğini denetler.</span><span class="sxs-lookup"><span data-stu-id="ebaad-114">This property first checks whether the collection contains at least one object.</span></span> <span data-ttu-id="ebaad-115">Bu özellik koleksiyonu boş ise döndürür `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="ebaad-115">If the collection is empty, this property returns `Nothing`.</span></span> <span data-ttu-id="ebaad-116">Aksi takdirde, bu özellik değerini döndürür <xref:System.Xml.Linq.XElement.Value%2A> koleksiyondaki ilk öğenin özellik.</span><span class="sxs-lookup"><span data-stu-id="ebaad-116">Otherwise, this property returns the value of the <xref:System.Xml.Linq.XElement.Value%2A> property of the first element in the collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ebaad-117">Kullanarak bir XML özniteliği değeri eriştiğinizde '\@' tanımlayıcısı, öznitelik değeri olarak döndürülür bir `String` ve açıkça belirtmeniz gerekmez <xref:System.Xml.Linq.XAttribute.Value%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="ebaad-117">When you access the value of an XML attribute using the '\@' identifier, the attribute value is returned as a `String` and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="ebaad-118">Bir koleksiyondaki diğer öğelere erişmek için XML uzantı dizin oluşturucu özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ebaad-118">To access other elements in a collection, you can use the XML extension indexer property.</span></span> <span data-ttu-id="ebaad-119">Daha fazla bilgi için [Extension Indexer özelliği](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).</span><span class="sxs-lookup"><span data-stu-id="ebaad-119">For more information, see [Extension Indexer Property](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).</span></span>  
  
## <a name="inheritance"></a><span data-ttu-id="ebaad-120">Devralma</span><span class="sxs-lookup"><span data-stu-id="ebaad-120">Inheritance</span></span>  
 <span data-ttu-id="ebaad-121">Çoğu kullanıcı uygulamak zorunda <xref:System.Collections.Generic.IEnumerable%601>ve bu nedenle bu bölüm yoksayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ebaad-121">Most users will not have to implement <xref:System.Collections.Generic.IEnumerable%601>, and can therefore ignore this section.</span></span>  
  
 <span data-ttu-id="ebaad-122"><xref:System.Xml.Linq.XElement.Value%2A> Özelliği uygulayan türler için bir uzantı özelliği `IEnumerable(Of XElement)`.</span><span class="sxs-lookup"><span data-stu-id="ebaad-122">The <xref:System.Xml.Linq.XElement.Value%2A> property is an extension property for types that implement `IEnumerable(Of XElement)`.</span></span> <span data-ttu-id="ebaad-123">Uzantı yöntemleri bağlama gibi bağlamadır bu uzantı özelliğinin: Bu özellik bir tür arabirimlerinden birini uygular ve "Value" adına sahip bir özelliğini tanımlar, uzantı özelliği önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ebaad-123">The binding of this extension property is like the binding of extension methods: if a type implements one of the interfaces and defines a property that has the name "Value", that property has precedence over the extension property.</span></span> <span data-ttu-id="ebaad-124">Diğer bir deyişle, bu <xref:System.Xml.Linq.XElement.Value%2A> özelliği, yeni bir özelliği uygulayan bir sınıf tanımlayarak kılınabilir `IEnumerable(Of XElement)`.</span><span class="sxs-lookup"><span data-stu-id="ebaad-124">In other words, this <xref:System.Xml.Linq.XElement.Value%2A> property can be overridden by defining a new property in a class that implements `IEnumerable(Of XElement)`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ebaad-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="ebaad-125">Example</span></span>  
 <span data-ttu-id="ebaad-126">Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Xml.Linq.XElement.Value%2A> koleksiyonunu ilk düğüm erişmek için özelliği <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="ebaad-126">The following example shows how to use the <xref:System.Xml.Linq.XElement.Value%2A> property to access the first node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="ebaad-127">Örnek child axis özelliği adlı tüm alt düğümleri koleksiyonu almak için kullanır. `phone` bulunan `contact` nesne.</span><span class="sxs-lookup"><span data-stu-id="ebaad-127">The example uses the child axis property to get the collection of all child nodes named `phone` that are in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_1.vb)]  
  
 <span data-ttu-id="ebaad-128">Bu kod, aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="ebaad-128">This code displays the following text:</span></span>  
  
 `Phone number: 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="ebaad-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="ebaad-129">Example</span></span>  
 <span data-ttu-id="ebaad-130">Aşağıdaki örnek koleksiyonundan bir XML özniteliği değeri almak nasıl gösterir <xref:System.Xml.Linq.XAttribute> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="ebaad-130">The following example shows how to get the value of an XML attribute from a collection of <xref:System.Xml.Linq.XAttribute> objects.</span></span> <span data-ttu-id="ebaad-131">Örnek attribute axis özelliği değerini görüntülemek için kullanır. `type` özniteliği için tüm `phone` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="ebaad-131">The example uses the attribute axis property to display the value of the `type` attribute for all of the `phone` elements.</span></span>  
  
 [!code-vb[VbXMLSamples#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_2.vb)]  
  
 <span data-ttu-id="ebaad-132">Bu kod, aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="ebaad-132">This code displays the following text:</span></span>  
  
 `home`  
  
 `work`  
  
## <a name="see-also"></a><span data-ttu-id="ebaad-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ebaad-133">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [<span data-ttu-id="ebaad-134">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="ebaad-134">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)  
 [<span data-ttu-id="ebaad-135">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="ebaad-135">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="ebaad-136">Visual Basic'de XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="ebaad-136">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="ebaad-137">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="ebaad-137">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
 [<span data-ttu-id="ebaad-138">Extension Indexer Özelliği</span><span class="sxs-lookup"><span data-stu-id="ebaad-138">Extension Indexer Property</span></span>](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)  
 [<span data-ttu-id="ebaad-139">XML Alt Axis Özelliği</span><span class="sxs-lookup"><span data-stu-id="ebaad-139">XML Child Axis Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)  
 [<span data-ttu-id="ebaad-140">XML Özniteliği Axis Özelliği</span><span class="sxs-lookup"><span data-stu-id="ebaad-140">XML Attribute Axis Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
