---
title: Visual Basic'de Kapsam
ms.date: 07/20/2015
helpviewer_keywords:
- module scope [Visual Basic]
- scope [Visual Basic], levels
- module level
- procedures [Visual Basic], scope
- declared elements [Visual Basic], scope
- namespaces [Visual Basic], scope
- scope [Visual Basic], declared elements
- scope [Visual Basic], about scope
- levels of scope [Visual Basic]
- block scope [Visual Basic]
- scope [Visual Basic], Visual Basic
- procedure scope [Visual Basic]
ms.assetid: 208106fe-79c9-4eec-93c6-55f08548895f
ms.openlocfilehash: 38dd9d6d40780c25f06a35cf1ffbe4743b7da4a4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537255"
---
# <a name="scope-in-visual-basic"></a><span data-ttu-id="3aaee-102">Visual Basic'de Kapsam</span><span class="sxs-lookup"><span data-stu-id="3aaee-102">Scope in Visual Basic</span></span>
<span data-ttu-id="3aaee-103">*Kapsam* bildirilen bir öğenin adını nitelendirme veya aracılığıyla kullanılabilir hale getirme olmadan başvurduğu tüm kod kümesidir. bir [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="3aaee-103">The *scope* of a declared element is the set of all code that can refer to it without qualifying its name or making it available through an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="3aaee-104">Bir öğe kapsamı aşağıdaki düzeylerde birine sahip olabilir:</span><span class="sxs-lookup"><span data-stu-id="3aaee-104">An element can have scope at one of the following levels:</span></span>  
  
|<span data-ttu-id="3aaee-105">Düzey</span><span class="sxs-lookup"><span data-stu-id="3aaee-105">Level</span></span>|<span data-ttu-id="3aaee-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3aaee-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3aaee-107">Blok kapsamı</span><span class="sxs-lookup"><span data-stu-id="3aaee-107">Block scope</span></span>|<span data-ttu-id="3aaee-108">Yalnızca kod içinde kullanılabilir block bildirildiği içinde</span><span class="sxs-lookup"><span data-stu-id="3aaee-108">Available only within the code block in which it is declared</span></span>|  
|<span data-ttu-id="3aaee-109">Yordam kapsamı</span><span class="sxs-lookup"><span data-stu-id="3aaee-109">Procedure scope</span></span>|<span data-ttu-id="3aaee-110">Tüm kod içinde bildirildiği yordam içinde kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="3aaee-110">Available to all code within the procedure in which it is declared</span></span>|  
|<span data-ttu-id="3aaee-111">Modül kapsamı</span><span class="sxs-lookup"><span data-stu-id="3aaee-111">Module scope</span></span>|<span data-ttu-id="3aaee-112">Modül, sınıf veya yapı içinde bildirildiği tüm kod için kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="3aaee-112">Available to all code within the module, class, or structure in which it is declared</span></span>|  
|<span data-ttu-id="3aaee-113">Namespace kapsamı</span><span class="sxs-lookup"><span data-stu-id="3aaee-113">Namespace scope</span></span>|<span data-ttu-id="3aaee-114">İçinde bildirildiği ad alanındaki tüm kod için kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="3aaee-114">Available to all code in the namespace in which it is declared</span></span>|  
  
 <span data-ttu-id="3aaee-115">Bu düzeyde dar (blok) kapsam ilerlemesini geniş (ad), burada *kapsamdan* nitelik olmadan öğesine başvurabilir kod en küçük kümesini anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3aaee-115">These levels of scope progress from the narrowest (block) to the widest (namespace), where *narrowest scope* means the smallest set of code that can refer to the element without qualification.</span></span> <span data-ttu-id="3aaee-116">Daha fazla bilgi için bu sayfada "Kapsam düzeyleri" konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="3aaee-116">For more information, see "Levels of Scope" on this page.</span></span>  
  
## <a name="specifying-scope-and-defining-variables"></a><span data-ttu-id="3aaee-117">Kapsam belirleme ve değişkenleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="3aaee-117">Specifying Scope and Defining Variables</span></span>  
 <span data-ttu-id="3aaee-118">Bildirdiğinizde, bir öğenin kapsamını belirtin.</span><span class="sxs-lookup"><span data-stu-id="3aaee-118">You specify the scope of an element when you declare it.</span></span> <span data-ttu-id="3aaee-119">Kapsam aşağıdaki etkenlere bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="3aaee-119">The scope can depend on the following factors:</span></span>  
  
-   <span data-ttu-id="3aaee-120">Öğe bildirdiğiniz bölge (blok, yordam, modül, sınıf veya yapının)</span><span class="sxs-lookup"><span data-stu-id="3aaee-120">The region (block, procedure, module, class, or structure) in which you declare the element</span></span>  
  
-   <span data-ttu-id="3aaee-121">Öğenin bildirimi içeren ad alanı</span><span class="sxs-lookup"><span data-stu-id="3aaee-121">The namespace containing the element's declaration</span></span>  
  
-   <span data-ttu-id="3aaee-122">Öğe için bildirmek erişim düzeyi</span><span class="sxs-lookup"><span data-stu-id="3aaee-122">The access level you declare for the element</span></span>  
  
 <span data-ttu-id="3aaee-123">Aynı ada ancak farklı kapsam değişkenlerle belirlemekten tanımlarken kullanmak dikkat beklenmeyen sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="3aaee-123">Use care when you define variables with the same name but different scope, because doing so can lead to unexpected results.</span></span> <span data-ttu-id="3aaee-124">Daha fazla bilgi için [bildirilmiş öğelere başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="3aaee-124">For more information, see [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
## <a name="levels-of-scope"></a><span data-ttu-id="3aaee-125">Kapsam düzeyleri</span><span class="sxs-lookup"><span data-stu-id="3aaee-125">Levels of Scope</span></span>  
 <span data-ttu-id="3aaee-126">Bir programlama öğesi bildirdiğiniz bölge kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3aaee-126">A programming element is available throughout the region in which you declare it.</span></span> <span data-ttu-id="3aaee-127">Aynı bölgedeki tüm kod adıyla nitelemeden öğesine başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="3aaee-127">All code in the same region can refer to the element without qualifying its name.</span></span>  
  
### <a name="block-scope"></a><span data-ttu-id="3aaee-128">Blok kapsamı</span><span class="sxs-lookup"><span data-stu-id="3aaee-128">Block Scope</span></span>  
 <span data-ttu-id="3aaee-129">Bir blok başlatma ve sonlandırma aşağıdaki gibi bildirim deyimleri içine alınmış deyimleri kümesidir:</span><span class="sxs-lookup"><span data-stu-id="3aaee-129">A block is a set of statements enclosed within initiating and terminating declaration statements, such as the following:</span></span>  
  
-   <span data-ttu-id="3aaee-130">`Do` ve `Loop`</span><span class="sxs-lookup"><span data-stu-id="3aaee-130">`Do` and `Loop`</span></span>  
  
-   <span data-ttu-id="3aaee-131">`For` [`Each`] ve `Next`</span><span class="sxs-lookup"><span data-stu-id="3aaee-131">`For` [`Each`] and `Next`</span></span>  
  
-   <span data-ttu-id="3aaee-132">`If` ve `End If`</span><span class="sxs-lookup"><span data-stu-id="3aaee-132">`If` and `End If`</span></span>  
  
-   <span data-ttu-id="3aaee-133">`Select` ve `End Select`</span><span class="sxs-lookup"><span data-stu-id="3aaee-133">`Select` and `End Select`</span></span>  
  
-   <span data-ttu-id="3aaee-134">`SyncLock` ve `End SyncLock`</span><span class="sxs-lookup"><span data-stu-id="3aaee-134">`SyncLock` and `End SyncLock`</span></span>  
  
-   <span data-ttu-id="3aaee-135">`Try` ve `End Try`</span><span class="sxs-lookup"><span data-stu-id="3aaee-135">`Try` and `End Try`</span></span>  
  
-   <span data-ttu-id="3aaee-136">`While` ve `End While`</span><span class="sxs-lookup"><span data-stu-id="3aaee-136">`While` and `End While`</span></span>  
  
-   <span data-ttu-id="3aaee-137">`With` ve `End With`</span><span class="sxs-lookup"><span data-stu-id="3aaee-137">`With` and `End With`</span></span>  
  
 <span data-ttu-id="3aaee-138">Bir blok içinde bir değişken bildirirseniz, yalnızca bu blokta kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3aaee-138">If you declare a variable within a block, you can use it only within that block.</span></span> <span data-ttu-id="3aaee-139">Aşağıdaki örnekte, tam sayı değişkeni kapsamını `cube` arasında blok `If` ve `End If`, ve artık başvurabilirsiniz `cube` zaman Yürütme bloğunun dışına geçirir.</span><span class="sxs-lookup"><span data-stu-id="3aaee-139">In the following example, the scope of the integer variable `cube` is the block between `If` and `End If`, and you can no longer refer to `cube` when execution passes out of the block.</span></span>  
  
```  
If n < 1291 Then  
    Dim cube As Integer  
    cube = n ^ 3  
End If  
```  
  
> [!NOTE]
>  <span data-ttu-id="3aaee-140">Bir değişkenin kapsamını bir blokla sınırlı olsa bile, yaşam süresi hala tüm yordamın olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="3aaee-140">Even if the scope of a variable is limited to a block, its lifetime is still that of the entire procedure.</span></span> <span data-ttu-id="3aaee-141">Blok yordam sırasında birden çok kez girerseniz, her bir blok değişken önceki değerini korur.</span><span class="sxs-lookup"><span data-stu-id="3aaee-141">If you enter the block more than once during the procedure, each block variable retains its previous value.</span></span> <span data-ttu-id="3aaee-142">Böyle bir durumda beklenmeyen sonuçlardan kaçınmak için bloğun başlangıcında blok değişkenlerini başlatmak üzere akıllıca olur.</span><span class="sxs-lookup"><span data-stu-id="3aaee-142">To avoid unexpected results in such a case, it is wise to initialize block variables at the beginning of the block.</span></span>  
  
### <a name="procedure-scope"></a><span data-ttu-id="3aaee-143">Yordam kapsamı</span><span class="sxs-lookup"><span data-stu-id="3aaee-143">Procedure Scope</span></span>  
 <span data-ttu-id="3aaee-144">Bir yordam içinde bildirilen bir öğenin dışında bu yordamın kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="3aaee-144">An element declared within a procedure is not available outside that procedure.</span></span> <span data-ttu-id="3aaee-145">Yalnızca bildirimi içeren yordamı da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3aaee-145">Only the procedure that contains the declaration can use it.</span></span> <span data-ttu-id="3aaee-146">Bu düzeyde değişkenlerdir olarak da bilinen *yerel değişkenler*.</span><span class="sxs-lookup"><span data-stu-id="3aaee-146">Variables at this level are also known as *local variables*.</span></span> <span data-ttu-id="3aaee-147">Kendileriyle bildirin [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md)veya bu profiller olmadan [statik](../../../../visual-basic/language-reference/modifiers/static.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="3aaee-147">You declare them with the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md), with or without the [Static](../../../../visual-basic/language-reference/modifiers/static.md) keyword.</span></span>  
  
 <span data-ttu-id="3aaee-148">Yordam ve blok kapsamı yakından ilgili.</span><span class="sxs-lookup"><span data-stu-id="3aaee-148">Procedure and block scope are closely related.</span></span> <span data-ttu-id="3aaee-149">Bir yordam içinde ancak bu yordam herhangi bir bloğu dışında bir değişken bildirirseniz, değişken blok yordamın tamamını olduğu blok kapsamlı olarak düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3aaee-149">If you declare a variable inside a procedure but outside any block within that procedure, you can think of the variable as having block scope, where the block is the entire procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3aaee-150">Tüm yerel öğeler, bunlar olsa bile `Static` göründükleri yordama özel değişkenler.</span><span class="sxs-lookup"><span data-stu-id="3aaee-150">All local elements, even if they are `Static` variables, are private to the procedure in which they appear.</span></span> <span data-ttu-id="3aaee-151">Öğesini kullanarak bildiremezsiniz [genel](../../../../visual-basic/language-reference/modifiers/public.md) anahtar sözcüğü bir yordam içinde.</span><span class="sxs-lookup"><span data-stu-id="3aaee-151">You cannot declare any element using the [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword within a procedure.</span></span>  
  
### <a name="module-scope"></a><span data-ttu-id="3aaee-152">Modül kapsamı</span><span class="sxs-lookup"><span data-stu-id="3aaee-152">Module Scope</span></span>  
 <span data-ttu-id="3aaee-153">Kolaylık sağlamak adına, tek ifadeli *modül düzeyi* modülleri, sınıflar ve yapılar için eşit oranda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3aaee-153">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="3aaee-154">Bildirim deyiminin dışında herhangi bir yordam veya blok ancak modül, sınıf veya yapı içinde yerleştirerek bu düzeyde öğeleri bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3aaee-154">You can declare elements at this level by placing the declaration statement outside of any procedure or block but within the module, class, or structure.</span></span>  
  
 <span data-ttu-id="3aaee-155">Bir bildirimi Modül düzeyinde değişiklik yaptığınızda, kapsamı seçtiğiniz erişim düzeyini belirler.</span><span class="sxs-lookup"><span data-stu-id="3aaee-155">When you make a declaration at the module level, the access level you choose determines the scope.</span></span> <span data-ttu-id="3aaee-156">Modül, sınıf veya yapı içeren ad uzayı kapsam de etkiler.</span><span class="sxs-lookup"><span data-stu-id="3aaee-156">The namespace that contains the module, class, or structure also affects the scope.</span></span>  
  
 <span data-ttu-id="3aaee-157">Bildirmek için öğeleri [özel](../../../../visual-basic/language-reference/modifiers/private.md) erişim düzeyi bu modüldeki her yordam, ancak farklı bir modül herhangi bir kod için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3aaee-157">Elements for which you declare [Private](../../../../visual-basic/language-reference/modifiers/private.md) access level are available to every procedure in that module, but not to any code in a different module.</span></span> <span data-ttu-id="3aaee-158">`Dim` Deyimi Modül düzeyinde varsayılan olarak `Private` erişim düzeyi anahtar sözcükleri kullanmazsanız.</span><span class="sxs-lookup"><span data-stu-id="3aaee-158">The `Dim` statement at module level defaults to `Private` if you do not use any access level keywords.</span></span> <span data-ttu-id="3aaee-159">Bununla birlikte, kapsamı ve erişim düzeyi daha belirgin kullanarak yapabileceğiniz `Private` anahtar sözcüğünü `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="3aaee-159">However, you can make the scope and access level more obvious by using the `Private` keyword in the `Dim` statement.</span></span>  
  
 <span data-ttu-id="3aaee-160">Aşağıdaki örnekte, tüm yordamları modülde tanımlanmış dize değişkenini ifade edebilir `strMsg`.</span><span class="sxs-lookup"><span data-stu-id="3aaee-160">In the following example, all procedures defined in the module can refer to the string variable `strMsg`.</span></span> <span data-ttu-id="3aaee-161">İkinci yordam çağrıldığında, string değişkeni içeriğini görüntüler. `strMsg` iletişim kutusunda.</span><span class="sxs-lookup"><span data-stu-id="3aaee-161">When the second procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>  
  
```  
' Put the following declaration at module level (not in any procedure).  
Private strMsg As String  
' Put the following Sub procedure in the same module.  
Sub initializePrivateVariable()  
    strMsg = "This variable cannot be used outside this module."  
End Sub  
' Put the following Sub procedure in the same module.  
Sub usePrivateVariable()  
    MsgBox(strMsg)  
End Sub  
```  
  
### <a name="namespace-scope"></a><span data-ttu-id="3aaee-162">Namespace kapsamı</span><span class="sxs-lookup"><span data-stu-id="3aaee-162">Namespace Scope</span></span>  
 <span data-ttu-id="3aaee-163">Modül kullanarak düzeyinde bir öğe bildirirseniz [arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md) veya [genel](../../../../visual-basic/language-reference/modifiers/public.md) anahtar sözcüğü, bu duruma öğesi bildirilmiş ad alanı genelinde tüm yordamları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3aaee-163">If you declare an element at module level using the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) or [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword, it becomes available to all procedures throughout the namespace in which the element is declared.</span></span> <span data-ttu-id="3aaee-164">Önceki örnekte, dize değişkeni için aşağıdaki değişikliği ile `strMsg` kod bildiriminden ad alanındaki herhangi bir ifade.</span><span class="sxs-lookup"><span data-stu-id="3aaee-164">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>  
  
```  
' Include this declaration at module level (not inside any procedure).  
Public strMsg As String  
```  
  
 <span data-ttu-id="3aaee-165">Namespace kapsam iç içe ad alanlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="3aaee-165">Namespace scope includes nested namespaces.</span></span> <span data-ttu-id="3aaee-166">Ad alanı içinde bulunan bir öğe aynı zamanda bu ad alanı içinde iç içe geçmiş herhangi bir ad alanı içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3aaee-166">An element available from within a namespace is also available from within any namespace nested inside that namespace.</span></span>  
  
 <span data-ttu-id="3aaee-167">Projenizi herhangi içermiyorsa [Namespace deyimi](../../../../visual-basic/language-reference/statements/namespace-statement.md)s, projedeki her şeyi aynı ad alanında.</span><span class="sxs-lookup"><span data-stu-id="3aaee-167">If your project does not contain any [Namespace Statement](../../../../visual-basic/language-reference/statements/namespace-statement.md)s, everything in the project is in the same namespace.</span></span> <span data-ttu-id="3aaee-168">Bu durumda, ad alanı kapsamında, proje kapsamı olarak düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="3aaee-168">In this case, namespace scope can be thought of as project scope.</span></span> <span data-ttu-id="3aaee-169">`Public` bir modül, sınıf veya yapı öğeleri de kendi projesine başvuran projeler için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3aaee-169">`Public` elements in a module, class, or structure are also available to any project that references their project.</span></span>  
  
## <a name="choice-of-scope"></a><span data-ttu-id="3aaee-170">Kapsam seçeneği</span><span class="sxs-lookup"><span data-stu-id="3aaee-170">Choice of Scope</span></span>  
 <span data-ttu-id="3aaee-171">Bir değişken bildirdiğinizde, aşağıdaki noktaları kapsamı seçerken göz önünde tutmalısınız.</span><span class="sxs-lookup"><span data-stu-id="3aaee-171">When you declare a variable, you should keep in mind the following points when choosing its scope.</span></span>  
  
### <a name="advantages-of-local-variables"></a><span data-ttu-id="3aaee-172">Yerel değişkenler avantajları</span><span class="sxs-lookup"><span data-stu-id="3aaee-172">Advantages of Local Variables</span></span>  
 <span data-ttu-id="3aaee-173">Yerel değişkenler, aşağıdaki nedenlerden dolayı herhangi bir türden geçici hesaplama için iyi bir seçim şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3aaee-173">Local variables are a good choice for any kind of temporary calculation, for the following reasons:</span></span>  
  
-   <span data-ttu-id="3aaee-174">**Ad çakışması engelleme.**</span><span class="sxs-lookup"><span data-stu-id="3aaee-174">**Name Conflict Avoidance.**</span></span> <span data-ttu-id="3aaee-175">Yerel değişken adları çakışma açık değildir.</span><span class="sxs-lookup"><span data-stu-id="3aaee-175">Local variable names are not susceptible to conflict.</span></span> <span data-ttu-id="3aaee-176">Örneğin, adında bir değişkene içeren birkaç farklı yordamlar oluşturabilirsiniz `intTemp`.</span><span class="sxs-lookup"><span data-stu-id="3aaee-176">For example, you can create several different procedures containing a variable called `intTemp`.</span></span> <span data-ttu-id="3aaee-177">Olduğu sürece her `intTemp` bildirilen yerel değişken olarak, her yordam, yalnızca kendi sürüm tanır, `intTemp`.</span><span class="sxs-lookup"><span data-stu-id="3aaee-177">As long as each `intTemp` is declared as a local variable, each procedure recognizes only its own version of `intTemp`.</span></span> <span data-ttu-id="3aaee-178">Herhangi bir yordam, yerel değeri değiştirebilir `intTemp` etkilemeden `intTemp` diğer yordamlar değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="3aaee-178">Any one procedure can alter the value in its local `intTemp` without affecting `intTemp` variables in other procedures.</span></span>  
  
-   <span data-ttu-id="3aaee-179">**Bellek tüketimi.**</span><span class="sxs-lookup"><span data-stu-id="3aaee-179">**Memory Consumption.**</span></span> <span data-ttu-id="3aaee-180">Yalnızca kendi yordamı çalışırken yerel değişkenler bellek tüketir.</span><span class="sxs-lookup"><span data-stu-id="3aaee-180">Local variables consume memory only while their procedure is running.</span></span> <span data-ttu-id="3aaee-181">Yordamı çağıran koda geri döndüğünde, kendi bellek serbest bırakılır.</span><span class="sxs-lookup"><span data-stu-id="3aaee-181">Their memory is released when the procedure returns to the calling code.</span></span> <span data-ttu-id="3aaee-182">Bunun aksine, [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md) ve [statik](../../../../visual-basic/language-reference/modifiers/static.md) değişkenleri uygulamanızın çalışmayı kadar bellek kaynaklarının kullanılmasına, bunları yalnızca gerekli olduğunda kullanın.</span><span class="sxs-lookup"><span data-stu-id="3aaee-182">By contrast, [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) and [Static](../../../../visual-basic/language-reference/modifiers/static.md) variables consume memory resources until your application stops running, so use them only when necessary.</span></span> <span data-ttu-id="3aaee-183">*Örnek değişkenleri* bunları daha az yerel değişkenler verimlidir, ancak büyük olasılıkla daha verimli olmasını sağlayan kendi örneği var olmaya devam ederken bellek `Shared` veya `Static` değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="3aaee-183">*Instance variables* consume memory while their instance continues to exist, which makes them less efficient than local variables, but potentially more efficient than `Shared` or `Static` variables.</span></span>  
  
### <a name="minimizing-scope"></a><span data-ttu-id="3aaee-184">Kapsam en aza indirme</span><span class="sxs-lookup"><span data-stu-id="3aaee-184">Minimizing Scope</span></span>  
 <span data-ttu-id="3aaee-185">Genel olarak, herhangi bir değişken veya sabit bildirdiğinizde, kapsam olarak dar yapmak alışkanlıktır (blok kapsamı olan en düşük).</span><span class="sxs-lookup"><span data-stu-id="3aaee-185">In general, when declaring any variable or constant, it is good programming practice to make the scope as narrow as possible (block scope is the narrowest).</span></span> <span data-ttu-id="3aaee-186">Bu işlem, bellek korunmasına yardımcı olur ve kodunuzu deneyebileceğinizi hatalı değişkenine başvuran olasılığını en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="3aaee-186">This helps conserve memory and minimizes the chances of your code erroneously referring to the wrong variable.</span></span> <span data-ttu-id="3aaee-187">Benzer şekilde, olması için bir değişken bildirmelidir [statik](../../../../visual-basic/language-reference/modifiers/static.md) yalnızca zaman değerini yordam çağrıları arasında korumak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3aaee-187">Similarly, you should declare a variable to be [Static](../../../../visual-basic/language-reference/modifiers/static.md) only when it is necessary to preserve its value between procedure calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aaee-188">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3aaee-188">See also</span></span>
- [<span data-ttu-id="3aaee-189">Bildirilen Öğe Özellikleri</span><span class="sxs-lookup"><span data-stu-id="3aaee-189">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="3aaee-190">Nasıl yapılır: Bir değişkenin kapsamını denetleme</span><span class="sxs-lookup"><span data-stu-id="3aaee-190">How to: Control the Scope of a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)
- [<span data-ttu-id="3aaee-191">Visual Basic'de ömür</span><span class="sxs-lookup"><span data-stu-id="3aaee-191">Lifetime in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="3aaee-192">Visual Basic'de erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="3aaee-192">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="3aaee-193">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="3aaee-193">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="3aaee-194">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="3aaee-194">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
