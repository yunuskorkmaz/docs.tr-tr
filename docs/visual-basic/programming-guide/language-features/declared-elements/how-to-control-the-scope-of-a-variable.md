---
title: 'Nasıl yapılır: Bir Değişkenin Kapsamını Denetleme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], scope
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- variables [Visual Basic], visibility
- scope [Visual Basic], declared elements
- scope [Visual Basic], variables
- scope [Visual Basic], Visual Basic
- declared elements [Visual Basic], visibility
- visibility [Visual Basic], variables
ms.assetid: 44b7f62a-cb5c-4d50-bce9-60ae68f87072
ms.openlocfilehash: 23a10bd2d6c0c9f3a13bff864559460c48927e01
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582610"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a><span data-ttu-id="fbcaa-102">Nasıl yapılır: Bir Değişkenin Kapsamını Denetleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fbcaa-102">How to: Control the Scope of a Variable (Visual Basic)</span></span>
<span data-ttu-id="fbcaa-103">Normalde, bir değişken *kapsam*içinde veya başvuru için görünür, burada, bildirdiğiniz bölge boyunca olur.</span><span class="sxs-lookup"><span data-stu-id="fbcaa-103">Normally, a variable is in *scope*, or visible for reference, throughout the region in which you declare it.</span></span> <span data-ttu-id="fbcaa-104">Bazı durumlarda, değişkenin *erişim düzeyi* kapsamını etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="fbcaa-104">In some cases, the variable's *access level* can influence its scope.</span></span>  
  
 <span data-ttu-id="fbcaa-105">Daha fazla bilgi için [Visual Basic kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="fbcaa-105">For more information, see [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span></span>  
  
## <a name="scope-at-block-or-procedure-level"></a><span data-ttu-id="fbcaa-106">Blok veya yordam düzeyindeki kapsam</span><span class="sxs-lookup"><span data-stu-id="fbcaa-106">Scope at Block or Procedure Level</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a><span data-ttu-id="fbcaa-107">Bir değişkeni yalnızca bir blok içinde görünür hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="fbcaa-107">To make a variable visible only within a block</span></span>  
  
- <span data-ttu-id="fbcaa-108">Bir `For` döngüsünün `For` ve `Next` deyimleri arasında örneğin, bu bloğun başlatma ve sonlandırma bildirimi deyimleri arasına, değişken için [Dim deyimini](../../../../visual-basic/language-reference/statements/dim-statement.md) yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="fbcaa-108">Place the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) for the variable between the initiating and terminating declaration statements of that block, for example between the `For` and `Next` statements of a `For` loop.</span></span>  
  
     <span data-ttu-id="fbcaa-109">Değişkenine yalnızca bloğun içinden başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbcaa-109">You can refer to the variable only from within the block.</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a><span data-ttu-id="fbcaa-110">Bir değişkeni yalnızca bir yordam içinde görünür hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="fbcaa-110">To make a variable visible only within a procedure</span></span>  
  
- <span data-ttu-id="fbcaa-111">Değişken için `Dim` ifadesini yordamın içine yerleştirin, ancak herhangi bir bloğun dışında (örneğin, bir `With`... `End With` bloğu).</span><span class="sxs-lookup"><span data-stu-id="fbcaa-111">Place the `Dim` statement for the variable inside the procedure but outside any block (such as a `With`...`End With` block).</span></span>  
  
     <span data-ttu-id="fbcaa-112">Yordamda yer alan herhangi bir bloğun içinde olduğu gibi yalnızca yordamın içinden değişkene başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbcaa-112">You can refer to the variable only from within the procedure, including inside any block contained in the procedure.</span></span>  
  
## <a name="scope-at-module-or-namespace-level"></a><span data-ttu-id="fbcaa-113">Modül veya ad alanı düzeyinde kapsam</span><span class="sxs-lookup"><span data-stu-id="fbcaa-113">Scope at Module or Namespace Level</span></span>  
 <span data-ttu-id="fbcaa-114">Kolaylık olması için, tek vadeli *Modül düzeyi* modüller, sınıflar ve yapılar için eşit oranda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="fbcaa-114">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="fbcaa-115">Modül düzeyi değişkeninin erişim düzeyi kapsamını belirler.</span><span class="sxs-lookup"><span data-stu-id="fbcaa-115">The access level of a module level variable determines its scope.</span></span> <span data-ttu-id="fbcaa-116">Modül, sınıf veya yapıyı içeren ad alanı da kapsamı etkiler.</span><span class="sxs-lookup"><span data-stu-id="fbcaa-116">The namespace that contains the module, class, or structure also influences the scope.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a><span data-ttu-id="fbcaa-117">Bir değişkeni bir modül, sınıf veya yapı genelinde görünür hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="fbcaa-117">To make a variable visible throughout a module, class, or structure</span></span>  
  
1. <span data-ttu-id="fbcaa-118">Değişken için `Dim` ifadesini modül, sınıf veya yapının içine, ancak herhangi bir yordamın dışına yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="fbcaa-118">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="fbcaa-119">@No__t_1 ifadesine [Private](../../../../visual-basic/language-reference/modifiers/private.md) anahtar sözcüğünü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fbcaa-119">Include the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="fbcaa-120">Değişkeni modülün, sınıfın veya yapının içinden herhangi bir yerde, ancak dışından kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="fbcaa-120">You can refer to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a><span data-ttu-id="fbcaa-121">Bir değişkeni bir ad alanı boyunca görünür hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="fbcaa-121">To make a variable visible throughout a namespace</span></span>  
  
1. <span data-ttu-id="fbcaa-122">Değişken için `Dim` ifadesini modül, sınıf veya yapının içine, ancak herhangi bir yordamın dışına yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="fbcaa-122">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="fbcaa-123">@No__t_2 ifadesine [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) veya [Public](../../../../visual-basic/language-reference/modifiers/public.md) anahtar sözcüğünü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fbcaa-123">Include the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) or [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="fbcaa-124">Değişkeni, modül, sınıf veya yapıyı içeren ad alanı içinde herhangi bir yerden yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbcaa-124">You can refer to the variable from anywhere within the namespace containing the module, class, or structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbcaa-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="fbcaa-125">Example</span></span>  
 <span data-ttu-id="fbcaa-126">Aşağıdaki örnek modül düzeyinde bir değişken bildirir ve görünürlüğünü modül içindeki kodla sınırlandırır.</span><span class="sxs-lookup"><span data-stu-id="fbcaa-126">The following example declares a variable at module level and limits its visibility to code within the module.</span></span>  
  
```vb  
Module demonstrateScope  
    Private strMsg As String  
    Sub initializePrivateVariable()  
        strMsg = "This variable cannot be used outside this module."  
    End Sub  
    Sub usePrivateVariable()  
        MsgBox(strMsg)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="fbcaa-127">Yukarıdaki örnekte, `demonstrateScope` modülünde tanımlanan tüm yordamlar `String` değişkenine başvurabilir `strMsg`.</span><span class="sxs-lookup"><span data-stu-id="fbcaa-127">In the preceding example, all the procedures defined in module `demonstrateScope` can refer to the `String` variable `strMsg`.</span></span> <span data-ttu-id="fbcaa-128">@No__t_0 yordam çağrıldığında, `strMsg` dize değişkeninin içeriğini bir iletişim kutusunda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="fbcaa-128">When the `usePrivateVariable` procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>  
  
 <span data-ttu-id="fbcaa-129">Önceki örnekte yapılan aşağıdaki değişiklikle, dize değişkeni `strMsg`, bildiriminin ad alanı içinde herhangi bir yerde kodla başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="fbcaa-129">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>  
  
```vb  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a><span data-ttu-id="fbcaa-130">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="fbcaa-130">Robust Programming</span></span>  
 <span data-ttu-id="fbcaa-131">Bir değişkenin kapsamını daraltmak için, yanlışlıkla aynı ada sahip başka bir değişken yerine buna başvuran daha az fırsat vardır.</span><span class="sxs-lookup"><span data-stu-id="fbcaa-131">The narrower the scope of a variable, the fewer opportunities you have for accidentally referring to it in place of another variable with the same name.</span></span> <span data-ttu-id="fbcaa-132">Ayrıca, başvuru eşleştirmesinin sorunlarını da en aza indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbcaa-132">You can also minimize problems of reference matching.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="fbcaa-133">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="fbcaa-133">.NET Framework Security</span></span>  
 <span data-ttu-id="fbcaa-134">Bir değişkenin kapsamını daraltmak, kötü amaçlı kodun yanlış kullanımı olasılığını en kısa hale getirir.</span><span class="sxs-lookup"><span data-stu-id="fbcaa-134">The narrower the scope of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbcaa-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fbcaa-135">See also</span></span>

- [<span data-ttu-id="fbcaa-136">Visual Basic kapsam</span><span class="sxs-lookup"><span data-stu-id="fbcaa-136">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [<span data-ttu-id="fbcaa-137">Visual Basic ömrü</span><span class="sxs-lookup"><span data-stu-id="fbcaa-137">Lifetime in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="fbcaa-138">Visual Basic erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="fbcaa-138">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="fbcaa-139">Değişkenler</span><span class="sxs-lookup"><span data-stu-id="fbcaa-139">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [<span data-ttu-id="fbcaa-140">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="fbcaa-140">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="fbcaa-141">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="fbcaa-141">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
