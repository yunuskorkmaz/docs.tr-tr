---
title: 'Nasıl yapılır: Değişkeninizle Aynı ada sahip bir değişkeni gizleyin (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- declarations [Visual Basic], elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
ms.assetid: e39c0752-f19f-4d2e-a453-00df1b5fc7ee
ms.openlocfilehash: 487e0a15ba6b52f92ab39fe0bae4ab15fa92707f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629993"
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a><span data-ttu-id="f293a-102">Nasıl yapılır: Değişkeninizle Aynı ada sahip bir değişkeni gizleyin (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f293a-102">How to: Hide a Variable with the Same Name as Your Variable (Visual Basic)</span></span>

<span data-ttu-id="f293a-103">Bir değişkeni, aynı ada sahip bir değişkenle yeniden tanımlayarak, bir değeri gölgelendirerek gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f293a-103">You can hide a variable by *shadowing* it, that is, by redefining it with a variable of the same name.</span></span> <span data-ttu-id="f293a-104">Gizlemek istediğiniz değişkeni iki şekilde gölgelendireseçebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f293a-104">You can shadow the variable you want to hide in two ways:</span></span>

- <span data-ttu-id="f293a-105">**Kapsam üzerinden gölgeleme.**</span><span class="sxs-lookup"><span data-stu-id="f293a-105">**Shadowing Through Scope.**</span></span> <span data-ttu-id="f293a-106">Onu, gizlemek istediğiniz değişkeni içeren bölgenin bir alt bölgesi içinde yeniden bildirerek kapsam aracılığıyla gölgelendirebilir.</span><span class="sxs-lookup"><span data-stu-id="f293a-106">You can shadow it through scope by redeclaring it inside a subregion of the region containing the variable you want to hide.</span></span>

- <span data-ttu-id="f293a-107">**Devralma yoluyla gölgeleme.**</span><span class="sxs-lookup"><span data-stu-id="f293a-107">**Shadowing Through Inheritance.**</span></span> <span data-ttu-id="f293a-108">Gizlemek istediğiniz değişken sınıf düzeyinde tanımlıysa, türetilmiş bir sınıftaki [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) anahtar sözcüğüyle yeniden bildirerek devralma yoluyla gölge oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f293a-108">If the variable you want to hide is defined at class level, you can shadow it through inheritance by redeclaring it with the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in a derived class.</span></span>

## <a name="two-ways-to-hide-a-variable"></a><span data-ttu-id="f293a-109">Bir değişkeni gizlemek için iki yol</span><span class="sxs-lookup"><span data-stu-id="f293a-109">Two Ways to Hide a Variable</span></span>

#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a><span data-ttu-id="f293a-110">Bir değişkeni kapsam aracılığıyla gölgelendirerek gizlemek için</span><span class="sxs-lookup"><span data-stu-id="f293a-110">To hide a variable by shadowing it through scope</span></span>

1. <span data-ttu-id="f293a-111">Gizlemek istediğiniz değişkeni tanımlayan bölgeyi belirleme ve Değişkeninizle birlikte yeniden tanımlanacak bir alt bölge belirleme.</span><span class="sxs-lookup"><span data-stu-id="f293a-111">Determine the region defining the variable you want to hide, and determine a subregion in which to redefine it with your variable.</span></span>

    |<span data-ttu-id="f293a-112">Değişkenin bölgesi</span><span class="sxs-lookup"><span data-stu-id="f293a-112">Variable's region</span></span>|<span data-ttu-id="f293a-113">Yeniden tanımlama için izin verilen alt bölge</span><span class="sxs-lookup"><span data-stu-id="f293a-113">Allowable subregion for redefining it</span></span>|
    |-----------------------|-------------------------------------------|
    |<span data-ttu-id="f293a-114">Modül</span><span class="sxs-lookup"><span data-stu-id="f293a-114">Module</span></span>|<span data-ttu-id="f293a-115">Modül içindeki bir sınıf</span><span class="sxs-lookup"><span data-stu-id="f293a-115">A class within the module</span></span>|
    |<span data-ttu-id="f293a-116">örneği</span><span class="sxs-lookup"><span data-stu-id="f293a-116">Class</span></span>|<span data-ttu-id="f293a-117">Sınıf içindeki bir alt sınıf</span><span class="sxs-lookup"><span data-stu-id="f293a-117">A subclass within the class</span></span><br /><br /> <span data-ttu-id="f293a-118">Sınıf içindeki bir yordam</span><span class="sxs-lookup"><span data-stu-id="f293a-118">A procedure within the class</span></span>|

    <span data-ttu-id="f293a-119">Bu yordam içindeki bir blok içindeki bir yordam değişkenini yeniden tanımlayamazsınız, örneğin bir `If`... oluşturma veya bir `For`döngü. `End If`</span><span class="sxs-lookup"><span data-stu-id="f293a-119">You cannot redefine a procedure variable in a block within that procedure, for example in an `If`...`End If` construction or a `For` loop.</span></span>

2. <span data-ttu-id="f293a-120">Zaten yoksa alt bölge oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f293a-120">Create the subregion if it does not already exist.</span></span>

3. <span data-ttu-id="f293a-121">Alt bölge içinde, gölgeleme değişkenini bildiren bir [Dim ekstresi](../../../../visual-basic/language-reference/statements/dim-statement.md) yazın.</span><span class="sxs-lookup"><span data-stu-id="f293a-121">Within the subregion, write a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) declaring the shadowing variable.</span></span>

    <span data-ttu-id="f293a-122">Alt bölge içindeki kod değişken adına başvurduğunda, derleyici, gölgeleme değişkeninin başvurusunu çözümler.</span><span class="sxs-lookup"><span data-stu-id="f293a-122">When code inside the subregion refers to the variable name, the compiler resolves the reference to the shadowing variable.</span></span>

    <span data-ttu-id="f293a-123">Aşağıdaki örnekte, kapsam aracılığıyla gölgeleme ve ayrıca, gölgelendirmeyi atlayan bir başvuru gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f293a-123">The following example illustrates shadowing through scope, as well as a reference that bypasses the shadowing.</span></span>

    ```vb
    Module shadowByScope
        ' The following statement declares num as a module-level variable.
        Public num As Integer
        Sub show()
            ' The following statement declares num as a local variable.
            Dim num As Integer
            ' The following statement sets the value of the local variable.
            num = 2
            ' The following statement displays the module-level variable.
            MsgBox(CStr(shadowByScope.num))
        End Sub
        Sub useModuleLevelNum()
            ' The following statement sets the value of the module-level variable.
            num = 1
            show()
        End Sub
    End Module
    ```

    <span data-ttu-id="f293a-124">Yukarıdaki örnek, değişkeni `num` hem modül düzeyinde hem de yordam düzeyinde (yordamda `show`) bildirir.</span><span class="sxs-lookup"><span data-stu-id="f293a-124">The preceding example declares the variable `num` both at module level and at procedure level (in the procedure `show`).</span></span> <span data-ttu-id="f293a-125">Yerel değişken `num` , içinde `show`modül düzeyi değişkeni `num` gölgeler, bu nedenle yerel değişken 2 olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f293a-125">The local variable `num` shadows the module-level variable `num` within `show`, so the local variable is set to 2.</span></span> <span data-ttu-id="f293a-126">Ancak, `num` `useModuleLevelNum` yordamda gölge için yerel bir değişken yoktur.</span><span class="sxs-lookup"><span data-stu-id="f293a-126">However, there is no local variable to shadow `num` in the `useModuleLevelNum` procedure.</span></span> <span data-ttu-id="f293a-127">Bu nedenle `useModuleLevelNum` , modül düzeyi değişkeninin değerini 1 olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f293a-127">Therefore, `useModuleLevelNum` sets the value of the module-level variable to 1.</span></span>

    <span data-ttu-id="f293a-128">`num` İçindeki `MsgBox` çağrı,`show` modül adıyla niteleyerek gölgeleme mekanizmasını atlar.</span><span class="sxs-lookup"><span data-stu-id="f293a-128">The `MsgBox` call inside `show` bypasses the shadowing mechanism by qualifying `num` with the module name.</span></span> <span data-ttu-id="f293a-129">Bu nedenle, yerel değişken yerine modül düzeyi değişkeni görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f293a-129">Therefore, it displays the module-level variable instead of the local variable.</span></span>

