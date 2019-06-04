---
title: C# 1 varsayılan ad alanlarının kapsamı
ms.date: 07/20/2015
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: 2eee1b0c79f585710962d8e84fe584bca6b8228b
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66483607"
---
# <a name="scope-of-default-namespaces-in-c"></a><span data-ttu-id="28ea8-102">C dilinde varsayılan ad alanlarının kapsamı\#</span><span class="sxs-lookup"><span data-stu-id="28ea8-102">Scope of Default Namespaces in C\#</span></span>
<span data-ttu-id="28ea8-103">XML ağacı içinde gösterilen varsayılan ad alanı, sorgular için kapsamda değildir.</span><span class="sxs-lookup"><span data-stu-id="28ea8-103">Default namespaces as represented in the XML tree are not in scope for queries.</span></span> <span data-ttu-id="28ea8-104">Yine de belirtmesi gerekir, varsayılan bir ad alanı XML varsa, bir <xref:System.Xml.Linq.XNamespace> değişkeni, sorguda kullanılan bir tam adı yerel adı ile birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28ea8-104">If you have XML that is in a default namespace, you still must declare an <xref:System.Xml.Linq.XNamespace> variable, and combine it with the local name to make a qualified name to be used in the query.</span></span>  
  
 <span data-ttu-id="28ea8-105">XML ağaçlarını sorgulama sırasında sık karşılaşılan sorunlar XML ağacı varsayılan ad alanı varsa, XML değil gibi davranarak bir ad alanında geliştirici bazen sorgu yazdığını biridir.</span><span class="sxs-lookup"><span data-stu-id="28ea8-105">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="28ea8-106">Bu konudaki örnekler ilk kümesi XML varsayılan ad alanı içinde yüklenir, ancak yanlış sorgulanır normal bir şekilde gösterir.</span><span class="sxs-lookup"><span data-stu-id="28ea8-106">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, but is queried improperly.</span></span>  
  
 <span data-ttu-id="28ea8-107">XML ad alanında sorgulayabilmesi ikinci örneklerde gerekli düzeltmeleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="28ea8-107">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28ea8-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="28ea8-108">Example</span></span>  
 <span data-ttu-id="28ea8-109">Bu örnek, bir ad alanında XML oluşturulmasını gösterir ve boş bir sonuç döndüren bir sorgu ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="28ea8-109">This example shows the creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
### <a name="code"></a><span data-ttu-id="28ea8-110">Kod</span><span class="sxs-lookup"><span data-stu-id="28ea8-110">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="28ea8-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="28ea8-111">Comments</span></span>  
 <span data-ttu-id="28ea8-112">Bu örnek aşağıdaki sonucu üretir:</span><span class="sxs-lookup"><span data-stu-id="28ea8-112">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="28ea8-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="28ea8-113">Example</span></span>  
 <span data-ttu-id="28ea8-114">Bu örnek, bir ad alanı ve düzgün şekilde kodlanmış bir sorgu içinde XML oluşturulmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="28ea8-114">This example shows the creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="28ea8-115">Yukarıdaki yanlış kodlanmış örnek aksine, C# kullanırken doğru bildirmek ve başlatmak için yaklaşımdır bir <xref:System.Xml.Linq.XNamespace> nesnesi ve belirtirken kullanılacak <xref:System.Xml.Linq.XName> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="28ea8-115">In contrast to the incorrectly coded example above, the correct approach when using C# is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="28ea8-116">Bu durumda, bağımsız değişkeni <xref:System.Xml.Linq.XContainer.Elements%2A> yöntemi bir <xref:System.Xml.Linq.XName> nesne.</span><span class="sxs-lookup"><span data-stu-id="28ea8-116">In this case, the argument to the <xref:System.Xml.Linq.XContainer.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>  
  
### <a name="code"></a><span data-ttu-id="28ea8-117">Kod</span><span class="sxs-lookup"><span data-stu-id="28ea8-117">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="28ea8-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="28ea8-118">Comments</span></span>  
 <span data-ttu-id="28ea8-119">Bu örnek aşağıdaki sonucu üretir:</span><span class="sxs-lookup"><span data-stu-id="28ea8-119">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="28ea8-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28ea8-120">See also</span></span>

- [<span data-ttu-id="28ea8-121">XML ad alanları (C#) ile çalışma</span><span class="sxs-lookup"><span data-stu-id="28ea8-121">Working with XML Namespaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md)
