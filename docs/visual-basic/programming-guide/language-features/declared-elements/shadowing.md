---
title: Visual Basic'de Gölgeleme
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], shadowing
- overriding, and shadowing
- shadowing
- duplicate names [Visual Basic]
- shadowing, by inheritance
- declared elements [Visual Basic], referencing
- shadowing, by scope
- declared elements [Visual Basic], hiding
- naming conflicts, shadowing
- declared elements [Visual Basic], shadowing
- shadowing, and overriding
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic], about
- objects [Visual Basic], names
- names [Visual Basic], shadowing
ms.assetid: 54bb4c25-12c4-4181-b4a0-93546053964e
ms.openlocfilehash: fde6259b67a8d963ed8c30b87c94029fb2658664
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656077"
---
# <a name="shadowing-in-visual-basic"></a><span data-ttu-id="19626-102">Visual Basic'de Gölgeleme</span><span class="sxs-lookup"><span data-stu-id="19626-102">Shadowing in Visual Basic</span></span>
<span data-ttu-id="19626-103">İki programlama öğeleri aynı adı paylaşan, bunlardan birini gizleyebilirsiniz, veya *gölge*, diğerinde.</span><span class="sxs-lookup"><span data-stu-id="19626-103">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="19626-104">Böyle bir durumda gölgeli öğesi başvurusu için kullanılabilir değil; kodunuzu öğe adı kullandığında, bunun yerine, Visual Basic derleyici gölgeleme öğesine çözer.</span><span class="sxs-lookup"><span data-stu-id="19626-104">In such a situation, the shadowed element is not available for reference; instead, when your code uses the element name, the Visual Basic compiler resolves it to the shadowing element.</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="19626-105">Amaç</span><span class="sxs-lookup"><span data-stu-id="19626-105">Purpose</span></span>  
 <span data-ttu-id="19626-106">Gölgeleme ana amacı, sınıf üyeleri tanımını korumaktır.</span><span class="sxs-lookup"><span data-stu-id="19626-106">The main purpose of shadowing is to protect the definition of your class members.</span></span> <span data-ttu-id="19626-107">Taban sınıf, bir önceden tanımlamış aynı ada sahip bir öğe oluşturan bir değişiklik uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="19626-107">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="19626-108">Bu durumda, `Shadows` değiştiricisi zorlar başvuran üyesine çözümlenmesi sınıfınız üzerinden tanımlanmış, yerine yeni bir temel sınıf öğesi için.</span><span class="sxs-lookup"><span data-stu-id="19626-108">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>  
  
## <a name="types-of-shadowing"></a><span data-ttu-id="19626-109">Gölgeleme türleri</span><span class="sxs-lookup"><span data-stu-id="19626-109">Types of Shadowing</span></span>  
 <span data-ttu-id="19626-110">Bir öğe başka bir öğe iki farklı şekilde gölge.</span><span class="sxs-lookup"><span data-stu-id="19626-110">An element can shadow another element in two different ways.</span></span> <span data-ttu-id="19626-111">Gölgeleme öğesi bir durumda gölgeleme gerçekleştirilir gölgeli öğeyi içeren bölge alt içinde bildirilebilir *kapsam aracılığıyla*.</span><span class="sxs-lookup"><span data-stu-id="19626-111">The shadowing element can be declared inside a subregion of the region containing the shadowed element, in which case the shadowing is accomplished *through scope*.</span></span> <span data-ttu-id="19626-112">Veya türetme sınıfı gölgeleme çalışması yapılır, bir taban sınıf üyesi tanımlayabilirsiniz *devralma yoluyla*.</span><span class="sxs-lookup"><span data-stu-id="19626-112">Or a deriving class can redefine a member of a base class, in which case the shadowing is done *through inheritance*.</span></span>  
  
