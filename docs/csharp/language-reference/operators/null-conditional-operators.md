---
title: Null koşullu işleçleri - C# başvurusu
ms.custom: seodec18
ms.date: 04/03/2015
helpviewer_keywords:
- null-conditional operators [C#]
- ?. operator [C#]
- ?[] operator [C#]
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
ms.openlocfilehash: 38298cded904cbfedeaf3c6b66c74d610d714902
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333245"
---
# <a name="-and--null-conditional-operators-c-and-visual-basic"></a><span data-ttu-id="216fc-102">?.</span><span class="sxs-lookup"><span data-stu-id="216fc-102">?.</span></span> <span data-ttu-id="216fc-103">ve? [] null koşullu işleçleri (C# ve Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="216fc-103">and ?[] null-conditional operators (C# and Visual Basic)</span></span>

<span data-ttu-id="216fc-104">Üye erişimi gerçekleştirmeden önce sol işleneni null değerini test eder (`?.`) ya da dizin (`?[]`) döndürür; işlem `null` sol işlenen değerlendirilirse `null`.</span><span class="sxs-lookup"><span data-stu-id="216fc-104">Tests the value of the left-hand operand for null before performing a member access (`?.`) or index (`?[]`) operation; returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="216fc-105">Bu işleçler null işlemek için daha az kod denetler, özellikle azalan düzende veri yapılarda yazmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="216fc-105">These operators help you write less code to handle null checks, especially for descending into data structures.</span></span>

```csharp
int? length = customers?.Length; // null if customers is null
Customer first = customers?[0];  // null if customers is null
int? count = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null
```

<span data-ttu-id="216fc-106">Null koşullu işleçleri short-circuiting.</span><span class="sxs-lookup"><span data-stu-id="216fc-106">The null-conditional operators are short-circuiting.</span></span>  <span data-ttu-id="216fc-107">Null koşullu üye erişimi ve dizin işlemlerini zincirinin tek bir işlemde döndürürse, rest zincirinin yürütme durdurur.</span><span class="sxs-lookup"><span data-stu-id="216fc-107">If one operation in a chain of conditional member access and index operations returns null, the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="216fc-108">Aşağıdaki örnekte, `E` değilse yürütülmez `A`, `B`, veya `C` null olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="216fc-108">In the following example, `E` doesn't execute if `A`, `B`, or `C` evaluates to null.</span></span>

```csharp
A?.B?.C?.Do(E);
A?.B?.C?[E];
```

<span data-ttu-id="216fc-109">Null koşullu üye erişimi için başka bir kullanım temsilciler çok daha az kod ile iş parçacığı güvenli bir şekilde çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="216fc-109">Another use for the null-conditional member access is invoking delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="216fc-110">Kod aşağıdaki gibi eski yöntem gerektirir:</span><span class="sxs-lookup"><span data-stu-id="216fc-110">The old way requires code like the following:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
    handler(…);
```

<span data-ttu-id="216fc-111">Yeni yolu çok daha kolaydır:</span><span class="sxs-lookup"><span data-stu-id="216fc-111">The new way is much simpler:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="216fc-112">Derleyici değerlendirmek için kod oluşturur çünkü iş parçacığı açısından güvenli yeni yoludur `PropertyChanged` sonucu geçici bir değişkende tutma yalnızca bir kez.</span><span class="sxs-lookup"><span data-stu-id="216fc-112">The new way is thread-safe because the compiler generates code to evaluate `PropertyChanged` one time only, keeping the result in a temporary variable.</span></span> <span data-ttu-id="216fc-113">Açıkça çağırmak ihtiyacınız `Invoke` yöntemi hiçbir null koşullu temsilci çağırma söz dizimi olduğundan `PropertyChanged?(e)`.</span><span class="sxs-lookup"><span data-stu-id="216fc-113">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `PropertyChanged?(e)`.</span></span>

## <a name="language-specifications"></a><span data-ttu-id="216fc-114">Dil özellikleri</span><span class="sxs-lookup"><span data-stu-id="216fc-114">Language specifications</span></span>

<span data-ttu-id="216fc-115">Daha fazla bilgi için [Null koşullu işleci](~/_csharplang/spec/expressions.md#null-conditional-operator) içinde [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="216fc-115">For more information, see [Null-conditional operator](~/_csharplang/spec/expressions.md#null-conditional-operator) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="216fc-116">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="216fc-116">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="216fc-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="216fc-117">See also</span></span>

- [<span data-ttu-id="216fc-118">?? (null birleşim işleci)</span><span class="sxs-lookup"><span data-stu-id="216fc-118">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="216fc-119">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="216fc-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="216fc-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="216fc-120">C# Programming Guide</span></span>](../../programming-guide/index.md)