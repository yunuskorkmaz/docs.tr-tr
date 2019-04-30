---
title: XDocument sınıfına genel bakış (C#)
ms.date: 07/20/2015
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
ms.openlocfilehash: e3ef7d66cb9759bd71e69c1a0db3614a02f785b3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61680645"
---
# <a name="xdocument-class-overview-c"></a><span data-ttu-id="13418-102">XDocument sınıfına genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="13418-102">XDocument Class Overview (C#)</span></span>
<span data-ttu-id="13418-103">Bu konu tanıtır <xref:System.Xml.Linq.XDocument> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="13418-103">This topic introduces the <xref:System.Xml.Linq.XDocument> class.</span></span>  
  
## <a name="overview-of-the-xdocument-class"></a><span data-ttu-id="13418-104">XDocument sınıfına genel bakış</span><span class="sxs-lookup"><span data-stu-id="13418-104">Overview of the XDocument class</span></span>  
 <span data-ttu-id="13418-105"><xref:System.Xml.Linq.XDocument> Sınıfı, geçerli bir XML belgesi için gereken bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="13418-105">The <xref:System.Xml.Linq.XDocument> class contains the information necessary for a valid XML document.</span></span> <span data-ttu-id="13418-106">Bu işleme yönergeleri ve açıklamaları, bir XML bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="13418-106">This includes an XML declaration, processing instructions, and comments.</span></span>  
  
 <span data-ttu-id="13418-107">Yalnızca oluşturmak zorunda Not <xref:System.Xml.Linq.XDocument> tarafından sağlanan belirli işlevleri gerektirip gerektirmediğini nesneleri <xref:System.Xml.Linq.XDocument> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="13418-107">Note that you only have to create <xref:System.Xml.Linq.XDocument> objects if you require the specific functionality provided by the <xref:System.Xml.Linq.XDocument> class.</span></span> <span data-ttu-id="13418-108">Çoğu durumda, doğrudan çalışabileceğiniz <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="13418-108">In many circumstances, you can work directly with <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="13418-109">Doğrudan çalışma <xref:System.Xml.Linq.XElement> daha basit bir programlama modelidir.</span><span class="sxs-lookup"><span data-stu-id="13418-109">Working directly with <xref:System.Xml.Linq.XElement> is a simpler programming model.</span></span>  
  
 <span data-ttu-id="13418-110"><xref:System.Xml.Linq.XDocument> öğesinden türetilen <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="13418-110"><xref:System.Xml.Linq.XDocument> derives from <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="13418-111">Bu nedenle, bu alt düğümler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="13418-111">Therefore, it can contain child nodes.</span></span> <span data-ttu-id="13418-112">Ancak, <xref:System.Xml.Linq.XDocument> nesneler yalnızca bir alt sahip <xref:System.Xml.Linq.XElement> düğümü.</span><span class="sxs-lookup"><span data-stu-id="13418-112">However, <xref:System.Xml.Linq.XDocument> objects can have only one child <xref:System.Xml.Linq.XElement> node.</span></span> <span data-ttu-id="13418-113">Bu, bir XML belgesinde yalnızca bir kök öğe olabileceğini XML standardı yansıtır.</span><span class="sxs-lookup"><span data-stu-id="13418-113">This reflects the XML standard that there can be only one root element in an XML document.</span></span>  
  
## <a name="components-of-xdocument"></a><span data-ttu-id="13418-114">XDocument bileşenleri</span><span class="sxs-lookup"><span data-stu-id="13418-114">Components of XDocument</span></span>  
 <span data-ttu-id="13418-115">Bir <xref:System.Xml.Linq.XDocument> aşağıdaki öğeleri içerebilir:</span><span class="sxs-lookup"><span data-stu-id="13418-115">An <xref:System.Xml.Linq.XDocument> can contain the following elements:</span></span>  
  
- <span data-ttu-id="13418-116">Bir <xref:System.Xml.Linq.XDeclaration> nesne.</span><span class="sxs-lookup"><span data-stu-id="13418-116">One <xref:System.Xml.Linq.XDeclaration> object.</span></span> <span data-ttu-id="13418-117"><xref:System.Xml.Linq.XDeclaration> bir XML bildirimi ilgili bölümleri belirtmenize olanak tanıyan: kodlama belgenin XML sürümü ve XML belge tek başına olup.</span><span class="sxs-lookup"><span data-stu-id="13418-117"><xref:System.Xml.Linq.XDeclaration> enables you to specify the pertinent parts of an XML declaration: the XML version, the encoding of the document, and whether the XML document is stand-alone.</span></span>  
  
- <span data-ttu-id="13418-118">Bir <xref:System.Xml.Linq.XElement> nesne.</span><span class="sxs-lookup"><span data-stu-id="13418-118">One <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="13418-119">Bu işlev, XML belgesi kök düğümüdür.</span><span class="sxs-lookup"><span data-stu-id="13418-119">This is the root node of the XML document.</span></span>  
  
- <span data-ttu-id="13418-120">Herhangi bir sayıda <xref:System.Xml.Linq.XProcessingInstruction> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="13418-120">Any number of <xref:System.Xml.Linq.XProcessingInstruction> objects.</span></span> <span data-ttu-id="13418-121">Bir işlem yönergesi, XML işleme uygulamaya bilgi iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="13418-121">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
- <span data-ttu-id="13418-122">Herhangi bir sayıda <xref:System.Xml.Linq.XComment> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="13418-122">Any number of <xref:System.Xml.Linq.XComment> objects.</span></span> <span data-ttu-id="13418-123">Açıklamalar, kök öğe kardeş olacaktır.</span><span class="sxs-lookup"><span data-stu-id="13418-123">The comments will be siblings to the root element.</span></span> <span data-ttu-id="13418-124"><xref:System.Xml.Linq.XComment> Bir yorum ile başlatmak bir XML belgesi için geçerli olmadığından, nesne ilk bağımsız değişken listesinde olamaz.</span><span class="sxs-lookup"><span data-stu-id="13418-124">The <xref:System.Xml.Linq.XComment> object cannot be the first argument in the list, because it is not valid for an XML document to start with a comment.</span></span>  
  
- <span data-ttu-id="13418-125">Bir <xref:System.Xml.Linq.XDocumentType> DTD'nin için.</span><span class="sxs-lookup"><span data-stu-id="13418-125">One <xref:System.Xml.Linq.XDocumentType> for the DTD.</span></span>  
  
 <span data-ttu-id="13418-126">Serileştirmek ne zaman bir <xref:System.Xml.Linq.XDocument>bile `XDocument.Declaration` olduğu `null`, yazıcı çıkış XML bildirimi varsa `Writer.Settings.OmitXmlDeclaration` kümesine `false` (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="13418-126">When you serialize an <xref:System.Xml.Linq.XDocument>, even if `XDocument.Declaration` is `null`, the output will have an XML declaration if the writer has `Writer.Settings.OmitXmlDeclaration` set to `false` (the default).</span></span>  
  
 <span data-ttu-id="13418-127">Varsayılan olarak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ayarlar sürüm "1.0" ve "utf-8" kodlama ayarlar.</span><span class="sxs-lookup"><span data-stu-id="13418-127">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sets the version to "1.0", and sets the encoding to "utf-8".</span></span>  
  
## <a name="using-xelement-without-xdocument"></a><span data-ttu-id="13418-128">XElement XDocument olmadan kullanma</span><span class="sxs-lookup"><span data-stu-id="13418-128">Using XElement without XDocument</span></span>  
 <span data-ttu-id="13418-129">Daha önce belirtildiği gibi <xref:System.Xml.Linq.XElement> ana sınıfı içinde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programlama arabirimi.</span><span class="sxs-lookup"><span data-stu-id="13418-129">As previously mentioned, the <xref:System.Xml.Linq.XElement> class is the main class in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface.</span></span> <span data-ttu-id="13418-130">Çoğu durumda, bir belge oluşturmak, uygulamanızın gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="13418-130">In many cases, your application will not require that you create a document.</span></span> <span data-ttu-id="13418-131">Kullanarak <xref:System.Xml.Linq.XElement> sınıfı, bir XML ağacı oluşturma, diğer XML ağaçlarını ekleyin, XML ağacı değiştirebilir ve kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13418-131">By using the <xref:System.Xml.Linq.XElement> class, you can create an XML tree, add other XML trees to it, modify the XML tree, and save it.</span></span>  
  
## <a name="using-xdocument"></a><span data-ttu-id="13418-132">XDocument kullanma</span><span class="sxs-lookup"><span data-stu-id="13418-132">Using XDocument</span></span>  
 <span data-ttu-id="13418-133">Oluşturmak için bir <xref:System.Xml.Linq.XDocument>, oluşturmak için yaptığınız gibi işlev yapım kullanın <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="13418-133">To construct an <xref:System.Xml.Linq.XDocument>, use functional construction, just like you do to construct <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="13418-134">Aşağıdaki kod oluşturur bir <xref:System.Xml.Linq.XDocument> nesne ve onun ilişkili kapsanan nesneleri.</span><span class="sxs-lookup"><span data-stu-id="13418-134">The following code creates an <xref:System.Xml.Linq.XDocument> object and its associated contained objects.</span></span>  
  
```csharp  
XDocument d = new XDocument(  
    new XComment("This is a comment."),  
    new XProcessingInstruction("xml-stylesheet",  
        "href='mystyle.css' title='Compact' type='text/css'"),  
    new XElement("Pubs",  
        new XElement("Book",  
            new XElement("Title", "Artifacts of Roman Civilization"),  
            new XElement("Author", "Moreno, Jordao")  
        ),  
        new XElement("Book",  
            new XElement("Title", "Midieval Tools and Implements"),  
            new XElement("Author", "Gazit, Inbar")  
        )  
    ),  
    new XComment("This is another comment.")  
);  
d.Declaration = new XDeclaration("1.0", "utf-8", "true");  
Console.WriteLine(d);  
  
d.Save("test.xml");  
```  
  
 <span data-ttu-id="13418-135">Dosya test.xml incelediğinizde, aşağıdaki çıkışı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="13418-135">When you examine the file test.xml, you get the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!--This is a comment.-->  
<?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
<Pubs>  
  <Book>  
    <Title>Artifacts of Roman Civilization</Title>  
    <Author>Moreno, Jordao</Author>  
  </Book>  
  <Book>  
    <Title>Midieval Tools and Implements</Title>  
    <Author>Gazit, Inbar</Author>  
  </Book>  
</Pubs>  
<!--This is another comment.-->  
```  
  
## <a name="see-also"></a><span data-ttu-id="13418-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13418-136">See also</span></span>

- [<span data-ttu-id="13418-137">LINQ to XML programlamaya genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="13418-137">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
