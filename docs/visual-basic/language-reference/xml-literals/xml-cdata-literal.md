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
ms.openlocfilehash: 889ec7f93d0503edac51652dda217c6a9f654f9b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64621428"
---
# <a name="xml-cdata-literal-visual-basic"></a><span data-ttu-id="b3e12-102">XML CDATA Değişmez Değeri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3e12-102">XML CDATA Literal (Visual Basic)</span></span>
<span data-ttu-id="b3e12-103">Bir değişmez değer temsil eden bir <xref:System.Xml.Linq.XCData> nesne.</span><span class="sxs-lookup"><span data-stu-id="b3e12-103">A literal representing an <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3e12-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b3e12-104">Syntax</span></span>  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a><span data-ttu-id="b3e12-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="b3e12-105">Parts</span></span>  
 `<![CDATA[`  
 <span data-ttu-id="b3e12-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="b3e12-106">Required.</span></span> <span data-ttu-id="b3e12-107">XML CDATA bölümü başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b3e12-107">Denotes the start of the XML CDATA section.</span></span>  
  
 `content`  
 <span data-ttu-id="b3e12-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="b3e12-108">Required.</span></span> <span data-ttu-id="b3e12-109">XML CDATA bölümde görüntülenecek metin içeriği.</span><span class="sxs-lookup"><span data-stu-id="b3e12-109">Text content to appear in the XML CDATA section.</span></span>  
  
 `]]>`  
 <span data-ttu-id="b3e12-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="b3e12-110">Required.</span></span> <span data-ttu-id="b3e12-111">Bölümün sonuna gösterir.</span><span class="sxs-lookup"><span data-stu-id="b3e12-111">Denotes the end of the section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b3e12-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b3e12-112">Return Value</span></span>  
 <span data-ttu-id="b3e12-113">Bir <xref:System.Xml.Linq.XCData> nesne.</span><span class="sxs-lookup"><span data-stu-id="b3e12-113">An <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3e12-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b3e12-114">Remarks</span></span>  
 <span data-ttu-id="b3e12-115">XML CDATA bölümler dahil, ancak, içerdiği XML çözümlenmemiş ham metni içerir.</span><span class="sxs-lookup"><span data-stu-id="b3e12-115">XML CDATA sections contain raw text that should be included, but not parsed, with the XML that contains it.</span></span> <span data-ttu-id="b3e12-116">XML CDATA bölümü herhangi bir metin içerebilir.</span><span class="sxs-lookup"><span data-stu-id="b3e12-116">A XML CDATA section can contain any text.</span></span> <span data-ttu-id="b3e12-117">Bu, ayrılmış XML karakterlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="b3e12-117">This includes reserved XML characters.</span></span> <span data-ttu-id="b3e12-118">XML CDATA bölümü dizisi ile biter "]] >".</span><span class="sxs-lookup"><span data-stu-id="b3e12-118">The XML CDATA section ends with the sequence "]]>".</span></span> <span data-ttu-id="b3e12-119">Bu, aşağıdaki noktaları anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="b3e12-119">This implies the following points:</span></span>  
  
- <span data-ttu-id="b3e12-120">Gömülü ifade sınırlayıcılar geçerli XML CDATA içerik olduğundan, bir katıştırılmış deyim bir XML CDATA değişmez değeri kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="b3e12-120">You cannot use an embedded expression in an XML CDATA literal because the embedded expression delimiters are valid XML CDATA content.</span></span>  
  
- <span data-ttu-id="b3e12-121">XML CDATA kısımları iç içe geçirilemez, çünkü `content` değeri içeremez "]] >".</span><span class="sxs-lookup"><span data-stu-id="b3e12-121">XML CDATA sections cannot be nested, because `content` cannot contain the value "]]>".</span></span>  
  
 <span data-ttu-id="b3e12-122">Bir XML CDATA değişmez değeri bir değişkene atayın ya da bir XML öğesi değişmez değeri içerir.</span><span class="sxs-lookup"><span data-stu-id="b3e12-122">You can assign an XML CDATA literal to a variable, or include it in an XML element literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3e12-123">XML değişmez değer birden fazla satırı kapsayabilir ancak satır devamlılığı karakteri kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="b3e12-123">An XML literal can span multiple lines but does not use line continuation characters.</span></span> <span data-ttu-id="b3e12-124">Bu içerik bir XML belgesinden kopyalayıp bir Visual Basic programa doğrudan yapıştırın olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b3e12-124">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="b3e12-125">XML CDATA değişmez değer Visual Basic Derleyicisi için bir çağrı dönüştürür <xref:System.Xml.Linq.XCData.%23ctor%2A> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="b3e12-125">The Visual Basic compiler converts the XML CDATA literal to a call to the <xref:System.Xml.Linq.XCData.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3e12-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="b3e12-126">Example</span></span>  
 <span data-ttu-id="b3e12-127">Aşağıdaki örnek, metni içeren CDATA bölümü oluşturur. "değişmez değer içerebilir \<XML > etiketleri".</span><span class="sxs-lookup"><span data-stu-id="b3e12-127">The following example creates a CDATA section that contains the text "Can contain literal \<XML> tags".</span></span>  
  
 [!code-vb[VbXMLSamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="b3e12-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3e12-128">See also</span></span>

- <xref:System.Xml.Linq.XCData>
- [<span data-ttu-id="b3e12-129">XML Öğesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="b3e12-129">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="b3e12-130">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="b3e12-130">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="b3e12-131">Visual Basic'de XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="b3e12-131">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
