---
title: 'Nasıl yapılır: XML Değişmez Değerlerine İfade Katıştırma'
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: 5ce1386e6a1ff8ffce296f5cea694499633eb011
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071215"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a><span data-ttu-id="4f53f-102">Nasıl yapılır: XML Değişmez Değerlerine İfade Katıştırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f53f-102">How to: Embed Expressions in XML Literals (Visual Basic)</span></span>

<span data-ttu-id="4f53f-103">Çalışma zamanında oluşturulan içeriği içeren bir XML belgesi, parça veya öğe oluşturmak için gömülü ifadelerle XML değişmez değerlerini birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f53f-103">You can combine XML literals with embedded expressions to create an XML document, fragment, or element that contains content created at run time.</span></span> <span data-ttu-id="4f53f-104">Aşağıdaki örneklerde, çalışma zamanında öğe içeriğini, öznitelikleri ve öğe adlarını doldurmak için katıştırılmış ifadelerin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4f53f-104">The following examples demonstrate how to use embedded expressions to populate element content, attributes, and element names at run time.</span></span>  
  
 <span data-ttu-id="4f53f-105">Gömülü ifade için sözdizimi `<%=` `exp` `%>` , ASP.net 'in kullandığı söz dizimi olan sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="4f53f-105">The syntax for an embedded expression is `<%=` `exp` `%>`, which is the same syntax that ASP.NET uses.</span></span> <span data-ttu-id="4f53f-106">Daha fazla bilgi için bkz. [XML 'de katıştırılmış ifadeler](embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4f53f-106">For more information, see [Embedded Expressions in XML](embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="4f53f-107">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]API 'leri, nesneleri oluşturmak için de kullanabilirsiniz [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4f53f-107">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="4f53f-108">Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="4f53f-108">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="4f53f-109">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="4f53f-109">Procedures</span></span>  
  
#### <a name="to-insert-text-as-element-content"></a><span data-ttu-id="4f53f-110">Metni öğe içeriği olarak eklemek için</span><span class="sxs-lookup"><span data-stu-id="4f53f-110">To insert text as element content</span></span>  
  
- <span data-ttu-id="4f53f-111">Aşağıdaki örnek, `contactName` açma ve kapatma adı öğeleri arasındaki değişkende bulunan metnin nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f53f-111">The following example shows how to insert the text that is contained in the `contactName` variable between the opening and closing name elements.</span></span>  
  
     [!code-vb[VbXMLSamples#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#39)]  
  
     <span data-ttu-id="4f53f-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="4f53f-112">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a><span data-ttu-id="4f53f-113">Bir öznitelik değeri olarak metin eklemek için</span><span class="sxs-lookup"><span data-stu-id="4f53f-113">To insert text as an attribute value</span></span>  
  
- <span data-ttu-id="4f53f-114">Aşağıdaki örnek, değişkeninde bulunan metnin `phoneType` özniteliğin değeri olarak nasıl ekleneceğini gösterir `type` .</span><span class="sxs-lookup"><span data-stu-id="4f53f-114">The following example shows how to insert the text that is contained in the `phoneType` variable as the value of the `type` attribute.</span></span>  
  
     [!code-vb[VbXMLSamples#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#40)]  
  
     <span data-ttu-id="4f53f-115">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="4f53f-115">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a><span data-ttu-id="4f53f-116">Öğe adı için metin eklemek için</span><span class="sxs-lookup"><span data-stu-id="4f53f-116">To insert text for an element name</span></span>  
  
- <span data-ttu-id="4f53f-117">Aşağıdaki örnek, `elementName` bir öğenin adı olarak değişkende bulunan metnin nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f53f-117">The following example shows how to insert the text that is contained in the `elementName` variable as the name of an element.</span></span>  
  
     <span data-ttu-id="4f53f-118">Bu tekniği kullanarak öğe oluştururken, bunları \</> etiketiyle kapatmalısınız.</span><span class="sxs-lookup"><span data-stu-id="4f53f-118">When creating elements by using this technique, you must close them with the \</> tag.</span></span>  
  
     [!code-vb[VbXMLSamples#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#41)]  
  
     <span data-ttu-id="4f53f-119">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="4f53f-119">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4f53f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f53f-120">See also</span></span>

- [<span data-ttu-id="4f53f-121">Nasıl yapılır: XML Değişmez Değerleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4f53f-121">How to: Create XML Literals</span></span>](how-to-create-xml-literals.md)
- [<span data-ttu-id="4f53f-122">XML'de Katıştırılmış İfadeler</span><span class="sxs-lookup"><span data-stu-id="4f53f-122">Embedded Expressions in XML</span></span>](embedded-expressions-in-xml.md)
- [<span data-ttu-id="4f53f-123">Visual Basic'de XML Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4f53f-123">Creating XML in Visual Basic</span></span>](creating-xml.md)
- [<span data-ttu-id="4f53f-124">XML</span><span class="sxs-lookup"><span data-stu-id="4f53f-124">XML</span></span>](index.md)
