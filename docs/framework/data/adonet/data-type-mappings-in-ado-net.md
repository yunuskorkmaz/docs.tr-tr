---
title: ADO.NET’te Veri Türü Eşlemeleri
ms.date: 03/30/2017
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
ms.openlocfilehash: 1db427424e48d5b94e6c158e1d9967626297f4aa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59178704"
---
# <a name="data-type-mappings-in-adonet"></a>ADO.NET’te Veri Türü Eşlemeleri
.NET Framework nasıl türleri bildirilen kullanılan ve çalışma zamanı'nda yönetilen tanımlar ortak tür sisteminin temel alır. Hem değer türleri ve türetilen tüm, başvuru türleri oluşur <xref:System.Object> temel türü. Bir veri kaynağı ile çalışırken, veri türü, açıkça belirtilmezse, veri sağlayıcısı'ndan algılanır. Örneğin, bir <xref:System.Data.DataSet> nesnedir herhangi belirli bir veri kaynağından bağımsız. Verileri bir `DataSet` bir veri kaynağından alınan ve değişiklikleri veri kaynağına geri kullanarak kaldı bir `DataAdapter`. Yani bir `DataAdapter` dolduran bir <xref:System.Data.DataTable> içinde bir `DataSet` sütunların sonuçta elde edilen veri türleri gibi veri kaynağından alınan değerlerle `DataTable` olan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türleri, özel türler yerine [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri veri kaynağına bağlanmak için kullanılan sağlayıcı.  
  
 Benzer şekilde, bir `DataReader` döndürür, sonuç değerini bir veri kaynağından bir değer olan bir yerel değişkende depolanan bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türü. Her ikisi için de `Fill` işlemlerini `DataAdapter` ve `Get` yöntemlerinin `DataReader`, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] döndürülen değerin türü çıkarılan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri sağlayıcısı.  
  
 Çıkarsanan veri türüne işlemine güvenmek yerine, türü belirlenmiş erişimci yöntemlerini kullanabilirsiniz `DataReader` belirli döndürülen değerin türü bildiğinizde. Türü belirtilmiş erişimci metotlarını size daha iyi performans olarak belirli bir değer döndürerek [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türü, ek bir tür dönüştürme ihtiyacını ortadan kaldırır.  
  
> [!NOTE]
>  Null değerler için [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri sağlayıcısı veri türleri tarafından temsil edilir `DBNull.Value`.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [SQL Server Veri Türü Eşlemeleri](../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 Veri türü eşlemeleri ve veri erişimci yöntemlerini listeler çıkarılan <xref:System.Data.SqlClient>.  
  
 [OLE DB Veri Türü Eşlemeleri](../../../../docs/framework/data/adonet/ole-db-data-type-mappings.md)  
 Veri türü eşlemeleri ve veri erişimci yöntemlerini listeler çıkarılan <xref:System.Data.OleDb>.  
  
 [ODBC Veri Türü Eşlemeleri](../../../../docs/framework/data/adonet/odbc-data-type-mappings.md)  
 Veri türü eşlemeleri ve veri erişimci yöntemlerini listeler çıkarılan <xref:System.Data.Odbc>.  
  
 [Oracle Veri Türü Eşlemeleri](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 Veri türü eşlemeleri ve veri erişimci yöntemlerini listeler çıkarılan <xref:System.Data.OracleClient>.  
  
 [Kayan Noktalı Sayılar](../../../../docs/framework/data/adonet/floating-point-numbers.md)  
 Geliştiriciler kayan nokta sayıları ile çalışırken sık karşılaştığınız sorunları açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server Veri Türleri ve ADO.NET](../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)
- [Parametreleri ve Parametre Veri Türlerini Yapılandırma](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)
- [Veritabanı Şema Bilgilerini Alma](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)
- [Ortak Tür Sistemi](../../../../docs/standard/base-types/common-type-system.md)
- [Türleri dönüştürme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/t8s7t9bf(v=vs.90))
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
