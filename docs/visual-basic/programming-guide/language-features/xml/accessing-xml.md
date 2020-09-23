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
ms.openlocfilehash: 8ffe6d5ed368aee6d6984ec6ab28c8832921a3f8
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91080185"
---
# <a name="accessing-xml-in-visual-basic"></a><span data-ttu-id="0c6e1-102">Visual Basic'de XML'e Erişme</span><span class="sxs-lookup"><span data-stu-id="0c6e1-102">Accessing XML in Visual Basic</span></span>

<span data-ttu-id="0c6e1-103">Visual Basic, yapılara erişmek ve bunları gezinmek için XML eksen özellikleri sağlar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0c6e1-103">Visual Basic provides XML axis properties for accessing and navigating [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] structures.</span></span> <span data-ttu-id="0c6e1-104">Bu özellikler, XML adlarını belirterek öğelere ve özniteliklere erişmenizi sağlamak için özel bir sözdizimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="0c6e1-104">These properties use a special syntax to enable you to access elements and attributes by specifying the XML names.</span></span>  
  
 <span data-ttu-id="0c6e1-105">Aşağıdaki tabloda, Visual Basic XML öğelerine ve özniteliklerine erişmenize olanak tanıyan dil özellikleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="0c6e1-105">The following table lists the language features that enable you to access XML elements and attributes in Visual Basic.</span></span>  
  
### <a name="xml-axis-properties"></a><span data-ttu-id="0c6e1-106">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="0c6e1-106">XML Axis Properties</span></span>  
  
