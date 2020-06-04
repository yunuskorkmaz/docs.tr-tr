---
title: XDocument Sınıfına Genel Bakış
ms.date: 07/20/2015
ms.assetid: 45cb7e71-196a-47da-bfe9-7a5589db1eed
ms.openlocfilehash: 90c97349006407b2eca861be31080ec17901fa5b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413238"
---
# <a name="xdocument-class-overview-visual-basic"></a><span data-ttu-id="85139-102">XDocument sınıfına genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85139-102">XDocument Class Overview (Visual Basic)</span></span>
<span data-ttu-id="85139-103">Bu konu sınıfı tanıtır <xref:System.Xml.Linq.XDocument> .</span><span class="sxs-lookup"><span data-stu-id="85139-103">This topic introduces the <xref:System.Xml.Linq.XDocument> class.</span></span>  
  
## <a name="overview-of-the-xdocument-class"></a><span data-ttu-id="85139-104">XDocument sınıfına genel bakış</span><span class="sxs-lookup"><span data-stu-id="85139-104">Overview of the XDocument class</span></span>  
 <span data-ttu-id="85139-105"><xref:System.Xml.Linq.XDocument>Sınıfı, geçerli BIR XML belgesi için gereken bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="85139-105">The <xref:System.Xml.Linq.XDocument> class contains the information necessary for a valid XML document.</span></span> <span data-ttu-id="85139-106">Buna bir XML bildirimi, işleme yönergeleri ve açıklamalar dahildir.</span><span class="sxs-lookup"><span data-stu-id="85139-106">This includes an XML declaration, processing instructions, and comments.</span></span>  
  
 <span data-ttu-id="85139-107">Yalnızca <xref:System.Xml.Linq.XDocument> sınıf tarafından sunulan belirli işlevselliğe ihtiyacınız varsa nesneler oluşturmanız gerektiğini unutmayın <xref:System.Xml.Linq.XDocument> .</span><span class="sxs-lookup"><span data-stu-id="85139-107">Note that you only have to create <xref:System.Xml.Linq.XDocument> objects if you require the specific functionality provided by the <xref:System.Xml.Linq.XDocument> class.</span></span> <span data-ttu-id="85139-108">Birçok durumda, doğrudan ile çalışabilirsiniz <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="85139-108">In many circumstances, you can work directly with <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="85139-109">İle doğrudan çalışmak <xref:System.Xml.Linq.XElement> daha basit bir programlama modelidir.</span><span class="sxs-lookup"><span data-stu-id="85139-109">Working directly with <xref:System.Xml.Linq.XElement> is a simpler programming model.</span></span>  
  
 <span data-ttu-id="85139-110"><xref:System.Xml.Linq.XDocument>türetiliyor <xref:System.Xml.Linq.XContainer> .</span><span class="sxs-lookup"><span data-stu-id="85139-110"><xref:System.Xml.Linq.XDocument> derives from <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="85139-111">Bu nedenle, alt düğümler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="85139-111">Therefore, it can contain child nodes.</span></span> <span data-ttu-id="85139-112">Ancak, <xref:System.Xml.Linq.XDocument> nesneler yalnızca bir alt düğüme sahip olabilir <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="85139-112">However, <xref:System.Xml.Linq.XDocument> objects can have only one child <xref:System.Xml.Linq.XElement> node.</span></span> <span data-ttu-id="85139-113">Bu, bir XML belgesinde yalnızca bir kök öğe olabilecek XML standardını yansıtır.</span><span class="sxs-lookup"><span data-stu-id="85139-113">This reflects the XML standard that there can be only one root element in an XML document.</span></span>  
  
## <a name="components-of-xdocument"></a><span data-ttu-id="85139-114">XDocument bileşenleri</span><span class="sxs-lookup"><span data-stu-id="85139-114">Components of XDocument</span></span>  
 <span data-ttu-id="85139-115">, <xref:System.Xml.Linq.XDocument> Aşağıdaki öğeleri içerebilir:</span><span class="sxs-lookup"><span data-stu-id="85139-115">An <xref:System.Xml.Linq.XDocument> can contain the following elements:</span></span>  
  
- <span data-ttu-id="85139-116">Bir <xref:System.Xml.Linq.XDeclaration> nesne.</span><span class="sxs-lookup"><span data-stu-id="85139-116">One <xref:System.Xml.Linq.XDeclaration> object.</span></span> <span data-ttu-id="85139-117"><xref:System.Xml.Linq.XDeclaration>XML bildiriminin ilgili parçalarını belirtmenizi sağlar: XML sürümü, belgenin kodlaması ve XML belgesinin tek başına olup olmadığı.</span><span class="sxs-lookup"><span data-stu-id="85139-117"><xref:System.Xml.Linq.XDeclaration> enables you to specify the pertinent parts of an XML declaration: the XML version, the encoding of the document, and whether the XML document is stand-alone.</span></span>  
  
- <span data-ttu-id="85139-118">Bir <xref:System.Xml.Linq.XElement> nesne.</span><span class="sxs-lookup"><span data-stu-id="85139-118">One <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="85139-119">Bu, XML belgesinin kök düğümüdür.</span><span class="sxs-lookup"><span data-stu-id="85139-119">This is the root node of the XML document.</span></span>  
  
