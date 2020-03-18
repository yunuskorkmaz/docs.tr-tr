---
title: Bir XML ağacının şeklini dönüştürme (C#)
ms.date: 07/20/2015
ms.assetid: 93c5d426-dea2-4709-a991-60204de42e8f
ms.openlocfilehash: 91f91ed6fea5371fae2ce67a413f4825f37af6c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347301"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-c"></a><span data-ttu-id="b28d9-102">Bir XML ağacının şeklini dönüştürme (C#)</span><span class="sxs-lookup"><span data-stu-id="b28d9-102">How to transform the shape of an XML tree (C#)</span></span>
<span data-ttu-id="b28d9-103">XML belgesinin *şekli,* öğe adlarını, öznitelik adlarını ve hiyerarşisinin özelliklerini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="b28d9-103">The *shape* of an XML document refers to its element names, attribute names, and the characteristics of its hierarchy.</span></span>  
  
 <span data-ttu-id="b28d9-104">Bazen bir XML belgesinin şeklini değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b28d9-104">Sometimes you will have to change the shape of an XML document.</span></span> <span data-ttu-id="b28d9-105">Örneğin, varolan bir XML belgesini farklı öğe ve öznitelik adları gerektiren başka bir sisteme göndermeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="b28d9-105">For example, you might have to send an existing XML document to another system that requires different element and attribute names.</span></span> <span data-ttu-id="b28d9-106">Öğeleri gerektiği gibi silip yeniden adlandırarak belgeyi gözden geçirebilirsiniz, ancak işlevsel yapı sonuçlarını daha okunabilir ve koruyabilir kodla kullanarak.</span><span class="sxs-lookup"><span data-stu-id="b28d9-106">You could go through the document, deleting and renaming elements as required, but using functional construction results in more readable and maintainable code.</span></span> <span data-ttu-id="b28d9-107">Fonksiyonel yapı hakkında daha fazla bilgi için bkz: [Fonksiyonel Yapı (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b28d9-107">For more information about functional construction, see [Functional Construction (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="b28d9-108">İlk örnek, XML belgesinin kuruluşunu değiştirir.</span><span class="sxs-lookup"><span data-stu-id="b28d9-108">The first example changes the organization of the XML document.</span></span> <span data-ttu-id="b28d9-109">Karmaşık öğeleri ağaçtaki bir konumdan diğerine taşır.</span><span class="sxs-lookup"><span data-stu-id="b28d9-109">It moves complex elements from one location in the tree to another.</span></span>  
  
 <span data-ttu-id="b28d9-110">Bu konudaki ikinci örnek, kaynak belgeden farklı bir şekle sahip bir XML belgesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b28d9-110">The second example in this topic creates an XML document with a different shape than the source document.</span></span> <span data-ttu-id="b28d9-111">Öğe adlarının gövdesini değiştirir, bazı öğeleri yeniden adlandırır ve kaynak ağaçtan bazı öğeleri dönüştürülmüş ağacın dışına bırakır.</span><span class="sxs-lookup"><span data-stu-id="b28d9-111">It changes the casing of the element names, renames some elements, and leaves some elements from the source tree out of the transformed tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b28d9-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="b28d9-112">Example</span></span>  
 <span data-ttu-id="b28d9-113">Aşağıdaki kod, katışılmış sorgu ifadelerini kullanarak bir XML dosyasının şeklini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="b28d9-113">The following code changes the shape of an XML file using embedded query expressions.</span></span>  
  
 <span data-ttu-id="b28d9-114">Bu örnekteki kaynak XML `Customers` belgesi, `Root` tüm müşterileri içeren öğenin altında bir öğe içerir.</span><span class="sxs-lookup"><span data-stu-id="b28d9-114">The source XML document in this example contains a `Customers` element under the `Root` element that contains all customers.</span></span> <span data-ttu-id="b28d9-115">Ayrıca tüm `Orders` siparişleri `Root` içeren öğe altında bir öğe içerir.</span><span class="sxs-lookup"><span data-stu-id="b28d9-115">It also contains an `Orders` element under the `Root` element that contains all orders.</span></span> <span data-ttu-id="b28d9-116">Bu örnek, her müşteri için `Orders` `Customer` siparişlerin öğe içindeki bir öğede bulunduğu yeni bir XML ağacı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b28d9-116">This example creates a new XML tree in which the orders for each customer are contained in an `Orders` element within the `Customer` element.</span></span> <span data-ttu-id="b28d9-117">Özgün belge de `CustomerID` `Order` öğebir öğe içerir; bu öğe yeniden şekillendirilen belgeden kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="b28d9-117">The original document also contains a `CustomerID` element in the `Order` element; this element will be removed from the re-shaped document.</span></span>  
  
 <span data-ttu-id="b28d9-118">Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Müşteriler ve Siparişler (LINQ-XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="b28d9-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="b28d9-119">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="b28d9-119">This code produces the following output:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="b28d9-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="b28d9-120">Example</span></span>  
 <span data-ttu-id="b28d9-121">Bu örnek, bazı öğeleri yeniden adlandırır ve bazı öznitelikleri öğelere dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="b28d9-121">This example renames some elements and converts some attributes to elements.</span></span>  
  
 <span data-ttu-id="b28d9-122">Nesnelerin listesini döndüren kod çağrıları. `ConvertAddress` <xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="b28d9-122">The code calls `ConvertAddress`, which returns a list of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="b28d9-123">Yöntemin bağımsız değişkeni, özniteliğin `Address` değeri `"Shipping"`olan `Type` karmaşık öğeyi belirleyen bir sorgudur.</span><span class="sxs-lookup"><span data-stu-id="b28d9-123">The argument to the method is a query that determines the `Address` complex element where the `Type` attribute has a value of `"Shipping"`.</span></span>  
  
 <span data-ttu-id="b28d9-124">Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Tipik SatınAlma Siparişi (LINQ-XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="b28d9-124">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
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
  
 <span data-ttu-id="b28d9-125">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="b28d9-125">This code produces the following output:</span></span>  
  
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
