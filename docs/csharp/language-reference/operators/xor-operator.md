---
title: ^ İşleci (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- ^_CSharpKeyword
helpviewer_keywords:
- ^ operator [C#]
- bitwise exclusive OR operator [C#]
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
ms.openlocfilehash: 5cc3cd2cfc932646e5b2dd6ec034555b07582379
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33271256"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="a2dd3-102">^ İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a2dd3-102">^ Operator (C# Reference)</span></span>
<span data-ttu-id="a2dd3-103">İkili `^` işleçleri tam sayı türleri için önceden tanımlanmış ve `bool`.</span><span class="sxs-lookup"><span data-stu-id="a2dd3-103">Binary `^` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="a2dd3-104">Tam sayı türleri için `^` bitwise hesaplar işlenenleri hariç veya.</span><span class="sxs-lookup"><span data-stu-id="a2dd3-104">For integral types, `^` computes the bitwise exclusive-OR of its operands.</span></span> <span data-ttu-id="a2dd3-105">İçin `bool` işlenenler, `^` mantıksal özel hesaplar- veya kendi işlenenleri; diğer bir deyişle, sonuç `true` işlenenleri tam olarak birine varsa ve yalnızca ise `true`.</span><span class="sxs-lookup"><span data-stu-id="a2dd3-105">For `bool` operands, `^` computes the logical exclusive-or of its operands; that is, the result is `true` if and only if exactly one of its operands is `true`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2dd3-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a2dd3-106">Remarks</span></span>  
 <span data-ttu-id="a2dd3-107">Kullanıcı tanımlı türler aşırı yükleme `^` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="a2dd3-107">User-defined types can overload the `^` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="a2dd3-108">Tam sayı türleri üzerinde işlemler genellikle numaralandırma üzerinde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="a2dd3-108">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2dd3-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2dd3-109">Example</span></span>  
 [!code-csharp[csRefOperators#30](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-operator_1.cs)]  
  
 <span data-ttu-id="a2dd3-110">Hesaplaması `0xf8 ^ 0x3f` önceki örnekte bit gerçekleştirir hariç veya onaltılık değerler F8 ve 3F karşılık gelen aşağıdaki iki ikili değerleri:</span><span class="sxs-lookup"><span data-stu-id="a2dd3-110">The computation of `0xf8 ^ 0x3f` in the previous example performs a bitwise exclusive-OR of the following two binary values, which correspond to the hexadecimal values F8 and 3F:</span></span>  
  
 `1111 1000`  
  
 `0011 1111`  
  
 <span data-ttu-id="a2dd3-111">Dışlayan OR sonucu `1100 0111`, onaltılık C7 değil.</span><span class="sxs-lookup"><span data-stu-id="a2dd3-111">The result of the exclusive-OR is `1100 0111`, which is C7 in hexadecimal.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2dd3-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a2dd3-112">See Also</span></span>  
 [<span data-ttu-id="a2dd3-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="a2dd3-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a2dd3-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a2dd3-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a2dd3-115">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="a2dd3-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
