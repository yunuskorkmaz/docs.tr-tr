---
title: ^= İşleci (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- ^=_CSharpKeyword
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
ms.openlocfilehash: d6546f23ffb6dee792339a7e3863bf58ae668d58
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43540052"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="b910e-102">^= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b910e-102">^= Operator (C# Reference)</span></span>
<span data-ttu-id="b910e-103">Düzeyinde dışlamalı OR ataması işleci.</span><span class="sxs-lookup"><span data-stu-id="b910e-103">The exclusive-OR assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b910e-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b910e-104">Remarks</span></span>  
 <span data-ttu-id="b910e-105">Bir ifade formu</span><span class="sxs-lookup"><span data-stu-id="b910e-105">An expression of the form</span></span>  
  
```csharp  
x ^= y  
```  
  
 <span data-ttu-id="b910e-106">olarak değerlendirilir</span><span class="sxs-lookup"><span data-stu-id="b910e-106">is evaluated as</span></span>  
  
```csharp  
x = x ^ y  
```  
  
 <span data-ttu-id="b910e-107">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="b910e-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="b910e-108">[^ İşleci](../../../csharp/language-reference/operators/xor-operator.md) bir bit düzeyinde dışlamalı OR işlemi integral işlenenlerde ve mantıksal hariç veya üzerinde gerçekleştirir [bool](../../../csharp/language-reference/keywords/bool.md) işlenen.</span><span class="sxs-lookup"><span data-stu-id="b910e-108">The [^ operator](../../../csharp/language-reference/operators/xor-operator.md) performs a bitwise exclusive-OR operation on integral operands and logical exclusive-OR on [bool](../../../csharp/language-reference/keywords/bool.md) operands.</span></span>  
  
 <span data-ttu-id="b910e-109">^ = İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [^ işleci](../../../csharp/language-reference/operators/xor-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="b910e-109">The ^= operator cannot be overloaded directly, but user-defined types can overload the [^ operator](../../../csharp/language-reference/operators/xor-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b910e-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="b910e-110">Example</span></span>  
 [!code-csharp[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="b910e-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b910e-111">See Also</span></span>

- [<span data-ttu-id="b910e-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="b910e-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="b910e-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b910e-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="b910e-114">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="b910e-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
