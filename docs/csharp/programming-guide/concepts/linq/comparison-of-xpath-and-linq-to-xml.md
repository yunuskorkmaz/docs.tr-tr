---
title: XPath ile LINQ to XML Karşılaştırması
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
ms.openlocfilehash: e9bf192a2075653802f0c5a8b4e44ff0ceacb975
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487537"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a><span data-ttu-id="a020a-102">XPath ile LINQ to XML Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="a020a-102">Comparison of XPath and LINQ to XML</span></span>
<span data-ttu-id="a020a-103">XPath ile LINQ to XML benzer bir işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="a020a-103">XPath and LINQ to XML offer some similar functionality.</span></span> <span data-ttu-id="a020a-104">Her ikisi de öğelerinin bir koleksiyonunu, özniteliklerin bir koleksiyonu, düğümlerin koleksiyonunu veya bir öğe veya öznitelik değeri olarak böyle sonuçları döndüren bir XML ağacı sorgulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a020a-104">Both can be used to query an XML tree, returning such results as a collection of elements, a collection of attributes, a collection of nodes, or the value of an element or attribute.</span></span> <span data-ttu-id="a020a-105">Ancak, aynı zamanda bazı farklar vardır.</span><span class="sxs-lookup"><span data-stu-id="a020a-105">However, there are also some differences.</span></span>  
  
## <a name="differences-between-xpath-and-linq-to-xml"></a><span data-ttu-id="a020a-106">XML için XPath ile LINQ arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="a020a-106">Differences Between XPath and LINQ to XML</span></span>  
 <span data-ttu-id="a020a-107">XPath yeni tür projeksiyonu izin vermez.</span><span class="sxs-lookup"><span data-stu-id="a020a-107">XPath does not allow projection of new types.</span></span> <span data-ttu-id="a020a-108">LINQ to XML bir sorgu yürütme ve bir nesne grafiğinin ya da yeni bir şekil içinde bir XML ağacı proje, düğüm koleksiyonlarının ağacından yalnızca döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="a020a-108">It can only return collections of nodes from the tree, whereas LINQ to XML can execute a query and project an object graph or an XML tree in a new shape.</span></span> <span data-ttu-id="a020a-109">LINQ to XML sorgularında kapsayabilir ve çok daha fazla işlevsellik ve XPath ifadeleri çok daha güçlü.</span><span class="sxs-lookup"><span data-stu-id="a020a-109">LINQ to XML queries encompass much more functionality and are much more powerful than XPath expressions.</span></span>  
  
 <span data-ttu-id="a020a-110">XPath ifadeleri bir dize içinde yalıtımı yok.</span><span class="sxs-lookup"><span data-stu-id="a020a-110">XPath expressions exist in isolation within a string.</span></span> <span data-ttu-id="a020a-111">C# Derleyici derleme zamanında XPath ifadesi ayrıştırılamıyor yardımcı olamaz.</span><span class="sxs-lookup"><span data-stu-id="a020a-111">The C# compiler cannot help parse the XPath expression at compile time.</span></span> <span data-ttu-id="a020a-112">Bunun aksine, LINQ to XML sorgularında ayrıştırılır ve C# derleyicisi tarafından derlenir.</span><span class="sxs-lookup"><span data-stu-id="a020a-112">By contrast, LINQ to XML queries are parsed and compiled by the C# compiler.</span></span> <span data-ttu-id="a020a-113">Derleyici, çok sayıda sorgu hataları yakaladığınızdan kuramıyor.</span><span class="sxs-lookup"><span data-stu-id="a020a-113">The compiler is able to catch many query errors.</span></span>  
  
 <span data-ttu-id="a020a-114">XPath sonuçları kesin türlü yapılır değil.</span><span class="sxs-lookup"><span data-stu-id="a020a-114">XPath results are not strongly typed.</span></span> <span data-ttu-id="a020a-115">Koşullar sayısı, bir XPath ifadesi değerlendirme sonucu bir nesnedir ve uygun türde belirlemek ve sonucu gerekli olarak atama için geliştirici kadar olan.</span><span class="sxs-lookup"><span data-stu-id="a020a-115">In a number of circumstances, the result of evaluating an XPath expression is an object, and it is up to the developer to determine the proper type and cast the result as necessary.</span></span> <span data-ttu-id="a020a-116">Buna karşılık gelen bir LINQ projeksiyonlar XML sorgusu için kesin türlü yapılır.</span><span class="sxs-lookup"><span data-stu-id="a020a-116">By contrast, the projections from a LINQ to XML query are strongly typed.</span></span>  
  
