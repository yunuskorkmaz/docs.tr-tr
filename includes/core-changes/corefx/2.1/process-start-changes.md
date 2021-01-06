---
ms.openlocfilehash: dcc64fe651b219ff1416c0afcdb4c6d275160f4b
ms.sourcegitcommit: 88fbb019b84c2d044d11fb4f6004aec07f2b25b1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97911568"
---
### <a name="change-in-default-value-of-useshellexecute"></a><span data-ttu-id="4b0ce-101">UseShellExecute varsayılan değerindeki değişiklik</span><span class="sxs-lookup"><span data-stu-id="4b0ce-101">Change in default value of UseShellExecute</span></span>

<span data-ttu-id="4b0ce-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> , .NET Core üzerinde varsayılan bir değer içerir `false` .</span><span class="sxs-lookup"><span data-stu-id="4b0ce-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> has a default value of `false` on .NET Core.</span></span> <span data-ttu-id="4b0ce-103">.NET Framework, varsayılan değeri ' dir `true` .</span><span class="sxs-lookup"><span data-stu-id="4b0ce-103">On .NET Framework, its default value is `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="4b0ce-104">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="4b0ce-104">Change description</span></span>

<span data-ttu-id="4b0ce-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> bir uygulamayı doğrudan başlatmanıza olanak tanır. Örneğin, Paint 'i Başlatan gibi kodla `Process.Start("mspaint.exe")` .</span><span class="sxs-lookup"><span data-stu-id="4b0ce-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> lets you launch an application directly, for example, with code such as `Process.Start("mspaint.exe")` that launches Paint.</span></span> <span data-ttu-id="4b0ce-106">Ayrıca, olarak ayarlandıysa ilişkili bir uygulamayı dolaylı olarak başlatmanıza olanak tanır <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `true` .</span><span class="sxs-lookup"><span data-stu-id="4b0ce-106">It also lets you indirectly launch an associated application if <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is set to `true`.</span></span> <span data-ttu-id="4b0ce-107">.NET Framework ' de, varsayılan değeri, <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `true` `Process.Start("mytextfile.txt")` *. txt* dosyalarını bu düzenleyici ile ilişkilendirdiyseniz Not defteri 'ni başlatacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4b0ce-107">On .NET Framework, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `true`, meaning that code such as `Process.Start("mytextfile.txt")` would launch Notepad, if you've associated *.txt* files with that editor.</span></span> <span data-ttu-id="4b0ce-108">.NET Framework bir uygulamanın dolaylı olarak başlatılmasını engellemek için, açıkça olarak ayarlamanız gerekir <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `false` .</span><span class="sxs-lookup"><span data-stu-id="4b0ce-108">To prevent indirectly launching an app on .NET Framework, you must explicitly set <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="4b0ce-109">.NET Core 'da, için varsayılan değer <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `false` .</span><span class="sxs-lookup"><span data-stu-id="4b0ce-109">On .NET Core, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `false`.</span></span> <span data-ttu-id="4b0ce-110">Bu, varsayılan olarak ilişkili uygulamaların, çağırdığınızda başlatılmayacağı anlamına gelir `Process.Start` .</span><span class="sxs-lookup"><span data-stu-id="4b0ce-110">This means that, by default, associated applications are not launched when you call `Process.Start`.</span></span>

<span data-ttu-id="4b0ce-111">Üzerinde aşağıdaki özellikler <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType> yalnızca şu durumlarda işlevsel olur <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `true` :</span><span class="sxs-lookup"><span data-stu-id="4b0ce-111">The following properties on <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType> are only functional when <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `true`:</span></span>

- <xref:System.Diagnostics.ProcessStartInfo.CreateNoWindow?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo.ErrorDialog?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo.Verb?displayProperty=nameWithType>
- <span data-ttu-id="4b0ce-112"><xref:System.Diagnostics.ProcessStartInfo.WindowStyle?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4b0ce-112"><xref:System.Diagnostics.ProcessStartInfo.WindowStyle?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="4b0ce-113">Bu değişiklik, performans nedenleriyle .NET Core 'da sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="4b0ce-113">This change was introduced in .NET Core for performance reasons.</span></span> <span data-ttu-id="4b0ce-114">Genellikle, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> bir uygulamayı doğrudan başlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4b0ce-114">Typically, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> is used to launch an application directly.</span></span> <span data-ttu-id="4b0ce-115">Bir uygulamayı doğrudan başlatmak, Windows kabuğunu dahil etmek ve ilişkili performans maliyetine tabi olmak zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="4b0ce-115">Launching an app directly does not need to involve the Windows shell and incur the associated performance cost.</span></span> <span data-ttu-id="4b0ce-116">Bu varsayılan örneği daha hızlı hale getirmek için, .NET Core varsayılan değerini <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> olarak değiştirir `false` .</span><span class="sxs-lookup"><span data-stu-id="4b0ce-116">To make this default case faster, .NET Core changes the default value of <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="4b0ce-117">Gerekirse, daha yavaş yolu kabul edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4b0ce-117">You can opt in to the slower path if you need it.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4b0ce-118">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="4b0ce-118">Version introduced</span></span>

<span data-ttu-id="4b0ce-119">2.1</span><span class="sxs-lookup"><span data-stu-id="4b0ce-119">2.1</span></span>

> [!NOTE]
> <span data-ttu-id="4b0ce-120">.NET Core 'un önceki sürümlerinde `UseShellExecute` Windows için uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="4b0ce-120">In earlier versions of .NET Core, `UseShellExecute` was not implemented for Windows.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4b0ce-121">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="4b0ce-121">Recommended action</span></span>

<span data-ttu-id="4b0ce-122">Uygulamanız eski davranışı kullanıyorsa, <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> nesne üzerinde olarak ayarla ' yı çağırın `true` <xref:System.Diagnostics.ProcessStartInfo> .</span><span class="sxs-lookup"><span data-stu-id="4b0ce-122">If your app relies on the old behavior, call <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> with <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> set to `true` on the <xref:System.Diagnostics.ProcessStartInfo> object.</span></span>

#### <a name="category"></a><span data-ttu-id="4b0ce-123">Kategori</span><span class="sxs-lookup"><span data-stu-id="4b0ce-123">Category</span></span>

<span data-ttu-id="4b0ce-124">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="4b0ce-124">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4b0ce-125">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="4b0ce-125">Affected APIs</span></span>

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
