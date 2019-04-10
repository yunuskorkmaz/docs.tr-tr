---
title: 'Nasıl yapılır: (Visual Basic) bir değişkenin kapsamını denetleme'
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
ms.openlocfilehash: 24a7ae3b8f3400beeaedb20ea6352ea44bdb7597
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59324324"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a><span data-ttu-id="0e6bc-102">Nasıl yapılır: (Visual Basic) bir değişkenin kapsamını denetleme</span><span class="sxs-lookup"><span data-stu-id="0e6bc-102">How to: Control the Scope of a Variable (Visual Basic)</span></span>
<span data-ttu-id="0e6bc-103">Normalde, içinde bir değişkeni olduğunu *kapsam*, ya da, bildirdiğiniz, bölge, başvuru için görünür.</span><span class="sxs-lookup"><span data-stu-id="0e6bc-103">Normally, a variable is in *scope*, or visible for reference, throughout the region in which you declare it.</span></span> <span data-ttu-id="0e6bc-104">Bazı durumlarda, değişken 's *erişim düzeyi* kapsamını etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="0e6bc-104">In some cases, the variable's *access level* can influence its scope.</span></span>  
  
 <span data-ttu-id="0e6bc-105">Daha fazla bilgi için [Visual Basic'de kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span><span class="sxs-lookup"><span data-stu-id="0e6bc-105">For more information, see [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span></span>  
  
## <a name="scope-at-block-or-procedure-level"></a><span data-ttu-id="0e6bc-106">Kapsamda blok veya yordam düzeyi</span><span class="sxs-lookup"><span data-stu-id="0e6bc-106">Scope at Block or Procedure Level</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a><span data-ttu-id="0e6bc-107">Bir değişken yalnızca bir blok içinde görünür hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="0e6bc-107">To make a variable visible only within a block</span></span>  
  
-   <span data-ttu-id="0e6bc-108">Bir yerde [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) başlatma ve bildirim deyimleri, bloğun başlangıcını arasında örneğin sonlandırma arasında değişken için `For` ve `Next` bilgilerinin bir `For` döngü.</span><span class="sxs-lookup"><span data-stu-id="0e6bc-108">Place the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) for the variable between the initiating and terminating declaration statements of that block, for example between the `For` and `Next` statements of a `For` loop.</span></span>  
  
     <span data-ttu-id="0e6bc-109">Yalnızca değişken bloğu içinde başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e6bc-109">You can refer to the variable only from within the block.</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a><span data-ttu-id="0e6bc-110">Bir değişken yalnızca bir yordam içinde görünür hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="0e6bc-110">To make a variable visible only within a procedure</span></span>  
  
-   <span data-ttu-id="0e6bc-111">Bir yerde `Dim` yordam içinde ancak herhangi bir blok dışındaki değişken bildirimi (gibi bir `With`... `End With` blok).</span><span class="sxs-lookup"><span data-stu-id="0e6bc-111">Place the `Dim` statement for the variable inside the procedure but outside any block (such as a `With`...`End With` block).</span></span>  
  
     <span data-ttu-id="0e6bc-112">İçinde yordamda bulunan herhangi bir bloğu içinde dahil olmak üzere bu yordamı yalnızca değişkene başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e6bc-112">You can refer to the variable only from within the procedure, including inside any block contained in the procedure.</span></span>  
  
## <a name="scope-at-module-or-namespace-level"></a><span data-ttu-id="0e6bc-113">Modül veya Namespace düzeyinde kapsamı</span><span class="sxs-lookup"><span data-stu-id="0e6bc-113">Scope at Module or Namespace Level</span></span>  
 <span data-ttu-id="0e6bc-114">Kolaylık sağlamak adına, tek ifadeli *modül düzeyi* modülleri, sınıflar ve yapılar için eşit oranda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0e6bc-114">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="0e6bc-115">Modül düzeyi değişkeni erişim düzeyini kapsamı belirler.</span><span class="sxs-lookup"><span data-stu-id="0e6bc-115">The access level of a module level variable determines its scope.</span></span> <span data-ttu-id="0e6bc-116">Modül, sınıf veya yapı içeren ad uzayı kapsam da etkiler.</span><span class="sxs-lookup"><span data-stu-id="0e6bc-116">The namespace that contains the module, class, or structure also influences the scope.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a><span data-ttu-id="0e6bc-117">Bir değişken bir modül, sınıf veya yapı içinde görünür hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="0e6bc-117">To make a variable visible throughout a module, class, or structure</span></span>  
  
