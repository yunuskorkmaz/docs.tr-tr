---
title: XML Belgesi Değişmez Değeri (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d5c84fecbb035c229cc3576bc556db6ecb6f3934
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="xml-document-literal-visual-basic"></a><span data-ttu-id="a9806-102">XML Belgesi Değişmez Değeri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9806-102">XML Document Literal (Visual Basic)</span></span>
<span data-ttu-id="a9806-103">Değişmez değer gösteren bir <xref:System.Xml.Linq.XDocument> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="a9806-103">A literal representing an <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9806-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a9806-104">Syntax</span></span>  
  
```xml  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a><span data-ttu-id="a9806-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="a9806-105">Parts</span></span>  
  
|<span data-ttu-id="a9806-106">Terim</span><span class="sxs-lookup"><span data-stu-id="a9806-106">Term</span></span>|<span data-ttu-id="a9806-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="a9806-107">Definition</span></span>|  
|---|---|  
|`encoding`|<span data-ttu-id="a9806-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="a9806-108">Optional.</span></span> <span data-ttu-id="a9806-109">Metin kodlama hangi belge bildirme kullanır.</span><span class="sxs-lookup"><span data-stu-id="a9806-109">Literal text declaring which encoding the document uses.</span></span>|  
|`standalone`|<span data-ttu-id="a9806-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="a9806-110">Optional.</span></span> <span data-ttu-id="a9806-111">Düz metin.</span><span class="sxs-lookup"><span data-stu-id="a9806-111">Literal text.</span></span> <span data-ttu-id="a9806-112">"Evet" olması gerekir veya "Hayır".</span><span class="sxs-lookup"><span data-stu-id="a9806-112">Must be "yes" or "no".</span></span>|  
|`piCommentList`|<span data-ttu-id="a9806-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="a9806-113">Optional.</span></span> <span data-ttu-id="a9806-114">XML işleme yönergeleri ve XML açıklamaları listesi.</span><span class="sxs-lookup"><span data-stu-id="a9806-114">List of XML processing instructions and XML comments.</span></span> <span data-ttu-id="a9806-115">Şu biçimi alır:</span><span class="sxs-lookup"><span data-stu-id="a9806-115">Takes the following format:</span></span><br /><br /> <span data-ttu-id="a9806-116">`piComment [` `piComment` `... ]`</span><span class="sxs-lookup"><span data-stu-id="a9806-116">`piComment [` `piComment` `... ]`</span></span><br /><br /> <span data-ttu-id="a9806-117">Her `piComment` şunlardan biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="a9806-117">Each `piComment` can be one of the following:</span></span><br /><br /> <span data-ttu-id="a9806-118">-   [XML işleme talimatı değişmez değeri](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="a9806-118">-   [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span></span><br /><span data-ttu-id="a9806-119">-   [XML açıklama değişmez değeri](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="a9806-119">-   [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span></span>|  
|`rootElement`|<span data-ttu-id="a9806-120">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="a9806-120">Required.</span></span> <span data-ttu-id="a9806-121">Belgenin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="a9806-121">Root element of the document.</span></span> <span data-ttu-id="a9806-122">Aşağıdakilerden birini biçimdedir:</span><span class="sxs-lookup"><span data-stu-id="a9806-122">The format is one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="a9806-123">[XML öğesi değişmez değeri](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="a9806-123">[XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span></li><li><span data-ttu-id="a9806-124">İfade biçiminde katıştırılmış `<%=` `elementExp` `%>`.</span><span class="sxs-lookup"><span data-stu-id="a9806-124">Embedded expression of the form `<%=` `elementExp` `%>`.</span></span> <span data-ttu-id="a9806-125">`elementExp` Aşağıdakilerden birini döndürür:</span><span class="sxs-lookup"><span data-stu-id="a9806-125">The `elementExp` returns one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="a9806-126">Bir <xref:System.Xml.Linq.XElement> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="a9806-126">An <xref:System.Xml.Linq.XElement> object.</span></span></li><li><span data-ttu-id="a9806-127">Birini içeren bir koleksiyon <xref:System.Xml.Linq.XElement> nesne ve herhangi bir sayıda <xref:System.Xml.Linq.XProcessingInstruction> ve <xref:System.Xml.Linq.XComment> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="a9806-127">A collection that contains one <xref:System.Xml.Linq.XElement> object and any number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects.</span></span></li></ul></li></ul><br /> <span data-ttu-id="a9806-128">Daha fazla bilgi için bkz: [XML'de katıştırılmış ifadeler](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a9806-128">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="a9806-129">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a9806-129">Return Value</span></span>  
 <span data-ttu-id="a9806-130">Bir <xref:System.Xml.Linq.XDocument> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="a9806-130">An <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9806-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a9806-131">Remarks</span></span>  
 <span data-ttu-id="a9806-132">Değişmez değer bir XML belgesi değişmez değeri başlangıç XML bildirimi tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a9806-132">An XML document literal is identified by the XML declaration at the start of the literal.</span></span> <span data-ttu-id="a9806-133">Her bir XML belgesi değişmez değeri tam olarak bir kök XML öğesi sahip olmanız gerekir, ancak herhangi bir sayıda XML işleme yönergeleri ve XML açıklamaları olabilir.</span><span class="sxs-lookup"><span data-stu-id="a9806-133">Although each XML document literal must have exactly one root XML element, it can have any number of XML processing instructions and XML comments.</span></span>  
  
 <span data-ttu-id="a9806-134">Bir XML belgesi değişmez değeri bir XML öğesi yer alamaz.</span><span class="sxs-lookup"><span data-stu-id="a9806-134">An XML document literal cannot appear in an XML element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a9806-135">XML değişmez değer, satır devamlılığı karakterleri kullanmadan birden fazla satır yayılabilir.</span><span class="sxs-lookup"><span data-stu-id="a9806-135">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="a9806-136">Bu, bir XML belgesinden içeriği Kopyala ve doğrudan bir Visual Basic programa yapıştırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a9806-136">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="a9806-137">Visual Basic derleyici çağrıları XML belgesi değişmez değeri dönüştürür <xref:System.Xml.Linq.XDocument.%23ctor%2A> ve <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> oluşturucular.</span><span class="sxs-lookup"><span data-stu-id="a9806-137">The Visual Basic compiler converts the XML document literal into calls to the <xref:System.Xml.Linq.XDocument.%23ctor%2A> and <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> constructors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9806-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="a9806-138">Example</span></span>  
 <span data-ttu-id="a9806-139">Aşağıdaki örnek, bir XML bildirimi, bir işleme yönergesi, açıklama ve başka bir öğe içeren bir öğeyi içeren bir XML belgesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a9806-139">The following example creates an XML document that has an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
 [!code-vb[VbXMLSamples#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-document-literal_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a9806-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a9806-140">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 <xref:System.Xml.Linq.XProcessingInstruction>  
 <xref:System.Xml.Linq.XComment>  
 <xref:System.Xml.Linq.XDocument>  
 [<span data-ttu-id="a9806-141">XML İşleme Talimatı Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="a9806-141">XML Processing Instruction Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)  
 [<span data-ttu-id="a9806-142">XML Açıklama Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="a9806-142">XML Comment Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)  
 [<span data-ttu-id="a9806-143">XML Öğesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="a9806-143">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="a9806-144">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="a9806-144">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="a9806-145">Visual Basic'de XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="a9806-145">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="a9806-146">XML'de Katıştırılmış İfadeler</span><span class="sxs-lookup"><span data-stu-id="a9806-146">Embedded Expressions in XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
