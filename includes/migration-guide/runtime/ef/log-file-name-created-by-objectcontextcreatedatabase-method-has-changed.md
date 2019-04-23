---
ms.openlocfilehash: cf1a8169351e29c18d85303fb32d4394877448f4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805315"
---
### <a name="log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a><span data-ttu-id="8aa88-101">SQL Server spesifikasyonlarına eşleştirilecek ObjectContext.CreateDatabase yöntemi tarafından oluşturulan günlük dosyası adı değiştirildi</span><span class="sxs-lookup"><span data-stu-id="8aa88-101">Log file name created by the ObjectContext.CreateDatabase method has changed to match SQL Server specifications</span></span>

|   |   |
|---|---|
|<span data-ttu-id="8aa88-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="8aa88-102">Details</span></span>|<span data-ttu-id="8aa88-103">Zaman <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=name> yöntemi çağrıldığında ya da doğrudan ya da Code First SqlClient sağlayıcısı ve bağlantı dizesinde AttachDBFilename değeri ile kullanarak (dosya adı olduğu adını filename_log.ldf filename.ldf yerine adlandırılmış bir günlük dosyası oluşturur AttachDBFilename değeri tarafından belirtilen dosya).</span><span class="sxs-lookup"><span data-stu-id="8aa88-103">When the <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=name> method is called either directly or by using Code First with the SqlClient provider and an AttachDBFilename value in the connection string, it creates a log file named filename_log.ldf instead of filename.ldf (where filename is the name of the file specified by the AttachDBFilename value).</span></span> <span data-ttu-id="8aa88-104">Bu değişiklik, SQL Server spesifikasyonlarına uygun olarak adlandırılan bir günlük dosyası sağlayarak hata ayıklamayı geliştirir.</span><span class="sxs-lookup"><span data-stu-id="8aa88-104">This change improves debugging by providing a log file named according to SQL Server specifications.</span></span>|
|<span data-ttu-id="8aa88-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="8aa88-105">Suggestion</span></span>|<span data-ttu-id="8aa88-106">Günlük dosyası adı bir uygulama için önemli ise, uygulama standart _log.ldf dosya adı biçimi beklenir güncelleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="8aa88-106">If the log file name is important for an app, the app should be updated to expect the standard _log.ldf file name format.</span></span>|
|<span data-ttu-id="8aa88-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="8aa88-107">Scope</span></span>|<span data-ttu-id="8aa88-108">Kenar</span><span class="sxs-lookup"><span data-stu-id="8aa88-108">Edge</span></span>|
|<span data-ttu-id="8aa88-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="8aa88-109">Version</span></span>|<span data-ttu-id="8aa88-110">4,5</span><span class="sxs-lookup"><span data-stu-id="8aa88-110">4.5</span></span>|
|<span data-ttu-id="8aa88-111">Tür</span><span class="sxs-lookup"><span data-stu-id="8aa88-111">Type</span></span>|<span data-ttu-id="8aa88-112">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="8aa88-112">Runtime</span></span>|
|<span data-ttu-id="8aa88-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="8aa88-113">Affected APIs</span></span>|<ul><li><xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li></ul>|
