---
title: '#pragma uyarı- C# başvuru'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: e34df66add032ad6324ac59a34f93b213d39ab48
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608551"
---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="6ece0-102">#pragma uyarısı (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="6ece0-102">#pragma warning (C# Reference)</span></span>
<span data-ttu-id="6ece0-103">`#pragma warning`Belirli uyarıları etkinleştirebilir veya devre dışı bırakabilir.</span><span class="sxs-lookup"><span data-stu-id="6ece0-103">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ece0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6ece0-104">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ece0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6ece0-105">Parameters</span></span>  
 `warning-list`  
 <span data-ttu-id="6ece0-106">Uyarı numaralarının virgülle ayrılmış bir listesi.</span><span class="sxs-lookup"><span data-stu-id="6ece0-106">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="6ece0-107">"CS" ön eki isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6ece0-107">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="6ece0-108">Hiçbir uyarı numarası belirtilmediğinde, `disable` tüm uyarıları devre dışı bırakır ve `restore` tüm uyarıları etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="6ece0-108">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ece0-109">Visual Studio 'da uyarı numaralarını bulmak için projenizi derleyin ve ardından **Çıkış** penceresinde uyarı numaralarını arayın.</span><span class="sxs-lookup"><span data-stu-id="6ece0-109">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ece0-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="6ece0-110">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6ece0-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ece0-111">See also</span></span>

- [<span data-ttu-id="6ece0-112">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="6ece0-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6ece0-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6ece0-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6ece0-114">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="6ece0-114">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="6ece0-115">C# Derleyici Hataları</span><span class="sxs-lookup"><span data-stu-id="6ece0-115">C# Compiler Errors</span></span>](../compiler-messages/index.md)
