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
ms.openlocfilehash: 525fa04db86a299d88e1612aac76d014f35124eb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922627"
---
# <a name="embedded-expressions-in-xml-visual-basic"></a><span data-ttu-id="690f4-102">XML'de Katıştırılmış İfadeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="690f4-102">Embedded Expressions in XML (Visual Basic)</span></span>
<span data-ttu-id="690f4-103">Katıştırılmış ifadeler çalışma zamanında değerlendirilen ifadeler içeren XML sabit değerleri oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="690f4-103">Embedded expressions enable you to create XML literals that contain expressions that are evaluated at run time.</span></span> <span data-ttu-id="690f4-104">Gömülü ifade `<%=` `expression` içinsözdizimi,ASP.NETiçindekullanılansöz`%>`dizimi ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="690f4-104">The syntax for an embedded expression is `<%=` `expression` `%>`, which is the same as the syntax used in ASP.NET.</span></span>  
  
 <span data-ttu-id="690f4-105">Örneğin, katıştırılmış ifadeleri sabit metin içeriğiyle birleştiren bir XML öğesi değişmez değeri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="690f4-105">For example, you can create an XML element literal, combining embedded expressions with literal text content.</span></span>  
  
 [!code-vb[VbXMLSamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#27)]  
  
 <span data-ttu-id="690f4-106">Eğer `isbnNumber` 12345 tamsayısını içeriyorsa ve `modifiedDate` 3/5/2006 tarihini içeriyorsa, değeri `book` şu şekilde olur:</span><span class="sxs-lookup"><span data-stu-id="690f4-106">If `isbnNumber` contains the integer 12345 and `modifiedDate` contains the date 3/5/2006, when this code executes, the value of `book` is:</span></span>  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a><span data-ttu-id="690f4-107">Katıştırılmış Ifade konumu ve doğrulama</span><span class="sxs-lookup"><span data-stu-id="690f4-107">Embedded Expression Location and Validation</span></span>  
 <span data-ttu-id="690f4-108">Katıştırılmış ifadeler yalnızca XML sabit ifadeleri içindeki belirli konumlarda görünebilir.</span><span class="sxs-lookup"><span data-stu-id="690f4-108">Embedded expressions can appear only at certain locations within XML literal expressions.</span></span> <span data-ttu-id="690f4-109">İfade konumu, ifadenin hangi türleri döndürebileceğini ve nasıl `Nothing` işlendiğini denetler.</span><span class="sxs-lookup"><span data-stu-id="690f4-109">The expression location controls which types the expression can return and how `Nothing` is handled.</span></span> <span data-ttu-id="690f4-110">Aşağıdaki tabloda, eklenmiş ifadelerin izin verilen konumları ve türleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="690f4-110">The following table describes the allowed locations and types of embedded expressions.</span></span>  
  
|<span data-ttu-id="690f4-111">Değişmez değer içindeki konum</span><span class="sxs-lookup"><span data-stu-id="690f4-111">Location in literal</span></span>|<span data-ttu-id="690f4-112">İfade türü</span><span class="sxs-lookup"><span data-stu-id="690f4-112">Type of expression</span></span>|<span data-ttu-id="690f4-113">İşleme`Nothing`</span><span class="sxs-lookup"><span data-stu-id="690f4-113">Handling of `Nothing`</span></span>|  
|---|---|---|  
|<span data-ttu-id="690f4-114">XML öğesi adı</span><span class="sxs-lookup"><span data-stu-id="690f4-114">XML element name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="690f4-115">Hata</span><span class="sxs-lookup"><span data-stu-id="690f4-115">Error</span></span>|  
|<span data-ttu-id="690f4-116">XML öğesi içeriği</span><span class="sxs-lookup"><span data-stu-id="690f4-116">XML element content</span></span>|<span data-ttu-id="690f4-117">`Object`veya dizisi`Object`</span><span class="sxs-lookup"><span data-stu-id="690f4-117">`Object` or array of `Object`</span></span>|<span data-ttu-id="690f4-118">Yoksayıldı</span><span class="sxs-lookup"><span data-stu-id="690f4-118">Ignored</span></span>|  
|<span data-ttu-id="690f4-119">XML öğesi öznitelik adı</span><span class="sxs-lookup"><span data-stu-id="690f4-119">XML element attribute name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="690f4-120">Öznitelik değeri de yoksa, hata`Nothing`</span><span class="sxs-lookup"><span data-stu-id="690f4-120">Error, unless the attribute value is also `Nothing`</span></span>|  
|<span data-ttu-id="690f4-121">XML öğesi öznitelik değeri</span><span class="sxs-lookup"><span data-stu-id="690f4-121">XML element attribute value</span></span>|`Object`|<span data-ttu-id="690f4-122">Öznitelik bildirimi yoksayıldı</span><span class="sxs-lookup"><span data-stu-id="690f4-122">Attribute declaration ignored</span></span>|  
|<span data-ttu-id="690f4-123">XML öğesi özniteliği</span><span class="sxs-lookup"><span data-stu-id="690f4-123">XML element attribute</span></span>|<span data-ttu-id="690f4-124"><xref:System.Xml.Linq.XAttribute>veya bir koleksiyonu<xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="690f4-124"><xref:System.Xml.Linq.XAttribute> or a collection of <xref:System.Xml.Linq.XAttribute></span></span>|<span data-ttu-id="690f4-125">Yoksayıldı</span><span class="sxs-lookup"><span data-stu-id="690f4-125">Ignored</span></span>|  
|<span data-ttu-id="690f4-126">XML belgesi kök öğesi</span><span class="sxs-lookup"><span data-stu-id="690f4-126">XML document root element</span></span>|<span data-ttu-id="690f4-127"><xref:System.Xml.Linq.XElement>ya da bir <xref:System.Xml.Linq.XElement> nesne ve rastgele <xref:System.Xml.Linq.XProcessingInstruction> sayıda ve <xref:System.Xml.Linq.XComment> nesne koleksiyonu</span><span class="sxs-lookup"><span data-stu-id="690f4-127"><xref:System.Xml.Linq.XElement> or a collection of one <xref:System.Xml.Linq.XElement> object and an arbitrary number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects</span></span>|<span data-ttu-id="690f4-128">Yoksayıldı</span><span class="sxs-lookup"><span data-stu-id="690f4-128">Ignored</span></span>|  
  
- <span data-ttu-id="690f4-129">Bir XML öğe adında katıştırılmış ifade örneği:</span><span class="sxs-lookup"><span data-stu-id="690f4-129">Example of an embedded expression in an XML element name:</span></span>  
  
     [!code-vb[VbXMLSamples#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#32)]  
  
- <span data-ttu-id="690f4-130">XML öğesi içeriğinde gömülü ifade örneği:</span><span class="sxs-lookup"><span data-stu-id="690f4-130">Example of an embedded expression in the content of an XML element:</span></span>  
  
     [!code-vb[VbXMLSamples#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#33)]  
  
- <span data-ttu-id="690f4-131">XML öğesi öznitelik adında gömülü ifade örneği:</span><span class="sxs-lookup"><span data-stu-id="690f4-131">Example of an embedded expression in an XML element attribute name:</span></span>  
  
     [!code-vb[VbXMLSamples#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#34)]  
  
- <span data-ttu-id="690f4-132">XML öğesi öznitelik değerinde gömülü ifade örneği:</span><span class="sxs-lookup"><span data-stu-id="690f4-132">Example of an embedded expression in an XML element attribute value:</span></span>  
  
     [!code-vb[VbXMLSamples#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#35)]  
  
- <span data-ttu-id="690f4-133">XML öğesi özniteliğinde gömülü ifade örneği:</span><span class="sxs-lookup"><span data-stu-id="690f4-133">Example of an embedded expression in an XML element attribute:</span></span>  
  
     [!code-vb[VbXMLSamples#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#36)]  
  
- <span data-ttu-id="690f4-134">XML belgesi kök öğesinde katıştırılmış ifade örneği:</span><span class="sxs-lookup"><span data-stu-id="690f4-134">Example of an embedded expression in an XML document root element:</span></span>  
  
     [!code-vb[VbXMLSamples#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#37)]  
  
 <span data-ttu-id="690f4-135">' I etkinleştirirseniz `Option Strict`, derleyici her bir katıştırılmış ifadenin türünün gerekli türe widens olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="690f4-135">If you enable `Option Strict`, the compiler checks that the type of each embedded expression widens to the required type.</span></span> <span data-ttu-id="690f4-136">Tek özel durum, kod çalıştırıldığında doğrulanan bir XML belgesinin kök öğesi içindir.</span><span class="sxs-lookup"><span data-stu-id="690f4-136">The only exception is for the root element of an XML document, which is verified when the code runs.</span></span> <span data-ttu-id="690f4-137">Olmadan `Option Strict`derlerseniz, türünde `Object` ifadeler ekleyebilirsiniz ve bunların türleri çalışma zamanında doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="690f4-137">If you compile without `Option Strict`, you can embed expressions of type `Object` and their type is verified at run time.</span></span>  
  
 <span data-ttu-id="690f4-138">İçeriğin isteğe bağlı olduğu konumlarda, içeren katıştırılmış ifadeler `Nothing` yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="690f4-138">In locations where content is optional, embedded expressions that contain `Nothing` are ignored.</span></span> <span data-ttu-id="690f4-139">Bu, bir XML sabit değeri kullanmadan `Nothing` önce öğe içeriği, öznitelik değerleri ve dizi öğelerinin olmadığını denetlemeniz gerekmediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="690f4-139">This means you do not have to check that element content, attribute values, and array elements are not `Nothing` before you use an XML literal.</span></span> <span data-ttu-id="690f4-140">Öğe ve öznitelik adları `Nothing`gibi gerekli değerler olamaz.</span><span class="sxs-lookup"><span data-stu-id="690f4-140">Required values, such as element and attribute names, cannot be `Nothing`.</span></span>  
  
 <span data-ttu-id="690f4-141">Belirli bir sabit değer türünde gömülü bir ifade kullanma hakkında daha fazla bilgi için bkz. [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [XML öğesi değişmez değeri](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="690f4-141">For more information about using an embedded expression in a particular type of literal, see [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="scoping-rules"></a><span data-ttu-id="690f4-142">Kapsam oluşturma kuralları</span><span class="sxs-lookup"><span data-stu-id="690f4-142">Scoping Rules</span></span>  
 <span data-ttu-id="690f4-143">Derleyici, her XML sabit değerini uygun değişmez değer türü için bir Oluşturucu çağrısına dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="690f4-143">The compiler converts each XML literal into a constructor call for the appropriate literal type.</span></span> <span data-ttu-id="690f4-144">Bir XML sabit değerinde değişmez içerik ve katıştırılmış ifadeler, oluşturucuya bağımsız değişken olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="690f4-144">The literal content and embedded expressions in an XML literal are passed as arguments to the constructor.</span></span> <span data-ttu-id="690f4-145">Bu, bir XML sabit değeri için kullanılabilen tüm Visual Basic programlama öğelerinin katıştırılmış ifadeler tarafından da kullanılabildiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="690f4-145">This means that all Visual Basic programming elements available to an XML literal are also available to its embedded expressions.</span></span>  
  
 <span data-ttu-id="690f4-146">Bir XML sabit değeri içinde, `Imports` ifadesiyle belirtilen xml ad alanı öneklerine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="690f4-146">Within an XML literal, you can access the XML namespace prefixes declared with the `Imports` statement.</span></span> <span data-ttu-id="690f4-147">`xmlns` Özniteliğini kullanarak bir öğesinde yeni bir XML ad alanı ön eki veya var olan bir XML ad alanı ön ekini gölgelendirebilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="690f4-147">You can declare a new XML namespace prefix, or shadow an existing XML namespace prefix, in an element by using the `xmlns` attribute.</span></span> <span data-ttu-id="690f4-148">Yeni ad alanı, bu öğenin alt düğümleri için kullanılabilir ancak gömülü ifadelerde XML değişmez değerleri için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="690f4-148">The new namespace is available to the child nodes of that element, but not to XML literals in embedded expressions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="690f4-149">`xmlns` Ad alanı özniteliğini kullanarak bir XML ad alanı öneki bildirdiğinizde, öznitelik değeri bir sabit dize olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="690f4-149">When you declare an XML namespace prefix by using the `xmlns` namespace attribute, the attribute value must be a constant string.</span></span> <span data-ttu-id="690f4-150">Bu şekilde, `xmlns` özniteliği kullanmak bir XML ad alanı bildirmek için `Imports` ifadesini kullanmak gibidir.</span><span class="sxs-lookup"><span data-stu-id="690f4-150">In this regard, using the `xmlns` attribute is like using the `Imports` statement to declare an XML namespace.</span></span> <span data-ttu-id="690f4-151">XML ad alanı değerini belirtmek için gömülü bir ifade kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="690f4-151">You cannot use an embedded expression to specify the XML namespace value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="690f4-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="690f4-152">See also</span></span>

- [<span data-ttu-id="690f4-153">Visual Basic XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="690f4-153">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="690f4-154">XML Belgesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="690f4-154">XML Document Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [<span data-ttu-id="690f4-155">XML Öğesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="690f4-155">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="690f4-156">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="690f4-156">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="690f4-157">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="690f4-157">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="690f4-158">XML Değişmez Değerlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="690f4-158">XML Literals Overview</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
