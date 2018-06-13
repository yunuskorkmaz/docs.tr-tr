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
ms.openlocfilehash: 6e8d1178398711226b88fee7e6defd5162b91fcb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649197"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a><span data-ttu-id="d38db-102">Nasıl yapılır: Bir Değişkenin Kapsamını Denetleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d38db-102">How to: Control the Scope of a Variable (Visual Basic)</span></span>
<span data-ttu-id="d38db-103">Bir değişken olarak normalde *kapsam*, veya içinde bildirdiğiniz, bölge boyunca, başvuru için görünür.</span><span class="sxs-lookup"><span data-stu-id="d38db-103">Normally, a variable is in *scope*, or visible for reference, throughout the region in which you declare it.</span></span> <span data-ttu-id="d38db-104">Bazı durumlarda, değişkeni 's *erişim düzeyine* kapsamını etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="d38db-104">In some cases, the variable's *access level* can influence its scope.</span></span>  
  
 <span data-ttu-id="d38db-105">Daha fazla bilgi için bkz: [Visual Basic'de kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span><span class="sxs-lookup"><span data-stu-id="d38db-105">For more information, see [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span></span>  
  
## <a name="scope-at-block-or-procedure-level"></a><span data-ttu-id="d38db-106">Blok veya yordam düzeyinde kapsamı</span><span class="sxs-lookup"><span data-stu-id="d38db-106">Scope at Block or Procedure Level</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a><span data-ttu-id="d38db-107">Bir değişken yalnızca bir bloğu içinde görünür hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="d38db-107">To make a variable visible only within a block</span></span>  
  
-   <span data-ttu-id="d38db-108">Yer [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) başlatmak ve bu bloğunun bildirim deyimleri arasında örneğin sonlandırma arasında bir değişken `For` ve `Next` bilgilerinin bir `For` döngü.</span><span class="sxs-lookup"><span data-stu-id="d38db-108">Place the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) for the variable between the initiating and terminating declaration statements of that block, for example between the `For` and `Next` statements of a `For` loop.</span></span>  
  
     <span data-ttu-id="d38db-109">Yalnızca değişken bloğu içinde başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d38db-109">You can refer to the variable only from within the block.</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a><span data-ttu-id="d38db-110">Bir değişken yalnızca bir yordam içinde görünür hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="d38db-110">To make a variable visible only within a procedure</span></span>  
  
-   <span data-ttu-id="d38db-111">Yer `Dim` yordam içindeki ancak herhangi bir bloğuna dışında değişken bildirimi (gibi bir `With`... `End With` blok).</span><span class="sxs-lookup"><span data-stu-id="d38db-111">Place the `Dim` statement for the variable inside the procedure but outside any block (such as a `With`...`End With` block).</span></span>  
  
     <span data-ttu-id="d38db-112">Yalnızca değişken yordamda bulunan tüm bloğunun dahil olmak üzere bu yordamı içinde başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d38db-112">You can refer to the variable only from within the procedure, including inside any block contained in the procedure.</span></span>  
  
## <a name="scope-at-module-or-namespace-level"></a><span data-ttu-id="d38db-113">Modül veya Namespace düzeyinde kapsamı</span><span class="sxs-lookup"><span data-stu-id="d38db-113">Scope at Module or Namespace Level</span></span>  
 <span data-ttu-id="d38db-114">Tek ifadeli kolaylık sağlamak için *modül düzeyi* modüller, sınıflar ve yapılar için eşit oranda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d38db-114">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="d38db-115">Modül düzeyi değişkeni erişim düzeyini kapsamı belirler.</span><span class="sxs-lookup"><span data-stu-id="d38db-115">The access level of a module level variable determines its scope.</span></span> <span data-ttu-id="d38db-116">Modül, sınıf veya yapı içeren ad alanı kapsamı de etkiler.</span><span class="sxs-lookup"><span data-stu-id="d38db-116">The namespace that contains the module, class, or structure also influences the scope.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a><span data-ttu-id="d38db-117">Bir değişken modülü, sınıf veya yapı boyunca görünür hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="d38db-117">To make a variable visible throughout a module, class, or structure</span></span>  
  
