---
title: XDocument Sınıf Genel Bakış (C#)
ms.date: 07/20/2015
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
ms.openlocfilehash: de49dc071d22dd77dddea29ca114663261e3edda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69590848"
---
# <a name="xdocument-class-overview-c"></a><span data-ttu-id="30f36-102">XDocument Sınıf Genel Bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="30f36-102">XDocument Class Overview (C#)</span></span>
<span data-ttu-id="30f36-103">Bu konu <xref:System.Xml.Linq.XDocument> sınıf tanıttı.</span><span class="sxs-lookup"><span data-stu-id="30f36-103">This topic introduces the <xref:System.Xml.Linq.XDocument> class.</span></span>  
  
## <a name="overview-of-the-xdocument-class"></a><span data-ttu-id="30f36-104">XDocument sınıfına genel bakış</span><span class="sxs-lookup"><span data-stu-id="30f36-104">Overview of the XDocument class</span></span>  
 <span data-ttu-id="30f36-105">Sınıf, <xref:System.Xml.Linq.XDocument> geçerli bir XML belgesi için gerekli bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="30f36-105">The <xref:System.Xml.Linq.XDocument> class contains the information necessary for a valid XML document.</span></span> <span data-ttu-id="30f36-106">Buna bir XML bildirimi, işleme yönergeleri ve açıklamalar dahildir.</span><span class="sxs-lookup"><span data-stu-id="30f36-106">This includes an XML declaration, processing instructions, and comments.</span></span>  
  
 <span data-ttu-id="30f36-107">Yalnızca <xref:System.Xml.Linq.XDocument> sınıf tarafından sağlanan <xref:System.Xml.Linq.XDocument> belirli işlevselliği gerekiyorsa nesneler oluşturmanız gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="30f36-107">Note that you only have to create <xref:System.Xml.Linq.XDocument> objects if you require the specific functionality provided by the <xref:System.Xml.Linq.XDocument> class.</span></span> <span data-ttu-id="30f36-108">Birçok durumda, doğrudan . <xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="30f36-108">In many circumstances, you can work directly with <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="30f36-109">Doğrudan çalışmak <xref:System.Xml.Linq.XElement> daha basit bir programlama modelidir.</span><span class="sxs-lookup"><span data-stu-id="30f36-109">Working directly with <xref:System.Xml.Linq.XElement> is a simpler programming model.</span></span>  
  
 <span data-ttu-id="30f36-110"><xref:System.Xml.Linq.XDocument><xref:System.Xml.Linq.XContainer>türetilmiştir.</span><span class="sxs-lookup"><span data-stu-id="30f36-110"><xref:System.Xml.Linq.XDocument> derives from <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="30f36-111">Bu nedenle, alt düğümleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="30f36-111">Therefore, it can contain child nodes.</span></span> <span data-ttu-id="30f36-112">Ancak, <xref:System.Xml.Linq.XDocument> nesnelerin yalnızca bir <xref:System.Xml.Linq.XElement> alt düğüm olabilir.</span><span class="sxs-lookup"><span data-stu-id="30f36-112">However, <xref:System.Xml.Linq.XDocument> objects can have only one child <xref:System.Xml.Linq.XElement> node.</span></span> <span data-ttu-id="30f36-113">Bu, bir XML belgesinde yalnızca bir kök öğesi olabileceği yönündeki XML standardını yansıtır.</span><span class="sxs-lookup"><span data-stu-id="30f36-113">This reflects the XML standard that there can be only one root element in an XML document.</span></span>  
  
## <a name="components-of-xdocument"></a><span data-ttu-id="30f36-114">XDocument bileşenleri</span><span class="sxs-lookup"><span data-stu-id="30f36-114">Components of XDocument</span></span>  
 <span data-ttu-id="30f36-115">An <xref:System.Xml.Linq.XDocument> aşağıdaki öğeleri içerebilir:</span><span class="sxs-lookup"><span data-stu-id="30f36-115">An <xref:System.Xml.Linq.XDocument> can contain the following elements:</span></span>  
  
- <span data-ttu-id="30f36-116">Bir <xref:System.Xml.Linq.XDeclaration> nesne.</span><span class="sxs-lookup"><span data-stu-id="30f36-116">One <xref:System.Xml.Linq.XDeclaration> object.</span></span> <span data-ttu-id="30f36-117"><xref:System.Xml.Linq.XDeclaration>XML bildiriminin ilgili bölümlerini belirtmenizi sağlar: XML sürümü, belgenin kodlanması ve XML belgesinin tek başına olup olmadığı.</span><span class="sxs-lookup"><span data-stu-id="30f36-117"><xref:System.Xml.Linq.XDeclaration> enables you to specify the pertinent parts of an XML declaration: the XML version, the encoding of the document, and whether the XML document is stand-alone.</span></span>  
  
- <span data-ttu-id="30f36-118">Bir <xref:System.Xml.Linq.XElement> nesne.</span><span class="sxs-lookup"><span data-stu-id="30f36-118">One <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="30f36-119">Bu, XML belgesinin kök düğümüdür.</span><span class="sxs-lookup"><span data-stu-id="30f36-119">This is the root node of the XML document.</span></span>  
  
- <span data-ttu-id="30f36-120">Herhangi bir <xref:System.Xml.Linq.XProcessingInstruction> sayıda nesne.</span><span class="sxs-lookup"><span data-stu-id="30f36-120">Any number of <xref:System.Xml.Linq.XProcessingInstruction> objects.</span></span> <span data-ttu-id="30f36-121">İşleme yönergesi, bilgileri XML'i işleyen bir uygulamaya iletir.</span><span class="sxs-lookup"><span data-stu-id="30f36-121">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
- <span data-ttu-id="30f36-122">Herhangi bir <xref:System.Xml.Linq.XComment> sayıda nesne.</span><span class="sxs-lookup"><span data-stu-id="30f36-122">Any number of <xref:System.Xml.Linq.XComment> objects.</span></span> <span data-ttu-id="30f36-123">Yorumlar kök öğesine kardeş olacaktır.</span><span class="sxs-lookup"><span data-stu-id="30f36-123">The comments will be siblings to the root element.</span></span> <span data-ttu-id="30f36-124">Bir <xref:System.Xml.Linq.XComment> XML belgesinin bir açıklamayla başlaması geçerli olmadığından, nesne listedeki ilk bağımsız değişken olamaz.</span><span class="sxs-lookup"><span data-stu-id="30f36-124">The <xref:System.Xml.Linq.XComment> object cannot be the first argument in the list, because it is not valid for an XML document to start with a comment.</span></span>  
  
- <span data-ttu-id="30f36-125">DTD için bir tane. <xref:System.Xml.Linq.XDocumentType></span><span class="sxs-lookup"><span data-stu-id="30f36-125">One <xref:System.Xml.Linq.XDocumentType> for the DTD.</span></span>  
  
 <span data-ttu-id="30f36-126">Bir <xref:System.Xml.Linq.XDocument>, olsa `XDocument.Declaration` `null`bile, yazar `Writer.Settings.OmitXmlDeclaration` `false` (varsayılan) olarak ayarlanmışsa çıktıbir XML bildirimi olacaktır serialize zaman.</span><span class="sxs-lookup"><span data-stu-id="30f36-126">When you serialize an <xref:System.Xml.Linq.XDocument>, even if `XDocument.Declaration` is `null`, the output will have an XML declaration if the writer has `Writer.Settings.OmitXmlDeclaration` set to `false` (the default).</span></span>  
  
 <span data-ttu-id="30f36-127">Varsayılan olarak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sürümü "1.0" olarak ayarlar ve kodlamayı "utf-8" olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="30f36-127">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sets the version to "1.0", and sets the encoding to "utf-8".</span></span>  
  
## <a name="using-xelement-without-xdocument"></a><span data-ttu-id="30f36-128">XDocument olmadan XElement kullanma</span><span class="sxs-lookup"><span data-stu-id="30f36-128">Using XElement without XDocument</span></span>  
 <span data-ttu-id="30f36-129">Daha önce de belirtildiği <xref:System.Xml.Linq.XElement> gibi, sınıf [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programlama arabiriminde ana sınıftır.</span><span class="sxs-lookup"><span data-stu-id="30f36-129">As previously mentioned, the <xref:System.Xml.Linq.XElement> class is the main class in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface.</span></span> <span data-ttu-id="30f36-130">Çoğu durumda, uygulamanız bir belge oluşturmanızı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="30f36-130">In many cases, your application will not require that you create a document.</span></span> <span data-ttu-id="30f36-131"><xref:System.Xml.Linq.XElement> Sınıfı kullanarak, bir XML ağacı oluşturabilir, diğer XML ağaçları ekleyebilir, XML ağacını değiştirebilir ve kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30f36-131">By using the <xref:System.Xml.Linq.XElement> class, you can create an XML tree, add other XML trees to it, modify the XML tree, and save it.</span></span>  
  
## <a name="using-xdocument"></a><span data-ttu-id="30f36-132">XDocument'ı Kullanma</span><span class="sxs-lookup"><span data-stu-id="30f36-132">Using XDocument</span></span>  
 <span data-ttu-id="30f36-133">Nesneleri oluşturmak <xref:System.Xml.Linq.XDocument>için yaptığınız gibi, işlevsel bir <xref:System.Xml.Linq.XElement> yapı oluşturmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="30f36-133">To construct an <xref:System.Xml.Linq.XDocument>, use functional construction, just like you do to construct <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="30f36-134">Aşağıdaki kod bir <xref:System.Xml.Linq.XDocument> nesne oluşturur ve ilişkili içerdiği nesneleri.</span><span class="sxs-lookup"><span data-stu-id="30f36-134">The following code creates an <xref:System.Xml.Linq.XDocument> object and its associated contained objects.</span></span>  
  
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
  
 <span data-ttu-id="30f36-135">Dosya test.xml'i incelediğinizde, aşağıdaki çıktıyı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="30f36-135">When you examine the file test.xml, you get the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="30f36-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30f36-136">See also</span></span>

- [<span data-ttu-id="30f36-137">LINQ - XML Programlamaya Genel Bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="30f36-137">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
