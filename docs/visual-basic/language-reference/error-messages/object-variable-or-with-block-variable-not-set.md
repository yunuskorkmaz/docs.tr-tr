---
title: Nesne değişkeni veya With bloğu değişkeni ayarlanmamış
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: 07c215d373e4ac1cbadf82a48b8cb3d90efdbdb4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040554"
---
# <a name="object-variable-or-with-block-variable-not-set"></a><span data-ttu-id="2efd2-102">Nesne değişkeni veya With bloğu değişkeni ayarlanmamış</span><span class="sxs-lookup"><span data-stu-id="2efd2-102">Object variable or With block variable not set</span></span>
<span data-ttu-id="2efd2-103">Geçersiz bir nesne değişkenine başvuruluyor.</span><span class="sxs-lookup"><span data-stu-id="2efd2-103">An invalid object variable is being referenced.</span></span>   <span data-ttu-id="2efd2-104">Bu hata, birkaç nedenden dolayı oluşabilir:</span><span class="sxs-lookup"><span data-stu-id="2efd2-104">This error can occur for several reasons:</span></span>

- <span data-ttu-id="2efd2-105">Bir değişken, bir tür belirtilmeden bildirildi.</span><span class="sxs-lookup"><span data-stu-id="2efd2-105">A variable was declared without specifying a type.</span></span> <span data-ttu-id="2efd2-106">Bir değişken bir tür belirtilmeden bildirilirse, varsayılan olarak yazın `Object`.</span><span class="sxs-lookup"><span data-stu-id="2efd2-106">If a variable is declared without specifying a type, it defaults to type `Object`.</span></span>

    <span data-ttu-id="2efd2-107">Örneğin `Dim x` , ile `Object;` tanımlanan bir değişken, `String`ile `Dim x As String` tanımlanan bir değişken türünde olacaktır.</span><span class="sxs-lookup"><span data-stu-id="2efd2-107">For example, a variable declared with `Dim x` would be of type `Object;` a variable declared with `Dim x As String` would be of type `String`.</span></span>

    > [!TIP]
    > <span data-ttu-id="2efd2-108">İfade `Option Strict` , bir `Object` tür ile sonuçlanan örtük yazmaya izin vermez.</span><span class="sxs-lookup"><span data-stu-id="2efd2-108">The `Option Strict` statement disallows implicit typing that results in an `Object` type.</span></span> <span data-ttu-id="2efd2-109">Türü atlarsanız, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="2efd2-109">If you omit the type, a compile-time error will occur.</span></span> <span data-ttu-id="2efd2-110">Bkz. [Option Strict deyimdir](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2efd2-110">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>

- <span data-ttu-id="2efd2-111">Olarak `Nothing`ayarlanmış bir nesneye başvurmaya çalışıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="2efd2-111">You are attempting to reference an object that has been set to `Nothing`.</span></span>

- <span data-ttu-id="2efd2-112">Düzgün şekilde bildirilmeyen bir dizi değişkeninin öğesine erişmeye çalışıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="2efd2-112">You are attempting to access an element of an array variable that wasn't properly declared.</span></span>

    <span data-ttu-id="2efd2-113">Örneğin, dizi `products(3) = "Widget"`öğesine başvuru yapmayı denerseniz `products() As String` , olarak tanımlanan bir dizi hatayı tetikler.</span><span class="sxs-lookup"><span data-stu-id="2efd2-113">For example, an array declared as `products() As String` will trigger the error if you try to reference an element of the array `products(3) = "Widget"`.</span></span> <span data-ttu-id="2efd2-114">Dizide hiç öğe yok ve bir nesne olarak değerlendirildi.</span><span class="sxs-lookup"><span data-stu-id="2efd2-114">The array has no elements and is treated as an object.</span></span>

- <span data-ttu-id="2efd2-115">Blok başlatılmadan önce bir `With...End With` blok içindeki koda erişmeye çalışıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="2efd2-115">You are attempting to access code within a `With...End With` block before the block has been initialized.</span></span>   <span data-ttu-id="2efd2-116">Bir `With...End With` blok, `With` ifade giriş noktası yürütülerek başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2efd2-116">A `With...End With` block must be initialized by executing the `With` statement entry point.</span></span>

> [!NOTE]
> <span data-ttu-id="2efd2-117">Visual Basic veya VBA 'nın önceki sürümlerinde bu hata, `Set` anahtar sözcüğü kullanılmadan bir değişkene bir değer atanarak da tetikleniyor (`x = "name"` yerine `Set x = "name"`).</span><span class="sxs-lookup"><span data-stu-id="2efd2-117">In earlier versions of Visual Basic or VBA this error was also triggered by assigning a value to a variable without using the `Set` keyword (`x = "name"` instead of `Set x = "name"`).</span></span> <span data-ttu-id="2efd2-118">`Set` Anahtar sözcüğü artık Visual Basic .NET içinde geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="2efd2-118">The `Set` keyword is no longer valid in Visual Basic .Net.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="2efd2-119">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="2efd2-119">To correct this error</span></span>

1. <span data-ttu-id="2efd2-120">Aşağıdaki `Option Strict` kodu `On` dosyanın başlangıcına ekleyerek olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="2efd2-120">Set `Option Strict` to `On` by adding the following code to the beginning of the file:</span></span>

    ```vb
    Option Strict On
    ```

    <span data-ttu-id="2efd2-121">Projeyi çalıştırdığınızda, bir tür olmadan belirtilen herhangi bir değişken için **hata listesi** bir derleyici hatası görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="2efd2-121">When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.</span></span>

2. <span data-ttu-id="2efd2-122">Etkinleştirmek `Option Strict`istemiyorsanız, kodunuzda bir tür olmadan belirtilen herhangi bir değişken (`Dim x` yerine `Dim x As String`) arayın ve hedeflenen türü bildirime ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2efd2-122">If you don't want to enable `Option Strict`, search your code for any variables that were specified without a type (`Dim x` instead of `Dim x As String`) and add the intended type to the declaration.</span></span>

3. <span data-ttu-id="2efd2-123">Olarak `Nothing`ayarlanmış bir nesne değişkenine başvurmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="2efd2-123">Make sure you aren't referring to  an object variable that has been set to `Nothing`.</span></span>  <span data-ttu-id="2efd2-124">Anahtar sözcüğü `Nothing`için kodunuzda arama yapın ve bu nesnenin, başvurulduktan sonra olarak ayarlanmaması için `Nothing` kodunuzu düzeltin.</span><span class="sxs-lookup"><span data-stu-id="2efd2-124">Search your code for the keyword `Nothing`, and revise your code so that the object isn't set to `Nothing` until after you have referenced it.</span></span>

4. <span data-ttu-id="2efd2-125">Herhangi bir dizi değişkeninin, erişmeden önce boyutlanır olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="2efd2-125">Make sure that any array  variables are dimensioned before you access them.</span></span> <span data-ttu-id="2efd2-126">İlk olarak diziyi oluştururken bir boyut atayabilir (`Dim x(5) As String` `Dim x() As String`yerine `ReDim` ) veya ilk kez erişmeden önce dizinin boyutlarını ayarlamak için anahtar sözcüğünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2efd2-126">You can either assign a dimension when you first create the array (`Dim x(5) As String` instead of `Dim x() As String`), or use the `ReDim` keyword to set the dimensions of the array before you first access it.</span></span>

5. <span data-ttu-id="2efd2-127">`With` Deyiminizin `With` giriş noktasını yürüterek blobunun başlatıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="2efd2-127">Make sure your `With` block is initialized by executing the `With` statement entry point.</span></span>

## <a name="see-also"></a><span data-ttu-id="2efd2-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2efd2-128">See also</span></span>

- [<span data-ttu-id="2efd2-129">Nesne Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="2efd2-129">Object Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="2efd2-130">ReDim Deyimi</span><span class="sxs-lookup"><span data-stu-id="2efd2-130">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="2efd2-131">With...End With Deyimi</span><span class="sxs-lookup"><span data-stu-id="2efd2-131">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
