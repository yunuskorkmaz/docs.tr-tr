---
title: Veri Türü Eşlemeleri
ms.date: 03/30/2017
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
ms.openlocfilehash: 065a9dcb5e03c784c5dec9ffbe6a3153aead9e3c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554716"
---
# <a name="data-type-mappings-in-adonet"></a>ADO.NET’te Veri Türü Eşlemeleri
.NET Framework, çalışma zamanında türlerin nasıl bildirildiği, kullanıldığı ve yönetildiğini tanımlayan ortak tür sistemine dayalıdır. Her ikisi de temel türden türetilen değer türleri ve başvuru türlerinden oluşur <xref:System.Object> . Bir veri kaynağıyla çalışırken, açıkça belirtilmemişse veri türü veri sağlayıcısından algılanır. Örneğin, bir <xref:System.Data.DataSet> nesne belirli bir veri kaynağından bağımsızdır. İçindeki veriler bir `DataSet` veri kaynağından alınır ve değişiklikler bir kullanılarak veri kaynağına geri kaydedilir `DataAdapter` . Yani `DataAdapter` <xref:System.Data.DataTable> , bir `DataSet` veri kaynağından değerleri olan bir ile bir doldurduğunda, içindeki sütunların sonuç veri türleri, `DataTable` veri kaynağına bağlanmak için kullanılan .NET Framework veri sağlayıcısına özgü türler yerine .NET Framework türlerdir.  
  
 Benzer şekilde, bir `DataReader` veri kaynağından bir değer döndürdüğünde, sonuçta elde edilen değer .NET Framework türüne sahip yerel bir değişkende depolanır. Ve yöntemlerinin her ikisi için `Fill` `DataAdapter` `Get` `DataReader` , .NET Framework türü .NET Framework veri sağlayıcısından döndürülen değerden çıkarsanamıyor.  
  
 Gösterilen veri türüne güvenmek yerine, `DataReader` döndürülmekte olan değerin belirli bir türünü bildiğiniz zaman türü belirlenmiş erişimci yöntemlerini kullanabilirsiniz. Türü belirlenmiş erişimci yöntemleri, bir değeri belirli bir .NET Framework türüne döndürerek daha iyi performans sağlar ve bu da ek tür dönüştürme gereksinimini ortadan kaldırır.  
  
> [!NOTE]
> .NET Framework veri sağlayıcısı veri türleri için null değerler tarafından temsil edilir `DBNull.Value` .  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [SQL Server Veri Türü Eşlemeleri](sql-server-data-type-mappings.md)  
 İçin gösterilen veri türü eşlemelerini ve veri erişimcisi yöntemlerini listeler <xref:System.Data.SqlClient> .  
  
 [OLE DB Veri Türü Eşlemeleri](ole-db-data-type-mappings.md)  
 İçin gösterilen veri türü eşlemelerini ve veri erişimcisi yöntemlerini listeler <xref:System.Data.OleDb> .  
  
 [ODBC Veri Türü Eşlemeleri](odbc-data-type-mappings.md)  
 İçin gösterilen veri türü eşlemelerini ve veri erişimcisi yöntemlerini listeler <xref:System.Data.Odbc> .  
  
 [Oracle Veri Türü Eşlemeleri](oracle-data-type-mappings.md)  
 İçin gösterilen veri türü eşlemelerini ve veri erişimcisi yöntemlerini listeler <xref:System.Data.OracleClient> .  
  
 [Kayan Noktalı Sayılar](floating-point-numbers.md)  
 Kayan nokta numaralarıyla çalışırken geliştiricilerin sıkça karşılaştığı sorunları açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server Veri Türleri ve ADO.NET](./sql/sql-server-data-types.md)
- [Parametreleri ve Parametre Veri Türlerini Yapılandırma](configuring-parameters-and-parameter-data-types.md)
- [Veritabanı Şema Bilgilerini Alma](retrieving-database-schema-information.md)
- [Ortak tür sistemi](../../../standard/base-types/common-type-system.md)
- [Türleri dönüştürme](/previous-versions/visualstudio/visual-studio-2008/t8s7t9bf(v=vs.90))
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
