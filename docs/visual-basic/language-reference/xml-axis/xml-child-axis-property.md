---
description: 'Daha fazla bilgi edinin: XML alt eksen özelliği (Visual Basic)'
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
ms.openlocfilehash: 54920ebd35635f215eb6cb58867be1e4a7acd847
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768798"
---
# <a name="xml-child-axis-property-visual-basic"></a><span data-ttu-id="2f58b-103">XML Alt Axis Özelliği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f58b-103">XML Child Axis Property (Visual Basic)</span></span>

<span data-ttu-id="2f58b-104">Aşağıdakilerden birinin alt öğelerine erişim sağlar: <xref:System.Xml.Linq.XElement> nesne, <xref:System.Xml.Linq.XDocument> nesne, <xref:System.Xml.Linq.XElement> nesneler koleksiyonu veya <xref:System.Xml.Linq.XDocument> nesne koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="2f58b-104">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f58b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="2f58b-105">Syntax</span></span>  
  
```vb  
object.<child>  
```  
  
## <a name="parts"></a><span data-ttu-id="2f58b-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="2f58b-106">Parts</span></span>  
  
|<span data-ttu-id="2f58b-107">Süre</span><span class="sxs-lookup"><span data-stu-id="2f58b-107">Term</span></span>|<span data-ttu-id="2f58b-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="2f58b-108">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="2f58b-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2f58b-109">Required.</span></span> <span data-ttu-id="2f58b-110"><xref:System.Xml.Linq.XElement>Nesne, <xref:System.Xml.Linq.XDocument> nesne, <xref:System.Xml.Linq.XElement> nesneler koleksiyonu veya nesne koleksiyonu <xref:System.Xml.Linq.XDocument> .</span><span class="sxs-lookup"><span data-stu-id="2f58b-110">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>|  
|<span data-ttu-id="2f58b-111">. <</span><span class="sxs-lookup"><span data-stu-id="2f58b-111">.<</span></span>|<span data-ttu-id="2f58b-112">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2f58b-112">Required.</span></span> <span data-ttu-id="2f58b-113">Bir alt eksen özelliğinin başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2f58b-113">Denotes the start of a child axis property.</span></span>|  
|`child`|<span data-ttu-id="2f58b-114">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2f58b-114">Required.</span></span> <span data-ttu-id="2f58b-115">Formun erişebileceği alt düğümlerin adı `[prefix:]name` .</span><span class="sxs-lookup"><span data-stu-id="2f58b-115">Name of the child nodes to access, of the form `[prefix:]name`.</span></span><br /><br /> <span data-ttu-id="2f58b-116">-   `Prefix` Seçim.</span><span class="sxs-lookup"><span data-stu-id="2f58b-116">-   `Prefix` - Optional.</span></span> <span data-ttu-id="2f58b-117">Alt düğüm için XML ad alanı ön eki.</span><span class="sxs-lookup"><span data-stu-id="2f58b-117">XML namespace prefix for the child node.</span></span> <span data-ttu-id="2f58b-118">Bir ifadesiyle tanımlanmış bir genel XML ad alanı olmalıdır `Imports` .</span><span class="sxs-lookup"><span data-stu-id="2f58b-118">Must be a global XML namespace defined with an `Imports` statement.</span></span><br /><span data-ttu-id="2f58b-119">-   `Name` İstenir.</span><span class="sxs-lookup"><span data-stu-id="2f58b-119">-   `Name` - Required.</span></span> <span data-ttu-id="2f58b-120">Yerel alt düğüm adı.</span><span class="sxs-lookup"><span data-stu-id="2f58b-120">Local child node name.</span></span> <span data-ttu-id="2f58b-121">[BELIRTILEN XML öğelerinin ve özniteliklerin adlarına](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="2f58b-121">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
|>|<span data-ttu-id="2f58b-122">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2f58b-122">Required.</span></span> <span data-ttu-id="2f58b-123">Alt eksen özelliğinin sonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2f58b-123">Denotes the end of a child axis property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="2f58b-124">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2f58b-124">Return Value</span></span>  

 <span data-ttu-id="2f58b-125"><xref:System.Xml.Linq.XElement> nesneleri topluluğu.</span><span class="sxs-lookup"><span data-stu-id="2f58b-125">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f58b-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2f58b-126">Remarks</span></span>  

 <span data-ttu-id="2f58b-127">Alt düğümlere bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesnesinden veya bir <xref:System.Xml.Linq.XElement> veya nesneleri koleksiyonundan bir ad ile erışmek için bir xml alt Axis özelliği kullanabilirsiniz <xref:System.Xml.Linq.XDocument> .</span><span class="sxs-lookup"><span data-stu-id="2f58b-127">You can use an XML child axis property to access child nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="2f58b-128">`Value`Döndürülen koleksiyondaki ilk alt düğümün değerine erişmek IÇIN XML özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2f58b-128">Use the XML `Value` property to access the value of the first child node in the returned collection.</span></span> <span data-ttu-id="2f58b-129">Daha fazla bilgi için bkz. [XML Value özelliği](xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="2f58b-129">For more information, see [XML Value Property](xml-value-property.md).</span></span>  
  
 <span data-ttu-id="2f58b-130">Visual Basic Derleyicisi alt eksen özelliklerini yöntemine yapılan çağrılara dönüştürür <xref:System.Xml.Linq.XContainer.Elements%2A> .</span><span class="sxs-lookup"><span data-stu-id="2f58b-130">The Visual Basic compiler converts child axis properties to calls to the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="2f58b-131">XML ad alanları</span><span class="sxs-lookup"><span data-stu-id="2f58b-131">XML Namespaces</span></span>  

 <span data-ttu-id="2f58b-132">Alt eksen özelliğindeki ad, ifadesiyle Global olarak belirtilen yalnızca XML ad alanı öneklerini kullanabilir `Imports` .</span><span class="sxs-lookup"><span data-stu-id="2f58b-132">The name in a child axis property can use only XML namespace prefixes declared globally with the `Imports` statement.</span></span> <span data-ttu-id="2f58b-133">XML öğesi değişmez değerleri içinde yerel olarak belirtilen XML ad alanı öneklerini kullanamaz.</span><span class="sxs-lookup"><span data-stu-id="2f58b-133">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="2f58b-134">Daha fazla bilgi için bkz. [Imports bildirisi (XML ad alanı)](../statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="2f58b-134">For more information, see [Imports Statement (XML Namespace)](../statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f58b-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="2f58b-135">Example</span></span>  

 <span data-ttu-id="2f58b-136">Aşağıdaki örnekte, nesnesinden adlı alt düğümlere nasıl erişebileceğiniz gösterilmektedir `phone` `contact` .</span><span class="sxs-lookup"><span data-stu-id="2f58b-136">The following example shows how to access the child nodes named `phone` from the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#17)]  
  
 <span data-ttu-id="2f58b-137">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="2f58b-137">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="2f58b-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="2f58b-138">Example</span></span>  

 <span data-ttu-id="2f58b-139">Aşağıdaki örnek, `phone` `contact` nesnesinin alt eksen özelliği tarafından döndürülen koleksiyondan adlı alt düğümlere nasıl erişegösterdiğini gösterir `contacts` .</span><span class="sxs-lookup"><span data-stu-id="2f58b-139">The following example shows how to access the child nodes named `phone` from the collection returned by the `contact` child axis property of the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#18)]  
  
 <span data-ttu-id="2f58b-140">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="2f58b-140">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="2f58b-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="2f58b-141">Example</span></span>  

 <span data-ttu-id="2f58b-142">Aşağıdaki örnek `ns` BIR XML ad alanı ön eki olarak bildirir.</span><span class="sxs-lookup"><span data-stu-id="2f58b-142">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="2f58b-143">Daha sonra bir XML sabit değeri oluşturmak için ad alanının önekini kullanır ve ilk alt düğüme tam adı ile erişin `ns:name` .</span><span class="sxs-lookup"><span data-stu-id="2f58b-143">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]  
  
 <span data-ttu-id="2f58b-144">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="2f58b-144">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="2f58b-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f58b-145">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="2f58b-146">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="2f58b-146">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="2f58b-147">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="2f58b-147">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="2f58b-148">Visual Basic'de XML Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2f58b-148">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="2f58b-149">Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları</span><span class="sxs-lookup"><span data-stu-id="2f58b-149">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
