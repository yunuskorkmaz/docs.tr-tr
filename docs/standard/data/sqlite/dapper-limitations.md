---
title: Kaber sınırlamaları
ms.date: 12/13/2019
description: Kaber kullanırken karşılaştığınız kısıtlamaların bazılarını açıklar.
ms.openlocfilehash: 396507f25f591a9ab5c3bb07c0af6fd8d175e4ea
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901205"
---
# <a name="dapper-limitations"></a><span data-ttu-id="f9a80-103">Kaber sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="f9a80-103">Dapper limitations</span></span>

<span data-ttu-id="f9a80-104">Microsoft. Data. SQLite ile [kaber](https://stackexchange.github.io/Dapper/)kullanılırken dikkat etmeniz gereken bazı sınırlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="f9a80-104">There are a few limitations you should be aware of when using Microsoft.Data.Sqlite with [Dapper](https://stackexchange.github.io/Dapper/).</span></span>

## <a name="parameters"></a><span data-ttu-id="f9a80-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f9a80-105">Parameters</span></span>

<span data-ttu-id="f9a80-106">SQLite parametre adları büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="f9a80-106">SQLite parameter names are case-sensitive.</span></span> <span data-ttu-id="f9a80-107">SQL 'de kullanılan parametre adlarının anonim nesne özellikleri ile eşleştiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="f9a80-107">Ensure that the parameter names used in SQL match the case of the anonymous object's properties.</span></span> <span data-ttu-id="f9a80-108">Sorun [#18861](https://github.com/dotnet/efcore/issues/18861) bu deneyimi iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="f9a80-108">Issue [#18861](https://github.com/dotnet/efcore/issues/18861) would improve this experience.</span></span>

<span data-ttu-id="f9a80-109">Paber aynı zamanda, `@` ön eki kullanmak için parametreler bekliyor.</span><span class="sxs-lookup"><span data-stu-id="f9a80-109">Dapper also expects parameters to use the `@` prefix.</span></span> <span data-ttu-id="f9a80-110">Diğer ön ekler çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="f9a80-110">Other prefixes won't work.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_Parameter)]

## <a name="data-types"></a><span data-ttu-id="f9a80-111">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="f9a80-111">Data types</span></span>

<span data-ttu-id="f9a80-112">Kaber, SqliteDataReader Dizin oluşturucuyu kullanarak değerleri okur.</span><span class="sxs-lookup"><span data-stu-id="f9a80-112">Dapper reads values using the SqliteDataReader indexer.</span></span> <span data-ttu-id="f9a80-113">Bu dizin oluşturucunun dönüş türü Object, yani yalnızca Long, Double, String veya Byte [] değerlerini döndürdüğüne gelir.</span><span class="sxs-lookup"><span data-stu-id="f9a80-113">The return type of this indexer is object, which means it will only ever return long, double, string, or byte[] values.</span></span> <span data-ttu-id="f9a80-114">Daha fazla bilgi için bkz. [veri türleri](types.md).</span><span class="sxs-lookup"><span data-stu-id="f9a80-114">For more information, see [Data types](types.md).</span></span> <span data-ttu-id="f9a80-115">Kaber, bu ve diğer temel türler arasındaki dönüştürmelerin çoğunu işler.</span><span class="sxs-lookup"><span data-stu-id="f9a80-115">Dapper handles most conversions between these and other primitive types.</span></span> <span data-ttu-id="f9a80-116">Ne yazık ki,, `DateTimeOffset`veya `Guid` `TimeSpan`işlemez.</span><span class="sxs-lookup"><span data-stu-id="f9a80-116">Unfortunately, it doesn't handle `DateTimeOffset`, `Guid`, or `TimeSpan`.</span></span> <span data-ttu-id="f9a80-117">Sonuçlarınızda bu türleri kullanmak istiyorsanız tür işleyicileri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f9a80-117">Create type handlers if you want to use these types in your results.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_TypeHandlers)]

<span data-ttu-id="f9a80-118">Sorgulama yapmadan önce tür işleyicilerini eklemeyi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f9a80-118">Don't forget to add the type handlers before querying.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_AddTypeHandlers)]

## <a name="see-also"></a><span data-ttu-id="f9a80-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9a80-119">See also</span></span>

* [<span data-ttu-id="f9a80-120">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="f9a80-120">Data types</span></span>](types.md)
* [<span data-ttu-id="f9a80-121">Zaman uyumsuz sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="f9a80-121">Async limitations</span></span>](async.md)
