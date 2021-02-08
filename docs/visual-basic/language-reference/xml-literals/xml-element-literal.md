---
description: 'Daha fazla bilgi edinin: XML öğesi değişmez değeri (Visual Basic)'
title: XML Öğesi Değişmez Değeri
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
ms.openlocfilehash: dfc78beded5c6f472b67fa272835ef0aa29d0187
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787545"
---
# <a name="xml-element-literal-visual-basic"></a><span data-ttu-id="77f4d-103">XML Öğesi Değişmez Değeri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77f4d-103">XML Element Literal (Visual Basic)</span></span>

<span data-ttu-id="77f4d-104">Bir nesneyi temsil eden bir sabit değer <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="77f4d-104">A literal that represents an <xref:System.Xml.Linq.XElement> object.</span></span>

## <a name="syntax"></a><span data-ttu-id="77f4d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="77f4d-105">Syntax</span></span>

```xml
<name [ attributeList ] />
-or-
<name [ attributeList ] > [ elementContents ] </[ name ]>
```

## <a name="parts"></a><span data-ttu-id="77f4d-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="77f4d-106">Parts</span></span>

- `<`

  <span data-ttu-id="77f4d-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="77f4d-107">Required.</span></span> <span data-ttu-id="77f4d-108">Başlangıç öğesi etiketini açar.</span><span class="sxs-lookup"><span data-stu-id="77f4d-108">Opens the starting element tag.</span></span>

