---
title: Kod Analizi uyarılarını gösterme
description: .NET kod analizi ihlallerini bastırmak için kullanabileceğiniz farklı yolları öğrenin.
ms.date: 01/28/2021
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- code analysis, suppress warnings
- suppress code analysis warnings
ms.openlocfilehash: a8fdfbddd2393f9c6c8cd882a63a9ecc6cb1dc95
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105637045"
---
# <a name="how-to-suppress-code-analysis-warnings"></a><span data-ttu-id="00223-103">Kod Analizi uyarılarını gösterme</span><span class="sxs-lookup"><span data-stu-id="00223-103">How to suppress code analysis warnings</span></span>

<span data-ttu-id="00223-104">Bu makalede, .NET uygulamanızı oluştururken kod analizinden gelen uyarıları bastırmak için çeşitli yollar ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="00223-104">This article covers the various ways you can suppress warnings from code analysis when you build your .NET app.</span></span>

> [!TIP]
> <span data-ttu-id="00223-105">Geliştirme ortamınız olarak Visual Studio kullanıyorsanız *ampul* menüsü, uyarıları sizin için göstermede kodu oluşturan seçenekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00223-105">If you're using Visual Studio as your development environment, the *light bulb* menu provides options that generate the code to suppress warnings for you.</span></span> <span data-ttu-id="00223-106">Daha fazla bilgi için bkz. [Ihlalleri gösterme](/visualstudio/code-quality/use-roslyn-analyzers?#suppress-violations).</span><span class="sxs-lookup"><span data-stu-id="00223-106">For more information, see [Suppress violations](/visualstudio/code-quality/use-roslyn-analyzers?#suppress-violations).</span></span>

## <a name="disable-the-rule"></a><span data-ttu-id="00223-107">Kuralı devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="00223-107">Disable the rule</span></span>

<span data-ttu-id="00223-108">Uyarıya neden olan kod analizi kuralını devre dışı bırakarak, tüm dosyanız veya projeniz için kuralı devre dışı bırakın (kullandığınız [yapılandırma dosyasının](configuration-files.md) kapsamına bağlı olarak).</span><span class="sxs-lookup"><span data-stu-id="00223-108">By disabling the code analysis rule that's causing the warning, you disable the rule for your entire file or project (depending on the scope of the [configuration file](configuration-files.md) that you use).</span></span> <span data-ttu-id="00223-109">Kuralı devre dışı bırakmak için yapılandırma dosyasında önem derecesini ayarlayın `none` .</span><span class="sxs-lookup"><span data-stu-id="00223-109">To disable the rule, set its severity to `none` in the configuration file.</span></span>

```ini
[*.{cs,vb}]
dotnet_diagnostic.<rule-ID>.severity = none
```

