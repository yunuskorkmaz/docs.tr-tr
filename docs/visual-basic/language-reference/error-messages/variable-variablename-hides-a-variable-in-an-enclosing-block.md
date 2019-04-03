---
title: "'<variablename>' değişkeni, kapsayan bir bloktaki değişkeni gizliyor"
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 15c35cbb829bec782771b584ea25b111b81b5e1f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827139"
---
# <a name="variable-variablename-hides-a-variable-in-an-enclosing-block"></a><span data-ttu-id="1206d-102">Değişken '\<variablename >' kapsayan bir blok içinde bir değişken gizliyor</span><span class="sxs-lookup"><span data-stu-id="1206d-102">Variable '\<variablename>' hides a variable in an enclosing block</span></span>
<span data-ttu-id="1206d-103">İçine bir blokta bir değişkeni başka bir yerel değişken aynı ada sahip.</span><span class="sxs-lookup"><span data-stu-id="1206d-103">A variable enclosed in a block has the same name as another local variable.</span></span>  
  
 <span data-ttu-id="1206d-104">**Hata Kimliği:** BC30616</span><span class="sxs-lookup"><span data-stu-id="1206d-104">**Error ID:** BC30616</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1206d-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="1206d-105">To correct this error</span></span>  
  
-   <span data-ttu-id="1206d-106">Böylece, aynı diğer herhangi bir yerel değişkenler değil kapalı bloktaki değişkeni yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="1206d-106">Rename the variable in the enclosed block so that it is not the same as any other local variables.</span></span> <span data-ttu-id="1206d-107">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="1206d-107">For example:</span></span>  
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
-   <span data-ttu-id="1206d-108">Bu hatanın yaygın bir nedeni kullanımıdır `Catch e As Exception` içinde bir olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="1206d-108">A common cause for this error is the use of `Catch e As Exception` inside an event handler.</span></span> <span data-ttu-id="1206d-109">Bu durumda, ad `Catch` bloğu değişkeni `ex` yerine `e`.</span><span class="sxs-lookup"><span data-stu-id="1206d-109">If this is the case, name the `Catch` block variable `ex` rather than `e`.</span></span>  
  
-   <span data-ttu-id="1206d-110">Bu hatanın başka bir ortak kaynak içinde bildirilen yerel değişken erişme denemesi, bir `Try` ayrı bir engelleme `Catch` blok.</span><span class="sxs-lookup"><span data-stu-id="1206d-110">Another common source of this error is an attempt to access a local variable declared within a `Try` block in a separate `Catch` block.</span></span> <span data-ttu-id="1206d-111">Bunu düzeltmek için değişken dışında bildirmek `Try...Catch...Finally` yapısı.</span><span class="sxs-lookup"><span data-stu-id="1206d-111">To correct this, declare the variable outside the `Try...Catch...Finally` structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1206d-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1206d-112">See also</span></span>

- [<span data-ttu-id="1206d-113">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="1206d-113">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="1206d-114">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="1206d-114">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
