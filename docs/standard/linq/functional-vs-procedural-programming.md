---
title: İşlevsel ve yordamsal programlama
description: LINQ to XML, XML uygulamaları oluşturmak için hem işlevsel oluşturma hem de yordamsal teknikleri destekler. İşlevsel oluşturma, bildirime dayalı bir yaklaşımdır. Yordamsal teknikler, XML ağaçlarının bellek içi değişikliğini destekler.
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: a2753a31e88fd338dad61063f559431869b9e17f
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552997"
---
# <a name="functional-vs-procedural-programming-linq-to-xml"></a><span data-ttu-id="22144-105">İşlevsel ve yordamsal programlama (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="22144-105">Functional vs. procedural programming (LINQ to XML)</span></span>

<span data-ttu-id="22144-106">Çeşitli türlerdeki XML uygulamaları vardır:</span><span class="sxs-lookup"><span data-stu-id="22144-106">There are various types of XML applications:</span></span>

- <span data-ttu-id="22144-107">Bazı uygulamalar kaynak XML belgelerini alır ve kaynak belgelerden farklı bir şekilde yeni XML belgeleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="22144-107">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>
- <span data-ttu-id="22144-108">Bazı uygulamalar kaynak XML belgelerini alır ve sonuç belgelerini HTML veya CSV metin dosyaları gibi tamamen farklı bir biçimde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="22144-108">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>
- <span data-ttu-id="22144-109">Bazı uygulamalar kaynak XML belgelerini alır ve bir veritabanına kayıt ekler.</span><span class="sxs-lookup"><span data-stu-id="22144-109">Some applications take source XML documents, and insert records into a database.</span></span>
- <span data-ttu-id="22144-110">Bazı uygulamalar, bir veritabanı gibi başka bir kaynaktan veri alır ve bundan XML belgesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="22144-110">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>

<span data-ttu-id="22144-111">Bunlar, XML uygulaması türlerinin hepsi değildir, ancak bunlar bir XML Programlayıcısının uygulamak zorunda olduğu işlevsellik türlerinin temsili bir kümesidir.</span><span class="sxs-lookup"><span data-stu-id="22144-111">These aren't all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>

<span data-ttu-id="22144-112">Bu tür uygulamaların tümünde, bir geliştiricinin uygulayabileceğiniz iki yaklaşım vardır:</span><span class="sxs-lookup"><span data-stu-id="22144-112">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>

- <span data-ttu-id="22144-113">Bildirim temelli bir yaklaşım kullanılarak işlevsel oluşturma.</span><span class="sxs-lookup"><span data-stu-id="22144-113">Functional construction using a declarative approach.</span></span>
- <span data-ttu-id="22144-114">Yordamsal kodu kullanarak bellek içi XML ağacı değişikliği.</span><span class="sxs-lookup"><span data-stu-id="22144-114">In-memory XML tree modification using procedural code.</span></span>

<span data-ttu-id="22144-115">LINQ to XML her iki yaklaşımı destekler.</span><span class="sxs-lookup"><span data-stu-id="22144-115">LINQ to XML supports both approaches.</span></span>

<span data-ttu-id="22144-116">İşlevsel yaklaşımı kullanırken, kaynak belgeleri alan ve istenen şekle sahip tamamen yeni sonuç belgeleri oluşturan dönüşümler yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="22144-116">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>

<span data-ttu-id="22144-117">Bir XML ağacını yerinde değiştirirken, düğüm içi bir XML ağacındaki düğümlerde geçen ve gezinen, düğümleri ekleme, silme ve değiştirme gibi bir kod yazın.</span><span class="sxs-lookup"><span data-stu-id="22144-117">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>

<span data-ttu-id="22144-118">LINQ to XML iki yaklaşımla de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22144-118">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="22144-119">Aynı sınıfları ve bazı durumlarda aynı yöntemleri kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="22144-119">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="22144-120">Ancak, iki yaklaşımın yapısı ve amaçları farklıdır.</span><span class="sxs-lookup"><span data-stu-id="22144-120">However, the structure and goals of the two approaches are different.</span></span> <span data-ttu-id="22144-121">Örneğin, farklı durumlarda, bir veya diğer yaklaşım genellikle daha iyi performansa sahip olur ve daha fazla veya daha az bellek kullanır.</span><span class="sxs-lookup"><span data-stu-id="22144-121">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="22144-122">Buna ek olarak, bir veya başka bir yaklaşım daha fazla erişilebilir kod yazmak ve sağlamak daha kolay olacaktır.</span><span class="sxs-lookup"><span data-stu-id="22144-122">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>

<span data-ttu-id="22144-123">Bu iki yaklaşımı görmek için bkz. [bellek ıçı XML ağacı değişikliği ve işlevsel oluşturma](in-memory-xml-tree-modification-vs-functional-construction.md).</span><span class="sxs-lookup"><span data-stu-id="22144-123">To see the two approaches contrasted, see [In-memory XML tree modification vs. functional construction](in-memory-xml-tree-modification-vs-functional-construction.md).</span></span>

<span data-ttu-id="22144-124">İşlev dönüşümleri yazma hakkında bir öğretici için bkz. [saf işlevsel dönüşümlere giriş](introduction-pure-functional-transformations.md).</span><span class="sxs-lookup"><span data-stu-id="22144-124">For a tutorial on writing functional transformations, see [Introduction to pure functional transformations](introduction-pure-functional-transformations.md).</span></span>
