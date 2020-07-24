---
title: XPath ile LINQ to XML Karşılaştırması
description: C# ' de XPath ve LINQ to XML arasındaki işlevlerin benzerlikleri ve farklılıkları hakkında bilgi edinin. XML ağacını sorgulamak için her ikisini de kullanabilirsiniz.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
ms.openlocfilehash: e2f34903b20a53dea6e5ff4858d4fadaebd9c37a
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104006"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a><span data-ttu-id="2ff4d-104">XPath ile LINQ to XML Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="2ff4d-104">Comparison of XPath and LINQ to XML</span></span>
<span data-ttu-id="2ff4d-105">XPath ve LINQ to XML bazı benzer işlevleri sunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2ff4d-105">XPath and LINQ to XML offer some similar functionality.</span></span> <span data-ttu-id="2ff4d-106">Her ikisi de bir XML ağacını sorgulamak için, bir öğe koleksiyonu, bir öznitelik koleksiyonu, bir düğüm koleksiyonu veya bir öğe ya da öznitelik değeri olarak döndürülüyor.</span><span class="sxs-lookup"><span data-stu-id="2ff4d-106">Both can be used to query an XML tree, returning such results as a collection of elements, a collection of attributes, a collection of nodes, or the value of an element or attribute.</span></span> <span data-ttu-id="2ff4d-107">Ancak bazı farklılıklar da vardır.</span><span class="sxs-lookup"><span data-stu-id="2ff4d-107">However, there are also some differences.</span></span>  
  
## <a name="differences-between-xpath-and-linq-to-xml"></a><span data-ttu-id="2ff4d-108">XPath ve LINQ to XML arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="2ff4d-108">Differences Between XPath and LINQ to XML</span></span>  
 <span data-ttu-id="2ff4d-109">XPath, yeni türlerin yansıtmasında izin vermiyor.</span><span class="sxs-lookup"><span data-stu-id="2ff4d-109">XPath does not allow projection of new types.</span></span> <span data-ttu-id="2ff4d-110">Yalnızca ağaçtan düğüm koleksiyonları döndürebilir, LINQ to XML bir sorgu yürütebilir ve bir nesne grafiğini ya da bir XML ağacını yeni bir şekilde proje olarak kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="2ff4d-110">It can only return collections of nodes from the tree, whereas LINQ to XML can execute a query and project an object graph or an XML tree in a new shape.</span></span> <span data-ttu-id="2ff4d-111">LINQ to XML sorguları çok daha fazla işlevselliğe sahiptir ve XPath ifadelerinden çok daha güçlüdür.</span><span class="sxs-lookup"><span data-stu-id="2ff4d-111">LINQ to XML queries encompass much more functionality and are much more powerful than XPath expressions.</span></span>  
  
 <span data-ttu-id="2ff4d-112">XPath ifadeleri bir dize içinde yalıtımda mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="2ff4d-112">XPath expressions exist in isolation within a string.</span></span> <span data-ttu-id="2ff4d-113">C# derleyicisi, derleme zamanında XPath ifadesinin ayrıştırmasına yardımcı olamaz.</span><span class="sxs-lookup"><span data-stu-id="2ff4d-113">The C# compiler cannot help parse the XPath expression at compile time.</span></span> <span data-ttu-id="2ff4d-114">Bunun aksine, LINQ to XML sorguları C# derleyicisi tarafından ayrıştırılır ve derlenir.</span><span class="sxs-lookup"><span data-stu-id="2ff4d-114">By contrast, LINQ to XML queries are parsed and compiled by the C# compiler.</span></span> <span data-ttu-id="2ff4d-115">Derleyici birçok sorgu hatasını yakalayabiliyor.</span><span class="sxs-lookup"><span data-stu-id="2ff4d-115">The compiler is able to catch many query errors.</span></span>  
  
 <span data-ttu-id="2ff4d-116">XPath sonuçları kesin yazılmamış.</span><span class="sxs-lookup"><span data-stu-id="2ff4d-116">XPath results are not strongly typed.</span></span> <span data-ttu-id="2ff4d-117">Bir dizi koşulda, bir XPath ifadesinin hesaplanmasının sonucu bir nesnedir ve uygun türü tespit etmek ve sonucu gerektiği şekilde dönüştürmek için geliştiriciye kadar olur.</span><span class="sxs-lookup"><span data-stu-id="2ff4d-117">In a number of circumstances, the result of evaluating an XPath expression is an object, and it is up to the developer to determine the proper type and cast the result as necessary.</span></span> <span data-ttu-id="2ff4d-118">Buna karşılık, bir LINQ to XML sorgusunun tahminleri kesin bir şekilde türdedir.</span><span class="sxs-lookup"><span data-stu-id="2ff4d-118">By contrast, the projections from a LINQ to XML query are strongly typed.</span></span>  
  
