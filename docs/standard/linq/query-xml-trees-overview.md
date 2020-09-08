---
title: Sorgu XML ağaçlarını genel bakış-LINQ to XML
description: Bir XML ağacını sorgulamayı ve bir ağacı yeniden şekillendirmek için sorgulama ve işlevsel oluşturmayı birleştirmeyi öğrenin.
ms.date: 07/20/2015
ms.assetid: 2e35c1ab-08c8-4378-9ca8-8ff344756eda
ms.openlocfilehash: 3529650aa5ee0575331653f5714c841d1fc1dfb5
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553893"
---
# <a name="query-xml-trees-overview-linq-to-xml"></a><span data-ttu-id="4cf27-103">Sorgu XML ağaçlarına genel bakış (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="4cf27-103">Query XML trees overview (LINQ to XML)</span></span>

<span data-ttu-id="4cf27-104">Bir XML ağacı örnekledikten sonra, verileri yazma, ağaçtan veri ayıklamaya yönelik en etkili yoldur.</span><span class="sxs-lookup"><span data-stu-id="4cf27-104">After you've instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="4cf27-105">Ayrıca, işlevsel oluşturma ile birlikte sorgulama, orijinal belgeden farklı bir şekle sahip yeni bir XML belgesi oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="4cf27-105">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>

<span data-ttu-id="4cf27-106">LINQ sorguları hakkında arka plan bilgileri için bkz.:</span><span class="sxs-lookup"><span data-stu-id="4cf27-106">For background information about LINQ queries, see:</span></span>

- [<span data-ttu-id="4cf27-107">LINQ Sorgularına Giriş (C#)</span><span class="sxs-lookup"><span data-stu-id="4cf27-107">Introduction to LINQ Queries (C#)</span></span>](../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)
- [<span data-ttu-id="4cf27-108">İlk LINQ Sorgunuzu Yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4cf27-108">Writing Your First LINQ Query (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)

## <a name="in-this-section"></a><span data-ttu-id="4cf27-109">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="4cf27-109">In this section</span></span>

<span data-ttu-id="4cf27-110">Makalelerin bu bölümü, LINQ to XML sorguları hakkında örnekler de dahil olmak üzere bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4cf27-110">This section of articles provides information, including examples, about LINQ to XML queries.</span></span> <span data-ttu-id="4cf27-111">Aşağıdaki alt bölümleri içerir:</span><span class="sxs-lookup"><span data-stu-id="4cf27-111">It comprises the following subsections:</span></span>

|<span data-ttu-id="4cf27-112">Makale</span><span class="sxs-lookup"><span data-stu-id="4cf27-112">Article</span></span>|<span data-ttu-id="4cf27-113">Description</span><span class="sxs-lookup"><span data-stu-id="4cf27-113">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="4cf27-114">Temel sorgular</span><span class="sxs-lookup"><span data-stu-id="4cf27-114">Basic queries</span></span>](find-element-specific-attribute.md)|<span data-ttu-id="4cf27-115">XML ağaçlarının sorgulanmasına ilişkin yaygın örnekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4cf27-115">Provides common examples of querying XML trees.</span></span>|
|[<span data-ttu-id="4cf27-116">Tahminler ve dönüşümler</span><span class="sxs-lookup"><span data-stu-id="4cf27-116">Projections and transformations</span></span>](work-dictionaries-linq-xml.md)|<span data-ttu-id="4cf27-117">XML ağaçlarını yansıtma ve dönüştürme yaygın örneklerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="4cf27-117">Provides common examples of projecting from and transforming XML trees.</span></span>|
|[<span data-ttu-id="4cf27-118">Gelişmiş sorgu teknikleri</span><span class="sxs-lookup"><span data-stu-id="4cf27-118">Advanced query techniques</span></span>](join-two-collections.md)|<span data-ttu-id="4cf27-119">Daha Gelişmiş senaryolarda yararlı olan sorgu teknikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="4cf27-119">Provides query techniques that are useful in more advanced scenarios.</span></span>|
|[<span data-ttu-id="4cf27-120">XPath kullanıcıları için LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="4cf27-120">LINQ to XML for XPath users</span></span>](comparison-xpath-linq-xml.md)|<span data-ttu-id="4cf27-121">Bir dizi XPath ifadesi ve bunların LINQ to XML eşdeğerlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4cf27-121">Presents a number of XPath expressions and their LINQ to XML equivalents.</span></span>|
|[<span data-ttu-id="4cf27-122">Saf işlevsel dönüşümlere giriş</span><span class="sxs-lookup"><span data-stu-id="4cf27-122">Introduction to pure functional transformations</span></span>](introduction-pure-functional-transformations.md)|<span data-ttu-id="4cf27-123">İşlevsel programlama stilinde sorgu yazma konusunda küçük bir öğretici sunar.</span><span class="sxs-lookup"><span data-stu-id="4cf27-123">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|

## <a name="see-also"></a><span data-ttu-id="4cf27-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4cf27-124">See also</span></span>

- [<span data-ttu-id="4cf27-125">Dil ile tümleşik sorgu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="4cf27-125">Language-Integrated Query (LINQ) (C#)</span></span>](../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="4cf27-126">LINQ Sorgularına Giriş (C#)</span><span class="sxs-lookup"><span data-stu-id="4cf27-126">Introduction to LINQ Queries (C#)</span></span>](../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)
- [<span data-ttu-id="4cf27-127">Visual Basic'de LINQ</span><span class="sxs-lookup"><span data-stu-id="4cf27-127">LINQ in Visual Basic</span></span>](../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="4cf27-128">Dil ile tümleşik sorgu (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4cf27-128">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="4cf27-129">Visual Basic'te LINQ'e Başlarken</span><span class="sxs-lookup"><span data-stu-id="4cf27-129">Getting Started with LINQ in Visual Basic</span></span>](../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="4cf27-130">İlk LINQ Sorgunuzu Yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4cf27-130">Writing Your First LINQ Query (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)
