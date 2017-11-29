---
title: Kaydetme ve bir belgeyi yazma
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 097b0cb1-5743-4c3a-86ef-caf5cbe6750d
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ad656e2db17e44733b5718fe2e3a2a48afcb1381
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="saving-and-writing-a-document"></a><span data-ttu-id="4f0a4-102">Kaydetme ve bir belgeyi yazma</span><span class="sxs-lookup"><span data-stu-id="4f0a4-102">Saving and Writing a Document</span></span>
<span data-ttu-id="4f0a4-103">Ne zaman yükle ve Kaydet bir <xref:System.Xml.XmlDocument>, aşağıdaki yollarla kaydedilmiş belge orijinal olandan farklı olabilir:</span><span class="sxs-lookup"><span data-stu-id="4f0a4-103">When you load and save an <xref:System.Xml.XmlDocument>, the saved document may differ from the original in the following ways:</span></span>  
  
-   <span data-ttu-id="4f0a4-104">Varsa <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> özelliği ayarlanmış `true` önce <xref:System.Xml.XmlDocument.Save%2A> yöntemi çağrıldığında, boşluk belgesinde, çıkış; korunur, bu özellik ise `false`, <xref:System.Xml.XmlDocument> otomatik girintileri çıktı.</span><span class="sxs-lookup"><span data-stu-id="4f0a4-104">If the <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> property is set to `true` before the <xref:System.Xml.XmlDocument.Save%2A> method is called, white space in the document is preserved in the output; if this property is `false`, <xref:System.Xml.XmlDocument> auto-indents the output.</span></span>  
  
-   <span data-ttu-id="4f0a4-105">Öznitelikler arasındaki tüm boşluk bir tek boşluk karakteri azalır.</span><span class="sxs-lookup"><span data-stu-id="4f0a4-105">All the white space between attributes is reduced to a single space character.</span></span>  
  
-   <span data-ttu-id="4f0a4-106">Öğeler arasında boşluk değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="4f0a4-106">The white space between elements is changed.</span></span> <span data-ttu-id="4f0a4-107">Önemli boşluk korunur ve önemsiz boşluk değil.</span><span class="sxs-lookup"><span data-stu-id="4f0a4-107">Significant white space is preserved and insignificant white space is not.</span></span> <span data-ttu-id="4f0a4-108">Ancak Belge kaydedildiğinde kullanacağı <xref:System.Xml.XmlTextWriter> **Indenting** düzgün çıktıyı daha okunabilir hale yazdırmak için varsayılan modu.</span><span class="sxs-lookup"><span data-stu-id="4f0a4-108">But when the document is saved, it will use the <xref:System.Xml.XmlTextWriter> **Indenting** mode by default to neatly print the output to make it more readable.</span></span>  
  
-   <span data-ttu-id="4f0a4-109">Öznitelik değerlerinin kullanılan tırnak karakteri çift tırnak varsayılan olarak değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="4f0a4-109">The quote character used around attribute values is changed to double quote by default.</span></span> <span data-ttu-id="4f0a4-110">Kullanabileceğiniz <xref:System.Xml.XmlTextReader.QuoteChar%2A> özellikte <xref:System.Xml.XmlTextWriter> adınızda çift tırnak işareti ya da tek tırnaklı için ayarlanacak.</span><span class="sxs-lookup"><span data-stu-id="4f0a4-110">You can use the <xref:System.Xml.XmlTextReader.QuoteChar%2A> property on <xref:System.Xml.XmlTextWriter> to set the quote character to either double quote or single quote.</span></span>  
  
-   <span data-ttu-id="4f0a4-111">Varsayılan olarak, sayısal karakter varlıkları ister `{` genişletilir.</span><span class="sxs-lookup"><span data-stu-id="4f0a4-111">By default, numeric character entities like `{` are expanded.</span></span>  
  
-   <span data-ttu-id="4f0a4-112">Giriş belgesinde bulunan bayt sırası işareti korunmaz.</span><span class="sxs-lookup"><span data-stu-id="4f0a4-112">The byte-order mark found in the input document is not preserved.</span></span> <span data-ttu-id="4f0a4-113">Farklı bir kodlama belirten bir XML bildirimi açıkça oluşturmadan UCS-2 UTF-8 olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="4f0a4-113">UCS-2 is saved as UTF-8 unless you explicitly create an XML declaration that specifies a different encoding.</span></span>  
  
