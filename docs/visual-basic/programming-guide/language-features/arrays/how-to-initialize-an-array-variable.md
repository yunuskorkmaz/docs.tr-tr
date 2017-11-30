---
title: "Nasıl yapılır: Visual Basic'te Dizi Değişkeni Başlatma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
caps.latest.revision: "42"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3ccdbed601d3fa87acb0833bc153c199b17a4eba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a><span data-ttu-id="c44e4-102">Nasıl yapılır: Visual Basic'te Dizi Değişkeni Başlatma</span><span class="sxs-lookup"><span data-stu-id="c44e4-102">How to: Initialize an Array Variable in Visual Basic</span></span>
<span data-ttu-id="c44e4-103">Dizi değişmez değer de dahil olmak üzere bir dizi değişkeni başlatma bir `New` yan tümcesi ve dizinin ilk değerleri belirtme.</span><span class="sxs-lookup"><span data-stu-id="c44e4-103">You initialize an array variable by including an array literal in a `New` clause and specifying the initial values of the array.</span></span> <span data-ttu-id="c44e4-104">Türünü belirtin veya değişmez değer dizideki olayla izin verin.</span><span class="sxs-lookup"><span data-stu-id="c44e4-104">You can either specify the type or allow it to be inferred from the values in the array literal.</span></span> <span data-ttu-id="c44e4-105">Ne tür çıkarımı yapılan hakkında daha fazla bilgi için "Doldurma bir dizi ile ilk değerleri" bölümüne bakın. [diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="c44e4-105">For more information about how the type is inferred, see "Populating an Array with Initial Values" in [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a><span data-ttu-id="c44e4-106">Değişmez değer bir dizi kullanarak bir dizi değişkeni başlatılamadı</span><span class="sxs-lookup"><span data-stu-id="c44e4-106">To initialize an array variable by using an array literal</span></span>  
  
-   <span data-ttu-id="c44e4-107">Ya da `New` yan tümcesi veya dizi değeri atadığınızda, köşeli parantez içindeki öğe değerlerini sağlayın (`{}`).</span><span class="sxs-lookup"><span data-stu-id="c44e4-107">Either in the `New` clause, or when you assign the array value, supply the element values inside braces (`{}`).</span></span> <span data-ttu-id="c44e4-108">Aşağıdaki örnek, bildirme, oluşturma ve bir değişken türü öğesi içeren bir dizi içerecek şekilde başlatmak için çeşitli yollar gösterir `Char`.</span><span class="sxs-lookup"><span data-stu-id="c44e4-108">The following example shows several ways to declare, create, and initialize a variable to contain an array that has elements of type `Char`.</span></span>  
  
     [!code-vb[VbVbalrArrays#16](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_1.vb)]  
  
     <span data-ttu-id="c44e4-109">Her deyim yürütüldükten sonra oluşturulan dizi dizini ilk değerleri içeren 2 aracılığıyla dizin 0 konumunda öğelerle 3 uzunluğuna sahip.</span><span class="sxs-lookup"><span data-stu-id="c44e4-109">After each statement executes, the array that's created has a length of 3, with elements at index 0 through index 2 containing the initial values.</span></span> <span data-ttu-id="c44e4-110">Üst sınır ve değerlerini sağlarsanız, üst sınır aracılığıyla 0 dizinden her öğe için bir değer içermelidir.</span><span class="sxs-lookup"><span data-stu-id="c44e4-110">If you supply both the upper bound and the values, you must include a value for every element from index 0 through the upper bound.</span></span>  
  
     <span data-ttu-id="c44e4-111">Değişmez değer bir dizi öğesi değerlerini sağlarsanız dizini üst sınırı belirtin gerekmez dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="c44e4-111">Notice that you do not have to specify the index upper bound if you supply element values in an array literal.</span></span> <span data-ttu-id="c44e4-112">Üst sınır belirtilirse, dizinin boyutunu değişmez değer dizideki sayısına dayalı olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="c44e4-112">If no upper bound is specified, the size of the array is inferred based on the number of values in the array literal.</span></span>  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a><span data-ttu-id="c44e4-113">Dizi değişmez değerleri kullanarak çok boyutlu bir diziye başlatmak için</span><span class="sxs-lookup"><span data-stu-id="c44e4-113">To initialize a multidimensional array variable by using array literals</span></span>  
  
-   <span data-ttu-id="c44e4-114">İç içe köşeli parantez içindeki değerleri (`{}`) küme ayraçları içinde.</span><span class="sxs-lookup"><span data-stu-id="c44e4-114">Nest values inside braces (`{}`) within braces.</span></span> <span data-ttu-id="c44e4-115">Tümü aynı türde ve uzunluk dizileri olarak Infer iç içe geçmiş dizi değişmez değerleri emin olun.</span><span class="sxs-lookup"><span data-stu-id="c44e4-115">Ensure that the nested array literals all infer as arrays of the same type and length.</span></span> <span data-ttu-id="c44e4-116">Aşağıdaki kod örneğinde boyutlu bir diziye başlatma bazı örnekleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c44e4-116">The following code example shows several examples of multidimensional array initialization.</span></span>  
  
     [!code-vb[VbVbalrArrays#17](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_2.vb)]  
  
-   <span data-ttu-id="c44e4-117">Açıkça dizi sınırları belirtin ya da bunları dışlamayı ve değişmez değer dizideki değerlere göre dizi sınırları Infer derleyici sahip.</span><span class="sxs-lookup"><span data-stu-id="c44e4-117">You can explicitly specify the array bounds, or leave them out and have the compiler infer the array bounds based on the values in the array literal.</span></span> <span data-ttu-id="c44e4-118">Üst sınırları ve değerlerini sağlarsanız, her boyut üst sınırı aracılığıyla 0 dizinden her öğe için bir değer içermelidir.</span><span class="sxs-lookup"><span data-stu-id="c44e4-118">If you supply both the upper bounds and the values, you must include a value for every element from index 0 through the upper bound in every dimension.</span></span> <span data-ttu-id="c44e4-119">Aşağıdaki örnek, bildirme, oluşturma ve türündeki öğeler sahip iki boyutlu bir dizi içeren bir değişkeni başlatmak için çeşitli yollar gösterir.`Short`</span><span class="sxs-lookup"><span data-stu-id="c44e4-119">The following example shows several ways to declare, create, and initialize a variable to contain a two-dimensional array that has elements of type `Short`</span></span>  
  
     [!code-vb[VbVbalrArrays#18](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_3.vb)]  
  
     <span data-ttu-id="c44e4-120">Her deyim yürütüldükten sonra oluşturulan dizi dizine sahip altı başlatılmış öğeleri içerir `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, ve `(1,2)`.</span><span class="sxs-lookup"><span data-stu-id="c44e4-120">After each statement executes, the created array contains six initialized elements that have indexes `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, and `(1,2)`.</span></span> <span data-ttu-id="c44e4-121">Her bir dizi konum değeri içeren `10`.</span><span class="sxs-lookup"><span data-stu-id="c44e4-121">Each array location contains the value `10`.</span></span>  
  
-   <span data-ttu-id="c44e4-122">Aşağıdaki örnek, çok boyutlu bir diziye yineler.</span><span class="sxs-lookup"><span data-stu-id="c44e4-122">The following example iterates through a multidimensional array.</span></span> <span data-ttu-id="c44e4-123">Visual Basic ile yazılmış bir Windows konsol uygulaması içinde içinde kod yapıştırın `Sub Main()` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c44e4-123">In a Windows console application that is written in Visual Basic, paste the code inside the `Sub Main()` method.</span></span> <span data-ttu-id="c44e4-124">Son açıklamaları çıktısını göster.</span><span class="sxs-lookup"><span data-stu-id="c44e4-124">The last comments show the output.</span></span>  
  
     [!code-vb[VbVbalrArrays#31](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_4.vb)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a><span data-ttu-id="c44e4-125">Dizi değişmez değerleri kullanarak basit bir diziye başlatmak için</span><span class="sxs-lookup"><span data-stu-id="c44e4-125">To initialize a jagged array variable by using array literals</span></span>  
  
-   <span data-ttu-id="c44e4-126">İç içe nesne değerleri kaşlı ayraçlar içinde (`{}`).</span><span class="sxs-lookup"><span data-stu-id="c44e4-126">Nest object values inside braces (`{}`).</span></span> <span data-ttu-id="c44e4-127">Ayrıca, basit bir dizi söz konusu olduğunda farklı uzunlukta diziler belirtin dizi değişmez değerleri geçirebilmenize rağmen emin olun, iç içe geçmiş dizi değişmez değerleri parantez içine alınmış (`()`).</span><span class="sxs-lookup"><span data-stu-id="c44e4-127">Although you can also nest array literals that specify arrays of different lengths, in the case of a jagged array, make sure that that the nested array literals are enclosed in parentheses (`()`).</span></span> <span data-ttu-id="c44e4-128">İç içe geçmiş dizi değişmez değerleri değerlendirmesi parantez zorlamak ve sonuçta elde edilen diziler Basit dizi ilk değerleri olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c44e4-128">The parentheses force the evaluation of the nested array literals, and the resulting arrays are used as the initial values of the jagged array.</span></span> <span data-ttu-id="c44e4-129">Aşağıdaki kod örneği iki örnek basit dizi başlatma gösterir.</span><span class="sxs-lookup"><span data-stu-id="c44e4-129">The following code example shows two examples of jagged array initialization.</span></span>  
  
     [!code-vb[VbVbalrArrays#19](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_5.vb)]  
  
-   <span data-ttu-id="c44e4-130">Aşağıdaki örnekte basit bir dizisini yineler.</span><span class="sxs-lookup"><span data-stu-id="c44e4-130">The following example iterates through a jagged array.</span></span> <span data-ttu-id="c44e4-131">Visual Basic ile yazılmış bir Windows konsol uygulaması içinde içinde kod yapıştırın `Sub Main()` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c44e4-131">In a Windows console application that is written in Visual Basic, paste the code inside the `Sub Main()` method.</span></span>  <span data-ttu-id="c44e4-132">Kodu son açıklamalarda çıktısını göster.</span><span class="sxs-lookup"><span data-stu-id="c44e4-132">The last comments in the code show the output.</span></span>  
  
     [!code-vb[VbVbalrArrays#32](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_6.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c44e4-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c44e4-133">See Also</span></span>  
 [<span data-ttu-id="c44e4-134">Diziler</span><span class="sxs-lookup"><span data-stu-id="c44e4-134">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="c44e4-135">Dizilerle ilgili sorun giderme</span><span class="sxs-lookup"><span data-stu-id="c44e4-135">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
