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
# <a name="adonet-limitations"></a>ADO.NET sınırlamaları

Microsoft. Data. SQLite birçok ADO.NET soyutlamasının uygulamalarını sağlar ancak bazı sınırlamalar vardır.

## <a name="database-schema-information"></a>Veritabanı şeması bilgileri

Sorgu sonuçlarıyla ilgili meta veriler <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> yöntemi kullanılarak kullanılabilir.

`DbConnection.GetSchema()` uygulanmadı. Bu API iyi tanımlanmış olmadığından, [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) tablosu ve [table_info](https://www.sqlite.org/pragma.html#pragma_table_info) pragma gibi standart SQLite API 'leri kullanarak doğrudan veritabanı meta verilerini almayı öneririz.

Daha fazla bilgi için bkz. [meta veriler](metadata.md).

## <a name="systemtransactions"></a>System. Transactions

Microsoft. Data. SQLite henüz System. Transactions 'yi desteklemez. Bunun yerine ADO.NET işlemlerini kullanın. Daha fazla bilgi için bkz. [işlemler](transactions.md).

Sorun [#13825](https://github.com/aspnet/EntityFrameworkCore/issues/13825)için System. Transactions desteğinin bulunmaması hakkında geri bildirim sağlayın.

## <a name="data-adapters"></a>Veri bağdaştırıcıları

`DbDataAdapter` henüz Microsoft. Data. SQLite tarafından uygulanmıyor. Bu, verileri yüklemek ve güncelleştirmek için yalnızca ADO.NET `DataSet` ve `DataTable` kullanabileceğiniz anlamına gelir.

`DbDataAdapter`uygulama hakkında geri bildirim sağlamak için sorun [#13838](https://github.com/aspnet/EntityFrameworkCore/issues/13838) kullanın.

## <a name="output-parameters"></a>Çıktı parametreleri

SQLite çıkış parametrelerini desteklemiyor.

## <a name="positional-parameters"></a>Konumsal parametreler

Microsoft. Data. SQLite yalnızca adlandırılmış [parametreleri](parameters.md)destekler. Konumsal parametreler desteklenmiyor.

## <a name="stored-procedures"></a>Saklı yordamlar

SQLite saklı yordamları desteklemez.

## <a name="isolation-levels"></a>Yalıtım düzeyleri

`Chaos` ve `Snapshot` yalıtım düzeyleri SQLite işlemlerinde desteklenmez.

## <a name="see-also"></a>Ayrıca bkz.

* [Zaman uyumsuz sınırlamalar](async.md)
* [Veri türleri](types.md)
* [İşlemler](transactions.md)
