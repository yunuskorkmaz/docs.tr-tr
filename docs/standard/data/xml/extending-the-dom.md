---
title: DOM Genişletme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: b5489c96-4afd-439a-a25d-fc82eb4a148d
ms.openlocfilehash: 11c7e8c8d2ea3b49fe73ab4dde4e2ccc8bc917ff
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159682"
---
# <a name="extending-the-dom"></a>DOM Genişletme

Microsoft .NET Framework, XML Belge Nesne Modeli (DOM) uygulamasını sağlayan bir temel sınıf kümesi içerir. <xref:System.Xml.XmlNode>Ve türetilmiş sınıfları, bir XML belgesinin içeriğini ve yapısını gezinmenize, sorgulamanızı ve değiştirebilmeniz için yöntemler ve özellikler sağlar.

XML içeriği DOM kullanılarak belleğe yüklendiğinde oluşturulan düğümler düğüm adı, düğüm türü vb. gibi bilgiler içerir. Temel sınıfların sağlamadığı belirli düğüm bilgilerinin gerekli olduğu durumlar olabilir. Örneğin, düğümün satır numarasını ve konumunu görmek isteyebilirsiniz. Bu durumda, var olan DOM sınıflarından yeni sınıflar türetebilir ve ek işlevler ekleyebilirsiniz.

Yeni sınıflar türetmede iki genel kılavuz vardır:

- <xref:System.Xml.XmlNode> Sınıfından hiçbir şekilde türetmeniz önerilir. Bunun yerine, ilgilendiğiniz düğüm türüne karşılık gelen sınıftan sınıfları türetmeniz önerilir. Örneğin, öznitelik düğümleri hakkında ek bilgi döndürmek istiyorsanız <xref:System.Xml.XmlAttribute> sınıfından türetebilirsiniz.

- Düğüm oluşturma yöntemleri hariç, bir işlevi geçersiz kıldığınızda, işlevin temel sürümünü her zaman çağırmanız ve sonra ek işlem eklemeniz önerilir.

## <a name="creating-your-own-node-instances"></a>Kendi düğüm örneklerinizi oluşturma

Sınıfı <xref:System.Xml.XmlDocument> , düğüm oluşturma yöntemlerini içerir. Bir XML dosyası yüklendiğinde, düğümleri oluşturmak için bu yöntemler çağırılır. Bir belge yüklendiğinde düğüm örneklerinizin oluşturulması için bu yöntemleri geçersiz kılabilirsiniz. Örneğin, <xref:System.Xml.XmlElement> sınıfı genişlettiyseniz, <xref:System.Xml.XmlDocument> sınıfını miras alıp <xref:System.Xml.XmlDocument.CreateElement%2A> yöntemi geçersiz kılabilirsiniz.

Aşağıdaki örnek, <xref:System.Xml.XmlDocument.CreateElement%2A> <xref:System.Xml.XmlElement> sınıfının uygulamanızı döndürmek için yönteminin nasıl geçersiz kılınacağını göstermektedir.

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

## <a name="extending-a-class"></a>Sınıf genişletme

Bir sınıfı genişletmek için, varolan DOM sınıflarından birindeki sınıfınızı türetebilirsiniz. Daha sonra, temel sınıftaki sanal yöntemlerin veya özelliklerden birini geçersiz kılabilir ya da kendinizinkini ekleyebilirsiniz.

Aşağıdaki örnekte, <xref:System.Xml.XmlElement> sınıfını ve <xref:System.Xml.IXmlLineInfo> arabirimini uygulayan yeni bir sınıf oluşturulur. Ek yöntemler ve özellikler, kullanıcıların hat bilgilerini toplamasına izin veren tanımlanmıştır.

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

Aşağıdaki örnek bir XML belgesindeki öğelerin sayısını sayar:

```vb
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

Book. xml

```xml
<!--sample XML fragment-->
<book genre='novel' ISBN='1-861001-57-5' misc='sale-item'>
  <title>The Handmaid's Tale</title>
  <price>14.95</price>
</book>
```

#### <a name="output"></a>Çıktı

```console
Number of elements in book.xml: 3
```

## <a name="node-event-handler"></a>Düğüm olay Işleyicisi

DOM 'ın .NET Framework uygulanması, bir XML belgesindeki düğümler değiştiğinde olayları almanıza ve işleyebilmenizi sağlayan bir olay sistemi de içerir. <xref:System.Xml.XmlNodeChangedEventHandler> Ve <xref:System.Xml.XmlNodeChangedEventArgs> sınıflarını kullanarak,,,,, `NodeChanged`ve `NodeChanging` `NodeRemoved` `NodeRemoving` olaylarını `NodeInserted`yakalayabilirsiniz `NodeInserting`.

Olay işleme işlemi, özgün DOM sınıflarında olduğu gibi, türetilen sınıflarda tam olarak aynı şekilde işler.

Düğüm olay işleme hakkında daha fazla bilgi için bkz [Events](../../../../docs/standard/events/index.md) . olaylar <xref:System.Xml.XmlNodeChangedEventHandler>ve.

## <a name="default-attributes-and-the-createelement-method"></a>Default öznitelikleri ve CreateElement yöntemi

Türetilmiş bir sınıftaki <xref:System.Xml.XmlDocument.CreateElement%2A> yöntemi geçersiz kılıyorsa, belgeyi düzenlenirken yeni öğeler oluştururken varsayılan öznitelikler eklenmez. Bu yalnızca düzenlenirken bir sorundur. Yöntemi ' a varsayılan öznitelikler eklemekten sorumlu olduğundan, bu işlevselliği <xref:System.Xml.XmlDocument.CreateElement%2A> yönteminde kodmalısınız. <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument.CreateElement%2A> Varsayılan öznitelikleri içeren bir <xref:System.Xml.XmlDocument> yüklüyorsanız, bunlar doğru şekilde işlenir. Varsayılan öznitelikler hakkında daha fazla bilgi için bkz. [Dom 'Daki öğeler Için yeni öznitelikler oluşturma](creating-new-attributes-for-elements-in-the-dom.md).

## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)
