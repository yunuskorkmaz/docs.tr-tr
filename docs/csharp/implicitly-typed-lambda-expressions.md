---
title: "Türü örtük olarak belirlenmiş lambda ifadeleri"
description: "Lambda ifadesi bildirmek için örtük olarak yazılan bir değişken bildirimi neden kullanamazsınız öğrenin."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: 663613af001f9727c48bd48553540305e47a6bab
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="implicitly-typed-lambda-expressions"></a><span data-ttu-id="85a5b-104">Türü örtük olarak belirlenmiş lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="85a5b-104">Implicitly typed lambda expressions</span></span>

<span data-ttu-id="85a5b-105">Değil kullanıyorum `var` Bu ifade ağacına bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="85a5b-105">I'm not using `var` to declare this expression tree.</span></span> <span data-ttu-id="85a5b-106">Türü örtük olarak belirlenmiş bir değişken bildirimi lambda ifadesi bildirmek için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="85a5b-106">You can't use an implicitly typed variable declaration to declare a lambda expression.</span></span>
<span data-ttu-id="85a5b-107">Derleyici için döngüsel mantığı sorun oluşturur.</span><span class="sxs-lookup"><span data-stu-id="85a5b-107">It creates a circular logic problem for the compiler.</span></span> <span data-ttu-id="85a5b-108">`var` Bildirimi atama işlecinin sağ tarafında ifadenin türünden değişkeninin türü ekleneceğini derleyici söyler.</span><span class="sxs-lookup"><span data-stu-id="85a5b-108">The `var` declaration tells the compiler to figure out the type of the variable from the type of expression on the right hand side of the assignment operator.</span></span> <span data-ttu-id="85a5b-109">Lambda ifadesi bir derleme zamanı türüne sahip değil, ancak hiçbir eşleşen temsilci ya da ifade türüne dönüştürülemez.</span><span class="sxs-lookup"><span data-stu-id="85a5b-109">A lambda expression does not have a compile time type, but is convertible to any matching delegate or expression type.</span></span> <span data-ttu-id="85a5b-110">Lambda ifadesi bir temsilci ya da ifade türü bir değişkene atadığınızda, deneyin ve lambda ifadesi bir deyim veya 'atanan' değişkeni imzası eşleşen temsilci dönüştürmek için derleyici söyleyin.</span><span class="sxs-lookup"><span data-stu-id="85a5b-110">When you assign a lambda expression to a variable of a delegate or expression type, you tell the compiler to try and convert the lambda expression into an expression or delegate that matches the signature of the 'assigned to' variable.</span></span> <span data-ttu-id="85a5b-111">Derleyici sağ tarafta atama eşleşme türünü sol taraftaki atama şey yapmaya gerekir.</span><span class="sxs-lookup"><span data-stu-id="85a5b-111">The compiler must try to make the thing on the right hand side of the assignment match the type on the left hand side of the assignment.</span></span> 

<span data-ttu-id="85a5b-112">Atama her iki tarafında derleyici atama işleci diğer tarafta nesneye bakabilir ve my türü eşleşip eşleşmediğini belirten olamaz.</span><span class="sxs-lookup"><span data-stu-id="85a5b-112">Both sides of the assignment can't be telling the compiler to look at the object on the other side of the assignment operator and see if my type matches.</span></span>

<span data-ttu-id="85a5b-113">Neden bu davranışı belirtir okuyarak C# dili hakkında daha fazla bilgi alabilirsiniz [bu makalede](http://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (PDF indirin)</span><span class="sxs-lookup"><span data-stu-id="85a5b-113">You can get even more details on why the C# language specifies that behavior by reading [this article](http://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (PDF Download)</span></span>