|<span data-ttu-id="0c6e1-107">Özellik açıklaması</span><span class="sxs-lookup"><span data-stu-id="0c6e1-107">Property description</span></span>|<span data-ttu-id="0c6e1-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="0c6e1-108">Example</span></span>|<span data-ttu-id="0c6e1-109">Description</span><span class="sxs-lookup"><span data-stu-id="0c6e1-109">Description</span></span>|  
|--------------------------|-------------|-----------------|  
|<span data-ttu-id="0c6e1-110">*alt eksen*</span><span class="sxs-lookup"><span data-stu-id="0c6e1-110">*child axis*</span></span>|`contact.<phone>`|<span data-ttu-id="0c6e1-111">`phone`Öğesinin alt öğesi olan tüm öğeleri alır `contact` .</span><span class="sxs-lookup"><span data-stu-id="0c6e1-111">Gets all `phone` elements that are child elements of the `contact` element.</span></span>|  
|<span data-ttu-id="0c6e1-112">*öznitelik ekseni*</span><span class="sxs-lookup"><span data-stu-id="0c6e1-112">*attribute axis*</span></span>|`phone.@type`|<span data-ttu-id="0c6e1-113">Öğesinin tüm `type` özniteliklerini alır `phone` .</span><span class="sxs-lookup"><span data-stu-id="0c6e1-113">Gets all `type` attributes of the `phone` element.</span></span>|  
|<span data-ttu-id="0c6e1-114">*alt öğe ekseni*</span><span class="sxs-lookup"><span data-stu-id="0c6e1-114">*descendant axis*</span></span>|`contacts...<name>`|<span data-ttu-id="0c6e1-115">`name` `contacts` Meydana gelen hiyerarşide ne kadar derinlikte olursa olsun, öğenin tüm öğelerini alır.</span><span class="sxs-lookup"><span data-stu-id="0c6e1-115">Gets all `name` elements of the `contacts` element, regardless of how deep in the hierarchy they occur.</span></span>|  
|<span data-ttu-id="0c6e1-116">*Uzantı Dizin Oluşturucu*</span><span class="sxs-lookup"><span data-stu-id="0c6e1-116">*extension indexer*</span></span>|`contacts...<name>(0)`|<span data-ttu-id="0c6e1-117">`name`Sıradaki ilk öğeyi alır.</span><span class="sxs-lookup"><span data-stu-id="0c6e1-117">Gets the first `name` element from the sequence.</span></span>|  
|<span data-ttu-id="0c6e1-118">*deeri*</span><span class="sxs-lookup"><span data-stu-id="0c6e1-118">*value*</span></span>|`contacts...<name>.Value`|<span data-ttu-id="0c6e1-119">Dizideki ilk nesnenin dize gösterimini alır veya `Nothing` dizi boşsa.</span><span class="sxs-lookup"><span data-stu-id="0c6e1-119">Gets the string representation of the first object in the sequence, or `Nothing` if the sequence is empty.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="0c6e1-120">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="0c6e1-120">In This Section</span></span>  

 [<span data-ttu-id="0c6e1-121">Nasıl yapılır: XML Bağımlı Öğelerine Erişme</span><span class="sxs-lookup"><span data-stu-id="0c6e1-121">How to: Access XML Descendant Elements</span></span>](how-to-access-xml-descendant-elements.md)  
 <span data-ttu-id="0c6e1-122">Belirtilen bir ada sahip olan ve belirtilen bir XML öğesinin altında bulunan tüm XML öğelerine erişmek için bir alt eksen özelliğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0c6e1-122">Shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under a specified XML element.</span></span>  
  
 [<span data-ttu-id="0c6e1-123">Nasıl yapılır: XML Alt Öğelerine Erişme</span><span class="sxs-lookup"><span data-stu-id="0c6e1-123">How to: Access XML Child Elements</span></span>](how-to-access-xml-child-elements.md)  
 <span data-ttu-id="0c6e1-124">Bir XML öğesinde belirtilen bir ada sahip tüm XML alt öğelerine erişmek için bir alt eksen özelliğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0c6e1-124">Shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="0c6e1-125">Nasıl yapılır: XML Özniteliklerine Erişme</span><span class="sxs-lookup"><span data-stu-id="0c6e1-125">How to: Access XML Attributes</span></span>](how-to-access-xml-attributes.md)  
 <span data-ttu-id="0c6e1-126">Bir XML öğesinde belirtilen bir ada sahip tüm XML özniteliklerine erişmek için bir öznitelik eksen özelliğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0c6e1-126">Shows how to use an attribute axis property to access all XML attributes that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="0c6e1-127">Nasıl yapılır: XML Ad Alanı Öneklerini Bildirme ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="0c6e1-127">How to: Declare and Use XML Namespace Prefixes</span></span>](how-to-declare-and-use-xml-namespace-prefixes.md)  
 <span data-ttu-id="0c6e1-128">XML ad alanı ön ekinin nasıl bildirilemeyeceğini ve XML öğeleri oluşturmak ve ona erişmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0c6e1-128">Shows how to declare an XML namespace prefix and use it to create and access XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0c6e1-129">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="0c6e1-129">Related Sections</span></span>  

 [<span data-ttu-id="0c6e1-130">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="0c6e1-130">XML Axis Properties</span></span>](../../../language-reference/xml-axis/index.md)  
 <span data-ttu-id="0c6e1-131">Çeşitli XML erişimi özelliklerini açıklayan bölümlerin bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0c6e1-131">Provides links to sections describing the various XML access properties.</span></span>  
  
 [<span data-ttu-id="0c6e1-132">Visual Basic'de LINQ - XML Dönüşümüne Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0c6e1-132">Overview of LINQ to XML in Visual Basic</span></span>](overview-of-linq-to-xml.md)  
 <span data-ttu-id="0c6e1-133">Visual Basic ' de kullanımı için bir giriş sağlar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0c6e1-133">Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="0c6e1-134">Visual Basic'de XML Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0c6e1-134">Creating XML in Visual Basic</span></span>](creating-xml.md)  
 <span data-ttu-id="0c6e1-135">Visual Basic XML sabit değerlerini kullanmaya giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="0c6e1-135">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="0c6e1-136">Visual Basic'de XML'i Düzenleme</span><span class="sxs-lookup"><span data-stu-id="0c6e1-136">Manipulating XML in Visual Basic</span></span>](manipulating-xml.md)  
 <span data-ttu-id="0c6e1-137">Visual Basic XML 'yi yükleme ve değiştirme hakkındaki bölümlere bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="0c6e1-137">Provides links to sections about loading and modifying XML in Visual Basic.</span></span>  
  
 [<span data-ttu-id="0c6e1-138">XML</span><span class="sxs-lookup"><span data-stu-id="0c6e1-138">XML</span></span>](index.md)  
 <span data-ttu-id="0c6e1-139">Visual Basic ' de kullanımı açıklayan bölümlere bağlantılar sağlar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0c6e1-139">Provides links to sections describing how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>
