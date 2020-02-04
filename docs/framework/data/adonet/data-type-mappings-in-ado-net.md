---
title: Veri Türü Eşlemeleri
ms.date: 03/30/2017
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
ms.openlocfilehash: 610cdc1a679b0c51125075076120e12db97da421
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980203"
---
# <a name="data-type-mappings-in-adonet"></a>ADO.NET’te Veri Türü Eşlemeleri
.NET Framework, çalışma zamanında türlerin nasıl bildirildiği, kullanıldığı ve yönetildiğini tanımlayan ortak tür sistemine dayalıdır. Hem değer türleri hem de başvuru türlerinden oluşur ve bunların hepsi <xref:System.Object> temel türünden türetilir. Bir veri kaynağıyla çalışırken, açıkça belirtilmemişse veri türü veri sağlayıcısından algılanır. Örneğin, bir <xref:System.Data.DataSet> nesnesi herhangi bir belirli veri kaynağından bağımsızdır. Bir `DataSet` veriler bir veri kaynağından alınır ve değişiklikler `DataAdapter`kullanılarak veri kaynağına geri kaydedilir. Bu, bir `DataAdapter` bir <xref:System.Data.DataTable> veri kaynağından alınan bir `DataSet` doldurduğunda, `DataTable` sütunların elde edilen veri türleri, veri kaynağına bağlanmak için kullanılan .NET Framework veri sağlayıcısına özgü türler yerine .NET Framework türlerdir.  
  
 Benzer şekilde, bir `DataReader` veri kaynağından bir değer döndürdüğünde, elde edilen değer bir .NET Framework türüne sahip yerel bir değişkende depolanır. `DataAdapter` `Fill` işlemler ve `DataReader``Get` yöntemleri için .NET Framework türü .NET Framework veri sağlayıcısından döndürülen değerden algılanır.  
  
 Çıkarılan veri türüne güvenmek yerine, döndürülmekte olan değerin belirli bir türünü bildiğiniz `DataReader` türü belirlenmiş erişimci yöntemlerini kullanabilirsiniz. Türü belirlenmiş erişimci yöntemleri, bir değeri belirli bir .NET Framework türüne döndürerek daha iyi performans sağlar ve bu da ek tür dönüştürme gereksinimini ortadan kaldırır.  
  
> [!NOTE]
> .NET Framework veri sağlayıcısı veri türleri için null değerler `DBNull.Value`temsil edilir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [SQL Server Veri Türü Eşlemeleri](sql-server-data-type-mappings.md)  
 <xref:System.Data.SqlClient>için gösterilen veri türü eşlemelerini ve veri erişimci yöntemlerini listeler.  
  
 [OLE DB Veri Türü Eşlemeleri](ole-db-data-type-mappings.md)  
 <xref:System.Data.OleDb>için gösterilen veri türü eşlemelerini ve veri erişimci yöntemlerini listeler.  
  
 [ODBC Veri Türü Eşlemeleri](odbc-data-type-mappings.md)  
 <xref:System.Data.Odbc>için gösterilen veri türü eşlemelerini ve veri erişimci yöntemlerini listeler.  
  
 [Oracle Veri Türü Eşlemeleri](oracle-data-type-mappings.md)  
 <xref:System.Data.OracleClient>için gösterilen veri türü eşlemelerini ve veri erişimci yöntemlerini listeler.  
  
 [Kayan Noktalı Sayılar](floating-point-numbers.md)  
 Kayan nokta numaralarıyla çalışırken geliştiricilerin sıkça karşılaştığı sorunları açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server Veri Türleri ve ADO.NET](./sql/sql-server-data-types.md)
- [Parametreleri ve Parametre Veri Türlerini Yapılandırma](configuring-parameters-and-parameter-data-types.md)
- [Veritabanı Şema Bilgilerini Alma](retrieving-database-schema-information.md)
- [Ortak Tür Sistemi](../../../standard/base-types/common-type-system.md)
- [Türleri dönüştürme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/t8s7t9bf(v=vs.90))
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
