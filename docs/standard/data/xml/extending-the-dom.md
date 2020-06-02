---
title: DOM Genişletme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: b5489c96-4afd-439a-a25d-fc82eb4a148d
ms.openlocfilehash: 4a1a7af0e841601542a30c7bd3f71395faa6cb57
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287798"
---
# <a name="extending-the-dom"></a>DOM Genişletme

Microsoft .NET Framework, XML Belge Nesne Modeli (DOM) uygulamasını sağlayan bir temel sınıf kümesi içerir. <xref:System.Xml.XmlNode>Ve türetilmiş sınıfları, BIR XML belgesinin içeriğini ve yapısını gezinmenize, sorgulamanızı ve değiştirebilmeniz için yöntemler ve özellikler sağlar.

XML içeriği DOM kullanılarak belleğe yüklendiğinde oluşturulan düğümler düğüm adı, düğüm türü vb. gibi bilgiler içerir. Temel sınıfların sağlamadığı belirli düğüm bilgilerinin gerekli olduğu durumlar olabilir. Örneğin, düğümün satır numarasını ve konumunu görmek isteyebilirsiniz. Bu durumda, var olan DOM sınıflarından yeni sınıflar türetebilir ve ek işlevler ekleyebilirsiniz.

Yeni sınıflar türetmede iki genel kılavuz vardır:

- Sınıfından hiçbir şekilde türetmeniz önerilir <xref:System.Xml.XmlNode> . Bunun yerine, ilgilendiğiniz düğüm türüne karşılık gelen sınıftan sınıfları türetmeniz önerilir. Örneğin, öznitelik düğümleri hakkında ek bilgi döndürmek istiyorsanız sınıfından türetebilirsiniz <xref:System.Xml.XmlAttribute> .

- Düğüm oluşturma yöntemleri hariç, bir işlevi geçersiz kıldığınızda, işlevin temel sürümünü her zaman çağırmanız ve sonra ek işlem eklemeniz önerilir.

## <a name="creating-your-own-node-instances"></a>Kendi düğüm örneklerinizi oluşturma

<xref:System.Xml.XmlDocument>Sınıfı, düğüm oluşturma yöntemlerini içerir. Bir XML dosyası yüklendiğinde, düğümleri oluşturmak için bu yöntemler çağırılır. Bir belge yüklendiğinde düğüm örneklerinizin oluşturulması için bu yöntemleri geçersiz kılabilirsiniz. Örneğin, sınıfı genişlettiyseniz <xref:System.Xml.XmlElement> , sınıfını miras alıp <xref:System.Xml.XmlDocument> yöntemi geçersiz kılabilirsiniz <xref:System.Xml.XmlDocument.CreateElement%2A> .

Aşağıdaki örnek, <xref:System.Xml.XmlDocument.CreateElement%2A> sınıfının uygulamanızı döndürmek için yönteminin nasıl geçersiz kılınacağını göstermektedir <xref:System.Xml.XmlElement> .

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

Aşağıdaki örnekte, sınıfını ve arabirimini uygulayan yeni bir sınıf oluşturulur <xref:System.Xml.XmlElement> <xref:System.Xml.IXmlLineInfo> . Ek yöntemler ve özellikler, kullanıcıların hat bilgilerini toplamasına izin veren tanımlanmıştır.

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

DOM 'ın .NET Framework uygulanması, bir XML belgesindeki düğümler değiştiğinde olayları almanıza ve işleyebilmenizi sağlayan bir olay sistemi de içerir. Ve sınıflarını kullanarak,,,,, <xref:System.Xml.XmlNodeChangedEventHandler> <xref:System.Xml.XmlNodeChangedEventArgs> `NodeChanged` `NodeChanging` `NodeInserted` `NodeInserting` `NodeRemoved` ve `NodeRemoving` olaylarını yakalayabilirsiniz.

Olay işleme işlemi, özgün DOM sınıflarında olduğu gibi, türetilen sınıflarda tam olarak aynı şekilde işler.

Düğüm olay işleme hakkında daha fazla bilgi için bkz. [Olaylar](../../events/index.md) ve <xref:System.Xml.XmlNodeChangedEventHandler> .

## <a name="default-attributes-and-the-createelement-method"></a>Default öznitelikleri ve CreateElement yöntemi

<xref:System.Xml.XmlDocument.CreateElement%2A>Türetilmiş bir sınıftaki yöntemi geçersiz kılıyorsa, belgeyi düzenlenirken yeni öğeler oluştururken varsayılan öznitelikler eklenmez. Bu yalnızca düzenlenirken bir sorundur. <xref:System.Xml.XmlDocument.CreateElement%2A>Yöntemi ' a varsayılan öznitelikler eklemekten sorumlu olduğundan <xref:System.Xml.XmlDocument> , bu işlevselliği yönteminde kodmalısınız <xref:System.Xml.XmlDocument.CreateElement%2A> . <xref:System.Xml.XmlDocument>Varsayılan öznitelikleri içeren bir yüklüyorsanız, bunlar doğru şekilde işlenir. Varsayılan öznitelikler hakkında daha fazla bilgi için bkz. [Dom 'Daki öğeler Için yeni öznitelikler oluşturma](creating-new-attributes-for-elements-in-the-dom.md).

## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)
