---
title: XML Alt Axis Özelliği
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
ms.openlocfilehash: 968154908bc6cb62bb221d42a1f71b329aa7096f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349464"
---
# <a name="xml-child-axis-property-visual-basic"></a><span data-ttu-id="5b0dc-102">XML Alt Axis Özelliği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b0dc-102">XML Child Axis Property (Visual Basic)</span></span>
<span data-ttu-id="5b0dc-103">Aşağıdakilerden birinin alt öğelerine erişim sağlar: <xref:System.Xml.Linq.XElement> nesnesi, <xref:System.Xml.Linq.XDocument> nesnesi, <xref:System.Xml.Linq.XElement> nesneleri koleksiyonu veya <xref:System.Xml.Linq.XDocument> nesneleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="5b0dc-103">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b0dc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5b0dc-104">Syntax</span></span>  
  
```vb  
object.<child>  
```  
  
## <a name="parts"></a><span data-ttu-id="5b0dc-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="5b0dc-105">Parts</span></span>  
  
|<span data-ttu-id="5b0dc-106">Terim</span><span class="sxs-lookup"><span data-stu-id="5b0dc-106">Term</span></span>|<span data-ttu-id="5b0dc-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="5b0dc-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="5b0dc-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="5b0dc-108">Required.</span></span> <span data-ttu-id="5b0dc-109"><xref:System.Xml.Linq.XElement> nesnesi, <xref:System.Xml.Linq.XDocument> nesnesi, <xref:System.Xml.Linq.XElement> nesneleri koleksiyonu veya <xref:System.Xml.Linq.XDocument> nesneleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="5b0dc-109">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>|  
|<span data-ttu-id="5b0dc-110">.<</span><span class="sxs-lookup"><span data-stu-id="5b0dc-110">.<</span></span>|<span data-ttu-id="5b0dc-111">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="5b0dc-111">Required.</span></span> <span data-ttu-id="5b0dc-112">Bir alt eksen özelliğinin başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b0dc-112">Denotes the start of a child axis property.</span></span>|  
|`child`|<span data-ttu-id="5b0dc-113">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="5b0dc-113">Required.</span></span> <span data-ttu-id="5b0dc-114">[`prefix:]name`biçiminde erişmek için alt düğümlerin adı.</span><span class="sxs-lookup"><span data-stu-id="5b0dc-114">Name of the child nodes to access, of the form [`prefix:]name`.</span></span><br /><br /> <span data-ttu-id="5b0dc-115">-   `Prefix`-Isteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="5b0dc-115">-   `Prefix` - Optional.</span></span> <span data-ttu-id="5b0dc-116">Alt düğüm için XML ad alanı ön eki.</span><span class="sxs-lookup"><span data-stu-id="5b0dc-116">XML namespace prefix for the child node.</span></span> <span data-ttu-id="5b0dc-117">Bir `Imports` ifadesiyle tanımlanmış bir genel XML ad alanı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5b0dc-117">Must be a global XML namespace defined with an `Imports` statement.</span></span><br /><span data-ttu-id="5b0dc-118">-   `Name`-gerekli.</span><span class="sxs-lookup"><span data-stu-id="5b0dc-118">-   `Name` - Required.</span></span> <span data-ttu-id="5b0dc-119">Yerel alt düğüm adı.</span><span class="sxs-lookup"><span data-stu-id="5b0dc-119">Local child node name.</span></span> <span data-ttu-id="5b0dc-120">[BELIRTILEN XML öğelerinin ve özniteliklerin adlarına](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="5b0dc-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
|>|<span data-ttu-id="5b0dc-121">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="5b0dc-121">Required.</span></span> <span data-ttu-id="5b0dc-122">Alt eksen özelliğinin sonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="5b0dc-122">Denotes the end of a child axis property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="5b0dc-123">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5b0dc-123">Return Value</span></span>  
 <span data-ttu-id="5b0dc-124"><xref:System.Xml.Linq.XElement> nesneleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="5b0dc-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b0dc-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5b0dc-125">Remarks</span></span>  
 <span data-ttu-id="5b0dc-126">Alt düğümlere bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesnesinden veya <xref:System.Xml.Linq.XElement> ya da <xref:System.Xml.Linq.XDocument> nesnelerinden oluşan bir koleksiyondan ad ile erişmek için bir XML alt eksen özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b0dc-126">You can use an XML child axis property to access child nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="5b0dc-127">Döndürülen koleksiyondaki ilk alt düğümün değerine erişmek için XML `Value` özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="5b0dc-127">Use the XML `Value` property to access the value of the first child node in the returned collection.</span></span> <span data-ttu-id="5b0dc-128">Daha fazla bilgi için bkz. [XML Value özelliği](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="5b0dc-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
 <span data-ttu-id="5b0dc-129">Visual Basic Derleyicisi alt eksen özelliklerini <xref:System.Xml.Linq.XContainer.Elements%2A> yöntemine yapılan çağrılara dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="5b0dc-129">The Visual Basic compiler converts child axis properties to calls to the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="5b0dc-130">XML ad alanları</span><span class="sxs-lookup"><span data-stu-id="5b0dc-130">XML Namespaces</span></span>  
 <span data-ttu-id="5b0dc-131">Bir alt eksen özelliğindeki ad, `Imports` ifadesiyle Global olarak belirtilen yalnızca XML ad alanı öneklerini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="5b0dc-131">The name in a child axis property can use only XML namespace prefixes declared globally with the `Imports` statement.</span></span> <span data-ttu-id="5b0dc-132">XML öğesi değişmez değerleri içinde yerel olarak belirtilen XML ad alanı öneklerini kullanamaz.</span><span class="sxs-lookup"><span data-stu-id="5b0dc-132">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="5b0dc-133">Daha fazla bilgi için bkz. [Imports bildirisi (XML ad alanı)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="5b0dc-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b0dc-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="5b0dc-134">Example</span></span>  
 <span data-ttu-id="5b0dc-135">Aşağıdaki örnekte, `contact` nesnesinden `phone` adlı alt düğümlere nasıl erişebileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5b0dc-135">The following example shows how to access the child nodes named `phone` from the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#17)]  
  
 <span data-ttu-id="5b0dc-136">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="5b0dc-136">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="5b0dc-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="5b0dc-137">Example</span></span>  
 <span data-ttu-id="5b0dc-138">Aşağıdaki örnekte, `contacts` nesnesinin `contact` alt eksen özelliği tarafından döndürülen koleksiyondan `phone` adlı alt düğümlere nasıl erişebileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5b0dc-138">The following example shows how to access the child nodes named `phone` from the collection returned by the `contact` child axis property of the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#18)]  
  
 <span data-ttu-id="5b0dc-139">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="5b0dc-139">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="5b0dc-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="5b0dc-140">Example</span></span>  
 <span data-ttu-id="5b0dc-141">Aşağıdaki örnek, `ns` bir XML ad alanı öneki olarak bildirir.</span><span class="sxs-lookup"><span data-stu-id="5b0dc-141">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="5b0dc-142">Daha sonra bir XML sabit değeri oluşturmak için ad alanının önekini kullanır ve `ns:name`nitelenmiş ada sahip ilk alt düğüme erişir.</span><span class="sxs-lookup"><span data-stu-id="5b0dc-142">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]  
  
 <span data-ttu-id="5b0dc-143">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="5b0dc-143">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="5b0dc-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b0dc-144">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="5b0dc-145">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="5b0dc-145">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="5b0dc-146">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="5b0dc-146">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="5b0dc-147">Visual Basic XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="5b0dc-147">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="5b0dc-148">Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları</span><span class="sxs-lookup"><span data-stu-id="5b0dc-148">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
