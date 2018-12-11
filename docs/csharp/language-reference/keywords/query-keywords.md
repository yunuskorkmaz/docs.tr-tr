---
title: Sorgu anahtar sözcükleri - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- query keywords [C#]
- LINQ [C#], query keywords
ms.assetid: 6c9bec16-dbd7-4a7c-a060-fe4600b2021f
ms.openlocfilehash: e5010c7e9f3550c79c86c6cab4579a0fb15eef10
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239491"
---
# <a name="query-keywords-c-reference"></a><span data-ttu-id="1a11e-102">Sorgu anahtar sözcükleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1a11e-102">Query keywords (C# Reference)</span></span>

<span data-ttu-id="1a11e-103">Bu bölüm, sorgu ifadelerinde kullanılan bağlamsal anahtar sözcükler içerir.</span><span class="sxs-lookup"><span data-stu-id="1a11e-103">This section contains the contextual keywords used in query expressions.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="1a11e-104">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="1a11e-104">In this section</span></span>

|<span data-ttu-id="1a11e-105">Yan Tümce</span><span class="sxs-lookup"><span data-stu-id="1a11e-105">Clause</span></span>|<span data-ttu-id="1a11e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a11e-106">Description</span></span>|
|------------|-----------------|
|[<span data-ttu-id="1a11e-107">Kaynak</span><span class="sxs-lookup"><span data-stu-id="1a11e-107">from</span></span>](from-clause.md)|<span data-ttu-id="1a11e-108">Bir veri kaynağı ve bir aralık değişkenine (bir yineleme değişkeni için benzer şekilde) belirtir.</span><span class="sxs-lookup"><span data-stu-id="1a11e-108">Specifies a data source and a range variable (similar to an iteration variable).</span></span>|
|[<span data-ttu-id="1a11e-109">Burada</span><span class="sxs-lookup"><span data-stu-id="1a11e-109">where</span></span>](where-clause.md)|<span data-ttu-id="1a11e-110">İşleçler ve mantıksal AND tarafından ayrılmış bir veya daha fazla Boole ifadesine göre öğeleri filtreler kaynağı ( `&&` veya <code>&#124;&#124;</code> ).</span><span class="sxs-lookup"><span data-stu-id="1a11e-110">Filters source elements based on one or more Boolean expressions separated by logical AND and OR operators ( `&&` or <code>&#124;&#124;</code> ).</span></span>|
|[<span data-ttu-id="1a11e-111">Seçin</span><span class="sxs-lookup"><span data-stu-id="1a11e-111">select</span></span>](select-clause.md)|<span data-ttu-id="1a11e-112">Sorgu yürütüldüğünde, döndürülen dizideki öğelerin sahip şekli ve türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="1a11e-112">Specifies the type and shape that the elements in the returned sequence will have when the query is executed.</span></span>|
|[<span data-ttu-id="1a11e-113">Grup</span><span class="sxs-lookup"><span data-stu-id="1a11e-113">group</span></span>](group-clause.md)|<span data-ttu-id="1a11e-114">Belirtilen anahtar değere göre gruplar sorgu sonuçları.</span><span class="sxs-lookup"><span data-stu-id="1a11e-114">Groups query results according to a specified key value.</span></span>|
|[<span data-ttu-id="1a11e-115">into</span><span class="sxs-lookup"><span data-stu-id="1a11e-115">into</span></span>](into.md)|<span data-ttu-id="1a11e-116">Sonuçları birleştirme, Grup veya select yan tümcesi bir başvuru olarak hizmet verebilen bir tanımlayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1a11e-116">Provides an identifier that can serve as a reference to the results of a join, group or select clause.</span></span>|
|[<span data-ttu-id="1a11e-117">OrderBy</span><span class="sxs-lookup"><span data-stu-id="1a11e-117">orderby</span></span>](orderby-clause.md)|<span data-ttu-id="1a11e-118">Öğe türü için varsayılan karşılaştırıcı göre azalan veya artan düzende sıralar sorgu sonuçları.</span><span class="sxs-lookup"><span data-stu-id="1a11e-118">Sorts query results in ascending or descending order based on the default comparer for the element type.</span></span>|
|[<span data-ttu-id="1a11e-119">Katılın</span><span class="sxs-lookup"><span data-stu-id="1a11e-119">join</span></span>](join-clause.md)|<span data-ttu-id="1a11e-120">İki veri kaynağı bir eşitlik karşılaştırması iki belirtilen eşleşen ölçütlere göre birleştirir.</span><span class="sxs-lookup"><span data-stu-id="1a11e-120">Joins two data sources based on an equality comparison between two specified matching criteria.</span></span>|
|[<span data-ttu-id="1a11e-121">let</span><span class="sxs-lookup"><span data-stu-id="1a11e-121">let</span></span>](let-clause.md)|<span data-ttu-id="1a11e-122">Bir sorgu ifadesinde alt ifade sonuçlarını depolamak için bir aralık değişkenine getirir.</span><span class="sxs-lookup"><span data-stu-id="1a11e-122">Introduces a range variable to store sub-expression results in a query expression.</span></span>|
|[<span data-ttu-id="1a11e-123">in</span><span class="sxs-lookup"><span data-stu-id="1a11e-123">in</span></span>](in.md)|<span data-ttu-id="1a11e-124">İçindeki bağlamsal anahtar sözcüğü bir [birleştirme](join-clause.md) yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="1a11e-124">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="1a11e-125">on</span><span class="sxs-lookup"><span data-stu-id="1a11e-125">on</span></span>](on.md)|<span data-ttu-id="1a11e-126">İçindeki bağlamsal anahtar sözcüğü bir [birleştirme](join-clause.md) yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="1a11e-126">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="1a11e-127">equals</span><span class="sxs-lookup"><span data-stu-id="1a11e-127">equals</span></span>](equals.md)|<span data-ttu-id="1a11e-128">İçindeki bağlamsal anahtar sözcüğü bir [birleştirme](join-clause.md) yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="1a11e-128">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="1a11e-129">by</span><span class="sxs-lookup"><span data-stu-id="1a11e-129">by</span></span>](by.md)|<span data-ttu-id="1a11e-130">İçindeki bağlamsal anahtar sözcüğü bir [grubu](group-clause.md) yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="1a11e-130">Contextual keyword in a [group](group-clause.md) clause.</span></span>|
|[<span data-ttu-id="1a11e-131">ascending</span><span class="sxs-lookup"><span data-stu-id="1a11e-131">ascending</span></span>](ascending.md)|<span data-ttu-id="1a11e-132">İçindeki bağlamsal anahtar sözcüğü bir [orderby](orderby-clause.md) yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="1a11e-132">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|
|[<span data-ttu-id="1a11e-133">descending</span><span class="sxs-lookup"><span data-stu-id="1a11e-133">descending</span></span>](descending.md)|<span data-ttu-id="1a11e-134">İçindeki bağlamsal anahtar sözcüğü bir [orderby](orderby-clause.md) yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="1a11e-134">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|

## <a name="see-also"></a><span data-ttu-id="1a11e-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a11e-135">See also</span></span>

- [<span data-ttu-id="1a11e-136">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="1a11e-136">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1a11e-137">LINQ (dil ile tümleşik sorgu)</span><span class="sxs-lookup"><span data-stu-id="1a11e-137">LINQ (Language-Integrated Query)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="1a11e-138">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="1a11e-138">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)
- [<span data-ttu-id="1a11e-139">C#'de LINQ Kullanmaya Başlama</span><span class="sxs-lookup"><span data-stu-id="1a11e-139">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)