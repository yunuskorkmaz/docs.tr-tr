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
# <a name="saving-and-writing-a-document"></a>Belge Kaydetme ve Yazma
Ne zaman yükler ve kaydeder bir <xref:System.Xml.XmlDocument>, aşağıdaki yollarla kaydedilmiş belge orijinalden farklı olabilir:  
  
- Varsa <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> özelliği `true` önce <xref:System.Xml.XmlDocument.Save%2A> yöntemi çağrıldığında, boşluk belgedeki; çıktısında korunur, bu özellik ise `false`, <xref:System.Xml.XmlDocument> otomatik girintileri çıktı.  
  
- Öznitelikler arasındaki tüm boşluk tek bir boşluk olarak azaltılır.  
  
- Öğeler arasındaki boşluk değiştirilir. Önemli boşluk korunur ve önemsiz boşluk değildir. Ancak Belge kaydedildiğinde kullanacak <xref:System.Xml.XmlTextWriter> **Indenting** düzgünce daha okunabilir yapmak için Çıkış'ı yazdırmak için varsayılan modu.  
  
- Kullanılan öznitelik değeri tırnak karakteri için çift tırnak işareti, varsayılan olarak değiştirilir. Kullanabileceğiniz <xref:System.Xml.XmlTextReader.QuoteChar%2A> özelliği <xref:System.Xml.XmlTextWriter> teklif karakter çift tırnak işareti veya tek tırnak işareti ayarlamak için.  
  
- Varsayılan olarak, sayısal karakter varlıkları ister `{` genişletilir.  
  
- Giriş belgesinde bulunan bayt sırası işareti korunmaz. Farklı bir kodlama belirten bir XML bildirimi açıkça oluşturmadığınız sürece UCS-2 UTF-8 kaydedilir.  
  
- Yazmak isterseniz <xref:System.Xml.XmlDocument> bir dosya veya akışı içine yazılan çıktıyı belgenin içeriğini aynıdır. Diğer bir deyişle, <xref:System.Xml.XmlDeclaration> bir belgede yer alan ve belgeyi yazılırken kullanılan kodlama bildirimi düğümde verilen aynı kodlama olup olmadığını yalnızca yazılır.  
  
## <a name="writing-an-xmldeclaration"></a>Bir XmlDeclaration yazma  
 <xref:System.Xml.XmlDocument> Ve <xref:System.Xml.XmlDeclaration> üyeleri <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlNode.InnerXml%2A>, ve <xref:System.Xml.XmlNode.WriteTo%2A>, ek olarak <xref:System.Xml.XmlDocument> yöntemlerinin <xref:System.Xml.XmlDocument.Save%2A> ve <xref:System.Xml.XmlDocument.WriteContentTo%2A>, bir XML bildirimi oluştur.  
  
 İçin <xref:System.Xml.XmlDocument> özelliklerini <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDocument.InnerXml%2A>ve <xref:System.Xml.XmlDocument.Save%2A>, <xref:System.Xml.XmlDocument.WriteTo%2A>, ve <xref:System.Xml.XmlDocument.WriteContentTo%2A> yöntemleri öğesinden alınır XML bildiriminde yazılan kodlama <xref:System.Xml.XmlDeclaration> düğümü. Yoksa hiçbir <xref:System.Xml.XmlDeclaration> düğümünün <xref:System.Xml.XmlDeclaration> yazılır değil. Varsa, hiçbir kodlama <xref:System.Xml.XmlDeclaration> düğümü, kodlama değil yazılmış XML bildiriminde.  
  
 <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> Ve <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> yöntem yazılmasına yarar her zaman bir <xref:System.Xml.XmlDeclaration>. Bu yöntemler için yazı yazan gelen kodlamayı Al. Diğer bir deyişle, belge üzerinde hem de kodlama yazıcısı kodlama değeri geçersiz kılar <xref:System.Xml.XmlDeclaration>. Örneğin, aşağıdaki kod bir çıkış dosyasında bulunan XML bildirimindeki kodlama yazmaz `out.xml`.  
  
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
  
 İçin <xref:System.Xml.XmlDocument.Save%2A> yöntemi, XML bildirimi yazılmış kullanarak <xref:System.Xml.XmlWriter.WriteStartDocument%2A> yönteminde <xref:System.Xml.XmlWriter> sınıfı. Bu nedenle, üzerine <xref:System.Xml.XmlWriter.WriteStartDocument%2A> yöntemi değiştirir belgenin başlangıcı nasıl yazılır.  
  
 İçin <xref:System.Xml.XmlDeclaration> üyeleri <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDeclaration.WriteTo%2A>, ve <xref:System.Xml.XmlNode.InnerXml%2A>, <xref:System.Xml.XmlDeclaration.Encoding%2A> özelliği ayarlı değil, hiçbir kodlama yazılır. Kodlama bulunan Aksi takdirde, XML bildiriminde yazılan kodlama aynıdır <xref:System.Xml.XmlDeclaration.Encoding%2A> özelliği.  
  
## <a name="writing-document-content-using-the-outerxml-property"></a>Belge içerik yazma OuterXml özelliğini kullanma  
 <xref:System.Xml.XmlNode.OuterXml%2A> Özelliği, World Wide Web Consortium (W3C) XML belge nesne modeli (DOM) standartları için bir Microsoft uzantısıdır. <xref:System.Xml.XmlNode.OuterXml%2A> Özelliği, biçimlendirmeyi tüm XML belgesi veya biçimlendirme yalnızca tek bir düğüm ve onun alt düğümleri almak için kullanılır. <xref:System.Xml.XmlNode.OuterXml%2A> Verilen düğüm ve onun tüm alt düğümleri temsil eden biçimlendirme döndürür.  
  
 Aşağıdaki kod örneği, belgeye bir dize olarak tamamen kaydetmek gösterilmektedir.  
  
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
  
 Aşağıdaki kod örneği, yalnızca belge öğesi kaydedileceği gösterilmektedir.  
  
```vb  
' For the content of the Document Element only.  
Dim xml As String = mydoc.DocumentElement.OuterXml  
```  
  
```csharp  
// For the content of the Document Element only.  
string xml = mydoc.DocumentElement.OuterXml;  
```  
  
 Buna karşılık, kullanabileceğiniz <xref:System.Xml.XmlNode.InnerText%2A> alt düğümleri içeriğini istiyorsanız özelliği.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
