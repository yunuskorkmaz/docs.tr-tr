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
ms.openlocfilehash: d6a91de4e279816bafd29f46bb4f5422cbd934ff
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400195"
---
# <a name="xml-element-literal-visual-basic"></a><span data-ttu-id="8478c-102">XML Öğesi Değişmez Değeri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8478c-102">XML Element Literal (Visual Basic)</span></span>

<span data-ttu-id="8478c-103">Bir nesneyi temsil eden bir sabit değer <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="8478c-103">A literal that represents an <xref:System.Xml.Linq.XElement> object.</span></span>

## <a name="syntax"></a><span data-ttu-id="8478c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8478c-104">Syntax</span></span>

```xml
<name [ attributeList ] />
-or-
<name [ attributeList ] > [ elementContents ] </[ name ]>
```

## <a name="parts"></a><span data-ttu-id="8478c-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="8478c-105">Parts</span></span>

- `<`

  <span data-ttu-id="8478c-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8478c-106">Required.</span></span> <span data-ttu-id="8478c-107">Başlangıç öğesi etiketini açar.</span><span class="sxs-lookup"><span data-stu-id="8478c-107">Opens the starting element tag.</span></span>

- `name`

  <span data-ttu-id="8478c-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8478c-108">Required.</span></span> <span data-ttu-id="8478c-109">Öğenin adı.</span><span class="sxs-lookup"><span data-stu-id="8478c-109">Name of the element.</span></span> <span data-ttu-id="8478c-110">Biçim aşağıdakilerden biridir:</span><span class="sxs-lookup"><span data-stu-id="8478c-110">The format is one of the following:</span></span>

  - <span data-ttu-id="8478c-111">Formun öğe adı için değişmez metin `[ePrefix:]eName` , burada:</span><span class="sxs-lookup"><span data-stu-id="8478c-111">Literal text for the element name, of the form `[ePrefix:]eName`, where:</span></span>

    |<span data-ttu-id="8478c-112">Bölüm</span><span class="sxs-lookup"><span data-stu-id="8478c-112">Part</span></span>|<span data-ttu-id="8478c-113">Description</span><span class="sxs-lookup"><span data-stu-id="8478c-113">Description</span></span>|
    |---|---|
    |`ePrefix`|<span data-ttu-id="8478c-114">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8478c-114">Optional.</span></span> <span data-ttu-id="8478c-115">Öğesi için XML ad alanı ön eki.</span><span class="sxs-lookup"><span data-stu-id="8478c-115">XML namespace prefix for the element.</span></span> <span data-ttu-id="8478c-116">Dosyadaki veya proje düzeyindeki bir deyimle tanımlanmış bir genel XML ad alanı ya da `Imports` Bu öğede veya bir üst öğede tanımlanan yerel BIR XML ad alanı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8478c-116">Must be a global XML namespace that is defined with an `Imports` statement in the file or at the project level, or a local XML namespace that is defined in this element or a parent element.</span></span>|
    |`eName`|<span data-ttu-id="8478c-117">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8478c-117">Required.</span></span> <span data-ttu-id="8478c-118">Öğenin adı.</span><span class="sxs-lookup"><span data-stu-id="8478c-118">Name of the element.</span></span> <span data-ttu-id="8478c-119">Biçim aşağıdakilerden biridir:</span><span class="sxs-lookup"><span data-stu-id="8478c-119">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="8478c-120">-Sabit metin.</span><span class="sxs-lookup"><span data-stu-id="8478c-120">- Literal text.</span></span> <span data-ttu-id="8478c-121">[BELIRTILEN XML öğelerinin ve özniteliklerin adlarına](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="8478c-121">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="8478c-122">-Formun katıştırılmış ifadesi `<%= eNameExp %>` .</span><span class="sxs-lookup"><span data-stu-id="8478c-122">- Embedded expression of the form `<%= eNameExp %>`.</span></span> <span data-ttu-id="8478c-123">Türü `eNameExp` `String` veya örtük olarak dönüştürülebilir bir tür olmalıdır <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="8478c-123">The type of `eNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|

  - <span data-ttu-id="8478c-124">Formun katıştırılmış ifadesi `<%= nameExp %>` .</span><span class="sxs-lookup"><span data-stu-id="8478c-124">Embedded expression of the form `<%= nameExp %>`.</span></span> <span data-ttu-id="8478c-125">Türü `nameExp` `String` veya örtülü olarak dönüştürülebilir bir tür olmalıdır <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="8478c-125">The type of `nameExp` must be `String` or a type implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="8478c-126">Bir öğenin kapanış etiketinde gömülü ifadeye izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="8478c-126">An embedded expression is not allowed in a closing tag of an element.</span></span>

