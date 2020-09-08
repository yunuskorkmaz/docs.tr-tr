---
title: XDocument sınıfına genel bakış
description: LINQ to XML XDocument sınıfı, geçerli bir XML belgesi için gereken bilgileri içerir. Çoğu durumda, bir XDocument nesnesinin işlevselliğine gerek kalmaz ve bunun yerine bir XElement nesnesi kullanabilirsiniz.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
ms.openlocfilehash: c26b7ac42733aad24d831f4a0a181e0fd8275eaf
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552925"
---
# <a name="xdocument-class-overview"></a><span data-ttu-id="72c16-104">XDocument sınıfına genel bakış</span><span class="sxs-lookup"><span data-stu-id="72c16-104">XDocument class overview</span></span>

<span data-ttu-id="72c16-105"><xref:System.Xml.Linq.XDocument>Sınıfı, BIR XML bildirimi, işleme yönergeleri ve açıklamalar içeren geçerli BIR XML belgesi için gereken bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="72c16-105">The <xref:System.Xml.Linq.XDocument> class contains the information necessary for a valid XML document, which includes an XML declaration, processing instructions, and comments.</span></span>

<span data-ttu-id="72c16-106">Yalnızca <xref:System.Xml.Linq.XDocument> sınıf tarafından sunulan belirli işlevselliğe ihtiyacınız varsa nesneler oluşturmanız gerekir <xref:System.Xml.Linq.XDocument> .</span><span class="sxs-lookup"><span data-stu-id="72c16-106">You only have to create <xref:System.Xml.Linq.XDocument> objects if you require the specific functionality provided by the <xref:System.Xml.Linq.XDocument> class.</span></span> <span data-ttu-id="72c16-107">Birçok durumda, doğrudan ile çalışabilirsiniz <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="72c16-107">In many circumstances, you can work directly with <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="72c16-108">İle doğrudan çalışmak <xref:System.Xml.Linq.XElement> daha basit bir programlama modelidir.</span><span class="sxs-lookup"><span data-stu-id="72c16-108">Working directly with <xref:System.Xml.Linq.XElement> is a simpler programming model.</span></span>

<span data-ttu-id="72c16-109"><xref:System.Xml.Linq.XDocument> öğesinden türetilir <xref:System.Xml.Linq.XContainer> , bu nedenle alt düğümler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="72c16-109"><xref:System.Xml.Linq.XDocument> derives from <xref:System.Xml.Linq.XContainer>, so it can contain child nodes.</span></span> <span data-ttu-id="72c16-110">Ancak, <xref:System.Xml.Linq.XDocument> nesneler yalnızca bir alt düğüme sahip olabilir <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="72c16-110">However, <xref:System.Xml.Linq.XDocument> objects can have only one child <xref:System.Xml.Linq.XElement> node.</span></span> <span data-ttu-id="72c16-111">Bu, bir XML belgesinde yalnızca bir kök öğe olabilecek XML standardını yansıtır.</span><span class="sxs-lookup"><span data-stu-id="72c16-111">This reflects the XML standard that there can be only one root element in an XML document.</span></span>

## <a name="components-of-xdocument"></a><span data-ttu-id="72c16-112">XDocument bileşenleri</span><span class="sxs-lookup"><span data-stu-id="72c16-112">Components of XDocument</span></span>

<span data-ttu-id="72c16-113">, <xref:System.Xml.Linq.XDocument> Aşağıdaki öğeleri içerebilir:</span><span class="sxs-lookup"><span data-stu-id="72c16-113">An <xref:System.Xml.Linq.XDocument> can contain the following elements:</span></span>

- <span data-ttu-id="72c16-114">Bir <xref:System.Xml.Linq.XDeclaration> nesne.</span><span class="sxs-lookup"><span data-stu-id="72c16-114">One <xref:System.Xml.Linq.XDeclaration> object.</span></span> <span data-ttu-id="72c16-115"><xref:System.Xml.Linq.XDeclaration> XML bildiriminin ilgili parçalarını belirtmenizi sağlar: XML sürümü, belgenin kodlaması ve XML belgesinin tek başına olup olmadığı.</span><span class="sxs-lookup"><span data-stu-id="72c16-115"><xref:System.Xml.Linq.XDeclaration> enables you to specify the pertinent parts of an XML declaration: the XML version, the encoding of the document, and whether the XML document is standalone.</span></span>
- <span data-ttu-id="72c16-116">Bir <xref:System.Xml.Linq.XElement> nesne.</span><span class="sxs-lookup"><span data-stu-id="72c16-116">One <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="72c16-117">Bu nesne, XML belgesinin kök düğümüdür.</span><span class="sxs-lookup"><span data-stu-id="72c16-117">This object is the root node of the XML document.</span></span>
- <span data-ttu-id="72c16-118">Herhangi bir sayıda <xref:System.Xml.Linq.XProcessingInstruction> nesne.</span><span class="sxs-lookup"><span data-stu-id="72c16-118">Any number of <xref:System.Xml.Linq.XProcessingInstruction> objects.</span></span> <span data-ttu-id="72c16-119">Bir işleme yönergesi, XML 'i işleyen bir uygulamayla ilgili bilgiler iletir.</span><span class="sxs-lookup"><span data-stu-id="72c16-119">A processing instruction communicates information to an application that processes the XML.</span></span>
- <span data-ttu-id="72c16-120">Herhangi bir sayıda <xref:System.Xml.Linq.XComment> nesne.</span><span class="sxs-lookup"><span data-stu-id="72c16-120">Any number of <xref:System.Xml.Linq.XComment> objects.</span></span> <span data-ttu-id="72c16-121">Yorumlar, kök öğesi için eşdüzey olacak.</span><span class="sxs-lookup"><span data-stu-id="72c16-121">The comments will be siblings to the root element.</span></span> <span data-ttu-id="72c16-122"><xref:System.Xml.Linq.XComment>Nesne, BIR XML belgesinin bir açıklama ile başlaması için geçerli olmadığından, listedeki ilk bağımsız değişken olamaz.</span><span class="sxs-lookup"><span data-stu-id="72c16-122">The <xref:System.Xml.Linq.XComment> object can't be the first argument in the list, because it's not valid for an XML document to start with a comment.</span></span>
- <span data-ttu-id="72c16-123"><xref:System.Xml.Linq.XDocumentType>DTD için bir tane.</span><span class="sxs-lookup"><span data-stu-id="72c16-123">One <xref:System.Xml.Linq.XDocumentType> for the DTD.</span></span>

