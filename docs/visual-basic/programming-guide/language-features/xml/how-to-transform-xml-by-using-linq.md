---
title: "Nasıl yapılır: XML'i LINQ Kullanarak Dönüştürme (Visual Basic)"
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], transforming
- LINQ to XML [Visual Basic], transforming XML
ms.assetid: 815687f4-0bc2-4c0b-adc6-d78744aa356f
ms.openlocfilehash: 08378775f2c30d8ebfcc4f7ceea6fc3ecb2066e5
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003254"
---
# <a name="how-to-transform-xml-by-using-linq-visual-basic"></a><span data-ttu-id="3c13a-102">Nasıl yapılır: XML'i LINQ Kullanarak Dönüştürme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c13a-102">How to: Transform XML by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="3c13a-103">[XML değişmez değerleri](../../../../visual-basic/language-reference/xml-literals/index.md) , BIR kaynaktan XML okumayı ve bunu yenı bir XML biçimine dönüştürmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="3c13a-103">[XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md) make it easy to read XML from one source and transform it to a new XML format.</span></span> <span data-ttu-id="3c13a-104">Dönüştürülecek içeriği almak veya varolan bir belgedeki içeriği yeni bir XML biçimiyle değiştirmek için LINQ sorgularından yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c13a-104">You can take advantage of LINQ queries to retrieve the content to transform, or change content in an existing document to a new XML format.</span></span>  
  
 <span data-ttu-id="3c13a-105">Bu konudaki örnek, bir XML kaynak belgesinden içeriği bir tarayıcıda görüntülenmek üzere HTML 'ye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="3c13a-105">The example in this topic transforms content from an XML source document to HTML to be viewed in a browser.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-transform-an-xml-document"></a><span data-ttu-id="3c13a-106">Bir XML belgesini dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="3c13a-106">To transform an XML document</span></span>  
  
1. <span data-ttu-id="3c13a-107">Visual Studio 'da, **konsol uygulaması** proje şablonunda yeni bir Visual Basic projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3c13a-107">In Visual Studio, create a new Visual Basic project in the **Console Application** project template.</span></span>  
  
2. <span data-ttu-id="3c13a-108">Visual Basic kodunu değiştirmek için projede oluşturulan Module1. vb dosyasını çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="3c13a-108">Double-click the Module1.vb file created in the project to modify the Visual Basic code.</span></span> <span data-ttu-id="3c13a-109">Aşağıdaki kodu `Module1` modülünün `Sub Main` ' a ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3c13a-109">Add the following code to the `Sub Main` of the `Module1` module.</span></span> <span data-ttu-id="3c13a-110">Bu kod, kaynak XML belgesini <xref:System.Xml.Linq.XDocument> nesnesi olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3c13a-110">This code creates the source XML document as an <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
    ```vb  
    Dim catalog =   
      <?xml version="1.0"?>  
        <Catalog>  
          <Book id="bk101">  
            <Author>Garghentini, Davide</Author>  
            <Title>XML Developer's Guide</Title>  
            <Price>44.95</Price>  
            <Description>  
              An in-depth look at creating applications  
              with <technology>XML</technology>. For   
              <audience>beginners</audience> or   
              <audience>advanced</audience> developers.  
            </Description>  
          </Book>  
          <Book id="bk331">  
            <Author>Spencer, Phil</Author>  
            <Title>Developing Applications with Visual Basic .NET</Title>  
            <Price>45.95</Price>  
            <Description>  
              Get the expert insights, practical code samples,   
              and best practices you need   
              to advance your expertise with <technology>Visual   
              Basic .NET</technology>.   
              Learn how to create faster, more reliable applications  
              based on professional,   
              pragmatic guidance by today's top <audience>developers</audience>.  
            </Description>  
          </Book>  
        </Catalog>  
    ```  
  
     <span data-ttu-id="3c13a-111">[Nasıl yapılır: bir dosyadan, dizeden veya AKıŞTAN XML yükleme](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md).</span><span class="sxs-lookup"><span data-stu-id="3c13a-111">[How to: Load XML from a File, String, or Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md).</span></span>  
  
3. <span data-ttu-id="3c13a-112">Kaynak XML belgesini oluşturma kodundan sonra, \<Book > öğelerini nesnesinden alıp bir HTML belgesine dönüştürmek için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3c13a-112">After the code to create the source XML document, add the following code to retrieve all the \<Book> elements from the object and transform them into an HTML document.</span></span> <span data-ttu-id="3c13a-113">@No__t-0Book > öğelerinin listesi, dönüştürülmüş HTML içeren <xref:System.Xml.Linq.XElement> nesnelerinin bir koleksiyonunu döndüren bir LINQ sorgusu kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3c13a-113">The list of \<Book> elements is created by using a LINQ query that returns a collection of <xref:System.Xml.Linq.XElement> objects that contain the transformed HTML.</span></span> <span data-ttu-id="3c13a-114">Kaynak belgeden yeni XML biçiminde değerleri yerleştirmek için katıştırılmış ifadeleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c13a-114">You can use embedded expressions to put the values from the source document in the new XML format.</span></span>  
  
     <span data-ttu-id="3c13a-115">Elde edilen HTML belgesi, <xref:System.Xml.Linq.XElement.Save%2A> yöntemi kullanılarak bir dosyaya yazılır.</span><span class="sxs-lookup"><span data-stu-id="3c13a-115">The resulting HTML document is written to a file by using the <xref:System.Xml.Linq.XElement.Save%2A> method.</span></span>  
  
    ```vb  
    Dim htmlOutput =   
      <html>  
        <body>  
          <%= From book In catalog.<Catalog>.<Book>   
              Select <div>  
                       <h1><%= book.<Title>.Value %></h1>  
                       <h3><%= "By " & book.<Author>.Value %></h3>  
                        <h3><%= "Price = " & book.<Price>.Value %></h3>  
                        <h2>Description</h2>  
                        <%= TransformDescription(book.<Description>(0)) %>  
                        <hr/>  
                      </div> %>  
        </body>  
      </html>  
  
    htmlOutput.Save("BookDescription.html")  
    ```  
  
