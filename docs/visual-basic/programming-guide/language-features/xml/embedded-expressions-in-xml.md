---
title: XML'de Katıştırılmış İfadeler (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3c6dff88d123f33ad4c33e91685104b760ecca3b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="embedded-expressions-in-xml-visual-basic"></a><span data-ttu-id="33922-102">XML'de Katıştırılmış İfadeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33922-102">Embedded Expressions in XML (Visual Basic)</span></span>
<span data-ttu-id="33922-103">Katıştırılmış ifadeler çalışma zamanında değerlendirilir ifadeleri içeren XML değişmez değerleri oluşturma olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="33922-103">Embedded expressions enable you to create XML literals that contain expressions that are evaluated at run time.</span></span> <span data-ttu-id="33922-104">Katıştırılmış bir ifade sözdizimi `<%=` `expression` `%>`, olduğu aynı sözdizimini kullanılan gibi [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="33922-104">The syntax for an embedded expression is `<%=` `expression` `%>`, which is the same as the syntax used in [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].</span></span>  
  
 <span data-ttu-id="33922-105">Örneğin, bir XML öğesi değişmez değeri metin içeriği katıştırılmış ifadeler birleştirme oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="33922-105">For example, you can create an XML element literal, combining embedded expressions with literal text content.</span></span>  
  
 [!code-vb[VbXMLSamples#27](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_1.vb)]  
  
 <span data-ttu-id="33922-106">Varsa `isbnNumber` 12345 tamsayı içerir ve `modifiedDate` tarihini içerir 3/5/ne zaman bu kodu yürütür, değerini 2006, `book` değil:</span><span class="sxs-lookup"><span data-stu-id="33922-106">If `isbnNumber` contains the integer 12345 and `modifiedDate` contains the date 3/5/2006, when this code executes, the value of `book` is:</span></span>  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a><span data-ttu-id="33922-107">Katıştırılmış ifade konumu ve doğrulama</span><span class="sxs-lookup"><span data-stu-id="33922-107">Embedded Expression Location and Validation</span></span>  
 <span data-ttu-id="33922-108">Katıştırılmış ifadeler yalnızca XML değişmez ifadeleri içinde belirli konumlarda yer alabilir.</span><span class="sxs-lookup"><span data-stu-id="33922-108">Embedded expressions can appear only at certain locations within XML literal expressions.</span></span> <span data-ttu-id="33922-109">İfade türleri ifade konumu denetimleri döndürebilir ve nasıl `Nothing` ele alınır.</span><span class="sxs-lookup"><span data-stu-id="33922-109">The expression location controls which types the expression can return and how `Nothing` is handled.</span></span> <span data-ttu-id="33922-110">Aşağıdaki tabloda, izin verilen konumların ve katıştırılmış ifadeler türleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="33922-110">The following table describes the allowed locations and types of embedded expressions.</span></span>  
  
|<span data-ttu-id="33922-111">Değişmez değeri konumda</span><span class="sxs-lookup"><span data-stu-id="33922-111">Location in literal</span></span>|<span data-ttu-id="33922-112">İfade türü</span><span class="sxs-lookup"><span data-stu-id="33922-112">Type of expression</span></span>|<span data-ttu-id="33922-113">İşleme `Nothing`</span><span class="sxs-lookup"><span data-stu-id="33922-113">Handling of `Nothing`</span></span>|  
|---|---|---|  
|<span data-ttu-id="33922-114">XML öğesi adı</span><span class="sxs-lookup"><span data-stu-id="33922-114">XML element name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="33922-115">Hata</span><span class="sxs-lookup"><span data-stu-id="33922-115">Error</span></span>|  
|<span data-ttu-id="33922-116">XML öğesi içeriği</span><span class="sxs-lookup"><span data-stu-id="33922-116">XML element content</span></span>|<span data-ttu-id="33922-117">`Object` veya dizi `Object`</span><span class="sxs-lookup"><span data-stu-id="33922-117">`Object` or array of `Object`</span></span>|<span data-ttu-id="33922-118">Yoksayıldı</span><span class="sxs-lookup"><span data-stu-id="33922-118">Ignored</span></span>|  
|<span data-ttu-id="33922-119">XML öğesi öznitelik adı</span><span class="sxs-lookup"><span data-stu-id="33922-119">XML element attribute name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="33922-120">Hata, öznitelik değeri de olmadığı sürece `Nothing`</span><span class="sxs-lookup"><span data-stu-id="33922-120">Error, unless the attribute value is also `Nothing`</span></span>|  
|<span data-ttu-id="33922-121">XML öğesi öznitelik değeri</span><span class="sxs-lookup"><span data-stu-id="33922-121">XML element attribute value</span></span>|`Object`|<span data-ttu-id="33922-122">Göz ardı özniteliği bildirimi</span><span class="sxs-lookup"><span data-stu-id="33922-122">Attribute declaration ignored</span></span>|  
|<span data-ttu-id="33922-123">XML öğe özniteliği</span><span class="sxs-lookup"><span data-stu-id="33922-123">XML element attribute</span></span>|<span data-ttu-id="33922-124"><xref:System.Xml.Linq.XAttribute> veya bir koleksiyonu <xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="33922-124"><xref:System.Xml.Linq.XAttribute> or a collection of <xref:System.Xml.Linq.XAttribute></span></span>|<span data-ttu-id="33922-125">Yoksayıldı</span><span class="sxs-lookup"><span data-stu-id="33922-125">Ignored</span></span>|  
|<span data-ttu-id="33922-126">XML belge kök öğesi</span><span class="sxs-lookup"><span data-stu-id="33922-126">XML document root element</span></span>|<span data-ttu-id="33922-127"><xref:System.Xml.Linq.XElement> veya bir koleksiyonu <xref:System.Xml.Linq.XElement> nesne ve isteğe bağlı sayıda <xref:System.Xml.Linq.XProcessingInstruction> ve <xref:System.Xml.Linq.XComment> nesneleri</span><span class="sxs-lookup"><span data-stu-id="33922-127"><xref:System.Xml.Linq.XElement> or a collection of one <xref:System.Xml.Linq.XElement> object and an arbitrary number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects</span></span>|<span data-ttu-id="33922-128">Yoksayıldı</span><span class="sxs-lookup"><span data-stu-id="33922-128">Ignored</span></span>|  
  
-   <span data-ttu-id="33922-129">Bir XML öğesi adı katıştırılmış bir ifadede örneği:</span><span class="sxs-lookup"><span data-stu-id="33922-129">Example of an embedded expression in an XML element name:</span></span>  
  
     [!code-vb[VbXMLSamples#32](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_2.vb)]  
  
-   <span data-ttu-id="33922-130">Katıştırılmış içerik ifadede bir XML öğesi örneği:</span><span class="sxs-lookup"><span data-stu-id="33922-130">Example of an embedded expression in the content of an XML element:</span></span>  
  
     [!code-vb[VbXMLSamples#33](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_3.vb)]  
  
-   <span data-ttu-id="33922-131">Bir XML öğesi öznitelik adı katıştırılmış bir ifadede örneği:</span><span class="sxs-lookup"><span data-stu-id="33922-131">Example of an embedded expression in an XML element attribute name:</span></span>  
  
     [!code-vb[VbXMLSamples#34](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_4.vb)]  
  
-   <span data-ttu-id="33922-132">Bir XML öğesi öznitelik değerinde katıştırılmış bir ifade örneği:</span><span class="sxs-lookup"><span data-stu-id="33922-132">Example of an embedded expression in an XML element attribute value:</span></span>  
  
     [!code-vb[VbXMLSamples#35](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_5.vb)]  
  
-   <span data-ttu-id="33922-133">Bir XML öğesi özniteliğindeki katıştırılmış bir ifade örneği:</span><span class="sxs-lookup"><span data-stu-id="33922-133">Example of an embedded expression in an XML element attribute:</span></span>  
  
     [!code-vb[VbXMLSamples#36](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_6.vb)]  
  
-   <span data-ttu-id="33922-134">Bir XML belgesi kök öğesi içinde katıştırılmış bir ifade örneği:</span><span class="sxs-lookup"><span data-stu-id="33922-134">Example of an embedded expression in an XML document root element:</span></span>  
  
     [!code-vb[VbXMLSamples#37](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_7.vb)]  
  
 <span data-ttu-id="33922-135">Etkinleştirirseniz, `Option Strict`, her katıştırılmış ifade türü için gerekli tür widens derleyici denetler.</span><span class="sxs-lookup"><span data-stu-id="33922-135">If you enable `Option Strict`, the compiler checks that the type of each embedded expression widens to the required type.</span></span> <span data-ttu-id="33922-136">Kod çalıştığında doğrulanır bir XML belgesi kök öğesi için yalnızca istisnadır.</span><span class="sxs-lookup"><span data-stu-id="33922-136">The only exception is for the root element of an XML document, which is verified when the code runs.</span></span> <span data-ttu-id="33922-137">Olmadan derleme yaparsanız `Option Strict`, türünde ifadeler katıştırmak `Object` ve bunların türü çalışma zamanında doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="33922-137">If you compile without `Option Strict`, you can embed expressions of type `Object` and their type is verified at run time.</span></span>  
  
 <span data-ttu-id="33922-138">İçerik nerede isteğe bağlı, konumlarda içeren ifadeleri katıştırılmış `Nothing` göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="33922-138">In locations where content is optional, embedded expressions that contain `Nothing` are ignored.</span></span> <span data-ttu-id="33922-139">Bu öznitelik değerleri, o öğe içeriği denetleyin gerekmez ve dizi öğeleri olmayan anlamına gelir `Nothing` bir XML değişmez değeri kullanmadan önce.</span><span class="sxs-lookup"><span data-stu-id="33922-139">This means you do not have to check that element content, attribute values, and array elements are not `Nothing` before you use an XML literal.</span></span> <span data-ttu-id="33922-140">Öğe ve öznitelik adları gibi değerler olamaz gerekli `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="33922-140">Required values, such as element and attribute names, cannot be `Nothing`.</span></span>  
  
 <span data-ttu-id="33922-141">Katıştırılmış bir ifade hazır değer belirli bir tür kullanma hakkında daha fazla bilgi için bkz: [XML belgesi değişmez değer](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [XML öğesi değişmez değer](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="33922-141">For more information about using an embedded expression in a particular type of literal, see [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="scoping-rules"></a><span data-ttu-id="33922-142">Kapsam kuralları</span><span class="sxs-lookup"><span data-stu-id="33922-142">Scoping Rules</span></span>  
 <span data-ttu-id="33922-143">Derleyici Oluşturucusu çağrısı uygun değişmez değer türü için her XML değişmez değer dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="33922-143">The compiler converts each XML literal into a constructor call for the appropriate literal type.</span></span> <span data-ttu-id="33922-144">Değişmez değer içeriğine ve XML değişmez değeri katıştırılmış ifadeler oluşturucuya bağımsız değişken olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="33922-144">The literal content and embedded expressions in an XML literal are passed as arguments to the constructor.</span></span> <span data-ttu-id="33922-145">Başka bir deyişle, bir XML değişmez değer kullanılabilir tüm Visual Basic programlama öğeleri de kendi katıştırılmış ifadeler için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="33922-145">This means that all Visual Basic programming elements available to an XML literal are also available to its embedded expressions.</span></span>  
  
 <span data-ttu-id="33922-146">XML değişmez değer içinde önekleri bildirilen ile XML ad alanına erişebildiğinizi `Imports` deyimi.</span><span class="sxs-lookup"><span data-stu-id="33922-146">Within an XML literal, you can access the XML namespace prefixes declared with the `Imports` statement.</span></span> <span data-ttu-id="33922-147">Yeni bir XML ad alanı önekini bildirmek veya kullanarak bir öğedeki var olan bir XML ad alanı öneki gölge `xmlns` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="33922-147">You can declare a new XML namespace prefix, or shadow an existing XML namespace prefix, in an element by using the `xmlns` attribute.</span></span> <span data-ttu-id="33922-148">Yeni ad alanı, o öğesinin alt düğümleri, ancak katıştırılmış ifadelerde XML değişmez değerleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="33922-148">The new namespace is available to the child nodes of that element, but not to XML literals in embedded expressions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33922-149">Ne zaman bildirdiğiniz bir XML ad alanı öneki kullanarak `xmlns` namespace özniteliği öznitelik değerinin bir sabit dize olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="33922-149">When you declare an XML namespace prefix by using the `xmlns` namespace attribute, the attribute value must be a constant string.</span></span> <span data-ttu-id="33922-150">Bu bağlamda kullanarak `xmlns` özniteliktir kullanarak gibi `Imports` bir XML ad alanı bildirmek için deyimi.</span><span class="sxs-lookup"><span data-stu-id="33922-150">In this regard, using the `xmlns` attribute is like using the `Imports` statement to declare an XML namespace.</span></span> <span data-ttu-id="33922-151">XML ad alanı değeri belirtmek için katıştırılmış bir ifade kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="33922-151">You cannot use an embedded expression to specify the XML namespace value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33922-152">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="33922-152">See Also</span></span>  
 [<span data-ttu-id="33922-153">Visual Basic'de XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="33922-153">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="33922-154">XML Belgesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="33922-154">XML Document Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)  
 [<span data-ttu-id="33922-155">XML Öğesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="33922-155">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="33922-156">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="33922-156">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="33922-157">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="33922-157">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="33922-158">XML Değişmez Değerlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="33922-158">XML Literals Overview</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
