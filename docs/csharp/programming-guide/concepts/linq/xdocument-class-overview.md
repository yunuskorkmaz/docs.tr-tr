---
title: XDocument sınıfına genel bakış (C#)
description: C# ' deki XDocument sınıfı, XML bildirimi, işleme yönergeleri ve açıklamalar dahil olmak üzere geçerli bir XML belgesi için gereken bilgileri Içerir.
ms.date: 07/20/2015
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
ms.openlocfilehash: 6d522cef25e99e4a5ea54e644855c8dfa7a05f4a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302197"
---
# <a name="xdocument-class-overview-c"></a><span data-ttu-id="0fc40-103">XDocument sınıfına genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="0fc40-103">XDocument Class Overview (C#)</span></span>
<span data-ttu-id="0fc40-104">Bu konu sınıfı tanıtır <xref:System.Xml.Linq.XDocument> .</span><span class="sxs-lookup"><span data-stu-id="0fc40-104">This topic introduces the <xref:System.Xml.Linq.XDocument> class.</span></span>  
  
## <a name="overview-of-the-xdocument-class"></a><span data-ttu-id="0fc40-105">XDocument sınıfına genel bakış</span><span class="sxs-lookup"><span data-stu-id="0fc40-105">Overview of the XDocument class</span></span>  
 <span data-ttu-id="0fc40-106"><xref:System.Xml.Linq.XDocument>Sınıfı, geçerli BIR XML belgesi için gereken bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="0fc40-106">The <xref:System.Xml.Linq.XDocument> class contains the information necessary for a valid XML document.</span></span> <span data-ttu-id="0fc40-107">Buna bir XML bildirimi, işleme yönergeleri ve açıklamalar dahildir.</span><span class="sxs-lookup"><span data-stu-id="0fc40-107">This includes an XML declaration, processing instructions, and comments.</span></span>  
  
 <span data-ttu-id="0fc40-108">Yalnızca <xref:System.Xml.Linq.XDocument> sınıf tarafından sunulan belirli işlevselliğe ihtiyacınız varsa nesneler oluşturmanız gerektiğini unutmayın <xref:System.Xml.Linq.XDocument> .</span><span class="sxs-lookup"><span data-stu-id="0fc40-108">Note that you only have to create <xref:System.Xml.Linq.XDocument> objects if you require the specific functionality provided by the <xref:System.Xml.Linq.XDocument> class.</span></span> <span data-ttu-id="0fc40-109">Birçok durumda, doğrudan ile çalışabilirsiniz <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="0fc40-109">In many circumstances, you can work directly with <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="0fc40-110">İle doğrudan çalışmak <xref:System.Xml.Linq.XElement> daha basit bir programlama modelidir.</span><span class="sxs-lookup"><span data-stu-id="0fc40-110">Working directly with <xref:System.Xml.Linq.XElement> is a simpler programming model.</span></span>  
  
 <span data-ttu-id="0fc40-111"><xref:System.Xml.Linq.XDocument>türetiliyor <xref:System.Xml.Linq.XContainer> .</span><span class="sxs-lookup"><span data-stu-id="0fc40-111"><xref:System.Xml.Linq.XDocument> derives from <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="0fc40-112">Bu nedenle, alt düğümler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="0fc40-112">Therefore, it can contain child nodes.</span></span> <span data-ttu-id="0fc40-113">Ancak, <xref:System.Xml.Linq.XDocument> nesneler yalnızca bir alt düğüme sahip olabilir <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="0fc40-113">However, <xref:System.Xml.Linq.XDocument> objects can have only one child <xref:System.Xml.Linq.XElement> node.</span></span> <span data-ttu-id="0fc40-114">Bu, bir XML belgesinde yalnızca bir kök öğe olabilecek XML standardını yansıtır.</span><span class="sxs-lookup"><span data-stu-id="0fc40-114">This reflects the XML standard that there can be only one root element in an XML document.</span></span>  
  
## <a name="components-of-xdocument"></a><span data-ttu-id="0fc40-115">XDocument bileşenleri</span><span class="sxs-lookup"><span data-stu-id="0fc40-115">Components of XDocument</span></span>  
 <span data-ttu-id="0fc40-116">, <xref:System.Xml.Linq.XDocument> Aşağıdaki öğeleri içerebilir:</span><span class="sxs-lookup"><span data-stu-id="0fc40-116">An <xref:System.Xml.Linq.XDocument> can contain the following elements:</span></span>  
  
- <span data-ttu-id="0fc40-117">Bir <xref:System.Xml.Linq.XDeclaration> nesne.</span><span class="sxs-lookup"><span data-stu-id="0fc40-117">One <xref:System.Xml.Linq.XDeclaration> object.</span></span> <span data-ttu-id="0fc40-118"><xref:System.Xml.Linq.XDeclaration>XML bildiriminin ilgili parçalarını belirtmenizi sağlar: XML sürümü, belgenin kodlaması ve XML belgesinin tek başına olup olmadığı.</span><span class="sxs-lookup"><span data-stu-id="0fc40-118"><xref:System.Xml.Linq.XDeclaration> enables you to specify the pertinent parts of an XML declaration: the XML version, the encoding of the document, and whether the XML document is stand-alone.</span></span>  
  
- <span data-ttu-id="0fc40-119">Bir <xref:System.Xml.Linq.XElement> nesne.</span><span class="sxs-lookup"><span data-stu-id="0fc40-119">One <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="0fc40-120">Bu, XML belgesinin kök düğümüdür.</span><span class="sxs-lookup"><span data-stu-id="0fc40-120">This is the root node of the XML document.</span></span>  
  
- <span data-ttu-id="0fc40-121">Herhangi bir sayıda <xref:System.Xml.Linq.XProcessingInstruction> nesne.</span><span class="sxs-lookup"><span data-stu-id="0fc40-121">Any number of <xref:System.Xml.Linq.XProcessingInstruction> objects.</span></span> <span data-ttu-id="0fc40-122">Bir işleme yönergesi, XML 'i işleyen bir uygulamayla ilgili bilgiler iletir.</span><span class="sxs-lookup"><span data-stu-id="0fc40-122">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
- <span data-ttu-id="0fc40-123">Herhangi bir sayıda <xref:System.Xml.Linq.XComment> nesne.</span><span class="sxs-lookup"><span data-stu-id="0fc40-123">Any number of <xref:System.Xml.Linq.XComment> objects.</span></span> <span data-ttu-id="0fc40-124">Yorumlar, kök öğesi için eşdüzey olacak.</span><span class="sxs-lookup"><span data-stu-id="0fc40-124">The comments will be siblings to the root element.</span></span> <span data-ttu-id="0fc40-125"><xref:System.Xml.Linq.XComment>Nesne, BIR XML belgesinin bir açıklama ile başlaması için geçerli olmadığından, listedeki ilk bağımsız değişken olamaz.</span><span class="sxs-lookup"><span data-stu-id="0fc40-125">The <xref:System.Xml.Linq.XComment> object cannot be the first argument in the list, because it is not valid for an XML document to start with a comment.</span></span>  
  
- <span data-ttu-id="0fc40-126"><xref:System.Xml.Linq.XDocumentType>DTD için bir tane.</span><span class="sxs-lookup"><span data-stu-id="0fc40-126">One <xref:System.Xml.Linq.XDocumentType> for the DTD.</span></span>  
  
 <span data-ttu-id="0fc40-127">Bir seri hale getirmek istediğinizde,, <xref:System.Xml.Linq.XDocument> `XDocument.Declaration` `null` yazıcı olarak AYARLANDıYSA çıkış bir XML bildirimine sahip olacaktır `Writer.Settings.OmitXmlDeclaration` `false` (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="0fc40-127">When you serialize an <xref:System.Xml.Linq.XDocument>, even if `XDocument.Declaration` is `null`, the output will have an XML declaration if the writer has `Writer.Settings.OmitXmlDeclaration` set to `false` (the default).</span></span>  
  
 <span data-ttu-id="0fc40-128">Varsayılan olarak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sürümü "1,0" olarak ayarlar ve kodlamayı "UTF-8" olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0fc40-128">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sets the version to "1.0", and sets the encoding to "utf-8".</span></span>  
  
## <a name="using-xelement-without-xdocument"></a><span data-ttu-id="0fc40-129">XDocument olmadan XElement kullanma</span><span class="sxs-lookup"><span data-stu-id="0fc40-129">Using XElement without XDocument</span></span>  
 <span data-ttu-id="0fc40-130">Daha önce belirtildiği gibi, <xref:System.Xml.Linq.XElement> sınıfı [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programlama arabirimindeki ana sınıftır.</span><span class="sxs-lookup"><span data-stu-id="0fc40-130">As previously mentioned, the <xref:System.Xml.Linq.XElement> class is the main class in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface.</span></span> <span data-ttu-id="0fc40-131">Çoğu durumda, uygulamanız bir belge oluşturmanızı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="0fc40-131">In many cases, your application will not require that you create a document.</span></span> <span data-ttu-id="0fc40-132"><xref:System.Xml.Linq.XElement>Sınıfını kullanarak BIR XML ağacı oluşturabilir, buna başka xml ağaçları ekleyebilir, xml ağacını değiştirebilir ve kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0fc40-132">By using the <xref:System.Xml.Linq.XElement> class, you can create an XML tree, add other XML trees to it, modify the XML tree, and save it.</span></span>  
  
## <a name="using-xdocument"></a><span data-ttu-id="0fc40-133">XDocument kullanma</span><span class="sxs-lookup"><span data-stu-id="0fc40-133">Using XDocument</span></span>  
 <span data-ttu-id="0fc40-134">Oluşturmak için <xref:System.Xml.Linq.XDocument> , nesneleri oluşturmak için yaptığınız gibi işlevsel oluşturma kullanın <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="0fc40-134">To construct an <xref:System.Xml.Linq.XDocument>, use functional construction, just like you do to construct <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="0fc40-135">Aşağıdaki kod bir <xref:System.Xml.Linq.XDocument> nesne ve ilişkili içerilen nesneleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0fc40-135">The following code creates an <xref:System.Xml.Linq.XDocument> object and its associated contained objects.</span></span>  
  
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
  
 <span data-ttu-id="0fc40-136">Dosyayı test.xml incelediğinizde aşağıdaki çıktıyı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="0fc40-136">When you examine the file test.xml, you get the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0fc40-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0fc40-137">See also</span></span>

- [<span data-ttu-id="0fc40-138">LINQ to XML programlamaya genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="0fc40-138">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
