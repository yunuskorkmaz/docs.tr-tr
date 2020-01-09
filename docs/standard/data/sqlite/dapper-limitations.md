---
title: Kaber sınırlamaları
ms.date: 12/13/2019
description: Kaber kullanırken karşılaştığınız kısıtlamaların bazılarını açıklar.
ms.openlocfilehash: 90c7fb24f068d663081390bdba9b1b222b4be56e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447281"
---
# <a name="dapper-limitations"></a><span data-ttu-id="d8f82-103">Kaber sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="d8f82-103">Dapper limitations</span></span>

<span data-ttu-id="d8f82-104">Microsoft. Data. SQLite ile [kaber](https://stackexchange.github.io/Dapper/)kullanılırken dikkat etmeniz gereken bazı sınırlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="d8f82-104">There are a few limitations you should be aware of when using Microsoft.Data.Sqlite with [Dapper](https://stackexchange.github.io/Dapper/).</span></span>

## <a name="parameters"></a><span data-ttu-id="d8f82-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d8f82-105">Parameters</span></span>

<span data-ttu-id="d8f82-106">SQLite parametre adları büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="d8f82-106">SQLite parameter names are case-sensitive.</span></span> <span data-ttu-id="d8f82-107">SQL 'de kullanılan parametre adlarının anonim nesne özellikleri ile eşleştiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="d8f82-107">Ensure that the parameter names used in SQL match the case of the anonymous object's properties.</span></span> <span data-ttu-id="d8f82-108">Sorun [#18861](https://github.com/aspnet/EntityFrameworkCore/issues/18861) bu deneyimi iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="d8f82-108">Issue [#18861](https://github.com/aspnet/EntityFrameworkCore/issues/18861) would improve this experience.</span></span>

<span data-ttu-id="d8f82-109">Paber Ayrıca `@` önekini kullanmak için parametreler bekliyor.</span><span class="sxs-lookup"><span data-stu-id="d8f82-109">Dapper also expects parameters to use the `@` prefix.</span></span> <span data-ttu-id="d8f82-110">Diğer ön ekler çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="d8f82-110">Other prefixes won't work.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_Parameter)]

## <a name="data-types"></a><span data-ttu-id="d8f82-111">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="d8f82-111">Data types</span></span>

<span data-ttu-id="d8f82-112">Kaber, SqliteDataReader Dizin oluşturucuyu kullanarak değerleri okur.</span><span class="sxs-lookup"><span data-stu-id="d8f82-112">Dapper reads values using the SqliteDataReader indexer.</span></span> <span data-ttu-id="d8f82-113">Bu dizin oluşturucunun dönüş türü Object, yani yalnızca Long, Double, String veya Byte [] değerlerini döndürdüğüne gelir.</span><span class="sxs-lookup"><span data-stu-id="d8f82-113">The return type of this indexer is object, which means it will only ever return long, double, string, or byte[] values.</span></span> <span data-ttu-id="d8f82-114">Daha fazla bilgi için bkz. [veri türleri](types.md).</span><span class="sxs-lookup"><span data-stu-id="d8f82-114">For more information, see [Data types](types.md).</span></span> <span data-ttu-id="d8f82-115">Kaber, bu ve diğer temel türler arasındaki dönüştürmelerin çoğunu işler.</span><span class="sxs-lookup"><span data-stu-id="d8f82-115">Dapper handles most conversions between these and other primitive types.</span></span> <span data-ttu-id="d8f82-116">Ne yazık ki `DateTimeOffset`, `Guid`veya `TimeSpan`işlemez.</span><span class="sxs-lookup"><span data-stu-id="d8f82-116">Unfortunately, it doesn't handle `DateTimeOffset`, `Guid`, or `TimeSpan`.</span></span> <span data-ttu-id="d8f82-117">Sonuçlarınızda bu türleri kullanmak istiyorsanız tür işleyicileri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d8f82-117">Create type handlers if you want to use these types in your results.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_TypeHandlers)]

<span data-ttu-id="d8f82-118">Sorgulama yapmadan önce tür işleyicilerini eklemeyi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d8f82-118">Don't forget to add the type handlers before querying.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_AddTypeHandlers)]

## <a name="see-also"></a><span data-ttu-id="d8f82-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8f82-119">See also</span></span>

* [<span data-ttu-id="d8f82-120">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="d8f82-120">Data types</span></span>](types.md)
* [<span data-ttu-id="d8f82-121">Zaman uyumsuz sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="d8f82-121">Async limitations</span></span>](async.md)
