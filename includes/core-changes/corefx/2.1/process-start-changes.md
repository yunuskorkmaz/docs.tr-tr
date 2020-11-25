---
ms.openlocfilehash: 9544b65f31772d0f4cee918528a73171fec4de99
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032050"
---
### <a name="change-in-default-value-of-useshellexecute"></a><span data-ttu-id="3bb61-101">UseShellExecute varsayılan değerindeki değişiklik</span><span class="sxs-lookup"><span data-stu-id="3bb61-101">Change in default value of UseShellExecute</span></span>

<span data-ttu-id="3bb61-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> , .NET Core üzerinde varsayılan bir değer içerir `false` .</span><span class="sxs-lookup"><span data-stu-id="3bb61-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> has a default value of `false` on .NET Core.</span></span> <span data-ttu-id="3bb61-103">.NET Framework, varsayılan değeri ' dir `true` .</span><span class="sxs-lookup"><span data-stu-id="3bb61-103">On .NET Framework, its default value is `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3bb61-104">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="3bb61-104">Change description</span></span>

<span data-ttu-id="3bb61-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> bir uygulamayı doğrudan başlatmanıza olanak tanır. Örneğin, Paint 'i Başlatan gibi kodla `Process.Start("mspaint.exe")` .</span><span class="sxs-lookup"><span data-stu-id="3bb61-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> lets you launch an application directly, for example, with code such as `Process.Start("mspaint.exe")` that launches Paint.</span></span> <span data-ttu-id="3bb61-106">Ayrıca, olarak ayarlandıysa ilişkili bir uygulamayı dolaylı olarak başlatmanıza olanak tanır <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `true` .</span><span class="sxs-lookup"><span data-stu-id="3bb61-106">It also lets you indirectly launch an associated application if <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is set to `true`.</span></span> <span data-ttu-id="3bb61-107">.NET Framework ' de, varsayılan değeri, <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `true` `Process.Start("mytextfile.txt")` *. txt* dosyalarını bu düzenleyici ile ilişkilendirdiyseniz Not defteri 'ni başlatacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3bb61-107">On .NET Framework, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `true`, meaning that code such as `Process.Start("mytextfile.txt")` would launch Notepad, if you've associated *.txt* files with that editor.</span></span> <span data-ttu-id="3bb61-108">.NET Framework bir uygulamanın dolaylı olarak başlatılmasını engellemek için, açıkça olarak ayarlamanız gerekir <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `false` .</span><span class="sxs-lookup"><span data-stu-id="3bb61-108">To prevent indirectly launching an app on .NET Framework, you must explicitly set <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="3bb61-109">.NET Core 'da, için varsayılan değer <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `false` .</span><span class="sxs-lookup"><span data-stu-id="3bb61-109">On .NET Core, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `false`.</span></span> <span data-ttu-id="3bb61-110">Bu, varsayılan olarak ilişkili uygulamaların, çağırdığınızda başlatılmayacağı anlamına gelir `Process.Start` .</span><span class="sxs-lookup"><span data-stu-id="3bb61-110">This means that, by default, associated applications are not launched when you call `Process.Start`.</span></span>

<span data-ttu-id="3bb61-111">Bu değişiklik, performans nedenleriyle .NET Core 'da sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="3bb61-111">This change was introduced in .NET Core for performance reasons.</span></span> <span data-ttu-id="3bb61-112">Genellikle, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> bir uygulamayı doğrudan başlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3bb61-112">Typically, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> is used to launch an application directly.</span></span> <span data-ttu-id="3bb61-113">Bir uygulamayı doğrudan başlatmak, Windows kabuğunu dahil etmek ve ilişkili performans maliyetine tabi olmak zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="3bb61-113">Launching an app directly does not need to involve the Windows shell and incur the associated performance cost.</span></span> <span data-ttu-id="3bb61-114">Bu varsayılan örneği daha hızlı hale getirmek için, .NET Core varsayılan değerini <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> olarak değiştirir `false` .</span><span class="sxs-lookup"><span data-stu-id="3bb61-114">To make this default case faster, .NET Core changes the default value of <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="3bb61-115">Gerekirse, daha yavaş yolu kabul edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3bb61-115">You can opt in to the slower path if you need it.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3bb61-116">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="3bb61-116">Version introduced</span></span>

<span data-ttu-id="3bb61-117">2.1</span><span class="sxs-lookup"><span data-stu-id="3bb61-117">2.1</span></span>

> [!NOTE]
> <span data-ttu-id="3bb61-118">.NET Core 'un önceki sürümlerinde `UseShellExecute` Windows için uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="3bb61-118">In earlier versions of .NET Core, `UseShellExecute` was not implemented for Windows.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3bb61-119">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="3bb61-119">Recommended action</span></span>

<span data-ttu-id="3bb61-120">Uygulamanız eski davranışı kullanıyorsa, <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> nesne üzerinde olarak ayarla ' yı çağırın `true` <xref:System.Diagnostics.ProcessStartInfo> .</span><span class="sxs-lookup"><span data-stu-id="3bb61-120">If your app relies on the old behavior, call <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> with <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> set to `true` on the <xref:System.Diagnostics.ProcessStartInfo> object.</span></span>

#### <a name="category"></a><span data-ttu-id="3bb61-121">Kategori</span><span class="sxs-lookup"><span data-stu-id="3bb61-121">Category</span></span>

<span data-ttu-id="3bb61-122">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="3bb61-122">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3bb61-123">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="3bb61-123">Affected APIs</span></span>

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
