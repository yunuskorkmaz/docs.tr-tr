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
# <a name="saving-and-writing-a-document"></a>Belge Kaydetme ve Yazma
Yüklediğinizde ve kaydettiğinizde <xref:System.Xml.XmlDocument>, kaydedilen belge orijinalden aşağıdaki yollarla farklılık gösterebilir:  
  
- Özelliği yöntemi çağrılmadan önce olarak `true` ayarlandıysa, çıktıda boşluk korunur; <xref:System.Xml.XmlDocument.Save%2A> <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> Bu özellik ise `false`çıktıyı <xref:System.Xml.XmlDocument> otomatik girintiler.  
  
- Öznitelikler arasındaki tüm boşluklar, tek bir boşluk karakteriyle azaltılır.  
  
- Öğeler arasındaki boşluk değişir. Önemli boşluk korunur ve çok önemli boşluk değildir. Ancak belge kaydedildiğinde, çıktıyı daha okunabilir hale getirmek için varsayılan <xref:System.Xml.XmlTextWriter> olarak, **girintilemeyi** seçerek yazdırmak için varsayılan olarak girintileme modunu kullanır.  
  
- Öznitelik değerleri etrafında kullanılan tırnak karakteri varsayılan olarak çift tırnak olarak değiştirilir. Tırnak karakterini çift tırnak <xref:System.Xml.XmlTextReader.QuoteChar%2A> ya da <xref:System.Xml.XmlTextWriter> tek tırnak olarak ayarlamak için üzerinde özelliğini kullanabilirsiniz.  
  
- Varsayılan olarak, benzer `{` sayısal karakter varlıkları genişletilir.  
  
- Giriş belgesinde bulunan bayt düzeni işareti korunmaz. Özel olarak farklı bir kodlama belirten bir XML bildirimi oluşturmadığınız sürece, UCS-2 UTF-8 olarak kaydedilir.  
  
- ' I bir dosyaya veya akışa yazmak <xref:System.Xml.XmlDocument> isterseniz, yazılan çıkış belgenin içeriğiyle aynı olur. Diğer bir deyişle <xref:System.Xml.XmlDeclaration> , yalnızca belgede bulunan bir belge varsa yazılır ve belgeyi yazarken kullanılan kodlama, bildirim düğümünde belirtilen kodlamayla aynı olur.  
  
## <a name="writing-an-xmldeclaration"></a>XmlDeclaration yazma  
 <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument> , Ve <xref:System.Xml.XmlDocument.Save%2A> yöntemlerinin <xref:System.Xml.XmlDocument.WriteContentTo%2A>yanı sıra bir XML bildirimi oluşturur. <xref:System.Xml.XmlDeclaration> <xref:System.Xml.XmlNode.OuterXml%2A> <xref:System.Xml.XmlNode.InnerXml%2A> <xref:System.Xml.XmlNode.WriteTo%2A>  
  
 , Ve <xref:System.Xml.XmlDocument> , ve <xref:System.Xml.XmlNode.OuterXml%2A> <xref:System.Xml.XmlDocument.WriteContentTo%2A> yöntemlerinin <xref:System.Xml.XmlDocument.InnerXml%2A>özellikleri <xref:System.Xml.XmlDocument.Save%2A> <xref:System.Xml.XmlDocument.WriteTo%2A>için, XML bildiriminde yazılan kodlama <xref:System.Xml.XmlDeclaration> düğümden alınır. <xref:System.Xml.XmlDeclaration> Düğüm yoksa, <xref:System.Xml.XmlDeclaration> yazılmaz. <xref:System.Xml.XmlDeclaration> Düğümde bir kodlama yoksa, kodlama XML bildiriminde yazılmaz.  
  
 <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> Ve <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> yöntemleri her zaman bir <xref:System.Xml.XmlDeclaration>yazar. Bu yöntemler, yazma yaptığı yazarın kodlamasını alır. Diğer bir deyişle, yazıcı üzerindeki kodlama değeri belgedeki ve içindeki kodlamayı geçersiz kılar <xref:System.Xml.XmlDeclaration>. Örneğin, aşağıdaki kod çıkış dosyasında `out.xml`bulunan XML bildiriminde bir kodlama yazmıyor.  
  
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
  
 <xref:System.Xml.XmlDocument.Save%2A> Yöntemi IÇIN, XML bildirimi <xref:System.Xml.XmlWriter.WriteStartDocument%2A> <xref:System.Xml.XmlWriter> sınıfında yöntemi kullanılarak yazılır. Bu nedenle, <xref:System.Xml.XmlWriter.WriteStartDocument%2A> yöntemin üzerine yazılması belgenin başlangıcını nasıl yazıldığı değişir.  
  
 , Ve <xref:System.Xml.XmlDeclaration> <xref:System.Xml.XmlNode.OuterXml%2A> <xref:System.Xml.XmlNode.InnerXml%2A> <xref:System.Xml.XmlDeclaration.Encoding%2A> üyeleri <xref:System.Xml.XmlDeclaration.WriteTo%2A>için, özelliği ayarlanmamışsa, hiçbir kodlama yazılmaz. Aksi halde, XML bildiriminde yazılan kodlama, <xref:System.Xml.XmlDeclaration.Encoding%2A> özelliğinde bulunan kodlamayla aynı olur.  
  
## <a name="writing-document-content-using-the-outerxml-property"></a>OuterXml özelliğini kullanarak belge Içeriği yazma  
 <xref:System.Xml.XmlNode.OuterXml%2A> Özelliği, world WIDE Web KONSORSIYUMU (W3C) XML belge nesne MODELI (DOM) standartlarına yönelik bir Microsoft uzantısıdır. <xref:System.Xml.XmlNode.OuterXml%2A> ÖZELLIĞI tüm XML belgesinin işaretlemesini veya yalnızca tek bir düğümün ve onun alt düğümlerinin işaretlemesini almak için kullanılır. <xref:System.Xml.XmlNode.OuterXml%2A>verilen düğümü ve onun tüm alt düğümlerini temsil eden biçimlendirmeyi döndürür.  
  
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
  
 Buna karşılık, alt düğümlerin içeriğini istiyorsanız <xref:System.Xml.XmlNode.InnerText%2A> özelliğini kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