-   <span data-ttu-id="4f0a4-114">Dışına yazmak istiyorsanız <xref:System.Xml.XmlDocument> bir dosya veya akış içine yazılan çıktı belgesinin içeriği aynıdır.</span><span class="sxs-lookup"><span data-stu-id="4f0a4-114">If you want to write out the <xref:System.Xml.XmlDocument> into a file or stream, the output written out is the same as the content of the document.</span></span> <span data-ttu-id="4f0a4-115">Diğer bir deyişle, <xref:System.Xml.XmlDeclaration> bir belgedeki ve belgeyi kullanıma yazılırken kullanılan bildirimi düğümünde verilen aynı kodlama kodlamadır yalnızca yazılır.</span><span class="sxs-lookup"><span data-stu-id="4f0a4-115">That is, the <xref:System.Xml.XmlDeclaration> is written out only if there is one contained in the document, and the encoding used when writing out the document is the same encoding given in the declaration node.</span></span>  
  
## <a name="writing-an-xmldeclaration"></a><span data-ttu-id="4f0a4-116">Bir XmlDeclaration yazma</span><span class="sxs-lookup"><span data-stu-id="4f0a4-116">Writing an XmlDeclaration</span></span>  
 <span data-ttu-id="4f0a4-117"><xref:System.Xml.XmlDocument> Ve <xref:System.Xml.XmlDeclaration> üyeleri <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlNode.InnerXml%2A>, ve <xref:System.Xml.XmlNode.WriteTo%2A>, ek olarak <xref:System.Xml.XmlDocument> yöntemlerinin <xref:System.Xml.XmlDocument.Save%2A> ve <xref:System.Xml.XmlDocument.WriteContentTo%2A>, bir XML bildirimi oluştur.</span><span class="sxs-lookup"><span data-stu-id="4f0a4-117">The <xref:System.Xml.XmlDocument> and <xref:System.Xml.XmlDeclaration> members of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlNode.InnerXml%2A>, and <xref:System.Xml.XmlNode.WriteTo%2A>, in addition to the <xref:System.Xml.XmlDocument> methods of <xref:System.Xml.XmlDocument.Save%2A> and <xref:System.Xml.XmlDocument.WriteContentTo%2A>, create an XML declaration.</span></span>  
  
 <span data-ttu-id="4f0a4-118">İçin <xref:System.Xml.XmlDocument> özelliklerini <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDocument.InnerXml%2A>ve <xref:System.Xml.XmlDocument.Save%2A>, <xref:System.Xml.XmlDocument.WriteTo%2A>, ve <xref:System.Xml.XmlDocument.WriteContentTo%2A> yöntemleri, gelen alınır XML bildiriminde yazılan kodlama <xref:System.Xml.XmlDeclaration> düğümü.</span><span class="sxs-lookup"><span data-stu-id="4f0a4-118">For the <xref:System.Xml.XmlDocument> properties of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDocument.InnerXml%2A>, and the <xref:System.Xml.XmlDocument.Save%2A>, <xref:System.Xml.XmlDocument.WriteTo%2A>, and <xref:System.Xml.XmlDocument.WriteContentTo%2A> methods, the encoding written out in the XML declaration is taken from the <xref:System.Xml.XmlDeclaration> node.</span></span> <span data-ttu-id="4f0a4-119">Varsa hiçbir <xref:System.Xml.XmlDeclaration> düğümü <xref:System.Xml.XmlDeclaration> yazılmaz. Varsa, hiçbir kodlama <xref:System.Xml.XmlDeclaration> düğümü, kodlama değil yazılmış XML bildiriminde.</span><span class="sxs-lookup"><span data-stu-id="4f0a4-119">If there is no <xref:System.Xml.XmlDeclaration> node, <xref:System.Xml.XmlDeclaration> is not written out. If there is no encoding in the <xref:System.Xml.XmlDeclaration> node, encoding is not written out in the XML declaration.</span></span>  
  
 <span data-ttu-id="4f0a4-120"><xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> Ve <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> yöntemleri her zaman yazamadı bir <xref:System.Xml.XmlDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="4f0a4-120">The <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> and <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> methods always write out an <xref:System.Xml.XmlDeclaration>.</span></span> <span data-ttu-id="4f0a4-121">Bu yöntemler için yazma yazan gelen kodlama alın.</span><span class="sxs-lookup"><span data-stu-id="4f0a4-121">These methods take the encoding from the writer that it is writing to.</span></span> <span data-ttu-id="4f0a4-122">Diğer bir deyişle, belge ve buna kodlama yazan kodlama değerini geçersiz kılar <xref:System.Xml.XmlDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="4f0a4-122">That is, the encoding value on the writer overrides the encoding on the document and in the <xref:System.Xml.XmlDeclaration>.</span></span> <span data-ttu-id="4f0a4-123">Örneğin, aşağıdaki kod bir çıktı dosyasında bulunan XML bildirimindeki kodlama yazmaz `out.xml`.</span><span class="sxs-lookup"><span data-stu-id="4f0a4-123">For example, the following code does not write an encoding in the XML declaration found in the output file `out.xml`.</span></span>  
  
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
  
 <span data-ttu-id="4f0a4-124">İçin <xref:System.Xml.XmlDocument.Save%2A> yöntemi, XML bildirimi yazılmış kullanarak <xref:System.Xml.XmlWriter.WriteStartDocument%2A> yönteminde <xref:System.Xml.XmlWriter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4f0a4-124">For the <xref:System.Xml.XmlDocument.Save%2A> method, the XML declaration is written out using the <xref:System.Xml.XmlWriter.WriteStartDocument%2A> method in the <xref:System.Xml.XmlWriter> class.</span></span> <span data-ttu-id="4f0a4-125">Bu nedenle, üzerine <xref:System.Xml.XmlWriter.WriteStartDocument%2A> yöntemi değiştirir belge başlangıcı nasıl yazılır.</span><span class="sxs-lookup"><span data-stu-id="4f0a4-125">Therefore, overwriting the <xref:System.Xml.XmlWriter.WriteStartDocument%2A> method changes how the start of the document is written.</span></span>  
  
 <span data-ttu-id="4f0a4-126">İçin <xref:System.Xml.XmlDeclaration> üyeleri <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDeclaration.WriteTo%2A>, ve <xref:System.Xml.XmlNode.InnerXml%2A>, <xref:System.Xml.XmlDeclaration.Encoding%2A> özelliği ayarlı değil, hiçbir kodlama yazılır. Kodlama bulunan Aksi halde, XML bildiriminde yazılan kodlama aynıdır <xref:System.Xml.XmlDeclaration.Encoding%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="4f0a4-126">For the <xref:System.Xml.XmlDeclaration> members of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDeclaration.WriteTo%2A>, and <xref:System.Xml.XmlNode.InnerXml%2A>, if the <xref:System.Xml.XmlDeclaration.Encoding%2A> property is not set, no encoding is written out. Otherwise, the encoding written out in the XML declaration is the same as the encoding found in the <xref:System.Xml.XmlDeclaration.Encoding%2A> property.</span></span>  
  
