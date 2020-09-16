---
ms.openlocfilehash: e128bdb5735b3e4844356ad4807cc092f6f2b105
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062437"
---
### <a name="no-aw-suffix-probing-on-non-windows-platforms"></a><span data-ttu-id="7e41d-101">Windows dışı platformlarda bir/W soneki yoklama yok</span><span class="sxs-lookup"><span data-stu-id="7e41d-101">No A/W suffix probing on non-Windows platforms</span></span>

<span data-ttu-id="7e41d-102">.NET çalışma zamanları artık `A` `W` Windows dışı platformlarda P/Invoke için yoklama sırasında dışarı aktarma adlarını işlevine bir veya sonek eklemez.</span><span class="sxs-lookup"><span data-stu-id="7e41d-102">The .NET runtimes no longer add an `A` or `W` suffix to function export names during probing for P/Invokes on non-Windows platforms.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7e41d-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="7e41d-103">Version introduced</span></span>

<span data-ttu-id="7e41d-104">5,0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="7e41d-104">5.0 Preview 4</span></span>

#### <a name="change-description"></a><span data-ttu-id="7e41d-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="7e41d-105">Change description</span></span>

<span data-ttu-id="7e41d-106">[Windows](/windows/win32/intl/conventions-for-function-prototypes) , `A` `W` sırasıyla Windows kod sayfasına ve Unicode sürümlerine karşılık gelen Windows SDK işlev adlarına bir veya son ek ekleme kuralına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="7e41d-106">[Windows has a convention](/windows/win32/intl/conventions-for-function-prototypes) of adding an `A` or `W` suffix to Windows SDK function names, which correspond to the Windows code page and Unicode versions, respectively.</span></span>

<span data-ttu-id="7e41d-107">Önceki .NET sürümlerinde CoreCLR ve mono çalışma zamanları, `A` `W` *tüm platformlarda*P/Invoke için dışarı aktarma keşfi sırasında dışarı aktarma adına bir veya son ek ekler.</span><span class="sxs-lookup"><span data-stu-id="7e41d-107">In previous versions of .NET, both the CoreCLR and Mono runtimes add an `A` or `W` suffix to the export name during export discovery for P/Invokes *on all platforms*.</span></span>

<span data-ttu-id="7e41d-108">.NET 5,0 ve sonraki sürümlerinde, `A` `W` *yalnızca Windows üzerinde*dışarı aktarma sırasında dışarı aktarma adına bir veya soneki eklenir.</span><span class="sxs-lookup"><span data-stu-id="7e41d-108">In .NET 5.0 and later versions, an `A` or `W` suffix is added to the export name during export discovery *on Windows only*.</span></span> <span data-ttu-id="7e41d-109">UNIX platformlarında, sonek eklenmez.</span><span class="sxs-lookup"><span data-stu-id="7e41d-109">On Unix platforms, the suffix is not added.</span></span> <span data-ttu-id="7e41d-110">Windows platformunda her iki çalışma alanının semantiği değişmeden kalır.</span><span class="sxs-lookup"><span data-stu-id="7e41d-110">The semantics of both runtimes on the Windows platform remain unchanged.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="7e41d-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="7e41d-111">Reason for change</span></span>

<span data-ttu-id="7e41d-112">Platformlar arası yoklama basitleştirecek bu değişiklik yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="7e41d-112">This change was made to simplify cross-platform probing.</span></span> <span data-ttu-id="7e41d-113">Windows dışı platformların Bu anlam içermediğini göz önüne alındığında, bu, tahakkuk etmemelidir.</span><span class="sxs-lookup"><span data-stu-id="7e41d-113">It's overhead that shouldn't be incurred, given that non-Windows platforms don't contain this semantic.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7e41d-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="7e41d-114">Recommended action</span></span>

<span data-ttu-id="7e41d-115">Değişikliği azaltmak için, istenen soneki Windows olmayan platformlarda el ile ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e41d-115">To mitigate the change, you can manually add the desired suffix on non-Windows platforms.</span></span> <span data-ttu-id="7e41d-116">Örnek:</span><span class="sxs-lookup"><span data-stu-id="7e41d-116">For example:</span></span>

```csharp
[DllImport(...)]
extern static void SetWindowTextW();
```

#### <a name="category"></a><span data-ttu-id="7e41d-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="7e41d-117">Category</span></span>

<span data-ttu-id="7e41d-118">Interop</span><span class="sxs-lookup"><span data-stu-id="7e41d-118">Interop</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7e41d-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="7e41d-119">Affected APIs</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Runtime.InteropServices.DllImportAttribute`

-->
