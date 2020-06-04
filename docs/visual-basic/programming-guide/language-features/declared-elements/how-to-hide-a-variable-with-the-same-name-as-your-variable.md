---
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
ms.openlocfilehash: c1f4c2fbf339358be77e76468b1db94616bf04a2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357238"
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a><span data-ttu-id="4f336-102">Nasıl yapılır: Değişkeninizle Aynı Adı Taşıyan Bir Değişkeni Gizleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f336-102">How to: Hide a Variable with the Same Name as Your Variable (Visual Basic)</span></span>

<span data-ttu-id="4f336-103">Bir değişkeni, aynı ada sahip bir değişkenle yeniden tanımlayarak, bir değeri *gölgelendirerek* gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f336-103">You can hide a variable by *shadowing* it, that is, by redefining it with a variable of the same name.</span></span> <span data-ttu-id="4f336-104">Gizlemek istediğiniz değişkeni iki şekilde gölgelendireseçebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4f336-104">You can shadow the variable you want to hide in two ways:</span></span>

- <span data-ttu-id="4f336-105">**Kapsam üzerinden gölgeleme.**</span><span class="sxs-lookup"><span data-stu-id="4f336-105">**Shadowing Through Scope.**</span></span> <span data-ttu-id="4f336-106">Onu, gizlemek istediğiniz değişkeni içeren bölgenin bir alt bölgesi içinde yeniden bildirerek kapsam aracılığıyla gölgelendirebilir.</span><span class="sxs-lookup"><span data-stu-id="4f336-106">You can shadow it through scope by redeclaring it inside a subregion of the region containing the variable you want to hide.</span></span>

- <span data-ttu-id="4f336-107">**Devralma yoluyla gölgeleme.**</span><span class="sxs-lookup"><span data-stu-id="4f336-107">**Shadowing Through Inheritance.**</span></span> <span data-ttu-id="4f336-108">Gizlemek istediğiniz değişken sınıf düzeyinde tanımlıysa, türetilmiş bir sınıftaki [Shadows](../../../language-reference/modifiers/shadows.md) anahtar sözcüğüyle yeniden bildirerek devralma yoluyla gölge oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f336-108">If the variable you want to hide is defined at class level, you can shadow it through inheritance by redeclaring it with the [Shadows](../../../language-reference/modifiers/shadows.md) keyword in a derived class.</span></span>

## <a name="two-ways-to-hide-a-variable"></a><span data-ttu-id="4f336-109">Bir değişkeni gizlemek için iki yol</span><span class="sxs-lookup"><span data-stu-id="4f336-109">Two Ways to Hide a Variable</span></span>

#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a><span data-ttu-id="4f336-110">Bir değişkeni kapsam aracılığıyla gölgelendirerek gizlemek için</span><span class="sxs-lookup"><span data-stu-id="4f336-110">To hide a variable by shadowing it through scope</span></span>

1. <span data-ttu-id="4f336-111">Gizlemek istediğiniz değişkeni tanımlayan bölgeyi belirleme ve Değişkeninizle birlikte yeniden tanımlanacak bir alt bölge belirleme.</span><span class="sxs-lookup"><span data-stu-id="4f336-111">Determine the region defining the variable you want to hide, and determine a subregion in which to redefine it with your variable.</span></span>

    |<span data-ttu-id="4f336-112">Değişkenin bölgesi</span><span class="sxs-lookup"><span data-stu-id="4f336-112">Variable's region</span></span>|<span data-ttu-id="4f336-113">Yeniden tanımlama için izin verilen alt bölge</span><span class="sxs-lookup"><span data-stu-id="4f336-113">Allowable subregion for redefining it</span></span>|
    |-----------------------|-------------------------------------------|
    |<span data-ttu-id="4f336-114">Modül</span><span class="sxs-lookup"><span data-stu-id="4f336-114">Module</span></span>|<span data-ttu-id="4f336-115">Modül içindeki bir sınıf</span><span class="sxs-lookup"><span data-stu-id="4f336-115">A class within the module</span></span>|
    |<span data-ttu-id="4f336-116">Sınıf</span><span class="sxs-lookup"><span data-stu-id="4f336-116">Class</span></span>|<span data-ttu-id="4f336-117">Sınıf içindeki bir alt sınıf</span><span class="sxs-lookup"><span data-stu-id="4f336-117">A subclass within the class</span></span><br /><br /> <span data-ttu-id="4f336-118">Sınıf içindeki bir yordam</span><span class="sxs-lookup"><span data-stu-id="4f336-118">A procedure within the class</span></span>|

    <span data-ttu-id="4f336-119">Bu yordam içindeki bir blok içindeki bir yordam değişkenini, örneğin bir `If` ... `End If` inşaat veya bir döngüde yeniden tanımlayamazsınız `For` .</span><span class="sxs-lookup"><span data-stu-id="4f336-119">You cannot redefine a procedure variable in a block within that procedure, for example in an `If`...`End If` construction or a `For` loop.</span></span>

