---
ms.openlocfilehash: 768a948849064cedb38110f5ed271717442325c0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620621"
---
### <a name="log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a><span data-ttu-id="15db7-101">ObjectContext. CreateDatabase yöntemi tarafından oluşturulan günlük dosyası adı SQL Server belirtimlerle eşleşecek şekilde değiştirildi</span><span class="sxs-lookup"><span data-stu-id="15db7-101">Log file name created by the ObjectContext.CreateDatabase method has changed to match SQL Server specifications</span></span>

#### <a name="details"></a><span data-ttu-id="15db7-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="15db7-102">Details</span></span>

<span data-ttu-id="15db7-103"><xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName>Yöntemi doğrudan Code First veya bağlantı dizesinde SqlClient sağlayıcısı ve AttachDBFilename değeri ile birlikte çağrıldığında, filename. ldf yerine filename_log. ldf adlı bir günlük dosyası oluşturur (dosya adı, AttachDBFilename değeri tarafından belirtilen dosyanın adıdır).</span><span class="sxs-lookup"><span data-stu-id="15db7-103">When the <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName> method is called either directly or by using Code First with the SqlClient provider and an AttachDBFilename value in the connection string, it creates a log file named filename_log.ldf instead of filename.ldf (where filename is the name of the file specified by the AttachDBFilename value).</span></span> <span data-ttu-id="15db7-104">Bu değişiklik, SQL Server spesifikasyonlarına uygun olarak adlandırılan bir günlük dosyası sağlayarak hata ayıklamayı geliştirir.</span><span class="sxs-lookup"><span data-stu-id="15db7-104">This change improves debugging by providing a log file named according to SQL Server specifications.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="15db7-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="15db7-105">Suggestion</span></span>

<span data-ttu-id="15db7-106">Günlük dosyası adı bir uygulama için önemliyse, uygulamanın standart _log. ldf dosya adı biçimini beklediği için güncelleştirilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="15db7-106">If the log file name is important for an app, the app should be updated to expect the standard _log.ldf file name format.</span></span>

| <span data-ttu-id="15db7-107">Name</span><span class="sxs-lookup"><span data-stu-id="15db7-107">Name</span></span>    | <span data-ttu-id="15db7-108">Değer</span><span class="sxs-lookup"><span data-stu-id="15db7-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="15db7-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="15db7-109">Scope</span></span>   |<span data-ttu-id="15db7-110">Edge</span><span class="sxs-lookup"><span data-stu-id="15db7-110">Edge</span></span>|
|<span data-ttu-id="15db7-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="15db7-111">Version</span></span>|<span data-ttu-id="15db7-112">4,5</span><span class="sxs-lookup"><span data-stu-id="15db7-112">4.5</span></span>|
|<span data-ttu-id="15db7-113">Tür</span><span class="sxs-lookup"><span data-stu-id="15db7-113">Type</span></span>|<span data-ttu-id="15db7-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="15db7-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="15db7-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="15db7-115">Affected APIs</span></span>

-<xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li></ul>|
