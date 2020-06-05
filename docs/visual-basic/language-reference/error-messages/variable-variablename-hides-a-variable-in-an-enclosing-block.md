---
title: "'<variablename>' değişkeni, kapsayan bir bloktaki değişkeni gizliyor"
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 474a920c9cfdfba7a8157320d9c88b8677958425
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406527"
---
# <a name="variable-variablename-hides-a-variable-in-an-enclosing-block"></a><span data-ttu-id="27fa9-102">'\<variablename>' değişkeni, kapsayan bir bloktaki değişkeni gizliyor</span><span class="sxs-lookup"><span data-stu-id="27fa9-102">Variable '\<variablename>' hides a variable in an enclosing block</span></span>
<span data-ttu-id="27fa9-103">Bir blok içine alınmış bir değişken, başka bir yerel değişkenle aynı ada sahiptir.</span><span class="sxs-lookup"><span data-stu-id="27fa9-103">A variable enclosed in a block has the same name as another local variable.</span></span>  
  
 <span data-ttu-id="27fa9-104">**Hata kimliği:** BC30616</span><span class="sxs-lookup"><span data-stu-id="27fa9-104">**Error ID:** BC30616</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="27fa9-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="27fa9-105">To correct this error</span></span>  
  
- <span data-ttu-id="27fa9-106">Diğer yerel değişkenlerle aynı olmaması için, ekteki bloktaki değişkeni yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="27fa9-106">Rename the variable in the enclosed block so that it is not the same as any other local variables.</span></span> <span data-ttu-id="27fa9-107">Örnek:</span><span class="sxs-lookup"><span data-stu-id="27fa9-107">For example:</span></span>  
  
    ```vb  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
- <span data-ttu-id="27fa9-108">Bu hatanın yaygın bir nedeni, `Catch e As Exception` bir olay işleyicisinin içinde kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="27fa9-108">A common cause for this error is the use of `Catch e As Exception` inside an event handler.</span></span> <span data-ttu-id="27fa9-109">Bu durumda, `Catch` blok değişkenini `ex` yerine adlandırın `e` .</span><span class="sxs-lookup"><span data-stu-id="27fa9-109">If this is the case, name the `Catch` block variable `ex` rather than `e`.</span></span>  
  
- <span data-ttu-id="27fa9-110">Bu hatanın daha yaygın bir kaynağı, farklı bir blokta bir blok içinde belirtilen yerel bir değişkene erişme girişiminde bulunur `Try` `Catch` .</span><span class="sxs-lookup"><span data-stu-id="27fa9-110">Another common source of this error is an attempt to access a local variable declared within a `Try` block in a separate `Catch` block.</span></span> <span data-ttu-id="27fa9-111">Bunu düzeltmek için değişkeni yapının dışında bildirin `Try...Catch...Finally` .</span><span class="sxs-lookup"><span data-stu-id="27fa9-111">To correct this, declare the variable outside the `Try...Catch...Finally` structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27fa9-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27fa9-112">See also</span></span>

- [<span data-ttu-id="27fa9-113">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="27fa9-113">Try...Catch...Finally Statement</span></span>](../statements/try-catch-finally-statement.md)
- [<span data-ttu-id="27fa9-114">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="27fa9-114">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
