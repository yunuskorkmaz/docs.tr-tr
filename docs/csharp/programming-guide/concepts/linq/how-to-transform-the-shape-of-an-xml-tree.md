---
title: XML ağacının şeklini dönüştürme (C#)
description: Bir XML ağacının şeklini dönüştürmeyi öğrenin. Bir XML ağacının şekli, öğe ve öznitelik adlarına ve hiyerarşi özelliklerine başvurur.
ms.date: 07/20/2015
ms.assetid: 93c5d426-dea2-4709-a991-60204de42e8f
ms.openlocfilehash: 4fa3cc18f235d061ae1778c177c4ac9b626f4b71
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302652"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-c"></a><span data-ttu-id="5ddf9-104">XML ağacının şeklini dönüştürme (C#)</span><span class="sxs-lookup"><span data-stu-id="5ddf9-104">How to transform the shape of an XML tree (C#)</span></span>
<span data-ttu-id="5ddf9-105">Bir XML belgesinin *şekli* öğe adlarına, öznitelik adlarına ve hiyerarşisinin özelliklerine başvurur.</span><span class="sxs-lookup"><span data-stu-id="5ddf9-105">The *shape* of an XML document refers to its element names, attribute names, and the characteristics of its hierarchy.</span></span>  
  
 <span data-ttu-id="5ddf9-106">Bazen bir XML belgesinin şeklini değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5ddf9-106">Sometimes you will have to change the shape of an XML document.</span></span> <span data-ttu-id="5ddf9-107">Örneğin, var olan bir XML belgesini farklı öğe ve öznitelik adları gerektiren başka bir sisteme göndermeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="5ddf9-107">For example, you might have to send an existing XML document to another system that requires different element and attribute names.</span></span> <span data-ttu-id="5ddf9-108">Belgeyi, gereken şekilde silip yeniden adlandırarak, ancak işlevsel oluşturmayı kullanmak daha okunabilir ve sürdürülebilir kod ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="5ddf9-108">You could go through the document, deleting and renaming elements as required, but using functional construction results in more readable and maintainable code.</span></span> <span data-ttu-id="5ddf9-109">İşlevsel oluşturma hakkında daha fazla bilgi için bkz. [Işlevsel oluşturma (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="5ddf9-109">For more information about functional construction, see [Functional Construction (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="5ddf9-110">İlk örnek, XML belgesi organizasyonunu değiştirir.</span><span class="sxs-lookup"><span data-stu-id="5ddf9-110">The first example changes the organization of the XML document.</span></span> <span data-ttu-id="5ddf9-111">Karmaşık öğeleri ağaçtaki bir konumdan diğerine taşımıştır.</span><span class="sxs-lookup"><span data-stu-id="5ddf9-111">It moves complex elements from one location in the tree to another.</span></span>  
  
 <span data-ttu-id="5ddf9-112">Bu konudaki ikinci örnek, kaynak belgeden farklı bir şekle sahip bir XML belgesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5ddf9-112">The second example in this topic creates an XML document with a different shape than the source document.</span></span> <span data-ttu-id="5ddf9-113">Öğe adlarının büyük küçük harflerini değiştirir, bazı öğeleri yeniden adlandırır ve dışarı dönüştürülen ağacın bazı öğelerini kaynak ağacından bırakır.</span><span class="sxs-lookup"><span data-stu-id="5ddf9-113">It changes the casing of the element names, renames some elements, and leaves some elements from the source tree out of the transformed tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ddf9-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="5ddf9-114">Example</span></span>  
 <span data-ttu-id="5ddf9-115">Aşağıdaki kod, ekli sorgu ifadeleri kullanarak bir XML dosyasının şeklini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="5ddf9-115">The following code changes the shape of an XML file using embedded query expressions.</span></span>  
  
 <span data-ttu-id="5ddf9-116">Bu örnekteki kaynak XML belgesi `Customers` , `Root` tüm müşterileri içeren öğesi altında bir öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="5ddf9-116">The source XML document in this example contains a `Customers` element under the `Root` element that contains all customers.</span></span> <span data-ttu-id="5ddf9-117">Ayrıca `Orders` , `Root` tüm siparişleri içeren öğesi altında bir öğesi de içerir.</span><span class="sxs-lookup"><span data-stu-id="5ddf9-117">It also contains an `Orders` element under the `Root` element that contains all orders.</span></span> <span data-ttu-id="5ddf9-118">Bu örnek, her müşteriye ait siparişlerin öğesi içindeki bir öğede bulunduğu yeni bir XML ağacı oluşturur `Orders` `Customer` .</span><span class="sxs-lookup"><span data-stu-id="5ddf9-118">This example creates a new XML tree in which the orders for each customer are contained in an `Orders` element within the `Customer` element.</span></span> <span data-ttu-id="5ddf9-119">Özgün belge ayrıca `CustomerID` öğesi içindeki bir öğesi de içerir `Order` ; Bu öğe, yeniden şekillendirilmiş belgeden kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="5ddf9-119">The original document also contains a `CustomerID` element in the `Order` element; this element will be removed from the re-shaped document.</span></span>  
  
 <span data-ttu-id="5ddf9-120">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: müşteriler ve siparişler (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="5ddf9-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="5ddf9-121">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="5ddf9-121">This code produces the following output:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="5ddf9-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="5ddf9-122">Example</span></span>  
 <span data-ttu-id="5ddf9-123">Bu örnek bazı öğeleri yeniden adlandırır ve bazı öznitelikleri öğelere dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="5ddf9-123">This example renames some elements and converts some attributes to elements.</span></span>  
  
 <span data-ttu-id="5ddf9-124">`ConvertAddress`Bir nesne listesi döndüren kod çağırır <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="5ddf9-124">The code calls `ConvertAddress`, which returns a list of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="5ddf9-125">Yöntemin bağımsız değişkeni, `Address` özniteliğinin değeri olan karmaşık öğeyi belirleyen bir sorgudur `Type` `"Shipping"` .</span><span class="sxs-lookup"><span data-stu-id="5ddf9-125">The argument to the method is a query that determines the `Address` complex element where the `Type` attribute has a value of `"Shipping"`.</span></span>  
  
 <span data-ttu-id="5ddf9-126">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: tipik satın alma siparişi (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="5ddf9-126">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
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
  
 <span data-ttu-id="5ddf9-127">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="5ddf9-127">This code produces the following output:</span></span>  
  
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
