---
title: "XDocument sınıfına genel bakış (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45cb7e71-196a-47da-bfe9-7a5589db1eed
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 41b09335ae124ac290d8cd51afda71dfd935b7ff
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="xdocument-class-overview-visual-basic"></a><span data-ttu-id="b026c-102">XDocument sınıfına genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b026c-102">XDocument Class Overview (Visual Basic)</span></span>
<span data-ttu-id="b026c-103">Bu konu tanıtır <xref:System.Xml.Linq.XDocument> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b026c-103">This topic introduces the <xref:System.Xml.Linq.XDocument> class.</span></span>  
  
## <a name="overview-of-the-xdocument-class"></a><span data-ttu-id="b026c-104">XDocument sınıfı genel bakış</span><span class="sxs-lookup"><span data-stu-id="b026c-104">Overview of the XDocument class</span></span>  
 <span data-ttu-id="b026c-105"><xref:System.Xml.Linq.XDocument> Sınıfı için geçerli bir XML belgesi gerekli bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="b026c-105">The <xref:System.Xml.Linq.XDocument> class contains the information necessary for a valid XML document.</span></span> <span data-ttu-id="b026c-106">Bu işlem yönergeleri ve açıklamaları bir XML bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="b026c-106">This includes an XML declaration, processing instructions, and comments.</span></span>  
  
 <span data-ttu-id="b026c-107">Yalnızca oluşturmak zorunda Not <xref:System.Xml.Linq.XDocument> tarafından sağlanan belirli işlevleri gerektirip gerektirmediğini nesneleri <xref:System.Xml.Linq.XDocument> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b026c-107">Note that you only have to create <xref:System.Xml.Linq.XDocument> objects if you require the specific functionality provided by the <xref:System.Xml.Linq.XDocument> class.</span></span> <span data-ttu-id="b026c-108">Çoğu durumda, doğrudan çalışabileceğiniz <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="b026c-108">In many circumstances, you can work directly with <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="b026c-109">Doğrudan çalışma <xref:System.Xml.Linq.XElement> daha basit bir programlama modelidir.</span><span class="sxs-lookup"><span data-stu-id="b026c-109">Working directly with <xref:System.Xml.Linq.XElement> is a simpler programming model.</span></span>  
  
 <span data-ttu-id="b026c-110"><xref:System.Xml.Linq.XDocument>türetilen <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="b026c-110"><xref:System.Xml.Linq.XDocument> derives from <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="b026c-111">Bu nedenle, alt düğümler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="b026c-111">Therefore, it can contain child nodes.</span></span> <span data-ttu-id="b026c-112">Ancak, <xref:System.Xml.Linq.XDocument> nesneleri, yalnızca bir alt olabilir <xref:System.Xml.Linq.XElement> düğümü.</span><span class="sxs-lookup"><span data-stu-id="b026c-112">However, <xref:System.Xml.Linq.XDocument> objects can have only one child <xref:System.Xml.Linq.XElement> node.</span></span> <span data-ttu-id="b026c-113">Bu bir XML belgesinde yalnızca bir kök öğe olabileceğini XML standart yansıtır.</span><span class="sxs-lookup"><span data-stu-id="b026c-113">This reflects the XML standard that there can be only one root element in an XML document.</span></span>  
  
## <a name="components-of-xdocument"></a><span data-ttu-id="b026c-114">XDocument bileşenleri</span><span class="sxs-lookup"><span data-stu-id="b026c-114">Components of XDocument</span></span>  
 <span data-ttu-id="b026c-115">Bir <xref:System.Xml.Linq.XDocument> aşağıdaki öğeleri içerebilir:</span><span class="sxs-lookup"><span data-stu-id="b026c-115">An <xref:System.Xml.Linq.XDocument> can contain the following elements:</span></span>  
  
-   <span data-ttu-id="b026c-116">Bir <xref:System.Xml.Linq.XDeclaration> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b026c-116">One <xref:System.Xml.Linq.XDeclaration> object.</span></span> <span data-ttu-id="b026c-117"><xref:System.Xml.Linq.XDeclaration>bir XML bildirimi ilgili bölümleri belirtmenize olanak sağlar: belgenin kodlama XML sürümü ve XML belgesi tek başına olup.</span><span class="sxs-lookup"><span data-stu-id="b026c-117"><xref:System.Xml.Linq.XDeclaration> enables you to specify the pertinent parts of an XML declaration: the XML version, the encoding of the document, and whether the XML document is stand-alone.</span></span>  
  
-   <span data-ttu-id="b026c-118">Bir <xref:System.Xml.Linq.XElement> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b026c-118">One <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="b026c-119">XML belgesinin kök düğümü budur.</span><span class="sxs-lookup"><span data-stu-id="b026c-119">This is the root node of the XML document.</span></span>  
  
