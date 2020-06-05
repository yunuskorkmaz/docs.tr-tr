---
title: Imports ekstresi-XML ad alanı
ms.date: 07/20/2015
f1_keywords:
- vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
ms.openlocfilehash: a3184d68b0e4cdff5d4296a5a638e22b4e83bcde
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404543"
---
# <a name="imports-statement-xml-namespace"></a><span data-ttu-id="aa371-102">Imports Deyimi (XML Ad Alanı)</span><span class="sxs-lookup"><span data-stu-id="aa371-102">Imports Statement (XML Namespace)</span></span>

<span data-ttu-id="aa371-103">XML sabit değerleri ve XML eksen özelliklerinde kullanılmak üzere XML ad alanı öneklerini içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="aa371-103">Imports XML namespace prefixes for use in XML literals and XML axis properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="aa371-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aa371-104">Syntax</span></span>

```vb
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">
```

## <a name="parts"></a><span data-ttu-id="aa371-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="aa371-105">Parts</span></span>

`xmlNamespacePrefix`  
<span data-ttu-id="aa371-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="aa371-106">Optional.</span></span> <span data-ttu-id="aa371-107">XML öğelerinin ve özniteliklerin başvurabileceği dize `xmlNamespaceName` .</span><span class="sxs-lookup"><span data-stu-id="aa371-107">The string by which XML elements and attributes can refer to `xmlNamespaceName`.</span></span> <span data-ttu-id="aa371-108">Hayır `xmlNamespacePrefix` sağlanmazsa, içeri AKTARıLAN XML ad alanı varsayılan XML ad alanıdır.</span><span class="sxs-lookup"><span data-stu-id="aa371-108">If no `xmlNamespacePrefix` is supplied, the imported XML namespace is the default XML namespace.</span></span> <span data-ttu-id="aa371-109">Geçerli bir XML tanımlayıcısı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aa371-109">Must be a valid XML identifier.</span></span> <span data-ttu-id="aa371-110">Daha fazla bilgi için bkz. [BELIRTILEN XML öğelerinin ve özniteliklerin adları](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="aa371-110">For more information, see [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>

`xmlNamespaceName`  
<span data-ttu-id="aa371-111">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="aa371-111">Required.</span></span> <span data-ttu-id="aa371-112">İçeri aktarılmakta olan XML ad alanını tanımlayan dize.</span><span class="sxs-lookup"><span data-stu-id="aa371-112">The string identifying the XML namespace being imported.</span></span>

## <a name="remarks"></a><span data-ttu-id="aa371-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aa371-113">Remarks</span></span>

<span data-ttu-id="aa371-114">`Imports`XML değişmez değerleri ve xml eksen özellikleriyle kullanabileceğiniz ya da işlecine geçirilen parametreler olarak genel XML ad alanlarını tanımlamak için, ifadesini kullanabilirsiniz `GetXmlNamespace` .</span><span class="sxs-lookup"><span data-stu-id="aa371-114">You can use the `Imports` statement to define global XML namespaces that you can use with XML literals and XML axis properties, or as parameters passed to the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="aa371-115">( `Imports` Tür adlarının kodunuzda kullanıldığı yerde kullanılabilecek bir diğer adı içe aktarmak için ifadesini kullanma hakkında bilgi için bkz. [Imports bildirisi (.net ad alanı ve türü)](imports-statement-net-namespace-and-type.md).) İfadesini kullanarak bir XML ad alanı bildirme sözdizimi, `Imports` XML 'de kullanılan söz dizimiyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="aa371-115">(For information about using the `Imports` statement to import an alias that can be used where type names are used in your code, see [Imports Statement (.NET Namespace and Type)](imports-statement-net-namespace-and-type.md).) The syntax for declaring an XML namespace by using the `Imports` statement is identical to the syntax used in XML.</span></span> <span data-ttu-id="aa371-116">Bu nedenle, bir XML dosyasından bir ad alanı bildirimi kopyalayabilir ve bunu bir `Imports` bildirimde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa371-116">Therefore, you can copy a namespace declaration from an XML file and use it in an `Imports` statement.</span></span>

<span data-ttu-id="aa371-117">XML ad alanı önekleri, aynı ad alanından daha tekrarlı XML öğeleri oluşturmak istediğinizde faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="aa371-117">XML namespace prefixes are useful when you want to repeatedly create XML elements that are from the same namespace.</span></span> <span data-ttu-id="aa371-118">İfadesiyle belirtilen XML ad alanı öneki, `Imports` dosyadaki tüm kod için kullanılabilir olduğunu anlamlı bir şekilde geneldir.</span><span class="sxs-lookup"><span data-stu-id="aa371-118">The XML namespace prefix declared with the `Imports` statement is global in the sense that it is available to all code in the file.</span></span> <span data-ttu-id="aa371-119">XML öğesi değişmez değerleri oluştururken ve XML eksen özelliklerine eriştiğinizde bu özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa371-119">You can use it when you create XML element literals and when you access XML axis properties.</span></span> <span data-ttu-id="aa371-120">Daha fazla bilgi için bkz. [XML öğesi değişmez değeri](../xml-literals/xml-element-literal.md) ve [xml eksen özellikleri](../xml-axis/index.md).</span><span class="sxs-lookup"><span data-stu-id="aa371-120">For more information, see [XML Element Literal](../xml-literals/xml-element-literal.md) and [XML Axis Properties](../xml-axis/index.md).</span></span>

<span data-ttu-id="aa371-121">Bir ad alanı öneki olmadan (örneğin,) genel bir XML ad alanı tanımlarsanız `Imports <xmlns="http://SomeNameSpace>"` , bu ad alanı varsayılan XML ad alanı olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="aa371-121">If you define a global XML namespace without a namespace prefix (for example, `Imports <xmlns="http://SomeNameSpace>"`), that namespace is considered the default XML namespace.</span></span> <span data-ttu-id="aa371-122">Varsayılan XML ad alanı, açıkça bir ad alanı belirtmeyen hiçbir XML öğesi değişmez değeri veya XML özniteliği eksen özellikleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aa371-122">The default XML namespace is used for any XML element literals or XML attribute axis properties that do not explicitly specify a namespace.</span></span> <span data-ttu-id="aa371-123">Varsayılan ad alanı, belirtilen ad alanı boş ad alanı (yani,) ise de kullanılır `xmlns=""` .</span><span class="sxs-lookup"><span data-stu-id="aa371-123">The default namespace is also used if the specified namespace is the empty namespace (that is, `xmlns=""`).</span></span> <span data-ttu-id="aa371-124">Varsayılan XML ad alanı, XML değişmez değerlerinde veya bir ad alanına sahip olmayan XML öznitelik ekseni özellikleriyle XML öznitelikleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="aa371-124">The default XML namespace does not apply to XML attributes in XML literals or to XML attribute axis properties that do not have a namespace.</span></span>

<span data-ttu-id="aa371-125">*Yerel xml ad alanları*olarak adlandırılan XML sabit DEĞERINDE tanımlanmış XML ad alanları, genel olarak, IFADESIYLE tanımlanmış XML ad alanlarını önceliklidir `Imports` .</span><span class="sxs-lookup"><span data-stu-id="aa371-125">XML namespaces that are defined in an XML literal, which are called *local XML namespaces*, take precedence over XML namespaces that are defined by the `Imports` statement as global.</span></span> <span data-ttu-id="aa371-126">İfadesiyle tanımlanan XML ad alanları, `Imports` bir Visual Basic projesi için içeri AKTARıLAN XML ad alanlarına göre önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="aa371-126">XML namespaces that are defined by the `Imports` statement take precedence over XML namespaces imported for a Visual Basic project.</span></span> <span data-ttu-id="aa371-127">Bir XML sabit değeri bir XML ad alanı tanımlıyorsa, bu yerel ad alanı katıştırılmış ifadeler için uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="aa371-127">If an XML literal defines an XML namespace, that local namespace does not apply to embedded expressions.</span></span>

<span data-ttu-id="aa371-128">Genel XML ad alanları, .NET Framework ad alanları ile aynı kapsam ve tanım kurallarını izler.</span><span class="sxs-lookup"><span data-stu-id="aa371-128">Global XML namespaces follow the same scoping and definition rules as .NET Framework namespaces.</span></span> <span data-ttu-id="aa371-129">Sonuç olarak, `Imports` bir .NET Framework ad alanını içeri aktarabileceğiniz yerde, genel BIR XML ad alanı tanımlamak için bir ifade ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa371-129">As a result, you can include an `Imports` statement to define a global XML namespace anywhere you can import a .NET Framework namespace.</span></span> <span data-ttu-id="aa371-130">Bu hem kod dosyalarını hem de proje düzeyinde içeri aktarılan ad alanlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="aa371-130">This includes both code files and project-level imported namespaces.</span></span> <span data-ttu-id="aa371-131">Proje düzeyinde içeri aktarılan ad alanları hakkında bilgi için bkz. [Başvurular sayfası, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="aa371-131">For information about project-level imported namespaces, see [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span>

<span data-ttu-id="aa371-132">Her kaynak dosya, herhangi bir sayıda `Imports` deyim içerebilir.</span><span class="sxs-lookup"><span data-stu-id="aa371-132">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="aa371-133">Bu, deyimi gibi seçenek bildirimlerini izlemelidir `Option Strict` ve veya deyimleri gibi programlama öğesi bildirimlerinin önüne alınmalıdır `Module` `Class` .</span><span class="sxs-lookup"><span data-stu-id="aa371-133">These must follow option declarations, such as the `Option Strict` statement, and they must precede programming element declarations, such as `Module` or `Class` statements.</span></span>

## <a name="example"></a><span data-ttu-id="aa371-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="aa371-134">Example</span></span>

<span data-ttu-id="aa371-135">Aşağıdaki örnek bir varsayılan XML ad alanını ve önekiyle tanımlanan bir XML ad alanını içeri aktarır `ns` .</span><span class="sxs-lookup"><span data-stu-id="aa371-135">The following example imports a default XML namespace and an XML namespace identified with the prefix `ns`.</span></span> <span data-ttu-id="aa371-136">Ardından, her iki ad alanını kullanan XML değişmez değerleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="aa371-136">It then creates XML literals that use both namespaces.</span></span>

[!code-vb[VbXMLSamples#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/Module1.vb#45)]

<span data-ttu-id="aa371-137">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="aa371-137">This code displays the following text:</span></span>

```xml
<ns:outer xmlns="http://DefaultNamespace"
          xmlns:ns="http://NewNamespace">
  <ns:innerElement></ns:innerElement>
  <siblingElement></siblingElement>
  <innerElement />
</ns:outer>
```

## <a name="example"></a><span data-ttu-id="aa371-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="aa371-138">Example</span></span>

<span data-ttu-id="aa371-139">Aşağıdaki örnek XML ad alanı önekini içeri aktarır `ns` .</span><span class="sxs-lookup"><span data-stu-id="aa371-139">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="aa371-140">Daha sonra ad alanı önekini kullanan bir XML sabit değeri oluşturur ve öğenin son formunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="aa371-140">It then creates an XML literal that uses the namespace prefix and displays the element's final form.</span></span>

[!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]

<span data-ttu-id="aa371-141">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="aa371-141">This code displays the following text:</span></span>

```xml
<ns:outer xmlns:ns="http://SomeNamespace">
  <ns:middle xmlns:ns="http://NewNamespace">
    <ns:inner1 />
    <inner2 xmlns="http://SomeNamespace" />
  </ns:middle>
</ns:outer>
```

<span data-ttu-id="aa371-142">Derleyicinin XML ad alanı önekini genel bir önekten yerel ön ek tanımına dönüştürdüğüne dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="aa371-142">Notice that the compiler converted the XML namespace prefix from a global prefix to a local prefix definition.</span></span>

## <a name="example"></a><span data-ttu-id="aa371-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="aa371-143">Example</span></span>

<span data-ttu-id="aa371-144">Aşağıdaki örnek XML ad alanı önekini içeri aktarır `ns` .</span><span class="sxs-lookup"><span data-stu-id="aa371-144">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="aa371-145">Daha sonra bir XML sabit değeri oluşturmak için ad alanının önekini kullanır ve ilk alt düğüme tam adı ile erişin `ns:name` .</span><span class="sxs-lookup"><span data-stu-id="aa371-145">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>

[!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]

<span data-ttu-id="aa371-146">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="aa371-146">This code displays the following text:</span></span>

`Patrick Hines`

## <a name="see-also"></a><span data-ttu-id="aa371-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa371-147">See also</span></span>

- [<span data-ttu-id="aa371-148">XML Öğesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="aa371-148">XML Element Literal</span></span>](../xml-literals/xml-element-literal.md)
- [<span data-ttu-id="aa371-149">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="aa371-149">XML Axis Properties</span></span>](../xml-axis/index.md)
- [<span data-ttu-id="aa371-150">Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları</span><span class="sxs-lookup"><span data-stu-id="aa371-150">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [<span data-ttu-id="aa371-151">GetXmlNamespace İşleci</span><span class="sxs-lookup"><span data-stu-id="aa371-151">GetXmlNamespace Operator</span></span>](../operators/getxmlnamespace-operator.md)
