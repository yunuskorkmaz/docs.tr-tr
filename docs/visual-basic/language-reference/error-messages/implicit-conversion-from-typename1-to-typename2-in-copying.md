---
title: "'<typename1>' 'ByRef' parametresinin değerini eşleşen bağımsız değişkene geri kopyalarken '<typename2>' türünden '<parametername>' türüne örtük dönüştürme"
ms.date: 07/20/2015
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
ms.openlocfilehash: 7ac0e7961e1a039e505c85a35c7c31353ed6578e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64661984"
---
# <a name="implicit-conversion-from-typename1-to-typename2-in-copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument"></a><span data-ttu-id="44147-102">Arasında örtük dönüşüm '\<typename1 >' için '\<typename2 >' 'ByRef' parametresinin değeri kopyalarken '\<parametername >' eşleşen bağımsız değişkene geri dönün.</span><span class="sxs-lookup"><span data-stu-id="44147-102">Implicit conversion from '\<typename1>' to '\<typename2>' in copying the value of 'ByRef' parameter '\<parametername>' back to the matching argument.</span></span>
<span data-ttu-id="44147-103">Bir yordam adlı bir [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) , karşılık gelen parametre farklı bir tür bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="44147-103">A procedure is called with a [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) argument of a different type than that of its corresponding parameter.</span></span>  
  
 <span data-ttu-id="44147-104">Bağımsız değişken geçirirseniz `ByRef`, Visual Basic bazen kopyalar bağımsız değişken değeri yordamda bir başvuru geçirmek yerine yerel bir değişken içine.</span><span class="sxs-lookup"><span data-stu-id="44147-104">If you pass an argument `ByRef`, Visual Basic sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="44147-105">Yordamı geri döndüğünde, böyle bir durumda, Visual Basic sonra yerel değişken değeri çağıran koddaki bağımsız değişken uygulamasına geri kopyalamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="44147-105">In such a case, when the procedure returns, Visual Basic must then copy the local variable value back into the argument in the calling code.</span></span>  
  
 <span data-ttu-id="44147-106">Varsa bir `ByRef` bağımsız değişken değeri yordama kopyalanır ve bağımsız değişken ile parametre aynı tür dönüştürme gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="44147-106">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="44147-107">Ancak, Visual Basic türleri farklı ise, her iki yönde dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="44147-107">But if the types are different, Visual Basic must convert in both directions.</span></span> <span data-ttu-id="44147-108">Kullanamazsınız çünkü `CType` veya herhangi bir dönüştürme anahtar bir yordam bağımsız değişkeninin veya parametre, böyle bir dönüştürme her zaman kesin.</span><span class="sxs-lookup"><span data-stu-id="44147-108">Because you cannot use `CType` or any of the other conversion keywords on a procedure argument or parameter, such a conversion is always implicit.</span></span>  
  
 <span data-ttu-id="44147-109">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="44147-109">By default, this message is a warning.</span></span> <span data-ttu-id="44147-110">Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini hakkında daha fazla bilgi için bkz: [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="44147-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="44147-111">**Hata Kimliği:** BC41999</span><span class="sxs-lookup"><span data-stu-id="44147-111">**Error ID:** BC41999</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="44147-112">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="44147-112">To correct this error</span></span>  
  
- <span data-ttu-id="44147-113">Mümkünse, Visual Basic, herhangi bir dönüştürme yapmak gerekmez. Bu nedenle aynı türde çağıran bir bağımsız değişken yordam parametresi kullanın.</span><span class="sxs-lookup"><span data-stu-id="44147-113">If possible, use a calling argument of the same type as the procedure parameter, so Visual Basic does not need to do any conversion.</span></span>  
  
- <span data-ttu-id="44147-114">Bağımsız değişken içeren bir yordamı çağırma gerekiyorsa parametre türünden farklı yazın ancak ihtiyaç duymayan çağırma bağımsız değişkeni bir değer döndürmek parametre tanımlayın [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) yerine `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="44147-114">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) instead of `ByRef`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44147-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44147-115">See also</span></span>

- [<span data-ttu-id="44147-116">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="44147-116">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="44147-117">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="44147-117">Procedure Parameters and Arguments</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [<span data-ttu-id="44147-118">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="44147-118">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="44147-119">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="44147-119">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
