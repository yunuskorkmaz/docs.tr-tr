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
ms.openlocfilehash: 3f60190a949856cb2bbc2eba09d097c09089bea7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408438"
---
# <a name="xml-attribute-axis-property-visual-basic"></a><span data-ttu-id="86e89-102">XML Özniteliği Axis Özelliği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="86e89-102">XML Attribute Axis Property (Visual Basic)</span></span>
<span data-ttu-id="86e89-103">Bir nesne için bir özniteliğin değerine <xref:System.Xml.Linq.XElement> veya nesne koleksiyonundaki ilk öğeye erişim sağlar <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="86e89-103">Provides access to the value of an attribute for an <xref:System.Xml.Linq.XElement> object or to the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86e89-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86e89-104">Syntax</span></span>  
  
```vb  
object.@attribute  
' -or-  
object.@<attribute>  
```  
  
## <a name="parts"></a><span data-ttu-id="86e89-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="86e89-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="86e89-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="86e89-106">Required.</span></span> <span data-ttu-id="86e89-107"><xref:System.Xml.Linq.XElement>Nesne veya nesne koleksiyonu <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="86e89-107">An <xref:System.Xml.Linq.XElement> object or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="86e89-108">.@</span><span class="sxs-lookup"><span data-stu-id="86e89-108">.@</span></span>  
 <span data-ttu-id="86e89-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="86e89-109">Required.</span></span> <span data-ttu-id="86e89-110">Öznitelik ekseni özelliğinin başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="86e89-110">Denotes the start of an attribute axis property.</span></span>  
  
 <  
 <span data-ttu-id="86e89-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="86e89-111">Optional.</span></span> <span data-ttu-id="86e89-112">Visual Basic geçerli bir tanımlayıcı olmadığında özniteliğin adının başlangıcını gösterir `attribute` .</span><span class="sxs-lookup"><span data-stu-id="86e89-112">Denotes the beginning of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
 `attribute`  
 <span data-ttu-id="86e89-113">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="86e89-113">Required.</span></span> <span data-ttu-id="86e89-114">[:] Biçiminde erişebileceğiniz özniteliğin adı `prefix` `name` .</span><span class="sxs-lookup"><span data-stu-id="86e89-114">Name of the attribute to access, of the form [`prefix`:]`name`.</span></span>  
  
