---
ms.openlocfilehash: 9e9e443be9ea51d214e95c676fc28f0d8790af8b
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70930070"
---
### <a name="c-locale-maps-to-the-invariant-locale"></a><span data-ttu-id="0b829-101">"C" yerel ayarı, sabit yerel ayara eşlenir</span><span class="sxs-lookup"><span data-stu-id="0b829-101">"C" locale maps to the invariant locale</span></span>

<span data-ttu-id="0b829-102">.NET Core 2,2 ve önceki sürümleri, "C" yerel ayarını en_US_POSIX yerel ayarıyla eşleyen varsayılan ıCU davranışına bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="0b829-102">.NET Core 2.2 and earlier versions depend on the default ICU behavior, which maps the "C" locale to the en_US_POSIX locale.</span></span> <span data-ttu-id="0b829-103">Büyük/küçük harfe duyarsız dize karşılaştırmaları desteklemediğinden en_US_POSIX yerel ayarının istenmeyen harmanlama davranışı vardır.</span><span class="sxs-lookup"><span data-stu-id="0b829-103">The en_US_POSIX locale has an undesirable collation behavior, because it doesn't support case-insensitive string comparisons.</span></span> <span data-ttu-id="0b829-104">Bazı Linux dağıtımları varsayılan yerel ayar olarak "C" yerel ayarını ayarlamadığı için, kullanıcılar beklenmeyen davranışlarla karşılaşıyor.</span><span class="sxs-lookup"><span data-stu-id="0b829-104">Because some Linux distributions set the "C" locale as the default locale, users were experiencing unexpected behavior.</span></span> 

#### <a name="details"></a><span data-ttu-id="0b829-105">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="0b829-105">Details</span></span>

<span data-ttu-id="0b829-106">.NET Core 3,0 ile başlayarak, "C" yerel ayar eşlemesi en_US_POSIX yerine sabit yerel ayarı kullanacak şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0b829-106">Starting with .NET Core 3.0, the "C" locale mapping has changed to use the Invariant locale instead of en_US_POSIX.</span></span> <span data-ttu-id="0b829-107">Sabit eşleme için "C" yerel ayarı Windows 'a tutarlılık için de uygulanır.</span><span class="sxs-lookup"><span data-stu-id="0b829-107">The "C" locale to Invariant mapping is also applied to Windows for consistency.</span></span>

<span data-ttu-id="0b829-108">En_US_POSIX, büyük/küçük harfe duyarsız sıralama/arama dizesi işlemlerini desteklemediğinden, "C" öğesini en_US_POSIX kültürüne eşleme, müşteri karmaşıklığına neden oldu.</span><span class="sxs-lookup"><span data-stu-id="0b829-108">Mapping "C" to en_US_POSIX culture caused customer confusion, because en_US_POSIX doesn't support case insensitive sorting/searching string operations.</span></span> <span data-ttu-id="0b829-109">"C" yerel ayarı bazı Linux dışı bir yerel ayar olarak kullanıldığından, müşteriler bu işletim sistemlerinde bu istenmeyen davranışla karşılaşmıştır.</span><span class="sxs-lookup"><span data-stu-id="0b829-109">Because the "C" locale is used as a default locale in some of the Linux distros, customers experienced this undesired behavior on these operating systems.</span></span> 

#### <a name="version-introduced"></a><span data-ttu-id="0b829-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="0b829-110">Version introduced</span></span>

<span data-ttu-id="0b829-111">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="0b829-111">.NET Core 3.0</span></span>

### <a name="recommended-action"></a><span data-ttu-id="0b829-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="0b829-112">Recommended action</span></span>

<span data-ttu-id="0b829-113">Bu değişikliğin farkından daha fazla hiçbir şey yok.</span><span class="sxs-lookup"><span data-stu-id="0b829-113">Nothing specific more than the awareness of this change.</span></span> <span data-ttu-id="0b829-114">Bu değişiklik yalnızca "C" yerel ayar eşlemesini kullanan uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="0b829-114">This change affects only applications that use the "C" locale mapping.</span></span>

### <a name="category"></a><span data-ttu-id="0b829-115">Kategori</span><span class="sxs-lookup"><span data-stu-id="0b829-115">Category</span></span>

<span data-ttu-id="0b829-116">Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="0b829-116">Globalization</span></span> 

### <a name="affected-apis"></a><span data-ttu-id="0b829-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="0b829-117">Affected APIs</span></span>

<span data-ttu-id="0b829-118">Tüm harmanlama ve kültür API 'Leri bu değişiklikten etkilenir.</span><span class="sxs-lookup"><span data-stu-id="0b829-118">All collation and culture APIs are affected by this change.</span></span>

<!--

-->
