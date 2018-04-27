---
title: Değerini kopyalayarak &#39;ByRef&#39; parametresi &#39; &lt;parametername&gt; &#39; eşleşen bağımsız daraltır türünden &#39; &lt;typename1&gt; &#39; &#39; &lt;typename2&gt;&#39;
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords:
- BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 18c72e56e4b2cc9c2251de2417a9f12a6688323f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument-narrows-from-type-39lttypename1gt39-to-type-39lttypename2gt39"></a><span data-ttu-id="61e6d-102">Değerini kopyalayarak &#39;ByRef&#39; parametresi &#39; &lt;parametername&gt; &#39; eşleşen bağımsız daraltır türünden &#39; &lt;typename1&gt; &#39; &#39; &lt;typename2&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="61e6d-102">Copying the value of &#39;ByRef&#39; parameter &#39;&lt;parametername&gt;&#39; back to the matching argument narrows from type &#39;&lt;typename1&gt;&#39; to type &#39;&lt;typename2&gt;&#39;</span></span>
<span data-ttu-id="61e6d-103">Bir yordam, karşılık gelen parametre türüyle widens bağımsız değişkeni adı verilir ve parametre bağımsız değişkeni dönüştürme daraltma.</span><span class="sxs-lookup"><span data-stu-id="61e6d-103">A procedure is called with an argument that widens to the corresponding parameter type, and the conversion from the parameter to the argument is narrowing.</span></span>  
  
 <span data-ttu-id="61e6d-104">Bir sınıf veya yapı tanımladığınızda, diğer türleri için bu sınıf veya yapı türüne dönüştürmek için bir veya daha fazla dönüşüm işleçleri tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61e6d-104">When you define a class or structure, you can define one or more conversion operators to convert that class or structure type to other types.</span></span> <span data-ttu-id="61e6d-105">Ayrıca, diğer geri sınıfınız türlerine veya bir yapı türüne dönüştürmek için Geri Dönüşüm işleçleri tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61e6d-105">You can also define reverse conversion operators to convert those other types back to your class or structure type.</span></span> <span data-ttu-id="61e6d-106">Bir yordam çağrısında sınıf veya yapı türünüzü kullandığınızda, Visual Basic bağımsız değişken türü, karşılık gelen bir parametre türüne dönüştürmek için bu dönüşüm işleçleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61e6d-106">When you use your class or structure type in a procedure call, Visual Basic can use these conversion operators to convert the type of an argument to the type of its corresponding parameter.</span></span>  
  
 <span data-ttu-id="61e6d-107">Bağımsız değişken geçirirseniz [ByRef](../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic bazen kopyalar bağımsız değişken değeri bir başvuru geçirme yerine yordamı yerel bir değişkende içine.</span><span class="sxs-lookup"><span data-stu-id="61e6d-107">If you pass the argument [ByRef](../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="61e6d-108">Yordamın geri döndüğünde, böyle bir durumda, Visual Basic sonra yerel değişken değerini geri çağıran kodu değişkeninde kopyalamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="61e6d-108">In such a case, when the procedure returns, Visual Basic must then copy the local variable value back into the argument in the calling code.</span></span>  
  
 <span data-ttu-id="61e6d-109">Varsa bir `ByRef` bağımsız değişken değeri yordama kopyalanır ve bağımsız değişkeni ve parametre aynı tür dönüştürme gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="61e6d-109">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="61e6d-110">Ancak türleri farklıysa, Visual Basic her iki yönde de dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="61e6d-110">But if the types are different, Visual Basic must convert in both directions.</span></span> <span data-ttu-id="61e6d-111">Türlerinden birini sınıf veya yapı türü ise, Visual Basic, hem gelen ve diğer tür dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="61e6d-111">If one of the types is your class or structure type, Visual Basic must convert it both to and from the other type.</span></span> <span data-ttu-id="61e6d-112">Bu dönüşümleri birini genişletme, geriye doğru dönüştürme daraltma.</span><span class="sxs-lookup"><span data-stu-id="61e6d-112">If one of these conversions is widening, the reverse conversion might be narrowing.</span></span>  
  
 <span data-ttu-id="61e6d-113">**Hata Kimliği:** BC32053</span><span class="sxs-lookup"><span data-stu-id="61e6d-113">**Error ID:** BC32053</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="61e6d-114">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="61e6d-114">To correct this error</span></span>  
  
-   <span data-ttu-id="61e6d-115">Mümkünse, Visual Basic herhangi bir dönüştürmeye gerçekleştirmeniz gereken şekilde aynı türden çağıran bir bağımsız değişken yordamı parametre olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="61e6d-115">If possible, use a calling argument of the same type as the procedure parameter, so Visual Basic does not need to do any conversion.</span></span>  
  
-   <span data-ttu-id="61e6d-116">Yordam bağımsız değişkeni çağrısı gerekiyorsa parametre türünden farklı yazın ancak gerekmez çağırma bağımsız değişkeni bir değer döndürmesi, olması için parametre tanımlayın [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) yerine `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="61e6d-116">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) instead of `ByRef`.</span></span>  
  
-   <span data-ttu-id="61e6d-117">Çağırma bağımsız değişkeni bir değer döndürmesi gerekiyorsa, olarak geri dönüşüm işleci tanımlama [Widening](../../../visual-basic/language-reference/modifiers/widening.md), mümkün olduğunda.</span><span class="sxs-lookup"><span data-stu-id="61e6d-117">If you need to return a value into the calling argument, define the reverse conversion operator as [Widening](../../../visual-basic/language-reference/modifiers/widening.md), if possible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61e6d-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="61e6d-118">See Also</span></span>  
 [<span data-ttu-id="61e6d-119">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="61e6d-119">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="61e6d-120">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="61e6d-120">Procedure Parameters and Arguments</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="61e6d-121">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="61e6d-121">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="61e6d-122">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="61e6d-122">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [<span data-ttu-id="61e6d-123">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="61e6d-123">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="61e6d-124">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="61e6d-124">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="61e6d-125">Nasıl yapılır: Dönüştürme İşleci Tanımlama</span><span class="sxs-lookup"><span data-stu-id="61e6d-125">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="61e6d-126">Visual Basic'de tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="61e6d-126">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="61e6d-127">Genişletme ve Daraltma Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="61e6d-127">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
