---
ms.openlocfilehash: 23ba6064a283b47312a66f3636c2834a7d58106e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620548"
---
### <a name="adonet-now-attempts-to-automatically-reconnect-broken-sql-connections"></a><span data-ttu-id="7b54e-101">ADO.NET artık bozuk SQL bağlantılarını otomatik olarak yeniden bağlamaya çalışır</span><span class="sxs-lookup"><span data-stu-id="7b54e-101">ADO.NET now attempts to automatically reconnect broken SQL connections</span></span>

#### <a name="details"></a><span data-ttu-id="7b54e-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="7b54e-102">Details</span></span>

<span data-ttu-id="7b54e-103">.NET Framework 4.5.1 başlayarak, .NET Framework bozuk SQL bağlantılarını otomatik olarak yeniden bağlamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="7b54e-103">Beginning in the .NET Framework 4.5.1, the .NET Framework will attempt to automatically reconnect broken SQL connections.</span></span> <span data-ttu-id="7b54e-104">Bu işlem genellikle uygulamaları daha güvenilir hale getirir, ancak bir uygulamanın yeniden bağlantıda bir işlem yapabilmesi için bağlantının kaybolduğunu bilmesi gereken uç durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="7b54e-104">Although this will typically make apps more reliable, there are edge cases in which an app needs to know that the connection was lost so that it can take some action upon reconnection.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7b54e-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="7b54e-105">Suggestion</span></span>

<span data-ttu-id="7b54e-106">Bu özellik uyumluluk sorunları nedeniyle istenerek, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=fullName> bağlantı dizesinin özelliği (veya) 0 olarak ayarlanarak devre dışı bırakılabilir <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="7b54e-106">If this feature is undesirable due to compatibility concerns, it can be disabled by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=fullName> property of a connection string (or <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=fullName>) to 0.</span></span>

| <span data-ttu-id="7b54e-107">Name</span><span class="sxs-lookup"><span data-stu-id="7b54e-107">Name</span></span>    | <span data-ttu-id="7b54e-108">Değer</span><span class="sxs-lookup"><span data-stu-id="7b54e-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7b54e-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="7b54e-109">Scope</span></span>   |<span data-ttu-id="7b54e-110">Edge</span><span class="sxs-lookup"><span data-stu-id="7b54e-110">Edge</span></span>|
|<span data-ttu-id="7b54e-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="7b54e-111">Version</span></span>|<span data-ttu-id="7b54e-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="7b54e-112">4.5.1</span></span>|
|<span data-ttu-id="7b54e-113">Tür</span><span class="sxs-lookup"><span data-stu-id="7b54e-113">Type</span></span>|<span data-ttu-id="7b54e-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="7b54e-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7b54e-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="7b54e-115">Affected APIs</span></span>

-<xref:System.Data.IDbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Configuration.ConnectionStringSettings.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor(System.String)></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor(System.Boolean)></li></ul>|
