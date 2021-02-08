---
description: 'Daha fazla bilgi edinin: XML descendant Axis Özelliği (Visual Basic)'
title: XML Descendant Axis Özelliği
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
ms.openlocfilehash: c356d4d6f9a84755e9df171b26060fc6bfc4ead6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768785"
---
# <a name="xml-descendant-axis-property-visual-basic"></a><span data-ttu-id="10693-103">XML Descendant Axis Özelliği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10693-103">XML Descendant Axis Property (Visual Basic)</span></span>

<span data-ttu-id="10693-104">Aşağıdakilerin alt öğeleri için erişim sağlar: <xref:System.Xml.Linq.XElement> nesne, <xref:System.Xml.Linq.XDocument> nesne, nesne koleksiyonu <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesne koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="10693-104">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>

## <a name="syntax"></a><span data-ttu-id="10693-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="10693-105">Syntax</span></span>

```vb
object...<descendant>
```

## <a name="parts"></a><span data-ttu-id="10693-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="10693-106">Parts</span></span>

<span data-ttu-id="10693-107">`object` Gerekli.</span><span class="sxs-lookup"><span data-stu-id="10693-107">`object` Required.</span></span> <span data-ttu-id="10693-108"><xref:System.Xml.Linq.XElement>Nesne, <xref:System.Xml.Linq.XDocument> nesne, <xref:System.Xml.Linq.XElement> nesneler koleksiyonu veya nesne koleksiyonu <xref:System.Xml.Linq.XDocument> .</span><span class="sxs-lookup"><span data-stu-id="10693-108">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>

<span data-ttu-id="10693-109">`...<` Gerekli.</span><span class="sxs-lookup"><span data-stu-id="10693-109">`...<` Required.</span></span> <span data-ttu-id="10693-110">Alt eksen özelliğinin başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="10693-110">Denotes the start of a descendant axis property.</span></span>

