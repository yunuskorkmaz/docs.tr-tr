---
title: Sorgu anahtar kelimeleri - C# Referans
ms.date: 07/20/2015
helpviewer_keywords:
- query keywords [C#]
- LINQ [C#], query keywords
ms.assetid: 6c9bec16-dbd7-4a7c-a060-fe4600b2021f
ms.openlocfilehash: 01134eda540c5141afbd11b2c89ff779da495a9a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173529"
---
# <a name="query-keywords-c-reference"></a><span data-ttu-id="b94a8-102">Sorgu anahtar kelimeleri (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="b94a8-102">Query keywords (C# Reference)</span></span>

<span data-ttu-id="b94a8-103">Bu bölümde sorgu ifadelerinde kullanılan bağlamsal anahtar kelimeler bulunur.</span><span class="sxs-lookup"><span data-stu-id="b94a8-103">This section contains the contextual keywords used in query expressions.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="b94a8-104">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="b94a8-104">In this section</span></span>

|<span data-ttu-id="b94a8-105">Yan Tümce</span><span class="sxs-lookup"><span data-stu-id="b94a8-105">Clause</span></span>|<span data-ttu-id="b94a8-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b94a8-106">Description</span></span>|
|------------|-----------------|
|[<span data-ttu-id="b94a8-107">Kaynak</span><span class="sxs-lookup"><span data-stu-id="b94a8-107">from</span></span>](from-clause.md)|<span data-ttu-id="b94a8-108">Bir veri kaynağı ve bir aralık değişkeni (yineleme değişkenine benzer) belirtir.</span><span class="sxs-lookup"><span data-stu-id="b94a8-108">Specifies a data source and a range variable (similar to an iteration variable).</span></span>|
|[<span data-ttu-id="b94a8-109">Nerede</span><span class="sxs-lookup"><span data-stu-id="b94a8-109">where</span></span>](where-clause.md)|<span data-ttu-id="b94a8-110">Kaynak öğelerini mantıksal VE ve OR işleçleri (veya) `&&` <code>&#124;&#124;</code> tarafından ayrılmış bir veya daha fazla Boolean ifadesini temel alır.</span><span class="sxs-lookup"><span data-stu-id="b94a8-110">Filters source elements based on one or more Boolean expressions separated by logical AND and OR operators ( `&&` or <code>&#124;&#124;</code> ).</span></span>|
|[<span data-ttu-id="b94a8-111">Seçin</span><span class="sxs-lookup"><span data-stu-id="b94a8-111">select</span></span>](select-clause.md)|<span data-ttu-id="b94a8-112">Sorgu yürütüldüğünde döndürülen dizideki öğelerin sahip olacağı türü ve şekli belirtir.</span><span class="sxs-lookup"><span data-stu-id="b94a8-112">Specifies the type and shape that the elements in the returned sequence will have when the query is executed.</span></span>|
|[<span data-ttu-id="b94a8-113">grup</span><span class="sxs-lookup"><span data-stu-id="b94a8-113">group</span></span>](group-clause.md)|<span data-ttu-id="b94a8-114">Grupları sorgu sonuçları belirtilen bir anahtar değerine göre.</span><span class="sxs-lookup"><span data-stu-id="b94a8-114">Groups query results according to a specified key value.</span></span>|
|[<span data-ttu-id="b94a8-115">içine</span><span class="sxs-lookup"><span data-stu-id="b94a8-115">into</span></span>](into.md)|<span data-ttu-id="b94a8-116">Birbirle, grupla veya seç yan tümcesinin sonuçlarına başvuru olarak hizmet verebilecek bir tanımlayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b94a8-116">Provides an identifier that can serve as a reference to the results of a join, group or select clause.</span></span>|
|[<span data-ttu-id="b94a8-117">Orderby</span><span class="sxs-lookup"><span data-stu-id="b94a8-117">orderby</span></span>](orderby-clause.md)|<span data-ttu-id="b94a8-118">Sorgu sonuçlarını, öğe türü için varsayılan karşılayıcıyı temel alan artan veya azalan sırada sıralar.</span><span class="sxs-lookup"><span data-stu-id="b94a8-118">Sorts query results in ascending or descending order based on the default comparer for the element type.</span></span>|
|[<span data-ttu-id="b94a8-119">Katılın</span><span class="sxs-lookup"><span data-stu-id="b94a8-119">join</span></span>](join-clause.md)|<span data-ttu-id="b94a8-120">İki veri kaynağını, belirtilen iki eşleşen ölçüt arasındaki eşitlik karşılaştırması temel alınabın.</span><span class="sxs-lookup"><span data-stu-id="b94a8-120">Joins two data sources based on an equality comparison between two specified matching criteria.</span></span>|
|[<span data-ttu-id="b94a8-121">Izin</span><span class="sxs-lookup"><span data-stu-id="b94a8-121">let</span></span>](let-clause.md)|<span data-ttu-id="b94a8-122">Bir sorgu ifadesinde alt ifade sonuçlarını depolamak için bir aralık değişkeni tanır.</span><span class="sxs-lookup"><span data-stu-id="b94a8-122">Introduces a range variable to store sub-expression results in a query expression.</span></span>|
|[<span data-ttu-id="b94a8-123">Inç</span><span class="sxs-lookup"><span data-stu-id="b94a8-123">in</span></span>](in.md)|<span data-ttu-id="b94a8-124">[Birleştirme](join-clause.md) yan tümcesindeki bağlamsal anahtar kelime.</span><span class="sxs-lookup"><span data-stu-id="b94a8-124">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="b94a8-125">-ını</span><span class="sxs-lookup"><span data-stu-id="b94a8-125">on</span></span>](on.md)|<span data-ttu-id="b94a8-126">[Birleştirme](join-clause.md) yan tümcesindeki bağlamsal anahtar kelime.</span><span class="sxs-lookup"><span data-stu-id="b94a8-126">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="b94a8-127">equals</span><span class="sxs-lookup"><span data-stu-id="b94a8-127">equals</span></span>](equals.md)|<span data-ttu-id="b94a8-128">[Birleştirme](join-clause.md) yan tümcesindeki bağlamsal anahtar kelime.</span><span class="sxs-lookup"><span data-stu-id="b94a8-128">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="b94a8-129">Tarafından</span><span class="sxs-lookup"><span data-stu-id="b94a8-129">by</span></span>](by.md)|<span data-ttu-id="b94a8-130">[Grup](group-clause.md) yan tümcesindeki bağlamsal anahtar kelime.</span><span class="sxs-lookup"><span data-stu-id="b94a8-130">Contextual keyword in a [group](group-clause.md) clause.</span></span>|
|[<span data-ttu-id="b94a8-131">ascending</span><span class="sxs-lookup"><span data-stu-id="b94a8-131">ascending</span></span>](ascending.md)|<span data-ttu-id="b94a8-132">[Sıralı](orderby-clause.md) yan tümcedeki bağlamsal anahtar kelime.</span><span class="sxs-lookup"><span data-stu-id="b94a8-132">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|
|[<span data-ttu-id="b94a8-133">descending</span><span class="sxs-lookup"><span data-stu-id="b94a8-133">descending</span></span>](descending.md)|<span data-ttu-id="b94a8-134">[Sıralı](orderby-clause.md) yan tümcedeki bağlamsal anahtar kelime.</span><span class="sxs-lookup"><span data-stu-id="b94a8-134">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|

## <a name="see-also"></a><span data-ttu-id="b94a8-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b94a8-135">See also</span></span>

- [<span data-ttu-id="b94a8-136">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="b94a8-136">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b94a8-137">LINQ (Dil-Entegre Sorgu)</span><span class="sxs-lookup"><span data-stu-id="b94a8-137">LINQ (Language-Integrated Query)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="b94a8-138">C# üzerinde LINQ</span><span class="sxs-lookup"><span data-stu-id="b94a8-138">LINQ in C#</span></span>](../../linq/index.md)
