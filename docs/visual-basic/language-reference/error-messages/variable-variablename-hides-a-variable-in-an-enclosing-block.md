---
description: "Hakkında daha fazla bilgi edinin: BC30616: ' <variablename> ' değişkeni kapsayan bir blokta bir değişkeni gizliyor"
title: "'<variablename>' değişkeni, kapsayan bir bloktaki değişkeni gizliyor"
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: a0b2a4d024ff0409b5617354b5e671ca6dc0305b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666127"
---
# <a name="bc30616-variable-variablename-hides-a-variable-in-an-enclosing-block"></a><span data-ttu-id="2c740-103">BC30616: ' \<variablename> ' değişkeni kapsayan bir blokta bir değişkeni gizliyor</span><span class="sxs-lookup"><span data-stu-id="2c740-103">BC30616: Variable '\<variablename>' hides a variable in an enclosing block</span></span>

<span data-ttu-id="2c740-104">Bir blok içine alınmış bir değişken, başka bir yerel değişkenle aynı ada sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2c740-104">A variable enclosed in a block has the same name as another local variable.</span></span>

 <span data-ttu-id="2c740-105">**Hata kimliği:** BC30616</span><span class="sxs-lookup"><span data-stu-id="2c740-105">**Error ID:** BC30616</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="2c740-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="2c740-106">To correct this error</span></span>

- <span data-ttu-id="2c740-107">Diğer yerel değişkenlerle aynı olmaması için, ekteki bloktaki değişkeni yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="2c740-107">Rename the variable in the enclosed block so that it is not the same as any other local variables.</span></span> <span data-ttu-id="2c740-108">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="2c740-108">For example:</span></span>

    ```vb
    Dim a, b, x As Integer
    If a = b Then
       Dim y As Integer = 20 ' Uniquely named block variable.
    End If
    ```

- <span data-ttu-id="2c740-109">Bu hatanın yaygın bir nedeni, `Catch e As Exception` bir olay işleyicisinin içinde kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="2c740-109">A common cause for this error is the use of `Catch e As Exception` inside an event handler.</span></span> <span data-ttu-id="2c740-110">Bu durumda, `Catch` blok değişkenini `ex` yerine adlandırın `e` .</span><span class="sxs-lookup"><span data-stu-id="2c740-110">If this is the case, name the `Catch` block variable `ex` rather than `e`.</span></span>

- <span data-ttu-id="2c740-111">Bu hatanın daha yaygın bir kaynağı, farklı bir blokta bir blok içinde belirtilen yerel bir değişkene erişme girişiminde bulunur `Try` `Catch` .</span><span class="sxs-lookup"><span data-stu-id="2c740-111">Another common source of this error is an attempt to access a local variable declared within a `Try` block in a separate `Catch` block.</span></span> <span data-ttu-id="2c740-112">Bunu düzeltmek için değişkeni yapının dışında bildirin `Try...Catch...Finally` .</span><span class="sxs-lookup"><span data-stu-id="2c740-112">To correct this, declare the variable outside the `Try...Catch...Finally` structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="2c740-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c740-113">See also</span></span>

- [<span data-ttu-id="2c740-114">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="2c740-114">Try...Catch...Finally Statement</span></span>](../statements/try-catch-finally-statement.md)
- [<span data-ttu-id="2c740-115">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="2c740-115">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