1.  <span data-ttu-id="d38db-118">Yer `Dim` modülü, sınıf veya yapı içinde ancak herhangi bir yordam dışında değişken bildirimi.</span><span class="sxs-lookup"><span data-stu-id="d38db-118">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="d38db-119">Dahil [özel](../../../../visual-basic/language-reference/modifiers/private.md) anahtar sözcük `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="d38db-119">Include the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
3.  <span data-ttu-id="d38db-120">Modül, sınıf veya yapı içinde istediğiniz yere değiştirebilir, ancak değişkeninden başvurabilirsiniz onu dışında.</span><span class="sxs-lookup"><span data-stu-id="d38db-120">You can refer to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a><span data-ttu-id="d38db-121">Bir değişkenin bir ad alanı boyunca görünür hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="d38db-121">To make a variable visible throughout a namespace</span></span>  
  
1.  <span data-ttu-id="d38db-122">Yer `Dim` modülü, sınıf veya yapı içinde ancak herhangi bir yordam dışında değişken bildirimi.</span><span class="sxs-lookup"><span data-stu-id="d38db-122">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="d38db-123">Dahil [arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md) veya [ortak](../../../../visual-basic/language-reference/modifiers/public.md) anahtar sözcük `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="d38db-123">Include the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) or [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
3.  <span data-ttu-id="d38db-124">Her yerden değişkenini ifade edebilir modülü, sınıf veya yapı içeren ad alanı içinde.</span><span class="sxs-lookup"><span data-stu-id="d38db-124">You can refer to the variable from anywhere within the namespace containing the module, class, or structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d38db-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="d38db-125">Example</span></span>  
 <span data-ttu-id="d38db-126">Aşağıdaki örnek modülü düzeyinde bir değişkeni bildirir ve modüldeki koduna görünürlüğü sınırlar.</span><span class="sxs-lookup"><span data-stu-id="d38db-126">The following example declares a variable at module level and limits its visibility to code within the module.</span></span>  
  
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
  
 <span data-ttu-id="d38db-127">Yukarıdaki örnekte tüm yordamları tanımlanan modülünde `demonstrateScope` başvurabilirsiniz `String` değişkeni `strMsg`.</span><span class="sxs-lookup"><span data-stu-id="d38db-127">In the preceding example, all the procedures defined in module `demonstrateScope` can refer to the `String` variable `strMsg`.</span></span> <span data-ttu-id="d38db-128">Zaman `usePrivateVariable` yordam çağrıldığında, dize değişkenine içeriğini görüntüler `strMsg` iletişim kutusunda.</span><span class="sxs-lookup"><span data-stu-id="d38db-128">When the `usePrivateVariable` procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>  
  
 <span data-ttu-id="d38db-129">Önceki örnekte, dize değişkenine için aşağıdaki değişiklikle birlikte `strMsg` için ad alanı bildiriminden başka bir yerindeki kodu tarafından başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="d38db-129">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>  
  
```  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a><span data-ttu-id="d38db-130">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="d38db-130">Robust Programming</span></span>  
 <span data-ttu-id="d38db-131">Daha dar bir değişkenin kapsamını, yanlışlıkla aynı ada sahip başka bir değişken yerine başvuruda için sahip kesintilerinden.</span><span class="sxs-lookup"><span data-stu-id="d38db-131">The narrower the scope of a variable, the fewer opportunities you have for accidentally referring to it in place of another variable with the same name.</span></span> <span data-ttu-id="d38db-132">Başvuru eşleşen sorunları en aza indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d38db-132">You can also minimize problems of reference matching.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="d38db-133">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="d38db-133">.NET Framework Security</span></span>  
 <span data-ttu-id="d38db-134">Daha dar bir değişkenin kapsamını, kötü amaçlı kod hatalı yapabilirsiniz küçük büyük olasılıkla bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="d38db-134">The narrower the scope of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d38db-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d38db-135">See Also</span></span>  
 [<span data-ttu-id="d38db-136">Visual Basic'de kapsam</span><span class="sxs-lookup"><span data-stu-id="d38db-136">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [<span data-ttu-id="d38db-137">Visual Basic'de ömür</span><span class="sxs-lookup"><span data-stu-id="d38db-137">Lifetime in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [<span data-ttu-id="d38db-138">Visual Basic'de erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="d38db-138">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="d38db-139">Değişkenler</span><span class="sxs-lookup"><span data-stu-id="d38db-139">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [<span data-ttu-id="d38db-140">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="d38db-140">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="d38db-141">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="d38db-141">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
