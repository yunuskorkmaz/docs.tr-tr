---
title: "'ByRef' '<parametername>' parametresinin değeri '<typename1>' türünden '<typename2>' türüne daralan eşleşen bağımsız değişkene geri kopyalanıyor"
ms.date: 07/20/2015
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords:
- BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
ms.openlocfilehash: 971110c505800b0ceba73506f2b2702516a7a23a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874545"
---
# <a name="copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument-narrows-from-type-typename1-to-type-typename2"></a><span data-ttu-id="213cd-102">'ByRef' '\<parametername>' parametresinin değeri '\<typename1>' türünden '\<typename2>' türüne daralan eşleşen bağımsız değişkene geri kopyalanıyor</span><span class="sxs-lookup"><span data-stu-id="213cd-102">Copying the value of 'ByRef' parameter '\<parametername>' back to the matching argument narrows from type '\<typename1>' to type '\<typename2>'</span></span>

<span data-ttu-id="213cd-103">Bir yordam, karşılık gelen parametre türüne widens bir bağımsız değişkenle çağrılır ve parametresinden bağımsız değişkene dönüştürme daraltma olur.</span><span class="sxs-lookup"><span data-stu-id="213cd-103">A procedure is called with an argument that widens to the corresponding parameter type, and the conversion from the parameter to the argument is narrowing.</span></span>  
  
 <span data-ttu-id="213cd-104">Bir sınıf veya yapı tanımladığınızda, bu sınıf veya yapı türünü diğer türlere dönüştürmek için bir veya daha fazla dönüştürme işleci tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="213cd-104">When you define a class or structure, you can define one or more conversion operators to convert that class or structure type to other types.</span></span> <span data-ttu-id="213cd-105">Ayrıca, bu diğer türleri sınıfınıza veya yapı türüne geri dönüştürmek için ters dönüştürme işleçleri tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="213cd-105">You can also define reverse conversion operators to convert those other types back to your class or structure type.</span></span> <span data-ttu-id="213cd-106">Sınıf veya yapı türünü bir yordam çağrısında kullandığınızda Visual Basic, bir bağımsız değişkenin türünü karşılık gelen parametresinin türüne dönüştürmek için bu dönüştürme işleçlerini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="213cd-106">When you use your class or structure type in a procedure call, Visual Basic can use these conversion operators to convert the type of an argument to the type of its corresponding parameter.</span></span>  
  
 <span data-ttu-id="213cd-107">[ByRef](../modifiers/byref.md)bağımsız değişkenini geçirirseniz Visual Basic bazen bağımsız değişken değerini bir başvuruyu geçirmek yerine yordamda yerel bir değişkene kopyalar.</span><span class="sxs-lookup"><span data-stu-id="213cd-107">If you pass the argument [ByRef](../modifiers/byref.md), Visual Basic sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="213cd-108">Böyle bir durumda, yordam döndürüldüğünde Visual Basic, ardından yerel değişken değerini çağıran koddaki bağımsız değişkene geri kopyalamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="213cd-108">In such a case, when the procedure returns, Visual Basic must then copy the local variable value back into the argument in the calling code.</span></span>  
  
 <span data-ttu-id="213cd-109">Bir `ByRef` bağımsız değişken değeri yordama kopyalanırsa ve bağımsız değişkeni ve parametresi aynı türde ise, dönüştürme gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="213cd-109">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="213cd-110">Ancak türler farklıysa Visual Basic her iki yönde de dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="213cd-110">But if the types are different, Visual Basic must convert in both directions.</span></span> <span data-ttu-id="213cd-111">Türlerden biri sınıfınız veya yapı türtipinizdeki Visual Basic, bunu diğer türden ve arasında dönüştürmelidir.</span><span class="sxs-lookup"><span data-stu-id="213cd-111">If one of the types is your class or structure type, Visual Basic must convert it both to and from the other type.</span></span> <span data-ttu-id="213cd-112">Bu dönüşümlerden biri genişletme ise, ters dönüştürme daraltma olabilir.</span><span class="sxs-lookup"><span data-stu-id="213cd-112">If one of these conversions is widening, the reverse conversion might be narrowing.</span></span>  
  
 <span data-ttu-id="213cd-113">**Hata kimliği:** BC32053</span><span class="sxs-lookup"><span data-stu-id="213cd-113">**Error ID:** BC32053</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="213cd-114">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="213cd-114">To correct this error</span></span>  
  
- <span data-ttu-id="213cd-115">Mümkünse, yordam parametresiyle aynı türde bir çağırma bağımsız değişkeni kullanın, bu nedenle Visual Basic herhangi bir dönüştürme yapması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="213cd-115">If possible, use a calling argument of the same type as the procedure parameter, so Visual Basic does not need to do any conversion.</span></span>  
  
- <span data-ttu-id="213cd-116">Parametre türünden farklı bir bağımsız değişken türü olan yordamı çağırmanız gerekiyorsa, ancak çağıran bağımsız değişkenine bir değer döndürmemelidir, yerine [ByVal](../modifiers/byval.md) olacak parametreyi tanımlayın `ByRef` .</span><span class="sxs-lookup"><span data-stu-id="213cd-116">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../modifiers/byval.md) instead of `ByRef`.</span></span>  
  
- <span data-ttu-id="213cd-117">Çağırma bağımsız değişkenine bir değer döndürmenize gerek varsa, uygunsa ters dönüştürme işlecini [genişletme](../modifiers/widening.md)olarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="213cd-117">If you need to return a value into the calling argument, define the reverse conversion operator as [Widening](../modifiers/widening.md), if possible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="213cd-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="213cd-118">See also</span></span>

- [<span data-ttu-id="213cd-119">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="213cd-119">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="213cd-120">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="213cd-120">Procedure Parameters and Arguments</span></span>](../../programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [<span data-ttu-id="213cd-121">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="213cd-121">Passing Arguments by Value and by Reference</span></span>](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="213cd-122">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="213cd-122">Operator Procedures</span></span>](../../programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="213cd-123">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="213cd-123">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="213cd-124">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="213cd-124">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="213cd-125">Nasıl yapılır: Dönüştürme İşleci Tanımlama</span><span class="sxs-lookup"><span data-stu-id="213cd-125">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="213cd-126">Visual Basic'de Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="213cd-126">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="213cd-127">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="213cd-127">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