### <a name="shadowing-through-scope"></a><span data-ttu-id="19626-113">Kapsam yoluyla gölgeleme</span><span class="sxs-lookup"><span data-stu-id="19626-113">Shadowing Through Scope</span></span>  
 <span data-ttu-id="19626-114">Programlama öğelerine modülü, sınıf veya aynı adlı ancak farklı bir kapsam için yapısı için mümkündür.</span><span class="sxs-lookup"><span data-stu-id="19626-114">It is possible for programming elements in the same module, class, or structure to have the same name but different scope.</span></span> <span data-ttu-id="19626-115">Bu şekilde iki öğe olarak bildirilen ve kod paylaştıkları adına başvuran daha dar kapsamlı öğesi başka bir öğenin shadows (blok kapsamı olan dar).</span><span class="sxs-lookup"><span data-stu-id="19626-115">When two elements are declared in this manner and the code refers to the name they share, the element with the narrower scope shadows the other element (block scope is the narrowest).</span></span>  
  
 <span data-ttu-id="19626-116">Örneğin, bir modül tanımlayabilirsiniz bir `Public` adlı değişken `temp`, ve bir yordam modülü içinde de adlı bir yerel değişken bildirebilir `temp`.</span><span class="sxs-lookup"><span data-stu-id="19626-116">For example, a module can define a `Public` variable named `temp`, and a procedure within the module can declare a local variable also named `temp`.</span></span> <span data-ttu-id="19626-117">Başvurular `temp` içinden yordamı erişim yerel değişken başvuruları sırasında `temp` gelen yordamı erişim dışında `Public` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="19626-117">References to `temp` from within the procedure access the local variable, while references to `temp` from outside the procedure access the `Public` variable.</span></span> <span data-ttu-id="19626-118">Bu durumda, yordam değişkeni `temp` modülü değişken shadows `temp`.</span><span class="sxs-lookup"><span data-stu-id="19626-118">In this case, the procedure variable `temp` shadows the module variable `temp`.</span></span>  
  
 <span data-ttu-id="19626-119">Aşağıdaki çizimde iki değişken gösterir, her ikisi de adlı `temp`.</span><span class="sxs-lookup"><span data-stu-id="19626-119">The following illustration shows two variables, both named `temp`.</span></span> <span data-ttu-id="19626-120">Yerel değişken `temp` üye değişkeni shadows `temp` kendi yordam içinde erişildiğinde `p`.</span><span class="sxs-lookup"><span data-stu-id="19626-120">The local variable `temp` shadows the member variable `temp` when accessed from within its own procedure `p`.</span></span> <span data-ttu-id="19626-121">Ancak, `MyClass` anahtar sözcüğü gölgeleme atlar ve üye değişkeni erişir.</span><span class="sxs-lookup"><span data-stu-id="19626-121">However, the `MyClass` keyword bypasses the shadowing and accesses the member variable.</span></span>  
  
 <span data-ttu-id="19626-122">![Kapsam yoluyla gölgeleme grafik diyagramı](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowscope.gif "ShadowScope")</span><span class="sxs-lookup"><span data-stu-id="19626-122">![Graphic diagram of shadowing through scope](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowscope.gif "ShadowScope")</span></span>  
