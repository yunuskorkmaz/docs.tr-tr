---
title: XSD kullanarak doğrulama (LINQ to XML) (C#)
description: Xml ağacının bir XML şeması tanım dili (XSD) dosyası ile nasıl doğrulandığını öğrenin. Kod örneklerine bakın ve ek kaynakları görüntüleyin.
ms.date: 07/20/2015
ms.assetid: 6a7f83a9-2d74-4c2b-8417-0a8595879516
ms.openlocfilehash: 3b4d2137d511efbe20e4d31ad27e4975d5444ec9
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302639"
---
# <a name="how-to-validate-using-xsd-linq-to-xml-c"></a><span data-ttu-id="839d2-104">XSD kullanarak doğrulama (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="839d2-104">How to validate using XSD (LINQ to XML) (C#)</span></span>
<span data-ttu-id="839d2-105">Ad alanı, bir XML <xref:System.Xml.Schema> ağacının BIR XML şeması tanım dili (xsd) dosyasına göre doğrulanmasını kolaylaştıran uzantı yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="839d2-105">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XML Schema Definition Language (XSD) file.</span></span> <span data-ttu-id="839d2-106">Daha fazla bilgi için <xref:System.Xml.Schema.Extensions.Validate%2A> Yöntem belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="839d2-106">For more information, see the <xref:System.Xml.Schema.Extensions.Validate%2A> method documentation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="839d2-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="839d2-107">Example</span></span>  
 <span data-ttu-id="839d2-108">Aşağıdaki örnek bir oluşturur <xref:System.Xml.Schema.XmlSchemaSet> , sonra <xref:System.Xml.Linq.XDocument> şema kümesinde iki nesneyi doğrular.</span><span class="sxs-lookup"><span data-stu-id="839d2-108">The following example creates an <xref:System.Xml.Schema.XmlSchemaSet>, then validates two <xref:System.Xml.Linq.XDocument> objects against the schema set.</span></span> <span data-ttu-id="839d2-109">Belgelerden biri geçerli, diğeri değildir.</span><span class="sxs-lookup"><span data-stu-id="839d2-109">One of the documents is valid, the other is not.</span></span>  
  
```csharp  
string xsdMarkup =  
    @"<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'>  
       <xsd:element name='Root'>  
        <xsd:complexType>  
         <xsd:sequence>  
          <xsd:element name='Child1' minOccurs='1' maxOccurs='1'/>  
          <xsd:element name='Child2' minOccurs='1' maxOccurs='1'/>  
         </xsd:sequence>  
        </xsd:complexType>  
       </xsd:element>  
      </xsd:schema>";  
XmlSchemaSet schemas = new XmlSchemaSet();  
schemas.Add("", XmlReader.Create(new StringReader(xsdMarkup)));  
  
XDocument doc1 = new XDocument(  
    new XElement("Root",  
        new XElement("Child1", "content1"),  
        new XElement("Child2", "content1")  
    )  
);  
  
XDocument doc2 = new XDocument(  
    new XElement("Root",  
        new XElement("Child1", "content1"),  
        new XElement("Child3", "content1")  
    )  
);  
  
Console.WriteLine("Validating doc1");  
bool errors = false;  
doc1.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("doc1 {0}", errors ? "did not validate" : "validated");  
  
Console.WriteLine();  
Console.WriteLine("Validating doc2");  
errors = false;  
doc2.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("doc2 {0}", errors ? "did not validate" : "validated");  
```  
  
 <span data-ttu-id="839d2-110">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="839d2-110">This example produces the following output:</span></span>  
  
```output  
Validating doc1  
doc1 validated  
  
Validating doc2  
The element 'Root' has invalid child element 'Child3'. List of possible elements expected: 'Child2'.  
doc2 did not validate  
```  
  
## <a name="example"></a><span data-ttu-id="839d2-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="839d2-111">Example</span></span>  
 <span data-ttu-id="839d2-112">Aşağıdaki örnek, XML belgesinin [örnek XML dosyasından bulunduğunu doğrular: müşteriler ve siparişler (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) [örnek xsd dosyasından şema başına geçerlidir: müşteriler ve siparişler](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="839d2-112">The following example validates that the XML document from [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) is valid per the schema from [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span> <span data-ttu-id="839d2-113">Sonra kaynak XML belgesini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="839d2-113">It then modifies the source XML document.</span></span> <span data-ttu-id="839d2-114">`CustomerID`İlk Müşterideki özniteliği değiştirir.</span><span class="sxs-lookup"><span data-stu-id="839d2-114">It changes the `CustomerID` attribute on the first customer.</span></span> <span data-ttu-id="839d2-115">Değişiklik sonrasında, siparişler var olmayan bir müşteriye başvuracaktır, bu nedenle XML belgesi artık doğrulanmaz.</span><span class="sxs-lookup"><span data-stu-id="839d2-115">After the change, orders will then refer to a customer that does not exist, so the XML document will no longer validate.</span></span>  
  
 <span data-ttu-id="839d2-116">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: müşteriler ve siparişler (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="839d2-116">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
 <span data-ttu-id="839d2-117">Bu örnek şu XSD şemasını kullanır: [örnek xsd dosyası: müşteriler ve siparişler](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="839d2-117">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span>  
  
```csharp  
XmlSchemaSet schemas = new XmlSchemaSet();  
schemas.Add("", "CustomersOrders.xsd");  
  
Console.WriteLine("Attempting to validate");  
XDocument custOrdDoc = XDocument.Load("CustomersOrders.xml");  
bool errors = false;  
custOrdDoc.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");  
  
Console.WriteLine();  
// Modify the source document so that it will not validate.  
custOrdDoc.Root.Element("Orders").Element("Order").Element("CustomerID").Value = "AAAAA";  
Console.WriteLine("Attempting to validate after modification");  
errors = false;  
custOrdDoc.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");  
```  
  
 <span data-ttu-id="839d2-118">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="839d2-118">This example produces the following output:</span></span>  
  
```output  
Attempting to validate  
custOrdDoc validated  
  
Attempting to validate after modification  
The key sequence 'AAAAA' in Keyref fails to refer to some key.  
custOrdDoc did not validate  
```  
  
## <a name="see-also"></a><span data-ttu-id="839d2-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="839d2-119">See also</span></span>

- <xref:System.Xml.Schema.Extensions.Validate%2A>
- [<span data-ttu-id="839d2-120">XML ağaçları oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="839d2-120">Creating XML Trees (C#)</span></span>](creating-xml-trees-linq-to-xml-2.md)
