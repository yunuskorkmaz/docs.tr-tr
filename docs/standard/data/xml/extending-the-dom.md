---
title: DOM Genişletme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: b5489c96-4afd-439a-a25d-fc82eb4a148d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3224250b08a780b87b9b7f96547830b0563daadf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351947"
---
# <a name="extending-the-dom"></a><span data-ttu-id="4bc7a-102">DOM Genişletme</span><span class="sxs-lookup"><span data-stu-id="4bc7a-102">Extending the DOM</span></span>

<span data-ttu-id="4bc7a-103">Microsoft .NET Framework, XML Belge Nesne Modeli (DOM) uygulamasını sağlayan bir temel sınıf kümesi içerir.</span><span class="sxs-lookup"><span data-stu-id="4bc7a-103">The Microsoft .NET Framework includes a base set of classes that provides an implementation of the XML Document Object Model (DOM).</span></span> <span data-ttu-id="4bc7a-104"><xref:System.Xml.XmlNode>ve türetilmiş sınıfları, bir XML belgesinin içeriğini ve yapısını gezinmenize, sorgulamanızı ve değiştirmenize olanak tanıyan yöntemler ve özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4bc7a-104">The <xref:System.Xml.XmlNode>, and its derived classes, provides methods and properties that allow you to navigate, query, and modify the content and structure of an XML document.</span></span>

<span data-ttu-id="4bc7a-105">XML içeriği DOM kullanılarak belleğe yüklendiğinde oluşturulan düğümler düğüm adı, düğüm türü vb. gibi bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="4bc7a-105">When XML content is loaded into memory using the DOM, the nodes created contain information such as node name, node type, and so on.</span></span> <span data-ttu-id="4bc7a-106">Temel sınıfların sağlamadığı belirli düğüm bilgilerinin gerekli olduğu durumlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="4bc7a-106">There may be occasions where you require specific node information that the base classes do not provide.</span></span> <span data-ttu-id="4bc7a-107">Örneğin, düğümün satır numarasını ve konumunu görmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4bc7a-107">For example, you may want to see the line number and position of the node.</span></span> <span data-ttu-id="4bc7a-108">Bu durumda, var olan DOM sınıflarından yeni sınıflar türetebilir ve ek işlevler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4bc7a-108">In this case, you can derive new classes from the existing DOM classes and add additional functionality.</span></span>

<span data-ttu-id="4bc7a-109">Yeni sınıflar türetmede iki genel kılavuz vardır:</span><span class="sxs-lookup"><span data-stu-id="4bc7a-109">There are two general guidelines when deriving new classes:</span></span>

- <span data-ttu-id="4bc7a-110"><xref:System.Xml.XmlNode> sınıfından hiçbir şekilde türetmeniz önerilir.</span><span class="sxs-lookup"><span data-stu-id="4bc7a-110">It is recommended that you never derive from the <xref:System.Xml.XmlNode> class.</span></span> <span data-ttu-id="4bc7a-111">Bunun yerine, ilgilendiğiniz düğüm türüne karşılık gelen sınıftan sınıfları türetmeniz önerilir.</span><span class="sxs-lookup"><span data-stu-id="4bc7a-111">Instead, it is recommended that you derive classes from the class corresponding to the node type that you are interested in.</span></span> <span data-ttu-id="4bc7a-112">Örneğin, öznitelik düğümleri hakkında ek bilgi döndürmek istiyorsanız <xref:System.Xml.XmlAttribute> sınıfından türetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4bc7a-112">For example, if you want to return additional information on attribute nodes, you can derive from the <xref:System.Xml.XmlAttribute> class.</span></span>

- <span data-ttu-id="4bc7a-113">Düğüm oluşturma yöntemleri hariç, bir işlevi geçersiz kıldığınızda, işlevin temel sürümünü her zaman çağırmanız ve sonra ek işlem eklemeniz önerilir.</span><span class="sxs-lookup"><span data-stu-id="4bc7a-113">Except for the node creation methods, it is recommended that when overriding a function, you should always call the base version of the function and then add any additional processing.</span></span>

## <a name="creating-your-own-node-instances"></a><span data-ttu-id="4bc7a-114">Kendi düğüm örneklerinizi oluşturma</span><span class="sxs-lookup"><span data-stu-id="4bc7a-114">Creating Your Own Node Instances</span></span>

