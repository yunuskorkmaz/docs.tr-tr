---
ms.openlocfilehash: 2ea9abca7578c2ddf92712a1c597f8f1ff4a5c0c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032078"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a><span data-ttu-id="a6781-101">Fılesystemınfo. Attributes tarafından oluşturulan UnauthorizedAccessException</span><span class="sxs-lookup"><span data-stu-id="a6781-101">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>

<span data-ttu-id="a6781-102">.NET Core 'da, <xref:System.UnauthorizedAccessException> çağıran bir dosya özniteliği değeri ayarlamaya çalıştığında ancak yazma iznine sahip olmadığında bir oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a6781-102">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown when the caller attempts to set a file attribute value but doesn't have write permission.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a6781-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="a6781-103">Change description</span></span>

<span data-ttu-id="a6781-104">.NET Framework, <xref:System.ArgumentException> çağıran bir dosya özniteliği değeri ayarlamaya çalıştığında, <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> ancak yazma iznine sahip olmadığında oluşur.</span><span class="sxs-lookup"><span data-stu-id="a6781-104">In .NET Framework, an <xref:System.ArgumentException> is thrown when the caller attempts to set a file attribute value in <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> but doesn't have write permission.</span></span> <span data-ttu-id="a6781-105">.NET Core 'da <xref:System.UnauthorizedAccessException> bunun yerine bir oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a6781-105">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown instead.</span></span> <span data-ttu-id="a6781-106">(.NET Core 'da, <xref:System.ArgumentException> çağıran geçersiz bir dosya özniteliği ayarlamaya çalışırsa yine bir oluşturulur.)</span><span class="sxs-lookup"><span data-stu-id="a6781-106">(In .NET Core, an <xref:System.ArgumentException> is still thrown if the caller attempts to set an invalid file attribute.)</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a6781-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="a6781-107">Version introduced</span></span>

<span data-ttu-id="a6781-108">1,0</span><span class="sxs-lookup"><span data-stu-id="a6781-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a6781-109">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="a6781-109">Recommended action</span></span>

<span data-ttu-id="a6781-110">Gerektiğinde, `catch` veya buna ek olarak, bir yerine yakalamak için herhangi bir deyimi değiştirin <xref:System.UnauthorizedAccessException> <xref:System.ArgumentException> .</span><span class="sxs-lookup"><span data-stu-id="a6781-110">Modify any `catch` statements to catch an <xref:System.UnauthorizedAccessException> instead of, or in addition to, an <xref:System.ArgumentException>, as necessary.</span></span>

#### <a name="category"></a><span data-ttu-id="a6781-111">Kategori</span><span class="sxs-lookup"><span data-stu-id="a6781-111">Category</span></span>

<span data-ttu-id="a6781-112">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="a6781-112">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a6781-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a6781-113">Affected APIs</span></span>

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
