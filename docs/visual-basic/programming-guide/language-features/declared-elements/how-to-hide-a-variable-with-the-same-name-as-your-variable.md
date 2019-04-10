---
title: 'Nasıl yapılır: Değişkeninizin (Visual Basic) aynı ada sahip bir değişkeni gizleme'
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
ms.openlocfilehash: 744c7aed50690d5591d1e8248e121cb66ef39108
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296192"
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a><span data-ttu-id="80808-102">Nasıl yapılır: Değişkeninizin (Visual Basic) aynı ada sahip bir değişkeni gizleme</span><span class="sxs-lookup"><span data-stu-id="80808-102">How to: Hide a Variable with the Same Name as Your Variable (Visual Basic)</span></span>
<span data-ttu-id="80808-103">Bir değişken gizleyebilirsiniz *gölgeleme* , diğer bir deyişle, aynı ada sahip bir değişken tanımlayarak tarafından.</span><span class="sxs-lookup"><span data-stu-id="80808-103">You can hide a variable by *shadowing* it, that is, by redefining it with a variable of the same name.</span></span> <span data-ttu-id="80808-104">İki yolla gizlemek istediğiniz değişkeni gölge:</span><span class="sxs-lookup"><span data-stu-id="80808-104">You can shadow the variable you want to hide in two ways:</span></span>  
  
-   **<span data-ttu-id="80808-105">Kapsam yoluyla gölgeleme.</span><span class="sxs-lookup"><span data-stu-id="80808-105">Shadowing Through Scope.</span></span>** <span data-ttu-id="80808-106">Bu kapsam yoluyla bir öğe alt bölgesini gizlemek istediğiniz değişkeni içeren bir bölge içinde redeclaring tarafından gölge.</span><span class="sxs-lookup"><span data-stu-id="80808-106">You can shadow it through scope by redeclaring it inside a subregion of the region containing the variable you want to hide.</span></span>  
  
-   **<span data-ttu-id="80808-107">Devralma üzerinden gölgeleme.</span><span class="sxs-lookup"><span data-stu-id="80808-107">Shadowing Through Inheritance.</span></span>** <span data-ttu-id="80808-108">Gizlemek istediğiniz değişken sınıf düzeyinde tanımlanmışsa, bu devralma yoluyla birlikte redeclaring gölge [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) anahtar sözcüğü türetilmiş bir sınıf içinde.</span><span class="sxs-lookup"><span data-stu-id="80808-108">If the variable you want to hide is defined at class level, you can shadow it through inheritance by redeclaring it with the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in a derived class.</span></span>  
  
## <a name="two-ways-to-hide-a-variable"></a><span data-ttu-id="80808-109">Bir değişkeni gizleme için iki yol</span><span class="sxs-lookup"><span data-stu-id="80808-109">Two Ways to Hide a Variable</span></span>  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a><span data-ttu-id="80808-110">Bir değişken kapsam yoluyla gölgeleme tarafından gizlemek için</span><span class="sxs-lookup"><span data-stu-id="80808-110">To hide a variable by shadowing it through scope</span></span>  
  
1. <span data-ttu-id="80808-111">Gizlemek istediğiniz değişken tanımlama bölgeyi belirlemeye ve burada, değişkenle tanımlanacak bir öğe alt bölgesini belirler.</span><span class="sxs-lookup"><span data-stu-id="80808-111">Determine the region defining the variable you want to hide, and determine a subregion in which to redefine it with your variable.</span></span>  
  
    |<span data-ttu-id="80808-112">Değişkenin bölge</span><span class="sxs-lookup"><span data-stu-id="80808-112">Variable's region</span></span>|<span data-ttu-id="80808-113">Bunu yeniden tanımlama için izin verilen öğe alt bölgesini</span><span class="sxs-lookup"><span data-stu-id="80808-113">Allowable subregion for redefining it</span></span>|  
    |-----------------------|-------------------------------------------|  
    |<span data-ttu-id="80808-114">Modül</span><span class="sxs-lookup"><span data-stu-id="80808-114">Module</span></span>|<span data-ttu-id="80808-115">Modüldeki bir sınıfı</span><span class="sxs-lookup"><span data-stu-id="80808-115">A class within the module</span></span>|  
    |<span data-ttu-id="80808-116">örneği</span><span class="sxs-lookup"><span data-stu-id="80808-116">Class</span></span>|<span data-ttu-id="80808-117">Sınıf içindeki bir alt sınıfı</span><span class="sxs-lookup"><span data-stu-id="80808-117">A subclass within the class</span></span><br /><br /> <span data-ttu-id="80808-118">Bir yordam içinde sınıfı</span><span class="sxs-lookup"><span data-stu-id="80808-118">A procedure within the class</span></span>|  
  
     <span data-ttu-id="80808-119">Bu yordamdaki bir blok içinde bir yordam değişken Örneğin içinde tanımlanamaz bir `If`... `End If` oluşturma veya `For` döngü.</span><span class="sxs-lookup"><span data-stu-id="80808-119">You cannot redefine a procedure variable in a block within that procedure, for example in an `If`...`End If` construction or a `For` loop.</span></span>  
  
