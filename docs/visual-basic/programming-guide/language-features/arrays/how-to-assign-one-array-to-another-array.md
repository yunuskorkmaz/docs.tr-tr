---
title: "Nasıl yapılır: Bir Diziyi Başka Diziye Atama (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0dd2d678bbfdeaa6b12b5b5a4f69d0fbca8c1944
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a><span data-ttu-id="eb29e-102">Nasıl yapılır: Bir Diziyi Başka Diziye Atama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb29e-102">How to: Assign One Array to Another Array (Visual Basic)</span></span>
<span data-ttu-id="eb29e-103">Diziler nesneler olduğundan, diğer nesne türleri gibi atama deyimleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb29e-103">Because arrays are objects, you can use them in assignment statements like other object types.</span></span> <span data-ttu-id="eb29e-104">Dizi öğeleri ve derece ve uzunluğu bilgileri oluşturan veri bir işaretçi bir dizi değişkeni tutar ve yalnızca bu işaretçinin atama kopyalar.</span><span class="sxs-lookup"><span data-stu-id="eb29e-104">An array variable holds a pointer to the data constituting the array elements and the rank and length information, and an assignment copies only this pointer.</span></span>  
  
### <a name="to-assign-one-array-to-another-array"></a><span data-ttu-id="eb29e-105">Bir diziyi başka diziye atama için</span><span class="sxs-lookup"><span data-stu-id="eb29e-105">To assign one array to another array</span></span>  
  
1.  <span data-ttu-id="eb29e-106">İki dizisi aynı derece (dimensions sayısı) ve uyumlu öğesi veri türleri bulunduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="eb29e-106">Ensure that the two arrays have the same rank (number of dimensions) and compatible element data types.</span></span>  
  
2.  <span data-ttu-id="eb29e-107">Hedef dizi kaynak dizi atamak için bir standart atama deyimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="eb29e-107">Use a standard assignment statement to assign the source array to the destination array.</span></span> <span data-ttu-id="eb29e-108">Parantezler ile ya da dizi adı izlemeyin.</span><span class="sxs-lookup"><span data-stu-id="eb29e-108">Do not follow either array name with parentheses.</span></span>  
  
    ```  
    Dim formArray() As System.Windows.Forms.Form  
    Dim controlArray() As System.Windows.Forms.Control  
    controlArray = formArray  
    ```  
  
 <span data-ttu-id="eb29e-109">Başka bir dizi atadığınızda, aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="eb29e-109">When you assign one array to another, the following rules apply:</span></span>  
  
-   <span data-ttu-id="eb29e-110">**Eşit sıralar.**</span><span class="sxs-lookup"><span data-stu-id="eb29e-110">**Equal Ranks.**</span></span> <span data-ttu-id="eb29e-111">Hedef dizi derecesini (dimensions sayısı), kaynak dizinin aynı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb29e-111">The rank (number of dimensions) of the destination array must be the same as that of the source array.</span></span>  
  
     <span data-ttu-id="eb29e-112">İki dizi sıralar eşit olması koşuluyla boyutları eşit olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="eb29e-112">Provided the ranks of the two arrays are equal, the dimensions do not need to be equal.</span></span> <span data-ttu-id="eb29e-113">Belirli bir boyut öğe sayısı, atama sırasında değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb29e-113">The number of elements in a given dimension can change during assignment.</span></span>  
  
-   <span data-ttu-id="eb29e-114">**Öğe türleri.**</span><span class="sxs-lookup"><span data-stu-id="eb29e-114">**Element Types.**</span></span> <span data-ttu-id="eb29e-115">Her iki ya da bir dizi olmalıdır *başvuru türüne* öğeleri veya her iki diziler olmalıdır *değer türü* öğeleri.</span><span class="sxs-lookup"><span data-stu-id="eb29e-115">Either both arrays must have *reference type* elements or both arrays must have *value type* elements.</span></span> <span data-ttu-id="eb29e-116">Daha fazla bilgi için bkz: [değer türleri ve başvuru türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="eb29e-116">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
    -   <span data-ttu-id="eb29e-117">Her iki diziler değer türü öğeleri varsa öğe veri türlerini tam olarak aynı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb29e-117">If both arrays have value type elements, the element data types must be exactly the same.</span></span> <span data-ttu-id="eb29e-118">Bunun tek istisnası, bir dizi atayabilirsiniz olan `Enum` , temel türü bir dizi öğelerine `Enum`.</span><span class="sxs-lookup"><span data-stu-id="eb29e-118">The only exception to this is that you can assign an array of `Enum` elements to an array of the base type of that `Enum`.</span></span>  
  
    -   <span data-ttu-id="eb29e-119">İki dizi öğeleri türü başvurusu varsa, kaynak öğe türü hedef öğe türünden türetilmelidir.</span><span class="sxs-lookup"><span data-stu-id="eb29e-119">If both arrays have reference type elements, the source element type must derive from the destination element type.</span></span> <span data-ttu-id="eb29e-120">Bu durumda, iki dizi öğeleri olarak aynı devralma ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="eb29e-120">When this is the case, the two arrays have the same inheritance relationship as their elements.</span></span> <span data-ttu-id="eb29e-121">Bu adlı *dizi kovaryansı*.</span><span class="sxs-lookup"><span data-stu-id="eb29e-121">This is called *array covariance*.</span></span>  
  
 <span data-ttu-id="eb29e-122">Veri türleri uyumlu değilse yukarıdaki kuralları, örneğin ihlal bir hata ya da sıralar eşit olmayan derleyici bildirir.</span><span class="sxs-lookup"><span data-stu-id="eb29e-122">The compiler reports an error if the above rules are violated, for example if the data types are not compatible or the ranks are unequal.</span></span> <span data-ttu-id="eb29e-123">Hata atama denemeden önce dizilerin uyumlu olduğundan emin olmak için kodunuzu işleme ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb29e-123">You can add error handling to your code to make sure that the arrays are compatible before attempting an assignment.</span></span> <span data-ttu-id="eb29e-124">Aynı zamanda [TryCast işleci](../../../../visual-basic/language-reference/operators/trycast-operator.md) bir özel durum atma önlemek isterseniz anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="eb29e-124">You can also use the [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md) keyword if you want to avoid throwing an exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb29e-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eb29e-125">See Also</span></span>  
 [<span data-ttu-id="eb29e-126">Diziler</span><span class="sxs-lookup"><span data-stu-id="eb29e-126">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="eb29e-127">Dizilerle ilgili sorun giderme</span><span class="sxs-lookup"><span data-stu-id="eb29e-127">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)  
 [<span data-ttu-id="eb29e-128">Enum deyimi</span><span class="sxs-lookup"><span data-stu-id="eb29e-128">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [<span data-ttu-id="eb29e-129">Dizi dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="eb29e-129">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
