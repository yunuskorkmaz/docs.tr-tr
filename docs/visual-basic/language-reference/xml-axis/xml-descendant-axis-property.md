---
title: XML Descendant Axis Özelliği (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Basic]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
ms.openlocfilehash: bc1dff6dc3b580079087f370212b7d3acd30e4fb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938677"
---
# <a name="xml-descendant-axis-property-visual-basic"></a><span data-ttu-id="b36d7-102">XML Descendant Axis Özelliği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b36d7-102">XML Descendant Axis Property (Visual Basic)</span></span>

<span data-ttu-id="b36d7-103">Aşağıdaki alt öğeleri için erişim sağlar: bir <xref:System.Xml.Linq.XElement> nesnesi bir <xref:System.Xml.Linq.XDocument> nesnesi, koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri ya da bir koleksiyonu <xref:System.Xml.Linq.XDocument> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="b36d7-103">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>

## <a name="syntax"></a><span data-ttu-id="b36d7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b36d7-104">Syntax</span></span>

```
object...<descendant>
```

## <a name="parts"></a><span data-ttu-id="b36d7-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="b36d7-105">Parts</span></span>

<span data-ttu-id="b36d7-106">`object` Gerekli.</span><span class="sxs-lookup"><span data-stu-id="b36d7-106">`object` Required.</span></span> <span data-ttu-id="b36d7-107">Bir <xref:System.Xml.Linq.XElement> nesnesi bir <xref:System.Xml.Linq.XDocument> nesnesi, koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri ya da bir koleksiyonu <xref:System.Xml.Linq.XDocument> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="b36d7-107">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>

<span data-ttu-id="b36d7-108">`...<` Gerekli.</span><span class="sxs-lookup"><span data-stu-id="b36d7-108">`...<` Required.</span></span> <span data-ttu-id="b36d7-109">Descendant axis özelliği başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b36d7-109">Denotes the start of a descendant axis property.</span></span>

