---
description: ': XML özniteliği eksen özelliği (Visual Basic) hakkında daha fazla bilgi'
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
ms.openlocfilehash: 2085ef2151e7aef7c5642e0ba9ac2e6fa90bfd4e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795176"
---
# <a name="xml-attribute-axis-property-visual-basic"></a><span data-ttu-id="21baf-103">XML Özniteliği Axis Özelliği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21baf-103">XML Attribute Axis Property (Visual Basic)</span></span>

<span data-ttu-id="21baf-104">Bir nesne için bir özniteliğin değerine <xref:System.Xml.Linq.XElement> veya nesne koleksiyonundaki ilk öğeye erişim sağlar <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="21baf-104">Provides access to the value of an attribute for an <xref:System.Xml.Linq.XElement> object or to the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21baf-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="21baf-105">Syntax</span></span>  
  
```vb  
object.@attribute  
' -or-  
object.@<attribute>  
```  
  
## <a name="parts"></a><span data-ttu-id="21baf-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="21baf-106">Parts</span></span>  

 `object`  
 <span data-ttu-id="21baf-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="21baf-107">Required.</span></span> <span data-ttu-id="21baf-108"><xref:System.Xml.Linq.XElement>Nesne veya nesne koleksiyonu <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="21baf-108">An <xref:System.Xml.Linq.XElement> object or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="21baf-109">.@</span><span class="sxs-lookup"><span data-stu-id="21baf-109">.@</span></span>  
 <span data-ttu-id="21baf-110">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="21baf-110">Required.</span></span> <span data-ttu-id="21baf-111">Öznitelik ekseni özelliğinin başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="21baf-111">Denotes the start of an attribute axis property.</span></span>  
  
 <  
 <span data-ttu-id="21baf-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="21baf-112">Optional.</span></span> <span data-ttu-id="21baf-113">Visual Basic geçerli bir tanımlayıcı olmadığında özniteliğin adının başlangıcını gösterir `attribute` .</span><span class="sxs-lookup"><span data-stu-id="21baf-113">Denotes the beginning of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
 `attribute`  
 <span data-ttu-id="21baf-114">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="21baf-114">Required.</span></span> <span data-ttu-id="21baf-115">[:] Biçiminde erişebileceğiniz özniteliğin adı `prefix` `name` .</span><span class="sxs-lookup"><span data-stu-id="21baf-115">Name of the attribute to access, of the form [`prefix`:]`name`.</span></span>  
  
