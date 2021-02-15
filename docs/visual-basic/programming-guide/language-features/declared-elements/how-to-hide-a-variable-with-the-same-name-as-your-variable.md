---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Değişkeninizle Aynı ada sahip bir değişkeni gizleme (Visual Basic)'
title: 'Nasıl yapılır: Değişkeninizle Aynı Adı Taşıyan Bir Değişkeni Gizleme'
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
ms.openlocfilehash: c6699abdc163c6ae1a78f6035cd08439d1b029f0
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429864"
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a><span data-ttu-id="0b0be-103">Nasıl yapılır: Değişkeninizle Aynı Adı Taşıyan Bir Değişkeni Gizleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b0be-103">How to: Hide a Variable with the Same Name as Your Variable (Visual Basic)</span></span>

<span data-ttu-id="0b0be-104">Bir değişkeni, aynı ada sahip bir değişkenle yeniden tanımlayarak, bir değeri *gölgelendirerek* gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b0be-104">You can hide a variable by *shadowing* it, that is, by redefining it with a variable of the same name.</span></span> <span data-ttu-id="0b0be-105">Gizlemek istediğiniz değişkeni iki şekilde gölgelendireseçebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0b0be-105">You can shadow the variable you want to hide in two ways:</span></span>

- <span data-ttu-id="0b0be-106">**Kapsam üzerinden gölgeleme.**</span><span class="sxs-lookup"><span data-stu-id="0b0be-106">**Shadowing Through Scope.**</span></span> <span data-ttu-id="0b0be-107">Onu, gizlemek istediğiniz değişkeni içeren bölgenin bir alt bölgesi içinde yeniden bildirerek kapsam aracılığıyla gölgelendirebilir.</span><span class="sxs-lookup"><span data-stu-id="0b0be-107">You can shadow it through scope by redeclaring it inside a subregion of the region containing the variable you want to hide.</span></span>

- <span data-ttu-id="0b0be-108">**Devralma yoluyla gölgeleme.**</span><span class="sxs-lookup"><span data-stu-id="0b0be-108">**Shadowing Through Inheritance.**</span></span> <span data-ttu-id="0b0be-109">Gizlemek istediğiniz değişken sınıf düzeyinde tanımlıysa, türetilmiş bir sınıftaki [Shadows](../../../language-reference/modifiers/shadows.md) anahtar sözcüğüyle yeniden bildirerek devralma yoluyla gölge oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b0be-109">If the variable you want to hide is defined at class level, you can shadow it through inheritance by redeclaring it with the [Shadows](../../../language-reference/modifiers/shadows.md) keyword in a derived class.</span></span>

## <a name="two-ways-to-hide-a-variable"></a><span data-ttu-id="0b0be-110">Bir değişkeni gizlemek için iki yol</span><span class="sxs-lookup"><span data-stu-id="0b0be-110">Two Ways to Hide a Variable</span></span>

#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a><span data-ttu-id="0b0be-111">Bir değişkeni kapsam aracılığıyla gölgelendirerek gizlemek için</span><span class="sxs-lookup"><span data-stu-id="0b0be-111">To hide a variable by shadowing it through scope</span></span>

1. <span data-ttu-id="0b0be-112">Gizlemek istediğiniz değişkeni tanımlayan bölgeyi belirleme ve Değişkeninizle birlikte yeniden tanımlanacak bir alt bölge belirleme.</span><span class="sxs-lookup"><span data-stu-id="0b0be-112">Determine the region defining the variable you want to hide, and determine a subregion in which to redefine it with your variable.</span></span>

    |<span data-ttu-id="0b0be-113">Değişkenin bölgesi</span><span class="sxs-lookup"><span data-stu-id="0b0be-113">Variable's region</span></span>|<span data-ttu-id="0b0be-114">Yeniden tanımlama için izin verilen alt bölge</span><span class="sxs-lookup"><span data-stu-id="0b0be-114">Allowable subregion for redefining it</span></span>|
    |-----------------------|-------------------------------------------|
    |<span data-ttu-id="0b0be-115">Modül</span><span class="sxs-lookup"><span data-stu-id="0b0be-115">Module</span></span>|<span data-ttu-id="0b0be-116">Modül içindeki bir sınıf</span><span class="sxs-lookup"><span data-stu-id="0b0be-116">A class within the module</span></span>|
    |<span data-ttu-id="0b0be-117">Sınıf</span><span class="sxs-lookup"><span data-stu-id="0b0be-117">Class</span></span>|<span data-ttu-id="0b0be-118">Sınıf içindeki bir alt sınıf</span><span class="sxs-lookup"><span data-stu-id="0b0be-118">A subclass within the class</span></span><br /><br /> <span data-ttu-id="0b0be-119">Sınıf içindeki bir yordam</span><span class="sxs-lookup"><span data-stu-id="0b0be-119">A procedure within the class</span></span>|

    <span data-ttu-id="0b0be-120">Bu yordam içindeki bir blok içindeki bir yordam değişkenini, örneğin bir `If` ... `End If` inşaat veya bir döngüde yeniden tanımlayamazsınız `For` .</span><span class="sxs-lookup"><span data-stu-id="0b0be-120">You cannot redefine a procedure variable in a block within that procedure, for example in an `If`...`End If` construction or a `For` loop.</span></span>