- `attributeList`

  <span data-ttu-id="8478c-127">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8478c-127">Optional.</span></span> <span data-ttu-id="8478c-128">Sabit değerde belirtilen özniteliklerin listesi.</span><span class="sxs-lookup"><span data-stu-id="8478c-128">List of attributes declared in the literal.</span></span>

  `attribute [ attribute ... ]`

  <span data-ttu-id="8478c-129">Her biri `attribute` aşağıdaki sözdizimlerinden birine sahiptir:</span><span class="sxs-lookup"><span data-stu-id="8478c-129">Each `attribute` has one of the following syntaxes:</span></span>

  - <span data-ttu-id="8478c-130">Formun öznitelik ataması, `[aPrefix:]aName=aValue` burada:</span><span class="sxs-lookup"><span data-stu-id="8478c-130">Attribute assignment, of the form `[aPrefix:]aName=aValue`, where:</span></span>

    |<span data-ttu-id="8478c-131">Bölüm</span><span class="sxs-lookup"><span data-stu-id="8478c-131">Part</span></span>|<span data-ttu-id="8478c-132">Description</span><span class="sxs-lookup"><span data-stu-id="8478c-132">Description</span></span>|
    |---|---|
    |`aPrefix`|<span data-ttu-id="8478c-133">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8478c-133">Optional.</span></span> <span data-ttu-id="8478c-134">Öznitelik için XML ad alanı ön eki.</span><span class="sxs-lookup"><span data-stu-id="8478c-134">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="8478c-135">Bir ifadesiyle tanımlanmış bir genel XML ad alanı `Imports` ya da bu öğede veya bir üst öğede tanımlanan yerel BIR XML ad alanı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8478c-135">Must be a global XML namespace that is defined with an `Imports` statement, or a local XML namespace that is defined in this element or a parent element.</span></span>|
    |`aName`|<span data-ttu-id="8478c-136">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8478c-136">Required.</span></span> <span data-ttu-id="8478c-137">Özniteliğin adı.</span><span class="sxs-lookup"><span data-stu-id="8478c-137">Name of the attribute.</span></span> <span data-ttu-id="8478c-138">Biçim aşağıdakilerden biridir:</span><span class="sxs-lookup"><span data-stu-id="8478c-138">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="8478c-139">-Sabit metin.</span><span class="sxs-lookup"><span data-stu-id="8478c-139">- Literal text.</span></span> <span data-ttu-id="8478c-140">[BELIRTILEN XML öğelerinin ve özniteliklerin adlarına](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="8478c-140">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="8478c-141">-Formun katıştırılmış ifadesi `<%= aNameExp %>` .</span><span class="sxs-lookup"><span data-stu-id="8478c-141">- Embedded expression of the form `<%= aNameExp %>`.</span></span> <span data-ttu-id="8478c-142">Türü `aNameExp` `String` veya örtük olarak dönüştürülebilir bir tür olmalıdır <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="8478c-142">The type of `aNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|
    |`aValue`|<span data-ttu-id="8478c-143">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8478c-143">Optional.</span></span> <span data-ttu-id="8478c-144">Özniteliğin değeri.</span><span class="sxs-lookup"><span data-stu-id="8478c-144">Value of the attribute.</span></span> <span data-ttu-id="8478c-145">Biçim aşağıdakilerden biridir:</span><span class="sxs-lookup"><span data-stu-id="8478c-145">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="8478c-146">-Düz metin, tırnak işaretleri içine alınır.</span><span class="sxs-lookup"><span data-stu-id="8478c-146">- Literal text, enclosed in quotation marks.</span></span><br /><span data-ttu-id="8478c-147">-Formun katıştırılmış ifadesi `<%= aValueExp %>` .</span><span class="sxs-lookup"><span data-stu-id="8478c-147">- Embedded expression of the form `<%= aValueExp %>`.</span></span> <span data-ttu-id="8478c-148">Herhangi bir türe izin verilir.</span><span class="sxs-lookup"><span data-stu-id="8478c-148">Any type is allowed.</span></span>|

  - <span data-ttu-id="8478c-149">Formun katıştırılmış ifadesi `<%= aExp %>` .</span><span class="sxs-lookup"><span data-stu-id="8478c-149">Embedded expression of the form `<%= aExp %>`.</span></span>

