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
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-linq-to-xml"></a><span data-ttu-id="2fc9d-104">Bir XmlReader 'dan XML parçalarını akışa alma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="2fc9d-104">How to stream XML fragments from an XmlReader (LINQ to XML)</span></span>

<span data-ttu-id="2fc9d-105">Büyük XML dosyalarını işlemek zorunda olduğunuzda, tüm XML ağacının belleğe yüklenmesi mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="2fc9d-105">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="2fc9d-106">Bu makalede <xref:System.Xml.XmlReader> , C# ve Visual Basic parçaları kullanılarak parçaların nasıl akışının yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2fc9d-106">This article shows how to stream fragments using an <xref:System.Xml.XmlReader> in C# and Visual Basic.</span></span>

<span data-ttu-id="2fc9d-107">Nesneleri okumak için kullanmanın en etkili yöntemlerinden biri <xref:System.Xml.XmlReader> <xref:System.Xml.Linq.XElement> kendi özel eksen yönteminizi yazmaktır.</span><span class="sxs-lookup"><span data-stu-id="2fc9d-107">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="2fc9d-108">Bir Axis yöntemi <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> , bu makaledeki örnekte gösterildiği gibi genellikle gibi bir koleksiyon döndürür.</span><span class="sxs-lookup"><span data-stu-id="2fc9d-108">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this article.</span></span> <span data-ttu-id="2fc9d-109">Özel eksen yönteminde, yöntemini çağırarak XML parçasını oluşturduktan sonra <xref:System.Xml.Linq.XNode.ReadFrom%2A> , kullanarak koleksiyonu döndürün `yield return` .</span><span class="sxs-lookup"><span data-stu-id="2fc9d-109">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="2fc9d-110">Bu, özel eksen yönteminiz için ertelenmiş yürütme semantiğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="2fc9d-110">This provides deferred execution semantics to your custom axis method.</span></span>

<span data-ttu-id="2fc9d-111">Nesnesinden bir XML ağacı oluşturduğunuzda, <xref:System.Xml.XmlReader> <xref:System.Xml.XmlReader> öğesinin bir öğe üzerinde konumlandırılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2fc9d-111">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="2fc9d-112"><xref:System.Xml.Linq.XNode.ReadFrom%2A>Yöntemi, öğenin kapanış etiketini okuuncaya kadar döndürmez.</span><span class="sxs-lookup"><span data-stu-id="2fc9d-112">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method doesn't return until it has read the close tag of the element.</span></span>

<span data-ttu-id="2fc9d-113">Kısmi bir ağaç oluşturmak isterseniz, bir <xref:System.Xml.XmlReader> ağaca dönüştürmek istediğiniz düğümde okuyucuyu konumlandırabilirsiniz <xref:System.Xml.Linq.XElement> ve sonra nesneyi oluşturabilirsiniz. Bu, bir ağacı oluşturabilir <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="2fc9d-113">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>

<span data-ttu-id="2fc9d-114">Üst bilgi [bilgilerine erişimi olan XML parçalarını akışa](stream-xml-fragments-access-header-information.md) alma makalesi, daha karmaşık bir belgeyi akışa alma hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="2fc9d-114">The article [How to stream XML fragments with access to header information](stream-xml-fragments-access-header-information.md) contains information on streaming a more complex document.</span></span>

<span data-ttu-id="2fc9d-115">[Büyük XML belgelerinin akış dönüşümünü gerçekleştirme](perform-streaming-transform-large-xml-documents.md) makalesi, küçük bir bellek parmak İZLİĞİ sağlarken çok büyük XML belgelerini dönüştürmek için LINQ to XML kullanma örneği içerir.</span><span class="sxs-lookup"><span data-stu-id="2fc9d-115">The article [How to perform streaming transform of large XML documents](perform-streaming-transform-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>

## <a name="example-create-a-custom-axis-method"></a><span data-ttu-id="2fc9d-116">Örnek: özel bir eksen yöntemi oluştur</span><span class="sxs-lookup"><span data-stu-id="2fc9d-116">Example: Create a custom axis method</span></span>

<span data-ttu-id="2fc9d-117">Bu örnek bir özel eksen yöntemi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2fc9d-117">This example creates a custom axis method.</span></span> <span data-ttu-id="2fc9d-118">Bir LINQ sorgusu kullanarak bunu sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2fc9d-118">You can query it by using a LINQ query.</span></span> <span data-ttu-id="2fc9d-119">Özel eksen yöntemi, `StreamRootChildDoc` yinelenen bir öğesi olan bir belgeyi okuyabilir `Child` .</span><span class="sxs-lookup"><span data-stu-id="2fc9d-119">The custom axis method `StreamRootChildDoc` can read a document that has a repeating `Child` element.</span></span>

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

<span data-ttu-id="2fc9d-120">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="2fc9d-120">This example produces the following output:</span></span>

```output
bbb
ccc
```

<span data-ttu-id="2fc9d-121">Bu örnekte kullanılan teknik, milyonlarca öğe için bile küçük bir bellek parmak izini saklar `Child` .</span><span class="sxs-lookup"><span data-stu-id="2fc9d-121">The technique used in this example maintains a small memory footprint even for millions of `Child` elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="2fc9d-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2fc9d-122">See also</span></span>

- [<span data-ttu-id="2fc9d-123">XML 'yi Ayrıştır</span><span class="sxs-lookup"><span data-stu-id="2fc9d-123">Parse XML</span></span>](parse-string.md)