## <a name="result-ordering"></a><span data-ttu-id="a020a-117">Sıralama neden</span><span class="sxs-lookup"><span data-stu-id="a020a-117">Result Ordering</span></span>  
 <span data-ttu-id="a020a-118">XPath 1.0 öneri, bir XPath ifadesi değerlendirme sonucu olan bir koleksiyon sırasız olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a020a-118">The XPath 1.0 Recommendation states that a collection that is the result of evaluating an XPath expression is unordered.</span></span>  
  
 <span data-ttu-id="a020a-119">Ancak, XPath XML eksen yöntemi bir LINQ tarafından döndürülen bir koleksiyon üzerinden yineleme yapma, koleksiyon düğümleri Belge düzeninde döndürülür.</span><span class="sxs-lookup"><span data-stu-id="a020a-119">However, when iterating through a collection returned by a LINQ to XML XPath axis method, the nodes in the collection are returned in document order.</span></span> <span data-ttu-id="a020a-120">Bu XPath eksenleri bile erişirken burada doğrulamaları ters belge sırayla açısından, gibi ifade edilir durumda `preceding` ve `preceding-sibling`.</span><span class="sxs-lookup"><span data-stu-id="a020a-120">This is the case even when accessing the XPath axes where predicates are expressed in terms of reverse document order, such as `preceding` and `preceding-sibling`.</span></span>  
  
 <span data-ttu-id="a020a-121">Belge sırada ancak iki tanesi, LINQ to XML eksenleri çoğunu koleksiyonları aksine, iade <xref:System.Xml.Linq.XNode.Ancestors%2A> ve <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, belge ters sırada koleksiyonlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="a020a-121">By contrast, most of the LINQ to XML axes return collections in document order, but two of them, <xref:System.Xml.Linq.XNode.Ancestors%2A> and <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, return collections in reverse document order.</span></span> <span data-ttu-id="a020a-122">Aşağıdaki tabloda, eksen numaralandırır ve her koleksiyon sırasını gösterir:</span><span class="sxs-lookup"><span data-stu-id="a020a-122">The following table enumerates the axes, and indicates collection order for each:</span></span>  
  
