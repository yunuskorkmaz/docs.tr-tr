---
title: 'Nasıl yapılır: (C#) XML ağacının şeklini dönüştürme'
ms.date: 07/20/2015
ms.assetid: 93c5d426-dea2-4709-a991-60204de42e8f
ms.openlocfilehash: 6bfa3e14694ce421dc349dc4449ae231c4628b79
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514886"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-c"></a><span data-ttu-id="00a9e-102">Nasıl yapılır: (C#) XML ağacının şeklini dönüştürme</span><span class="sxs-lookup"><span data-stu-id="00a9e-102">How to: Transform the Shape of an XML Tree (C#)</span></span>
<span data-ttu-id="00a9e-103">*Şekli* alt öğe adları, öznitelik adları ve özellikleri, hiyerarşinin bir XML'sini belge başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="00a9e-103">The *shape* of an XML document refers to its element names, attribute names, and the characteristics of its hierarchy.</span></span>  
  
 <span data-ttu-id="00a9e-104">Bazen, bir XML belgesi şeklini değiştirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="00a9e-104">Sometimes you will have to change the shape of an XML document.</span></span> <span data-ttu-id="00a9e-105">Örneğin, var olan bir XML belgesi farklı öğe ve öznitelik adları gerektiren başka bir sisteme gönderme gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="00a9e-105">For example, you might have to send an existing XML document to another system that requires different element and attribute names.</span></span> <span data-ttu-id="00a9e-106">Belgede, silme ve gerekli, ancak kullanarak işlevsel oluşturma sonuçları daha okunabilir ve sürdürülebilir kod öğeleri yeniden adlandırma gidilemedi.</span><span class="sxs-lookup"><span data-stu-id="00a9e-106">You could go through the document, deleting and renaming elements as required, but using functional construction results in more readable and maintainable code.</span></span> <span data-ttu-id="00a9e-107">İşlevsel oluşturma hakkında daha fazla bilgi için bkz: [işlevsel oluşturma (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="00a9e-107">For more information about functional construction, see [Functional Construction (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="00a9e-108">İlk örnek, XML belgesi kuruluş değiştirir.</span><span class="sxs-lookup"><span data-stu-id="00a9e-108">The first example changes the organization of the XML document.</span></span> <span data-ttu-id="00a9e-109">Bu karmaşık öğe ağacında bir konumdan diğerine taşır.</span><span class="sxs-lookup"><span data-stu-id="00a9e-109">It moves complex elements from one location in the tree to another.</span></span>  
  
 <span data-ttu-id="00a9e-110">Bu konudaki ikinci örnek, kaynak belgedeki daha farklı bir şekilde bir XML belgesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="00a9e-110">The second example in this topic creates an XML document with a different shape than the source document.</span></span> <span data-ttu-id="00a9e-111">Öğe adları büyük küçük harfleri değiştirir, bazı öğelerin yeniden adlandırır ve bazı öğeleri kaynak ağaç dönüştürülmüş ağaç dışında bırakır.</span><span class="sxs-lookup"><span data-stu-id="00a9e-111">It changes the casing of the element names, renames some elements, and leaves some elements from the source tree out of the transformed tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00a9e-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="00a9e-112">Example</span></span>  
 <span data-ttu-id="00a9e-113">Aşağıdaki kod, katıştırılmış sorgu ifadeleri kullanarak bir XML dosyası şeklini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="00a9e-113">The following code changes the shape of an XML file using embedded query expressions.</span></span>  
  
 <span data-ttu-id="00a9e-114">Bu örnekte kaynak XML belgesinde içeren bir `Customers` öğesi altında `Root` tüm müşteriler içeren öğe.</span><span class="sxs-lookup"><span data-stu-id="00a9e-114">The source XML document in this example contains a `Customers` element under the `Root` element that contains all customers.</span></span> <span data-ttu-id="00a9e-115">Ayrıca içerdiği bir `Orders` öğesi altında `Root` tüm siparişleri içeren öğe.</span><span class="sxs-lookup"><span data-stu-id="00a9e-115">It also contains an `Orders` element under the `Root` element that contains all orders.</span></span> <span data-ttu-id="00a9e-116">Bu örnekte, her bir müşterinin siparişlerini içerdiği yeni bir XML ağacı oluşturur bir `Orders` öğesiyle `Customer` öğesi.</span><span class="sxs-lookup"><span data-stu-id="00a9e-116">This example creates a new XML tree in which the orders for each customer are contained in an `Orders` element within the `Customer` element.</span></span> <span data-ttu-id="00a9e-117">Özgün belgeyi de içeren bir `CustomerID` öğesinde `Order` öğesi; yeniden şekillendirilmiş belgeden kaldırılması bu öğe olacaktır.</span><span class="sxs-lookup"><span data-stu-id="00a9e-117">The original document also contains a `CustomerID` element in the `Order` element; this element will be removed from the re-shaped document.</span></span>  
  
 <span data-ttu-id="00a9e-118">Bu örnekte aşağıdaki XML belgesi: [örnek XML dosyası: müşteriler ve siparişler (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="00a9e-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
XElement co = XElement.Load("CustomersOrders.xml");  
XElement newCustOrd =  
    new XElement("Root",  
        from cust in co.Element("Customers").Elements("Customer")  
        select new XElement("Customer",  
            cust.Attributes(),  
            cust.Elements(),  
            new XElement("Orders",  
                from ord in co.Element("Orders").Elements("Order")  
                where (string)ord.Element("CustomerID") == (string)cust.Attribute("CustomerID")  
                select new XElement("Order",  
                    ord.Attributes(),  
                    ord.Element("EmployeeID"),  
                    ord.Element("OrderDate"),  
                    ord.Element("RequiredDate"),  
                    ord.Element("ShipInfo")  
                )  
            )  
        )  
    );  
Console.WriteLine(newCustOrd);  
```  
  
 <span data-ttu-id="00a9e-119">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="00a9e-119">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Customer CustomerID="GREAL">  
    <CompanyName>Great Lakes Food Market</CompanyName>  
    <ContactName>Howard Snyder</ContactName>  
    <ContactTitle>Marketing Manager</ContactTitle>  
    <Phone>(503) 555-7555</Phone>  
    <FullAddress>  
      <Address>2732 Baker Blvd.</Address>  
      <City>Eugene</City>  
      <Region>OR</Region>  
      <PostalCode>97403</PostalCode>  
      <Country>USA</Country>  
    </FullAddress>  
    <Orders />  
  </Customer>  
  <Customer CustomerID="HUNGC">  
    <CompanyName>Hungry Coyote Import Store</CompanyName>  
    <ContactName>Yoshi Latimer</ContactName>  
    <ContactTitle>Sales Representative</ContactTitle>  
    <Phone>(503) 555-6874</Phone>  
    <Fax>(503) 555-2376</Fax>  
    <FullAddress>  
      <Address>City Center Plaza 516 Main St.</Address>  
      <City>Elgin</City>  
      <Region>OR</Region>  
      <PostalCode>97827</PostalCode>  
      <Country>USA</Country>  
    </FullAddress>  
    <Orders />  
  </Customer>  
  . . .  
```  
  
## <a name="example"></a><span data-ttu-id="00a9e-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="00a9e-120">Example</span></span>  
 <span data-ttu-id="00a9e-121">Bu örnek, bazı öğelerin yeniden adlandırır ve bazı öznitelikler öğesine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="00a9e-121">This example renames some elements and converts some attributes to elements.</span></span>  
  
 <span data-ttu-id="00a9e-122">Kod çağrıları `ConvertAddress`, listesini döndürür <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="00a9e-122">The code calls `ConvertAddress`, which returns a list of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="00a9e-123">Yöntem bağımsız değişkeninin belirleyen bir sorgudur `Address` karmaşık bir öğe olduğu `Type` öznitelik değerine sahip `"Shipping"`.</span><span class="sxs-lookup"><span data-stu-id="00a9e-123">The argument to the method is a query that determines the `Address` complex element where the `Type` attribute has a value of `"Shipping"`.</span></span>  
  
 <span data-ttu-id="00a9e-124">Bu örnekte aşağıdaki XML belgesi: [örnek XML dosyası: tipik satın alma siparişi (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="00a9e-124">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
static IEnumerable<XElement> ConvertAddress(XElement add)  
{  
    List<XElement> fragment = new List<XElement>() {  
        new XElement("NAME", (string)add.Element("Name")),  
        new XElement("STREET", (string)add.Element("Street")),  
        new XElement("CITY", (string)add.Element("City")),  
        new XElement("ST", (string)add.Element("State")),  
        new XElement("POSTALCODE", (string)add.Element("Zip")),  
        new XElement("COUNTRY", (string)add.Element("Country"))  
    };  
    return fragment;  
}  
  
static void Main(string[] args)  
{  
    XElement po = XElement.Load("PurchaseOrder.xml");  
    XElement newPo = new XElement("PO",  
        new XElement("ID", (string)po.Attribute("PurchaseOrderNumber")),  
        new XElement("DATE", (DateTime)po.Attribute("OrderDate")),  
        ConvertAddress(  
            (from el in po.Elements("Address")  
            where (string)el.Attribute("Type") == "Shipping"  
            select el)  
            .First()  
        )  
    );  
    Console.WriteLine(newPo);  
}  
```  
  
 <span data-ttu-id="00a9e-125">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="00a9e-125">This code produces the following output:</span></span>  
  
```xml  
<PO>  
  <ID>99503</ID>  
  <DATE>1999-10-20T00:00:00</DATE>  
  <NAME>Ellen Adams</NAME>  
  <STREET>123 Maple Street</STREET>  
  <CITY>Mill Valley</CITY>  
  <ST>CA</ST>  
  <POSTALCODE>10999</POSTALCODE>  
  <COUNTRY>USA</COUNTRY>  
</PO>  
```  
  
## <a name="see-also"></a><span data-ttu-id="00a9e-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="00a9e-126">See Also</span></span>

- [<span data-ttu-id="00a9e-127">Projeksiyonlar ve Dönüşümler (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="00a9e-127">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
