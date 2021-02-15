---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bağımsız değişkeni değere göre geçirilecek şekilde zorlama (Visual Basic)'
title: 'Nasıl yapılır: Bağımsız Değişkeni Değere Göre Geçirilecek Şekilde Zorlama'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], in parentheses
- procedure arguments [Visual Basic], in parentheses
- arguments [Visual Basic], changing value
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
ms.openlocfilehash: 471ddbf8993ad671dc4285729a11f5b17a5b19dc
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475428"
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a><span data-ttu-id="76d5f-103">Nasıl yapılır: Bağımsız Değişkeni Değere Göre Geçirilecek Şekilde Zorlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76d5f-103">How to: Force an Argument to Be Passed by Value (Visual Basic)</span></span>

<span data-ttu-id="76d5f-104">Yordam bildirimi, geçen mekanizmayı belirler.</span><span class="sxs-lookup"><span data-stu-id="76d5f-104">The procedure declaration determines the passing mechanism.</span></span> <span data-ttu-id="76d5f-105">Bir parametre [ByRef](../../../language-reference/modifiers/byref.md)olarak bildirilirse, Visual Basic karşılık gelen bağımsız değişkeni başvuruya göre geçmesini bekler.</span><span class="sxs-lookup"><span data-stu-id="76d5f-105">If a parameter is declared [ByRef](../../../language-reference/modifiers/byref.md), Visual Basic expects to pass the corresponding argument by reference.</span></span> <span data-ttu-id="76d5f-106">Bu yordam, çağıran koddaki bağımsız değişkenin temelindeki programlama öğesinin değerini değiştirmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="76d5f-106">This allows the procedure to change the value of the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="76d5f-107">Temel alınan öğeyi bu değişikliğe karşı korumak istiyorsanız `ByRef` bağımsız değişken adını parantez içine alarak yordam çağrısındaki geçen mekanizmayı geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76d5f-107">If you wish to protect the underlying element against such change, you can override the `ByRef` passing mechanism in the procedure call by enclosing the argument name in parentheses.</span></span> <span data-ttu-id="76d5f-108">Bu parantezler, çağrısındaki bağımsız değişken listesini çevreleyen parantezler için de ek olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="76d5f-108">These parentheses are in addition to the parentheses enclosing the argument list in the call.</span></span>  
  
 <span data-ttu-id="76d5f-109">Çağıran kod bir [ByVal](../../../language-reference/modifiers/byval.md) mekanizmasını geçersiz kılamaz.</span><span class="sxs-lookup"><span data-stu-id="76d5f-109">The calling code cannot override a [ByVal](../../../language-reference/modifiers/byval.md) mechanism.</span></span>  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a><span data-ttu-id="76d5f-110">Bir bağımsız değişkenin değere göre geçirilmesini zorlamak için</span><span class="sxs-lookup"><span data-stu-id="76d5f-110">To force an argument to be passed by value</span></span>  
  
- <span data-ttu-id="76d5f-111">Yordamda karşılık gelen parametre bildirilirse `ByVal` , ek adımlar uygulamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="76d5f-111">If the corresponding parameter is declared `ByVal` in the procedure, you do not need to take any additional steps.</span></span> <span data-ttu-id="76d5f-112">Visual Basic, zaten bağımsız değişkeni değere göre geçmesini bekliyor.</span><span class="sxs-lookup"><span data-stu-id="76d5f-112">Visual Basic already expects to pass the argument by value.</span></span>  
  
