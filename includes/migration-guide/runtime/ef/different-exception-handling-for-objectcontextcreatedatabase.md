---
ms.openlocfilehash: 33ad1c044001e0a8d09708cc7a1f06e05cb307de
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805293"
---
### <a name="different-exception-handling-for-objectcontextcreatedatabase-and-dbproviderservicescreatedatabase-methods"></a>Farklı özel durum işleme için ObjectContext.CreateDatabase ve DbProviderServices.CreateDatabase yöntemi

|   |   |
|---|---|
|Ayrıntılar|Veritabanı oluşturma başarısız olursa, .NET Framework 4.5 içinde başlayan <code>CreateDatabase</code> boş veritabanını bırakmak yöntemleri çalışır. Bu işlem başarılı olursa, özgün <xref:System.Data.SqlClient.SqlException?displayProperty=name> aktarılacaktır (yerine <xref:System.InvalidOperationException?displayProperty=name> , her zaman oluşturuldu .NET Framework 4. 0 ')|
|Öneri|Yakalama sırasında bir <xref:System.InvalidOperationException?displayProperty=name> yürütülürken <xref:System.Data.Objects.ObjectContext.CreateDatabase> veya <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)>, SQLExceptions şimdi de yakalandı.|
|Kapsam|İkincil|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)?displayProperty=nameWithType></li></ul>|
