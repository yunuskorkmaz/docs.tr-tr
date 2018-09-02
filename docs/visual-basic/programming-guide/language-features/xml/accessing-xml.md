---
title: Visual Basic'de XML'e Erişme
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
ms.openlocfilehash: 0540c52cf3e4cd7594f051c10832ea99cf58a34e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43386466"
---
# <a name="accessing-xml-in-visual-basic"></a><span data-ttu-id="49ab2-102">Visual Basic'de XML'e Erişme</span><span class="sxs-lookup"><span data-stu-id="49ab2-102">Accessing XML in Visual Basic</span></span>
<span data-ttu-id="49ab2-103">Visual Basic, XML eksen özellikleri erişmek ve gezinme sağlar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yapıları.</span><span class="sxs-lookup"><span data-stu-id="49ab2-103">Visual Basic provides XML axis properties for accessing and navigating [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] structures.</span></span> <span data-ttu-id="49ab2-104">Bu özellikler, öğeler ve öznitelikler XML adları belirterek erişim sağlamak için özel bir söz dizimi kullanın.</span><span class="sxs-lookup"><span data-stu-id="49ab2-104">These properties use a special syntax to enable you to access elements and attributes by specifying the XML names.</span></span>  
  
 <span data-ttu-id="49ab2-105">Aşağıdaki tablo, XML öğeleri ve özniteliklerinin Visual Basic'te erişmenize olanak sağlayan dil özellikleri listeler.</span><span class="sxs-lookup"><span data-stu-id="49ab2-105">The following table lists the language features that enable you to access XML elements and attributes in Visual Basic.</span></span>  
  
### <a name="xml-axis-properties"></a><span data-ttu-id="49ab2-106">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="49ab2-106">XML Axis Properties</span></span>  
  
