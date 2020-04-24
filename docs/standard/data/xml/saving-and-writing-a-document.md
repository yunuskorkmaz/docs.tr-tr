---
title: Belge Kaydetme ve Yazma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 097b0cb1-5743-4c3a-86ef-caf5cbe6750d
ms.openlocfilehash: 0af160b720b9eddd9e72689c920316bffdc6d21e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710225"
---
# <a name="saving-and-writing-a-document"></a><span data-ttu-id="04c29-102">Belge Kaydetme ve Yazma</span><span class="sxs-lookup"><span data-stu-id="04c29-102">Saving and Writing a Document</span></span>
<span data-ttu-id="04c29-103">Yüklediğinizde ve kaydettiğinizde <xref:System.Xml.XmlDocument>, kaydedilen belge orijinalden aşağıdaki yollarla farklılık gösterebilir:</span><span class="sxs-lookup"><span data-stu-id="04c29-103">When you load and save an <xref:System.Xml.XmlDocument>, the saved document may differ from the original in the following ways:</span></span>  
  
- <span data-ttu-id="04c29-104">Özelliği yöntemi çağrılmadan önce olarak `true` ayarlandıysa, çıktıda boşluk korunur; <xref:System.Xml.XmlDocument.Save%2A> <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> Bu özellik ise `false`çıktıyı <xref:System.Xml.XmlDocument> otomatik girintiler.</span><span class="sxs-lookup"><span data-stu-id="04c29-104">If the <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> property is set to `true` before the <xref:System.Xml.XmlDocument.Save%2A> method is called, white space in the document is preserved in the output; if this property is `false`, <xref:System.Xml.XmlDocument> auto-indents the output.</span></span>  
  
- <span data-ttu-id="04c29-105">Öznitelikler arasındaki tüm boşluklar, tek bir boşluk karakteriyle azaltılır.</span><span class="sxs-lookup"><span data-stu-id="04c29-105">All the white space between attributes is reduced to a single space character.</span></span>  
  
- <span data-ttu-id="04c29-106">Öğeler arasındaki boşluk değişir.</span><span class="sxs-lookup"><span data-stu-id="04c29-106">The white space between elements is changed.</span></span> <span data-ttu-id="04c29-107">Önemli boşluk korunur ve çok önemli boşluk değildir.</span><span class="sxs-lookup"><span data-stu-id="04c29-107">Significant white space is preserved and insignificant white space is not.</span></span> <span data-ttu-id="04c29-108">Ancak belge kaydedildiğinde, çıktıyı daha okunabilir hale getirmek için varsayılan <xref:System.Xml.XmlTextWriter> olarak, **girintilemeyi** seçerek yazdırmak için varsayılan olarak girintileme modunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="04c29-108">But when the document is saved, it will use the <xref:System.Xml.XmlTextWriter> **Indenting** mode by default to neatly print the output to make it more readable.</span></span>  
  
- <span data-ttu-id="04c29-109">Öznitelik değerleri etrafında kullanılan tırnak karakteri varsayılan olarak çift tırnak olarak değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="04c29-109">The quote character used around attribute values is changed to double quote by default.</span></span> <span data-ttu-id="04c29-110">Tırnak karakterini çift tırnak <xref:System.Xml.XmlTextReader.QuoteChar%2A> ya da <xref:System.Xml.XmlTextWriter> tek tırnak olarak ayarlamak için üzerinde özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="04c29-110">You can use the <xref:System.Xml.XmlTextReader.QuoteChar%2A> property on <xref:System.Xml.XmlTextWriter> to set the quote character to either double quote or single quote.</span></span>  
  
- <span data-ttu-id="04c29-111">Varsayılan olarak, benzer `{` sayısal karakter varlıkları genişletilir.</span><span class="sxs-lookup"><span data-stu-id="04c29-111">By default, numeric character entities like `{` are expanded.</span></span>  
  
- <span data-ttu-id="04c29-112">Giriş belgesinde bulunan bayt düzeni işareti korunmaz.</span><span class="sxs-lookup"><span data-stu-id="04c29-112">The byte-order mark found in the input document is not preserved.</span></span> <span data-ttu-id="04c29-113">Özel olarak farklı bir kodlama belirten bir XML bildirimi oluşturmadığınız sürece, UCS-2 UTF-8 olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="04c29-113">UCS-2 is saved as UTF-8 unless you explicitly create an XML declaration that specifies a different encoding.</span></span>  
  
- <span data-ttu-id="04c29-114">' I bir dosyaya veya akışa yazmak <xref:System.Xml.XmlDocument> isterseniz, yazılan çıkış belgenin içeriğiyle aynı olur.</span><span class="sxs-lookup"><span data-stu-id="04c29-114">If you want to write out the <xref:System.Xml.XmlDocument> into a file or stream, the output written out is the same as the content of the document.</span></span> <span data-ttu-id="04c29-115">Diğer bir deyişle <xref:System.Xml.XmlDeclaration> , yalnızca belgede bulunan bir belge varsa yazılır ve belgeyi yazarken kullanılan kodlama, bildirim düğümünde belirtilen kodlamayla aynı olur.</span><span class="sxs-lookup"><span data-stu-id="04c29-115">That is, the <xref:System.Xml.XmlDeclaration> is written out only if there is one contained in the document, and the encoding used when writing out the document is the same encoding given in the declaration node.</span></span>  
  
