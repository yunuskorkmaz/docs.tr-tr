---
title: ADO.NET’te Veri Türü Eşlemeleri
ms.date: 03/30/2017
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
ms.openlocfilehash: 9c0d19f724c1876f7dac86055bed2ef77ac76a77
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785595"
---
# <a name="data-type-mappings-in-adonet"></a>ADO.NET’te Veri Türü Eşlemeleri
.NET Framework, çalışma zamanında türlerin nasıl bildirildiği, kullanıldığı ve yönetildiğini tanımlayan ortak tür sistemine dayalıdır. Her ikisi de <xref:System.Object> temel türden türetilen değer türleri ve başvuru türlerinden oluşur. Bir veri kaynağıyla çalışırken, açıkça belirtilmemişse veri türü veri sağlayıcısından algılanır. Örneğin, bir nesne <xref:System.Data.DataSet> belirli bir veri kaynağından bağımsızdır. İçindeki `DataSet` veriler bir veri kaynağından alınır ve değişiklikler bir `DataAdapter`kullanılarak veri kaynağına geri kaydedilir. Diğer bir deyişle, bir `DataAdapter` veri kaynağından <xref:System.Data.DataTable> değerleri `DataSet` olan bir ile bir doldurduğunda, içindeki sütunların sonuç veri türleri, .NET Framework veri sağlayıcısına özgü `DataTable` türler yerine .NET Framework türlerdir. veri kaynağına bağlanmak için kullanılır.  
  
 Benzer şekilde, bir `DataReader` veri kaynağından bir değer döndürdüğünde, sonuçta elde edilen değer .NET Framework türüne sahip yerel bir değişkende depolanır. Ve yöntemlerinin her `Fill`ikisi için,.NETFrameworktürü.NETFrameworkverisağlayıcısındandöndürülendeğerdençıkarsanamıyor.`Get` `DataAdapter` `DataReader`  
  
 Gösterilen veri türüne güvenmek yerine, döndürülmekte olan değerin belirli bir türünü bildiğiniz `DataReader` zaman türü belirlenmiş erişimci yöntemlerini kullanabilirsiniz. Türü belirlenmiş erişimci yöntemleri, bir değeri belirli bir .NET Framework türüne döndürerek daha iyi performans sağlar ve bu da ek tür dönüştürme gereksinimini ortadan kaldırır.  
  
> [!NOTE]
> .NET Framework veri sağlayıcısı veri türleri için null değerler tarafından `DBNull.Value`temsil edilir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [SQL Server Veri Türü Eşlemeleri](sql-server-data-type-mappings.md)  
 İçin <xref:System.Data.SqlClient>gösterilen veri türü eşlemelerini ve veri erişimcisi yöntemlerini listeler.  
  
 [OLE DB Veri Türü Eşlemeleri](ole-db-data-type-mappings.md)  
 İçin <xref:System.Data.OleDb>gösterilen veri türü eşlemelerini ve veri erişimcisi yöntemlerini listeler.  
  
 [ODBC Veri Türü Eşlemeleri](odbc-data-type-mappings.md)  
 İçin <xref:System.Data.Odbc>gösterilen veri türü eşlemelerini ve veri erişimcisi yöntemlerini listeler.  
  
 [Oracle Veri Türü Eşlemeleri](oracle-data-type-mappings.md)  
 İçin <xref:System.Data.OracleClient>gösterilen veri türü eşlemelerini ve veri erişimcisi yöntemlerini listeler.  
  
 [Kayan Noktalı Sayılar](floating-point-numbers.md)  
 Kayan nokta numaralarıyla çalışırken geliştiricilerin sıkça karşılaştığı sorunları açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server Veri Türleri ve ADO.NET](./sql/sql-server-data-types.md)
- [Parametreleri ve Parametre Veri Türlerini Yapılandırma](configuring-parameters-and-parameter-data-types.md)
- [Veritabanı Şema Bilgilerini Alma](retrieving-database-schema-information.md)
- [Ortak Tür Sistemi](../../../standard/base-types/common-type-system.md)
- [Türleri dönüştürme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/t8s7t9bf(v=vs.90))
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
