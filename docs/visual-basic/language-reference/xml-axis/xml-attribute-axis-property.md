---
title: XML Özniteliği Axis Özelliği (Visual Basic)
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
ms.openlocfilehash: 9107b946394ab70980e4865364fc1ba9683e2025
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43785166"
---
# <a name="xml-attribute-axis-property-visual-basic"></a><span data-ttu-id="b8350-102">XML Özniteliği Axis Özelliği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8350-102">XML Attribute Axis Property (Visual Basic)</span></span>
<span data-ttu-id="b8350-103">İçin bir öznitelik değeri erişim sağlayan bir <xref:System.Xml.Linq.XElement> nesne veya koleksiyonu içindeki ilk öğeye <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="b8350-103">Provides access to the value of an attribute for an <xref:System.Xml.Linq.XElement> object or to the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8350-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b8350-104">Syntax</span></span>  
  
```  
      object.@attribute  
-or-  
object.@<attribute>  
```  
  
## <a name="parts"></a><span data-ttu-id="b8350-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="b8350-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="b8350-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="b8350-106">Required.</span></span> <span data-ttu-id="b8350-107">Bir <xref:System.Xml.Linq.XElement> nesnesi veya bir koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="b8350-107">An <xref:System.Xml.Linq.XElement> object or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="b8350-108">.@</span><span class="sxs-lookup"><span data-stu-id="b8350-108">.@</span></span>  
 <span data-ttu-id="b8350-109">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="b8350-109">Required.</span></span> <span data-ttu-id="b8350-110">Bir özniteliği axis özelliği başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b8350-110">Denotes the start of an attribute axis property.</span></span>  
  
 <  
 <span data-ttu-id="b8350-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="b8350-111">Optional.</span></span> <span data-ttu-id="b8350-112">Özniteliğin adını başlangıcını gösterir, `attribute` Visual Basic'te geçerli bir tanımlayıcı değil.</span><span class="sxs-lookup"><span data-stu-id="b8350-112">Denotes the beginning of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
 `attribute`  
 <span data-ttu-id="b8350-113">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="b8350-113">Required.</span></span> <span data-ttu-id="b8350-114">Biçiminde erişmeye özniteliğin adı [`prefix`:]`name`.</span><span class="sxs-lookup"><span data-stu-id="b8350-114">Name of the attribute to access, of the form [`prefix`:]`name`.</span></span>  
  
