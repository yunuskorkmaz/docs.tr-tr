---
title: XPath ile LINQ to XML Karşılaştırması
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
ms.openlocfilehash: e9bf192a2075653802f0c5a8b4e44ff0ceacb975
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "66487537"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a><span data-ttu-id="25614-102">XPath ile LINQ to XML Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="25614-102">Comparison of XPath and LINQ to XML</span></span>
<span data-ttu-id="25614-103">XPath ve LINQ XML bazı benzer işlevsellik sunuyoruz.</span><span class="sxs-lookup"><span data-stu-id="25614-103">XPath and LINQ to XML offer some similar functionality.</span></span> <span data-ttu-id="25614-104">Her ikisi de bir XML ağacını sorgulamak için kullanılabilir, öğeler topluluğu, özniteliklertopluluğu, düğümler koleksiyonu veya bir öğe nin veya öznitelik değeri gibi sonuçları döndürür.</span><span class="sxs-lookup"><span data-stu-id="25614-104">Both can be used to query an XML tree, returning such results as a collection of elements, a collection of attributes, a collection of nodes, or the value of an element or attribute.</span></span> <span data-ttu-id="25614-105">Ancak, bazı farklılıklar da vardır.</span><span class="sxs-lookup"><span data-stu-id="25614-105">However, there are also some differences.</span></span>  
  
## <a name="differences-between-xpath-and-linq-to-xml"></a><span data-ttu-id="25614-106">XPath ve LINQ ile XML arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="25614-106">Differences Between XPath and LINQ to XML</span></span>  
 <span data-ttu-id="25614-107">XPath yeni türlerin projeksiyonuna izin vermez.</span><span class="sxs-lookup"><span data-stu-id="25614-107">XPath does not allow projection of new types.</span></span> <span data-ttu-id="25614-108">Yalnızca ağaçtan düğüm koleksiyonlarını döndürebilir, linq'den XML'e bir sorgu yürütebilir ve bir nesne grafiği veya XML ağacını yeni bir şekilde yansıtabilir.</span><span class="sxs-lookup"><span data-stu-id="25614-108">It can only return collections of nodes from the tree, whereas LINQ to XML can execute a query and project an object graph or an XML tree in a new shape.</span></span> <span data-ttu-id="25614-109">LINQ xml sorguları çok daha fazla işlevselliği kapsar ve XPath ifadelerinden çok daha güçlüdür.</span><span class="sxs-lookup"><span data-stu-id="25614-109">LINQ to XML queries encompass much more functionality and are much more powerful than XPath expressions.</span></span>  
  
 <span data-ttu-id="25614-110">XPath ifadeleri bir dize içinde yalıtılmış olarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="25614-110">XPath expressions exist in isolation within a string.</span></span> <span data-ttu-id="25614-111">C# derleyicisi, XPath ifadesini derleme zamanında ayrışdırma yardımcı olamaz.</span><span class="sxs-lookup"><span data-stu-id="25614-111">The C# compiler cannot help parse the XPath expression at compile time.</span></span> <span data-ttu-id="25614-112">Buna karşılık, LINQ xml sorguları ayrıştı ve C # derleyici tarafından derlenir.</span><span class="sxs-lookup"><span data-stu-id="25614-112">By contrast, LINQ to XML queries are parsed and compiled by the C# compiler.</span></span> <span data-ttu-id="25614-113">Derleyici birçok sorgu hatasını yakalayabilir.</span><span class="sxs-lookup"><span data-stu-id="25614-113">The compiler is able to catch many query errors.</span></span>  
  
 <span data-ttu-id="25614-114">XPath sonuçları güçlü bir şekilde yazılmıyor.</span><span class="sxs-lookup"><span data-stu-id="25614-114">XPath results are not strongly typed.</span></span> <span data-ttu-id="25614-115">Bir dizi durumda, bir XPath ifadesini değerlendirmenin sonucu bir nesnedir ve uygun türü belirlemek ve sonucu gerektiği gibi atmak geliştiriciye katılır.</span><span class="sxs-lookup"><span data-stu-id="25614-115">In a number of circumstances, the result of evaluating an XPath expression is an object, and it is up to the developer to determine the proper type and cast the result as necessary.</span></span> <span data-ttu-id="25614-116">Bunun aksine, bir LINQ'dan XML sorgusuna kadar olan projeksiyonlar güçlü bir şekilde yazılır.</span><span class="sxs-lookup"><span data-stu-id="25614-116">By contrast, the projections from a LINQ to XML query are strongly typed.</span></span>  
  
