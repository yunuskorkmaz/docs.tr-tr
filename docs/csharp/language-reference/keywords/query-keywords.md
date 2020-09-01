---
description: Sorgu anahtar sözcükleri-C# başvurusu
title: Sorgu anahtar sözcükleri-C# başvurusu
ms.date: 07/20/2015
helpviewer_keywords:
- query keywords [C#]
- LINQ [C#], query keywords
ms.assetid: 6c9bec16-dbd7-4a7c-a060-fe4600b2021f
ms.openlocfilehash: 0beea8634d13222aa18f14d79fdbd95a35cc832e
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137142"
---
# <a name="query-keywords-c-reference"></a><span data-ttu-id="048c1-103">Sorgu anahtar sözcükleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="048c1-103">Query keywords (C# Reference)</span></span>

<span data-ttu-id="048c1-104">Bu bölüm sorgu ifadelerinde kullanılan bağlamsal anahtar sözcüklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="048c1-104">This section contains the contextual keywords used in query expressions.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="048c1-105">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="048c1-105">In this section</span></span>

|<span data-ttu-id="048c1-106">Yan Tümce</span><span class="sxs-lookup"><span data-stu-id="048c1-106">Clause</span></span>|<span data-ttu-id="048c1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="048c1-107">Description</span></span>|
|------------|-----------------|
|[<span data-ttu-id="048c1-108">Kaynak</span><span class="sxs-lookup"><span data-stu-id="048c1-108">from</span></span>](from-clause.md)|<span data-ttu-id="048c1-109">Bir veri kaynağını ve bir Aralık değişkenini (yineleme değişkenine benzer) belirtir.</span><span class="sxs-lookup"><span data-stu-id="048c1-109">Specifies a data source and a range variable (similar to an iteration variable).</span></span>|
|[<span data-ttu-id="048c1-110">olmadığı</span><span class="sxs-lookup"><span data-stu-id="048c1-110">where</span></span>](where-clause.md)|<span data-ttu-id="048c1-111">Mantıksal ve ve veya işleçlerle (veya) ayrılmış bir veya daha fazla Boole ifadesine göre kaynak öğelerine filtre uygular `&&` <code>&#124;&#124;</code> .</span><span class="sxs-lookup"><span data-stu-id="048c1-111">Filters source elements based on one or more Boolean expressions separated by logical AND and OR operators ( `&&` or <code>&#124;&#124;</code> ).</span></span>|
|[<span data-ttu-id="048c1-112">seçin</span><span class="sxs-lookup"><span data-stu-id="048c1-112">select</span></span>](select-clause.md)|<span data-ttu-id="048c1-113">Sorgu yürütüldüğünde döndürülen dizideki öğelerin sahip olacağı türü ve şekli belirtir.</span><span class="sxs-lookup"><span data-stu-id="048c1-113">Specifies the type and shape that the elements in the returned sequence will have when the query is executed.</span></span>|
|[<span data-ttu-id="048c1-114">grup</span><span class="sxs-lookup"><span data-stu-id="048c1-114">group</span></span>](group-clause.md)|<span data-ttu-id="048c1-115">Sorgu sonuçlarını belirtilen bir anahtar değerine göre gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="048c1-115">Groups query results according to a specified key value.</span></span>|
|[<span data-ttu-id="048c1-116">birleştirin</span><span class="sxs-lookup"><span data-stu-id="048c1-116">into</span></span>](into.md)|<span data-ttu-id="048c1-117">JOIN, Group veya Select yan tümcesinin sonuçlarına başvuru olarak sunacak bir tanımlayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="048c1-117">Provides an identifier that can serve as a reference to the results of a join, group or select clause.</span></span>|
|[<span data-ttu-id="048c1-118">OrderBy</span><span class="sxs-lookup"><span data-stu-id="048c1-118">orderby</span></span>](orderby-clause.md)|<span data-ttu-id="048c1-119">Sorgu sonuçlarını, öğe türünün varsayılan karşılaştırmasına göre artan veya azalan düzende sıralar.</span><span class="sxs-lookup"><span data-stu-id="048c1-119">Sorts query results in ascending or descending order based on the default comparer for the element type.</span></span>|
|[<span data-ttu-id="048c1-120">ayrılma</span><span class="sxs-lookup"><span data-stu-id="048c1-120">join</span></span>](join-clause.md)|<span data-ttu-id="048c1-121">İki veri kaynağını belirtilen iki eşleşen ölçüt arasında bir eşitlik karşılaştırması temelinde birleştirir.</span><span class="sxs-lookup"><span data-stu-id="048c1-121">Joins two data sources based on an equality comparison between two specified matching criteria.</span></span>|
|[<span data-ttu-id="048c1-122">atalım</span><span class="sxs-lookup"><span data-stu-id="048c1-122">let</span></span>](let-clause.md)|<span data-ttu-id="048c1-123">Bir sorgu ifadesinde alt ifade sonuçlarının depolanması için bir Aralık değişkeni tanıtır.</span><span class="sxs-lookup"><span data-stu-id="048c1-123">Introduces a range variable to store sub-expression results in a query expression.</span></span>|
|[<span data-ttu-id="048c1-124">'ndaki</span><span class="sxs-lookup"><span data-stu-id="048c1-124">in</span></span>](in.md)|<span data-ttu-id="048c1-125">[JOIN](join-clause.md) yan tümcesinde bağlamsal anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="048c1-125">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="048c1-126">dayanır</span><span class="sxs-lookup"><span data-stu-id="048c1-126">on</span></span>](on.md)|<span data-ttu-id="048c1-127">[JOIN](join-clause.md) yan tümcesinde bağlamsal anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="048c1-127">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="048c1-128">equals</span><span class="sxs-lookup"><span data-stu-id="048c1-128">equals</span></span>](equals.md)|<span data-ttu-id="048c1-129">[JOIN](join-clause.md) yan tümcesinde bağlamsal anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="048c1-129">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="048c1-130">by</span><span class="sxs-lookup"><span data-stu-id="048c1-130">by</span></span>](by.md)|<span data-ttu-id="048c1-131">Bir [Group](group-clause.md) yan tümcesindeki bağlamsal anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="048c1-131">Contextual keyword in a [group](group-clause.md) clause.</span></span>|
|[<span data-ttu-id="048c1-132">ascending</span><span class="sxs-lookup"><span data-stu-id="048c1-132">ascending</span></span>](ascending.md)|<span data-ttu-id="048c1-133">Bir [OrderBy](orderby-clause.md) yan tümcesindeki bağlamsal anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="048c1-133">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|
|[<span data-ttu-id="048c1-134">descending</span><span class="sxs-lookup"><span data-stu-id="048c1-134">descending</span></span>](descending.md)|<span data-ttu-id="048c1-135">Bir [OrderBy](orderby-clause.md) yan tümcesindeki bağlamsal anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="048c1-135">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|

## <a name="see-also"></a><span data-ttu-id="048c1-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="048c1-136">See also</span></span>

- [<span data-ttu-id="048c1-137">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="048c1-137">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="048c1-138">LINQ (dil ile tümleşik sorgu)</span><span class="sxs-lookup"><span data-stu-id="048c1-138">LINQ (Language-Integrated Query)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="048c1-139">C# üzerinde LINQ</span><span class="sxs-lookup"><span data-stu-id="048c1-139">LINQ in C#</span></span>](../../linq/index.md)