|<span data-ttu-id="b8350-115">Bölümü</span><span class="sxs-lookup"><span data-stu-id="b8350-115">Part</span></span>|<span data-ttu-id="b8350-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8350-116">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="b8350-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="b8350-117">Optional.</span></span> <span data-ttu-id="b8350-118">Özniteliği için XML ad alanı öneki.</span><span class="sxs-lookup"><span data-stu-id="b8350-118">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="b8350-119">Genel XML ad alanı ile tanımlanmalıdır bir `Imports` deyimi.</span><span class="sxs-lookup"><span data-stu-id="b8350-119">Must be a global XML namespace defined with an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="b8350-120">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="b8350-120">Required.</span></span> <span data-ttu-id="b8350-121">Yerel bir öznitelik adı.</span><span class="sxs-lookup"><span data-stu-id="b8350-121">Local attribute name.</span></span> <span data-ttu-id="b8350-122">Bkz: [bildirilmiş XML öğeleri ve özniteliklerinin adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="b8350-122">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="b8350-123">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="b8350-123">Optional.</span></span> <span data-ttu-id="b8350-124">Özniteliğin adını sonuna gösterir, `attribute` Visual Basic'te geçerli bir tanımlayıcı değil.</span><span class="sxs-lookup"><span data-stu-id="b8350-124">Denotes the end of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b8350-125">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b8350-125">Return Value</span></span>  
 <span data-ttu-id="b8350-126">Değerini içeren bir dize `attribute`.</span><span class="sxs-lookup"><span data-stu-id="b8350-126">A string that contains the value of `attribute`.</span></span> <span data-ttu-id="b8350-127">Öznitelik adı mevcut değilse `Nothing` döndürülür.</span><span class="sxs-lookup"><span data-stu-id="b8350-127">If the attribute name does not exist, `Nothing` is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8350-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b8350-128">Remarks</span></span>  
 <span data-ttu-id="b8350-129">Bir XML özniteliği axis özelliği bir özniteliğin değerini adından tarafından erişmek için kullanabileceğiniz bir <xref:System.Xml.Linq.XElement> nesne veya koleksiyonu içindeki ilk öğeyi <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="b8350-129">You can use an XML attribute axis property to access the value of an attribute by name from an <xref:System.Xml.Linq.XElement> object or from the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="b8350-130">Bir özniteliği değeri ada göre alabilirsiniz veya koyarak yeni bir ad belirterek, bir öğeye yeni bir öznitelik eklemek @ tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="b8350-130">You can retrieve an attribute value by name, or add a new attribute to an element by specifying a new name preceded by the @ identifier.</span></span>  
  
 <span data-ttu-id="b8350-131">Ne zaman başvuru kullanarak bir XML özniteliği tanımlayıcı, dize olarak öznitelik değeri döndürülür ve açıkça belirtmeniz gerekmez <xref:System.Xml.Linq.XAttribute.Value%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="b8350-131">When you refer to an XML attribute using the @ identifier, the attribute value is returned as a string and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="b8350-132">Visual Basic tanımlayıcıları için adlandırma kuralları adlandırma kuralları için XML özniteliklerini farklıdır.</span><span class="sxs-lookup"><span data-stu-id="b8350-132">The naming rules for XML attributes differ from the naming rules for Visual Basic identifiers.</span></span> <span data-ttu-id="b8350-133">Geçerli bir Visual Basic tanımlayıcı bir ada sahip bir XML özniteliği erişmek için ad, açılı ayraçlar içine (\< ve >).</span><span class="sxs-lookup"><span data-stu-id="b8350-133">To access an XML attribute that has a name that is not a valid Visual Basic identifier, enclose the name in angle brackets (\< and >).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="b8350-134">XML ad alanları</span><span class="sxs-lookup"><span data-stu-id="b8350-134">XML Namespaces</span></span>  
 <span data-ttu-id="b8350-135">Bir özniteliği axis özelliği adı genel olarak kullanılarak bildirilen XML ad alanı öneklerini kullanabilirsiniz `Imports` deyimi.</span><span class="sxs-lookup"><span data-stu-id="b8350-135">The name in an attribute axis property can use only XML namespace prefixes declared globally by using the `Imports` statement.</span></span> <span data-ttu-id="b8350-136">XML ad alanı öneklerini XML öğesi değişmez değerleri içinde yerel olarak bildirilen kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="b8350-136">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="b8350-137">Daha fazla bilgi için [Imports deyimi (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="b8350-137">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8350-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8350-138">Example</span></span>  
 <span data-ttu-id="b8350-139">Aşağıdaki örnekte adlı XML öznitelik değerleri, alınacağı gösterilmektedir `type` adlı XML öğesi bir koleksiyondan `phone`.</span><span class="sxs-lookup"><span data-stu-id="b8350-139">The following example shows how to get the values of the XML attributes named `type` from a collection of XML elements that are named `phone`.</span></span>  
  
 [!code-vb[VbXMLSamples#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_1.vb)]  
  
 <span data-ttu-id="b8350-140">Bu kod, aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="b8350-140">This code displays the following text:</span></span>  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a><span data-ttu-id="b8350-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8350-141">Example</span></span>  
 <span data-ttu-id="b8350-142">Aşağıdaki örnek, hem bir XML öğesi için öznitelikleri bildirimli olarak, XML ve dinamik olarak örneğine bir öznitelik ekleyerek bir parçası olarak oluşturma işlemi gösterilmektedir bir <xref:System.Xml.Linq.XElement> nesne.</span><span class="sxs-lookup"><span data-stu-id="b8350-142">The following example shows how to create attributes for an XML element both declaratively, as part of the XML, and dynamically by adding an attribute to an instance of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="b8350-143">`type` Özniteliği bildirimli olarak oluşturulur ve `owner` özniteliği dinamik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b8350-143">The `type` attribute is created declaratively and the `owner` attribute is created dynamically.</span></span>  
  
 [!code-vb[VbXMLSamples#44](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_2.vb)]  
  
 <span data-ttu-id="b8350-144">Bu kod, aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="b8350-144">This code displays the following text:</span></span>  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a><span data-ttu-id="b8350-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8350-145">Example</span></span>  
 <span data-ttu-id="b8350-146">Aşağıdaki örnek açılı ayraç sözdizimini XML özniteliğinin değerini almak için kullanır. `number-type`, Visual Basic'te geçerli bir tanımlayıcı değil.</span><span class="sxs-lookup"><span data-stu-id="b8350-146">The following example uses the angle bracket syntax to get the value of the XML attribute named `number-type`, which is not a valid identifier in Visual Basic.</span></span>  
  
 [!code-vb[VbXMLSamples#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_3.vb)]  
  
 <span data-ttu-id="b8350-147">Bu kod, aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="b8350-147">This code displays the following text:</span></span>  
  
 `Phone type: work`  
  
## <a name="example"></a><span data-ttu-id="b8350-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8350-148">Example</span></span>  
 <span data-ttu-id="b8350-149">Aşağıdaki örnek bildirir `ns` olarak bir XML ad alanı öneki.</span><span class="sxs-lookup"><span data-stu-id="b8350-149">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="b8350-150">XML değişmez değer oluşturun ve ilk alt düğüm tam adı ile erişmek için bir ad alanı öneki kullanır "`ns:name`".</span><span class="sxs-lookup"><span data-stu-id="b8350-150">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name "`ns:name`".</span></span>  
  
 [!code-vb[VbXMLSamples#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_4.vb)]  
  
 <span data-ttu-id="b8350-151">Bu kod, aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="b8350-151">This code displays the following text:</span></span>  
  
 `Phone type: home`  
  
## <a name="see-also"></a><span data-ttu-id="b8350-152">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b8350-152">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 [<span data-ttu-id="b8350-153">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="b8350-153">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)  
 [<span data-ttu-id="b8350-154">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="b8350-154">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="b8350-155">Visual Basic'de XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="b8350-155">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="b8350-156">Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları</span><span class="sxs-lookup"><span data-stu-id="b8350-156">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
