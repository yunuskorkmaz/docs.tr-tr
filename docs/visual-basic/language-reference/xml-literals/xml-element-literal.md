---
title: XML Öğesi Değişmez Değeri
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
ms.openlocfilehash: d6d900ca6868cfffe6b0e5b349321a79c5716c46
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347023"
---
# <a name="xml-element-literal-visual-basic"></a><span data-ttu-id="c0379-102">XML Öğesi Değişmez Değeri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0379-102">XML Element Literal (Visual Basic)</span></span>

<span data-ttu-id="c0379-103">Bir <xref:System.Xml.Linq.XElement> nesnesini temsil eden bir sabit değer.</span><span class="sxs-lookup"><span data-stu-id="c0379-103">A literal that represents an <xref:System.Xml.Linq.XElement> object.</span></span>

## <a name="syntax"></a><span data-ttu-id="c0379-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c0379-104">Syntax</span></span>

```xml
<name [ attributeList ] />
-or-
<name [ attributeList ] > [ elementContents ] </[ name ]>
```

## <a name="parts"></a><span data-ttu-id="c0379-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="c0379-105">Parts</span></span>

- `<`

  <span data-ttu-id="c0379-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c0379-106">Required.</span></span> <span data-ttu-id="c0379-107">Başlangıç öğesi etiketini açar.</span><span class="sxs-lookup"><span data-stu-id="c0379-107">Opens the starting element tag.</span></span>

- `name`

  <span data-ttu-id="c0379-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c0379-108">Required.</span></span> <span data-ttu-id="c0379-109">Öğenin adı.</span><span class="sxs-lookup"><span data-stu-id="c0379-109">Name of the element.</span></span> <span data-ttu-id="c0379-110">Biçim aşağıdakilerden biridir:</span><span class="sxs-lookup"><span data-stu-id="c0379-110">The format is one of the following:</span></span>

  - <span data-ttu-id="c0379-111">Form `[ePrefix:]eName`, öğe adı için değişmez metin, burada:</span><span class="sxs-lookup"><span data-stu-id="c0379-111">Literal text for the element name, of the form `[ePrefix:]eName`, where:</span></span>

    |<span data-ttu-id="c0379-112">Bölümüyle</span><span class="sxs-lookup"><span data-stu-id="c0379-112">Part</span></span>|<span data-ttu-id="c0379-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c0379-113">Description</span></span>|
    |---|---|
    |`ePrefix`|<span data-ttu-id="c0379-114">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c0379-114">Optional.</span></span> <span data-ttu-id="c0379-115">Öğesi için XML ad alanı ön eki.</span><span class="sxs-lookup"><span data-stu-id="c0379-115">XML namespace prefix for the element.</span></span> <span data-ttu-id="c0379-116">Dosyadaki veya proje düzeyindeki bir `Imports` ifadesiyle tanımlanmış bir genel XML ad alanı ya da bu öğede veya bir üst öğede tanımlanan yerel bir XML ad alanı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c0379-116">Must be a global XML namespace that is defined with an `Imports` statement in the file or at the project level, or a local XML namespace that is defined in this element or a parent element.</span></span>|
    |`eName`|<span data-ttu-id="c0379-117">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c0379-117">Required.</span></span> <span data-ttu-id="c0379-118">Öğenin adı.</span><span class="sxs-lookup"><span data-stu-id="c0379-118">Name of the element.</span></span> <span data-ttu-id="c0379-119">Biçim aşağıdakilerden biridir:</span><span class="sxs-lookup"><span data-stu-id="c0379-119">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="c0379-120">-Sabit metin.</span><span class="sxs-lookup"><span data-stu-id="c0379-120">- Literal text.</span></span> <span data-ttu-id="c0379-121">[BELIRTILEN XML öğelerinin ve özniteliklerin adlarına](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="c0379-121">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="c0379-122">-`<%= eNameExp %>`form Embedded ifadesi.</span><span class="sxs-lookup"><span data-stu-id="c0379-122">- Embedded expression of the form `<%= eNameExp %>`.</span></span> <span data-ttu-id="c0379-123">`eNameExp` türü `String` veya <xref:System.Xml.Linq.XName>örtük olarak dönüştürülebilir bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c0379-123">The type of `eNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|

  - <span data-ttu-id="c0379-124">Formun katıştırılmış ifadesi `<%= nameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="c0379-124">Embedded expression of the form `<%= nameExp %>`.</span></span> <span data-ttu-id="c0379-125">`nameExp` türü `String` veya <xref:System.Xml.Linq.XName>öğesine örtülü olarak dönüştürülebilir bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c0379-125">The type of `nameExp` must be `String` or a type implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="c0379-126">Bir öğenin kapanış etiketinde gömülü ifadeye izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="c0379-126">An embedded expression is not allowed in a closing tag of an element.</span></span>