#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a><span data-ttu-id="f293a-130">Bir değişkeni devralma yoluyla gölgelendirerek gizlemek için</span><span class="sxs-lookup"><span data-stu-id="f293a-130">To hide a variable by shadowing it through inheritance</span></span>

1. <span data-ttu-id="f293a-131">Gizlemek istediğiniz değişkenin bir sınıfta ve sınıf düzeyinde (herhangi bir yordam dışında) olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="f293a-131">Be sure the variable you want to hide is declared in a class, and at class level (outside any procedure).</span></span> <span data-ttu-id="f293a-132">Aksi takdirde, devralma aracılığıyla gölgelendiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="f293a-132">Otherwise you cannot shadow it through inheritance.</span></span>

2. <span data-ttu-id="f293a-133">Değişkenin sınıfından türetilmiş bir sınıfı, zaten mevcut değilse tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="f293a-133">Define a class derived from the variable's class if one does not already exist.</span></span>

3. <span data-ttu-id="f293a-134">Türetilmiş sınıfın içinde, değişkeninizi bildiren `Dim` bir ifade yazın.</span><span class="sxs-lookup"><span data-stu-id="f293a-134">Inside the derived class, write a `Dim` statement declaring your variable.</span></span> <span data-ttu-id="f293a-135">Bildirime [gölgeler](../../../../visual-basic/language-reference/modifiers/shadows.md) anahtar sözcüğünü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f293a-135">Include the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>

    <span data-ttu-id="f293a-136">Türetilmiş sınıftaki kod, değişken adına başvurduğunda, derleyici değişkeninizin başvurusunu çözer.</span><span class="sxs-lookup"><span data-stu-id="f293a-136">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>

    <span data-ttu-id="f293a-137">Aşağıdaki örnek, devralma yoluyla gölgelendirmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="f293a-137">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="f293a-138">Biri, gölgeleme değişkenine erişen diğeri de gölgelendirmeyi atlayan iki başvuru yapar.</span><span class="sxs-lookup"><span data-stu-id="f293a-138">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>

    ```vb
    Public Class shadowBaseClass
        Public shadowString As String = "This is the base class string."
    End Class
    Public Class shadowDerivedClass
        Inherits shadowBaseClass
        Public Shadows shadowString As String = "This is the derived class string."
        Public Sub showStrings()
            Dim s As String = "Unqualified shadowString: " & shadowString &
                 vbCrLf & "MyBase.shadowString: " & MyBase.shadowString
            MsgBox(s)
        End Sub
    End Class
    ```

    <span data-ttu-id="f293a-139">Önceki örnek, değişkeni `shadowString` temel sınıfta bildirir ve türetilmiş sınıfta gölgeleri.</span><span class="sxs-lookup"><span data-stu-id="f293a-139">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="f293a-140">Türetilmiş sınıftaki `showStrings` yordamda, ad `shadowString` uygun olmadığında dizenin gölgeleme sürümü görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f293a-140">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="f293a-141">Ardından, `shadowString` `MyBase` anahtar sözcüğü ile nitelendirilmeden gölgeli sürümü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f293a-141">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="f293a-142">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="f293a-142">Robust Programming</span></span>

