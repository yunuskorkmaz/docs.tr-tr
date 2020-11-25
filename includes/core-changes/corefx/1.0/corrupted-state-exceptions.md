---
ms.openlocfilehash: 394f2daebad7b6af94bee4d7876796e87fe8ab19
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032064"
---
### <a name="handling-corrupted-state-exceptions-is-not-supported"></a><span data-ttu-id="76ff1-101">Bozuk durum özel durumlarını işleme desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="76ff1-101">Handling corrupted state exceptions is not supported</span></span>

<span data-ttu-id="76ff1-102">.NET Core 'da bozuk işlem durumu özel durumlarını işleme desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="76ff1-102">Handling corrupted-process-state exceptions in .NET Core is not supported.</span></span>

#### <a name="change-description"></a><span data-ttu-id="76ff1-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="76ff1-103">Change description</span></span>

<span data-ttu-id="76ff1-104">Daha önce, bozuk işlem durumu özel durumları, örneğin, C# ' de bir [try-catch](../../../../docs/csharp/language-reference/keywords/try-catch.md) ifadesiyle kullanılarak, yönetilen kod özel durum işleyicileri tarafından yakalanıp Işlenebiliyor.</span><span class="sxs-lookup"><span data-stu-id="76ff1-104">Previously, corrupted-process-state exceptions could be caught and handled by managed code exception handlers, for example, by using a [try-catch](../../../../docs/csharp/language-reference/keywords/try-catch.md) statement in C#.</span></span>

<span data-ttu-id="76ff1-105">.NET Core 1,0 ' den başlayarak, bozuk işlem durumu özel durumları yönetilen kod tarafından işlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="76ff1-105">Starting in .NET Core 1.0, corrupted-process-state exceptions cannot be handled by managed code.</span></span> <span data-ttu-id="76ff1-106">Ortak dil çalışma zamanı, yönetilen koda bozuk işlem durumu özel durumları teslim etmez.</span><span class="sxs-lookup"><span data-stu-id="76ff1-106">The common language runtime doesn't deliver corrupted-process-state exceptions to managed code.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="76ff1-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="76ff1-107">Version introduced</span></span>

<span data-ttu-id="76ff1-108">1,0</span><span class="sxs-lookup"><span data-stu-id="76ff1-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="76ff1-109">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="76ff1-109">Recommended action</span></span>

<span data-ttu-id="76ff1-110">Bunun yerine, bunlara neden olan durumları ele alarak bozuk işlem durumu özel durumlarını işleme gereksinimini önleyin.</span><span class="sxs-lookup"><span data-stu-id="76ff1-110">Avoid the need to handle corrupted-process-state exceptions by addressing the situations that lead to them instead.</span></span> <span data-ttu-id="76ff1-111">Bozuk işlem durumu özel durumlarını işlemek kesinlikle gerekliyse, özel durum işleyicisini C veya C++ koduna yazın.</span><span class="sxs-lookup"><span data-stu-id="76ff1-111">If it's absolutely necessary to handle corrupted-process-state exceptions, write the exception handler in C or C++ code.</span></span>

#### <a name="category"></a><span data-ttu-id="76ff1-112">Kategori</span><span class="sxs-lookup"><span data-stu-id="76ff1-112">Category</span></span>

<span data-ttu-id="76ff1-113">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="76ff1-113">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="76ff1-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="76ff1-114">Affected APIs</span></span>

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=fullName>
- [<span data-ttu-id="76ff1-115">Legacyboztedstateexceptionspolicy öğesi</span><span class="sxs-lookup"><span data-stu-id="76ff1-115">legacyCorruptedStateExceptionsPolicy element</span></span>](~/docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)

<!--

#### Affected APIs

- `T:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute`

-->
