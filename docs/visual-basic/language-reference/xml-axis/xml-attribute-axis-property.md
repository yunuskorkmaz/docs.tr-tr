---
title: XML Özniteliği Axis Özelliği
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyAttributeAxis
helpviewer_keywords:
- attribute axis property [Visual Basic]
- Visual Basic code, accessing XML
- XML attribute axis property [Visual Basic]
- XML axis [Visual Basic], attribute
- XML [Visual Basic], accessing
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
ms.openlocfilehash: 109c4b45a5e3ed4e3e4db49687df5cb127a5e0c6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352666"
---
# <a name="xml-attribute-axis-property-visual-basic"></a><span data-ttu-id="89ae4-102">XML Özniteliği Axis Özelliği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89ae4-102">XML Attribute Axis Property (Visual Basic)</span></span>
<span data-ttu-id="89ae4-103">Bir <xref:System.Xml.Linq.XElement> nesnesi veya bir <xref:System.Xml.Linq.XElement> nesneleri koleksiyonundaki ilk öğe için bir özniteliğin değerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="89ae4-103">Provides access to the value of an attribute for an <xref:System.Xml.Linq.XElement> object or to the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89ae4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="89ae4-104">Syntax</span></span>  
  
```vb  
object.@attribute  
' -or-  
object.@<attribute>  
```  
  
## <a name="parts"></a><span data-ttu-id="89ae4-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="89ae4-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="89ae4-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="89ae4-106">Required.</span></span> <span data-ttu-id="89ae4-107"><xref:System.Xml.Linq.XElement> nesnesi veya <xref:System.Xml.Linq.XElement> nesneleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="89ae4-107">An <xref:System.Xml.Linq.XElement> object or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="89ae4-108">.@</span><span class="sxs-lookup"><span data-stu-id="89ae4-108">.@</span></span>  
 <span data-ttu-id="89ae4-109">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="89ae4-109">Required.</span></span> <span data-ttu-id="89ae4-110">Öznitelik ekseni özelliğinin başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="89ae4-110">Denotes the start of an attribute axis property.</span></span>  
  
 <  
 <span data-ttu-id="89ae4-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="89ae4-111">Optional.</span></span> <span data-ttu-id="89ae4-112">`attribute` Visual Basic geçerli bir tanımlayıcı olmadığında özniteliğin adının başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="89ae4-112">Denotes the beginning of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
 `attribute`  
 <span data-ttu-id="89ae4-113">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="89ae4-113">Required.</span></span> <span data-ttu-id="89ae4-114">[`prefix`:]`name`biçiminde erişebileceğiniz özniteliğin adı.</span><span class="sxs-lookup"><span data-stu-id="89ae4-114">Name of the attribute to access, of the form [`prefix`:]`name`.</span></span>  
  