<span data-ttu-id="00223-110">Kural özellikleri hakkında daha fazla bilgi için bkz. [kural önem derecesini yapılandırma](~/docs/fundamentals/code-analysis/configuration-options.md#severity-level).</span><span class="sxs-lookup"><span data-stu-id="00223-110">For more information about rule severities, see [Configure rule severity](~/docs/fundamentals/code-analysis/configuration-options.md#severity-level).</span></span>

## <a name="use-a-preprocessor-directive"></a><span data-ttu-id="00223-111">Önişlemci yönergesi kullanma</span><span class="sxs-lookup"><span data-stu-id="00223-111">Use a preprocessor directive</span></span>

<span data-ttu-id="00223-112">Yalnızca belirli bir kod satırı için uyarıyı bastırmak üzere [#pragma warning (C#)](../../csharp/language-reference/preprocessor-directives.md#pragma-warning) veya [Disable (Visual Basic)](../../visual-basic/language-reference/directives/disable-enable.md) yönergesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="00223-112">Use a [#pragma warning (C#)](../../csharp/language-reference/preprocessor-directives.md#pragma-warning) or [Disable (Visual Basic)](../../visual-basic/language-reference/directives/disable-enable.md) directive to suppress the warning for only a specific line of code.</span></span>

```csharp
    try { ... }
    catch (Exception e)
    {
#pragma warning disable CA2200 // Rethrow to preserve stack details
        throw e;
#pragma warning restore CA2200 // Rethrow to preserve stack details
    }
```

```vb
    Try
        ...
    Catch e As Exception
#Disable Warning CA2200 ' Rethrow to preserve stack details
        Throw e
#Enable Warning CA2200 ' Rethrow to preserve stack details
    End Try
```

## <a name="use-the-suppressmessageattribute"></a><span data-ttu-id="00223-113">SuppressMessageAttribute kullanın</span><span class="sxs-lookup"><span data-stu-id="00223-113">Use the SuppressMessageAttribute</span></span>

<span data-ttu-id="00223-114">Bir <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> uyarıyı, kaynak dosyasında ya da proje için küresel bir gizlemeler dosyasında (*globalsuppressions. cs* veya *globalsuppressions. vb*) gizlemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00223-114">You can use a <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> to suppress a warning either in the source file or in a global suppressions file for the project (*GlobalSuppressions.cs* or *GlobalSuppressions.vb*).</span></span> <span data-ttu-id="00223-115">Bu öznitelik, bir uyarıyı yalnızca projenizin veya dosyanızın belirli bölümlerinde bastırmak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="00223-115">This attribute provides a way to suppress a warning in only certain parts of your project or file.</span></span>

<span data-ttu-id="00223-116">Özniteliği için gereken iki, Konumsal parametre <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> ve kural *kimliği* *kategorisidir* .</span><span class="sxs-lookup"><span data-stu-id="00223-116">The two required, positional parameters for the <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attribute are the *category* of the rule and the *rule ID*.</span></span> <span data-ttu-id="00223-117">Aşağıdaki kod parçacığı, `"Usage"` ve `"CA2200:Rethrow to preserve stack details"` Bu parametreleri geçirir.</span><span class="sxs-lookup"><span data-stu-id="00223-117">The following code snippet passes `"Usage"` and `"CA2200:Rethrow to preserve stack details"` for these parameters.</span></span>

```csharp
[System.Diagnostics.CodeAnalysis.SuppressMessage("Usage", "CA2200:Rethrow to preserve stack details", Justification = "Not production code.")]
private static void IngorableCharacters()
{
    try
    {
        ...
    }
    catch (Exception e)
    {
        throw e;
    }
}
```

<span data-ttu-id="00223-118">Özniteliği genel gizlemeleri dosyasına eklerseniz, gizleme, örneğin, gizlemeyi istediğiniz düzeye göre [kapsamınızda](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) `"member"` .</span><span class="sxs-lookup"><span data-stu-id="00223-118">If you add the attribute to the global suppressions file, you [scope](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) the suppression to the desired level, for example `"member"`.</span></span> <span data-ttu-id="00223-119">Uyarının özelliği kullanılarak gizlenmesi gereken API 'YI belirtirsiniz <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Target> .</span><span class="sxs-lookup"><span data-stu-id="00223-119">You specify the API where the warning should be suppressed using the <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Target> property.</span></span>

```csharp
[assembly: SuppressMessage("Usage", "CA2200:Rethrow to preserve stack details", Justification = "Not production code.", Scope = "member", Target = "~M:MyApp.Program.IngorableCharacters")]
```

<span data-ttu-id="00223-120">Açıkça sağlanmış Kullanıcı kaynağıyla eşleşmeyen derleyici tarafından oluşturulan koda yönelik uyarıları gizlemek için, gizleme özniteliğini küresel bir gizlemeleri dosyasına koymanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="00223-120">To suppress warnings for compiler-generated code that doesn't map to explicitly provided user source, you must put the suppression attribute in a global suppressions file.</span></span> <span data-ttu-id="00223-121">Örneğin, aşağıdaki kod derleyiciye yayılan bir oluşturucuya karşı bir ihlalin bastırır:</span><span class="sxs-lookup"><span data-stu-id="00223-121">For example, the following code suppresses a violation against a compiler-emitted constructor:</span></span>

```csharp
[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="MyTools.Type..ctor()")]
```

## <a name="see-also"></a><span data-ttu-id="00223-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00223-122">See also</span></span>

- [<span data-ttu-id="00223-123">İhlalleri gösterme (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="00223-123">Suppress violations (Visual Studio)</span></span>](/visualstudio/code-quality/use-roslyn-analyzers?#suppress-violations)
