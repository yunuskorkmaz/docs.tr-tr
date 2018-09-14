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
ms.openlocfilehash: 70e13893cf350a193411f1833e2e3b21c9b64182
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45515723"
---
# <a name="extending-the-dom"></a><span data-ttu-id="553d3-102">DOM genişletme</span><span class="sxs-lookup"><span data-stu-id="553d3-102">Extending the DOM</span></span>

<span data-ttu-id="553d3-103">Microsoft .NET Framework XML belge nesne modeli (DOM) uygulaması sağlayan bir temel sınıf kümesi içerir.</span><span class="sxs-lookup"><span data-stu-id="553d3-103">The Microsoft .NET Framework includes a base set of classes that provides an implementation of the XML Document Object Model (DOM).</span></span> <span data-ttu-id="553d3-104"><xref:System.Xml.XmlNode>Ve onun türetilmiş sınıfları, yöntemleri ve gidin olanak tanıyan özellikler sorgulamak ve içeriği ve yapısı bir XML belgesi değiştirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="553d3-104">The <xref:System.Xml.XmlNode>, and its derived classes, provides methods and properties that allow you to navigate, query, and modify the content and structure of an XML document.</span></span>

<span data-ttu-id="553d3-105">XML içeriği kullanılarak DOM'a belleğe yüklendiğinde oluşturulan düğümleri düğüm adı, düğüm türü vb. gibi bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="553d3-105">When XML content is loaded into memory using the DOM, the nodes created contain information such as node name, node type, and so on.</span></span> <span data-ttu-id="553d3-106">Temel sınıflar sağlamadığı belirli düğüm bilgileri gerektiren burada durumlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="553d3-106">There may be occasions where you require specific node information that the base classes do not provide.</span></span> <span data-ttu-id="553d3-107">Örneğin, satır numarasını ve düğümün konumu görmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="553d3-107">For example, you may want to see the line number and position of the node.</span></span> <span data-ttu-id="553d3-108">Bu durumda, yeni sınıflar mevcut DOM sınıflarından ve ek işlevler ekleyin.</span><span class="sxs-lookup"><span data-stu-id="553d3-108">In this case, you can derive new classes from the existing DOM classes and add additional functionality.</span></span>

<span data-ttu-id="553d3-109">Yeni sınıflar türetilirken iki genel kurallar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="553d3-109">There are two general guidelines when deriving new classes:</span></span>

- <span data-ttu-id="553d3-110">Hiçbir zaman türetilir, önerilen <xref:System.Xml.XmlNode> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="553d3-110">It is recommended that you never derive from the <xref:System.Xml.XmlNode> class.</span></span> <span data-ttu-id="553d3-111">Bunun yerine, ilgilendiğiniz düğüm türü için karşılık gelen sınıf sınıfların türetilmesi önerilir.</span><span class="sxs-lookup"><span data-stu-id="553d3-111">Instead, it is recommended that you derive classes from the class corresponding to the node type that you are interested in.</span></span> <span data-ttu-id="553d3-112">Öznitelik düğümleri hakkında ek bilgi döndürmek isterseniz, örneğin, türetebilirsiniz <xref:System.Xml.XmlAttribute> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="553d3-112">For example, if you want to return additional information on attribute nodes, you can derive from the <xref:System.Xml.XmlAttribute> class.</span></span>

- <span data-ttu-id="553d3-113">Düğüm oluşturma yöntemleri dışında bir işlevi geçersiz kılarken, her zaman temel sürümü, işlev çağrısı ve ardından herhangi bir ek işleme ekleyin önerilir.</span><span class="sxs-lookup"><span data-stu-id="553d3-113">Except for the node creation methods, it is recommended that when overriding a function, you should always call the base version of the function and then add any additional processing.</span></span>

## <a name="creating-your-own-node-instances"></a><span data-ttu-id="553d3-114">Kendi düğüm örnekleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="553d3-114">Creating Your Own Node Instances</span></span>

