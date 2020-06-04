---
title: "'<typename1>' 'ByRef' parametresinin değerini eşleşen bağımsız değişkene geri kopyalarken '<typename2>' türünden '<parametername>' türüne örtük dönüştürme"
ms.date: 07/20/2015
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
ms.openlocfilehash: 4d0f9aac795f683cf58210ea38b3783e451ccfc3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402868"
---
# <a name="implicit-conversion-from-typename1-to-typename2-in-copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument"></a><span data-ttu-id="e3981-102">'\<typename1>' 'ByRef' parametresinin değerini eşleşen bağımsız değişkene geri kopyalarken '\<typename2>' türünden '\<parametername>' türüne örtük dönüştürme</span><span class="sxs-lookup"><span data-stu-id="e3981-102">Implicit conversion from '\<typename1>' to '\<typename2>' in copying the value of 'ByRef' parameter '\<parametername>' back to the matching argument.</span></span>
<span data-ttu-id="e3981-103">Bir yordam, karşılık gelen parametresinden farklı bir türün [ByRef](../modifiers/byref.md) bağımsız değişkeniyle çağırılır.</span><span class="sxs-lookup"><span data-stu-id="e3981-103">A procedure is called with a [ByRef](../modifiers/byref.md) argument of a different type than that of its corresponding parameter.</span></span>  
  
 <span data-ttu-id="e3981-104">Bir bağımsız değişken geçirirseniz `ByRef` Visual Basic bazen bağımsız değişken değerini bir başvuruyu geçirmek yerine yordamda yerel bir değişkene kopyalar.</span><span class="sxs-lookup"><span data-stu-id="e3981-104">If you pass an argument `ByRef`, Visual Basic sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="e3981-105">Böyle bir durumda, yordam döndürüldüğünde Visual Basic, ardından yerel değişken değerini çağıran koddaki bağımsız değişkene geri kopyalamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e3981-105">In such a case, when the procedure returns, Visual Basic must then copy the local variable value back into the argument in the calling code.</span></span>  
  
 <span data-ttu-id="e3981-106">Bir `ByRef` bağımsız değişken değeri yordama kopyalanırsa ve bağımsız değişkeni ve parametresi aynı türde ise, dönüştürme gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="e3981-106">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="e3981-107">Ancak türler farklıysa Visual Basic her iki yönde de dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e3981-107">But if the types are different, Visual Basic must convert in both directions.</span></span> <span data-ttu-id="e3981-108">`CType`Bir yordam bağımsız değişkeninde veya parametresinde diğer dönüştürme anahtar sözcüklerini de kullanamadığı için, bu dönüştürme her zaman örtük olur.</span><span class="sxs-lookup"><span data-stu-id="e3981-108">Because you cannot use `CType` or any of the other conversion keywords on a procedure argument or parameter, such a conversion is always implicit.</span></span>  
  
 <span data-ttu-id="e3981-109">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="e3981-109">By default, this message is a warning.</span></span> <span data-ttu-id="e3981-110">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="e3981-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="e3981-111">**Hata kimliği:** BC41999</span><span class="sxs-lookup"><span data-stu-id="e3981-111">**Error ID:** BC41999</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e3981-112">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="e3981-112">To correct this error</span></span>  
  
- <span data-ttu-id="e3981-113">Mümkünse, yordam parametresiyle aynı türde bir çağırma bağımsız değişkeni kullanın, bu nedenle Visual Basic herhangi bir dönüştürme yapması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e3981-113">If possible, use a calling argument of the same type as the procedure parameter, so Visual Basic does not need to do any conversion.</span></span>  
  
- <span data-ttu-id="e3981-114">Parametre türünden farklı bir bağımsız değişken türü olan yordamı çağırmanız gerekiyorsa, ancak çağıran bağımsız değişkenine bir değer döndürmemelidir, yerine [ByVal](../modifiers/byval.md) olacak parametreyi tanımlayın `ByRef` .</span><span class="sxs-lookup"><span data-stu-id="e3981-114">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../modifiers/byval.md) instead of `ByRef`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3981-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3981-115">See also</span></span>

- [<span data-ttu-id="e3981-116">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="e3981-116">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="e3981-117">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="e3981-117">Procedure Parameters and Arguments</span></span>](../../programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [<span data-ttu-id="e3981-118">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="e3981-118">Passing Arguments by Value and by Reference</span></span>](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="e3981-119">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="e3981-119">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