<span data-ttu-id="f293a-143">Gölgeleme aynı ada sahip bir değişkenin birden fazla sürümünü tanıtır.</span><span class="sxs-lookup"><span data-stu-id="f293a-143">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="f293a-144">Bir kod açıklaması değişken adına başvurduğunda, derleyicinin başvuruyu çözümleyen sürüm, kod ifadesinin konumu ve uygun bir dizenin varlığı gibi faktörlere bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f293a-144">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="f293a-145">Bu, gölgelendirilmiş bir değişkenin istenmeyen bir sürümüne başvurma riskini artırabilir.</span><span class="sxs-lookup"><span data-stu-id="f293a-145">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="f293a-146">Gölgelendirilmiş bir değişkene tüm başvuruları tam olarak niteleyerek bu riski düşürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f293a-146">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="f293a-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f293a-147">See also</span></span>

- [<span data-ttu-id="f293a-148">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="f293a-148">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="f293a-149">Visual Basic gölgeleme</span><span class="sxs-lookup"><span data-stu-id="f293a-149">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="f293a-150">Gölgeleme ve Geçersiz Kılma Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="f293a-150">Differences Between Shadowing and Overriding</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="f293a-151">Nasıl yapılır: Devralınan bir değişkeni gizleme</span><span class="sxs-lookup"><span data-stu-id="f293a-151">How to: Hide an Inherited Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="f293a-152">Nasıl yapılır: Türetilmiş bir sınıf tarafından gizlenen bir değişkene erişme</span><span class="sxs-lookup"><span data-stu-id="f293a-152">How to: Access a Variable Hidden by a Derived Class</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [<span data-ttu-id="f293a-153">Overrides</span><span class="sxs-lookup"><span data-stu-id="f293a-153">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="f293a-154">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="f293a-154">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="f293a-155">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="f293a-155">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