- <span data-ttu-id="76d5f-113">Yordamda karşılık gelen parametre bildirilirse `ByRef` , bağımsız değişkeni yordam çağrısında parantez içine alın.</span><span class="sxs-lookup"><span data-stu-id="76d5f-113">If the corresponding parameter is declared `ByRef` in the procedure, enclose the argument in parentheses in the procedure call.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76d5f-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="76d5f-114">Example</span></span>  

 <span data-ttu-id="76d5f-115">Aşağıdaki örnek bir `ByRef` parametre bildirimini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="76d5f-115">The following example overrides a `ByRef` parameter declaration.</span></span> <span data-ttu-id="76d5f-116">Zorlayan çağrıda `ByVal` , iki parantez düzeyini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="76d5f-116">In the call that forces `ByVal`, note the two levels of parentheses.</span></span>  
  
 [!code-vb[VbVbcnProcedures#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#39)]  
  
 [!code-vb[VbVbcnProcedures#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#40)]  
  
 <span data-ttu-id="76d5f-117">`str`Bağımsız değişken listesi içinde fazladan parantezler içine geçirildiğinde `setNewString` yordam, çağıran koddaki değerini değiştiremez ve `MsgBox` "bir ByVal geçirildiğinde değiştirilemez" şeklinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="76d5f-117">When `str` is enclosed in extra parentheses within the argument list, the `setNewString` procedure cannot change its value in the calling code, and `MsgBox` displays "Cannot be replaced if passed ByVal".</span></span> <span data-ttu-id="76d5f-118">`str`Ek parantezler içine alınmayan yordam bunu değiştirebilir ve `MsgBox` "ınString bağımsız değişkeni için yeni bir değer" görüntüler.</span><span class="sxs-lookup"><span data-stu-id="76d5f-118">When `str` is not enclosed in extra parentheses, the procedure can change it, and `MsgBox` displays "This is a new value for the inString argument."</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="76d5f-119">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="76d5f-119">Compile the code</span></span>  

 <span data-ttu-id="76d5f-120">Bir değişkeni başvuruya göre geçirdiğinizde, `ByRef` Bu mekanizmayı belirtmek için anahtar sözcüğünü kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="76d5f-120">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="76d5f-121">Visual Basic varsayılan değeri, bağımsız değişkenleri değere göre geçirmektir.</span><span class="sxs-lookup"><span data-stu-id="76d5f-121">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="76d5f-122">Ancak, her bir belirtilen parametreye ilişkin [ByVal](../../../language-reference/modifiers/byval.md) veya [ByRef](../../../language-reference/modifiers/byref.md) anahtar sözcüğünü eklemek iyi bir programlama uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="76d5f-122">However, it is good programming practice to include either the [ByVal](../../../language-reference/modifiers/byval.md) or [ByRef](../../../language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="76d5f-123">Bu, kodunuzun okunmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="76d5f-123">This makes your code easier to read.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="76d5f-124">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="76d5f-124">Robust Programming</span></span>  

 <span data-ttu-id="76d5f-125">Bir yordam [ByRef](../../../language-reference/modifiers/byref.md)parametresini bildiriyorsa, kodun doğru yürütülmesi, çağıran kodda temel alınan öğeyi değiştirebilmeyle ilgili olarak değişebilir.</span><span class="sxs-lookup"><span data-stu-id="76d5f-125">If a procedure declares a parameter [ByRef](../../../language-reference/modifiers/byref.md), the correct execution of the code might depend on being able to change the underlying element in the calling code.</span></span> <span data-ttu-id="76d5f-126">Çağıran kod, bağımsız değişkeni parantez içine alarak bu çağıran mekanizmayı geçersiz kılıyorsa veya değiştirilemeyen bir bağımsız değişken geçirirse yordam, temel alınan öğeyi değiştiremez.</span><span class="sxs-lookup"><span data-stu-id="76d5f-126">If the calling code overrides this calling mechanism by enclosing the argument in parentheses, or if it passes a nonmodifiable argument, the procedure cannot change the underlying element.</span></span> <span data-ttu-id="76d5f-127">Bu, çağıran kodda beklenmeyen sonuçlara neden olabilirler.</span><span class="sxs-lookup"><span data-stu-id="76d5f-127">This might produce unexpected results in the calling code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="76d5f-128">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="76d5f-128">.NET Framework Security</span></span>  

 <span data-ttu-id="76d5f-129">Bir yordamın, çağıran koddaki bağımsız değişkenin temelindeki değeri değiştirmesine izin vermek için her zaman potansiyel bir risk vardır.</span><span class="sxs-lookup"><span data-stu-id="76d5f-129">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="76d5f-130">Bu değerin değiştirilmesini beklediğinizden ve kullanılmadan önce geçerliliği göz önünde denetlediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="76d5f-130">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76d5f-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76d5f-131">See also</span></span>

- [<span data-ttu-id="76d5f-132">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="76d5f-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="76d5f-133">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="76d5f-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="76d5f-134">Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme</span><span class="sxs-lookup"><span data-stu-id="76d5f-134">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="76d5f-135">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="76d5f-135">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="76d5f-136">Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="76d5f-136">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="76d5f-137">Değere ve Başvuruya Göre Bağımsız Değişken Geçirme Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="76d5f-137">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="76d5f-138">Nasıl yapılır: Bir Yordam Bağımsız Değişkeninin Değerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="76d5f-138">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="76d5f-139">Nasıl yapılır: Bir Yordam Bağımsız Değişkenini Değer Değişikliklerine Karşı Koruma</span><span class="sxs-lookup"><span data-stu-id="76d5f-139">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="76d5f-140">Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="76d5f-140">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="76d5f-141">Değer türleri ve başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="76d5f-141">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
