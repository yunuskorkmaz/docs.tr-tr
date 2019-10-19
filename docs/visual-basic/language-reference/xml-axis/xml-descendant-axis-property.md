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
ms.openlocfilehash: e2c3e01808d3eeb18f6753a5fc79b8627e7f323b
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582225"
---
# <a name="xml-descendant-axis-property-visual-basic"></a><span data-ttu-id="42c46-102">XML Descendant Axis Özelliği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42c46-102">XML Descendant Axis Property (Visual Basic)</span></span>

<span data-ttu-id="42c46-103">Aşağıdakilerin alt öğeleri için erişim sağlar: <xref:System.Xml.Linq.XElement> nesnesi, <xref:System.Xml.Linq.XDocument> nesnesi, <xref:System.Xml.Linq.XElement> nesneleri koleksiyonu veya <xref:System.Xml.Linq.XDocument> nesneleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="42c46-103">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>

## <a name="syntax"></a><span data-ttu-id="42c46-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="42c46-104">Syntax</span></span>

```vb
object...<descendant>
```

## <a name="parts"></a><span data-ttu-id="42c46-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="42c46-105">Parts</span></span>

<span data-ttu-id="42c46-106">`object` gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="42c46-106">`object` Required.</span></span> <span data-ttu-id="42c46-107">@No__t_0 nesnesi, <xref:System.Xml.Linq.XDocument> nesnesi, <xref:System.Xml.Linq.XElement> nesneleri koleksiyonu veya <xref:System.Xml.Linq.XDocument> nesneleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="42c46-107">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>

<span data-ttu-id="42c46-108">`...<` gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="42c46-108">`...<` Required.</span></span> <span data-ttu-id="42c46-109">Alt eksen özelliğinin başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="42c46-109">Denotes the start of a descendant axis property.</span></span>

