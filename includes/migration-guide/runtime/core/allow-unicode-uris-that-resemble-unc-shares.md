---
ms.openlocfilehash: 1047f4028697a73741470d1aac8b3aeed37be217
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496812"
---
### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a><span data-ttu-id="b8348-101">UNC Paylaşımlarına benzeyen URI 'Lerinde Unicode 'a izin ver</span><span class="sxs-lookup"><span data-stu-id="b8348-101">Allow Unicode in URIs that resemble UNC shares</span></span>

#### <a name="details"></a><span data-ttu-id="b8348-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b8348-102">Details</span></span>

<span data-ttu-id="b8348-103">' De <xref:System.Uri?displayProperty=fullName> , hem UNC paylaşma adı hem de Unicode karakterler içeren bir dosya URI 'si oluşturmak, artık geçersiz iç duruma sahip BIR URI ile sonuçlanmaz.</span><span class="sxs-lookup"><span data-stu-id="b8348-103">In <xref:System.Uri?displayProperty=fullName>, constructing a file URI containing both a UNC share name and Unicode characters will no longer result in a URI with invalid internal state.</span></span> <span data-ttu-id="b8348-104">Bu davranış yalnızca aşağıdakilerin tümü doğru olduğunda değişir:</span><span class="sxs-lookup"><span data-stu-id="b8348-104">The behavior will change only when all of the following are true:</span></span><ul><li><span data-ttu-id="b8348-105">URI şemaya sahiptir <code>file:</code> ve ardından dört veya daha fazla eğik çizgi gelir.</span><span class="sxs-lookup"><span data-stu-id="b8348-105">The URI has the scheme <code>file:</code> and is followed by four or more slashes.</span></span></li><li><span data-ttu-id="b8348-106">Ana bilgisayar adı, alt çizgi veya ayrılmış olmayan başka bir sembol ile başlar.</span><span class="sxs-lookup"><span data-stu-id="b8348-106">The host name begins with an underscore or other non-reserved symbol.</span></span></li><li><span data-ttu-id="b8348-107">URI Unicode karakterler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="b8348-107">The URI contains Unicode characters.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="b8348-108">Öneri</span><span class="sxs-lookup"><span data-stu-id="b8348-108">Suggestion</span></span>

<span data-ttu-id="b8348-109">Bir şekilde Unicode içeren URI 'Ler ile çalışan uygulamalar, UNC Paylaşımlarına yönelik başvurulara izin vermek için bu davranışı çalıp.</span><span class="sxs-lookup"><span data-stu-id="b8348-109">Applications working with URIs consistently containing Unicode could have conceivably used this behavior to disallow references to UNC shares.</span></span> <span data-ttu-id="b8348-110">Bunun yerine bu uygulamalar kullanılmalıdır <xref:System.Uri.IsUnc> .</span><span class="sxs-lookup"><span data-stu-id="b8348-110">Those applications should use <xref:System.Uri.IsUnc> instead.</span></span>

| <span data-ttu-id="b8348-111">Name</span><span class="sxs-lookup"><span data-stu-id="b8348-111">Name</span></span>    | <span data-ttu-id="b8348-112">Değer</span><span class="sxs-lookup"><span data-stu-id="b8348-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b8348-113">Kapsam</span><span class="sxs-lookup"><span data-stu-id="b8348-113">Scope</span></span>   |<span data-ttu-id="b8348-114">Edge</span><span class="sxs-lookup"><span data-stu-id="b8348-114">Edge</span></span>|
|<span data-ttu-id="b8348-115">Sürüm</span><span class="sxs-lookup"><span data-stu-id="b8348-115">Version</span></span>|<span data-ttu-id="b8348-116">4.7.2</span><span class="sxs-lookup"><span data-stu-id="b8348-116">4.7.2</span></span>|
|<span data-ttu-id="b8348-117">Tür</span><span class="sxs-lookup"><span data-stu-id="b8348-117">Type</span></span>|<span data-ttu-id="b8348-118">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="b8348-118">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="b8348-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="b8348-119">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Uri`

-->
