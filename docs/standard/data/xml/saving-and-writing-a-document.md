---
title: Belge Kaydetme ve Yazma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 097b0cb1-5743-4c3a-86ef-caf5cbe6750d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83aad5d45dda1784069839662486f7dbcc307542
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62027036"
---
# <a name="saving-and-writing-a-document"></a><span data-ttu-id="eb52b-102">Belge Kaydetme ve Yazma</span><span class="sxs-lookup"><span data-stu-id="eb52b-102">Saving and Writing a Document</span></span>
<span data-ttu-id="eb52b-103">Ne zaman yükler ve kaydeder bir <xref:System.Xml.XmlDocument>, aşağıdaki yollarla kaydedilmiş belge orijinalden farklı olabilir:</span><span class="sxs-lookup"><span data-stu-id="eb52b-103">When you load and save an <xref:System.Xml.XmlDocument>, the saved document may differ from the original in the following ways:</span></span>  
  
- <span data-ttu-id="eb52b-104">Varsa <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> özelliği `true` önce <xref:System.Xml.XmlDocument.Save%2A> yöntemi çağrıldığında, boşluk belgedeki; çıktısında korunur, bu özellik ise `false`, <xref:System.Xml.XmlDocument> otomatik girintileri çıktı.</span><span class="sxs-lookup"><span data-stu-id="eb52b-104">If the <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> property is set to `true` before the <xref:System.Xml.XmlDocument.Save%2A> method is called, white space in the document is preserved in the output; if this property is `false`, <xref:System.Xml.XmlDocument> auto-indents the output.</span></span>  
  
- <span data-ttu-id="eb52b-105">Öznitelikler arasındaki tüm boşluk tek bir boşluk olarak azaltılır.</span><span class="sxs-lookup"><span data-stu-id="eb52b-105">All the white space between attributes is reduced to a single space character.</span></span>  
  
- <span data-ttu-id="eb52b-106">Öğeler arasındaki boşluk değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="eb52b-106">The white space between elements is changed.</span></span> <span data-ttu-id="eb52b-107">Önemli boşluk korunur ve önemsiz boşluk değildir.</span><span class="sxs-lookup"><span data-stu-id="eb52b-107">Significant white space is preserved and insignificant white space is not.</span></span> <span data-ttu-id="eb52b-108">Ancak Belge kaydedildiğinde kullanacak <xref:System.Xml.XmlTextWriter> **Indenting** düzgünce daha okunabilir yapmak için Çıkış'ı yazdırmak için varsayılan modu.</span><span class="sxs-lookup"><span data-stu-id="eb52b-108">But when the document is saved, it will use the <xref:System.Xml.XmlTextWriter> **Indenting** mode by default to neatly print the output to make it more readable.</span></span>  
  
- <span data-ttu-id="eb52b-109">Kullanılan öznitelik değeri tırnak karakteri için çift tırnak işareti, varsayılan olarak değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="eb52b-109">The quote character used around attribute values is changed to double quote by default.</span></span> <span data-ttu-id="eb52b-110">Kullanabileceğiniz <xref:System.Xml.XmlTextReader.QuoteChar%2A> özelliği <xref:System.Xml.XmlTextWriter> teklif karakter çift tırnak işareti veya tek tırnak işareti ayarlamak için.</span><span class="sxs-lookup"><span data-stu-id="eb52b-110">You can use the <xref:System.Xml.XmlTextReader.QuoteChar%2A> property on <xref:System.Xml.XmlTextWriter> to set the quote character to either double quote or single quote.</span></span>  
  
- <span data-ttu-id="eb52b-111">Varsayılan olarak, sayısal karakter varlıkları ister `{` genişletilir.</span><span class="sxs-lookup"><span data-stu-id="eb52b-111">By default, numeric character entities like `{` are expanded.</span></span>  
  
- <span data-ttu-id="eb52b-112">Giriş belgesinde bulunan bayt sırası işareti korunmaz.</span><span class="sxs-lookup"><span data-stu-id="eb52b-112">The byte-order mark found in the input document is not preserved.</span></span> <span data-ttu-id="eb52b-113">Farklı bir kodlama belirten bir XML bildirimi açıkça oluşturmadığınız sürece UCS-2 UTF-8 kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="eb52b-113">UCS-2 is saved as UTF-8 unless you explicitly create an XML declaration that specifies a different encoding.</span></span>  
  
