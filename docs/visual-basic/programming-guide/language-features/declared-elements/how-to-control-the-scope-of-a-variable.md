---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: bir değişkenin kapsamını denetleme (Visual Basic)'
title: 'Nasıl yapılır: Bir Değişkenin Kapsamını Denetleme'
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
ms.openlocfilehash: c6da599f76883cba545efbdf9570aa05770602a2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429877"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a><span data-ttu-id="6d11d-103">Nasıl yapılır: Bir Değişkenin Kapsamını Denetleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d11d-103">How to: Control the Scope of a Variable (Visual Basic)</span></span>

<span data-ttu-id="6d11d-104">Normalde, bir değişken *kapsam* içinde veya başvuru için görünür, burada, bildirdiğiniz bölge boyunca olur.</span><span class="sxs-lookup"><span data-stu-id="6d11d-104">Normally, a variable is in *scope*, or visible for reference, throughout the region in which you declare it.</span></span> <span data-ttu-id="6d11d-105">Bazı durumlarda, değişkenin *erişim düzeyi* kapsamını etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="6d11d-105">In some cases, the variable's *access level* can influence its scope.</span></span>  
  
 <span data-ttu-id="6d11d-106">Daha fazla bilgi için [Visual Basic kapsam](scope.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="6d11d-106">For more information, see [Scope in Visual Basic](scope.md).</span></span>  
  
## <a name="scope-at-block-or-procedure-level"></a><span data-ttu-id="6d11d-107">Blok veya yordam düzeyindeki kapsam</span><span class="sxs-lookup"><span data-stu-id="6d11d-107">Scope at Block or Procedure Level</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a><span data-ttu-id="6d11d-108">Bir değişkeni yalnızca bir blok içinde görünür hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="6d11d-108">To make a variable visible only within a block</span></span>  
  
- <span data-ttu-id="6d11d-109">Değişken için [Dim deyimini](../../../language-reference/statements/dim-statement.md) , bu bloktaki başlatma ve sonlandırma bildirimi deyimleri arasına, örneğin `For` `Next` bir döngünün ve deyimleri arasına yerleştirin `For` .</span><span class="sxs-lookup"><span data-stu-id="6d11d-109">Place the [Dim Statement](../../../language-reference/statements/dim-statement.md) for the variable between the initiating and terminating declaration statements of that block, for example between the `For` and `Next` statements of a `For` loop.</span></span>  
  
     <span data-ttu-id="6d11d-110">Değişkenine yalnızca bloğun içinden başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d11d-110">You can refer to the variable only from within the block.</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a><span data-ttu-id="6d11d-111">Bir değişkeni yalnızca bir yordam içinde görünür hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="6d11d-111">To make a variable visible only within a procedure</span></span>  
  
- <span data-ttu-id="6d11d-112">`Dim`Değişkeninin ifadesini yordamın içine yerleştirin, ancak herhangi bir bloğun dışında (örneğin, `With` ... `End With` bloğu).</span><span class="sxs-lookup"><span data-stu-id="6d11d-112">Place the `Dim` statement for the variable inside the procedure but outside any block (such as a `With`...`End With` block).</span></span>  
  
     <span data-ttu-id="6d11d-113">Yordamda yer alan herhangi bir bloğun içinde olduğu gibi yalnızca yordamın içinden değişkene başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d11d-113">You can refer to the variable only from within the procedure, including inside any block contained in the procedure.</span></span>  
  
## <a name="scope-at-module-or-namespace-level"></a><span data-ttu-id="6d11d-114">Modül veya ad alanı düzeyinde kapsam</span><span class="sxs-lookup"><span data-stu-id="6d11d-114">Scope at Module or Namespace Level</span></span>  

 <span data-ttu-id="6d11d-115">Kolaylık olması için, tek vadeli *Modül düzeyi* modüller, sınıflar ve yapılar için eşit oranda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6d11d-115">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="6d11d-116">Modül düzeyi değişkeninin erişim düzeyi kapsamını belirler.</span><span class="sxs-lookup"><span data-stu-id="6d11d-116">The access level of a module level variable determines its scope.</span></span> <span data-ttu-id="6d11d-117">Modül, sınıf veya yapıyı içeren ad alanı da kapsamı etkiler.</span><span class="sxs-lookup"><span data-stu-id="6d11d-117">The namespace that contains the module, class, or structure also influences the scope.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a><span data-ttu-id="6d11d-118">Bir değişkeni bir modül, sınıf veya yapı genelinde görünür hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="6d11d-118">To make a variable visible throughout a module, class, or structure</span></span>  
  
1. <span data-ttu-id="6d11d-119">`Dim`Değişkenin ifadesini modül, sınıf veya yapının içine, ancak herhangi bir yordamın dışına yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="6d11d-119">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="6d11d-120">Deyimdeki [Private](../../../language-reference/modifiers/private.md) anahtar sözcüğünü ekleyin `Dim` .</span><span class="sxs-lookup"><span data-stu-id="6d11d-120">Include the [Private](../../../language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="6d11d-121">Değişkeni modülün, sınıfın veya yapının içinden herhangi bir yerde, ancak dışından kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="6d11d-121">You can refer to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a><span data-ttu-id="6d11d-122">Bir değişkeni bir ad alanı boyunca görünür hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="6d11d-122">To make a variable visible throughout a namespace</span></span>  
  
1. <span data-ttu-id="6d11d-123">`Dim`Değişkenin ifadesini modül, sınıf veya yapının içine, ancak herhangi bir yordamın dışına yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="6d11d-123">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="6d11d-124">İfadeye [Friend](../../../language-reference/modifiers/friend.md) veya [Public](../../../language-reference/modifiers/public.md) anahtar sözcüğünü ekleyin `Dim` .</span><span class="sxs-lookup"><span data-stu-id="6d11d-124">Include the [Friend](../../../language-reference/modifiers/friend.md) or [Public](../../../language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="6d11d-125">Değişkeni, modül, sınıf veya yapıyı içeren ad alanı içinde herhangi bir yerden yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d11d-125">You can refer to the variable from anywhere within the namespace containing the module, class, or structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d11d-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="6d11d-126">Example</span></span>  

 <span data-ttu-id="6d11d-127">Aşağıdaki örnek modül düzeyinde bir değişken bildirir ve görünürlüğünü modül içindeki kodla sınırlandırır.</span><span class="sxs-lookup"><span data-stu-id="6d11d-127">The following example declares a variable at module level and limits its visibility to code within the module.</span></span>  
  
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
  
 <span data-ttu-id="6d11d-128">Önceki örnekte, modülünde tanımlanan tüm yordamlar `demonstrateScope` `String` değişkenine başvurabilir `strMsg` .</span><span class="sxs-lookup"><span data-stu-id="6d11d-128">In the preceding example, all the procedures defined in module `demonstrateScope` can refer to the `String` variable `strMsg`.</span></span> <span data-ttu-id="6d11d-129">`usePrivateVariable`Yordam çağrıldığında, dize değişkeninin içeriğini `strMsg` bir iletişim kutusunda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6d11d-129">When the `usePrivateVariable` procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>  
  
 <span data-ttu-id="6d11d-130">Önceki örnekte yapılan aşağıdaki değişiklikle, dize değişkenine, `strMsg` bildiriminin ad alanı içinde herhangi bir yerde kod eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="6d11d-130">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>  
  
```vb  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a><span data-ttu-id="6d11d-131">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="6d11d-131">Robust Programming</span></span>  

 <span data-ttu-id="6d11d-132">Bir değişkenin kapsamını daraltmak için, yanlışlıkla aynı ada sahip başka bir değişken yerine buna başvuran daha az fırsat vardır.</span><span class="sxs-lookup"><span data-stu-id="6d11d-132">The narrower the scope of a variable, the fewer opportunities you have for accidentally referring to it in place of another variable with the same name.</span></span> <span data-ttu-id="6d11d-133">Ayrıca, başvuru eşleştirmesinin sorunlarını da en aza indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d11d-133">You can also minimize problems of reference matching.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="6d11d-134">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="6d11d-134">.NET Framework Security</span></span>  

 <span data-ttu-id="6d11d-135">Bir değişkenin kapsamını daraltmak, kötü amaçlı kodun yanlış kullanımı olasılığını en kısa hale getirir.</span><span class="sxs-lookup"><span data-stu-id="6d11d-135">The narrower the scope of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d11d-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d11d-136">See also</span></span>

- [<span data-ttu-id="6d11d-137">Visual Basic'de Kapsam</span><span class="sxs-lookup"><span data-stu-id="6d11d-137">Scope in Visual Basic</span></span>](scope.md)
- [<span data-ttu-id="6d11d-138">Visual Basic'de Ömür</span><span class="sxs-lookup"><span data-stu-id="6d11d-138">Lifetime in Visual Basic</span></span>](lifetime.md)
- [<span data-ttu-id="6d11d-139">Visual Basic erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="6d11d-139">Access levels in Visual Basic</span></span>](access-levels.md)
- [<span data-ttu-id="6d11d-140">Değişkenler</span><span class="sxs-lookup"><span data-stu-id="6d11d-140">Variables</span></span>](../variables/index.md)
- [<span data-ttu-id="6d11d-141">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="6d11d-141">Variable Declaration</span></span>](../variables/variable-declaration.md)
- [<span data-ttu-id="6d11d-142">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="6d11d-142">Dim Statement</span></span>](../../../language-reference/statements/dim-statement.md)
