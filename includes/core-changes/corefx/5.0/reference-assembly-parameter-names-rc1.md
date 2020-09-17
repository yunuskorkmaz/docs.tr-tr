---
ms.openlocfilehash: 760c9ce2427bc1f5e9276e66ecb6d2cf2ed83c16
ms.sourcegitcommit: a8730298170b8d96b4272e0c3dfc9819c606947b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90738832"
---
### <a name="parameter-names-changed-in-rc1"></a><span data-ttu-id="a8c69-101">RC1 'de parametre adları değişti</span><span class="sxs-lookup"><span data-stu-id="a8c69-101">Parameter names changed in RC1</span></span>

<span data-ttu-id="a8c69-102">Bazı başvuru derleme parametresi adları, uygulama derlemelerindeki parametre adlarıyla eşleşecek şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a8c69-102">Some reference assembly parameter names have changed to match parameter names in the implementation assemblies.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a8c69-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="a8c69-103">Change description</span></span>

<span data-ttu-id="a8c69-104">Önceki .NET 5,0 Önizleme ve RC sürümlerinde, bazı [Başvuru derleme](../../../../docs/standard/assembly/reference-assemblies.md) parametresi adları, uygulama derlemesinde karşılık gelen parametrelere farklıdır.</span><span class="sxs-lookup"><span data-stu-id="a8c69-104">In previous .NET 5.0 preview and RC versions, some [reference assembly](../../../../docs/standard/assembly/reference-assemblies.md) parameter names are different to their corresponding parameters in the implementation assembly.</span></span> <span data-ttu-id="a8c69-105">Bu, adlandırılmış bağımsız değişkenler ve yansıma kullanılırken soruna neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="a8c69-105">This can cause problems while using named arguments and reflection.</span></span>

<span data-ttu-id="a8c69-106">.NET 5,0 RC2 'de, bu eşleşmeyen parametre adları, başvuru derlemelerinde, uygulama derlemelerindeki karşılık gelen parametre adlarıyla tam olarak eşleşecek şekilde güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="a8c69-106">In .NET 5.0 RC2, these mismatched parameter names were updated in the reference assemblies to exactly match the corresponding parameter names in the implementation assemblies.</span></span>

<span data-ttu-id="a8c69-107">Aşağıdaki tabloda, değiştirilen API 'Ler ve parametre adları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a8c69-107">The following table shows the APIs and parameter names that changed.</span></span>

| <span data-ttu-id="a8c69-108">API</span><span class="sxs-lookup"><span data-stu-id="a8c69-108">API</span></span> | <span data-ttu-id="a8c69-109">Eski parametre adı</span><span class="sxs-lookup"><span data-stu-id="a8c69-109">Old parameter name</span></span> | <span data-ttu-id="a8c69-110">Yeni parametre adı</span><span class="sxs-lookup"><span data-stu-id="a8c69-110">New parameter name</span></span> |
| - | - | - |
| <xref:System.Diagnostics.ActivityContext.%23ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)> | `traceOptions` | `traceFlags` |
| <xref:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)?displayProperty=nameWithType> | `suffix` | `prefix` |

#### <a name="reason-for-change"></a><span data-ttu-id="a8c69-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="a8c69-111">Reason for change</span></span>

<span data-ttu-id="a8c69-112">Parametre adları tutarlılık için değiştirilmiştir ve adlandırılmış bağımsız değişkenler ve yansıma kullanılırken hatalardan kaçınmak için.</span><span class="sxs-lookup"><span data-stu-id="a8c69-112">The parameter names were changed for consistency and to avoid failures when using named arguments and reflection.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a8c69-113">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="a8c69-113">Version introduced</span></span>

<span data-ttu-id="a8c69-114">5,0 RC2</span><span class="sxs-lookup"><span data-stu-id="a8c69-114">5.0 RC2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a8c69-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="a8c69-115">Recommended action</span></span>

<span data-ttu-id="a8c69-116">Bir parametre adı değişikliği nedeniyle bir derleyici hatasıyla karşılaşırsanız parametre adını uygun şekilde güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="a8c69-116">If you encounter a compiler error due to a parameter name change, update the parameter name accordingly.</span></span>

#### <a name="category"></a><span data-ttu-id="a8c69-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="a8c69-117">Category</span></span>

<span data-ttu-id="a8c69-118">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="a8c69-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a8c69-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a8c69-119">Affected APIs</span></span>

- <xref:System.Diagnostics.ActivityContext.%23ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)>
- <xref:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Diagnostics.ActivityContext.#ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)`
- `M:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)`

-->