<span data-ttu-id="42c46-110">`descendant` gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="42c46-110">`descendant` Required.</span></span> <span data-ttu-id="42c46-111">[@No__t_0 biçiminde erişmek için alt düğümlerin adı.</span><span class="sxs-lookup"><span data-stu-id="42c46-111">Name of the descendant nodes to access, of the form [`prefix:]name`.</span></span>

|<span data-ttu-id="42c46-112">Bölümüyle</span><span class="sxs-lookup"><span data-stu-id="42c46-112">Part</span></span>|<span data-ttu-id="42c46-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="42c46-113">Description</span></span>|
|----------|-----------------|
|`prefix`|<span data-ttu-id="42c46-114">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="42c46-114">Optional.</span></span> <span data-ttu-id="42c46-115">Alt düğüm için XML ad alanı öneki.</span><span class="sxs-lookup"><span data-stu-id="42c46-115">XML namespace prefix for the descendant node.</span></span> <span data-ttu-id="42c46-116">Bir `Imports` ekstresi kullanılarak tanımlanmış bir genel XML ad alanı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="42c46-116">Must be a global XML namespace that is defined by using an `Imports` statement.</span></span>|
|`name`|<span data-ttu-id="42c46-117">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="42c46-117">Required.</span></span> <span data-ttu-id="42c46-118">Alt düğümün yerel adı.</span><span class="sxs-lookup"><span data-stu-id="42c46-118">Local name of the descendant node.</span></span> <span data-ttu-id="42c46-119">[BELIRTILEN XML öğelerinin ve özniteliklerin adlarına](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="42c46-119">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|

<span data-ttu-id="42c46-120">`>` gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="42c46-120">`>` Required.</span></span> <span data-ttu-id="42c46-121">Alt eksen özelliğinin sonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="42c46-121">Denotes the end of a descendant axis property.</span></span>

## <a name="return-value"></a><span data-ttu-id="42c46-122">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="42c46-122">Return Value</span></span>

<span data-ttu-id="42c46-123">@No__t_0 nesneleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="42c46-123">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>

## <a name="remarks"></a><span data-ttu-id="42c46-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="42c46-124">Remarks</span></span>

<span data-ttu-id="42c46-125">Alt düğümlere bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesnesinden veya <xref:System.Xml.Linq.XElement> ya da <xref:System.Xml.Linq.XDocument> nesnelerinden oluşan bir koleksiyondan ad ile erişmek için bir XML alt eksen özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42c46-125">You can use an XML descendant axis property to access descendant nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="42c46-126">Döndürülen koleksiyondaki ilk alt düğümün değerine erişmek için XML `Value` özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="42c46-126">Use the XML `Value` property to access the value of the first descendant node in the returned collection.</span></span> <span data-ttu-id="42c46-127">Daha fazla bilgi için bkz. [XML Value özelliği](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="42c46-127">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>

<span data-ttu-id="42c46-128">Visual Basic derleyici, alt eksen özelliklerini <xref:System.Xml.Linq.XContainer.Descendants%2A> yöntemine yapılan çağrılara dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="42c46-128">The Visual Basic compiler converts descendant axis properties into calls to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method.</span></span>

## <a name="xml-namespaces"></a><span data-ttu-id="42c46-129">XML ad alanları</span><span class="sxs-lookup"><span data-stu-id="42c46-129">XML Namespaces</span></span>

<span data-ttu-id="42c46-130">Alt eksen özelliğindeki ad, `Imports` ifadesiyle Global olarak belirtilen yalnızca XML ad alanlarını kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="42c46-130">The name in a descendant axis property can use only XML namespaces declared globally with the `Imports` statement.</span></span> <span data-ttu-id="42c46-131">XML öğesi değişmez değerleri içinde yerel olarak belirtilen XML ad alanlarını kullanamaz.</span><span class="sxs-lookup"><span data-stu-id="42c46-131">It cannot use XML namespaces declared locally within XML element literals.</span></span> <span data-ttu-id="42c46-132">Daha fazla bilgi için bkz. [Imports bildirisi (XML ad alanı)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="42c46-132">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>

## <a name="example"></a><span data-ttu-id="42c46-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="42c46-133">Example</span></span>

<span data-ttu-id="42c46-134">Aşağıdaki örnek, `name` adlı ilk alt düğümün değerine ve `contacts` nesnesinden `phone` adlı tüm alt düğümlerin değerlerine nasıl erişebileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="42c46-134">The following example shows how to access the value of the first descendant node named `name` and the values of all descendant nodes named `phone` from the `contacts` object.</span></span>

[!code-vb[VbXMLSamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#25)]

<span data-ttu-id="42c46-135">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="42c46-135">This code displays the following text:</span></span>

`Name: Patrick Hines`

`Home Phone = 206-555-0144`

## <a name="example"></a><span data-ttu-id="42c46-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="42c46-136">Example</span></span>

<span data-ttu-id="42c46-137">Aşağıdaki örnek, `ns` bir XML ad alanı öneki olarak bildirir.</span><span class="sxs-lookup"><span data-stu-id="42c46-137">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="42c46-138">Daha sonra bir XML sabit değeri oluşturmak için ad alanının önekini kullanır ve `ns:name` nitelenmiş ada sahip ilk alt düğümün değerine erişir.</span><span class="sxs-lookup"><span data-stu-id="42c46-138">It then uses the prefix of the namespace to create an XML literal and access the value of the first child node with the qualified name `ns:name`.</span></span>

[!code-vb[VbXMLSamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples12.vb#26)]

<span data-ttu-id="42c46-139">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="42c46-139">This code displays the following text:</span></span>

`Name: Patrick Hines`

## <a name="see-also"></a><span data-ttu-id="42c46-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42c46-140">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="42c46-141">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="42c46-141">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="42c46-142">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="42c46-142">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="42c46-143">Visual Basic XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="42c46-143">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="42c46-144">Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları</span><span class="sxs-lookup"><span data-stu-id="42c46-144">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
