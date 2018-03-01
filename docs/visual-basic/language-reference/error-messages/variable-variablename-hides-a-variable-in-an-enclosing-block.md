---
title: "Değişken &#39; &lt;variablename&gt;&#39; kapsayan bir bloktaki bir değişken gizler"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2af570cd002b4be4e15a7c03b0ffc2ff84ba3982
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="variable-39ltvariablenamegt39-hides-a-variable-in-an-enclosing-block"></a><span data-ttu-id="6534b-102">Değişken &#39; &lt;variablename&gt;&#39; kapsayan bir bloktaki bir değişken gizler</span><span class="sxs-lookup"><span data-stu-id="6534b-102">Variable &#39;&lt;variablename&gt;&#39; hides a variable in an enclosing block</span></span>
<span data-ttu-id="6534b-103">Bir blok içine bir değişken başka bir yerel değişken aynı ada sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6534b-103">A variable enclosed in a block has the same name as another local variable.</span></span>  
  
 <span data-ttu-id="6534b-104">**Hata Kimliği:** BC30616</span><span class="sxs-lookup"><span data-stu-id="6534b-104">**Error ID:** BC30616</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6534b-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="6534b-105">To correct this error</span></span>  
  
-   <span data-ttu-id="6534b-106">Böylece, aynı herhangi bir yerel değişkenler değil kapalı bloğundaki değişken yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="6534b-106">Rename the variable in the enclosed block so that it is not the same as any other local variables.</span></span> <span data-ttu-id="6534b-107">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="6534b-107">For example:</span></span>  
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
-   <span data-ttu-id="6534b-108">Bu hatanın sık karşılaşılan bir nedeni kullanımıdır `Catch e As Exception` olay işleyici içinde.</span><span class="sxs-lookup"><span data-stu-id="6534b-108">A common cause for this error is the use of `Catch e As Exception` inside an event handler.</span></span> <span data-ttu-id="6534b-109">Bu durumda, ad `Catch` bloğu değişkeni `ex` yerine `e`.</span><span class="sxs-lookup"><span data-stu-id="6534b-109">If this is the case, name the `Catch` block variable `ex` rather than `e`.</span></span>  
  
-   <span data-ttu-id="6534b-110">Bu hatanın ortak başka bir kaynak içinde bildirilen yerel bir değişkene erişme girişimi olan bir `Try` ayrı bir engelleme `Catch` bloğu.</span><span class="sxs-lookup"><span data-stu-id="6534b-110">Another common source of this error is an attempt to access a local variable declared within a `Try` block in a separate `Catch` block.</span></span> <span data-ttu-id="6534b-111">Bu sorunu gidermek için dışında değişkeni bildirme `Try...Catch...Finally` yapısı.</span><span class="sxs-lookup"><span data-stu-id="6534b-111">To correct this, declare the variable outside the `Try...Catch...Finally` structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6534b-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6534b-112">See Also</span></span>  
 [<span data-ttu-id="6534b-113">Try... Catch... Finally ifadesi</span><span class="sxs-lookup"><span data-stu-id="6534b-113">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="6534b-114">Değişken bildirimi</span><span class="sxs-lookup"><span data-stu-id="6534b-114">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
