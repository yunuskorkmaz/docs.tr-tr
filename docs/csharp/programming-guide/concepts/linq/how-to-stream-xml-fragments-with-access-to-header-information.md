---
title: Üstbilgi bilgilerine erişim (C#) ile XML parçaları akışı nasıl
ms.date: 07/20/2015
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
ms.openlocfilehash: 5bc10bcadae0e33ee63f953608ca841d44dd6527
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712396"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-c"></a><span data-ttu-id="f459e-102">Üstbilgi bilgilerine erişim (C#) ile XML parçaları akışı nasıl</span><span class="sxs-lookup"><span data-stu-id="f459e-102">How to stream XML fragments with access to header information (C#)</span></span>
<span data-ttu-id="f459e-103">Bazen rasgele büyük XML dosyaları okumak ve uygulamanın bellek ayak izi öngörülebilir böylece uygulama yazmak zorunda.</span><span class="sxs-lookup"><span data-stu-id="f459e-103">Sometimes you have to read arbitrarily large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="f459e-104">Bir XML ağacını büyük bir XML dosyasıyla doldurmaya çalışırsanız, bellek kullanımınız dosyanın boyutuyla orantılı olacaktır, yani aşırı.</span><span class="sxs-lookup"><span data-stu-id="f459e-104">If you attempt to populate an XML tree with a large XML file, your memory usage will be proportional to the size of the file—that is, excessive.</span></span> <span data-ttu-id="f459e-105">Bu nedenle, bunun yerine bir akış tekniği kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f459e-105">Therefore, you should use a streaming technique instead.</span></span>  
  
<span data-ttu-id="f459e-106">Bir seçenek kullanarak <xref:System.Xml.XmlReader>uygulamanızı yazmaktır.</span><span class="sxs-lookup"><span data-stu-id="f459e-106">One option is to write your application using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="f459e-107">Ancak, XML ağacını sorgulamak için LINQ'yi kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f459e-107">However, you might want to use LINQ to query the XML tree.</span></span> <span data-ttu-id="f459e-108">Bu durumda, kendi özel eksen yönteminizi yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f459e-108">If this is the case, you can write your own custom axis method.</span></span> <span data-ttu-id="f459e-109">Daha fazla bilgi için, [XML ekseni yöntemine (C#) linq nasıl yazılır.](./how-to-write-a-linq-to-xml-axis-method.md)</span><span class="sxs-lookup"><span data-stu-id="f459e-109">For more information, see [How to write a LINQ to XML axis method (C#)](./how-to-write-a-linq-to-xml-axis-method.md).</span></span>
  
 <span data-ttu-id="f459e-110">Kendi eksen yönteminizi yazmak için, ilgilendiğiniz <xref:System.Xml.XmlReader> düğümlerden birine ulaşana kadar düğümleri okumak için kullanan küçük bir yöntem yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="f459e-110">To write your own axis method, you write a small method that uses the <xref:System.Xml.XmlReader> to read nodes until it reaches one of the nodes in which you are interested.</span></span> <span data-ttu-id="f459e-111">Yöntem daha <xref:System.Xml.Linq.XNode.ReadFrom%2A>sonra çağırır , <xref:System.Xml.XmlReader> hangi okur ve bir XML parçası anlık.</span><span class="sxs-lookup"><span data-stu-id="f459e-111">The method then calls <xref:System.Xml.Linq.XNode.ReadFrom%2A>, which reads from the <xref:System.Xml.XmlReader> and instantiates an XML fragment.</span></span> <span data-ttu-id="f459e-112">Daha sonra her parçayı özel eksen yönteminizi sayısallaştırıyor `yield return` yönteminize verir.</span><span class="sxs-lookup"><span data-stu-id="f459e-112">It then yields each fragment through `yield return` to the method that is enumerating your custom axis method.</span></span> <span data-ttu-id="f459e-113">Daha sonra özel eksen yönteminize LINQ sorguları yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f459e-113">You can then write LINQ queries on your custom axis method.</span></span>  
  
 <span data-ttu-id="f459e-114">Akış teknikleri en iyi kaynak belgeyi yalnızca bir kez işlemeniz gereken durumlarda uygulanır ve öğeleri belge sırasına göre işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f459e-114">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="f459e-115">Kaynaklarını yineleyin, <xref:System.Linq.Enumerable.OrderBy%2A>tüm verileri toplar, sıralar ve ardından son olarak dizideki ilk öğeyi verir.</span><span class="sxs-lookup"><span data-stu-id="f459e-115">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="f459e-116">İlk öğeyi vermeden önce kaynağını somutlaştıran bir sorgu işleci kullanırsanız, küçük bir bellek ayak izini saklamazsınız.</span><span class="sxs-lookup"><span data-stu-id="f459e-116">If you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f459e-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="f459e-117">Example</span></span>  

<span data-ttu-id="f459e-118">Bazen sorun biraz daha ilginç oluyor.</span><span class="sxs-lookup"><span data-stu-id="f459e-118">Sometimes the problem gets just a little more interesting.</span></span> <span data-ttu-id="f459e-119">Aşağıdaki XML belgesinde, özel eksen yönteminizin tüketicisinin de her öğenin ait olduğu müşterinin adını bilmesi gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="f459e-119">In the following XML document, the consumer of your custom axis method also has to know the name of the customer that each item belongs to.</span></span>  
  
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
  
 <span data-ttu-id="f459e-120">Bu örnekte aldığı yaklaşım, bu üstbilgi bilgilerini izlemek, üstbilgi bilgilerini kaydetmek ve sonra hem üstbilgi hem de sayısalbilgilerinizi içeren küçük bir XML ağacı oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="f459e-120">The approach that this example takes is to also watch for this header information, save the header information, and then build a small XML tree that contains both the header information and the detail that you are enumerating.</span></span> <span data-ttu-id="f459e-121">Eksen yöntemi daha sonra bu yeni, küçük XML ağacı verir.</span><span class="sxs-lookup"><span data-stu-id="f459e-121">The axis method then yields this new, small XML tree.</span></span> <span data-ttu-id="f459e-122">Sorgu daha sonra üstbilgi bilgilerinin yanı sıra ayrıntı bilgilerine de erişebilir.</span><span class="sxs-lookup"><span data-stu-id="f459e-122">The query then has access to the header information as well as the detail information.</span></span>  
  
 <span data-ttu-id="f459e-123">Bu yaklaşım küçük bir bellek ayak izi vardır.</span><span class="sxs-lookup"><span data-stu-id="f459e-123">This approach has a small memory footprint.</span></span> <span data-ttu-id="f459e-124">Her ayrıntı XML parçası verim olarak, önceki parçaya hiçbir başvuru tutulur ve çöp toplama için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f459e-124">As each detail XML fragment is yielded, no references are kept to the previous fragment, and it is available for garbage collection.</span></span> <span data-ttu-id="f459e-125">Bu teknik yığın üzerinde birçok kısa ömürlü nesneler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f459e-125">This technique creates many short lived objects on the heap.</span></span>  
  
 <span data-ttu-id="f459e-126">Aşağıdaki örnek, URI tarafından belirtilen dosyadan XML parçalarını aktaran özel bir eksen yönteminin nasıl uygulanacağını ve kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f459e-126">The following example shows how to implement and use a custom axis method that streams XML fragments from the file specified by the URI.</span></span> <span data-ttu-id="f459e-127">Bu `Customer`özel eksen, , , ve `Name` `Item` öğeleri olan bir belge bekliyor ve bu öğeleri `Source.xml` yukarıdaki belgede olduğu gibi düzenlenecek şekilde yazılır.</span><span class="sxs-lookup"><span data-stu-id="f459e-127">This custom axis is written such that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the above `Source.xml` document.</span></span> <span data-ttu-id="f459e-128">Bu basit bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="f459e-128">It is a simplistic implementation.</span></span> <span data-ttu-id="f459e-129">Geçersiz bir belgeyi ayrıştırmak için daha sağlam bir uygulama hazırlanacak.</span><span class="sxs-lookup"><span data-stu-id="f459e-129">A more robust implementation would be prepared to parse an invalid document.</span></span>  
  
```csharp  
static IEnumerable<XElement> StreamCustomerItem(string uri)  
{  
    using (XmlReader reader = XmlReader.Create(uri))  
    {  
        XElement name = null;  
        XElement item = null;  
  
        reader.MoveToContent();  
  
        // Parse the file, save header information when encountered, and yield the  
        // Item XElement objects as they are created.  
  
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
  
                // loop through Item elements  
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
  
 <span data-ttu-id="f459e-130">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="f459e-130">This code produces the following output:</span></span>  
  
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
