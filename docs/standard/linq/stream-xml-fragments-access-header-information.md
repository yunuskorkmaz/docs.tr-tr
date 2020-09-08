---
title: Üst bilgi bilgilerine erişimi olan XML parçalarını akışa alma-LINQ to XML
description: XML parçalarını bir URI tarafından belirtilen dosyadan akıyan bir özel eksen yönteminin nasıl uygulanacağını ve kullanılacağını öğrenin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
ms.openlocfilehash: d50c29feb305341155257cd215e0292350689e7b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553254"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-linq-to-xml"></a><span data-ttu-id="39891-103">Üst bilgi bilgilerine erişimi olan XML parçalarını akışa alma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="39891-103">How to stream XML fragments with access to header information (LINQ to XML)</span></span>

<span data-ttu-id="39891-104">Bazen rastgele büyük XML dosyalarını okumanız ve uygulamanın bellek parmak izin tahmin edilebilir olması için uygulamanızı yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="39891-104">Sometimes you have to read arbitrarily large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="39891-105">Bir XML ağacını büyük bir XML dosyası ile doldurmayı denerseniz, bellek kullanımınız dosyanın boyutuyla orantılıdır; yani çok fazla.</span><span class="sxs-lookup"><span data-stu-id="39891-105">If you attempt to populate an XML tree with a large XML file, your memory usage will be proportional to the size of the file—that is, excessive.</span></span> <span data-ttu-id="39891-106">Bu nedenle, bunun yerine bir akış tekniği kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="39891-106">Therefore, you should use a streaming technique instead.</span></span>

<span data-ttu-id="39891-107">Bir seçenek, kullanarak uygulamanızı yazmaktır <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="39891-107">One option is to write your application using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="39891-108">Ancak, XML ağacını sorgulamak için LINQ kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="39891-108">However, you might want to use LINQ to query the XML tree.</span></span> <span data-ttu-id="39891-109">Varsa, kendi özel eksen yönteminizi yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="39891-109">If so, you can write your own custom axis method.</span></span> <span data-ttu-id="39891-110">Daha fazla bilgi için bkz. [LINQ to XML eksen yöntemi yazma](write-linq-xml-axis-method.md).</span><span class="sxs-lookup"><span data-stu-id="39891-110">For more information, see [How to write a LINQ to XML axis method](write-linq-xml-axis-method.md).</span></span>

<span data-ttu-id="39891-111">Kendi eksen yönteminizi yazmak için, <xref:System.Xml.XmlReader> ilgilendiğiniz düğümlerin birine ulaşana kadar düğümleri okumak için kullanan küçük bir yöntem yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="39891-111">To write your own axis method, you write a small method that uses the <xref:System.Xml.XmlReader> to read nodes until it reaches one of the nodes in which you're interested.</span></span> <span data-ttu-id="39891-112">Yöntemi, <xref:System.Xml.Linq.XNode.ReadFrom%2A> öğesinden okuyan <xref:System.Xml.XmlReader> ve bir XML parçasını örnekleyen öğesini çağırır.</span><span class="sxs-lookup"><span data-stu-id="39891-112">The method then calls <xref:System.Xml.Linq.XNode.ReadFrom%2A>, which reads from the <xref:System.Xml.XmlReader> and instantiates an XML fragment.</span></span> <span data-ttu-id="39891-113">Ardından, her parçayı aracılığıyla `yield return` özel eksen yönteminizi numaralandırma yöntemine verir.</span><span class="sxs-lookup"><span data-stu-id="39891-113">It then yields each fragment through `yield return` to the method that's enumerating your custom axis method.</span></span> <span data-ttu-id="39891-114">Daha sonra özel eksen yönteinizde LINQ sorguları yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="39891-114">You can then write LINQ queries on your custom axis method.</span></span>

<span data-ttu-id="39891-115">Akış teknikleri en iyi şekilde, kaynak belgeyi yalnızca bir kez işleyebilmeniz ve öğeleri belge düzeninde işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="39891-115">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="39891-116">Gibi belirli standart sorgu işleçleri, <xref:System.Linq.Enumerable.OrderBy%2A> kaynaklarını yineleyebilir, tüm verileri toplar, sıralar ve son olarak dizideki ilk öğeyi verir.</span><span class="sxs-lookup"><span data-stu-id="39891-116">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="39891-117">İlk öğeyi bırakmadan önce kaynağını üreten bir sorgu işleci kullanırsanız, küçük bir bellek parmak izini korumayacağız.</span><span class="sxs-lookup"><span data-stu-id="39891-117">If you use a query operator that materializes its source before yielding the first item, you won't retain a small memory footprint.</span></span>

## <a name="example-implement-and-use-a-custom-axis-method-that-streams-xml-fragments-from-the-file-specified-by-a-uri"></a><span data-ttu-id="39891-118">Örnek: bir URI tarafından belirtilen dosyadan XML parçalarını akıyan bir özel eksen yöntemi uygulayın ve kullanın</span><span class="sxs-lookup"><span data-stu-id="39891-118">Example: Implement and use a custom axis method that streams XML fragments from the file specified by a URI</span></span>