## <a name="result-ordering"></a><span data-ttu-id="2ff4d-119">Sonuç sıralaması</span><span class="sxs-lookup"><span data-stu-id="2ff4d-119">Result Ordering</span></span>  
 <span data-ttu-id="2ff4d-120">XPath 1,0 önerisi, bir XPath ifadesinin hesaplanmasının sonucu olan bir koleksiyonun sırasız olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2ff4d-120">The XPath 1.0 Recommendation states that a collection that is the result of evaluating an XPath expression is unordered.</span></span>  
  
 <span data-ttu-id="2ff4d-121">Ancak, bir LINQ to XML XPath eksen yöntemi tarafından döndürülen bir koleksiyon üzerinden yineleme yaparken, koleksiyondaki düğümler belge sırasıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="2ff4d-121">However, when iterating through a collection returned by a LINQ to XML XPath axis method, the nodes in the collection are returned in document order.</span></span> <span data-ttu-id="2ff4d-122">Bu durum, koşulların, ve gibi tersine belge sırası açısından ifade edildiği XPath eksenlerine erişirken bile olur `preceding` `preceding-sibling` .</span><span class="sxs-lookup"><span data-stu-id="2ff4d-122">This is the case even when accessing the XPath axes where predicates are expressed in terms of reverse document order, such as `preceding` and `preceding-sibling`.</span></span>  
  
 <span data-ttu-id="2ff4d-123">Buna karşılık, LINQ to XML eksenlerinin çoğu, koleksiyonları belge sırasıyla, ancak ikisi de, <xref:System.Xml.Linq.XNode.Ancestors%2A> <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A> ters belge sırasıyla koleksiyonları döndürür.</span><span class="sxs-lookup"><span data-stu-id="2ff4d-123">By contrast, most of the LINQ to XML axes return collections in document order, but two of them, <xref:System.Xml.Linq.XNode.Ancestors%2A> and <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, return collections in reverse document order.</span></span> <span data-ttu-id="2ff4d-124">Aşağıdaki tabloda eksenleri numaralandırılır ve her biri için koleksiyon sırası belirtilir:</span><span class="sxs-lookup"><span data-stu-id="2ff4d-124">The following table enumerates the axes, and indicates collection order for each:</span></span>  
  
