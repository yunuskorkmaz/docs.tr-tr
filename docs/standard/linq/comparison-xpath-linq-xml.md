---
title: XPath ve LINQ to XML karşılaştırması-LINQ to XML
description: Hem XPath hem de LINQ to XML sorguları, XML ağaçlarını sorgulayabilir. Bu makaleler iki seçeneği karşılaştırır ve LINQ to XML sorguları, daha güçlü, çok yönlü, daha hızlı, daha güvenli ve daha kolay bir seçim olacak şekilde bulur.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
ms.openlocfilehash: b98651ffd7e0df0057164f40bedbc43d654d8c81
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553398"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a><span data-ttu-id="45952-104">XPath ile LINQ to XML Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="45952-104">Comparison of XPath and LINQ to XML</span></span>

<span data-ttu-id="45952-105">XPath ve LINQ to XML bazı yollarla benzerdir.</span><span class="sxs-lookup"><span data-stu-id="45952-105">XPath and LINQ to XML are similar in some ways.</span></span> <span data-ttu-id="45952-106">Her ikisi de bir XML ağacını sorgulamak için, bir öğe koleksiyonu, bir öznitelik koleksiyonu, bir düğüm koleksiyonu veya bir öğe ya da öznitelik değeri olarak döndürülüyor.</span><span class="sxs-lookup"><span data-stu-id="45952-106">Both can be used to query an XML tree, returning such results as a collection of elements, a collection of attributes, a collection of nodes, or the value of an element or attribute.</span></span> <span data-ttu-id="45952-107">Ancak, iki seçenek arasında önemli farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="45952-107">However, there are significant differences between the two options.</span></span>

## <a name="differences-between-xpath-and-linq-to-xml"></a><span data-ttu-id="45952-108">XPath ve LINQ to XML arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="45952-108">Differences between XPath and LINQ to XML</span></span>

<span data-ttu-id="45952-109">XPath, yeni türlerin projeksiyonunu izin vermez.</span><span class="sxs-lookup"><span data-stu-id="45952-109">XPath doesn't allow projection of new types.</span></span> <span data-ttu-id="45952-110">Yalnızca ağaçtan düğüm koleksiyonları döndürebilir, LINQ to XML bir sorgu yürütebilir ve bir nesne grafiğini ya da bir XML ağacını yeni bir şekilde proje olarak kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="45952-110">It can only return collections of nodes from the tree, whereas LINQ to XML can execute a query and project an object graph or an XML tree in a new shape.</span></span> <span data-ttu-id="45952-111">LINQ to XML sorguları, XPath ifadelerinden çok daha fazlasını yapabilir.</span><span class="sxs-lookup"><span data-stu-id="45952-111">LINQ to XML queries can do much more than XPath expressions.</span></span>

<span data-ttu-id="45952-112">XPath ifadeleri bir dize içinde yalıtımda mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="45952-112">XPath expressions exist in isolation within a string.</span></span> <span data-ttu-id="45952-113">C# derleyicisi, derleme zamanında XPath ifadesinin ayrıştırmasına yardımcı olamaz.</span><span class="sxs-lookup"><span data-stu-id="45952-113">The C# compiler can't help parse the XPath expression at compile time.</span></span> <span data-ttu-id="45952-114">Bunun aksine, LINQ to XML sorguları C# derleyicisi tarafından ayrıştırılır ve derlenir.</span><span class="sxs-lookup"><span data-stu-id="45952-114">By contrast, LINQ to XML queries are parsed and compiled by the C# compiler.</span></span> <span data-ttu-id="45952-115">Derleyici birçok sorgu hatasını yakalayabilir.</span><span class="sxs-lookup"><span data-stu-id="45952-115">The compiler can catch many query errors.</span></span>

<span data-ttu-id="45952-116">XPath sonuçları kesin olarak yazılmamış.</span><span class="sxs-lookup"><span data-stu-id="45952-116">XPath results aren't strongly typed.</span></span> <span data-ttu-id="45952-117">Bir dizi koşulda, bir XPath ifadesinin hesaplanmasının sonucu bir nesnedir ve uygun türü tespit etmek ve sonucu gerektiği şekilde dönüştürmek için geliştiriciye de sahip olur.</span><span class="sxs-lookup"><span data-stu-id="45952-117">In a number of circumstances, the result of evaluating an XPath expression is an object, and it's up to the developer to determine the proper type and cast the result as necessary.</span></span> <span data-ttu-id="45952-118">Buna karşılık, bir LINQ to XML sorgusunun tahminleri kesin bir şekilde türdedir.</span><span class="sxs-lookup"><span data-stu-id="45952-118">By contrast, the projections from a LINQ to XML query are strongly typed.</span></span>

