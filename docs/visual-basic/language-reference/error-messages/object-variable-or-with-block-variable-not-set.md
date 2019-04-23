---
title: Nesne değişkeni veya With bloğu değişkeni ayarlanmamış
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: b2c0c47b359e218111c1629ea574303a6d663046
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59297934"
---
# <a name="object-variable-or-with-block-variable-not-set"></a><span data-ttu-id="b044e-102">Nesne değişkeni veya With bloğu değişkeni ayarlanmamış</span><span class="sxs-lookup"><span data-stu-id="b044e-102">Object variable or With block variable not set</span></span>
<span data-ttu-id="b044e-103">Geçersiz nesne değişkeni başvuruda bulunuyor.</span><span class="sxs-lookup"><span data-stu-id="b044e-103">An invalid object variable is being referenced.</span></span>   <span data-ttu-id="b044e-104">Bu hata, çeşitli nedenlerle oluşabilir:</span><span class="sxs-lookup"><span data-stu-id="b044e-104">This error can occur for several reasons:</span></span>  
  
-   <span data-ttu-id="b044e-105">Bir tür belirtmeden bir değişken bildirildi.</span><span class="sxs-lookup"><span data-stu-id="b044e-105">A variable was declared without specifying a type.</span></span> <span data-ttu-id="b044e-106">Bir tür belirtmeden bildirilen bir değişken, yazmak için varsayılanları `Object`.</span><span class="sxs-lookup"><span data-stu-id="b044e-106">If a variable is declared without specifying a type, it defaults to type `Object`.</span></span>  
  
     <span data-ttu-id="b044e-107">Örneğin, bildirilen bir değişken `Dim x` türünde olur `Object;` ile bildirilen bir değişken `Dim x As String` türünde olur `String`.</span><span class="sxs-lookup"><span data-stu-id="b044e-107">For example, a variable declared with `Dim x` would be of type `Object;` a variable declared with `Dim x As String` would be of type `String`.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="b044e-108">`Option Strict` Deyimi izin vermiyor sonuçlanır örtülü yazma bir `Object` türü.</span><span class="sxs-lookup"><span data-stu-id="b044e-108">The `Option Strict` statement disallows implicit typing that results in an `Object` type.</span></span> <span data-ttu-id="b044e-109">Türü atlarsanız, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="b044e-109">If you omit the type, a compile-time error will occur.</span></span> <span data-ttu-id="b044e-110">Bkz: [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b044e-110">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
-   <span data-ttu-id="b044e-111">Ayarlanmış bir nesneye başvurmak çalışıyorsunuz. `Nothing`</span><span class="sxs-lookup"><span data-stu-id="b044e-111">You are attempting to reference an object that has been set to `Nothing`</span></span>  
  
     <span data-ttu-id="b044e-112">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="b044e-112">.</span></span>  
  
-   <span data-ttu-id="b044e-113">Doğru değildi bildirilen bir dizi değişkenini öğesi erişmeye çalışıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="b044e-113">You are attempting to access an element of an array variable that wasn't properly declared.</span></span>  
  
     <span data-ttu-id="b044e-114">Örneğin, bir dizi olarak bildirilen `products() As String` dizinin bir öğesine başvurmak denerseniz hata tetikleyecek `products(3) = "Widget"`.</span><span class="sxs-lookup"><span data-stu-id="b044e-114">For example, an array declared as `products() As String` will trigger the error if you try to reference an element of the array `products(3) = "Widget"`.</span></span> <span data-ttu-id="b044e-115">Dizinin öğe yok ve bir nesne olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="b044e-115">The array has no elements and is treated as an object.</span></span>  
  
-   <span data-ttu-id="b044e-116">Erişim kodu içinde çalıştığınız bir `With...End With` blok başlatılmadan önce engelleyin.</span><span class="sxs-lookup"><span data-stu-id="b044e-116">You are attempting to access code within a `With...End With` block before the block has been initialized.</span></span>   <span data-ttu-id="b044e-117">A `With...End With` blok yürüterek başlatılmalı `With` deyimi giriş noktası.</span><span class="sxs-lookup"><span data-stu-id="b044e-117">A `With...End With` block must be initialized by executing the `With` statement entry point.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b044e-118">Visual Basic veya VBA önceki sürümlerinde bu hata ayrıca kullanmadan bir değeri bir değişkene atayarak tetiklendi `Set` anahtar sözcüğü (`x = "name"` yerine `Set x = "name"`).</span><span class="sxs-lookup"><span data-stu-id="b044e-118">In earlier versions of Visual Basic or VBA this error was also triggered by assigning a value to a variable without using the `Set` keyword (`x = "name"` instead of `Set x = "name"`).</span></span> <span data-ttu-id="b044e-119">`Set` Anahtar sözcüğü artık Visual Basic. NET'te geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="b044e-119">The `Set` keyword is no longer valid in Visual Basic .Net.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b044e-120">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="b044e-120">To correct this error</span></span>  
  
1. <span data-ttu-id="b044e-121">Ayarlama `Option Strict` için `On` dosyasının başına aşağıdaki kodu ekleyerek:</span><span class="sxs-lookup"><span data-stu-id="b044e-121">Set `Option Strict` to `On` by adding the following code to the beginning of the file:</span></span>  
  
```vb  
Option Strict On  
```  

     When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.  
  
2. <span data-ttu-id="b044e-122">Etkinleştirmek istemiyorsanız `Option Strict`, olmadan bir türü belirtilmiş tüm değişkenler için kodunuzu arama (`Dim x` yerine `Dim x As String`) ve amaçlanan türü bildirimini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b044e-122">If you don't want to enable `Option Strict`, search your code for any variables that were specified without a type (`Dim x` instead of `Dim x As String`) and add the intended type to the declaration.</span></span>  
  
3. <span data-ttu-id="b044e-123">Olarak ayarlanan bir nesne değişkenine başvuran olmayan emin `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="b044e-123">Make sure you aren't referring to  an object variable that has been set to `Nothing`.</span></span>  <span data-ttu-id="b044e-124">Kodunuz için bir anahtar sözcük arama `Nothing`ve böylece nesnenin belirlendiğinden, kodunuzu gözden geçirme `Nothing` sonra başvurduğunuz kadar.</span><span class="sxs-lookup"><span data-stu-id="b044e-124">Search your code for the keyword `Nothing`, and revise your code so that the object isn't set to `Nothing` until after you have referenced it.</span></span>  
  
4. <span data-ttu-id="b044e-125">Bunları erişmeden önce herhangi bir dizi değişkeni dimensioned emin olun.</span><span class="sxs-lookup"><span data-stu-id="b044e-125">Make sure that any array  variables are dimensioned before you access them.</span></span> <span data-ttu-id="b044e-126">Dizinin ilk oluşturduğunuzda, bir boyut ya da atayabilirsiniz (`Dim x(5) As String` yerine `Dim x() As String`), veya `ReDim` ilk erişmeden önce dizinin boyut sayısını ayarlamak için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="b044e-126">You can either assign a dimension when you first create the array (`Dim x(5) As String` instead of `Dim x() As String`), or use the `ReDim` keyword to set the dimensions of the array before you first access it.</span></span>  
  
5. <span data-ttu-id="b044e-127">Emin olun, `With` blok yürüterek başlatılan `With` deyimi giriş noktası.</span><span class="sxs-lookup"><span data-stu-id="b044e-127">Make sure your `With` block is initialized by executing the `With` statement entry point.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b044e-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b044e-128">See also</span></span>

- [<span data-ttu-id="b044e-129">Nesne Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="b044e-129">Object Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="b044e-130">ReDim Deyimi</span><span class="sxs-lookup"><span data-stu-id="b044e-130">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="b044e-131">With...End With Deyimi</span><span class="sxs-lookup"><span data-stu-id="b044e-131">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