|<span data-ttu-id="a020a-123">LINQ to XML eksen</span><span class="sxs-lookup"><span data-stu-id="a020a-123">LINQ to XML axis</span></span>|<span data-ttu-id="a020a-124">Sıralama</span><span class="sxs-lookup"><span data-stu-id="a020a-124">Ordering</span></span>|  
|----------------------|--------------|  
|<span data-ttu-id="a020a-125">XContainer.DescendantNodes</span><span class="sxs-lookup"><span data-stu-id="a020a-125">XContainer.DescendantNodes</span></span>|<span data-ttu-id="a020a-126">Belge sırada</span><span class="sxs-lookup"><span data-stu-id="a020a-126">Document order</span></span>|  
|<span data-ttu-id="a020a-127">XContainer.Descendants</span><span class="sxs-lookup"><span data-stu-id="a020a-127">XContainer.Descendants</span></span>|<span data-ttu-id="a020a-128">Belge sırada</span><span class="sxs-lookup"><span data-stu-id="a020a-128">Document order</span></span>|  
|<span data-ttu-id="a020a-129">XContainer.Elements</span><span class="sxs-lookup"><span data-stu-id="a020a-129">XContainer.Elements</span></span>|<span data-ttu-id="a020a-130">Belge sırada</span><span class="sxs-lookup"><span data-stu-id="a020a-130">Document order</span></span>|  
|<span data-ttu-id="a020a-131">XContainer.Nodes</span><span class="sxs-lookup"><span data-stu-id="a020a-131">XContainer.Nodes</span></span>|<span data-ttu-id="a020a-132">Belge sırada</span><span class="sxs-lookup"><span data-stu-id="a020a-132">Document order</span></span>|  
|<span data-ttu-id="a020a-133">XContainer.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="a020a-133">XContainer.NodesAfterSelf</span></span>|<span data-ttu-id="a020a-134">Belge sırada</span><span class="sxs-lookup"><span data-stu-id="a020a-134">Document order</span></span>|  
|<span data-ttu-id="a020a-135">XContainer.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="a020a-135">XContainer.NodesBeforeSelf</span></span>|<span data-ttu-id="a020a-136">Belge sırada</span><span class="sxs-lookup"><span data-stu-id="a020a-136">Document order</span></span>|  
|<span data-ttu-id="a020a-137">XElement.AncestorsAndSelf</span><span class="sxs-lookup"><span data-stu-id="a020a-137">XElement.AncestorsAndSelf</span></span>|<span data-ttu-id="a020a-138">Ters belge sırayla</span><span class="sxs-lookup"><span data-stu-id="a020a-138">Reverse document order</span></span>|  
|<span data-ttu-id="a020a-139">XElement.Attributes</span><span class="sxs-lookup"><span data-stu-id="a020a-139">XElement.Attributes</span></span>|<span data-ttu-id="a020a-140">Belge sırada</span><span class="sxs-lookup"><span data-stu-id="a020a-140">Document order</span></span>|  
|<span data-ttu-id="a020a-141">XElement.DescendantNodesAndSelf</span><span class="sxs-lookup"><span data-stu-id="a020a-141">XElement.DescendantNodesAndSelf</span></span>|<span data-ttu-id="a020a-142">Belge sırada</span><span class="sxs-lookup"><span data-stu-id="a020a-142">Document order</span></span>|  
|<span data-ttu-id="a020a-143">XElement.DescendantsAndSelf</span><span class="sxs-lookup"><span data-stu-id="a020a-143">XElement.DescendantsAndSelf</span></span>|<span data-ttu-id="a020a-144">Belge sırada</span><span class="sxs-lookup"><span data-stu-id="a020a-144">Document order</span></span>|  
|<span data-ttu-id="a020a-145">XNode.Ancestors</span><span class="sxs-lookup"><span data-stu-id="a020a-145">XNode.Ancestors</span></span>|<span data-ttu-id="a020a-146">Ters belge sırayla</span><span class="sxs-lookup"><span data-stu-id="a020a-146">Reverse document order</span></span>|  
|<span data-ttu-id="a020a-147">XNode.ElementsAfterSelf</span><span class="sxs-lookup"><span data-stu-id="a020a-147">XNode.ElementsAfterSelf</span></span>|<span data-ttu-id="a020a-148">Belge sırada</span><span class="sxs-lookup"><span data-stu-id="a020a-148">Document order</span></span>|  
|<span data-ttu-id="a020a-149">XNode.ElementsBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="a020a-149">XNode.ElementsBeforeSelf</span></span>|<span data-ttu-id="a020a-150">Belge sırada</span><span class="sxs-lookup"><span data-stu-id="a020a-150">Document order</span></span>|  
|<span data-ttu-id="a020a-151">XNode.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="a020a-151">XNode.NodesAfterSelf</span></span>|<span data-ttu-id="a020a-152">Belge sırada</span><span class="sxs-lookup"><span data-stu-id="a020a-152">Document order</span></span>|  
|<span data-ttu-id="a020a-153">XNode.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="a020a-153">XNode.NodesBeforeSelf</span></span>|<span data-ttu-id="a020a-154">Belge sırada</span><span class="sxs-lookup"><span data-stu-id="a020a-154">Document order</span></span>|  
  
