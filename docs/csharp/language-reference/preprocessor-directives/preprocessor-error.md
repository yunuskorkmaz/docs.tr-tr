---
title: '#Hata-C# başvurusu'
ms.date: 08/24/2020
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: cc1e0640886e3f3c1c74a54f64961a56c8b030e4
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812373"
---
# <a name="error-c-reference"></a><span data-ttu-id="138db-102">#error (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="138db-102">#error (C# Reference)</span></span>

<span data-ttu-id="138db-103">`#error` kodunuzda belirli bir konumdan [CS1029](../compiler-messages/cs1029.md) Kullanıcı tanımlı bir hata oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="138db-103">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="138db-104">Örnek:</span><span class="sxs-lookup"><span data-stu-id="138db-104">For example:</span></span>

```csharp
#error Deprecated code in this method.
```

> [!NOTE]
> <span data-ttu-id="138db-105">Derleyici `#error version` özel bir şekilde davranır ve bir derleyici hatası, CS8304, kullanılan derleyici ve dil sürümlerini içeren bir ileti ile rapor eder.</span><span class="sxs-lookup"><span data-stu-id="138db-105">The compiler treats `#error version` in a special way and reports a compiler error, CS8304, with a message containing the used compiler and language versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="138db-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="138db-106">Remarks</span></span>

<span data-ttu-id="138db-107">Öğesinin yaygın kullanımı `#error` koşullu bir yönergedir.</span><span class="sxs-lookup"><span data-stu-id="138db-107">A common use of `#error` is in a conditional directive.</span></span>

<span data-ttu-id="138db-108">[#Warning](./preprocessor-warning.md)ile Kullanıcı tanımlı bir uyarı oluşturmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="138db-108">It is also possible to generate a user-defined warning with [#warning](./preprocessor-warning.md).</span></span>

## <a name="example"></a><span data-ttu-id="138db-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="138db-109">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="138db-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="138db-110">See also</span></span>

- [<span data-ttu-id="138db-111">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="138db-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="138db-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="138db-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="138db-113">C# Önişlemci yönergeleri</span><span class="sxs-lookup"><span data-stu-id="138db-113">C# Preprocessor Directives</span></span>](./index.md)
