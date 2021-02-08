---
description: 'Hakkında daha fazla bilgi edinin: XML açıklama değişmez değeri (Visual Basic)'
title: XML Açıklama Değişmez Değeri
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
ms.openlocfilehash: f44d2e132236d74d312910921fabb3a85afd82d6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768746"
---
# <a name="xml-comment-literal-visual-basic"></a><span data-ttu-id="374aa-103">XML Açıklama Değişmez Değeri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="374aa-103">XML Comment Literal (Visual Basic)</span></span>

<span data-ttu-id="374aa-104">Bir nesneyi temsil eden sabit değer <xref:System.Xml.Linq.XComment> .</span><span class="sxs-lookup"><span data-stu-id="374aa-104">A literal representing an <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="374aa-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="374aa-105">Syntax</span></span>  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a><span data-ttu-id="374aa-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="374aa-106">Parts</span></span>  
  
|<span data-ttu-id="374aa-107">Süre</span><span class="sxs-lookup"><span data-stu-id="374aa-107">Term</span></span>|<span data-ttu-id="374aa-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="374aa-108">Definition</span></span>|  
|---|---|  
|`<!--`|<span data-ttu-id="374aa-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="374aa-109">Required.</span></span> <span data-ttu-id="374aa-110">XML açıklamasının başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="374aa-110">Denotes the start of the XML comment.</span></span>|  
|`content`|<span data-ttu-id="374aa-111">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="374aa-111">Required.</span></span> <span data-ttu-id="374aa-112">XML açıklamasında görüntülenecek metin.</span><span class="sxs-lookup"><span data-stu-id="374aa-112">Text to appear in the XML comment.</span></span> <span data-ttu-id="374aa-113">Bir dizi iki kısa çizgi (--) veya kapanış etiketinin bitişiğindeki bir tire ile bitemez.</span><span class="sxs-lookup"><span data-stu-id="374aa-113">Cannot contain a series of two hyphens (--) or end with a hyphen adjacent to the closing tag.</span></span>|  
|`-->`|<span data-ttu-id="374aa-114">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="374aa-114">Required.</span></span> <span data-ttu-id="374aa-115">XML açıklamasının sonunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="374aa-115">Denotes the end of the XML comment.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="374aa-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="374aa-116">Return Value</span></span>  

 <span data-ttu-id="374aa-117">Bir <xref:System.Xml.Linq.XComment> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="374aa-117">An <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="374aa-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="374aa-118">Remarks</span></span>  

 <span data-ttu-id="374aa-119">XML açıklama değişmez değerleri belge içeriği içermez; Bunlar belge hakkında bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="374aa-119">XML comment literals do not contain document content; they contain information about the document.</span></span> <span data-ttu-id="374aa-120">XML açıklama bölümü "-->" sırasıyla biter.</span><span class="sxs-lookup"><span data-stu-id="374aa-120">The XML comment section ends with the sequence "-->".</span></span> <span data-ttu-id="374aa-121">Bu, aşağıdaki noktaları gösterir:</span><span class="sxs-lookup"><span data-stu-id="374aa-121">This implies the following points:</span></span>  
  
- <span data-ttu-id="374aa-122">Gömülü ifade sınırlayıcıları geçerli XML açıklama içeriği olduğundan, bir XML açıklama değişmez değerinde katıştırılmış ifade kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="374aa-122">You cannot use an embedded expression in an XML comment literal because the embedded expression delimiters are valid XML comment content.</span></span>  
  
- <span data-ttu-id="374aa-123">`content`"-->" değerini IÇEREMEDIĞINDEN XML açıklama bölümleri iç içe geçirilemez.</span><span class="sxs-lookup"><span data-stu-id="374aa-123">XML comment sections cannot be nested, because `content` cannot contain the value "-->".</span></span>  
  
 <span data-ttu-id="374aa-124">Bir değişkene bir XML açıklama sabit değeri atayabilir veya onu bir XML öğesi değişmez değerine dahil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="374aa-124">You can assign an XML comment literal to a variable, or you can include it in an XML element literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="374aa-125">Bir XML sabit değeri, satır devamlılık karakterleri kullanmadan birden fazla satıra yayılabilir.</span><span class="sxs-lookup"><span data-stu-id="374aa-125">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="374aa-126">Bu özellik bir XML belgesinden içerik kopyalamanızı ve bunu doğrudan bir Visual Basic programına yapıştırmayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="374aa-126">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="374aa-127">Visual Basic derleyici, XML açıklama değişmez değerini oluşturucuya bir çağrıya dönüştürür <xref:System.Xml.Linq.XComment.%23ctor%2A> .</span><span class="sxs-lookup"><span data-stu-id="374aa-127">The Visual Basic compiler converts the XML comment literal to a call to the <xref:System.Xml.Linq.XComment.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="374aa-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="374aa-128">Example</span></span>  

 <span data-ttu-id="374aa-129">Aşağıdaki örnek "This bir açıklamadır" metnini içeren bir XML açıklaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="374aa-129">The following example creates an XML comment that contains the text "This is a comment".</span></span>  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="374aa-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="374aa-130">See also</span></span>

- <xref:System.Xml.Linq.XComment>
- [<span data-ttu-id="374aa-131">XML Öğesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="374aa-131">XML Element Literal</span></span>](xml-element-literal.md)
- [<span data-ttu-id="374aa-132">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="374aa-132">XML Literals</span></span>](index.md)
- [<span data-ttu-id="374aa-133">Visual Basic'de XML Oluşturma</span><span class="sxs-lookup"><span data-stu-id="374aa-133">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
