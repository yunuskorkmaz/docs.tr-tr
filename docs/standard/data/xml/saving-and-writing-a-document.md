---
title: Belge Kaydetme ve Yazma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 097b0cb1-5743-4c3a-86ef-caf5cbe6750d
ms.openlocfilehash: 40d031c06f0b76668a634fac46b8defccce62f01
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289050"
---
# <a name="saving-and-writing-a-document"></a>Belge Kaydetme ve Yazma
Yüklediğinizde ve kaydettiğinizde <xref:System.Xml.XmlDocument> , kaydedilen belge orijinalden aşağıdaki yollarla farklılık gösterebilir:  
  
- <xref:System.Xml.XmlDocument.PreserveWhitespace%2A>Özelliği `true` yöntemi çağrılmadan önce olarak ayarlandıysa <xref:System.Xml.XmlDocument.Save%2A> , çıktıda boşluk korunur; Bu özellik ise `false` <xref:System.Xml.XmlDocument> çıktıyı otomatik olarak girintiler.  
  
- Öznitelikler arasındaki tüm boşluklar, tek bir boşluk karakteriyle azaltılır.  
  
- Öğeler arasındaki boşluk değişir. Önemli boşluk korunur ve çok önemli boşluk değildir. Ancak belge kaydedildiğinde, <xref:System.Xml.XmlTextWriter> çıktıyı daha okunabilir hale getirmek için varsayılan olarak, **girintilemeyi** seçerek yazdırmak için varsayılan olarak girintileme modunu kullanır.  
  
- Öznitelik değerleri etrafında kullanılan tırnak karakteri varsayılan olarak çift tırnak olarak değiştirilir. <xref:System.Xml.XmlTextReader.QuoteChar%2A> <xref:System.Xml.XmlTextWriter> Tırnak karakterini çift tırnak ya da tek tırnak olarak ayarlamak için üzerinde özelliğini kullanabilirsiniz.  
  
- Varsayılan olarak, benzer sayısal karakter varlıkları `{` genişletilir.  
  
- Giriş belgesinde bulunan bayt düzeni işareti korunmaz. Özel olarak farklı bir kodlama belirten bir XML bildirimi oluşturmadığınız sürece, UCS-2 UTF-8 olarak kaydedilir.  
  
- <xref:System.Xml.XmlDocument>' I bir dosyaya veya akışa yazmak isterseniz, yazılan çıkış belgenin içeriğiyle aynı olur. Diğer bir deyişle, <xref:System.Xml.XmlDeclaration> yalnızca belgede bulunan bir belge varsa yazılır ve belgeyi yazarken kullanılan kodlama, bildirim düğümünde belirtilen kodlamayla aynı olur.  
  
## <a name="writing-an-xmldeclaration"></a>XmlDeclaration yazma  
 , <xref:System.Xml.XmlDocument> Ve <xref:System.Xml.XmlDeclaration> <xref:System.Xml.XmlNode.OuterXml%2A> <xref:System.Xml.XmlNode.InnerXml%2A> <xref:System.Xml.XmlNode.WriteTo%2A> yöntemlerinin yanı sıra <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument.Save%2A> <xref:System.Xml.XmlDocument.WriteContentTo%2A> bir XML bildirimi oluşturur.  
  
 , Ve, <xref:System.Xml.XmlDocument> ve yöntemlerinin özellikleri için, <xref:System.Xml.XmlNode.OuterXml%2A> <xref:System.Xml.XmlDocument.InnerXml%2A> <xref:System.Xml.XmlDocument.Save%2A> <xref:System.Xml.XmlDocument.WriteTo%2A> <xref:System.Xml.XmlDocument.WriteContentTo%2A> XML bildiriminde yazılan kodlama <xref:System.Xml.XmlDeclaration> düğümden alınır. <xref:System.Xml.XmlDeclaration>Düğüm yoksa, <xref:System.Xml.XmlDeclaration> yazılmaz. Düğümde bir kodlama yoksa <xref:System.Xml.XmlDeclaration> , kodlama XML bildiriminde yazılmaz.  
  
 <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType>Ve <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> yöntemleri her zaman bir yazar <xref:System.Xml.XmlDeclaration> . Bu yöntemler, yazma yaptığı yazarın kodlamasını alır. Diğer bir deyişle, yazıcı üzerindeki kodlama değeri belgedeki ve içindeki kodlamayı geçersiz kılar <xref:System.Xml.XmlDeclaration> . Örneğin, aşağıdaki kod çıkış dosyasında bulunan XML bildiriminde bir kodlama yazmıyor `out.xml` .  
  
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
  
 Yöntemi için <xref:System.Xml.XmlDocument.Save%2A> , XML bildirimi <xref:System.Xml.XmlWriter.WriteStartDocument%2A> sınıfında yöntemi kullanılarak yazılır <xref:System.Xml.XmlWriter> . Bu nedenle, yöntemin üzerine yazılması <xref:System.Xml.XmlWriter.WriteStartDocument%2A> belgenin başlangıcını nasıl yazıldığı değişir.  
  
 , <xref:System.Xml.XmlDeclaration> Ve üyeleri için <xref:System.Xml.XmlNode.OuterXml%2A> , <xref:System.Xml.XmlDeclaration.WriteTo%2A> <xref:System.Xml.XmlNode.InnerXml%2A> <xref:System.Xml.XmlDeclaration.Encoding%2A> özelliği ayarlanmamışsa, hiçbir kodlama yazılmaz. Aksi halde, XML bildiriminde yazılan kodlama, özelliğinde bulunan kodlamayla aynı olur <xref:System.Xml.XmlDeclaration.Encoding%2A> .  
  
## <a name="writing-document-content-using-the-outerxml-property"></a>OuterXml özelliğini kullanarak belge Içeriği yazma  
 <xref:System.Xml.XmlNode.OuterXml%2A>Özelliği, World Wide Web Konsorsiyumu (W3C) XML belge nesne modeli (DOM) standartlarına yönelik bir Microsoft uzantısıdır. <xref:System.Xml.XmlNode.OuterXml%2A>Özelliği tüm XML belgesinin işaretlemesini veya yalnızca tek bir düğümün ve onun alt düğümlerinin işaretlemesini almak için kullanılır. <xref:System.Xml.XmlNode.OuterXml%2A>verilen düğümü ve onun tüm alt düğümlerini temsil eden biçimlendirmeyi döndürür.  
  
 Aşağıdaki kod örneği, bir belgenin tamamen dize olarak nasıl kaydedileceğini gösterir.  
  
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
  
 Aşağıdaki kod örneğinde, yalnızca belge öğesinin nasıl kaydedileceği gösterilmektedir.  
  
```vb  
' For the content of the Document Element only.  
Dim xml As String = mydoc.DocumentElement.OuterXml  
```  
  
```csharp  
// For the content of the Document Element only.  
string xml = mydoc.DocumentElement.OuterXml;  
```  
  
 Buna karşılık, <xref:System.Xml.XmlNode.InnerText%2A> alt düğümlerin içeriğini istiyorsanız özelliğini kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)