- `attributeList`

  <span data-ttu-id="c0379-127">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c0379-127">Optional.</span></span> <span data-ttu-id="c0379-128">Sabit değerde belirtilen özniteliklerin listesi.</span><span class="sxs-lookup"><span data-stu-id="c0379-128">List of attributes declared in the literal.</span></span>

  `attribute [ attribute ... ]`

  <span data-ttu-id="c0379-129">Her `attribute` aşağıdaki sözdizimlerinden birine sahiptir:</span><span class="sxs-lookup"><span data-stu-id="c0379-129">Each `attribute` has one of the following syntaxes:</span></span>

  - <span data-ttu-id="c0379-130">Form `[aPrefix:]aName=aValue`öznitelik ataması, burada:</span><span class="sxs-lookup"><span data-stu-id="c0379-130">Attribute assignment, of the form `[aPrefix:]aName=aValue`, where:</span></span>

    |<span data-ttu-id="c0379-131">Bölümüyle</span><span class="sxs-lookup"><span data-stu-id="c0379-131">Part</span></span>|<span data-ttu-id="c0379-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c0379-132">Description</span></span>|
    |---|---|
    |`aPrefix`|<span data-ttu-id="c0379-133">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c0379-133">Optional.</span></span> <span data-ttu-id="c0379-134">Öznitelik için XML ad alanı ön eki.</span><span class="sxs-lookup"><span data-stu-id="c0379-134">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="c0379-135">Bir `Imports` ifadesiyle tanımlanmış bir genel XML ad alanı ya da bu öğede veya bir üst öğede tanımlanan yerel bir XML ad alanı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c0379-135">Must be a global XML namespace that is defined with an `Imports` statement, or a local XML namespace that is defined in this element or a parent element.</span></span>|
    |`aName`|<span data-ttu-id="c0379-136">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c0379-136">Required.</span></span> <span data-ttu-id="c0379-137">Özniteliğin adı.</span><span class="sxs-lookup"><span data-stu-id="c0379-137">Name of the attribute.</span></span> <span data-ttu-id="c0379-138">Biçim aşağıdakilerden biridir:</span><span class="sxs-lookup"><span data-stu-id="c0379-138">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="c0379-139">-Sabit metin.</span><span class="sxs-lookup"><span data-stu-id="c0379-139">- Literal text.</span></span> <span data-ttu-id="c0379-140">[BELIRTILEN XML öğelerinin ve özniteliklerin adlarına](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="c0379-140">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="c0379-141">-`<%= aNameExp %>`form Embedded ifadesi.</span><span class="sxs-lookup"><span data-stu-id="c0379-141">- Embedded expression of the form `<%= aNameExp %>`.</span></span> <span data-ttu-id="c0379-142">`aNameExp` türü `String` veya <xref:System.Xml.Linq.XName>örtük olarak dönüştürülebilir bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c0379-142">The type of `aNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|
    |`aValue`|<span data-ttu-id="c0379-143">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c0379-143">Optional.</span></span> <span data-ttu-id="c0379-144">Özniteliğin değeri.</span><span class="sxs-lookup"><span data-stu-id="c0379-144">Value of the attribute.</span></span> <span data-ttu-id="c0379-145">Biçim aşağıdakilerden biridir:</span><span class="sxs-lookup"><span data-stu-id="c0379-145">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="c0379-146">-Düz metin, tırnak işaretleri içine alınır.</span><span class="sxs-lookup"><span data-stu-id="c0379-146">- Literal text, enclosed in quotation marks.</span></span><br /><span data-ttu-id="c0379-147">-`<%= aValueExp %>`form Embedded ifadesi.</span><span class="sxs-lookup"><span data-stu-id="c0379-147">- Embedded expression of the form `<%= aValueExp %>`.</span></span> <span data-ttu-id="c0379-148">Herhangi bir türe izin verilir.</span><span class="sxs-lookup"><span data-stu-id="c0379-148">Any type is allowed.</span></span>|

  - <span data-ttu-id="c0379-149">Formun katıştırılmış ifadesi `<%= aExp %>`.</span><span class="sxs-lookup"><span data-stu-id="c0379-149">Embedded expression of the form `<%= aExp %>`.</span></span>

- `/>`

  <span data-ttu-id="c0379-150">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c0379-150">Optional.</span></span> <span data-ttu-id="c0379-151">Öğenin, içerik olmadan boş bir öğe olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c0379-151">Indicates that the element is an empty element, without content.</span></span>

- `>`

  <span data-ttu-id="c0379-152">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c0379-152">Required.</span></span> <span data-ttu-id="c0379-153">Başlangıç veya boş öğe etiketini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="c0379-153">Ends the beginning or empty element tag.</span></span>

- `elementContents`

  <span data-ttu-id="c0379-154">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c0379-154">Optional.</span></span> <span data-ttu-id="c0379-155">Öğenin içeriği.</span><span class="sxs-lookup"><span data-stu-id="c0379-155">Content of the element.</span></span>

  `content [ content ... ]`

  <span data-ttu-id="c0379-156">Her `content` aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="c0379-156">Each `content` can be one of the following:</span></span>

  - <span data-ttu-id="c0379-157">Değişmez değer metni.</span><span class="sxs-lookup"><span data-stu-id="c0379-157">Literal text.</span></span> <span data-ttu-id="c0379-158">`elementContents` tüm boşluklar, herhangi bir sabit metin varsa önemli hale gelir.</span><span class="sxs-lookup"><span data-stu-id="c0379-158">All the white space in `elementContents` becomes significant if there is any literal text.</span></span>

  - <span data-ttu-id="c0379-159">Formun katıştırılmış ifadesi `<%= contentExp %>`.</span><span class="sxs-lookup"><span data-stu-id="c0379-159">Embedded expression of the form `<%= contentExp %>`.</span></span>

  - <span data-ttu-id="c0379-160">XML öğesi değişmez değeri.</span><span class="sxs-lookup"><span data-stu-id="c0379-160">XML element literal.</span></span>

  - <span data-ttu-id="c0379-161">XML açıklama değişmez değeri.</span><span class="sxs-lookup"><span data-stu-id="c0379-161">XML comment literal.</span></span> <span data-ttu-id="c0379-162">Bkz. [XML açıklama değişmez değeri](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="c0379-162">See [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span></span>

  - <span data-ttu-id="c0379-163">XML işleme yönergesi sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="c0379-163">XML processing instruction literal.</span></span> <span data-ttu-id="c0379-164">Bkz. [XML Işleme yönergesi sabit değeri](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="c0379-164">See [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span></span>

  - <span data-ttu-id="c0379-165">XML CDATA değişmez değeri.</span><span class="sxs-lookup"><span data-stu-id="c0379-165">XML CDATA literal.</span></span> <span data-ttu-id="c0379-166">Bkz. [XML CDATA değişmez değeri](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).</span><span class="sxs-lookup"><span data-stu-id="c0379-166">See [XML CDATA Literal](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).</span></span>

- `</[name]>`

  <span data-ttu-id="c0379-167">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c0379-167">Optional.</span></span> <span data-ttu-id="c0379-168">Öğe için kapanış etiketini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c0379-168">Represents the closing tag for the element.</span></span> <span data-ttu-id="c0379-169">İsteğe bağlı `name` parametresine, gömülü bir ifadenin sonucu olduğunda izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="c0379-169">The optional `name` parameter is not allowed when it is the result of an embedded expression.</span></span>

## <a name="return-value"></a><span data-ttu-id="c0379-170">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c0379-170">Return Value</span></span>

<span data-ttu-id="c0379-171"><xref:System.Xml.Linq.XElement> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="c0379-171">An <xref:System.Xml.Linq.XElement> object.</span></span>

## <a name="remarks"></a><span data-ttu-id="c0379-172">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c0379-172">Remarks</span></span>

<span data-ttu-id="c0379-173">Kodunuzda <xref:System.Xml.Linq.XElement> nesneleri oluşturmak için XML öğesi değişmez sözdizimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0379-173">You can use the XML element literal syntax to create <xref:System.Xml.Linq.XElement> objects in your code.</span></span>

> [!NOTE]
> <span data-ttu-id="c0379-174">Bir XML sabit değeri, satır devamlılık karakterleri kullanmadan birden fazla satıra yayılabilir.</span><span class="sxs-lookup"><span data-stu-id="c0379-174">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="c0379-175">Bu özellik bir XML belgesinden içerik kopyalamanızı ve bunu doğrudan bir Visual Basic programına yapıştırmayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c0379-175">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>

<span data-ttu-id="c0379-176">Form `<%= exp %>` katıştırılmış ifadeler, bir XML öğesi değişmez değerine dinamik bilgi eklemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="c0379-176">Embedded expressions of the form `<%= exp %>` enable you to add dynamic information to an XML element literal.</span></span> <span data-ttu-id="c0379-177">Daha fazla bilgi için bkz. [XML 'de katıştırılmış ifadeler](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c0379-177">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>

<span data-ttu-id="c0379-178">Visual Basic derleyici, XML öğesi değişmez değerini <xref:System.Xml.Linq.XElement.%23ctor%2A> oluşturucusuna çağrılara dönüştürür ve gerekirse <xref:System.Xml.Linq.XAttribute.%23ctor%2A> Oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="c0379-178">The Visual Basic compiler converts the XML element literal into calls to the <xref:System.Xml.Linq.XElement.%23ctor%2A> constructor and, if it is required, the <xref:System.Xml.Linq.XAttribute.%23ctor%2A> constructor.</span></span>

## <a name="xml-namespaces"></a><span data-ttu-id="c0379-179">XML ad alanları</span><span class="sxs-lookup"><span data-stu-id="c0379-179">XML Namespaces</span></span>

<span data-ttu-id="c0379-180">XML ad alanı önekleri, kodda birçok kez aynı ad alanındaki öğelerle XML değişmez değerleri oluşturmanız gerektiğinde faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="c0379-180">XML namespace prefixes are useful when you have to create XML literals with elements from the same namespace many times in code.</span></span> <span data-ttu-id="c0379-181">`xmlns:xmlPrefix="xmlNamespace"` öznitelik sözdizimini kullanarak tanımladığınız `Imports` ifadesini veya yerel ön ekleri kullanarak tanımladığınız genel XML ad alanı öneklerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0379-181">You can use global XML namespace prefixes, which you define by using the `Imports` statement, or local prefixes, which you define by using the `xmlns:xmlPrefix="xmlNamespace"` attribute syntax.</span></span> <span data-ttu-id="c0379-182">Daha fazla bilgi için bkz. [Imports bildirisi (XML ad alanı)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="c0379-182">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>

<span data-ttu-id="c0379-183">XML ad alanları için kapsam kurallarına uygun olarak, yerel ön ekler genel öneklere göre önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="c0379-183">In accordance with the scoping rules for XML namespaces, local prefixes take precedence over global prefixes.</span></span> <span data-ttu-id="c0379-184">Ancak, bir XML sabit değeri bir XML ad alanı tanımlıyorsa, bu ad alanı katıştırılmış ifadede görünen ifadeler için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c0379-184">However, if an XML literal defines an XML namespace, that namespace is not available to expressions that appear in an embedded expression.</span></span> <span data-ttu-id="c0379-185">Katıştırılmış ifade yalnızca genel XML ad alanına erişebilir.</span><span class="sxs-lookup"><span data-stu-id="c0379-185">The embedded expression can access only the global XML namespace.</span></span>

<span data-ttu-id="c0379-186">Visual Basic Derleyicisi, bir XML sabit değeri tarafından kullanılan her genel XML ad alanını oluşturulan kodda tek bir yerel ad alanı tanımına dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="c0379-186">The Visual Basic compiler converts each global XML namespace that is used by an XML literal into a one local namespace definition in the generated code.</span></span> <span data-ttu-id="c0379-187">Kullanılmayan genel XML ad alanları oluşturulan kodda görünmez.</span><span class="sxs-lookup"><span data-stu-id="c0379-187">Global XML namespaces that are not used do not appear in the generated code.</span></span>

## <a name="example"></a><span data-ttu-id="c0379-188">Örnek</span><span class="sxs-lookup"><span data-stu-id="c0379-188">Example</span></span>

<span data-ttu-id="c0379-189">Aşağıdaki örnek, iki iç içe boş öğesi olan basit bir XML öğesinin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c0379-189">The following example shows how to create a simple XML element that has two nested empty elements.</span></span>

[!code-vb[VbXMLSamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#20)]

<span data-ttu-id="c0379-190">Örnekte aşağıdaki metin görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c0379-190">The example displays the following text.</span></span> <span data-ttu-id="c0379-191">Sabit değerin boş öğelerin yapısını koruyan bir değer görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="c0379-191">Notice that the literal preserves the structure of the empty elements.</span></span>

```xml
<outer>
  <inner1></inner1>
  <inner2 />
