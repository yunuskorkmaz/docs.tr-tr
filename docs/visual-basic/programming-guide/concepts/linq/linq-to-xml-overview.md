---
title: LINQ to XML’e Genel Bakış
ms.date: 07/20/2015
ms.assetid: 502661e0-bc5d-438d-94c2-7efb63bb6fbd
ms.openlocfilehash: ef3fca844dc98440eb4816110a5a78482cfa4f4e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346788"
---
# <a name="linq-to-xml-overview-visual-basic"></a><span data-ttu-id="65a18-102">LINQ to XML genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65a18-102">LINQ to XML Overview (Visual Basic)</span></span>
<span data-ttu-id="65a18-103">XML, çok sayıda bağlamdaki verileri biçimlendirmeye yönelik bir yöntem olarak çok daha benimsemiştir.</span><span class="sxs-lookup"><span data-stu-id="65a18-103">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="65a18-104">Örneğin, Web 'de, yapılandırma dosyalarında, Microsoft Office Word dosyalarında ve veritabanlarında XML bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65a18-104">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="65a18-105">, XML ile programlamaya yönelik güncel ve yeniden tasarlanan bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="65a18-105">is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="65a18-106">Belge Nesne Modeli (DOM) için bellek içi belge değiştirme yeteneklerini sağlar ve [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="65a18-106">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="65a18-107">Bu sorgu ifadeleri XPath 'ten farklı bir şekilde farklılık içerse de, benzer işlevler sağlarlar.</span><span class="sxs-lookup"><span data-stu-id="65a18-107">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>  
  
## <a name="linq-to-xml-developers"></a><span data-ttu-id="65a18-108">LINQ to XML geliştiriciler</span><span class="sxs-lookup"><span data-stu-id="65a18-108">LINQ to XML Developers</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="65a18-109">çeşitli geliştiricilere hedefler.</span><span class="sxs-lookup"><span data-stu-id="65a18-109">targets a variety of developers.</span></span> <span data-ttu-id="65a18-110">Yalnızca bir şey yapmak isteyen ortalama bir geliştirici için, SQL 'e benzer bir sorgu deneyimi sağlayarak XML 'i daha kolay hale getirir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="65a18-110">For an average developer who just wants to get something done, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] makes XML easier by providing a query experience that is similar to SQL.</span></span> <span data-ttu-id="65a18-111">Yalnızca bir çok çalışma sayesinde programcılar, tercih ettiğiniz programlama dilinde kısa ve güçlü sorgular yazmayı öğreniyor.</span><span class="sxs-lookup"><span data-stu-id="65a18-111">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>  
  
 <span data-ttu-id="65a18-112">Profesyonel geliştiriciler, üretkenliğini önemli ölçüde artırmak için [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="65a18-112">Professional developers can use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to greatly increase their productivity.</span></span> <span data-ttu-id="65a18-113">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]sayesinde, daha açıklayıcı, daha kompakt ve daha güçlü bir kod yazabilir.</span><span class="sxs-lookup"><span data-stu-id="65a18-113">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], they can write less code that is more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="65a18-114">Aynı anda birden çok veri etki alanından sorgu ifadeleri kullanabilirler.</span><span class="sxs-lookup"><span data-stu-id="65a18-114">They can use query expressions from multiple data domains at the same time.</span></span>  
  
