---
description: 'Daha fazla bilgi edinin: XML CDATA değişmez değeri (Visual Basic)'
title: XML CDATA Değişmez Değeri
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
ms.openlocfilehash: d0b419954acb5a9e8ae824dbac8234e2116d09b9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768759"
---
# <a name="xml-cdata-literal-visual-basic"></a><span data-ttu-id="5effd-103">XML CDATA Değişmez Değeri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5effd-103">XML CDATA Literal (Visual Basic)</span></span>

<span data-ttu-id="5effd-104">Bir nesneyi temsil eden sabit değer <xref:System.Xml.Linq.XCData> .</span><span class="sxs-lookup"><span data-stu-id="5effd-104">A literal representing an <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5effd-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5effd-105">Syntax</span></span>  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a><span data-ttu-id="5effd-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="5effd-106">Parts</span></span>  

 `<![CDATA[`  
 <span data-ttu-id="5effd-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5effd-107">Required.</span></span> <span data-ttu-id="5effd-108">XML CDATA bölümünün başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5effd-108">Denotes the start of the XML CDATA section.</span></span>  
  
 `content`  
 <span data-ttu-id="5effd-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5effd-109">Required.</span></span> <span data-ttu-id="5effd-110">XML CDATA bölümünde görünecek metin içeriği.</span><span class="sxs-lookup"><span data-stu-id="5effd-110">Text content to appear in the XML CDATA section.</span></span>  
  
 `]]>`  
 <span data-ttu-id="5effd-111">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5effd-111">Required.</span></span> <span data-ttu-id="5effd-112">Bölümün sonunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="5effd-112">Denotes the end of the section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5effd-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5effd-113">Return Value</span></span>  

 <span data-ttu-id="5effd-114">Bir <xref:System.Xml.Linq.XCData> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="5effd-114">An <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5effd-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5effd-115">Remarks</span></span>  

 <span data-ttu-id="5effd-116">XML CDATA kısımları, kendisini içeren XML ile birlikte dahil edilmelidir, ancak ayrıştırılmaz olması gereken ham metni içerir.</span><span class="sxs-lookup"><span data-stu-id="5effd-116">XML CDATA sections contain raw text that should be included, but not parsed, with the XML that contains it.</span></span> <span data-ttu-id="5effd-117">Bir XML CDATA bölümü, herhangi bir metin içerebilir.</span><span class="sxs-lookup"><span data-stu-id="5effd-117">A XML CDATA section can contain any text.</span></span> <span data-ttu-id="5effd-118">Bu, ayrılmış XML karakterleri içerir.</span><span class="sxs-lookup"><span data-stu-id="5effd-118">This includes reserved XML characters.</span></span> <span data-ttu-id="5effd-119">XML CDATA bölümü "]] >" dizisiyle biter.</span><span class="sxs-lookup"><span data-stu-id="5effd-119">The XML CDATA section ends with the sequence "]]>".</span></span> <span data-ttu-id="5effd-120">Bu, aşağıdaki noktaları gösterir:</span><span class="sxs-lookup"><span data-stu-id="5effd-120">This implies the following points:</span></span>  
  
- <span data-ttu-id="5effd-121">Gömülü ifade sınırlayıcıları geçerli XML CDATA içeriği olduğundan, bir XML CDATA değişmez değerinde gömülü bir ifade kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="5effd-121">You cannot use an embedded expression in an XML CDATA literal because the embedded expression delimiters are valid XML CDATA content.</span></span>  
  
- <span data-ttu-id="5effd-122">`content`"]] >" değerini IÇEREMEDIĞINDEN XML CDATA bölümleri iç içe geçirilemez.</span><span class="sxs-lookup"><span data-stu-id="5effd-122">XML CDATA sections cannot be nested, because `content` cannot contain the value "]]>".</span></span>  
  
 <span data-ttu-id="5effd-123">Bir değişkene bir XML CDATA sabit değeri atayabilir veya onu bir XML öğesi değişmez değerine dahil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5effd-123">You can assign an XML CDATA literal to a variable, or include it in an XML element literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5effd-124">Bir XML sabit değeri birden fazla satıra yayılabilir, ancak satır devamlılık karakterlerini kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="5effd-124">An XML literal can span multiple lines but does not use line continuation characters.</span></span> <span data-ttu-id="5effd-125">Bu sayede bir XML belgesinden içerik kopyalayabilir ve doğrudan bir Visual Basic programına yapıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5effd-125">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="5effd-126">Visual Basic derleyici, XML CDATA değişmez değerini oluşturucuya bir çağrıya dönüştürür <xref:System.Xml.Linq.XCData.%23ctor%2A> .</span><span class="sxs-lookup"><span data-stu-id="5effd-126">The Visual Basic compiler converts the XML CDATA literal to a call to the <xref:System.Xml.Linq.XCData.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5effd-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="5effd-127">Example</span></span>  

 <span data-ttu-id="5effd-128">Aşağıdaki örnek, "değişmez Etiketler içerebilir" metnini içeren bir CDATA bölümü oluşturur \<XML> .</span><span class="sxs-lookup"><span data-stu-id="5effd-128">The following example creates a CDATA section that contains the text "Can contain literal \<XML> tags".</span></span>  
  
 [!code-vb[VbXMLSamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="5effd-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5effd-129">See also</span></span>

- <xref:System.Xml.Linq.XCData>
- [<span data-ttu-id="5effd-130">XML Öğesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="5effd-130">XML Element Literal</span></span>](xml-element-literal.md)
- [<span data-ttu-id="5effd-131">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="5effd-131">XML Literals</span></span>](index.md)
- [<span data-ttu-id="5effd-132">Visual Basic'de XML Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5effd-132">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
