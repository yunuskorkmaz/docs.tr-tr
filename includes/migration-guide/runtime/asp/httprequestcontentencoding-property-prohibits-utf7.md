---
ms.openlocfilehash: 668d047d3247d64cb1400d4a9ea6887795fa0d44
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805280"
---
### <a name="httprequestcontentencoding-property-prohibits-utf7"></a><span data-ttu-id="62d6a-101">UTF7 HttpRequest.ContentEncoding özelliği engeller</span><span class="sxs-lookup"><span data-stu-id="62d6a-101">HttpRequest.ContentEncoding property prohibits UTF7</span></span>

|   |   |
|---|---|
|<span data-ttu-id="62d6a-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="62d6a-102">Details</span></span>|<span data-ttu-id="62d6a-103">.NET Framework 4. 5 ' başlayarak, UTF-7 kodlaması MMC'deki <xref:System.Web.HttpRequest?displayProperty=name>s' gövdesi.</span><span class="sxs-lookup"><span data-stu-id="62d6a-103">Beginning in .NET Framework 4.5, UTF-7 encoding is prohibited in <xref:System.Web.HttpRequest?displayProperty=name>s' bodies.</span></span> <span data-ttu-id="62d6a-104">Gelen UTF-7 verilerine bağlı olan uygulamalar için verilerin kodları bazı durumlarda düzgün çözülmez.</span><span class="sxs-lookup"><span data-stu-id="62d6a-104">Data for applications that depend on incoming UTF-7 data will not decode properly in some cases.</span></span>|
|<span data-ttu-id="62d6a-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="62d6a-105">Suggestion</span></span>|<span data-ttu-id="62d6a-106">İdeal olarak, uygulamalar UTF-7 içinde kodlama kullanmayacak şekilde güncelleştirilmelidir <xref:System.Web.HttpRequest?displayProperty=name>s.</span><span class="sxs-lookup"><span data-stu-id="62d6a-106">Ideally, applications should be updated to not use UTF-7 encoding in <xref:System.Web.HttpRequest?displayProperty=name>s.</span></span> <span data-ttu-id="62d6a-107">Alternatif olarak, eski davranışı kullanılarak geri yüklenebilir <code>aspnet:AllowUtf7RequestContentEncoding</code> özniteliği [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="62d6a-107">Alternatively, legacy behavior can be restored by using the <code>aspnet:AllowUtf7RequestContentEncoding</code> attribute of the [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) element.</span></span>|
|<span data-ttu-id="62d6a-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="62d6a-108">Scope</span></span>|<span data-ttu-id="62d6a-109">Kenar</span><span class="sxs-lookup"><span data-stu-id="62d6a-109">Edge</span></span>|
|<span data-ttu-id="62d6a-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="62d6a-110">Version</span></span>|<span data-ttu-id="62d6a-111">4,5</span><span class="sxs-lookup"><span data-stu-id="62d6a-111">4.5</span></span>|
|<span data-ttu-id="62d6a-112">Tür</span><span class="sxs-lookup"><span data-stu-id="62d6a-112">Type</span></span>|<span data-ttu-id="62d6a-113">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="62d6a-113">Runtime</span></span>|
|<span data-ttu-id="62d6a-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="62d6a-114">Affected APIs</span></span>|<ul><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|
