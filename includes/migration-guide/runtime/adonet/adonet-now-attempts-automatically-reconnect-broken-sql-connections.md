---
ms.openlocfilehash: 7f7e718d543a4abdf2b8a87e52d8c0e2ba28203f
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497685"
---
### <a name="adonet-now-attempts-to-automatically-reconnect-broken-sql-connections"></a><span data-ttu-id="ffca1-101">ADO.NET artık bozuk SQL bağlantılarını otomatik olarak yeniden bağlamaya çalışır</span><span class="sxs-lookup"><span data-stu-id="ffca1-101">ADO.NET now attempts to automatically reconnect broken SQL connections</span></span>

#### <a name="details"></a><span data-ttu-id="ffca1-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ffca1-102">Details</span></span>

<span data-ttu-id="ffca1-103">.NET Framework 4.5.1 başlayarak, .NET Framework bozuk SQL bağlantılarını otomatik olarak yeniden bağlamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="ffca1-103">Beginning in the .NET Framework 4.5.1, the .NET Framework will attempt to automatically reconnect broken SQL connections.</span></span> <span data-ttu-id="ffca1-104">Bu işlem genellikle uygulamaları daha güvenilir hale getirir, ancak bir uygulamanın yeniden bağlantıda bir işlem yapabilmesi için bağlantının kaybolduğunu bilmesi gereken uç durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="ffca1-104">Although this will typically make apps more reliable, there are edge cases in which an app needs to know that the connection was lost so that it can take some action upon reconnection.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ffca1-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="ffca1-105">Suggestion</span></span>

<span data-ttu-id="ffca1-106">Bu özellik uyumluluk sorunları nedeniyle istenerek, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=fullName> bağlantı dizesinin özelliği (veya) 0 olarak ayarlanarak devre dışı bırakılabilir <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="ffca1-106">If this feature is undesirable due to compatibility concerns, it can be disabled by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=fullName> property of a connection string (or <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=fullName>) to 0.</span></span>

| <span data-ttu-id="ffca1-107">Name</span><span class="sxs-lookup"><span data-stu-id="ffca1-107">Name</span></span>    | <span data-ttu-id="ffca1-108">Değer</span><span class="sxs-lookup"><span data-stu-id="ffca1-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ffca1-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="ffca1-109">Scope</span></span>   |<span data-ttu-id="ffca1-110">Edge</span><span class="sxs-lookup"><span data-stu-id="ffca1-110">Edge</span></span>|
|<span data-ttu-id="ffca1-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="ffca1-111">Version</span></span>|<span data-ttu-id="ffca1-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="ffca1-112">4.5.1</span></span>|
|<span data-ttu-id="ffca1-113">Tür</span><span class="sxs-lookup"><span data-stu-id="ffca1-113">Type</span></span>|<span data-ttu-id="ffca1-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="ffca1-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="ffca1-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="ffca1-115">Affected APIs</span></span>

- <xref:System.Data.IDbConnection.ConnectionString?displayProperty=nameWithType>
- <xref:System.Data.SqlClient.SqlConnection.ConnectionString?displayProperty=nameWithType>
- <xref:System.Configuration.ConnectionStringSettings.ConnectionString?displayProperty=nameWithType>
- <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType>
- <xref:System.Data.Common.DbConnectionStringBuilder.ConnectionString?displayProperty=nameWithType>
- <xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor>
- <xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor(System.String)>
- <xref:System.Data.Common.DbConnectionStringBuilder.%23ctor>
- <xref:System.Data.Common.DbConnectionStringBuilder.%23ctor(System.Boolean)>

<!--

#### Affected APIs

- `P:System.Data.IDbConnection.ConnectionString`
- `P:System.Data.SqlClient.SqlConnection.ConnectionString`
- `P:System.Configuration.ConnectionStringSettings.ConnectionString`
- `P:System.Data.Common.DbConnection.ConnectionString`
- `P:System.Data.Common.DbConnectionStringBuilder.ConnectionString`
- `M:System.Data.SqlClient.SqlConnectionStringBuilder.#ctor`
- `M:System.Data.SqlClient.SqlConnectionStringBuilder.#ctor(System.String)`
- `M:System.Data.Common.DbConnectionStringBuilder.#ctor`
- `M:System.Data.Common.DbConnectionStringBuilder.#ctor(System.Boolean)`

-->
