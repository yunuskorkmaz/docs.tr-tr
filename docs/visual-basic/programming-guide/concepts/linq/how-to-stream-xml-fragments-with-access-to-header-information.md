---
title: 'Nasıl yapılır: XML parçaları üst bilgileri (Visual Basic) erişim akışı'
ms.date: 07/20/2015
ms.assetid: effd10df-87c4-4d7a-8a9a-1434d829dca5
ms.openlocfilehash: 60ec63c33d20fa38bed32d9c46c4acfe649ecd15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644478"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-visual-basic"></a><span data-ttu-id="41b07-102">Nasıl yapılır: XML parçaları üst bilgileri (Visual Basic) erişim akışı</span><span class="sxs-lookup"><span data-stu-id="41b07-102">How to: Stream XML Fragments with Access to Header Information (Visual Basic)</span></span>
<span data-ttu-id="41b07-103">Bazen büyük XML dosyaları okuma ve böylece uygulamanın bellek alanını tahmin edilebilir uygulamanızı yazma gerekir.</span><span class="sxs-lookup"><span data-stu-id="41b07-103">Sometimes you have to read arbitrarily large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="41b07-104">Bir XML ağaç içeren büyük bir XML dosyası doldurmak çalışırsanız, bellek kullanımı dosyasının boyutunu orantılı — diğer bir deyişle, aşırı.</span><span class="sxs-lookup"><span data-stu-id="41b07-104">If you attempt to populate an XML tree with a large XML file, your memory usage will be proportional to the size of the file—that is, excessive.</span></span> <span data-ttu-id="41b07-105">Bu nedenle, bir akış teknik yerine kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="41b07-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="41b07-106">Bir seçenektir kullanarak uygulamanızı yazmak için <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="41b07-106">One option is to write your application using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="41b07-107">Ancak, kullanmak isteyebilirsiniz [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] XML ağaç sorgulanamıyor.</span><span class="sxs-lookup"><span data-stu-id="41b07-107">However, you might want to use [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to query the XML tree.</span></span> <span data-ttu-id="41b07-108">Bu durumda, kendi özel eksen yöntemi yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41b07-108">If this is the case, you can write your own custom axis method.</span></span> <span data-ttu-id="41b07-109">Daha fazla bilgi için bkz: [nasıl yapılır: XML eksen yöntemi (Visual Basic) için bir LINQ yazma](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).</span><span class="sxs-lookup"><span data-stu-id="41b07-109">For more information, see [How to: Write a LINQ to XML Axis Method (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).</span></span>  
  
 <span data-ttu-id="41b07-110">Kendi eksen yöntemi yazmak için kullandığı küçük bir yöntem yazmak <xref:System.Xml.XmlReader> içinde ilgi düğümlerinden biri ulaşana kadar düğümleri okumak için.</span><span class="sxs-lookup"><span data-stu-id="41b07-110">To write your own axis method, you write a small method that uses the <xref:System.Xml.XmlReader> to read nodes until it reaches one of the nodes in which you are interested.</span></span> <span data-ttu-id="41b07-111">Daha sonra yöntemi çağırır <xref:System.Xml.Linq.XNode.ReadFrom%2A>, olarak okuyan <xref:System.Xml.XmlReader> ve bir XML parçası başlatır.</span><span class="sxs-lookup"><span data-stu-id="41b07-111">The method then calls <xref:System.Xml.Linq.XNode.ReadFrom%2A>, which reads from the <xref:System.Xml.XmlReader> and instantiates an XML fragment.</span></span> <span data-ttu-id="41b07-112">Ardından, özel eksen yöntemi LINQ sorgularını yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41b07-112">You can then write LINQ queries on your custom axis method.</span></span>  
  
 <span data-ttu-id="41b07-113">Akış teknikleri en iyi kaynak belge yalnızca bir kez işlem gerekir ve belge sırayla öğeleri işleyebilmesi için durumlarda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="41b07-113">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="41b07-114">Belirli standart sorgu işleçleri gibi <xref:System.Linq.Enumerable.OrderBy%2A>kendi kaynak yinelemek, tüm verileri toplamak, sıralanmasını ve son olarak dizinin ilk öğesi verim.</span><span class="sxs-lookup"><span data-stu-id="41b07-114">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="41b07-115">İlk öğe sağlayan önce kaynağı gerçeğe bir sorgu işleci kullanırsanız, bir küçük bellek alanını bulamayacaktır unutmayın.</span><span class="sxs-lookup"><span data-stu-id="41b07-115">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41b07-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="41b07-116">Example</span></span>  
 <span data-ttu-id="41b07-117">Bazen biraz daha fazla ilginç sorun alır.</span><span class="sxs-lookup"><span data-stu-id="41b07-117">Sometimes the problem gets just a little more interesting.</span></span> <span data-ttu-id="41b07-118">Aşağıdaki XML belgesinde özel eksen yönteminizi tüketici ayrıca her öğenin ait olduğu müşterinin adını bilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="41b07-118">In the following XML document, the consumer of your custom axis method also has to know the name of the customer that each item belongs to.</span></span>  
  
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
  
 <span data-ttu-id="41b07-119">Bu örnek alan aynı zamanda bu başlık bilgilerini izleme, üst bilgileri kaydedin ve üst bilgileri ve numaralandırma ayrıntı içeren küçük bir XML ağaç yapı yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="41b07-119">The approach that this example takes is to also watch for this header information, save the header information, and then build a small XML tree that contains both the header information and the detail that you are enumerating.</span></span> <span data-ttu-id="41b07-120">Eksen yöntemi, daha sonra bu yeni, küçük XML ağaç verir.</span><span class="sxs-lookup"><span data-stu-id="41b07-120">The axis method then yields this new, small XML tree.</span></span> <span data-ttu-id="41b07-121">Sorgu daha sonra ayrıntılı bilgilerin yanı sıra üst bilgileri erişebilir.</span><span class="sxs-lookup"><span data-stu-id="41b07-121">The query then has access to the header information as well as the detail information.</span></span>  
  
 <span data-ttu-id="41b07-122">Bu yaklaşımın küçük bellek kaplama alanı vardır.</span><span class="sxs-lookup"><span data-stu-id="41b07-122">This approach has a small memory footprint.</span></span> <span data-ttu-id="41b07-123">Her ayrıntı XML parçası verdiğini gibi başvuru önceki parça tutulur ve atık toplama için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="41b07-123">As each detail XML fragment is yielded, no references are kept to the previous fragment, and it is available for garbage collection.</span></span> <span data-ttu-id="41b07-124">Bu teknik öbek üzerinde birçok kısa süreli nesne oluşturduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="41b07-124">Note that this technique creates many short lived objects on the heap.</span></span>  
  
 <span data-ttu-id="41b07-125">Aşağıdaki örnek XML parçaları URI tarafından belirtilen dosyadan akışları özel eksen yöntemi uygulamak ve nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="41b07-125">The following example shows how to implement and use a custom axis method that streams XML fragments from the file specified by the URI.</span></span> <span data-ttu-id="41b07-126">Bu özel eksen özellikle sahip bir belge bekliyor gibi yazılır `Customer`, `Name`, ve `Item` öğeleri ve bu öğeleri yukarıdaki olduğu gibi düzenlenmesini, `Source.xml` belge.</span><span class="sxs-lookup"><span data-stu-id="41b07-126">This custom axis is specifically written such that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the above `Source.xml` document.</span></span> <span data-ttu-id="41b07-127">Bu simplistic bir uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="41b07-127">It is a simplistic implementation.</span></span> <span data-ttu-id="41b07-128">Geçersiz bir belge ayrıştırmak için daha sağlam bir uygulama hazırlanması.</span><span class="sxs-lookup"><span data-stu-id="41b07-128">A more robust implementation would be prepared to parse an invalid document.</span></span>  
  
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
  
 <span data-ttu-id="41b07-129">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="41b07-129">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="41b07-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="41b07-130">See Also</span></span>  
 [<span data-ttu-id="41b07-131">Gelişmiş LINQ-XML programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41b07-131">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