|<span data-ttu-id="49ab2-107">Özellik açıklaması</span><span class="sxs-lookup"><span data-stu-id="49ab2-107">Property description</span></span>|<span data-ttu-id="49ab2-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="49ab2-108">Example</span></span>|<span data-ttu-id="49ab2-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49ab2-109">Description</span></span>|  
|--------------------------|-------------|-----------------|  
|<span data-ttu-id="49ab2-110">*alt eksen*</span><span class="sxs-lookup"><span data-stu-id="49ab2-110">*child axis*</span></span>|`contact.<phone>`|<span data-ttu-id="49ab2-111">Tüm alır `phone` alt öğeleri olan öğeler `contact` öğesi.</span><span class="sxs-lookup"><span data-stu-id="49ab2-111">Gets all `phone` elements that are child elements of the `contact` element.</span></span>|  
|<span data-ttu-id="49ab2-112">*öznitelik eksen*</span><span class="sxs-lookup"><span data-stu-id="49ab2-112">*attribute axis*</span></span>|`phone.@type`|<span data-ttu-id="49ab2-113">Tüm alır `type` özniteliklerini `phone` öğesi.</span><span class="sxs-lookup"><span data-stu-id="49ab2-113">Gets all `type` attributes of the `phone` element.</span></span>|  
|<span data-ttu-id="49ab2-114">*alt eksen*</span><span class="sxs-lookup"><span data-stu-id="49ab2-114">*descendant axis*</span></span>|`contacts...<name>`|<span data-ttu-id="49ab2-115">Tüm alır `name` öğelerini `contacts` bağımsız olarak hiyerarşideki ortaya nasıl derin bir öğe.</span><span class="sxs-lookup"><span data-stu-id="49ab2-115">Gets all `name` elements of the `contacts` element, regardless of how deep in the hierarchy they occur.</span></span>|  
|<span data-ttu-id="49ab2-116">*uzantı dizin oluşturucu*</span><span class="sxs-lookup"><span data-stu-id="49ab2-116">*extension indexer*</span></span>|`contacts...<name>(0)`|<span data-ttu-id="49ab2-117">İlk alır `name` serisinden öğesi.</span><span class="sxs-lookup"><span data-stu-id="49ab2-117">Gets the first `name` element from the sequence.</span></span>|  
|<span data-ttu-id="49ab2-118">*value*</span><span class="sxs-lookup"><span data-stu-id="49ab2-118">*value*</span></span>|`contacts...<name>.Value`|<span data-ttu-id="49ab2-119">İlk nesnenin dize gösterimini sırada alır veya `Nothing` Serisi boşsa.</span><span class="sxs-lookup"><span data-stu-id="49ab2-119">Gets the string representation of the first object in the sequence, or `Nothing` if the sequence is empty.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="49ab2-120">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="49ab2-120">In This Section</span></span>  
 [<span data-ttu-id="49ab2-121">Nasıl yapılır: XML Bağımlı Öğelerine Erişme</span><span class="sxs-lookup"><span data-stu-id="49ab2-121">How to: Access XML Descendant Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 <span data-ttu-id="49ab2-122">Descendant axis özelliği belirtilen ada sahip ve belirtilen bir XML öğesi altında içerdiği tüm XML öğelerine erişmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="49ab2-122">Shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under a specified XML element.</span></span>  
  
 [<span data-ttu-id="49ab2-123">Nasıl yapılır: XML Alt Öğelerine Erişme</span><span class="sxs-lookup"><span data-stu-id="49ab2-123">How to: Access XML Child Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 <span data-ttu-id="49ab2-124">Belirtilen ada sahip bir XML öğesi tüm XML alt öğelerine erişmek için axis özelliği bir alt kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="49ab2-124">Shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="49ab2-125">Nasıl yapılır: XML Özniteliklerine Erişme</span><span class="sxs-lookup"><span data-stu-id="49ab2-125">How to: Access XML Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 <span data-ttu-id="49ab2-126">Belirtilen ada sahip bir XML öğesi tüm XML özniteliklerini erişmek için bir özniteliği axis özelliği kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="49ab2-126">Shows how to use an attribute axis property to access all XML attributes that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="49ab2-127">Nasıl yapılır: XML Ad Alanı Öneklerini Bildirme ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="49ab2-127">How to: Declare and Use XML Namespace Prefixes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 <span data-ttu-id="49ab2-128">Bir XML ad alanı öneki bildirin ve XML öğeleri oluşturma ve kullanma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="49ab2-128">Shows how to declare an XML namespace prefix and use it to create and access XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="49ab2-129">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="49ab2-129">Related Sections</span></span>  
 [<span data-ttu-id="49ab2-130">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="49ab2-130">XML Axis Properties</span></span>](../../../../visual-basic/language-reference/xml-axis/index.md)  
 <span data-ttu-id="49ab2-131">Çeşitli XML erişim özelliklerini açıklayan bölümlerin bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="49ab2-131">Provides links to sections describing the various XML access properties.</span></span>  
  
 [<span data-ttu-id="49ab2-132">LINQ to XML Visual Basic'de genel bakış</span><span class="sxs-lookup"><span data-stu-id="49ab2-132">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 <span data-ttu-id="49ab2-133">Kullanarak bir giriş sağlar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Visual Basic'te.</span><span class="sxs-lookup"><span data-stu-id="49ab2-133">Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="49ab2-134">Visual Basic'de XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="49ab2-134">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 <span data-ttu-id="49ab2-135">Visual Basic'de XML değişmez değerlerini kullanarak bir giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="49ab2-135">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="49ab2-136">Visual Basic'de XML düzenleme</span><span class="sxs-lookup"><span data-stu-id="49ab2-136">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 <span data-ttu-id="49ab2-137">Yükleme ve Visual Basic'te XML değiştirme hakkında bölümlerine bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="49ab2-137">Provides links to sections about loading and modifying XML in Visual Basic.</span></span>  
  
 [<span data-ttu-id="49ab2-138">XML</span><span class="sxs-lookup"><span data-stu-id="49ab2-138">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="49ab2-139">Nasıl kullanılacağını açıklayan bölümlerin bağlantılarını sağlar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Visual Basic'te.</span><span class="sxs-lookup"><span data-stu-id="49ab2-139">Provides links to sections describing how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>
