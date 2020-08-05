---
ms.openlocfilehash: 74c3d3247912dcd638a9379d54e682967c5e400b
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302729"
---
### <a name="globalization-apis-use-icu-libraries-on-windows"></a><span data-ttu-id="5be2b-101">Genelleştirme API 'Leri Windows üzerinde ıCU kitaplıklarını kullanır</span><span class="sxs-lookup"><span data-stu-id="5be2b-101">Globalization APIs use ICU libraries on Windows</span></span>

<span data-ttu-id="5be2b-102">.NET 5,0 ve sonraki sürümleri, Windows 10 Mayıs 2019 güncelleştirme veya sonrasında çalışırken Genelleştirme işlevselliği için [Unicode (ıCU)](http://site.icu-project.org/home) kitaplıklarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="5be2b-102">.NET 5.0 and later versions use [International Components for Unicode (ICU)](http://site.icu-project.org/home) libraries for globalization functionality when running on Windows 10 May 2019 Update or later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5be2b-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="5be2b-103">Change description</span></span>

<span data-ttu-id="5be2b-104">Daha önce .NET kitaplıkları, Genelleştirme işlevselliği için [ulusal dil desteği (NLS)](/windows/win32/intl/national-language-support) API 'lerini kullandı.</span><span class="sxs-lookup"><span data-stu-id="5be2b-104">Previously, .NET libraries used [National Language Support (NLS)](/windows/win32/intl/national-language-support) APIs for globalization functionality.</span></span> <span data-ttu-id="5be2b-105">Örneğin, NLS işlevleri, tarih ve saat biçimi desenleri gibi kültür verilerini almak, dizeleri karşılaştırmak ve uygun kültür içinde dize büyük harfleri gerçekleştirmek için kullanılmıştır.</span><span class="sxs-lookup"><span data-stu-id="5be2b-105">For example, NLS functions were used to get culture data, such as date and time format patterns, compare strings, and perform string casing in the appropriate culture.</span></span>

<span data-ttu-id="5be2b-106">.NET 5,0 ' den itibaren, bir uygulama Windows 10 Mayıs 2019 veya sonraki sürümlerde çalışıyorsa, .NET kitaplıkları [ICU](http://site.icu-project.org/home) genelleştirme API 'lerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5be2b-106">Starting in .NET 5.0, if an app is running on Windows 10 May 2019 Update or later, .NET libraries use [ICU](http://site.icu-project.org/home) globalization APIs.</span></span> <span data-ttu-id="5be2b-107">Windows 10 Mayıs 2019 güncelleştirmesi ve sonraki sürümleri ıCU yerel kitaplığıyla birlikte sevk.</span><span class="sxs-lookup"><span data-stu-id="5be2b-107">Windows 10 May 2019 Update and later versions ship with the ICU native library.</span></span> <span data-ttu-id="5be2b-108">.NET çalışma zamanı ıCU 'yi yükleye, bunun yerine NLS kullanır.</span><span class="sxs-lookup"><span data-stu-id="5be2b-108">If the .NET runtime can't load ICU, it uses NLS instead.</span></span>

<span data-ttu-id="5be2b-109">Bu değişiklik iki nedenden dolayı sunulmuştur:</span><span class="sxs-lookup"><span data-stu-id="5be2b-109">This change was introduced for two reasons:</span></span>

- <span data-ttu-id="5be2b-110">Uygulamalar Linux, macOS ve Windows dahil olmak üzere platformlar genelinde aynı Genelleştirme davranışına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5be2b-110">Apps have the same globalization behavior across platforms, including Linux, macOS, and Windows.</span></span>
- <span data-ttu-id="5be2b-111">Uygulamalar, özel ıCU kitaplıklarını kullanarak Genelleştirme davranışını denetleyebilir.</span><span class="sxs-lookup"><span data-stu-id="5be2b-111">Apps can control globalization behavior by using custom ICU libraries.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5be2b-112">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="5be2b-112">Version introduced</span></span>

<span data-ttu-id="5be2b-113">.NET 5,0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="5be2b-113">.NET 5.0 Preview 4</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5be2b-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="5be2b-114">Recommended action</span></span>

<span data-ttu-id="5be2b-115">Geliştiricinin bölümünde herhangi bir eylem gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5be2b-115">No action is required on the part of the developer.</span></span> <span data-ttu-id="5be2b-116">Ancak, NLS genelleştirme API 'Lerini kullanmaya devam etmek istiyorsanız, bu davranışa dönmek için bir [çalışma zamanı anahtarı](../../../../docs/core/run-time-config/globalization.md#nls) ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5be2b-116">However, if you wish to continue using NLS globalization APIs, you can set a [run-time switch](../../../../docs/core/run-time-config/globalization.md#nls) to revert to that behavior.</span></span> <span data-ttu-id="5be2b-117">Kullanılabilir anahtarlar hakkında daha fazla bilgi için bkz. [.NET Genelleştirme ve ıCU](/dotnet/standard/globalization-localization/globalization-icu) makalesi.</span><span class="sxs-lookup"><span data-stu-id="5be2b-117">For more information about the available switches, see the [.NET globalization and ICU](/dotnet/standard/globalization-localization/globalization-icu) article.</span></span>

#### <a name="category"></a><span data-ttu-id="5be2b-118">Kategori</span><span class="sxs-lookup"><span data-stu-id="5be2b-118">Category</span></span>

<span data-ttu-id="5be2b-119">Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="5be2b-119">Globalization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5be2b-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="5be2b-120">Affected APIs</span></span>

- <xref:System.Span%601?displayProperty=fullName>
- <xref:System.String?displayProperty=fullName>
- <span data-ttu-id="5be2b-121">Ad alanındaki çoğu tür <xref:System.Globalization?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="5be2b-121">Most types in the <xref:System.Globalization?displayProperty=fullName> namespace</span></span>

<!--

#### Affected APIs

- ``T:System.Span`1``
- `T:System.String`
- `N:System.Globalization`

-->
