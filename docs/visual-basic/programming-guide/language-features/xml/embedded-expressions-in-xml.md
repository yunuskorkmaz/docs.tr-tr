---
title: XML'de Katıştırılmış İfadeler (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
ms.openlocfilehash: 4c96665994a7e56bc70f72b66d5922f5a6472a13
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58827581"
---
# <a name="embedded-expressions-in-xml-visual-basic"></a><span data-ttu-id="d8eef-102">XML'de Katıştırılmış İfadeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8eef-102">Embedded Expressions in XML (Visual Basic)</span></span>
<span data-ttu-id="d8eef-103">Katıştırılmış ifadeler, çalışma zamanında değerlendirilen bir ifade içeren bir XML sabit değerleri oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d8eef-103">Embedded expressions enable you to create XML literals that contain expressions that are evaluated at run time.</span></span> <span data-ttu-id="d8eef-104">Katıştırılmış bir ifade sözdizimi `<%=` `expression` `%>`, olduğu aynı söz dizimi içinde kullanılan [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d8eef-104">The syntax for an embedded expression is `<%=` `expression` `%>`, which is the same as the syntax used in [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].</span></span>  
  
 <span data-ttu-id="d8eef-105">Örneğin, bir XML öğesi değişmez değeri katıştırılmış ifadeler sabit metin içerikli birleştirme oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8eef-105">For example, you can create an XML element literal, combining embedded expressions with literal text content.</span></span>  
  
 [!code-vb[VbXMLSamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#27)]  
  
 <span data-ttu-id="d8eef-106">Varsa `isbnNumber` 12345 tamsayı içerir ve `modifiedDate` tarihi içeren 3/5/olduğunda bu kodu yürütür, değerini 2006 `book` olan:</span><span class="sxs-lookup"><span data-stu-id="d8eef-106">If `isbnNumber` contains the integer 12345 and `modifiedDate` contains the date 3/5/2006, when this code executes, the value of `book` is:</span></span>  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a><span data-ttu-id="d8eef-107">Gömülü deyim konumu ve doğrulama</span><span class="sxs-lookup"><span data-stu-id="d8eef-107">Embedded Expression Location and Validation</span></span>  
 <span data-ttu-id="d8eef-108">XML değişmez ifadelerinde içinde belirli konumlara yalnızca katıştırılmış ifadeler görünür.</span><span class="sxs-lookup"><span data-stu-id="d8eef-108">Embedded expressions can appear only at certain locations within XML literal expressions.</span></span> <span data-ttu-id="d8eef-109">İfade türleri ifade konumu denetimleri döndürebilir ve nasıl `Nothing` ele alınır.</span><span class="sxs-lookup"><span data-stu-id="d8eef-109">The expression location controls which types the expression can return and how `Nothing` is handled.</span></span> <span data-ttu-id="d8eef-110">Aşağıdaki tabloda, izin verilen konumlar ve katıştırılmış ifadeler türleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d8eef-110">The following table describes the allowed locations and types of embedded expressions.</span></span>  
  
|<span data-ttu-id="d8eef-111">Konumda sabit değer</span><span class="sxs-lookup"><span data-stu-id="d8eef-111">Location in literal</span></span>|<span data-ttu-id="d8eef-112">İfadenin türü</span><span class="sxs-lookup"><span data-stu-id="d8eef-112">Type of expression</span></span>|<span data-ttu-id="d8eef-113">İşleme `Nothing`</span><span class="sxs-lookup"><span data-stu-id="d8eef-113">Handling of `Nothing`</span></span>|  
|---|---|---|  
|<span data-ttu-id="d8eef-114">XML öğesi adı</span><span class="sxs-lookup"><span data-stu-id="d8eef-114">XML element name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="d8eef-115">Hata</span><span class="sxs-lookup"><span data-stu-id="d8eef-115">Error</span></span>|  
|<span data-ttu-id="d8eef-116">XML öğesi içeriği</span><span class="sxs-lookup"><span data-stu-id="d8eef-116">XML element content</span></span>|<span data-ttu-id="d8eef-117">`Object` veya dizi `Object`</span><span class="sxs-lookup"><span data-stu-id="d8eef-117">`Object` or array of `Object`</span></span>|<span data-ttu-id="d8eef-118">Yoksayıldı</span><span class="sxs-lookup"><span data-stu-id="d8eef-118">Ignored</span></span>|  
|<span data-ttu-id="d8eef-119">XML öğesi öznitelik adı</span><span class="sxs-lookup"><span data-stu-id="d8eef-119">XML element attribute name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="d8eef-120">Hata, öznitelik değeri de olmadığı sürece `Nothing`</span><span class="sxs-lookup"><span data-stu-id="d8eef-120">Error, unless the attribute value is also `Nothing`</span></span>|  
|<span data-ttu-id="d8eef-121">XML öğesi öznitelik değeri</span><span class="sxs-lookup"><span data-stu-id="d8eef-121">XML element attribute value</span></span>|`Object`|<span data-ttu-id="d8eef-122">Öznitelik bildirim yoksayıldı</span><span class="sxs-lookup"><span data-stu-id="d8eef-122">Attribute declaration ignored</span></span>|  
|<span data-ttu-id="d8eef-123">XML öğesi özniteliği</span><span class="sxs-lookup"><span data-stu-id="d8eef-123">XML element attribute</span></span>|<span data-ttu-id="d8eef-124"><xref:System.Xml.Linq.XAttribute> veya bir koleksiyonu <xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="d8eef-124"><xref:System.Xml.Linq.XAttribute> or a collection of <xref:System.Xml.Linq.XAttribute></span></span>|<span data-ttu-id="d8eef-125">Yoksayıldı</span><span class="sxs-lookup"><span data-stu-id="d8eef-125">Ignored</span></span>|  
|<span data-ttu-id="d8eef-126">XML belgesi kök öğesi</span><span class="sxs-lookup"><span data-stu-id="d8eef-126">XML document root element</span></span>|<span data-ttu-id="d8eef-127"><xref:System.Xml.Linq.XElement> veya bir koleksiyonu <xref:System.Xml.Linq.XElement> nesne ve tercihe bağlı sayıda <xref:System.Xml.Linq.XProcessingInstruction> ve <xref:System.Xml.Linq.XComment> nesneleri</span><span class="sxs-lookup"><span data-stu-id="d8eef-127"><xref:System.Xml.Linq.XElement> or a collection of one <xref:System.Xml.Linq.XElement> object and an arbitrary number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects</span></span>|<span data-ttu-id="d8eef-128">Yoksayıldı</span><span class="sxs-lookup"><span data-stu-id="d8eef-128">Ignored</span></span>|  
  
-   <span data-ttu-id="d8eef-129">Bir XML öğesinin adındaki katıştırılmış bir ifade örneği:</span><span class="sxs-lookup"><span data-stu-id="d8eef-129">Example of an embedded expression in an XML element name:</span></span>  
  
     [!code-vb[VbXMLSamples#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#32)]  
  
-   <span data-ttu-id="d8eef-130">Bir XML öğesi içeriğinde katıştırılmış bir ifade örneği:</span><span class="sxs-lookup"><span data-stu-id="d8eef-130">Example of an embedded expression in the content of an XML element:</span></span>  
  
     [!code-vb[VbXMLSamples#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#33)]  
  
-   <span data-ttu-id="d8eef-131">Bir XML öğesi öznitelik adı bir gömülü ifade örneği:</span><span class="sxs-lookup"><span data-stu-id="d8eef-131">Example of an embedded expression in an XML element attribute name:</span></span>  
  
     [!code-vb[VbXMLSamples#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#34)]  
  
-   <span data-ttu-id="d8eef-132">Gömülü deyim bir XML öğesi öznitelik değeri örneği:</span><span class="sxs-lookup"><span data-stu-id="d8eef-132">Example of an embedded expression in an XML element attribute value:</span></span>  
  
     [!code-vb[VbXMLSamples#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#35)]  
  
-   <span data-ttu-id="d8eef-133">Bir XML öğesi özniteliği katıştırılmış bir ifadede örneği:</span><span class="sxs-lookup"><span data-stu-id="d8eef-133">Example of an embedded expression in an XML element attribute:</span></span>  
  
     [!code-vb[VbXMLSamples#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#36)]  
  
-   <span data-ttu-id="d8eef-134">Bir XML belgesi kök öğesi içinde katıştırılmış bir ifade örneği:</span><span class="sxs-lookup"><span data-stu-id="d8eef-134">Example of an embedded expression in an XML document root element:</span></span>  
  
     [!code-vb[VbXMLSamples#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#37)]  
  
 <span data-ttu-id="d8eef-135">Etkinleştirirseniz `Option Strict`, derleyici her katıştırılmış ifadenin türü için gerekli tür widens denetler.</span><span class="sxs-lookup"><span data-stu-id="d8eef-135">If you enable `Option Strict`, the compiler checks that the type of each embedded expression widens to the required type.</span></span> <span data-ttu-id="d8eef-136">Tek özel durum için kod çalıştığında doğrulanır bir XML belgesi kök öğesidir.</span><span class="sxs-lookup"><span data-stu-id="d8eef-136">The only exception is for the root element of an XML document, which is verified when the code runs.</span></span> <span data-ttu-id="d8eef-137">Olmadan derlerseniz `Option Strict`, türündeki ifadeler katıştırabilirsiniz `Object` ve çalışma zamanında türlerine doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="d8eef-137">If you compile without `Option Strict`, you can embed expressions of type `Object` and their type is verified at run time.</span></span>  
  
 <span data-ttu-id="d8eef-138">İçeriğin bulunduğu, isteğe bağlı konumlarda içeren ifadeler katıştırılmış `Nothing` göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="d8eef-138">In locations where content is optional, embedded expressions that contain `Nothing` are ignored.</span></span> <span data-ttu-id="d8eef-139">Bunun anlamı, öznitelik değerleri, öğe içerik denetleme gerekmez ve dizi öğesi olmayan `Nothing` önce bir XML değişmez değeri kullanın.</span><span class="sxs-lookup"><span data-stu-id="d8eef-139">This means you do not have to check that element content, attribute values, and array elements are not `Nothing` before you use an XML literal.</span></span> <span data-ttu-id="d8eef-140">Öğe ve öznitelik adları gibi bir değer olamaz gerekli `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="d8eef-140">Required values, such as element and attribute names, cannot be `Nothing`.</span></span>  
  
 <span data-ttu-id="d8eef-141">Katıştırılmış bir ifade sabit değeri belirli bir tür kullanma hakkında daha fazla bilgi için bkz. [XML belgesi değişmez değeri](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [XML öğesi değişmez değeri](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="d8eef-141">For more information about using an embedded expression in a particular type of literal, see [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="scoping-rules"></a><span data-ttu-id="d8eef-142">Kapsam kuralları</span><span class="sxs-lookup"><span data-stu-id="d8eef-142">Scoping Rules</span></span>  
 <span data-ttu-id="d8eef-143">Derleyici uygun bir değişmez değer türü için bir oluşturucu çağrısı her XML değişmez değer dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="d8eef-143">The compiler converts each XML literal into a constructor call for the appropriate literal type.</span></span> <span data-ttu-id="d8eef-144">Katıştırılmış ifadelerde XML sabit ve değişmez değer içeriğine oluşturucusuna bağımsız değişken olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="d8eef-144">The literal content and embedded expressions in an XML literal are passed as arguments to the constructor.</span></span> <span data-ttu-id="d8eef-145">Başka bir deyişle, XML değişmez değer için kullanılabilir tüm Visual Basic programlama öğeleri de kendi katıştırılmış ifadeler için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d8eef-145">This means that all Visual Basic programming elements available to an XML literal are also available to its embedded expressions.</span></span>  
  
 <span data-ttu-id="d8eef-146">XML değişmez değer içinde XML ad alanı ön ekleri ile bildirilmiş erişebileceğiniz `Imports` deyimi.</span><span class="sxs-lookup"><span data-stu-id="d8eef-146">Within an XML literal, you can access the XML namespace prefixes declared with the `Imports` statement.</span></span> <span data-ttu-id="d8eef-147">Yeni bir XML ad alanı öneki bildirin veya bir öğedeki kullanarak varolan bir XML ad alanı öneki gölge `xmlns` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d8eef-147">You can declare a new XML namespace prefix, or shadow an existing XML namespace prefix, in an element by using the `xmlns` attribute.</span></span> <span data-ttu-id="d8eef-148">Yeni ad alanı, o öğenin alt düğümleri, ancak XML değişmez değerlerine katıştırılmış ifadeler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d8eef-148">The new namespace is available to the child nodes of that element, but not to XML literals in embedded expressions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d8eef-149">Kullanarak bir XML ad alanı öneki bildirdiğinizde `xmlns` namespace özniteliği, öznitelik değeri bir sabit dize olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d8eef-149">When you declare an XML namespace prefix by using the `xmlns` namespace attribute, the attribute value must be a constant string.</span></span> <span data-ttu-id="d8eef-150">Bu bağlamda kullanarak `xmlns` özniteliktir kullanma gibi `Imports` deyimi bir XML ad alanı bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="d8eef-150">In this regard, using the `xmlns` attribute is like using the `Imports` statement to declare an XML namespace.</span></span> <span data-ttu-id="d8eef-151">XML ad alanı değeri belirtmek için bir katıştırılmış deyim kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="d8eef-151">You cannot use an embedded expression to specify the XML namespace value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8eef-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8eef-152">See also</span></span>

- [<span data-ttu-id="d8eef-153">Visual Basic'de XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="d8eef-153">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="d8eef-154">XML Belgesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="d8eef-154">XML Document Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [<span data-ttu-id="d8eef-155">XML Öğesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="d8eef-155">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="d8eef-156">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="d8eef-156">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="d8eef-157">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="d8eef-157">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="d8eef-158">XML Değişmez Değerlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d8eef-158">XML Literals Overview</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
