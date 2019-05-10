---
title: XML Öğesi Değişmez Değeri (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
ms.openlocfilehash: 3431ad32809e1f15eb8473d5af7660367cca04de
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64751956"
---
# <a name="xml-element-literal-visual-basic"></a><span data-ttu-id="32c47-102">XML Öğesi Değişmez Değeri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32c47-102">XML Element Literal (Visual Basic)</span></span>

<span data-ttu-id="32c47-103">Temsil eden bir değişmez bir <xref:System.Xml.Linq.XElement> nesne.</span><span class="sxs-lookup"><span data-stu-id="32c47-103">A literal that represents an <xref:System.Xml.Linq.XElement> object.</span></span>

## <a name="syntax"></a><span data-ttu-id="32c47-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32c47-104">Syntax</span></span>

```xml
<name [ attributeList ] />
-or-
<name [ attributeList ] > [ elementContents ] </[ name ]>
```

## <a name="parts"></a><span data-ttu-id="32c47-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="32c47-105">Parts</span></span>

- `<`

  <span data-ttu-id="32c47-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="32c47-106">Required.</span></span> <span data-ttu-id="32c47-107">Başlangıç öğesi etiketi açılır.</span><span class="sxs-lookup"><span data-stu-id="32c47-107">Opens the starting element tag.</span></span>

- `name`

  <span data-ttu-id="32c47-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="32c47-108">Required.</span></span> <span data-ttu-id="32c47-109">Öğe adı.</span><span class="sxs-lookup"><span data-stu-id="32c47-109">Name of the element.</span></span> <span data-ttu-id="32c47-110">Biçim aşağıdakilerden biridir:</span><span class="sxs-lookup"><span data-stu-id="32c47-110">The format is one of the following:</span></span>

  - <span data-ttu-id="32c47-111">Düz metin biçiminde öğe adı için `[ePrefix:]eName`burada:</span><span class="sxs-lookup"><span data-stu-id="32c47-111">Literal text for the element name, of the form `[ePrefix:]eName`, where:</span></span>

    |<span data-ttu-id="32c47-112">Bölümü</span><span class="sxs-lookup"><span data-stu-id="32c47-112">Part</span></span>|<span data-ttu-id="32c47-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32c47-113">Description</span></span>|
    |---|---|
    |`ePrefix`|<span data-ttu-id="32c47-114">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="32c47-114">Optional.</span></span> <span data-ttu-id="32c47-115">Öğesi için XML ad alanı öneki.</span><span class="sxs-lookup"><span data-stu-id="32c47-115">XML namespace prefix for the element.</span></span> <span data-ttu-id="32c47-116">İle tanımlanan genel bir XML ad alanı olmalıdır bir `Imports` dosyası veya proje düzeyinde veya bu öğenin veya üst öğenin tanımlandığı yerel bir XML ad alanı bildirimi.</span><span class="sxs-lookup"><span data-stu-id="32c47-116">Must be a global XML namespace that is defined with an `Imports` statement in the file or at the project level, or a local XML namespace that is defined in this element or a parent element.</span></span>|
    |`eName`|<span data-ttu-id="32c47-117">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="32c47-117">Required.</span></span> <span data-ttu-id="32c47-118">Öğe adı.</span><span class="sxs-lookup"><span data-stu-id="32c47-118">Name of the element.</span></span> <span data-ttu-id="32c47-119">Biçim aşağıdakilerden biridir:</span><span class="sxs-lookup"><span data-stu-id="32c47-119">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="32c47-120">-Düz metin.</span><span class="sxs-lookup"><span data-stu-id="32c47-120">- Literal text.</span></span> <span data-ttu-id="32c47-121">Bkz: [bildirilmiş XML öğeleri ve özniteliklerinin adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="32c47-121">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="32c47-122">-Gömülü ifade formun `<%= eNameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="32c47-122">- Embedded expression of the form `<%= eNameExp %>`.</span></span> <span data-ttu-id="32c47-123">Türünü `eNameExp` olmalıdır `String` ya da örtük olarak dönüştürülebilir bir türün <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="32c47-123">The type of `eNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|

  - <span data-ttu-id="32c47-124">Gömülü deyim `<%= nameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="32c47-124">Embedded expression of the form `<%= nameExp %>`.</span></span> <span data-ttu-id="32c47-125">Türünü `nameExp` olmalıdır `String` ya da bir tür için örtük olarak dönüştürülebilir <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="32c47-125">The type of `nameExp` must be `String` or a type implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="32c47-126">Gömülü deyim bir öğenin kapatma etiketi içinde izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="32c47-126">An embedded expression is not allowed in a closing tag of an element.</span></span>

- `attributeList`

  <span data-ttu-id="32c47-127">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="32c47-127">Optional.</span></span> <span data-ttu-id="32c47-128">Öznitelikler listesi değişmez değer bildirilmiş.</span><span class="sxs-lookup"><span data-stu-id="32c47-128">List of attributes declared in the literal.</span></span>

  `attribute [ attribute ... ]`

  <span data-ttu-id="32c47-129">Her `attribute` aşağıdaki sözdizimlerinden birini içeriyor:</span><span class="sxs-lookup"><span data-stu-id="32c47-129">Each `attribute` has one of the following syntaxes:</span></span>

  - <span data-ttu-id="32c47-130">Özniteliği formun atamasının `[aPrefix:]aName=aValue`burada:</span><span class="sxs-lookup"><span data-stu-id="32c47-130">Attribute assignment, of the form `[aPrefix:]aName=aValue`, where:</span></span>

    |<span data-ttu-id="32c47-131">Bölümü</span><span class="sxs-lookup"><span data-stu-id="32c47-131">Part</span></span>|<span data-ttu-id="32c47-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32c47-132">Description</span></span>|
    |---|---|
    |`aPrefix`|<span data-ttu-id="32c47-133">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="32c47-133">Optional.</span></span> <span data-ttu-id="32c47-134">Özniteliği için XML ad alanı öneki.</span><span class="sxs-lookup"><span data-stu-id="32c47-134">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="32c47-135">İle tanımlanan genel bir XML ad alanı olmalıdır bir `Imports` deyimi veya bu öğenin veya üst öğenin tanımlandığı yerel bir XML ad alanı.</span><span class="sxs-lookup"><span data-stu-id="32c47-135">Must be a global XML namespace that is defined with an `Imports` statement, or a local XML namespace that is defined in this element or a parent element.</span></span>|
    |`aName`|<span data-ttu-id="32c47-136">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="32c47-136">Required.</span></span> <span data-ttu-id="32c47-137">Özniteliğin adı.</span><span class="sxs-lookup"><span data-stu-id="32c47-137">Name of the attribute.</span></span> <span data-ttu-id="32c47-138">Biçim aşağıdakilerden biridir:</span><span class="sxs-lookup"><span data-stu-id="32c47-138">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="32c47-139">-Düz metin.</span><span class="sxs-lookup"><span data-stu-id="32c47-139">- Literal text.</span></span> <span data-ttu-id="32c47-140">Bkz: [bildirilmiş XML öğeleri ve özniteliklerinin adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="32c47-140">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="32c47-141">-Gömülü ifade formun `<%= aNameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="32c47-141">- Embedded expression of the form `<%= aNameExp %>`.</span></span> <span data-ttu-id="32c47-142">Türünü `aNameExp` olmalıdır `String` ya da örtük olarak dönüştürülebilir bir türün <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="32c47-142">The type of `aNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|
    |`aValue`|<span data-ttu-id="32c47-143">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="32c47-143">Optional.</span></span> <span data-ttu-id="32c47-144">Öznitelik değeri.</span><span class="sxs-lookup"><span data-stu-id="32c47-144">Value of the attribute.</span></span> <span data-ttu-id="32c47-145">Biçim aşağıdakilerden biridir:</span><span class="sxs-lookup"><span data-stu-id="32c47-145">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="32c47-146">-Tırnak işareti içine alınmış değişmez değer metni.</span><span class="sxs-lookup"><span data-stu-id="32c47-146">- Literal text, enclosed in quotation marks.</span></span><br /><span data-ttu-id="32c47-147">-Gömülü ifade formun `<%= aValueExp %>`.</span><span class="sxs-lookup"><span data-stu-id="32c47-147">- Embedded expression of the form `<%= aValueExp %>`.</span></span> <span data-ttu-id="32c47-148">Her türlü izin verilir.</span><span class="sxs-lookup"><span data-stu-id="32c47-148">Any type is allowed.</span></span>|

  - <span data-ttu-id="32c47-149">Gömülü deyim `<%= aExp %>`.</span><span class="sxs-lookup"><span data-stu-id="32c47-149">Embedded expression of the form `<%= aExp %>`.</span></span>

- `/>`

  <span data-ttu-id="32c47-150">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="32c47-150">Optional.</span></span> <span data-ttu-id="32c47-151">Öğe içeriği olmadan boş bir öğe olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="32c47-151">Indicates that the element is an empty element, without content.</span></span>

- `>`

  <span data-ttu-id="32c47-152">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="32c47-152">Required.</span></span> <span data-ttu-id="32c47-153">Başlangıç veya boş öğesi etiketi sona erer.</span><span class="sxs-lookup"><span data-stu-id="32c47-153">Ends the beginning or empty element tag.</span></span>

- `elementContents`

  <span data-ttu-id="32c47-154">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="32c47-154">Optional.</span></span> <span data-ttu-id="32c47-155">Öğe içeriği.</span><span class="sxs-lookup"><span data-stu-id="32c47-155">Content of the element.</span></span>

  `content [ content ... ]`

  <span data-ttu-id="32c47-156">Her `content` aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="32c47-156">Each `content` can be one of the following:</span></span>

  - <span data-ttu-id="32c47-157">Değişmez değer metni.</span><span class="sxs-lookup"><span data-stu-id="32c47-157">Literal text.</span></span> <span data-ttu-id="32c47-158">Tüm bölünemez boşluğu `elementContents` herhangi bir metin ise önemli hale gelir.</span><span class="sxs-lookup"><span data-stu-id="32c47-158">All the white space in `elementContents` becomes significant if there is any literal text.</span></span>

  - <span data-ttu-id="32c47-159">Gömülü deyim `<%= contentExp %>`.</span><span class="sxs-lookup"><span data-stu-id="32c47-159">Embedded expression of the form `<%= contentExp %>`.</span></span>

  - <span data-ttu-id="32c47-160">XML öğesi değişmez değeri.</span><span class="sxs-lookup"><span data-stu-id="32c47-160">XML element literal.</span></span>

  - <span data-ttu-id="32c47-161">XML açıklama değişmez değeri.</span><span class="sxs-lookup"><span data-stu-id="32c47-161">XML comment literal.</span></span> <span data-ttu-id="32c47-162">Bkz: [XML açıklama değişmez değeri](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="32c47-162">See [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span></span>

  - <span data-ttu-id="32c47-163">XML işleme yönergesi değişmez değeri.</span><span class="sxs-lookup"><span data-stu-id="32c47-163">XML processing instruction literal.</span></span> <span data-ttu-id="32c47-164">Bkz: [XML işleme talimatı değişmez değeri](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="32c47-164">See [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span></span>

  - <span data-ttu-id="32c47-165">XML CDATA değişmez değeri.</span><span class="sxs-lookup"><span data-stu-id="32c47-165">XML CDATA literal.</span></span> <span data-ttu-id="32c47-166">Bkz: [XML CDATA değişmez değeri](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).</span><span class="sxs-lookup"><span data-stu-id="32c47-166">See [XML CDATA Literal](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).</span></span>

- `</[name]>`

  <span data-ttu-id="32c47-167">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="32c47-167">Optional.</span></span> <span data-ttu-id="32c47-168">Öğesi için kapanış etiketi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="32c47-168">Represents the closing tag for the element.</span></span> <span data-ttu-id="32c47-169">İsteğe bağlı `name` katıştırılmış bir ifadenin sonucu olduğunda parametresi kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="32c47-169">The optional `name` parameter is not allowed when it is the result of an embedded expression.</span></span>

## <a name="return-value"></a><span data-ttu-id="32c47-170">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="32c47-170">Return Value</span></span>

<span data-ttu-id="32c47-171">Bir <xref:System.Xml.Linq.XElement> nesne.</span><span class="sxs-lookup"><span data-stu-id="32c47-171">An <xref:System.Xml.Linq.XElement> object.</span></span>

## <a name="remarks"></a><span data-ttu-id="32c47-172">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="32c47-172">Remarks</span></span>

<span data-ttu-id="32c47-173">XML öğesi değişmez değeri sözdizimi oluşturmak için kullanabileceğiniz <xref:System.Xml.Linq.XElement> kodunuzda nesneleri.</span><span class="sxs-lookup"><span data-stu-id="32c47-173">You can use the XML element literal syntax to create <xref:System.Xml.Linq.XElement> objects in your code.</span></span>

> [!NOTE]
> <span data-ttu-id="32c47-174">XML değişmez değer birden fazla satır, satır devamlılığı karakteri kullanmadan yayılabilir.</span><span class="sxs-lookup"><span data-stu-id="32c47-174">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="32c47-175">Bu özellik, bir XML belgesinden içeriği kopyalayın ve doğrudan bir Visual Basic programına yapıştırın sağlar.</span><span class="sxs-lookup"><span data-stu-id="32c47-175">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>

<span data-ttu-id="32c47-176">Katıştırılmış ifadeler formun `<%= exp %>` bir XML öğesi değişmez değeri dinamik bilgi eklemenize imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="32c47-176">Embedded expressions of the form `<%= exp %>` enable you to add dynamic information to an XML element literal.</span></span> <span data-ttu-id="32c47-177">Daha fazla bilgi için [XML'de katıştırılmış ifadeler](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="32c47-177">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>

<span data-ttu-id="32c47-178">Visual Basic derleyici çağrıları XML öğesi değişmez değeri dönüştürür <xref:System.Xml.Linq.XElement.%23ctor%2A> oluşturucusu ve, gerekirse <xref:System.Xml.Linq.XAttribute.%23ctor%2A> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="32c47-178">The Visual Basic compiler converts the XML element literal into calls to the <xref:System.Xml.Linq.XElement.%23ctor%2A> constructor and, if it is required, the <xref:System.Xml.Linq.XAttribute.%23ctor%2A> constructor.</span></span>

## <a name="xml-namespaces"></a><span data-ttu-id="32c47-179">XML ad alanları</span><span class="sxs-lookup"><span data-stu-id="32c47-179">XML Namespaces</span></span>

<span data-ttu-id="32c47-180">XML ad alanı öneklerini kodda birden çok kez aynı ad alanından öğeler ile XML değişmez değerleri oluşturma gerektiğinde kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="32c47-180">XML namespace prefixes are useful when you have to create XML literals with elements from the same namespace many times in code.</span></span> <span data-ttu-id="32c47-181">Kullanarak tanımlayan genel XML ad alanı öneklerini kullanabileceğiniz `Imports` deyimi kullanarak tanımladığınız yerel ön ek veya `xmlns:xmlPrefix="xmlNamespace"` öznitelik sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="32c47-181">You can use global XML namespace prefixes, which you define by using the `Imports` statement, or local prefixes, which you define by using the `xmlns:xmlPrefix="xmlNamespace"` attribute syntax.</span></span> <span data-ttu-id="32c47-182">Daha fazla bilgi için [Imports deyimi (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="32c47-182">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>

<span data-ttu-id="32c47-183">XML ad alanları için içeriğin kapsamını belirleyen kuralları uygun olarak yerel öneklerini genel ön ekler öncelik kazanır.</span><span class="sxs-lookup"><span data-stu-id="32c47-183">In accordance with the scoping rules for XML namespaces, local prefixes take precedence over global prefixes.</span></span> <span data-ttu-id="32c47-184">Bir XML değişmez değeri bir XML ad alanı tanımlıyorsa, ancak bu ad alanı bir katıştırılmış deyim içinde görünen ifadeleri kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="32c47-184">However, if an XML literal defines an XML namespace, that namespace is not available to expressions that appear in an embedded expression.</span></span> <span data-ttu-id="32c47-185">Gömülü deyim yalnızca genel XML ad alanı erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32c47-185">The embedded expression can access only the global XML namespace.</span></span>

<span data-ttu-id="32c47-186">Visual Basic Derleyicisi, bir XML değişmez değer oluşturulan kodda bir yerel ad alanı tanımı içinde kullanılan her genel XML ad alanı dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="32c47-186">The Visual Basic compiler converts each global XML namespace that is used by an XML literal into a one local namespace definition in the generated code.</span></span> <span data-ttu-id="32c47-187">Kullanılmayan genel XML ad alanları oluşturulan kodda görünmez.</span><span class="sxs-lookup"><span data-stu-id="32c47-187">Global XML namespaces that are not used do not appear in the generated code.</span></span>

## <a name="example"></a><span data-ttu-id="32c47-188">Örnek</span><span class="sxs-lookup"><span data-stu-id="32c47-188">Example</span></span>

<span data-ttu-id="32c47-189">Aşağıdaki örnekte, iç içe iki boş öğeleri olan basit bir XML öğesi oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="32c47-189">The following example shows how to create a simple XML element that has two nested empty elements.</span></span>

[!code-vb[VbXMLSamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#20)]

<span data-ttu-id="32c47-190">Örneğin, aşağıdaki metni görüntüler.</span><span class="sxs-lookup"><span data-stu-id="32c47-190">The example displays the following text.</span></span> <span data-ttu-id="32c47-191">Değişmez değer boş öğeleri yapısını korur dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="32c47-191">Notice that the literal preserves the structure of the empty elements.</span></span>

```xml
<outer>
  <inner1></inner1>
  <inner2 />
</outer>
```

## <a name="example"></a><span data-ttu-id="32c47-192">Örnek</span><span class="sxs-lookup"><span data-stu-id="32c47-192">Example</span></span>

<span data-ttu-id="32c47-193">Aşağıdaki örnek, bir öğe adı ve öznitelikler oluşturmak için katıştırılmış ifadeleri kullanma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="32c47-193">The following example shows how to use embedded expressions to name an element and create attributes.</span></span>

[!code-vb[VbXMLSamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#21)]

<span data-ttu-id="32c47-194">Bu kod, aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="32c47-194">This code displays the following text:</span></span>

```xml
<book isbn="1234" author="My Author" year="1999" title="My Book" />
```

## <a name="example"></a><span data-ttu-id="32c47-195">Örnek</span><span class="sxs-lookup"><span data-stu-id="32c47-195">Example</span></span>

<span data-ttu-id="32c47-196">Aşağıdaki örnek bildirir `ns` olarak bir XML ad alanı öneki.</span><span class="sxs-lookup"><span data-stu-id="32c47-196">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="32c47-197">XML değişmez değer oluşturmak için ad alanı öneki kullanır ve öğenin son form görüntüler.</span><span class="sxs-lookup"><span data-stu-id="32c47-197">It then uses the prefix of the namespace to create an XML literal and displays the element's final form.</span></span>

[!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]

<span data-ttu-id="32c47-198">Bu kod, aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="32c47-198">This code displays the following text:</span></span>

```xml
<ns:outer xmlns:ns="http://SomeNamespace">
  <ns:middle xmlns:ns="http://NewNamespace">
    <ns:inner1 />
    <inner2 xmlns="http://SomeNamespace" />
  </ns:middle>
</ns:outer>
```

<span data-ttu-id="32c47-199">Derleyicinin XML ad alanı için bir önek tanımı genel XML ad alanı öneki dönüştürülür dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="32c47-199">Notice that the compiler converted the prefix of the global XML namespace into a prefix definition for the XML namespace.</span></span> <span data-ttu-id="32c47-200">\<Ns:middle > öğesi için XML ad alanı öneki'ı yeniden tanımladığı \<ns:inner1 > öğesi.</span><span class="sxs-lookup"><span data-stu-id="32c47-200">The \<ns:middle> element redefines the XML namespace prefix for the \<ns:inner1> element.</span></span> <span data-ttu-id="32c47-201">Ancak, \<ns:inner2 > öğesi tarafından tanımlanan ad alanı kullanan `Imports` deyimi.</span><span class="sxs-lookup"><span data-stu-id="32c47-201">However, the \<ns:inner2> element uses the namespace defined by the `Imports` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="32c47-202">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32c47-202">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="32c47-203">Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları</span><span class="sxs-lookup"><span data-stu-id="32c47-203">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [<span data-ttu-id="32c47-204">XML Açıklama Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="32c47-204">XML Comment Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [<span data-ttu-id="32c47-205">XML CDATA Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="32c47-205">XML CDATA Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)
- [<span data-ttu-id="32c47-206">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="32c47-206">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="32c47-207">Visual Basic'de XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="32c47-207">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="32c47-208">XML'de Katıştırılmış İfadeler</span><span class="sxs-lookup"><span data-stu-id="32c47-208">Embedded Expressions in XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [<span data-ttu-id="32c47-209">Imports Deyimi (XML Ad Alanı)</span><span class="sxs-lookup"><span data-stu-id="32c47-209">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
