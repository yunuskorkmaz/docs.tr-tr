---
title: XML Descendant Axis Özelliği (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Baisc]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
ms.openlocfilehash: 6040401ce3e98c835677be3c4cc7698013348f37
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44129001"
---
# <a name="xml-descendant-axis-property-visual-basic"></a><span data-ttu-id="d1855-102">XML Descendant Axis Özelliği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d1855-102">XML Descendant Axis Property (Visual Basic)</span></span>
<span data-ttu-id="d1855-103">Aşağıdaki alt öğeleri için erişim sağlar: bir <xref:System.Xml.Linq.XElement> nesnesi bir <xref:System.Xml.Linq.XDocument> nesnesi, koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri ya da bir koleksiyonu <xref:System.Xml.Linq.XDocument> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="d1855-103">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1855-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d1855-104">Syntax</span></span>  
  
```  
object...<descendant>  
```  
  
## <a name="parts"></a><span data-ttu-id="d1855-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="d1855-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="d1855-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d1855-106">Required.</span></span> <span data-ttu-id="d1855-107">Bir <xref:System.Xml.Linq.XElement> nesnesi bir <xref:System.Xml.Linq.XDocument> nesnesi, koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri ya da bir koleksiyonu <xref:System.Xml.Linq.XDocument> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="d1855-107">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
 <span data-ttu-id="d1855-108">...<</span><span class="sxs-lookup"><span data-stu-id="d1855-108">...<</span></span>  
 <span data-ttu-id="d1855-109">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d1855-109">Required.</span></span> <span data-ttu-id="d1855-110">Descendant axis özelliği başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d1855-110">Denotes the start of a descendant axis property.</span></span>  
  
 `descendant`  
 <span data-ttu-id="d1855-111">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d1855-111">Required.</span></span> <span data-ttu-id="d1855-112">Adı biçiminin erişmeye alt düğümleri [`prefix``:`]`name`.</span><span class="sxs-lookup"><span data-stu-id="d1855-112">Name of the descendant nodes to access, of the form [`prefix``:`]`name`.</span></span>  
  
|<span data-ttu-id="d1855-113">Bölümü</span><span class="sxs-lookup"><span data-stu-id="d1855-113">Part</span></span>|<span data-ttu-id="d1855-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d1855-114">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="d1855-115">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d1855-115">Optional.</span></span> <span data-ttu-id="d1855-116">Alt düğümü için XML ad alanı öneki.</span><span class="sxs-lookup"><span data-stu-id="d1855-116">XML namespace prefix for the descendant node.</span></span> <span data-ttu-id="d1855-117">Tarafından tanımlanan genel bir XML ad alanı olmalıdır bir `Imports` deyimi.</span><span class="sxs-lookup"><span data-stu-id="d1855-117">Must be a global XML namespace that is defined by using an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="d1855-118">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d1855-118">Required.</span></span> <span data-ttu-id="d1855-119">Alt düğümü yerel adı.</span><span class="sxs-lookup"><span data-stu-id="d1855-119">Local name of the descendant node.</span></span> <span data-ttu-id="d1855-120">Bkz: [bildirilmiş XML öğeleri ve özniteliklerinin adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="d1855-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="d1855-121">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d1855-121">Required.</span></span> <span data-ttu-id="d1855-122">Descendant axis özelliği sonunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d1855-122">Denotes the end of a descendant axis property.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1855-123">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d1855-123">Return Value</span></span>  
 <span data-ttu-id="d1855-124">Bir koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="d1855-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1855-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d1855-125">Remarks</span></span>  
 <span data-ttu-id="d1855-126">Bir XML descendant axis özelliği tarafından adından alt düğümleri erişmek için kullanabileceğiniz bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesnesi veya bir koleksiyonunu <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="d1855-126">You can use an XML descendant axis property to access descendant nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="d1855-127">XML'i `Value` özelliği döndürülen koleksiyondaki ilk alt düğümü değerine erişin.</span><span class="sxs-lookup"><span data-stu-id="d1855-127">Use the XML `Value` property to access the value of the first descendant node in the returned collection.</span></span> <span data-ttu-id="d1855-128">Daha fazla bilgi için [XML değeri özelliği](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="d1855-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
 <span data-ttu-id="d1855-129">Visual Basic derleyici çağrıları alt eksen özellikleri dönüştürür <xref:System.Xml.Linq.XContainer.Descendants%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d1855-129">The Visual Basic compiler converts descendant axis properties into calls to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="d1855-130">XML ad alanları</span><span class="sxs-lookup"><span data-stu-id="d1855-130">XML Namespaces</span></span>  
 <span data-ttu-id="d1855-131">Descendant axis özelliği adı yalnızca XML ad alanları ile küresel olarak bildirilen kullanabilirsiniz `Imports` deyimi.</span><span class="sxs-lookup"><span data-stu-id="d1855-131">The name in a descendant axis property can use only XML namespaces declared globally with the `Imports` statement.</span></span> <span data-ttu-id="d1855-132">XML ad alanları XML öğesi değişmez değerleri içinde yerel olarak bildirilen kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="d1855-132">It cannot use XML namespaces declared locally within XML element literals.</span></span> <span data-ttu-id="d1855-133">Daha fazla bilgi için [Imports deyimi (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="d1855-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1855-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="d1855-134">Example</span></span>  
 <span data-ttu-id="d1855-135">Aşağıdaki örnekte adlı ilk alt düğüm değerine erişin gösterilmiştir `name` ve tüm alt düğümleri adlı değerlerini `phone` gelen `contacts` nesne.</span><span class="sxs-lookup"><span data-stu-id="d1855-135">The following example shows how to access the value of the first descendant node named `name` and the values of all descendant nodes named `phone` from the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#25](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_1.vb)]  
  
 <span data-ttu-id="d1855-136">Bu kod, aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="d1855-136">This code displays the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="d1855-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="d1855-137">Example</span></span>  
 <span data-ttu-id="d1855-138">Aşağıdaki örnek bildirir `ns` olarak bir XML ad alanı öneki.</span><span class="sxs-lookup"><span data-stu-id="d1855-138">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="d1855-139">XML değişmez değer oluşturun ve nitelikli ada sahip ilk alt düğüm değerini erişmek için ad alanı öneki kullanır `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="d1855-139">It then uses the prefix of the namespace to create an XML literal and access the value of the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_2.vb)]  
  
 <span data-ttu-id="d1855-140">Bu kod, aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="d1855-140">This code displays the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="d1855-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d1855-141">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 [<span data-ttu-id="d1855-142">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="d1855-142">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)  
 [<span data-ttu-id="d1855-143">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="d1855-143">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="d1855-144">Visual Basic'de XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="d1855-144">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="d1855-145">Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları</span><span class="sxs-lookup"><span data-stu-id="d1855-145">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