- `name`

  <span data-ttu-id="77f4d-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="77f4d-109">Required.</span></span> <span data-ttu-id="77f4d-110">Öğenin adı.</span><span class="sxs-lookup"><span data-stu-id="77f4d-110">Name of the element.</span></span> <span data-ttu-id="77f4d-111">Biçim aşağıdakilerden biridir:</span><span class="sxs-lookup"><span data-stu-id="77f4d-111">The format is one of the following:</span></span>

  - <span data-ttu-id="77f4d-112">Formun öğe adı için değişmez metin `[ePrefix:]eName` , burada:</span><span class="sxs-lookup"><span data-stu-id="77f4d-112">Literal text for the element name, of the form `[ePrefix:]eName`, where:</span></span>

    |<span data-ttu-id="77f4d-113">Bölüm</span><span class="sxs-lookup"><span data-stu-id="77f4d-113">Part</span></span>|<span data-ttu-id="77f4d-114">Description</span><span class="sxs-lookup"><span data-stu-id="77f4d-114">Description</span></span>|
    |---|---|
    |`ePrefix`|<span data-ttu-id="77f4d-115">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="77f4d-115">Optional.</span></span> <span data-ttu-id="77f4d-116">Öğesi için XML ad alanı ön eki.</span><span class="sxs-lookup"><span data-stu-id="77f4d-116">XML namespace prefix for the element.</span></span> <span data-ttu-id="77f4d-117">Dosyadaki veya proje düzeyindeki bir deyimle tanımlanmış bir genel XML ad alanı ya da `Imports` Bu öğede veya bir üst öğede tanımlanan yerel BIR XML ad alanı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="77f4d-117">Must be a global XML namespace that is defined with an `Imports` statement in the file or at the project level, or a local XML namespace that is defined in this element or a parent element.</span></span>|
    |`eName`|<span data-ttu-id="77f4d-118">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="77f4d-118">Required.</span></span> <span data-ttu-id="77f4d-119">Öğenin adı.</span><span class="sxs-lookup"><span data-stu-id="77f4d-119">Name of the element.</span></span> <span data-ttu-id="77f4d-120">Biçim aşağıdakilerden biridir:</span><span class="sxs-lookup"><span data-stu-id="77f4d-120">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="77f4d-121">-Sabit metin.</span><span class="sxs-lookup"><span data-stu-id="77f4d-121">- Literal text.</span></span> <span data-ttu-id="77f4d-122">[BELIRTILEN XML öğelerinin ve özniteliklerin adlarına](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="77f4d-122">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="77f4d-123">-Formun katıştırılmış ifadesi `<%= eNameExp %>` .</span><span class="sxs-lookup"><span data-stu-id="77f4d-123">- Embedded expression of the form `<%= eNameExp %>`.</span></span> <span data-ttu-id="77f4d-124">Türü `eNameExp` `String` veya örtük olarak dönüştürülebilir bir tür olmalıdır <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="77f4d-124">The type of `eNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|

  - <span data-ttu-id="77f4d-125">Formun katıştırılmış ifadesi `<%= nameExp %>` .</span><span class="sxs-lookup"><span data-stu-id="77f4d-125">Embedded expression of the form `<%= nameExp %>`.</span></span> <span data-ttu-id="77f4d-126">Türü `nameExp` `String` veya örtülü olarak dönüştürülebilir bir tür olmalıdır <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="77f4d-126">The type of `nameExp` must be `String` or a type implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="77f4d-127">Bir öğenin kapanış etiketinde gömülü ifadeye izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="77f4d-127">An embedded expression is not allowed in a closing tag of an element.</span></span>

- `attributeList`

  <span data-ttu-id="77f4d-128">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="77f4d-128">Optional.</span></span> <span data-ttu-id="77f4d-129">Sabit değerde belirtilen özniteliklerin listesi.</span><span class="sxs-lookup"><span data-stu-id="77f4d-129">List of attributes declared in the literal.</span></span>

  `attribute [ attribute ... ]`

  <span data-ttu-id="77f4d-130">Her biri `attribute` aşağıdaki sözdizimlerinden birine sahiptir:</span><span class="sxs-lookup"><span data-stu-id="77f4d-130">Each `attribute` has one of the following syntaxes:</span></span>

  - <span data-ttu-id="77f4d-131">Formun öznitelik ataması, `[aPrefix:]aName=aValue` burada:</span><span class="sxs-lookup"><span data-stu-id="77f4d-131">Attribute assignment, of the form `[aPrefix:]aName=aValue`, where:</span></span>

    |<span data-ttu-id="77f4d-132">Bölüm</span><span class="sxs-lookup"><span data-stu-id="77f4d-132">Part</span></span>|<span data-ttu-id="77f4d-133">Description</span><span class="sxs-lookup"><span data-stu-id="77f4d-133">Description</span></span>|
    |---|---|
    |`aPrefix`|<span data-ttu-id="77f4d-134">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="77f4d-134">Optional.</span></span> <span data-ttu-id="77f4d-135">Öznitelik için XML ad alanı ön eki.</span><span class="sxs-lookup"><span data-stu-id="77f4d-135">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="77f4d-136">Bir ifadesiyle tanımlanmış bir genel XML ad alanı `Imports` ya da bu öğede veya bir üst öğede tanımlanan yerel BIR XML ad alanı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="77f4d-136">Must be a global XML namespace that is defined with an `Imports` statement, or a local XML namespace that is defined in this element or a parent element.</span></span>|
    |`aName`|<span data-ttu-id="77f4d-137">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="77f4d-137">Required.</span></span> <span data-ttu-id="77f4d-138">Özniteliğin adı.</span><span class="sxs-lookup"><span data-stu-id="77f4d-138">Name of the attribute.</span></span> <span data-ttu-id="77f4d-139">Biçim aşağıdakilerden biridir:</span><span class="sxs-lookup"><span data-stu-id="77f4d-139">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="77f4d-140">-Sabit metin.</span><span class="sxs-lookup"><span data-stu-id="77f4d-140">- Literal text.</span></span> <span data-ttu-id="77f4d-141">[BELIRTILEN XML öğelerinin ve özniteliklerin adlarına](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="77f4d-141">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="77f4d-142">-Formun katıştırılmış ifadesi `<%= aNameExp %>` .</span><span class="sxs-lookup"><span data-stu-id="77f4d-142">- Embedded expression of the form `<%= aNameExp %>`.</span></span> <span data-ttu-id="77f4d-143">Türü `aNameExp` `String` veya örtük olarak dönüştürülebilir bir tür olmalıdır <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="77f4d-143">The type of `aNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|
    |`aValue`|<span data-ttu-id="77f4d-144">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="77f4d-144">Optional.</span></span> <span data-ttu-id="77f4d-145">Özniteliğin değeri.</span><span class="sxs-lookup"><span data-stu-id="77f4d-145">Value of the attribute.</span></span> <span data-ttu-id="77f4d-146">Biçim aşağıdakilerden biridir:</span><span class="sxs-lookup"><span data-stu-id="77f4d-146">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="77f4d-147">-Düz metin, tırnak işaretleri içine alınır.</span><span class="sxs-lookup"><span data-stu-id="77f4d-147">- Literal text, enclosed in quotation marks.</span></span><br /><span data-ttu-id="77f4d-148">-Formun katıştırılmış ifadesi `<%= aValueExp %>` .</span><span class="sxs-lookup"><span data-stu-id="77f4d-148">- Embedded expression of the form `<%= aValueExp %>`.</span></span> <span data-ttu-id="77f4d-149">Herhangi bir türe izin verilir.</span><span class="sxs-lookup"><span data-stu-id="77f4d-149">Any type is allowed.</span></span>|

  - <span data-ttu-id="77f4d-150">Formun katıştırılmış ifadesi `<%= aExp %>` .</span><span class="sxs-lookup"><span data-stu-id="77f4d-150">Embedded expression of the form `<%= aExp %>`.</span></span>

- `/>`

  <span data-ttu-id="77f4d-151">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="77f4d-151">Optional.</span></span> <span data-ttu-id="77f4d-152">Öğenin, içerik olmadan boş bir öğe olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="77f4d-152">Indicates that the element is an empty element, without content.</span></span>

- `>`

  <span data-ttu-id="77f4d-153">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="77f4d-153">Required.</span></span> <span data-ttu-id="77f4d-154">Başlangıç veya boş öğe etiketini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="77f4d-154">Ends the beginning or empty element tag.</span></span>

- `elementContents`

  <span data-ttu-id="77f4d-155">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="77f4d-155">Optional.</span></span> <span data-ttu-id="77f4d-156">Öğenin içeriği.</span><span class="sxs-lookup"><span data-stu-id="77f4d-156">Content of the element.</span></span>

  `content [ content ... ]`

  <span data-ttu-id="77f4d-157">Her biri `content` aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="77f4d-157">Each `content` can be one of the following:</span></span>

  - <span data-ttu-id="77f4d-158">Değişmez değer metni.</span><span class="sxs-lookup"><span data-stu-id="77f4d-158">Literal text.</span></span> <span data-ttu-id="77f4d-159">İçindeki tüm boşluklar, `elementContents` herhangi bir sabit metin varsa önemli hale gelir.</span><span class="sxs-lookup"><span data-stu-id="77f4d-159">All the white space in `elementContents` becomes significant if there is any literal text.</span></span>

  - <span data-ttu-id="77f4d-160">Formun katıştırılmış ifadesi `<%= contentExp %>` .</span><span class="sxs-lookup"><span data-stu-id="77f4d-160">Embedded expression of the form `<%= contentExp %>`.</span></span>

  - <span data-ttu-id="77f4d-161">XML öğesi değişmez değeri.</span><span class="sxs-lookup"><span data-stu-id="77f4d-161">XML element literal.</span></span>

  - <span data-ttu-id="77f4d-162">XML açıklama değişmez değeri.</span><span class="sxs-lookup"><span data-stu-id="77f4d-162">XML comment literal.</span></span> <span data-ttu-id="77f4d-163">Bkz. [XML açıklama değişmez değeri](xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="77f4d-163">See [XML Comment Literal](xml-comment-literal.md).</span></span>

  - <span data-ttu-id="77f4d-164">XML işleme yönergesi sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="77f4d-164">XML processing instruction literal.</span></span> <span data-ttu-id="77f4d-165">Bkz. [XML Işleme yönergesi sabit değeri](xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="77f4d-165">See [XML Processing Instruction Literal](xml-processing-instruction-literal.md).</span></span>

  - <span data-ttu-id="77f4d-166">XML CDATA değişmez değeri.</span><span class="sxs-lookup"><span data-stu-id="77f4d-166">XML CDATA literal.</span></span> <span data-ttu-id="77f4d-167">Bkz. [XML CDATA değişmez değeri](xml-cdata-literal.md).</span><span class="sxs-lookup"><span data-stu-id="77f4d-167">See [XML CDATA Literal](xml-cdata-literal.md).</span></span>

- `</[name]>`

  <span data-ttu-id="77f4d-168">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="77f4d-168">Optional.</span></span> <span data-ttu-id="77f4d-169">Öğe için kapanış etiketini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="77f4d-169">Represents the closing tag for the element.</span></span> <span data-ttu-id="77f4d-170">İsteğe bağlı `name` parametreye, gömülü bir ifadenin sonucu olduğunda izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="77f4d-170">The optional `name` parameter is not allowed when it is the result of an embedded expression.</span></span>

## <a name="return-value"></a><span data-ttu-id="77f4d-171">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="77f4d-171">Return Value</span></span>

<span data-ttu-id="77f4d-172">Bir <xref:System.Xml.Linq.XElement> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="77f4d-172">An <xref:System.Xml.Linq.XElement> object.</span></span>

## <a name="remarks"></a><span data-ttu-id="77f4d-173">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="77f4d-173">Remarks</span></span>

<span data-ttu-id="77f4d-174">Kodunuzda nesneler oluşturmak için XML öğesi değişmez sözdizimini kullanabilirsiniz <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="77f4d-174">You can use the XML element literal syntax to create <xref:System.Xml.Linq.XElement> objects in your code.</span></span>

> [!NOTE]
> <span data-ttu-id="77f4d-175">Bir XML sabit değeri, satır devamlılık karakterleri kullanmadan birden fazla satıra yayılabilir.</span><span class="sxs-lookup"><span data-stu-id="77f4d-175">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="77f4d-176">Bu özellik bir XML belgesinden içerik kopyalamanızı ve bunu doğrudan bir Visual Basic programına yapıştırmayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="77f4d-176">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>

<span data-ttu-id="77f4d-177">Formun katıştırılmış ifadeleri `<%= exp %>` , BIR XML öğesi değişmez değerine dinamik bilgi eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="77f4d-177">Embedded expressions of the form `<%= exp %>` enable you to add dynamic information to an XML element literal.</span></span> <span data-ttu-id="77f4d-178">Daha fazla bilgi için bkz. [XML 'de katıştırılmış ifadeler](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="77f4d-178">For more information, see [Embedded Expressions in XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>

<span data-ttu-id="77f4d-179">Visual Basic derleyici, XML öğesi değişmez değerini oluşturucuya yapılan çağrılara dönüştürür <xref:System.Xml.Linq.XElement.%23ctor%2A> ve gerekirse, <xref:System.Xml.Linq.XAttribute.%23ctor%2A> Oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="77f4d-179">The Visual Basic compiler converts the XML element literal into calls to the <xref:System.Xml.Linq.XElement.%23ctor%2A> constructor and, if it is required, the <xref:System.Xml.Linq.XAttribute.%23ctor%2A> constructor.</span></span>

## <a name="xml-namespaces"></a><span data-ttu-id="77f4d-180">XML ad alanları</span><span class="sxs-lookup"><span data-stu-id="77f4d-180">XML Namespaces</span></span>

<span data-ttu-id="77f4d-181">XML ad alanı önekleri, kodda birçok kez aynı ad alanındaki öğelerle XML değişmez değerleri oluşturmanız gerektiğinde faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="77f4d-181">XML namespace prefixes are useful when you have to create XML literals with elements from the same namespace many times in code.</span></span> <span data-ttu-id="77f4d-182">Özniteliğini kullanarak tanımladığınız genel XML ad alanı öneklerini `Imports` veya öznitelik sözdizimini kullanarak tanımladığınız yerel önekleri kullanabilirsiniz `xmlns:xmlPrefix="xmlNamespace"` .</span><span class="sxs-lookup"><span data-stu-id="77f4d-182">You can use global XML namespace prefixes, which you define by using the `Imports` statement, or local prefixes, which you define by using the `xmlns:xmlPrefix="xmlNamespace"` attribute syntax.</span></span> <span data-ttu-id="77f4d-183">Daha fazla bilgi için bkz. [Imports bildirisi (XML ad alanı)](../statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="77f4d-183">For more information, see [Imports Statement (XML Namespace)](../statements/imports-statement-xml-namespace.md).</span></span>

<span data-ttu-id="77f4d-184">XML ad alanları için kapsam kurallarına uygun olarak, yerel ön ekler genel öneklere göre önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="77f4d-184">In accordance with the scoping rules for XML namespaces, local prefixes take precedence over global prefixes.</span></span> <span data-ttu-id="77f4d-185">Ancak, bir XML sabit değeri bir XML ad alanı tanımlıyorsa, bu ad alanı katıştırılmış ifadede görünen ifadeler için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="77f4d-185">However, if an XML literal defines an XML namespace, that namespace is not available to expressions that appear in an embedded expression.</span></span> <span data-ttu-id="77f4d-186">Katıştırılmış ifade yalnızca genel XML ad alanına erişebilir.</span><span class="sxs-lookup"><span data-stu-id="77f4d-186">The embedded expression can access only the global XML namespace.</span></span>

<span data-ttu-id="77f4d-187">Visual Basic Derleyicisi, bir XML sabit değeri tarafından kullanılan her genel XML ad alanını oluşturulan kodda tek bir yerel ad alanı tanımına dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="77f4d-187">The Visual Basic compiler converts each global XML namespace that is used by an XML literal into a one local namespace definition in the generated code.</span></span> <span data-ttu-id="77f4d-188">Kullanılmayan genel XML ad alanları oluşturulan kodda görünmez.</span><span class="sxs-lookup"><span data-stu-id="77f4d-188">Global XML namespaces that are not used do not appear in the generated code.</span></span>

## <a name="example"></a><span data-ttu-id="77f4d-189">Örnek</span><span class="sxs-lookup"><span data-stu-id="77f4d-189">Example</span></span>

<span data-ttu-id="77f4d-190">Aşağıdaki örnek, iki iç içe boş öğesi olan basit bir XML öğesinin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="77f4d-190">The following example shows how to create a simple XML element that has two nested empty elements.</span></span>

[!code-vb[VbXMLSamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#20)]

<span data-ttu-id="77f4d-191">Örnekte aşağıdaki metin görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="77f4d-191">The example displays the following text.</span></span> <span data-ttu-id="77f4d-192">Sabit değerin boş öğelerin yapısını koruyan bir değer görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="77f4d-192">Notice that the literal preserves the structure of the empty elements.</span></span>

```xml
<outer>
  <inner1></inner1>
  <inner2 />
</outer>
```

## <a name="example"></a><span data-ttu-id="77f4d-193">Örnek</span><span class="sxs-lookup"><span data-stu-id="77f4d-193">Example</span></span>

<span data-ttu-id="77f4d-194">Aşağıdaki örnek, bir öğeyi adlandırmak ve öznitelikleri oluşturmak için katıştırılmış ifadelerin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="77f4d-194">The following example shows how to use embedded expressions to name an element and create attributes.</span></span>

[!code-vb[VbXMLSamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#21)]

<span data-ttu-id="77f4d-195">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="77f4d-195">This code displays the following text:</span></span>

```xml
<book isbn="1234" author="My Author" year="1999" title="My Book" />
```

## <a name="example"></a><span data-ttu-id="77f4d-196">Örnek</span><span class="sxs-lookup"><span data-stu-id="77f4d-196">Example</span></span>

<span data-ttu-id="77f4d-197">Aşağıdaki örnek `ns` BIR XML ad alanı ön eki olarak bildirir.</span><span class="sxs-lookup"><span data-stu-id="77f4d-197">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="77f4d-198">Daha sonra bir XML sabit değeri oluşturmak için ad alanının önekini kullanır ve öğenin son formunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="77f4d-198">It then uses the prefix of the namespace to create an XML literal and displays the element's final form.</span></span>

[!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]

<span data-ttu-id="77f4d-199">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="77f4d-199">This code displays the following text:</span></span>

```xml
<ns:outer xmlns:ns="http://SomeNamespace">
  <ns:middle xmlns:ns="http://NewNamespace">
    <ns:inner1 />
    <inner2 xmlns="http://SomeNamespace" />
  </ns:middle>
</ns:outer>
```

<span data-ttu-id="77f4d-200">Derleyicinin genel XML ad alanının önekini XML ad alanı için bir önek tanımına dönüştürdüğüne dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="77f4d-200">Notice that the compiler converted the prefix of the global XML namespace into a prefix definition for the XML namespace.</span></span> <span data-ttu-id="77f4d-201">\<ns:middle>Öğesi öğesi IÇIN XML ad alanı önekini tekrar tanımlar \<ns:inner1> .</span><span class="sxs-lookup"><span data-stu-id="77f4d-201">The \<ns:middle> element redefines the XML namespace prefix for the \<ns:inner1> element.</span></span> <span data-ttu-id="77f4d-202">Ancak, \<ns:inner2> öğesi, ifadesiyle tanımlanan ad alanını kullanır `Imports` .</span><span class="sxs-lookup"><span data-stu-id="77f4d-202">However, the \<ns:inner2> element uses the namespace defined by the `Imports` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="77f4d-203">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77f4d-203">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="77f4d-204">Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları</span><span class="sxs-lookup"><span data-stu-id="77f4d-204">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [<span data-ttu-id="77f4d-205">XML Açıklama Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="77f4d-205">XML Comment Literal</span></span>](xml-comment-literal.md)
- [<span data-ttu-id="77f4d-206">XML CDATA Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="77f4d-206">XML CDATA Literal</span></span>](xml-cdata-literal.md)
- [<span data-ttu-id="77f4d-207">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="77f4d-207">XML Literals</span></span>](index.md)
- [<span data-ttu-id="77f4d-208">Visual Basic'de XML Oluşturma</span><span class="sxs-lookup"><span data-stu-id="77f4d-208">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="77f4d-209">XML'de Katıştırılmış İfadeler</span><span class="sxs-lookup"><span data-stu-id="77f4d-209">Embedded Expressions in XML</span></span>](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [<span data-ttu-id="77f4d-210">Imports Deyimi (XML Ad Alanı)</span><span class="sxs-lookup"><span data-stu-id="77f4d-210">Imports Statement (XML Namespace)</span></span>](../statements/imports-statement-xml-namespace.md)
