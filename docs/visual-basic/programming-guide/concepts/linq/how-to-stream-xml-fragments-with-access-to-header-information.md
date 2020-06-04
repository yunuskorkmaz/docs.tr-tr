---
title: 'Nasıl yapılır: Üst Bilgilere Erişimle XML Parçalarının Akışını Yapma'
ms.date: 07/20/2015
ms.assetid: effd10df-87c4-4d7a-8a9a-1434d829dca5
ms.openlocfilehash: 8d0543ff5a772768292c0e3117f41bea9367d23a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397693"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-visual-basic"></a>Nasıl yapılır: üst bilgi bilgilerine erişimi olan XML parçalarını akışa alma (Visual Basic)
Bazen rastgele büyük XML dosyalarını okumanız ve uygulamanın bellek parmak izin tahmin edilebilir olması için uygulamanızı yazmanız gerekir. Bir XML ağacını büyük bir XML dosyası ile doldurmayı denerseniz, bellek kullanımınız dosyanın boyutuyla orantılıdır; yani çok fazla. Bu nedenle, bunun yerine bir akış tekniği kullanmanız gerekir.  
  
 Bir seçenek, kullanarak uygulamanızı yazmaktır <xref:System.Xml.XmlReader> . Ancak, XML ağacını sorgulamak için LINQ kullanmak isteyebilirsiniz. Bu durumda, kendi özel eksen yönteminizi yazabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: LINQ to XML eksen yöntemi yazma (Visual Basic)](how-to-write-a-linq-to-xml-axis-method.md).  
  
 Kendi eksen yönteminizi yazmak için, <xref:System.Xml.XmlReader> ilgilendiğiniz düğümlerin birine ulaşana kadar düğümleri okumak için kullanan küçük bir yöntem yazarsınız. Yöntemi, <xref:System.Xml.Linq.XNode.ReadFrom%2A> öğesinden okuyan <xref:System.Xml.XmlReader> ve bir XML parçasını örnekleyen öğesini çağırır. Daha sonra özel eksen yönteinizde LINQ sorguları yazabilirsiniz.  
  
 Akış teknikleri en iyi şekilde, kaynak belgeyi yalnızca bir kez işleyebilmeniz ve öğeleri belge düzeninde işleyebilirsiniz. Gibi belirli standart sorgu işleçleri, <xref:System.Linq.Enumerable.OrderBy%2A> kaynaklarını yineleyebilir, tüm verileri toplar, sıralar ve son olarak dizideki ilk öğeyi verir. İlk öğeyi bırakmadan önce kaynağını üreten bir sorgu işleci kullanırsanız, küçük bir bellek parmak izini saklayacağınızı unutmayın.  
  
## <a name="example"></a>Örnek  
 Bazen sorun biraz daha ilginç olur. Aşağıdaki XML belgesinde, özel eksen yönteminizin tüketicisi, her öğenin ait olduğu müşterinin adını da bilmelidir.  
  
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
  
 Bu örnekte geçen yaklaşım ayrıca, bu üstbilgi bilgilerini izlemek, üst bilgi bilgilerini kaydetmek ve ardından hem başlık bilgilerini hem de numaralandırdığınız ayrıntıyı içeren küçük bir XML ağacı oluşturmanızı kullanmaktır. Ardından Axis yöntemi bu yeni, küçük XML ağacını verir. Sorgu daha sonra başlık bilgilerine ve ayrıntı bilgilerine erişimi de vardır.  
  
 Bu yaklaşımın küçük bir bellek ayak izi vardır. Her ayrıntı XML parçası, bir önceki parçaya hiçbir başvuru tutulmazsa ve çöp toplama için kullanılabilir. Bu tekniğin yığın üzerinde birçok kısa süreli nesne oluşturduğunu unutmayın.  
  
 Aşağıdaki örnek, URI tarafından belirtilen dosyadan XML parçalarını akıyan bir özel eksen yönteminin nasıl uygulanacağını ve kullanılacağını gösterir. Bu özel eksen özellikle,, ve öğelerinin bulunduğu bir belgeyi beklediğinden `Customer` `Name` `Item` ve bu öğelerin yukarıdaki belgede olarak düzenlenebilmesini sağlayacak şekilde yazılmıştır `Source.xml` . Bu bir uyarlaması uygulamasıdır. Daha sağlam bir uygulama, geçersiz bir belgeyi ayrıştırmaya hazırlanmalıdır.  
  
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

- [Gelişmiş LINQ to XML Programlama (Visual Basic)](advanced-linq-to-xml-programming.md)
