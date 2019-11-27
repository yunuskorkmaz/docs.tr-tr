---
title: XML İşleme Talimatı Değişmez Değeri
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
ms.openlocfilehash: 3602a81feae9287a77d060bb46f10eefee4fc05d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347039"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a><span data-ttu-id="56e14-102">XML İşleme Talimatı Değişmez Değeri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56e14-102">XML Processing Instruction Literal (Visual Basic)</span></span>
<span data-ttu-id="56e14-103"><xref:System.Xml.Linq.XProcessingInstruction> nesnesini temsil eden bir sabit değer.</span><span class="sxs-lookup"><span data-stu-id="56e14-103">A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56e14-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="56e14-104">Syntax</span></span>  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a><span data-ttu-id="56e14-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="56e14-105">Parts</span></span>  
 `<?`  
 <span data-ttu-id="56e14-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="56e14-106">Required.</span></span> <span data-ttu-id="56e14-107">XML işleme yönergesi sabit değerinin başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="56e14-107">Denotes the start of the XML processing instruction literal.</span></span>  
  
 `piName`  
 <span data-ttu-id="56e14-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="56e14-108">Required.</span></span> <span data-ttu-id="56e14-109">İşleme yönergesinin hangi uygulamayı hedeflediğini belirten ad.</span><span class="sxs-lookup"><span data-stu-id="56e14-109">Name indicating which application the processing instruction targets.</span></span> <span data-ttu-id="56e14-110">"Xml" veya "XML" ile başlayamaz.</span><span class="sxs-lookup"><span data-stu-id="56e14-110">Cannot begin with "xml" or "XML".</span></span>  
  
 `piData`  
 <span data-ttu-id="56e14-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="56e14-111">Optional.</span></span> <span data-ttu-id="56e14-112">`piName` tarafından hedeflenen uygulamanın XML belgesini nasıl işleyeceğini belirten dize.</span><span class="sxs-lookup"><span data-stu-id="56e14-112">String indicating how the application targeted by `piName` should process the XML document.</span></span>  
  
 `?>`  
 <span data-ttu-id="56e14-113">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="56e14-113">Required.</span></span> <span data-ttu-id="56e14-114">İşleme yönergesinin sonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="56e14-114">Denotes the end of the processing instruction.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56e14-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="56e14-115">Return Value</span></span>  
 <span data-ttu-id="56e14-116"><xref:System.Xml.Linq.XProcessingInstruction> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="56e14-116">An <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56e14-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="56e14-117">Remarks</span></span>  
 <span data-ttu-id="56e14-118">XML işleme yönergesi sabit değerleri, uygulamaların bir XML belgesini nasıl işleyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="56e14-118">XML processing instruction literals indicate how applications should process an XML document.</span></span> <span data-ttu-id="56e14-119">Bir uygulama bir XML belgesi yüklediğinde, uygulama, belgeyi nasıl işleyeceğini belirleyebilmek için XML işleme talimatlarını denetleyebilir.</span><span class="sxs-lookup"><span data-stu-id="56e14-119">When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document.</span></span> <span data-ttu-id="56e14-120">Uygulama `piName` ve `piData`anlamını yorumlar.</span><span class="sxs-lookup"><span data-stu-id="56e14-120">The application interprets the meaning of `piName` and `piData`.</span></span>  
  
 <span data-ttu-id="56e14-121">XML belgesi değişmez değeri, XML işleme yönergesinden benzer bir sözdizimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="56e14-121">The XML document literal uses syntax that is similar to that of the XML processing instruction.</span></span> <span data-ttu-id="56e14-122">Daha fazla bilgi için bkz. [XML belgesi değişmez değeri](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span><span class="sxs-lookup"><span data-stu-id="56e14-122">For more information, see [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="56e14-123">XML 1,0 belirtimi Bu tanımlayıcıları ayırdığından `piName` öğesi "xml" veya "XML" dizeleriyle başlayamaz.</span><span class="sxs-lookup"><span data-stu-id="56e14-123">The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.</span></span>  
  
 <span data-ttu-id="56e14-124">Bir değişkene XML işlem yönergesi sabit değeri atayabilir veya onu bir XML belge değişmez değerine ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56e14-124">You can assign an XML processing instruction literal to a variable or include it in an XML document literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="56e14-125">Bir XML sabit değeri, satır devamlılık karakterlerine gerek duymadan birden çok satıra yayılabilir.</span><span class="sxs-lookup"><span data-stu-id="56e14-125">An XML literal can span multiple lines without needing line continuation characters.</span></span> <span data-ttu-id="56e14-126">Bu sayede bir XML belgesinden içerik kopyalayabilir ve doğrudan bir Visual Basic programına yapıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56e14-126">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="56e14-127">Visual Basic derleyici, XML işleme yönergesi sabit değerini <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> oluşturucusuna bir çağrıya dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="56e14-127">The Visual Basic compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56e14-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="56e14-128">Example</span></span>  
 <span data-ttu-id="56e14-129">Aşağıdaki örnek, bir XML belgesi için stil sayfası tanımlayan bir işleme yönergesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="56e14-129">The following example creates a processing instruction identifying a style-sheet for an XML document.</span></span>  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="56e14-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56e14-130">See also</span></span>

- <xref:System.Xml.Linq.XProcessingInstruction>
- [<span data-ttu-id="56e14-131">XML Belgesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="56e14-131">XML Document Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [<span data-ttu-id="56e14-132">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="56e14-132">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="56e14-133">Visual Basic XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="56e14-133">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
