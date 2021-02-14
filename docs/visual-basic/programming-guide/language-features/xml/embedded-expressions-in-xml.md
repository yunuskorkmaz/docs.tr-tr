---
description: "Daha fazla bilgi edinin: XML 'de katıştırılmış Ifadeler (Visual Basic)"
title: XML'de Katıştırılmış İfadeler
ms.date: 07/20/2015
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
ms.openlocfilehash: 52cf8341cb0a55abad230543bbc6367aea071142
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433193"
---
# <a name="embedded-expressions-in-xml-visual-basic"></a><span data-ttu-id="c6c9d-103">XML'de Katıştırılmış İfadeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6c9d-103">Embedded Expressions in XML (Visual Basic)</span></span>

<span data-ttu-id="c6c9d-104">Katıştırılmış ifadeler çalışma zamanında değerlendirilen ifadeler içeren XML sabit değerleri oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6c9d-104">Embedded expressions enable you to create XML literals that contain expressions that are evaluated at run time.</span></span> <span data-ttu-id="c6c9d-105">Gömülü ifade için sözdizimi `<%=` `expression` `%>` , ASP.NET içinde kullanılan söz dizimi ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="c6c9d-105">The syntax for an embedded expression is `<%=` `expression` `%>`, which is the same as the syntax used in ASP.NET.</span></span>  
  
 <span data-ttu-id="c6c9d-106">Örneğin, katıştırılmış ifadeleri sabit metin içeriğiyle birleştiren bir XML öğesi değişmez değeri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6c9d-106">For example, you can create an XML element literal, combining embedded expressions with literal text content.</span></span>  
  
 [!code-vb[VbXMLSamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#27)]  
  
 <span data-ttu-id="c6c9d-107">Eğer `isbnNumber` 12345 tamsayısını içeriyorsa ve `modifiedDate` 3/5/2006 tarihini içeriyorsa, değeri `book` Şu şekilde olur:</span><span class="sxs-lookup"><span data-stu-id="c6c9d-107">If `isbnNumber` contains the integer 12345 and `modifiedDate` contains the date 3/5/2006, when this code executes, the value of `book` is:</span></span>  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a><span data-ttu-id="c6c9d-108">Katıştırılmış Ifade konumu ve doğrulama</span><span class="sxs-lookup"><span data-stu-id="c6c9d-108">Embedded Expression Location and Validation</span></span>  

 <span data-ttu-id="c6c9d-109">Katıştırılmış ifadeler yalnızca XML sabit ifadeleri içindeki belirli konumlarda görünebilir.</span><span class="sxs-lookup"><span data-stu-id="c6c9d-109">Embedded expressions can appear only at certain locations within XML literal expressions.</span></span> <span data-ttu-id="c6c9d-110">İfade konumu, ifadenin hangi türleri döndürebileceğini ve nasıl işlendiğini denetler `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="c6c9d-110">The expression location controls which types the expression can return and how `Nothing` is handled.</span></span> <span data-ttu-id="c6c9d-111">Aşağıdaki tabloda, eklenmiş ifadelerin izin verilen konumları ve türleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c6c9d-111">The following table describes the allowed locations and types of embedded expressions.</span></span>  
  
|<span data-ttu-id="c6c9d-112">Değişmez değer içindeki konum</span><span class="sxs-lookup"><span data-stu-id="c6c9d-112">Location in literal</span></span>|<span data-ttu-id="c6c9d-113">İfade türü</span><span class="sxs-lookup"><span data-stu-id="c6c9d-113">Type of expression</span></span>|<span data-ttu-id="c6c9d-114">İşleme `Nothing`</span><span class="sxs-lookup"><span data-stu-id="c6c9d-114">Handling of `Nothing`</span></span>|  
|---|---|---|  
|<span data-ttu-id="c6c9d-115">XML öğesi adı</span><span class="sxs-lookup"><span data-stu-id="c6c9d-115">XML element name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="c6c9d-116">Hata</span><span class="sxs-lookup"><span data-stu-id="c6c9d-116">Error</span></span>|  
|<span data-ttu-id="c6c9d-117">XML öğesi içeriği</span><span class="sxs-lookup"><span data-stu-id="c6c9d-117">XML element content</span></span>|<span data-ttu-id="c6c9d-118">`Object` veya dizisi `Object`</span><span class="sxs-lookup"><span data-stu-id="c6c9d-118">`Object` or array of `Object`</span></span>|<span data-ttu-id="c6c9d-119">Yoksayıldı</span><span class="sxs-lookup"><span data-stu-id="c6c9d-119">Ignored</span></span>|  
|<span data-ttu-id="c6c9d-120">XML öğesi öznitelik adı</span><span class="sxs-lookup"><span data-stu-id="c6c9d-120">XML element attribute name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="c6c9d-121">Öznitelik değeri de yoksa, hata `Nothing`</span><span class="sxs-lookup"><span data-stu-id="c6c9d-121">Error, unless the attribute value is also `Nothing`</span></span>|  
|<span data-ttu-id="c6c9d-122">XML öğesi öznitelik değeri</span><span class="sxs-lookup"><span data-stu-id="c6c9d-122">XML element attribute value</span></span>|`Object`|<span data-ttu-id="c6c9d-123">Öznitelik bildirimi yoksayıldı</span><span class="sxs-lookup"><span data-stu-id="c6c9d-123">Attribute declaration ignored</span></span>|  
|<span data-ttu-id="c6c9d-124">XML öğesi özniteliği</span><span class="sxs-lookup"><span data-stu-id="c6c9d-124">XML element attribute</span></span>|<span data-ttu-id="c6c9d-125"><xref:System.Xml.Linq.XAttribute> veya bir koleksiyonu <xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="c6c9d-125"><xref:System.Xml.Linq.XAttribute> or a collection of <xref:System.Xml.Linq.XAttribute></span></span>|<span data-ttu-id="c6c9d-126">Yoksayıldı</span><span class="sxs-lookup"><span data-stu-id="c6c9d-126">Ignored</span></span>|  
|<span data-ttu-id="c6c9d-127">XML belgesi kök öğesi</span><span class="sxs-lookup"><span data-stu-id="c6c9d-127">XML document root element</span></span>|<span data-ttu-id="c6c9d-128"><xref:System.Xml.Linq.XElement> ya da bir <xref:System.Xml.Linq.XElement> nesne ve rastgele sayıda <xref:System.Xml.Linq.XProcessingInstruction> ve <xref:System.Xml.Linq.XComment> nesne koleksiyonu</span><span class="sxs-lookup"><span data-stu-id="c6c9d-128"><xref:System.Xml.Linq.XElement> or a collection of one <xref:System.Xml.Linq.XElement> object and an arbitrary number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects</span></span>|<span data-ttu-id="c6c9d-129">Yoksayıldı</span><span class="sxs-lookup"><span data-stu-id="c6c9d-129">Ignored</span></span>|  
  
- <span data-ttu-id="c6c9d-130">Bir XML öğe adında katıştırılmış ifade örneği:</span><span class="sxs-lookup"><span data-stu-id="c6c9d-130">Example of an embedded expression in an XML element name:</span></span>  
  
     [!code-vb[VbXMLSamples#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#32)]  
  
- <span data-ttu-id="c6c9d-131">XML öğesi içeriğinde gömülü ifade örneği:</span><span class="sxs-lookup"><span data-stu-id="c6c9d-131">Example of an embedded expression in the content of an XML element:</span></span>  
  
     [!code-vb[VbXMLSamples#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#33)]  
  
- <span data-ttu-id="c6c9d-132">XML öğesi öznitelik adında gömülü ifade örneği:</span><span class="sxs-lookup"><span data-stu-id="c6c9d-132">Example of an embedded expression in an XML element attribute name:</span></span>  
  
     [!code-vb[VbXMLSamples#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#34)]  
  
- <span data-ttu-id="c6c9d-133">XML öğesi öznitelik değerinde gömülü ifade örneği:</span><span class="sxs-lookup"><span data-stu-id="c6c9d-133">Example of an embedded expression in an XML element attribute value:</span></span>  
  
     [!code-vb[VbXMLSamples#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#35)]  
  
- <span data-ttu-id="c6c9d-134">XML öğesi özniteliğinde gömülü ifade örneği:</span><span class="sxs-lookup"><span data-stu-id="c6c9d-134">Example of an embedded expression in an XML element attribute:</span></span>  
  
     [!code-vb[VbXMLSamples#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#36)]  
  
- <span data-ttu-id="c6c9d-135">XML belgesi kök öğesinde katıştırılmış ifade örneği:</span><span class="sxs-lookup"><span data-stu-id="c6c9d-135">Example of an embedded expression in an XML document root element:</span></span>  
  
     [!code-vb[VbXMLSamples#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#37)]  
  
 <span data-ttu-id="c6c9d-136">`Option Strict`' I etkinleştirirseniz, derleyici her bir katıştırılmış ifadenin türünün gerekli türe widens olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="c6c9d-136">If you enable `Option Strict`, the compiler checks that the type of each embedded expression widens to the required type.</span></span> <span data-ttu-id="c6c9d-137">Tek özel durum, kod çalıştırıldığında doğrulanan bir XML belgesinin kök öğesi içindir.</span><span class="sxs-lookup"><span data-stu-id="c6c9d-137">The only exception is for the root element of an XML document, which is verified when the code runs.</span></span> <span data-ttu-id="c6c9d-138">Olmadan derlerseniz `Option Strict` , türünde ifadeler ekleyebilirsiniz `Object` ve bunların türleri çalışma zamanında doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="c6c9d-138">If you compile without `Option Strict`, you can embed expressions of type `Object` and their type is verified at run time.</span></span>  
  
 <span data-ttu-id="c6c9d-139">İçeriğin isteğe bağlı olduğu konumlarda, içeren katıştırılmış ifadeler `Nothing` yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="c6c9d-139">In locations where content is optional, embedded expressions that contain `Nothing` are ignored.</span></span> <span data-ttu-id="c6c9d-140">Bu, `Nothing` BIR XML sabit değeri kullanmadan önce öğe içeriği, öznitelik değerleri ve dizi öğelerinin olmadığını denetlemeniz gerekmediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c6c9d-140">This means you do not have to check that element content, attribute values, and array elements are not `Nothing` before you use an XML literal.</span></span> <span data-ttu-id="c6c9d-141">Öğe ve öznitelik adları gibi gerekli değerler olamaz `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="c6c9d-141">Required values, such as element and attribute names, cannot be `Nothing`.</span></span>  
  
 <span data-ttu-id="c6c9d-142">Belirli bir sabit değer türünde gömülü bir ifade kullanma hakkında daha fazla bilgi için bkz. [XML Document Literal](../../../language-reference/xml-literals/xml-document-literal.md), [XML öğesi değişmez değeri](../../../language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="c6c9d-142">For more information about using an embedded expression in a particular type of literal, see [XML Document Literal](../../../language-reference/xml-literals/xml-document-literal.md), [XML Element Literal](../../../language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="scoping-rules"></a><span data-ttu-id="c6c9d-143">Kapsam oluşturma kuralları</span><span class="sxs-lookup"><span data-stu-id="c6c9d-143">Scoping Rules</span></span>  

 <span data-ttu-id="c6c9d-144">Derleyici, her XML sabit değerini uygun değişmez değer türü için bir Oluşturucu çağrısına dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="c6c9d-144">The compiler converts each XML literal into a constructor call for the appropriate literal type.</span></span> <span data-ttu-id="c6c9d-145">Bir XML sabit değerinde değişmez içerik ve katıştırılmış ifadeler, oluşturucuya bağımsız değişken olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="c6c9d-145">The literal content and embedded expressions in an XML literal are passed as arguments to the constructor.</span></span> <span data-ttu-id="c6c9d-146">Bu, bir XML sabit değeri için kullanılabilen tüm Visual Basic programlama öğelerinin katıştırılmış ifadeler tarafından da kullanılabildiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c6c9d-146">This means that all Visual Basic programming elements available to an XML literal are also available to its embedded expressions.</span></span>  
  
 <span data-ttu-id="c6c9d-147">Bir XML sabit değeri içinde, ifadesiyle belirtilen XML ad alanı öneklerine erişebilirsiniz `Imports` .</span><span class="sxs-lookup"><span data-stu-id="c6c9d-147">Within an XML literal, you can access the XML namespace prefixes declared with the `Imports` statement.</span></span> <span data-ttu-id="c6c9d-148">Özniteliğini kullanarak bir öğesinde yeni bir XML ad alanı ön eki veya var olan bir XML ad alanı ön ekini gölgelendirebilmeniz gerekir `xmlns` .</span><span class="sxs-lookup"><span data-stu-id="c6c9d-148">You can declare a new XML namespace prefix, or shadow an existing XML namespace prefix, in an element by using the `xmlns` attribute.</span></span> <span data-ttu-id="c6c9d-149">Yeni ad alanı, bu öğenin alt düğümleri için kullanılabilir ancak gömülü ifadelerde XML değişmez değerleri için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c6c9d-149">The new namespace is available to the child nodes of that element, but not to XML literals in embedded expressions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c6c9d-150">Ad alanı özniteliğini kullanarak bir XML ad alanı öneki bildirdiğinizde `xmlns` , öznitelik değeri bir sabit dize olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c6c9d-150">When you declare an XML namespace prefix by using the `xmlns` namespace attribute, the attribute value must be a constant string.</span></span> <span data-ttu-id="c6c9d-151">Bu şekilde, `xmlns` özniteliği kullanmak `Imports` bir XML ad alanı bildirmek için ifadesini kullanmak gibidir.</span><span class="sxs-lookup"><span data-stu-id="c6c9d-151">In this regard, using the `xmlns` attribute is like using the `Imports` statement to declare an XML namespace.</span></span> <span data-ttu-id="c6c9d-152">XML ad alanı değerini belirtmek için gömülü bir ifade kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="c6c9d-152">You cannot use an embedded expression to specify the XML namespace value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6c9d-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6c9d-153">See also</span></span>

- [<span data-ttu-id="c6c9d-154">Visual Basic'de XML Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c6c9d-154">Creating XML in Visual Basic</span></span>](creating-xml.md)
- [<span data-ttu-id="c6c9d-155">XML Belgesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="c6c9d-155">XML Document Literal</span></span>](../../../language-reference/xml-literals/xml-document-literal.md)
- [<span data-ttu-id="c6c9d-156">XML Öğesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="c6c9d-156">XML Element Literal</span></span>](../../../language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="c6c9d-157">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="c6c9d-157">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="c6c9d-158">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="c6c9d-158">Imports Statement (.NET Namespace and Type)</span></span>](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="c6c9d-159">XML Değişmez Değerlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c6c9d-159">XML Literals Overview</span></span>](xml-literals-overview.md)