## <a name="writing-an-xmldeclaration"></a><span data-ttu-id="04c29-116">XmlDeclaration yazma</span><span class="sxs-lookup"><span data-stu-id="04c29-116">Writing an XmlDeclaration</span></span>  
 <span data-ttu-id="04c29-117"><xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument> , Ve <xref:System.Xml.XmlDocument.Save%2A> yöntemlerinin <xref:System.Xml.XmlDocument.WriteContentTo%2A>yanı sıra bir XML bildirimi oluşturur. <xref:System.Xml.XmlDeclaration> <xref:System.Xml.XmlNode.OuterXml%2A> <xref:System.Xml.XmlNode.InnerXml%2A> <xref:System.Xml.XmlNode.WriteTo%2A></span><span class="sxs-lookup"><span data-stu-id="04c29-117">The <xref:System.Xml.XmlDocument> and <xref:System.Xml.XmlDeclaration> members of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlNode.InnerXml%2A>, and <xref:System.Xml.XmlNode.WriteTo%2A>, in addition to the <xref:System.Xml.XmlDocument> methods of <xref:System.Xml.XmlDocument.Save%2A> and <xref:System.Xml.XmlDocument.WriteContentTo%2A>, create an XML declaration.</span></span>  
  
 <span data-ttu-id="04c29-118">, Ve <xref:System.Xml.XmlDocument> , ve <xref:System.Xml.XmlNode.OuterXml%2A> <xref:System.Xml.XmlDocument.WriteContentTo%2A> yöntemlerinin <xref:System.Xml.XmlDocument.InnerXml%2A>özellikleri <xref:System.Xml.XmlDocument.Save%2A> <xref:System.Xml.XmlDocument.WriteTo%2A>için, XML bildiriminde yazılan kodlama <xref:System.Xml.XmlDeclaration> düğümden alınır.</span><span class="sxs-lookup"><span data-stu-id="04c29-118">For the <xref:System.Xml.XmlDocument> properties of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDocument.InnerXml%2A>, and the <xref:System.Xml.XmlDocument.Save%2A>, <xref:System.Xml.XmlDocument.WriteTo%2A>, and <xref:System.Xml.XmlDocument.WriteContentTo%2A> methods, the encoding written out in the XML declaration is taken from the <xref:System.Xml.XmlDeclaration> node.</span></span> <span data-ttu-id="04c29-119"><xref:System.Xml.XmlDeclaration> Düğüm yoksa, <xref:System.Xml.XmlDeclaration> yazılmaz. <xref:System.Xml.XmlDeclaration> Düğümde bir kodlama yoksa, kodlama XML bildiriminde yazılmaz.</span><span class="sxs-lookup"><span data-stu-id="04c29-119">If there is no <xref:System.Xml.XmlDeclaration> node, <xref:System.Xml.XmlDeclaration> is not written out. If there is no encoding in the <xref:System.Xml.XmlDeclaration> node, encoding is not written out in the XML declaration.</span></span>  
  
 <span data-ttu-id="04c29-120"><xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> Ve <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> yöntemleri her zaman bir <xref:System.Xml.XmlDeclaration>yazar.</span><span class="sxs-lookup"><span data-stu-id="04c29-120">The <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> and <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> methods always write out an <xref:System.Xml.XmlDeclaration>.</span></span> <span data-ttu-id="04c29-121">Bu yöntemler, yazma yaptığı yazarın kodlamasını alır.</span><span class="sxs-lookup"><span data-stu-id="04c29-121">These methods take the encoding from the writer that it is writing to.</span></span> <span data-ttu-id="04c29-122">Diğer bir deyişle, yazıcı üzerindeki kodlama değeri belgedeki ve içindeki kodlamayı geçersiz kılar <xref:System.Xml.XmlDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="04c29-122">That is, the encoding value on the writer overrides the encoding on the document and in the <xref:System.Xml.XmlDeclaration>.</span></span> <span data-ttu-id="04c29-123">Örneğin, aşağıdaki kod çıkış dosyasında `out.xml`bulunan XML bildiriminde bir kodlama yazmıyor.</span><span class="sxs-lookup"><span data-stu-id="04c29-123">For example, the following code does not write an encoding in the XML declaration found in the output file `out.xml`.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
