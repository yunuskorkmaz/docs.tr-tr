---
title: C# Dilinde Varsayılan Ad Alanlarının Kapsamı
description: C# ' deki LINQ to XML varsayılan XML ad alanlarında sorgulama hakkında bilgi edinin. Sorgu için tam bir ad oluşturmak üzere bir XNamespace değişkeni ve yerel adı kullanın.
ms.date: 07/20/2015
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: 912e47099f89daa9b80ac58b422d39d598509ac9
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302405"
---
# <a name="scope-of-default-namespaces-in-c"></a><span data-ttu-id="eca5e-104">C 'de varsayılan ad alanlarının kapsamı\#</span><span class="sxs-lookup"><span data-stu-id="eca5e-104">Scope of Default Namespaces in C\#</span></span>
<span data-ttu-id="eca5e-105">XML ağacında temsil edilen varsayılan ad alanları sorgular kapsamında değildir.</span><span class="sxs-lookup"><span data-stu-id="eca5e-105">Default namespaces as represented in the XML tree are not in scope for queries.</span></span> <span data-ttu-id="eca5e-106">Varsayılan bir ad alanında olan XML varsa, <xref:System.Xml.Linq.XNamespace> sorguda kullanılacak nitelikli bir ad oluşturmak için bir değişken bildirmeniz ve bunu yerel adla birleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="eca5e-106">If you have XML that is in a default namespace, you still must declare an <xref:System.Xml.Linq.XNamespace> variable, and combine it with the local name to make a qualified name to be used in the query.</span></span>  
  
 <span data-ttu-id="eca5e-107">XML ağaçlarını sorgularken en yaygın sorunlardan biri, XML ağacının varsayılan bir ad alanına sahip olması ve geliştiricinin bazen sorguyu bir ad alanında olmamasına rağmen yazar.</span><span class="sxs-lookup"><span data-stu-id="eca5e-107">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="eca5e-108">Bu konudaki ilk örnek kümesi, varsayılan bir ad alanındaki XML 'nin yüklendiği, ancak yanlış sorgulandığı tipik bir yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="eca5e-108">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, but is queried improperly.</span></span>  
  
 <span data-ttu-id="eca5e-109">İkinci örnek kümesinde, bir ad alanında XML 'yi sorgulayabilmeniz için gerekli düzeltmeler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="eca5e-109">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eca5e-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="eca5e-110">Example</span></span>  
 <span data-ttu-id="eca5e-111">Bu örnek, bir ad alanında XML oluşturmayı ve boş bir sonuç kümesi döndüren bir sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="eca5e-111">This example shows the creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
### <a name="code"></a><span data-ttu-id="eca5e-112">Kod</span><span class="sxs-lookup"><span data-stu-id="eca5e-112">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="eca5e-113">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="eca5e-113">Comments</span></span>  
 <span data-ttu-id="eca5e-114">Bu örnek aşağıdaki sonucu üretir:</span><span class="sxs-lookup"><span data-stu-id="eca5e-114">This example produces the following result:</span></span>  
  
```output  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="eca5e-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="eca5e-115">Example</span></span>  
 <span data-ttu-id="eca5e-116">Bu örnek, bir ad alanında XML oluşturmayı ve düzgün kodlanmış bir sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="eca5e-116">This example shows the creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="eca5e-117">Yukarıdaki yanlış kodlanmış örneğin aksine, C# kullanırken doğru yaklaşım bir nesneyi bildirmek ve başlatmak <xref:System.Xml.Linq.XNamespace> ve nesneleri belirtirken kullanmak <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="eca5e-117">In contrast to the incorrectly coded example above, the correct approach when using C# is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="eca5e-118">Bu durumda, yöntemin bağımsız değişkeni <xref:System.Xml.Linq.XContainer.Elements%2A> bir <xref:System.Xml.Linq.XName> nesnedir.</span><span class="sxs-lookup"><span data-stu-id="eca5e-118">In this case, the argument to the <xref:System.Xml.Linq.XContainer.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>  
  
### <a name="code"></a><span data-ttu-id="eca5e-119">Kod</span><span class="sxs-lookup"><span data-stu-id="eca5e-119">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="eca5e-120">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="eca5e-120">Comments</span></span>  
 <span data-ttu-id="eca5e-121">Bu örnek aşağıdaki sonucu üretir:</span><span class="sxs-lookup"><span data-stu-id="eca5e-121">This example produces the following result:</span></span>  
  
```output  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="eca5e-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eca5e-122">See also</span></span>

- [<span data-ttu-id="eca5e-123">Ad alanlarına genel bakış (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="eca5e-123">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
