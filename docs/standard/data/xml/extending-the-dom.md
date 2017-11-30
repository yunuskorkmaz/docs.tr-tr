---
title: "DOM genişletme"
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
ms.assetid: b5489c96-4afd-439a-a25d-fc82eb4a148d
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b91c49be9268d8dc967daeac116cf67b2ed7d742
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="extending-the-dom"></a>DOM genişletme
Microsoft .NET Framework uygulaması XML belge nesne modeli (DOM) sağlayan bir temel sınıfları içerir. <xref:System.Xml.XmlNode>Ve kendi türetilmiş sınıfları, yöntemleri ve gidin olanak tanıyan özellikler sorgulamak ve içeriği ve bir XML belgesi yapısını değiştirmek sağlar.  
  
 XML içeriği DOM kullanarak belleğe yüklendiğinde oluşturulan düğümler düğüm adı, düğüm türü vb. gibi bilgileri içerir. Temel sınıflar sağlıyor mu belirli düğüm bilgi gerektiren burada durumlar olabilir. Örneğin, satır numarası ve düğüm konumunu görmek isteyebilirsiniz. Bu durumda, yeni sınıflar mevcut DOM sınıflarından ve ek işlevsellik ekleyin.  
  
 Yeni sınıflar türetilirken iki genel kurallar şunlardır:  
  
-   Hiçbir zaman öğesinden türetilen olduğunu önerilir <xref:System.Xml.XmlNode> sınıfı. Bunun yerine, ilgilendiğiniz düğüm türü için karşılık gelen sınıf sınıf türetin önerilir. Özniteliği düğümlerinde ek döndürmesini istiyorsanız, örneğin, gelen türetilemeyeceğini <xref:System.Xml.XmlAttribute> sınıfı.  
  
-   Düğüm oluşturma yöntemleri dışında bir işlevi geçersiz kılarken, her zaman işlevi temel sürümünü çağırın ve herhangi bir ek işlem eklemek, önerilir.  
  
## <a name="creating-your-own-node-instances"></a>Kendi düğüm örnekleri oluşturma  
 <xref:System.Xml.XmlDocument> Sınıfı düğüm oluşturma yöntemlerini içerir. Bir XML dosyası yüklendiğinde, bu yöntemleri düğümleri oluşturmak için denir. Böylece bir belge yüklendiğinde düğümü örneklerinizi oluşturulan bu yöntemleri geçersiz kılabilirsiniz. Örneğin, genişlettiyseniz <xref:System.Xml.XmlElement> devral sınıfı, <xref:System.Xml.XmlDocument> sınıfı ve geçersiz kılma <xref:System.Xml.XmlDocument.CreateElement%2A> yöntemi.  
  
 Aşağıdaki örnekte nasıl geçersiz kılınacağını gösterir <xref:System.Xml.XmlDocument.CreateElement%2A> uygulamanıza döndürülecek yöntemi <xref:System.Xml.XmlElement> sınıfı.  
  
```vb  
Class LineInfoDocument  
    Inherits XmlDocument  
        Public Overrides Function CreateElement(prefix As String, localname As String, nsURI As String) As XmlElement  
        Dim elem As New LineInfoElement(prefix, localname, nsURI, Me)  
        Return elem  
    End Function 'CreateElement  
End Class 'LineInfoDocument  
```  
  
```csharp  
class LineInfoDocument : XmlDocument {  
  public override XmlElement CreateElement(string prefix, string localname, string nsURI) {  
  LineInfoElement elem = new LineInfoElement(prefix, localname, nsURI, this);  
  return elem;  
  }  
```  
  
## <a name="extending-a-class"></a>Bir sınıf genişletme  
 Bir sınıf genişletmek için varolan DOM sınıflarının birinden, sınıf türetin. Sanal yöntemler veya temel sınıf özelliklerini geçersiz kılabilir veya kendi ekleyin.  
  
 Aşağıdaki örnekte, yeni bir sınıf oluşturulur, hangi uygulayan <xref:System.Xml.XmlElement> sınıfı ve <xref:System.Xml.IXmlLineInfo> arabirimi. Satırı bilgileri toplamak kullanıcıların sağlayan ek yöntemleri ve özellikleri tanımlanır.  
  
```vb  
Class LineInfoElement  
   Inherits XmlElement  
   Implements IXmlLineInfo  
   Private lineNumber As Integer = 0  
   Private linePosition As Integer = 0  
  
   Friend Sub New(prefix As String, localname As String, nsURI As String, doc As XmlDocument)  
      MyBase.New(prefix, localname, nsURI, doc)  
      CType(doc, LineInfoDocument).IncrementElementCount()  
   End Sub 'New  
  
   Public Sub SetLineInfo(linenum As Integer, linepos As Integer)  
      lineNumber = linenum  
      linePosition = linepos  
   End Sub 'SetLineInfo  
  
   Public ReadOnly Property LineNumber() As Integer  
      Get  
         Return lineNumber  
      End Get  
   End Property  
  
   Public ReadOnly Property LinePosition() As Integer  
      Get  
         Return linePosition  
      End Get  
   End Property  
  
   Public Function HasLineInfo() As Boolean  
      Return True  
   End Function 'HasLineInfo  
End Class 'LineInfoElement ' End LineInfoElement class.  
```  
  
