---
title: XML CDATA Değişmez Değeri (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
ms.openlocfilehash: 999531d8146748fe491255663f0d2d17d056bcd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603840"
---
# <a name="xml-cdata-literal-visual-basic"></a><span data-ttu-id="9e4a3-102">XML CDATA Değişmez Değeri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e4a3-102">XML CDATA Literal (Visual Basic)</span></span>
<span data-ttu-id="9e4a3-103">Değişmez değer gösteren bir <xref:System.Xml.Linq.XCData> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-103">A literal representing an <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e4a3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9e4a3-104">Syntax</span></span>  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a><span data-ttu-id="9e4a3-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="9e4a3-105">Parts</span></span>  
 `<![CDATA[`  
 <span data-ttu-id="9e4a3-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-106">Required.</span></span> <span data-ttu-id="9e4a3-107">XML CDATA bölümünün başlangıç gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-107">Denotes the start of the XML CDATA section.</span></span>  
  
 `content`  
 <span data-ttu-id="9e4a3-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-108">Required.</span></span> <span data-ttu-id="9e4a3-109">XML CDATA bölümünde görüntülenecek metin içeriği.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-109">Text content to appear in the XML CDATA section.</span></span>  
  
 `]]>`  
 <span data-ttu-id="9e4a3-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-110">Required.</span></span> <span data-ttu-id="9e4a3-111">Bölümün sonuna gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-111">Denotes the end of the section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9e4a3-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9e4a3-112">Return Value</span></span>  
 <span data-ttu-id="9e4a3-113">Bir <xref:System.Xml.Linq.XCData> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-113">An <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e4a3-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9e4a3-114">Remarks</span></span>  
 <span data-ttu-id="9e4a3-115">XML CDATA bölümler dahil, ancak, içerdiği XML çözümlenmemiş ham metni içerir.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-115">XML CDATA sections contain raw text that should be included, but not parsed, with the XML that contains it.</span></span> <span data-ttu-id="9e4a3-116">XML CDATA bölümünde herhangi bir metin içerebilir.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-116">A XML CDATA section can contain any text.</span></span> <span data-ttu-id="9e4a3-117">Bu ayrılmış XML karakterleri içerir.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-117">This includes reserved XML characters.</span></span> <span data-ttu-id="9e4a3-118">XML CDATA bölümü dizisi ile biten "]] >".</span><span class="sxs-lookup"><span data-stu-id="9e4a3-118">The XML CDATA section ends with the sequence "]]>".</span></span> <span data-ttu-id="9e4a3-119">Bu, aşağıdaki noktaları anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="9e4a3-119">This implies the following points:</span></span>  
  
-   <span data-ttu-id="9e4a3-120">Katıştırılmış ifade sınırlayıcıları geçerli XML CDATA içerik olduğundan, bir XML CDATA değişmez değer katıştırılmış bir ifade kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-120">You cannot use an embedded expression in an XML CDATA literal because the embedded expression delimiters are valid XML CDATA content.</span></span>  
  
-   <span data-ttu-id="9e4a3-121">XML CDATA bölümleri iç içe geçirilemez, çünkü `content` değer içeremez "]] >".</span><span class="sxs-lookup"><span data-stu-id="9e4a3-121">XML CDATA sections cannot be nested, because `content` cannot contain the value "]]>".</span></span>  
  
 <span data-ttu-id="9e4a3-122">Bir XML CDATA değişmez değer bir değişkene atayın veya bir XML öğesi değişmez değeri içerir.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-122">You can assign an XML CDATA literal to a variable, or include it in an XML element literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e4a3-123">XML değişmez değer birden çok satıra yayılmış olabilir ancak satır devamlılığı karakterleri kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-123">An XML literal can span multiple lines but does not use line continuation characters.</span></span> <span data-ttu-id="9e4a3-124">Bu, bir XML belgesinden içeriği Kopyala ve doğrudan bir Visual Basic programa yapıştırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-124">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="9e4a3-125">Visual Basic derleyici yapılan bir çağrı XML CDATA değişmez değer dönüştürür <xref:System.Xml.Linq.XCData.%23ctor%2A> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-125">The Visual Basic compiler converts the XML CDATA literal to a call to the <xref:System.Xml.Linq.XCData.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e4a3-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e4a3-126">Example</span></span>  
 <span data-ttu-id="9e4a3-127">Aşağıdaki örnek metin içeren bir CDATA bölümü oluşturur "değişmez değer içerebilir \<XML > etiketleri".</span><span class="sxs-lookup"><span data-stu-id="9e4a3-127">The following example creates a CDATA section that contains the text "Can contain literal \<XML> tags".</span></span>  
  
 [!code-vb[VbXMLSamples#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-cdata-literal_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9e4a3-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-128">See Also</span></span>  
 <xref:System.Xml.Linq.XCData>  
 [<span data-ttu-id="9e4a3-129">XML Öğesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="9e4a3-129">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="9e4a3-130">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="9e4a3-130">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="9e4a3-131">Visual Basic'de XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="9e4a3-131">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
