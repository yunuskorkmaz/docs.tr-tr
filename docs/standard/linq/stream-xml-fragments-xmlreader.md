---
title: Bir XmlReader LINQ to XML XML parçalarını akışa alma
description: C# ve Visual Basic özel bir eksen yöntemi kullanarak bir XmlReader 'dan XML parçaları akışla aktarabilirsiniz. Bu, tüm XML ağacının belleğe yüklenmesi uygun olmadığında çalışauygulanabilecek bir yaklaşımdır.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: e3a7a6260c66f0295216552c6aa56f71a8536bdf
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553046"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-linq-to-xml"></a>Bir XmlReader 'dan XML parçalarını akışa alma (LINQ to XML)

Büyük XML dosyalarını işlemek zorunda olduğunuzda, tüm XML ağacının belleğe yüklenmesi mümkün olmayabilir. Bu makalede <xref:System.Xml.XmlReader> , C# ve Visual Basic parçaları kullanılarak parçaların nasıl akışının yapılacağı gösterilmektedir.

Nesneleri okumak için kullanmanın en etkili yöntemlerinden biri <xref:System.Xml.XmlReader> <xref:System.Xml.Linq.XElement> kendi özel eksen yönteminizi yazmaktır. Bir Axis yöntemi <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> , bu makaledeki örnekte gösterildiği gibi genellikle gibi bir koleksiyon döndürür. Özel eksen yönteminde, yöntemini çağırarak XML parçasını oluşturduktan sonra <xref:System.Xml.Linq.XNode.ReadFrom%2A> , kullanarak koleksiyonu döndürün `yield return` . Bu, özel eksen yönteminiz için ertelenmiş yürütme semantiğini sağlar.

Nesnesinden bir XML ağacı oluşturduğunuzda, <xref:System.Xml.XmlReader> <xref:System.Xml.XmlReader> öğesinin bir öğe üzerinde konumlandırılmış olması gerekir. <xref:System.Xml.Linq.XNode.ReadFrom%2A>Yöntemi, öğenin kapanış etiketini okuuncaya kadar döndürmez.

Kısmi bir ağaç oluşturmak isterseniz, bir <xref:System.Xml.XmlReader> ağaca dönüştürmek istediğiniz düğümde okuyucuyu konumlandırabilirsiniz <xref:System.Xml.Linq.XElement> ve sonra nesneyi oluşturabilirsiniz. Bu, bir ağacı oluşturabilir <xref:System.Xml.Linq.XElement> .

Üst bilgi [bilgilerine erişimi olan XML parçalarını akışa](stream-xml-fragments-access-header-information.md) alma makalesi, daha karmaşık bir belgeyi akışa alma hakkında bilgi içerir.

[Büyük XML belgelerinin akış dönüşümünü gerçekleştirme](perform-streaming-transform-large-xml-documents.md) makalesi, küçük bir bellek parmak İZLİĞİ sağlarken çok büyük XML belgelerini dönüştürmek için LINQ to XML kullanma örneği içerir.

## <a name="example-create-a-custom-axis-method"></a>Örnek: özel bir eksen yöntemi oluştur

Bu örnek bir özel eksen yöntemi oluşturur. Bir LINQ sorgusu kullanarak bunu sorgulayabilirsiniz. Özel eksen yöntemi, `StreamRootChildDoc` yinelenen bir öğesi olan bir belgeyi okuyabilir `Child` .

```csharp
static IEnumerable<XElement> StreamRootChildDoc(StringReader stringReader)
{
    using (XmlReader reader = XmlReader.Create(stringReader))
    {
        reader.MoveToContent();
        // Parse the file and display each of the nodes.
        while (reader.Read())
        {
            switch (reader.NodeType)
            {
                case XmlNodeType.Element:
                    if (reader.Name == "Child") {
                        XElement el = XElement.ReadFrom(reader) as XElement;
                        if (el != null)
                            yield return el;
                    }
                    break;
            }
        }
    }
}

static void Main(string[] args)
{
    string markup = @"<Root>
      <Child Key=""01"">
        <GrandChild>aaa</GrandChild>
      </Child>
      <Child Key=""02"">
        <GrandChild>bbb</GrandChild>
      </Child>
      <Child Key=""03"">
        <GrandChild>ccc</GrandChild>
      </Child>
    </Root>";

    IEnumerable<string> grandChildData =
        from el in StreamRootChildDoc(new StringReader(markup))
        where (int)el.Attribute("Key") > 1
        select (string)el.Element("GrandChild");

    foreach (string str in grandChildData) {
        Console.WriteLine(str);
    }
}
```

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

```output
bbb
ccc
```

Bu örnekte kullanılan teknik, milyonlarca öğe için bile küçük bir bellek parmak izini saklar `Child` .

## <a name="see-also"></a>Ayrıca bkz.

- [XML 'yi Ayrıştır](parse-string.md)
