---
title: '#pragma uyarı- C# başvuru'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 5620ea9e5f31c22e26bee95a450335bb179ced25
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712474"
---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="2eac9-102">#pragma uyarısı (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="2eac9-102">#pragma warning (C# Reference)</span></span>
<span data-ttu-id="2eac9-103">`#pragma warning` belirli uyarıları etkinleştirebilir veya devre dışı bırakabilir.</span><span class="sxs-lookup"><span data-stu-id="2eac9-103">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2eac9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2eac9-104">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
## <a name="parameters"></a><span data-ttu-id="2eac9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2eac9-105">Parameters</span></span>  
 `warning-list`  
 <span data-ttu-id="2eac9-106">Uyarı numaralarının virgülle ayrılmış bir listesi.</span><span class="sxs-lookup"><span data-stu-id="2eac9-106">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="2eac9-107">"CS" ön eki isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="2eac9-107">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="2eac9-108">Hiçbir uyarı numarası belirtilmediğinde `disable` tüm uyarıları devre dışı bırakır ve tüm uyarıları `restore`.</span><span class="sxs-lookup"><span data-stu-id="2eac9-108">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2eac9-109">Visual Studio 'da uyarı numaralarını bulmak için projenizi derleyin ve ardından **Çıkış** penceresinde uyarı numaralarını arayın.</span><span class="sxs-lookup"><span data-stu-id="2eac9-109">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2eac9-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="2eac9-110">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2eac9-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2eac9-111">See also</span></span>

- [<span data-ttu-id="2eac9-112">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="2eac9-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2eac9-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2eac9-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2eac9-114">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="2eac9-114">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="2eac9-115">C# Derleyici Hataları</span><span class="sxs-lookup"><span data-stu-id="2eac9-115">C# Compiler Errors</span></span>](../compiler-messages/index.md)