|<span data-ttu-id="2ff4d-125">LINQ to XML ekseni</span><span class="sxs-lookup"><span data-stu-id="2ff4d-125">LINQ to XML axis</span></span>|<span data-ttu-id="2ff4d-126">Sıralama</span><span class="sxs-lookup"><span data-stu-id="2ff4d-126">Ordering</span></span>|  
|----------------------|--------------|  
|<span data-ttu-id="2ff4d-127">XContainer. DescendantNodes</span><span class="sxs-lookup"><span data-stu-id="2ff4d-127">XContainer.DescendantNodes</span></span>|<span data-ttu-id="2ff4d-128">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="2ff4d-128">Document order</span></span>|  
|<span data-ttu-id="2ff4d-129">XContainer. bağımlıları</span><span class="sxs-lookup"><span data-stu-id="2ff4d-129">XContainer.Descendants</span></span>|<span data-ttu-id="2ff4d-130">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="2ff4d-130">Document order</span></span>|  
|<span data-ttu-id="2ff4d-131">XContainer. Elements</span><span class="sxs-lookup"><span data-stu-id="2ff4d-131">XContainer.Elements</span></span>|<span data-ttu-id="2ff4d-132">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="2ff4d-132">Document order</span></span>|  
|<span data-ttu-id="2ff4d-133">XContainer. Nodes</span><span class="sxs-lookup"><span data-stu-id="2ff4d-133">XContainer.Nodes</span></span>|<span data-ttu-id="2ff4d-134">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="2ff4d-134">Document order</span></span>|  
|<span data-ttu-id="2ff4d-135">XContainer. NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="2ff4d-135">XContainer.NodesAfterSelf</span></span>|<span data-ttu-id="2ff4d-136">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="2ff4d-136">Document order</span></span>|  
|<span data-ttu-id="2ff4d-137">XContainer. NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="2ff4d-137">XContainer.NodesBeforeSelf</span></span>|<span data-ttu-id="2ff4d-138">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="2ff4d-138">Document order</span></span>|  
|<span data-ttu-id="2ff4d-139">XElement. AncestorsAndSelf</span><span class="sxs-lookup"><span data-stu-id="2ff4d-139">XElement.AncestorsAndSelf</span></span>|<span data-ttu-id="2ff4d-140">Belge sırasını ters çevir</span><span class="sxs-lookup"><span data-stu-id="2ff4d-140">Reverse document order</span></span>|  
|<span data-ttu-id="2ff4d-141">XElement. Attributes</span><span class="sxs-lookup"><span data-stu-id="2ff4d-141">XElement.Attributes</span></span>|<span data-ttu-id="2ff4d-142">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="2ff4d-142">Document order</span></span>|  
|<span data-ttu-id="2ff4d-143">XElement. DescendantNodesAndSelf</span><span class="sxs-lookup"><span data-stu-id="2ff4d-143">XElement.DescendantNodesAndSelf</span></span>|<span data-ttu-id="2ff4d-144">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="2ff4d-144">Document order</span></span>|  
|<span data-ttu-id="2ff4d-145">XElement. DescendantsAndSelf</span><span class="sxs-lookup"><span data-stu-id="2ff4d-145">XElement.DescendantsAndSelf</span></span>|<span data-ttu-id="2ff4d-146">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="2ff4d-146">Document order</span></span>|  
|<span data-ttu-id="2ff4d-147">XNode. öncüleri</span><span class="sxs-lookup"><span data-stu-id="2ff4d-147">XNode.Ancestors</span></span>|<span data-ttu-id="2ff4d-148">Belge sırasını ters çevir</span><span class="sxs-lookup"><span data-stu-id="2ff4d-148">Reverse document order</span></span>|  
|<span data-ttu-id="2ff4d-149">XNode. ElementsAfterSelf</span><span class="sxs-lookup"><span data-stu-id="2ff4d-149">XNode.ElementsAfterSelf</span></span>|<span data-ttu-id="2ff4d-150">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="2ff4d-150">Document order</span></span>|  
|<span data-ttu-id="2ff4d-151">XNode. ElementsBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="2ff4d-151">XNode.ElementsBeforeSelf</span></span>|<span data-ttu-id="2ff4d-152">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="2ff4d-152">Document order</span></span>|  
|<span data-ttu-id="2ff4d-153">XNode. NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="2ff4d-153">XNode.NodesAfterSelf</span></span>|<span data-ttu-id="2ff4d-154">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="2ff4d-154">Document order</span></span>|  
|<span data-ttu-id="2ff4d-155">XNode. NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="2ff4d-155">XNode.NodesBeforeSelf</span></span>|<span data-ttu-id="2ff4d-156">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="2ff4d-156">Document order</span></span>|  
  
