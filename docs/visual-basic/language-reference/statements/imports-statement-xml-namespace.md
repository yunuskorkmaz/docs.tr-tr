---
title: Imports deyimi - XML Namespace (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
ms.openlocfilehash: 8cce1cc918b150fdf30449f127b1e2f0a73e6f6c
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973281"
---
# <a name="imports-statement-xml-namespace"></a><span data-ttu-id="3baf2-102">Imports Deyimi (XML Ad Alanı)</span><span class="sxs-lookup"><span data-stu-id="3baf2-102">Imports Statement (XML Namespace)</span></span>
<span data-ttu-id="3baf2-103">XML değişmez değerleri ve XML eksen özellikleri kullanılmak üzere XML ad alanı öneklerini alır.</span><span class="sxs-lookup"><span data-stu-id="3baf2-103">Imports XML namespace prefixes for use in XML literals and XML axis properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3baf2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3baf2-104">Syntax</span></span>  
  
```  
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">  
```  
  
## <a name="parts"></a><span data-ttu-id="3baf2-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="3baf2-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="3baf2-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3baf2-106">Optional.</span></span> <span data-ttu-id="3baf2-107">Tarafından hangi XML öğeleri ve özniteliklerinin başvurabilir dize `xmlNamespaceName`.</span><span class="sxs-lookup"><span data-stu-id="3baf2-107">The string by which XML elements and attributes can refer to `xmlNamespaceName`.</span></span> <span data-ttu-id="3baf2-108">Hayır ise `xmlNamespacePrefix` olan sağlanan, içeri aktarılan XML ad alanı varsayılan XML ad alanı.</span><span class="sxs-lookup"><span data-stu-id="3baf2-108">If no `xmlNamespacePrefix` is supplied, the imported XML namespace is the default XML namespace.</span></span> <span data-ttu-id="3baf2-109">Geçerli bir XML tanımlayıcısı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3baf2-109">Must be a valid XML identifier.</span></span> <span data-ttu-id="3baf2-110">Daha fazla bilgi için [adları, bildirilmiş XML öğeleri ve özniteliklerinin](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="3baf2-110">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>  
  
 `xmlNamespaceName`  
 <span data-ttu-id="3baf2-111">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="3baf2-111">Required.</span></span> <span data-ttu-id="3baf2-112">İçeri aktarılan XML ad alanı tanımlayan dize.</span><span class="sxs-lookup"><span data-stu-id="3baf2-112">The string identifying the XML namespace being imported.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3baf2-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3baf2-113">Remarks</span></span>  
 <span data-ttu-id="3baf2-114">Kullanabileceğiniz `Imports` XML sabit değerleri ve XML eksen özellikleri ile ya da geçirilen parametre olarak kullanabileceğiniz genel XML ad alanları tanımlamak için deyimi `GetXmlNamespace` işleci.</span><span class="sxs-lookup"><span data-stu-id="3baf2-114">You can use the `Imports` statement to define global XML namespaces that you can use with XML literals and XML axis properties, or as parameters passed to the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="3baf2-115">(Kullanma hakkında bilgi için `Imports` tür adları, kodunuzda kullanıldığı kullanılabilecek diğer ad içeri aktarmak için bildirimini [Imports deyimi (.NET Namespace ve türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) Kullanarak bir XML ad alanı bildirmek için söz dizimi `Imports` ifade ile kullanılan XML sözdizimi aynıdır.</span><span class="sxs-lookup"><span data-stu-id="3baf2-115">(For information about using the `Imports` statement to import an alias that can be used where type names are used in your code, see [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) The syntax for declaring an XML namespace by using the `Imports` statement is identical to the syntax used in XML.</span></span> <span data-ttu-id="3baf2-116">Bu nedenle, bir ad alanı bildirimi bir XML dosyasından kopyalayın ve bunu kullanmak bir `Imports` deyimi.</span><span class="sxs-lookup"><span data-stu-id="3baf2-116">Therefore, you can copy a namespace declaration from an XML file and use it in an `Imports` statement.</span></span>  
  
 <span data-ttu-id="3baf2-117">XML ad alanı öneklerini tekrar tekrar aynı ad alanındandır XML öğelerini oluşturmak istediğinizde kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="3baf2-117">XML namespace prefixes are useful when you want to repeatedly create XML elements that are from the same namespace.</span></span> <span data-ttu-id="3baf2-118">XML ad alanı öneki ile bildirilen `Imports` deyimi, genel anlamda dosyadaki tüm kod için kullanılabilir olduğunu.</span><span class="sxs-lookup"><span data-stu-id="3baf2-118">The XML namespace prefix declared with the `Imports` statement is global in the sense that it is available to all code in the file.</span></span> <span data-ttu-id="3baf2-119">XML öğesi değişmez değerleri ve XML eksen özellikleri eriştiğinizde oluştururken kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3baf2-119">You can use it when you create XML element literals and when you access XML axis properties.</span></span> <span data-ttu-id="3baf2-120">Daha fazla bilgi için [XML öğesi değişmez değeri](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) ve [XML eksen özellikleri](../../../visual-basic/language-reference/xml-axis/index.md).</span><span class="sxs-lookup"><span data-stu-id="3baf2-120">For more information, see [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) and [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/index.md).</span></span>  
  
 <span data-ttu-id="3baf2-121">Bir ad alanı öneki olmadan genel bir XML ad alanı tanımlarsanız, (örneğin, `Imports <xmlns="http://SomeNameSpace>"`), bu ad alanı varsayılan XML ad alanı olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="3baf2-121">If you define a global XML namespace without a namespace prefix (for example, `Imports <xmlns="http://SomeNameSpace>"`), that namespace is considered the default XML namespace.</span></span> <span data-ttu-id="3baf2-122">Varsayılan XML ad alanı, herhangi bir XML öğesi değişmez değerler veya bir ad alanını açıkça belirtmeyen XML öznitelik eksen özellikleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3baf2-122">The default XML namespace is used for any XML element literals or XML attribute axis properties that do not explicitly specify a namespace.</span></span> <span data-ttu-id="3baf2-123">Belirtilen ad alanı boş ad alanı varsayılan ad alanı ayrıca kullanılır (yani `xmlns=""`).</span><span class="sxs-lookup"><span data-stu-id="3baf2-123">The default namespace is also used if the specified namespace is the empty namespace (that is, `xmlns=""`).</span></span> <span data-ttu-id="3baf2-124">Varsayılan XML ad alanı XML değişmez değerlerinde XML öznitelikleri veya bir ad alanı olmayan XML öznitelik eksen özellikleri için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="3baf2-124">The default XML namespace does not apply to XML attributes in XML literals or to XML attribute axis properties that do not have a namespace.</span></span>  
  
 <span data-ttu-id="3baf2-125">Olarak adlandırılan bir XML sabit değeri, tanımlanan XML ad alanları *yerel XML ad alanları*, tarafından tanımlanan XML ad alanları öncelikli `Imports` genel olarak deyimi.</span><span class="sxs-lookup"><span data-stu-id="3baf2-125">XML namespaces that are defined in an XML literal, which are called *local XML namespaces*, take precedence over XML namespaces that are defined by the `Imports` statement as global.</span></span> <span data-ttu-id="3baf2-126">Tarafından tanımlanan XML ad alanları `Imports` deyimi önceliklidir Visual Basic projesi için içeri aktarılan XML ad alanları.</span><span class="sxs-lookup"><span data-stu-id="3baf2-126">XML namespaces that are defined by the `Imports` statement take precedence over XML namespaces imported for a Visual Basic project.</span></span> <span data-ttu-id="3baf2-127">Bir XML değişmez değeri bir XML ad alanı tanımlıyorsa, yerel ad alanı için katıştırılmış ifadeleri geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="3baf2-127">If an XML literal defines an XML namespace, that local namespace does not apply to embedded expressions.</span></span>  
  
 <span data-ttu-id="3baf2-128">Genel XML ad alanları, .NET Framework ad alanları aynı kapsamı ve tanımı kuralları uygulayın.</span><span class="sxs-lookup"><span data-stu-id="3baf2-128">Global XML namespaces follow the same scoping and definition rules as .NET Framework namespaces.</span></span> <span data-ttu-id="3baf2-129">Sonuç olarak, dahil edebileceğiniz bir `Imports` genel bir XML ad alanı tanımlamak için deyimi herhangi bir .NET Framework ad alanı içeri aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3baf2-129">As a result, you can include an `Imports` statement to define a global XML namespace anywhere you can import a .NET Framework namespace.</span></span> <span data-ttu-id="3baf2-130">Bu proje düzeyi içeri aktarılan ad alanlarını ve kod dosyaları içerir.</span><span class="sxs-lookup"><span data-stu-id="3baf2-130">This includes both code files and project-level imported namespaces.</span></span> <span data-ttu-id="3baf2-131">Proje düzeyi içeri aktarılan ad alanları hakkında daha fazla bilgi için bkz: [başvurular sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="3baf2-131">For information about project-level imported namespaces, see [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="3baf2-132">Her kaynak dosyası herhangi bir sayıda içerebilir `Imports` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="3baf2-132">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="3baf2-133">Bu seçenek bildirimleri gibi izlemelisiniz `Option Strict` deyimi ve gelmelidir programlama öğesi bildirimleri gibi `Module` veya `Class` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="3baf2-133">These must follow option declarations, such as the `Option Strict` statement, and they must precede programming element declarations, such as `Module` or `Class` statements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3baf2-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="3baf2-134">Example</span></span>  
 <span data-ttu-id="3baf2-135">Aşağıdaki örnek bir varsayılan XML ad alanı ve bir XML ad alanı öneki ile tanımlanan aktarır `ns`.</span><span class="sxs-lookup"><span data-stu-id="3baf2-135">The following example imports a default XML namespace and an XML namespace identified with the prefix `ns`.</span></span> <span data-ttu-id="3baf2-136">Ardından, her iki ad alanlarını XML değişmez değerlerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3baf2-136">It then creates XML literals that use both namespaces.</span></span>  
  
 [!code-vb[VbXMLSamples#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/Module1.vb#45)]  
  
 <span data-ttu-id="3baf2-137">Bu kod, aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="3baf2-137">This code displays the following text:</span></span>  
  
```xml  
<ns:outer xmlns="http://DefaultNamespace"   
          xmlns:ns="http://NewNamespace">  
  <ns:innerElement></ns:innerElement>  
  <siblingElement></siblingElement>  
  <innerElement />  
</ns:outer>  
```  
  
## <a name="example"></a><span data-ttu-id="3baf2-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="3baf2-138">Example</span></span>  
 <span data-ttu-id="3baf2-139">Aşağıdaki örnek XML ad alanı öneki alır `ns`.</span><span class="sxs-lookup"><span data-stu-id="3baf2-139">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="3baf2-140">Ardından, ad alanı öneki kullanıyor ve öğenin son formunu görüntüleyen bir XML değişmez değer oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3baf2-140">It then creates an XML literal that uses the namespace prefix and displays the element's final form.</span></span>  
  
 [!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]  
  
 <span data-ttu-id="3baf2-141">Bu kod, aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="3baf2-141">This code displays the following text:</span></span>  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 <span data-ttu-id="3baf2-142">Derleyici global bir önekten XML ad alanı öneki yerel önek tanımına dönüştürülen dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="3baf2-142">Notice that the compiler converted the XML namespace prefix from a global prefix to a local prefix definition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3baf2-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="3baf2-143">Example</span></span>  
 <span data-ttu-id="3baf2-144">Aşağıdaki örnek XML ad alanı öneki alır `ns`.</span><span class="sxs-lookup"><span data-stu-id="3baf2-144">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="3baf2-145">XML değişmez değer oluşturun ve ilk alt düğüm tam adı ile erişmek için bir ad alanı öneki kullanır `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="3baf2-145">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]  
  
 <span data-ttu-id="3baf2-146">Bu kod, aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="3baf2-146">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="3baf2-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3baf2-147">See also</span></span>
- [<span data-ttu-id="3baf2-148">XML Öğesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="3baf2-148">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="3baf2-149">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="3baf2-149">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="3baf2-150">Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları</span><span class="sxs-lookup"><span data-stu-id="3baf2-150">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [<span data-ttu-id="3baf2-151">GetXmlNamespace İşleci</span><span class="sxs-lookup"><span data-stu-id="3baf2-151">GetXmlNamespace Operator</span></span>](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)
