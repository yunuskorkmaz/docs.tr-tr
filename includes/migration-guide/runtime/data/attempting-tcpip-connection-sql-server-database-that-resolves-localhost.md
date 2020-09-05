---
ms.openlocfilehash: bbeca87b3f498213b91d942cc4f197c9d80457a8
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497899"
---
### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a><span data-ttu-id="34de1-101">Başarısız olarak çözümlenen bir SQL Server veritabanına TCP/IP bağlantısı kurmaya çalışılıyor `localhost`</span><span class="sxs-lookup"><span data-stu-id="34de1-101">Attempting a TCP/IP connection to a SQL Server database that resolves to `localhost` fails</span></span>

#### <a name="details"></a><span data-ttu-id="34de1-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="34de1-102">Details</span></span>

<span data-ttu-id="34de1-103">.NET Framework 4,6 ve 4.6.1 ' de, hata ile başarısız olarak çözümlenen bir SQL Server veritabanına TCP/IP bağlantısı kurmaya çalışırken <code>localhost</code> , &quot; SQL Server bağlantı kurulurken ağla ilgili veya örneğe özgü bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="34de1-103">In the .NET Framework 4.6 and 4.6.1, attempting a TCP/IP connection to a SQL Server database that resolves to <code>localhost</code> fails with the error, &quot;A network-related or instance-specific error occurred while establishing a connection to SQL Server.</span></span> <span data-ttu-id="34de1-104">Sunucu bulunamadı veya erişilebilir değildi.</span><span class="sxs-lookup"><span data-stu-id="34de1-104">The server was not found or was not accessible.</span></span> <span data-ttu-id="34de1-105">Örnek adının doğru olduğundan ve SQL Server uzak bağlantılara izin verecek şekilde yapılandırıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="34de1-105">Verify that the instance name is correct and that SQL Server is configured to allow remote connections.</span></span> <span data-ttu-id="34de1-106">(sağlayıcı: SQL ağ arabirimleri, hata: 26-belirtilen sunucu/örnek bulunurken hata oluştu)&quot;</span><span class="sxs-lookup"><span data-stu-id="34de1-106">(provider: SQL Network Interfaces, error: 26 - Error Locating Server/Instance Specified)&quot;</span></span>

#### <a name="suggestion"></a><span data-ttu-id="34de1-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="34de1-107">Suggestion</span></span>

<span data-ttu-id="34de1-108">Bu sorun giderilmiştir ve önceki davranış .NET Framework 4.6.2 geri yüklendi.</span><span class="sxs-lookup"><span data-stu-id="34de1-108">This issue has been addressed and the previous behavior restored in the .NET Framework 4.6.2.</span></span> <span data-ttu-id="34de1-109">' A çözümlenen SQL Server bir veritabanına bağlanmak için <code>localhost</code> .NET Framework 4.6.2 yükseltin.</span><span class="sxs-lookup"><span data-stu-id="34de1-109">To connect to a SQL Server database that resolves to <code>localhost</code>, upgrade to the .NET Framework 4.6.2.</span></span>

| <span data-ttu-id="34de1-110">Name</span><span class="sxs-lookup"><span data-stu-id="34de1-110">Name</span></span>    | <span data-ttu-id="34de1-111">Değer</span><span class="sxs-lookup"><span data-stu-id="34de1-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="34de1-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="34de1-112">Scope</span></span>   |<span data-ttu-id="34de1-113">İkincil</span><span class="sxs-lookup"><span data-stu-id="34de1-113">Minor</span></span>|
|<span data-ttu-id="34de1-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="34de1-114">Version</span></span>|<span data-ttu-id="34de1-115">4.6</span><span class="sxs-lookup"><span data-stu-id="34de1-115">4.6</span></span>|
|<span data-ttu-id="34de1-116">Tür</span><span class="sxs-lookup"><span data-stu-id="34de1-116">Type</span></span>|<span data-ttu-id="34de1-117">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="34de1-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="34de1-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="34de1-118">Affected APIs</span></span>

<span data-ttu-id="34de1-119">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="34de1-119">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
