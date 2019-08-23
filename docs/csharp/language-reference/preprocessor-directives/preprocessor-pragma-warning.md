---
title: '#pragma uyarı- C# başvuru'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: dc221235e78a187f921815ed6e6c7750778014d8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922269"
---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="61986-102">#pragma uyarısı (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="61986-102">#pragma warning (C# Reference)</span></span>
<span data-ttu-id="61986-103">`#pragma warning`Belirli uyarıları etkinleştirebilir veya devre dışı bırakabilir.</span><span class="sxs-lookup"><span data-stu-id="61986-103">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61986-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="61986-104">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
## <a name="parameters"></a><span data-ttu-id="61986-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="61986-105">Parameters</span></span>  
 `warning-list`  
 <span data-ttu-id="61986-106">Uyarı numaralarının virgülle ayrılmış bir listesi.</span><span class="sxs-lookup"><span data-stu-id="61986-106">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="61986-107">"CS" ön eki isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="61986-107">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="61986-108">Hiçbir uyarı numarası belirtilmediğinde, `disable` tüm uyarıları devre dışı bırakır ve `restore` tüm uyarıları etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="61986-108">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="61986-109">Visual Studio 'da uyarı numaralarını bulmak için projenizi derleyin ve ardından **Çıkış** penceresinde uyarı numaralarını arayın.</span><span class="sxs-lookup"><span data-stu-id="61986-109">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61986-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="61986-110">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="61986-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61986-111">See also</span></span>

- [<span data-ttu-id="61986-112">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="61986-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="61986-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="61986-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="61986-114">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="61986-114">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="61986-115">C# Derleyici Hataları</span><span class="sxs-lookup"><span data-stu-id="61986-115">C# Compiler Errors</span></span>](../compiler-messages/index.md)
