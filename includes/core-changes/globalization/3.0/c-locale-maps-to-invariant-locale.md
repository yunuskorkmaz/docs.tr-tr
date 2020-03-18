---
ms.openlocfilehash: d35de48dd22003c851cf5dba9e8517ec48b9217b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567775"
---
### <a name="c-locale-maps-to-the-invariant-locale"></a><span data-ttu-id="65cf3-101">Değişmez yerel ekiyle "C" yerel eşlemleri</span><span class="sxs-lookup"><span data-stu-id="65cf3-101">"C" locale maps to the invariant locale</span></span>

<span data-ttu-id="65cf3-102">.NET Core 2.2 ve önceki sürümler, "C" yerelsini en_US_POSIX yerel le eşleyen varsayılan Yoğun Bakım Davranışı'na bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="65cf3-102">.NET Core 2.2 and earlier versions depend on the default ICU behavior, which maps the "C" locale to the en_US_POSIX locale.</span></span> <span data-ttu-id="65cf3-103">Büyük/küçük harf duyarsız dize karşılaştırmalarını desteklemediği için en_US_POSIX yerel alanı istenmeyen bir harmanlama davranışına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="65cf3-103">The en_US_POSIX locale has an undesirable collation behavior, because it doesn't support case-insensitive string comparisons.</span></span> <span data-ttu-id="65cf3-104">Bazı Linux dağıtımları "C" yerel ayarını varsayılan yerel ayar olarak ayarladıklarından, kullanıcılar beklenmeyen davranışlar yaşıyordu.</span><span class="sxs-lookup"><span data-stu-id="65cf3-104">Because some Linux distributions set the "C" locale as the default locale, users were experiencing unexpected behavior.</span></span>

#### <a name="change-description"></a><span data-ttu-id="65cf3-105">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="65cf3-105">Change description</span></span>

<span data-ttu-id="65cf3-106">.NET Core 3.0 ile başlayarak, "C" yerel eşleme en_US_POSIX yerine Değişmez yerel eşlemi kullanmak üzere değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="65cf3-106">Starting with .NET Core 3.0, the "C" locale mapping has changed to use the Invariant locale instead of en_US_POSIX.</span></span> <span data-ttu-id="65cf3-107">Değişmez eşleme için "C" yerel eşleme tutarlılık için Windows'a da uygulanır.</span><span class="sxs-lookup"><span data-stu-id="65cf3-107">The "C" locale to Invariant mapping is also applied to Windows for consistency.</span></span>

<span data-ttu-id="65cf3-108">"C"yi en_US_POSIX kültüre eşleme, en_US_POSIX hızlı servis talebi duyarsız sıralama/arama dize işlemlerini desteklemediği için müşteri karışıklığına neden oldu.</span><span class="sxs-lookup"><span data-stu-id="65cf3-108">Mapping "C" to en_US_POSIX culture caused customer confusion, because en_US_POSIX doesn't support case insensitive sorting/searching string operations.</span></span> <span data-ttu-id="65cf3-109">"C" yerel alanı, Linux dağıtımlarının bazılarında varsayılan bir yerel alan olarak kullanıldığından, müşteriler bu işletim sistemlerinde bu istenmeyen davranışı yaşadılar.</span><span class="sxs-lookup"><span data-stu-id="65cf3-109">Because the "C" locale is used as a default locale in some of the Linux distros, customers experienced this undesired behavior on these operating systems.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="65cf3-110">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="65cf3-110">Version introduced</span></span>

<span data-ttu-id="65cf3-111">3,0</span><span class="sxs-lookup"><span data-stu-id="65cf3-111">3.0</span></span>

### <a name="recommended-action"></a><span data-ttu-id="65cf3-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="65cf3-112">Recommended action</span></span>

<span data-ttu-id="65cf3-113">Bu değişikliğin farkındalığından daha özel bir şey yok.</span><span class="sxs-lookup"><span data-stu-id="65cf3-113">Nothing specific more than the awareness of this change.</span></span> <span data-ttu-id="65cf3-114">Bu değişiklik yalnızca "C" yerel eşleme eşlemesi kullanan uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="65cf3-114">This change affects only applications that use the "C" locale mapping.</span></span>

### <a name="category"></a><span data-ttu-id="65cf3-115">Kategori</span><span class="sxs-lookup"><span data-stu-id="65cf3-115">Category</span></span>

<span data-ttu-id="65cf3-116">Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="65cf3-116">Globalization</span></span>

### <a name="affected-apis"></a><span data-ttu-id="65cf3-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="65cf3-117">Affected APIs</span></span>

<span data-ttu-id="65cf3-118">Tüm harmanlama ve kültür API'leri bu değişiklikden etkilenir.</span><span class="sxs-lookup"><span data-stu-id="65cf3-118">All collation and culture APIs are affected by this change.</span></span>

<!--

-->