<span data-ttu-id="19626-123">Kapsam yoluyla gölgeleme</span><span class="sxs-lookup"><span data-stu-id="19626-123">Shadowing through scope</span></span>  
  
 <span data-ttu-id="19626-124">Kapsam yoluyla gölgeleme ilişkin bir örnek için bkz: [nasıl yapılır: bilgisayarınızı değişken aynı ada sahip bir değişken Gizle](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span><span class="sxs-lookup"><span data-stu-id="19626-124">For an example of shadowing through scope, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span></span>  
  
### <a name="shadowing-through-inheritance"></a><span data-ttu-id="19626-125">Devralma yoluyla gölgeleme</span><span class="sxs-lookup"><span data-stu-id="19626-125">Shadowing Through Inheritance</span></span>  
 <span data-ttu-id="19626-126">Türetilmiş bir sınıf bir taban sınıftan devralınan bir programlama öğesi yeniden tanımlamaktadır, redefining öğesi özgün öğesi shadows.</span><span class="sxs-lookup"><span data-stu-id="19626-126">If a derived class redefines a programming element inherited from a base class, the redefining element shadows the original element.</span></span> <span data-ttu-id="19626-127">Bildirilen öğe herhangi bir türde veya aşırı yüklenmiş öğelerin herhangi bir türü ile gölge.</span><span class="sxs-lookup"><span data-stu-id="19626-127">You can shadow any type of declared element, or set of overloaded elements, with any other type.</span></span> <span data-ttu-id="19626-128">Örneğin, bir `Integer` değişkeni gölge bir `Function` yordamı.</span><span class="sxs-lookup"><span data-stu-id="19626-128">For example, an `Integer` variable can shadow a `Function` procedure.</span></span> <span data-ttu-id="19626-129">Başka bir yordam yordamla gölge, farklı parametre listesi ve farklı bir dönüş türü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19626-129">If you shadow a procedure with another procedure, you can use a different parameter list and a different return type.</span></span>  
  
 <span data-ttu-id="19626-130">Aşağıdaki çizimde bir taban sınıfı gösterir `b` ve türetilmiş bir sınıf `d` devraldığı `b`.</span><span class="sxs-lookup"><span data-stu-id="19626-130">The following illustration shows a base class `b` and a derived class `d` that inherits from `b`.</span></span> <span data-ttu-id="19626-131">Adlı bir yordam temel sınıf tanımlar `proc`, ve isteğe bağlı olarak türetilmiş sınıf ile aynı ada sahip başka bir yordam shadows.</span><span class="sxs-lookup"><span data-stu-id="19626-131">The base class defines a procedure named `proc`, and the derived class shadows it with another procedure of the same name.</span></span> <span data-ttu-id="19626-132">İlk `Call` deyimi erişen gölgeleme `proc` türetilen sınıfta.</span><span class="sxs-lookup"><span data-stu-id="19626-132">The first `Call` statement accesses the shadowing `proc` in the derived class.</span></span> <span data-ttu-id="19626-133">Ancak, `MyBase` anahtar sözcüğü gölgeleme atlar ve temel sınıfı gölgeli yordamda erişir.</span><span class="sxs-lookup"><span data-stu-id="19626-133">However, the `MyBase` keyword bypasses the shadowing and accesses the shadowed procedure in the base class.</span></span>  
  
 <span data-ttu-id="19626-134">![Devralma yoluyla gölgeleme grafik diyagramı](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowinherit.gif "ShadowInherit")</span><span class="sxs-lookup"><span data-stu-id="19626-134">![Graphic diagram of shadowing through inheritance](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowinherit.gif "ShadowInherit")</span></span>  
<span data-ttu-id="19626-135">Devralma yoluyla gölgeleme</span><span class="sxs-lookup"><span data-stu-id="19626-135">Shadowing through inheritance</span></span>  
  
 <span data-ttu-id="19626-136">Devralma yoluyla gölgeleme ilişkin bir örnek için bkz: [nasıl yapılır: bilgisayarınızı değişken aynı ada sahip bir değişken Gizle](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) ve [nasıl yapılır: bir devralınmış değişkeni gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).</span><span class="sxs-lookup"><span data-stu-id="19626-136">For an example of shadowing through inheritance, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) and [How to: Hide an Inherited Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).</span></span>  
  
#### <a name="shadowing-and-access-level"></a><span data-ttu-id="19626-137">Gölgeleme ve erişim düzeyi</span><span class="sxs-lookup"><span data-stu-id="19626-137">Shadowing and Access Level</span></span>  
 <span data-ttu-id="19626-138">Gölgeleme öğe her zaman koddan türetilmiş bir sınıf kullanarak erişilebilir değil.</span><span class="sxs-lookup"><span data-stu-id="19626-138">The shadowing element is not always accessible from the code using the derived class.</span></span> <span data-ttu-id="19626-139">Örneğin, bunu bildirilmesi `Private`.</span><span class="sxs-lookup"><span data-stu-id="19626-139">For example, it might be declared `Private`.</span></span> <span data-ttu-id="19626-140">Böyle bir durumda gölgeleme engellenmediğinden ve derleyici sahip aynı öğesine herhangi bir referans çözümler geliştirilmişse gölgeleme yok.</span><span class="sxs-lookup"><span data-stu-id="19626-140">In such a case, shadowing is defeated and the compiler resolves any reference to the same element it would have if there had been no shadowing.</span></span> <span data-ttu-id="19626-141">Bu öğe ve en az derivational adımları geriye doğru gölgeleme sınıfından erişilebilir öğedir.</span><span class="sxs-lookup"><span data-stu-id="19626-141">This element is the accessible element the fewest derivational steps backward from the shadowing class.</span></span> <span data-ttu-id="19626-142">Gölgeli öğesi bir yordam ise, çözümleme en yakın erişilebilir sürüme parametre listesi, aynı ada sahip olan ve dönüş türü.</span><span class="sxs-lookup"><span data-stu-id="19626-142">If the shadowed element is a procedure, the resolution is to the closest accessible version with the same name, parameter list, and return type.</span></span>  
  
 <span data-ttu-id="19626-143">Aşağıdaki örnekte, üç sınıf devralma hiyerarşisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="19626-143">The following example shows an inheritance hierarchy of three classes.</span></span> <span data-ttu-id="19626-144">Her sınıf tanımlayan bir `Sub` yordamı `display`, ve her türetilmiş sınıf gölgeleri `display` devralınabilir. taban sınıf yordamda.</span><span class="sxs-lookup"><span data-stu-id="19626-144">Each class defines a `Sub` procedure `display`, and each derived class shadows the `display` procedure in its base class.</span></span>  
  
