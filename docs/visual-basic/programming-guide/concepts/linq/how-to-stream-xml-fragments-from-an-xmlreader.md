---
title: "Nasıl yapılır: Stream parçalarını xmlreader'dan (Visual Basic)"
ms.date: 07/20/2015
ms.assetid: f67ce598-4a12-4dcb-9a07-24deca02a111
ms.openlocfilehash: 8c5aa1afff983f3763bbf7c74268eba622df7751
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61614902"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-visual-basic"></a><span data-ttu-id="0a414-102">Nasıl yapılır: Stream parçalarını xmlreader'dan (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a414-102">How to: Stream XML Fragments from an XmlReader (Visual Basic)</span></span>
<span data-ttu-id="0a414-103">Büyük XML dosyalarını işlemek varsa, tüm XML ağacının belleğe yüklemek için uygun olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="0a414-103">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="0a414-104">Bu konuda gösterir kullanarak parçalarının akışını yapma hakkında bir <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="0a414-104">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="0a414-105">Kullanmak için en etkili yollarından biri bir <xref:System.Xml.XmlReader> okunacak <xref:System.Xml.Linq.XElement> nesneleri, kendi özel eksen yöntem yazmaktır.</span><span class="sxs-lookup"><span data-stu-id="0a414-105">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="0a414-106">Eksen yöntemi genellikle bir koleksiyonu gibi döndürür <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement>, bu konudaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="0a414-106">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="0a414-107">Özel eksen yöntemi çağırarak XML parçası oluşturduktan sonra <xref:System.Xml.Linq.XNode.ReadFrom%2A> yöntemini kullanarak koleksiyon döndürmek `yield return`.</span><span class="sxs-lookup"><span data-stu-id="0a414-107">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="0a414-108">Bu özel eksen yönteminize ertelenmiş yürütme semantiği sağlar.</span><span class="sxs-lookup"><span data-stu-id="0a414-108">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="0a414-109">XML ağacından oluşturduğunuzda bir <xref:System.Xml.XmlReader> nesnesi <xref:System.Xml.XmlReader> bir öğede konumlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0a414-109">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="0a414-110"><xref:System.Xml.Linq.XNode.ReadFrom%2A> Öğenin kapatma etiketi okudu kadar yöntemi döndürmez.</span><span class="sxs-lookup"><span data-stu-id="0a414-110">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="0a414-111">Kısmi bir ağaç oluşturmak istiyorsanız, oluşturabileceğiniz bir <xref:System.Xml.XmlReader>, dönüştürmek istediğiniz düğüme okuyucu getirin bir <xref:System.Xml.Linq.XElement> ağaç ve oluşturup <xref:System.Xml.Linq.XElement> nesne.</span><span class="sxs-lookup"><span data-stu-id="0a414-111">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
 <span data-ttu-id="0a414-112">Konu [nasıl yapılır: Stream (Visual Basic) üst bilgilere erişimle XML parçalarının](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) bilgileri ve daha karmaşık bir belge akışı konusunda bir örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="0a414-112">The topic [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>  
  
 <span data-ttu-id="0a414-113">Konu [nasıl yapılır: Akış dönüştürme, büyük XML belgeleri (Visual Basic) gerçekleştirmek](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) küçük bellek ayak izini sürdürürken son derece büyük XML belgelerini dönüştürmek için LINQ to XML kullanarak bir örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="0a414-113">The topic [How to: Perform Streaming Transform of Large XML Documents (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a414-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="0a414-114">Example</span></span>  
 <span data-ttu-id="0a414-115">Bu örnek bir özel eksen yöntemi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0a414-115">This example creates a custom axis method.</span></span> <span data-ttu-id="0a414-116">Kullanarak sorgulayabilirsiniz bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu.</span><span class="sxs-lookup"><span data-stu-id="0a414-116">You can query it by using a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query.</span></span> <span data-ttu-id="0a414-117">Özel eksen yöntemi `StreamRootChildDoc`, özellikle yinelenen olan bir belgeyi okumak için tasarlanmış bir yöntem `Child` öğesi.</span><span class="sxs-lookup"><span data-stu-id="0a414-117">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        Dim markup = "<Root>" &  
                     "  <Child Key=""01"">" &  
                     "    <GrandChild>aaa</GrandChild>" &  
                     "  </Child>" &  
                     "  <Child Key=""02"">" &  
                     "    <GrandChild>bbb</GrandChild>" &  
                     "  </Child>" &  
                     "  <Child Key=""03"">" &  
                     "    <GrandChild>ccc</GrandChild>" &  
                     "  </Child>" &  
                     "</Root>"  
  
        Dim grandChildData =  
             From el In New StreamRootChildDoc(New IO.StringReader(markup))  
             Where CInt(el.@Key) > 1  
             Select el.<GrandChild>.Value  
  
        For Each s In grandChildData  
            Console.WriteLine(s)  
        Next  
    End Sub  
End Module  
  
Public Class StreamRootChildDoc  
    Implements IEnumerable(Of XElement)  
  
    Private _stringReader As IO.StringReader  
  
    Public Sub New(ByVal stringReader As IO.StringReader)  
        _stringReader = stringReader  
    End Sub  
  
    Public Function GetEnumerator() As IEnumerator(Of XElement) Implements IEnumerable(Of XElement).GetEnumerator  
        Return New StreamChildEnumerator(_stringReader)  
    End Function  
  
    Public Function GetEnumerator1() As IEnumerator Implements IEnumerable.GetEnumerator  
        Return Me.GetEnumerator()  
    End Function  
End Class  
  
Public Class StreamChildEnumerator  
    Implements IEnumerator(Of XElement)  
  
    Private _current As XElement  
    Private _reader As Xml.XmlReader  
    Private _stringReader As IO.StringReader  
  
    Public Sub New(ByVal stringReader As IO.StringReader)  
        _stringReader = stringReader  
        _reader = Xml.XmlReader.Create(_stringReader)  
        _reader.MoveToContent()  
    End Sub  
  
    Public ReadOnly Property Current As XElement Implements IEnumerator(Of XElement).Current  
        Get  
            Return _current  
        End Get  
    End Property  
  
    Public ReadOnly Property Current1 As Object Implements IEnumerator.Current  
        Get  
            Return Me.Current  
        End Get  
    End Property  
  
    Public Function MoveNext() As Boolean Implements IEnumerator.MoveNext  
        While _reader.Read()  
            Select Case _reader.NodeType  
                Case Xml.XmlNodeType.Element  
                    Dim el = TryCast(XElement.ReadFrom(_reader), XElement)  
                    If el IsNot Nothing Then  
                        _current = el  
                        Return True  
                    End If  
            End Select  
        End While  
  
        Return False  
    End Function  
  
    Public Sub Reset() Implements IEnumerator.Reset  
        _reader = Xml.XmlReader.Create(_stringReader)  
        _reader.MoveToContent()  
    End Sub  
  
#Region "IDisposable Support"  
    Private disposedValue As Boolean ' To detect redundant calls  
  
    ' IDisposable  
    Protected Overridable Sub Dispose(ByVal disposing As Boolean)  
        If Not Me.disposedValue Then  
            If disposing Then  
                _reader.Close()  
            End If  
        End If  
        Me.disposedValue = True  
    End Sub  
  
    Public Sub Dispose() Implements IDisposable.Dispose  
        Dispose(True)  
        GC.SuppressFinalize(Me)  
    End Sub  
#End Region  
  
End Class  
```  
  
 <span data-ttu-id="0a414-118">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="0a414-118">This example produces the following output:</span></span>  
  
```  
bbb  
ccc  
```  
  
 <span data-ttu-id="0a414-119">Bu örnekte, kaynak belge çok küçüktür.</span><span class="sxs-lookup"><span data-stu-id="0a414-119">In this example, the source document is very small.</span></span> <span data-ttu-id="0a414-120">Ancak, milyonlarca olsa bile `Child` öğeleri, bu örnekte küçük bellek Ayak izi yine de sahip.</span><span class="sxs-lookup"><span data-stu-id="0a414-120">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a414-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a414-121">See also</span></span>

- [<span data-ttu-id="0a414-122">İzlenecek yol: Visual Basic'te IEnumerable(Of T) uygulama</span><span class="sxs-lookup"><span data-stu-id="0a414-122">Walkthrough: Implementing IEnumerable(Of T) in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md)
- [<span data-ttu-id="0a414-123">Ayrıştırma XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a414-123">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
