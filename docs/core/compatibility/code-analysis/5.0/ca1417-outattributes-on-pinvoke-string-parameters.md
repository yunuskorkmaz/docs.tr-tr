---
title: 'Son değişiklik: P/Invoke için dize parametresinde CA1417: OutAttribute'
description: Kod Analizi kuralı CA1417 'nin etkinleştirilmesi nedeniyle .NET 5,0 'deki Son değişiklik hakkında bilgi edinin.
ms.date: 09/29/2020
ms.openlocfilehash: 3316d07108ec7f9da985494413336cba6d560dc9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761337"
---
# <a name="warning-ca1417-outattribute-on-string-parameter-for-pinvoke"></a><span data-ttu-id="1f2e1-103">Uyarı CA1417: P/Invoke için dize parametresindeki OutAttribute</span><span class="sxs-lookup"><span data-stu-id="1f2e1-103">Warning CA1417: OutAttribute on string parameter for P/Invoke</span></span>

<span data-ttu-id="1f2e1-104">.Net Code Analyzer Rule [CA1417](/visualstudio/code-quality/ca1417) , varsayılan olarak .NET 5,0 ' den başlayarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="1f2e1-104">.NET code analyzer rule [CA1417](/visualstudio/code-quality/ca1417) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="1f2e1-105">Bir parametrenin değere göre geçirildiği ve ile işaretlenen tüm [Platform çağırma (P/Invoke)](../../../../standard/native-interop/pinvoke.md) yöntemi tanımları için bir derleme uyarısı oluşturur <xref:System.String> <xref:System.Runtime.InteropServices.OutAttribute> .</span><span class="sxs-lookup"><span data-stu-id="1f2e1-105">It produces a build warning for any [Platform Invoke (P/Invoke)](../../../../standard/native-interop/pinvoke.md) method definitions where a <xref:System.String> parameter is passed by value and marked with <xref:System.Runtime.InteropServices.OutAttribute>.</span></span>

## <a name="change-description"></a><span data-ttu-id="1f2e1-106">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="1f2e1-106">Change description</span></span>

<span data-ttu-id="1f2e1-107">.NET SDK, .NET 5,0 'den başlayarak [.net kaynak kodu Çözümleyicileri](../../../../fundamentals/code-analysis/overview.md)içerir.</span><span class="sxs-lookup"><span data-stu-id="1f2e1-107">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="1f2e1-108">Bu kuralların bazıları varsayılan olarak [CA1417](/visualstudio/code-quality/ca1417)dahil olmak üzere etkindir.</span><span class="sxs-lookup"><span data-stu-id="1f2e1-108">Several of these rules are enabled, by default, including [CA1417](/visualstudio/code-quality/ca1417).</span></span> <span data-ttu-id="1f2e1-109">Projeniz bu kuralı ihlal eden ve uyarıları hata olarak işleyecek şekilde yapılandırılan kodu içeriyorsa, bu değişiklik yapınızı bozabilir.</span><span class="sxs-lookup"><span data-stu-id="1f2e1-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="1f2e1-110">Rule CA1417 bayrakları [P/](../../../../standard/native-interop/pinvoke.md) bir <xref:System.String> parametrenin öznitelik ile işaretlendiği <xref:System.Runtime.InteropServices.OutAttribute> ve değer Ile geçirildiği yöntem tanımlarını çağırır.</span><span class="sxs-lookup"><span data-stu-id="1f2e1-110">Rule CA1417 flags [P/Invoke](../../../../standard/native-interop/pinvoke.md) method definitions where a <xref:System.String> parameter is marked with the <xref:System.Runtime.InteropServices.OutAttribute> attribute and is passed by value.</span></span> <span data-ttu-id="1f2e1-111">Örnek:</span><span class="sxs-lookup"><span data-stu-id="1f2e1-111">For example:</span></span>

```csharp
[DllImport("MyLibrary")]
private static extern void PIMethod([Out] string s);
```

<span data-ttu-id="1f2e1-112">.NET çalışma zamanı, bir programdaki her benzersiz sabit değer dizesine tek bir başvuru içeren Intern havuzu adlı bir tablo tutar.</span><span class="sxs-lookup"><span data-stu-id="1f2e1-112">The .NET runtime maintains a table, called the intern pool, that contains a single reference to each unique literal string in a program.</span></span> <span data-ttu-id="1f2e1-113">İle işaretlenmiş bir dize, <xref:System.Runtime.InteropServices.OutAttribute> bir P/Invoke yöntemine değer ile geçirildiyse, çalışma zamanı kararsız hale gelebilirler.</span><span class="sxs-lookup"><span data-stu-id="1f2e1-113">If an interned string marked with <xref:System.Runtime.InteropServices.OutAttribute> is passed by value to a P/Invoke method, the runtime can be destabilized.</span></span> <span data-ttu-id="1f2e1-114">Dize oluşturma hakkında daha fazla bilgi için, bkz <xref:System.String.Intern(System.String)?displayProperty=nameWithType> . açıklamalar.</span><span class="sxs-lookup"><span data-stu-id="1f2e1-114">For more information about string interning, see the remarks for <xref:System.String.Intern(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="1f2e1-115">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="1f2e1-115">Version introduced</span></span>

<span data-ttu-id="1f2e1-116">5.0</span><span class="sxs-lookup"><span data-stu-id="1f2e1-116">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="1f2e1-117">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="1f2e1-117">Recommended action</span></span>

- <span data-ttu-id="1f2e1-118">Değiştirilen dize verilerini çağırana geri almanız gerekiyorsa, dizeyi başvuruya göre geçirin.</span><span class="sxs-lookup"><span data-stu-id="1f2e1-118">If you need to marshal modified string data back to the caller, pass the string by reference instead.</span></span>

  ```csharp
  [DllImport("MyLibrary")]
  private static extern void PIMethod(out string s);
  ```

- <span data-ttu-id="1f2e1-119">Değiştirilen dize verilerini çağırana geri sıralayamaz, öğesini kaldırmanız yeterlidir <xref:System.Runtime.InteropServices.OutAttribute> .</span><span class="sxs-lookup"><span data-stu-id="1f2e1-119">If you don't need to marshal modified string data back to the caller, simply remove the <xref:System.Runtime.InteropServices.OutAttribute>.</span></span>

  ```csharp
  [DllImport("MyLibrary")]
  private static extern void PIMethod(string s);
  ```

  <span data-ttu-id="1f2e1-120">Daha fazla bilgi için bkz. [CA1417](/visualstudio/code-quality/ca1417).</span><span class="sxs-lookup"><span data-stu-id="1f2e1-120">For more information, see [CA1417](/visualstudio/code-quality/ca1417).</span></span>

- <span data-ttu-id="1f2e1-121">Kod analizini tamamen devre dışı bırakmak için `EnableNETAnalyzers` , `false` proje dosyanızda olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1f2e1-121">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="1f2e1-122">Daha fazla bilgi için bkz. [Enablenetçözümleyiciler](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="1f2e1-122">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="1f2e1-123">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="1f2e1-123">Affected APIs</span></span>

<span data-ttu-id="1f2e1-124">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="1f2e1-124">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
