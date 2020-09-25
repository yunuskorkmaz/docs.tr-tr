---
description: '#pragma warning-C# başvurusu'
title: '#pragma warning-C# başvurusu'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 5b67d384e37a5e509ce8ebcc5ddeb16a4437ea2b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168536"
---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="69645-103">#pragma uyarısı (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="69645-103">#pragma warning (C# Reference)</span></span>

<span data-ttu-id="69645-104">`#pragma warning` Belirli uyarıları etkinleştirebilir veya devre dışı bırakabilir.</span><span class="sxs-lookup"><span data-stu-id="69645-104">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69645-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="69645-105">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
## <a name="parameters"></a><span data-ttu-id="69645-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="69645-106">Parameters</span></span>  

 `warning-list`  
 <span data-ttu-id="69645-107">Uyarı numaralarının virgülle ayrılmış bir listesi.</span><span class="sxs-lookup"><span data-stu-id="69645-107">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="69645-108">"CS" ön eki isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="69645-108">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="69645-109">Hiçbir uyarı numarası belirtilmediğinde, `disable` tüm uyarıları devre dışı bırakır ve `restore` tüm uyarıları etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="69645-109">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="69645-110">Visual Studio 'da uyarı numaralarını bulmak için projenizi derleyin ve ardından **Çıkış** penceresinde uyarı numaralarını arayın.</span><span class="sxs-lookup"><span data-stu-id="69645-110">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69645-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="69645-111">Example</span></span>  
  
```csharp
// pragma_warning.cs  
using System;  
  
#pragma warning disable 414, CS3021  
[CLSCompliant(false)]  
public class C  
{  
    int i = 1;  
    static void Main()  
    {  
    }  
}  
#pragma warning restore CS3021  
[CLSCompliant(false)]  // CS3021  
public class D  
{  
    int i = 1;  
    public static void F()  
    {  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="69645-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69645-112">See also</span></span>

- [<span data-ttu-id="69645-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="69645-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="69645-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="69645-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="69645-115">C# Önişlemci yönergeleri</span><span class="sxs-lookup"><span data-stu-id="69645-115">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="69645-116">C# derleyici hataları</span><span class="sxs-lookup"><span data-stu-id="69645-116">C# Compiler Errors</span></span>](../compiler-messages/index.md)