## <a name="result-ordering"></a><span data-ttu-id="45952-119">Sonuç sıralaması</span><span class="sxs-lookup"><span data-stu-id="45952-119">Result ordering</span></span>

<span data-ttu-id="45952-120">XPath 1,0 önerisi, bir XPath ifadesinin hesaplanmasının sonucu olan bir koleksiyonun sırasız olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="45952-120">The XPath 1.0 Recommendation states that a collection that's the result of evaluating an XPath expression is unordered.</span></span>

<span data-ttu-id="45952-121">Ancak, bir LINQ to XML XPath eksen yöntemi tarafından döndürülen bir koleksiyon üzerinden yineleme yaparken, koleksiyondaki düğümler belge sırasıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="45952-121">However, when iterating through a collection returned by a LINQ to XML XPath axis method, the nodes in the collection are returned in document order.</span></span> <span data-ttu-id="45952-122">Bu durum, koşulların, ve gibi tersine belge sırası açısından ifade edildiği XPath eksenlerine erişirken bile olur `preceding` `preceding-sibling` .</span><span class="sxs-lookup"><span data-stu-id="45952-122">This is the case even when accessing the XPath axes where predicates are expressed in terms of reverse document order, such as `preceding` and `preceding-sibling`.</span></span>

<span data-ttu-id="45952-123">Buna karşılık, LINQ to XML eksenlerinin çoğu koleksiyonları belge sırasıyla geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="45952-123">By contrast, most of the LINQ to XML axes return collections in document order.</span></span> <span data-ttu-id="45952-124">Ancak, ve iki tane, <xref:System.Xml.Linq.XNode.Ancestors%2A> ve <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A> , koleksiyonları ters belge sırasıyla geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="45952-124">However, two of them, <xref:System.Xml.Linq.XNode.Ancestors%2A> and <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, return collections in reverse document order.</span></span> <span data-ttu-id="45952-125">Aşağıdaki tabloda eksenleri numaralandırılır ve her biri için koleksiyon sırası belirtilir:</span><span class="sxs-lookup"><span data-stu-id="45952-125">The following table enumerates the axes, and indicates the collection order for each:</span></span>

|<span data-ttu-id="45952-126">LINQ to XML ekseni</span><span class="sxs-lookup"><span data-stu-id="45952-126">LINQ to XML axis</span></span>|<span data-ttu-id="45952-127">Sıralama</span><span class="sxs-lookup"><span data-stu-id="45952-127">Ordering</span></span>|
|----------------------|--------------|
|<span data-ttu-id="45952-128">XContainer. DescendantNodes</span><span class="sxs-lookup"><span data-stu-id="45952-128">XContainer.DescendantNodes</span></span>|<span data-ttu-id="45952-129">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="45952-129">Document order</span></span>|
|<span data-ttu-id="45952-130">XContainer. bağımlıları</span><span class="sxs-lookup"><span data-stu-id="45952-130">XContainer.Descendants</span></span>|<span data-ttu-id="45952-131">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="45952-131">Document order</span></span>|
|<span data-ttu-id="45952-132">XContainer. Elements</span><span class="sxs-lookup"><span data-stu-id="45952-132">XContainer.Elements</span></span>|<span data-ttu-id="45952-133">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="45952-133">Document order</span></span>|
|<span data-ttu-id="45952-134">XContainer. Nodes</span><span class="sxs-lookup"><span data-stu-id="45952-134">XContainer.Nodes</span></span>|<span data-ttu-id="45952-135">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="45952-135">Document order</span></span>|
|<span data-ttu-id="45952-136">XContainer. NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="45952-136">XContainer.NodesAfterSelf</span></span>|<span data-ttu-id="45952-137">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="45952-137">Document order</span></span>|
|<span data-ttu-id="45952-138">XContainer. NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="45952-138">XContainer.NodesBeforeSelf</span></span>|<span data-ttu-id="45952-139">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="45952-139">Document order</span></span>|
|<span data-ttu-id="45952-140">XElement. AncestorsAndSelf</span><span class="sxs-lookup"><span data-stu-id="45952-140">XElement.AncestorsAndSelf</span></span>|<span data-ttu-id="45952-141">Belge sırasını ters çevir</span><span class="sxs-lookup"><span data-stu-id="45952-141">Reverse document order</span></span>|
|<span data-ttu-id="45952-142">XElement. Attributes</span><span class="sxs-lookup"><span data-stu-id="45952-142">XElement.Attributes</span></span>|<span data-ttu-id="45952-143">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="45952-143">Document order</span></span>|
|<span data-ttu-id="45952-144">XElement. DescendantNodesAndSelf</span><span class="sxs-lookup"><span data-stu-id="45952-144">XElement.DescendantNodesAndSelf</span></span>|<span data-ttu-id="45952-145">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="45952-145">Document order</span></span>|
|<span data-ttu-id="45952-146">XElement. DescendantsAndSelf</span><span class="sxs-lookup"><span data-stu-id="45952-146">XElement.DescendantsAndSelf</span></span>|<span data-ttu-id="45952-147">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="45952-147">Document order</span></span>|
|<span data-ttu-id="45952-148">XNode. öncüleri</span><span class="sxs-lookup"><span data-stu-id="45952-148">XNode.Ancestors</span></span>|<span data-ttu-id="45952-149">Belge sırasını ters çevir</span><span class="sxs-lookup"><span data-stu-id="45952-149">Reverse document order</span></span>|
|<span data-ttu-id="45952-150">XNode. ElementsAfterSelf</span><span class="sxs-lookup"><span data-stu-id="45952-150">XNode.ElementsAfterSelf</span></span>|<span data-ttu-id="45952-151">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="45952-151">Document order</span></span>|
|<span data-ttu-id="45952-152">XNode. ElementsBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="45952-152">XNode.ElementsBeforeSelf</span></span>|<span data-ttu-id="45952-153">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="45952-153">Document order</span></span>|
|<span data-ttu-id="45952-154">XNode. NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="45952-154">XNode.NodesAfterSelf</span></span>|<span data-ttu-id="45952-155">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="45952-155">Document order</span></span>|
|<span data-ttu-id="45952-156">XNode. NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="45952-156">XNode.NodesBeforeSelf</span></span>|<span data-ttu-id="45952-157">Belge sırası</span><span class="sxs-lookup"><span data-stu-id="45952-157">Document order</span></span>|