|<span data-ttu-id="21baf-116">Bölüm</span><span class="sxs-lookup"><span data-stu-id="21baf-116">Part</span></span>|<span data-ttu-id="21baf-117">Description</span><span class="sxs-lookup"><span data-stu-id="21baf-117">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="21baf-118">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="21baf-118">Optional.</span></span> <span data-ttu-id="21baf-119">Öznitelik için XML ad alanı ön eki.</span><span class="sxs-lookup"><span data-stu-id="21baf-119">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="21baf-120">Bir ifadesiyle tanımlanmış bir genel XML ad alanı olmalıdır `Imports` .</span><span class="sxs-lookup"><span data-stu-id="21baf-120">Must be a global XML namespace defined with an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="21baf-121">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="21baf-121">Required.</span></span> <span data-ttu-id="21baf-122">Yerel öznitelik adı.</span><span class="sxs-lookup"><span data-stu-id="21baf-122">Local attribute name.</span></span> <span data-ttu-id="21baf-123">[BELIRTILEN XML öğelerinin ve özniteliklerin adlarına](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="21baf-123">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="21baf-124">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="21baf-124">Optional.</span></span> <span data-ttu-id="21baf-125">Visual Basic geçerli bir tanımlayıcı olmadığında özniteliğin adının sonunu belirtir `attribute` .</span><span class="sxs-lookup"><span data-stu-id="21baf-125">Denotes the end of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21baf-126">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="21baf-126">Return Value</span></span>  

 <span data-ttu-id="21baf-127">Değerini içeren bir dize `attribute` .</span><span class="sxs-lookup"><span data-stu-id="21baf-127">A string that contains the value of `attribute`.</span></span> <span data-ttu-id="21baf-128">Öznitelik adı yoksa, `Nothing` döndürülür.</span><span class="sxs-lookup"><span data-stu-id="21baf-128">If the attribute name does not exist, `Nothing` is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21baf-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21baf-129">Remarks</span></span>  

 <span data-ttu-id="21baf-130">Bir özniteliğin değerine bir <xref:System.Xml.Linq.XElement> nesneden veya nesne koleksiyonundaki ilk öğeden ada göre erişmek için BIR XML özniteliği eksen özelliği kullanabilirsiniz <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="21baf-130">You can use an XML attribute axis property to access the value of an attribute by name from an <xref:System.Xml.Linq.XElement> object or from the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="21baf-131">Ada göre bir öznitelik değeri alabilir veya bir öğeye yeni bir öznitelik ekleyerek @ tanımlayıcısının önüne yeni bir ad belirterek ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21baf-131">You can retrieve an attribute value by name, or add a new attribute to an element by specifying a new name preceded by the @ identifier.</span></span>  
  
 <span data-ttu-id="21baf-132">@ Tanımlayıcısını kullanarak bir XML özniteliğine başvurduğunuzda, öznitelik değeri bir dize olarak döndürülür ve özelliği açıkça belirtmeniz gerekmez <xref:System.Xml.Linq.XAttribute.Value%2A> .</span><span class="sxs-lookup"><span data-stu-id="21baf-132">When you refer to an XML attribute using the @ identifier, the attribute value is returned as a string and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="21baf-133">XML öznitelikleri için adlandırma kuralları Visual Basic Tanımlayıcılarla ilgili adlandırma kurallarından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="21baf-133">The naming rules for XML attributes differ from the naming rules for Visual Basic identifiers.</span></span> <span data-ttu-id="21baf-134">Geçerli bir Visual Basic tanımlayıcı olmayan bir ada sahip bir XML özniteliğine erişmek için, adı açılı ayraç () içine alın \< and > .</span><span class="sxs-lookup"><span data-stu-id="21baf-134">To access an XML attribute that has a name that is not a valid Visual Basic identifier, enclose the name in angle brackets (\< and >).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="21baf-135">XML ad alanları</span><span class="sxs-lookup"><span data-stu-id="21baf-135">XML Namespaces</span></span>  

 <span data-ttu-id="21baf-136">Öznitelik ekseni özelliğindeki ad, yalnızca, ifadesini kullanarak genel olarak belirtilen XML ad alanı öneklerini kullanabilir `Imports` .</span><span class="sxs-lookup"><span data-stu-id="21baf-136">The name in an attribute axis property can use only XML namespace prefixes declared globally by using the `Imports` statement.</span></span> <span data-ttu-id="21baf-137">XML öğesi değişmez değerleri içinde yerel olarak belirtilen XML ad alanı öneklerini kullanamaz.</span><span class="sxs-lookup"><span data-stu-id="21baf-137">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="21baf-138">Daha fazla bilgi için bkz. [Imports bildirisi (XML ad alanı)](../statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="21baf-138">For more information, see [Imports Statement (XML Namespace)](../statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="21baf-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="21baf-139">Example</span></span>  

 <span data-ttu-id="21baf-140">Aşağıdaki örnek, `type` adlı XML öğelerinin bir koleksiyonundan ADLı XML özniteliklerinin değerlerinin nasıl alınacağını gösterir `phone` .</span><span class="sxs-lookup"><span data-stu-id="21baf-140">The following example shows how to get the values of the XML attributes named `type` from a collection of XML elements that are named `phone`.</span></span>  
  
 [!code-vb[VbXMLSamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#12)]  
  
 <span data-ttu-id="21baf-141">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="21baf-141">This code displays the following text:</span></span>  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a><span data-ttu-id="21baf-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="21baf-142">Example</span></span>  

 <span data-ttu-id="21baf-143">Aşağıdaki örnek, bir XML öğesi için, XML 'nin bir parçası olarak ve bir nesne örneğine bir öznitelik ekleyerek dinamik olarak nasıl öznitelik oluşturulacağını gösterir <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="21baf-143">The following example shows how to create attributes for an XML element both declaratively, as part of the XML, and dynamically by adding an attribute to an instance of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="21baf-144">`type`Özniteliği bildirimli olarak oluşturulur ve `owner` özniteliği dinamik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="21baf-144">The `type` attribute is created declaratively and the `owner` attribute is created dynamically.</span></span>  
  
 [!code-vb[VbXMLSamples#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#44)]  
  
 <span data-ttu-id="21baf-145">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="21baf-145">This code displays the following text:</span></span>  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a><span data-ttu-id="21baf-146">Örnek</span><span class="sxs-lookup"><span data-stu-id="21baf-146">Example</span></span>  

 <span data-ttu-id="21baf-147">Aşağıdaki örnek `number-type` , Visual Basic ' de geçerli bir tanımlayıcı olmayan ADLı xml özniteliğinin değerini almak için açılı ayraç sözdizimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="21baf-147">The following example uses the angle bracket syntax to get the value of the XML attribute named `number-type`, which is not a valid identifier in Visual Basic.</span></span>  
  
 [!code-vb[VbXMLSamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#13)]  
  
 <span data-ttu-id="21baf-148">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="21baf-148">This code displays the following text:</span></span>  
  
 `Phone type: work`  
  
## <a name="example"></a><span data-ttu-id="21baf-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="21baf-149">Example</span></span>  

 <span data-ttu-id="21baf-150">Aşağıdaki örnek `ns` BIR XML ad alanı ön eki olarak bildirir.</span><span class="sxs-lookup"><span data-stu-id="21baf-150">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="21baf-151">Daha sonra, bir XML sabit değeri oluşturmak ve "" tam adına sahip ilk alt düğüme erişmek için ad alanının önekini kullanır `ns:name` .</span><span class="sxs-lookup"><span data-stu-id="21baf-151">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name "`ns:name`".</span></span>  
  
 [!code-vb[VbXMLSamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples6.vb#14)]  
  
 <span data-ttu-id="21baf-152">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="21baf-152">This code displays the following text:</span></span>  
  
 `Phone type: home`  
  
## <a name="see-also"></a><span data-ttu-id="21baf-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21baf-153">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="21baf-154">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="21baf-154">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="21baf-155">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="21baf-155">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="21baf-156">Visual Basic'de XML Oluşturma</span><span class="sxs-lookup"><span data-stu-id="21baf-156">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="21baf-157">Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları</span><span class="sxs-lookup"><span data-stu-id="21baf-157">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
