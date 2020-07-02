---
ms.openlocfilehash: 5f1a8af37a305ab0904801002dd99e17e8eca62e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616128"
---
### <a name="two-way-data-binding-to-a-property-with-a-non-public-setter-is-not-supported"></a><span data-ttu-id="e382b-101">Ortak olmayan bir ayarlayıcıya sahip bir özelliğe iki yönlü veri bağlama desteklenmez</span><span class="sxs-lookup"><span data-stu-id="e382b-101">Two-way data-binding to a property with a non-public setter is not supported</span></span>

#### <a name="details"></a><span data-ttu-id="e382b-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e382b-102">Details</span></span>

<span data-ttu-id="e382b-103">Ortak bir ayarlayıcı olmadan bir özelliğe veri bağlama girişimi hiçbir şekilde desteklenmeyen bir senaryoya sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="e382b-103">Attempting to data bind to a property without a public setter has never been a supported scenario.</span></span> <span data-ttu-id="e382b-104">.NET Framework 4.5.1 başlayarak, bu senaryo bir oluşturur <xref:System.InvalidOperationException?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="e382b-104">Beginning in the .NET Framework 4.5.1, this scenario will throw an <xref:System.InvalidOperationException?displayProperty=fullName>.</span></span> <span data-ttu-id="e382b-105">Bu yeni özel durumun yalnızca, özellikle .NET Framework 4.5.1 hedefleyen uygulamalar için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e382b-105">Note that this new exception will only be thrown for apps that specifically target the .NET Framework 4.5.1.</span></span> <span data-ttu-id="e382b-106">Bir uygulama .NET Framework 4,5 ' i hedefliyorsa, çağrıya izin verilir.</span><span class="sxs-lookup"><span data-stu-id="e382b-106">If an app targets the .NET Framework 4.5, the call will be allowed.</span></span> <span data-ttu-id="e382b-107">Uygulama belirli bir .NET Framework sürümünü hedeflemez, bağlama tek yönlü olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="e382b-107">If the app does not target a particular .NET Framework version, the binding will be treated as one-way.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e382b-108">Öneri</span><span class="sxs-lookup"><span data-stu-id="e382b-108">Suggestion</span></span>

<span data-ttu-id="e382b-109">Uygulama tek yönlü bağlama kullanacak şekilde veya özelliğin ayarlayıcısı genel olarak kullanıma sunulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e382b-109">The app should be updated to either use one-way binding, or expose the property's setter publicly.</span></span> <span data-ttu-id="e382b-110">Alternatif olarak, 4,5 .NET Framework hedeflemek uygulamanın eski davranışı sergilemesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="e382b-110">Alternatively, targeting the .NET Framework 4.5 will cause the app to exhibit the old behavior.</span></span>

| <span data-ttu-id="e382b-111">Name</span><span class="sxs-lookup"><span data-stu-id="e382b-111">Name</span></span>    | <span data-ttu-id="e382b-112">Değer</span><span class="sxs-lookup"><span data-stu-id="e382b-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e382b-113">Kapsam</span><span class="sxs-lookup"><span data-stu-id="e382b-113">Scope</span></span>   | <span data-ttu-id="e382b-114">İkincil</span><span class="sxs-lookup"><span data-stu-id="e382b-114">Minor</span></span>       |
| <span data-ttu-id="e382b-115">Sürüm</span><span class="sxs-lookup"><span data-stu-id="e382b-115">Version</span></span> | <span data-ttu-id="e382b-116">4.5.1</span><span class="sxs-lookup"><span data-stu-id="e382b-116">4.5.1</span></span>       |
| <span data-ttu-id="e382b-117">Tür</span><span class="sxs-lookup"><span data-stu-id="e382b-117">Type</span></span>    | <span data-ttu-id="e382b-118">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="e382b-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="e382b-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e382b-119">Affected APIs</span></span>

- <xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType>