<span data-ttu-id="553d3-115"><xref:System.Xml.XmlDocument> Sınıf düğümü oluşturma yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="553d3-115">The <xref:System.Xml.XmlDocument> class contains node creation methods.</span></span> <span data-ttu-id="553d3-116">Bir XML dosyası yüklendiğinde düğümleri oluşturmak için bu yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="553d3-116">When an XML file is loaded, these methods are called to create the nodes.</span></span> <span data-ttu-id="553d3-117">Bir belge yüklendiğinde düğüm örneklerinizin oluşturulmasını sağlayacak şekilde bu yöntemleri geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="553d3-117">You can override these methods so that your node instances are created when a document is loaded.</span></span> <span data-ttu-id="553d3-118">Genişlettiyseniz, örneğin, <xref:System.Xml.XmlElement> devralan sınıf <xref:System.Xml.XmlDocument> sınıf ve geçersiz kılma <xref:System.Xml.XmlDocument.CreateElement%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="553d3-118">For example, if you have extended the <xref:System.Xml.XmlElement> class, you would inherit the <xref:System.Xml.XmlDocument> class and override the <xref:System.Xml.XmlDocument.CreateElement%2A> method.</span></span>

<span data-ttu-id="553d3-119">Aşağıdaki örnek nasıl geçersiz kılınacağını gösterir <xref:System.Xml.XmlDocument.CreateElement%2A> uygulamanıza döndürülecek yöntemi <xref:System.Xml.XmlElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="553d3-119">The following example shows how to override the <xref:System.Xml.XmlDocument.CreateElement%2A> method to return your implementation of the <xref:System.Xml.XmlElement> class.</span></span>

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

## <a name="extending-a-class"></a><span data-ttu-id="553d3-120">Bir sınıf genişletme</span><span class="sxs-lookup"><span data-stu-id="553d3-120">Extending a Class</span></span>

<span data-ttu-id="553d3-121">Bir sınıf genişletmek için var olan DOM sınıflarının birinden sınıfınıza türetilir.</span><span class="sxs-lookup"><span data-stu-id="553d3-121">To extend a class, derive your class from one of the existing DOM classes.</span></span> <span data-ttu-id="553d3-122">Ardından, herhangi bir sanal yöntem ya da temel sınıfta özellikleri geçersiz kılabilir veya kendi uygulamanızı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="553d3-122">You can then override any of the virtual methods or properties in the base class, or add your own.</span></span>

<span data-ttu-id="553d3-123">Aşağıdaki örnekte, yeni bir sınıf oluşturulduğunda uygulayan <xref:System.Xml.XmlElement> sınıfı ve <xref:System.Xml.IXmlLineInfo> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="553d3-123">In the following example, a new class is created, which implements the <xref:System.Xml.XmlElement> class and the <xref:System.Xml.IXmlLineInfo> interface.</span></span> <span data-ttu-id="553d3-124">Ek yöntemleri ve özellikleri satır bilgileri toplamak kullanıcıların sağlayan tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="553d3-124">Additional methods and properties are defined which allows users to gather line information.</span></span>

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

### <a name="example"></a><span data-ttu-id="553d3-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="553d3-125">Example</span></span>

<span data-ttu-id="553d3-126">Aşağıdaki örnek, bir XML belgesi içindeki öğelerin sayısını sayar:</span><span class="sxs-lookup"><span data-stu-id="553d3-126">The following example counts the number of elements in an XML document:</span></span>

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

#### <a name="input"></a><span data-ttu-id="553d3-127">Giriş</span><span class="sxs-lookup"><span data-stu-id="553d3-127">Input</span></span>

<span data-ttu-id="553d3-128">Book.XML</span><span class="sxs-lookup"><span data-stu-id="553d3-128">book.xml</span></span>

```xml
<!--sample XML fragment-->
<book genre='novel' ISBN='1-861001-57-5' misc='sale-item'>
  <title>The Handmaid's Tale</title>
  <price>14.95</price>
</book>
```

#### <a name="output"></a><span data-ttu-id="553d3-129">Çıkış</span><span class="sxs-lookup"><span data-stu-id="553d3-129">Output</span></span>

```console
Number of elements in book.xml: 3
```

## <a name="node-event-handler"></a><span data-ttu-id="553d3-130">Düğüm olay işleyicisi</span><span class="sxs-lookup"><span data-stu-id="553d3-130">Node Event Handler</span></span>

