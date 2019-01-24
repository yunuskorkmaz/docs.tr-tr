---
title: XML İşleme Talimatı Değişmez Değeri (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
ms.openlocfilehash: cb9ad1d687203dff497e4cd451933a8bbbdf4bf6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491239"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a><span data-ttu-id="240c0-102">XML İşleme Talimatı Değişmez Değeri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="240c0-102">XML Processing Instruction Literal (Visual Basic)</span></span>
<span data-ttu-id="240c0-103">Bir değişmez değer temsil eden bir <xref:System.Xml.Linq.XProcessingInstruction> nesne.</span><span class="sxs-lookup"><span data-stu-id="240c0-103">A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="240c0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="240c0-104">Syntax</span></span>  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a><span data-ttu-id="240c0-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="240c0-105">Parts</span></span>  
 `<?`  
 <span data-ttu-id="240c0-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="240c0-106">Required.</span></span> <span data-ttu-id="240c0-107">XML işleme yönergesi değişmez değeri başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="240c0-107">Denotes the start of the XML processing instruction literal.</span></span>  
  
 `piName`  
 <span data-ttu-id="240c0-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="240c0-108">Required.</span></span> <span data-ttu-id="240c0-109">Hangi uygulamayı gösteren işleme yönergesi hedefleri adlandırın.</span><span class="sxs-lookup"><span data-stu-id="240c0-109">Name indicating which application the processing instruction targets.</span></span> <span data-ttu-id="240c0-110">"Xml" veya "XML" ile başlayamaz.</span><span class="sxs-lookup"><span data-stu-id="240c0-110">Cannot begin with "xml" or "XML".</span></span>  
  
 `piData`  
 <span data-ttu-id="240c0-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="240c0-111">Optional.</span></span> <span data-ttu-id="240c0-112">Uygulamayı nasıl hedeflenen belirten bir dize `piName` XML belgesi işlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="240c0-112">String indicating how the application targeted by `piName` should process the XML document.</span></span>  
  
 `?>`  
 <span data-ttu-id="240c0-113">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="240c0-113">Required.</span></span> <span data-ttu-id="240c0-114">İşleme yönergenin bitiminden gösterir.</span><span class="sxs-lookup"><span data-stu-id="240c0-114">Denotes the end of the processing instruction.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="240c0-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="240c0-115">Return Value</span></span>  
 <span data-ttu-id="240c0-116">Bir <xref:System.Xml.Linq.XProcessingInstruction> nesne.</span><span class="sxs-lookup"><span data-stu-id="240c0-116">An <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="240c0-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="240c0-117">Remarks</span></span>  
 <span data-ttu-id="240c0-118">XML işleme talimatı değişmez değerleri, bir XML belgesi uygulamaları nasıl işleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="240c0-118">XML processing instruction literals indicate how applications should process an XML document.</span></span> <span data-ttu-id="240c0-119">Bir XML belgesi bir uygulama yüklendiğinde uygulama belgeyi işlemek nasıl belirlemek için XML işleme yönergeleri kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="240c0-119">When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document.</span></span> <span data-ttu-id="240c0-120">Uygulama anlamını yorumlar `piName` ve `piData`.</span><span class="sxs-lookup"><span data-stu-id="240c0-120">The application interprets the meaning of `piName` and `piData`.</span></span>  
  
 <span data-ttu-id="240c0-121">XML belgesi değişmez değeri XML işlem yönergesi için benzer bir sözdizimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="240c0-121">The XML document literal uses syntax that is similar to that of the XML processing instruction.</span></span> <span data-ttu-id="240c0-122">Daha fazla bilgi için [XML belgesi değişmez değeri](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span><span class="sxs-lookup"><span data-stu-id="240c0-122">For more information, see [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="240c0-123">`piName` Öğesi başlayamaz dizeleri "xml" veya "XML" ile XML 1.0 belirtimi bu tanımlayıcıları ayırdığından.</span><span class="sxs-lookup"><span data-stu-id="240c0-123">The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.</span></span>  
  
 <span data-ttu-id="240c0-124">Bir XML işleme yönergesi değişmez değeri bir değişkene atayın ya da bir XML belgesi değişmez değeri içerir.</span><span class="sxs-lookup"><span data-stu-id="240c0-124">You can assign an XML processing instruction literal to a variable or include it in an XML document literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="240c0-125">Bir XML değişmez değeri birden fazla satır, satır devamlılığı karakteri gerek kalmadan yayılabilir.</span><span class="sxs-lookup"><span data-stu-id="240c0-125">An XML literal can span multiple lines without needing line continuation characters.</span></span> <span data-ttu-id="240c0-126">Bu içerik bir XML belgesinden kopyalayıp bir Visual Basic programa doğrudan yapıştırın olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="240c0-126">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="240c0-127">Visual Basic Derleyicisi için bir çağrı XML işleme yönergesi değişmez değeri dönüştürür <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="240c0-127">The Visual Basic compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="240c0-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="240c0-128">Example</span></span>  
 <span data-ttu-id="240c0-129">Aşağıdaki örnek, bir XML belgesi için bir stil sayfası tanımlayan bir işlem yönergesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="240c0-129">The following example creates a processing instruction identifying a style-sheet for an XML document.</span></span>  
  
 [!code-vb[VbXMLSamples#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-processing-instruction-literal_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="240c0-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="240c0-130">See also</span></span>
- <xref:System.Xml.Linq.XProcessingInstruction>
- [<span data-ttu-id="240c0-131">XML Belgesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="240c0-131">XML Document Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [<span data-ttu-id="240c0-132">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="240c0-132">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="240c0-133">Visual Basic'de XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="240c0-133">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