4. <span data-ttu-id="3c13a-116">@No__t-0 ' dan `Module1` ' den sonra, \<Description > düğümünü belirtilen HTML biçimine dönüştürmek için yeni bir Yöntem (`Sub`) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3c13a-116">After `Sub Main` of `Module1`, add a new method (`Sub`) to transform a \<Description> node into the specified HTML format.</span></span> <span data-ttu-id="3c13a-117">Bu yöntem, önceki adımda kod tarafından çağrılır ve \<Description > öğelerinin biçimini korumak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3c13a-117">This method is called by the code in the previous step and is used to preserve the format of the \<Description> elements.</span></span>  
  
     <span data-ttu-id="3c13a-118">Bu yöntem, \<Description > öğesinin alt öğelerini HTML ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="3c13a-118">This method replaces sub-elements of the \<Description> element with HTML.</span></span> <span data-ttu-id="3c13a-119">@No__t-0 yöntemi alt öğelerin konumunu korumak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3c13a-119">The `ReplaceWith` method is used to preserve the location of the sub-elements.</span></span> <span data-ttu-id="3c13a-120">@No__t-0Description > öğesinin dönüştürülmüş içeriği bir HTML paragrafına (\<p >) eklenir.</span><span class="sxs-lookup"><span data-stu-id="3c13a-120">The transformed content of the \<Description> element is included in an HTML paragraph (\<p>) element.</span></span> <span data-ttu-id="3c13a-121">@No__t-0 özelliği, \<Description > öğesinin dönüştürülmüş içeriğini almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3c13a-121">The <xref:System.Xml.Linq.XContainer.Nodes%2A> property is used to retrieve the transformed content of the \<Description> element.</span></span> <span data-ttu-id="3c13a-122">Bu, alt öğelerin dönüştürülmüş içeriğe dahil edilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c13a-122">This ensures that sub-elements are included in the transformed content.</span></span>  
  
     <span data-ttu-id="3c13a-123">@No__t-0 ' a `Module1` ' den sonra aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3c13a-123">Add the following code after `Sub Main` of `Module1`.</span></span>  
  
    ```vb  
    Public Function TransformDescription(ByVal desc As XElement) As XElement  
  
      ' Replace <technology> elements with <b>.  
      Dim content = (From element In desc...<technology>).ToList()  
  
      If content.Count > 0 Then  
        For i = 0 To content.Count - 1  
          content(i).ReplaceWith(<b><%= content(i).Value %></b>)  
        Next  
      End If  
  
      ' Replace <audience> elements with <i>.  
      content = (From element In desc...<audience>).ToList()  
  
      If content.Count > 0 Then  
        For i = 0 To content.Count - 1  
          content(i).ReplaceWith(<i><%= content(i).Value %></i>)  
        Next  
      End If  
  
      ' Return the updated contents of the <Description> element.  
      Return <p><%= desc.Nodes %></p>  
    End Function  
    ```  
  
5. <span data-ttu-id="3c13a-124">Değişikliklerinizi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="3c13a-124">Save your changes.</span></span>  
  
6. <span data-ttu-id="3c13a-125">Kodu çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="3c13a-125">Press F5 to run the code.</span></span> <span data-ttu-id="3c13a-126">Sonuç olarak kaydedilen belge aşağıdakine benzeyecektir:</span><span class="sxs-lookup"><span data-stu-id="3c13a-126">The resulting saved document will resemble the following:</span></span>  
  
    ```html  
    <?xml version="1.0"?>  
    <html>  
      <body>  
        <div>  
          <h1>XML Developer's Guide</h1>  
          <h3>By Garghentini, Davide</h3>  
          <h3>Price = 44.95</h3>  
          <h2>Description</h2>  
          <p>  
            An in-depth look at creating applications  
            with <b>XML</b>. For   
            <i>beginners</i> or   
            <i>advanced</i> developers.  
          </p>  
          <hr />  
        </div>  
        <div>  
          <h1>Developing Applications with Visual Basic .NET</h1>  
          <h3>By Spencer, Phil</h3>  
          <h3>Price = 45.95</h3>  
          <h2>Description</h2>  
          <p>  
            Get the expert insights, practical code   
            samples, and best practices you need   
            to advance your expertise with <b>Visual   
            Basic .NET</b>. Learn how to create faster,  
            more reliable applications based on  
            professional, pragmatic guidance by today's   
            top <i>developers</i>.  
          </p>  
          <hr />  
        </div>  
      </body>  
    </html>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3c13a-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c13a-127">See also</span></span>

- [<span data-ttu-id="3c13a-128">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="3c13a-128">XML Literals</span></span>](../../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="3c13a-129">Visual Basic XML 'yi düzenleme</span><span class="sxs-lookup"><span data-stu-id="3c13a-129">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
- [<span data-ttu-id="3c13a-130">XML</span><span class="sxs-lookup"><span data-stu-id="3c13a-130">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="3c13a-131">Nasıl yapılır: Dosya, Dize veya Akıştan XML Yükleme</span><span class="sxs-lookup"><span data-stu-id="3c13a-131">How to: Load XML from a File, String, or Stream</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)
- [<span data-ttu-id="3c13a-132">LINQ</span><span class="sxs-lookup"><span data-stu-id="3c13a-132">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="3c13a-133">Visual Basic LINQ 'e giriş</span><span class="sxs-lookup"><span data-stu-id="3c13a-133">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