<span data-ttu-id="b36d7-110">`descendant` Gerekli.</span><span class="sxs-lookup"><span data-stu-id="b36d7-110">`descendant` Required.</span></span> <span data-ttu-id="b36d7-111">Adı biçiminin erişmeye alt düğümleri [`prefix:]name`.</span><span class="sxs-lookup"><span data-stu-id="b36d7-111">Name of the descendant nodes to access, of the form [`prefix:]name`.</span></span>

|<span data-ttu-id="b36d7-112">Bölümü</span><span class="sxs-lookup"><span data-stu-id="b36d7-112">Part</span></span>|<span data-ttu-id="b36d7-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b36d7-113">Description</span></span>|
|----------|-----------------|
|`prefix`|<span data-ttu-id="b36d7-114">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="b36d7-114">Optional.</span></span> <span data-ttu-id="b36d7-115">Alt düğümü için XML ad alanı öneki.</span><span class="sxs-lookup"><span data-stu-id="b36d7-115">XML namespace prefix for the descendant node.</span></span> <span data-ttu-id="b36d7-116">Tarafından tanımlanan genel bir XML ad alanı olmalıdır bir `Imports` deyimi.</span><span class="sxs-lookup"><span data-stu-id="b36d7-116">Must be a global XML namespace that is defined by using an `Imports` statement.</span></span>|
|`name`|<span data-ttu-id="b36d7-117">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="b36d7-117">Required.</span></span> <span data-ttu-id="b36d7-118">Alt düğümü yerel adı.</span><span class="sxs-lookup"><span data-stu-id="b36d7-118">Local name of the descendant node.</span></span> <span data-ttu-id="b36d7-119">Bkz: [bildirilmiş XML öğeleri ve özniteliklerinin adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="b36d7-119">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|

<span data-ttu-id="b36d7-120">`>` Gerekli.</span><span class="sxs-lookup"><span data-stu-id="b36d7-120">`>` Required.</span></span> <span data-ttu-id="b36d7-121">Descendant axis özelliği sonunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b36d7-121">Denotes the end of a descendant axis property.</span></span>

## <a name="return-value"></a><span data-ttu-id="b36d7-122">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b36d7-122">Return Value</span></span>

<span data-ttu-id="b36d7-123">Bir koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="b36d7-123">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>

## <a name="remarks"></a><span data-ttu-id="b36d7-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b36d7-124">Remarks</span></span>

<span data-ttu-id="b36d7-125">Bir XML descendant axis özelliği tarafından adından alt düğümleri erişmek için kullanabileceğiniz bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesnesi veya bir koleksiyonunu <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="b36d7-125">You can use an XML descendant axis property to access descendant nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="b36d7-126">XML'i `Value` özelliği döndürülen koleksiyondaki ilk alt düğümü değerine erişin.</span><span class="sxs-lookup"><span data-stu-id="b36d7-126">Use the XML `Value` property to access the value of the first descendant node in the returned collection.</span></span> <span data-ttu-id="b36d7-127">Daha fazla bilgi için [XML değeri özelliği](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="b36d7-127">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>

<span data-ttu-id="b36d7-128">Visual Basic derleyici çağrıları alt eksen özellikleri dönüştürür <xref:System.Xml.Linq.XContainer.Descendants%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b36d7-128">The Visual Basic compiler converts descendant axis properties into calls to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method.</span></span>

## <a name="xml-namespaces"></a><span data-ttu-id="b36d7-129">XML ad alanları</span><span class="sxs-lookup"><span data-stu-id="b36d7-129">XML Namespaces</span></span>

<span data-ttu-id="b36d7-130">Descendant axis özelliği adı yalnızca XML ad alanları ile küresel olarak bildirilen kullanabilirsiniz `Imports` deyimi.</span><span class="sxs-lookup"><span data-stu-id="b36d7-130">The name in a descendant axis property can use only XML namespaces declared globally with the `Imports` statement.</span></span> <span data-ttu-id="b36d7-131">XML ad alanları XML öğesi değişmez değerleri içinde yerel olarak bildirilen kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="b36d7-131">It cannot use XML namespaces declared locally within XML element literals.</span></span> <span data-ttu-id="b36d7-132">Daha fazla bilgi için [Imports deyimi (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="b36d7-132">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>

## <a name="example"></a><span data-ttu-id="b36d7-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="b36d7-133">Example</span></span>

<span data-ttu-id="b36d7-134">Aşağıdaki örnekte adlı ilk alt düğüm değerine erişin gösterilmiştir `name` ve tüm alt düğümleri adlı değerlerini `phone` gelen `contacts` nesne.</span><span class="sxs-lookup"><span data-stu-id="b36d7-134">The following example shows how to access the value of the first descendant node named `name` and the values of all descendant nodes named `phone` from the `contacts` object.</span></span>

[!code-vb[VbXMLSamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#25)]

<span data-ttu-id="b36d7-135">Bu kod, aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="b36d7-135">This code displays the following text:</span></span>

`Name: Patrick Hines`

`Home Phone = 206-555-0144`

## <a name="example"></a><span data-ttu-id="b36d7-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="b36d7-136">Example</span></span>

<span data-ttu-id="b36d7-137">Aşağıdaki örnek bildirir `ns` olarak bir XML ad alanı öneki.</span><span class="sxs-lookup"><span data-stu-id="b36d7-137">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="b36d7-138">XML değişmez değer oluşturun ve nitelikli ada sahip ilk alt düğüm değerini erişmek için ad alanı öneki kullanır `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="b36d7-138">It then uses the prefix of the namespace to create an XML literal and access the value of the first child node with the qualified name `ns:name`.</span></span>

[!code-vb[VbXMLSamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples12.vb#26)]

<span data-ttu-id="b36d7-139">Bu kod, aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="b36d7-139">This code displays the following text:</span></span>

`Name: Patrick Hines`

## <a name="see-also"></a><span data-ttu-id="b36d7-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b36d7-140">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="b36d7-141">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="b36d7-141">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="b36d7-142">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="b36d7-142">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="b36d7-143">Visual Basic'de XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="b36d7-143">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="b36d7-144">Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları</span><span class="sxs-lookup"><span data-stu-id="b36d7-144">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