## <a name="positional-predicates"></a><span data-ttu-id="2ff4d-157">Konumsal koşullar</span><span class="sxs-lookup"><span data-stu-id="2ff4d-157">Positional Predicates</span></span>  
 <span data-ttu-id="2ff4d-158">Bir XPath ifadesinde konumsal koşullar, birçok eksenin belge sırası açısından ifade edilir, ancak,, ve olan ters eksenler için ters belge sırasıyla ifade edilir `preceding` `preceding-sibling` `ancestor` `ancestor-or-self` .</span><span class="sxs-lookup"><span data-stu-id="2ff4d-158">Within an XPath expression, positional predicates are expressed in terms of document order for many axes, but are expressed in reverse document order for reverse axes, which are `preceding`, `preceding-sibling`, `ancestor`, and `ancestor-or-self`.</span></span> <span data-ttu-id="2ff4d-159">Örneğin, XPath ifadesi `preceding-sibling::*[1]` hemen önceki eşdüzey öğeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="2ff4d-159">For example, the XPath expression `preceding-sibling::*[1]` returns the immediately preceding sibling.</span></span> <span data-ttu-id="2ff4d-160">Bu durum, son sonuç kümesi belge sırasıyla sunulsa bile olur.</span><span class="sxs-lookup"><span data-stu-id="2ff4d-160">This is the case even though the final result set is presented in document order.</span></span>  
  
 <span data-ttu-id="2ff4d-161">Bunun aksine, LINQ to XML tüm konumsal koşullar her zaman eksenin sırası açısından ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="2ff4d-161">By contrast, all positional predicates in LINQ to XML are always expressed in terms of the order of the axis.</span></span> <span data-ttu-id="2ff4d-162">Örneğin, `anElement.ElementsBeforeSelf().ElementAt(0)` önceki eşdüzey öğeyi değil, sorgulanan öğenin üst öğesinin ilk alt öğesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="2ff4d-162">For example, `anElement.ElementsBeforeSelf().ElementAt(0)` returns the first child element of the parent of the queried element, not the immediate preceding sibling.</span></span> <span data-ttu-id="2ff4d-163">Başka bir örnek: `anElement.Ancestors().ElementAt(0)` üst öğeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="2ff4d-163">Another example: `anElement.Ancestors().ElementAt(0)` returns the parent element.</span></span>  
  
 <span data-ttu-id="2ff4d-164">LINQ to XML hemen önceki öğeyi bulmak isterseniz, aşağıdaki ifadeyi yazarsınız:</span><span class="sxs-lookup"><span data-stu-id="2ff4d-164">If you wanted to find the immediately preceding element in LINQ to XML, you would write the following expression:</span></span>  
  
```csharp
ElementsBeforeSelf().Last()
```
  
```vb
ElementsBeforeSelf().Last()
```
  
## <a name="performance-differences"></a><span data-ttu-id="2ff4d-165">Performans farkları</span><span class="sxs-lookup"><span data-stu-id="2ff4d-165">Performance Differences</span></span>  
 <span data-ttu-id="2ff4d-166">LINQ to XML XPath işlevini kullanan XPath sorguları, LINQ to XML sorguları ile birlikte gerçekleştirmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="2ff4d-166">XPath queries that use the XPath functionality in LINQ to XML will not perform as well as LINQ to XML queries.</span></span>  
  
## <a name="comparison-of-composition"></a><span data-ttu-id="2ff4d-167">Birleşim karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="2ff4d-167">Comparison of Composition</span></span>  
 <span data-ttu-id="2ff4d-168">Bir LINQ to XML sorgusunun bileşimi, söz dizimi içinde çok farklı olmasına rağmen bir XPath ifadesinin kompozisyonunun bir şekilde paraleldir.</span><span class="sxs-lookup"><span data-stu-id="2ff4d-168">Composition of a LINQ to XML query is somewhat parallel to composition of an XPath expression, although very different in syntax.</span></span>  
  
 <span data-ttu-id="2ff4d-169">Örneğin, adlı bir değişkende bir öğe varsa `customers` ve adlı tüm alt öğeler altında adlı bir alt öğe bulmak istiyorsanız `CompanyName` `Customer` , aşağıdaki gibi bir XPath ifadesi yazarsınız:</span><span class="sxs-lookup"><span data-stu-id="2ff4d-169">For example, if you have an element in a variable named `customers`, and you want to find a grandchild element named `CompanyName` under all child elements named `Customer`, you would write an XPath expression as follows:</span></span>  
  