-   <span data-ttu-id="b026c-120">Herhangi bir sayıda <xref:System.Xml.Linq.XProcessingInstruction> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="b026c-120">Any number of <xref:System.Xml.Linq.XProcessingInstruction> objects.</span></span> <span data-ttu-id="b026c-121">Bir işleme yönergesi XML işleyen bir uygulama için bilgi iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="b026c-121">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
-   <span data-ttu-id="b026c-122">Herhangi bir sayıda <xref:System.Xml.Linq.XComment> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="b026c-122">Any number of <xref:System.Xml.Linq.XComment> objects.</span></span> <span data-ttu-id="b026c-123">Açıklamaları kök öğesi için eşdüzey olacaktır.</span><span class="sxs-lookup"><span data-stu-id="b026c-123">The comments will be siblings to the root element.</span></span> <span data-ttu-id="b026c-124"><xref:System.Xml.Linq.XComment> Birlikte bir açıklama başlatmak bir XML belgesi için geçerli değil çünkü nesne listesinde, ilk bağımsız değişken olamaz.</span><span class="sxs-lookup"><span data-stu-id="b026c-124">The <xref:System.Xml.Linq.XComment> object cannot be the first argument in the list, because it is not valid for an XML document to start with a comment.</span></span>  
  
-   <span data-ttu-id="b026c-125">Bir <xref:System.Xml.Linq.XDocumentType> DTD için.</span><span class="sxs-lookup"><span data-stu-id="b026c-125">One <xref:System.Xml.Linq.XDocumentType> for the DTD.</span></span>  
  
 <span data-ttu-id="b026c-126">Ne zaman, seri bir <xref:System.Xml.Linq.XDocument>olsa bile `XDocument.Declaration` olan `null`, yazıcı varsa çıktı XML bildirimi olacaktır `Writer.Settings.OmitXmlDeclaration` kümesine `false` (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="b026c-126">When you serialize an <xref:System.Xml.Linq.XDocument>, even if `XDocument.Declaration` is `null`, the output will have an XML declaration if the writer has `Writer.Settings.OmitXmlDeclaration` set to `false` (the default).</span></span>  
  
 <span data-ttu-id="b026c-127">Varsayılan olarak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sürüm "1.0" olarak ayarlar ve "utf-8" kodlama ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b026c-127">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sets the version to "1.0", and sets the encoding to "utf-8".</span></span>  
  
## <a name="using-xelement-without-xdocument"></a><span data-ttu-id="b026c-128">XElement XDocument olmadan kullanma</span><span class="sxs-lookup"><span data-stu-id="b026c-128">Using XElement without XDocument</span></span>  
 <span data-ttu-id="b026c-129">Daha önce belirtildiği gibi <xref:System.Xml.Linq.XElement> sınıfı, ana sınıfında [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programlama arabirimi.</span><span class="sxs-lookup"><span data-stu-id="b026c-129">As previously mentioned, the <xref:System.Xml.Linq.XElement> class is the main class in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface.</span></span> <span data-ttu-id="b026c-130">Çoğu durumda, bir belge oluşturun, uygulamanızın gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="b026c-130">In many cases, your application will not require that you create a document.</span></span> <span data-ttu-id="b026c-131">Kullanarak <xref:System.Xml.Linq.XElement> sınıfı, bir XML ağacı oluşturmak, diğer XML ağaçları ekleyin, XML ağacını değiştirmek ve dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="b026c-131">By using the <xref:System.Xml.Linq.XElement> class, you can create an XML tree, add other XML trees to it, modify the XML tree, and save it.</span></span>  
  
## <a name="using-xdocument"></a><span data-ttu-id="b026c-132">XDocument kullanma</span><span class="sxs-lookup"><span data-stu-id="b026c-132">Using XDocument</span></span>  
 <span data-ttu-id="b026c-133">Oluşturmak için bir <xref:System.Xml.Linq.XDocument>, oluşturmak için yaptığınız gibi işlev yapım kullanmak <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="b026c-133">To construct an <xref:System.Xml.Linq.XDocument>, use functional construction, just like you do to construct <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="b026c-134">Aşağıdaki kod oluşturur bir <xref:System.Xml.Linq.XDocument> nesne ve onunla ilişkili bulunan nesneleri.</span><span class="sxs-lookup"><span data-stu-id="b026c-134">The following code creates an <xref:System.Xml.Linq.XDocument> object and its associated contained objects.</span></span>  
  
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
  
 <span data-ttu-id="b026c-135">Dosya test.xml incelediğinizde, aşağıdaki çıkış alın:</span><span class="sxs-lookup"><span data-stu-id="b026c-135">When you examine the file test.xml, you get the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b026c-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b026c-136">See Also</span></span>  
 [<span data-ttu-id="b026c-137">LINQ-XML programlamaya genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b026c-137">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
