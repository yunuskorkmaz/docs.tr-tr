---
title: Örtük dönüştürme &#39; &lt;typename1&gt; &#39; için &#39; &lt;typename2&gt; &#39; değerini kopyalayarak içinde &#39;ByRef&#39; parametresi &#39; &lt; parametername&gt; &#39; eşleşen bağımsız değişkene dön.
ms.date: 07/20/2015
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
ms.openlocfilehash: b1f772598b18f8edfe0198f62d78854d30f993ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590006"
---
# <a name="implicit-conversion-from-39lttypename1gt39-to-39lttypename2gt39-in-copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument"></a><span data-ttu-id="4d5a7-102">Örtük dönüştürme &#39; &lt;typename1&gt; &#39; için &#39; &lt;typename2&gt; &#39; değerini kopyalayarak içinde &#39;ByRef&#39; parametresi &#39; &lt; parametername&gt; &#39; eşleşen bağımsız değişkene dön.</span><span class="sxs-lookup"><span data-stu-id="4d5a7-102">Implicit conversion from &#39;&lt;typename1&gt;&#39; to &#39;&lt;typename2&gt;&#39; in copying the value of &#39;ByRef&#39; parameter &#39;&lt;parametername&gt;&#39; back to the matching argument.</span></span>
<span data-ttu-id="4d5a7-103">Bir yordam ile adlı bir [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) bağımsız değişkeni, karşılık gelen bir parametre daha farklı bir türde.</span><span class="sxs-lookup"><span data-stu-id="4d5a7-103">A procedure is called with a [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) argument of a different type than that of its corresponding parameter.</span></span>  
  
 <span data-ttu-id="4d5a7-104">Bir bağımsız değişken geçirirseniz `ByRef`, Visual Basic bazen kopyalar bağımsız değişken değeri bir başvuru geçirme yerine yordamı yerel bir değişkende içine.</span><span class="sxs-lookup"><span data-stu-id="4d5a7-104">If you pass an argument `ByRef`, Visual Basic sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="4d5a7-105">Yordamın geri döndüğünde, böyle bir durumda, Visual Basic sonra yerel değişken değerini geri çağıran kodu değişkeninde kopyalamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4d5a7-105">In such a case, when the procedure returns, Visual Basic must then copy the local variable value back into the argument in the calling code.</span></span>  
  
 <span data-ttu-id="4d5a7-106">Varsa bir `ByRef` bağımsız değişken değeri yordama kopyalanır ve bağımsız değişkeni ve parametre aynı tür dönüştürme gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="4d5a7-106">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="4d5a7-107">Ancak türleri farklıysa, Visual Basic her iki yönde de dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4d5a7-107">But if the types are different, Visual Basic must convert in both directions.</span></span> <span data-ttu-id="4d5a7-108">Kullanamadığından `CType` veya diğer dönüşüm anahtar sözcükleri bir yordam bağımsız değişkenini veya parametresi, bu tür dönüştürme olan her zaman örtük.</span><span class="sxs-lookup"><span data-stu-id="4d5a7-108">Because you cannot use `CType` or any of the other conversion keywords on a procedure argument or parameter, such a conversion is always implicit.</span></span>  
  
 <span data-ttu-id="4d5a7-109">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="4d5a7-109">By default, this message is a warning.</span></span> <span data-ttu-id="4d5a7-110">Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="4d5a7-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="4d5a7-111">**Hata Kimliği:** BC41999</span><span class="sxs-lookup"><span data-stu-id="4d5a7-111">**Error ID:** BC41999</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4d5a7-112">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="4d5a7-112">To correct this error</span></span>  
  
-   <span data-ttu-id="4d5a7-113">Mümkünse, Visual Basic herhangi bir dönüştürmeye gerçekleştirmeniz gereken şekilde aynı türden çağıran bir bağımsız değişken yordamı parametre olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="4d5a7-113">If possible, use a calling argument of the same type as the procedure parameter, so Visual Basic does not need to do any conversion.</span></span>  
  
-   <span data-ttu-id="4d5a7-114">Yordam bağımsız değişkeni çağrısı gerekiyorsa parametre türünden farklı yazın ancak gerekmez çağırma bağımsız değişkeni bir değer döndürmesi, olması için parametre tanımlayın [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) yerine `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="4d5a7-114">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) instead of `ByRef`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d5a7-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4d5a7-115">See Also</span></span>  
 [<span data-ttu-id="4d5a7-116">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="4d5a7-116">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="4d5a7-117">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="4d5a7-117">Procedure Parameters and Arguments</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="4d5a7-118">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="4d5a7-118">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="4d5a7-119">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="4d5a7-119">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
