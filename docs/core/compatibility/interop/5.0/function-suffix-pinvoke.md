---
title: 'Son değişiklik: Windows dışı platformlarda bir/W soneki yoklama yok'
description: Windows dışı platformlarda P/Invoke için yoklama sırasında son eklerin artık işlev dışa aktarma adlarına eklenmemiş olduğunu .NET 5 ' teki birlikte çalışma son değişikliği hakkında bilgi edinin.
ms.date: 08/13/2020
ms.openlocfilehash: 924cbcb6c432e2f7c52c7218d48a938b61306c9c
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256627"
---
# <a name="no-aw-suffix-probing-on-non-windows-platforms"></a><span data-ttu-id="6462f-103">Windows olmayan platformlarda A/W sonek yoklaması yok</span><span class="sxs-lookup"><span data-stu-id="6462f-103">No A/W suffix probing on non-Windows platforms</span></span>

<span data-ttu-id="6462f-104">.NET çalışma zamanları artık `A` `W` Windows dışı platformlarda P/Invoke için yoklama sırasında dışarı aktarma adlarını işlevine bir veya sonek eklemez.</span><span class="sxs-lookup"><span data-stu-id="6462f-104">The .NET runtimes no longer add an `A` or `W` suffix to function export names during probing for P/Invokes on non-Windows platforms.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="6462f-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="6462f-105">Version introduced</span></span>

<span data-ttu-id="6462f-106">5.0</span><span class="sxs-lookup"><span data-stu-id="6462f-106">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="6462f-107">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="6462f-107">Change description</span></span>

<span data-ttu-id="6462f-108">[Windows](/windows/win32/intl/conventions-for-function-prototypes) , `A` `W` sırasıyla Windows kod sayfasına ve Unicode sürümlerine karşılık gelen Windows SDK işlev adlarına bir veya son ek ekleme kuralına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6462f-108">[Windows has a convention](/windows/win32/intl/conventions-for-function-prototypes) of adding an `A` or `W` suffix to Windows SDK function names, which correspond to the Windows code page and Unicode versions, respectively.</span></span>

<span data-ttu-id="6462f-109">Önceki .NET sürümlerinde CoreCLR ve mono çalışma zamanları, `A` `W` *tüm platformlarda* P/Invoke için dışarı aktarma keşfi sırasında dışarı aktarma adına bir veya son ek ekler.</span><span class="sxs-lookup"><span data-stu-id="6462f-109">In previous versions of .NET, both the CoreCLR and Mono runtimes add an `A` or `W` suffix to the export name during export discovery for P/Invokes *on all platforms*.</span></span>

<span data-ttu-id="6462f-110">.NET 5 ve sonraki sürümlerinde, `A` `W` *yalnızca Windows üzerinde* dışarı aktarma sırasında dışarı aktarma adına bir veya soneki eklenir.</span><span class="sxs-lookup"><span data-stu-id="6462f-110">In .NET 5 and later versions, an `A` or `W` suffix is added to the export name during export discovery *on Windows only*.</span></span> <span data-ttu-id="6462f-111">UNIX platformlarında, sonek eklenmez.</span><span class="sxs-lookup"><span data-stu-id="6462f-111">On Unix platforms, the suffix is not added.</span></span> <span data-ttu-id="6462f-112">Windows platformunda her iki çalışma alanının semantiği değişmeden kalır.</span><span class="sxs-lookup"><span data-stu-id="6462f-112">The semantics of both runtimes on the Windows platform remain unchanged.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="6462f-113">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="6462f-113">Reason for change</span></span>

<span data-ttu-id="6462f-114">Platformlar arası yoklama basitleştirecek bu değişiklik yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="6462f-114">This change was made to simplify cross-platform probing.</span></span> <span data-ttu-id="6462f-115">Windows dışı platformların Bu anlam içermediğini göz önüne alındığında, bu, tahakkuk etmemelidir.</span><span class="sxs-lookup"><span data-stu-id="6462f-115">It's overhead that shouldn't be incurred, given that non-Windows platforms don't contain this semantic.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="6462f-116">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="6462f-116">Recommended action</span></span>

<span data-ttu-id="6462f-117">Değişikliği azaltmak için, istenen soneki Windows olmayan platformlarda el ile ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6462f-117">To mitigate the change, you can manually add the desired suffix on non-Windows platforms.</span></span> <span data-ttu-id="6462f-118">Örnek:</span><span class="sxs-lookup"><span data-stu-id="6462f-118">For example:</span></span>

```csharp
[DllImport(...)]
extern static void SetWindowTextW();
```

## <a name="affected-apis"></a><span data-ttu-id="6462f-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="6462f-119">Affected APIs</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Runtime.InteropServices.DllImportAttribute`

### Category

Interop

-->