2. <span data-ttu-id="4f336-120">Zaten yoksa alt bölge oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4f336-120">Create the subregion if it does not already exist.</span></span>

3. <span data-ttu-id="4f336-121">Alt bölge içinde, gölgeleme değişkenini bildiren bir [Dim ekstresi](../../../language-reference/statements/dim-statement.md) yazın.</span><span class="sxs-lookup"><span data-stu-id="4f336-121">Within the subregion, write a [Dim Statement](../../../language-reference/statements/dim-statement.md) declaring the shadowing variable.</span></span>

    <span data-ttu-id="4f336-122">Alt bölge içindeki kod değişken adına başvurduğunda, derleyici, gölgeleme değişkeninin başvurusunu çözümler.</span><span class="sxs-lookup"><span data-stu-id="4f336-122">When code inside the subregion refers to the variable name, the compiler resolves the reference to the shadowing variable.</span></span>

    <span data-ttu-id="4f336-123">Aşağıdaki örnekte, kapsam aracılığıyla gölgeleme ve ayrıca, gölgelendirmeyi atlayan bir başvuru gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4f336-123">The following example illustrates shadowing through scope, as well as a reference that bypasses the shadowing.</span></span>

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

    <span data-ttu-id="4f336-124">Yukarıdaki örnek, değişkeni `num` hem modül düzeyinde hem de yordam düzeyinde (yordamda `show` ) bildirir.</span><span class="sxs-lookup"><span data-stu-id="4f336-124">The preceding example declares the variable `num` both at module level and at procedure level (in the procedure `show`).</span></span> <span data-ttu-id="4f336-125">Yerel değişken, `num` içinde modül düzeyi değişkeni gölgeler `num` , bu `show` nedenle yerel değişken 2 olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="4f336-125">The local variable `num` shadows the module-level variable `num` within `show`, so the local variable is set to 2.</span></span> <span data-ttu-id="4f336-126">Ancak, yordamda gölge için yerel bir değişken yoktur `num` `useModuleLevelNum` .</span><span class="sxs-lookup"><span data-stu-id="4f336-126">However, there is no local variable to shadow `num` in the `useModuleLevelNum` procedure.</span></span> <span data-ttu-id="4f336-127">Bu nedenle, `useModuleLevelNum` Modül düzeyi değişkeninin değerini 1 olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4f336-127">Therefore, `useModuleLevelNum` sets the value of the module-level variable to 1.</span></span>

    <span data-ttu-id="4f336-128">`MsgBox`İçindeki çağrı, `show` modül adıyla niteleyerek gölgeleme mekanizmasını atlar `num` .</span><span class="sxs-lookup"><span data-stu-id="4f336-128">The `MsgBox` call inside `show` bypasses the shadowing mechanism by qualifying `num` with the module name.</span></span> <span data-ttu-id="4f336-129">Bu nedenle, yerel değişken yerine modül düzeyi değişkeni görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4f336-129">Therefore, it displays the module-level variable instead of the local variable.</span></span>

#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a><span data-ttu-id="4f336-130">Bir değişkeni devralma yoluyla gölgelendirerek gizlemek için</span><span class="sxs-lookup"><span data-stu-id="4f336-130">To hide a variable by shadowing it through inheritance</span></span>

1. <span data-ttu-id="4f336-131">Gizlemek istediğiniz değişkenin bir sınıfta ve sınıf düzeyinde (herhangi bir yordam dışında) olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="4f336-131">Be sure the variable you want to hide is declared in a class, and at class level (outside any procedure).</span></span> <span data-ttu-id="4f336-132">Aksi takdirde, devralma aracılığıyla gölgelendiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f336-132">Otherwise you cannot shadow it through inheritance.</span></span>

