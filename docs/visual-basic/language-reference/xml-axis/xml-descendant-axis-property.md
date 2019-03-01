---
title: XML Descendant Axis Özelliği (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Baisc]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
ms.openlocfilehash: f6d8a958b5a33c236ca5273cccda0e13693b564e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973541"
---
# <a name="xml-descendant-axis-property-visual-basic"></a><span data-ttu-id="c036c-102">XML Descendant Axis Özelliği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c036c-102">XML Descendant Axis Property (Visual Basic)</span></span>
<span data-ttu-id="c036c-103">Aşağıdaki alt öğeleri için erişim sağlar: bir <xref:System.Xml.Linq.XElement> nesnesi bir <xref:System.Xml.Linq.XDocument> nesnesi, koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri ya da bir koleksiyonu <xref:System.Xml.Linq.XDocument> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="c036c-103">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c036c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c036c-104">Syntax</span></span>  
  
```  
object...<descendant>  
```  
  
## <a name="parts"></a><span data-ttu-id="c036c-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="c036c-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="c036c-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c036c-106">Required.</span></span> <span data-ttu-id="c036c-107">Bir <xref:System.Xml.Linq.XElement> nesnesi bir <xref:System.Xml.Linq.XDocument> nesnesi, koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri ya da bir koleksiyonu <xref:System.Xml.Linq.XDocument> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="c036c-107">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
 <span data-ttu-id="c036c-108">...<</span><span class="sxs-lookup"><span data-stu-id="c036c-108">...<</span></span>  
 <span data-ttu-id="c036c-109">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c036c-109">Required.</span></span> <span data-ttu-id="c036c-110">Descendant axis özelliği başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c036c-110">Denotes the start of a descendant axis property.</span></span>  
  
 `descendant`  
 <span data-ttu-id="c036c-111">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c036c-111">Required.</span></span> <span data-ttu-id="c036c-112">Adı biçiminin erişmeye alt düğümleri [`prefix:]name`.</span><span class="sxs-lookup"><span data-stu-id="c036c-112">Name of the descendant nodes to access, of the form [`prefix:]name`.</span></span>  
  
|<span data-ttu-id="c036c-113">Bölümü</span><span class="sxs-lookup"><span data-stu-id="c036c-113">Part</span></span>|<span data-ttu-id="c036c-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c036c-114">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="c036c-115">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c036c-115">Optional.</span></span> <span data-ttu-id="c036c-116">Alt düğümü için XML ad alanı öneki.</span><span class="sxs-lookup"><span data-stu-id="c036c-116">XML namespace prefix for the descendant node.</span></span> <span data-ttu-id="c036c-117">Tarafından tanımlanan genel bir XML ad alanı olmalıdır bir `Imports` deyimi.</span><span class="sxs-lookup"><span data-stu-id="c036c-117">Must be a global XML namespace that is defined by using an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="c036c-118">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c036c-118">Required.</span></span> <span data-ttu-id="c036c-119">Alt düğümü yerel adı.</span><span class="sxs-lookup"><span data-stu-id="c036c-119">Local name of the descendant node.</span></span> <span data-ttu-id="c036c-120">Bkz: [bildirilmiş XML öğeleri ve özniteliklerinin adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="c036c-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="c036c-121">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c036c-121">Required.</span></span> <span data-ttu-id="c036c-122">Descendant axis özelliği sonunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c036c-122">Denotes the end of a descendant axis property.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c036c-123">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c036c-123">Return Value</span></span>  
 <span data-ttu-id="c036c-124">Bir koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="c036c-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c036c-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c036c-125">Remarks</span></span>  
 <span data-ttu-id="c036c-126">Bir XML descendant axis özelliği tarafından adından alt düğümleri erişmek için kullanabileceğiniz bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesnesi veya bir koleksiyonunu <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="c036c-126">You can use an XML descendant axis property to access descendant nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="c036c-127">XML'i `Value` özelliği döndürülen koleksiyondaki ilk alt düğümü değerine erişin.</span><span class="sxs-lookup"><span data-stu-id="c036c-127">Use the XML `Value` property to access the value of the first descendant node in the returned collection.</span></span> <span data-ttu-id="c036c-128">Daha fazla bilgi için [XML değeri özelliği](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="c036c-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
 <span data-ttu-id="c036c-129">Visual Basic derleyici çağrıları alt eksen özellikleri dönüştürür <xref:System.Xml.Linq.XContainer.Descendants%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c036c-129">The Visual Basic compiler converts descendant axis properties into calls to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="c036c-130">XML ad alanları</span><span class="sxs-lookup"><span data-stu-id="c036c-130">XML Namespaces</span></span>  
 <span data-ttu-id="c036c-131">Descendant axis özelliği adı yalnızca XML ad alanları ile küresel olarak bildirilen kullanabilirsiniz `Imports` deyimi.</span><span class="sxs-lookup"><span data-stu-id="c036c-131">The name in a descendant axis property can use only XML namespaces declared globally with the `Imports` statement.</span></span> <span data-ttu-id="c036c-132">XML ad alanları XML öğesi değişmez değerleri içinde yerel olarak bildirilen kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="c036c-132">It cannot use XML namespaces declared locally within XML element literals.</span></span> <span data-ttu-id="c036c-133">Daha fazla bilgi için [Imports deyimi (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="c036c-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c036c-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="c036c-134">Example</span></span>  
 <span data-ttu-id="c036c-135">Aşağıdaki örnekte adlı ilk alt düğüm değerine erişin gösterilmiştir `name` ve tüm alt düğümleri adlı değerlerini `phone` gelen `contacts` nesne.</span><span class="sxs-lookup"><span data-stu-id="c036c-135">The following example shows how to access the value of the first descendant node named `name` and the values of all descendant nodes named `phone` from the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#25)]  
  
 <span data-ttu-id="c036c-136">Bu kod, aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="c036c-136">This code displays the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="c036c-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="c036c-137">Example</span></span>  
 <span data-ttu-id="c036c-138">Aşağıdaki örnek bildirir `ns` olarak bir XML ad alanı öneki.</span><span class="sxs-lookup"><span data-stu-id="c036c-138">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="c036c-139">XML değişmez değer oluşturun ve nitelikli ada sahip ilk alt düğüm değerini erişmek için ad alanı öneki kullanır `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="c036c-139">It then uses the prefix of the namespace to create an XML literal and access the value of the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples12.vb#26)]  
  
 <span data-ttu-id="c036c-140">Bu kod, aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="c036c-140">This code displays the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="c036c-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c036c-141">See also</span></span>
- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="c036c-142">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="c036c-142">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="c036c-143">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="c036c-143">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="c036c-144">Visual Basic'de XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="c036c-144">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="c036c-145">Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları</span><span class="sxs-lookup"><span data-stu-id="c036c-145">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