<span data-ttu-id="4bc7a-115"><xref:System.Xml.XmlDocument> sınıfı, düğüm oluşturma yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="4bc7a-115">The <xref:System.Xml.XmlDocument> class contains node creation methods.</span></span> <span data-ttu-id="4bc7a-116">Bir XML dosyası yüklendiğinde, düğümleri oluşturmak için bu yöntemler çağırılır.</span><span class="sxs-lookup"><span data-stu-id="4bc7a-116">When an XML file is loaded, these methods are called to create the nodes.</span></span> <span data-ttu-id="4bc7a-117">Bir belge yüklendiğinde düğüm örneklerinizin oluşturulması için bu yöntemleri geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4bc7a-117">You can override these methods so that your node instances are created when a document is loaded.</span></span> <span data-ttu-id="4bc7a-118">Örneğin, <xref:System.Xml.XmlElement> sınıfını genişlettiyseniz, <xref:System.Xml.XmlDocument> sınıfını devralacak ve <xref:System.Xml.XmlDocument.CreateElement%2A> yöntemini geçersiz kılarsınız.</span><span class="sxs-lookup"><span data-stu-id="4bc7a-118">For example, if you have extended the <xref:System.Xml.XmlElement> class, you would inherit the <xref:System.Xml.XmlDocument> class and override the <xref:System.Xml.XmlDocument.CreateElement%2A> method.</span></span>

<span data-ttu-id="4bc7a-119">Aşağıdaki örnek, <xref:System.Xml.XmlElement> sınıfının uygulamanızı döndürmek için <xref:System.Xml.XmlDocument.CreateElement%2A> yönteminin nasıl geçersiz kılınacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="4bc7a-119">The following example shows how to override the <xref:System.Xml.XmlDocument.CreateElement%2A> method to return your implementation of the <xref:System.Xml.XmlElement> class.</span></span>

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

## <a name="extending-a-class"></a><span data-ttu-id="4bc7a-120">Sınıf genişletme</span><span class="sxs-lookup"><span data-stu-id="4bc7a-120">Extending a Class</span></span>

<span data-ttu-id="4bc7a-121">Bir sınıfı genişletmek için, varolan DOM sınıflarından birindeki sınıfınızı türetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4bc7a-121">To extend a class, derive your class from one of the existing DOM classes.</span></span> <span data-ttu-id="4bc7a-122">Daha sonra, temel sınıftaki sanal yöntemlerin veya özelliklerden birini geçersiz kılabilir ya da kendinizinkini ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4bc7a-122">You can then override any of the virtual methods or properties in the base class, or add your own.</span></span>

<span data-ttu-id="4bc7a-123">Aşağıdaki örnekte, <xref:System.Xml.XmlElement> sınıfını ve <xref:System.Xml.IXmlLineInfo> arabirimini uygulayan yeni bir sınıf oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4bc7a-123">In the following example, a new class is created, which implements the <xref:System.Xml.XmlElement> class and the <xref:System.Xml.IXmlLineInfo> interface.</span></span> <span data-ttu-id="4bc7a-124">Ek yöntemler ve özellikler, kullanıcıların hat bilgilerini toplamasına izin veren tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4bc7a-124">Additional methods and properties are defined which allows users to gather line information.</span></span>

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

### <a name="example"></a><span data-ttu-id="4bc7a-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="4bc7a-125">Example</span></span>

<span data-ttu-id="4bc7a-126">Aşağıdaki örnek bir XML belgesindeki öğelerin sayısını sayar:</span><span class="sxs-lookup"><span data-stu-id="4bc7a-126">The following example counts the number of elements in an XML document:</span></span>

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

#### <a name="input"></a><span data-ttu-id="4bc7a-127">Giriş</span><span class="sxs-lookup"><span data-stu-id="4bc7a-127">Input</span></span>

<span data-ttu-id="4bc7a-128">Book. xml</span><span class="sxs-lookup"><span data-stu-id="4bc7a-128">book.xml</span></span>

```xml
<!--sample XML fragment-->
<book genre='novel' ISBN='1-861001-57-5' misc='sale-item'>
  <title>The Handmaid's Tale</title>
  <price>14.95</price>
</book>
```

#### <a name="output"></a><span data-ttu-id="4bc7a-129">Çıktı</span><span class="sxs-lookup"><span data-stu-id="4bc7a-129">Output</span></span>

```console
Number of elements in book.xml: 3
```

## <a name="node-event-handler"></a><span data-ttu-id="4bc7a-130">Düğüm olay Işleyicisi</span><span class="sxs-lookup"><span data-stu-id="4bc7a-130">Node Event Handler</span></span>

