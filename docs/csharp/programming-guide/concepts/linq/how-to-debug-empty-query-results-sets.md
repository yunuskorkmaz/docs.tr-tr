---
title: 'Nasıl yapılır: Boş sorgu sonuçları kümelerinde hata ayıklaC#()'
ms.date: 07/20/2015
ms.assetid: b569f0dc-425e-45a6-acbf-770fb761c981
ms.openlocfilehash: 12d2132f1f088050fdd109d067069870b82f2661
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205310"
---
# <a name="how-to-debug-empty-query-results-sets-c"></a><span data-ttu-id="4571d-102">Nasıl yapılır: Boş sorgu sonuçları kümelerinde hata ayıklaC#()</span><span class="sxs-lookup"><span data-stu-id="4571d-102">How to: Debug Empty Query Results Sets (C#)</span></span>
<span data-ttu-id="4571d-103">XML ağaçlarını sorgularken en yaygın sorunlardan biri, XML ağacının varsayılan bir ad alanına sahip olması ve geliştiricinin bazen sorguyu bir ad alanında olmamasına rağmen yazar.</span><span class="sxs-lookup"><span data-stu-id="4571d-103">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="4571d-104">Bu konudaki ilk örnek kümesi, varsayılan bir ad alanındaki XML 'nin yüklendiği ve yanlış sorgulandığı tipik bir yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="4571d-104">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, and is queried improperly.</span></span>  
  
 <span data-ttu-id="4571d-105">İkinci örnek kümesinde, bir ad alanında XML 'yi sorgulayabilmeniz için gerekli düzeltmeler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4571d-105">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
 <span data-ttu-id="4571d-106">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (C#LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4571d-106">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4571d-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="4571d-107">Example</span></span>  
 <span data-ttu-id="4571d-108">Bu örnek, bir ad alanında XML oluşturmayı ve boş bir sonuç kümesi döndüren bir sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4571d-108">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements("Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
 <span data-ttu-id="4571d-109">Bu örnek aşağıdaki sonucu üretir:</span><span class="sxs-lookup"><span data-stu-id="4571d-109">This example produces the following result:</span></span>  
  
```output  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="4571d-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="4571d-110">Example</span></span>  
 <span data-ttu-id="4571d-111">Bu örnek, bir ad alanında XML oluşturmayı ve düzgün kodlanmış bir sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4571d-111">This example shows creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="4571d-112">Çözüm, bir <xref:System.Xml.Linq.XNamespace> nesneyi bildirmek ve başlatmak ve nesneleri belirtirken <xref:System.Xml.Linq.XName> kullanmak.</span><span class="sxs-lookup"><span data-stu-id="4571d-112">The solution is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="4571d-113">Bu durumda, <xref:System.Xml.Linq.XContainer.Elements%2A> yöntemin bağımsız değişkeni bir <xref:System.Xml.Linq.XName> nesnedir.</span><span class="sxs-lookup"><span data-stu-id="4571d-113">In this case, the argument to the <xref:System.Xml.Linq.XContainer.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
 <span data-ttu-id="4571d-114">Bu örnek aşağıdaki sonucu üretir:</span><span class="sxs-lookup"><span data-stu-id="4571d-114">This example produces the following result:</span></span>  
  
```output  
Result set follows:  
1  
2  
3  
End of result set  
```  