```  
Public Class firstClass  
    Public Sub display()  
        MsgBox("This is firstClass")  
    End Sub  
End Class  
Public Class secondClass  
    Inherits firstClass  
    Private Shadows Sub display()  
        MsgBox("This is secondClass")  
    End Sub  
End Class  
Public Class thirdClass  
    Inherits secondClass  
    Public Shadows Sub display()  
        MsgBox("This is thirdClass")  
    End Sub  
End Class  
Module callDisplay  
    Dim first As New firstClass  
    Dim second As New secondClass  
    Dim third As New thirdClass  
    Public Sub callDisplayProcedures()  
        ' The following statement displays "This is firstClass".  
        first.display()  
        ' The following statement displays "This is firstClass".  
        second.display()  
        ' The following statement displays "This is thirdClass".  
        third.display()  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="19626-145">Önceki örnekte, türetilmiş sınıf `secondClass` gölgeleri `display` ile bir `Private` yordamı.</span><span class="sxs-lookup"><span data-stu-id="19626-145">In the preceding example, the derived class `secondClass` shadows `display` with a `Private` procedure.</span></span> <span data-ttu-id="19626-146">Zaman Modülü `callDisplay` çağrıları `display` içinde `secondClass`, çağrıyı yapan kod dışında `secondClass` ve bu nedenle özel erişemiyor `display` yordamı.</span><span class="sxs-lookup"><span data-stu-id="19626-146">When module `callDisplay` calls `display` in `secondClass`, the calling code is outside `secondClass` and therefore cannot access the private `display` procedure.</span></span> <span data-ttu-id="19626-147">Gölgeleme engellenmediğinden ve temel sınıfı referansı derleyici çözümler `display` yordamı.</span><span class="sxs-lookup"><span data-stu-id="19626-147">Shadowing is defeated, and the compiler resolves the reference to the base class `display` procedure.</span></span>  
  
 <span data-ttu-id="19626-148">Ancak, daha fazla türetilmiş sınıf `thirdClass` bildirir `display` olarak `Public`, bu nedenle kodda `callDisplay` erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="19626-148">However, the further derived class `thirdClass` declares `display` as `Public`, so the code in `callDisplay` can access it.</span></span>  
  
## <a name="shadowing-and-overriding"></a><span data-ttu-id="19626-149">Gölgeleme ve geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="19626-149">Shadowing and Overriding</span></span>  
 <span data-ttu-id="19626-150">Geçersiz kılma ile gölgeleme karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="19626-150">Do not confuse shadowing with overriding.</span></span> <span data-ttu-id="19626-151">Her ikisi de türetilmiş bir sınıf bir taban sınıfından devralıyor ve her ikisi de bildirilen bir öğe başka bir yeniden tanımlamanız olduğunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="19626-151">Both are used when a derived class inherits from a base class, and both redefine one declared element with another.</span></span> <span data-ttu-id="19626-152">Ancak ikisi arasındaki önemli farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="19626-152">But there are significant differences between the two.</span></span> <span data-ttu-id="19626-153">Bir karşılaştırması için bkz: [arasındaki farklar gölgeleme ve geçersiz kılınıyor](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).</span><span class="sxs-lookup"><span data-stu-id="19626-153">For a comparison, see [Differences Between Shadowing and Overriding](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).</span></span>  
  
## <a name="shadowing-and-overloading"></a><span data-ttu-id="19626-154">Gölgeleme ve aşırı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="19626-154">Shadowing and Overloading</span></span>  
 <span data-ttu-id="19626-155">Türetilen sınıfta birden fazla öğe ile aynı temel sınıfı öğesi gölge varsa, o öğenin aşırı yüklenmiş sürümler gölgeleme öğeleri olur.</span><span class="sxs-lookup"><span data-stu-id="19626-155">If you shadow the same base class element with more than one element in your derived class, the shadowing elements become overloaded versions of that element.</span></span> <span data-ttu-id="19626-156">Daha fazla bilgi için bkz: [yordam aşırı yüklemesi](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="19626-156">For more information, see [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span></span>  
  
## <a name="accessing-a-shadowed-element"></a><span data-ttu-id="19626-157">Gölgeli öğesi erişme</span><span class="sxs-lookup"><span data-stu-id="19626-157">Accessing a Shadowed Element</span></span>  
 <span data-ttu-id="19626-158">Türetilen bir sınıftan bir öğe eriştiğinizde, normalde bu türetilmiş sınıfının geçerli örneği aracılığıyla öğe adı ile niteleme tarafından bunu `Me` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="19626-158">When you access an element from a derived class, you normally do so through the current instance of that derived class, by qualifying the element name with the `Me` keyword.</span></span> <span data-ttu-id="19626-159">Türetilmiş sınıf temel sınıfı öğesinde shadows, kendisiyle niteleme temel sınıf öğesi erişebilir `MyBase` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="19626-159">If your derived class shadows the element in the base class, you can access the base class element by qualifying it with the `MyBase` keyword.</span></span>  
  
 <span data-ttu-id="19626-160">Gölgeli öğesi erişme ilişkin bir örnek için bkz: [nasıl yapılır: değişken gizli türetilmiş bir sınıf tarafından erişim](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="19626-160">For an example of accessing a shadowed element, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
### <a name="declaration-of-the-object-variable"></a><span data-ttu-id="19626-161">Nesne değişken bildirimi</span><span class="sxs-lookup"><span data-stu-id="19626-161">Declaration of the Object Variable</span></span>  
 <span data-ttu-id="19626-162">Nesne değişkeni oluşturma, ayrıca bir gölgeleme gölgeli öğesi veya türetilmiş bir sınıf erişen olup olmadığını etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="19626-162">How you create the object variable can also affect whether the derived class accesses a shadowing element or the shadowed element.</span></span> <span data-ttu-id="19626-163">Aşağıdaki örnekte iki nesne öğesinden türetilmiş bir sınıf oluşturur, ancak bir nesne temel sınıf ve türetilen sınıf olarak diğer olarak bildirilir.</span><span class="sxs-lookup"><span data-stu-id="19626-163">The following example creates two objects from a derived class, but one object is declared as the base class and the other as the derived class.</span></span>  
  
```  
Public Class baseCls  
    ' The following statement declares the element that is to be shadowed.  
    Public z As Integer = 100  
