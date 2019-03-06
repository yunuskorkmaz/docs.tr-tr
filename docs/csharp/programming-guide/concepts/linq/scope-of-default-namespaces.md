---
title: C# 1 varsayılan ad alanlarının kapsamı
ms.date: 07/20/2015
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: d60f489f616a413e25bf5cd427bd467852a97c7b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379451"
---
# <a name="scope-of-default-namespaces-in-c"></a><span data-ttu-id="4ed5d-102">C dilinde varsayılan ad alanlarının kapsamı\#</span><span class="sxs-lookup"><span data-stu-id="4ed5d-102">Scope of Default Namespaces in C\#</span></span>
<span data-ttu-id="4ed5d-103">XML ağacı içinde gösterilen varsayılan ad alanı, sorgular için kapsamda değildir.</span><span class="sxs-lookup"><span data-stu-id="4ed5d-103">Default namespaces as represented in the XML tree are not in scope for queries.</span></span> <span data-ttu-id="4ed5d-104">Yine de belirtmesi gerekir, varsayılan bir ad alanı XML varsa, bir <xref:System.Xml.Linq.XNamespace> değişkeni, sorguda kullanılan bir tam adı yerel adı ile birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ed5d-104">If you have XML that is in a default namespace, you still must declare an <xref:System.Xml.Linq.XNamespace> variable, and combine it with the local name to make a qualified name to be used in the query.</span></span>  
  
 <span data-ttu-id="4ed5d-105">XML ağaçlarını sorgulama sırasında sık karşılaşılan sorunlar XML ağacı varsayılan ad alanı varsa, XML değil gibi davranarak bir ad alanında geliştirici bazen sorgu yazdığını biridir.</span><span class="sxs-lookup"><span data-stu-id="4ed5d-105">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="4ed5d-106">Bu konudaki örnekler ilk kümesi XML varsayılan ad alanı içinde yüklenir, ancak yanlış sorgulanır normal bir şekilde gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ed5d-106">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, but is queried improperly.</span></span>  
  
 <span data-ttu-id="4ed5d-107">XML ad alanında sorgulayabilmesi ikinci örneklerde gerekli düzeltmeleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4ed5d-107">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ed5d-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ed5d-108">Example</span></span>  
 <span data-ttu-id="4ed5d-109">Bu örnek, bir ad alanında XML oluşturulmasını gösterir ve boş bir sonuç döndüren bir sorgu ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4ed5d-109">This example shows the creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
### <a name="code"></a><span data-ttu-id="4ed5d-110">Kod</span><span class="sxs-lookup"><span data-stu-id="4ed5d-110">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="4ed5d-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4ed5d-111">Comments</span></span>  
 <span data-ttu-id="4ed5d-112">Bu örnek aşağıdaki sonucu üretir:</span><span class="sxs-lookup"><span data-stu-id="4ed5d-112">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="4ed5d-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ed5d-113">Example</span></span>  
 <span data-ttu-id="4ed5d-114">Bu örnek, bir ad alanı ve düzgün şekilde kodlanmış bir sorgu içinde XML oluşturulmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ed5d-114">This example shows the creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="4ed5d-115">Yukarıdaki yanlış kodlanmış örnek aksine, C# kullanırken doğru bildirmek ve başlatmak için yaklaşımdır bir <xref:System.Xml.Linq.XNamespace> nesnesi ve belirtirken kullanılacak <xref:System.Xml.Linq.XName> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="4ed5d-115">In contrast to the incorrectly coded example above, the correct approach when using C# is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="4ed5d-116">Bu durumda, bağımsız değişkeni <xref:System.Xml.Linq.XContainer.Elements%2A> yöntemi bir <xref:System.Xml.Linq.XName> nesne.</span><span class="sxs-lookup"><span data-stu-id="4ed5d-116">In this case, the argument to the <xref:System.Xml.Linq.XContainer.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>  
  
### <a name="code"></a><span data-ttu-id="4ed5d-117">Kod</span><span class="sxs-lookup"><span data-stu-id="4ed5d-117">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="4ed5d-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4ed5d-118">Comments</span></span>  
 <span data-ttu-id="4ed5d-119">Bu örnek aşağıdaki sonucu üretir:</span><span class="sxs-lookup"><span data-stu-id="4ed5d-119">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="4ed5d-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ed5d-120">See also</span></span>

- [<span data-ttu-id="4ed5d-121">XML ad alanları (C#) ile çalışma</span><span class="sxs-lookup"><span data-stu-id="4ed5d-121">Working with XML Namespaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