```csharp  
customers.XPathSelectElements("./Customer/CompanyName")
```  
  
```vb
customers.XPathSelectElements("./Customer/CompanyName")
```

 <span data-ttu-id="2ff4d-170">Eşdeğer LINQ to XML sorgusu:</span><span class="sxs-lookup"><span data-stu-id="2ff4d-170">The equivalent LINQ to XML query is:</span></span>  
  
```csharp  
customers.Elements("Customer").Elements("CompanyName")
```  
  
```vb
customers.Elements("Customer").Elements("CompanyName")
```  

 <span data-ttu-id="2ff4d-171">Her XPath eksenine ilişkin benzer paraleller vardır.</span><span class="sxs-lookup"><span data-stu-id="2ff4d-171">There are similar parallels for each of the XPath axes.</span></span>  
  
|<span data-ttu-id="2ff4d-172">XPath ekseni</span><span class="sxs-lookup"><span data-stu-id="2ff4d-172">XPath axis</span></span>|<span data-ttu-id="2ff4d-173">LINQ to XML ekseni</span><span class="sxs-lookup"><span data-stu-id="2ff4d-173">LINQ to XML axis</span></span>|  
|----------------|----------------------|  
|<span data-ttu-id="2ff4d-174">alt öğe (varsayılan eksen)</span><span class="sxs-lookup"><span data-stu-id="2ff4d-174">child (the default axis)</span></span>|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="2ff4d-175">Üst (..)</span><span class="sxs-lookup"><span data-stu-id="2ff4d-175">Parent (..)</span></span>|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="2ff4d-176">öznitelik ekseni (@)</span><span class="sxs-lookup"><span data-stu-id="2ff4d-176">attribute axis (@)</span></span>|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="2ff4d-177">veya</span><span class="sxs-lookup"><span data-stu-id="2ff4d-177">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="2ff4d-178">üst öğe ekseni</span><span class="sxs-lookup"><span data-stu-id="2ff4d-178">ancestor axis</span></span>|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="2ff4d-179">üst veya-kendi ekseni</span><span class="sxs-lookup"><span data-stu-id="2ff4d-179">ancestor-or-self axis</span></span>|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="2ff4d-180">alt eksen (//)</span><span class="sxs-lookup"><span data-stu-id="2ff4d-180">descendant axis (//)</span></span>|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="2ff4d-181">veya</span><span class="sxs-lookup"><span data-stu-id="2ff4d-181">or</span></span><br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="2ff4d-182">descendant-or-self</span><span class="sxs-lookup"><span data-stu-id="2ff4d-182">descendant-or-self</span></span>|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="2ff4d-183">veya</span><span class="sxs-lookup"><span data-stu-id="2ff4d-183">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="2ff4d-184">aşağıdaki-eşdüzey</span><span class="sxs-lookup"><span data-stu-id="2ff4d-184">following-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="2ff4d-185">veya</span><span class="sxs-lookup"><span data-stu-id="2ff4d-185">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="2ff4d-186">önceki eşdüzey</span><span class="sxs-lookup"><span data-stu-id="2ff4d-186">preceding-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="2ff4d-187">veya</span><span class="sxs-lookup"><span data-stu-id="2ff4d-187">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="2ff4d-188">Sonraki</span><span class="sxs-lookup"><span data-stu-id="2ff4d-188">following</span></span>|<span data-ttu-id="2ff4d-189">Doğrudan eşdeğer olmaz.</span><span class="sxs-lookup"><span data-stu-id="2ff4d-189">No direct equivalent.</span></span>|  
|<span data-ttu-id="2ff4d-190">SCRIPT</span><span class="sxs-lookup"><span data-stu-id="2ff4d-190">preceding</span></span>|<span data-ttu-id="2ff4d-191">Doğrudan eşdeğer olmaz.</span><span class="sxs-lookup"><span data-stu-id="2ff4d-191">No direct equivalent.</span></span>|  
  