---
title: XML Açıklama Değişmez Değeri (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
ms.openlocfilehash: 60c354215c627683fd6c69d9ca66fc115c26ccda
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603944"
---
# <a name="xml-comment-literal-visual-basic"></a><span data-ttu-id="10113-102">XML Açıklama Değişmez Değeri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10113-102">XML Comment Literal (Visual Basic)</span></span>
<span data-ttu-id="10113-103">Değişmez değer gösteren bir <xref:System.Xml.Linq.XComment> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="10113-103">A literal representing an <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10113-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="10113-104">Syntax</span></span>  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a><span data-ttu-id="10113-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="10113-105">Parts</span></span>  
  
|<span data-ttu-id="10113-106">Terim</span><span class="sxs-lookup"><span data-stu-id="10113-106">Term</span></span>|<span data-ttu-id="10113-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="10113-107">Definition</span></span>|  
|---|---|  
|`<!--`|<span data-ttu-id="10113-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="10113-108">Required.</span></span> <span data-ttu-id="10113-109">XML açıklama başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="10113-109">Denotes the start of the XML comment.</span></span>|  
|`content`|<span data-ttu-id="10113-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="10113-110">Required.</span></span> <span data-ttu-id="10113-111">XML açıklama görüntülenecek metin.</span><span class="sxs-lookup"><span data-stu-id="10113-111">Text to appear in the XML comment.</span></span> <span data-ttu-id="10113-112">İki kısa çizgi (-) veya kapanış etiketi bitişik bir tire ile biten bir dizi içeremez.</span><span class="sxs-lookup"><span data-stu-id="10113-112">Cannot contain a series of two hyphens (--) or end with a hyphen adjacent to the closing tag.</span></span>|  
|`-->`|<span data-ttu-id="10113-113">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="10113-113">Required.</span></span> <span data-ttu-id="10113-114">XML açıklama sonunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="10113-114">Denotes the end of the XML comment.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="10113-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="10113-115">Return Value</span></span>  
 <span data-ttu-id="10113-116">Bir <xref:System.Xml.Linq.XComment> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="10113-116">An <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10113-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="10113-117">Remarks</span></span>  
 <span data-ttu-id="10113-118">XML açıklama değişmez değerleri belgesinin içeriği içermez; Belge hakkındaki bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="10113-118">XML comment literals do not contain document content; they contain information about the document.</span></span> <span data-ttu-id="10113-119">XML açıklama bölümüne sona erer sırası "--> ile".</span><span class="sxs-lookup"><span data-stu-id="10113-119">The XML comment section ends with the sequence "-->".</span></span> <span data-ttu-id="10113-120">Bu, aşağıdaki noktaları anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="10113-120">This implies the following points:</span></span>  
  
-   <span data-ttu-id="10113-121">Katıştırılmış ifade sınırlayıcıları geçerli XML açıklama içerik olduğundan, bir XML açıklama değişmez değer katıştırılmış bir ifade kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="10113-121">You cannot use an embedded expression in an XML comment literal because the embedded expression delimiters are valid XML comment content.</span></span>  
  
-   <span data-ttu-id="10113-122">XML açıklama bölümleri iç içe geçirilemez, çünkü `content` değer içeremez "-->".</span><span class="sxs-lookup"><span data-stu-id="10113-122">XML comment sections cannot be nested, because `content` cannot contain the value "-->".</span></span>  
  
 <span data-ttu-id="10113-123">Bir değişkene bir XML açıklama değişmez değer atayabilir veya bir XML öğesi değişmez değeri içerir.</span><span class="sxs-lookup"><span data-stu-id="10113-123">You can assign an XML comment literal to a variable, or you can include it in an XML element literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="10113-124">XML değişmez değer, satır devamlılığı karakterleri kullanmadan birden fazla satır yayılabilir.</span><span class="sxs-lookup"><span data-stu-id="10113-124">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="10113-125">Bu özellik, bir XML belgesinden içeriği Kopyala ve doğrudan bir Visual Basic programa yapıştırmak sağlar.</span><span class="sxs-lookup"><span data-stu-id="10113-125">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="10113-126">Visual Basic derleyici yapılan bir çağrı XML açıklama değişmez değer dönüştürür <xref:System.Xml.Linq.XComment.%23ctor%2A> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="10113-126">The Visual Basic compiler converts the XML comment literal to a call to the <xref:System.Xml.Linq.XComment.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10113-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="10113-127">Example</span></span>  
 <span data-ttu-id="10113-128">Aşağıdaki örnekte, "Bu bir açıklamadır" metnini içeren bir XML açıklama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="10113-128">The following example creates an XML comment that contains the text "This is a comment".</span></span>  
  
 [!code-vb[VbXMLSamples#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-comment-literal_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="10113-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="10113-129">See Also</span></span>  
 <xref:System.Xml.Linq.XComment>  
 [<span data-ttu-id="10113-130">XML Öğesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="10113-130">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="10113-131">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="10113-131">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="10113-132">Visual Basic'de XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="10113-132">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
