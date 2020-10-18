---
title: Döngü sınırları ve step değişkeni aynı türe genişlemediğinden '<variablename>' türü çıkarılamıyor
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: 1330cbd6567b69df9bd811ced49c6df2e120a0b2
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161215"
---
# <a name="bc30982-type-of-variablename-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a><span data-ttu-id="7e7fc-102">BC30982: ' ' türü, \<variablename> döngü sınırları ve Step değişkeni aynı türe genişlemediğinden çıkarsanamıyor</span><span class="sxs-lookup"><span data-stu-id="7e7fc-102">BC30982: Type of '\<variablename>' cannot be inferred because the loop bounds and the step variable do not widen to the same type</span></span>

<span data-ttu-id="7e7fc-103">`For...Next`Aşağıdaki koşullar doğru olduğu için derleyicinin döngü denetim değişkeni için bir veri türünü çıkarmadığı bir döngü yazmadınız:</span><span class="sxs-lookup"><span data-stu-id="7e7fc-103">You have written a `For...Next` loop in which the compiler cannot infer a data type for the loop control variable because the following conditions are true:</span></span>

- <span data-ttu-id="7e7fc-104">Döngü denetim değişkeninin veri türü bir `As` yan tümcesiyle belirtilmemiş.</span><span class="sxs-lookup"><span data-stu-id="7e7fc-104">The data type of the loop control variable is not specified with an `As` clause.</span></span>

- <span data-ttu-id="7e7fc-105">Döngü sınırları ve Step değişkeni en az iki veri türü içeriyor.</span><span class="sxs-lookup"><span data-stu-id="7e7fc-105">The loop bounds and step variable contain at least two data types.</span></span>

- <span data-ttu-id="7e7fc-106">Veri türleri arasında standart dönüştürmeler yok.</span><span class="sxs-lookup"><span data-stu-id="7e7fc-106">No standard conversions exist between the data types.</span></span>

 <span data-ttu-id="7e7fc-107">Bu nedenle, derleyici bir döngünün denetim değişkeninin veri türünü çıkarsamaz.</span><span class="sxs-lookup"><span data-stu-id="7e7fc-107">Therefore, the compiler cannot infer the data type of a loop's control variable.</span></span>

 <span data-ttu-id="7e7fc-108">Aşağıdaki örnekte, Step değişkeni bir karakterdir ve döngü sınırlarının her ikisi de tamsayılardır.</span><span class="sxs-lookup"><span data-stu-id="7e7fc-108">In the following example, the step variable is a character and the loop bounds are both integers.</span></span> <span data-ttu-id="7e7fc-109">Karakterler ve tamsayılar arasında standart dönüştürme olmadığından, bu hata bildirilir.</span><span class="sxs-lookup"><span data-stu-id="7e7fc-109">Because there is no standard conversion between characters and integers, this error is reported.</span></span>

```vb
Dim stepVar = "1"c
Dim m = 0
Dim n = 20

' Not valid.
' For i = 1 To 10 Step stepVar
    ' Loop processing
' Next
```

<span data-ttu-id="7e7fc-110">**Hata kimliği:** BC30982</span><span class="sxs-lookup"><span data-stu-id="7e7fc-110">**Error ID:** BC30982</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="7e7fc-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="7e7fc-111">To correct this error</span></span>

- <span data-ttu-id="7e7fc-112">Döngü sınırlarının ve adım değişkeninin türlerini, en az birinin diğerlerinin genişlecekleri bir tür olması için gereken şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7e7fc-112">Change the types of the loop bounds and step variable as necessary so that at least one of them is a type that the others widen to.</span></span> <span data-ttu-id="7e7fc-113">Yukarıdaki örnekte, türünü `stepVar` olarak değiştirin `Integer` .</span><span class="sxs-lookup"><span data-stu-id="7e7fc-113">In the preceding example, change the type of `stepVar` to `Integer`.</span></span>

  ```vb
  Dim stepVar = 1
  ```

  <span data-ttu-id="7e7fc-114">-veya-</span><span class="sxs-lookup"><span data-stu-id="7e7fc-114">-or-</span></span>

  ```vb
  Dim stepVar As Integer = 1
  ```

- <span data-ttu-id="7e7fc-115">Döngü sınırlarını ve adım değişkenini uygun türlere dönüştürmek için açık dönüştürme işlevlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7e7fc-115">Use explicit conversion functions to convert the loop bounds and step variable to the appropriate types.</span></span> <span data-ttu-id="7e7fc-116">Yukarıdaki örnekte, `Val` işlevini öğesine uygulayın `stepVar` .</span><span class="sxs-lookup"><span data-stu-id="7e7fc-116">In the preceding example, apply the `Val` function to `stepVar`.</span></span>

  ```vb
  For i = 1 To 10 Step Val(stepVar)
      ' Loop processing
  Next
  ```

## <a name="see-also"></a><span data-ttu-id="7e7fc-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e7fc-117">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [<span data-ttu-id="7e7fc-118">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="7e7fc-118">For...Next Statement</span></span>](../statements/for-next-statement.md)
- [<span data-ttu-id="7e7fc-119">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="7e7fc-119">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="7e7fc-120">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7e7fc-120">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="7e7fc-121">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="7e7fc-121">Option Infer Statement</span></span>](../statements/option-infer-statement.md)
- [<span data-ttu-id="7e7fc-122">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="7e7fc-122">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="7e7fc-123">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="7e7fc-123">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
