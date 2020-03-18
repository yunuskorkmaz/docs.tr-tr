---
title: Bir öğenin sığ değeri nasıl alınır (C#)
ms.date: 07/20/2015
ms.assetid: 924a2699-72f6-4be1-aaa6-de62f8ec73b9
ms.openlocfilehash: b9b69b5a18106f82d13cb54208c2362f8239711e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347442"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-c"></a><span data-ttu-id="84ded-102">Bir öğenin sığ değeri nasıl alınır (C#)</span><span class="sxs-lookup"><span data-stu-id="84ded-102">How to retrieve the shallow value of an element (C#)</span></span>
<span data-ttu-id="84ded-103">Bu konu, bir öğenin sığ değerini nasıl elde edilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="84ded-103">This topic shows how to get the shallow value of an element.</span></span> <span data-ttu-id="84ded-104">Sığ değer, tek bir dize içine sıkıştırılmış tüm soyundan gelen öğelerin değerlerini içeren derin değerin aksine, yalnızca belirli öğenin değeridir.</span><span class="sxs-lookup"><span data-stu-id="84ded-104">The shallow value is the value of the specific element only, as opposed to the deep value, which includes the values of all descendent elements concatenated into a single string.</span></span>  
  
 <span data-ttu-id="84ded-105">Döküm veya <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> özelliği kullanarak bir öğe değeri aldığınızda, derin değeri alırsınız.</span><span class="sxs-lookup"><span data-stu-id="84ded-105">When you retrieve an element value by using either casting or the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property, you retrieve the deep value.</span></span> <span data-ttu-id="84ded-106">Sığ değeri almak için, aşağıdaki `ShallowValue` örnekte gösterildiği gibi uzantı yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84ded-106">To retrieve the shallow value, you can use the `ShallowValue` extension method, as shown in the following example.</span></span> <span data-ttu-id="84ded-107">Öğeleri içeriğine göre seçmek istediğinizde sığ değeri almak yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="84ded-107">Retrieving the shallow value is useful when you want to select elements based on their content.</span></span>  
  
 <span data-ttu-id="84ded-108">Aşağıdaki örnek, bir öğenin sığ değerini alan bir uzantı yöntemi ni bildirir.</span><span class="sxs-lookup"><span data-stu-id="84ded-108">The following example declares an extension method that retrieves the shallow value of an element.</span></span> <span data-ttu-id="84ded-109">Daha sonra, hesaplanan değer içeren tüm öğeleri listelemek için sorgudaki uzantı yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="84ded-109">It then uses the extension method in a query to list all elements that contain a calculated value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84ded-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="84ded-110">Example</span></span>  
 <span data-ttu-id="84ded-111">Aşağıdaki metin dosyası, Report.xml, bu örneğin kaynağıdır.</span><span class="sxs-lookup"><span data-stu-id="84ded-111">The following text file, Report.xml, is the source for this example.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Report>  
  <Section>  
    <Heading>  
      <Column Name="CustomerId">=Customer.CustomerId.Heading</Column>  
      <Column Name="Name">=Customer.Name.Heading</Column>  
    </Heading>  
    <Detail>  
      <Column Name="CustomerId">=Customer.CustomerId</Column>  
      <Column Name="Name">=Customer.Name</Column>  
    </Detail>  
  </Section>  
</Report>  
```  
  
```csharp  
public static class MyExtensions  
{  
    public static string ShallowValue(this XElement xe)  
    {  
        return xe  
               .Nodes()  
               .OfType<XText>()  
               .Aggregate(new StringBuilder(),  
                          (s, c) => s.Append(c),  
                          s => s.ToString());  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        XElement root = XElement.Load("Report.xml");  
  
        IEnumerable<XElement> query = from el in root.Descendants()  
                                      where el.ShallowValue().StartsWith("=")  
                                      select el;  
  
        foreach (var q in query)  
        {  
            Console.WriteLine("{0}{1}{2}",  
                q.Name.ToString().PadRight(8),  
                q.Attribute("Name").ToString().PadRight(20),  
                q.ShallowValue());  
        }  
    }  
}  
```  
  
 <span data-ttu-id="84ded-112">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="84ded-112">This example produces the following output:</span></span>  
  
```output  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a><span data-ttu-id="84ded-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84ded-113">See also</span></span>

- [<span data-ttu-id="84ded-114">LINQ - XML Eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="84ded-114">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