## <a name="positional-predicates"></a><span data-ttu-id="a020a-155">Konumsal doğrulamaları</span><span class="sxs-lookup"><span data-stu-id="a020a-155">Positional Predicates</span></span>  
 <span data-ttu-id="a020a-156">Bir XPath ifadesi içinde konumsal koşullar açısından birçok eksenleri için belge sırada ifade edilir, ancak olan ters eksenleri ters belge sırayla ifade `preceding`, `preceding-sibling`, `ancestor`, ve `ancestor-or-self`.</span><span class="sxs-lookup"><span data-stu-id="a020a-156">Within an XPath expression, positional predicates are expressed in terms of document order for many axes, but are expressed in reverse document order for reverse axes, which are `preceding`, `preceding-sibling`, `ancestor`, and `ancestor-or-self`.</span></span> <span data-ttu-id="a020a-157">Örneğin, XPath ifadesi `preceding-sibling::*[1]` hemen önceki eşdüzey öğeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="a020a-157">For example, the XPath expression `preceding-sibling::*[1]` returns the immediately preceding sibling.</span></span> <span data-ttu-id="a020a-158">Son sonuç kümesi belge sırada sunulur olsa bile bu durum geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a020a-158">This is the case even though the final result set is presented in document order.</span></span>  
  
 <span data-ttu-id="a020a-159">Bunun aksine, tüm konumsal koşullarda LINQ to XML eksen sırası açısından her zaman ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="a020a-159">By contrast, all positional predicates in LINQ to XML are always expressed in terms of the order of the axis.</span></span> <span data-ttu-id="a020a-160">Örneğin, `anElement.ElementsBeforeSelf().ElementAt(0)` değil önceki eşdüzeyi sorgulanan öğenin üst ilk alt öğesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="a020a-160">For example, `anElement.ElementsBeforeSelf().ElementAt(0)` returns the first child element of the parent of the queried element, not the immediate preceding sibling.</span></span> <span data-ttu-id="a020a-161">Başka bir örnek: `anElement.Ancestors().ElementAt(0)` üst öğesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="a020a-161">Another example: `anElement.Ancestors().ElementAt(0)` returns the parent element.</span></span>  
  
 <span data-ttu-id="a020a-162">LINQ to XML hemen önceki öğeyi bulmak istiyorsanız, aşağıdaki ifade'ı yazmalısınız:</span><span class="sxs-lookup"><span data-stu-id="a020a-162">If you wanted to find the immediately preceding element in LINQ to XML, you would write the following expression:</span></span>  
  
```csharp
ElementsBeforeSelf().Last()
```
  
```vb
ElementsBeforeSelf().Last()
```
  
## <a name="performance-differences"></a><span data-ttu-id="a020a-163">Performans farkları</span><span class="sxs-lookup"><span data-stu-id="a020a-163">Performance Differences</span></span>  
 <span data-ttu-id="a020a-164">LINQ to XML XPath işlevleri kullanın XPath sorguları, XML sorgularında LINQ yanı sıra gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="a020a-164">XPath queries that use the XPath functionality in LINQ to XML will not perform as well as LINQ to XML queries.</span></span>  
  
## <a name="comparison-of-composition"></a><span data-ttu-id="a020a-165">Birleşim karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="a020a-165">Comparison of Composition</span></span>  
 <span data-ttu-id="a020a-166">Bir LINQ to XML sorgusu söz dizimi içinde çok farklı olsa bir XPath ifadesi, oluşumunu için biraz paralel bileşimiyse.</span><span class="sxs-lookup"><span data-stu-id="a020a-166">Composition of a LINQ to XML query is somewhat parallel to composition of an XPath expression, although very different in syntax.</span></span>  
  
 <span data-ttu-id="a020a-167">Örneğin, bir öğenin adlı bir değişkende varsa `customers`, ve adlı en alt öğe bulmak istediğiniz `CompanyName` adlı tüm alt öğeleri altında `Customer`, bir XPath ifadesi şu şekilde yazmalısınız:</span><span class="sxs-lookup"><span data-stu-id="a020a-167">For example, if you have an element in a variable named `customers`, and you want to find a grandchild element named `CompanyName` under all child elements named `Customer`, you would write an XPath expression as follows:</span></span>  
  
