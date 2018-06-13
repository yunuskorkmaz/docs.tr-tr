---
title: Imports Deyimi (XML Ad Alanı)
ms.date: 07/20/2015
f1_keywords:
- vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
ms.openlocfilehash: ba7475416d8a4e2eb3c892d457c03eeb695045eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604568"
---
# <a name="imports-statement-xml-namespace"></a><span data-ttu-id="58a61-102">Imports Deyimi (XML Ad Alanı)</span><span class="sxs-lookup"><span data-stu-id="58a61-102">Imports Statement (XML Namespace)</span></span>
<span data-ttu-id="58a61-103">XML değişmez değerleri ve XML eksen özellikleri kullanılmak üzere XML ad alanı öneklerini alır.</span><span class="sxs-lookup"><span data-stu-id="58a61-103">Imports XML namespace prefixes for use in XML literals and XML axis properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58a61-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="58a61-104">Syntax</span></span>  
  
```  
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">  
```  
  
## <a name="parts"></a><span data-ttu-id="58a61-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="58a61-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="58a61-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="58a61-106">Optional.</span></span> <span data-ttu-id="58a61-107">Tarafından hangi XML öğeleri ve özniteliklerinin başvurabilir dize `xmlNamespaceName`.</span><span class="sxs-lookup"><span data-stu-id="58a61-107">The string by which XML elements and attributes can refer to `xmlNamespaceName`.</span></span> <span data-ttu-id="58a61-108">Öyle değilse `xmlNamespacePrefix` olan sağlanan, içeri aktarılan XML ad alanı varsayılan XML ad alanıdır.</span><span class="sxs-lookup"><span data-stu-id="58a61-108">If no `xmlNamespacePrefix` is supplied, the imported XML namespace is the default XML namespace.</span></span> <span data-ttu-id="58a61-109">Geçerli bir XML tanımlayıcısı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="58a61-109">Must be a valid XML identifier.</span></span> <span data-ttu-id="58a61-110">Daha fazla bilgi için bkz: [adları bildirilmiş XML öğeleri ve öznitelikleri](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="58a61-110">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>  
  
 `xmlNamespaceName`  
 <span data-ttu-id="58a61-111">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="58a61-111">Required.</span></span> <span data-ttu-id="58a61-112">İçeri aktarılan XML ad alanı tanımlayan dize.</span><span class="sxs-lookup"><span data-stu-id="58a61-112">The string identifying the XML namespace being imported.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58a61-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="58a61-113">Remarks</span></span>  
 <span data-ttu-id="58a61-114">Kullanabileceğiniz `Imports` XML değişmez değerleri ve XML eksen özellikleri ile ya da geçirilen parametre olarak kullanabileceğiniz genel XML ad alanları tanımlamak için deyimi `GetXmlNamespace` işleci.</span><span class="sxs-lookup"><span data-stu-id="58a61-114">You can use the `Imports` statement to define global XML namespaces that you can use with XML literals and XML axis properties, or as parameters passed to the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="58a61-115">(Kullanma hakkında bilgi için `Imports` deyimi tür adları, kodunuzda kullanıldığı kullanılabilmesi için bir diğer ad almak için bkz: [Imports deyimi (.NET Namespace ve türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) Kullanarak bir XML ad alanı bildirme sözdizimi `Imports` deyimi, XML'de kullanılan sözdizimi aynıdır.</span><span class="sxs-lookup"><span data-stu-id="58a61-115">(For information about using the `Imports` statement to import an alias that can be used where type names are used in your code, see [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) The syntax for declaring an XML namespace by using the `Imports` statement is identical to the syntax used in XML.</span></span> <span data-ttu-id="58a61-116">Bu nedenle, bir XML dosyasından bir ad alanı bildiriminin kopyalayın ve bunu kullanın bir `Imports` deyimi.</span><span class="sxs-lookup"><span data-stu-id="58a61-116">Therefore, you can copy a namespace declaration from an XML file and use it in an `Imports` statement.</span></span>  
  
 <span data-ttu-id="58a61-117">XML ad alanı önekleri, sürekli olarak, aynı ad alanından XML öğelerini oluşturmak istediğinizde faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="58a61-117">XML namespace prefixes are useful when you want to repeatedly create XML elements that are from the same namespace.</span></span> <span data-ttu-id="58a61-118">XML ad alanı öneki ile bildirilen `Imports` açıklamadır dosyasındaki tüm kod için kullanılabilir olduğunu herkese açık genel.</span><span class="sxs-lookup"><span data-stu-id="58a61-118">The XML namespace prefix declared with the `Imports` statement is global in the sense that it is available to all code in the file.</span></span> <span data-ttu-id="58a61-119">XML öğesi değişmez değerleri ve XML eksen özellikleri eriştiğinizde oluştururken kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58a61-119">You can use it when you create XML element literals and when you access XML axis properties.</span></span> <span data-ttu-id="58a61-120">Daha fazla bilgi için bkz: [XML öğesi değişmez değer](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) ve [XML eksen özellikleri](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md).</span><span class="sxs-lookup"><span data-stu-id="58a61-120">For more information, see [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) and [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md).</span></span>  
  
 <span data-ttu-id="58a61-121">Genel bir XML ad alanı bir ad alanı öneki olmadan tanımlarsanız, (örneğin, `Imports <xmlns="http://SomeNameSpace>"`), bu ad alanı varsayılan XML ad alanı olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="58a61-121">If you define a global XML namespace without a namespace prefix (for example, `Imports <xmlns="http://SomeNameSpace>"`), that namespace is considered the default XML namespace.</span></span> <span data-ttu-id="58a61-122">Varsayılan XML ad alanı, herhangi bir XML öğesi değişmez değerleri veya açıkça bir ad alanı belirtmeyin XML özniteliği axis özellikleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="58a61-122">The default XML namespace is used for any XML element literals or XML attribute axis properties that do not explicitly specify a namespace.</span></span> <span data-ttu-id="58a61-123">Belirtilen ad boş ad alanı ise varsayılan ad alanı da kullanılır (yani, `xmlns=""`).</span><span class="sxs-lookup"><span data-stu-id="58a61-123">The default namespace is also used if the specified namespace is the empty namespace (that is, `xmlns=""`).</span></span> <span data-ttu-id="58a61-124">Varsayılan XML ad alanı XML öznitelikleri XML değişmez değerlerinde veya bir ad alanına sahip değil XML özniteliği axis özellikleri geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="58a61-124">The default XML namespace does not apply to XML attributes in XML literals or to XML attribute axis properties that do not have a namespace.</span></span>  
  
 <span data-ttu-id="58a61-125">Olarak adlandırılan bir XML değişmez değer, tanımlanan XML ad alanları *yerel XML ad alanları*, tarafından tanımlanan XML ad alanları önceliklidir `Imports` genel olarak deyimi.</span><span class="sxs-lookup"><span data-stu-id="58a61-125">XML namespaces that are defined in an XML literal, which are called *local XML namespaces*, take precedence over XML namespaces that are defined by the `Imports` statement as global.</span></span> <span data-ttu-id="58a61-126">Tarafından tanımlanan XML ad alanları `Imports` deyimi önceliklidir XML ad alanları için Visual Basic projesinde alındı.</span><span class="sxs-lookup"><span data-stu-id="58a61-126">XML namespaces that are defined by the `Imports` statement take precedence over XML namespaces imported for a Visual Basic project.</span></span> <span data-ttu-id="58a61-127">XML değişmez değeri bir XML ad alanı tanımlıyorsa, yerel ad alanına katıştırılmış ifadeler için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="58a61-127">If an XML literal defines an XML namespace, that local namespace does not apply to embedded expressions.</span></span>  
  
 <span data-ttu-id="58a61-128">Genel XML ad alanları, .NET Framework ad alanları olarak aynı kapsamı ve tanım kuralları izleyin.</span><span class="sxs-lookup"><span data-stu-id="58a61-128">Global XML namespaces follow the same scoping and definition rules as .NET Framework namespaces.</span></span> <span data-ttu-id="58a61-129">Sonuç olarak, dahil edebileceğiniz bir `Imports` genel bir XML ad alanı tanımlamak için deyimi herhangi bir .NET Framework ad alanı içe aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58a61-129">As a result, you can include an `Imports` statement to define a global XML namespace anywhere you can import a .NET Framework namespace.</span></span> <span data-ttu-id="58a61-130">Bu proje düzeyi içeri aktarılan ad alanlarını ve kod dosyaları içerir.</span><span class="sxs-lookup"><span data-stu-id="58a61-130">This includes both code files and project-level imported namespaces.</span></span> <span data-ttu-id="58a61-131">Proje düzeyi içeri aktarılan ad alanları hakkında daha fazla bilgi için bkz: [başvurular sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="58a61-131">For information about project-level imported namespaces, see [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="58a61-132">Her kaynak dosyasının herhangi bir sayıda içerebilir `Imports` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="58a61-132">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="58a61-133">Bu seçenek bildirimleri gibi izlemelisiniz `Option Strict` deyimi ve gelmelidir programlama öğesi bildirimleri gibi `Module` veya `Class` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="58a61-133">These must follow option declarations, such as the `Option Strict` statement, and they must precede programming element declarations, such as `Module` or `Class` statements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58a61-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="58a61-134">Example</span></span>  
 <span data-ttu-id="58a61-135">Aşağıdaki örnekte bir varsayılan XML ad alanı ve bir XML ad alanı öneki ile tanımlanan alır `ns`.</span><span class="sxs-lookup"><span data-stu-id="58a61-135">The following example imports a default XML namespace and an XML namespace identified with the prefix `ns`.</span></span> <span data-ttu-id="58a61-136">Ardından, her iki ad alanları kullanmak XML değişmez değerleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="58a61-136">It then creates XML literals that use both namespaces.</span></span>  
  
 [!code-vb[VbXMLSamples#45](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_1.vb)]  
  
 <span data-ttu-id="58a61-137">Bu kod, aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="58a61-137">This code displays the following text:</span></span>  
  
```xml  
<ns:outer xmlns="http://DefaultNamespace"   
          xmlns:ns="http://NewNamespace">  
  <ns:innerElement></ns:innerElement>  
  <siblingElement></siblingElement>  
  <innerElement />  
</ns:outer>  
```  
  
## <a name="example"></a><span data-ttu-id="58a61-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="58a61-138">Example</span></span>  
 <span data-ttu-id="58a61-139">Aşağıdaki örnek XML ad alanı önekini alır `ns`.</span><span class="sxs-lookup"><span data-stu-id="58a61-139">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="58a61-140">Daha sonra ad alanı öneki kullanıyor ve öğenin son formunu görüntüleyen bir XML değişmez değer oluşturur.</span><span class="sxs-lookup"><span data-stu-id="58a61-140">It then creates an XML literal that uses the namespace prefix and displays the element's final form.</span></span>  
  
 [!code-vb[VbXMLSamples#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_2.vb)]  
  
 <span data-ttu-id="58a61-141">Bu kod, aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="58a61-141">This code displays the following text:</span></span>  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 <span data-ttu-id="58a61-142">Derleyici global önekten XML ad alanı öneki yerel önek tanımına dönüştürülen dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="58a61-142">Notice that the compiler converted the XML namespace prefix from a global prefix to a local prefix definition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58a61-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="58a61-143">Example</span></span>  
 <span data-ttu-id="58a61-144">Aşağıdaki örnek XML ad alanı önekini alır `ns`.</span><span class="sxs-lookup"><span data-stu-id="58a61-144">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="58a61-145">XML değişmez değer oluşturmak ve ilk alt düğüm tam adı ile erişmek için ad alanı öneki sonra kullanan `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="58a61-145">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#19](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_3.vb)]  
  
 <span data-ttu-id="58a61-146">Bu kod, aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="58a61-146">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="58a61-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="58a61-147">See Also</span></span>  
 [<span data-ttu-id="58a61-148">XML Öğesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="58a61-148">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="58a61-149">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="58a61-149">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [<span data-ttu-id="58a61-150">Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları</span><span class="sxs-lookup"><span data-stu-id="58a61-150">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)  
 [<span data-ttu-id="58a61-151">GetXmlNamespace İşleci</span><span class="sxs-lookup"><span data-stu-id="58a61-151">GetXmlNamespace Operator</span></span>](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)