<span data-ttu-id="72c16-124">Bir seri hale getirmek istediğinizde,, <xref:System.Xml.Linq.XDocument> `XDocument.Declaration` `null` yazıcı olarak AYARLANDıYSA çıkış bir XML bildirimine sahip olacaktır `Writer.Settings.OmitXmlDeclaration` `false` (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="72c16-124">When you serialize an <xref:System.Xml.Linq.XDocument>, even if `XDocument.Declaration` is `null`, the output will have an XML declaration if the writer has `Writer.Settings.OmitXmlDeclaration` set to `false` (the default).</span></span>

<span data-ttu-id="72c16-125">Varsayılan olarak, LINQ to XML sürümü "1,0" olarak ayarlar ve kodlamayı "UTF-8" olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="72c16-125">By default, LINQ to XML sets the version to "1.0", and sets the encoding to "utf-8".</span></span>

## <a name="use-xelement-without-xdocument"></a><span data-ttu-id="72c16-126">XDocument olmadan XElement kullanma</span><span class="sxs-lookup"><span data-stu-id="72c16-126">Use XElement without XDocument</span></span>

<span data-ttu-id="72c16-127">Daha önce belirtildiği gibi, <xref:System.Xml.Linq.XElement> sınıfı LINQ to XML programlama arabirimindeki ana sınıftır.</span><span class="sxs-lookup"><span data-stu-id="72c16-127">As previously mentioned, the <xref:System.Xml.Linq.XElement> class is the main class in the LINQ to XML programming interface.</span></span> <span data-ttu-id="72c16-128">Çoğu durumda, uygulamanız bir belge oluşturmanızı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="72c16-128">In many cases, your application won't require that you create a document.</span></span> <span data-ttu-id="72c16-129">Sınıfını kullanarak şunları <xref:System.Xml.Linq.XElement> yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="72c16-129">By using the <xref:System.Xml.Linq.XElement> class, you can:</span></span>

- <span data-ttu-id="72c16-130">Bir XML ağacı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="72c16-130">Create an XML tree.</span></span>
- <span data-ttu-id="72c16-131">Buna başka XML ağaçları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="72c16-131">Add other XML trees to it.</span></span>
- <span data-ttu-id="72c16-132">XML ağacını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="72c16-132">Modify the XML tree.</span></span>
- <span data-ttu-id="72c16-133">Kaydedin.</span><span class="sxs-lookup"><span data-stu-id="72c16-133">Save it.</span></span>

## <a name="use-xdocument"></a><span data-ttu-id="72c16-134">XDocument kullanma</span><span class="sxs-lookup"><span data-stu-id="72c16-134">Use XDocument</span></span>

<span data-ttu-id="72c16-135">Oluşturmak için <xref:System.Xml.Linq.XDocument> , nesneleri oluşturmak için yaptığınız gibi işlevsel oluşturma kullanın <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="72c16-135">To construct an <xref:System.Xml.Linq.XDocument>, use functional construction, just like you do to construct <xref:System.Xml.Linq.XElement> objects.</span></span>

<span data-ttu-id="72c16-136">Aşağıdaki örnek bir <xref:System.Xml.Linq.XDocument> nesnesi ve ilişkili içerilen nesnelerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="72c16-136">The following example creates an <xref:System.Xml.Linq.XDocument> object and its associated contained objects.</span></span>

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

```vb
Dim doc As XDocument = <?xml version="1.0" encoding="utf-8"?>
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
doc.Save("test.xml")
```

<span data-ttu-id="72c16-137">Örnek bu çıktıyı test.xml üretir:</span><span class="sxs-lookup"><span data-stu-id="72c16-137">The example produces this output in test.xml:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="72c16-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72c16-138">See also</span></span>

- [<span data-ttu-id="72c16-139">LINQ to XML genel bakış</span><span class="sxs-lookup"><span data-stu-id="72c16-139">LINQ to XML overview</span></span>](linq-xml-overview.md)
