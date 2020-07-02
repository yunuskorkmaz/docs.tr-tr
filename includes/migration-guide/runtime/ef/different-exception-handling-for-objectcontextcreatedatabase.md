---
ms.openlocfilehash: 687118157020ede200f97a0125c4740a06bf4b5e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620615"
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
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)?displayProperty=nameWithType></li></ul>|
