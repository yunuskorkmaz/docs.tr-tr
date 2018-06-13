---
title: '#pragma Uyarısı (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 079045f4eb52f03afa8733620029396d80cb75fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273663"
---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="a6697-102">#pragma uyarısı (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a6697-102">#pragma warning (C# Reference)</span></span>
<span data-ttu-id="a6697-103">`#pragma warning` etkinleştirmek veya belirli uyarıları devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6697-103">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6697-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a6697-104">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a6697-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a6697-105">Parameters</span></span>  
 `warning-list`  
 <span data-ttu-id="a6697-106">Uyarı numaralarını virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="a6697-106">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="a6697-107">"CS" öneki isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a6697-107">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="a6697-108">Hiçbir uyarı numaralarını belirtildiğinde `disable` tüm uyarıları devre dışı bırakır ve `restore` tüm uyarıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6697-108">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6697-109">Visual Studio'da uyarı numaralarını bulmak için projeyi oluşturun ve uyarı sayıları arayın **çıkış** penceresi.</span><span class="sxs-lookup"><span data-stu-id="a6697-109">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6697-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="a6697-110">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a6697-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a6697-111">See Also</span></span>  
 [<span data-ttu-id="a6697-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="a6697-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a6697-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a6697-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a6697-114">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="a6697-114">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)  
 [<span data-ttu-id="a6697-115">C# Derleyici Hataları</span><span class="sxs-lookup"><span data-stu-id="a6697-115">C# Compiler Errors</span></span>](../../../csharp/language-reference/compiler-messages/index.md)
