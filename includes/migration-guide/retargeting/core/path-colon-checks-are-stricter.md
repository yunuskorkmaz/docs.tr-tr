---
ms.openlocfilehash: 3e4a5936bbac4e77efc5f7e68b55ddf49bae5d43
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614715"
---
### <a name="path-colon-checks-are-stricter"></a><span data-ttu-id="00d1b-101">Yol noktalı virgül denetimleri daha sıkı</span><span class="sxs-lookup"><span data-stu-id="00d1b-101">Path colon checks are stricter</span></span>

#### <a name="details"></a><span data-ttu-id="00d1b-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="00d1b-102">Details</span></span>

<span data-ttu-id="00d1b-103">.NET Framework 4.6.2 ' de, daha önce desteklenmeyen yolları (hem length hem de biçiminde) desteklemeye yönelik bir dizi değişiklik yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="00d1b-103">In .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in length and format).</span></span> <span data-ttu-id="00d1b-104">Uygun sürücü ayırıcı (iki nokta üst üste) olup olmadığını denetler ve daha doğru bir şekilde, birkaç seçim yolu API 'SI ile kullanım dışı olarak kullanıldıkları yerde bazı URI yollarını engellemenin yan etkisi vardı.</span><span class="sxs-lookup"><span data-stu-id="00d1b-104">Checks for proper drive separator (colon) syntax were made more correct, which had the side effect of blocking some URI paths in a few select Path APIs where they used to be tolerated.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="00d1b-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="00d1b-105">Suggestion</span></span>

<span data-ttu-id="00d1b-106">Bir URI 'yi etkilenen API 'lere geçiriyorsanız, dizeyi önce geçerli bir yol olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="00d1b-106">If passing a URI to affected APIs, modify the string to be a legal path first.</span></span><ul><li><span data-ttu-id="00d1b-107">Şemayı, URL 'lerden el ile kaldırın (örn. `file://` URL 'lerden Kaldır)</span><span class="sxs-lookup"><span data-stu-id="00d1b-107">Remove the scheme from URLs manually (e.g. remove `file://` from URLs)</span></span>

- <span data-ttu-id="00d1b-108">URI 'yi <xref:System.Uri> sınıfa geçirin ve kullanın<xref:System.Uri.LocalPath></span><span class="sxs-lookup"><span data-stu-id="00d1b-108">Pass the URI to the <xref:System.Uri> class and use <xref:System.Uri.LocalPath></span></span>

<span data-ttu-id="00d1b-109">Alternatif olarak, `Switch.System.IO.UseLegacyPathHandling` AppContext anahtarını true olarak ayarlayarak yeni yol normalleştirmesini devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00d1b-109">Alternatively, you can opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling` AppContext switch to true.</span></span>

| <span data-ttu-id="00d1b-110">Name</span><span class="sxs-lookup"><span data-stu-id="00d1b-110">Name</span></span>    | <span data-ttu-id="00d1b-111">Değer</span><span class="sxs-lookup"><span data-stu-id="00d1b-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="00d1b-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="00d1b-112">Scope</span></span>   | <span data-ttu-id="00d1b-113">Edge</span><span class="sxs-lookup"><span data-stu-id="00d1b-113">Edge</span></span>        |
| <span data-ttu-id="00d1b-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="00d1b-114">Version</span></span> | <span data-ttu-id="00d1b-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="00d1b-115">4.6.2</span></span>       |
| <span data-ttu-id="00d1b-116">Tür</span><span class="sxs-lookup"><span data-stu-id="00d1b-116">Type</span></span>    | <span data-ttu-id="00d1b-117">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="00d1b-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="00d1b-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="00d1b-118">Affected APIs</span></span>

- <xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType>
- <xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType>
