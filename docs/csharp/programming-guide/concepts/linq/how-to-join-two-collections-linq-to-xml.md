---
title: 'Nasıl yapılır: (LINQ to XML) iki koleksiyonu birleştirme (C#)'
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: fb158427afd59caea5eecdad29fa0a68686f6381
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667970"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a><span data-ttu-id="ff8ff-102">Nasıl yapılır: (LINQ to XML) iki koleksiyonu birleştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="ff8ff-102">How to: Join Two Collections (LINQ to XML) (C#)</span></span>
<span data-ttu-id="ff8ff-103">Bazen bir öğe veya öznitelik XML belgesindeki başka bir öğe veya öznitelik başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="ff8ff-103">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="ff8ff-104">Örneğin, [örnek XML dosyası: Müşteriler ve siparişler (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md) XML belgesi, müşterilerin listesini ve siparişlerinin listesi içerir.</span><span class="sxs-lookup"><span data-stu-id="ff8ff-104">For example, the [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md) XML document contains a list of customers and a list of orders.</span></span> <span data-ttu-id="ff8ff-105">Her `Customer` öğesi içeren bir `CustomerID` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="ff8ff-105">Each `Customer` element contains a `CustomerID` attribute.</span></span> <span data-ttu-id="ff8ff-106">Her `Order` öğesi içeren bir `CustomerID` öğesi.</span><span class="sxs-lookup"><span data-stu-id="ff8ff-106">Each `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="ff8ff-107">`CustomerID` Öğesi her sırada başvurduğu `CustomerID` öznitelik bir müşteri.</span><span class="sxs-lookup"><span data-stu-id="ff8ff-107">The `CustomerID` element in each order refers to the `CustomerID` attribute in a customer.</span></span>  
  
 <span data-ttu-id="ff8ff-108">Konu [örnek XSD dosyası: Müşteriler ve siparişler](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md) bu belgeyi doğrulamak için kullanılan bir XSD içerir.</span><span class="sxs-lookup"><span data-stu-id="ff8ff-108">The topic [Sample XSD File: Customers and Orders](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md) contains an XSD that can be used to validate this document.</span></span> <span data-ttu-id="ff8ff-109">Kullandığı `xs:key` ve `xs:keyref` , kurmak için XSD özelliklerinin `CustomerID` özniteliği `Customer` öğesi olan bir anahtar ve arasında ilişki kurmak için `CustomerID` her öğe `Order` öğesi ve `CustomerID` her öznitelik `Customer` öğesi.</span><span class="sxs-lookup"><span data-stu-id="ff8ff-109">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>  
  
 <span data-ttu-id="ff8ff-110">İle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], bu ilişkinin kullanarak yararlanabilirsiniz `join` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="ff8ff-110">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can take advantage of this relationship by using the `join` clause.</span></span>  
  
 <span data-ttu-id="ff8ff-111">Kullanılabilir hiçbir dizin olduğundan birleştirme gibi zayıf çalışma zamanı performansını olacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ff8ff-111">Note that because there is no index available, such joining will have poor runtime performance.</span></span>  
  
 <span data-ttu-id="ff8ff-112">Hakkında ayrıntılı bilgi için `join`, bkz: [birleştirme işlemleri (C#)](../../../../csharp/programming-guide/concepts/linq/join-operations.md).</span><span class="sxs-lookup"><span data-stu-id="ff8ff-112">For more detailed information about `join`, see [Join Operations (C#)](../../../../csharp/programming-guide/concepts/linq/join-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff8ff-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="ff8ff-113">Example</span></span>  
 <span data-ttu-id="ff8ff-114">Aşağıdaki örnek birleştirmeleri `Customer` öğelerine `Order` öğeleri içeren yeni bir XML belgesi oluşturur `CompanyName` siparişlerin öğesi.</span><span class="sxs-lookup"><span data-stu-id="ff8ff-114">The following example joins the `Customer` elements to the `Order` elements, and generates a new XML document that includes the `CompanyName` element in the orders.</span></span>  
  
 <span data-ttu-id="ff8ff-115">Örnek Belge şemada uygun doğrular sorguyu çalıştırmadan önce [örnek XSD dosyası: Müşteriler ve siparişler](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="ff8ff-115">Before executing the query, the example validates that the document complies with the schema in [Sample XSD File: Customers and Orders](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span></span> <span data-ttu-id="ff8ff-116">Bu, JOIN yan tümcesi her zaman çalışmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff8ff-116">This ensures that the join clause will always work.</span></span>  
  
 <span data-ttu-id="ff8ff-117">Bu sorgu tüm ilk alır `Customer` öğeleri ve bunları birleştirir `Order` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="ff8ff-117">This query first retrieves all `Customer` elements, and then joins them to the `Order` elements.</span></span> <span data-ttu-id="ff8ff-118">Yalnızca müşterilerle siparişler seçen bir `CustomerID` "K" büyüktür.</span><span class="sxs-lookup"><span data-stu-id="ff8ff-118">It selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="ff8ff-119">Ardından yeni bir proje `Order` her sipariş içindeki müşteri bilgileri içeren öğe.</span><span class="sxs-lookup"><span data-stu-id="ff8ff-119">It then projects a new `Order` element that contains the customer information within each order.</span></span>  
  
 <span data-ttu-id="ff8ff-120">Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Müşteriler ve siparişler (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="ff8ff-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
 <span data-ttu-id="ff8ff-121">Bu örnek aşağıdaki XSD şeması kullanır: [Örnek XSD Dosyası: Müşteriler ve siparişler](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="ff8ff-121">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span></span>  
  
 <span data-ttu-id="ff8ff-122">Bu şekilde katılma çok iyi gerçekleştirmez olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ff8ff-122">Note that joining in this fashion will not perform very well.</span></span> <span data-ttu-id="ff8ff-123">Birleşimler, doğrusal bir arama yoluyla gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ff8ff-123">Joins are performed via a linear search.</span></span> <span data-ttu-id="ff8ff-124">Karma tabloları veya performansa yardımcı olmak için dizinleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="ff8ff-124">There are no hash tables or indexes to help with performance.</span></span>  
  
```csharp  
XmlSchemaSet schemas = new XmlSchemaSet();  
schemas.Add("", "CustomersOrders.xsd");  
  
Console.Write("Attempting to validate, ");  
XDocument custOrdDoc = XDocument.Load("CustomersOrders.xml");  
  
bool errors = false;  
custOrdDoc.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");  
  
if (!errors)  
{  
    // Join customers and orders, and create a new XML document with  
    // a different shape.  
  
    // The new document contains orders only for customers with a  
    // CustomerID > 'K'  
    XElement custOrd = custOrdDoc.Element("Root");  
    XElement newCustOrd = new XElement("Root",  
        from c in custOrd.Element("Customers").Elements("Customer")  
        join o in custOrd.Element("Orders").Elements("Order")  
                   on (string)c.Attribute("CustomerID") equals  
                      (string)o.Element("CustomerID")  
        where ((string)c.Attribute("CustomerID")).CompareTo("K") > 0  
        select new XElement("Order",  
            new XElement("CustomerID", (string)c.Attribute("CustomerID")),  
            new XElement("CompanyName", (string)c.Element("CompanyName")),  
            new XElement("ContactName", (string)c.Element("ContactName")),  
            new XElement("EmployeeID", (string)o.Element("EmployeeID")),  
            new XElement("OrderDate", (DateTime)o.Element("OrderDate"))  
        )  
    );  
    Console.WriteLine(newCustOrd);  
}  
```  
  
 <span data-ttu-id="ff8ff-125">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="ff8ff-125">This code produces the following output:</span></span>  
  
```  
Attempting to validate, custOrdDoc validated  
<Root>  
  <Order>  
    <CustomerID>LAZYK</CustomerID>  
    <CompanyName>Lazy K Kountry Store</CompanyName>  
    <ContactName>John Steel</ContactName>  
    <EmployeeID>1</EmployeeID>  
    <OrderDate>1997-03-21T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LAZYK</CustomerID>  
    <CompanyName>Lazy K Kountry Store</CompanyName>  
    <ContactName>John Steel</ContactName>  
    <EmployeeID>8</EmployeeID>  
    <OrderDate>1997-05-22T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>1</EmployeeID>  
    <OrderDate>1997-06-25T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>8</EmployeeID>  
    <OrderDate>1997-10-27T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>6</EmployeeID>  
    <OrderDate>1997-11-10T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>4</EmployeeID>  
    <OrderDate>1998-02-12T00:00:00</OrderDate>  
  </Order>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ff8ff-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff8ff-126">See also</span></span>

- [<span data-ttu-id="ff8ff-127">Gelişmiş sorgu teknikleri (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ff8ff-127">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
