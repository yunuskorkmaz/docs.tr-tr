---
title: XML Alt Axis Özelliği (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyChildAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 89a59d00-985e-4f5c-b59f-29b47bad11cb
ms.openlocfilehash: 0b504a9e368e5179d5f91faf7256445d7da47b1d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43484900"
---
# <a name="xml-child-axis-property-visual-basic"></a><span data-ttu-id="ba636-102">XML Alt Axis Özelliği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba636-102">XML Child Axis Property (Visual Basic)</span></span>
<span data-ttu-id="ba636-103">Aşağıdakilerden birinin alt öğelere erişim sağlar: bir <xref:System.Xml.Linq.XElement> nesnesi bir <xref:System.Xml.Linq.XDocument> nesnesi, koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri ya da bir koleksiyonu <xref:System.Xml.Linq.XDocument> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="ba636-103">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba636-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba636-104">Syntax</span></span>  
  
```  
object.<child>  
```  
  
## <a name="parts"></a><span data-ttu-id="ba636-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="ba636-105">Parts</span></span>  
  
|<span data-ttu-id="ba636-106">Terim</span><span class="sxs-lookup"><span data-stu-id="ba636-106">Term</span></span>|<span data-ttu-id="ba636-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="ba636-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="ba636-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="ba636-108">Required.</span></span> <span data-ttu-id="ba636-109">Bir <xref:System.Xml.Linq.XElement> nesnesi bir <xref:System.Xml.Linq.XDocument> nesnesi, koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri ya da bir koleksiyonu <xref:System.Xml.Linq.XDocument> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="ba636-109">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>|  
|<span data-ttu-id="ba636-110">.<</span><span class="sxs-lookup"><span data-stu-id="ba636-110">.<</span></span>|<span data-ttu-id="ba636-111">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="ba636-111">Required.</span></span> <span data-ttu-id="ba636-112">Child axis özelliği başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ba636-112">Denotes the start of a child axis property.</span></span>|  
|`child`|<span data-ttu-id="ba636-113">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="ba636-113">Required.</span></span> <span data-ttu-id="ba636-114">Adı biçiminin erişmeye alt düğümleri [`prefix``:`]`name`.</span><span class="sxs-lookup"><span data-stu-id="ba636-114">Name of the child nodes to access, of the form [`prefix``:`]`name`.</span></span><br /><br /> <span data-ttu-id="ba636-115">-   `Prefix` -İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ba636-115">-   `Prefix` - Optional.</span></span> <span data-ttu-id="ba636-116">Alt düğümü için XML ad alanı öneki.</span><span class="sxs-lookup"><span data-stu-id="ba636-116">XML namespace prefix for the child node.</span></span> <span data-ttu-id="ba636-117">Genel XML ad alanı ile tanımlanmalıdır bir `Imports` deyimi.</span><span class="sxs-lookup"><span data-stu-id="ba636-117">Must be a global XML namespace defined with an `Imports` statement.</span></span><br /><span data-ttu-id="ba636-118">-   `Name` -Gerekli.</span><span class="sxs-lookup"><span data-stu-id="ba636-118">-   `Name` - Required.</span></span> <span data-ttu-id="ba636-119">Yerel alt düğüm adı.</span><span class="sxs-lookup"><span data-stu-id="ba636-119">Local child node name.</span></span> <span data-ttu-id="ba636-120">Bkz: [bildirilmiş XML öğeleri ve özniteliklerinin adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="ba636-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
|>|<span data-ttu-id="ba636-121">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="ba636-121">Required.</span></span> <span data-ttu-id="ba636-122">Child axis özelliği sonunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ba636-122">Denotes the end of a child axis property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="ba636-123">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ba636-123">Return Value</span></span>  
 <span data-ttu-id="ba636-124">Bir koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="ba636-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba636-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ba636-125">Remarks</span></span>  
 <span data-ttu-id="ba636-126">Adından tarafından erişim alt düğümler için bir XML alt axis özelliği kullanabilirsiniz bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesnesi veya bir koleksiyonunu <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="ba636-126">You can use an XML child axis property to access child nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="ba636-127">XML'i `Value` özelliği döndürülen koleksiyondaki ilk alt düğüm değerine erişin.</span><span class="sxs-lookup"><span data-stu-id="ba636-127">Use the XML `Value` property to access the value of the first child node in the returned collection.</span></span> <span data-ttu-id="ba636-128">Daha fazla bilgi için [XML değeri özelliği](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="ba636-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
 <span data-ttu-id="ba636-129">Visual Basic derleyici çağrıları alt eksen özellikleri dönüştürür <xref:System.Xml.Linq.XContainer.Elements%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ba636-129">The Visual Basic compiler converts child axis properties to calls to the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="ba636-130">XML ad alanları</span><span class="sxs-lookup"><span data-stu-id="ba636-130">XML Namespaces</span></span>  
 <span data-ttu-id="ba636-131">Child axis özelliği adı ile küresel olarak bildirilen XML ad alanı öneklerini kullanabilirsiniz `Imports` deyimi.</span><span class="sxs-lookup"><span data-stu-id="ba636-131">The name in a child axis property can use only XML namespace prefixes declared globally with the `Imports` statement.</span></span> <span data-ttu-id="ba636-132">XML ad alanı öneklerini XML öğesi değişmez değerleri içinde yerel olarak bildirilen kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="ba636-132">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="ba636-133">Daha fazla bilgi için [Imports deyimi (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="ba636-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba636-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="ba636-134">Example</span></span>  
 <span data-ttu-id="ba636-135">Aşağıdaki örnekte adlı alt düğümleri nasıl gösterir `phone` gelen `contact` nesne.</span><span class="sxs-lookup"><span data-stu-id="ba636-135">The following example shows how to access the child nodes named `phone` from the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#17](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_1.vb)]  
  
 <span data-ttu-id="ba636-136">Bu kod, aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="ba636-136">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="ba636-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="ba636-137">Example</span></span>  
 <span data-ttu-id="ba636-138">Aşağıdaki örnekte adlı alt düğümleri nasıl gösterir `phone` tarafından döndürülen koleksiyondan `contact` child axis özelliği, `contacts` nesne.</span><span class="sxs-lookup"><span data-stu-id="ba636-138">The following example shows how to access the child nodes named `phone` from the collection returned by the `contact` child axis property of the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#18](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_2.vb)]  
  
 <span data-ttu-id="ba636-139">Bu kod, aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="ba636-139">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="ba636-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="ba636-140">Example</span></span>  
 <span data-ttu-id="ba636-141">Aşağıdaki örnek bildirir `ns` olarak bir XML ad alanı öneki.</span><span class="sxs-lookup"><span data-stu-id="ba636-141">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="ba636-142">XML değişmez değer oluşturun ve ilk alt düğüm tam adı ile erişmek için bir ad alanı öneki kullanır `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="ba636-142">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#19](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_3.vb)]  
  
 <span data-ttu-id="ba636-143">Bu kod, aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="ba636-143">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="ba636-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ba636-144">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 [<span data-ttu-id="ba636-145">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="ba636-145">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)  
 [<span data-ttu-id="ba636-146">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="ba636-146">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="ba636-147">Visual Basic'de XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="ba636-147">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="ba636-148">Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları</span><span class="sxs-lookup"><span data-stu-id="ba636-148">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