|<span data-ttu-id="89ae4-115">Bölümüyle</span><span class="sxs-lookup"><span data-stu-id="89ae4-115">Part</span></span>|<span data-ttu-id="89ae4-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89ae4-116">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="89ae4-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="89ae4-117">Optional.</span></span> <span data-ttu-id="89ae4-118">Öznitelik için XML ad alanı ön eki.</span><span class="sxs-lookup"><span data-stu-id="89ae4-118">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="89ae4-119">Bir `Imports` ifadesiyle tanımlanmış bir genel XML ad alanı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="89ae4-119">Must be a global XML namespace defined with an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="89ae4-120">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="89ae4-120">Required.</span></span> <span data-ttu-id="89ae4-121">Yerel öznitelik adı.</span><span class="sxs-lookup"><span data-stu-id="89ae4-121">Local attribute name.</span></span> <span data-ttu-id="89ae4-122">[BELIRTILEN XML öğelerinin ve özniteliklerin adlarına](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="89ae4-122">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="89ae4-123">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="89ae4-123">Optional.</span></span> <span data-ttu-id="89ae4-124">`attribute` Visual Basic geçerli bir tanımlayıcı olmadığında özniteliğin adının sonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="89ae4-124">Denotes the end of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89ae4-125">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="89ae4-125">Return Value</span></span>  
 <span data-ttu-id="89ae4-126">`attribute`değerini içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="89ae4-126">A string that contains the value of `attribute`.</span></span> <span data-ttu-id="89ae4-127">Öznitelik adı yoksa `Nothing` döndürülür.</span><span class="sxs-lookup"><span data-stu-id="89ae4-127">If the attribute name does not exist, `Nothing` is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89ae4-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="89ae4-128">Remarks</span></span>  
 <span data-ttu-id="89ae4-129">Bir özniteliğin değerine bir <xref:System.Xml.Linq.XElement> nesnesinden veya bir <xref:System.Xml.Linq.XElement> nesneleri koleksiyonundaki ilk öğeden ada göre erişmek için bir XML öznitelik ekseni özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="89ae4-129">You can use an XML attribute axis property to access the value of an attribute by name from an <xref:System.Xml.Linq.XElement> object or from the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="89ae4-130">Ada göre bir öznitelik değeri alabilir veya bir öğeye yeni bir öznitelik ekleyerek @ tanımlayıcısının önüne yeni bir ad belirterek ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="89ae4-130">You can retrieve an attribute value by name, or add a new attribute to an element by specifying a new name preceded by the @ identifier.</span></span>  
  
 <span data-ttu-id="89ae4-131">@ Tanımlayıcısını kullanarak bir XML özniteliğine başvurduğunuzda, öznitelik değeri bir dize olarak döndürülür ve <xref:System.Xml.Linq.XAttribute.Value%2A> özelliğini açık bir şekilde belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="89ae4-131">When you refer to an XML attribute using the @ identifier, the attribute value is returned as a string and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="89ae4-132">XML öznitelikleri için adlandırma kuralları Visual Basic Tanımlayıcılarla ilgili adlandırma kurallarından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="89ae4-132">The naming rules for XML attributes differ from the naming rules for Visual Basic identifiers.</span></span> <span data-ttu-id="89ae4-133">Geçerli bir Visual Basic tanımlayıcı olmayan bir ada sahip bir XML özniteliğine erişmek için, adı açılı ayraçlar (\< ve >) içine alın.</span><span class="sxs-lookup"><span data-stu-id="89ae4-133">To access an XML attribute that has a name that is not a valid Visual Basic identifier, enclose the name in angle brackets (\< and >).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="89ae4-134">XML ad alanları</span><span class="sxs-lookup"><span data-stu-id="89ae4-134">XML Namespaces</span></span>  
 <span data-ttu-id="89ae4-135">Öznitelik ekseni özelliğindeki ad, `Imports` ifadesini kullanarak genel olarak belirtilen yalnızca XML ad alanı öneklerini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="89ae4-135">The name in an attribute axis property can use only XML namespace prefixes declared globally by using the `Imports` statement.</span></span> <span data-ttu-id="89ae4-136">XML öğesi değişmez değerleri içinde yerel olarak belirtilen XML ad alanı öneklerini kullanamaz.</span><span class="sxs-lookup"><span data-stu-id="89ae4-136">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="89ae4-137">Daha fazla bilgi için bkz. [Imports bildirisi (XML ad alanı)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="89ae4-137">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="89ae4-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="89ae4-138">Example</span></span>  
 <span data-ttu-id="89ae4-139">Aşağıdaki örnek, `phone`adlı bir XML öğeleri koleksiyonundan `type` adlı XML özniteliklerinin değerlerinin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="89ae4-139">The following example shows how to get the values of the XML attributes named `type` from a collection of XML elements that are named `phone`.</span></span>  
  
 [!code-vb[VbXMLSamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#12)]  
  
 <span data-ttu-id="89ae4-140">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="89ae4-140">This code displays the following text:</span></span>  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a><span data-ttu-id="89ae4-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="89ae4-141">Example</span></span>  
 <span data-ttu-id="89ae4-142">Aşağıdaki örnek, bir XML öğesi için, XML 'nin bir parçası olarak ve bir <xref:System.Xml.Linq.XElement> nesnesinin örneğine bir öznitelik ekleyerek dinamik olarak nasıl öznitelik oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="89ae4-142">The following example shows how to create attributes for an XML element both declaratively, as part of the XML, and dynamically by adding an attribute to an instance of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="89ae4-143">`type` özniteliği bildirimli olarak oluşturulur ve `owner` özniteliği dinamik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="89ae4-143">The `type` attribute is created declaratively and the `owner` attribute is created dynamically.</span></span>  
  
 [!code-vb[VbXMLSamples#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#44)]  
  
 <span data-ttu-id="89ae4-144">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="89ae4-144">This code displays the following text:</span></span>  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a><span data-ttu-id="89ae4-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="89ae4-145">Example</span></span>  
 <span data-ttu-id="89ae4-146">Aşağıdaki örnek, Visual Basic ' de geçerli bir tanımlayıcı olmayan `number-type`adlı XML özniteliğinin değerini almak için açılı ayraç sözdizimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="89ae4-146">The following example uses the angle bracket syntax to get the value of the XML attribute named `number-type`, which is not a valid identifier in Visual Basic.</span></span>  
  
 [!code-vb[VbXMLSamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#13)]  
  
 <span data-ttu-id="89ae4-147">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="89ae4-147">This code displays the following text:</span></span>  
  
 `Phone type: work`  
  
## <a name="example"></a><span data-ttu-id="89ae4-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="89ae4-148">Example</span></span>  
 <span data-ttu-id="89ae4-149">Aşağıdaki örnek, `ns` bir XML ad alanı öneki olarak bildirir.</span><span class="sxs-lookup"><span data-stu-id="89ae4-149">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="89ae4-150">Daha sonra bir XML sabit değeri oluşturmak için ad alanının önekini kullanır ve "`ns:name`" tam adına sahip ilk alt düğüme erişir.</span><span class="sxs-lookup"><span data-stu-id="89ae4-150">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name "`ns:name`".</span></span>  
  
 [!code-vb[VbXMLSamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples6.vb#14)]  
  
 <span data-ttu-id="89ae4-151">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="89ae4-151">This code displays the following text:</span></span>  
  
 `Phone type: home`  
  
## <a name="see-also"></a><span data-ttu-id="89ae4-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89ae4-152">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="89ae4-153">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="89ae4-153">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="89ae4-154">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="89ae4-154">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="89ae4-155">Visual Basic XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="89ae4-155">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="89ae4-156">Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları</span><span class="sxs-lookup"><span data-stu-id="89ae4-156">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
