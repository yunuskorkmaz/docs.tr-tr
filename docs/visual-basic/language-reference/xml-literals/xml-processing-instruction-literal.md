---
description: 'Hakkında daha fazla bilgi edinin: XML Işleme yönergesi değişmez değeri (Visual Basic)'
title: XML İşleme Talimatı Değişmez Değeri
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
ms.openlocfilehash: 5037aab343cbe50ebc48614991e96da8198a481f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787532"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a><span data-ttu-id="af223-103">XML İşleme Talimatı Değişmez Değeri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af223-103">XML Processing Instruction Literal (Visual Basic)</span></span>

<span data-ttu-id="af223-104">Bir nesneyi temsil eden sabit değer <xref:System.Xml.Linq.XProcessingInstruction> .</span><span class="sxs-lookup"><span data-stu-id="af223-104">A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af223-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="af223-105">Syntax</span></span>  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a><span data-ttu-id="af223-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="af223-106">Parts</span></span>  

 `<?`  
 <span data-ttu-id="af223-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="af223-107">Required.</span></span> <span data-ttu-id="af223-108">XML işleme yönergesi sabit değerinin başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="af223-108">Denotes the start of the XML processing instruction literal.</span></span>  
  
 `piName`  
 <span data-ttu-id="af223-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="af223-109">Required.</span></span> <span data-ttu-id="af223-110">İşleme yönergesinin hangi uygulamayı hedeflediğini belirten ad.</span><span class="sxs-lookup"><span data-stu-id="af223-110">Name indicating which application the processing instruction targets.</span></span> <span data-ttu-id="af223-111">"Xml" veya "XML" ile başlayamaz.</span><span class="sxs-lookup"><span data-stu-id="af223-111">Cannot begin with "xml" or "XML".</span></span>  
  
 `piData`  
 <span data-ttu-id="af223-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="af223-112">Optional.</span></span> <span data-ttu-id="af223-113">Tarafından hedeflenen uygulamanın `piName` XML belgesini işlemesi gerektiğini belirten dize.</span><span class="sxs-lookup"><span data-stu-id="af223-113">String indicating how the application targeted by `piName` should process the XML document.</span></span>  
  
 `?>`  
 <span data-ttu-id="af223-114">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="af223-114">Required.</span></span> <span data-ttu-id="af223-115">İşleme yönergesinin sonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="af223-115">Denotes the end of the processing instruction.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="af223-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="af223-116">Return Value</span></span>  

 <span data-ttu-id="af223-117">Bir <xref:System.Xml.Linq.XProcessingInstruction> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="af223-117">An <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af223-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="af223-118">Remarks</span></span>  

 <span data-ttu-id="af223-119">XML işleme yönergesi sabit değerleri, uygulamaların bir XML belgesini nasıl işleyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="af223-119">XML processing instruction literals indicate how applications should process an XML document.</span></span> <span data-ttu-id="af223-120">Bir uygulama bir XML belgesi yüklediğinde, uygulama, belgeyi nasıl işleyeceğini belirleyebilmek için XML işleme talimatlarını denetleyebilir.</span><span class="sxs-lookup"><span data-stu-id="af223-120">When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document.</span></span> <span data-ttu-id="af223-121">Uygulama, ve anlamını Yorumlar `piName` `piData` .</span><span class="sxs-lookup"><span data-stu-id="af223-121">The application interprets the meaning of `piName` and `piData`.</span></span>  
  
 <span data-ttu-id="af223-122">XML belgesi değişmez değeri, XML işleme yönergesinden benzer bir sözdizimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="af223-122">The XML document literal uses syntax that is similar to that of the XML processing instruction.</span></span> <span data-ttu-id="af223-123">Daha fazla bilgi için bkz. [XML belgesi değişmez değeri](xml-document-literal.md).</span><span class="sxs-lookup"><span data-stu-id="af223-123">For more information, see [XML Document Literal](xml-document-literal.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="af223-124">`piName`Xml 1,0 belirtimi Bu tanımlayıcıları ayırdığından, öğe "xml" veya "xml" dizeleriyle başlayamaz.</span><span class="sxs-lookup"><span data-stu-id="af223-124">The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.</span></span>  
  
 <span data-ttu-id="af223-125">Bir değişkene XML işlem yönergesi sabit değeri atayabilir veya onu bir XML belge değişmez değerine ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af223-125">You can assign an XML processing instruction literal to a variable or include it in an XML document literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="af223-126">Bir XML sabit değeri, satır devamlılık karakterlerine gerek duymadan birden çok satıra yayılabilir.</span><span class="sxs-lookup"><span data-stu-id="af223-126">An XML literal can span multiple lines without needing line continuation characters.</span></span> <span data-ttu-id="af223-127">Bu sayede bir XML belgesinden içerik kopyalayabilir ve doğrudan bir Visual Basic programına yapıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af223-127">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="af223-128">Visual Basic Derleyicisi, XML işleme yönerge hazır değerini oluşturucuya bir çağrıya dönüştürür <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> .</span><span class="sxs-lookup"><span data-stu-id="af223-128">The Visual Basic compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af223-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="af223-129">Example</span></span>  

 <span data-ttu-id="af223-130">Aşağıdaki örnek, bir XML belgesi için stil sayfası tanımlayan bir işleme yönergesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="af223-130">The following example creates a processing instruction identifying a style-sheet for an XML document.</span></span>  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="af223-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af223-131">See also</span></span>

- <xref:System.Xml.Linq.XProcessingInstruction>
- [<span data-ttu-id="af223-132">XML Belgesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="af223-132">XML Document Literal</span></span>](xml-document-literal.md)
- [<span data-ttu-id="af223-133">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="af223-133">XML Literals</span></span>](index.md)
- [<span data-ttu-id="af223-134">Visual Basic'de XML Oluşturma</span><span class="sxs-lookup"><span data-stu-id="af223-134">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
