---
title: XDocument sınıfına genel bakış (C#)
ms.date: 07/20/2015
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
ms.openlocfilehash: 999d570725acbf328858b0ef6c69f709317f10fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333355"
---
# <a name="xdocument-class-overview-c"></a><span data-ttu-id="28cd4-102">XDocument sınıfına genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="28cd4-102">XDocument Class Overview (C#)</span></span>
<span data-ttu-id="28cd4-103">Bu konu tanıtır <xref:System.Xml.Linq.XDocument> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="28cd4-103">This topic introduces the <xref:System.Xml.Linq.XDocument> class.</span></span>  
  
## <a name="overview-of-the-xdocument-class"></a><span data-ttu-id="28cd4-104">XDocument sınıfı genel bakış</span><span class="sxs-lookup"><span data-stu-id="28cd4-104">Overview of the XDocument class</span></span>  
 <span data-ttu-id="28cd4-105"><xref:System.Xml.Linq.XDocument> Sınıfı için geçerli bir XML belgesi gerekli bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="28cd4-105">The <xref:System.Xml.Linq.XDocument> class contains the information necessary for a valid XML document.</span></span> <span data-ttu-id="28cd4-106">Bu işlem yönergeleri ve açıklamaları bir XML bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="28cd4-106">This includes an XML declaration, processing instructions, and comments.</span></span>  
  
 <span data-ttu-id="28cd4-107">Yalnızca oluşturmak zorunda Not <xref:System.Xml.Linq.XDocument> tarafından sağlanan belirli işlevleri gerektirip gerektirmediğini nesneleri <xref:System.Xml.Linq.XDocument> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="28cd4-107">Note that you only have to create <xref:System.Xml.Linq.XDocument> objects if you require the specific functionality provided by the <xref:System.Xml.Linq.XDocument> class.</span></span> <span data-ttu-id="28cd4-108">Çoğu durumda, doğrudan çalışabileceğiniz <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="28cd4-108">In many circumstances, you can work directly with <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="28cd4-109">Doğrudan çalışma <xref:System.Xml.Linq.XElement> daha basit bir programlama modelidir.</span><span class="sxs-lookup"><span data-stu-id="28cd4-109">Working directly with <xref:System.Xml.Linq.XElement> is a simpler programming model.</span></span>  
  
 <span data-ttu-id="28cd4-110"><xref:System.Xml.Linq.XDocument> türetilen <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="28cd4-110"><xref:System.Xml.Linq.XDocument> derives from <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="28cd4-111">Bu nedenle, alt düğümler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="28cd4-111">Therefore, it can contain child nodes.</span></span> <span data-ttu-id="28cd4-112">Ancak, <xref:System.Xml.Linq.XDocument> nesneleri, yalnızca bir alt olabilir <xref:System.Xml.Linq.XElement> düğümü.</span><span class="sxs-lookup"><span data-stu-id="28cd4-112">However, <xref:System.Xml.Linq.XDocument> objects can have only one child <xref:System.Xml.Linq.XElement> node.</span></span> <span data-ttu-id="28cd4-113">Bu bir XML belgesinde yalnızca bir kök öğe olabileceğini XML standart yansıtır.</span><span class="sxs-lookup"><span data-stu-id="28cd4-113">This reflects the XML standard that there can be only one root element in an XML document.</span></span>  
  
## <a name="components-of-xdocument"></a><span data-ttu-id="28cd4-114">XDocument bileşenleri</span><span class="sxs-lookup"><span data-stu-id="28cd4-114">Components of XDocument</span></span>  
 <span data-ttu-id="28cd4-115">Bir <xref:System.Xml.Linq.XDocument> aşağıdaki öğeleri içerebilir:</span><span class="sxs-lookup"><span data-stu-id="28cd4-115">An <xref:System.Xml.Linq.XDocument> can contain the following elements:</span></span>  
  
-   <span data-ttu-id="28cd4-116">Bir <xref:System.Xml.Linq.XDeclaration> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="28cd4-116">One <xref:System.Xml.Linq.XDeclaration> object.</span></span> <span data-ttu-id="28cd4-117"><xref:System.Xml.Linq.XDeclaration> bir XML bildirimi ilgili bölümleri belirtmenize olanak sağlar: belgenin kodlama XML sürümü ve XML belgesi tek başına olup.</span><span class="sxs-lookup"><span data-stu-id="28cd4-117"><xref:System.Xml.Linq.XDeclaration> enables you to specify the pertinent parts of an XML declaration: the XML version, the encoding of the document, and whether the XML document is stand-alone.</span></span>  
  
-   <span data-ttu-id="28cd4-118">Bir <xref:System.Xml.Linq.XElement> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="28cd4-118">One <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="28cd4-119">XML belgesinin kök düğümü budur.</span><span class="sxs-lookup"><span data-stu-id="28cd4-119">This is the root node of the XML document.</span></span>  
  
-   <span data-ttu-id="28cd4-120">Herhangi bir sayıda <xref:System.Xml.Linq.XProcessingInstruction> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="28cd4-120">Any number of <xref:System.Xml.Linq.XProcessingInstruction> objects.</span></span> <span data-ttu-id="28cd4-121">Bir işleme yönergesi XML işleyen bir uygulama için bilgi iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="28cd4-121">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
-   <span data-ttu-id="28cd4-122">Herhangi bir sayıda <xref:System.Xml.Linq.XComment> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="28cd4-122">Any number of <xref:System.Xml.Linq.XComment> objects.</span></span> <span data-ttu-id="28cd4-123">Açıklamaları kök öğesi için eşdüzey olacaktır.</span><span class="sxs-lookup"><span data-stu-id="28cd4-123">The comments will be siblings to the root element.</span></span> <span data-ttu-id="28cd4-124"><xref:System.Xml.Linq.XComment> Birlikte bir açıklama başlatmak bir XML belgesi için geçerli değil çünkü nesne listesinde, ilk bağımsız değişken olamaz.</span><span class="sxs-lookup"><span data-stu-id="28cd4-124">The <xref:System.Xml.Linq.XComment> object cannot be the first argument in the list, because it is not valid for an XML document to start with a comment.</span></span>  
  
-   <span data-ttu-id="28cd4-125">Bir <xref:System.Xml.Linq.XDocumentType> DTD için.</span><span class="sxs-lookup"><span data-stu-id="28cd4-125">One <xref:System.Xml.Linq.XDocumentType> for the DTD.</span></span>  
  
 <span data-ttu-id="28cd4-126">Ne zaman, seri bir <xref:System.Xml.Linq.XDocument>olsa bile `XDocument.Declaration` olan `null`, yazıcı varsa çıktı XML bildirimi olacaktır `Writer.Settings.OmitXmlDeclaration` kümesine `false` (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="28cd4-126">When you serialize an <xref:System.Xml.Linq.XDocument>, even if `XDocument.Declaration` is `null`, the output will have an XML declaration if the writer has `Writer.Settings.OmitXmlDeclaration` set to `false` (the default).</span></span>  
  
 <span data-ttu-id="28cd4-127">Varsayılan olarak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sürüm "1.0" olarak ayarlar ve "utf-8" kodlama ayarlar.</span><span class="sxs-lookup"><span data-stu-id="28cd4-127">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sets the version to "1.0", and sets the encoding to "utf-8".</span></span>  
  
## <a name="using-xelement-without-xdocument"></a><span data-ttu-id="28cd4-128">XElement XDocument olmadan kullanma</span><span class="sxs-lookup"><span data-stu-id="28cd4-128">Using XElement without XDocument</span></span>  
 <span data-ttu-id="28cd4-129">Daha önce belirtildiği gibi <xref:System.Xml.Linq.XElement> sınıfı, ana sınıfında [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programlama arabirimi.</span><span class="sxs-lookup"><span data-stu-id="28cd4-129">As previously mentioned, the <xref:System.Xml.Linq.XElement> class is the main class in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface.</span></span> <span data-ttu-id="28cd4-130">Çoğu durumda, bir belge oluşturun, uygulamanızın gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="28cd4-130">In many cases, your application will not require that you create a document.</span></span> <span data-ttu-id="28cd4-131">Kullanarak <xref:System.Xml.Linq.XElement> sınıfı, bir XML ağacı oluşturmak, diğer XML ağaçları ekleyin, XML ağacını değiştirmek ve dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="28cd4-131">By using the <xref:System.Xml.Linq.XElement> class, you can create an XML tree, add other XML trees to it, modify the XML tree, and save it.</span></span>  
  
## <a name="using-xdocument"></a><span data-ttu-id="28cd4-132">XDocument kullanma</span><span class="sxs-lookup"><span data-stu-id="28cd4-132">Using XDocument</span></span>  
 <span data-ttu-id="28cd4-133">Oluşturmak için bir <xref:System.Xml.Linq.XDocument>, oluşturmak için yaptığınız gibi işlev yapım kullanmak <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="28cd4-133">To construct an <xref:System.Xml.Linq.XDocument>, use functional construction, just like you do to construct <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="28cd4-134">Aşağıdaki kod oluşturur bir <xref:System.Xml.Linq.XDocument> nesne ve onunla ilişkili bulunan nesneleri.</span><span class="sxs-lookup"><span data-stu-id="28cd4-134">The following code creates an <xref:System.Xml.Linq.XDocument> object and its associated contained objects.</span></span>  
  
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
  
 <span data-ttu-id="28cd4-135">Dosya test.xml incelediğinizde, aşağıdaki çıkış alın:</span><span class="sxs-lookup"><span data-stu-id="28cd4-135">When you examine the file test.xml, you get the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="28cd4-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="28cd4-136">See Also</span></span>  
 [<span data-ttu-id="28cd4-137">LINQ-XML programlamaya genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="28cd4-137">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