2. <span data-ttu-id="80808-120">Zaten yoksa, öğe alt bölgesini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="80808-120">Create the subregion if it does not already exist.</span></span>  
  
3. <span data-ttu-id="80808-121">Öğe alt bölgesini içinde yazma bir [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) gölgeleme değişken bildirme.</span><span class="sxs-lookup"><span data-stu-id="80808-121">Within the subregion, write a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) declaring the shadowing variable.</span></span>  
  
     <span data-ttu-id="80808-122">Öğe alt bölgesini içinde kod değişkenin adı başvurduğunda, derleyicinin gölgeleme değişkenine başvuru çözümler.</span><span class="sxs-lookup"><span data-stu-id="80808-122">When code inside the subregion refers to the variable name, the compiler resolves the reference to the shadowing variable.</span></span>  
  
     <span data-ttu-id="80808-123">Aşağıdaki örnek, kapsam yanı sıra gölgeleme atlar bir başvuru gölgeleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="80808-123">The following example illustrates shadowing through scope, as well as a reference that bypasses the shadowing.</span></span>  
  
    ```  
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
  
     <span data-ttu-id="80808-124">Yukarıdaki örnekte değişkeni bildirir `num` Modül düzeyinde ve yordamı düzeyinde (yordamda `show`).</span><span class="sxs-lookup"><span data-stu-id="80808-124">The preceding example declares the variable `num` both at module level and at procedure level (in the procedure `show`).</span></span> <span data-ttu-id="80808-125">Yerel değişken `num` Modül düzeyinde bir değişkene gölgeleri `num` içinde `show`, yerel değişken 2'ye ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="80808-125">The local variable `num` shadows the module-level variable `num` within `show`, so the local variable is set to 2.</span></span> <span data-ttu-id="80808-126">Ancak, hiçbir gölge yerel bir değişkene yoktur `num` içinde `useModuleLevelNum` yordamı.</span><span class="sxs-lookup"><span data-stu-id="80808-126">However, there is no local variable to shadow `num` in the `useModuleLevelNum` procedure.</span></span> <span data-ttu-id="80808-127">Bu nedenle, `useModuleLevelNum` Modül düzeyinde değişkeninin değeri 1'e ayarlar.</span><span class="sxs-lookup"><span data-stu-id="80808-127">Therefore, `useModuleLevelNum` sets the value of the module-level variable to 1.</span></span>  
  
     <span data-ttu-id="80808-128">`MsgBox` İçinde çağrı `show` sağladığı gölgeleme mekanizması atlar `num` modül adı ile.</span><span class="sxs-lookup"><span data-stu-id="80808-128">The `MsgBox` call inside `show` bypasses the shadowing mechanism by qualifying `num` with the module name.</span></span> <span data-ttu-id="80808-129">Bu nedenle, yerel değişken yerine Modül düzeyinde değişkeni görüntüler.</span><span class="sxs-lookup"><span data-stu-id="80808-129">Therefore, it displays the module-level variable instead of the local variable.</span></span>  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a><span data-ttu-id="80808-130">Bir değişken devralma yoluyla gölgeleme tarafından gizlemek için</span><span class="sxs-lookup"><span data-stu-id="80808-130">To hide a variable by shadowing it through inheritance</span></span>  
  
1. <span data-ttu-id="80808-131">Gizlemek istediğiniz değişkeni, bir sınıf ve sınıf düzeyinde (dışında herhangi bir yordam) bildirildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="80808-131">Be sure the variable you want to hide is declared in a class, and at class level (outside any procedure).</span></span> <span data-ttu-id="80808-132">Aksi takdirde, devralma yoluyla gölgeleyemez.</span><span class="sxs-lookup"><span data-stu-id="80808-132">Otherwise you cannot shadow it through inheritance.</span></span>  
  
2. <span data-ttu-id="80808-133">Henüz mevcut değilse, değişkenin sınıfından türetilen bir sınıf tanımlar.</span><span class="sxs-lookup"><span data-stu-id="80808-133">Define a class derived from the variable's class if one does not already exist.</span></span>  
  
3. <span data-ttu-id="80808-134">Türetilmiş sınıf içinde yazma bir `Dim` deyimi, değişken bildirme.</span><span class="sxs-lookup"><span data-stu-id="80808-134">Inside the derived class, write a `Dim` statement declaring your variable.</span></span> <span data-ttu-id="80808-135">Dahil [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) bildirimindeki anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="80808-135">Include the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>  
  
     <span data-ttu-id="80808-136">Türetilmiş sınıftaki kod değişken adıdır, derleyici Değişkeninizi başvuruyu çözümler.</span><span class="sxs-lookup"><span data-stu-id="80808-136">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>  
  
     <span data-ttu-id="80808-137">Aşağıdaki örnek, devralma yoluyla gölgeleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="80808-137">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="80808-138">İki başvuru, gölgelendirme değişkeni erişen diğeri, gölgeleme atlar kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="80808-138">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>  
  
    ```  
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
  
     <span data-ttu-id="80808-139">Yukarıdaki örnekte değişkeni bildirir `shadowString` temel sınıf ve türetilen sınıfta gölgeliyor.</span><span class="sxs-lookup"><span data-stu-id="80808-139">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="80808-140">Yordamı `showStrings` türetilmiş bir sınıf içindeki dize gölgeleme sürümünü görüntüler, ad `shadowString` yetkili değil.</span><span class="sxs-lookup"><span data-stu-id="80808-140">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="80808-141">Ardından gölgeli sürüm görüntüler, `shadowString` ile tam olduğundan `MyBase` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="80808-141">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="80808-142">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="80808-142">Robust Programming</span></span>  
 <span data-ttu-id="80808-143">Gölgeleme, bir değişken aynı ada sahip birden fazla sürümünü tanıtır.</span><span class="sxs-lookup"><span data-stu-id="80808-143">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="80808-144">Kod açıklaması değişken adıdır, derleyici başvurusu açığını giderir sürüm kod açıklaması konumunu ve uygun bir dize varlığını gibi faktörlere bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="80808-144">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="80808-145">Bu gölgeli bir değişkenin istenmeyen bir sürüme başvuran riskini artırabilir.</span><span class="sxs-lookup"><span data-stu-id="80808-145">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="80808-146">Bu riski tam olarak gölgeli bir değişken tüm başvurularını uygun tarafından düşürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80808-146">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80808-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80808-147">See also</span></span>

- [<span data-ttu-id="80808-148">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="80808-148">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="80808-149">Visual Basic'de Gölgeleme</span><span class="sxs-lookup"><span data-stu-id="80808-149">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="80808-150">Gölgeleme ve Geçersiz Kılma Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="80808-150">Differences Between Shadowing and Overriding</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="80808-151">Nasıl yapılır: Devralınmış Değişkeni Gizleme</span><span class="sxs-lookup"><span data-stu-id="80808-151">How to: Hide an Inherited Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="80808-152">Nasıl yapılır: Türetilmiş Sınıf Tarafından Gizlenen Bir Değişkene Erişme</span><span class="sxs-lookup"><span data-stu-id="80808-152">How to: Access a Variable Hidden by a Derived Class</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [<span data-ttu-id="80808-153">Geçersiz Kılmalar</span><span class="sxs-lookup"><span data-stu-id="80808-153">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="80808-154">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="80808-154">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="80808-155">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="80808-155">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
