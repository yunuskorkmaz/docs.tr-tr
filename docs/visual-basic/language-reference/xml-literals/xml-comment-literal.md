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
ms.openlocfilehash: 96a7281cde546c3077cf15c625c6e09d2d0ee46f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624684"
---
# <a name="xml-comment-literal-visual-basic"></a><span data-ttu-id="581e5-102">XML Açıklama Değişmez Değeri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="581e5-102">XML Comment Literal (Visual Basic)</span></span>
<span data-ttu-id="581e5-103">Bir değişmez değer temsil eden bir <xref:System.Xml.Linq.XComment> nesne.</span><span class="sxs-lookup"><span data-stu-id="581e5-103">A literal representing an <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="581e5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="581e5-104">Syntax</span></span>  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a><span data-ttu-id="581e5-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="581e5-105">Parts</span></span>  
  
|<span data-ttu-id="581e5-106">Terim</span><span class="sxs-lookup"><span data-stu-id="581e5-106">Term</span></span>|<span data-ttu-id="581e5-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="581e5-107">Definition</span></span>|  
|---|---|  
|`<!--`|<span data-ttu-id="581e5-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="581e5-108">Required.</span></span> <span data-ttu-id="581e5-109">XML yorumu başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="581e5-109">Denotes the start of the XML comment.</span></span>|  
|`content`|<span data-ttu-id="581e5-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="581e5-110">Required.</span></span> <span data-ttu-id="581e5-111">XML açıklamasında görüntülenecek metin.</span><span class="sxs-lookup"><span data-stu-id="581e5-111">Text to appear in the XML comment.</span></span> <span data-ttu-id="581e5-112">İki kısa çizgi (-) veya kapanış etiketi için bitişik bir tire ile biten bir dizi içeremez.</span><span class="sxs-lookup"><span data-stu-id="581e5-112">Cannot contain a series of two hyphens (--) or end with a hyphen adjacent to the closing tag.</span></span>|  
|`-->`|<span data-ttu-id="581e5-113">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="581e5-113">Required.</span></span> <span data-ttu-id="581e5-114">XML yorumu sonunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="581e5-114">Denotes the end of the XML comment.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="581e5-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="581e5-115">Return Value</span></span>  
 <span data-ttu-id="581e5-116">Bir <xref:System.Xml.Linq.XComment> nesne.</span><span class="sxs-lookup"><span data-stu-id="581e5-116">An <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="581e5-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="581e5-117">Remarks</span></span>  
 <span data-ttu-id="581e5-118">XML açıklama değişmez değerleri, belge içeriğini içermez; Belge hakkındaki bilgileri içerirler.</span><span class="sxs-lookup"><span data-stu-id="581e5-118">XML comment literals do not contain document content; they contain information about the document.</span></span> <span data-ttu-id="581e5-119">XML açıklama bölümü dizisi "--> ile" sona erer.</span><span class="sxs-lookup"><span data-stu-id="581e5-119">The XML comment section ends with the sequence "-->".</span></span> <span data-ttu-id="581e5-120">Bu, aşağıdaki noktaları anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="581e5-120">This implies the following points:</span></span>  
  
-   <span data-ttu-id="581e5-121">Gömülü ifade sınırlayıcılar geçerli XML yorumu içerik olduğundan, bir katıştırılmış deyim bir XML açıklama değişmez değeri kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="581e5-121">You cannot use an embedded expression in an XML comment literal because the embedded expression delimiters are valid XML comment content.</span></span>  
  
-   <span data-ttu-id="581e5-122">XML açıklama bölümleri iç içe geçirilemez, çünkü `content` değeri içeremez "-->".</span><span class="sxs-lookup"><span data-stu-id="581e5-122">XML comment sections cannot be nested, because `content` cannot contain the value "-->".</span></span>  
  
 <span data-ttu-id="581e5-123">Bir XML açıklama değişmez değeri bir değişkene atayın ya da bir XML öğesi değişmez değeri içerir.</span><span class="sxs-lookup"><span data-stu-id="581e5-123">You can assign an XML comment literal to a variable, or you can include it in an XML element literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="581e5-124">XML değişmez değer birden fazla satır, satır devamlılığı karakteri kullanmadan yayılabilir.</span><span class="sxs-lookup"><span data-stu-id="581e5-124">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="581e5-125">Bu özellik, bir XML belgesinden içeriği kopyalayın ve doğrudan bir Visual Basic programına yapıştırın sağlar.</span><span class="sxs-lookup"><span data-stu-id="581e5-125">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="581e5-126">XML açıklama değişmez değer Visual Basic Derleyicisi için bir çağrı dönüştürür <xref:System.Xml.Linq.XComment.%23ctor%2A> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="581e5-126">The Visual Basic compiler converts the XML comment literal to a call to the <xref:System.Xml.Linq.XComment.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="581e5-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="581e5-127">Example</span></span>  
 <span data-ttu-id="581e5-128">Aşağıdaki örnek, "Bu bir açıklamadır" metni içeren bir XML yorumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="581e5-128">The following example creates an XML comment that contains the text "This is a comment".</span></span>  
  
 [!code-vb[VbXMLSamples#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-comment-literal_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="581e5-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="581e5-129">See also</span></span>
- <xref:System.Xml.Linq.XComment>
- [<span data-ttu-id="581e5-130">XML Öğesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="581e5-130">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="581e5-131">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="581e5-131">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="581e5-132">Visual Basic'de XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="581e5-132">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
