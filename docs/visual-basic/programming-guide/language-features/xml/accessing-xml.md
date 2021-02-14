---
description: "Hakkında daha fazla bilgi edinin: Visual Basic XML 'e erişme"
title: XML'e erişme
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
ms.openlocfilehash: 2d77b2aa5f4136095ce5684976fe3ba03be7c28c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462665"
---
# <a name="accessing-xml-in-visual-basic"></a><span data-ttu-id="e2da3-103">Visual Basic'de XML'e Erişme</span><span class="sxs-lookup"><span data-stu-id="e2da3-103">Accessing XML in Visual Basic</span></span>

<span data-ttu-id="e2da3-104">Visual Basic, yapılara erişmek ve bunları gezinmek için XML eksen özellikleri sağlar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e2da3-104">Visual Basic provides XML axis properties for accessing and navigating [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] structures.</span></span> <span data-ttu-id="e2da3-105">Bu özellikler, XML adlarını belirterek öğelere ve özniteliklere erişmenizi sağlamak için özel bir sözdizimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="e2da3-105">These properties use a special syntax to enable you to access elements and attributes by specifying the XML names.</span></span>  
  
 <span data-ttu-id="e2da3-106">Aşağıdaki tabloda, Visual Basic XML öğelerine ve özniteliklerine erişmenize olanak tanıyan dil özellikleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="e2da3-106">The following table lists the language features that enable you to access XML elements and attributes in Visual Basic.</span></span>  
  
### <a name="xml-axis-properties"></a><span data-ttu-id="e2da3-107">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="e2da3-107">XML Axis Properties</span></span>  
  
