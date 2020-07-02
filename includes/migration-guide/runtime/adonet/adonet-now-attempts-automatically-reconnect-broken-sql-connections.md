---
ms.openlocfilehash: 23ba6064a283b47312a66f3636c2834a7d58106e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620548"
---
### <a name="adonet-now-attempts-to-automatically-reconnect-broken-sql-connections"></a>ADO.NET artık bozuk SQL bağlantılarını otomatik olarak yeniden bağlamaya çalışır

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.5.1 başlayarak, .NET Framework bozuk SQL bağlantılarını otomatik olarak yeniden bağlamaya çalışır. Bu işlem genellikle uygulamaları daha güvenilir hale getirir, ancak bir uygulamanın yeniden bağlantıda bir işlem yapabilmesi için bağlantının kaybolduğunu bilmesi gereken uç durumlar vardır.

#### <a name="suggestion"></a>Öneri

Bu özellik uyumluluk sorunları nedeniyle istenerek, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=fullName> bağlantı dizesinin özelliği (veya) 0 olarak ayarlanarak devre dışı bırakılabilir <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=fullName> .

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4.5.1|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Data.IDbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Configuration.ConnectionStringSettings.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor(System.String)></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor(System.Boolean)></li></ul>|
