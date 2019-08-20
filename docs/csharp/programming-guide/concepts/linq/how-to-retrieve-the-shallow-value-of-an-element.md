---
title: 'Nasıl yapılır: Bir öğenin (C#) Yüzeysel değerini alma'
ms.date: 07/20/2015
ms.assetid: 924a2699-72f6-4be1-aaa6-de62f8ec73b9
ms.openlocfilehash: 2b37cc19e2ec5149589131497b36ad381900336b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592504"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-c"></a><span data-ttu-id="f4dd0-102">Nasıl yapılır: Bir öğenin (C#) Yüzeysel değerini alma</span><span class="sxs-lookup"><span data-stu-id="f4dd0-102">How to: Retrieve the Shallow Value of an Element (C#)</span></span>
<span data-ttu-id="f4dd0-103">Bu konu, bir öğenin yüzeysel değerinin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4dd0-103">This topic shows how to get the shallow value of an element.</span></span> <span data-ttu-id="f4dd0-104">Yüzeysel değer, tek bir dizeye birleştirilmiş tüm alt öğelerin değerlerini içeren derin değeri aksine, yalnızca belirli bir öğenin değeridir.</span><span class="sxs-lookup"><span data-stu-id="f4dd0-104">The shallow value is the value of the specific element only, as opposed to the deep value, which includes the values of all descendent elements concatenated into a single string.</span></span>  
  
 <span data-ttu-id="f4dd0-105">Ya da <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> özelliğini kullanarak bir öğe değeri aldığınızda, derin değeri alırsınız.</span><span class="sxs-lookup"><span data-stu-id="f4dd0-105">When you retrieve an element value by using either casting or the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property, you retrieve the deep value.</span></span> <span data-ttu-id="f4dd0-106">Yüzeysel değeri almak için, aşağıdaki örnekte gösterildiği gibi `ShallowValue` genişletme yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4dd0-106">To retrieve the shallow value, you can use the `ShallowValue` extension method, as shown in the following example.</span></span> <span data-ttu-id="f4dd0-107">Yüzeysel değer alma, içeriğine göre öğeleri seçmek istediğinizde faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="f4dd0-107">Retrieving the shallow value is useful when you want to select elements based on their content.</span></span>  
  
 <span data-ttu-id="f4dd0-108">Aşağıdaki örnek, bir öğenin yüzeysel değerini alan bir genişletme yöntemi bildirir.</span><span class="sxs-lookup"><span data-stu-id="f4dd0-108">The following example declares an extension method that retrieves the shallow value of an element.</span></span> <span data-ttu-id="f4dd0-109">Daha sonra, hesaplanmış bir değer içeren tüm öğeleri listelemek için bir sorgudaki genişletme yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f4dd0-109">It then uses the extension method in a query to list all elements that contain a calculated value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4dd0-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="f4dd0-110">Example</span></span>  
 <span data-ttu-id="f4dd0-111">Aşağıdaki metin dosyası, Report. xml, bu örneğin kaynağıdır.</span><span class="sxs-lookup"><span data-stu-id="f4dd0-111">The following text file, Report.xml, is the source for this example.</span></span>  
  
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
  
 <span data-ttu-id="f4dd0-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="f4dd0-112">This example produces the following output:</span></span>  
  
```  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a><span data-ttu-id="f4dd0-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4dd0-113">See also</span></span>

- [<span data-ttu-id="f4dd0-114">LINQ to XML eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="f4dd0-114">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
