---
title: 'Son değişiklik: CA2200: yığın ayrıntılarını korumak için yeniden throw'
description: Kod Analizi kuralı CA2200 'nin etkinleştirilmesi nedeniyle .NET 5 ' teki önemli değişiklik hakkında bilgi edinin.
ms.date: 09/03/2020
ms.openlocfilehash: 776a1bcf16c19364017e4652837720080fb7ba72
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257732"
---
# <a name="warning-ca2200-rethrow-to-preserve-stack-details"></a><span data-ttu-id="4315e-103">Uyarı CA2200: yığın ayrıntılarını korumak için yeniden throw</span><span class="sxs-lookup"><span data-stu-id="4315e-103">Warning CA2200: Rethrow to preserve stack details</span></span>

<span data-ttu-id="4315e-104">.Net Code Analyzer Rule [CA2200](/visualstudio/code-quality/ca2200) , varsayılan olarak .NET 5,0 ' den başlayarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="4315e-104">.NET code analyzer rule [CA2200](/visualstudio/code-quality/ca2200) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="4315e-105">Özel durum oluşturan herhangi bir blok için derleme uyarısı üretir `catch` ve özel durum `throw` deyimde açıkça belirtilir.</span><span class="sxs-lookup"><span data-stu-id="4315e-105">It produces a build warning for any `catch` blocks that rethrow an exception and the exception is explicitly specified in the `throw` statement.</span></span>

## <a name="change-description"></a><span data-ttu-id="4315e-106">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="4315e-106">Change description</span></span>

<span data-ttu-id="4315e-107">.NET 5 ' den başlayarak .NET SDK [.net kaynak kodu Çözümleyicileri](../../../../fundamentals/code-analysis/overview.md)içerir.</span><span class="sxs-lookup"><span data-stu-id="4315e-107">Starting in .NET 5, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="4315e-108">Bu kuralların bazıları varsayılan olarak [CA2200](/visualstudio/code-quality/ca2200)dahil olmak üzere etkindir.</span><span class="sxs-lookup"><span data-stu-id="4315e-108">Several of these rules are enabled, by default, including [CA2200](/visualstudio/code-quality/ca2200).</span></span> <span data-ttu-id="4315e-109">Projeniz bu kuralı ihlal eden ve uyarıları hata olarak işleyecek şekilde yapılandırılan kodu içeriyorsa, bu değişiklik yapınızı bozabilir.</span><span class="sxs-lookup"><span data-stu-id="4315e-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="4315e-110">Kural CA2200 bayrakları, özel durumların yeniden oluşturulduğu ve özel durum değişkeninin bildiriminde belirtildiği durumdur `throw` .</span><span class="sxs-lookup"><span data-stu-id="4315e-110">Rule CA2200 flags code where exceptions are rethrown and the exception variable is specified in the `throw` statement.</span></span> <span data-ttu-id="4315e-111">Bir özel durum oluştuğunda, içerdiği bilgilerin bir kısmı yığın izdir.</span><span class="sxs-lookup"><span data-stu-id="4315e-111">When an exception is thrown, part of the information it carries is the stack trace.</span></span> <span data-ttu-id="4315e-112">Yığın izlemesi, özel durumu oluşturan yöntemiyle başlayan ve özel durumu yakalayan yöntemle biten Yöntem çağrısı hiyerarşisinin bir listesidir.</span><span class="sxs-lookup"><span data-stu-id="4315e-112">The stack trace is a list of the method call hierarchy that starts with the method that throws the exception and ends with the method that catches the exception.</span></span> <span data-ttu-id="4315e-113">Deyimdeki özel durum belirtilerek bir özel durum yeniden oluşturulursa `throw` , yığın izlemesi geçerli yöntemde yeniden başlatılır ve özel durumu oluşturan özgün yöntem ile geçerli yöntem arasındaki yöntem çağrılarının listesi kaybedilir.</span><span class="sxs-lookup"><span data-stu-id="4315e-113">If an exception is rethrown by specifying the exception in the `throw` statement, the stack trace restarts at the current method and the list of method calls between the original method that threw the exception and the current method is lost.</span></span> <span data-ttu-id="4315e-114">Özgün yığın izleme bilgilerini özel durumla birlikte tutmak için, `throw` özel durumu belirtmeden ifadesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="4315e-114">To keep the original stack trace information with the exception, use the `throw` statement without specifying the exception.</span></span>

<span data-ttu-id="4315e-115">Aşağıdaki kod parçacığı kural CA2200 için bir uyarı oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="4315e-115">The following code snippet does not produce a warning for rule CA2200.</span></span> <span data-ttu-id="4315e-116">Ancak açıklamalı çizgi bir ihlalin *tetikleyecektir* .</span><span class="sxs-lookup"><span data-stu-id="4315e-116">The commented line *would* trigger a violation, however.</span></span>

```csharp
catch (ArithmeticException e)
{
    // throw e;
    throw;
}
```

## <a name="version-introduced"></a><span data-ttu-id="4315e-117">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="4315e-117">Version introduced</span></span>

<span data-ttu-id="4315e-118">5.0</span><span class="sxs-lookup"><span data-stu-id="4315e-118">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="4315e-119">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="4315e-119">Recommended action</span></span>

- <span data-ttu-id="4315e-120">Özel durumu açıkça belirtmeden özel durumları yeniden throw.</span><span class="sxs-lookup"><span data-stu-id="4315e-120">Rethrow exceptions without specifying the exception explicitly.</span></span> <span data-ttu-id="4315e-121">Daha fazla bilgi için bkz. [CA2200](/visualstudio/code-quality/ca2200).</span><span class="sxs-lookup"><span data-stu-id="4315e-121">For more information, see [CA2200](/visualstudio/code-quality/ca2200).</span></span>

- <span data-ttu-id="4315e-122">Kod analizini tamamen devre dışı bırakmak için `EnableNETAnalyzers` , `false` proje dosyanızda olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4315e-122">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="4315e-123">Daha fazla bilgi için bkz. [Enablenetçözümleyiciler](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="4315e-123">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="4315e-124">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="4315e-124">Affected APIs</span></span>

<span data-ttu-id="4315e-125">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="4315e-125">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
