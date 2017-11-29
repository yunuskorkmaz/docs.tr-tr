---
title: "Nasıl yapılır: XML CSV dosyalarından (C#) oluştur"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 57b9ccde-f983-4a21-ae61-70ecede30307
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9ec534c53445a1c0568dae36d54d9140e0220057
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-generate-xml-from-csv-files-c"></a><span data-ttu-id="0d73d-102">Nasıl yapılır: XML CSV dosyalarından (C#) oluştur</span><span class="sxs-lookup"><span data-stu-id="0d73d-102">How to: Generate XML from CSV Files (C#)</span></span>
<span data-ttu-id="0d73d-103">Bu örnek nasıl kullanılacağını gösterir [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bir virgülle ayrılmış değer (CSV) dosyasından bir XML dosyası oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="0d73d-103">This example shows how to use [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to generate an XML file from a comma-separated value (CSV) file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d73d-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="0d73d-104">Example</span></span>  
 <span data-ttu-id="0d73d-105">Aşağıdaki kod gerçekleştiren bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorguda bir dizeler dizisi.</span><span class="sxs-lookup"><span data-stu-id="0d73d-105">The following code performs a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query on an array of strings.</span></span>  
  
 <span data-ttu-id="0d73d-106">Sorgu kullanan `let` her dize alanları bir diziye bölmek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="0d73d-106">The query uses the `let` clause to split each string into an array of fields.</span></span>  
  
```csharp  
// Create the text file.  
string csvString = @"GREAL,Great Lakes Food Market,Howard Snyder,Marketing Manager,(503) 555-7555,2732 Baker Blvd.,Eugene,OR,97403,USA  
HUNGC,Hungry Coyote Import Store,Yoshi Latimer,Sales Representative,(503) 555-6874,City Center Plaza 516 Main St.,Elgin,OR,97827,USA  
LAZYK,Lazy K Kountry Store,John Steel,Marketing Manager,(509) 555-7969,12 Orchestra Terrace,Walla Walla,WA,99362,USA  
LETSS,Let's Stop N Shop,Jaime Yorres,Owner,(415) 555-5938,87 Polk St. Suite 5,San Francisco,CA,94117,USA";  
File.WriteAllText("cust.csv", csvString);  
  
// Read into an array of strings.  
string[] source = File.ReadAllLines("cust.csv");  
XElement cust = new XElement("Root",  
    from str in source  
    let fields = str.Split(',')  
    select new XElement("Customer",  
        new XAttribute("CustomerID", fields[0]),  
        new XElement("CompanyName", fields[1]),  
        new XElement("ContactName", fields[2]),  
        new XElement("ContactTitle", fields[3]),  
        new XElement("Phone", fields[4]),  
        new XElement("FullAddress",  
            new XElement("Address", fields[5]),  
            new XElement("City", fields[6]),  
            new XElement("Region", fields[7]),  
            new XElement("PostalCode", fields[8]),  
            new XElement("Country", fields[9])  
        )  
    )  
);  
Console.WriteLine(cust);  
```  
  
 <span data-ttu-id="0d73d-107">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="0d73d-107">This code produces the following output:</span></span>  
  
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
  </Customer>  
  <Customer CustomerID="HUNGC">  
    <CompanyName>Hungry Coyote Import Store</CompanyName>  
    <ContactName>Yoshi Latimer</ContactName>  
    <ContactTitle>Sales Representative</ContactTitle>  
    <Phone>(503) 555-6874</Phone>  
    <FullAddress>  
      <Address>City Center Plaza 516 Main St.</Address>  
      <City>Elgin</City>  
      <Region>OR</Region>  
      <PostalCode>97827</PostalCode>  
      <Country>USA</Country>  
    </FullAddress>  
  </Customer>  
  <Customer CustomerID="LAZYK">  
    <CompanyName>Lazy K Kountry Store</CompanyName>  
    <ContactName>John Steel</ContactName>  
    <ContactTitle>Marketing Manager</ContactTitle>  
    <Phone>(509) 555-7969</Phone>  
    <FullAddress>  
      <Address>12 Orchestra Terrace</Address>  
      <City>Walla Walla</City>  
      <Region>WA</Region>  
      <PostalCode>99362</PostalCode>  
      <Country>USA</Country>  
    </FullAddress>  
  </Customer>  
  <Customer CustomerID="LETSS">  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <ContactTitle>Owner</ContactTitle>  
    <Phone>(415) 555-5938</Phone>  
    <FullAddress>  
      <Address>87 Polk St. Suite 5</Address>  
      <City>San Francisco</City>  
      <Region>CA</Region>  
      <PostalCode>94117</PostalCode>  
      <Country>USA</Country>  
    </FullAddress>  
  </Customer>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d73d-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0d73d-108">See Also</span></span>  
 [<span data-ttu-id="0d73d-109">Projeksiyonlar ve dönüştürmeler (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="0d73d-109">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
