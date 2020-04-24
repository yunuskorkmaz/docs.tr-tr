---
title: Parametreler
ms.date: 12/13/2019
description: SQL parametrelerini nasıl kullanacağınızı öğrenin.
ms.openlocfilehash: 1d2f818ad392a919faedd785394de28a9c6f56c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400458"
---
# <a name="parameters"></a><span data-ttu-id="8d061-103">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8d061-103">Parameters</span></span>

<span data-ttu-id="8d061-104">Parametreleri SQL ekleme saldırılarına karşı korumak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8d061-104">Parameters are used to protect against SQL injection attacks.</span></span> <span data-ttu-id="8d061-105">Kullanıcı girişini SQL deyimleriyle birleştirerek, girişin yalnızca bir sabit değer olarak değerlendirildiğinden ve hiçbir zaman yürütüldüğünden emin olmak için parametreleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="8d061-105">Instead of concatenating user input with SQL statements, use parameters to ensure input is only ever treated as a literal value and never executed.</span></span> <span data-ttu-id="8d061-106">SQLite 'ta, parametrelere genellikle SQL deyimlerde bir sabit değere izin verilen her yerde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="8d061-106">In SQLite, parameters are typically allowed anywhere a literal is allowed in SQL statements.</span></span>

<span data-ttu-id="8d061-107">Parametrelere `:`, `@`ya `$`da ön eki uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="8d061-107">Parameters can be prefixed with either `:`, `@`, or `$`.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_Parameter)]

<span data-ttu-id="8d061-108">.NET değerlerinin SQLite değerlerine nasıl eşlendiğine ilişkin ayrıntılar için bkz. [veri türleri](types.md) .</span><span class="sxs-lookup"><span data-stu-id="8d061-108">See [Data types](types.md) for details about how .NET values are mapped to SQLite values.</span></span>

## <a name="truncation"></a><span data-ttu-id="8d061-109">Kesildi</span><span class="sxs-lookup"><span data-stu-id="8d061-109">Truncation</span></span>

<span data-ttu-id="8d061-110">METIN ve <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> blob değerlerini kesmek için özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8d061-110">Use the <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> property to truncate TEXT and BLOB values.</span></span>

```csharp
// Truncate name to 30 characters
command.Parameters.AddWithValue("$name", name).Length = 30;
```

## <a name="alternative-types"></a><span data-ttu-id="8d061-111">Alternatif türler</span><span class="sxs-lookup"><span data-stu-id="8d061-111">Alternative types</span></span>

<span data-ttu-id="8d061-112">Bazen alternatif bir SQLite türü kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d061-112">Sometimes, you may want to use an alternative SQLite type.</span></span> <span data-ttu-id="8d061-113"><xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType> Özelliği ayarlayarak bunu yapın.</span><span class="sxs-lookup"><span data-stu-id="8d061-113">Do this by setting the <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType> property.</span></span>

<span data-ttu-id="8d061-114">Aşağıdaki alternatif tür eşlemeleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8d061-114">The following alternative type mappings can be used.</span></span> <span data-ttu-id="8d061-115">Varsayılan eşlemeler için bkz. [veri türleri](types.md).</span><span class="sxs-lookup"><span data-stu-id="8d061-115">For the default mappings, see [Data types](types.md).</span></span>

| <span data-ttu-id="8d061-116">Değer</span><span class="sxs-lookup"><span data-stu-id="8d061-116">Value</span></span>          | <span data-ttu-id="8d061-117">SqliteType</span><span class="sxs-lookup"><span data-stu-id="8d061-117">SqliteType</span></span> | <span data-ttu-id="8d061-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8d061-118">Remarks</span></span>          |
| -------------- | ---------- | ---------------- |
| <span data-ttu-id="8d061-119">Char</span><span class="sxs-lookup"><span data-stu-id="8d061-119">Char</span></span>           | <span data-ttu-id="8d061-120">Tamsayı</span><span class="sxs-lookup"><span data-stu-id="8d061-120">Integer</span></span>    | <span data-ttu-id="8d061-121">UTF-16</span><span class="sxs-lookup"><span data-stu-id="8d061-121">UTF-16</span></span>           |
| <span data-ttu-id="8d061-122">DateTime</span><span class="sxs-lookup"><span data-stu-id="8d061-122">DateTime</span></span>       | <span data-ttu-id="8d061-123">Gerçek</span><span class="sxs-lookup"><span data-stu-id="8d061-123">Real</span></span>       | <span data-ttu-id="8d061-124">Jülyen gün değeri</span><span class="sxs-lookup"><span data-stu-id="8d061-124">Julian day value</span></span> |
| <span data-ttu-id="8d061-125">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="8d061-125">DateTimeOffset</span></span> | <span data-ttu-id="8d061-126">Gerçek</span><span class="sxs-lookup"><span data-stu-id="8d061-126">Real</span></span>       | <span data-ttu-id="8d061-127">Jülyen gün değeri</span><span class="sxs-lookup"><span data-stu-id="8d061-127">Julian day value</span></span> |
| <span data-ttu-id="8d061-128">Guid</span><span class="sxs-lookup"><span data-stu-id="8d061-128">Guid</span></span>           | <span data-ttu-id="8d061-129">Blob</span><span class="sxs-lookup"><span data-stu-id="8d061-129">Blob</span></span>       |                  |
| <span data-ttu-id="8d061-130">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="8d061-130">TimeSpan</span></span>       | <span data-ttu-id="8d061-131">Gerçek</span><span class="sxs-lookup"><span data-stu-id="8d061-131">Real</span></span>       | <span data-ttu-id="8d061-132">Gün cinsinden</span><span class="sxs-lookup"><span data-stu-id="8d061-132">In days</span></span>          |

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_SqliteType)]

## <a name="output-parameters"></a><span data-ttu-id="8d061-133">Çıktı parametreleri</span><span class="sxs-lookup"><span data-stu-id="8d061-133">Output parameters</span></span>

<span data-ttu-id="8d061-134">SQLite çıkış parametrelerini desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="8d061-134">SQLite doesn't support output parameters.</span></span> <span data-ttu-id="8d061-135">Bunun yerine sorgu sonuçlarındaki değerleri döndürün.</span><span class="sxs-lookup"><span data-stu-id="8d061-135">Return values in the query results instead.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d061-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d061-136">See also</span></span>

* [<span data-ttu-id="8d061-137">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="8d061-137">Data types</span></span>](types.md)
