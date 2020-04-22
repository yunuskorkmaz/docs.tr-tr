---
ms.openlocfilehash: 2ea9abca7578c2ddf92712a1c597f8f1ff4a5c0c
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021793"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a><span data-ttu-id="2326d-101">FileSystemInfo.Attributes tarafından atılan Yetkisiz ErişimÖzel Durum</span><span class="sxs-lookup"><span data-stu-id="2326d-101">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>

<span data-ttu-id="2326d-102">.NET Core'da, arayan bir dosya özniteliği değerini ayarlamaya çalıştığında ancak yazma izni olmadığında bir <xref:System.UnauthorizedAccessException> atma yapılır.</span><span class="sxs-lookup"><span data-stu-id="2326d-102">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown when the caller attempts to set a file attribute value but doesn't have write permission.</span></span>

#### <a name="change-description"></a><span data-ttu-id="2326d-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="2326d-103">Change description</span></span>

<span data-ttu-id="2326d-104">.NET Framework'de, arayan bir dosya özniteliği değerini ayarlamaya çalıştığında <xref:System.ArgumentException> <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> ancak yazma izni olmadığında bir atma yapılır.</span><span class="sxs-lookup"><span data-stu-id="2326d-104">In .NET Framework, an <xref:System.ArgumentException> is thrown when the caller attempts to set a file attribute value in <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> but doesn't have write permission.</span></span> <span data-ttu-id="2326d-105">.NET Core'da <xref:System.UnauthorizedAccessException> bunun yerine bir atılmıştır.</span><span class="sxs-lookup"><span data-stu-id="2326d-105">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown instead.</span></span> <span data-ttu-id="2326d-106">(.NET Core'da, arayan geçersiz bir dosya özniteliği ayarlamaya çalışırsa yine de bir <xref:System.ArgumentException> atılabilir.)</span><span class="sxs-lookup"><span data-stu-id="2326d-106">(In .NET Core, an <xref:System.ArgumentException> is still thrown if the caller attempts to set an invalid file attribute.)</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2326d-107">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="2326d-107">Version introduced</span></span>

<span data-ttu-id="2326d-108">1.0</span><span class="sxs-lookup"><span data-stu-id="2326d-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2326d-109">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="2326d-109">Recommended action</span></span>

<span data-ttu-id="2326d-110">Gerekli `catch` olduğu gibi <xref:System.UnauthorizedAccessException> bir yerine veya buna ek <xref:System.ArgumentException>olarak, bir yakalamak için herhangi bir deyimdeğiştirin.</span><span class="sxs-lookup"><span data-stu-id="2326d-110">Modify any `catch` statements to catch an <xref:System.UnauthorizedAccessException> instead of, or in addition to, an <xref:System.ArgumentException>, as necessary.</span></span>

#### <a name="category"></a><span data-ttu-id="2326d-111">Kategori</span><span class="sxs-lookup"><span data-stu-id="2326d-111">Category</span></span>

<span data-ttu-id="2326d-112">Çekirdek .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="2326d-112">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2326d-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="2326d-113">Affected APIs</span></span>

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