2. <span data-ttu-id="0b0be-121">Zaten yoksa alt bölge oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0b0be-121">Create the subregion if it does not already exist.</span></span>

3. <span data-ttu-id="0b0be-122">Alt bölge içinde, gölgeleme değişkenini bildiren bir [Dim ekstresi](../../../language-reference/statements/dim-statement.md) yazın.</span><span class="sxs-lookup"><span data-stu-id="0b0be-122">Within the subregion, write a [Dim Statement](../../../language-reference/statements/dim-statement.md) declaring the shadowing variable.</span></span>

    <span data-ttu-id="0b0be-123">Alt bölge içindeki kod değişken adına başvurduğunda, derleyici, gölgeleme değişkeninin başvurusunu çözümler.</span><span class="sxs-lookup"><span data-stu-id="0b0be-123">When code inside the subregion refers to the variable name, the compiler resolves the reference to the shadowing variable.</span></span>

    <span data-ttu-id="0b0be-124">Aşağıdaki örnekte, kapsam aracılığıyla gölgeleme ve ayrıca, gölgelendirmeyi atlayan bir başvuru gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0b0be-124">The following example illustrates shadowing through scope, as well as a reference that bypasses the shadowing.</span></span>

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

    <span data-ttu-id="0b0be-125">Yukarıdaki örnek, değişkeni `num` hem modül düzeyinde hem de yordam düzeyinde (yordamda `show` ) bildirir.</span><span class="sxs-lookup"><span data-stu-id="0b0be-125">The preceding example declares the variable `num` both at module level and at procedure level (in the procedure `show`).</span></span> <span data-ttu-id="0b0be-126">Yerel değişken, `num` içinde modül düzeyi değişkeni gölgeler `num` , bu `show` nedenle yerel değişken 2 olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="0b0be-126">The local variable `num` shadows the module-level variable `num` within `show`, so the local variable is set to 2.</span></span> <span data-ttu-id="0b0be-127">Ancak, yordamda gölge için yerel bir değişken yoktur `num` `useModuleLevelNum` .</span><span class="sxs-lookup"><span data-stu-id="0b0be-127">However, there is no local variable to shadow `num` in the `useModuleLevelNum` procedure.</span></span> <span data-ttu-id="0b0be-128">Bu nedenle, `useModuleLevelNum` Modül düzeyi değişkeninin değerini 1 olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0b0be-128">Therefore, `useModuleLevelNum` sets the value of the module-level variable to 1.</span></span>

    <span data-ttu-id="0b0be-129">`MsgBox`İçindeki çağrı, `show` modül adıyla niteleyerek gölgeleme mekanizmasını atlar `num` .</span><span class="sxs-lookup"><span data-stu-id="0b0be-129">The `MsgBox` call inside `show` bypasses the shadowing mechanism by qualifying `num` with the module name.</span></span> <span data-ttu-id="0b0be-130">Bu nedenle, yerel değişken yerine modül düzeyi değişkeni görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0b0be-130">Therefore, it displays the module-level variable instead of the local variable.</span></span>

#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a><span data-ttu-id="0b0be-131">Bir değişkeni devralma yoluyla gölgelendirerek gizlemek için</span><span class="sxs-lookup"><span data-stu-id="0b0be-131">To hide a variable by shadowing it through inheritance</span></span>

1. <span data-ttu-id="0b0be-132">Gizlemek istediğiniz değişkenin bir sınıfta ve sınıf düzeyinde (herhangi bir yordam dışında) olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="0b0be-132">Be sure the variable you want to hide is declared in a class, and at class level (outside any procedure).</span></span> <span data-ttu-id="0b0be-133">Aksi takdirde, devralma aracılığıyla gölgelendiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b0be-133">Otherwise you cannot shadow it through inheritance.</span></span>

