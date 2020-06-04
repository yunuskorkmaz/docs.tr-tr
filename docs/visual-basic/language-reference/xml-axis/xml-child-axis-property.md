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
ms.openlocfilehash: 90dc22d12be5566fa1ee40f6b0e48eff8088e67b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400272"
---
# <a name="xml-child-axis-property-visual-basic"></a><span data-ttu-id="749e7-102">XML Alt Axis Özelliği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="749e7-102">XML Child Axis Property (Visual Basic)</span></span>
<span data-ttu-id="749e7-103">Aşağıdakilerden birinin alt öğelerine erişim sağlar: <xref:System.Xml.Linq.XElement> nesne, <xref:System.Xml.Linq.XDocument> nesne, <xref:System.Xml.Linq.XElement> nesneler koleksiyonu veya <xref:System.Xml.Linq.XDocument> nesne koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="749e7-103">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="749e7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="749e7-104">Syntax</span></span>  
  
```vb  
object.<child>  
```  
  
## <a name="parts"></a><span data-ttu-id="749e7-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="749e7-105">Parts</span></span>  
  
|<span data-ttu-id="749e7-106">Terim</span><span class="sxs-lookup"><span data-stu-id="749e7-106">Term</span></span>|<span data-ttu-id="749e7-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="749e7-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="749e7-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="749e7-108">Required.</span></span> <span data-ttu-id="749e7-109"><xref:System.Xml.Linq.XElement>Nesne, <xref:System.Xml.Linq.XDocument> nesne, <xref:System.Xml.Linq.XElement> nesneler koleksiyonu veya nesne koleksiyonu <xref:System.Xml.Linq.XDocument> .</span><span class="sxs-lookup"><span data-stu-id="749e7-109">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>|  
|<span data-ttu-id="749e7-110">. <</span><span class="sxs-lookup"><span data-stu-id="749e7-110">.<</span></span>|<span data-ttu-id="749e7-111">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="749e7-111">Required.</span></span> <span data-ttu-id="749e7-112">Bir alt eksen özelliğinin başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="749e7-112">Denotes the start of a child axis property.</span></span>|  
|`child`|<span data-ttu-id="749e7-113">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="749e7-113">Required.</span></span> <span data-ttu-id="749e7-114">Formun erişebileceği alt düğümlerin adı `[prefix:]name` .</span><span class="sxs-lookup"><span data-stu-id="749e7-114">Name of the child nodes to access, of the form `[prefix:]name`.</span></span><br /><br /> <span data-ttu-id="749e7-115">-   `Prefix`Seçim.</span><span class="sxs-lookup"><span data-stu-id="749e7-115">-   `Prefix` - Optional.</span></span> <span data-ttu-id="749e7-116">Alt düğüm için XML ad alanı ön eki.</span><span class="sxs-lookup"><span data-stu-id="749e7-116">XML namespace prefix for the child node.</span></span> <span data-ttu-id="749e7-117">Bir ifadesiyle tanımlanmış bir genel XML ad alanı olmalıdır `Imports` .</span><span class="sxs-lookup"><span data-stu-id="749e7-117">Must be a global XML namespace defined with an `Imports` statement.</span></span><br /><span data-ttu-id="749e7-118">-   `Name`İstenir.</span><span class="sxs-lookup"><span data-stu-id="749e7-118">-   `Name` - Required.</span></span> <span data-ttu-id="749e7-119">Yerel alt düğüm adı.</span><span class="sxs-lookup"><span data-stu-id="749e7-119">Local child node name.</span></span> <span data-ttu-id="749e7-120">[BELIRTILEN XML öğelerinin ve özniteliklerin adlarına](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="749e7-120">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
|>|<span data-ttu-id="749e7-121">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="749e7-121">Required.</span></span> <span data-ttu-id="749e7-122">Alt eksen özelliğinin sonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="749e7-122">Denotes the end of a child axis property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="749e7-123">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="749e7-123">Return Value</span></span>  
 <span data-ttu-id="749e7-124"><xref:System.Xml.Linq.XElement> nesneleri topluluğu.</span><span class="sxs-lookup"><span data-stu-id="749e7-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="749e7-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="749e7-125">Remarks</span></span>  
 <span data-ttu-id="749e7-126">Alt düğümlere bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesnesinden veya bir <xref:System.Xml.Linq.XElement> veya nesneleri koleksiyonundan bir ad ile erışmek için bir xml alt Axis özelliği kullanabilirsiniz <xref:System.Xml.Linq.XDocument> .</span><span class="sxs-lookup"><span data-stu-id="749e7-126">You can use an XML child axis property to access child nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="749e7-127">`Value`Döndürülen koleksiyondaki ilk alt düğümün değerine erişmek IÇIN XML özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="749e7-127">Use the XML `Value` property to access the value of the first child node in the returned collection.</span></span> <span data-ttu-id="749e7-128">Daha fazla bilgi için bkz. [XML Value özelliği](xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="749e7-128">For more information, see [XML Value Property](xml-value-property.md).</span></span>  
  
 <span data-ttu-id="749e7-129">Visual Basic Derleyicisi alt eksen özelliklerini yöntemine yapılan çağrılara dönüştürür <xref:System.Xml.Linq.XContainer.Elements%2A> .</span><span class="sxs-lookup"><span data-stu-id="749e7-129">The Visual Basic compiler converts child axis properties to calls to the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="749e7-130">XML ad alanları</span><span class="sxs-lookup"><span data-stu-id="749e7-130">XML Namespaces</span></span>  
 <span data-ttu-id="749e7-131">Alt eksen özelliğindeki ad, ifadesiyle Global olarak belirtilen yalnızca XML ad alanı öneklerini kullanabilir `Imports` .</span><span class="sxs-lookup"><span data-stu-id="749e7-131">The name in a child axis property can use only XML namespace prefixes declared globally with the `Imports` statement.</span></span> <span data-ttu-id="749e7-132">XML öğesi değişmez değerleri içinde yerel olarak belirtilen XML ad alanı öneklerini kullanamaz.</span><span class="sxs-lookup"><span data-stu-id="749e7-132">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="749e7-133">Daha fazla bilgi için bkz. [Imports bildirisi (XML ad alanı)](../statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="749e7-133">For more information, see [Imports Statement (XML Namespace)](../statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="749e7-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="749e7-134">Example</span></span>  
 <span data-ttu-id="749e7-135">Aşağıdaki örnekte, nesnesinden adlı alt düğümlere nasıl erişebileceğiniz gösterilmektedir `phone` `contact` .</span><span class="sxs-lookup"><span data-stu-id="749e7-135">The following example shows how to access the child nodes named `phone` from the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#17)]  
  
 <span data-ttu-id="749e7-136">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="749e7-136">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="749e7-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="749e7-137">Example</span></span>  
 <span data-ttu-id="749e7-138">Aşağıdaki örnek, `phone` `contact` nesnesinin alt eksen özelliği tarafından döndürülen koleksiyondan adlı alt düğümlere nasıl erişegösterdiğini gösterir `contacts` .</span><span class="sxs-lookup"><span data-stu-id="749e7-138">The following example shows how to access the child nodes named `phone` from the collection returned by the `contact` child axis property of the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#18)]  
  
 <span data-ttu-id="749e7-139">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="749e7-139">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="749e7-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="749e7-140">Example</span></span>  
 <span data-ttu-id="749e7-141">Aşağıdaki örnek `ns` BIR XML ad alanı ön eki olarak bildirir.</span><span class="sxs-lookup"><span data-stu-id="749e7-141">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="749e7-142">Daha sonra bir XML sabit değeri oluşturmak için ad alanının önekini kullanır ve ilk alt düğüme tam adı ile erişin `ns:name` .</span><span class="sxs-lookup"><span data-stu-id="749e7-142">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]  
  
 <span data-ttu-id="749e7-143">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="749e7-143">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="749e7-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="749e7-144">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="749e7-145">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="749e7-145">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="749e7-146">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="749e7-146">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="749e7-147">Visual Basic'de XML Oluşturma</span><span class="sxs-lookup"><span data-stu-id="749e7-147">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="749e7-148">Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları</span><span class="sxs-lookup"><span data-stu-id="749e7-148">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
