---
title: 'Nasıl yapılır: bir XML ağacının (C#) şekil Dönüştür'
ms.date: 07/20/2015
ms.assetid: 93c5d426-dea2-4709-a991-60204de42e8f
ms.openlocfilehash: 2c1f5728781a89caa813c2e3cbd822ae711a77e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33326111"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-c"></a><span data-ttu-id="c9a83-102">Nasıl yapılır: bir XML ağacının (C#) şekil Dönüştür</span><span class="sxs-lookup"><span data-stu-id="c9a83-102">How to: Transform the Shape of an XML Tree (C#)</span></span>
<span data-ttu-id="c9a83-103">*Şekli* bir XML belgesi öğe adları, öznitelik adları ve özellikleri, hiyerarşinin başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="c9a83-103">The *shape* of an XML document refers to its element names, attribute names, and the characteristics of its hierarchy.</span></span>  
  
 <span data-ttu-id="c9a83-104">Bazen, bir XML belgesi şeklini değiştirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="c9a83-104">Sometimes you will have to change the shape of an XML document.</span></span> <span data-ttu-id="c9a83-105">Örneğin, var olan bir XML belgesi farklı öğe ve öznitelik adları gerektiren başka bir sisteme gönderme gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="c9a83-105">For example, you might have to send an existing XML document to another system that requires different element and attribute names.</span></span> <span data-ttu-id="c9a83-106">Belgenin silmeyi ve daha okunabilir ve sürdürülebilir kodu gerekli, ancak kullanarak işlev yapım sonuç olarak öğeleri yeniden adlandırma gidebilir.</span><span class="sxs-lookup"><span data-stu-id="c9a83-106">You could go through the document, deleting and renaming elements as required, but using functional construction results in more readable and maintainable code.</span></span> <span data-ttu-id="c9a83-107">İşlev oluşturma hakkında daha fazla bilgi için bkz: [işlevsel yapımı (LINQ-XML) (C#)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c9a83-107">For more information about functional construction, see [Functional Construction (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="c9a83-108">İlk örnek XML belgesi organizasyonu değiştirir.</span><span class="sxs-lookup"><span data-stu-id="c9a83-108">The first example changes the organization of the XML document.</span></span> <span data-ttu-id="c9a83-109">Bu karmaşık öğeleri ağacında bir konumdan diğerine taşır.</span><span class="sxs-lookup"><span data-stu-id="c9a83-109">It moves complex elements from one location in the tree to another.</span></span>  
  
 <span data-ttu-id="c9a83-110">Bu konudaki ikinci örnek kaynak belgedeki daha farklı bir şekli bir XML belgesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c9a83-110">The second example in this topic creates an XML document with a different shape than the source document.</span></span> <span data-ttu-id="c9a83-111">Öğe adları büyük küçük harf değiştirir, bazı öğelerin yeniden adlandırır ve bazı öğeler kaynak ağaç dönüştürülmüş ağaç dışında bırakır.</span><span class="sxs-lookup"><span data-stu-id="c9a83-111">It changes the casing of the element names, renames some elements, and leaves some elements from the source tree out of the transformed tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9a83-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="c9a83-112">Example</span></span>  
 <span data-ttu-id="c9a83-113">Aşağıdaki kod katıştırılmış sorgu ifadeleri kullanarak XML dosyasını şeklini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="c9a83-113">The following code changes the shape of an XML file using embedded query expressions.</span></span>  
  
 <span data-ttu-id="c9a83-114">Bu örnekte kaynak XML belgesi içeriyor bir `Customers` öğesinin altında `Root` tüm müşteriler içeren öğe.</span><span class="sxs-lookup"><span data-stu-id="c9a83-114">The source XML document in this example contains a `Customers` element under the `Root` element that contains all customers.</span></span> <span data-ttu-id="c9a83-115">Ayrıca içeren bir `Orders` öğesinin altında `Root` tüm siparişleri içeren öğe.</span><span class="sxs-lookup"><span data-stu-id="c9a83-115">It also contains an `Orders` element under the `Root` element that contains all orders.</span></span> <span data-ttu-id="c9a83-116">Bu örnekte, her bir müşteri için siparişleri içerdiği yeni bir XML ağacı oluşturur bir `Orders` öğesi içinde `Customer` öğesi.</span><span class="sxs-lookup"><span data-stu-id="c9a83-116">This example creates a new XML tree in which the orders for each customer are contained in an `Orders` element within the `Customer` element.</span></span> <span data-ttu-id="c9a83-117">Özgün belgeyi de içeren bir `CustomerID` öğesinde `Order` öğesi; yeniden şekilli belgeden kaldırılması bu öğe olacaktır.</span><span class="sxs-lookup"><span data-stu-id="c9a83-117">The original document also contains a `CustomerID` element in the `Order` element; this element will be removed from the re-shaped document.</span></span>  
  
 <span data-ttu-id="c9a83-118">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: müşteriler ve siparişler (LINQ-XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="c9a83-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="c9a83-119">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="c9a83-119">This code produces the following output:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="c9a83-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="c9a83-120">Example</span></span>  
 <span data-ttu-id="c9a83-121">Bu örnekte, bazı öğelerin yeniden adlandırır ve bazı öznitelikler öğelerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="c9a83-121">This example renames some elements and converts some attributes to elements.</span></span>  
  
 <span data-ttu-id="c9a83-122">Kod çağrıları `ConvertAddress`, listesini döndürür <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="c9a83-122">The code calls `ConvertAddress`, which returns a list of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="c9a83-123">Yöntemin bağımsız değişkeni belirleyen bir sorgudur `Address` karmaşık bir öğe burada `Type` özniteliği değerine sahip `"Shipping"`.</span><span class="sxs-lookup"><span data-stu-id="c9a83-123">The argument to the method is a query that determines the `Address` complex element where the `Type` attribute has a value of `"Shipping"`.</span></span>  
  
 <span data-ttu-id="c9a83-124">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: tipik satın alma siparişi (LINQ-XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="c9a83-124">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
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
  
 <span data-ttu-id="c9a83-125">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="c9a83-125">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c9a83-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c9a83-126">See Also</span></span>  
 [<span data-ttu-id="c9a83-127">Projeksiyonlar ve dönüştürmeler (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c9a83-127">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