</outer>
```

## <a name="example"></a><span data-ttu-id="c0379-192">Örnek</span><span class="sxs-lookup"><span data-stu-id="c0379-192">Example</span></span>

<span data-ttu-id="c0379-193">Aşağıdaki örnek, bir öğeyi adlandırmak ve öznitelikleri oluşturmak için katıştırılmış ifadelerin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c0379-193">The following example shows how to use embedded expressions to name an element and create attributes.</span></span>

[!code-vb[VbXMLSamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#21)]

<span data-ttu-id="c0379-194">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="c0379-194">This code displays the following text:</span></span>

```xml
<book isbn="1234" author="My Author" year="1999" title="My Book" />
```

## <a name="example"></a><span data-ttu-id="c0379-195">Örnek</span><span class="sxs-lookup"><span data-stu-id="c0379-195">Example</span></span>

<span data-ttu-id="c0379-196">Aşağıdaki örnek, `ns` bir XML ad alanı öneki olarak bildirir.</span><span class="sxs-lookup"><span data-stu-id="c0379-196">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="c0379-197">Daha sonra bir XML sabit değeri oluşturmak için ad alanının önekini kullanır ve öğenin son formunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c0379-197">It then uses the prefix of the namespace to create an XML literal and displays the element's final form.</span></span>

[!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]

<span data-ttu-id="c0379-198">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="c0379-198">This code displays the following text:</span></span>

```xml
<ns:outer xmlns:ns="http://SomeNamespace">
  <ns:middle xmlns:ns="http://NewNamespace">
    <ns:inner1 />
    <inner2 xmlns="http://SomeNamespace" />
  </ns:middle>