## <a name="positional-predicates"></a><span data-ttu-id="45952-158">Konumsal koşullar</span><span class="sxs-lookup"><span data-stu-id="45952-158">Positional predicates</span></span>

<span data-ttu-id="45952-159">Bir XPath ifadesinde konumsal koşullar, birçok eksen için belge sırası açısından ifade edilir, ancak ters eksenler için ters belge sırasıyla ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="45952-159">Within an XPath expression, positional predicates are expressed in terms of document order for many axes, but are expressed in reverse document order for reverse axes.</span></span> <span data-ttu-id="45952-160">Ters eksenler: `preceding` , `preceding-sibling` , `ancestor` , ve `ancestor-or-self` .</span><span class="sxs-lookup"><span data-stu-id="45952-160">The reverse axes are: `preceding`, `preceding-sibling`, `ancestor`, and `ancestor-or-self`.</span></span> <span data-ttu-id="45952-161">Örneğin, XPath ifadesi `preceding-sibling::*[1]` hemen önceki eşdüzey öğeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="45952-161">For example, the XPath expression `preceding-sibling::*[1]` returns the immediately preceding sibling.</span></span> <span data-ttu-id="45952-162">Bu durum, son sonuç kümesi belge sırasıyla sunulsa bile olur.</span><span class="sxs-lookup"><span data-stu-id="45952-162">This is the case even though the final result set is presented in document order.</span></span>

<span data-ttu-id="45952-163">Bunun aksine, LINQ to XML tüm konumsal koşullar her zaman eksenin sırası açısından ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="45952-163">By contrast, all positional predicates in LINQ to XML are always expressed in terms of the order of the axis.</span></span> <span data-ttu-id="45952-164">Örneğin, `anElement.ElementsBeforeSelf().ElementAt(0)` önceki eşdüzey öğeyi değil, sorgulanan öğenin üst öğesinin ilk alt öğesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="45952-164">For example, `anElement.ElementsBeforeSelf().ElementAt(0)` returns the first child element of the parent of the queried element, not the immediate preceding sibling.</span></span> <span data-ttu-id="45952-165">Başka bir örnek: `anElement.Ancestors().ElementAt(0)` üst öğeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="45952-165">Another example: `anElement.Ancestors().ElementAt(0)` returns the parent element.</span></span>

<span data-ttu-id="45952-166">LINQ to XML hemen önceki öğeyi bulmak isterseniz, aşağıdaki ifadeyi yazarsınız:</span><span class="sxs-lookup"><span data-stu-id="45952-166">If you wanted to find the immediately preceding element in LINQ to XML, you would write the following expression:</span></span>

```csharp
ElementsBeforeSelf().Last()
```

```vb
ElementsBeforeSelf().Last()
```

## <a name="performance-differences"></a><span data-ttu-id="45952-167">Performans farkları</span><span class="sxs-lookup"><span data-stu-id="45952-167">Performance differences</span></span>

<span data-ttu-id="45952-168">LINQ to XML XPath işlevini kullanan XPath sorguları LINQ to XML sorgulardan daha yavaş olacaktır.</span><span class="sxs-lookup"><span data-stu-id="45952-168">XPath queries that use the XPath functionality in LINQ to XML will be slower than LINQ to XML queries.</span></span>

