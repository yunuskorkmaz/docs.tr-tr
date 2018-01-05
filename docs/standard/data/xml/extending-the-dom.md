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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 06cac8d76b17f3ef32931ea21d0556085f05d7b1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="extending-the-dom"></a><span data-ttu-id="98ec5-102">DOM genişletme</span><span class="sxs-lookup"><span data-stu-id="98ec5-102">Extending the DOM</span></span>
<span data-ttu-id="98ec5-103">Microsoft .NET Framework uygulaması XML belge nesne modeli (DOM) sağlayan bir temel sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="98ec5-103">The Microsoft .NET Framework includes a base set of classes that provides an implementation of the XML Document Object Model (DOM).</span></span> <span data-ttu-id="98ec5-104"><xref:System.Xml.XmlNode>Ve kendi türetilmiş sınıfları, yöntemleri ve gidin olanak tanıyan özellikler sorgulamak ve içeriği ve bir XML belgesi yapısını değiştirmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="98ec5-104">The <xref:System.Xml.XmlNode>, and its derived classes, provides methods and properties that allow you to navigate, query, and modify the content and structure of an XML document.</span></span>  
  
 <span data-ttu-id="98ec5-105">XML içeriği DOM kullanarak belleğe yüklendiğinde oluşturulan düğümler düğüm adı, düğüm türü vb. gibi bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="98ec5-105">When XML content is loaded into memory using the DOM, the nodes created contain information such as node name, node type, and so on.</span></span> <span data-ttu-id="98ec5-106">Temel sınıflar sağlıyor mu belirli düğüm bilgi gerektiren burada durumlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="98ec5-106">There may be occasions where you require specific node information that the base classes do not provide.</span></span> <span data-ttu-id="98ec5-107">Örneğin, satır numarası ve düğüm konumunu görmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98ec5-107">For example, you may want to see the line number and position of the node.</span></span> <span data-ttu-id="98ec5-108">Bu durumda, yeni sınıflar mevcut DOM sınıflarından ve ek işlevsellik ekleyin.</span><span class="sxs-lookup"><span data-stu-id="98ec5-108">In this case, you can derive new classes from the existing DOM classes and add additional functionality.</span></span>  
  
 <span data-ttu-id="98ec5-109">Yeni sınıflar türetilirken iki genel kurallar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="98ec5-109">There are two general guidelines when deriving new classes:</span></span>  
  
-   <span data-ttu-id="98ec5-110">Hiçbir zaman öğesinden türetilen olduğunu önerilir <xref:System.Xml.XmlNode> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="98ec5-110">It is recommended that you never derive from the <xref:System.Xml.XmlNode> class.</span></span> <span data-ttu-id="98ec5-111">Bunun yerine, ilgilendiğiniz düğüm türü için karşılık gelen sınıf sınıf türetin önerilir.</span><span class="sxs-lookup"><span data-stu-id="98ec5-111">Instead, it is recommended that you derive classes from the class corresponding to the node type that you are interested in.</span></span> <span data-ttu-id="98ec5-112">Özniteliği düğümlerinde ek döndürmesini istiyorsanız, örneğin, gelen türetilemeyeceğini <xref:System.Xml.XmlAttribute> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="98ec5-112">For example, if you want to return additional information on attribute nodes, you can derive from the <xref:System.Xml.XmlAttribute> class.</span></span>  
  
-   <span data-ttu-id="98ec5-113">Düğüm oluşturma yöntemleri dışında bir işlevi geçersiz kılarken, her zaman işlevi temel sürümünü çağırın ve herhangi bir ek işlem eklemek, önerilir.</span><span class="sxs-lookup"><span data-stu-id="98ec5-113">Except for the node creation methods, it is recommended that when overriding a function, you should always call the base version of the function and then add any additional processing.</span></span>  
  
