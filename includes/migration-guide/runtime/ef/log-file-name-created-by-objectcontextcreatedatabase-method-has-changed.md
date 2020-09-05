---
ms.openlocfilehash: e77e37156de759856c8a6f2e0c009caf9e1fe826
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497446"
---
### <a name="log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a><span data-ttu-id="f2645-101">ObjectContext. CreateDatabase yöntemi tarafından oluşturulan günlük dosyası adı SQL Server belirtimlerle eşleşecek şekilde değiştirildi</span><span class="sxs-lookup"><span data-stu-id="f2645-101">Log file name created by the ObjectContext.CreateDatabase method has changed to match SQL Server specifications</span></span>

#### <a name="details"></a><span data-ttu-id="f2645-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f2645-102">Details</span></span>

<span data-ttu-id="f2645-103"><xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName>Yöntemi doğrudan Code First veya bağlantı dizesinde SqlClient sağlayıcısı ve AttachDBFilename değeri ile birlikte çağrıldığında, filename. ldf yerine filename_log. ldf adlı bir günlük dosyası oluşturur (dosya adı, AttachDBFilename değeri tarafından belirtilen dosyanın adıdır).</span><span class="sxs-lookup"><span data-stu-id="f2645-103">When the <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName> method is called either directly or by using Code First with the SqlClient provider and an AttachDBFilename value in the connection string, it creates a log file named filename_log.ldf instead of filename.ldf (where filename is the name of the file specified by the AttachDBFilename value).</span></span> <span data-ttu-id="f2645-104">Bu değişiklik, SQL Server spesifikasyonlarına uygun olarak adlandırılan bir günlük dosyası sağlayarak hata ayıklamayı geliştirir.</span><span class="sxs-lookup"><span data-stu-id="f2645-104">This change improves debugging by providing a log file named according to SQL Server specifications.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f2645-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="f2645-105">Suggestion</span></span>

<span data-ttu-id="f2645-106">Günlük dosyası adı bir uygulama için önemliyse, uygulamanın standart _log. ldf dosya adı biçimini beklediği için güncelleştirilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2645-106">If the log file name is important for an app, the app should be updated to expect the standard _log.ldf file name format.</span></span>

| <span data-ttu-id="f2645-107">Name</span><span class="sxs-lookup"><span data-stu-id="f2645-107">Name</span></span>    | <span data-ttu-id="f2645-108">Değer</span><span class="sxs-lookup"><span data-stu-id="f2645-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f2645-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="f2645-109">Scope</span></span>   |<span data-ttu-id="f2645-110">Edge</span><span class="sxs-lookup"><span data-stu-id="f2645-110">Edge</span></span>|
|<span data-ttu-id="f2645-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="f2645-111">Version</span></span>|<span data-ttu-id="f2645-112">4,5</span><span class="sxs-lookup"><span data-stu-id="f2645-112">4.5</span></span>|
|<span data-ttu-id="f2645-113">Tür</span><span class="sxs-lookup"><span data-stu-id="f2645-113">Type</span></span>|<span data-ttu-id="f2645-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="f2645-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f2645-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="f2645-115">Affected APIs</span></span>

- <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Data.Objects.ObjectContext.CreateDatabase`

-->
