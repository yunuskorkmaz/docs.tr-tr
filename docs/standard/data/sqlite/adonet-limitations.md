---
title: ADO.NET sınırlamaları
ms.date: 12/13/2019
description: Karşılaşabileceğiniz bazı ADO.NET sınırlamalarından bazılarını açıklar.
ms.openlocfilehash: b58fd3a9ea324e9c17ad21479e53e45f5982db9d
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447092"
---
# <a name="adonet-limitations"></a><span data-ttu-id="76397-103">ADO.NET sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="76397-103">ADO.NET limitations</span></span>

<span data-ttu-id="76397-104">Microsoft. Data. SQLite birçok ADO.NET soyutlamasının uygulamalarını sağlar ancak bazı sınırlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="76397-104">Microsoft.Data.Sqlite provides implementations of many of the ADO.NET abstractions, but there are some limitations.</span></span>

## <a name="database-schema-information"></a><span data-ttu-id="76397-105">Veritabanı şeması bilgileri</span><span class="sxs-lookup"><span data-stu-id="76397-105">Database schema information</span></span>

<span data-ttu-id="76397-106">Sorgu sonuçlarıyla ilgili meta veriler <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> yöntemi kullanılarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="76397-106">Metadata about query results is available using the <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> method.</span></span>

<span data-ttu-id="76397-107">`DbConnection.GetSchema()` uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="76397-107">`DbConnection.GetSchema()` isn't implemented.</span></span> <span data-ttu-id="76397-108">Bu API iyi tanımlanmış olmadığından, [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) tablosu ve [table_info](https://www.sqlite.org/pragma.html#pragma_table_info) pragma gibi standart SQLite API 'leri kullanarak doğrudan veritabanı meta verilerini almayı öneririz.</span><span class="sxs-lookup"><span data-stu-id="76397-108">This API isn't well-defined, so we recommend retrieving database metadata directly using standard SQLite APIs like the [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) table and the [table_info](https://www.sqlite.org/pragma.html#pragma_table_info) PRAGMA.</span></span>

<span data-ttu-id="76397-109">Daha fazla bilgi için bkz. [meta veriler](metadata.md).</span><span class="sxs-lookup"><span data-stu-id="76397-109">For more information, see [Metadata](metadata.md).</span></span>

## <a name="systemtransactions"></a><span data-ttu-id="76397-110">System. Transactions</span><span class="sxs-lookup"><span data-stu-id="76397-110">System.Transactions</span></span>

<span data-ttu-id="76397-111">Microsoft. Data. SQLite henüz System. Transactions 'yi desteklemez.</span><span class="sxs-lookup"><span data-stu-id="76397-111">Microsoft.Data.Sqlite doesn't yet support System.Transactions.</span></span> <span data-ttu-id="76397-112">Bunun yerine ADO.NET işlemlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="76397-112">Use ADO.NET transactions instead.</span></span> <span data-ttu-id="76397-113">Daha fazla bilgi için bkz. [işlemler](transactions.md).</span><span class="sxs-lookup"><span data-stu-id="76397-113">For more information, see [Transactions](transactions.md).</span></span>

<span data-ttu-id="76397-114">Sorun [#13825](https://github.com/aspnet/EntityFrameworkCore/issues/13825)için System. Transactions desteğinin bulunmaması hakkında geri bildirim sağlayın.</span><span class="sxs-lookup"><span data-stu-id="76397-114">Provide feedback about the lack of support for System.Transactions on issue [#13825](https://github.com/aspnet/EntityFrameworkCore/issues/13825).</span></span>

## <a name="data-adapters"></a><span data-ttu-id="76397-115">Veri bağdaştırıcıları</span><span class="sxs-lookup"><span data-stu-id="76397-115">Data adapters</span></span>

<span data-ttu-id="76397-116">`DbDataAdapter` henüz Microsoft. Data. SQLite tarafından uygulanmıyor.</span><span class="sxs-lookup"><span data-stu-id="76397-116">`DbDataAdapter` isn't yet implemented by Microsoft.Data.Sqlite.</span></span> <span data-ttu-id="76397-117">Bu, verileri yüklemek ve güncelleştirmek için yalnızca ADO.NET `DataSet` ve `DataTable` kullanabileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="76397-117">This means you can only use ADO.NET `DataSet` and `DataTable` to load data and not update it.</span></span>

<span data-ttu-id="76397-118">`DbDataAdapter`uygulama hakkında geri bildirim sağlamak için sorun [#13838](https://github.com/aspnet/EntityFrameworkCore/issues/13838) kullanın.</span><span class="sxs-lookup"><span data-stu-id="76397-118">Use issue [#13838](https://github.com/aspnet/EntityFrameworkCore/issues/13838) to provide feedback about implementing `DbDataAdapter`.</span></span>

## <a name="output-parameters"></a><span data-ttu-id="76397-119">Çıktı parametreleri</span><span class="sxs-lookup"><span data-stu-id="76397-119">Output parameters</span></span>

<span data-ttu-id="76397-120">SQLite çıkış parametrelerini desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="76397-120">SQLite doesn't support output parameters.</span></span>

## <a name="positional-parameters"></a><span data-ttu-id="76397-121">Konumsal parametreler</span><span class="sxs-lookup"><span data-stu-id="76397-121">Positional parameters</span></span>

<span data-ttu-id="76397-122">Microsoft. Data. SQLite yalnızca adlandırılmış [parametreleri](parameters.md)destekler.</span><span class="sxs-lookup"><span data-stu-id="76397-122">Microsoft.Data.Sqlite only supports named [parameters](parameters.md).</span></span> <span data-ttu-id="76397-123">Konumsal parametreler desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="76397-123">Positional parameters aren't supported.</span></span>

## <a name="stored-procedures"></a><span data-ttu-id="76397-124">Saklı yordamlar</span><span class="sxs-lookup"><span data-stu-id="76397-124">Stored procedures</span></span>

<span data-ttu-id="76397-125">SQLite saklı yordamları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="76397-125">SQLite doesn't support stored procedures.</span></span>

## <a name="isolation-levels"></a><span data-ttu-id="76397-126">Yalıtım düzeyleri</span><span class="sxs-lookup"><span data-stu-id="76397-126">Isolation levels</span></span>

<span data-ttu-id="76397-127">`Chaos` ve `Snapshot` yalıtım düzeyleri SQLite işlemlerinde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="76397-127">The `Chaos` and `Snapshot` isolation levels aren't supported in SQLite transactions.</span></span>

## <a name="see-also"></a><span data-ttu-id="76397-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76397-128">See also</span></span>

* [<span data-ttu-id="76397-129">Zaman uyumsuz sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="76397-129">Async limitations</span></span>](async.md)
* [<span data-ttu-id="76397-130">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="76397-130">Data types</span></span>](types.md)
* [<span data-ttu-id="76397-131">İşlemler</span><span class="sxs-lookup"><span data-stu-id="76397-131">Transactions</span></span>](transactions.md)
