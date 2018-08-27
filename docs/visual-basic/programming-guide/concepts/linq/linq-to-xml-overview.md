---
title: LINQ to XML genel bakış (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 502661e0-bc5d-438d-94c2-7efb63bb6fbd
ms.openlocfilehash: 3818177c2ed14b1159b8e63e324894d7e89b72b6
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42932409"
---
# <a name="linq-to-xml-overview-visual-basic"></a><span data-ttu-id="0361b-102">LINQ to XML genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0361b-102">LINQ to XML Overview (Visual Basic)</span></span>
<span data-ttu-id="0361b-103">XML, yaygın olarak birçok bağlamları verileri biçimlendirme bir yolu olarak benimsenmiştir.</span><span class="sxs-lookup"><span data-stu-id="0361b-103">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="0361b-104">Örneğin, yapılandırma dosyalarını, Microsoft Office Word dosyaları ve veritabanlarının Web XML bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0361b-104">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="0361b-105"> güncel ve yeniden tasarlanan XML ile programlamaya yaklaşımıdır.</span><span class="sxs-lookup"><span data-stu-id="0361b-105"> is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="0361b-106">Bellek içi belge değiştirme özelliklerini belge nesne modeli (DOM) sağlar ve destekleyen [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadelerinde.</span><span class="sxs-lookup"><span data-stu-id="0361b-106">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="0361b-107">Bu sorgu ifadeleri XPath sözdizimi kurallarına göre farklı olsa da, benzer bir işlevsellik sağlarlar.</span><span class="sxs-lookup"><span data-stu-id="0361b-107">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>  
  
## <a name="linq-to-xml-developers"></a><span data-ttu-id="0361b-108">LINQ to XML geliştiriciler</span><span class="sxs-lookup"><span data-stu-id="0361b-108">LINQ to XML Developers</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="0361b-109"> geliştiricilerin çeşitli hedefler.</span><span class="sxs-lookup"><span data-stu-id="0361b-109"> targets a variety of developers.</span></span> <span data-ttu-id="0361b-110">Yalnızca bir şey yapmanız, almak isteyen bir ortalama geliştiricinin [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML SQL'e benzeyen bir sorgu deneyimi sunarak daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="0361b-110">For an average developer who just wants to get something done, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] makes XML easier by providing a query experience that is similar to SQL.</span></span> <span data-ttu-id="0361b-111">Yalnızca bir bit öğrenim, programcılar kendi seçtiğiniz programlama dilinde birleştiren ve güçlü sorgular yazmak bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0361b-111">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>  
  
 <span data-ttu-id="0361b-112">Profesyonel Geliştiriciler [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] üretkenliklerini büyük ölçüde artırmak için.</span><span class="sxs-lookup"><span data-stu-id="0361b-112">Professional developers can use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to greatly increase their productivity.</span></span> <span data-ttu-id="0361b-113">İle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], bunlar daha ifadesel, daha küçük ve daha güçlü daha az kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0361b-113">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], they can write less code that is more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="0361b-114">Aynı anda birden çok veri etki alanından bunlar sorgu ifadeleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0361b-114">They can use query expressions from multiple data domains at the same time.</span></span>  
  
