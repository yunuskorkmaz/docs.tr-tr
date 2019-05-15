---
title: ADO.NET’te Veri Türü Eşlemeleri
ms.date: 03/30/2017
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
ms.openlocfilehash: 4e85db4732da664848cee2ef48f9a880a86fef18
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583767"
---
# <a name="data-type-mappings-in-adonet"></a>ADO.NET’te Veri Türü Eşlemeleri
.NET Framework nasıl türleri bildirilen kullanılan ve çalışma zamanı'nda yönetilen tanımlar ortak tür sisteminin temel alır. Hem değer türleri ve türetilen tüm, başvuru türleri oluşur <xref:System.Object> temel türü. Bir veri kaynağı ile çalışırken, veri türü, açıkça belirtilmezse, veri sağlayıcısı'ndan algılanır. Örneğin, bir <xref:System.Data.DataSet> nesnedir herhangi belirli bir veri kaynağından bağımsız. Verileri bir `DataSet` bir veri kaynağından alınan ve değişiklikleri veri kaynağına geri kullanarak kaldı bir `DataAdapter`. Yani bir `DataAdapter` dolduran bir <xref:System.Data.DataTable> içinde bir `DataSet` sütunların sonuçta elde edilen veri türleri gibi veri kaynağından alınan değerlerle `DataTable` türler için .NET Framework veri sağlayıcısı belirli yerine .NET Framework türleri, veri kaynağına bağlanmak için kullanılır.  
  
 Benzer şekilde, bir `DataReader` sonuç değerini bir veri kaynağından alınan bir değer, .NET Framework türü olan bir yerel değişkende depolanan döndürür. Her ikisi için de `Fill` işlemlerini `DataAdapter` ve `Get` yöntemlerinin `DataReader`, .NET Framework türü .NET Framework veri sağlayıcısı tarafından döndürülen değer gösterilir.  
  
 Çıkarsanan veri türüne işlemine güvenmek yerine, türü belirlenmiş erişimci yöntemlerini kullanabilirsiniz `DataReader` belirli döndürülen değerin türü bildiğinizde. Türü belirtilmiş erişimci metotlarını ek tür dönüştürme ihtiyacını ortadan kaldırır belirli bir .NET Framework türü bir değer döndürerek daha iyi performans verir.  
  
> [!NOTE]
>  .NET Framework veri sağlayıcısı veri türleri için null değerler tarafından temsil edilir `DBNull.Value`.  
  
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