- <span data-ttu-id="85139-120">Herhangi bir sayıda <xref:System.Xml.Linq.XProcessingInstruction> nesne.</span><span class="sxs-lookup"><span data-stu-id="85139-120">Any number of <xref:System.Xml.Linq.XProcessingInstruction> objects.</span></span> <span data-ttu-id="85139-121">Bir işleme yönergesi, XML 'i işleyen bir uygulamayla ilgili bilgiler iletir.</span><span class="sxs-lookup"><span data-stu-id="85139-121">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
- <span data-ttu-id="85139-122">Herhangi bir sayıda <xref:System.Xml.Linq.XComment> nesne.</span><span class="sxs-lookup"><span data-stu-id="85139-122">Any number of <xref:System.Xml.Linq.XComment> objects.</span></span> <span data-ttu-id="85139-123">Yorumlar, kök öğesi için eşdüzey olacak.</span><span class="sxs-lookup"><span data-stu-id="85139-123">The comments will be siblings to the root element.</span></span> <span data-ttu-id="85139-124"><xref:System.Xml.Linq.XComment>Nesne, BIR XML belgesinin bir açıklama ile başlaması için geçerli olmadığından, listedeki ilk bağımsız değişken olamaz.</span><span class="sxs-lookup"><span data-stu-id="85139-124">The <xref:System.Xml.Linq.XComment> object cannot be the first argument in the list, because it is not valid for an XML document to start with a comment.</span></span>  
  
- <span data-ttu-id="85139-125"><xref:System.Xml.Linq.XDocumentType>DTD için bir tane.</span><span class="sxs-lookup"><span data-stu-id="85139-125">One <xref:System.Xml.Linq.XDocumentType> for the DTD.</span></span>  
  
 <span data-ttu-id="85139-126">Bir seri hale getirmek istediğinizde,, <xref:System.Xml.Linq.XDocument> `XDocument.Declaration` `null` yazıcı olarak AYARLANDıYSA çıkış bir XML bildirimine sahip olacaktır `Writer.Settings.OmitXmlDeclaration` `false` (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="85139-126">When you serialize an <xref:System.Xml.Linq.XDocument>, even if `XDocument.Declaration` is `null`, the output will have an XML declaration if the writer has `Writer.Settings.OmitXmlDeclaration` set to `false` (the default).</span></span>  
  
 <span data-ttu-id="85139-127">Varsayılan olarak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sürümü "1,0" olarak ayarlar ve kodlamayı "UTF-8" olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="85139-127">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sets the version to "1.0", and sets the encoding to "utf-8".</span></span>  
  
## <a name="using-xelement-without-xdocument"></a><span data-ttu-id="85139-128">XDocument olmadan XElement kullanma</span><span class="sxs-lookup"><span data-stu-id="85139-128">Using XElement without XDocument</span></span>  
 <span data-ttu-id="85139-129">Daha önce belirtildiği gibi, <xref:System.Xml.Linq.XElement> sınıfı [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programlama arabirimindeki ana sınıftır.</span><span class="sxs-lookup"><span data-stu-id="85139-129">As previously mentioned, the <xref:System.Xml.Linq.XElement> class is the main class in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface.</span></span> <span data-ttu-id="85139-130">Çoğu durumda, uygulamanız bir belge oluşturmanızı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="85139-130">In many cases, your application will not require that you create a document.</span></span> <span data-ttu-id="85139-131"><xref:System.Xml.Linq.XElement>Sınıfını kullanarak BIR XML ağacı oluşturabilir, buna başka xml ağaçları ekleyebilir, xml ağacını değiştirebilir ve kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85139-131">By using the <xref:System.Xml.Linq.XElement> class, you can create an XML tree, add other XML trees to it, modify the XML tree, and save it.</span></span>  
  
## <a name="using-xdocument"></a><span data-ttu-id="85139-132">XDocument kullanma</span><span class="sxs-lookup"><span data-stu-id="85139-132">Using XDocument</span></span>  
 <span data-ttu-id="85139-133">Oluşturmak için <xref:System.Xml.Linq.XDocument> , nesneleri oluşturmak için yaptığınız gibi işlevsel oluşturma kullanın <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="85139-133">To construct an <xref:System.Xml.Linq.XDocument>, use functional construction, just like you do to construct <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="85139-134">Aşağıdaki kod bir <xref:System.Xml.Linq.XDocument> nesne ve ilişkili içerilen nesneleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="85139-134">The following code creates an <xref:System.Xml.Linq.XDocument> object and its associated contained objects.</span></span>  
  
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
  
 <span data-ttu-id="85139-135">Test. xml dosyasını incelediğinizde aşağıdaki çıktıyı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="85139-135">When you examine the file test.xml, you get the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="85139-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85139-136">See also</span></span>

- [<span data-ttu-id="85139-137">LINQ to XML programlamaya genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85139-137">LINQ to XML Programming Overview (Visual Basic)</span></span>](linq-to-xml-programming-overview.md)