## <a name="creating-your-own-node-instances"></a><span data-ttu-id="98ec5-114">Kendi düğüm örnekleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="98ec5-114">Creating Your Own Node Instances</span></span>  
 <span data-ttu-id="98ec5-115"><xref:System.Xml.XmlDocument> Sınıfı düğüm oluşturma yöntemlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="98ec5-115">The <xref:System.Xml.XmlDocument> class contains node creation methods.</span></span> <span data-ttu-id="98ec5-116">Bir XML dosyası yüklendiğinde, bu yöntemleri düğümleri oluşturmak için denir.</span><span class="sxs-lookup"><span data-stu-id="98ec5-116">When an XML file is loaded, these methods are called to create the nodes.</span></span> <span data-ttu-id="98ec5-117">Böylece bir belge yüklendiğinde düğümü örneklerinizi oluşturulan bu yöntemleri geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98ec5-117">You can override these methods so that your node instances are created when a document is loaded.</span></span> <span data-ttu-id="98ec5-118">Örneğin, genişlettiyseniz <xref:System.Xml.XmlElement> devral sınıfı, <xref:System.Xml.XmlDocument> sınıfı ve geçersiz kılma <xref:System.Xml.XmlDocument.CreateElement%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="98ec5-118">For example, if you have extended the <xref:System.Xml.XmlElement> class, you would inherit the <xref:System.Xml.XmlDocument> class and override the <xref:System.Xml.XmlDocument.CreateElement%2A> method.</span></span>  
  
 <span data-ttu-id="98ec5-119">Aşağıdaki örnekte nasıl geçersiz kılınacağını gösterir <xref:System.Xml.XmlDocument.CreateElement%2A> uygulamanıza döndürülecek yöntemi <xref:System.Xml.XmlElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="98ec5-119">The following example shows how to override the <xref:System.Xml.XmlDocument.CreateElement%2A> method to return your implementation of the <xref:System.Xml.XmlElement> class.</span></span>  
  
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
  
## <a name="extending-a-class"></a><span data-ttu-id="98ec5-120">Bir sınıf genişletme</span><span class="sxs-lookup"><span data-stu-id="98ec5-120">Extending a Class</span></span>  
 <span data-ttu-id="98ec5-121">Bir sınıf genişletmek için varolan DOM sınıflarının birinden, sınıf türetin.</span><span class="sxs-lookup"><span data-stu-id="98ec5-121">To extend a class, derive your class from one of the existing DOM classes.</span></span> <span data-ttu-id="98ec5-122">Sanal yöntemler veya temel sınıf özelliklerini geçersiz kılabilir veya kendi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="98ec5-122">You can then override any of the virtual methods or properties in the base class, or add your own.</span></span>  
  
 <span data-ttu-id="98ec5-123">Aşağıdaki örnekte, yeni bir sınıf oluşturulur, hangi uygulayan <xref:System.Xml.XmlElement> sınıfı ve <xref:System.Xml.IXmlLineInfo> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="98ec5-123">In the following example, a new class is created, which implements the <xref:System.Xml.XmlElement> class and the <xref:System.Xml.IXmlLineInfo> interface.</span></span> <span data-ttu-id="98ec5-124">Satırı bilgileri toplamak kullanıcıların sağlayan ek yöntemleri ve özellikleri tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="98ec5-124">Additional methods and properties are defined which allows users to gather line information.</span></span>  
  
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
  
### <a name="example"></a><span data-ttu-id="98ec5-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="98ec5-125">Example</span></span>  
 <span data-ttu-id="98ec5-126">Aşağıdaki örnek bir XML belgesi öğelerinde sayar.</span><span class="sxs-lookup"><span data-stu-id="98ec5-126">The following example counts the number of elements in an XML document.</span></span>  
  
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
  
##### <a name="input"></a><span data-ttu-id="98ec5-127">Giriş</span><span class="sxs-lookup"><span data-stu-id="98ec5-127">Input</span></span>  
 <span data-ttu-id="98ec5-128">Book.XML</span><span class="sxs-lookup"><span data-stu-id="98ec5-128">book.xml</span></span>  
  
```xml  
<!--sample XML fragment-->  
<book genre='novel' ISBN='1-861001-57-5' misc='sale-item'>  
  <title>The Handmaid's Tale</title>  
  <price>14.95</price>  
</book>  
```  
  
##### <a name="output"></a><span data-ttu-id="98ec5-129">Çıkış</span><span class="sxs-lookup"><span data-stu-id="98ec5-129">Output</span></span>  
  
```  
Number of elements in book.xml: 3  
```  
  
 <span data-ttu-id="98ec5-130">Www.gotdotnet.com/userfiles/XMLDom/extendDOM.zip XML DOM sınıfları (System.Xml) genişletmek nasıl gösteren bir örnek için bkz.</span><span class="sxs-lookup"><span data-stu-id="98ec5-130">For an example showing how to extend the XML DOM classes (System.Xml), see www.gotdotnet.com/userfiles/XMLDom/extendDOM.zip.</span></span>  
  