|<span data-ttu-id="86e89-115">Bölüm</span><span class="sxs-lookup"><span data-stu-id="86e89-115">Part</span></span>|<span data-ttu-id="86e89-116">Description</span><span class="sxs-lookup"><span data-stu-id="86e89-116">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="86e89-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="86e89-117">Optional.</span></span> <span data-ttu-id="86e89-118">Öznitelik için XML ad alanı ön eki.</span><span class="sxs-lookup"><span data-stu-id="86e89-118">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="86e89-119">Bir ifadesiyle tanımlanmış bir genel XML ad alanı olmalıdır `Imports` .</span><span class="sxs-lookup"><span data-stu-id="86e89-119">Must be a global XML namespace defined with an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="86e89-120">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="86e89-120">Required.</span></span> <span data-ttu-id="86e89-121">Yerel öznitelik adı.</span><span class="sxs-lookup"><span data-stu-id="86e89-121">Local attribute name.</span></span> <span data-ttu-id="86e89-122">[BELIRTILEN XML öğelerinin ve özniteliklerin adlarına](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="86e89-122">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="86e89-123">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="86e89-123">Optional.</span></span> <span data-ttu-id="86e89-124">Visual Basic geçerli bir tanımlayıcı olmadığında özniteliğin adının sonunu belirtir `attribute` .</span><span class="sxs-lookup"><span data-stu-id="86e89-124">Denotes the end of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86e89-125">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="86e89-125">Return Value</span></span>  
 <span data-ttu-id="86e89-126">Değerini içeren bir dize `attribute` .</span><span class="sxs-lookup"><span data-stu-id="86e89-126">A string that contains the value of `attribute`.</span></span> <span data-ttu-id="86e89-127">Öznitelik adı yoksa, `Nothing` döndürülür.</span><span class="sxs-lookup"><span data-stu-id="86e89-127">If the attribute name does not exist, `Nothing` is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86e89-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86e89-128">Remarks</span></span>  
 <span data-ttu-id="86e89-129">Bir özniteliğin değerine bir <xref:System.Xml.Linq.XElement> nesneden veya nesne koleksiyonundaki ilk öğeden ada göre erişmek için BIR XML özniteliği eksen özelliği kullanabilirsiniz <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="86e89-129">You can use an XML attribute axis property to access the value of an attribute by name from an <xref:System.Xml.Linq.XElement> object or from the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="86e89-130">Ada göre bir öznitelik değeri alabilir veya bir öğeye yeni bir öznitelik ekleyerek @ tanımlayıcısının önüne yeni bir ad belirterek ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86e89-130">You can retrieve an attribute value by name, or add a new attribute to an element by specifying a new name preceded by the @ identifier.</span></span>  
  
 <span data-ttu-id="86e89-131">@ Tanımlayıcısını kullanarak bir XML özniteliğine başvurduğunuzda, öznitelik değeri bir dize olarak döndürülür ve özelliği açıkça belirtmeniz gerekmez <xref:System.Xml.Linq.XAttribute.Value%2A> .</span><span class="sxs-lookup"><span data-stu-id="86e89-131">When you refer to an XML attribute using the @ identifier, the attribute value is returned as a string and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="86e89-132">XML öznitelikleri için adlandırma kuralları Visual Basic Tanımlayıcılarla ilgili adlandırma kurallarından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="86e89-132">The naming rules for XML attributes differ from the naming rules for Visual Basic identifiers.</span></span> <span data-ttu-id="86e89-133">Geçerli bir Visual Basic tanımlayıcı olmayan bir ada sahip bir XML özniteliğine erişmek için, adı açılı ayraç () içine alın \< and > .</span><span class="sxs-lookup"><span data-stu-id="86e89-133">To access an XML attribute that has a name that is not a valid Visual Basic identifier, enclose the name in angle brackets (\< and >).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="86e89-134">XML ad alanları</span><span class="sxs-lookup"><span data-stu-id="86e89-134">XML Namespaces</span></span>  
 <span data-ttu-id="86e89-135">Öznitelik ekseni özelliğindeki ad, yalnızca, ifadesini kullanarak genel olarak belirtilen XML ad alanı öneklerini kullanabilir `Imports` .</span><span class="sxs-lookup"><span data-stu-id="86e89-135">The name in an attribute axis property can use only XML namespace prefixes declared globally by using the `Imports` statement.</span></span> <span data-ttu-id="86e89-136">XML öğesi değişmez değerleri içinde yerel olarak belirtilen XML ad alanı öneklerini kullanamaz.</span><span class="sxs-lookup"><span data-stu-id="86e89-136">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="86e89-137">Daha fazla bilgi için bkz. [Imports bildirisi (XML ad alanı)](../statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="86e89-137">For more information, see [Imports Statement (XML Namespace)](../statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="86e89-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="86e89-138">Example</span></span>  
 <span data-ttu-id="86e89-139">Aşağıdaki örnek, `type` adlı XML öğelerinin bir koleksiyonundan ADLı XML özniteliklerinin değerlerinin nasıl alınacağını gösterir `phone` .</span><span class="sxs-lookup"><span data-stu-id="86e89-139">The following example shows how to get the values of the XML attributes named `type` from a collection of XML elements that are named `phone`.</span></span>  
  
 [!code-vb[VbXMLSamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#12)]  
  
 <span data-ttu-id="86e89-140">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="86e89-140">This code displays the following text:</span></span>  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a><span data-ttu-id="86e89-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="86e89-141">Example</span></span>  
 <span data-ttu-id="86e89-142">Aşağıdaki örnek, bir XML öğesi için, XML 'nin bir parçası olarak ve bir nesne örneğine bir öznitelik ekleyerek dinamik olarak nasıl öznitelik oluşturulacağını gösterir <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="86e89-142">The following example shows how to create attributes for an XML element both declaratively, as part of the XML, and dynamically by adding an attribute to an instance of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="86e89-143">`type`Özniteliği bildirimli olarak oluşturulur ve `owner` özniteliği dinamik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="86e89-143">The `type` attribute is created declaratively and the `owner` attribute is created dynamically.</span></span>  
  
 [!code-vb[VbXMLSamples#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#44)]  
  
 <span data-ttu-id="86e89-144">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="86e89-144">This code displays the following text:</span></span>  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a><span data-ttu-id="86e89-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="86e89-145">Example</span></span>  
 <span data-ttu-id="86e89-146">Aşağıdaki örnek `number-type` , Visual Basic ' de geçerli bir tanımlayıcı olmayan ADLı xml özniteliğinin değerini almak için açılı ayraç sözdizimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="86e89-146">The following example uses the angle bracket syntax to get the value of the XML attribute named `number-type`, which is not a valid identifier in Visual Basic.</span></span>  
  
 [!code-vb[VbXMLSamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#13)]  
  
 <span data-ttu-id="86e89-147">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="86e89-147">This code displays the following text:</span></span>  
  
 `Phone type: work`  
  
## <a name="example"></a><span data-ttu-id="86e89-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="86e89-148">Example</span></span>  
 <span data-ttu-id="86e89-149">Aşağıdaki örnek `ns` BIR XML ad alanı ön eki olarak bildirir.</span><span class="sxs-lookup"><span data-stu-id="86e89-149">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="86e89-150">Daha sonra, bir XML sabit değeri oluşturmak ve "" tam adına sahip ilk alt düğüme erişmek için ad alanının önekini kullanır `ns:name` .</span><span class="sxs-lookup"><span data-stu-id="86e89-150">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name "`ns:name`".</span></span>  
  
 [!code-vb[VbXMLSamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples6.vb#14)]  
  
 <span data-ttu-id="86e89-151">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="86e89-151">This code displays the following text:</span></span>  
  
 `Phone type: home`  
  
## <a name="see-also"></a><span data-ttu-id="86e89-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86e89-152">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="86e89-153">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="86e89-153">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="86e89-154">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="86e89-154">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="86e89-155">Visual Basic'de XML Oluşturma</span><span class="sxs-lookup"><span data-stu-id="86e89-155">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="86e89-156">Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları</span><span class="sxs-lookup"><span data-stu-id="86e89-156">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