</ns:outer>
```

<span data-ttu-id="c0379-199">Derleyicinin genel XML ad alanının önekini XML ad alanı için bir önek tanımına dönüştürdüğüne dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="c0379-199">Notice that the compiler converted the prefix of the global XML namespace into a prefix definition for the XML namespace.</span></span> <span data-ttu-id="c0379-200">\<NS: Middle > öğesi, \<NS: inner1 > öğesi için XML ad alanı önekini tekrar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c0379-200">The \<ns:middle> element redefines the XML namespace prefix for the \<ns:inner1> element.</span></span> <span data-ttu-id="c0379-201">Ancak, \<NS: inner2 > öğesi `Imports` ifadesiyle tanımlanan ad alanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="c0379-201">However, the \<ns:inner2> element uses the namespace defined by the `Imports` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="c0379-202">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0379-202">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="c0379-203">Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları</span><span class="sxs-lookup"><span data-stu-id="c0379-203">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [<span data-ttu-id="c0379-204">XML Açıklama Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="c0379-204">XML Comment Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [<span data-ttu-id="c0379-205">XML CDATA Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="c0379-205">XML CDATA Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)
- [<span data-ttu-id="c0379-206">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="c0379-206">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="c0379-207">Visual Basic XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="c0379-207">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="c0379-208">XML'de Katıştırılmış İfadeler</span><span class="sxs-lookup"><span data-stu-id="c0379-208">Embedded Expressions in XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [<span data-ttu-id="c0379-209">Imports Deyimi (XML Ad Alanı)</span><span class="sxs-lookup"><span data-stu-id="c0379-209">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
