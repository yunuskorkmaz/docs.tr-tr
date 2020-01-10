---
title: 'Nasıl yapılır: üst bilgi bilgilerine erişimi olan XML parçalarını akışa alma'
ms.date: 07/20/2015
ms.assetid: effd10df-87c4-4d7a-8a9a-1434d829dca5
ms.openlocfilehash: 325609b9f8cf1feebcb4be1fcfd0122e12100156
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636698"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-visual-basic"></a><span data-ttu-id="93f9c-102">Nasıl yapılır: üst bilgi bilgilerine erişimi olan XML parçalarını akışa alma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93f9c-102">How to: Stream XML Fragments with Access to Header Information (Visual Basic)</span></span>
<span data-ttu-id="93f9c-103">Bazen rastgele büyük XML dosyalarını okumanız ve uygulamanın bellek parmak izin tahmin edilebilir olması için uygulamanızı yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="93f9c-103">Sometimes you have to read arbitrarily large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="93f9c-104">Bir XML ağacını büyük bir XML dosyası ile doldurmayı denerseniz, bellek kullanımınız dosyanın boyutuyla orantılıdır; yani çok fazla.</span><span class="sxs-lookup"><span data-stu-id="93f9c-104">If you attempt to populate an XML tree with a large XML file, your memory usage will be proportional to the size of the file—that is, excessive.</span></span> <span data-ttu-id="93f9c-105">Bu nedenle, bunun yerine bir akış tekniği kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="93f9c-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="93f9c-106">Bir seçenek <xref:System.Xml.XmlReader>kullanarak uygulamanızı yazmaktır.</span><span class="sxs-lookup"><span data-stu-id="93f9c-106">One option is to write your application using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="93f9c-107">Ancak, XML ağacını sorgulamak için LINQ kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93f9c-107">However, you might want to use LINQ to query the XML tree.</span></span> <span data-ttu-id="93f9c-108">Bu durumda, kendi özel eksen yönteminizi yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93f9c-108">If this is the case, you can write your own custom axis method.</span></span> <span data-ttu-id="93f9c-109">Daha fazla bilgi için bkz. [nasıl yapılır: LINQ to XML eksen yöntemi yazma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).</span><span class="sxs-lookup"><span data-stu-id="93f9c-109">For more information, see [How to: Write a LINQ to XML Axis Method (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).</span></span>  
  
 <span data-ttu-id="93f9c-110">Kendi eksen yönteminizi yazmak için, ilgilendiğiniz düğümlerin birine ulaşıncaya kadar düğümleri okumak için <xref:System.Xml.XmlReader> kullanan küçük bir yöntem yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="93f9c-110">To write your own axis method, you write a small method that uses the <xref:System.Xml.XmlReader> to read nodes until it reaches one of the nodes in which you are interested.</span></span> <span data-ttu-id="93f9c-111">Daha sonra yöntemi, <xref:System.Xml.XmlReader> okuyan ve bir XML parçasını örnekleyen <xref:System.Xml.Linq.XNode.ReadFrom%2A>çağırır.</span><span class="sxs-lookup"><span data-stu-id="93f9c-111">The method then calls <xref:System.Xml.Linq.XNode.ReadFrom%2A>, which reads from the <xref:System.Xml.XmlReader> and instantiates an XML fragment.</span></span> <span data-ttu-id="93f9c-112">Daha sonra özel eksen yönteinizde LINQ sorguları yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93f9c-112">You can then write LINQ queries on your custom axis method.</span></span>  
  
 <span data-ttu-id="93f9c-113">Akış teknikleri en iyi şekilde, kaynak belgeyi yalnızca bir kez işleyebilmeniz ve öğeleri belge düzeninde işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93f9c-113">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="93f9c-114"><xref:System.Linq.Enumerable.OrderBy%2A>gibi bazı standart sorgu işleçleri, kaynaklarını yineleyebilir, tüm verileri toplar, sıralar ve son olarak dizideki ilk öğeyi verir.</span><span class="sxs-lookup"><span data-stu-id="93f9c-114">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="93f9c-115">İlk öğeyi bırakmadan önce kaynağını üreten bir sorgu işleci kullanırsanız, küçük bir bellek parmak izini saklayacağınızı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="93f9c-115">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93f9c-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="93f9c-116">Example</span></span>  
 <span data-ttu-id="93f9c-117">Bazen sorun biraz daha ilginç olur.</span><span class="sxs-lookup"><span data-stu-id="93f9c-117">Sometimes the problem gets just a little more interesting.</span></span> <span data-ttu-id="93f9c-118">Aşağıdaki XML belgesinde, özel eksen yönteminizin tüketicisi, her öğenin ait olduğu müşterinin adını da bilmelidir.</span><span class="sxs-lookup"><span data-stu-id="93f9c-118">In the following XML document, the consumer of your custom axis method also has to know the name of the customer that each item belongs to.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root>  
  <Customer>  
    <Name>A. Datum Corporation</Name>  
    <Item>  
      <Key>0001</Key>  
    </Item>  
    <Item>  
      <Key>0002</Key>  
    </Item>  
    <Item>  
      <Key>0003</Key>  
    </Item>  
    <Item>  
      <Key>0004</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Fabrikam, Inc.</Name>  
    <Item>  
      <Key>0005</Key>  
    </Item>  
    <Item>  
      <Key>0006</Key>  
    </Item>  
    <Item>  
      <Key>0007</Key>  
    </Item>  
    <Item>  
      <Key>0008</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Southridge Video</Name>  
    <Item>  
      <Key>0009</Key>  
    </Item>  
    <Item>  
      <Key>0010</Key>  
    </Item>  
  </Customer>  
