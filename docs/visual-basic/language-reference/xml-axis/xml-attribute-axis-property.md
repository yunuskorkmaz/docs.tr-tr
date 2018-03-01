---
title: "XML Özniteliği Axis Özelliği (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyAttributeAxis
helpviewer_keywords:
- attribute axis property [Visual Basic]
- Visual Basic code, accessing XML
- XML attribute axis property [Visual Basic]
- XML axis [Visual Basic], attribute
- XML [Visual Basic], accessing
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a286c70f57128d0406b3a300610fea5e1c44b32d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-attribute-axis-property-visual-basic"></a><span data-ttu-id="20b68-102">XML Özniteliği Axis Özelliği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20b68-102">XML Attribute Axis Property (Visual Basic)</span></span>
<span data-ttu-id="20b68-103">İçin bir öznitelik değeri erişim sağlayan bir <xref:System.Xml.Linq.XElement> nesnesi veya bir koleksiyonunu ilk öğe <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="20b68-103">Provides access to the value of an attribute for an <xref:System.Xml.Linq.XElement> object or to the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20b68-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20b68-104">Syntax</span></span>  
  
```  
      object.@attribute  
-or-  
object.@<attribute>  
```  
  
## <a name="parts"></a><span data-ttu-id="20b68-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="20b68-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="20b68-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="20b68-106">Required.</span></span> <span data-ttu-id="20b68-107">Bir <xref:System.Xml.Linq.XElement> nesne ya da bir koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="20b68-107">An <xref:System.Xml.Linq.XElement> object or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="20b68-108">.@</span><span class="sxs-lookup"><span data-stu-id="20b68-108">.@</span></span>  
 <span data-ttu-id="20b68-109">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="20b68-109">Required.</span></span> <span data-ttu-id="20b68-110">Attribute axis özelliği başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="20b68-110">Denotes the start of an attribute axis property.</span></span>  
  
 <  
 <span data-ttu-id="20b68-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="20b68-111">Optional.</span></span> <span data-ttu-id="20b68-112">Özniteliğin adını başlangıcını gösterir, `attribute` geçerli bir tanımlayıcı değil [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="20b68-112">Denotes the beginning of the name of the attribute when `attribute` is not a valid identifier in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
 `attribute`  
 <span data-ttu-id="20b68-113">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="20b68-113">Required.</span></span> <span data-ttu-id="20b68-114">Biçiminde erişmeye özniteliğinin adı [`prefix`:]`name`.</span><span class="sxs-lookup"><span data-stu-id="20b68-114">Name of the attribute to access, of the form [`prefix`:]`name`.</span></span>  
  
