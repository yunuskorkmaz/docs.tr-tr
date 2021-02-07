---
description: 'Daha fazla bilgi edinin: XML belgesi değişmez değeri (Visual Basic)'
title: XML Belgesi Değişmez Değeri
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
ms.openlocfilehash: d268f205c9357598a631216879b424dd8155268a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700318"
---
# <a name="xml-document-literal-visual-basic"></a><span data-ttu-id="5fec3-103">XML Belgesi Değişmez Değeri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5fec3-103">XML Document Literal (Visual Basic)</span></span>

<span data-ttu-id="5fec3-104">Bir nesneyi temsil eden sabit değer <xref:System.Xml.Linq.XDocument> .</span><span class="sxs-lookup"><span data-stu-id="5fec3-104">A literal representing an <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fec3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5fec3-105">Syntax</span></span>  
  
```xml  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a><span data-ttu-id="5fec3-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="5fec3-106">Parts</span></span>  
  
|<span data-ttu-id="5fec3-107">Süre</span><span class="sxs-lookup"><span data-stu-id="5fec3-107">Term</span></span>|<span data-ttu-id="5fec3-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="5fec3-108">Definition</span></span>|  
|---|---|  
|`encoding`|<span data-ttu-id="5fec3-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="5fec3-109">Optional.</span></span> <span data-ttu-id="5fec3-110">Belgenin hangi kodlamayla kullandığını bildiren değişmez metin.</span><span class="sxs-lookup"><span data-stu-id="5fec3-110">Literal text declaring which encoding the document uses.</span></span>|  
|`standalone`|<span data-ttu-id="5fec3-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="5fec3-111">Optional.</span></span> <span data-ttu-id="5fec3-112">Değişmez değer metni.</span><span class="sxs-lookup"><span data-stu-id="5fec3-112">Literal text.</span></span> <span data-ttu-id="5fec3-113">"Yes" veya "No" olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5fec3-113">Must be "yes" or "no".</span></span>|  
|`piCommentList`|<span data-ttu-id="5fec3-114">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="5fec3-114">Optional.</span></span> <span data-ttu-id="5fec3-115">XML işleme yönergelerinin ve XML açıklamalarının listesi.</span><span class="sxs-lookup"><span data-stu-id="5fec3-115">List of XML processing instructions and XML comments.</span></span> <span data-ttu-id="5fec3-116">Aşağıdaki biçimi alır:</span><span class="sxs-lookup"><span data-stu-id="5fec3-116">Takes the following format:</span></span><br /><br /> <span data-ttu-id="5fec3-117">`piComment [` `piComment` `... ]`</span><span class="sxs-lookup"><span data-stu-id="5fec3-117">`piComment [` `piComment` `... ]`</span></span><br /><br /> <span data-ttu-id="5fec3-118">Her biri `piComment` aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="5fec3-118">Each `piComment` can be one of the following:</span></span><br /><br /> <span data-ttu-id="5fec3-119">-   [XML Işleme yönergesi sabit değeri](xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="5fec3-119">-   [XML Processing Instruction Literal](xml-processing-instruction-literal.md).</span></span><br /><span data-ttu-id="5fec3-120">-   [XML açıklama değişmez değeri](xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="5fec3-120">-   [XML Comment Literal](xml-comment-literal.md).</span></span>|  
|`rootElement`|<span data-ttu-id="5fec3-121">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5fec3-121">Required.</span></span> <span data-ttu-id="5fec3-122">Belgenin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="5fec3-122">Root element of the document.</span></span> <span data-ttu-id="5fec3-123">Biçim aşağıdakilerden biridir:</span><span class="sxs-lookup"><span data-stu-id="5fec3-123">The format is one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="5fec3-124">[XML öğesi değişmez değeri](xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="5fec3-124">[XML Element Literal](xml-element-literal.md).</span></span></li><li><span data-ttu-id="5fec3-125">Formun katıştırılmış ifadesi `<%=` `elementExp` `%>` .</span><span class="sxs-lookup"><span data-stu-id="5fec3-125">Embedded expression of the form `<%=` `elementExp` `%>`.</span></span> <span data-ttu-id="5fec3-126">, Aşağıdakilerden `elementExp` birini döndürür:</span><span class="sxs-lookup"><span data-stu-id="5fec3-126">The `elementExp` returns one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="5fec3-127">Bir <xref:System.Xml.Linq.XElement> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="5fec3-127">An <xref:System.Xml.Linq.XElement> object.</span></span></li><li><span data-ttu-id="5fec3-128">Bir <xref:System.Xml.Linq.XElement> nesne ve herhangi bir sayıda ve nesne içeren bir <xref:System.Xml.Linq.XProcessingInstruction> koleksiyon <xref:System.Xml.Linq.XComment> .</span><span class="sxs-lookup"><span data-stu-id="5fec3-128">A collection that contains one <xref:System.Xml.Linq.XElement> object and any number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects.</span></span></li></ul></li></ul><br /> <span data-ttu-id="5fec3-129">Daha fazla bilgi için bkz. [XML 'de katıştırılmış ifadeler](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="5fec3-129">For more information, see [Embedded Expressions in XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="5fec3-130">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5fec3-130">Return Value</span></span>  

 <span data-ttu-id="5fec3-131">Bir <xref:System.Xml.Linq.XDocument> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="5fec3-131">An <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fec3-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5fec3-132">Remarks</span></span>  

 <span data-ttu-id="5fec3-133">XML belgesi değişmez değeri, değişmez değerin başlangıcında XML bildirimi tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="5fec3-133">An XML document literal is identified by the XML declaration at the start of the literal.</span></span> <span data-ttu-id="5fec3-134">Her XML belgesi değişmez değeri tam olarak bir kök XML öğesi içermelidir, ancak herhangi bir sayıda XML işleme yönergesi ve XML açıklaması olabilir.</span><span class="sxs-lookup"><span data-stu-id="5fec3-134">Although each XML document literal must have exactly one root XML element, it can have any number of XML processing instructions and XML comments.</span></span>  
  
 <span data-ttu-id="5fec3-135">XML belgesi değişmez değeri bir XML öğesinde görünemez.</span><span class="sxs-lookup"><span data-stu-id="5fec3-135">An XML document literal cannot appear in an XML element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5fec3-136">Bir XML sabit değeri, satır devamlılık karakterleri kullanmadan birden fazla satıra yayılabilir.</span><span class="sxs-lookup"><span data-stu-id="5fec3-136">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="5fec3-137">Bu sayede bir XML belgesinden içerik kopyalayabilir ve doğrudan bir Visual Basic programına yapıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fec3-137">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="5fec3-138">Visual Basic derleyici, XML belgesi değişmez değerini <xref:System.Xml.Linq.XDocument.%23ctor%2A> ve oluşturuculara çağrılarına dönüştürür <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> .</span><span class="sxs-lookup"><span data-stu-id="5fec3-138">The Visual Basic compiler converts the XML document literal into calls to the <xref:System.Xml.Linq.XDocument.%23ctor%2A> and <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> constructors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fec3-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="5fec3-139">Example</span></span>  

 <span data-ttu-id="5fec3-140">Aşağıdaki örnek, bir XML bildirimi, işleme yönergesi, açıklama ve başka bir öğesi içeren bir öğesi olan bir XML belgesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5fec3-140">The following example creates an XML document that has an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
 [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="5fec3-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5fec3-141">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- <xref:System.Xml.Linq.XProcessingInstruction>
- <xref:System.Xml.Linq.XComment>
- <xref:System.Xml.Linq.XDocument>
- [<span data-ttu-id="5fec3-142">XML İşleme Talimatı Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="5fec3-142">XML Processing Instruction Literal</span></span>](xml-processing-instruction-literal.md)
- [<span data-ttu-id="5fec3-143">XML Açıklama Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="5fec3-143">XML Comment Literal</span></span>](xml-comment-literal.md)
- [<span data-ttu-id="5fec3-144">XML Öğesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="5fec3-144">XML Element Literal</span></span>](xml-element-literal.md)
- [<span data-ttu-id="5fec3-145">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="5fec3-145">XML Literals</span></span>](index.md)
- [<span data-ttu-id="5fec3-146">Visual Basic'de XML Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5fec3-146">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="5fec3-147">XML'de Katıştırılmış İfadeler</span><span class="sxs-lookup"><span data-stu-id="5fec3-147">Embedded Expressions in XML</span></span>](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)