## <a name="result-ordering"></a><span data-ttu-id="25614-117">Sonuç Sıralama</span><span class="sxs-lookup"><span data-stu-id="25614-117">Result Ordering</span></span>  
 <span data-ttu-id="25614-118">XPath 1.0 Önerisi, Bir XPath ifadesini değerlendirme nin sonucu olan bir koleksiyonun sırasız olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="25614-118">The XPath 1.0 Recommendation states that a collection that is the result of evaluating an XPath expression is unordered.</span></span>  
  
 <span data-ttu-id="25614-119">Ancak, bir LINQ tarafından XML XPath ekseni yöntemine döndürülen bir koleksiyon aracılığıyla yinelendiğinde, koleksiyondaki düğümler belge sırasına göre döndürülür.</span><span class="sxs-lookup"><span data-stu-id="25614-119">However, when iterating through a collection returned by a LINQ to XML XPath axis method, the nodes in the collection are returned in document order.</span></span> <span data-ttu-id="25614-120">Bu durum, yüklemlerin ters belge sırası açısından ifade edildiği XPath eksenlerine erişirken `preceding-sibling`bile durum böyledir. `preceding`</span><span class="sxs-lookup"><span data-stu-id="25614-120">This is the case even when accessing the XPath axes where predicates are expressed in terms of reverse document order, such as `preceding` and `preceding-sibling`.</span></span>  
  
 <span data-ttu-id="25614-121">Bunun aksine, LINQ'dan XML eksenlerine kadar olan eksenlerin çoğu <xref:System.Xml.Linq.XNode.Ancestors%2A> koleksiyonları <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>belge sırasına göre döndürer, ancak bunlardan ikisi ve koleksiyonları ters belge sırasına göre döndürer.</span><span class="sxs-lookup"><span data-stu-id="25614-121">By contrast, most of the LINQ to XML axes return collections in document order, but two of them, <xref:System.Xml.Linq.XNode.Ancestors%2A> and <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, return collections in reverse document order.</span></span> <span data-ttu-id="25614-122">Aşağıdaki tablo eksenleri sıralar ve her biri için toplama sırasını gösterir:</span><span class="sxs-lookup"><span data-stu-id="25614-122">The following table enumerates the axes, and indicates collection order for each:</span></span>  
  
|<span data-ttu-id="25614-123">LINQ - XML ekseni</span><span class="sxs-lookup"><span data-stu-id="25614-123">LINQ to XML axis</span></span>|<span data-ttu-id="25614-124">Sıralama</span><span class="sxs-lookup"><span data-stu-id="25614-124">Ordering</span></span>|  
|----------------------|--------------|  
|<span data-ttu-id="25614-125">XContainer.DescendantNodes</span><span class="sxs-lookup"><span data-stu-id="25614-125">XContainer.DescendantNodes</span></span>|<span data-ttu-id="25614-126">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="25614-126">Document order</span></span>|  
|<span data-ttu-id="25614-127">XContainer.Descendants</span><span class="sxs-lookup"><span data-stu-id="25614-127">XContainer.Descendants</span></span>|<span data-ttu-id="25614-128">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="25614-128">Document order</span></span>|  
|<span data-ttu-id="25614-129">XContainer.Elements</span><span class="sxs-lookup"><span data-stu-id="25614-129">XContainer.Elements</span></span>|<span data-ttu-id="25614-130">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="25614-130">Document order</span></span>|  
|<span data-ttu-id="25614-131">XContainer.Nodes</span><span class="sxs-lookup"><span data-stu-id="25614-131">XContainer.Nodes</span></span>|<span data-ttu-id="25614-132">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="25614-132">Document order</span></span>|  
|<span data-ttu-id="25614-133">XContainer.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="25614-133">XContainer.NodesAfterSelf</span></span>|<span data-ttu-id="25614-134">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="25614-134">Document order</span></span>|  
|<span data-ttu-id="25614-135">XContainer.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="25614-135">XContainer.NodesBeforeSelf</span></span>|<span data-ttu-id="25614-136">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="25614-136">Document order</span></span>|  
|<span data-ttu-id="25614-137">xelement.atalarandself</span><span class="sxs-lookup"><span data-stu-id="25614-137">XElement.AncestorsAndSelf</span></span>|<span data-ttu-id="25614-138">Ters belge sırası</span><span class="sxs-lookup"><span data-stu-id="25614-138">Reverse document order</span></span>|  
|<span data-ttu-id="25614-139">xelement.öznitelikler</span><span class="sxs-lookup"><span data-stu-id="25614-139">XElement.Attributes</span></span>|<span data-ttu-id="25614-140">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="25614-140">Document order</span></span>|  
|<span data-ttu-id="25614-141">XElement.DescendantNodesAndSelf</span><span class="sxs-lookup"><span data-stu-id="25614-141">XElement.DescendantNodesAndSelf</span></span>|<span data-ttu-id="25614-142">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="25614-142">Document order</span></span>|  
|<span data-ttu-id="25614-143">XElement.DescendantsAndSelf</span><span class="sxs-lookup"><span data-stu-id="25614-143">XElement.DescendantsAndSelf</span></span>|<span data-ttu-id="25614-144">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="25614-144">Document order</span></span>|  
|<span data-ttu-id="25614-145">XNode.Atalar</span><span class="sxs-lookup"><span data-stu-id="25614-145">XNode.Ancestors</span></span>|<span data-ttu-id="25614-146">Ters belge sırası</span><span class="sxs-lookup"><span data-stu-id="25614-146">Reverse document order</span></span>|  
|<span data-ttu-id="25614-147">XNode.ElementsAfterSelf</span><span class="sxs-lookup"><span data-stu-id="25614-147">XNode.ElementsAfterSelf</span></span>|<span data-ttu-id="25614-148">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="25614-148">Document order</span></span>|  
|<span data-ttu-id="25614-149">XNode.ElementsBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="25614-149">XNode.ElementsBeforeSelf</span></span>|<span data-ttu-id="25614-150">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="25614-150">Document order</span></span>|  
|<span data-ttu-id="25614-151">XNode.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="25614-151">XNode.NodesAfterSelf</span></span>|<span data-ttu-id="25614-152">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="25614-152">Document order</span></span>|  
|<span data-ttu-id="25614-153">XNode.DüğümlerKendinden Önce</span><span class="sxs-lookup"><span data-stu-id="25614-153">XNode.NodesBeforeSelf</span></span>|<span data-ttu-id="25614-154">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="25614-154">Document order</span></span>|  
  
