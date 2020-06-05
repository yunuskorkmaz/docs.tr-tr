---
title: 'Nasıl yapılır: XmlReader’dan XML Parçalarının Akışını Yapma'
ms.date: 07/20/2015
ms.assetid: f67ce598-4a12-4dcb-9a07-24deca02a111
ms.openlocfilehash: ff22625767c4e0752ca19d5a315395934b566230
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397706"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-visual-basic"></a>Nasıl yapılır: bir XmlReader 'dan XML parçalarını akışa alma (Visual Basic)
Büyük XML dosyalarını işlemek zorunda olduğunuzda, tüm XML ağacının belleğe yüklenmesi mümkün olmayabilir. Bu konuda, kullanarak parçaların nasıl akışının yapılacağı gösterilmektedir <xref:System.Xml.XmlReader> .  
  
 Nesneleri okumak için kullanmanın en etkili yöntemlerinden biri <xref:System.Xml.XmlReader> <xref:System.Xml.Linq.XElement> kendi özel eksen yönteminizi yazmaktır. Bir Axis yöntemi <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> , bu konudaki örnekte gösterildiği gibi genellikle gibi bir koleksiyon döndürür. Özel eksen yönteminde, yöntemini çağırarak XML parçasını oluşturduktan sonra <xref:System.Xml.Linq.XNode.ReadFrom%2A> , kullanarak koleksiyonu döndürün `yield return` . Bu, özel eksen yönteminiz için ertelenmiş yürütme semantiğini sağlar.  
  
 Nesnesinden bir XML ağacı oluşturduğunuzda, <xref:System.Xml.XmlReader> <xref:System.Xml.XmlReader> öğesinin bir öğe üzerinde konumlandırılmış olması gerekir. <xref:System.Xml.Linq.XNode.ReadFrom%2A>Yöntemi, öğenin kapanış etiketini okuuncaya kadar döndürmez.  
  
 Kısmi bir ağaç oluşturmak isterseniz, bir <xref:System.Xml.XmlReader> ağaca dönüştürmek istediğiniz düğümde okuyucuyu konumlandırabilirsiniz <xref:System.Xml.Linq.XElement> ve sonra nesneyi oluşturabilirsiniz. Bu, bir ağacı oluşturabilir <xref:System.Xml.Linq.XElement> .  
  
 [Nasıl yapılır: başlık bilgilerine erişimi olan XML parçalarını akışa alma (Visual Basic)](how-to-stream-xml-fragments-with-access-to-header-information.md) , daha karmaşık bir belgeyi akışa alma hakkında bilgi ve bir örnek içerir.  
  
 [Nasıl yapılır: büyük XML belgelerinin (Visual Basic) akış dönüşümünü gerçekleştirme](how-to-perform-streaming-transform-of-large-xml-documents.md) , küçük bir bellek parmak izini sağlarken çok büyük XML belgelerini dönüştürmek için LINQ to XML kullanmayla bir örnek içerir.  
  
## <a name="example"></a>Örnek  
 Bu örnek bir özel eksen yöntemi oluşturur. Bir LINQ sorgusu kullanarak bunu sorgulayabilirsiniz. Özel eksen yöntemi, bir `StreamRootChildDoc` yinelenen öğesi olan bir belgeyi okumak için özel olarak tasarlanan bir yöntemdir `Child` .  
  
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```console  
bbb  
ccc  
```  
  
 Bu örnekte, kaynak belge çok küçüktür. Ancak milyonlarca öğe olsa bile `Child` , bu örnekte küçük bir bellek ayak izine sahip olmaya devam edersiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: Visual Basic'de IEnumerable(Of T) Uygulama](../../language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md)
- [XML 'yi ayrıştırma (Visual Basic)](parsing-xml.md)
