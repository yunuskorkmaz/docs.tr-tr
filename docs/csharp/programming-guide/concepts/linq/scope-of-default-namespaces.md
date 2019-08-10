---
title: C# Dilinde Varsayılan Ad Alanlarının Kapsamı
ms.date: 07/20/2015
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: 0c5f5cccda6ba6a75a8631ed095921b90b02916b
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868868"
---
# <a name="scope-of-default-namespaces-in-c"></a><span data-ttu-id="cb675-102">C 'de varsayılan ad alanlarının kapsamı\#</span><span class="sxs-lookup"><span data-stu-id="cb675-102">Scope of Default Namespaces in C\#</span></span>
<span data-ttu-id="cb675-103">XML ağacında temsil edilen varsayılan ad alanları sorgular kapsamında değildir.</span><span class="sxs-lookup"><span data-stu-id="cb675-103">Default namespaces as represented in the XML tree are not in scope for queries.</span></span> <span data-ttu-id="cb675-104">Varsayılan bir ad alanında olan XML varsa, sorguda kullanılacak nitelikli bir ad oluşturmak için bir <xref:System.Xml.Linq.XNamespace> değişken bildirmeniz ve bunu yerel adla birleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cb675-104">If you have XML that is in a default namespace, you still must declare an <xref:System.Xml.Linq.XNamespace> variable, and combine it with the local name to make a qualified name to be used in the query.</span></span>  
  
 <span data-ttu-id="cb675-105">XML ağaçlarını sorgularken en yaygın sorunlardan biri, XML ağacının varsayılan bir ad alanına sahip olması ve geliştiricinin bazen sorguyu bir ad alanında olmamasına rağmen yazar.</span><span class="sxs-lookup"><span data-stu-id="cb675-105">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="cb675-106">Bu konudaki ilk örnek kümesi, varsayılan bir ad alanındaki XML 'nin yüklendiği, ancak yanlış sorgulandığı tipik bir yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb675-106">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, but is queried improperly.</span></span>  
  
 <span data-ttu-id="cb675-107">İkinci örnek kümesinde, bir ad alanında XML 'yi sorgulayabilmeniz için gerekli düzeltmeler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cb675-107">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb675-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb675-108">Example</span></span>  
 <span data-ttu-id="cb675-109">Bu örnek, bir ad alanında XML oluşturmayı ve boş bir sonuç kümesi döndüren bir sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb675-109">This example shows the creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
### <a name="code"></a><span data-ttu-id="cb675-110">Kod</span><span class="sxs-lookup"><span data-stu-id="cb675-110">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="cb675-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb675-111">Comments</span></span>  
 <span data-ttu-id="cb675-112">Bu örnek aşağıdaki sonucu üretir:</span><span class="sxs-lookup"><span data-stu-id="cb675-112">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="cb675-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb675-113">Example</span></span>  
 <span data-ttu-id="cb675-114">Bu örnek, bir ad alanında XML oluşturmayı ve düzgün kodlanmış bir sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb675-114">This example shows the creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="cb675-115">Yukarıdaki yanlış kodlanmış örneğin aksine, kullanırken C# doğru yaklaşım bir <xref:System.Xml.Linq.XNamespace> nesneyi bildirmek ve başlatmak ve nesneleri belirtirken <xref:System.Xml.Linq.XName> kullanmak.</span><span class="sxs-lookup"><span data-stu-id="cb675-115">In contrast to the incorrectly coded example above, the correct approach when using C# is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="cb675-116">Bu durumda, <xref:System.Xml.Linq.XContainer.Elements%2A> yöntemin bağımsız değişkeni bir <xref:System.Xml.Linq.XName> nesnedir.</span><span class="sxs-lookup"><span data-stu-id="cb675-116">In this case, the argument to the <xref:System.Xml.Linq.XContainer.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>  
  
### <a name="code"></a><span data-ttu-id="cb675-117">Kod</span><span class="sxs-lookup"><span data-stu-id="cb675-117">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="cb675-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb675-118">Comments</span></span>  
 <span data-ttu-id="cb675-119">Bu örnek aşağıdaki sonucu üretir:</span><span class="sxs-lookup"><span data-stu-id="cb675-119">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="cb675-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb675-120">See also</span></span>

- [<span data-ttu-id="cb675-121">Ad alanlarına genel bakış (LINQ to XMLC#) ()</span><span class="sxs-lookup"><span data-stu-id="cb675-121">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