1. <span data-ttu-id="0e6bc-118">Bir yerde `Dim` modülü, sınıf veya yapı içinde ancak her türlü yordam dışındaki değişken bildirimi.</span><span class="sxs-lookup"><span data-stu-id="0e6bc-118">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="0e6bc-119">Dahil [özel](../../../../visual-basic/language-reference/modifiers/private.md) anahtar sözcüğünü `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="0e6bc-119">Include the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="0e6bc-120">Modül, sınıf veya yapı içinde herhangi bir yere değiştirebilir, ancak değişkeninden başvurabilirsiniz dışı.</span><span class="sxs-lookup"><span data-stu-id="0e6bc-120">You can refer to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a><span data-ttu-id="0e6bc-121">Bir değişken bir isim uzayı boyunca görünür hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="0e6bc-121">To make a variable visible throughout a namespace</span></span>  
  
1. <span data-ttu-id="0e6bc-122">Bir yerde `Dim` modülü, sınıf veya yapı içinde ancak her türlü yordam dışındaki değişken bildirimi.</span><span class="sxs-lookup"><span data-stu-id="0e6bc-122">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="0e6bc-123">Dahil [arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md) veya [genel](../../../../visual-basic/language-reference/modifiers/public.md) anahtar sözcüğünü `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="0e6bc-123">Include the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) or [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="0e6bc-124">Her yerden değişkene başvurabilirsiniz modül, sınıf veya yapı içeren ad alanı içinde.</span><span class="sxs-lookup"><span data-stu-id="0e6bc-124">You can refer to the variable from anywhere within the namespace containing the module, class, or structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e6bc-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="0e6bc-125">Example</span></span>  
 <span data-ttu-id="0e6bc-126">Aşağıdaki örnek, Modül düzeyinde bir değişkeni bildirir ve kod modülündeki görünürlüğü sınırlar.</span><span class="sxs-lookup"><span data-stu-id="0e6bc-126">The following example declares a variable at module level and limits its visibility to code within the module.</span></span>  
  
```  
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
  
 <span data-ttu-id="0e6bc-127">Önceki örnekte, tüm yordamları modülde tanımlanan `demonstrateScope` başvurabilir `String` değişkeni `strMsg`.</span><span class="sxs-lookup"><span data-stu-id="0e6bc-127">In the preceding example, all the procedures defined in module `demonstrateScope` can refer to the `String` variable `strMsg`.</span></span> <span data-ttu-id="0e6bc-128">Zaman `usePrivateVariable` yordamı çağrılır, string değişkeni içeriğini görüntüler `strMsg` iletişim kutusunda.</span><span class="sxs-lookup"><span data-stu-id="0e6bc-128">When the `usePrivateVariable` procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>  
  
 <span data-ttu-id="0e6bc-129">Önceki örnekte, dize değişkeni için aşağıdaki değişikliği ile `strMsg` kod bildiriminden ad alanındaki herhangi bir ifade.</span><span class="sxs-lookup"><span data-stu-id="0e6bc-129">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>  
  
```  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a><span data-ttu-id="0e6bc-130">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="0e6bc-130">Robust Programming</span></span>  
 <span data-ttu-id="0e6bc-131">Dar bir değişkenin kapsamını, yanlışlıkla aynı ada sahip başka bir değişken yerine başvuruda için sahip olduğunuz kesintilerinden.</span><span class="sxs-lookup"><span data-stu-id="0e6bc-131">The narrower the scope of a variable, the fewer opportunities you have for accidentally referring to it in place of another variable with the same name.</span></span> <span data-ttu-id="0e6bc-132">Başvuru eşleşen sorunlarını en aza indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e6bc-132">You can also minimize problems of reference matching.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="0e6bc-133">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="0e6bc-133">.NET Framework Security</span></span>  
 <span data-ttu-id="0e6bc-134">Kötü amaçlı kod hatalı yapabileceğiniz küçük olasılığını daha dar bir değişkenin kapsamını, bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="0e6bc-134">The narrower the scope of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e6bc-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e6bc-135">See also</span></span>

- [<span data-ttu-id="0e6bc-136">Visual Basic'de Kapsam</span><span class="sxs-lookup"><span data-stu-id="0e6bc-136">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [<span data-ttu-id="0e6bc-137">Visual Basic'de Ömür</span><span class="sxs-lookup"><span data-stu-id="0e6bc-137">Lifetime in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="0e6bc-138">Visual Basic'de erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="0e6bc-138">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="0e6bc-139">Değişkenler</span><span class="sxs-lookup"><span data-stu-id="0e6bc-139">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [<span data-ttu-id="0e6bc-140">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="0e6bc-140">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="0e6bc-141">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="0e6bc-141">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