End Class  
Public Class dervCls  
    Inherits baseCls  
    ' The following statement declares the shadowing element.  
    Public Shadows z As String = "*"  
End Class  
Public Class useClasses  
    ' The following statement creates the object declared as the base class.  
    Dim basObj As baseCls = New dervCls()  
    ' Note that dervCls widens to its base class baseCls.  
    ' The following statement creates the object declared as the derived class.  
    Dim derObj As dervCls = New dervCls()  
    Public Sub showZ()   
    ' The following statement outputs 100 (the shadowed element).  
        MsgBox("Accessed through base class: " & basObj.z)  
    ' The following statement outputs "*" (the shadowing element).  
        MsgBox("Accessed through derived class: " & derObj.z)  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="19626-164">Önceki örnekte, değişken `basObj` temel sınıf olarak bildirilmedi.</span><span class="sxs-lookup"><span data-stu-id="19626-164">In the preceding example, the variable `basObj` is declared as the base class.</span></span> <span data-ttu-id="19626-165">Atama bir `dervCls` nesnesiyle Genişletme dönüşümü oluşturduğunu ve bu nedenle geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="19626-165">Assigning a `dervCls` object to it constitutes a widening conversion and is therefore valid.</span></span> <span data-ttu-id="19626-166">Ancak, temel sınıf değişkeni gölgeleme sürümü erişemiyor `z` türetilen sınıfta bu nedenle derleyici çözümler `basObj.z` özgün temel sınıf değerine.</span><span class="sxs-lookup"><span data-stu-id="19626-166">However, the base class cannot access the shadowing version of the variable `z` in the derived class, so the compiler resolves `basObj.z` to the original base class value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19626-167">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="19626-167">See Also</span></span>  
 [<span data-ttu-id="19626-168">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="19626-168">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="19626-169">Visual Basic'de kapsam</span><span class="sxs-lookup"><span data-stu-id="19626-169">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [<span data-ttu-id="19626-170">Genişletme ve Daraltma Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="19626-170">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="19626-171">Shadows</span><span class="sxs-lookup"><span data-stu-id="19626-171">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="19626-172">Overrides</span><span class="sxs-lookup"><span data-stu-id="19626-172">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="19626-173">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="19626-173">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="19626-174">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="19626-174">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
