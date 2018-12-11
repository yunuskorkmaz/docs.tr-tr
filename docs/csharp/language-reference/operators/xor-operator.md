---
title: ^ İşleci - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ^_CSharpKeyword
helpviewer_keywords:
- ^ operator [C#]
- bitwise exclusive OR operator [C#]
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
ms.openlocfilehash: f6f09f197502af1bc38bcdef97dd1db0ad9c7c08
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236953"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="506af-102">^ İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="506af-102">^ Operator (C# Reference)</span></span>
<span data-ttu-id="506af-103">İkili `^` işleçleri tamsayı türleri için önceden tanımlanmış ve `bool`.</span><span class="sxs-lookup"><span data-stu-id="506af-103">Binary `^` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="506af-104">İntegral türleri için `^` hesaplar. bit düzeyinde dışlamalı OR işlenenleri.</span><span class="sxs-lookup"><span data-stu-id="506af-104">For integral types, `^` computes the bitwise exclusive-OR of its operands.</span></span> <span data-ttu-id="506af-105">İçin `bool` işlenenini `^` mantıksal özel hesaplar- veya kendi işlenenler; diğer bir deyişle, sonuç `true` işlenenleri tam olarak biri olan ve yalnızca, `true`.</span><span class="sxs-lookup"><span data-stu-id="506af-105">For `bool` operands, `^` computes the logical exclusive-or of its operands; that is, the result is `true` if and only if exactly one of its operands is `true`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="506af-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="506af-106">Remarks</span></span>  
 <span data-ttu-id="506af-107">Kullanıcı tanımlı türler aşırı yükleme `^` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="506af-107">User-defined types can overload the `^` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="506af-108">Tamsayı türlerinde işlemler genellikle numaralandırma üzerinde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="506af-108">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="506af-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="506af-109">Example</span></span>  
 [!code-csharp[csRefOperators#30](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-operator_1.cs)]  
  
 <span data-ttu-id="506af-110">Hesaplama `0xf8 ^ 0x3f` önceki örnekte bir bit düzeyinde gerçekleştirir hariç veya F8 ve 3F onaltılık değerlerine karşılık gelen aşağıdaki iki ikili değerleri:</span><span class="sxs-lookup"><span data-stu-id="506af-110">The computation of `0xf8 ^ 0x3f` in the previous example performs a bitwise exclusive-OR of the following two binary values, which correspond to the hexadecimal values F8 and 3F:</span></span>  
  
 `1111 1000`  
  
 `0011 1111`  
  
 <span data-ttu-id="506af-111">Özel veya sonucu `1100 0111`, onaltılık C7 olduğu.</span><span class="sxs-lookup"><span data-stu-id="506af-111">The result of the exclusive-OR is `1100 0111`, which is C7 in hexadecimal.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="506af-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="506af-112">See Also</span></span>

- [<span data-ttu-id="506af-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="506af-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="506af-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="506af-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="506af-115">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="506af-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