## <a name="comparison-of-composition"></a><span data-ttu-id="45952-169">Birleşim karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="45952-169">Comparison of composition</span></span>

<span data-ttu-id="45952-170">Bir LINQ to XML sorgusunun bileşimi bir XPath ifadesinin kompozisyonine benzerdir, ancak söz dizimi çok farklıdır.</span><span class="sxs-lookup"><span data-stu-id="45952-170">Composition of a LINQ to XML query is similar to composition of an XPath expression, but the syntax is very different.</span></span>

<span data-ttu-id="45952-171">Örneğin, adlı bir değişkende bir öğe varsa `customers` ve adlı tüm alt öğeler altında adlı bir alt öğe bulmak istiyorsanız `CompanyName` `Customer` , Bu XPath ifadesini yazarsınız:</span><span class="sxs-lookup"><span data-stu-id="45952-171">For example, if you have an element in a variable named `customers`, and you want to find a grandchild element named `CompanyName` under all child elements named `Customer`, you would write this XPath expression:</span></span>

```csharp
customers.XPathSelectElements("./Customer/CompanyName")
```

```vb
customers.XPathSelectElements("./Customer/CompanyName")
```

<span data-ttu-id="45952-172">Eşdeğer LINQ to XML sorgusu:</span><span class="sxs-lookup"><span data-stu-id="45952-172">The equivalent LINQ to XML query is:</span></span>

```csharp
customers.Elements("Customer").Elements("CompanyName")
```

```vb
customers.Elements("Customer").Elements("CompanyName")
```

<span data-ttu-id="45952-173">Her XPath eksenine ilişkin benzer paraleller vardır.</span><span class="sxs-lookup"><span data-stu-id="45952-173">There are similar parallels for each of the XPath axes.</span></span>

|<span data-ttu-id="45952-174">XPath ekseni</span><span class="sxs-lookup"><span data-stu-id="45952-174">XPath axis</span></span>|<span data-ttu-id="45952-175">LINQ to XML ekseni</span><span class="sxs-lookup"><span data-stu-id="45952-175">LINQ to XML axis</span></span>|
|----------------|----------------------|
|<span data-ttu-id="45952-176">alt öğe (varsayılan eksen)</span><span class="sxs-lookup"><span data-stu-id="45952-176">child (the default axis)</span></span>|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|
|<span data-ttu-id="45952-177">Üst (..)</span><span class="sxs-lookup"><span data-stu-id="45952-177">Parent (..)</span></span>|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|
|<span data-ttu-id="45952-178">öznitelik ekseni (@)</span><span class="sxs-lookup"><span data-stu-id="45952-178">attribute axis (@)</span></span>|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="45952-179">veya</span><span class="sxs-lookup"><span data-stu-id="45952-179">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|
|<span data-ttu-id="45952-180">üst öğe ekseni</span><span class="sxs-lookup"><span data-stu-id="45952-180">ancestor axis</span></span>|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|
|<span data-ttu-id="45952-181">üst veya-kendi ekseni</span><span class="sxs-lookup"><span data-stu-id="45952-181">ancestor-or-self axis</span></span>|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|
|<span data-ttu-id="45952-182">alt eksen (//)</span><span class="sxs-lookup"><span data-stu-id="45952-182">descendant axis (//)</span></span>|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="45952-183">veya</span><span class="sxs-lookup"><span data-stu-id="45952-183">or</span></span><br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|
|<span data-ttu-id="45952-184">descendant-or-self</span><span class="sxs-lookup"><span data-stu-id="45952-184">descendant-or-self</span></span>|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="45952-185">veya</span><span class="sxs-lookup"><span data-stu-id="45952-185">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|
|<span data-ttu-id="45952-186">aşağıdaki-eşdüzey</span><span class="sxs-lookup"><span data-stu-id="45952-186">following-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="45952-187">veya</span><span class="sxs-lookup"><span data-stu-id="45952-187">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|
|<span data-ttu-id="45952-188">önceki eşdüzey</span><span class="sxs-lookup"><span data-stu-id="45952-188">preceding-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="45952-189">veya</span><span class="sxs-lookup"><span data-stu-id="45952-189">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|
|<span data-ttu-id="45952-190">Sonraki</span><span class="sxs-lookup"><span data-stu-id="45952-190">following</span></span>|<span data-ttu-id="45952-191">Doğrudan eşdeğer olmaz.</span><span class="sxs-lookup"><span data-stu-id="45952-191">No direct equivalent.</span></span>|
|<span data-ttu-id="45952-192">SCRIPT</span><span class="sxs-lookup"><span data-stu-id="45952-192">preceding</span></span>|<span data-ttu-id="45952-193">Doğrudan eşdeğer olmaz.</span><span class="sxs-lookup"><span data-stu-id="45952-193">No direct equivalent.</span></span>|
