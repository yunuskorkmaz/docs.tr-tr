---
title: Sorgu anahtar sözcükleri C# -başvuru
ms.date: 07/20/2015
helpviewer_keywords:
- query keywords [C#]
- LINQ [C#], query keywords
ms.assetid: 6c9bec16-dbd7-4a7c-a060-fe4600b2021f
ms.openlocfilehash: 3c08c2b6ecdaa4b875f118531e7e77f7164dd784
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713163"
---
# <a name="query-keywords-c-reference"></a><span data-ttu-id="d7c44-102">Sorgu anahtar sözcükleriC# (başvuru)</span><span class="sxs-lookup"><span data-stu-id="d7c44-102">Query keywords (C# Reference)</span></span>

<span data-ttu-id="d7c44-103">Bu bölüm sorgu ifadelerinde kullanılan bağlamsal anahtar sözcüklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="d7c44-103">This section contains the contextual keywords used in query expressions.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d7c44-104">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="d7c44-104">In this section</span></span>

|<span data-ttu-id="d7c44-105">Yan Tümce</span><span class="sxs-lookup"><span data-stu-id="d7c44-105">Clause</span></span>|<span data-ttu-id="d7c44-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d7c44-106">Description</span></span>|
|------------|-----------------|
|[<span data-ttu-id="d7c44-107">from</span><span class="sxs-lookup"><span data-stu-id="d7c44-107">from</span></span>](from-clause.md)|<span data-ttu-id="d7c44-108">Bir veri kaynağını ve bir Aralık değişkenini (yineleme değişkenine benzer) belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7c44-108">Specifies a data source and a range variable (similar to an iteration variable).</span></span>|
|[<span data-ttu-id="d7c44-109">olmadığı</span><span class="sxs-lookup"><span data-stu-id="d7c44-109">where</span></span>](where-clause.md)|<span data-ttu-id="d7c44-110">Mantıksal ve ve veya işleçlerle (`&&` veya <code>&#124;&#124;</code>) ayrılmış bir veya daha fazla Boole ifadesine göre kaynak öğelerine filtre uygular.</span><span class="sxs-lookup"><span data-stu-id="d7c44-110">Filters source elements based on one or more Boolean expressions separated by logical AND and OR operators ( `&&` or <code>&#124;&#124;</code> ).</span></span>|
|[<span data-ttu-id="d7c44-111">seçin</span><span class="sxs-lookup"><span data-stu-id="d7c44-111">select</span></span>](select-clause.md)|<span data-ttu-id="d7c44-112">Sorgu yürütüldüğünde döndürülen dizideki öğelerin sahip olacağı türü ve şekli belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7c44-112">Specifies the type and shape that the elements in the returned sequence will have when the query is executed.</span></span>|
|[<span data-ttu-id="d7c44-113">grubu</span><span class="sxs-lookup"><span data-stu-id="d7c44-113">group</span></span>](group-clause.md)|<span data-ttu-id="d7c44-114">Sorgu sonuçlarını belirtilen bir anahtar değerine göre gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="d7c44-114">Groups query results according to a specified key value.</span></span>|
|[<span data-ttu-id="d7c44-115">into</span><span class="sxs-lookup"><span data-stu-id="d7c44-115">into</span></span>](into.md)|<span data-ttu-id="d7c44-116">JOIN, Group veya Select yan tümcesinin sonuçlarına başvuru olarak sunacak bir tanımlayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d7c44-116">Provides an identifier that can serve as a reference to the results of a join, group or select clause.</span></span>|
|[<span data-ttu-id="d7c44-117">OrderBy</span><span class="sxs-lookup"><span data-stu-id="d7c44-117">orderby</span></span>](orderby-clause.md)|<span data-ttu-id="d7c44-118">Sorgu sonuçlarını, öğe türünün varsayılan karşılaştırmasına göre artan veya azalan düzende sıralar.</span><span class="sxs-lookup"><span data-stu-id="d7c44-118">Sorts query results in ascending or descending order based on the default comparer for the element type.</span></span>|
|[<span data-ttu-id="d7c44-119">join</span><span class="sxs-lookup"><span data-stu-id="d7c44-119">join</span></span>](join-clause.md)|<span data-ttu-id="d7c44-120">İki veri kaynağını belirtilen iki eşleşen ölçüt arasında bir eşitlik karşılaştırması temelinde birleştirir.</span><span class="sxs-lookup"><span data-stu-id="d7c44-120">Joins two data sources based on an equality comparison between two specified matching criteria.</span></span>|
|[<span data-ttu-id="d7c44-121">atalım</span><span class="sxs-lookup"><span data-stu-id="d7c44-121">let</span></span>](let-clause.md)|<span data-ttu-id="d7c44-122">Bir sorgu ifadesinde alt ifade sonuçlarının depolanması için bir Aralık değişkeni tanıtır.</span><span class="sxs-lookup"><span data-stu-id="d7c44-122">Introduces a range variable to store sub-expression results in a query expression.</span></span>|
|[<span data-ttu-id="d7c44-123">in</span><span class="sxs-lookup"><span data-stu-id="d7c44-123">in</span></span>](in.md)|<span data-ttu-id="d7c44-124">[JOIN](join-clause.md) yan tümcesinde bağlamsal anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="d7c44-124">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="d7c44-125">on</span><span class="sxs-lookup"><span data-stu-id="d7c44-125">on</span></span>](on.md)|<span data-ttu-id="d7c44-126">[JOIN](join-clause.md) yan tümcesinde bağlamsal anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="d7c44-126">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="d7c44-127">equals</span><span class="sxs-lookup"><span data-stu-id="d7c44-127">equals</span></span>](equals.md)|<span data-ttu-id="d7c44-128">[JOIN](join-clause.md) yan tümcesinde bağlamsal anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="d7c44-128">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="d7c44-129">by</span><span class="sxs-lookup"><span data-stu-id="d7c44-129">by</span></span>](by.md)|<span data-ttu-id="d7c44-130">Bir [Group](group-clause.md) yan tümcesindeki bağlamsal anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="d7c44-130">Contextual keyword in a [group](group-clause.md) clause.</span></span>|
|[<span data-ttu-id="d7c44-131">ascending</span><span class="sxs-lookup"><span data-stu-id="d7c44-131">ascending</span></span>](ascending.md)|<span data-ttu-id="d7c44-132">Bir [OrderBy](orderby-clause.md) yan tümcesindeki bağlamsal anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="d7c44-132">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|
|[<span data-ttu-id="d7c44-133">descending</span><span class="sxs-lookup"><span data-stu-id="d7c44-133">descending</span></span>](descending.md)|<span data-ttu-id="d7c44-134">Bir [OrderBy](orderby-clause.md) yan tümcesindeki bağlamsal anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="d7c44-134">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|

## <a name="see-also"></a><span data-ttu-id="d7c44-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7c44-135">See also</span></span>

- [<span data-ttu-id="d7c44-136">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="d7c44-136">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="d7c44-137">LINQ (dil ile tümleşik sorgu)</span><span class="sxs-lookup"><span data-stu-id="d7c44-137">LINQ (Language-Integrated Query)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="d7c44-138">C# üzerinde LINQ</span><span class="sxs-lookup"><span data-stu-id="d7c44-138">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="d7c44-139">C#'de LINQ Kullanmaya Başlama</span><span class="sxs-lookup"><span data-stu-id="d7c44-139">Getting Started with LINQ in C#</span></span>](/dotnet/csharp/programming-guide/concepts/linq/)
