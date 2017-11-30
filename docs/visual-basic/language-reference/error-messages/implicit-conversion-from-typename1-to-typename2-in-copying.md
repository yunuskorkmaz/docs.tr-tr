---
title: "Örtük dönüştürme &#39; &lt;typename1&gt;&#39; çok &#39;&lt; TypeName2&gt;&#39; değeri &#39; kopyalama ByRef &#39; Parametre &#39; &lt;parametername&gt;&#39; eşleşen bağımsız değişkene geri."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords: BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9e858b475a816a35d18822643de5a273abe28562
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="implicit-conversion-from-39lttypename1gt39-to-39lttypename2gt39-in-copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument"></a><span data-ttu-id="ffa58-102">Örtük dönüştürme &#39; &lt;typename1&gt;&#39; çok &#39;&lt; TypeName2&gt;&#39; değeri &#39; kopyalama ByRef &#39; Parametre &#39; &lt;parametername&gt;&#39; eşleşen bağımsız değişkene geri.</span><span class="sxs-lookup"><span data-stu-id="ffa58-102">Implicit conversion from &#39;&lt;typename1&gt;&#39; to &#39;&lt;typename2&gt;&#39; in copying the value of &#39;ByRef&#39; parameter &#39;&lt;parametername&gt;&#39; back to the matching argument.</span></span>
<span data-ttu-id="ffa58-103">Bir yordam ile adlı bir [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) bağımsız değişkeni, karşılık gelen bir parametre daha farklı bir türde.</span><span class="sxs-lookup"><span data-stu-id="ffa58-103">A procedure is called with a [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) argument of a different type than that of its corresponding parameter.</span></span>  
  
 <span data-ttu-id="ffa58-104">Bir bağımsız değişken geçirirseniz `ByRef`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] bazen bir başvuru geçirme yerine yordamdaki yerel bir değişken bağımsız değişken değeri kopyalar.</span><span class="sxs-lookup"><span data-stu-id="ffa58-104">If you pass an argument `ByRef`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="ffa58-105">Yordamın geri döndüğünde, böyle bir durumda, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] sonra yerel değişken değerini geri çağırma kodu değişkeninde kopyalamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ffa58-105">In such a case, when the procedure returns, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] must then copy the local variable value back into the argument in the calling code.</span></span>  
  
 <span data-ttu-id="ffa58-106">Varsa bir `ByRef` bağımsız değişken değeri yordama kopyalanır ve bağımsız değişkeni ve parametre aynı tür dönüştürme gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="ffa58-106">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="ffa58-107">Ancak türleri farklıysa [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] her iki yönde de dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ffa58-107">But if the types are different, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] must convert in both directions.</span></span> <span data-ttu-id="ffa58-108">Kullanamadığından `CType` veya diğer dönüşüm anahtar sözcükleri bir yordam bağımsız değişkenini veya parametresi, bu tür dönüştürme olan her zaman örtük.</span><span class="sxs-lookup"><span data-stu-id="ffa58-108">Because you cannot use `CType` or any of the other conversion keywords on a procedure argument or parameter, such a conversion is always implicit.</span></span>  
  
 <span data-ttu-id="ffa58-109">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="ffa58-109">By default, this message is a warning.</span></span> <span data-ttu-id="ffa58-110">Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="ffa58-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="ffa58-111">**Hata Kimliği:** BC41999</span><span class="sxs-lookup"><span data-stu-id="ffa58-111">**Error ID:** BC41999</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ffa58-112">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="ffa58-112">To correct this error</span></span>  
  
-   <span data-ttu-id="ffa58-113">Mümkünse, aynı türden çağıran bir bağımsız değişken yordamı parametre olarak kullanın [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] herhangi bir dönüştürmeye yapmak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ffa58-113">If possible, use a calling argument of the same type as the procedure parameter, so [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] does not need to do any conversion.</span></span>  
  
-   <span data-ttu-id="ffa58-114">Yordam bağımsız değişkeni çağrısı gerekiyorsa parametre türünden farklı yazın ancak gerekmez çağırma bağımsız değişkeni bir değer döndürmesi, olması için parametre tanımlayın [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) yerine `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="ffa58-114">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) instead of `ByRef`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffa58-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ffa58-115">See Also</span></span>  
 [<span data-ttu-id="ffa58-116">Yordamları</span><span class="sxs-lookup"><span data-stu-id="ffa58-116">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="ffa58-117">Parametreler ve bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="ffa58-117">Procedure Parameters and Arguments</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="ffa58-118">Bağımsız değişkenleri değere ve başvuruya göre geçirme</span><span class="sxs-lookup"><span data-stu-id="ffa58-118">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="ffa58-119">Örtük ve açık dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="ffa58-119">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
