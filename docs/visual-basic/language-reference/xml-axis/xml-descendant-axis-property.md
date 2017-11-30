---
title: "XML Descendant Axis Özelliği (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Baisc]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0f3c42b5134b058c010ca4c7a5ee7c24627c65fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-descendant-axis-property-visual-basic"></a><span data-ttu-id="52828-102">XML Descendant Axis Özelliği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52828-102">XML Descendant Axis Property (Visual Basic)</span></span>
<span data-ttu-id="52828-103">Aşağıdaki alt öğelere erişim sağlar: bir <xref:System.Xml.Linq.XElement> nesne, bir <xref:System.Xml.Linq.XDocument> nesnesi, bir koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri veya koleksiyonu <xref:System.Xml.Linq.XDocument> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="52828-103">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52828-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52828-104">Syntax</span></span>  
  
```  
object...<descendant>  
```  
  
## <a name="parts"></a><span data-ttu-id="52828-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="52828-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="52828-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="52828-106">Required.</span></span> <span data-ttu-id="52828-107">Bir <xref:System.Xml.Linq.XElement> nesne, bir <xref:System.Xml.Linq.XDocument> nesnesi, bir koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri veya koleksiyonu <xref:System.Xml.Linq.XDocument> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="52828-107">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
 <span data-ttu-id="52828-108">...<</span><span class="sxs-lookup"><span data-stu-id="52828-108">...<</span></span>  
 <span data-ttu-id="52828-109">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="52828-109">Required.</span></span> <span data-ttu-id="52828-110">Descendant axis özelliği başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="52828-110">Denotes the start of a descendant axis property.</span></span>  
  
 `descendant`  
 <span data-ttu-id="52828-111">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="52828-111">Required.</span></span> <span data-ttu-id="52828-112">Biçiminde erişmeye alt düğümlerin adı [`prefix``:`]`name`.</span><span class="sxs-lookup"><span data-stu-id="52828-112">Name of the descendant nodes to access, of the form [`prefix``:`]`name`.</span></span>  
  
|<span data-ttu-id="52828-113">Bölümü</span><span class="sxs-lookup"><span data-stu-id="52828-113">Part</span></span>|<span data-ttu-id="52828-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52828-114">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="52828-115">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="52828-115">Optional.</span></span> <span data-ttu-id="52828-116">Alt düğüm için XML ad alanı öneki.</span><span class="sxs-lookup"><span data-stu-id="52828-116">XML namespace prefix for the descendant node.</span></span> <span data-ttu-id="52828-117">Kullanılarak tanımlanmış genel bir XML ad alanı olmalıdır bir `Imports` deyimi.</span><span class="sxs-lookup"><span data-stu-id="52828-117">Must be a global XML namespace that is defined by using an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="52828-118">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="52828-118">Required.</span></span> <span data-ttu-id="52828-119">Yerel alt düğümün adı.</span><span class="sxs-lookup"><span data-stu-id="52828-119">Local name of the descendant node.</span></span> <span data-ttu-id="52828-120">Bkz: [bildirilmiş XML öğeleri ve özniteliklerinin adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="52828-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="52828-121">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="52828-121">Required.</span></span> <span data-ttu-id="52828-122">Descendant axis özelliği sonunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="52828-122">Denotes the end of a descendant axis property.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52828-123">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="52828-123">Return Value</span></span>  
 <span data-ttu-id="52828-124">Bir koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="52828-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52828-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="52828-125">Remarks</span></span>  
 <span data-ttu-id="52828-126">XML descendant axis özelliği adından tarafından alt düğümleri erişmek için kullanabileceğiniz bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesnesi veya bir koleksiyonundan <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="52828-126">You can use an XML descendant axis property to access descendant nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="52828-127">XML kullanmak `Value` döndürülen koleksiyon ilk alt düğüm değerini erişmek için özellik.</span><span class="sxs-lookup"><span data-stu-id="52828-127">Use the XML `Value` property to access the value of the first descendant node in the returned collection.</span></span> <span data-ttu-id="52828-128">Daha fazla bilgi için bkz: [XML değeri özelliği](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="52828-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
 <span data-ttu-id="52828-129">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Derleyici çağrıları alt eksen özellikleri dönüştürür <xref:System.Xml.Linq.XContainer.Descendants%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="52828-129">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler converts descendant axis properties into calls to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="52828-130">XML ad alanları</span><span class="sxs-lookup"><span data-stu-id="52828-130">XML Namespaces</span></span>  
 <span data-ttu-id="52828-131">Descendant axis özelliği adı yalnızca XML ad alanları ile genel olarak bildirilen kullanabilirsiniz `Imports` deyimi.</span><span class="sxs-lookup"><span data-stu-id="52828-131">The name in a descendant axis property can use only XML namespaces declared globally with the `Imports` statement.</span></span> <span data-ttu-id="52828-132">XML öğesi değişmez içinde yerel olarak bildirilen XML ad alanları kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="52828-132">It cannot use XML namespaces declared locally within XML element literals.</span></span> <span data-ttu-id="52828-133">Daha fazla bilgi için bkz: [Imports deyimi (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="52828-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="52828-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="52828-134">Example</span></span>  
 <span data-ttu-id="52828-135">Aşağıdaki örnekte nasıl adlı ilk alt düğüm değerini erişeceğinizi gösterir `name` ve tüm alt düğümlerin adlı değerleri `phone` gelen `contacts` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="52828-135">The following example shows how to access the value of the first descendant node named `name` and the values of all descendant nodes named `phone` from the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#25](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_1.vb)]  
  
 <span data-ttu-id="52828-136">Bu kod, aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="52828-136">This code displays the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="52828-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="52828-137">Example</span></span>  
 <span data-ttu-id="52828-138">Aşağıdaki örnek bildirir `ns` bir XML ad alanı öneki olarak.</span><span class="sxs-lookup"><span data-stu-id="52828-138">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="52828-139">XML değişmez değer oluşturmak ve tam adı ile ilk alt düğüm değerini erişmek için ad alanı öneki sonra kullanan `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="52828-139">It then uses the prefix of the namespace to create an XML literal and access the value of the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_2.vb)]  
  
 <span data-ttu-id="52828-140">Bu kod, aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="52828-140">This code displays the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="52828-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="52828-141">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 [<span data-ttu-id="52828-142">XML eksen özellikleri</span><span class="sxs-lookup"><span data-stu-id="52828-142">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [<span data-ttu-id="52828-143">XML değişmez değerleri</span><span class="sxs-lookup"><span data-stu-id="52828-143">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="52828-144">Visual Basic'de XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="52828-144">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="52828-145">Bildirilmiş XML öğeleri ve özniteliklerinin adları</span><span class="sxs-lookup"><span data-stu-id="52828-145">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
