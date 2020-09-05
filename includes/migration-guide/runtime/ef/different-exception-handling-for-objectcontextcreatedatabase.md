---
ms.openlocfilehash: 8c593fa6490451c6236f0d4390f09d4e9e4f0cbb
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497080"
---
### <a name="different-exception-handling-for-objectcontextcreatedatabase-and-dbproviderservicescreatedatabase-methods"></a>ObjectContext. CreateDatabase ve DbProviderServices. CreateDatabase metotları için farklı özel durum işleme

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,5 ' den başlayarak, veritabanı oluşturma başarısız olursa, <code>CreateDatabase</code> Yöntemler boş veritabanını bırakmaya çalışır. Bu işlem başarılı olursa, orijinalin <xref:System.Data.SqlClient.SqlException?displayProperty=fullName> yayılacağı ( <xref:System.InvalidOperationException?displayProperty=fullName> .NET Framework 4,0 ' de her zaman oluşturulan)

#### <a name="suggestion"></a>Öneri

<xref:System.InvalidOperationException?displayProperty=fullName>Ya da yürütülürken <xref:System.Data.Objects.ObjectContext.CreateDatabase> veya <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)> SqlExceptions artık yakalanmalıdır.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType>
- <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Data.Objects.ObjectContext.CreateDatabase`
- `M:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)`

-->
