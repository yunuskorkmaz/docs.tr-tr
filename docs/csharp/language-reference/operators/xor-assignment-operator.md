---
title: ^ = İşleci - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ^=_CSharpKeyword
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
ms.openlocfilehash: cf39c8e8586e9d4f537fe38d8b28f55542db6ab8
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237161"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="4611d-102">^= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="4611d-102">^= Operator (C# Reference)</span></span>
<span data-ttu-id="4611d-103">Düzeyinde dışlamalı OR ataması işleci.</span><span class="sxs-lookup"><span data-stu-id="4611d-103">The exclusive-OR assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4611d-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4611d-104">Remarks</span></span>  
 <span data-ttu-id="4611d-105">Bir ifade formu</span><span class="sxs-lookup"><span data-stu-id="4611d-105">An expression of the form</span></span>  
  
```csharp  
x ^= y  
```  
  
 <span data-ttu-id="4611d-106">olarak değerlendirilir</span><span class="sxs-lookup"><span data-stu-id="4611d-106">is evaluated as</span></span>  
  
```csharp  
x = x ^ y  
```  
  
 <span data-ttu-id="4611d-107">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="4611d-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="4611d-108">[^ İşleci](../../../csharp/language-reference/operators/xor-operator.md) bir bit düzeyinde dışlamalı OR işlemi integral işlenenlerde ve mantıksal hariç veya üzerinde gerçekleştirir [bool](../../../csharp/language-reference/keywords/bool.md) işlenen.</span><span class="sxs-lookup"><span data-stu-id="4611d-108">The [^ operator](../../../csharp/language-reference/operators/xor-operator.md) performs a bitwise exclusive-OR operation on integral operands and logical exclusive-OR on [bool](../../../csharp/language-reference/keywords/bool.md) operands.</span></span>  
  
 <span data-ttu-id="4611d-109">^ = İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [^ işleci](../../../csharp/language-reference/operators/xor-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="4611d-109">The ^= operator cannot be overloaded directly, but user-defined types can overload the [^ operator](../../../csharp/language-reference/operators/xor-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4611d-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="4611d-110">Example</span></span>  
 [!code-csharp[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="4611d-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4611d-111">See Also</span></span>

- [<span data-ttu-id="4611d-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="4611d-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="4611d-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4611d-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="4611d-114">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="4611d-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
