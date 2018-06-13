---
title: 'Nasıl yapılır: akış parçalarını gelen XmlReader (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: f67ce598-4a12-4dcb-9a07-24deca02a111
ms.openlocfilehash: 38a81e83421dffc997a2cbfd6d0996da5ece18d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643402"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-visual-basic"></a><span data-ttu-id="76f44-102">Nasıl yapılır: akış parçalarını gelen XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76f44-102">How to: Stream XML Fragments from an XmlReader (Visual Basic)</span></span>
<span data-ttu-id="76f44-103">Büyük XML dosyalarını işlemek varsa, XML ağacın tamamı belleğe yüklemek için uygun olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="76f44-103">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="76f44-104">Bu konuda kullanarak parçaları akışı gösterilmektedir bir <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="76f44-104">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="76f44-105">Kullanmak için en etkili yollarından biri, bir <xref:System.Xml.XmlReader> okumak için <xref:System.Xml.Linq.XElement> nesnedir kendi özel eksen yöntemi yazmak için.</span><span class="sxs-lookup"><span data-stu-id="76f44-105">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="76f44-106">Bir eksen yöntemi bir koleksiyon gibi tipik döndürür <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement>, bu konuda örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="76f44-106">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="76f44-107">Özel eksen yönteminde çağırarak XML parçası oluşturduktan sonra <xref:System.Xml.Linq.XNode.ReadFrom%2A> yöntemi kullanarak koleksiyon döndürmek `yield return`.</span><span class="sxs-lookup"><span data-stu-id="76f44-107">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="76f44-108">Bu, özel eksen yönteminize ertelenmiş yürütme semantiği sağlar.</span><span class="sxs-lookup"><span data-stu-id="76f44-108">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="76f44-109">Bir XML ağacından oluşturduğunuzda bir <xref:System.Xml.XmlReader> nesnesi <xref:System.Xml.XmlReader> bir öğede konumlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="76f44-109">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="76f44-110"><xref:System.Xml.Linq.XNode.ReadFrom%2A> Yöntemi öğenin kapatma etiketi okudu kadar döndürmez.</span><span class="sxs-lookup"><span data-stu-id="76f44-110">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="76f44-111">Kısmi bir ağaç oluşturmak istiyorsanız, örneği oluşturmak bir <xref:System.Xml.XmlReader>, dönüştürmek istediğiniz düğüme okuyucu getirin bir <xref:System.Xml.Linq.XElement> ağacı ve ardından oluşturun <xref:System.Xml.Linq.XElement> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="76f44-111">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
 <span data-ttu-id="76f44-112">Konu [nasıl yapılır: akışı XML parçaları üst bilgileri (Visual Basic) erişimi](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) bilgi ve daha karmaşık bir belge akış konusunda bir örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="76f44-112">The topic [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>  
  
 <span data-ttu-id="76f44-113">Konu [nasıl yapılır: gerçekleştirmek akış dönüştürme, büyük XML belgeleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) küçük bellek alanını korurken son derece büyük XML belgelerini dönüştürmek için LINQ-XML kullanarak bir örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="76f44-113">The topic [How to: Perform Streaming Transform of Large XML Documents (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76f44-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="76f44-114">Example</span></span>  
 <span data-ttu-id="76f44-115">Bu örnek, bir özel eksen yöntemi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="76f44-115">This example creates a custom axis method.</span></span> <span data-ttu-id="76f44-116">Kullanarak sorgulama yapabilirsiniz bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu.</span><span class="sxs-lookup"><span data-stu-id="76f44-116">You can query it by using a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query.</span></span> <span data-ttu-id="76f44-117">Özel eksen yöntemi `StreamRootChildDoc`, özellikle yinelenen olan bir belgeyi okumak için tasarlanmış bir yöntemle `Child` öğesi.</span><span class="sxs-lookup"><span data-stu-id="76f44-117">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
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
  
 <span data-ttu-id="76f44-118">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="76f44-118">This example produces the following output:</span></span>  
  
```  
bbb  
ccc  
```  
  
 <span data-ttu-id="76f44-119">Bu örnekte, kaynak belge çok küçük.</span><span class="sxs-lookup"><span data-stu-id="76f44-119">In this example, the source document is very small.</span></span> <span data-ttu-id="76f44-120">Ancak, milyonlarca olsa bile `Child` öğeleri, bu örnekte küçük bellek alanını hala sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="76f44-120">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76f44-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="76f44-121">See Also</span></span>  
 [<span data-ttu-id="76f44-122">İzlenecek yol: Visual Basic'te IEnumerable(Of T) uygulama</span><span class="sxs-lookup"><span data-stu-id="76f44-122">Walkthrough: Implementing IEnumerable(Of T) in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md)  
 [<span data-ttu-id="76f44-123">Ayrıştırma XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76f44-123">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
