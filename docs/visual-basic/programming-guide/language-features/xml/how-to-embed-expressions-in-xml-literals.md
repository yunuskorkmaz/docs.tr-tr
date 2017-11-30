---
title: "Nasıl yapılır: XML Değişmez Değerlerine İfade Katıştırma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bef4662d69ca7ceddeb2641cbe265d93712c5d16
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a><span data-ttu-id="40d68-102">Nasıl yapılır: XML Değişmez Değerlerine İfade Katıştırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40d68-102">How to: Embed Expressions in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="40d68-103">XML değişmez değerleri, bir XML belgesi, parça veya çalışma zamanında oluşturulmuş içeriğe öğesi oluşturmak için katıştırılmış ifadeler ile birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40d68-103">You can combine XML literals with embedded expressions to create an XML document, fragment, or element that contains content created at run time.</span></span> <span data-ttu-id="40d68-104">Aşağıdaki örnekler katıştırılmış ifadeler öğe içeriği, öznitelikleri ve öğe adları çalışma zamanında doldurmak için nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="40d68-104">The following examples demonstrate how to use embedded expressions to populate element content, attributes, and element names at run time.</span></span>  
  
 <span data-ttu-id="40d68-105">Katıştırılmış bir ifade sözdizimi `<%=` `exp` `%>`, aynı sözdizimini olduğu, [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] kullanır.</span><span class="sxs-lookup"><span data-stu-id="40d68-105">The syntax for an embedded expression is `<%=` `exp` `%>`, which is the same syntax that [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] uses.</span></span> <span data-ttu-id="40d68-106">Daha fazla bilgi için bkz: [XML'de katıştırılmış ifadeler](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="40d68-106">For more information, see [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="40d68-107">Aynı zamanda [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] oluşturmak için API'lerini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesneleri.</span><span class="sxs-lookup"><span data-stu-id="40d68-107">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="40d68-108">Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="40d68-108">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="40d68-109">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="40d68-109">Procedures</span></span>  
  
#### <a name="to-insert-text-as-element-content"></a><span data-ttu-id="40d68-110">Metin öğe içeriği eklemek için</span><span class="sxs-lookup"><span data-stu-id="40d68-110">To insert text as element content</span></span>  
  
-   <span data-ttu-id="40d68-111">Aşağıdaki örnekte yer metin eklemek gösterilmiştir `contactName` açma ve kapatma adı öğeler arasında değişken.</span><span class="sxs-lookup"><span data-stu-id="40d68-111">The following example shows how to insert the text that is contained in the `contactName` variable between the opening and closing name elements.</span></span>  
  
     [!code-vb[VbXMLSamples#39](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_1.vb)]  
  
     <span data-ttu-id="40d68-112">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="40d68-112">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a><span data-ttu-id="40d68-113">Öznitelik değeri olarak metin eklemek için</span><span class="sxs-lookup"><span data-stu-id="40d68-113">To insert text as an attribute value</span></span>  
  
-   <span data-ttu-id="40d68-114">Aşağıdaki örnekte yer metin eklemek gösterilmiştir `phoneType` değeri olarak değişken `type` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="40d68-114">The following example shows how to insert the text that is contained in the `phoneType` variable as the value of the `type` attribute.</span></span>  
  
     [!code-vb[VbXMLSamples#40](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_2.vb)]  
  
     <span data-ttu-id="40d68-115">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="40d68-115">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a><span data-ttu-id="40d68-116">Bir öğe adı için metin eklemek için</span><span class="sxs-lookup"><span data-stu-id="40d68-116">To insert text for an element name</span></span>  
  
-   <span data-ttu-id="40d68-117">Aşağıdaki örnekte yer metin eklemek gösterilmiştir `elementName` değişken, bir öğenin adı.</span><span class="sxs-lookup"><span data-stu-id="40d68-117">The following example shows how to insert the text that is contained in the `elementName` variable as the name of an element.</span></span>  
  
     <span data-ttu-id="40d68-118">Bu yöntemi kullanarak öğeleri oluştururken, kapatmalısınız \</ > etiketi.</span><span class="sxs-lookup"><span data-stu-id="40d68-118">When creating elements by using this technique, you must close them with the \</> tag.</span></span>  
  
     [!code-vb[VbXMLSamples#41](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_3.vb)]  
  
     <span data-ttu-id="40d68-119">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="40d68-119">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="40d68-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="40d68-120">See Also</span></span>  
 [<span data-ttu-id="40d68-121">Nasıl yapılır: XML değişmez değerleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="40d68-121">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)  
 [<span data-ttu-id="40d68-122">XML'de katıştırılmış ifadeler</span><span class="sxs-lookup"><span data-stu-id="40d68-122">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [<span data-ttu-id="40d68-123">Visual Basic'de XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="40d68-123">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="40d68-124">XML</span><span class="sxs-lookup"><span data-stu-id="40d68-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