## <a name="what-is-linq-to-xml"></a><span data-ttu-id="0361b-115">LINQ to XML nedir?</span><span class="sxs-lookup"><span data-stu-id="0361b-115">What Is LINQ to XML?</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="0361b-116"> XML ile içinden çalışmanızı sağlayan bir LINQ-etkin, bellek içi XML programlama arabirimi olan [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] programlama.</span><span class="sxs-lookup"><span data-stu-id="0361b-116"> is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] programming languages.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="0361b-117"> XML belgesi belleğe getirdiği belge nesne modeli (DOM) gibi olmamasıdır.</span><span class="sxs-lookup"><span data-stu-id="0361b-117"> is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="0361b-118">Sorgulamak ve belgeyi değiştirmesine ve değiştirdikten sonra bir dosyaya kaydedebilir veya bu seri hale getirmek ve Internet üzerinden gönder.</span><span class="sxs-lookup"><span data-stu-id="0361b-118">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="0361b-119">Ancak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] DOM farklıdır: açık ağırlığı olan yeni bir nesne modeli sağlar ve çalışmak, daha kolay ve Visual Basic Dil özelliklerinden alan.</span><span class="sxs-lookup"><span data-stu-id="0361b-119">However, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in Visual Basic.</span></span>  
  
 <span data-ttu-id="0361b-120">En önemli avantajı [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tümleştirmesi sayesinde olan [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0361b-120">The most important advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is its integration with [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span></span> <span data-ttu-id="0361b-121">Bu tümleştirme, öğeleri ve özniteliklerinin koleksiyonu almak için bellek içi XML belgesi sorgular yazmaya olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="0361b-121">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="0361b-122">Sorgu yeteneğini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] (değil, ancak sözdizimi) işlevselliği karşılaştırılabilir XPath ve XQuery.</span><span class="sxs-lookup"><span data-stu-id="0361b-122">The query capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="0361b-123">Tümleştirmesini [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] Visual Basic'te daha güçlü yazım, denetleme ve geliştirilmiş hata ayıklayıcı desteği zamanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="0361b-123">The integration of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] in Visual Basic provides stronger typing, compile-time checking, and improved debugger support.</span></span>  
  
 <span data-ttu-id="0361b-124">Başka bir avantajı [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu sonuçları için parametre olarak kullanma olanağı <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XAttribute> nesne oluşturucuları XML ağaçları oluşturma için güçlü bir yaklaşım sağlar.</span><span class="sxs-lookup"><span data-stu-id="0361b-124">Another advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="0361b-125">Adlandırılan bu yaklaşım *işlevsel oluşturma*, geliştiricilerin bir şekilden XML ağaçlarını başka bir kolayca dönüştürüp olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="0361b-125">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>  
  
 <span data-ttu-id="0361b-126">Örneğin, satınalma siparişi açıklandığı gibi tipik bir XML olabilir [örnek XML dosyası: tipik satın alma siparişi (LINQ to XML)](http://msdn.microsoft.com/library/0606c09f-6e43-4f8d-95c8-e8e2e08d2348).</span><span class="sxs-lookup"><span data-stu-id="0361b-126">For example, you might have a typical XML purchase order as described in [Sample XML File: Typical Purchase Order (LINQ to XML)](http://msdn.microsoft.com/library/0606c09f-6e43-4f8d-95c8-e8e2e08d2348).</span></span> <span data-ttu-id="0361b-127">Kullanarak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], satın alma siparişi her öğe öğe için bölüm numarası özniteliği değeri elde etmek için şu sorguyu çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0361b-127">By using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>  
  
```vb  
Dim partNos = _  
    From item In purchaseOrder...<Item> _  
    Select item.@PartNumber  
```  
  
 <span data-ttu-id="0361b-128">Başka bir örnek olarak $100'den büyük bir değer ile öğelerinin parça numarası tarafından sıralanan bir liste isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0361b-128">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="0361b-129">Bu bilgiler edinmek için şu sorguyu çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0361b-129">To obtain this information, you could run the following query:</span></span>  
  
```vb  
Dim partNos = _  
From item In purchaseOrder...<Item> _  
Where (item.<Quantity>.Value * _  
       item.<USPrice>.Value) > 100 _  
Order By item.<PartNumber>.Value _  
Select item  
```  
  
 <span data-ttu-id="0361b-130">Bunların yanı sıra [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] yeteneklerini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] geliştirilmiş bir XML programlama arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="0361b-130">In addition to these [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] capabilities, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides an improved XML programming interface.</span></span> <span data-ttu-id="0361b-131">Kullanarak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0361b-131">Using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can:</span></span>  
  
-   <span data-ttu-id="0361b-132">XML dosyaları ya da akış'ı yükleyin.</span><span class="sxs-lookup"><span data-stu-id="0361b-132">Load XML from files or streams.</span></span>  
  
-   <span data-ttu-id="0361b-133">XML dosyaları ya da akış serileştirir.</span><span class="sxs-lookup"><span data-stu-id="0361b-133">Serialize XML to files or streams.</span></span>  
  
-   <span data-ttu-id="0361b-134">XML işlevsel oluşturma kullanarak sıfırdan oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0361b-134">Create XML from scratch by using functional construction.</span></span>  
  
-   <span data-ttu-id="0361b-135">Sorgu XPath benzeri eksen kullanılarak XML.</span><span class="sxs-lookup"><span data-stu-id="0361b-135">Query XML using XPath-like axes.</span></span>  
  
-   <span data-ttu-id="0361b-136">Bellek içi XML ağacı yöntemleri kullanarak işleme <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, ve <xref:System.Xml.Linq.XElement.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="0361b-136">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>  
  
-   <span data-ttu-id="0361b-137">XML ağaçlarını XSD kullanarak doğrulama.</span><span class="sxs-lookup"><span data-stu-id="0361b-137">Validate XML trees using XSD.</span></span>  
  
-   <span data-ttu-id="0361b-138">Başka bir şekilden XML ağaçlarını dönüştürmek için bu özellikleri bir birleşimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0361b-138">Use a combination of these features to transform XML trees from one shape into another.</span></span>  
  
## <a name="creating-xml-trees"></a><span data-ttu-id="0361b-139">XML ağaçları oluşturma</span><span class="sxs-lookup"><span data-stu-id="0361b-139">Creating XML Trees</span></span>  
 <span data-ttu-id="0361b-140">En önemli avantajlarından biri ile programlama IOne [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML ağaçları oluşturma kolay olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="0361b-140">IOne of the most significant advantages of programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is that it is easy to create XML trees.</span></span> <span data-ttu-id="0361b-141">Örneğin, küçük bir XML ağacı oluşturmak için kod şu şekilde yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0361b-141">For example, to create a small XML tree, you can write  code as follows:</span></span>  
  
```vb  
Dim contacts = _  
<Contacts>  
    <Contact>  
        <Name>Patrick Hines</Name>  
        <Phone Type="Home">206-555-0144</Phone>  
        <Phone Type="Work">425-555-0145</Phone>  
        <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
        </Address>  
    </Contact>  
</Contacts>  
```  
  
 <span data-ttu-id="0361b-142">Visual Basic derleyici içine XML sabit değerleri çevirir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="0361b-142">The Visual Basic compiler translates XML literals into [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] method calls.</span></span>  
  
 <span data-ttu-id="0361b-143">Daha fazla bilgi için [XML ağaçları oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="0361b-143">For more information, see [Creating XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0361b-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0361b-144">See Also</span></span>  
 <xref:System.Xml.Linq>  
 [<span data-ttu-id="0361b-145">Başlarken (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="0361b-145">Getting Started (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)  
 [<span data-ttu-id="0361b-146">LINQ to XML Visual Basic'de genel bakış</span><span class="sxs-lookup"><span data-stu-id="0361b-146">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 [<span data-ttu-id="0361b-147">XML</span><span class="sxs-lookup"><span data-stu-id="0361b-147">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