```csharp  
customers.XPathSelectElements("./Customer/CompanyName")
```  
  
```vb
customers.XPathSelectElements("./Customer/CompanyName")
```

 <span data-ttu-id="a020a-168">Eşdeğer LINQ to XML sorgu aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="a020a-168">The equivalent LINQ to XML query is:</span></span>  
  
```csharp  
customers.Elements("Customer").Elements("CompanyName")
```  
  
```vb
customers.Elements("Customer").Elements("CompanyName")
```  

 <span data-ttu-id="a020a-169">Her bir XPath eksenleri için benzer parallels vardır.</span><span class="sxs-lookup"><span data-stu-id="a020a-169">There are similar parallels for each of the XPath axes.</span></span>  
  
|<span data-ttu-id="a020a-170">XPath eksen</span><span class="sxs-lookup"><span data-stu-id="a020a-170">XPath axis</span></span>|<span data-ttu-id="a020a-171">LINQ to XML eksen</span><span class="sxs-lookup"><span data-stu-id="a020a-171">LINQ to XML axis</span></span>|  
|----------------|----------------------|  
|<span data-ttu-id="a020a-172">Alt (varsayılan eksen)</span><span class="sxs-lookup"><span data-stu-id="a020a-172">child (the default axis)</span></span>|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a020a-173">Üst (.)</span><span class="sxs-lookup"><span data-stu-id="a020a-173">Parent (..)</span></span>|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a020a-174">öznitelik eksen (@)</span><span class="sxs-lookup"><span data-stu-id="a020a-174">attribute axis (@)</span></span>|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="a020a-175">veya</span><span class="sxs-lookup"><span data-stu-id="a020a-175">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a020a-176">üst öğe ekseni</span><span class="sxs-lookup"><span data-stu-id="a020a-176">ancestor axis</span></span>|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a020a-177">üst veya self ekseni</span><span class="sxs-lookup"><span data-stu-id="a020a-177">ancestor-or-self axis</span></span>|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a020a-178">alt eksen (/ /)</span><span class="sxs-lookup"><span data-stu-id="a020a-178">descendant axis (//)</span></span>|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="a020a-179">veya</span><span class="sxs-lookup"><span data-stu-id="a020a-179">or</span></span><br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a020a-180">alt öğesi veya kendi kendine</span><span class="sxs-lookup"><span data-stu-id="a020a-180">descendant-or-self</span></span>|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="a020a-181">veya</span><span class="sxs-lookup"><span data-stu-id="a020a-181">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a020a-182">Aşağıdaki eşdüzey</span><span class="sxs-lookup"><span data-stu-id="a020a-182">following-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="a020a-183">veya</span><span class="sxs-lookup"><span data-stu-id="a020a-183">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a020a-184">Önceki eşdüzey</span><span class="sxs-lookup"><span data-stu-id="a020a-184">preceding-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="a020a-185">veya</span><span class="sxs-lookup"><span data-stu-id="a020a-185">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a020a-186">Aşağıdaki</span><span class="sxs-lookup"><span data-stu-id="a020a-186">following</span></span>|<span data-ttu-id="a020a-187">Doğrudan eşdeğeri.</span><span class="sxs-lookup"><span data-stu-id="a020a-187">No direct equivalent.</span></span>|  
|<span data-ttu-id="a020a-188">önceki</span><span class="sxs-lookup"><span data-stu-id="a020a-188">preceding</span></span>|<span data-ttu-id="a020a-189">Doğrudan eşdeğeri.</span><span class="sxs-lookup"><span data-stu-id="a020a-189">No direct equivalent.</span></span>|  
  