---
ms.openlocfilehash: 4091bdcf7d9ed8872aed5faa6e6d3ed143903787
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449419"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a><span data-ttu-id="365d2-101">Fılesystemınfo. Attributes tarafından oluşturulan UnauthorizedAccessException</span><span class="sxs-lookup"><span data-stu-id="365d2-101">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>

<span data-ttu-id="365d2-102">.NET Core 'da, çağıran bir dosya özniteliği değeri ayarlamaya çalıştığında ancak yazma iznine sahip olmadığında <xref:System.UnauthorizedAccessException> oluşur.</span><span class="sxs-lookup"><span data-stu-id="365d2-102">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown when the caller attempts to set a file attribute value but doesn't have write permission.</span></span>

#### <a name="change-description"></a><span data-ttu-id="365d2-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="365d2-103">Change description</span></span>

<span data-ttu-id="365d2-104">.NET Framework, çağıran <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> bir dosya özniteliği değeri ayarlamaya çalıştığında ancak yazma iznine sahip olmayan bir <xref:System.ArgumentException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="365d2-104">In .NET Framework, an <xref:System.ArgumentException> is thrown when the caller attempts to set a file attribute value in <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> but doesn't have write permission.</span></span> <span data-ttu-id="365d2-105">.NET Core 'da bunun yerine bir <xref:System.UnauthorizedAccessException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="365d2-105">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown instead.</span></span> <span data-ttu-id="365d2-106">(.NET Core 'da, çağıran geçersiz bir dosya özniteliği ayarlamaya çalışırsa <xref:System.ArgumentException> yine de oluşturulur.)</span><span class="sxs-lookup"><span data-stu-id="365d2-106">(In .NET Core, an <xref:System.ArgumentException> is still thrown if the caller attempts to set an invalid file attribute.)</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="365d2-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="365d2-107">Version introduced</span></span>

<span data-ttu-id="365d2-108">1.0</span><span class="sxs-lookup"><span data-stu-id="365d2-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="365d2-109">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="365d2-109">Recommended action</span></span>

<span data-ttu-id="365d2-110">`catch` deyimlerini, gerektiğinde bir <xref:System.ArgumentException>veya buna ek olarak <xref:System.UnauthorizedAccessException> yakalamak üzere değiştirin.</span><span class="sxs-lookup"><span data-stu-id="365d2-110">Modify any `catch` statements to catch an <xref:System.UnauthorizedAccessException> instead of, or in addition to, an <xref:System.ArgumentException>, as necessary.</span></span>

#### <a name="category"></a><span data-ttu-id="365d2-111">Kategori</span><span class="sxs-lookup"><span data-stu-id="365d2-111">Category</span></span>

<span data-ttu-id="365d2-112">CoreFx</span><span class="sxs-lookup"><span data-stu-id="365d2-112">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="365d2-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="365d2-113">Affected APIs</span></span>

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