<span data-ttu-id="553d3-131">DOM .NET Framework uygulamasını ayrıca Al ve düğümleri bir XML belgesi değiştirdiğinizde olayları işlemek için sağlayan bir olay sistemi içerir.</span><span class="sxs-lookup"><span data-stu-id="553d3-131">The .NET Framework implementation of the DOM also includes an event system that enables you to receive and handle events when nodes in an XML document change.</span></span> <span data-ttu-id="553d3-132">Kullanarak <xref:System.Xml.XmlNodeChangedEventHandler> ve <xref:System.Xml.XmlNodeChangedEventArgs> sınıfları yakalayabilirsiniz `NodeChanged`, `NodeChanging`, `NodeInserted`, `NodeInserting`, `NodeRemoved`, ve `NodeRemoving` olayları.</span><span class="sxs-lookup"><span data-stu-id="553d3-132">Using the <xref:System.Xml.XmlNodeChangedEventHandler> and <xref:System.Xml.XmlNodeChangedEventArgs> classes, you can capture `NodeChanged`, `NodeChanging`, `NodeInserted`, `NodeInserting`, `NodeRemoved`, and `NodeRemoving` events.</span></span>

<span data-ttu-id="553d3-133">Özgün DOM sınıflarda gibi olay işleme işlemi tam olarak aynı türetilmiş sınıflarda çalışır.</span><span class="sxs-lookup"><span data-stu-id="553d3-133">The event-handling process works exactly the same in derived classes as it would in the original DOM classes.</span></span>

<span data-ttu-id="553d3-134">Düğüm olay işleme hakkında daha fazla bilgi için bkz. [olayları](../../../../docs/standard/events/index.md) ve <xref:System.Xml.XmlNodeChangedEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="553d3-134">For more information regarding node event handling, see [Events](../../../../docs/standard/events/index.md) and <xref:System.Xml.XmlNodeChangedEventHandler>.</span></span>

## <a name="default-attributes-and-the-createelement-method"></a><span data-ttu-id="553d3-135">Varsayılan öznitelikler ve CreateElement yöntemi</span><span class="sxs-lookup"><span data-stu-id="553d3-135">Default Attributes and the CreateElement Method</span></span>

<span data-ttu-id="553d3-136">Kılıyorsa <xref:System.Xml.XmlDocument.CreateElement%2A> varsayılan belgesi düzenlenirken yeni öğeler oluştururken, öznitelikleri eklenip eklenmeyeceği türetilen bir sınıfta yöntemi.</span><span class="sxs-lookup"><span data-stu-id="553d3-136">If you are overriding the <xref:System.Xml.XmlDocument.CreateElement%2A> method in a derived class, default attributes are not added when you are creating new elements while editing the document.</span></span> <span data-ttu-id="553d3-137">Düzenlenirken bir sorun budur.</span><span class="sxs-lookup"><span data-stu-id="553d3-137">This is only an issue while editing.</span></span> <span data-ttu-id="553d3-138">Çünkü <xref:System.Xml.XmlDocument.CreateElement%2A> yöntemdir varsayılan öznitelikler eklemek için sorumlu bir <xref:System.Xml.XmlDocument>, bu işlev kodu gerekir <xref:System.Xml.XmlDocument.CreateElement%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="553d3-138">Because the <xref:System.Xml.XmlDocument.CreateElement%2A> method is responsible for adding default attributes to an <xref:System.Xml.XmlDocument>, you must code this functionality in the <xref:System.Xml.XmlDocument.CreateElement%2A> method.</span></span> <span data-ttu-id="553d3-139">Yüklüyorsanız, size bir <xref:System.Xml.XmlDocument> , düzgün işlenecek, varsayılan öznitelikler içerir.</span><span class="sxs-lookup"><span data-stu-id="553d3-139">If you are loading an <xref:System.Xml.XmlDocument> that includes default attributes, they will be handled correctly.</span></span> <span data-ttu-id="553d3-140">Varsayılan öznitelikler hakkında daha fazla bilgi için bkz. [DOM öğeleri için yeni öznitelikler oluşturma](creating-new-attributes-for-elements-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="553d3-140">For more information on default attributes, see [Creating New Attributes for Elements in the DOM](creating-new-attributes-for-elements-in-the-dom.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="553d3-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="553d3-141">See also</span></span>

- [<span data-ttu-id="553d3-142">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="553d3-142">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)  