<span data-ttu-id="10693-111">`descendant` Gerekli.</span><span class="sxs-lookup"><span data-stu-id="10693-111">`descendant` Required.</span></span> <span data-ttu-id="10693-112">Erişmek için alt düğümlerin adı, form [ `prefix:]name` .</span><span class="sxs-lookup"><span data-stu-id="10693-112">Name of the descendant nodes to access, of the form [`prefix:]name`.</span></span>

|<span data-ttu-id="10693-113">Bölüm</span><span class="sxs-lookup"><span data-stu-id="10693-113">Part</span></span>|<span data-ttu-id="10693-114">Description</span><span class="sxs-lookup"><span data-stu-id="10693-114">Description</span></span>|
|----------|-----------------|
|`prefix`|<span data-ttu-id="10693-115">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="10693-115">Optional.</span></span> <span data-ttu-id="10693-116">Alt düğüm için XML ad alanı öneki.</span><span class="sxs-lookup"><span data-stu-id="10693-116">XML namespace prefix for the descendant node.</span></span> <span data-ttu-id="10693-117">Bir ifade kullanılarak tanımlanmış bir genel XML ad alanı olmalıdır `Imports` .</span><span class="sxs-lookup"><span data-stu-id="10693-117">Must be a global XML namespace that is defined by using an `Imports` statement.</span></span>|
|`name`|<span data-ttu-id="10693-118">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="10693-118">Required.</span></span> <span data-ttu-id="10693-119">Alt düğümün yerel adı.</span><span class="sxs-lookup"><span data-stu-id="10693-119">Local name of the descendant node.</span></span> <span data-ttu-id="10693-120">[BELIRTILEN XML öğelerinin ve özniteliklerin adlarına](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="10693-120">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|

<span data-ttu-id="10693-121">`>` Gerekli.</span><span class="sxs-lookup"><span data-stu-id="10693-121">`>` Required.</span></span> <span data-ttu-id="10693-122">Alt eksen özelliğinin sonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="10693-122">Denotes the end of a descendant axis property.</span></span>

## <a name="return-value"></a><span data-ttu-id="10693-123">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="10693-123">Return Value</span></span>

<span data-ttu-id="10693-124"><xref:System.Xml.Linq.XElement> nesneleri topluluğu.</span><span class="sxs-lookup"><span data-stu-id="10693-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>

## <a name="remarks"></a><span data-ttu-id="10693-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="10693-125">Remarks</span></span>

<span data-ttu-id="10693-126">Alt düğümlere bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesnesinden veya bir <xref:System.Xml.Linq.XElement> veya nesneleri koleksiyonundan bir ad ile erışmek için bir xml alt eksen özelliği kullanabilirsiniz <xref:System.Xml.Linq.XDocument> .</span><span class="sxs-lookup"><span data-stu-id="10693-126">You can use an XML descendant axis property to access descendant nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="10693-127">`Value`Döndürülen koleksiyondaki ilk alt düğümün değerine erişmek IÇIN XML özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="10693-127">Use the XML `Value` property to access the value of the first descendant node in the returned collection.</span></span> <span data-ttu-id="10693-128">Daha fazla bilgi için bkz. [XML Value özelliği](xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="10693-128">For more information, see [XML Value Property](xml-value-property.md).</span></span>

<span data-ttu-id="10693-129">Visual Basic derleyici, alt eksen özelliklerini yöntemine yapılan çağrılara dönüştürür <xref:System.Xml.Linq.XContainer.Descendants%2A> .</span><span class="sxs-lookup"><span data-stu-id="10693-129">The Visual Basic compiler converts descendant axis properties into calls to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method.</span></span>

## <a name="xml-namespaces"></a><span data-ttu-id="10693-130">XML ad alanları</span><span class="sxs-lookup"><span data-stu-id="10693-130">XML Namespaces</span></span>

<span data-ttu-id="10693-131">Alt eksen özelliğindeki ad, ifadesiyle Global olarak belirtilen yalnızca XML ad alanlarını kullanabilir `Imports` .</span><span class="sxs-lookup"><span data-stu-id="10693-131">The name in a descendant axis property can use only XML namespaces declared globally with the `Imports` statement.</span></span> <span data-ttu-id="10693-132">XML öğesi değişmez değerleri içinde yerel olarak belirtilen XML ad alanlarını kullanamaz.</span><span class="sxs-lookup"><span data-stu-id="10693-132">It cannot use XML namespaces declared locally within XML element literals.</span></span> <span data-ttu-id="10693-133">Daha fazla bilgi için bkz. [Imports bildirisi (XML ad alanı)](../statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="10693-133">For more information, see [Imports Statement (XML Namespace)](../statements/imports-statement-xml-namespace.md).</span></span>

## <a name="example"></a><span data-ttu-id="10693-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="10693-134">Example</span></span>

<span data-ttu-id="10693-135">Aşağıdaki örnek, adlı ilk alt düğümün değerine `name` ve nesne adındaki tüm alt düğümlerin değerlerine nasıl erişegösterdiğini gösterir `phone` `contacts` .</span><span class="sxs-lookup"><span data-stu-id="10693-135">The following example shows how to access the value of the first descendant node named `name` and the values of all descendant nodes named `phone` from the `contacts` object.</span></span>

[!code-vb[VbXMLSamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#25)]

<span data-ttu-id="10693-136">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="10693-136">This code displays the following text:</span></span>

`Name: Patrick Hines`

`Home Phone = 206-555-0144`

## <a name="example"></a><span data-ttu-id="10693-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="10693-137">Example</span></span>

<span data-ttu-id="10693-138">Aşağıdaki örnek `ns` BIR XML ad alanı ön eki olarak bildirir.</span><span class="sxs-lookup"><span data-stu-id="10693-138">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="10693-139">Daha sonra bir XML sabit değeri oluşturmak için ad alanının önekini kullanır ve ilk alt düğümün değerine tam adı ile erişin `ns:name` .</span><span class="sxs-lookup"><span data-stu-id="10693-139">It then uses the prefix of the namespace to create an XML literal and access the value of the first child node with the qualified name `ns:name`.</span></span>

[!code-vb[VbXMLSamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples12.vb#26)]

<span data-ttu-id="10693-140">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="10693-140">This code displays the following text:</span></span>

`Name: Patrick Hines`

## <a name="see-also"></a><span data-ttu-id="10693-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10693-141">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="10693-142">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="10693-142">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="10693-143">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="10693-143">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="10693-144">Visual Basic'de XML Oluşturma</span><span class="sxs-lookup"><span data-stu-id="10693-144">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="10693-145">Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları</span><span class="sxs-lookup"><span data-stu-id="10693-145">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