- `/>`

  <span data-ttu-id="8478c-150">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8478c-150">Optional.</span></span> <span data-ttu-id="8478c-151">Öğenin, içerik olmadan boş bir öğe olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8478c-151">Indicates that the element is an empty element, without content.</span></span>

- `>`

  <span data-ttu-id="8478c-152">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8478c-152">Required.</span></span> <span data-ttu-id="8478c-153">Başlangıç veya boş öğe etiketini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="8478c-153">Ends the beginning or empty element tag.</span></span>

- `elementContents`

  <span data-ttu-id="8478c-154">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8478c-154">Optional.</span></span> <span data-ttu-id="8478c-155">Öğenin içeriği.</span><span class="sxs-lookup"><span data-stu-id="8478c-155">Content of the element.</span></span>

  `content [ content ... ]`

  <span data-ttu-id="8478c-156">Her biri `content` aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="8478c-156">Each `content` can be one of the following:</span></span>

  - <span data-ttu-id="8478c-157">Değişmez değer metni.</span><span class="sxs-lookup"><span data-stu-id="8478c-157">Literal text.</span></span> <span data-ttu-id="8478c-158">İçindeki tüm boşluklar, `elementContents` herhangi bir sabit metin varsa önemli hale gelir.</span><span class="sxs-lookup"><span data-stu-id="8478c-158">All the white space in `elementContents` becomes significant if there is any literal text.</span></span>

  - <span data-ttu-id="8478c-159">Formun katıştırılmış ifadesi `<%= contentExp %>` .</span><span class="sxs-lookup"><span data-stu-id="8478c-159">Embedded expression of the form `<%= contentExp %>`.</span></span>

  - <span data-ttu-id="8478c-160">XML öğesi değişmez değeri.</span><span class="sxs-lookup"><span data-stu-id="8478c-160">XML element literal.</span></span>

  - <span data-ttu-id="8478c-161">XML açıklama değişmez değeri.</span><span class="sxs-lookup"><span data-stu-id="8478c-161">XML comment literal.</span></span> <span data-ttu-id="8478c-162">Bkz. [XML açıklama değişmez değeri](xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="8478c-162">See [XML Comment Literal](xml-comment-literal.md).</span></span>

  - <span data-ttu-id="8478c-163">XML işleme yönergesi sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="8478c-163">XML processing instruction literal.</span></span> <span data-ttu-id="8478c-164">Bkz. [XML Işleme yönergesi sabit değeri](xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="8478c-164">See [XML Processing Instruction Literal](xml-processing-instruction-literal.md).</span></span>

  - <span data-ttu-id="8478c-165">XML CDATA değişmez değeri.</span><span class="sxs-lookup"><span data-stu-id="8478c-165">XML CDATA literal.</span></span> <span data-ttu-id="8478c-166">Bkz. [XML CDATA değişmez değeri](xml-cdata-literal.md).</span><span class="sxs-lookup"><span data-stu-id="8478c-166">See [XML CDATA Literal](xml-cdata-literal.md).</span></span>

- `</[name]>`

  <span data-ttu-id="8478c-167">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8478c-167">Optional.</span></span> <span data-ttu-id="8478c-168">Öğe için kapanış etiketini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8478c-168">Represents the closing tag for the element.</span></span> <span data-ttu-id="8478c-169">İsteğe bağlı `name` parametreye, gömülü bir ifadenin sonucu olduğunda izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="8478c-169">The optional `name` parameter is not allowed when it is the result of an embedded expression.</span></span>

## <a name="return-value"></a><span data-ttu-id="8478c-170">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8478c-170">Return Value</span></span>

<span data-ttu-id="8478c-171">Bir <xref:System.Xml.Linq.XElement> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="8478c-171">An <xref:System.Xml.Linq.XElement> object.</span></span>

## <a name="remarks"></a><span data-ttu-id="8478c-172">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8478c-172">Remarks</span></span>

<span data-ttu-id="8478c-173">Kodunuzda nesneler oluşturmak için XML öğesi değişmez sözdizimini kullanabilirsiniz <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="8478c-173">You can use the XML element literal syntax to create <xref:System.Xml.Linq.XElement> objects in your code.</span></span>

> [!NOTE]
> <span data-ttu-id="8478c-174">Bir XML sabit değeri, satır devamlılık karakterleri kullanmadan birden fazla satıra yayılabilir.</span><span class="sxs-lookup"><span data-stu-id="8478c-174">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="8478c-175">Bu özellik bir XML belgesinden içerik kopyalamanızı ve bunu doğrudan bir Visual Basic programına yapıştırmayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="8478c-175">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>

<span data-ttu-id="8478c-176">Formun katıştırılmış ifadeleri `<%= exp %>` , BIR XML öğesi değişmez değerine dinamik bilgi eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8478c-176">Embedded expressions of the form `<%= exp %>` enable you to add dynamic information to an XML element literal.</span></span> <span data-ttu-id="8478c-177">Daha fazla bilgi için bkz. [XML 'de katıştırılmış ifadeler](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8478c-177">For more information, see [Embedded Expressions in XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>

<span data-ttu-id="8478c-178">Visual Basic derleyici, XML öğesi değişmez değerini oluşturucuya yapılan çağrılara dönüştürür <xref:System.Xml.Linq.XElement.%23ctor%2A> ve gerekirse, <xref:System.Xml.Linq.XAttribute.%23ctor%2A> Oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="8478c-178">The Visual Basic compiler converts the XML element literal into calls to the <xref:System.Xml.Linq.XElement.%23ctor%2A> constructor and, if it is required, the <xref:System.Xml.Linq.XAttribute.%23ctor%2A> constructor.</span></span>

## <a name="xml-namespaces"></a><span data-ttu-id="8478c-179">XML ad alanları</span><span class="sxs-lookup"><span data-stu-id="8478c-179">XML Namespaces</span></span>

<span data-ttu-id="8478c-180">XML ad alanı önekleri, kodda birçok kez aynı ad alanındaki öğelerle XML değişmez değerleri oluşturmanız gerektiğinde faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="8478c-180">XML namespace prefixes are useful when you have to create XML literals with elements from the same namespace many times in code.</span></span> <span data-ttu-id="8478c-181">Özniteliğini kullanarak tanımladığınız genel XML ad alanı öneklerini `Imports` veya öznitelik sözdizimini kullanarak tanımladığınız yerel önekleri kullanabilirsiniz `xmlns:xmlPrefix="xmlNamespace"` .</span><span class="sxs-lookup"><span data-stu-id="8478c-181">You can use global XML namespace prefixes, which you define by using the `Imports` statement, or local prefixes, which you define by using the `xmlns:xmlPrefix="xmlNamespace"` attribute syntax.</span></span> <span data-ttu-id="8478c-182">Daha fazla bilgi için bkz. [Imports bildirisi (XML ad alanı)](../statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="8478c-182">For more information, see [Imports Statement (XML Namespace)](../statements/imports-statement-xml-namespace.md).</span></span>

<span data-ttu-id="8478c-183">XML ad alanları için kapsam kurallarına uygun olarak, yerel ön ekler genel öneklere göre önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="8478c-183">In accordance with the scoping rules for XML namespaces, local prefixes take precedence over global prefixes.</span></span> <span data-ttu-id="8478c-184">Ancak, bir XML sabit değeri bir XML ad alanı tanımlıyorsa, bu ad alanı katıştırılmış ifadede görünen ifadeler için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8478c-184">However, if an XML literal defines an XML namespace, that namespace is not available to expressions that appear in an embedded expression.</span></span> <span data-ttu-id="8478c-185">Katıştırılmış ifade yalnızca genel XML ad alanına erişebilir.</span><span class="sxs-lookup"><span data-stu-id="8478c-185">The embedded expression can access only the global XML namespace.</span></span>

<span data-ttu-id="8478c-186">Visual Basic Derleyicisi, bir XML sabit değeri tarafından kullanılan her genel XML ad alanını oluşturulan kodda tek bir yerel ad alanı tanımına dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="8478c-186">The Visual Basic compiler converts each global XML namespace that is used by an XML literal into a one local namespace definition in the generated code.</span></span> <span data-ttu-id="8478c-187">Kullanılmayan genel XML ad alanları oluşturulan kodda görünmez.</span><span class="sxs-lookup"><span data-stu-id="8478c-187">Global XML namespaces that are not used do not appear in the generated code.</span></span>

## <a name="example"></a><span data-ttu-id="8478c-188">Örnek</span><span class="sxs-lookup"><span data-stu-id="8478c-188">Example</span></span>

<span data-ttu-id="8478c-189">Aşağıdaki örnek, iki iç içe boş öğesi olan basit bir XML öğesinin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8478c-189">The following example shows how to create a simple XML element that has two nested empty elements.</span></span>

[!code-vb[VbXMLSamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#20)]

<span data-ttu-id="8478c-190">Örnekte aşağıdaki metin görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8478c-190">The example displays the following text.</span></span> <span data-ttu-id="8478c-191">Sabit değerin boş öğelerin yapısını koruyan bir değer görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="8478c-191">Notice that the literal preserves the structure of the empty elements.</span></span>

```xml
<outer>
  <inner1></inner1>
  <inner2 />
</outer>
```

## <a name="example"></a><span data-ttu-id="8478c-192">Örnek</span><span class="sxs-lookup"><span data-stu-id="8478c-192">Example</span></span>

<span data-ttu-id="8478c-193">Aşağıdaki örnek, bir öğeyi adlandırmak ve öznitelikleri oluşturmak için katıştırılmış ifadelerin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8478c-193">The following example shows how to use embedded expressions to name an element and create attributes.</span></span>

[!code-vb[VbXMLSamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#21)]

<span data-ttu-id="8478c-194">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="8478c-194">This code displays the following text:</span></span>

```xml
<book isbn="1234" author="My Author" year="1999" title="My Book" />
```

## <a name="example"></a><span data-ttu-id="8478c-195">Örnek</span><span class="sxs-lookup"><span data-stu-id="8478c-195">Example</span></span>

<span data-ttu-id="8478c-196">Aşağıdaki örnek `ns` BIR XML ad alanı ön eki olarak bildirir.</span><span class="sxs-lookup"><span data-stu-id="8478c-196">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="8478c-197">Daha sonra bir XML sabit değeri oluşturmak için ad alanının önekini kullanır ve öğenin son formunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8478c-197">It then uses the prefix of the namespace to create an XML literal and displays the element's final form.</span></span>

[!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]

<span data-ttu-id="8478c-198">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="8478c-198">This code displays the following text:</span></span>

```xml
<ns:outer xmlns:ns="http://SomeNamespace">
  <ns:middle xmlns:ns="http://NewNamespace">
    <ns:inner1 />
    <inner2 xmlns="http://SomeNamespace" />
  </ns:middle>
</ns:outer>
```

<span data-ttu-id="8478c-199">Derleyicinin genel XML ad alanının önekini XML ad alanı için bir önek tanımına dönüştürdüğüne dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="8478c-199">Notice that the compiler converted the prefix of the global XML namespace into a prefix definition for the XML namespace.</span></span> <span data-ttu-id="8478c-200">\<ns:middle>Öğesi öğesi IÇIN XML ad alanı önekini tekrar tanımlar \<ns:inner1> .</span><span class="sxs-lookup"><span data-stu-id="8478c-200">The \<ns:middle> element redefines the XML namespace prefix for the \<ns:inner1> element.</span></span> <span data-ttu-id="8478c-201">Ancak, \<ns:inner2> öğesi, ifadesiyle tanımlanan ad alanını kullanır `Imports` .</span><span class="sxs-lookup"><span data-stu-id="8478c-201">However, the \<ns:inner2> element uses the namespace defined by the `Imports` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="8478c-202">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8478c-202">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="8478c-203">Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları</span><span class="sxs-lookup"><span data-stu-id="8478c-203">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [<span data-ttu-id="8478c-204">XML Açıklama Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="8478c-204">XML Comment Literal</span></span>](xml-comment-literal.md)
- [<span data-ttu-id="8478c-205">XML CDATA Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="8478c-205">XML CDATA Literal</span></span>](xml-cdata-literal.md)
- [<span data-ttu-id="8478c-206">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="8478c-206">XML Literals</span></span>](index.md)
- [<span data-ttu-id="8478c-207">Visual Basic'de XML Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8478c-207">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="8478c-208">XML'de Katıştırılmış İfadeler</span><span class="sxs-lookup"><span data-stu-id="8478c-208">Embedded Expressions in XML</span></span>](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [<span data-ttu-id="8478c-209">Imports Deyimi (XML Ad Alanı)</span><span class="sxs-lookup"><span data-stu-id="8478c-209">Imports Statement (XML Namespace)</span></span>](../statements/imports-statement-xml-namespace.md)
