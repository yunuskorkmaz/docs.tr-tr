---
title: Türü örtük olarak belirlenmiş lambda ifadeleri
description: Türü örtük olarak belirlenmiş bir değişken bildirimi bir lambda ifadesi bildirmek için neden kullanamazsınız öğrenin.
ms.date: 06/20/2016
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: 9b798f40676afaad2075806d6dc512f279bc7065
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58126103"
---
# <a name="implicitly-typed-lambda-expressions"></a><span data-ttu-id="1dde4-103">Türü örtük olarak belirlenmiş lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="1dde4-103">Implicitly typed lambda expressions</span></span>

<span data-ttu-id="1dde4-104">Türü örtük olarak belirlenmiş bir değişken bildirimi bir lambda ifadesi bildirmek için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="1dde4-104">You can't use an implicitly typed variable declaration to declare a lambda expression.</span></span>
<span data-ttu-id="1dde4-105">Derleyici için döngüsel mantıksal sorun oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1dde4-105">It creates a circular logic problem for the compiler.</span></span> <span data-ttu-id="1dde4-106">`var` Bildirimi atama işlecinin sağ tarafı ifadesinin türünden değişkeninin türü ekleyeceğimi derleyiciye bildirir.</span><span class="sxs-lookup"><span data-stu-id="1dde4-106">The `var` declaration tells the compiler to figure out the type of the variable from the type of expression on the right hand side of the assignment operator.</span></span> <span data-ttu-id="1dde4-107">Bir lambda ifadesi, bir derleme zamanı tür yok, ancak eşleşen bir temsilci veya ifade türüne dönüştürülemez.</span><span class="sxs-lookup"><span data-stu-id="1dde4-107">A lambda expression does not have a compile time type, but is convertible to any matching delegate or expression type.</span></span> <span data-ttu-id="1dde4-108">Bir lambda ifadesi bir temsilci veya ifade türünde bir değişkene atadığınızda, deneyin ve lambda ifadesindeki bir ifade veya 'atanan' değişkeninin imzayla eşleşen temsilci dönüştürmek için derleyicinin söyleyin.</span><span class="sxs-lookup"><span data-stu-id="1dde4-108">When you assign a lambda expression to a variable of a delegate or expression type, you tell the compiler to try and convert the lambda expression into an expression or delegate that matches the signature of the 'assigned to' variable.</span></span> <span data-ttu-id="1dde4-109">Derleyici, sağ tarafta atama eşleşmenin atama türünü sol tarafında bir şey yapmak denemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1dde4-109">The compiler must try to make the thing on the right hand side of the assignment match the type on the left hand side of the assignment.</span></span> 

<span data-ttu-id="1dde4-110">Her iki tarafında atama derleyicinin nesne atama işlecinin diğer tarafında bakın ve türüm eşleşip eşleşmediğini belirten olamaz.</span><span class="sxs-lookup"><span data-stu-id="1dde4-110">Both sides of the assignment can't be telling the compiler to look at the object on the other side of the assignment operator and see if my type matches.</span></span>

<span data-ttu-id="1dde4-111">Neden bu davranışı belirtir okuyarak C# dili hakkında daha fazla ayrıntıya ulaşabilirsiniz [bu makalede](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (PDF olarak indirin)</span><span class="sxs-lookup"><span data-stu-id="1dde4-111">You can get even more details on why the C# language specifies that behavior by reading [this article](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (PDF Download)</span></span>