<span data-ttu-id="4bc7a-131">DOM 'ın .NET Framework uygulanması, bir XML belgesindeki düğümler değiştiğinde olayları almanıza ve işleyebilmenizi sağlayan bir olay sistemi de içerir.</span><span class="sxs-lookup"><span data-stu-id="4bc7a-131">The .NET Framework implementation of the DOM also includes an event system that enables you to receive and handle events when nodes in an XML document change.</span></span> <span data-ttu-id="4bc7a-132"><xref:System.Xml.XmlNodeChangedEventHandler> ve <xref:System.Xml.XmlNodeChangedEventArgs> sınıfları kullanarak `NodeChanged`, `NodeChanging`, `NodeInserted`, `NodeInserting`, `NodeRemoved`ve `NodeRemoving` olaylarını yakalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4bc7a-132">Using the <xref:System.Xml.XmlNodeChangedEventHandler> and <xref:System.Xml.XmlNodeChangedEventArgs> classes, you can capture `NodeChanged`, `NodeChanging`, `NodeInserted`, `NodeInserting`, `NodeRemoved`, and `NodeRemoving` events.</span></span>

<span data-ttu-id="4bc7a-133">Olay işleme işlemi, özgün DOM sınıflarında olduğu gibi, türetilen sınıflarda tam olarak aynı şekilde işler.</span><span class="sxs-lookup"><span data-stu-id="4bc7a-133">The event-handling process works exactly the same in derived classes as it would in the original DOM classes.</span></span>

<span data-ttu-id="4bc7a-134">Düğüm olay işleme hakkında daha fazla bilgi için bkz. [Olaylar](../../../../docs/standard/events/index.md) ve <xref:System.Xml.XmlNodeChangedEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="4bc7a-134">For more information regarding node event handling, see [Events](../../../../docs/standard/events/index.md) and <xref:System.Xml.XmlNodeChangedEventHandler>.</span></span>

## <a name="default-attributes-and-the-createelement-method"></a><span data-ttu-id="4bc7a-135">Default öznitelikleri ve CreateElement yöntemi</span><span class="sxs-lookup"><span data-stu-id="4bc7a-135">Default Attributes and the CreateElement Method</span></span>

<span data-ttu-id="4bc7a-136">Türetilmiş bir sınıfta <xref:System.Xml.XmlDocument.CreateElement%2A> yöntemini geçersiz kılıyorsa, belgeyi düzenlenirken yeni öğeler oluştururken varsayılan öznitelikler eklenmez.</span><span class="sxs-lookup"><span data-stu-id="4bc7a-136">If you are overriding the <xref:System.Xml.XmlDocument.CreateElement%2A> method in a derived class, default attributes are not added when you are creating new elements while editing the document.</span></span> <span data-ttu-id="4bc7a-137">Bu yalnızca düzenlenirken bir sorundur.</span><span class="sxs-lookup"><span data-stu-id="4bc7a-137">This is only an issue while editing.</span></span> <span data-ttu-id="4bc7a-138"><xref:System.Xml.XmlDocument.CreateElement%2A> yöntemi bir <xref:System.Xml.XmlDocument>varsayılan öznitelikleri eklemekten sorumlu olduğundan, bu işlevi <xref:System.Xml.XmlDocument.CreateElement%2A> yönteminde kodmalısınız.</span><span class="sxs-lookup"><span data-stu-id="4bc7a-138">Because the <xref:System.Xml.XmlDocument.CreateElement%2A> method is responsible for adding default attributes to an <xref:System.Xml.XmlDocument>, you must code this functionality in the <xref:System.Xml.XmlDocument.CreateElement%2A> method.</span></span> <span data-ttu-id="4bc7a-139">Varsayılan öznitelikleri içeren bir <xref:System.Xml.XmlDocument> yüklüyorsanız, bunlar doğru şekilde işlenir.</span><span class="sxs-lookup"><span data-stu-id="4bc7a-139">If you are loading an <xref:System.Xml.XmlDocument> that includes default attributes, they will be handled correctly.</span></span> <span data-ttu-id="4bc7a-140">Varsayılan öznitelikler hakkında daha fazla bilgi için bkz. [Dom 'Daki öğeler Için yeni öznitelikler oluşturma](creating-new-attributes-for-elements-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="4bc7a-140">For more information on default attributes, see [Creating New Attributes for Elements in the DOM](creating-new-attributes-for-elements-in-the-dom.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4bc7a-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4bc7a-141">See also</span></span>

- [<span data-ttu-id="4bc7a-142">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="4bc7a-142">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
