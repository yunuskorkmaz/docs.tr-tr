---
title: Parametreler
ms.date: 12/13/2019
description: SQL parametrelerini nasıl kullanacağınızı öğrenin.
ms.openlocfilehash: 1d2f818ad392a919faedd785394de28a9c6f56c3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447190"
---
# <a name="parameters"></a><span data-ttu-id="3b7cc-103">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3b7cc-103">Parameters</span></span>

<span data-ttu-id="3b7cc-104">Parametreleri SQL ekleme saldırılarına karşı korumak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-104">Parameters are used to protect against SQL injection attacks.</span></span> <span data-ttu-id="3b7cc-105">Kullanıcı girişini SQL deyimleriyle birleştirerek, girişin yalnızca bir sabit değer olarak değerlendirildiğinden ve hiçbir zaman yürütüldüğünden emin olmak için parametreleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-105">Instead of concatenating user input with SQL statements, use parameters to ensure input is only ever treated as a literal value and never executed.</span></span> <span data-ttu-id="3b7cc-106">SQLite 'ta, parametrelere genellikle SQL deyimlerde bir sabit değere izin verilen her yerde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-106">In SQLite, parameters are typically allowed anywhere a literal is allowed in SQL statements.</span></span>

<span data-ttu-id="3b7cc-107">Parametrelere `:`, `@`veya `$`ön eki uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-107">Parameters can be prefixed with either `:`, `@`, or `$`.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_Parameter)]

<span data-ttu-id="3b7cc-108">.NET değerlerinin SQLite değerlerine nasıl eşlendiğine ilişkin ayrıntılar için bkz. [veri türleri](types.md) .</span><span class="sxs-lookup"><span data-stu-id="3b7cc-108">See [Data types](types.md) for details about how .NET values are mapped to SQLite values.</span></span>

## <a name="truncation"></a><span data-ttu-id="3b7cc-109">Kesildi</span><span class="sxs-lookup"><span data-stu-id="3b7cc-109">Truncation</span></span>

<span data-ttu-id="3b7cc-110">METIN ve BLOB değerlerini kesmek için <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-110">Use the <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> property to truncate TEXT and BLOB values.</span></span>

```csharp
// Truncate name to 30 characters
command.Parameters.AddWithValue("$name", name).Length = 30;
```

## <a name="alternative-types"></a><span data-ttu-id="3b7cc-111">Alternatif türler</span><span class="sxs-lookup"><span data-stu-id="3b7cc-111">Alternative types</span></span>

<span data-ttu-id="3b7cc-112">Bazen alternatif bir SQLite türü kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-112">Sometimes, you may want to use an alternative SQLite type.</span></span> <span data-ttu-id="3b7cc-113"><xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType> özelliğini ayarlayarak bunu yapın.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-113">Do this by setting the <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType> property.</span></span>

<span data-ttu-id="3b7cc-114">Aşağıdaki alternatif tür eşlemeleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-114">The following alternative type mappings can be used.</span></span> <span data-ttu-id="3b7cc-115">Varsayılan eşlemeler için bkz. [veri türleri](types.md).</span><span class="sxs-lookup"><span data-stu-id="3b7cc-115">For the default mappings, see [Data types](types.md).</span></span>

| <span data-ttu-id="3b7cc-116">Değer</span><span class="sxs-lookup"><span data-stu-id="3b7cc-116">Value</span></span>          | <span data-ttu-id="3b7cc-117">SqliteType</span><span class="sxs-lookup"><span data-stu-id="3b7cc-117">SqliteType</span></span> | <span data-ttu-id="3b7cc-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3b7cc-118">Remarks</span></span>          |
| -------------- | ---------- | ---------------- |
| <span data-ttu-id="3b7cc-119">Char</span><span class="sxs-lookup"><span data-stu-id="3b7cc-119">Char</span></span>           | <span data-ttu-id="3b7cc-120">Tamsayı</span><span class="sxs-lookup"><span data-stu-id="3b7cc-120">Integer</span></span>    | <span data-ttu-id="3b7cc-121">UTF-16</span><span class="sxs-lookup"><span data-stu-id="3b7cc-121">UTF-16</span></span>           |
| <span data-ttu-id="3b7cc-122">DateTime</span><span class="sxs-lookup"><span data-stu-id="3b7cc-122">DateTime</span></span>       | <span data-ttu-id="3b7cc-123">Gerçek</span><span class="sxs-lookup"><span data-stu-id="3b7cc-123">Real</span></span>       | <span data-ttu-id="3b7cc-124">Jülyen gün değeri</span><span class="sxs-lookup"><span data-stu-id="3b7cc-124">Julian day value</span></span> |
| <span data-ttu-id="3b7cc-125">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="3b7cc-125">DateTimeOffset</span></span> | <span data-ttu-id="3b7cc-126">Gerçek</span><span class="sxs-lookup"><span data-stu-id="3b7cc-126">Real</span></span>       | <span data-ttu-id="3b7cc-127">Jülyen gün değeri</span><span class="sxs-lookup"><span data-stu-id="3b7cc-127">Julian day value</span></span> |
| <span data-ttu-id="3b7cc-128">Guid</span><span class="sxs-lookup"><span data-stu-id="3b7cc-128">Guid</span></span>           | <span data-ttu-id="3b7cc-129">Blob</span><span class="sxs-lookup"><span data-stu-id="3b7cc-129">Blob</span></span>       |                  |
| <span data-ttu-id="3b7cc-130">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="3b7cc-130">TimeSpan</span></span>       | <span data-ttu-id="3b7cc-131">Gerçek</span><span class="sxs-lookup"><span data-stu-id="3b7cc-131">Real</span></span>       | <span data-ttu-id="3b7cc-132">Gün cinsinden</span><span class="sxs-lookup"><span data-stu-id="3b7cc-132">In days</span></span>          |

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_SqliteType)]

## <a name="output-parameters"></a><span data-ttu-id="3b7cc-133">Çıktı parametreleri</span><span class="sxs-lookup"><span data-stu-id="3b7cc-133">Output parameters</span></span>

<span data-ttu-id="3b7cc-134">SQLite çıkış parametrelerini desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-134">SQLite doesn't support output parameters.</span></span> <span data-ttu-id="3b7cc-135">Bunun yerine sorgu sonuçlarındaki değerleri döndürün.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-135">Return values in the query results instead.</span></span>

## <a name="see-also"></a><span data-ttu-id="3b7cc-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b7cc-136">See also</span></span>

* [<span data-ttu-id="3b7cc-137">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="3b7cc-137">Data types</span></span>](types.md)
