---
title: XML CDATA Değişmez Değeri
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
ms.openlocfilehash: 72e899e7bd30f2edf0e88207bb3b75bdf36fa11c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349429"
---
# <a name="xml-cdata-literal-visual-basic"></a><span data-ttu-id="1945c-102">XML CDATA Değişmez Değeri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1945c-102">XML CDATA Literal (Visual Basic)</span></span>
<span data-ttu-id="1945c-103">A literal representing an <xref:System.Xml.Linq.XCData> object.</span><span class="sxs-lookup"><span data-stu-id="1945c-103">A literal representing an <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1945c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1945c-104">Syntax</span></span>  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a><span data-ttu-id="1945c-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="1945c-105">Parts</span></span>  
 `<![CDATA[`  
 <span data-ttu-id="1945c-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="1945c-106">Required.</span></span> <span data-ttu-id="1945c-107">Denotes the start of the XML CDATA section.</span><span class="sxs-lookup"><span data-stu-id="1945c-107">Denotes the start of the XML CDATA section.</span></span>  
  
 `content`  
 <span data-ttu-id="1945c-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="1945c-108">Required.</span></span> <span data-ttu-id="1945c-109">Text content to appear in the XML CDATA section.</span><span class="sxs-lookup"><span data-stu-id="1945c-109">Text content to appear in the XML CDATA section.</span></span>  
  
 `]]>`  
 <span data-ttu-id="1945c-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="1945c-110">Required.</span></span> <span data-ttu-id="1945c-111">Denotes the end of the section.</span><span class="sxs-lookup"><span data-stu-id="1945c-111">Denotes the end of the section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1945c-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1945c-112">Return Value</span></span>  
 <span data-ttu-id="1945c-113">An <xref:System.Xml.Linq.XCData> object.</span><span class="sxs-lookup"><span data-stu-id="1945c-113">An <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1945c-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1945c-114">Remarks</span></span>  
 <span data-ttu-id="1945c-115">XML CDATA sections contain raw text that should be included, but not parsed, with the XML that contains it.</span><span class="sxs-lookup"><span data-stu-id="1945c-115">XML CDATA sections contain raw text that should be included, but not parsed, with the XML that contains it.</span></span> <span data-ttu-id="1945c-116">A XML CDATA section can contain any text.</span><span class="sxs-lookup"><span data-stu-id="1945c-116">A XML CDATA section can contain any text.</span></span> <span data-ttu-id="1945c-117">This includes reserved XML characters.</span><span class="sxs-lookup"><span data-stu-id="1945c-117">This includes reserved XML characters.</span></span> <span data-ttu-id="1945c-118">The XML CDATA section ends with the sequence "]]>".</span><span class="sxs-lookup"><span data-stu-id="1945c-118">The XML CDATA section ends with the sequence "]]>".</span></span> <span data-ttu-id="1945c-119">This implies the following points:</span><span class="sxs-lookup"><span data-stu-id="1945c-119">This implies the following points:</span></span>  
  
- <span data-ttu-id="1945c-120">You cannot use an embedded expression in an XML CDATA literal because the embedded expression delimiters are valid XML CDATA content.</span><span class="sxs-lookup"><span data-stu-id="1945c-120">You cannot use an embedded expression in an XML CDATA literal because the embedded expression delimiters are valid XML CDATA content.</span></span>  
  
- <span data-ttu-id="1945c-121">XML CDATA sections cannot be nested, because `content` cannot contain the value "]]>".</span><span class="sxs-lookup"><span data-stu-id="1945c-121">XML CDATA sections cannot be nested, because `content` cannot contain the value "]]>".</span></span>  
  
 <span data-ttu-id="1945c-122">You can assign an XML CDATA literal to a variable, or include it in an XML element literal.</span><span class="sxs-lookup"><span data-stu-id="1945c-122">You can assign an XML CDATA literal to a variable, or include it in an XML element literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1945c-123">An XML literal can span multiple lines but does not use line continuation characters.</span><span class="sxs-lookup"><span data-stu-id="1945c-123">An XML literal can span multiple lines but does not use line continuation characters.</span></span> <span data-ttu-id="1945c-124">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span><span class="sxs-lookup"><span data-stu-id="1945c-124">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="1945c-125">The Visual Basic compiler converts the XML CDATA literal to a call to the <xref:System.Xml.Linq.XCData.%23ctor%2A> constructor.</span><span class="sxs-lookup"><span data-stu-id="1945c-125">The Visual Basic compiler converts the XML CDATA literal to a call to the <xref:System.Xml.Linq.XCData.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1945c-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="1945c-126">Example</span></span>  
 <span data-ttu-id="1945c-127">The following example creates a CDATA section that contains the text "Can contain literal \<XML> tags".</span><span class="sxs-lookup"><span data-stu-id="1945c-127">The following example creates a CDATA section that contains the text "Can contain literal \<XML> tags".</span></span>  
  
 [!code-vb[VbXMLSamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="1945c-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1945c-128">See also</span></span>

- <xref:System.Xml.Linq.XCData>
- [<span data-ttu-id="1945c-129">XML Öğesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="1945c-129">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="1945c-130">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="1945c-130">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="1945c-131">Creating XML in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1945c-131">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