## <a name="node-event-handler"></a><span data-ttu-id="98ec5-131">Düğüm olay işleyicisi</span><span class="sxs-lookup"><span data-stu-id="98ec5-131">Node Event Handler</span></span>  
 <span data-ttu-id="98ec5-132">DOM .NET Framework uygulamasını almak ve bir XML belgesi düğümler değiştirdiğinizde olayları işlemek sağlayan bir olay sistem de içerir.</span><span class="sxs-lookup"><span data-stu-id="98ec5-132">The .NET Framework implementation of the DOM also includes an event system that enables you to receive and handle events when nodes in an XML document change.</span></span> <span data-ttu-id="98ec5-133">Kullanarak <xref:System.Xml.XmlNodeChangedEventHandler> ve <xref:System.Xml.XmlNodeChangedEventArgs> sınıfları yakalayabilirsiniz `NodeChanged`, `NodeChanging`, `NodeInserted`, `NodeInserting`, `NodeRemoved`, ve `NodeRemoving` olaylar.</span><span class="sxs-lookup"><span data-stu-id="98ec5-133">Using the <xref:System.Xml.XmlNodeChangedEventHandler> and <xref:System.Xml.XmlNodeChangedEventArgs> classes, you can capture `NodeChanged`, `NodeChanging`, `NodeInserted`, `NodeInserting`, `NodeRemoved`, and `NodeRemoving` events.</span></span>  
  
 <span data-ttu-id="98ec5-134">Özgün DOM sınıflarda gibi olay işleme işlemi tam olarak aynı türetilmiş sınıflarda çalışır.</span><span class="sxs-lookup"><span data-stu-id="98ec5-134">The event-handling process works exactly the same in derived classes as it would in the original DOM classes.</span></span>  
  
 <span data-ttu-id="98ec5-135">Düğüm olay işleme hakkında daha fazla bilgi için bkz: [olayları](../../../../docs/standard/events/index.md) ve <xref:System.Xml.XmlNodeChangedEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="98ec5-135">For more information regarding node event handling, see [Events](../../../../docs/standard/events/index.md) and <xref:System.Xml.XmlNodeChangedEventHandler>.</span></span>  
  
## <a name="default-attributes-and-the-createelement-method"></a><span data-ttu-id="98ec5-136">Varsayılan öznitelikleri ve CreateElement yöntemi</span><span class="sxs-lookup"><span data-stu-id="98ec5-136">Default Attributes and the CreateElement Method</span></span>  
 <span data-ttu-id="98ec5-137">Kılıyorsa <xref:System.Xml.XmlDocument.CreateElement%2A> türetilmiş bir sınıf, varsayılan belge düzenlerken yeni öğeler oluştururken, öznitelikler eklenip eklenmeyeceği yöntemi.</span><span class="sxs-lookup"><span data-stu-id="98ec5-137">If you are overriding the <xref:System.Xml.XmlDocument.CreateElement%2A> method in a derived class, default attributes are not added when you are creating new elements while editing the document.</span></span> <span data-ttu-id="98ec5-138">Bu yalnızca bir düzenlenirken bir sorundur.</span><span class="sxs-lookup"><span data-stu-id="98ec5-138">This is only an issue while editing.</span></span> <span data-ttu-id="98ec5-139">Çünkü <xref:System.Xml.XmlDocument.CreateElement%2A> yöntemdir varsayılan öznitelikler eklemek için sorumlu bir <xref:System.Xml.XmlDocument>, bu işlev kod <xref:System.Xml.XmlDocument.CreateElement%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="98ec5-139">Because the <xref:System.Xml.XmlDocument.CreateElement%2A> method is responsible for adding default attributes to an <xref:System.Xml.XmlDocument>, you must code this functionality in the <xref:System.Xml.XmlDocument.CreateElement%2A> method.</span></span> <span data-ttu-id="98ec5-140">Yüklüyorsanız, size bir <xref:System.Xml.XmlDocument> varsayılan öznitelikleri içeren, düzgün işlenecek.</span><span class="sxs-lookup"><span data-stu-id="98ec5-140">If you are loading an <xref:System.Xml.XmlDocument> that includes default attributes, they will be handled correctly.</span></span> <span data-ttu-id="98ec5-141">Varsayılan öznitelikleri hakkında daha fazla bilgi için bkz: [DOM öğeleri için yeni öznitelikler oluşturma](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="98ec5-141">For more information on default attributes, see [Creating New Attributes for Elements in the DOM](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98ec5-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="98ec5-142">See Also</span></span>  
 [<span data-ttu-id="98ec5-143">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="98ec5-143">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
