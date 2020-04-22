---
ms.openlocfilehash: 9544b65f31772d0f4cee918528a73171fec4de99
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021815"
---
### <a name="change-in-default-value-of-useshellexecute"></a><span data-ttu-id="98c75-101">UseShellExecute'ın varsayılan değerindeki değişiklik</span><span class="sxs-lookup"><span data-stu-id="98c75-101">Change in default value of UseShellExecute</span></span>

<span data-ttu-id="98c75-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType>.NET Core `false` üzerinde varsayılan değeri vardır.</span><span class="sxs-lookup"><span data-stu-id="98c75-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> has a default value of `false` on .NET Core.</span></span> <span data-ttu-id="98c75-103">.NET Framework'de varsayılan `true`değeri .</span><span class="sxs-lookup"><span data-stu-id="98c75-103">On .NET Framework, its default value is `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="98c75-104">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="98c75-104">Change description</span></span>

<span data-ttu-id="98c75-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>örneğin Paint'i başlatan gibi `Process.Start("mspaint.exe")` kodlarla doğrudan bir uygulama başlatmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="98c75-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> lets you launch an application directly, for example, with code such as `Process.Start("mspaint.exe")` that launches Paint.</span></span> <span data-ttu-id="98c75-106">Ayrıca, '' olarak ayarlanmışsa, <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> dolaylı `true`olarak ilişkili bir uygulamayı başlatmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="98c75-106">It also lets you indirectly launch an associated application if <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is set to `true`.</span></span> <span data-ttu-id="98c75-107">.NET Framework'de, *.txt* dosyalarını `Process.Start("mytextfile.txt")` bu düzenleyiciyle ilişkilendirdiyseniz, not defteri gibi kodun başlatılması anlamına gelen varsayılan <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> değerdir. `true`</span><span class="sxs-lookup"><span data-stu-id="98c75-107">On .NET Framework, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `true`, meaning that code such as `Process.Start("mytextfile.txt")` would launch Notepad, if you've associated *.txt* files with that editor.</span></span> <span data-ttu-id="98c75-108">.NET Framework'de dolaylı olarak bir uygulama başlatılmasını <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `false`önlemek için, açıkça .</span><span class="sxs-lookup"><span data-stu-id="98c75-108">To prevent indirectly launching an app on .NET Framework, you must explicitly set <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="98c75-109">.NET Core'da varsayılan <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `false`değer.</span><span class="sxs-lookup"><span data-stu-id="98c75-109">On .NET Core, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `false`.</span></span> <span data-ttu-id="98c75-110">Bu, varsayılan olarak, ilişkili uygulamaların . `Process.Start`</span><span class="sxs-lookup"><span data-stu-id="98c75-110">This means that, by default, associated applications are not launched when you call `Process.Start`.</span></span>

<span data-ttu-id="98c75-111">Bu değişiklik performans nedenleriyle .NET Core'da kullanılmaya başlandı.</span><span class="sxs-lookup"><span data-stu-id="98c75-111">This change was introduced in .NET Core for performance reasons.</span></span> <span data-ttu-id="98c75-112">Genellikle, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> doğrudan bir uygulama başlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="98c75-112">Typically, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> is used to launch an application directly.</span></span> <span data-ttu-id="98c75-113">Doğrudan bir uygulama başlatmanın Windows kabuğunu içermesi ve ilişkili performans maliyetine tabi olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="98c75-113">Launching an app directly does not need to involve the Windows shell and incur the associated performance cost.</span></span> <span data-ttu-id="98c75-114">Bu varsayılan durumu daha hızlı yapmak için ,NET Core varsayılan değerini <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `false`.</span><span class="sxs-lookup"><span data-stu-id="98c75-114">To make this default case faster, .NET Core changes the default value of <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="98c75-115">İhtiyacınız olduğunda daha yavaş yolu tercih edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98c75-115">You can opt in to the slower path if you need it.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="98c75-116">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="98c75-116">Version introduced</span></span>

<span data-ttu-id="98c75-117">2.1</span><span class="sxs-lookup"><span data-stu-id="98c75-117">2.1</span></span>

> [!NOTE]
> <span data-ttu-id="98c75-118">.NET Core'un önceki `UseShellExecute` sürümlerinde, Windows için uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="98c75-118">In earlier versions of .NET Core, `UseShellExecute` was not implemented for Windows.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="98c75-119">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="98c75-119">Recommended action</span></span>

<span data-ttu-id="98c75-120">Uygulamanız eski davranışa <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> dayanıyorsa, <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> `true` <xref:System.Diagnostics.ProcessStartInfo> nesneüzerinde ayarla'yı arayın.</span><span class="sxs-lookup"><span data-stu-id="98c75-120">If your app relies on the old behavior, call <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> with <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> set to `true` on the <xref:System.Diagnostics.ProcessStartInfo> object.</span></span>

#### <a name="category"></a><span data-ttu-id="98c75-121">Kategori</span><span class="sxs-lookup"><span data-stu-id="98c75-121">Category</span></span>

<span data-ttu-id="98c75-122">Çekirdek .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="98c75-122">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="98c75-123">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="98c75-123">Affected APIs</span></span>

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
