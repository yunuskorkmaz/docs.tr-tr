---
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
ms.openlocfilehash: 3272cc0f976d6e8819e51bb5d5fce73066007963
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875194"
---
# <a name="xml-comment-literal-visual-basic"></a><span data-ttu-id="412cd-102">XML Açıklama Değişmez Değeri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="412cd-102">XML Comment Literal (Visual Basic)</span></span>

<span data-ttu-id="412cd-103">Bir nesneyi temsil eden sabit değer <xref:System.Xml.Linq.XComment> .</span><span class="sxs-lookup"><span data-stu-id="412cd-103">A literal representing an <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="412cd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="412cd-104">Syntax</span></span>  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a><span data-ttu-id="412cd-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="412cd-105">Parts</span></span>  
  
|<span data-ttu-id="412cd-106">Terim</span><span class="sxs-lookup"><span data-stu-id="412cd-106">Term</span></span>|<span data-ttu-id="412cd-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="412cd-107">Definition</span></span>|  
|---|---|  
|`<!--`|<span data-ttu-id="412cd-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="412cd-108">Required.</span></span> <span data-ttu-id="412cd-109">XML açıklamasının başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="412cd-109">Denotes the start of the XML comment.</span></span>|  
|`content`|<span data-ttu-id="412cd-110">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="412cd-110">Required.</span></span> <span data-ttu-id="412cd-111">XML açıklamasında görüntülenecek metin.</span><span class="sxs-lookup"><span data-stu-id="412cd-111">Text to appear in the XML comment.</span></span> <span data-ttu-id="412cd-112">Bir dizi iki kısa çizgi (--) veya kapanış etiketinin bitişiğindeki bir tire ile bitemez.</span><span class="sxs-lookup"><span data-stu-id="412cd-112">Cannot contain a series of two hyphens (--) or end with a hyphen adjacent to the closing tag.</span></span>|  
|`-->`|<span data-ttu-id="412cd-113">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="412cd-113">Required.</span></span> <span data-ttu-id="412cd-114">XML açıklamasının sonunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="412cd-114">Denotes the end of the XML comment.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="412cd-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="412cd-115">Return Value</span></span>  

 <span data-ttu-id="412cd-116">Bir <xref:System.Xml.Linq.XComment> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="412cd-116">An <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="412cd-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="412cd-117">Remarks</span></span>  

 <span data-ttu-id="412cd-118">XML açıklama değişmez değerleri belge içeriği içermez; Bunlar belge hakkında bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="412cd-118">XML comment literals do not contain document content; they contain information about the document.</span></span> <span data-ttu-id="412cd-119">XML açıklama bölümü "-->" sırasıyla biter.</span><span class="sxs-lookup"><span data-stu-id="412cd-119">The XML comment section ends with the sequence "-->".</span></span> <span data-ttu-id="412cd-120">Bu, aşağıdaki noktaları gösterir:</span><span class="sxs-lookup"><span data-stu-id="412cd-120">This implies the following points:</span></span>  
  
- <span data-ttu-id="412cd-121">Gömülü ifade sınırlayıcıları geçerli XML açıklama içeriği olduğundan, bir XML açıklama değişmez değerinde katıştırılmış ifade kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="412cd-121">You cannot use an embedded expression in an XML comment literal because the embedded expression delimiters are valid XML comment content.</span></span>  
  
- <span data-ttu-id="412cd-122">`content`"-->" değerini IÇEREMEDIĞINDEN XML açıklama bölümleri iç içe geçirilemez.</span><span class="sxs-lookup"><span data-stu-id="412cd-122">XML comment sections cannot be nested, because `content` cannot contain the value "-->".</span></span>  
  
 <span data-ttu-id="412cd-123">Bir değişkene bir XML açıklama sabit değeri atayabilir veya onu bir XML öğesi değişmez değerine dahil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="412cd-123">You can assign an XML comment literal to a variable, or you can include it in an XML element literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="412cd-124">Bir XML sabit değeri, satır devamlılık karakterleri kullanmadan birden fazla satıra yayılabilir.</span><span class="sxs-lookup"><span data-stu-id="412cd-124">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="412cd-125">Bu özellik bir XML belgesinden içerik kopyalamanızı ve bunu doğrudan bir Visual Basic programına yapıştırmayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="412cd-125">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="412cd-126">Visual Basic derleyici, XML açıklama değişmez değerini oluşturucuya bir çağrıya dönüştürür <xref:System.Xml.Linq.XComment.%23ctor%2A> .</span><span class="sxs-lookup"><span data-stu-id="412cd-126">The Visual Basic compiler converts the XML comment literal to a call to the <xref:System.Xml.Linq.XComment.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="412cd-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="412cd-127">Example</span></span>  

 <span data-ttu-id="412cd-128">Aşağıdaki örnek "This bir açıklamadır" metnini içeren bir XML açıklaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="412cd-128">The following example creates an XML comment that contains the text "This is a comment".</span></span>  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="412cd-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="412cd-129">See also</span></span>

- <xref:System.Xml.Linq.XComment>
- [<span data-ttu-id="412cd-130">XML Öğesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="412cd-130">XML Element Literal</span></span>](xml-element-literal.md)
- [<span data-ttu-id="412cd-131">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="412cd-131">XML Literals</span></span>](index.md)
- [<span data-ttu-id="412cd-132">Visual Basic'de XML Oluşturma</span><span class="sxs-lookup"><span data-stu-id="412cd-132">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