- <span data-ttu-id="eb52b-114">Yazmak isterseniz <xref:System.Xml.XmlDocument> bir dosya veya akışı içine yazılan çıktıyı belgenin içeriğini aynıdır.</span><span class="sxs-lookup"><span data-stu-id="eb52b-114">If you want to write out the <xref:System.Xml.XmlDocument> into a file or stream, the output written out is the same as the content of the document.</span></span> <span data-ttu-id="eb52b-115">Diğer bir deyişle, <xref:System.Xml.XmlDeclaration> bir belgede yer alan ve belgeyi yazılırken kullanılan kodlama bildirimi düğümde verilen aynı kodlama olup olmadığını yalnızca yazılır.</span><span class="sxs-lookup"><span data-stu-id="eb52b-115">That is, the <xref:System.Xml.XmlDeclaration> is written out only if there is one contained in the document, and the encoding used when writing out the document is the same encoding given in the declaration node.</span></span>  
  
## <a name="writing-an-xmldeclaration"></a><span data-ttu-id="eb52b-116">Bir XmlDeclaration yazma</span><span class="sxs-lookup"><span data-stu-id="eb52b-116">Writing an XmlDeclaration</span></span>  
 <span data-ttu-id="eb52b-117"><xref:System.Xml.XmlDocument> Ve <xref:System.Xml.XmlDeclaration> üyeleri <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlNode.InnerXml%2A>, ve <xref:System.Xml.XmlNode.WriteTo%2A>, ek olarak <xref:System.Xml.XmlDocument> yöntemlerinin <xref:System.Xml.XmlDocument.Save%2A> ve <xref:System.Xml.XmlDocument.WriteContentTo%2A>, bir XML bildirimi oluştur.</span><span class="sxs-lookup"><span data-stu-id="eb52b-117">The <xref:System.Xml.XmlDocument> and <xref:System.Xml.XmlDeclaration> members of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlNode.InnerXml%2A>, and <xref:System.Xml.XmlNode.WriteTo%2A>, in addition to the <xref:System.Xml.XmlDocument> methods of <xref:System.Xml.XmlDocument.Save%2A> and <xref:System.Xml.XmlDocument.WriteContentTo%2A>, create an XML declaration.</span></span>  
  
 <span data-ttu-id="eb52b-118">İçin <xref:System.Xml.XmlDocument> özelliklerini <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDocument.InnerXml%2A>ve <xref:System.Xml.XmlDocument.Save%2A>, <xref:System.Xml.XmlDocument.WriteTo%2A>, ve <xref:System.Xml.XmlDocument.WriteContentTo%2A> yöntemleri öğesinden alınır XML bildiriminde yazılan kodlama <xref:System.Xml.XmlDeclaration> düğümü.</span><span class="sxs-lookup"><span data-stu-id="eb52b-118">For the <xref:System.Xml.XmlDocument> properties of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDocument.InnerXml%2A>, and the <xref:System.Xml.XmlDocument.Save%2A>, <xref:System.Xml.XmlDocument.WriteTo%2A>, and <xref:System.Xml.XmlDocument.WriteContentTo%2A> methods, the encoding written out in the XML declaration is taken from the <xref:System.Xml.XmlDeclaration> node.</span></span> <span data-ttu-id="eb52b-119">Yoksa hiçbir <xref:System.Xml.XmlDeclaration> düğümünün <xref:System.Xml.XmlDeclaration> yazılır değil. Varsa, hiçbir kodlama <xref:System.Xml.XmlDeclaration> düğümü, kodlama değil yazılmış XML bildiriminde.</span><span class="sxs-lookup"><span data-stu-id="eb52b-119">If there is no <xref:System.Xml.XmlDeclaration> node, <xref:System.Xml.XmlDeclaration> is not written out. If there is no encoding in the <xref:System.Xml.XmlDeclaration> node, encoding is not written out in the XML declaration.</span></span>  
  
 <span data-ttu-id="eb52b-120"><xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> Ve <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> yöntem yazılmasına yarar her zaman bir <xref:System.Xml.XmlDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="eb52b-120">The <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> and <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> methods always write out an <xref:System.Xml.XmlDeclaration>.</span></span> <span data-ttu-id="eb52b-121">Bu yöntemler için yazı yazan gelen kodlamayı Al.</span><span class="sxs-lookup"><span data-stu-id="eb52b-121">These methods take the encoding from the writer that it is writing to.</span></span> <span data-ttu-id="eb52b-122">Diğer bir deyişle, belge üzerinde hem de kodlama yazıcısı kodlama değeri geçersiz kılar <xref:System.Xml.XmlDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="eb52b-122">That is, the encoding value on the writer overrides the encoding on the document and in the <xref:System.Xml.XmlDeclaration>.</span></span> <span data-ttu-id="eb52b-123">Örneğin, aşağıdaki kod bir çıkış dosyasında bulunan XML bildirimindeki kodlama yazmaz `out.xml`.</span><span class="sxs-lookup"><span data-stu-id="eb52b-123">For example, the following code does not write an encoding in the XML declaration found in the output file `out.xml`.</span></span>  
  
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
  
 <span data-ttu-id="eb52b-124">İçin <xref:System.Xml.XmlDocument.Save%2A> yöntemi, XML bildirimi yazılmış kullanarak <xref:System.Xml.XmlWriter.WriteStartDocument%2A> yönteminde <xref:System.Xml.XmlWriter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="eb52b-124">For the <xref:System.Xml.XmlDocument.Save%2A> method, the XML declaration is written out using the <xref:System.Xml.XmlWriter.WriteStartDocument%2A> method in the <xref:System.Xml.XmlWriter> class.</span></span> <span data-ttu-id="eb52b-125">Bu nedenle, üzerine <xref:System.Xml.XmlWriter.WriteStartDocument%2A> yöntemi değiştirir belgenin başlangıcı nasıl yazılır.</span><span class="sxs-lookup"><span data-stu-id="eb52b-125">Therefore, overwriting the <xref:System.Xml.XmlWriter.WriteStartDocument%2A> method changes how the start of the document is written.</span></span>  
  
 <span data-ttu-id="eb52b-126">İçin <xref:System.Xml.XmlDeclaration> üyeleri <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDeclaration.WriteTo%2A>, ve <xref:System.Xml.XmlNode.InnerXml%2A>, <xref:System.Xml.XmlDeclaration.Encoding%2A> özelliği ayarlı değil, hiçbir kodlama yazılır. Kodlama bulunan Aksi takdirde, XML bildiriminde yazılan kodlama aynıdır <xref:System.Xml.XmlDeclaration.Encoding%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="eb52b-126">For the <xref:System.Xml.XmlDeclaration> members of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDeclaration.WriteTo%2A>, and <xref:System.Xml.XmlNode.InnerXml%2A>, if the <xref:System.Xml.XmlDeclaration.Encoding%2A> property is not set, no encoding is written out. Otherwise, the encoding written out in the XML declaration is the same as the encoding found in the <xref:System.Xml.XmlDeclaration.Encoding%2A> property.</span></span>  
  
