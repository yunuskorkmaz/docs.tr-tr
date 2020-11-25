---
title: "Son değişiklik: RC2 'de parametre adları değişti"
description: Bazı başvuru derleme parametresi adlarının, .NET 5,0 ' nin önizleme ve sürüm adayı sürümlerinden değiştiği çekirdek .NET kitaplıklarında .NET 5,0 son değişikliği hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: 554a4fa9e08fdb504f380465496d7e7e9df85814
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761502"
---
# <a name="parameter-names-changed-in-rc2"></a><span data-ttu-id="abfd6-103">RC2 'de parametre adları değiştirildi</span><span class="sxs-lookup"><span data-stu-id="abfd6-103">Parameter names changed in RC2</span></span>

<span data-ttu-id="abfd6-104">Bazı başvuru derleme parametresi adları, uygulama derlemelerindeki parametre adlarıyla eşleşecek şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="abfd6-104">Some reference assembly parameter names have changed to match parameter names in the implementation assemblies.</span></span>

## <a name="change-description"></a><span data-ttu-id="abfd6-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="abfd6-105">Change description</span></span>

<span data-ttu-id="abfd6-106">Önceki .NET 5,0 Önizleme ve RC sürümlerinde, bazı [Başvuru derleme](../../../../standard/assembly/reference-assemblies.md) parametresi adları, uygulama derlemesinde karşılık gelen parametrelere farklıdır.</span><span class="sxs-lookup"><span data-stu-id="abfd6-106">In previous .NET 5.0 preview and RC versions, some [reference assembly](../../../../standard/assembly/reference-assemblies.md) parameter names are different to their corresponding parameters in the implementation assembly.</span></span> <span data-ttu-id="abfd6-107">Bu, adlandırılmış bağımsız değişkenler ve yansıma kullanılırken soruna neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="abfd6-107">This can cause problems while using named arguments and reflection.</span></span>

<span data-ttu-id="abfd6-108">.NET 5,0 RC2 'de, bu eşleşmeyen parametre adları, başvuru derlemelerinde, uygulama derlemelerindeki karşılık gelen parametre adlarıyla tam olarak eşleşecek şekilde güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="abfd6-108">In .NET 5.0 RC2, these mismatched parameter names were updated in the reference assemblies to exactly match the corresponding parameter names in the implementation assemblies.</span></span>

<span data-ttu-id="abfd6-109">Aşağıdaki tabloda, değiştirilen API 'Ler ve parametre adları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="abfd6-109">The following table shows the APIs and parameter names that changed.</span></span>

| <span data-ttu-id="abfd6-110">API</span><span class="sxs-lookup"><span data-stu-id="abfd6-110">API</span></span> | <span data-ttu-id="abfd6-111">Eski parametre adı</span><span class="sxs-lookup"><span data-stu-id="abfd6-111">Old parameter name</span></span> | <span data-ttu-id="abfd6-112">Yeni parametre adı</span><span class="sxs-lookup"><span data-stu-id="abfd6-112">New parameter name</span></span> |
| - | - | - |
| <xref:System.Diagnostics.ActivityContext.%23ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)> | `traceOptions` | `traceFlags` |
| <xref:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)?displayProperty=nameWithType> | `suffix` | `prefix` |

## <a name="reason-for-change"></a><span data-ttu-id="abfd6-113">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="abfd6-113">Reason for change</span></span>

<span data-ttu-id="abfd6-114">Parametre adları tutarlılık için değiştirilmiştir ve adlandırılmış bağımsız değişkenler ve yansıma kullanılırken hatalardan kaçınmak için.</span><span class="sxs-lookup"><span data-stu-id="abfd6-114">The parameter names were changed for consistency and to avoid failures when using named arguments and reflection.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="abfd6-115">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="abfd6-115">Version introduced</span></span>

<span data-ttu-id="abfd6-116">5,0 RC2</span><span class="sxs-lookup"><span data-stu-id="abfd6-116">5.0 RC2</span></span>

## <a name="recommended-action"></a><span data-ttu-id="abfd6-117">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="abfd6-117">Recommended action</span></span>

<span data-ttu-id="abfd6-118">Bir parametre adı değişikliği nedeniyle bir derleyici hatasıyla karşılaşırsanız parametre adını uygun şekilde güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="abfd6-118">If you encounter a compiler error due to a parameter name change, update the parameter name accordingly.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="abfd6-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="abfd6-119">Affected APIs</span></span>

- <xref:System.Diagnostics.ActivityContext.%23ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)>
- <xref:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `M:System.Diagnostics.ActivityContext.#ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)`
- `M:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)`

-->
