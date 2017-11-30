---
title: "Nesne değişkeni veya With bloğu değişkeni ayarlanmamış"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9e1f587e194acf744b6ec9b8f1bede3acef7b753
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="object-variable-or-with-block-variable-not-set"></a><span data-ttu-id="f69d7-102">Nesne değişkeni veya With bloğu değişkeni ayarlanmamış</span><span class="sxs-lookup"><span data-stu-id="f69d7-102">Object variable or With block variable not set</span></span>
<span data-ttu-id="f69d7-103">Geçersiz nesne değişkeni başvuruluyor.</span><span class="sxs-lookup"><span data-stu-id="f69d7-103">An invalid object variable is being referenced.</span></span>   <span data-ttu-id="f69d7-104">Bu hata, çeşitli nedenlerle oluşabilir:</span><span class="sxs-lookup"><span data-stu-id="f69d7-104">This error can occur for several reasons:</span></span>  
  
-   <span data-ttu-id="f69d7-105">Bir değişken türü belirtmeden bildirildi.</span><span class="sxs-lookup"><span data-stu-id="f69d7-105">A variable was declared without specifying a type.</span></span> <span data-ttu-id="f69d7-106">Bir değişken türü belirtmeden bildirilirse türü için varsayılan `Object`.</span><span class="sxs-lookup"><span data-stu-id="f69d7-106">If a variable is declared without specifying a type, it defaults to type `Object`.</span></span>  
  
     <span data-ttu-id="f69d7-107">Örneğin, ile bildirilen bir değişken `Dim x` türü olacaktır `Object;` ile bildirilen bir değişken `Dim x As String` türü olacaktır `String`.</span><span class="sxs-lookup"><span data-stu-id="f69d7-107">For example, a variable declared with `Dim x` would be of type `Object;` a variable declared with `Dim x As String` would be of type `String`.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="f69d7-108">`Option Strict` Deyimi izin vermez sonuçlanır örtük yazarak bir `Object` türü.</span><span class="sxs-lookup"><span data-stu-id="f69d7-108">The `Option Strict` statement disallows implicit typing that results in an `Object` type.</span></span> <span data-ttu-id="f69d7-109">Türü atlarsanız, derleme zamanı hatası meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="f69d7-109">If you omit the type, a compile-time error will occur.</span></span> <span data-ttu-id="f69d7-110">Bkz: [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f69d7-110">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
-   <span data-ttu-id="f69d7-111">Ayarlanmış bir nesneye başvurmak çalışıyorsunuz`Nothing`</span><span class="sxs-lookup"><span data-stu-id="f69d7-111">You are attempting to reference an object that has been set to `Nothing`</span></span>  
  
     <span data-ttu-id="f69d7-112">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="f69d7-112">.</span></span>  
  
-   <span data-ttu-id="f69d7-113">Bir öğe düzgün bildirilen değildi bir dizi değişkeni erişmeye çalışıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="f69d7-113">You are attempting to access an element of an array variable that wasn't properly declared.</span></span>  
  
     <span data-ttu-id="f69d7-114">Örneğin, bir dizi olarak bildirilen `products() As String` dizinin bir öğeye başvuru denerseniz hata tetikleyecek `products(3) = "Widget"`.</span><span class="sxs-lookup"><span data-stu-id="f69d7-114">For example, an array declared as `products() As String` will trigger the error if you try to reference an element of the array `products(3) = "Widget"`.</span></span> <span data-ttu-id="f69d7-115">Dizi öğe var ve bir nesne olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="f69d7-115">The array has no elements and is treated as an object.</span></span>  
  
-   <span data-ttu-id="f69d7-116">Erişim kodu içinde çalıştığınız bir `With...End With` blok başlatıldı önce engeller.</span><span class="sxs-lookup"><span data-stu-id="f69d7-116">You are attempting to access code within a `With...End With` block before the block has been initialized.</span></span>   <span data-ttu-id="f69d7-117">A `With...End With` blok yürüterek başlatılmalı `With` deyimi giriş noktası.</span><span class="sxs-lookup"><span data-stu-id="f69d7-117">A `With...End With` block must be initialized by executing the `With` statement entry point.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f69d7-118">Visual Basic veya VBA önceki sürümlerinde bu hata ayrıca kullanmadan bir değişkene bir değer atayarak tetiklendi `Set` anahtar sözcüğü (`x = "name"` yerine `Set x = "name"`).</span><span class="sxs-lookup"><span data-stu-id="f69d7-118">In earlier versions of Visual Basic or VBA this error was also triggered by assigning a value to a variable without using the `Set` keyword (`x = "name"` instead of `Set x = "name"`).</span></span> <span data-ttu-id="f69d7-119">`Set` Anahtar sözcüğü artık Visual Basic .net içinde geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="f69d7-119">The `Set` keyword is no longer valid in Visual Basic .Net.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f69d7-120">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="f69d7-120">To correct this error</span></span>  
  
1.  <span data-ttu-id="f69d7-121">Ayarlama `Option Strict` için `On` dosyanın başına aşağıdaki kodu ekleyerek:</span><span class="sxs-lookup"><span data-stu-id="f69d7-121">Set `Option Strict` to `On` by adding the following code to the beginning of the file:</span></span>  
  
```vb  
Option Strict On  
```  

     When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.  
  
2.  <span data-ttu-id="f69d7-122">Etkinleştirmek istemiyorsanız, `Option Strict`, kodunuzu olmadan türü belirtilmiş herhangi bir değişkeni için arama (`Dim x` yerine `Dim x As String`) ve amaçlanan türü bildirimini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f69d7-122">If you don't want to enable `Option Strict`, search your code for any variables that were specified without a type (`Dim x` instead of `Dim x As String`) and add the intended type to the declaration.</span></span>  
  
3.  <span data-ttu-id="f69d7-123">Ayarlanmış olan bir nesne değişkeni için başvuran olmayan emin `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="f69d7-123">Make sure you aren't referring to  an object variable that has been set to `Nothing`.</span></span>  <span data-ttu-id="f69d7-124">Kodunuz için anahtar sözcüğü arama `Nothing`ve nesne ayarlanmamış kodunuzu düzeltmeniz `Nothing` sonra gösterdiğiniz kadar.</span><span class="sxs-lookup"><span data-stu-id="f69d7-124">Search your code for the keyword `Nothing`, and revise your code so that the object isn't set to `Nothing` until after you have referenced it.</span></span>  
  
4.  <span data-ttu-id="f69d7-125">Bunlara erişim önce herhangi bir dizi değişkeni dimensioned emin olun.</span><span class="sxs-lookup"><span data-stu-id="f69d7-125">Make sure that any array  variables are dimensioned before you access them.</span></span> <span data-ttu-id="f69d7-126">Dizinin ilk oluşturduğunuzda, bir boyut ya da atayabilirsiniz (`Dim x(5) As String` yerine `Dim x() As String`), veya `ReDim` ilk erişebilmesi dizi boyutları ayarlamak için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="f69d7-126">You can either assign a dimension when you first create the array (`Dim x(5) As String` instead of `Dim x() As String`), or use the `ReDim` keyword to set the dimensions of the array before you first access it.</span></span>  
  
5.  <span data-ttu-id="f69d7-127">Emin olun, `With` blok yürüterek başlatılır `With` deyimi giriş noktası.</span><span class="sxs-lookup"><span data-stu-id="f69d7-127">Make sure your `With` block is initialized by executing the `With` statement entry point.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f69d7-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f69d7-128">See Also</span></span>  
 [<span data-ttu-id="f69d7-129">Nesne değişken bildirimi</span><span class="sxs-lookup"><span data-stu-id="f69d7-129">Object Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="f69d7-130">ReDim deyimi</span><span class="sxs-lookup"><span data-stu-id="f69d7-130">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="f69d7-131">İle... End With deyimi</span><span class="sxs-lookup"><span data-stu-id="f69d7-131">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
