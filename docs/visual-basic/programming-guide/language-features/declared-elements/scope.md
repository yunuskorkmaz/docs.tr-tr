---
title: Kapsam
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
ms.openlocfilehash: 1bee904996257474b7457b2aefb1f17d250933cb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410740"
---
# <a name="scope-in-visual-basic"></a><span data-ttu-id="8ee06-102">Visual Basic'de Kapsam</span><span class="sxs-lookup"><span data-stu-id="8ee06-102">Scope in Visual Basic</span></span>

<span data-ttu-id="8ee06-103">Belirtilen bir öğenin *kapsamı* , adını nitelemeden veya bir [içeri aktarmalar Ifadesiyle (.net ad alanı ve türü)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)kullanılabilir hale getirmeden başvurabilen tüm kod kümesidir.</span><span class="sxs-lookup"><span data-stu-id="8ee06-103">The *scope* of a declared element is the set of all code that can refer to it without qualifying its name or making it available through an [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="8ee06-104">Bir öğesi aşağıdaki düzeylerin birinde kapsama sahip olabilir:</span><span class="sxs-lookup"><span data-stu-id="8ee06-104">An element can have scope at one of the following levels:</span></span>

|<span data-ttu-id="8ee06-105">Düzey</span><span class="sxs-lookup"><span data-stu-id="8ee06-105">Level</span></span>|<span data-ttu-id="8ee06-106">Description</span><span class="sxs-lookup"><span data-stu-id="8ee06-106">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="8ee06-107">Blok kapsamı</span><span class="sxs-lookup"><span data-stu-id="8ee06-107">Block scope</span></span>|<span data-ttu-id="8ee06-108">Yalnızca bildirildiği kod bloğu içinde kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="8ee06-108">Available only within the code block in which it is declared</span></span>|
|<span data-ttu-id="8ee06-109">Yordam kapsamı</span><span class="sxs-lookup"><span data-stu-id="8ee06-109">Procedure scope</span></span>|<span data-ttu-id="8ee06-110">İçinde bildirildiği yordamın içindeki tüm kodlar için kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="8ee06-110">Available to all code within the procedure in which it is declared</span></span>|
|<span data-ttu-id="8ee06-111">Modül kapsamı</span><span class="sxs-lookup"><span data-stu-id="8ee06-111">Module scope</span></span>|<span data-ttu-id="8ee06-112">Bildirildiği modül, sınıf veya yapı içindeki tüm kodlar için kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="8ee06-112">Available to all code within the module, class, or structure in which it is declared</span></span>|
|<span data-ttu-id="8ee06-113">Ad alanı kapsamı</span><span class="sxs-lookup"><span data-stu-id="8ee06-113">Namespace scope</span></span>|<span data-ttu-id="8ee06-114">İçinde bildirildiği ad alanındaki tüm kodlar için kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="8ee06-114">Available to all code in the namespace in which it is declared</span></span>|

<span data-ttu-id="8ee06-115">Bu kapsam düzeyleri en dar (blok) en geniş (ad alanı) arasında ilerleme gösterir; burada *dar kapsam* , nitelendirme olmadan öğeye başvurabilen en küçük kod kümesidir.</span><span class="sxs-lookup"><span data-stu-id="8ee06-115">These levels of scope progress from the narrowest (block) to the widest (namespace), where *narrowest scope* means the smallest set of code that can refer to the element without qualification.</span></span> <span data-ttu-id="8ee06-116">Daha fazla bilgi için bu sayfadaki "kapsam düzeyleri" başlığına bakın.</span><span class="sxs-lookup"><span data-stu-id="8ee06-116">For more information, see "Levels of Scope" on this page.</span></span>

## <a name="specifying-scope-and-defining-variables"></a><span data-ttu-id="8ee06-117">Kapsam belirtme ve değişkenleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="8ee06-117">Specifying Scope and Defining Variables</span></span>

<span data-ttu-id="8ee06-118">Bir öğenin kapsamını bildirdiğinizde belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ee06-118">You specify the scope of an element when you declare it.</span></span> <span data-ttu-id="8ee06-119">Kapsam aşağıdaki faktörlere bağlı olabilir:</span><span class="sxs-lookup"><span data-stu-id="8ee06-119">The scope can depend on the following factors:</span></span>

- <span data-ttu-id="8ee06-120">İçinde öğeyi bildirdiğiniz bölge (blok, yordam, modül, sınıf veya yapı)</span><span class="sxs-lookup"><span data-stu-id="8ee06-120">The region (block, procedure, module, class, or structure) in which you declare the element</span></span>

- <span data-ttu-id="8ee06-121">Öğenin bildirimini içeren ad alanı</span><span class="sxs-lookup"><span data-stu-id="8ee06-121">The namespace containing the element's declaration</span></span>

- <span data-ttu-id="8ee06-122">Öğesi için bildirdiğiniz erişim düzeyi</span><span class="sxs-lookup"><span data-stu-id="8ee06-122">The access level you declare for the element</span></span>

<span data-ttu-id="8ee06-123">Aynı ada ancak farklı kapsama sahip değişkenler tanımladığınızda, bu durum beklenmedik sonuçlara yol açacağından dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ee06-123">Use care when you define variables with the same name but different scope, because doing so can lead to unexpected results.</span></span> <span data-ttu-id="8ee06-124">Daha fazla bilgi için bkz. [bildirilmemiş öğelere başvurular](references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="8ee06-124">For more information, see [References to Declared Elements](references-to-declared-elements.md).</span></span>

## <a name="levels-of-scope"></a><span data-ttu-id="8ee06-125">Kapsam düzeyleri</span><span class="sxs-lookup"><span data-stu-id="8ee06-125">Levels of Scope</span></span>

<span data-ttu-id="8ee06-126">Bir programlama öğesi, bildirdiğiniz bölgenin tamamında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8ee06-126">A programming element is available throughout the region in which you declare it.</span></span> <span data-ttu-id="8ee06-127">Aynı bölgedeki tüm kodlar, adını nitelemeden öğesine başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="8ee06-127">All code in the same region can refer to the element without qualifying its name.</span></span>

### <a name="block-scope"></a><span data-ttu-id="8ee06-128">Blok kapsamı</span><span class="sxs-lookup"><span data-stu-id="8ee06-128">Block Scope</span></span>

<span data-ttu-id="8ee06-129">Blok, aşağıdaki gibi bildirim deyimlerini başlatma ve sonlandırma içinde yer alan deyimler kümesidir:</span><span class="sxs-lookup"><span data-stu-id="8ee06-129">A block is a set of statements enclosed within initiating and terminating declaration statements, such as the following:</span></span>

- <span data-ttu-id="8ee06-130">`Do` ve `Loop`</span><span class="sxs-lookup"><span data-stu-id="8ee06-130">`Do` and `Loop`</span></span>

- <span data-ttu-id="8ee06-131">`For`[ `Each` ] ve`Next`</span><span class="sxs-lookup"><span data-stu-id="8ee06-131">`For` [`Each`] and `Next`</span></span>

- <span data-ttu-id="8ee06-132">`If` ve `End If`</span><span class="sxs-lookup"><span data-stu-id="8ee06-132">`If` and `End If`</span></span>

- <span data-ttu-id="8ee06-133">`Select` ve `End Select`</span><span class="sxs-lookup"><span data-stu-id="8ee06-133">`Select` and `End Select`</span></span>

- <span data-ttu-id="8ee06-134">`SyncLock` ve `End SyncLock`</span><span class="sxs-lookup"><span data-stu-id="8ee06-134">`SyncLock` and `End SyncLock`</span></span>

- <span data-ttu-id="8ee06-135">`Try` ve `End Try`</span><span class="sxs-lookup"><span data-stu-id="8ee06-135">`Try` and `End Try`</span></span>

- <span data-ttu-id="8ee06-136">`While` ve `End While`</span><span class="sxs-lookup"><span data-stu-id="8ee06-136">`While` and `End While`</span></span>

- <span data-ttu-id="8ee06-137">`With` ve `End With`</span><span class="sxs-lookup"><span data-stu-id="8ee06-137">`With` and `End With`</span></span>

<span data-ttu-id="8ee06-138">Bir blok içinde bir değişken bildirirseniz, bunu yalnızca bu blok içinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ee06-138">If you declare a variable within a block, you can use it only within that block.</span></span> <span data-ttu-id="8ee06-139">Aşağıdaki örnekte, tamsayı değişkeninin kapsamı `cube` ve arasındaki blokdır `If` `End If` ve artık `cube` yürütme bloğundan dışarı geçtiğinde başvurursunuz.</span><span class="sxs-lookup"><span data-stu-id="8ee06-139">In the following example, the scope of the integer variable `cube` is the block between `If` and `End If`, and you can no longer refer to `cube` when execution passes out of the block.</span></span>

```vb
If n < 1291 Then
    Dim cube As Integer
    cube = n ^ 3
End If
```

> [!NOTE]
> <span data-ttu-id="8ee06-140">Bir değişkenin kapsamı bir blokla sınırlı olsa da, ömrü tamamen yordamın tamamıdır.</span><span class="sxs-lookup"><span data-stu-id="8ee06-140">Even if the scope of a variable is limited to a block, its lifetime is still that of the entire procedure.</span></span> <span data-ttu-id="8ee06-141">Yordamı yordam sırasında birden fazla kez girerseniz, her blok değişkeni önceki değerini korur.</span><span class="sxs-lookup"><span data-stu-id="8ee06-141">If you enter the block more than once during the procedure, each block variable retains its previous value.</span></span> <span data-ttu-id="8ee06-142">Böyle bir durumda beklenmedik sonuçlara engel olmak için, bloğun başlangıcında blok değişkenlerini başlatmak uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="8ee06-142">To avoid unexpected results in such a case, it is wise to initialize block variables at the beginning of the block.</span></span>

### <a name="procedure-scope"></a><span data-ttu-id="8ee06-143">Yordam kapsamı</span><span class="sxs-lookup"><span data-stu-id="8ee06-143">Procedure Scope</span></span>

<span data-ttu-id="8ee06-144">Yordam içinde belirtilen bir öğe, bu yordamın dışında kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8ee06-144">An element declared within a procedure is not available outside that procedure.</span></span> <span data-ttu-id="8ee06-145">Yalnızca bildirimi içeren yordam bunu kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="8ee06-145">Only the procedure that contains the declaration can use it.</span></span> <span data-ttu-id="8ee06-146">Bu düzeydeki değişkenler *yerel değişkenler*olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="8ee06-146">Variables at this level are also known as *local variables*.</span></span> <span data-ttu-id="8ee06-147">Onları, [static](../../../language-reference/modifiers/static.md) anahtar sözcüğüyle veya olmadan [Dim ifadesiyle](../../../language-reference/statements/dim-statement.md)bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ee06-147">You declare them with the [Dim Statement](../../../language-reference/statements/dim-statement.md), with or without the [Static](../../../language-reference/modifiers/static.md) keyword.</span></span>

<span data-ttu-id="8ee06-148">Yordam ve blok kapsamı yakından ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="8ee06-148">Procedure and block scope are closely related.</span></span> <span data-ttu-id="8ee06-149">Bir yordam içinde bir değişken bildirirseniz, ancak bu yordamın içindeki herhangi bir blok dışında, değişkenini blok kapsamına sahip olarak düşünebilirsiniz; burada blok tüm yordamdır.</span><span class="sxs-lookup"><span data-stu-id="8ee06-149">If you declare a variable inside a procedure but outside any block within that procedure, you can think of the variable as having block scope, where the block is the entire procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="8ee06-150">Değişkenler olsalar bile tüm yerel öğeler `Static` , göründükleri yordama özeldir.</span><span class="sxs-lookup"><span data-stu-id="8ee06-150">All local elements, even if they are `Static` variables, are private to the procedure in which they appear.</span></span> <span data-ttu-id="8ee06-151">Bir yordam içinde [Public](../../../language-reference/modifiers/public.md) anahtar sözcüğünü kullanarak hiçbir öğe bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ee06-151">You cannot declare any element using the [Public](../../../language-reference/modifiers/public.md) keyword within a procedure.</span></span>

### <a name="module-scope"></a><span data-ttu-id="8ee06-152">Modül kapsamı</span><span class="sxs-lookup"><span data-stu-id="8ee06-152">Module Scope</span></span>

<span data-ttu-id="8ee06-153">Kolaylık olması için, tek vadeli *Modül düzeyi* modüller, sınıflar ve yapılar için eşit oranda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8ee06-153">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="8ee06-154">Bildirim ifadesini herhangi bir yordamın veya bloğun dışında, ancak modül, sınıf veya yapı içinde yerleştirerek bu düzeydeki öğeleri bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ee06-154">You can declare elements at this level by placing the declaration statement outside of any procedure or block but within the module, class, or structure.</span></span>

<span data-ttu-id="8ee06-155">Modül düzeyinde bir bildirim yaptığınızda seçtiğiniz erişim düzeyi kapsamı belirler.</span><span class="sxs-lookup"><span data-stu-id="8ee06-155">When you make a declaration at the module level, the access level you choose determines the scope.</span></span> <span data-ttu-id="8ee06-156">Modül, sınıf veya yapıyı içeren ad alanı da kapsamı etkiler.</span><span class="sxs-lookup"><span data-stu-id="8ee06-156">The namespace that contains the module, class, or structure also affects the scope.</span></span>

<span data-ttu-id="8ee06-157">[Özel](../../../language-reference/modifiers/private.md) erişim düzeyi bildirdiğiniz öğeler, bu modüldeki her yordamda kullanılabilir, ancak farklı bir modüldeki herhangi bir koda uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="8ee06-157">Elements for which you declare [Private](../../../language-reference/modifiers/private.md) access level are available to every procedure in that module, but not to any code in a different module.</span></span> <span data-ttu-id="8ee06-158">`Dim`Modül düzeyindeki deyimin değeri, `Private` herhangi bir erişim düzeyi anahtar sözcüğü kullanmıyorsanız varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="8ee06-158">The `Dim` statement at module level defaults to `Private` if you do not use any access level keywords.</span></span> <span data-ttu-id="8ee06-159">Ancak, bildiriminde anahtar sözcüğünü kullanarak kapsamı ve erişim düzeyini daha belirgin hale getirebilirsiniz `Private` `Dim` .</span><span class="sxs-lookup"><span data-stu-id="8ee06-159">However, you can make the scope and access level more obvious by using the `Private` keyword in the `Dim` statement.</span></span>

<span data-ttu-id="8ee06-160">Aşağıdaki örnekte, modülünde tanımlanan tüm yordamlar dize değişkenine başvurabilir `strMsg` .</span><span class="sxs-lookup"><span data-stu-id="8ee06-160">In the following example, all procedures defined in the module can refer to the string variable `strMsg`.</span></span> <span data-ttu-id="8ee06-161">İkinci yordam çağrıldığında, dize değişkeninin içeriğini `strMsg` bir iletişim kutusunda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8ee06-161">When the second procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>

```vb
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

### <a name="namespace-scope"></a><span data-ttu-id="8ee06-162">Ad alanı kapsamı</span><span class="sxs-lookup"><span data-stu-id="8ee06-162">Namespace Scope</span></span>

<span data-ttu-id="8ee06-163">Bir öğeyi, [Friend](../../../language-reference/modifiers/friend.md) veya [Public](../../../language-reference/modifiers/public.md) anahtar sözcüğünü kullanarak modül düzeyinde bildirirseniz, bu, öğenin bildirildiği ad alanı boyunca tüm yordamlarda kullanılabilir hale gelir.</span><span class="sxs-lookup"><span data-stu-id="8ee06-163">If you declare an element at module level using the [Friend](../../../language-reference/modifiers/friend.md) or [Public](../../../language-reference/modifiers/public.md) keyword, it becomes available to all procedures throughout the namespace in which the element is declared.</span></span> <span data-ttu-id="8ee06-164">Önceki örnekte yapılan aşağıdaki değişiklikle, dize değişkenine, `strMsg` bildiriminin ad alanı içinde herhangi bir yerde kod eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="8ee06-164">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>

```vb
' Include this declaration at module level (not inside any procedure).
Public strMsg As String
```

<span data-ttu-id="8ee06-165">Ad alanı kapsamı iç içe geçmiş ad alanlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="8ee06-165">Namespace scope includes nested namespaces.</span></span> <span data-ttu-id="8ee06-166">Ad alanı içinde bulunan bir öğe, bu ad alanı içinde iç içe yerleştirilmiş herhangi bir ad alanı içinde de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8ee06-166">An element available from within a namespace is also available from within any namespace nested inside that namespace.</span></span>

<span data-ttu-id="8ee06-167">Projeniz herhangi bir [ad alanı bildirisi](../../../language-reference/statements/namespace-statement.md)içermiyorsa, projedeki her şey aynı ad alanında bulunur.</span><span class="sxs-lookup"><span data-stu-id="8ee06-167">If your project does not contain any [Namespace Statement](../../../language-reference/statements/namespace-statement.md)s, everything in the project is in the same namespace.</span></span> <span data-ttu-id="8ee06-168">Bu durumda, ad alanı kapsamı Proje kapsamı olarak düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="8ee06-168">In this case, namespace scope can be thought of as project scope.</span></span> <span data-ttu-id="8ee06-169">`Public`bir modül, sınıf veya yapıdaki öğeler, projesine başvuran tüm projeler için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8ee06-169">`Public` elements in a module, class, or structure are also available to any project that references their project.</span></span>

## <a name="choice-of-scope"></a><span data-ttu-id="8ee06-170">Kapsam seçimi</span><span class="sxs-lookup"><span data-stu-id="8ee06-170">Choice of Scope</span></span>

<span data-ttu-id="8ee06-171">Bir değişken bildirdiğinizde, kapsamını seçerken aşağıdaki noktaları göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ee06-171">When you declare a variable, you should keep in mind the following points when choosing its scope.</span></span>

### <a name="advantages-of-local-variables"></a><span data-ttu-id="8ee06-172">Yerel değişkenlerin avantajları</span><span class="sxs-lookup"><span data-stu-id="8ee06-172">Advantages of Local Variables</span></span>

<span data-ttu-id="8ee06-173">Yerel değişkenler, aşağıdaki nedenlerden dolayı her türlü geçici hesaplama için iyi bir seçimdir:</span><span class="sxs-lookup"><span data-stu-id="8ee06-173">Local variables are a good choice for any kind of temporary calculation, for the following reasons:</span></span>

- <span data-ttu-id="8ee06-174">**Ad çakışması engelleme.**</span><span class="sxs-lookup"><span data-stu-id="8ee06-174">**Name Conflict Avoidance.**</span></span> <span data-ttu-id="8ee06-175">Yerel değişken adları çakışmaya karşı savunmasız değildir.</span><span class="sxs-lookup"><span data-stu-id="8ee06-175">Local variable names are not susceptible to conflict.</span></span> <span data-ttu-id="8ee06-176">Örneğin, adlı bir değişken içeren birkaç farklı yordam oluşturabilirsiniz `intTemp` .</span><span class="sxs-lookup"><span data-stu-id="8ee06-176">For example, you can create several different procedures containing a variable called `intTemp`.</span></span> <span data-ttu-id="8ee06-177">Her biri `intTemp` yerel değişken olarak bildirildiği sürece, her yordam yalnızca kendi sürümünü tanır `intTemp` .</span><span class="sxs-lookup"><span data-stu-id="8ee06-177">As long as each `intTemp` is declared as a local variable, each procedure recognizes only its own version of `intTemp`.</span></span> <span data-ttu-id="8ee06-178">Herhangi bir yordam, `intTemp` diğer yordamlardan değişkenleri etkilemeden yerel içindeki değeri değiştirebilir `intTemp` .</span><span class="sxs-lookup"><span data-stu-id="8ee06-178">Any one procedure can alter the value in its local `intTemp` without affecting `intTemp` variables in other procedures.</span></span>

- <span data-ttu-id="8ee06-179">**Bellek tüketimi.**</span><span class="sxs-lookup"><span data-stu-id="8ee06-179">**Memory Consumption.**</span></span> <span data-ttu-id="8ee06-180">Yerel değişkenler yalnızca yordamı çalışırken belleği tüketir.</span><span class="sxs-lookup"><span data-stu-id="8ee06-180">Local variables consume memory only while their procedure is running.</span></span> <span data-ttu-id="8ee06-181">Yordamı çağıran koda geri döndüğünde, belleği serbest bırakılır.</span><span class="sxs-lookup"><span data-stu-id="8ee06-181">Their memory is released when the procedure returns to the calling code.</span></span> <span data-ttu-id="8ee06-182">Aksine, [paylaşılan](../../../language-reference/modifiers/shared.md) ve [statik](../../../language-reference/modifiers/static.md) değişkenler, uygulamanız çalışmayı durdurana kadar bellek kaynaklarını kullanır, bu nedenle onları yalnızca gerekli olduğunda kullanın.</span><span class="sxs-lookup"><span data-stu-id="8ee06-182">By contrast, [Shared](../../../language-reference/modifiers/shared.md) and [Static](../../../language-reference/modifiers/static.md) variables consume memory resources until your application stops running, so use them only when necessary.</span></span> <span data-ttu-id="8ee06-183">Örnek *değişkenleri* , örnekleri mevcut olmaya devam ederken belleği tüketir, bu da yerel değişkenlerden daha az verimlidir, ancak büyük olasılıkla `Shared` veya değişkenlerinden daha etkilidir `Static` .</span><span class="sxs-lookup"><span data-stu-id="8ee06-183">*Instance variables* consume memory while their instance continues to exist, which makes them less efficient than local variables, but potentially more efficient than `Shared` or `Static` variables.</span></span>

### <a name="minimizing-scope"></a><span data-ttu-id="8ee06-184">Kapsamı küçültme</span><span class="sxs-lookup"><span data-stu-id="8ee06-184">Minimizing Scope</span></span>

<span data-ttu-id="8ee06-185">Genel olarak, herhangi bir değişken veya sabit bildirirken, kapsamı olabildiğince dar hale getirmek için iyi bir programlama uygulamasıdır (blok kapsam en dar olur).</span><span class="sxs-lookup"><span data-stu-id="8ee06-185">In general, when declaring any variable or constant, it is good programming practice to make the scope as narrow as possible (block scope is the narrowest).</span></span> <span data-ttu-id="8ee06-186">Bu, belleğin korunmasına yardımcı olur ve yanlış değişkene başvuran kodunuzun yanlışlıkla yanlış olduğunu en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="8ee06-186">This helps conserve memory and minimizes the chances of your code erroneously referring to the wrong variable.</span></span> <span data-ttu-id="8ee06-187">Benzer şekilde, bir değişkeni yalnızca yordam çağrıları arasında değerini korumak gerektiğinde [statik](../../../language-reference/modifiers/static.md) olacak şekilde bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ee06-187">Similarly, you should declare a variable to be [Static](../../../language-reference/modifiers/static.md) only when it is necessary to preserve its value between procedure calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="8ee06-188">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ee06-188">See also</span></span>

- [<span data-ttu-id="8ee06-189">Bildirilen Öğe Özellikleri</span><span class="sxs-lookup"><span data-stu-id="8ee06-189">Declared Element Characteristics</span></span>](declared-element-characteristics.md)
- [<span data-ttu-id="8ee06-190">Nasıl yapılır: Bir Değişkenin Kapsamını Denetleme</span><span class="sxs-lookup"><span data-stu-id="8ee06-190">How to: Control the Scope of a Variable</span></span>](how-to-control-the-scope-of-a-variable.md)
- [<span data-ttu-id="8ee06-191">Visual Basic'de Ömür</span><span class="sxs-lookup"><span data-stu-id="8ee06-191">Lifetime in Visual Basic</span></span>](lifetime.md)
- [<span data-ttu-id="8ee06-192">Visual Basic erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="8ee06-192">Access levels in Visual Basic</span></span>](access-levels.md)
- [<span data-ttu-id="8ee06-193">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="8ee06-193">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="8ee06-194">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="8ee06-194">Variable Declaration</span></span>](../variables/variable-declaration.md)
