---
ms.openlocfilehash: d3c6818861f8b0261a9a71a4654029143d928d08
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760753"
---
### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a><span data-ttu-id="612ec-101">Unicode UNC paylaşımlarını benzer bir URI'leri izin ver</span><span class="sxs-lookup"><span data-stu-id="612ec-101">Allow Unicode in URIs that resemble UNC shares</span></span>

|   |   |
|---|---|
|<span data-ttu-id="612ec-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="612ec-102">Details</span></span>|<span data-ttu-id="612ec-103">İçinde <xref:System.Uri?displayProperty=fullName>, bir dosya oluşturmak URI içeren iki UNC paylaşım adını ve Unicode karakterler artık sonuçlanır geçersiz iç durum ile bir URI.</span><span class="sxs-lookup"><span data-stu-id="612ec-103">In <xref:System.Uri?displayProperty=fullName>, constructing a file URI containing both a UNC share name and Unicode characters will no longer result in a URI with invalid internal state.</span></span> <span data-ttu-id="612ec-104">Yalnızca aşağıdakilerin tümü doğru olduğunda davranışı değiştirir:</span><span class="sxs-lookup"><span data-stu-id="612ec-104">The behavior will change only when all of the following are true:</span></span><ul><li><span data-ttu-id="612ec-105">URI şeması bulunuyor <code>file:</code> ve dört veya daha fazla eğik çizgiyle izlenir.</span><span class="sxs-lookup"><span data-stu-id="612ec-105">The URI has the scheme <code>file:</code> and is followed by four or more slashes.</span></span></li><li><span data-ttu-id="612ec-106">Ana bilgisayar adı, alt çizgi veya başka ayrılmamış bir simge ile başlar.</span><span class="sxs-lookup"><span data-stu-id="612ec-106">The host name begins with an underscore or other non-reserved symbol.</span></span></li><li><span data-ttu-id="612ec-107">URI, Unicode karakterler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="612ec-107">The URI contains Unicode characters.</span></span></li></ul>|
|<span data-ttu-id="612ec-108">Öneri</span><span class="sxs-lookup"><span data-stu-id="612ec-108">Suggestion</span></span>|<span data-ttu-id="612ec-109">Tutarlı bir şekilde Unicode karakterler içeren URI'leri ile çalışan uygulamalar, kısıtlanmamışsa UNC paylaşımlarına başvuruları engellemek için bu davranışı kullanabilirdiniz.</span><span class="sxs-lookup"><span data-stu-id="612ec-109">Applications working with URIs consistently containing Unicode could have conceivably used this behavior to disallow references to UNC shares.</span></span> <span data-ttu-id="612ec-110">Bu uygulamaların kullanması gereken <xref:System.Uri.IsUnc> yerine.</span><span class="sxs-lookup"><span data-stu-id="612ec-110">Those applications should use <xref:System.Uri.IsUnc> instead.</span></span>|
|<span data-ttu-id="612ec-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="612ec-111">Scope</span></span>|<span data-ttu-id="612ec-112">Kenar</span><span class="sxs-lookup"><span data-stu-id="612ec-112">Edge</span></span>|
|<span data-ttu-id="612ec-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="612ec-113">Version</span></span>|<span data-ttu-id="612ec-114">4.7.2</span><span class="sxs-lookup"><span data-stu-id="612ec-114">4.7.2</span></span>|
|<span data-ttu-id="612ec-115">Tür</span><span class="sxs-lookup"><span data-stu-id="612ec-115">Type</span></span>|<span data-ttu-id="612ec-116">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="612ec-116">Runtime</span></span>|
|<span data-ttu-id="612ec-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="612ec-117">Affected APIs</span></span>|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|

