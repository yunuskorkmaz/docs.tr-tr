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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2138b9c47c6e41cd94e775eaed005d8a6fd976c9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="saving-and-writing-a-document"></a>Kaydetme ve bir belgeyi yazma
Ne zaman yükle ve Kaydet bir <xref:System.Xml.XmlDocument>, aşağıdaki yollarla kaydedilmiş belge orijinal olandan farklı olabilir:  
  
-   Varsa <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> özelliği ayarlanmış `true` önce <xref:System.Xml.XmlDocument.Save%2A> yöntemi çağrıldığında, boşluk belgesinde, çıkış; korunur, bu özellik ise `false`, <xref:System.Xml.XmlDocument> otomatik girintileri çıktı.  
  
-   Öznitelikler arasındaki tüm boşluk bir tek boşluk karakteri azalır.  
  
-   Öğeler arasında boşluk değiştirilir. Önemli boşluk korunur ve önemsiz boşluk değil. Ancak Belge kaydedildiğinde kullanacağı <xref:System.Xml.XmlTextWriter> **Indenting** düzgün çıktıyı daha okunabilir hale yazdırmak için varsayılan modu.  
  
-   Öznitelik değerlerinin kullanılan tırnak karakteri çift tırnak varsayılan olarak değiştirilir. Kullanabileceğiniz <xref:System.Xml.XmlTextReader.QuoteChar%2A> özellikte <xref:System.Xml.XmlTextWriter> adınızda çift tırnak işareti ya da tek tırnaklı için ayarlanacak.  
  
-   Varsayılan olarak, sayısal karakter varlıkları ister `{` genişletilir.  
  
-   Giriş belgesinde bulunan bayt sırası işareti korunmaz. Farklı bir kodlama belirten bir XML bildirimi açıkça oluşturmadan UCS-2 UTF-8 olarak kaydedilir.  
  
-   Dışına yazmak istiyorsanız <xref:System.Xml.XmlDocument> bir dosya veya akış içine yazılan çıktı belgesinin içeriği aynıdır. Diğer bir deyişle, <xref:System.Xml.XmlDeclaration> bir belgedeki ve belgeyi kullanıma yazılırken kullanılan bildirimi düğümünde verilen aynı kodlama kodlamadır yalnızca yazılır.  
  
## <a name="writing-an-xmldeclaration"></a>Bir XmlDeclaration yazma  
 <xref:System.Xml.XmlDocument> Ve <xref:System.Xml.XmlDeclaration> üyeleri <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlNode.InnerXml%2A>, ve <xref:System.Xml.XmlNode.WriteTo%2A>, ek olarak <xref:System.Xml.XmlDocument> yöntemlerinin <xref:System.Xml.XmlDocument.Save%2A> ve <xref:System.Xml.XmlDocument.WriteContentTo%2A>, bir XML bildirimi oluştur.  
  
 İçin <xref:System.Xml.XmlDocument> özelliklerini <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDocument.InnerXml%2A>ve <xref:System.Xml.XmlDocument.Save%2A>, <xref:System.Xml.XmlDocument.WriteTo%2A>, ve <xref:System.Xml.XmlDocument.WriteContentTo%2A> yöntemleri, gelen alınır XML bildiriminde yazılan kodlama <xref:System.Xml.XmlDeclaration> düğümü. Varsa hiçbir <xref:System.Xml.XmlDeclaration> düğümü <xref:System.Xml.XmlDeclaration> yazılmaz. Varsa, hiçbir kodlama <xref:System.Xml.XmlDeclaration> düğümü, kodlama değil yazılmış XML bildiriminde.  
  
 <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> Ve <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> yöntemleri her zaman yazamadı bir <xref:System.Xml.XmlDeclaration>. Bu yöntemler için yazma yazan gelen kodlama alın. Diğer bir deyişle, belge ve buna kodlama yazan kodlama değerini geçersiz kılar <xref:System.Xml.XmlDeclaration>. Örneğin, aşağıdaki kod bir çıktı dosyasında bulunan XML bildirimindeki kodlama yazmaz `out.xml`.  
  
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
  
 İçin <xref:System.Xml.XmlDocument.Save%2A> yöntemi, XML bildirimi yazılmış kullanarak <xref:System.Xml.XmlWriter.WriteStartDocument%2A> yönteminde <xref:System.Xml.XmlWriter> sınıfı. Bu nedenle, üzerine <xref:System.Xml.XmlWriter.WriteStartDocument%2A> yöntemi değiştirir belge başlangıcı nasıl yazılır.  
  
 İçin <xref:System.Xml.XmlDeclaration> üyeleri <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDeclaration.WriteTo%2A>, ve <xref:System.Xml.XmlNode.InnerXml%2A>, <xref:System.Xml.XmlDeclaration.Encoding%2A> özelliği ayarlı değil, hiçbir kodlama yazılır. Kodlama bulunan Aksi halde, XML bildiriminde yazılan kodlama aynıdır <xref:System.Xml.XmlDeclaration.Encoding%2A> özelliği.  
  
## <a name="writing-document-content-using-the-outerxml-property"></a>Yazma belgesinin içeriği OuterXml özelliğini kullanma  
 <xref:System.Xml.XmlNode.OuterXml%2A> World Wide Web Konsorsiyumu (W3C) XML belge nesne modeli (DOM) standartları için bir Microsoft uzantısı bir özelliktir. <xref:System.Xml.XmlNode.OuterXml%2A> Özelliği tüm XML belgenin biçimlendirme veya işaretleme yalnızca tek bir düğüme ve alt düğümleri almak için kullanılır. <xref:System.Xml.XmlNode.OuterXml%2A>Verilen düğüm ve tüm alt düğümlerini temsil eden biçimlendirme döndürür.  
  
 Aşağıdaki kod örneği, bir belgeyi tamamının bir dize olarak kaydetmek gösterilmiştir.  
  
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
  
 Aşağıdaki kod örneği, yalnızca belge öğesini kaydetmek gösterilmiştir.  
  
```vb  
' For the content of the Document Element only.  
Dim xml As String = mydoc.DocumentElement.OuterXml  
```  
  
```csharp  
// For the content of the Document Element only.  
string xml = mydoc.DocumentElement.OuterXml;  
```  
  
 Buna karşılık, kullanabileceğiniz <xref:System.Xml.XmlNode.InnerText%2A> alt düğümleri içeriğini istiyorsanız özelliği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