|<span data-ttu-id="e2da3-108">Özellik açıklaması</span><span class="sxs-lookup"><span data-stu-id="e2da3-108">Property description</span></span>|<span data-ttu-id="e2da3-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="e2da3-109">Example</span></span>|<span data-ttu-id="e2da3-110">Description</span><span class="sxs-lookup"><span data-stu-id="e2da3-110">Description</span></span>|  
|--------------------------|-------------|-----------------|  
|<span data-ttu-id="e2da3-111">*alt eksen*</span><span class="sxs-lookup"><span data-stu-id="e2da3-111">*child axis*</span></span>|`contact.<phone>`|<span data-ttu-id="e2da3-112">`phone`Öğesinin alt öğesi olan tüm öğeleri alır `contact` .</span><span class="sxs-lookup"><span data-stu-id="e2da3-112">Gets all `phone` elements that are child elements of the `contact` element.</span></span>|  
|<span data-ttu-id="e2da3-113">*öznitelik ekseni*</span><span class="sxs-lookup"><span data-stu-id="e2da3-113">*attribute axis*</span></span>|`phone.@type`|<span data-ttu-id="e2da3-114">Öğesinin tüm `type` özniteliklerini alır `phone` .</span><span class="sxs-lookup"><span data-stu-id="e2da3-114">Gets all `type` attributes of the `phone` element.</span></span>|  
|<span data-ttu-id="e2da3-115">*alt öğe ekseni*</span><span class="sxs-lookup"><span data-stu-id="e2da3-115">*descendant axis*</span></span>|`contacts...<name>`|<span data-ttu-id="e2da3-116">`name` `contacts` Meydana gelen hiyerarşide ne kadar derinlikte olursa olsun, öğenin tüm öğelerini alır.</span><span class="sxs-lookup"><span data-stu-id="e2da3-116">Gets all `name` elements of the `contacts` element, regardless of how deep in the hierarchy they occur.</span></span>|  
|<span data-ttu-id="e2da3-117">*Uzantı Dizin Oluşturucu*</span><span class="sxs-lookup"><span data-stu-id="e2da3-117">*extension indexer*</span></span>|`contacts...<name>(0)`|<span data-ttu-id="e2da3-118">`name`Sıradaki ilk öğeyi alır.</span><span class="sxs-lookup"><span data-stu-id="e2da3-118">Gets the first `name` element from the sequence.</span></span>|  
|<span data-ttu-id="e2da3-119">*değer*</span><span class="sxs-lookup"><span data-stu-id="e2da3-119">*value*</span></span>|`contacts...<name>.Value`|<span data-ttu-id="e2da3-120">Dizideki ilk nesnenin dize gösterimini alır veya `Nothing` dizi boşsa.</span><span class="sxs-lookup"><span data-stu-id="e2da3-120">Gets the string representation of the first object in the sequence, or `Nothing` if the sequence is empty.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="e2da3-121">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e2da3-121">In This Section</span></span>  

 [<span data-ttu-id="e2da3-122">Nasıl yapılır: XML Bağımlı Öğelerine Erişme</span><span class="sxs-lookup"><span data-stu-id="e2da3-122">How to: Access XML Descendant Elements</span></span>](how-to-access-xml-descendant-elements.md)  
 <span data-ttu-id="e2da3-123">Belirtilen bir ada sahip olan ve belirtilen bir XML öğesinin altında bulunan tüm XML öğelerine erişmek için bir alt eksen özelliğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e2da3-123">Shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under a specified XML element.</span></span>  
  
 [<span data-ttu-id="e2da3-124">Nasıl yapılır: XML Alt Öğelerine Erişme</span><span class="sxs-lookup"><span data-stu-id="e2da3-124">How to: Access XML Child Elements</span></span>](how-to-access-xml-child-elements.md)  
 <span data-ttu-id="e2da3-125">Bir XML öğesinde belirtilen bir ada sahip tüm XML alt öğelerine erişmek için bir alt eksen özelliğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e2da3-125">Shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="e2da3-126">Nasıl yapılır: XML Özniteliklerine Erişme</span><span class="sxs-lookup"><span data-stu-id="e2da3-126">How to: Access XML Attributes</span></span>](how-to-access-xml-attributes.md)  
 <span data-ttu-id="e2da3-127">Bir XML öğesinde belirtilen bir ada sahip tüm XML özniteliklerine erişmek için bir öznitelik eksen özelliğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e2da3-127">Shows how to use an attribute axis property to access all XML attributes that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="e2da3-128">Nasıl yapılır: XML Ad Alanı Öneklerini Bildirme ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="e2da3-128">How to: Declare and Use XML Namespace Prefixes</span></span>](how-to-declare-and-use-xml-namespace-prefixes.md)  
 <span data-ttu-id="e2da3-129">XML ad alanı ön ekinin nasıl bildirilemeyeceğini ve XML öğeleri oluşturmak ve ona erişmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e2da3-129">Shows how to declare an XML namespace prefix and use it to create and access XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e2da3-130">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="e2da3-130">Related Sections</span></span>  

 [<span data-ttu-id="e2da3-131">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="e2da3-131">XML Axis Properties</span></span>](../../../language-reference/xml-axis/index.md)  
 <span data-ttu-id="e2da3-132">Çeşitli XML erişimi özelliklerini açıklayan bölümlerin bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2da3-132">Provides links to sections describing the various XML access properties.</span></span>  
  
 [<span data-ttu-id="e2da3-133">Visual Basic'de LINQ - XML Dönüşümüne Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e2da3-133">Overview of LINQ to XML in Visual Basic</span></span>](overview-of-linq-to-xml.md)  
 <span data-ttu-id="e2da3-134">Visual Basic ' de kullanımı için bir giriş sağlar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e2da3-134">Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="e2da3-135">Visual Basic'de XML Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e2da3-135">Creating XML in Visual Basic</span></span>](creating-xml.md)  
 <span data-ttu-id="e2da3-136">Visual Basic XML sabit değerlerini kullanmaya giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2da3-136">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="e2da3-137">Visual Basic'de XML'i Düzenleme</span><span class="sxs-lookup"><span data-stu-id="e2da3-137">Manipulating XML in Visual Basic</span></span>](manipulating-xml.md)  
 <span data-ttu-id="e2da3-138">Visual Basic XML 'yi yükleme ve değiştirme hakkındaki bölümlere bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2da3-138">Provides links to sections about loading and modifying XML in Visual Basic.</span></span>  
  
 [<span data-ttu-id="e2da3-139">XML</span><span class="sxs-lookup"><span data-stu-id="e2da3-139">XML</span></span>](index.md)  
 <span data-ttu-id="e2da3-140">Visual Basic ' de kullanımı açıklayan bölümlere bağlantılar sağlar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e2da3-140">Provides links to sections describing how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>