## <a name="positional-predicates"></a><span data-ttu-id="25614-155">Pozisyonel Yüklemler</span><span class="sxs-lookup"><span data-stu-id="25614-155">Positional Predicates</span></span>  
 <span data-ttu-id="25614-156">Bir XPath ifadesi içinde, konumsal yüklemler birçok eksen için belge sırası açısından ifade edilir, ancak ters `preceding`eksenler `ancestor`için `ancestor-or-self`ters belge sırasına göre ifade edilir, hangi , , `preceding-sibling`, ve .</span><span class="sxs-lookup"><span data-stu-id="25614-156">Within an XPath expression, positional predicates are expressed in terms of document order for many axes, but are expressed in reverse document order for reverse axes, which are `preceding`, `preceding-sibling`, `ancestor`, and `ancestor-or-self`.</span></span> <span data-ttu-id="25614-157">Örneğin, XPath ifadesi `preceding-sibling::*[1]` hemen önceki kardeş döndürür.</span><span class="sxs-lookup"><span data-stu-id="25614-157">For example, the XPath expression `preceding-sibling::*[1]` returns the immediately preceding sibling.</span></span> <span data-ttu-id="25614-158">Nihai sonuç kümesi belge sırasına göre sunulsa da durum böyledir.</span><span class="sxs-lookup"><span data-stu-id="25614-158">This is the case even though the final result set is presented in document order.</span></span>  
  
 <span data-ttu-id="25614-159">Buna karşılık, LINQ'dan XML'e kadar olan tüm konumsal yüklemler her zaman eksenin sırası açısından ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="25614-159">By contrast, all positional predicates in LINQ to XML are always expressed in terms of the order of the axis.</span></span> <span data-ttu-id="25614-160">Örneğin, `anElement.ElementsBeforeSelf().ElementAt(0)` sorgulandı öğenin üst ilk alt öğesi değil, hemen önceki kardeş döndürür.</span><span class="sxs-lookup"><span data-stu-id="25614-160">For example, `anElement.ElementsBeforeSelf().ElementAt(0)` returns the first child element of the parent of the queried element, not the immediate preceding sibling.</span></span> <span data-ttu-id="25614-161">Başka bir `anElement.Ancestors().ElementAt(0)` örnek: üst öğeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="25614-161">Another example: `anElement.Ancestors().ElementAt(0)` returns the parent element.</span></span>  
  
 <span data-ttu-id="25614-162">Linq'te XML'de hemen önceki öğeyi bulmak isterseniz, aşağıdaki ifadeyi yazarsınız:</span><span class="sxs-lookup"><span data-stu-id="25614-162">If you wanted to find the immediately preceding element in LINQ to XML, you would write the following expression:</span></span>  
  
```csharp
ElementsBeforeSelf().Last()
```
  
```vb
ElementsBeforeSelf().Last()
```
  
## <a name="performance-differences"></a><span data-ttu-id="25614-163">Performans Farklılıkları</span><span class="sxs-lookup"><span data-stu-id="25614-163">Performance Differences</span></span>  
 <span data-ttu-id="25614-164">LINQ'dan XML'e XPath işlevini kullanan XPath sorguları, LINQ'dan XML sorgularına kadar performans göstermez.</span><span class="sxs-lookup"><span data-stu-id="25614-164">XPath queries that use the XPath functionality in LINQ to XML will not perform as well as LINQ to XML queries.</span></span>  
  
