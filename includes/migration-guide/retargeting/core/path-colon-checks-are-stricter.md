---
ms.openlocfilehash: 6af63c0a58a3273aa98fa70f22e3637b481806b4
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497387"
---
### <a name="path-colon-checks-are-stricter"></a><span data-ttu-id="e8da3-101">Yol noktalı virgül denetimleri daha sıkı</span><span class="sxs-lookup"><span data-stu-id="e8da3-101">Path colon checks are stricter</span></span>

#### <a name="details"></a><span data-ttu-id="e8da3-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e8da3-102">Details</span></span>

<span data-ttu-id="e8da3-103">.NET Framework 4.6.2 ' de, daha önce desteklenmeyen yolları (hem length hem de biçiminde) desteklemeye yönelik bir dizi değişiklik yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="e8da3-103">In .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in length and format).</span></span> <span data-ttu-id="e8da3-104">Doğru sürücü ayırıcı (iki nokta üst üste) olup olmadığını denetler ve daha önceden toleranslı olan birkaç seçim yolu API 'sindeki bazı URI yollarını engellemeyi yan etkisi olan daha doğru yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="e8da3-104">Checks for proper drive separator (colon) syntax were made more correct, which had the side effect of blocking some URI paths in a few select Path APIs where they were previously tolerated.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e8da3-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="e8da3-105">Suggestion</span></span>

<span data-ttu-id="e8da3-106">Bir URI 'yi etkilenen API 'lere geçiriyorsanız, dizeyi önce geçerli bir yol olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e8da3-106">If passing a URI to affected APIs, modify the string to be a legal path first.</span></span>

- <span data-ttu-id="e8da3-107">Şemayı, URL 'lerden el ile kaldırın (örneğin, URL 'lerden kaldırın `file://` ).</span><span class="sxs-lookup"><span data-stu-id="e8da3-107">Remove the scheme from URLs manually (for example, remove `file://` from URLs).</span></span>

- <span data-ttu-id="e8da3-108">URI 'yi <xref:System.Uri> sınıfa geçirin ve kullanın <xref:System.Uri.LocalPath> .</span><span class="sxs-lookup"><span data-stu-id="e8da3-108">Pass the URI to the <xref:System.Uri> class and use <xref:System.Uri.LocalPath>.</span></span>

<span data-ttu-id="e8da3-109">Alternatif olarak, `Switch.System.IO.UseLegacyPathHandling` AppContext anahtarını olarak ayarlayarak yeni yol normalleştirmesini devre dışı bırakabilirsiniz `true` .</span><span class="sxs-lookup"><span data-stu-id="e8da3-109">Alternatively, you can opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling` AppContext switch to `true`.</span></span>

| <span data-ttu-id="e8da3-110">Name</span><span class="sxs-lookup"><span data-stu-id="e8da3-110">Name</span></span>    | <span data-ttu-id="e8da3-111">Değer</span><span class="sxs-lookup"><span data-stu-id="e8da3-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e8da3-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="e8da3-112">Scope</span></span>   | <span data-ttu-id="e8da3-113">Edge</span><span class="sxs-lookup"><span data-stu-id="e8da3-113">Edge</span></span>        |
| <span data-ttu-id="e8da3-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="e8da3-114">Version</span></span> | <span data-ttu-id="e8da3-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="e8da3-115">4.6.2</span></span>       |
| <span data-ttu-id="e8da3-116">Tür</span><span class="sxs-lookup"><span data-stu-id="e8da3-116">Type</span></span>    | <span data-ttu-id="e8da3-117">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="e8da3-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="e8da3-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e8da3-118">Affected APIs</span></span>

- <xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType>
- <xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType>
