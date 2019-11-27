---
title: XML'e erişme
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
ms.openlocfilehash: 1fa1d94fc710272ac0ba9ea7167989da42a51fcd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351743"
---
# <a name="accessing-xml-in-visual-basic"></a><span data-ttu-id="adfb3-102">Visual Basic'de XML'e Erişme</span><span class="sxs-lookup"><span data-stu-id="adfb3-102">Accessing XML in Visual Basic</span></span>
<span data-ttu-id="adfb3-103">Visual Basic, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yapılarına erişmek ve bunları gezinmek için XML eksen özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="adfb3-103">Visual Basic provides XML axis properties for accessing and navigating [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] structures.</span></span> <span data-ttu-id="adfb3-104">Bu özellikler, XML adlarını belirterek öğelere ve özniteliklere erişmenizi sağlamak için özel bir sözdizimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="adfb3-104">These properties use a special syntax to enable you to access elements and attributes by specifying the XML names.</span></span>  
  
 <span data-ttu-id="adfb3-105">Aşağıdaki tabloda, Visual Basic XML öğelerine ve özniteliklerine erişmenize olanak tanıyan dil özellikleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="adfb3-105">The following table lists the language features that enable you to access XML elements and attributes in Visual Basic.</span></span>  
  
### <a name="xml-axis-properties"></a><span data-ttu-id="adfb3-106">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="adfb3-106">XML Axis Properties</span></span>  
  
|<span data-ttu-id="adfb3-107">Özellik açıklaması</span><span class="sxs-lookup"><span data-stu-id="adfb3-107">Property description</span></span>|<span data-ttu-id="adfb3-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="adfb3-108">Example</span></span>|<span data-ttu-id="adfb3-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="adfb3-109">Description</span></span>|  
|--------------------------|-------------|-----------------|  
|<span data-ttu-id="adfb3-110">*alt eksen*</span><span class="sxs-lookup"><span data-stu-id="adfb3-110">*child axis*</span></span>|`contact.<phone>`|<span data-ttu-id="adfb3-111">`contact` öğesinin alt öğesi olan tüm `phone` öğelerini alır.</span><span class="sxs-lookup"><span data-stu-id="adfb3-111">Gets all `phone` elements that are child elements of the `contact` element.</span></span>|  
|<span data-ttu-id="adfb3-112">*öznitelik ekseni*</span><span class="sxs-lookup"><span data-stu-id="adfb3-112">*attribute axis*</span></span>|`phone.@type`|<span data-ttu-id="adfb3-113">`phone` öğesinin tüm `type` özniteliklerini alır.</span><span class="sxs-lookup"><span data-stu-id="adfb3-113">Gets all `type` attributes of the `phone` element.</span></span>|  
|<span data-ttu-id="adfb3-114">*alt öğe ekseni*</span><span class="sxs-lookup"><span data-stu-id="adfb3-114">*descendant axis*</span></span>|`contacts...<name>`|<span data-ttu-id="adfb3-115">`contacts` öğesinin tüm `name` öğelerini alır ve bu hiyerarşide ne kadar derinlikte olursa olsun.</span><span class="sxs-lookup"><span data-stu-id="adfb3-115">Gets all `name` elements of the `contacts` element, regardless of how deep in the hierarchy they occur.</span></span>|  
|<span data-ttu-id="adfb3-116">*Uzantı Dizin Oluşturucu*</span><span class="sxs-lookup"><span data-stu-id="adfb3-116">*extension indexer*</span></span>|`contacts...<name>(0)`|<span data-ttu-id="adfb3-117">Sıradaki ilk `name` öğeyi alır.</span><span class="sxs-lookup"><span data-stu-id="adfb3-117">Gets the first `name` element from the sequence.</span></span>|  
|<span data-ttu-id="adfb3-118">*value*</span><span class="sxs-lookup"><span data-stu-id="adfb3-118">*value*</span></span>|`contacts...<name>.Value`|<span data-ttu-id="adfb3-119">Dizideki ilk nesnenin dize gösterimini alır veya dizi boşsa `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="adfb3-119">Gets the string representation of the first object in the sequence, or `Nothing` if the sequence is empty.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="adfb3-120">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="adfb3-120">In This Section</span></span>  
 [<span data-ttu-id="adfb3-121">Nasıl yapılır: XML Bağımlı Öğelerine Erişme</span><span class="sxs-lookup"><span data-stu-id="adfb3-121">How to: Access XML Descendant Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 <span data-ttu-id="adfb3-122">Belirtilen bir ada sahip olan ve belirtilen bir XML öğesinin altında bulunan tüm XML öğelerine erişmek için bir alt eksen özelliğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="adfb3-122">Shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under a specified XML element.</span></span>  
  
 [<span data-ttu-id="adfb3-123">Nasıl yapılır: XML Alt Öğelerine Erişme</span><span class="sxs-lookup"><span data-stu-id="adfb3-123">How to: Access XML Child Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 <span data-ttu-id="adfb3-124">Bir XML öğesinde belirtilen bir ada sahip tüm XML alt öğelerine erişmek için bir alt eksen özelliğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="adfb3-124">Shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="adfb3-125">Nasıl yapılır: XML Özniteliklerine Erişme</span><span class="sxs-lookup"><span data-stu-id="adfb3-125">How to: Access XML Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 <span data-ttu-id="adfb3-126">Bir XML öğesinde belirtilen bir ada sahip tüm XML özniteliklerine erişmek için bir öznitelik eksen özelliğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="adfb3-126">Shows how to use an attribute axis property to access all XML attributes that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="adfb3-127">Nasıl yapılır: XML Ad Alanı Öneklerini Bildirme ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="adfb3-127">How to: Declare and Use XML Namespace Prefixes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 <span data-ttu-id="adfb3-128">XML ad alanı ön ekinin nasıl bildirilemeyeceğini ve XML öğeleri oluşturmak ve ona erişmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="adfb3-128">Shows how to declare an XML namespace prefix and use it to create and access XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="adfb3-129">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="adfb3-129">Related Sections</span></span>  
 [<span data-ttu-id="adfb3-130">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="adfb3-130">XML Axis Properties</span></span>](../../../../visual-basic/language-reference/xml-axis/index.md)  
 <span data-ttu-id="adfb3-131">Çeşitli XML erişimi özelliklerini açıklayan bölümlerin bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="adfb3-131">Provides links to sections describing the various XML access properties.</span></span>  
  
 [<span data-ttu-id="adfb3-132">Visual Basic LINQ to XML genel bakış</span><span class="sxs-lookup"><span data-stu-id="adfb3-132">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 <span data-ttu-id="adfb3-133">Visual Basic [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] kullanımı için bir giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="adfb3-133">Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="adfb3-134">Visual Basic XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="adfb3-134">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 <span data-ttu-id="adfb3-135">Visual Basic XML sabit değerlerini kullanmaya giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="adfb3-135">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="adfb3-136">Visual Basic XML 'yi düzenleme</span><span class="sxs-lookup"><span data-stu-id="adfb3-136">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 <span data-ttu-id="adfb3-137">Visual Basic XML 'yi yükleme ve değiştirme hakkındaki bölümlere bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="adfb3-137">Provides links to sections about loading and modifying XML in Visual Basic.</span></span>  
  
 [<span data-ttu-id="adfb3-138">XML</span><span class="sxs-lookup"><span data-stu-id="adfb3-138">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="adfb3-139">Visual Basic [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] kullanımını açıklayan bölümlerin bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="adfb3-139">Provides links to sections describing how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>