2. <span data-ttu-id="4f336-133">Değişkenin sınıfından türetilmiş bir sınıfı, zaten mevcut değilse tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="4f336-133">Define a class derived from the variable's class if one does not already exist.</span></span>

3. <span data-ttu-id="4f336-134">Türetilmiş sınıfın içinde, `Dim` değişkeninizi bildiren bir ifade yazın.</span><span class="sxs-lookup"><span data-stu-id="4f336-134">Inside the derived class, write a `Dim` statement declaring your variable.</span></span> <span data-ttu-id="4f336-135">Bildirime [gölgeler](../../../language-reference/modifiers/shadows.md) anahtar sözcüğünü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4f336-135">Include the [Shadows](../../../language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>

    <span data-ttu-id="4f336-136">Türetilmiş sınıftaki kod, değişken adına başvurduğunda, derleyici değişkeninizin başvurusunu çözer.</span><span class="sxs-lookup"><span data-stu-id="4f336-136">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>

    <span data-ttu-id="4f336-137">Aşağıdaki örnek, devralma yoluyla gölgelendirmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f336-137">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="4f336-138">Biri, gölgeleme değişkenine erişen diğeri de gölgelendirmeyi atlayan iki başvuru yapar.</span><span class="sxs-lookup"><span data-stu-id="4f336-138">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>

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

    <span data-ttu-id="4f336-139">Önceki örnek, değişkeni `shadowString` temel sınıfta bildirir ve türetilmiş sınıfta gölgeleri.</span><span class="sxs-lookup"><span data-stu-id="4f336-139">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="4f336-140">`showStrings`Türetilmiş sınıftaki yordamda, ad uygun olmadığında dizenin gölgeleme sürümü görüntülenir `shadowString` .</span><span class="sxs-lookup"><span data-stu-id="4f336-140">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="4f336-141">Ardından, `shadowString` anahtar sözcüğü ile nitelendirilmeden gölgeli sürümü görüntüler `MyBase` .</span><span class="sxs-lookup"><span data-stu-id="4f336-141">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="4f336-142">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="4f336-142">Robust Programming</span></span>

<span data-ttu-id="4f336-143">Gölgeleme aynı ada sahip bir değişkenin birden fazla sürümünü tanıtır.</span><span class="sxs-lookup"><span data-stu-id="4f336-143">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="4f336-144">Bir kod açıklaması değişken adına başvurduğunda, derleyicinin başvuruyu çözümleyen sürüm, kod ifadesinin konumu ve uygun bir dizenin varlığı gibi faktörlere bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="4f336-144">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="4f336-145">Bu, gölgelendirilmiş bir değişkenin istenmeyen bir sürümüne başvurma riskini artırabilir.</span><span class="sxs-lookup"><span data-stu-id="4f336-145">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="4f336-146">Gölgelendirilmiş bir değişkene tüm başvuruları tam olarak niteleyerek bu riski düşürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f336-146">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="4f336-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f336-147">See also</span></span>

- [<span data-ttu-id="4f336-148">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="4f336-148">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="4f336-149">Visual Basic'de Gölgeleme</span><span class="sxs-lookup"><span data-stu-id="4f336-149">Shadowing in Visual Basic</span></span>](shadowing.md)
- [<span data-ttu-id="4f336-150">Gölgeleme ve Geçersiz Kılma Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="4f336-150">Differences Between Shadowing and Overriding</span></span>](differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="4f336-151">Nasıl yapılır: Devralınmış Değişkeni Gizleme</span><span class="sxs-lookup"><span data-stu-id="4f336-151">How to: Hide an Inherited Variable</span></span>](how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="4f336-152">Nasıl yapılır: Türetilmiş Sınıf Tarafından Gizlenen Bir Değişkene Erişme</span><span class="sxs-lookup"><span data-stu-id="4f336-152">How to: Access a Variable Hidden by a Derived Class</span></span>](how-to-access-a-variable-hidden-by-a-derived-class.md)
- [<span data-ttu-id="4f336-153">Geçersiz Kılmalar</span><span class="sxs-lookup"><span data-stu-id="4f336-153">Overrides</span></span>](../../../language-reference/modifiers/overrides.md)
- [<span data-ttu-id="4f336-154">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="4f336-154">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="4f336-155">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="4f336-155">Inheritance Basics</span></span>](../objects-and-classes/inheritance-basics.md)
