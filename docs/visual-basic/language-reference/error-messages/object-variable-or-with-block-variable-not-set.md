---
description: 'Hakkında daha fazla bilgi edinin: nesne değişkeni veya with bloğu değişkeni ayarlanmamış'
title: Nesne değişkeni veya With bloğu değişkeni ayarlanmamış
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: a20655c2219aa5b90015e025a38ea9dd02894a6c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795579"
---
# <a name="object-variable-or-with-block-variable-not-set"></a><span data-ttu-id="5fc8f-103">Nesne değişkeni veya With bloğu değişkeni ayarlanmamış</span><span class="sxs-lookup"><span data-stu-id="5fc8f-103">Object variable or With block variable not set</span></span>

<span data-ttu-id="5fc8f-104">Geçersiz bir nesne değişkenine başvuruluyor.</span><span class="sxs-lookup"><span data-stu-id="5fc8f-104">An invalid object variable is being referenced.</span></span> <span data-ttu-id="5fc8f-105">Bu hata, birkaç nedenden dolayı oluşabilir:</span><span class="sxs-lookup"><span data-stu-id="5fc8f-105">This error can occur for several reasons:</span></span>

- <span data-ttu-id="5fc8f-106">Bir değişken, bir tür belirtilmeden bildirildi.</span><span class="sxs-lookup"><span data-stu-id="5fc8f-106">A variable was declared without specifying a type.</span></span> <span data-ttu-id="5fc8f-107">Bir değişken bir tür belirtilmeden bildirilirse, varsayılan olarak yazın `Object` .</span><span class="sxs-lookup"><span data-stu-id="5fc8f-107">If a variable is declared without specifying a type, it defaults to type `Object`.</span></span>

    <span data-ttu-id="5fc8f-108">Örneğin, ile tanımlanan bir değişken, `Dim x` `Object;` ile tanımlanan bir değişken türünde olacaktır `Dim x As String` `String` .</span><span class="sxs-lookup"><span data-stu-id="5fc8f-108">For example, a variable declared with `Dim x` would be of type `Object;` a variable declared with `Dim x As String` would be of type `String`.</span></span>

    > [!TIP]
    > <span data-ttu-id="5fc8f-109">`Option Strict`İfade, bir tür ile sonuçlanan örtük yazmaya izin vermez `Object` .</span><span class="sxs-lookup"><span data-stu-id="5fc8f-109">The `Option Strict` statement disallows implicit typing that results in an `Object` type.</span></span> <span data-ttu-id="5fc8f-110">Türü atlarsanız, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="5fc8f-110">If you omit the type, a compile-time error will occur.</span></span> <span data-ttu-id="5fc8f-111">Bkz. [Option Strict deyimdir](../statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5fc8f-111">See [Option Strict Statement](../statements/option-strict-statement.md).</span></span>

- <span data-ttu-id="5fc8f-112">Olarak ayarlanmış bir nesneye başvurmaya çalışıyorsunuz `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="5fc8f-112">You are attempting to reference an object that has been set to `Nothing`.</span></span>

- <span data-ttu-id="5fc8f-113">Düzgün şekilde bildirilmeyen bir dizi değişkeninin öğesine erişmeye çalışıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="5fc8f-113">You are attempting to access an element of an array variable that wasn't properly declared.</span></span>

    <span data-ttu-id="5fc8f-114">Örneğin, `products() As String` dizi öğesine başvuru yapmayı denerseniz, olarak tanımlanan bir dizi hatayı tetikler `products(3) = "Widget"` .</span><span class="sxs-lookup"><span data-stu-id="5fc8f-114">For example, an array declared as `products() As String` will trigger the error if you try to reference an element of the array `products(3) = "Widget"`.</span></span> <span data-ttu-id="5fc8f-115">Dizide hiç öğe yok ve bir nesne olarak değerlendirildi.</span><span class="sxs-lookup"><span data-stu-id="5fc8f-115">The array has no elements and is treated as an object.</span></span>

- <span data-ttu-id="5fc8f-116">Blok başlatılmadan önce bir blok içindeki koda erişmeye çalışıyorsunuz `With...End With` .</span><span class="sxs-lookup"><span data-stu-id="5fc8f-116">You are attempting to access code within a `With...End With` block before the block has been initialized.</span></span>   <span data-ttu-id="5fc8f-117">Bir `With...End With` blok, `With` ifade giriş noktası yürütülerek başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5fc8f-117">A `With...End With` block must be initialized by executing the `With` statement entry point.</span></span>

> [!NOTE]
> <span data-ttu-id="5fc8f-118">Visual Basic veya VBA 'nın önceki sürümlerinde bu hata, anahtar sözcüğü kullanılmadan bir değişkene bir değer atanarak da tetikleniyor `Set` ( `x = "name"` yerine `Set x = "name"` ).</span><span class="sxs-lookup"><span data-stu-id="5fc8f-118">In earlier versions of Visual Basic or VBA, this error was also triggered by assigning a value to a variable without using the `Set` keyword (`x = "name"` instead of `Set x = "name"`).</span></span> <span data-ttu-id="5fc8f-119">`Set`Anahtar sözcüğü artık Visual Basic .NET içinde geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="5fc8f-119">The `Set` keyword is no longer valid in Visual Basic .Net.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="5fc8f-120">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="5fc8f-120">To correct this error</span></span>

1. <span data-ttu-id="5fc8f-121">`Option Strict` `On` Aşağıdaki kodu dosyanın başlangıcına ekleyerek olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="5fc8f-121">Set `Option Strict` to `On` by adding the following code to the beginning of the file:</span></span>

    ```vb
    Option Strict On
    ```

    <span data-ttu-id="5fc8f-122">Projeyi çalıştırdığınızda, bir tür olmadan belirtilen herhangi bir değişken için **hata listesi** bir derleyici hatası görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5fc8f-122">When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.</span></span>

2. <span data-ttu-id="5fc8f-123">Etkinleştirmek istemiyorsanız `Option Strict` , kodunuzda bir tür olmadan belirtilen herhangi bir değişken ( `Dim x` yerine `Dim x As String` ) arayın ve hedeflenen türü bildirime ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5fc8f-123">If you don't want to enable `Option Strict`, search your code for any variables that were specified without a type (`Dim x` instead of `Dim x As String`) and add the intended type to the declaration.</span></span>

3. <span data-ttu-id="5fc8f-124">Olarak ayarlanmış bir nesne değişkenine başvurmadığından emin olun `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="5fc8f-124">Make sure you aren't referring to  an object variable that has been set to `Nothing`.</span></span>  <span data-ttu-id="5fc8f-125">Anahtar sözcüğü için kodunuzda arama `Nothing` yapın ve bu nesnenin, başvurulduktan sonra olarak ayarlanmaması için kodunuzu düzeltin `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="5fc8f-125">Search your code for the keyword `Nothing`, and revise your code so that the object isn't set to `Nothing` until after you have referenced it.</span></span>

4. <span data-ttu-id="5fc8f-126">Herhangi bir dizi değişkeninin, erişmeden önce boyutlanır olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="5fc8f-126">Make sure that any array  variables are dimensioned before you access them.</span></span> <span data-ttu-id="5fc8f-127">İlk olarak diziyi oluştururken bir boyut atayabilir ( `Dim x(5) As String` yerine `Dim x() As String` ) veya `ReDim` ilk kez erişmeden önce dizinin boyutlarını ayarlamak için anahtar sözcüğünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fc8f-127">You can either assign a dimension when you first create the array (`Dim x(5) As String` instead of `Dim x() As String`), or use the `ReDim` keyword to set the dimensions of the array before you first access it.</span></span>

5. <span data-ttu-id="5fc8f-128">`With`Deyiminizin giriş noktasını yürüterek blobunun başlatıldığından emin olun `With` .</span><span class="sxs-lookup"><span data-stu-id="5fc8f-128">Make sure your `With` block is initialized by executing the `With` statement entry point.</span></span>

## <a name="see-also"></a><span data-ttu-id="5fc8f-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5fc8f-129">See also</span></span>

- [<span data-ttu-id="5fc8f-130">Nesne Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="5fc8f-130">Object Variable Declaration</span></span>](../../programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="5fc8f-131">ReDim Deyimi</span><span class="sxs-lookup"><span data-stu-id="5fc8f-131">ReDim Statement</span></span>](../statements/redim-statement.md)
- [<span data-ttu-id="5fc8f-132">With...End With Deyimi</span><span class="sxs-lookup"><span data-stu-id="5fc8f-132">With...End With Statement</span></span>](../statements/with-end-with-statement.md)
