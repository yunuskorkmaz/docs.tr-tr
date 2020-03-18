---
title: C# Dilinde Varsayılan Ad Alanlarının Kapsamı
ms.date: 07/20/2015
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: 7615351f6e5f8b18bd6466a83d54aa65a6c99b50
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253047"
---
# <a name="scope-of-default-namespaces-in-c"></a><span data-ttu-id="8d620-102">C'deki Varsayılan Ad Alanlarının Kapsamı\#</span><span class="sxs-lookup"><span data-stu-id="8d620-102">Scope of Default Namespaces in C\#</span></span>
<span data-ttu-id="8d620-103">XML ağacında temsil edilen varsayılan ad alanları sorgular için kapsam içinde değildir.</span><span class="sxs-lookup"><span data-stu-id="8d620-103">Default namespaces as represented in the XML tree are not in scope for queries.</span></span> <span data-ttu-id="8d620-104">Varsayılan ad alanında bulunan XML'niz varsa, yine <xref:System.Xml.Linq.XNamespace> de bir değişken ilbildirmeniz ve sorguda kullanılacak nitelikli bir ad yapmak için bunu yerel adla birleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d620-104">If you have XML that is in a default namespace, you still must declare an <xref:System.Xml.Linq.XNamespace> variable, and combine it with the local name to make a qualified name to be used in the query.</span></span>  
  
 <span data-ttu-id="8d620-105">XML ağaçlarını sorgularken en sık karşılaşılan sorunlardan biri, XML ağacının varsayılan ad alanı varsa, geliştiricinin bazen sorguyu XML ad alanında değilmiş gibi yazmasıdır.</span><span class="sxs-lookup"><span data-stu-id="8d620-105">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="8d620-106">Bu konudaki ilk örnek kümesi, varsayılan ad alanında XML'nin yüklenmesinin tipik bir yolunu gösterir, ancak yanlış sorgulanır.</span><span class="sxs-lookup"><span data-stu-id="8d620-106">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, but is queried improperly.</span></span>  
  
 <span data-ttu-id="8d620-107">İkinci örnek kümesi, xml'i bir ad alanında sorgulayabilmeniz için gerekli düzeltmeleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="8d620-107">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d620-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="8d620-108">Example</span></span>  
 <span data-ttu-id="8d620-109">Bu örnek, bir ad alanında XML oluşturulmasını ve boş bir sonuç kümesidöndüren bir sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8d620-109">This example shows the creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8d620-110">Kod</span><span class="sxs-lookup"><span data-stu-id="8d620-110">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="8d620-111">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="8d620-111">Comments</span></span>  
 <span data-ttu-id="8d620-112">Bu örnek aşağıdaki sonucu üretir:</span><span class="sxs-lookup"><span data-stu-id="8d620-112">This example produces the following result:</span></span>  
  
```output  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="8d620-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="8d620-113">Example</span></span>  
 <span data-ttu-id="8d620-114">Bu örnek, bir ad alanında XML oluşturulmasını ve düzgün kodlanmış bir sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8d620-114">This example shows the creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="8d620-115">Yukarıdaki yanlış kodlanmış örneğin aksine, C# kullanırken doğru yaklaşım, bir <xref:System.Xml.Linq.XNamespace> nesneyi bildirmek ve başlatmak <xref:System.Xml.Linq.XName> ve nesneleri belirtirken kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="8d620-115">In contrast to the incorrectly coded example above, the correct approach when using C# is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="8d620-116">Bu durumda, yönteme <xref:System.Xml.Linq.XContainer.Elements%2A> bağımsız değişken <xref:System.Xml.Linq.XName> bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="8d620-116">In this case, the argument to the <xref:System.Xml.Linq.XContainer.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8d620-117">Kod</span><span class="sxs-lookup"><span data-stu-id="8d620-117">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="8d620-118">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="8d620-118">Comments</span></span>  
 <span data-ttu-id="8d620-119">Bu örnek aşağıdaki sonucu üretir:</span><span class="sxs-lookup"><span data-stu-id="8d620-119">This example produces the following result:</span></span>  
  
```output  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="8d620-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d620-120">See also</span></span>

- [<span data-ttu-id="8d620-121">İsim Alanlarına Genel Bakış (LINQ - XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8d620-121">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