<span data-ttu-id="39891-119">Bazen sorun biraz daha ilginç olur.</span><span class="sxs-lookup"><span data-stu-id="39891-119">Sometimes the problem gets just a little more interesting.</span></span> <span data-ttu-id="39891-120">Aşağıdaki XML belgesinde, özel eksen yönteminizin tüketicisi, her öğenin ait olduğu müşterinin adını da bilmelidir.</span><span class="sxs-lookup"><span data-stu-id="39891-120">In the following XML document, the consumer of your custom axis method also has to know the name of the customer that each item belongs to.</span></span>

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

<span data-ttu-id="39891-121">Bu örnekte geçen yaklaşım ayrıca, bu üstbilgi bilgilerini izlemek, üst bilgi bilgilerini kaydetmek ve ardından hem başlık bilgilerini hem de numaralandırdığınız ayrıntıyı içeren küçük bir XML ağacı oluşturmanızı kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="39891-121">The approach that this example takes is to also watch for this header information, save the header information, and then build a small XML tree that contains both the header information and the detail that you're enumerating.</span></span> <span data-ttu-id="39891-122">Ardından Axis yöntemi bu yeni, küçük XML ağacını verir.</span><span class="sxs-lookup"><span data-stu-id="39891-122">The axis method then yields this new, small XML tree.</span></span> <span data-ttu-id="39891-123">Sorgu daha sonra başlık bilgilerine ve ayrıntı bilgilerine erişimi de vardır.</span><span class="sxs-lookup"><span data-stu-id="39891-123">The query then has access to the header information as well as the detail information.</span></span>

<span data-ttu-id="39891-124">Bu yaklaşımın küçük bir bellek ayak izi vardır.</span><span class="sxs-lookup"><span data-stu-id="39891-124">This approach has a small memory footprint.</span></span> <span data-ttu-id="39891-125">Her ayrıntı XML parçası, bir önceki parçaya hiçbir başvuru tutulmazsa ve çöp toplama için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="39891-125">As each detail XML fragment is yielded, no references are kept to the previous fragment, and it's available for garbage collection.</span></span> <span data-ttu-id="39891-126">Bu teknik yığın üzerinde birçok kısa süreli nesne oluşturur.</span><span class="sxs-lookup"><span data-stu-id="39891-126">This technique creates many short lived objects on the heap.</span></span>

<span data-ttu-id="39891-127">Aşağıdaki örnek, URI tarafından belirtilen dosyadan XML parçalarını akıyan bir özel eksen yönteminin nasıl uygulanacağını ve kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="39891-127">The following example shows how to implement and use a custom axis method that streams XML fragments from the file specified by the URI.</span></span> <span data-ttu-id="39891-128">Bu özel eksen,, ve öğelerinin bulunduğu bir belgeyi beklediğinden `Customer` `Name` `Item` ve bu öğelerin yukarıdaki belgede olarak düzenlenebilmesini sağlayacak şekilde yazılmıştır `Source.xml` .</span><span class="sxs-lookup"><span data-stu-id="39891-128">This custom axis is written such that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the above `Source.xml` document.</span></span> <span data-ttu-id="39891-129">Bu bir uyarlaması uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="39891-129">It's a simplistic implementation.</span></span> <span data-ttu-id="39891-130">Daha sağlam bir uygulama, geçersiz bir belgeyi ayrıştırmaya hazırlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="39891-130">A more robust implementation would be prepared to parse an invalid document.</span></span>

```csharp
static IEnumerable<XElement> StreamCustomerItem(string uri)
{
    using (XmlReader reader = XmlReader.Create(uri))
    {
        XElement name = null;
        XElement item = null;

        reader.MoveToContent();

        // Parse the file, save header information when encountered, and yield the
        // Item XElement objects as they're created.

        // loop through Customer elements
        while (reader.Read())
        {
            if (reader.NodeType == XmlNodeType.Element
                && reader.Name == "Customer")
            {
                // move to Name element
                while (reader.Read())
                {
                    if (reader.NodeType == XmlNodeType.Element &&
                        reader.Name == "Name")
                    {
                        name = XElement.ReadFrom(reader) as XElement;
                        break;
                    }
                }

                // Loop through Item elements
                while (reader.Read())
                {
                    if (reader.NodeType == XmlNodeType.EndElement)
                        break;
                    if (reader.NodeType == XmlNodeType.Element
                        && reader.Name == "Item")
                    {
                        item = XElement.ReadFrom(reader) as XElement;
                        if (item != null) {
                            XElement tempRoot = new XElement("Root",
                                new XElement(name)
                            );
                            tempRoot.Add(item);
                            yield return item;
                        }
                    }
                }
            }
        }
    }
}

static void Main(string[] args)
{
    XElement xmlTree = new XElement("Root",
        from el in StreamCustomerItem("Source.xml")
        where (int)el.Element("Key") >= 3 && (int)el.Element("Key") <= 7
        select new XElement("Item",
            new XElement("Customer", (string)el.Parent.Element("Name")),
            new XElement(el.Element("Key"))
        )
    );
    Console.WriteLine(xmlTree);
}
```

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

 <span data-ttu-id="39891-131">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="39891-131">This code produces the following output:</span></span>

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