## <a name="comparison-of-composition"></a><span data-ttu-id="25614-165">Kompozisyon Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="25614-165">Comparison of Composition</span></span>  
 <span data-ttu-id="25614-166">LinQ'dan XML sorgusuna kompozisyon, sözdiziminde çok farklı olsa da, xpath ifadesinin bileşimine biraz paraleldir.</span><span class="sxs-lookup"><span data-stu-id="25614-166">Composition of a LINQ to XML query is somewhat parallel to composition of an XPath expression, although very different in syntax.</span></span>  
  
 <span data-ttu-id="25614-167">Örneğin, adlı `customers`bir değişkende bir öğeniz varsa ve tüm alt `CompanyName` öğelerin altında `Customer`adı geçen bir torun öğesi bulmak istiyorsanız, aşağıdaki gibi bir XPath ifadesi yazarsınız:</span><span class="sxs-lookup"><span data-stu-id="25614-167">For example, if you have an element in a variable named `customers`, and you want to find a grandchild element named `CompanyName` under all child elements named `Customer`, you would write an XPath expression as follows:</span></span>  
  
```csharp  
customers.XPathSelectElements("./Customer/CompanyName")
```  
  
```vb
customers.XPathSelectElements("./Customer/CompanyName")
```

 <span data-ttu-id="25614-168">XML sorgusuna eşdeğer LINQ:</span><span class="sxs-lookup"><span data-stu-id="25614-168">The equivalent LINQ to XML query is:</span></span>  
  
```csharp  
customers.Elements("Customer").Elements("CompanyName")
```  
  
```vb
customers.Elements("Customer").Elements("CompanyName")
```  

 <span data-ttu-id="25614-169">XPath eksenlerinin her biri için benzer paralellikler vardır.</span><span class="sxs-lookup"><span data-stu-id="25614-169">There are similar parallels for each of the XPath axes.</span></span>  
  
|<span data-ttu-id="25614-170">XPath ekseni</span><span class="sxs-lookup"><span data-stu-id="25614-170">XPath axis</span></span>|<span data-ttu-id="25614-171">LINQ - XML ekseni</span><span class="sxs-lookup"><span data-stu-id="25614-171">LINQ to XML axis</span></span>|  
|----------------|----------------------|  
|<span data-ttu-id="25614-172">alt (varsayılan eksen)</span><span class="sxs-lookup"><span data-stu-id="25614-172">child (the default axis)</span></span>|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="25614-173">Veli (..)</span><span class="sxs-lookup"><span data-stu-id="25614-173">Parent (..)</span></span>|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="25614-174">öznitelik ekseni (@)</span><span class="sxs-lookup"><span data-stu-id="25614-174">attribute axis (@)</span></span>|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="25614-175">or</span><span class="sxs-lookup"><span data-stu-id="25614-175">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="25614-176">ata ekseni</span><span class="sxs-lookup"><span data-stu-id="25614-176">ancestor axis</span></span>|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="25614-177">ata ya da benlik ekseni</span><span class="sxs-lookup"><span data-stu-id="25614-177">ancestor-or-self axis</span></span>|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="25614-178">soyundan gelen eksen (//)</span><span class="sxs-lookup"><span data-stu-id="25614-178">descendant axis (//)</span></span>|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="25614-179">or</span><span class="sxs-lookup"><span data-stu-id="25614-179">or</span></span><br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="25614-180">soyundan gelen ya da kendi kendine</span><span class="sxs-lookup"><span data-stu-id="25614-180">descendant-or-self</span></span>|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="25614-181">or</span><span class="sxs-lookup"><span data-stu-id="25614-181">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="25614-182">aşağıdaki kardeş</span><span class="sxs-lookup"><span data-stu-id="25614-182">following-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="25614-183">or</span><span class="sxs-lookup"><span data-stu-id="25614-183">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="25614-184">önceki kardeş</span><span class="sxs-lookup"><span data-stu-id="25614-184">preceding-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="25614-185">or</span><span class="sxs-lookup"><span data-stu-id="25614-185">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="25614-186">Aşağıdaki</span><span class="sxs-lookup"><span data-stu-id="25614-186">following</span></span>|<span data-ttu-id="25614-187">Doğrudan eşdeğeri yok.</span><span class="sxs-lookup"><span data-stu-id="25614-187">No direct equivalent.</span></span>|  
|<span data-ttu-id="25614-188">Önceki</span><span class="sxs-lookup"><span data-stu-id="25614-188">preceding</span></span>|<span data-ttu-id="25614-189">Doğrudan eşdeğeri yok.</span><span class="sxs-lookup"><span data-stu-id="25614-189">No direct equivalent.</span></span>|  
  