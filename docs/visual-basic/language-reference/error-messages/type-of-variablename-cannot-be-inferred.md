---
description: "Daha fazla bilgi: BC30982: ' ' türü, <variablename> döngü sınırları ve Step değişkeni aynı türe genişlemediğinden gösterilemiyor"
title: Döngü sınırları ve step değişkeni aynı türe genişlemediğinden '<variablename>' türü çıkarılamıyor
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: 399e021500813127df6ecede2534783df09ac8dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641167"
---
# <a name="bc30982-type-of-variablename-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a><span data-ttu-id="25960-103">BC30982: ' ' türü, \<variablename> döngü sınırları ve Step değişkeni aynı türe genişlemediğinden çıkarsanamıyor</span><span class="sxs-lookup"><span data-stu-id="25960-103">BC30982: Type of '\<variablename>' cannot be inferred because the loop bounds and the step variable do not widen to the same type</span></span>

<span data-ttu-id="25960-104">`For...Next`Aşağıdaki koşullar doğru olduğu için derleyicinin döngü denetim değişkeni için bir veri türünü çıkarmadığı bir döngü yazmadınız:</span><span class="sxs-lookup"><span data-stu-id="25960-104">You have written a `For...Next` loop in which the compiler cannot infer a data type for the loop control variable because the following conditions are true:</span></span>

- <span data-ttu-id="25960-105">Döngü denetim değişkeninin veri türü bir `As` yan tümcesiyle belirtilmemiş.</span><span class="sxs-lookup"><span data-stu-id="25960-105">The data type of the loop control variable is not specified with an `As` clause.</span></span>

- <span data-ttu-id="25960-106">Döngü sınırları ve Step değişkeni en az iki veri türü içeriyor.</span><span class="sxs-lookup"><span data-stu-id="25960-106">The loop bounds and step variable contain at least two data types.</span></span>

- <span data-ttu-id="25960-107">Veri türleri arasında standart dönüştürmeler yok.</span><span class="sxs-lookup"><span data-stu-id="25960-107">No standard conversions exist between the data types.</span></span>

 <span data-ttu-id="25960-108">Bu nedenle, derleyici bir döngünün denetim değişkeninin veri türünü çıkarsamaz.</span><span class="sxs-lookup"><span data-stu-id="25960-108">Therefore, the compiler cannot infer the data type of a loop's control variable.</span></span>

 <span data-ttu-id="25960-109">Aşağıdaki örnekte, Step değişkeni bir karakterdir ve döngü sınırlarının her ikisi de tamsayılardır.</span><span class="sxs-lookup"><span data-stu-id="25960-109">In the following example, the step variable is a character and the loop bounds are both integers.</span></span> <span data-ttu-id="25960-110">Karakterler ve tamsayılar arasında standart dönüştürme olmadığından, bu hata bildirilir.</span><span class="sxs-lookup"><span data-stu-id="25960-110">Because there is no standard conversion between characters and integers, this error is reported.</span></span>

```vb
Dim stepVar = "1"c
Dim m = 0
Dim n = 20

' Not valid.
' For i = 1 To 10 Step stepVar
    ' Loop processing
' Next
```

<span data-ttu-id="25960-111">**Hata kimliği:** BC30982</span><span class="sxs-lookup"><span data-stu-id="25960-111">**Error ID:** BC30982</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="25960-112">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="25960-112">To correct this error</span></span>

- <span data-ttu-id="25960-113">Döngü sınırlarının ve adım değişkeninin türlerini, en az birinin diğerlerinin genişlecekleri bir tür olması için gereken şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="25960-113">Change the types of the loop bounds and step variable as necessary so that at least one of them is a type that the others widen to.</span></span> <span data-ttu-id="25960-114">Yukarıdaki örnekte, türünü `stepVar` olarak değiştirin `Integer` .</span><span class="sxs-lookup"><span data-stu-id="25960-114">In the preceding example, change the type of `stepVar` to `Integer`.</span></span>

  ```vb
  Dim stepVar = 1
  ```

  <span data-ttu-id="25960-115">-veya-</span><span class="sxs-lookup"><span data-stu-id="25960-115">-or-</span></span>

  ```vb
  Dim stepVar As Integer = 1
  ```

- <span data-ttu-id="25960-116">Döngü sınırlarını ve adım değişkenini uygun türlere dönüştürmek için açık dönüştürme işlevlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="25960-116">Use explicit conversion functions to convert the loop bounds and step variable to the appropriate types.</span></span> <span data-ttu-id="25960-117">Yukarıdaki örnekte, `Val` işlevini öğesine uygulayın `stepVar` .</span><span class="sxs-lookup"><span data-stu-id="25960-117">In the preceding example, apply the `Val` function to `stepVar`.</span></span>

  ```vb
  For i = 1 To 10 Step Val(stepVar)
      ' Loop processing
  Next
  ```

## <a name="see-also"></a><span data-ttu-id="25960-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25960-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [<span data-ttu-id="25960-119">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="25960-119">For...Next Statement</span></span>](../statements/for-next-statement.md)
- [<span data-ttu-id="25960-120">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="25960-120">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="25960-121">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25960-121">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="25960-122">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="25960-122">Option Infer Statement</span></span>](../statements/option-infer-statement.md)
- [<span data-ttu-id="25960-123">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="25960-123">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="25960-124">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="25960-124">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
