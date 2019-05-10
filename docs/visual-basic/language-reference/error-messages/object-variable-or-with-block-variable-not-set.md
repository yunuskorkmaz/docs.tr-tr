---
title: Nesne değişkeni veya With bloğu değişkeni ayarlanmamış
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: 766b95163f164ec76135b964115069b6855ceebf
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64750681"
---
# <a name="object-variable-or-with-block-variable-not-set"></a><span data-ttu-id="73eae-102">Nesne değişkeni veya With bloğu değişkeni ayarlanmamış</span><span class="sxs-lookup"><span data-stu-id="73eae-102">Object variable or With block variable not set</span></span>
<span data-ttu-id="73eae-103">Geçersiz nesne değişkeni başvuruda bulunuyor.</span><span class="sxs-lookup"><span data-stu-id="73eae-103">An invalid object variable is being referenced.</span></span>   <span data-ttu-id="73eae-104">Bu hata, çeşitli nedenlerle oluşabilir:</span><span class="sxs-lookup"><span data-stu-id="73eae-104">This error can occur for several reasons:</span></span>

- <span data-ttu-id="73eae-105">Bir tür belirtmeden bir değişken bildirildi.</span><span class="sxs-lookup"><span data-stu-id="73eae-105">A variable was declared without specifying a type.</span></span> <span data-ttu-id="73eae-106">Bir tür belirtmeden bildirilen bir değişken, yazmak için varsayılanları `Object`.</span><span class="sxs-lookup"><span data-stu-id="73eae-106">If a variable is declared without specifying a type, it defaults to type `Object`.</span></span>

    <span data-ttu-id="73eae-107">Örneğin, bildirilen bir değişken `Dim x` türünde olur `Object;` ile bildirilen bir değişken `Dim x As String` türünde olur `String`.</span><span class="sxs-lookup"><span data-stu-id="73eae-107">For example, a variable declared with `Dim x` would be of type `Object;` a variable declared with `Dim x As String` would be of type `String`.</span></span>

    > [!TIP]
    >  <span data-ttu-id="73eae-108">`Option Strict` Deyimi izin vermiyor sonuçlanır örtülü yazma bir `Object` türü.</span><span class="sxs-lookup"><span data-stu-id="73eae-108">The `Option Strict` statement disallows implicit typing that results in an `Object` type.</span></span> <span data-ttu-id="73eae-109">Türü atlarsanız, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="73eae-109">If you omit the type, a compile-time error will occur.</span></span> <span data-ttu-id="73eae-110">Bkz: [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="73eae-110">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>

- <span data-ttu-id="73eae-111">Olarak ayarlanan bir nesne başvurmayı denediğiniz `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="73eae-111">You are attempting to reference an object that has been set to `Nothing`.</span></span>

- <span data-ttu-id="73eae-112">Doğru değildi bildirilen bir dizi değişkenini öğesi erişmeye çalışıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="73eae-112">You are attempting to access an element of an array variable that wasn't properly declared.</span></span>

    <span data-ttu-id="73eae-113">Örneğin, bir dizi olarak bildirilen `products() As String` dizinin bir öğesine başvurmak denerseniz hata tetikleyecek `products(3) = "Widget"`.</span><span class="sxs-lookup"><span data-stu-id="73eae-113">For example, an array declared as `products() As String` will trigger the error if you try to reference an element of the array `products(3) = "Widget"`.</span></span> <span data-ttu-id="73eae-114">Dizinin öğe yok ve bir nesne olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="73eae-114">The array has no elements and is treated as an object.</span></span>

- <span data-ttu-id="73eae-115">Erişim kodu içinde çalıştığınız bir `With...End With` blok başlatılmadan önce engelleyin.</span><span class="sxs-lookup"><span data-stu-id="73eae-115">You are attempting to access code within a `With...End With` block before the block has been initialized.</span></span>   <span data-ttu-id="73eae-116">A `With...End With` blok yürüterek başlatılmalı `With` deyimi giriş noktası.</span><span class="sxs-lookup"><span data-stu-id="73eae-116">A `With...End With` block must be initialized by executing the `With` statement entry point.</span></span>

> [!NOTE]
> <span data-ttu-id="73eae-117">Visual Basic veya VBA önceki sürümlerinde bu hata ayrıca kullanmadan bir değeri bir değişkene atayarak tetiklendi `Set` anahtar sözcüğü (`x = "name"` yerine `Set x = "name"`).</span><span class="sxs-lookup"><span data-stu-id="73eae-117">In earlier versions of Visual Basic or VBA this error was also triggered by assigning a value to a variable without using the `Set` keyword (`x = "name"` instead of `Set x = "name"`).</span></span> <span data-ttu-id="73eae-118">`Set` Anahtar sözcüğü artık Visual Basic. NET'te geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="73eae-118">The `Set` keyword is no longer valid in Visual Basic .Net.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="73eae-119">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="73eae-119">To correct this error</span></span>

1. <span data-ttu-id="73eae-120">Ayarlama `Option Strict` için `On` dosyasının başına aşağıdaki kodu ekleyerek:</span><span class="sxs-lookup"><span data-stu-id="73eae-120">Set `Option Strict` to `On` by adding the following code to the beginning of the file:</span></span>

    ```vb
    Option Strict On
    ```

    <span data-ttu-id="73eae-121">Projeyi çalıştırdığınızda, bir derleyici hatası görünür **hata listesi** olmadan bir türü belirtilmiş herhangi bir değişken için.</span><span class="sxs-lookup"><span data-stu-id="73eae-121">When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.</span></span>

2. <span data-ttu-id="73eae-122">Etkinleştirmek istemiyorsanız `Option Strict`, olmadan bir türü belirtilmiş tüm değişkenler için kodunuzu arama (`Dim x` yerine `Dim x As String`) ve amaçlanan türü bildirimini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="73eae-122">If you don't want to enable `Option Strict`, search your code for any variables that were specified without a type (`Dim x` instead of `Dim x As String`) and add the intended type to the declaration.</span></span>

3. <span data-ttu-id="73eae-123">Olarak ayarlanan bir nesne değişkenine başvuran olmayan emin `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="73eae-123">Make sure you aren't referring to  an object variable that has been set to `Nothing`.</span></span>  <span data-ttu-id="73eae-124">Kodunuz için bir anahtar sözcük arama `Nothing`ve böylece nesnenin belirlendiğinden, kodunuzu gözden geçirme `Nothing` sonra başvurduğunuz kadar.</span><span class="sxs-lookup"><span data-stu-id="73eae-124">Search your code for the keyword `Nothing`, and revise your code so that the object isn't set to `Nothing` until after you have referenced it.</span></span>

4. <span data-ttu-id="73eae-125">Bunları erişmeden önce herhangi bir dizi değişkeni dimensioned emin olun.</span><span class="sxs-lookup"><span data-stu-id="73eae-125">Make sure that any array  variables are dimensioned before you access them.</span></span> <span data-ttu-id="73eae-126">Dizinin ilk oluşturduğunuzda, bir boyut ya da atayabilirsiniz (`Dim x(5) As String` yerine `Dim x() As String`), veya `ReDim` ilk erişmeden önce dizinin boyut sayısını ayarlamak için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="73eae-126">You can either assign a dimension when you first create the array (`Dim x(5) As String` instead of `Dim x() As String`), or use the `ReDim` keyword to set the dimensions of the array before you first access it.</span></span>

5. <span data-ttu-id="73eae-127">Emin olun, `With` blok yürüterek başlatılan `With` deyimi giriş noktası.</span><span class="sxs-lookup"><span data-stu-id="73eae-127">Make sure your `With` block is initialized by executing the `With` statement entry point.</span></span>

## <a name="see-also"></a><span data-ttu-id="73eae-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73eae-128">See also</span></span>

- [<span data-ttu-id="73eae-129">Nesne Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="73eae-129">Object Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="73eae-130">ReDim Deyimi</span><span class="sxs-lookup"><span data-stu-id="73eae-130">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="73eae-131">With...End With Deyimi</span><span class="sxs-lookup"><span data-stu-id="73eae-131">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
