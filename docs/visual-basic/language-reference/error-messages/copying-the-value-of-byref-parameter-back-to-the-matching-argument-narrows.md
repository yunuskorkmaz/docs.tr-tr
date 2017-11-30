---
title: "Değeri &#39;kopyalama; ByRef &#39; Parametre &#39; &lt;parametername&gt;&#39; türündeki &#39; eşleşen bağımsız değişken daraltır için yeniden&lt; TypeName1&gt;& yazmak için #39; &#39;&lt; TypeName2&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords: BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4bf993639007162e2e17d4b8cb9dfe8d5316acaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument-narrows-from-type-39lttypename1gt39-to-type-39lttypename2gt39"></a><span data-ttu-id="6cb29-102">Değeri &#39;kopyalama; ByRef &#39; Parametre &#39; &lt;parametername&gt;&#39; türündeki &#39; eşleşen bağımsız değişken daraltır için yeniden&lt; TypeName1&gt;& yazmak için #39; &#39;&lt; TypeName2&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="6cb29-102">Copying the value of &#39;ByRef&#39; parameter &#39;&lt;parametername&gt;&#39; back to the matching argument narrows from type &#39;&lt;typename1&gt;&#39; to type &#39;&lt;typename2&gt;&#39;</span></span>
<span data-ttu-id="6cb29-103">Bir yordam, karşılık gelen parametre türüyle widens bağımsız değişkeni adı verilir ve parametre bağımsız değişkeni dönüştürme daraltma.</span><span class="sxs-lookup"><span data-stu-id="6cb29-103">A procedure is called with an argument that widens to the corresponding parameter type, and the conversion from the parameter to the argument is narrowing.</span></span>  
  
 <span data-ttu-id="6cb29-104">Bir sınıf veya yapı tanımladığınızda, diğer türleri için bu sınıf veya yapı türüne dönüştürmek için bir veya daha fazla dönüşüm işleçleri tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6cb29-104">When you define a class or structure, you can define one or more conversion operators to convert that class or structure type to other types.</span></span> <span data-ttu-id="6cb29-105">Ayrıca, diğer geri sınıfınız türlerine veya bir yapı türüne dönüştürmek için Geri Dönüşüm işleçleri tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6cb29-105">You can also define reverse conversion operators to convert those other types back to your class or structure type.</span></span> <span data-ttu-id="6cb29-106">Bir yordam çağrısı, sınıf veya yapı türünü kullandığınızda [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] bağımsız değişken türü, karşılık gelen bir parametre türüne dönüştürmek için bu dönüşüm işleçleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6cb29-106">When you use your class or structure type in a procedure call, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] can use these conversion operators to convert the type of an argument to the type of its corresponding parameter.</span></span>  
  
 <span data-ttu-id="6cb29-107">Bağımsız değişken geçirirseniz [ByRef](../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] bazen bir başvuru geçirme yerine yordamdaki yerel bir değişken bağımsız değişken değeri kopyalar.</span><span class="sxs-lookup"><span data-stu-id="6cb29-107">If you pass the argument [ByRef](../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="6cb29-108">Yordamın geri döndüğünde, böyle bir durumda, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] sonra yerel değişken değerini geri çağırma kodu değişkeninde kopyalamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6cb29-108">In such a case, when the procedure returns, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] must then copy the local variable value back into the argument in the calling code.</span></span>  
  
 <span data-ttu-id="6cb29-109">Varsa bir `ByRef` bağımsız değişken değeri yordama kopyalanır ve bağımsız değişkeni ve parametre aynı tür dönüştürme gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="6cb29-109">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="6cb29-110">Ancak türleri farklıysa [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] her iki yönde de dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6cb29-110">But if the types are different, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] must convert in both directions.</span></span> <span data-ttu-id="6cb29-111">Türlerinden birini, sınıf veya yapı türü ise [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] için hem de diğer türünden dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6cb29-111">If one of the types is your class or structure type, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] must convert it both to and from the other type.</span></span> <span data-ttu-id="6cb29-112">Bu dönüşümleri birini genişletme, geriye doğru dönüştürme daraltma.</span><span class="sxs-lookup"><span data-stu-id="6cb29-112">If one of these conversions is widening, the reverse conversion might be narrowing.</span></span>  
  
 <span data-ttu-id="6cb29-113">**Hata Kimliği:** BC32053</span><span class="sxs-lookup"><span data-stu-id="6cb29-113">**Error ID:** BC32053</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6cb29-114">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="6cb29-114">To correct this error</span></span>  
  
-   <span data-ttu-id="6cb29-115">Mümkünse, aynı türden çağıran bir bağımsız değişken yordamı parametre olarak kullanın [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] herhangi bir dönüştürmeye yapmak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="6cb29-115">If possible, use a calling argument of the same type as the procedure parameter, so [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] does not need to do any conversion.</span></span>  
  
-   <span data-ttu-id="6cb29-116">Yordam bağımsız değişkeni çağrısı gerekiyorsa parametre türünden farklı yazın ancak gerekmez çağırma bağımsız değişkeni bir değer döndürmesi, olması için parametre tanımlayın [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) yerine `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="6cb29-116">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) instead of `ByRef`.</span></span>  
  
-   <span data-ttu-id="6cb29-117">Çağırma bağımsız değişkeni bir değer döndürmesi gerekiyorsa, olarak geri dönüşüm işleci tanımlama [Widening](../../../visual-basic/language-reference/modifiers/widening.md), mümkün olduğunda.</span><span class="sxs-lookup"><span data-stu-id="6cb29-117">If you need to return a value into the calling argument, define the reverse conversion operator as [Widening](../../../visual-basic/language-reference/modifiers/widening.md), if possible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cb29-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6cb29-118">See Also</span></span>  
 [<span data-ttu-id="6cb29-119">Yordamları</span><span class="sxs-lookup"><span data-stu-id="6cb29-119">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="6cb29-120">Parametreler ve bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="6cb29-120">Procedure Parameters and Arguments</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="6cb29-121">Bağımsız değişkenleri değere ve başvuruya göre geçirme</span><span class="sxs-lookup"><span data-stu-id="6cb29-121">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="6cb29-122">İşleç yordamları</span><span class="sxs-lookup"><span data-stu-id="6cb29-122">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [<span data-ttu-id="6cb29-123">Operator deyimi</span><span class="sxs-lookup"><span data-stu-id="6cb29-123">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="6cb29-124">Nasıl yapılır: bir işleci tanımlama</span><span class="sxs-lookup"><span data-stu-id="6cb29-124">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="6cb29-125">Nasıl yapılır: bir dönüşüm işleci tanımlama</span><span class="sxs-lookup"><span data-stu-id="6cb29-125">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="6cb29-126">Visual Basic'de tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="6cb29-126">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="6cb29-127">Genişletme ve daraltma dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="6cb29-127">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
