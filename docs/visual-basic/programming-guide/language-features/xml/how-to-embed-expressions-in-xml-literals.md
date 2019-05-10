---
title: 'Nasıl yapılır: (Visual Basic) XML değişmez değerlerine ifade katıştırma'
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: ca80ac666e8676e4e58a9741b00125c0126570fa
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64598386"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a><span data-ttu-id="0d427-102">Nasıl yapılır: (Visual Basic) XML değişmez değerlerine ifade katıştırma</span><span class="sxs-lookup"><span data-stu-id="0d427-102">How to: Embed Expressions in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="0d427-103">XML değişmez değerleri, bir XML belge, parça veya çalışma zamanında oluşturulan içeriği içeren bir öğe oluşturmak için katıştırılmış ifadeleri ile birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d427-103">You can combine XML literals with embedded expressions to create an XML document, fragment, or element that contains content created at run time.</span></span> <span data-ttu-id="0d427-104">Aşağıdaki örnekler, katıştırılmış ifadeler öğe içeriği, öznitelikleri ve öğe adları çalışma zamanında doldurmak için nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="0d427-104">The following examples demonstrate how to use embedded expressions to populate element content, attributes, and element names at run time.</span></span>  
  
 <span data-ttu-id="0d427-105">Katıştırılmış bir ifade sözdizimi `<%=` `exp` `%>`, aynı sözdizimini olduğu, [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] kullanır.</span><span class="sxs-lookup"><span data-stu-id="0d427-105">The syntax for an embedded expression is `<%=` `exp` `%>`, which is the same syntax that [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] uses.</span></span> <span data-ttu-id="0d427-106">Daha fazla bilgi için [XML'de katıştırılmış ifadeler](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0d427-106">For more information, see [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="0d427-107">Ayrıca [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] oluşturmak için API'ler [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesneleri.</span><span class="sxs-lookup"><span data-stu-id="0d427-107">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="0d427-108">Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="0d427-108">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="0d427-109">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="0d427-109">Procedures</span></span>  
  
#### <a name="to-insert-text-as-element-content"></a><span data-ttu-id="0d427-110">Öğe içeriği metin eklemek için</span><span class="sxs-lookup"><span data-stu-id="0d427-110">To insert text as element content</span></span>  
  
- <span data-ttu-id="0d427-111">Aşağıdaki örnekte yer alan metin eklemek gösterilmektedir `contactName` açılış ve kapanış adı öğeler arasında değişken.</span><span class="sxs-lookup"><span data-stu-id="0d427-111">The following example shows how to insert the text that is contained in the `contactName` variable between the opening and closing name elements.</span></span>  
  
     [!code-vb[VbXMLSamples#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#39)]  
  
     <span data-ttu-id="0d427-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="0d427-112">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a><span data-ttu-id="0d427-113">Bir öznitelik değeri metin eklemek için</span><span class="sxs-lookup"><span data-stu-id="0d427-113">To insert text as an attribute value</span></span>  
  
- <span data-ttu-id="0d427-114">Aşağıdaki örnekte yer alan metin eklemek gösterilmektedir `phoneType` değeri olarak değişken `type` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="0d427-114">The following example shows how to insert the text that is contained in the `phoneType` variable as the value of the `type` attribute.</span></span>  
  
     [!code-vb[VbXMLSamples#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#40)]  
  
     <span data-ttu-id="0d427-115">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="0d427-115">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a><span data-ttu-id="0d427-116">Bir öğe adı için metin eklemek için</span><span class="sxs-lookup"><span data-stu-id="0d427-116">To insert text for an element name</span></span>  
  
- <span data-ttu-id="0d427-117">Aşağıdaki örnekte yer alan metin eklemek gösterilmektedir `elementName` değişken olarak bir öğe adı.</span><span class="sxs-lookup"><span data-stu-id="0d427-117">The following example shows how to insert the text that is contained in the `elementName` variable as the name of an element.</span></span>  
  
     <span data-ttu-id="0d427-118">Bu tekniği kullanarak öğeleri oluştururken kapatmalısınız \</ > etiketi.</span><span class="sxs-lookup"><span data-stu-id="0d427-118">When creating elements by using this technique, you must close them with the \</> tag.</span></span>  
  
     [!code-vb[VbXMLSamples#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#41)]  
  
     <span data-ttu-id="0d427-119">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="0d427-119">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0d427-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d427-120">See also</span></span>

- [<span data-ttu-id="0d427-121">Nasıl yapılır: XML değişmez değerleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="0d427-121">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)
- [<span data-ttu-id="0d427-122">XML'de Katıştırılmış İfadeler</span><span class="sxs-lookup"><span data-stu-id="0d427-122">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [<span data-ttu-id="0d427-123">Visual Basic'de XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="0d427-123">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="0d427-124">XML</span><span class="sxs-lookup"><span data-stu-id="0d427-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
