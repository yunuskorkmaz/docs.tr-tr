---
ms.openlocfilehash: 7c0930f6606aa96d2863dc740aef8e9cab724b37
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344857"
---
### <a name="change-in-default-value-of-useshellexecute"></a><span data-ttu-id="dfce1-101">UseShellExecute varsayılan değerindeki değişiklik</span><span class="sxs-lookup"><span data-stu-id="dfce1-101">Change in default value of UseShellExecute</span></span>

<span data-ttu-id="dfce1-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `false` varsayılan değeri .NET Core üzerinde vardır.</span><span class="sxs-lookup"><span data-stu-id="dfce1-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> has a default value of `false` on .NET Core.</span></span> <span data-ttu-id="dfce1-103">.NET Framework, varsayılan değeri `true`' dir.</span><span class="sxs-lookup"><span data-stu-id="dfce1-103">On .NET Framework, its default value is `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="dfce1-104">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="dfce1-104">Change description</span></span>

<span data-ttu-id="dfce1-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>, bir uygulamayı doğrudan başlatmanıza olanak tanır. Örneğin, Paint 'i Başlatan `Process.Start("mspaint.exe")` gibi kodla.</span><span class="sxs-lookup"><span data-stu-id="dfce1-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> lets you launch an application directly, for example, with code such as `Process.Start("mspaint.exe")` that launches Paint.</span></span> <span data-ttu-id="dfce1-106">Ayrıca, <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `true`olarak ayarlandıysa ilişkili uygulamayı dolaylı olarak başlatmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="dfce1-106">It also lets you indirectly launch an associated application if <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is set to `true`.</span></span> <span data-ttu-id="dfce1-107">.NET Framework, <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> için varsayılan değer `true`, yani *. txt* dosyalarını bu düzenleyici ile ilişkilendirdiyseniz, `Process.Start("mytextfile.txt")` gibi kodun Not defteri 'ni başlatacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="dfce1-107">On .NET Framework, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `true`, meaning that code such as `Process.Start("mytextfile.txt")` would launch Notepad, if you've associated *.txt* files with that editor.</span></span> <span data-ttu-id="dfce1-108">.NET Framework bir uygulamanın dolaylı olarak başlatılmasını engellemek için <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> açıkça `false`olarak ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="dfce1-108">To prevent indirectly launching an app on .NET Framework, you must explicitly set <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="dfce1-109">.NET Core 'da, <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> için varsayılan değer `false`.</span><span class="sxs-lookup"><span data-stu-id="dfce1-109">On .NET Core, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `false`.</span></span> <span data-ttu-id="dfce1-110">Bu, varsayılan olarak, `Process.Start`çağırdığınızda ilişkili uygulamaların başlatılmayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="dfce1-110">This means that, by default, associated applications are not launched when you call `Process.Start`.</span></span>

<span data-ttu-id="dfce1-111">Bu değişiklik, performans nedenleriyle .NET Core 'da sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="dfce1-111">This change was introduced in .NET Core for performance reasons.</span></span> <span data-ttu-id="dfce1-112">Genellikle, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> doğrudan bir uygulamayı başlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dfce1-112">Typically, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> is used to launch an application directly.</span></span> <span data-ttu-id="dfce1-113">Bir uygulamayı doğrudan başlatmak, Windows kabuğunu dahil etmek ve ilişkili performans maliyetine tabi olmak zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="dfce1-113">Launching an app directly does not need to involve the Windows shell and incur the associated performance cost.</span></span> <span data-ttu-id="dfce1-114">Bu varsayılan örneği daha hızlı hale getirmek için, .NET Core <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> varsayılan değerini `false`olarak değiştirir.</span><span class="sxs-lookup"><span data-stu-id="dfce1-114">To make this default case faster, .NET Core changes the default value of <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="dfce1-115">Gerekirse, daha yavaş yolu kabul edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dfce1-115">You can opt in to the slower path if you need it.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="dfce1-116">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="dfce1-116">Version introduced</span></span>

<span data-ttu-id="dfce1-117">2.1</span><span class="sxs-lookup"><span data-stu-id="dfce1-117">2.1</span></span>

> [!NOTE]
> <span data-ttu-id="dfce1-118">.NET Core 'un önceki sürümlerinde `UseShellExecute` Windows için uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="dfce1-118">In earlier versions of .NET Core, `UseShellExecute` was not implemented for Windows.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="dfce1-119">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="dfce1-119">Recommended action</span></span>

<span data-ttu-id="dfce1-120">Uygulamanız eski davranışı kullanıyorsa, <xref:System.Diagnostics.ProcessStartInfo> nesnesi üzerinde `true` olarak ayarlanan <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> çağırın.</span><span class="sxs-lookup"><span data-stu-id="dfce1-120">If your app relies on the old behavior, call <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> with <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> set to `true` on the <xref:System.Diagnostics.ProcessStartInfo> object.</span></span>

#### <a name="category"></a><span data-ttu-id="dfce1-121">Kategori</span><span class="sxs-lookup"><span data-stu-id="dfce1-121">Category</span></span>

<span data-ttu-id="dfce1-122">CoreFx</span><span class="sxs-lookup"><span data-stu-id="dfce1-122">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="dfce1-123">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="dfce1-123">Affected APIs</span></span>

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