## <a name="writing-document-content-using-the-outerxml-property"></a><span data-ttu-id="4f0a4-127">Yazma belgesinin içeriği OuterXml özelliğini kullanma</span><span class="sxs-lookup"><span data-stu-id="4f0a4-127">Writing Document Content Using the OuterXml Property</span></span>  
 <span data-ttu-id="4f0a4-128"><xref:System.Xml.XmlNode.OuterXml%2A> World Wide Web Konsorsiyumu (W3C) XML belge nesne modeli (DOM) standartları için bir Microsoft uzantısı bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="4f0a4-128">The <xref:System.Xml.XmlNode.OuterXml%2A> property is a Microsoft extension to the World Wide Web Consortium (W3C) XML Document Object Model (DOM) standards.</span></span> <span data-ttu-id="4f0a4-129"><xref:System.Xml.XmlNode.OuterXml%2A> Özelliği tüm XML belgenin biçimlendirme veya işaretleme yalnızca tek bir düğüme ve alt düğümleri almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4f0a4-129">The <xref:System.Xml.XmlNode.OuterXml%2A> property is used to get the markup of the whole XML document, or just the markup of a single node and its child nodes.</span></span> <span data-ttu-id="4f0a4-130"><xref:System.Xml.XmlNode.OuterXml%2A>Verilen düğüm ve tüm alt düğümlerini temsil eden biçimlendirme döndürür.</span><span class="sxs-lookup"><span data-stu-id="4f0a4-130"><xref:System.Xml.XmlNode.OuterXml%2A> returns the markup representing the given node and all its child nodes.</span></span>  
  
 <span data-ttu-id="4f0a4-131">Aşağıdaki kod örneği, bir belgeyi tamamının bir dize olarak kaydetmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4f0a4-131">The following code sample shows how to save a document in its entirety as a string.</span></span>  
  
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
  
 <span data-ttu-id="4f0a4-132">Aşağıdaki kod örneği, yalnızca belge öğesini kaydetmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4f0a4-132">The following code sample shows how to save only the document element.</span></span>  
  
```vb  
' For the content of the Document Element only.  
Dim xml As String = mydoc.DocumentElement.OuterXml  
```  
  
```csharp  
// For the content of the Document Element only.  
string xml = mydoc.DocumentElement.OuterXml;  
```  
  
 <span data-ttu-id="4f0a4-133">Buna karşılık, kullanabileceğiniz <xref:System.Xml.XmlNode.InnerText%2A> alt düğümleri içeriğini istiyorsanız özelliği.</span><span class="sxs-lookup"><span data-stu-id="4f0a4-133">In contrast, you can use the <xref:System.Xml.XmlNode.InnerText%2A> property if you want the content of child nodes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f0a4-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4f0a4-134">See Also</span></span>  
 [<span data-ttu-id="4f0a4-135">XML belge nesne modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="4f0a4-135">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
