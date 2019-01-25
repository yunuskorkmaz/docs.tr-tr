---
title: '#pragma Uyarısı - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 7c664ee7d6e0e083eba958e6ee36a63009e13956
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606614"
---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="7a91c-102">#pragma uyarısı (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7a91c-102">#pragma warning (C# Reference)</span></span>
<span data-ttu-id="7a91c-103">`#pragma warning` etkinleştirebilir veya belirli uyarıları devre dışı bırak.</span><span class="sxs-lookup"><span data-stu-id="7a91c-103">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a91c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7a91c-104">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7a91c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7a91c-105">Parameters</span></span>  
 `warning-list`  
 <span data-ttu-id="7a91c-106">Uyarı numaralarını virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="7a91c-106">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="7a91c-107">"CS" ön eki isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7a91c-107">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="7a91c-108">Hiçbir uyarı numaralarını belirtildiğinde `disable` tüm uyarıları devre dışı bırakır ve `restore` tüm uyarıları etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="7a91c-108">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a91c-109">Visual Studio'da uyarı numaralarını bulmak için projenizi derleyin ve uyarısı sayıları bulun **çıkış** penceresi.</span><span class="sxs-lookup"><span data-stu-id="7a91c-109">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a91c-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="7a91c-110">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7a91c-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a91c-111">See also</span></span>

- [<span data-ttu-id="7a91c-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="7a91c-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="7a91c-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7a91c-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="7a91c-114">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="7a91c-114">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
- [<span data-ttu-id="7a91c-115">C# Derleyici Hataları</span><span class="sxs-lookup"><span data-stu-id="7a91c-115">C# Compiler Errors</span></span>](../../../csharp/language-reference/compiler-messages/index.md)
