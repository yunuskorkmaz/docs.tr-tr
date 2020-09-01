---
description: '#Hata-C# başvurusu'
title: '#Hata-C# başvurusu'
ms.date: 08/24/2020
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 76325901c5e39f340545b186a0aa9546cd853ff8
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138104"
---
# <a name="error-c-reference"></a><span data-ttu-id="b0f68-103">#error (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b0f68-103">#error (C# Reference)</span></span>

<span data-ttu-id="b0f68-104">`#error` kodunuzda belirli bir konumdan [CS1029](../compiler-messages/cs1029.md) Kullanıcı tanımlı bir hata oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0f68-104">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="b0f68-105">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b0f68-105">For example:</span></span>

```csharp
#error Deprecated code in this method.
```

> [!NOTE]
> <span data-ttu-id="b0f68-106">Derleyici `#error version` özel bir şekilde davranır ve bir derleyici hatası, CS8304, kullanılan derleyici ve dil sürümlerini içeren bir ileti ile rapor eder.</span><span class="sxs-lookup"><span data-stu-id="b0f68-106">The compiler treats `#error version` in a special way and reports a compiler error, CS8304, with a message containing the used compiler and language versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="b0f68-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b0f68-107">Remarks</span></span>

<span data-ttu-id="b0f68-108">Öğesinin yaygın kullanımı `#error` koşullu bir yönergedir.</span><span class="sxs-lookup"><span data-stu-id="b0f68-108">A common use of `#error` is in a conditional directive.</span></span>

<span data-ttu-id="b0f68-109">[#Warning](./preprocessor-warning.md)ile Kullanıcı tanımlı bir uyarı oluşturmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="b0f68-109">It is also possible to generate a user-defined warning with [#warning](./preprocessor-warning.md).</span></span>

## <a name="example"></a><span data-ttu-id="b0f68-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="b0f68-110">Example</span></span>

```csharp
// preprocessor_error.cs
// CS1029 expected
#define DEBUG
class MainClass
{
    static void Main()
    {
#if DEBUG
#error DEBUG is defined
#endif
    }
}
```

## <a name="see-also"></a><span data-ttu-id="b0f68-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0f68-111">See also</span></span>

- [<span data-ttu-id="b0f68-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="b0f68-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b0f68-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b0f68-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b0f68-114">C# Önişlemci yönergeleri</span><span class="sxs-lookup"><span data-stu-id="b0f68-114">C# Preprocessor Directives</span></span>](./index.md)
