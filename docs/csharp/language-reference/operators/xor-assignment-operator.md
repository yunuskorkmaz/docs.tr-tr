---
title: ^ = işleci - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ^=_CSharpKeyword
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
ms.openlocfilehash: 12189d6469a9716d3b7ebcffef23423a75692d1a
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333557"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="0560f-102">^ = işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0560f-102">^= operator (C# Reference)</span></span>

<span data-ttu-id="0560f-103">Düzeyinde dışlamalı OR ataması işleci.</span><span class="sxs-lookup"><span data-stu-id="0560f-103">The exclusive-OR assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="0560f-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0560f-104">Remarks</span></span>

<span data-ttu-id="0560f-105">Bir ifade formu</span><span class="sxs-lookup"><span data-stu-id="0560f-105">An expression of the form</span></span>

```csharp
x ^= y
```

<span data-ttu-id="0560f-106">olarak değerlendirilir</span><span class="sxs-lookup"><span data-stu-id="0560f-106">is evaluated as</span></span>

```csharp
x = x ^ y
```

<span data-ttu-id="0560f-107">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="0560f-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="0560f-108">[^ İşleci](xor-operator.md) bir bit düzeyinde dışlamalı OR işlemi integral işlenenlerde ve mantıksal hariç veya üzerinde gerçekleştirir [bool](../keywords/bool.md) işlenen.</span><span class="sxs-lookup"><span data-stu-id="0560f-108">The [^ operator](xor-operator.md) performs a bitwise exclusive-OR operation on integral operands and logical exclusive-OR on [bool](../keywords/bool.md) operands.</span></span>

<span data-ttu-id="0560f-109">^ = İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [^ işleci](xor-operator.md) (bkz [işleci](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="0560f-109">The ^= operator cannot be overloaded directly, but user-defined types can overload the [^ operator](xor-operator.md) (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="0560f-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="0560f-110">Example</span></span>

[!code-csharp[csRefOperators#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#23)]

## <a name="see-also"></a><span data-ttu-id="0560f-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0560f-111">See also</span></span>

- [<span data-ttu-id="0560f-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="0560f-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0560f-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0560f-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0560f-114">C#işleçleri</span><span class="sxs-lookup"><span data-stu-id="0560f-114">C# operators</span></span>](index.md)