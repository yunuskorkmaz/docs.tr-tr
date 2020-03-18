---
ms.openlocfilehash: 4091bdcf7d9ed8872aed5faa6e6d3ed143903787
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449419"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a><span data-ttu-id="08b96-101">FileSystemInfo.Attributes tarafından atılan Yetkisiz ErişimÖzel Durum</span><span class="sxs-lookup"><span data-stu-id="08b96-101">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>

<span data-ttu-id="08b96-102">.NET Core'da, arayan bir dosya özniteliği değerini ayarlamaya çalıştığında ancak yazma izni olmadığında bir <xref:System.UnauthorizedAccessException> atma yapılır.</span><span class="sxs-lookup"><span data-stu-id="08b96-102">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown when the caller attempts to set a file attribute value but doesn't have write permission.</span></span>

#### <a name="change-description"></a><span data-ttu-id="08b96-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="08b96-103">Change description</span></span>

<span data-ttu-id="08b96-104">.NET Framework'de, arayan bir dosya özniteliği değerini ayarlamaya çalıştığında <xref:System.ArgumentException> <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> ancak yazma izni olmadığında bir atma yapılır.</span><span class="sxs-lookup"><span data-stu-id="08b96-104">In .NET Framework, an <xref:System.ArgumentException> is thrown when the caller attempts to set a file attribute value in <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> but doesn't have write permission.</span></span> <span data-ttu-id="08b96-105">.NET Core'da <xref:System.UnauthorizedAccessException> bunun yerine bir atılmıştır.</span><span class="sxs-lookup"><span data-stu-id="08b96-105">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown instead.</span></span> <span data-ttu-id="08b96-106">(.NET Core'da, arayan geçersiz bir dosya özniteliği ayarlamaya çalışırsa yine de bir <xref:System.ArgumentException> atılabilir.)</span><span class="sxs-lookup"><span data-stu-id="08b96-106">(In .NET Core, an <xref:System.ArgumentException> is still thrown if the caller attempts to set an invalid file attribute.)</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="08b96-107">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="08b96-107">Version introduced</span></span>

<span data-ttu-id="08b96-108">1.0</span><span class="sxs-lookup"><span data-stu-id="08b96-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="08b96-109">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="08b96-109">Recommended action</span></span>

<span data-ttu-id="08b96-110">Gerekli `catch` olduğu gibi <xref:System.UnauthorizedAccessException> bir yerine veya buna ek <xref:System.ArgumentException>olarak, bir yakalamak için herhangi bir deyimdeğiştirin.</span><span class="sxs-lookup"><span data-stu-id="08b96-110">Modify any `catch` statements to catch an <xref:System.UnauthorizedAccessException> instead of, or in addition to, an <xref:System.ArgumentException>, as necessary.</span></span>

#### <a name="category"></a><span data-ttu-id="08b96-111">Kategori</span><span class="sxs-lookup"><span data-stu-id="08b96-111">Category</span></span>

<span data-ttu-id="08b96-112">CoreFx</span><span class="sxs-lookup"><span data-stu-id="08b96-112">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="08b96-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="08b96-113">Affected APIs</span></span>

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