```csharp  
class LineInfoElement : XmlElement, IXmlLineInfo {  
   int lineNumber = 0;  
   int linePosition = 0;  
   internal LineInfoElement( string prefix, string localname, string nsURI, XmlDocument doc ) : base( prefix, localname, nsURI, doc ) {  
       ( (LineInfoDocument)doc ).IncrementElementCount();  
  }     
  public void SetLineInfo( int linenum, int linepos ) {  
      lineNumber = linenum;  
      linePosition = linepos;  
  }  
  public int LineNumber {  
     get {  
       return lineNumber;  
     }  
  }  
  public int LinePosition {  
      get {  
        return linePosition;  
      }  
  }  
  public bool HasLineInfo() {   
    return true;   
  }  
} // End LineInfoElement class.  
```  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek bir XML belgesi öğelerinde sayar.  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.IO  
  
 _  
  
Class LineInfoDocument  
   Inherits XmlDocument  
  
   Private elementCount As Integer  
  
   Friend Sub New()  
      elementCount = 0  
   End Sub 'New  
  
   Public Overrides Function CreateElement(prefix As String, localname As String, nsURI As String) As XmlElement  
      Dim elem As New LineInfoElement(prefix, localname, nsURI, Me)  
      Return elem  
   End Function 'CreateElement  
  
   Public Sub IncrementElementCount()  
      elementCount += 1  
   End Sub 'IncrementElementCount  
  
   Public Function GetCount() As Integer  
      Return elementCount  
   End Function 'GetCount  
End Class 'LineInfoDocument  
 _ 'End LineInfoDocument class.  
  
Class LineInfoElement  
   Inherits XmlElement  
  
   Friend Sub New(prefix As String, localname As String, nsURI As String, doc As XmlDocument)  
      MyBase.New(prefix, localname, nsURI, doc)  
      CType(doc, LineInfoDocument).IncrementElementCount()  
   End Sub 'New  
End Class 'LineInfoElement  
 _ 'End LineInfoElement class.  
  
Public Class Test  
  
   Private filename As [String] = "book.xml"  
  
   Public Shared Sub Main()  
  
      Dim doc As New LineInfoDocument()  
      doc.Load(filename)  
      Console.WriteLine("Number of elements in {0}: {1}", filename, doc.GetCount())  
   End Sub 'Main   
End Class 'Test  
```  
  
```csharp  
using System;  
using System.Xml;  
using System.IO;  
  
class LineInfoDocument : XmlDocument {  
  
  int elementCount;  
  internal LineInfoDocument():base() {  
    elementCount = 0;  
  }  
  
  public override XmlElement CreateElement( string prefix, string localname, string nsURI) {  
    LineInfoElement elem = new LineInfoElement(prefix, localname, nsURI, this );  
    return elem;  
  }  
  
  public void IncrementElementCount() {  
     elementCount++;  
  }  
  
  public int GetCount() {  
     return elementCount;  
  }  
} // End LineInfoDocument class.  
  
class LineInfoElement:XmlElement {  
  
    internal LineInfoElement( string prefix, string localname, string nsURI, XmlDocument doc ):base( prefix,localname,nsURI, doc ){  
      ((LineInfoDocument)doc).IncrementElementCount();  
    }     
} // End LineInfoElement class.  
  
public class Test {  
  
  const String filename = "book.xml";  
  public static void Main() {  
  
     LineInfoDocument doc =new LineInfoDocument();  
     doc.Load(filename);      
     Console.WriteLine("Number of elements in {0}: {1}", filename, doc.GetCount());  
  
  }  
}   
```  
  
##### <a name="input"></a>Giriş  
 Book.XML  
  
```xml  
<!--sample XML fragment-->  
<book genre='novel' ISBN='1-861001-57-5' misc='sale-item'>  
  <title>The Handmaid's Tale</title>  
  <price>14.95</price>  
</book>  
```  
  
##### <a name="output"></a>Çıkış  
  
```  
Number of elements in book.xml: 3  
```  
  
 Www.gotdotnet.com/userfiles/XMLDom/extendDOM.zip XML DOM sınıfları (System.Xml) genişletmek nasıl gösteren bir örnek için bkz.  
  
## <a name="node-event-handler"></a>Düğüm olay işleyicisi  
 DOM .NET Framework uygulamasını almak ve bir XML belgesi düğümler değiştirdiğinizde olayları işlemek sağlayan bir olay sistem de içerir. Kullanarak <xref:System.Xml.XmlNodeChangedEventHandler> ve <xref:System.Xml.XmlNodeChangedEventArgs> sınıfları yakalayabilirsiniz `NodeChanged`, `NodeChanging`, `NodeInserted`, `NodeInserting`, `NodeRemoved`, ve `NodeRemoving` olaylar.  
  
 Özgün DOM sınıflarda gibi olay işleme işlemi tam olarak aynı türetilmiş sınıflarda çalışır.  
  
 Düğüm olay işleme hakkında daha fazla bilgi için bkz: [olayları](../../../../docs/standard/events/index.md) ve <xref:System.Xml.XmlNodeChangedEventHandler>.  
  
## <a name="default-attributes-and-the-createelement-method"></a>Varsayılan öznitelikleri ve CreateElement yöntemi  
 Kılıyorsa <xref:System.Xml.XmlDocument.CreateElement%2A> türetilmiş bir sınıf, varsayılan belge düzenlerken yeni öğeler oluştururken, öznitelikler eklenip eklenmeyeceği yöntemi. Bu yalnızca bir düzenlenirken bir sorundur. Çünkü <xref:System.Xml.XmlDocument.CreateElement%2A> yöntemdir varsayılan öznitelikler eklemek için sorumlu bir <xref:System.Xml.XmlDocument>, bu işlev kod <xref:System.Xml.XmlDocument.CreateElement%2A> yöntemi. Yüklüyorsanız, size bir <xref:System.Xml.XmlDocument> varsayılan öznitelikleri içeren, düzgün işlenecek. Varsayılan öznitelikleri hakkında daha fazla bilgi için bkz: [DOM öğeleri için yeni öznitelikler oluşturma](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML belge nesne modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