</Root>  
```  
  
 <span data-ttu-id="93f9c-119">Bu örnekte geçen yaklaşım ayrıca, bu üstbilgi bilgilerini izlemek, üst bilgi bilgilerini kaydetmek ve ardından hem başlık bilgilerini hem de numaralandırdığınız ayrıntıyı içeren küçük bir XML ağacı oluşturmanızı kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="93f9c-119">The approach that this example takes is to also watch for this header information, save the header information, and then build a small XML tree that contains both the header information and the detail that you are enumerating.</span></span> <span data-ttu-id="93f9c-120">Ardından Axis yöntemi bu yeni, küçük XML ağacını verir.</span><span class="sxs-lookup"><span data-stu-id="93f9c-120">The axis method then yields this new, small XML tree.</span></span> <span data-ttu-id="93f9c-121">Sorgu daha sonra başlık bilgilerine ve ayrıntı bilgilerine erişimi de vardır.</span><span class="sxs-lookup"><span data-stu-id="93f9c-121">The query then has access to the header information as well as the detail information.</span></span>  
  
 <span data-ttu-id="93f9c-122">Bu yaklaşımın küçük bir bellek ayak izi vardır.</span><span class="sxs-lookup"><span data-stu-id="93f9c-122">This approach has a small memory footprint.</span></span> <span data-ttu-id="93f9c-123">Her ayrıntı XML parçası, bir önceki parçaya hiçbir başvuru tutulmazsa ve çöp toplama için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="93f9c-123">As each detail XML fragment is yielded, no references are kept to the previous fragment, and it is available for garbage collection.</span></span> <span data-ttu-id="93f9c-124">Bu tekniğin yığın üzerinde birçok kısa süreli nesne oluşturduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="93f9c-124">Note that this technique creates many short lived objects on the heap.</span></span>  
  
 <span data-ttu-id="93f9c-125">Aşağıdaki örnek, URI tarafından belirtilen dosyadan XML parçalarını akıyan bir özel eksen yönteminin nasıl uygulanacağını ve kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="93f9c-125">The following example shows how to implement and use a custom axis method that streams XML fragments from the file specified by the URI.</span></span> <span data-ttu-id="93f9c-126">Bu özel eksen özellikle `Customer`, `Name`ve `Item` öğelerine sahip bir belgeyi beklediğinden ve bu öğelerin yukarıdaki `Source.xml` belgesinde olarak düzenlenebilmesini sağlayacak şekilde yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="93f9c-126">This custom axis is specifically written such that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the above `Source.xml` document.</span></span> <span data-ttu-id="93f9c-127">Bu bir uyarlaması uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="93f9c-127">It is a simplistic implementation.</span></span> <span data-ttu-id="93f9c-128">Daha sağlam bir uygulama, geçersiz bir belgeyi ayrıştırmaya hazırlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="93f9c-128">A more robust implementation would be prepared to parse an invalid document.</span></span>  
  
```vb  
Module Module1  
  
    Sub Main()  
        Dim xmlTree = <Root>  
                          <%=  
                              From el In New StreamCustomerItem("Source.xml")  
                              Let itemKey = CInt(el.<Key>.Value)  
                              Where itemKey >= 3 AndAlso itemKey <= 7  
                              Select <Item>  
                                         <Customer><%= el.Parent.<Name>.Value %></Customer>  
                                         <%= el.<Key> %>  
                                     </Item>  
                          %>  
                      </Root>  
  
        Console.WriteLine(xmlTree)  
    End Sub  
  