## <a name="what-is-linq-to-xml"></a><span data-ttu-id="65a18-115">LINQ to XML nedir?</span><span class="sxs-lookup"><span data-stu-id="65a18-115">What Is LINQ to XML?</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="65a18-116">, XML ile .NET Framework programlama dillerinin içinden çalışmanıza olanak sağlayan, LINQ özellikli, bellek içi bir XML programlama arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="65a18-116">is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the .NET Framework programming languages.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="65a18-117">, XML belgesini belleğe getiren Belge Nesne Modeli (DOM) gibidir.</span><span class="sxs-lookup"><span data-stu-id="65a18-117">is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="65a18-118">Belgeyi sorgulayabilir ve değiştirebilir ve değişiklik yaptıktan sonra dosyayı bir dosyaya kaydedebilir veya seri hale getirebilirsiniz ve Internet üzerinden gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65a18-118">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="65a18-119">Ancak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] DOM 'dan farklıdır: Bu, daha hafif ve daha kolay bir şekilde çalışacak ve Visual Basic dil özelliklerinden faydalanan yeni bir nesne modeli sağlar.</span><span class="sxs-lookup"><span data-stu-id="65a18-119">However, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in Visual Basic.</span></span>  
  
 <span data-ttu-id="65a18-120">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] en önemli avantajı [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]Tümleştirmesidir.</span><span class="sxs-lookup"><span data-stu-id="65a18-120">The most important advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is its integration with [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span></span> <span data-ttu-id="65a18-121">Bu tümleştirme, öğelerin ve özniteliklerin koleksiyonlarını almak için bellek içi XML belgesi üzerinde sorgular yazmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="65a18-121">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="65a18-122">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu özelliği, XPath ve XQuery için (sözdiziminde olmasa da) işlev olarak karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="65a18-122">The query capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="65a18-123">Visual Basic [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] tümleştirmesi daha güçlü yazma, derleme zamanı denetimi ve geliştirilmiş hata ayıklayıcı desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="65a18-123">The integration of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] in Visual Basic provides stronger typing, compile-time checking, and improved debugger support.</span></span>  
  
 <span data-ttu-id="65a18-124">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] başka bir avantajı, sorgu sonuçlarının <xref:System.Xml.Linq.XElement> parametre olarak kullanılması ve <xref:System.Xml.Linq.XAttribute> nesne oluşturucuları, XML ağaçları oluşturmaya yönelik güçlü bir yaklaşım sağlar.</span><span class="sxs-lookup"><span data-stu-id="65a18-124">Another advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="65a18-125">*İşlevsel oluşturma*olarak adlandırılan bu yaklaşım, geliştiricilerin XML ağaçlarını bir şekilden diğerine kolayca dönüştürmelerine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="65a18-125">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>  
  
 <span data-ttu-id="65a18-126">Örneğin, örnek XML dosyasında açıklandığı gibi tipik bir XML satın alma siparişiniz olabilir [: tipik satın alma siparişi (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="65a18-126">For example, you might have a typical XML purchase order as described in [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span> <span data-ttu-id="65a18-127">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]kullanarak, satın alma sırasındaki her öğe öğesi için bölüm numarası öznitelik değerini almak üzere aşağıdaki sorguyu çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="65a18-127">By using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>  
  
```vb  
Dim partNos = _  
    From item In purchaseOrder...<Item> _  
    Select item.@PartNumber  
```  
  
 <span data-ttu-id="65a18-128">Başka bir örnek olarak, $100 'den büyük bir değere sahip olan öğelerin bölüm numarasına göre sıralanmış bir liste olmasını isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65a18-128">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="65a18-129">Bu bilgileri almak için aşağıdaki sorguyu çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="65a18-129">To obtain this information, you could run the following query:</span></span>  
  
```vb  
Dim partNos = _  
From item In purchaseOrder...<Item> _  
Where (item.<Quantity>.Value * _  
       item.<USPrice>.Value) > 100 _  
Order By item.<PartNumber>.Value _  
Select item  
```  
  
 <span data-ttu-id="65a18-130">Bu [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] özelliklerine ek olarak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] geliştirilmiş bir XML programlama arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="65a18-130">In addition to these [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] capabilities, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides an improved XML programming interface.</span></span> <span data-ttu-id="65a18-131">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]kullanarak şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="65a18-131">Using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can:</span></span>  
  
- <span data-ttu-id="65a18-132">Dosyalardan veya akışlardan XML yükleyin.</span><span class="sxs-lookup"><span data-stu-id="65a18-132">Load XML from files or streams.</span></span>  
  
- <span data-ttu-id="65a18-133">XML 'yi dosyalara veya akışlara seri hale getirme.</span><span class="sxs-lookup"><span data-stu-id="65a18-133">Serialize XML to files or streams.</span></span>  
  
- <span data-ttu-id="65a18-134">İşlevsel oluşturma kullanarak sıfırdan XML oluşturun.</span><span class="sxs-lookup"><span data-stu-id="65a18-134">Create XML from scratch by using functional construction.</span></span>  
  
- <span data-ttu-id="65a18-135">XPath benzeri eksenleri kullanarak XML 'yi sorgula.</span><span class="sxs-lookup"><span data-stu-id="65a18-135">Query XML using XPath-like axes.</span></span>  
  
- <span data-ttu-id="65a18-136"><xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>ve <xref:System.Xml.Linq.XElement.SetValue%2A>gibi yöntemleri kullanarak bellek içi XML ağacını işleme.</span><span class="sxs-lookup"><span data-stu-id="65a18-136">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>  
  
- <span data-ttu-id="65a18-137">XSD kullanarak XML ağaçlarını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="65a18-137">Validate XML trees using XSD.</span></span>  
  
- <span data-ttu-id="65a18-138">XML ağaçlarını bir şekilden diğerine dönüştürmek için bu özelliklerin birleşimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="65a18-138">Use a combination of these features to transform XML trees from one shape into another.</span></span>  
  
## <a name="creating-xml-trees"></a><span data-ttu-id="65a18-139">XML Ağaçları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="65a18-139">Creating XML Trees</span></span>  
 <span data-ttu-id="65a18-140">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programlamanın en önemli avantajlarından biri, XML ağaçları oluşturmak kolaydır.</span><span class="sxs-lookup"><span data-stu-id="65a18-140">IOne of the most significant advantages of programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is that it is easy to create XML trees.</span></span> <span data-ttu-id="65a18-141">Örneğin, küçük bir XML ağacı oluşturmak için aşağıdaki gibi bir kod yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="65a18-141">For example, to create a small XML tree, you can write  code as follows:</span></span>  
  
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
  
 <span data-ttu-id="65a18-142">Visual Basic Derleyicisi, XML değişmez değerlerini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yöntemi çağrılarına çevirir.</span><span class="sxs-lookup"><span data-stu-id="65a18-142">The Visual Basic compiler translates XML literals into [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] method calls.</span></span>  
  
 <span data-ttu-id="65a18-143">Daha fazla bilgi için bkz. [xml ağaçları oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="65a18-143">For more information, see [Creating XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65a18-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65a18-144">See also</span></span>

- <xref:System.Xml.Linq>
- [<span data-ttu-id="65a18-145">Başlarken (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="65a18-145">Getting Started (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
- [<span data-ttu-id="65a18-146">Visual Basic LINQ to XML genel bakış</span><span class="sxs-lookup"><span data-stu-id="65a18-146">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)
- [<span data-ttu-id="65a18-147">XML</span><span class="sxs-lookup"><span data-stu-id="65a18-147">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
