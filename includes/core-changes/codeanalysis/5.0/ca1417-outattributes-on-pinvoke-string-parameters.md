---
ms.openlocfilehash: ada458ffeeba95d4989507f90c789b159f359797
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065173"
---
### <a name="ca1417-outattribute-on-string-parameter-for-pinvoke"></a><span data-ttu-id="0fd60-101">P/Invoke için String parametresinde CA1417: OutAttribute</span><span class="sxs-lookup"><span data-stu-id="0fd60-101">CA1417: OutAttribute on string parameter for P/Invoke</span></span>

<span data-ttu-id="0fd60-102">.Net Code Analyzer Rule [CA1417](/visualstudio/code-quality/ca1417) , varsayılan olarak .NET 5,0 ' den başlayarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="0fd60-102">.NET code analyzer rule [CA1417](/visualstudio/code-quality/ca1417) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="0fd60-103">Bir parametrenin değere göre geçirildiği ve ile işaretlenen tüm [Platform çağırma (P/Invoke)](../../../../docs/standard/native-interop/pinvoke.md) yöntemi tanımları için bir derleme uyarısı oluşturur <xref:System.String> <xref:System.Runtime.InteropServices.OutAttribute> .</span><span class="sxs-lookup"><span data-stu-id="0fd60-103">It produces a build warning for any [Platform Invoke (P/Invoke)](../../../../docs/standard/native-interop/pinvoke.md) method definitions where a <xref:System.String> parameter is passed by value and marked with <xref:System.Runtime.InteropServices.OutAttribute>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0fd60-104">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="0fd60-104">Change description</span></span>

<span data-ttu-id="0fd60-105">.NET SDK, .NET 5,0 'den başlayarak [.net kaynak kodu Çözümleyicileri](../../../../docs/fundamentals/productivity/code-analysis.md)içerir.</span><span class="sxs-lookup"><span data-stu-id="0fd60-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="0fd60-106">Bu kuralların bazıları varsayılan olarak [CA1417](/visualstudio/code-quality/ca1417)dahil olmak üzere etkindir.</span><span class="sxs-lookup"><span data-stu-id="0fd60-106">Several of these rules are enabled, by default, including [CA1417](/visualstudio/code-quality/ca1417).</span></span> <span data-ttu-id="0fd60-107">Projeniz bu kuralı ihlal eden ve uyarıları hata olarak işleyecek şekilde yapılandırılan kodu içeriyorsa, bu değişiklik yapınızı bozabilir.</span><span class="sxs-lookup"><span data-stu-id="0fd60-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="0fd60-108">Rule CA1417 bayrakları [P/](../../../../docs/standard/native-interop/pinvoke.md) bir <xref:System.String> parametrenin öznitelik ile işaretlendiği <xref:System.Runtime.InteropServices.OutAttribute> ve değer Ile geçirildiği yöntem tanımlarını çağırır.</span><span class="sxs-lookup"><span data-stu-id="0fd60-108">Rule CA1417 flags [P/Invoke](../../../../docs/standard/native-interop/pinvoke.md) method definitions where a <xref:System.String> parameter is marked with the <xref:System.Runtime.InteropServices.OutAttribute> attribute and is passed by value.</span></span> <span data-ttu-id="0fd60-109">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="0fd60-109">For example:</span></span>

```csharp
[DllImport("MyLibrary")]
private static extern void PIMethod([Out] string s);
```

<span data-ttu-id="0fd60-110">.NET çalışma zamanı, bir programdaki her benzersiz sabit değer dizesine tek bir başvuru içeren Intern havuzu adlı bir tablo tutar.</span><span class="sxs-lookup"><span data-stu-id="0fd60-110">The .NET runtime maintains a table, called the intern pool, that contains a single reference to each unique literal string in a program.</span></span> <span data-ttu-id="0fd60-111">İle işaretlenmiş bir dize, <xref:System.Runtime.InteropServices.OutAttribute> bir P/Invoke yöntemine değer ile geçirildiyse, çalışma zamanı kararsız hale gelebilirler.</span><span class="sxs-lookup"><span data-stu-id="0fd60-111">If an interned string marked with <xref:System.Runtime.InteropServices.OutAttribute> is passed by value to a P/Invoke method, the runtime can be destabilized.</span></span> <span data-ttu-id="0fd60-112">Dize oluşturma hakkında daha fazla bilgi için, bkz <xref:System.String.Intern(System.String)?displayProperty=nameWithType> . açıklamalar.</span><span class="sxs-lookup"><span data-stu-id="0fd60-112">For more information about string interning, see the remarks for <xref:System.String.Intern(System.String)?displayProperty=nameWithType>.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0fd60-113">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="0fd60-113">Version introduced</span></span>

<span data-ttu-id="0fd60-114">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="0fd60-114">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0fd60-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="0fd60-115">Recommended action</span></span>

- <span data-ttu-id="0fd60-116">Değiştirilen dize verilerini çağırana geri almanız gerekiyorsa, dizeyi başvuruya göre geçirin.</span><span class="sxs-lookup"><span data-stu-id="0fd60-116">If you need to marshal modified string data back to the caller, pass the string by reference instead.</span></span>

  ```csharp
  [DllImport("MyLibrary")]
  private static extern void PIMethod(out string s);
  ```

- <span data-ttu-id="0fd60-117">Değiştirilen dize verilerini çağırana geri sıralayamaz, öğesini kaldırmanız yeterlidir <xref:System.Runtime.InteropServices.OutAttribute> .</span><span class="sxs-lookup"><span data-stu-id="0fd60-117">If you don't need to marshal modified string data back to the caller, simply remove the <xref:System.Runtime.InteropServices.OutAttribute>.</span></span>

  ```csharp
  [DllImport("MyLibrary")]
  private static extern void PIMethod(string s);
  ```

  <span data-ttu-id="0fd60-118">Daha fazla bilgi için bkz. [CA1417](/visualstudio/code-quality/ca1417).</span><span class="sxs-lookup"><span data-stu-id="0fd60-118">For more information, see [CA1417](/visualstudio/code-quality/ca1417).</span></span>

- <span data-ttu-id="0fd60-119">Kod analizini tamamen devre dışı bırakmak için `EnableNETAnalyzers` , `false` proje dosyanızda olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0fd60-119">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="0fd60-120">Daha fazla bilgi için bkz. [Enablenetçözümleyiciler](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="0fd60-120">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="0fd60-121">Kategori</span><span class="sxs-lookup"><span data-stu-id="0fd60-121">Category</span></span>

<span data-ttu-id="0fd60-122">Kod analizi</span><span class="sxs-lookup"><span data-stu-id="0fd60-122">Code analysis</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0fd60-123">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="0fd60-123">Affected APIs</span></span>

<span data-ttu-id="0fd60-124">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="0fd60-124">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
