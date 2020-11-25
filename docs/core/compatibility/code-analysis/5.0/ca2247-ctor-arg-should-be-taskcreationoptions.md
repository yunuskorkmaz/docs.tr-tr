---
title: 'Son değişiklik: CA2247: TaskCompletionSource oluşturucusuna bağımsız değişken TaskCreationOptions değeri olmalıdır'
description: Kod Analizi kuralı CA2247 'nin etkinleştirilmesi nedeniyle .NET 5,0 'deki Son değişiklik hakkında bilgi edinin.
ms.date: 09/03/2020
ms.openlocfilehash: 323fd5a05da4dfeb68ef75d88d5d293ba01c8ade
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761534"
---
# <a name="warning-ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value"></a><span data-ttu-id="32725-103">Uyarı CA2247: TaskCompletionSource oluşturucusunun bağımsız değişkeni TaskCreationOptions değeri olmalıdır</span><span class="sxs-lookup"><span data-stu-id="32725-103">Warning CA2247: Argument to TaskCompletionSource constructor should be TaskCreationOptions value</span></span>

<span data-ttu-id="32725-104">.Net Code Analyzer Rule [CA2247](/visualstudio/code-quality/ca2247) , varsayılan olarak .NET 5,0 ' den başlayarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="32725-104">.NET code analyzer rule [CA2247](/visualstudio/code-quality/ca2247) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="32725-105"><xref:System.Threading.Tasks.TaskCompletionSource%601>Türünde bir bağımsız değişken geçiren oluşturucuya yapılan çağrılar için bir derleme uyarısı oluşturur <xref:System.Threading.Tasks.TaskContinuationOptions> .</span><span class="sxs-lookup"><span data-stu-id="32725-105">It produces a build warning for calls to the <xref:System.Threading.Tasks.TaskCompletionSource%601> constructor that pass an argument of type <xref:System.Threading.Tasks.TaskContinuationOptions>.</span></span>

## <a name="change-description"></a><span data-ttu-id="32725-106">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="32725-106">Change description</span></span>

<span data-ttu-id="32725-107">.NET SDK, .NET 5,0 'den başlayarak [.net kaynak kodu Çözümleyicileri](../../../../fundamentals/code-analysis/overview.md)içerir.</span><span class="sxs-lookup"><span data-stu-id="32725-107">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="32725-108">Bu kuralların bazıları varsayılan olarak [CA2247](/visualstudio/code-quality/ca2247)dahil olmak üzere etkindir.</span><span class="sxs-lookup"><span data-stu-id="32725-108">Several of these rules are enabled, by default, including [CA2247](/visualstudio/code-quality/ca2247).</span></span> <span data-ttu-id="32725-109">Projeniz bu kuralı ihlal eden ve uyarıları hata olarak işleyecek şekilde yapılandırılan kodu içeriyorsa, bu değişiklik yapınızı bozabilir.</span><span class="sxs-lookup"><span data-stu-id="32725-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="32725-110">Rule CA2247, <xref:System.Threading.Tasks.TaskCompletionSource%601> türünde bir bağımsız değişken geçiren oluşturucuya yapılan çağrıları bulur <xref:System.Threading.Tasks.TaskContinuationOptions> .</span><span class="sxs-lookup"><span data-stu-id="32725-110">Rule CA2247 finds calls to the <xref:System.Threading.Tasks.TaskCompletionSource%601> constructor that pass an argument of type <xref:System.Threading.Tasks.TaskContinuationOptions>.</span></span> <span data-ttu-id="32725-111"><xref:System.Threading.Tasks.TaskCompletionSource%601>Türün bir değeri kabul eden bir oluşturucusu <xref:System.Threading.Tasks.TaskCreationOptions> ve öğesini kabul eden başka bir Oluşturucu vardır <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="32725-111">The <xref:System.Threading.Tasks.TaskCompletionSource%601> type has a constructor that accepts a <xref:System.Threading.Tasks.TaskCreationOptions> value, and another constructor that accepts an <xref:System.Object>.</span></span> <span data-ttu-id="32725-112">Yanlışlıkla bir değer yerine bir <xref:System.Threading.Tasks.TaskContinuationOptions> değer geçirirseniz <xref:System.Threading.Tasks.TaskCreationOptions> , parametresine sahip Oluşturucu <xref:System.Object> çalışma zamanında çağırılır.</span><span class="sxs-lookup"><span data-stu-id="32725-112">If you accidentally pass a <xref:System.Threading.Tasks.TaskContinuationOptions> value instead of a <xref:System.Threading.Tasks.TaskCreationOptions> value, the constructor with the <xref:System.Object> parameter is called at run time.</span></span> <span data-ttu-id="32725-113">Kodunuz derleyip çalıştırılır, ancak amaçlanan davranışa sahip olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="32725-113">Your code will compile and run but won't have the intended behavior.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="32725-114">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="32725-114">Version introduced</span></span>

<span data-ttu-id="32725-115">5.0</span><span class="sxs-lookup"><span data-stu-id="32725-115">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="32725-116">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="32725-116">Recommended action</span></span>

- <span data-ttu-id="32725-117"><xref:System.Threading.Tasks.TaskContinuationOptions>Bağımsız değişkenini karşılık gelen değerle değiştirin <xref:System.Threading.Tasks.TaskCreationOptions> .</span><span class="sxs-lookup"><span data-stu-id="32725-117">Replace the <xref:System.Threading.Tasks.TaskContinuationOptions> argument with the corresponding <xref:System.Threading.Tasks.TaskCreationOptions> value.</span></span> <span data-ttu-id="32725-118">Kodunuzda bir hatayı neredeyse her zaman vurgudığından, bu uyarıyı göstermez.</span><span class="sxs-lookup"><span data-stu-id="32725-118">Do not suppress this warning, since it almost always highlights a bug in your code.</span></span> <span data-ttu-id="32725-119">Daha fazla bilgi için bkz. [CA2247](/visualstudio/code-quality/ca2247).</span><span class="sxs-lookup"><span data-stu-id="32725-119">For more information, see [CA2247](/visualstudio/code-quality/ca2247).</span></span>

- <span data-ttu-id="32725-120">Kod analizini tamamen devre dışı bırakmak için `EnableNETAnalyzers` , `false` proje dosyanızda olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="32725-120">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="32725-121">Daha fazla bilgi için bkz. [Enablenetçözümleyiciler](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="32725-121">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="32725-122">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="32725-122">Affected APIs</span></span>

- <xref:System.Threading.Tasks.TaskCompletionSource%601.%23ctor(System.Object)>

<!--

### Affected APIs

- ``M:System.Threading.Tasks.TaskCompletionSource`1.#ctor(System.Object)``

### Category

Code analysis

-->
