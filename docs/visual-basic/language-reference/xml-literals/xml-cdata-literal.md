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
# <a name="xml-cdata-literal-visual-basic"></a><span data-ttu-id="2e0f8-102">XML CDATA Değişmez Değeri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e0f8-102">XML CDATA Literal (Visual Basic)</span></span>
<span data-ttu-id="2e0f8-103"><xref:System.Xml.Linq.XCData> nesnesini temsil eden bir sabit değer.</span><span class="sxs-lookup"><span data-stu-id="2e0f8-103">A literal representing an <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e0f8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2e0f8-104">Syntax</span></span>  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a><span data-ttu-id="2e0f8-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="2e0f8-105">Parts</span></span>  
 `<![CDATA[`  
 <span data-ttu-id="2e0f8-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="2e0f8-106">Required.</span></span> <span data-ttu-id="2e0f8-107">XML CDATA bölümünün başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2e0f8-107">Denotes the start of the XML CDATA section.</span></span>  
  
 `content`  
 <span data-ttu-id="2e0f8-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="2e0f8-108">Required.</span></span> <span data-ttu-id="2e0f8-109">XML CDATA bölümünde görünecek metin içeriği.</span><span class="sxs-lookup"><span data-stu-id="2e0f8-109">Text content to appear in the XML CDATA section.</span></span>  
  
 `]]>`  
 <span data-ttu-id="2e0f8-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="2e0f8-110">Required.</span></span> <span data-ttu-id="2e0f8-111">Bölümün sonunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="2e0f8-111">Denotes the end of the section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2e0f8-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2e0f8-112">Return Value</span></span>  
 <span data-ttu-id="2e0f8-113"><xref:System.Xml.Linq.XCData> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="2e0f8-113">An <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e0f8-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2e0f8-114">Remarks</span></span>  
 <span data-ttu-id="2e0f8-115">XML CDATA kısımları, kendisini içeren XML ile birlikte dahil edilmelidir, ancak ayrıştırılmaz olması gereken ham metni içerir.</span><span class="sxs-lookup"><span data-stu-id="2e0f8-115">XML CDATA sections contain raw text that should be included, but not parsed, with the XML that contains it.</span></span> <span data-ttu-id="2e0f8-116">Bir XML CDATA bölümü, herhangi bir metin içerebilir.</span><span class="sxs-lookup"><span data-stu-id="2e0f8-116">A XML CDATA section can contain any text.</span></span> <span data-ttu-id="2e0f8-117">Bu, ayrılmış XML karakterleri içerir.</span><span class="sxs-lookup"><span data-stu-id="2e0f8-117">This includes reserved XML characters.</span></span> <span data-ttu-id="2e0f8-118">XML CDATA bölümü "]] >" dizisiyle biter.</span><span class="sxs-lookup"><span data-stu-id="2e0f8-118">The XML CDATA section ends with the sequence "]]>".</span></span> <span data-ttu-id="2e0f8-119">Bu, aşağıdaki noktaları gösterir:</span><span class="sxs-lookup"><span data-stu-id="2e0f8-119">This implies the following points:</span></span>  
  
- <span data-ttu-id="2e0f8-120">Gömülü ifade sınırlayıcıları geçerli XML CDATA içeriği olduğundan, bir XML CDATA değişmez değerinde gömülü bir ifade kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="2e0f8-120">You cannot use an embedded expression in an XML CDATA literal because the embedded expression delimiters are valid XML CDATA content.</span></span>  
  
- <span data-ttu-id="2e0f8-121">`content` "]] >" değerini içeremediğinden, XML CDATA bölümleri iç içe geçirilemez.</span><span class="sxs-lookup"><span data-stu-id="2e0f8-121">XML CDATA sections cannot be nested, because `content` cannot contain the value "]]>".</span></span>  
  
 <span data-ttu-id="2e0f8-122">Bir değişkene bir XML CDATA sabit değeri atayabilir veya onu bir XML öğesi değişmez değerine dahil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e0f8-122">You can assign an XML CDATA literal to a variable, or include it in an XML element literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2e0f8-123">Bir XML sabit değeri birden fazla satıra yayılabilir, ancak satır devamlılık karakterlerini kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="2e0f8-123">An XML literal can span multiple lines but does not use line continuation characters.</span></span> <span data-ttu-id="2e0f8-124">Bu sayede bir XML belgesinden içerik kopyalayabilir ve doğrudan bir Visual Basic programına yapıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e0f8-124">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="2e0f8-125">Visual Basic derleyici, XML CDATA değişmez değerini <xref:System.Xml.Linq.XCData.%23ctor%2A> oluşturucusuna bir çağrıya dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="2e0f8-125">The Visual Basic compiler converts the XML CDATA literal to a call to the <xref:System.Xml.Linq.XCData.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e0f8-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="2e0f8-126">Example</span></span>  
 <span data-ttu-id="2e0f8-127">Aşağıdaki örnek, "değişmez \<XML > etiketleri içerebilir" metnini içeren bir CDATA bölümü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2e0f8-127">The following example creates a CDATA section that contains the text "Can contain literal \<XML> tags".</span></span>  
  
 [!code-vb[VbXMLSamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="2e0f8-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e0f8-128">See also</span></span>

- <xref:System.Xml.Linq.XCData>
- [<span data-ttu-id="2e0f8-129">XML Öğesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="2e0f8-129">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="2e0f8-130">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="2e0f8-130">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="2e0f8-131">Visual Basic XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="2e0f8-131">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