End Module  
  
Public Class StreamCustomerItem  
    Implements IEnumerable(Of XElement)  
  
    Private _uri As String  
  
    Public Sub New(ByVal uri As String)  
        _uri = uri  
    End Sub  
  
    Public Function GetEnumerator() As IEnumerator(Of XElement) Implements IEnumerable(Of XElement).GetEnumerator  
        Return New StreamCustomerItemEnumerator(_uri)  
    End Function  
  
    Public Function GetEnumerator1() As IEnumerator Implements IEnumerable.GetEnumerator  
        Return Me.GetEnumerator()  
    End Function  
End Class  
  
Public Class StreamCustomerItemEnumerator  
    Implements IEnumerator(Of XElement)  
  
    Private _current As XElement  
    Private _customerName As String  
    Private _reader As Xml.XmlReader  
    Private _uri As String  
  
    Public Sub New(ByVal uri As String)  
        _uri = uri  
        _reader = Xml.XmlReader.Create(_uri)  
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
        Dim item As XElement  
        Dim name As XElement  
  
        ' Parse the file, save header information when encountered, and return the  
        ' current Item XElement.  
  
        ' loop through Customer elements  
        While _reader.Read()  
            If _reader.NodeType = Xml.XmlNodeType.Element Then  
                Select Case _reader.Name  
                    Case "Customer"  
                        ' move to Name element  
                        While _reader.Read()  
  
                            If _reader.NodeType = Xml.XmlNodeType.Element AndAlso  
                                _reader.Name = "Name" Then  
  
                                name = TryCast(XElement.ReadFrom(_reader), XElement)  
                                _customerName = If(name IsNot Nothing, name.Value, "")  
                                Exit While  
                            End If  
  
                        End While  
                    Case "Item"  
                        item = TryCast(XElement.ReadFrom(_reader), XElement)  
                        Dim tempRoot = <Root>  
                                           <Name><%= _customerName %></Name>  
                                           <%= item %>  
                                       </Root>  
                        _current = item  
                        Return True  
                End Select  
            End If  
        End While  
  
        Return False  
    End Function  
  
    Public Sub Reset() Implements IEnumerator.Reset  
        _reader = Xml.XmlReader.Create(_uri)  
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
  
 <span data-ttu-id="93f9c-129">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="93f9c-129">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0003</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0004</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0005</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0006</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0007</Key>  
  </Item>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="93f9c-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93f9c-130">See also</span></span>

- [<span data-ttu-id="93f9c-131">Gelişmiş LINQ to XML Programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93f9c-131">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