## <a name="writing-document-content-using-the-outerxml-property"></a><span data-ttu-id="eb52b-127">Belge içerik yazma OuterXml özelliğini kullanma</span><span class="sxs-lookup"><span data-stu-id="eb52b-127">Writing Document Content Using the OuterXml Property</span></span>  
 <span data-ttu-id="eb52b-128"><xref:System.Xml.XmlNode.OuterXml%2A> Özelliği, World Wide Web Consortium (W3C) XML belge nesne modeli (DOM) standartları için bir Microsoft uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="eb52b-128">The <xref:System.Xml.XmlNode.OuterXml%2A> property is a Microsoft extension to the World Wide Web Consortium (W3C) XML Document Object Model (DOM) standards.</span></span> <span data-ttu-id="eb52b-129"><xref:System.Xml.XmlNode.OuterXml%2A> Özelliği, biçimlendirmeyi tüm XML belgesi veya biçimlendirme yalnızca tek bir düğüm ve onun alt düğümleri almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eb52b-129">The <xref:System.Xml.XmlNode.OuterXml%2A> property is used to get the markup of the whole XML document, or just the markup of a single node and its child nodes.</span></span> <span data-ttu-id="eb52b-130"><xref:System.Xml.XmlNode.OuterXml%2A> Verilen düğüm ve onun tüm alt düğümleri temsil eden biçimlendirme döndürür.</span><span class="sxs-lookup"><span data-stu-id="eb52b-130"><xref:System.Xml.XmlNode.OuterXml%2A> returns the markup representing the given node and all its child nodes.</span></span>  
  
 <span data-ttu-id="eb52b-131">Aşağıdaki kod örneği, belgeye bir dize olarak tamamen kaydetmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="eb52b-131">The following code sample shows how to save a document in its entirety as a string.</span></span>  
  
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
  
 <span data-ttu-id="eb52b-132">Aşağıdaki kod örneği, yalnızca belge öğesi kaydedileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="eb52b-132">The following code sample shows how to save only the document element.</span></span>  
  
```vb  
' For the content of the Document Element only.  
Dim xml As String = mydoc.DocumentElement.OuterXml  
```  
  
```csharp  
// For the content of the Document Element only.  
string xml = mydoc.DocumentElement.OuterXml;  
```  
  
 <span data-ttu-id="eb52b-133">Buna karşılık, kullanabileceğiniz <xref:System.Xml.XmlNode.InnerText%2A> alt düğümleri içeriğini istiyorsanız özelliği.</span><span class="sxs-lookup"><span data-stu-id="eb52b-133">In contrast, you can use the <xref:System.Xml.XmlNode.InnerText%2A> property if you want the content of child nodes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb52b-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb52b-134">See also</span></span>

- [<span data-ttu-id="eb52b-135">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="eb52b-135">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
