---
title: Örtük olarak yazılan lambda ifadeleri
description: Bir lambda ifadesi bildirmek için neden örtük olarak yazılmış bir değişken bildirimi kullanamadığınızı öğrenin.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: cf16bb4d9ed27f536ae163284f36a0f305877139
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713882"
---
# <a name="implicitly-typed-lambda-expressions"></a><span data-ttu-id="379fd-103">Örtük olarak yazılan lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="379fd-103">Implicitly typed lambda expressions</span></span>

<span data-ttu-id="379fd-104">Bir lambda ifadesi bildirmek için örtük olarak yazılmış bir değişken bildirimi kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="379fd-104">You can't use an implicitly typed variable declaration to declare a lambda expression.</span></span>
<span data-ttu-id="379fd-105">Derleyici için bir dairesel mantık sorunu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="379fd-105">It creates a circular logic problem for the compiler.</span></span> <span data-ttu-id="379fd-106">`var` bildirimi, derleyiciye atama işlecinin sağ tarafındaki ifadenin türünden değişkenin türünü eklemesini söyler.</span><span class="sxs-lookup"><span data-stu-id="379fd-106">The `var` declaration tells the compiler to figure out the type of the variable from the type of expression on the right hand side of the assignment operator.</span></span> <span data-ttu-id="379fd-107">Lambda ifadesinin derleme zamanı türü yoktur, ancak eşleşen herhangi bir temsilciye veya ifade türüne dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="379fd-107">A lambda expression does not have a compile time type, but is convertible to any matching delegate or expression type.</span></span> <span data-ttu-id="379fd-108">Bir temsilci veya ifade türü değişkenine bir lambda ifadesi atadığınızda, derleyiciye lambda ifadesini ' atandı ' değişkeninin imzasıyla eşleşen bir ifadeye veya temsilciye dönüştürmenize söylemiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="379fd-108">When you assign a lambda expression to a variable of a delegate or expression type, you tell the compiler to try and convert the lambda expression into an expression or delegate that matches the signature of the 'assigned to' variable.</span></span> <span data-ttu-id="379fd-109">Derleyicinin, atamanın sağ tarafındaki her şeyi atamanın sol tarafındaki türle eşleştirmek için deneme yapması gerekir.</span><span class="sxs-lookup"><span data-stu-id="379fd-109">The compiler must try to make the thing on the right hand side of the assignment match the type on the left hand side of the assignment.</span></span> 

<span data-ttu-id="379fd-110">Atamanın her iki tarafı da derleyiciye atama işlecinin diğer tarafındaki nesneye bakmasını ve bu türden eşleşip eşleşmediğini görmenizi söyleyemiyorum.</span><span class="sxs-lookup"><span data-stu-id="379fd-110">Both sides of the assignment can't be telling the compiler to look at the object on the other side of the assignment operator and see if my type matches.</span></span>

<span data-ttu-id="379fd-111">C# [Bu makaleyi](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) okuyarak dilin neden bu davranışı belirtmekle ilgili daha fazla ayrıntı alabilirsiniz (PDF indirme).</span><span class="sxs-lookup"><span data-stu-id="379fd-111">You can get even more details on why the C# language specifies that behavior by reading [this article](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (PDF download).</span></span>
