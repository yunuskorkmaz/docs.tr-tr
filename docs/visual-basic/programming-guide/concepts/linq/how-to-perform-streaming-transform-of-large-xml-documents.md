---
title: 'Nasıl yapılır: büyük XML belgelerinin akış dönüşümünü gerçekleştirme'
ms.date: 07/20/2015
ms.assetid: 3d954cc9-4b3c-4b47-8132-ff7541cff53b
ms.openlocfilehash: 58bc76e6f2a269b0baac009f1247d5e94d508cbd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344503"
---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-visual-basic"></a><span data-ttu-id="51f4f-102">Nasıl yapılır: büyük XML belgelerinin akış dönüşümünü gerçekleştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51f4f-102">How to: Perform Streaming Transform of Large XML Documents (Visual Basic)</span></span>
<span data-ttu-id="51f4f-103">Bazen büyük XML dosyalarını dönüştürmeniz ve uygulamanın bellek parmak izin tahmin edilebilir olması için uygulamanızı yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="51f4f-103">Sometimes you have to transform large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="51f4f-104">Bir XML ağacını çok büyük bir XML dosyası ile doldurmayı denerseniz, bellek kullanımınız dosyanın boyutuyla (aşırı) orantılı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="51f4f-104">If you try to populate an XML tree with a very large XML file, your memory usage will be proportional to the size of the file (that is, excessive).</span></span> <span data-ttu-id="51f4f-105">Bu nedenle, bunun yerine bir akış tekniği kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="51f4f-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="51f4f-106">Akış teknikleri en iyi şekilde, kaynak belgeyi yalnızca bir kez işleyebilmeniz ve öğeleri belge düzeninde işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51f4f-106">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="51f4f-107"><xref:System.Linq.Enumerable.OrderBy%2A>gibi bazı standart sorgu işleçleri, kaynaklarını yineleyebilir, tüm verileri toplar, sıralar ve son olarak dizideki ilk öğeyi verir.</span><span class="sxs-lookup"><span data-stu-id="51f4f-107">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="51f4f-108">İlk öğeyi bırakmadan önce kaynağını üreten bir sorgu işleci kullanırsanız, uygulamanız için küçük bir bellek parmak izini saklayacağınızı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="51f4f-108">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint for your application.</span></span>  
  
 <span data-ttu-id="51f4f-109">[Nasıl yapılır: başlık bilgilerine erişimi olan XML parçalarını akışa alma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md)' de açıklanan tekniği kullansanız bile, dönüştürülmüş belgeyi IÇEREN bir xml ağacını oluşturmayı denerseniz bellek kullanımı çok büyük olur.</span><span class="sxs-lookup"><span data-stu-id="51f4f-109">Even if you use the technique described in [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md), if you try to assemble an XML tree that contains the transformed document, memory usage will be too great.</span></span>  
  
 <span data-ttu-id="51f4f-110">İki ana yaklaşım vardır.</span><span class="sxs-lookup"><span data-stu-id="51f4f-110">There are two main approaches.</span></span> <span data-ttu-id="51f4f-111">Bir yaklaşım, <xref:System.Xml.Linq.XStreamingElement>ertelenmiş işleme özelliklerini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="51f4f-111">One approach is to use the deferred processing characteristics of <xref:System.Xml.Linq.XStreamingElement>.</span></span> <span data-ttu-id="51f4f-112">Başka bir yaklaşım de <xref:System.Xml.XmlWriter>oluşturmak ve bir <xref:System.Xml.XmlWriter>öğeleri yazmak için [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yeteneklerini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="51f4f-112">Another approach is to create an <xref:System.Xml.XmlWriter>, and use the capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="51f4f-113">Bu konuda her iki yaklaşım da gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="51f4f-113">This topic demonstrates both approaches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51f4f-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="51f4f-114">Example</span></span>  
 <span data-ttu-id="51f4f-115">Aşağıdaki örnek, [nasıl yapılır: başlık bilgilerine erişimi olan XML parçalarının akışını oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md)hakkında örnek oluşturur.</span><span class="sxs-lookup"><span data-stu-id="51f4f-115">The following example builds on the example in [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>  
  
 <span data-ttu-id="51f4f-116">Bu örnek, çıktının akışı için <xref:System.Xml.Linq.XStreamingElement> ertelenmiş yürütme yeteneklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="51f4f-116">This example uses the deferred execution capabilities of <xref:System.Xml.Linq.XStreamingElement> to stream the output.</span></span> <span data-ttu-id="51f4f-117">Bu örnek, küçük bir bellek parmak izini koruyarak çok büyük bir belgeyi dönüştürebilir.</span><span class="sxs-lookup"><span data-stu-id="51f4f-117">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="51f4f-118">Özel eksenin (`StreamCustomerItem`) özellikle `Customer`, `Name`ve `Item` öğelerine sahip bir belge beklediği ve bu öğelerin aşağıdaki Source. xml belgesinde düzenlenebilmesini sağlayacak şekilde yazıldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="51f4f-118">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="51f4f-119">Ancak, daha güçlü bir uygulama, geçersiz bir belgeyi ayrıştırmaya hazırlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="51f4f-119">A more robust implementation, however, would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="51f4f-120">Kaynak. xml kaynak belgesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="51f4f-120">The following is the source document, Source.xml:</span></span>  
  
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
  
```vb  
Module Module1  
    Sub Main()  
        Dim root = New XStreamingElement("Root",  
            From el In New StreamCustomerItem("Source.xml")  
            Select <Item>  
                       <Customer><%= el.Parent.<Name>.Value %></Customer>  
                       <%= el.<Key> %>  
                   </Item>  
            )  
        root.Save("Test.xml")  
        Console.WriteLine(My.Computer.FileSystem.ReadAllText("Test.xml"))  
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
  
 <span data-ttu-id="51f4f-121">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="51f4f-121">This code produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0001</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0002</Key>  
  </Item>  
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
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0008</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0009</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0010</Key>  
  </Item>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="51f4f-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="51f4f-122">Example</span></span>  
 <span data-ttu-id="51f4f-123">Aşağıdaki örnek ayrıca [nasıl yapılır: başlık bilgilerine erişimi olan XML parçalarının akışını oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span><span class="sxs-lookup"><span data-stu-id="51f4f-123">The following example also builds on the example in [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>  
  
 <span data-ttu-id="51f4f-124">Bu örnek, öğeleri bir <xref:System.Xml.XmlWriter>yazmak için [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="51f4f-124">This example uses the capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="51f4f-125">Bu örnek, küçük bir bellek parmak izini koruyarak çok büyük bir belgeyi dönüştürebilir.</span><span class="sxs-lookup"><span data-stu-id="51f4f-125">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="51f4f-126">Özel eksenin (`StreamCustomerItem`) özellikle `Customer`, `Name`ve `Item` öğelerine sahip bir belge beklediği ve bu öğelerin aşağıdaki Source. xml belgesinde düzenlenebilmesini sağlayacak şekilde yazıldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="51f4f-126">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="51f4f-127">Ancak daha sağlam bir uygulama, kaynak belgeyi bir XSD ile doğrular ya da geçersiz bir belgeyi ayrıştırmaya hazırlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="51f4f-127">A more robust implementation, however, would either validate the source document with an XSD, or would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="51f4f-128">Bu örnek, bu konudaki önceki örnekte olduğu gibi, Source. xml kaynak belgesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="51f4f-128">This example uses the same source document, Source.xml, as the previous example in this topic.</span></span> <span data-ttu-id="51f4f-129">Aynı zamanda tam olarak aynı çıktıyı da üretir.</span><span class="sxs-lookup"><span data-stu-id="51f4f-129">It also produces exactly the same output.</span></span>  
  
 <span data-ttu-id="51f4f-130">Çıkış XML 'sini akışa almak için <xref:System.Xml.Linq.XStreamingElement> kullanmak bir <xref:System.Xml.XmlWriter>yazmaya göre tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="51f4f-130">Using <xref:System.Xml.Linq.XStreamingElement> for streaming the output XML is preferred over writing to an <xref:System.Xml.XmlWriter>.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        Dim srcTree =  
            From el In New StreamCustomerItem("Source.xml")  
            Select <Item>  
                       <Customer><%= el.Parent.<Name>.Value %></Customer>  
                       <%= el.<Key> %>  
                   </Item>  
  
        Dim xws = New Xml.XmlWriterSettings()  
        xws.OmitXmlDeclaration = True  
        xws.Indent = True  
        Using xw = Xml.XmlWriter.Create("Output.xml", xws)  
            xw.WriteStartElement("Root")  
            For Each el In srcTree  
                el.WriteTo(xw)  
            Next  
            xw.WriteEndElement()  
        End Using  
  
        Dim s = My.Computer.FileSystem.ReadAllText("Output.xml")  
        Console.WriteLine(s)  
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
  
 <span data-ttu-id="51f4f-131">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="51f4f-131">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0001</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0002</Key>  
  </Item>  
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
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0008</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0009</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0010</Key>  
  </Item>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="51f4f-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51f4f-132">See also</span></span>

- [<span data-ttu-id="51f4f-133">Gelişmiş LINQ to XML Programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51f4f-133">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
