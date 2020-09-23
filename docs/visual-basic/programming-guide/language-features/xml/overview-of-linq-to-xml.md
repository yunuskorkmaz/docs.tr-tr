---
title: LINQ to XML’e Genel Bakış
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
ms.openlocfilehash: 4ec1c96bdca96a6e9b68b240c147b70536514d85
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91099196"
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a><span data-ttu-id="f8885-102">Visual Basic'de LINQ - XML Dönüşümüne Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f8885-102">Overview of LINQ to XML in Visual Basic</span></span>

<span data-ttu-id="f8885-103">Visual Basic, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML değişmez değerleri ve xml eksen özellikleri için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8885-103">Visual Basic provides support for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] through XML literals and XML axis properties.</span></span> <span data-ttu-id="f8885-104">Bu, Visual Basic kodunuzda XML ile çalışmak için tanıdık, kullanışlı bir sözdizimi kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8885-104">This enables you to use a familiar, convenient syntax for working with XML in your Visual Basic code.</span></span> <span data-ttu-id="f8885-105">*XML değişmez değerleri* doğrudan kodunuza XML dahil etme olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8885-105">*XML literals* enable you to include XML directly in your code.</span></span> <span data-ttu-id="f8885-106">*Xml eksen özellikleri* , bir XML sabit değerinin alt düğümlerine, alt düğümlerine ve özniteliklerine erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8885-106">*XML axis properties* enable you to access child nodes, descendant nodes, and attributes of an XML literal.</span></span> <span data-ttu-id="f8885-107">Daha fazla bilgi için bkz. [XML değişmez değerlerine genel bakış](xml-literals-overview.md) ve [Visual Basic xml 'e erişme](accessing-xml.md).</span><span class="sxs-lookup"><span data-stu-id="f8885-107">For more information, see [XML Literals Overview](xml-literals-overview.md) and [Accessing XML in Visual Basic](accessing-xml.md).</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="f8885-108">, özellikle dil ile tümleşik sorgu (LINQ) avantajlarından yararlanmak için tasarlanan, bellek içi bir XML programlama API 'sidir.</span><span class="sxs-lookup"><span data-stu-id="f8885-108">is an in-memory XML programming API designed specifically to take advantage of Language-Integrated Query (LINQ).</span></span> <span data-ttu-id="f8885-109">LINQ API 'Lerini doğrudan çağırabilseniz de yalnızca Visual Basic, XML değişmez değerlerini bildirmenize ve doğrudan XML ekseni özelliklerine erişebilmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8885-109">Although you can call the LINQ APIs directly, only Visual Basic enables you to declare XML literals and directly access XML axis properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8885-110">ASP.NET sayfasındaki bildirim temelli kodda XML sabit değerleri ve XML eksen özellikleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="f8885-110">XML literals and XML axis properties are not supported in declarative code in an ASP.NET page.</span></span> <span data-ttu-id="f8885-111">Visual Basic XML özelliklerini kullanmak için kodunuzu ASP.NET uygulamanızdaki bir arka plan kod sayfasına koyun.</span><span class="sxs-lookup"><span data-stu-id="f8885-111">To use Visual Basic XML features, put your code in a code-behind page in your ASP.NET application.</span></span>  
  
 <span data-ttu-id="f8885-112">[Yürüt düğmesi](./media/overview-of-linq-to-xml/play-video-icon-example.gif) İlgili video gösterileri için bkz. [LINQ to XML nasıl başladım?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml) ve [LINQ to XML kullanarak Excel elektronik tabloları nasıl oluşturabilirim?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml).</span><span class="sxs-lookup"><span data-stu-id="f8885-112">[Play button](./media/overview-of-linq-to-xml/play-video-icon-example.gif) For related video demonstrations, see [How Do I Get Started with LINQ to XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml) and [How Do I Create Excel Spreadsheets using LINQ to XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml).</span></span>
  
## <a name="creating-xml"></a><span data-ttu-id="f8885-113">XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="f8885-113">Creating XML</span></span>  

 <span data-ttu-id="f8885-114">Visual Basic XML ağaçları oluşturmanın iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="f8885-114">There are two ways to create XML trees in Visual Basic.</span></span> <span data-ttu-id="f8885-115">Doğrudan kodda bir XML sabit değeri bildirebilirsiniz veya ağacı oluşturmak için LINQ API 'Lerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8885-115">You can declare an XML literal directly in code, or you can use the LINQ APIs to create the tree.</span></span> <span data-ttu-id="f8885-116">Her iki işlem de kodun XML ağacının son yapısını yansıtmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8885-116">Both processes enable the code to reflect the final structure of the XML tree.</span></span> <span data-ttu-id="f8885-117">Örneğin, aşağıdaki kod örneği bir XML öğesi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="f8885-117">For example, the following code example creates an XML element:</span></span>  
  
 [!code-vb[VbXmlSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 <span data-ttu-id="f8885-118">Daha fazla bilgi için bkz. [VISUAL BASIC XML oluşturma](creating-xml.md).</span><span class="sxs-lookup"><span data-stu-id="f8885-118">For more information, see [Creating XML in Visual Basic](creating-xml.md).</span></span>  
  
## <a name="accessing-and-navigating-xml"></a><span data-ttu-id="f8885-119">XML 'e erişme ve gezinme</span><span class="sxs-lookup"><span data-stu-id="f8885-119">Accessing and Navigating XML</span></span>  

 <span data-ttu-id="f8885-120">Visual Basic, XML yapılarına erişmek ve bunları gezinmek için XML eksen özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8885-120">Visual Basic provides XML axis properties for accessing and navigating XML structures.</span></span> <span data-ttu-id="f8885-121">Bu özellikler, xml alt öğe adlarını belirterek XML öğelerine ve özniteliklerine erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8885-121">These properties enable you to access XML elements and attributes by specifying the XML child element names.</span></span> <span data-ttu-id="f8885-122">Alternatif olarak, öğeleri ve öznitelikleri gezinmek ve bulmak için LINQ yöntemlerini açık bir şekilde çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8885-122">Alternatively, you can explicitly call the LINQ methods for navigating and locating elements and attributes.</span></span> <span data-ttu-id="f8885-123">Örneğin, aşağıdaki kod örneği bir XML öğesinin özniteliklerine ve alt öğelerine başvurmak için XML eksen özelliklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f8885-123">For example, the following code example uses XML axis properties to refer to the attributes and child elements of an XML element.</span></span> <span data-ttu-id="f8885-124">Kod örneği, alt öğeleri almak için bir LINQ sorgusu kullanır ve bunları, etkin bir şekilde bir dönüşüm gerçekleştirerek XML öğeleri olarak çıktılar.</span><span class="sxs-lookup"><span data-stu-id="f8885-124">The code example uses a LINQ query to retrieve child elements and output them as XML elements, effectively performing a transform.</span></span>  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 <span data-ttu-id="f8885-125">Daha fazla bilgi için bkz. [VISUAL BASIC XML 'e erişme](accessing-xml.md).</span><span class="sxs-lookup"><span data-stu-id="f8885-125">For more information, see [Accessing XML in Visual Basic](accessing-xml.md).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="f8885-126">XML ad alanları</span><span class="sxs-lookup"><span data-stu-id="f8885-126">XML Namespaces</span></span>  

 <span data-ttu-id="f8885-127">Visual Basic, bir genel XML ad alanı için ifadesini kullanarak bir diğer ad belirtmenizi sağlar `Imports` .</span><span class="sxs-lookup"><span data-stu-id="f8885-127">Visual Basic enables you to specify an alias to a global XML namespace by using the `Imports` statement.</span></span> <span data-ttu-id="f8885-128">Aşağıdaki örnek, `Imports` BIR XML ad alanını içeri aktarmak için deyimin nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="f8885-128">The following example shows how to use the `Imports` statement to import an XML namespace:</span></span>  
  
 [!code-vb[VbXMLSamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#1)]  
  
 <span data-ttu-id="f8885-129">Xml eksen özelliklerine eriştiğinizde ve XML belgeleri ve öğeleri için XML değişmez değerleri bildirdiğinizde bir XML ad alanı diğer adı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8885-129">You can use an XML namespace alias when you access XML axis properties and declare XML literals for XML documents and elements.</span></span>  
  
 <span data-ttu-id="f8885-130"><xref:System.Xml.Linq.XNamespace> [GetXmlNamespace işlecini](../../../language-reference/operators/getxmlnamespace-operator.md)kullanarak belirli bir ad alanı öneki için bir nesne alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8885-130">You can retrieve an <xref:System.Xml.Linq.XNamespace> object for a particular namespace prefix by using the [GetXmlNamespace Operator](../../../language-reference/operators/getxmlnamespace-operator.md).</span></span>  
  
 <span data-ttu-id="f8885-131">Daha fazla bilgi için bkz. [Imports bildirisi (XML ad alanı)](../../../language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="f8885-131">For more information, see [Imports Statement (XML Namespace)](../../../language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
### <a name="using-xml-namespaces-in-xml-literals"></a><span data-ttu-id="f8885-132">XML sabit değerlerinde XML ad alanlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="f8885-132">Using XML Namespaces in XML Literals</span></span>  

 <span data-ttu-id="f8885-133">Aşağıdaki örnek, <xref:System.Xml.Linq.XElement> genel ad alanını kullanan bir nesnenin nasıl oluşturulacağını gösterir `ns` :</span><span class="sxs-lookup"><span data-stu-id="f8885-133">The following example shows how to create an <xref:System.Xml.Linq.XElement> object that uses the global namespace `ns`:</span></span>  
  
 [!code-vb[VbXMLSamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#2)]  
  
 <span data-ttu-id="f8885-134">Visual Basic Derleyicisi, XML ad alanı diğer adlarını içeren XML değişmez değerlerini özniteliği ile XML ad alanlarını kullanmak için XML gösterimini kullanan eşdeğer koda çevirir `xmlns` .</span><span class="sxs-lookup"><span data-stu-id="f8885-134">The Visual Basic compiler translates XML literals that contain XML namespace aliases into equivalent code that uses the XML notation for using XML namespaces, with the `xmlns` attribute.</span></span> <span data-ttu-id="f8885-135">Derlendiğinde, önceki bölümdeki kod aşağıdaki örnekteki gibi temelde aynı çalıştırılabilir kodu üretir:</span><span class="sxs-lookup"><span data-stu-id="f8885-135">When compiled, the code in the previous section's example produces essentially the same executable code as the following example:</span></span>  
  
 [!code-vb[VbXMLSamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#3)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a><span data-ttu-id="f8885-136">Xml eksen özelliklerinde XML ad alanlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="f8885-136">Using XML Namespaces in XML Axis Properties</span></span>  

 <span data-ttu-id="f8885-137">XML sabit değerlerinde belirtilen XML ad alanları, XML ekseni özelliklerinde kullanım için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f8885-137">XML namespaces declared in XML literals are not available for use in XML axis properties.</span></span> <span data-ttu-id="f8885-138">Ancak, genel ad alanları XML ekseni özellikleriyle birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f8885-138">However, global namespaces can be used with the XML axis properties.</span></span> <span data-ttu-id="f8885-139">XML ad alanı önekini yerel öğe adından ayırmak için iki nokta üst üste kullanın.</span><span class="sxs-lookup"><span data-stu-id="f8885-139">Use a colon to separate the XML namespace prefix from the local element name.</span></span> <span data-ttu-id="f8885-140">Aşağıda bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f8885-140">Following is an example:</span></span>  
  
 [!code-vb[VbXMLSamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="f8885-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8885-141">See also</span></span>

- [<span data-ttu-id="f8885-142">XML</span><span class="sxs-lookup"><span data-stu-id="f8885-142">XML</span></span>](index.md)
- [<span data-ttu-id="f8885-143">Visual Basic'de XML Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f8885-143">Creating XML in Visual Basic</span></span>](creating-xml.md)
- [<span data-ttu-id="f8885-144">Visual Basic'de XML'e Erişme</span><span class="sxs-lookup"><span data-stu-id="f8885-144">Accessing XML in Visual Basic</span></span>](accessing-xml.md)
- [<span data-ttu-id="f8885-145">Visual Basic'de XML'i Düzenleme</span><span class="sxs-lookup"><span data-stu-id="f8885-145">Manipulating XML in Visual Basic</span></span>](manipulating-xml.md)
