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
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-visual-basic"></a>Nasıl yapılır: akış parçalarını gelen XmlReader (Visual Basic)
Büyük XML dosyalarını işlemek varsa, XML ağacın tamamı belleğe yüklemek için uygun olmayabilir. Bu konuda kullanarak parçaları akışı gösterilmektedir bir <xref:System.Xml.XmlReader>.  
  
 Kullanmak için en etkili yollarından biri, bir <xref:System.Xml.XmlReader> okumak için <xref:System.Xml.Linq.XElement> nesnedir kendi özel eksen yöntemi yazmak için. Bir eksen yöntemi bir koleksiyon gibi tipik döndürür <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement>, bu konuda örnekte gösterildiği gibi. Özel eksen yönteminde çağırarak XML parçası oluşturduktan sonra <xref:System.Xml.Linq.XNode.ReadFrom%2A> yöntemi kullanarak koleksiyon döndürmek `yield return`. Bu, özel eksen yönteminize ertelenmiş yürütme semantiği sağlar.  
  
 Bir XML ağacından oluşturduğunuzda bir <xref:System.Xml.XmlReader> nesnesi <xref:System.Xml.XmlReader> bir öğede konumlandırılmalıdır. <xref:System.Xml.Linq.XNode.ReadFrom%2A> Yöntemi öğenin kapatma etiketi okudu kadar döndürmez.  
  
 Kısmi bir ağaç oluşturmak istiyorsanız, örneği oluşturmak bir <xref:System.Xml.XmlReader>, dönüştürmek istediğiniz düğüme okuyucu getirin bir <xref:System.Xml.Linq.XElement> ağacı ve ardından oluşturun <xref:System.Xml.Linq.XElement> nesnesi.  
  
 Konu [nasıl yapılır: akışı XML parçaları üst bilgileri (Visual Basic) erişimi](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) bilgi ve daha karmaşık bir belge akış konusunda bir örnek içerir.  
  
 Konu [nasıl yapılır: gerçekleştirmek akış dönüştürme, büyük XML belgeleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) küçük bellek alanını korurken son derece büyük XML belgelerini dönüştürmek için LINQ-XML kullanarak bir örnek içerir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir özel eksen yöntemi oluşturur. Kullanarak sorgulama yapabilirsiniz bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu. Özel eksen yöntemi `StreamRootChildDoc`, özellikle yinelenen olan bir belgeyi okumak için tasarlanmış bir yöntemle `Child` öğesi.  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```  
bbb  
ccc  
```  
  
 Bu örnekte, kaynak belge çok küçük. Ancak, milyonlarca olsa bile `Child` öğeleri, bu örnekte küçük bellek alanını hala sahip olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: Visual Basic'te IEnumerable(Of T) uygulama](../../../../visual-basic/programming-guide/language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md)  
 [Ayrıştırma XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
