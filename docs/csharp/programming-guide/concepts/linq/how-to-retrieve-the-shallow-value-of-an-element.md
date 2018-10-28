---
title: 'Nasıl yapılır: (C#) öğenin yüzeysel değerini alma'
ms.date: 07/20/2015
ms.assetid: 924a2699-72f6-4be1-aaa6-de62f8ec73b9
ms.openlocfilehash: 2555b2f17120e4dce670a9fef9fc6a126a47e935
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180659"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-c"></a><span data-ttu-id="91def-102">Nasıl yapılır: (C#) öğenin yüzeysel değerini alma</span><span class="sxs-lookup"><span data-stu-id="91def-102">How to: Retrieve the Shallow Value of an Element (C#)</span></span>
<span data-ttu-id="91def-103">Bu konuda, bir öğenin yüzeysel değerini alma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="91def-103">This topic shows how to get the shallow value of an element.</span></span> <span data-ttu-id="91def-104">Basit yalnızca belirli öğenin değeri tek bir dize olarak birleştirilmiş tüm alt öğe değerlerini içeren ayrıntılı değer aksine değerdir.</span><span class="sxs-lookup"><span data-stu-id="91def-104">The shallow value is the value of the specific element only, as opposed to the deep value, which includes the values of all descendent elements concatenated into a single string.</span></span>  
  
 <span data-ttu-id="91def-105">Ya da bir çevrim kullanarak bir öğe değeri aldığınızda veya <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> özelliği, derin değeri alın.</span><span class="sxs-lookup"><span data-stu-id="91def-105">When you retrieve an element value by using either casting or the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property, you retrieve the deep value.</span></span> <span data-ttu-id="91def-106">Yüzeysel değerini almak için kullanabileceğiniz `ShallowValue` genişletme yöntemi, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="91def-106">To retrieve the shallow value, you can use the `ShallowValue` extension method, as shown in the following example.</span></span> <span data-ttu-id="91def-107">Yüzeysel değerini alma içeriklerine göre öğeleri seçmek istediğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="91def-107">Retrieving the shallow value is useful when you want to select elements based on their content.</span></span>  
  
 <span data-ttu-id="91def-108">Aşağıdaki örnek, bir öğenin yüzeysel değerini alır. bir genişletme yöntemi bildirir.</span><span class="sxs-lookup"><span data-stu-id="91def-108">The following example declares an extension method that retrieves the shallow value of an element.</span></span> <span data-ttu-id="91def-109">Ardından, hesaplanan değeri içeren tüm öğeleri listelemek için genişletme yöntemi bir sorguda kullanır.</span><span class="sxs-lookup"><span data-stu-id="91def-109">It then uses the extension method in a query to list all elements that contain a calculated value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91def-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="91def-110">Example</span></span>  
 <span data-ttu-id="91def-111">Aşağıdaki metin dosyası Report.xml, bu örnekte kaynağıdır.</span><span class="sxs-lookup"><span data-stu-id="91def-111">The following text file, Report.xml, is the source for this example.</span></span>  
  
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
  
 <span data-ttu-id="91def-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="91def-112">This example produces the following output:</span></span>  
  
```  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a><span data-ttu-id="91def-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="91def-113">See Also</span></span>

- [<span data-ttu-id="91def-114">LINQ to XML eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="91def-114">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