|<span data-ttu-id="20b68-115">Bölümü</span><span class="sxs-lookup"><span data-stu-id="20b68-115">Part</span></span>|<span data-ttu-id="20b68-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20b68-116">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="20b68-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="20b68-117">Optional.</span></span> <span data-ttu-id="20b68-118">Öznitelik için XML ad alanı öneki.</span><span class="sxs-lookup"><span data-stu-id="20b68-118">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="20b68-119">Genel bir XML ad alanı ile tanımlanmalıdır bir `Imports` deyimi.</span><span class="sxs-lookup"><span data-stu-id="20b68-119">Must be a global XML namespace defined with an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="20b68-120">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="20b68-120">Required.</span></span> <span data-ttu-id="20b68-121">Yerel öznitelik adı.</span><span class="sxs-lookup"><span data-stu-id="20b68-121">Local attribute name.</span></span> <span data-ttu-id="20b68-122">Bkz: [bildirilmiş XML öğeleri ve özniteliklerinin adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="20b68-122">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="20b68-123">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="20b68-123">Optional.</span></span> <span data-ttu-id="20b68-124">Özniteliğin adını sonunu gösterir, `attribute` geçerli bir tanımlayıcı değil [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="20b68-124">Denotes the end of the name of the attribute when `attribute` is not a valid identifier in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20b68-125">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="20b68-125">Return Value</span></span>  
 <span data-ttu-id="20b68-126">Değerini içeren bir dize `attribute`.</span><span class="sxs-lookup"><span data-stu-id="20b68-126">A string that contains the value of `attribute`.</span></span> <span data-ttu-id="20b68-127">Öznitelik adı yoksa, `Nothing` döndürülür.</span><span class="sxs-lookup"><span data-stu-id="20b68-127">If the attribute name does not exist, `Nothing` is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20b68-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="20b68-128">Remarks</span></span>  
 <span data-ttu-id="20b68-129">Bir XML özniteliği axis özelliği adından tarafından özniteliğin değerini erişmek için kullanabileceğiniz bir <xref:System.Xml.Linq.XElement> nesnesi veya bir koleksiyonunu ilk öğe <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="20b68-129">You can use an XML attribute axis property to access the value of an attribute by name from an <xref:System.Xml.Linq.XElement> object or from the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="20b68-130">Ada göre bir öznitelik değeri alınamıyor veya öncesinde yeni bir ad belirterek bir öğeye yeni bir öznitelik Ekle @ tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="20b68-130">You can retrieve an attribute value by name, or add a new attribute to an element by specifying a new name preceded by the @ identifier.</span></span>  
  
 <span data-ttu-id="20b68-131">Ne zaman başvuran bir XML özniteliği kullanmaya tanımlayıcısı öznitelik değeri bir dize olarak döndürülür ve açıkça belirtmek gerekmez <xref:System.Xml.Linq.XAttribute.Value%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="20b68-131">When you refer to an XML attribute using the @ identifier, the attribute value is returned as a string and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="20b68-132">Adlandırma kuralları XML öznitelikleri için adlandırma kuralları için farklı [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] tanımlayıcıları.</span><span class="sxs-lookup"><span data-stu-id="20b68-132">The naming rules for XML attributes differ from the naming rules for [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] identifiers.</span></span> <span data-ttu-id="20b68-133">Adı, geçerli bir Visual Basic tanımlayıcısı değil bir ada sahip bir XML özniteliği erişmek için açılı ayraç içine alın (\< ve >).</span><span class="sxs-lookup"><span data-stu-id="20b68-133">To access an XML attribute that has a name that is not a valid Visual Basic identifier, enclose the name in angle brackets (\< and >).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="20b68-134">XML ad alanları</span><span class="sxs-lookup"><span data-stu-id="20b68-134">XML Namespaces</span></span>  
 <span data-ttu-id="20b68-135">Attribute axis özelliği adı kullanarak genel olarak bildirilen XML ad alanı önekleri kullanabilirsiniz `Imports` deyimi.</span><span class="sxs-lookup"><span data-stu-id="20b68-135">The name in an attribute axis property can use only XML namespace prefixes declared globally by using the `Imports` statement.</span></span> <span data-ttu-id="20b68-136">XML ad alanı önekleri XML öğesi değişmez içinde yerel olarak bildirilen kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="20b68-136">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="20b68-137">Daha fazla bilgi için bkz: [Imports deyimi (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="20b68-137">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="20b68-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="20b68-138">Example</span></span>  
 <span data-ttu-id="20b68-139">Aşağıdaki örnek adlı XML özniteliklerinin değerlerini alma gösterir `type` adlandırıldığı XML öğeleri koleksiyonundan `phone`.</span><span class="sxs-lookup"><span data-stu-id="20b68-139">The following example shows how to get the values of the XML attributes named `type` from a collection of XML elements that are named `phone`.</span></span>  
  
 [!code-vb[VbXMLSamples#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_1.vb)]  
  
 <span data-ttu-id="20b68-140">Bu kod, aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="20b68-140">This code displays the following text:</span></span>  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a><span data-ttu-id="20b68-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="20b68-141">Example</span></span>  
 <span data-ttu-id="20b68-142">Aşağıdaki örnekte iki bir XML öğesi özniteliklerini bildirimli olarak, XML ve dinamik olarak bir öznitelik örneğine ekleyerek bir parçası olarak oluşturulacağını gösterir bir <xref:System.Xml.Linq.XElement> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="20b68-142">The following example shows how to create attributes for an XML element both declaratively, as part of the XML, and dynamically by adding an attribute to an instance of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="20b68-143">`type` Özniteliği bildirimli olarak oluşturulur ve `owner` özniteliği dinamik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="20b68-143">The `type` attribute is created declaratively and the `owner` attribute is created dynamically.</span></span>  
  
 [!code-vb[VbXMLSamples#44](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_2.vb)]  
  
 <span data-ttu-id="20b68-144">Bu kod, aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="20b68-144">This code displays the following text:</span></span>  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a><span data-ttu-id="20b68-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="20b68-145">Example</span></span>  
 <span data-ttu-id="20b68-146">Aşağıdaki örnek, adlı XML özniteliğinin değerini almak için açılı ayraç sözdizimini kullanır. `number-type`, geçerli bir tanımlayıcı değil [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="20b68-146">The following example uses the angle bracket syntax to get the value of the XML attribute named `number-type`, which is not a valid identifier in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
 [!code-vb[VbXMLSamples#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_3.vb)]  
  
 <span data-ttu-id="20b68-147">Bu kod, aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="20b68-147">This code displays the following text:</span></span>  
  
 `Phone type: work`  
  
## <a name="example"></a><span data-ttu-id="20b68-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="20b68-148">Example</span></span>  
 <span data-ttu-id="20b68-149">Aşağıdaki örnek bildirir `ns` bir XML ad alanı öneki olarak.</span><span class="sxs-lookup"><span data-stu-id="20b68-149">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="20b68-150">XML değişmez değer oluşturmak ve ilk alt düğüm tam adı ile erişmek için ad alanı öneki sonra kullanan "`ns:name`".</span><span class="sxs-lookup"><span data-stu-id="20b68-150">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name "`ns:name`".</span></span>  
  
 [!code-vb[VbXMLSamples#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_4.vb)]  
  
 <span data-ttu-id="20b68-151">Bu kod, aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="20b68-151">This code displays the following text:</span></span>  
  
 `Phone type: home`  
  
## <a name="see-also"></a><span data-ttu-id="20b68-152">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="20b68-152">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 [<span data-ttu-id="20b68-153">XML eksen özellikleri</span><span class="sxs-lookup"><span data-stu-id="20b68-153">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [<span data-ttu-id="20b68-154">XML değişmez değerleri</span><span class="sxs-lookup"><span data-stu-id="20b68-154">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="20b68-155">Visual Basic'de XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="20b68-155">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="20b68-156">Bildirilmiş XML öğeleri ve özniteliklerinin adları</span><span class="sxs-lookup"><span data-stu-id="20b68-156">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
