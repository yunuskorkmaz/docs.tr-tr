---
title: '#pragma Uyarısı (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 89ff8151d55ac58a1b114f7727297704ce26b9a7
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43481936"
---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="6001f-102">#pragma uyarısı (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="6001f-102">#pragma warning (C# Reference)</span></span>
<span data-ttu-id="6001f-103">`#pragma warning` etkinleştirebilir veya belirli uyarıları devre dışı bırak.</span><span class="sxs-lookup"><span data-stu-id="6001f-103">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6001f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6001f-104">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6001f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6001f-105">Parameters</span></span>  
 `warning-list`  
 <span data-ttu-id="6001f-106">Uyarı numaralarını virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="6001f-106">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="6001f-107">"CS" ön eki isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6001f-107">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="6001f-108">Hiçbir uyarı numaralarını belirtildiğinde `disable` tüm uyarıları devre dışı bırakır ve `restore` tüm uyarıları etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="6001f-108">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6001f-109">Visual Studio'da uyarı numaralarını bulmak için projenizi derleyin ve uyarısı sayıları bulun **çıkış** penceresi.</span><span class="sxs-lookup"><span data-stu-id="6001f-109">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6001f-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="6001f-110">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6001f-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6001f-111">See Also</span></span>

- [<span data-ttu-id="6001f-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="6001f-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="6001f-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6001f-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="6001f-114">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="6001f-114">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)  
- [<span data-ttu-id="6001f-115">C# Derleyici Hataları</span><span class="sxs-lookup"><span data-stu-id="6001f-115">C# Compiler Errors</span></span>](../../../csharp/language-reference/compiler-messages/index.md)
