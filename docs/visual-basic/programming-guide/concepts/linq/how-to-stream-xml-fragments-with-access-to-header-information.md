---
title: "Nasıl yapılır: XML parçaları üst bilgileri (Visual Basic) erişim akışı"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: effd10df-87c4-4d7a-8a9a-1434d829dca5
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f745d0725b9b05620b4b967e51b452e54fe5e6d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-visual-basic"></a>Nasıl yapılır: XML parçaları üst bilgileri (Visual Basic) erişim akışı
Bazen büyük XML dosyaları okuma ve böylece uygulamanın bellek alanını tahmin edilebilir uygulamanızı yazma gerekir. Bir XML ağaç içeren büyük bir XML dosyası doldurmak çalışırsanız, bellek kullanımı dosyasının boyutunu orantılı — diğer bir deyişle, aşırı. Bu nedenle, bir akış teknik yerine kullanmanız gerekir.  
  
 Bir seçenektir kullanarak uygulamanızı yazmak için <xref:System.Xml.XmlReader>. Ancak, kullanmak isteyebilirsiniz [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] XML ağaç sorgulanamıyor. Bu durumda, kendi özel eksen yöntemi yazabilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: XML eksen yöntemi (Visual Basic) için bir LINQ yazma](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).  
  
 Kendi eksen yöntemi yazmak için kullandığı küçük bir yöntem yazmak <xref:System.Xml.XmlReader> içinde ilgi düğümlerinden biri ulaşana kadar düğümleri okumak için. Daha sonra yöntemi çağırır <xref:System.Xml.Linq.XNode.ReadFrom%2A>, olarak okuyan <xref:System.Xml.XmlReader> ve bir XML parçası başlatır. Ardından, özel eksen yöntemi LINQ sorgularını yazabilirsiniz.  
  
 Akış teknikleri en iyi kaynak belge yalnızca bir kez işlem gerekir ve belge sırayla öğeleri işleyebilmesi için durumlarda uygulanır. Belirli standart sorgu işleçleri gibi <xref:System.Linq.Enumerable.OrderBy%2A>kendi kaynak yinelemek, tüm verileri toplamak, sıralanmasını ve son olarak dizinin ilk öğesi verim. İlk öğe sağlayan önce kaynağı gerçeğe bir sorgu işleci kullanırsanız, bir küçük bellek alanını bulamayacaktır unutmayın.  
  
## <a name="example"></a>Örnek  
 Bazen biraz daha fazla ilginç sorun alır. Aşağıdaki XML belgesinde özel eksen yönteminizi tüketici ayrıca her öğenin ait olduğu müşterinin adını bilmesi gerekir.  
  
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
  
 Bu örnek alan aynı zamanda bu başlık bilgilerini izleme, üst bilgileri kaydedin ve üst bilgileri ve numaralandırma ayrıntı içeren küçük bir XML ağaç yapı yaklaşımdır. Eksen yöntemi, daha sonra bu yeni, küçük XML ağaç verir. Sorgu daha sonra ayrıntılı bilgilerin yanı sıra üst bilgileri erişebilir.  
  
 Bu yaklaşımın küçük bellek kaplama alanı vardır. Her ayrıntı XML parçası verdiğini gibi başvuru önceki parça tutulur ve atık toplama için kullanılabilir. Bu teknik öbek üzerinde birçok kısa süreli nesne oluşturduğuna dikkat edin.  
  
 Aşağıdaki örnek XML parçaları URI tarafından belirtilen dosyadan akışları özel eksen yöntemi uygulamak ve nasıl kullanılacağını gösterir. Bu özel eksen özellikle sahip bir belge bekliyor gibi yazılır `Customer`, `Name`, ve `Item` öğeleri ve bu öğeleri yukarıdaki olduğu gibi düzenlenmesini, `Source.xml` belge. Bu simplistic bir uygulamasıdır. Geçersiz bir belge ayrıştırmak için daha sağlam bir uygulama hazırlanması.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gelişmiş LINQ-XML programlama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
