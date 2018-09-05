---
title: 'Nasıl yapılır: bir öznitelik (LINQ to XML) değerini alma (C#)'
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: a78cda390cc7b3d489cfda212cf8fb8111e4dde2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43501510"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a><span data-ttu-id="04d3a-102">Nasıl yapılır: bir öznitelik (LINQ to XML) değerini alma (C#)</span><span class="sxs-lookup"><span data-stu-id="04d3a-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="04d3a-103">Bu konuda, öznitelik değerini elde etme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="04d3a-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="04d3a-104">Başlıca iki yolu vardır: edebilirsiniz bir <xref:System.Xml.Linq.XAttribute> istenen türe; açık dönüştürme operatörü sonra içeriği öğe veya öznitelik belirtilen türe dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="04d3a-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="04d3a-105">Alternatif olarak, <xref:System.Xml.Linq.XAttribute.Value%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="04d3a-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="04d3a-106">Ancak, atama, genellikle daha iyi bir yaklaşım değildir.</span><span class="sxs-lookup"><span data-stu-id="04d3a-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="04d3a-107">Öznitelik boş değer atanabilir bir tür için tür dönüştürme, kod var olmayabilir veya bir özniteliğin değeri alınırken yazmak kolaydır.</span><span class="sxs-lookup"><span data-stu-id="04d3a-107">If you cast the attribute to a nullable type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="04d3a-108">Bu tekniğe ilişkin örnekler için bkz [nasıl yapılır: bir öğe (LINQ to XML) değerini alma (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="04d3a-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="04d3a-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="04d3a-109">Example</span></span>  
 <span data-ttu-id="04d3a-110">Bir özniteliğin değerini almak için yalnızca cast <xref:System.Xml.Linq.XAttribute> istenen türünüz için nesne.</span><span class="sxs-lookup"><span data-stu-id="04d3a-110">To retrieve the value of an attribute, you just cast the <xref:System.Xml.Linq.XAttribute> object to your desired type.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="04d3a-111">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="04d3a-111">This example produces the following output:</span></span>  
  
```  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="04d3a-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="04d3a-112">Example</span></span>  
 <span data-ttu-id="04d3a-113">Aşağıdaki örnekte, öznitelik bir ad alanında olduğu bir özniteliğin değerini almak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="04d3a-113">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="04d3a-114">Daha fazla bilgi için [(C#) XML ad alanları ile çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="04d3a-114">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="04d3a-115">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="04d3a-115">This example produces the following output:</span></span>  
  
```  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="04d3a-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="04d3a-116">See Also</span></span>

- [<span data-ttu-id="04d3a-117">LINQ to XML eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="04d3a-117">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
