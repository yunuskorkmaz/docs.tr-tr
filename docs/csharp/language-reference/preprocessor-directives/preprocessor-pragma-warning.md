---
title: '#pragma uyarısı - C# Referans'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 5620ea9e5f31c22e26bee95a450335bb179ced25
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712474"
---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="30e57-102">#pragma uyarısı (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="30e57-102">#pragma warning (C# Reference)</span></span>
<span data-ttu-id="30e57-103">`#pragma warning`bazı uyarıları etkinleştirebilir veya devre dışı kılabilir.</span><span class="sxs-lookup"><span data-stu-id="30e57-103">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30e57-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30e57-104">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
## <a name="parameters"></a><span data-ttu-id="30e57-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="30e57-105">Parameters</span></span>  
 `warning-list`  
 <span data-ttu-id="30e57-106">Uyarı numaralarının virgülden ayrılmış bir listesi.</span><span class="sxs-lookup"><span data-stu-id="30e57-106">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="30e57-107">"CS" öneki isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="30e57-107">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="30e57-108">Uyarı numarası belirtilmediğinde, `disable` tüm uyarıları devre `restore` dışı katanır ve tüm uyarıları etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="30e57-108">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="30e57-109">Visual Studio'da uyarı numaralarını bulmak için projenizi oluşturun ve **çıktı** penceresindeuyarı numaralarını arayın.</span><span class="sxs-lookup"><span data-stu-id="30e57-109">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30e57-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="30e57-110">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="30e57-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30e57-111">See also</span></span>

- [<span data-ttu-id="30e57-112">C# Referans</span><span class="sxs-lookup"><span data-stu-id="30e57-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="30e57-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="30e57-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="30e57-114">C# Önİşleme İşlemciler Direktifleri</span><span class="sxs-lookup"><span data-stu-id="30e57-114">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="30e57-115">C# Derleyici Hataları</span><span class="sxs-lookup"><span data-stu-id="30e57-115">C# Compiler Errors</span></span>](../compiler-messages/index.md)
