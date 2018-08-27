---
title: DOM genişletme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: b5489c96-4afd-439a-a25d-fc82eb4a148d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 58f32dcb76246bed1030f3d0a45db2541f381877
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2018
ms.locfileid: "42908273"
---
# <a name="extending-the-dom"></a>DOM genişletme

Microsoft .NET Framework XML belge nesne modeli (DOM) uygulaması sağlayan bir temel sınıf kümesi içerir. <xref:System.Xml.XmlNode>Ve onun türetilmiş sınıfları, yöntemleri ve gidin olanak tanıyan özellikler sorgulamak ve içeriği ve yapısı bir XML belgesi değiştirme sağlar.

XML içeriği kullanılarak DOM'a belleğe yüklendiğinde oluşturulan düğümleri düğüm adı, düğüm türü vb. gibi bilgileri içerir. Temel sınıflar sağlamadığı belirli düğüm bilgileri gerektiren burada durumlar olabilir. Örneğin, satır numarasını ve düğümün konumu görmek isteyebilirsiniz. Bu durumda, yeni sınıflar mevcut DOM sınıflarından ve ek işlevler ekleyin.

Yeni sınıflar türetilirken iki genel kurallar şunlardır:

- Hiçbir zaman türetilir, önerilen <xref:System.Xml.XmlNode> sınıfı. Bunun yerine, ilgilendiğiniz düğüm türü için karşılık gelen sınıf sınıfların türetilmesi önerilir. Öznitelik düğümleri hakkında ek bilgi döndürmek isterseniz, örneğin, türetebilirsiniz <xref:System.Xml.XmlAttribute> sınıfı.

- Düğüm oluşturma yöntemleri dışında bir işlevi geçersiz kılarken, her zaman temel sürümü, işlev çağrısı ve ardından herhangi bir ek işleme ekleyin önerilir.

## <a name="creating-your-own-node-instances"></a>Kendi düğüm örnekleri oluşturma

<xref:System.Xml.XmlDocument> Sınıf düğümü oluşturma yöntemleri içerir. Bir XML dosyası yüklendiğinde düğümleri oluşturmak için bu yöntem çağrılır. Bir belge yüklendiğinde düğüm örneklerinizin oluşturulmasını sağlayacak şekilde bu yöntemleri geçersiz kılabilirsiniz. Genişlettiyseniz, örneğin, <xref:System.Xml.XmlElement> devralan sınıf <xref:System.Xml.XmlDocument> sınıf ve geçersiz kılma <xref:System.Xml.XmlDocument.CreateElement%2A> yöntemi.

Aşağıdaki örnek nasıl geçersiz kılınacağını gösterir <xref:System.Xml.XmlDocument.CreateElement%2A> uygulamanıza döndürülecek yöntemi <xref:System.Xml.XmlElement> sınıfı.

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
class LineInfoDocument : XmlDocument 
{
    public override XmlElement CreateElement(string prefix, string localname, string nsURI) 
    {
        LineInfoElement elem = new LineInfoElement(prefix, localname, nsURI, this);
        return elem;
    }
}
```

## <a name="extending-a-class"></a>Bir sınıf genişletme

Bir sınıf genişletmek için var olan DOM sınıflarının birinden sınıfınıza türetilir. Ardından, herhangi bir sanal yöntem ya da temel sınıfta özellikleri geçersiz kılabilir veya kendi uygulamanızı ekleyin.

Aşağıdaki örnekte, yeni bir sınıf oluşturulduğunda uygulayan <xref:System.Xml.XmlElement> sınıfı ve <xref:System.Xml.IXmlLineInfo> arabirimi. Ek yöntemleri ve özellikleri satır bilgileri toplamak kullanıcıların sağlayan tanımlanır.

```vb
Class LineInfoElement
   Inherits XmlElement
   Implements IXmlLineInfo
   Private lineNumber As Integer = 0
   Private linePosition As Integer = 0

   Friend Sub New(prefix As String, localname As String, nsURI As String, doc As XmlDocument)
      MyBase.New(prefix, localname, nsURI, doc)
      CType(doc, LineInfoDocument).IncrementElementCount()
   End Sub

   Public Sub SetLineInfo(linenum As Integer, linepos As Integer)
      lineNumber = linenum
      linePosition = linepos
   End Sub

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
   End Function
End Class ' End LineInfoElement class.
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

Aşağıdaki örnek, bir XML belgesi içindeki öğelerin sayısını sayar:

```vb
Imports System
Imports System.Xml
Imports System.IO

Class LineInfoDocument
   Inherits XmlDocument

   Private elementCount As Integer

   Friend Sub New()
      elementCount = 0
   End Sub

   Public Overrides Function CreateElement(prefix As String, localname As String, nsURI As String) As XmlElement
      Dim elem As New LineInfoElement(prefix, localname, nsURI, Me)
      Return elem
   End Function

   Public Sub IncrementElementCount()
      elementCount += 1
   End Sub

   Public Function GetCount() As Integer
      Return elementCount
   End Function
End Class 'End LineInfoDocument class.

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
   End Sub
End Class
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

#### <a name="input"></a>Giriş

Book.XML

```xml
<!--sample XML fragment-->
<book genre='novel' ISBN='1-861001-57-5' misc='sale-item'>
  <title>The Handmaid's Tale</title>
  <price>14.95</price>
</book>
```

#### <a name="output"></a>Çıkış

```console
Number of elements in book.xml: 3
```

## <a name="node-event-handler"></a>Düğüm olay işleyicisi

DOM .NET Framework uygulamasını ayrıca Al ve düğümleri bir XML belgesi değiştirdiğinizde olayları işlemek için sağlayan bir olay sistemi içerir. Kullanarak <xref:System.Xml.XmlNodeChangedEventHandler> ve <xref:System.Xml.XmlNodeChangedEventArgs> sınıfları yakalayabilirsiniz `NodeChanged`, `NodeChanging`, `NodeInserted`, `NodeInserting`, `NodeRemoved`, ve `NodeRemoving` olayları.

Özgün DOM sınıflarda gibi olay işleme işlemi tam olarak aynı türetilmiş sınıflarda çalışır.

Düğüm olay işleme hakkında daha fazla bilgi için bkz. [olayları](../../../../docs/standard/events/index.md) ve <xref:System.Xml.XmlNodeChangedEventHandler>.

## <a name="default-attributes-and-the-createelement-method"></a>Varsayılan öznitelikler ve CreateElement yöntemi

Kılıyorsa <xref:System.Xml.XmlDocument.CreateElement%2A> varsayılan belgesi düzenlenirken yeni öğeler oluştururken, öznitelikleri eklenip eklenmeyeceği türetilen bir sınıfta yöntemi. Düzenlenirken bir sorun budur. Çünkü <xref:System.Xml.XmlDocument.CreateElement%2A> yöntemdir varsayılan öznitelikler eklemek için sorumlu bir <xref:System.Xml.XmlDocument>, bu işlev kodu gerekir <xref:System.Xml.XmlDocument.CreateElement%2A> yöntemi. Yüklüyorsanız, size bir <xref:System.Xml.XmlDocument> , düzgün işlenecek, varsayılan öznitelikler içerir. Varsayılan öznitelikler hakkında daha fazla bilgi için bkz. [DOM öğeleri için yeni öznitelikler oluşturma](creating-new-attributes-for-elements-in-the-dom.md).

## <a name="see-also"></a>Ayrıca Bkz.

[XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)  
