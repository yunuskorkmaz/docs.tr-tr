---
ms.openlocfilehash: b697bbf6844759de8babd4245667e7b333884ff8
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538936"
---
### <a name="ca2200-rethrow-to-preserve-stack-details"></a><span data-ttu-id="83440-101">CA2200: Yığın ayrıntılarını korumak için yeniden fırlatın</span><span class="sxs-lookup"><span data-stu-id="83440-101">CA2200: Rethrow to preserve stack details</span></span>

<span data-ttu-id="83440-102">.Net Code Analyzer Rule [CA2200](/visualstudio/code-quality/ca2200) , varsayılan olarak .NET 5,0 ' den başlayarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="83440-102">.NET code analyzer rule [CA2200](/visualstudio/code-quality/ca2200) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="83440-103">Özel durum oluşturan herhangi bir blok için derleme uyarısı üretir `catch` ve özel durum `throw` deyimde açıkça belirtilir.</span><span class="sxs-lookup"><span data-stu-id="83440-103">It produces a build warning for any `catch` blocks that rethrow an exception and the exception is explicitly specified in the `throw` statement.</span></span>

#### <a name="change-description"></a><span data-ttu-id="83440-104">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="83440-104">Change description</span></span>

<span data-ttu-id="83440-105">.NET SDK, .NET 5,0 'den başlayarak [.net kaynak kodu Çözümleyicileri](../../../../docs/fundamentals/productivity/code-analysis.md)içerir.</span><span class="sxs-lookup"><span data-stu-id="83440-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="83440-106">Bu kuralların bazıları varsayılan olarak [CA2200](/visualstudio/code-quality/ca2200)dahil olmak üzere etkindir.</span><span class="sxs-lookup"><span data-stu-id="83440-106">Several of these rules are enabled, by default, including [CA2200](/visualstudio/code-quality/ca2200).</span></span> <span data-ttu-id="83440-107">Projeniz bu kuralı ihlal eden ve uyarıları hata olarak işleyecek şekilde yapılandırılan kodu içeriyorsa, bu değişiklik yapınızı bozabilir.</span><span class="sxs-lookup"><span data-stu-id="83440-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="83440-108">Kural CA2200 bayrakları, özel durumların yeniden oluşturulduğu ve özel durum değişkeninin bildiriminde belirtildiği durumdur `throw` .</span><span class="sxs-lookup"><span data-stu-id="83440-108">Rule CA2200 flags code where exceptions are rethrown and the exception variable is specified in the `throw` statement.</span></span> <span data-ttu-id="83440-109">Bir özel durum oluştuğunda, içerdiği bilgilerin bir kısmı yığın izdir.</span><span class="sxs-lookup"><span data-stu-id="83440-109">When an exception is thrown, part of the information it carries is the stack trace.</span></span> <span data-ttu-id="83440-110">Yığın izlemesi, özel durumu oluşturan yöntemiyle başlayan ve özel durumu yakalayan yöntemle biten Yöntem çağrısı hiyerarşisinin bir listesidir.</span><span class="sxs-lookup"><span data-stu-id="83440-110">The stack trace is a list of the method call hierarchy that starts with the method that throws the exception and ends with the method that catches the exception.</span></span> <span data-ttu-id="83440-111">Deyimdeki özel durum belirtilerek bir özel durum yeniden oluşturulursa `throw` , yığın izlemesi geçerli yöntemde yeniden başlatılır ve özel durumu oluşturan özgün yöntem ile geçerli yöntem arasındaki yöntem çağrılarının listesi kaybedilir.</span><span class="sxs-lookup"><span data-stu-id="83440-111">If an exception is rethrown by specifying the exception in the `throw` statement, the stack trace restarts at the current method and the list of method calls between the original method that threw the exception and the current method is lost.</span></span> <span data-ttu-id="83440-112">Özgün yığın izleme bilgilerini özel durumla birlikte tutmak için, `throw` özel durumu belirtmeden ifadesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="83440-112">To keep the original stack trace information with the exception, use the `throw` statement without specifying the exception.</span></span>

<span data-ttu-id="83440-113">Aşağıdaki kod parçacığı kural CA2200 için bir uyarı oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="83440-113">The following code snippet does not produce a warning for rule CA2200.</span></span> <span data-ttu-id="83440-114">Ancak açıklamalı çizgi bir ihlalin *tetikleyecektir* .</span><span class="sxs-lookup"><span data-stu-id="83440-114">The commented line *would* trigger a violation, however.</span></span>

```csharp
catch (ArithmeticException e)
{
    // throw e;
    throw;
}
```

#### <a name="version-introduced"></a><span data-ttu-id="83440-115">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="83440-115">Version introduced</span></span>

<span data-ttu-id="83440-116">5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="83440-116">5.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="83440-117">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="83440-117">Recommended action</span></span>

- <span data-ttu-id="83440-118">Özel durumu açıkça belirtmeden özel durumları yeniden throw.</span><span class="sxs-lookup"><span data-stu-id="83440-118">Rethrow exceptions without specifying the exception explicitly.</span></span> <span data-ttu-id="83440-119">Daha fazla bilgi için bkz. [CA2200](/visualstudio/code-quality/ca2200).</span><span class="sxs-lookup"><span data-stu-id="83440-119">For more information, see [CA2200](/visualstudio/code-quality/ca2200).</span></span>

- <span data-ttu-id="83440-120">Kod analizini tamamen devre dışı bırakmak için `EnableNETAnalyzers` , `false` proje dosyanızda olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="83440-120">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="83440-121">Daha fazla bilgi için bkz. [Enablenetçözümleyiciler](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="83440-121">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="83440-122">Kategori</span><span class="sxs-lookup"><span data-stu-id="83440-122">Category</span></span>

<span data-ttu-id="83440-123">Kod analizi</span><span class="sxs-lookup"><span data-stu-id="83440-123">Code analysis</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="83440-124">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="83440-124">Affected APIs</span></span>

<span data-ttu-id="83440-125">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="83440-125">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
