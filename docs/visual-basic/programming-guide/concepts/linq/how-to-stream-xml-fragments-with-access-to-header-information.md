---
title: 'Nasıl yapılır: (Visual Basic) üst bilgilere erişimle XML parçalarının Stream'
ms.date: 07/20/2015
ms.assetid: effd10df-87c4-4d7a-8a9a-1434d829dca5
ms.openlocfilehash: c11a64eb28e8952636ab877479852bd883fc7eba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61614653"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-visual-basic"></a>Nasıl yapılır: (Visual Basic) üst bilgilere erişimle XML parçalarının Stream
Bazen büyük XML dosyaları okur ve bellek Ayak izi uygulamanın öngörülebilir böylece uygulamanız yazma gerekir. İle büyük bir XML dosyasını bir XML ağacı doldurma çalışırsanız, bellek kullanım için dosya boyutu orantılı — diğer bir deyişle, aşırı. Bu nedenle, bir akış teknik yerine kullanmanız gerekir.  
  
 Bir seçenektir kullanarak uygulamanızı yazmak için <xref:System.Xml.XmlReader>. Ancak, kullanmak isteyebilirsiniz [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] XML ağacı sorgulanamıyor. Bu durumda, kendi özel eksen yöntemi yazabilirsiniz. Daha fazla bilgi için [nasıl yapılır: LINQ to XML eksen yöntemi (Visual Basic) yazma](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).  
  
 Kendi eksen yöntemi yazma için kullanan küçük bir yöntem yazmaktır. <xref:System.Xml.XmlReader> , olduğu ilgilenen düğümlerinden biri ulaşana dek düğümleri okumak için. Daha sonra yöntemi çağırır <xref:System.Xml.Linq.XNode.ReadFrom%2A>, hangi okur <xref:System.Xml.XmlReader> ve bir XML parçası başlatır. Ardından, özel eksen yöntemi LINQ sorguları da yazabilirsiniz.  
  
 Akış teknikleri, burada yalnızca bir kez kaynak belge işlemek gereken ve belge sırada öğeleri işleyebilir durumlarda en iyi şekilde uygulanır. Belirli standart sorgu işleçleri gibi <xref:System.Linq.Enumerable.OrderBy%2A>kaynağına yineleme, tüm verileri Topla, sıralanmasını ve son sıradaki ilk öğeyi yield. İlk öğeyi oluşturan önce kaynağına gerçekleştiren bir sorgu işlecini kullanmak, bir küçük bellek Ayak izi korumaz unutmayın.  
  
## <a name="example"></a>Örnek  
 Bazı durumlarda biraz daha fazla ilgi çekici sorun alır. Aşağıdaki XML belgesindeki özel eksen yönteminizi tüketicisinin her öğenin ait olduğu müşterinin adını bilmek de vardır.  
  
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
  
 Bu örnek alan için bu üst bilgi bilgileri izlemek, üst bilgi bilgileri kaydedin ve ardından üst bilgi bilgileri hem numaralandırma ayrıntı içeren küçük bir XML ağacı oluşturmak için bir yaklaşımdır. Eksen yöntemi, ardından bu yeni, küçük XML ağacı verir. Sorgu, daha sonra ayrıntılı bilgilerin yanı sıra, üst bilgi bilgileri erişimi vardır.  
  
 Bu yaklaşım, küçük bellek Ayak izi sahiptir. Her ayrıntı XML parçası veriyor gibi başvuru için önceki parça tutulur ve çöp toplama için kullanılabilir. Bu teknik yığın üzerinde çok kısa süreli nesneleri oluşturur unutmayın.  
  
 Aşağıdaki örnek, uygulamak ve URI tarafından belirtilen dosyaya XML parçalarının akışını bir özel eksen yöntemi kullanmak gösterilmektedir. Bu özel eksen özellikle sahip bir belge beklediği gibi yazılır `Customer`, `Name`, ve `Item` öğeleri ve bu öğeleri olduğu gibi yukarıdaki düzenlenmesini, `Source.xml` belge. Bu basitleştirilmiş bir uygulamasıdır. Geçersiz bir belge ayrıştırmak için daha sağlam bir uygulama hazır.  
  
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
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş LINQ to XML programlama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