Dim tw As XmlTextWriter = New XmlTextWriter("out.xml", Nothing)  
doc.Load("text.xml")  
doc.Save(tw)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlTextWriter tw = new XmlTextWriter("out.xml", null);  
doc.Load("text.xml");  
doc.Save(tw);  
```  
  
 <span data-ttu-id="04c29-124"><xref:System.Xml.XmlDocument.Save%2A> Yöntemi IÇIN, XML bildirimi <xref:System.Xml.XmlWriter.WriteStartDocument%2A> <xref:System.Xml.XmlWriter> sınıfında yöntemi kullanılarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="04c29-124">For the <xref:System.Xml.XmlDocument.Save%2A> method, the XML declaration is written out using the <xref:System.Xml.XmlWriter.WriteStartDocument%2A> method in the <xref:System.Xml.XmlWriter> class.</span></span> <span data-ttu-id="04c29-125">Bu nedenle, <xref:System.Xml.XmlWriter.WriteStartDocument%2A> yöntemin üzerine yazılması belgenin başlangıcını nasıl yazıldığı değişir.</span><span class="sxs-lookup"><span data-stu-id="04c29-125">Therefore, overwriting the <xref:System.Xml.XmlWriter.WriteStartDocument%2A> method changes how the start of the document is written.</span></span>  
  
 <span data-ttu-id="04c29-126">, Ve <xref:System.Xml.XmlDeclaration> <xref:System.Xml.XmlNode.OuterXml%2A> <xref:System.Xml.XmlNode.InnerXml%2A> <xref:System.Xml.XmlDeclaration.Encoding%2A> üyeleri <xref:System.Xml.XmlDeclaration.WriteTo%2A>için, özelliği ayarlanmamışsa, hiçbir kodlama yazılmaz. Aksi halde, XML bildiriminde yazılan kodlama, <xref:System.Xml.XmlDeclaration.Encoding%2A> özelliğinde bulunan kodlamayla aynı olur.</span><span class="sxs-lookup"><span data-stu-id="04c29-126">For the <xref:System.Xml.XmlDeclaration> members of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDeclaration.WriteTo%2A>, and <xref:System.Xml.XmlNode.InnerXml%2A>, if the <xref:System.Xml.XmlDeclaration.Encoding%2A> property is not set, no encoding is written out. Otherwise, the encoding written out in the XML declaration is the same as the encoding found in the <xref:System.Xml.XmlDeclaration.Encoding%2A> property.</span></span>  
  
## <a name="writing-document-content-using-the-outerxml-property"></a><span data-ttu-id="04c29-127">OuterXml özelliğini kullanarak belge Içeriği yazma</span><span class="sxs-lookup"><span data-stu-id="04c29-127">Writing Document Content Using the OuterXml Property</span></span>  
 <span data-ttu-id="04c29-128"><xref:System.Xml.XmlNode.OuterXml%2A> Özelliği, world WIDE Web KONSORSIYUMU (W3C) XML belge nesne MODELI (DOM) standartlarına yönelik bir Microsoft uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="04c29-128">The <xref:System.Xml.XmlNode.OuterXml%2A> property is a Microsoft extension to the World Wide Web Consortium (W3C) XML Document Object Model (DOM) standards.</span></span> <span data-ttu-id="04c29-129"><xref:System.Xml.XmlNode.OuterXml%2A> ÖZELLIĞI tüm XML belgesinin işaretlemesini veya yalnızca tek bir düğümün ve onun alt düğümlerinin işaretlemesini almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="04c29-129">The <xref:System.Xml.XmlNode.OuterXml%2A> property is used to get the markup of the whole XML document, or just the markup of a single node and its child nodes.</span></span> <span data-ttu-id="04c29-130"><xref:System.Xml.XmlNode.OuterXml%2A>verilen düğümü ve onun tüm alt düğümlerini temsil eden biçimlendirmeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="04c29-130"><xref:System.Xml.XmlNode.OuterXml%2A> returns the markup representing the given node and all its child nodes.</span></span>  
  
 <span data-ttu-id="04c29-131">Aşağıdaki kod örneği, bir belgenin tamamen dize olarak nasıl kaydedileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="04c29-131">The following code sample shows how to save a document in its entirety as a string.</span></span>  
  
```vb  
Dim mydoc As New XmlDocument()  
' Perform application needs here, like mydoc.Load("myfile");  
' Now save the entire document to a string variable called "xml".  
Dim xml As String = mydoc.OuterXml  
```  
  
```csharp  
XmlDocument mydoc = new XmlDocument();  
// Perform application needs here, like mydoc.Load("myfile");  
// Now save the entire document to a string variable called "xml".  
string xml = mydoc.OuterXml;  
```  
  
 <span data-ttu-id="04c29-132">Aşağıdaki kod örneğinde, yalnızca belge öğesinin nasıl kaydedileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="04c29-132">The following code sample shows how to save only the document element.</span></span>  
  
```vb  
' For the content of the Document Element only.  
Dim xml As String = mydoc.DocumentElement.OuterXml  
```  
  
```csharp  
// For the content of the Document Element only.  
string xml = mydoc.DocumentElement.OuterXml;  
```  
  
 <span data-ttu-id="04c29-133">Buna karşılık, alt düğümlerin içeriğini istiyorsanız <xref:System.Xml.XmlNode.InnerText%2A> özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="04c29-133">In contrast, you can use the <xref:System.Xml.XmlNode.InnerText%2A> property if you want the content of child nodes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04c29-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04c29-134">See also</span></span>

- [<span data-ttu-id="04c29-135">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="04c29-135">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