2. <span data-ttu-id="0b0be-134">Değişkenin sınıfından türetilmiş bir sınıfı, zaten mevcut değilse tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="0b0be-134">Define a class derived from the variable's class if one does not already exist.</span></span>

3. <span data-ttu-id="0b0be-135">Türetilmiş sınıfın içinde, `Dim` değişkeninizi bildiren bir ifade yazın.</span><span class="sxs-lookup"><span data-stu-id="0b0be-135">Inside the derived class, write a `Dim` statement declaring your variable.</span></span> <span data-ttu-id="0b0be-136">Bildirime [gölgeler](../../../language-reference/modifiers/shadows.md) anahtar sözcüğünü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0b0be-136">Include the [Shadows](../../../language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>

    <span data-ttu-id="0b0be-137">Türetilmiş sınıftaki kod, değişken adına başvurduğunda, derleyici değişkeninizin başvurusunu çözer.</span><span class="sxs-lookup"><span data-stu-id="0b0be-137">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>

    <span data-ttu-id="0b0be-138">Aşağıdaki örnek, devralma yoluyla gölgelendirmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b0be-138">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="0b0be-139">Biri, gölgeleme değişkenine erişen diğeri de gölgelendirmeyi atlayan iki başvuru yapar.</span><span class="sxs-lookup"><span data-stu-id="0b0be-139">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>

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

    <span data-ttu-id="0b0be-140">Önceki örnek, değişkeni `shadowString` temel sınıfta bildirir ve türetilmiş sınıfta gölgeleri.</span><span class="sxs-lookup"><span data-stu-id="0b0be-140">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="0b0be-141">`showStrings`Türetilmiş sınıftaki yordamda, ad uygun olmadığında dizenin gölgeleme sürümü görüntülenir `shadowString` .</span><span class="sxs-lookup"><span data-stu-id="0b0be-141">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="0b0be-142">Ardından, `shadowString` anahtar sözcüğü ile nitelendirilmeden gölgeli sürümü görüntüler `MyBase` .</span><span class="sxs-lookup"><span data-stu-id="0b0be-142">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="0b0be-143">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="0b0be-143">Robust Programming</span></span>

<span data-ttu-id="0b0be-144">Gölgeleme aynı ada sahip bir değişkenin birden fazla sürümünü tanıtır.</span><span class="sxs-lookup"><span data-stu-id="0b0be-144">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="0b0be-145">Bir kod açıklaması değişken adına başvurduğunda, derleyicinin başvuruyu çözümleyen sürüm, kod ifadesinin konumu ve uygun bir dizenin varlığı gibi faktörlere bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0b0be-145">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="0b0be-146">Bu, gölgelendirilmiş bir değişkenin istenmeyen bir sürümüne başvurma riskini artırabilir.</span><span class="sxs-lookup"><span data-stu-id="0b0be-146">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="0b0be-147">Gölgelendirilmiş bir değişkene tüm başvuruları tam olarak niteleyerek bu riski düşürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b0be-147">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="0b0be-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b0be-148">See also</span></span>

- [<span data-ttu-id="0b0be-149">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="0b0be-149">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="0b0be-150">Visual Basic'de Gölgeleme</span><span class="sxs-lookup"><span data-stu-id="0b0be-150">Shadowing in Visual Basic</span></span>](shadowing.md)
- [<span data-ttu-id="0b0be-151">Gölgeleme ve Geçersiz Kılma Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="0b0be-151">Differences Between Shadowing and Overriding</span></span>](differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="0b0be-152">Nasıl yapılır: Devralınmış Değişkeni Gizleme</span><span class="sxs-lookup"><span data-stu-id="0b0be-152">How to: Hide an Inherited Variable</span></span>](how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="0b0be-153">Nasıl yapılır: Türetilmiş Sınıf Tarafından Gizlenen Bir Değişkene Erişme</span><span class="sxs-lookup"><span data-stu-id="0b0be-153">How to: Access a Variable Hidden by a Derived Class</span></span>](how-to-access-a-variable-hidden-by-a-derived-class.md)
- [<span data-ttu-id="0b0be-154">Geçersiz Kılmalar</span><span class="sxs-lookup"><span data-stu-id="0b0be-154">Overrides</span></span>](../../../language-reference/modifiers/overrides.md)
- [<span data-ttu-id="0b0be-155">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="0b0be-155">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="0b0be-156">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="0b0be-156">Inheritance Basics</span></span>](../objects-and-classes/inheritance-basics.md)
