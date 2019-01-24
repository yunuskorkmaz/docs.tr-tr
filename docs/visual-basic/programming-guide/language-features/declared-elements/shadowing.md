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
ms.openlocfilehash: 6ac973493b67fa15ca935f61bbb8e5c07bda1e0f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580869"
---
# <a name="shadowing-in-visual-basic"></a><span data-ttu-id="154c8-102">Visual Basic'de Gölgeleme</span><span class="sxs-lookup"><span data-stu-id="154c8-102">Shadowing in Visual Basic</span></span>
<span data-ttu-id="154c8-103">Bunlardan biri, iki programlama öğeleri aynı adı paylaşan, gizleyebilirsiniz, veya *gölge*, diğerinde.</span><span class="sxs-lookup"><span data-stu-id="154c8-103">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="154c8-104">Böyle bir durumda gölgeli öğe başvuru için kullanılabilir değildir; Bunun yerine, kodunuzu öğe adı kullandığında, Visual Basic Derleyicisi, gölgelendirme öğesine çözümler.</span><span class="sxs-lookup"><span data-stu-id="154c8-104">In such a situation, the shadowed element is not available for reference; instead, when your code uses the element name, the Visual Basic compiler resolves it to the shadowing element.</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="154c8-105">Amaç</span><span class="sxs-lookup"><span data-stu-id="154c8-105">Purpose</span></span>  
 <span data-ttu-id="154c8-106">Gölgeleme ana amacı, sınıf üyelerinin tanımına korunmasını sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="154c8-106">The main purpose of shadowing is to protect the definition of your class members.</span></span> <span data-ttu-id="154c8-107">Temel sınıf olarak zaten tanımlanmış aynı ada sahip bir öğe oluşturan bir değişiklik uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="154c8-107">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="154c8-108">Böyle bir durumda `Shadows` değiştiricisi zorlar başvuruyor, sınıf üyesine çözümlenmesi aracılığıyla tanımlanmış, yerine yeni bir temel sınıf öğe için.</span><span class="sxs-lookup"><span data-stu-id="154c8-108">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>  
  
## <a name="types-of-shadowing"></a><span data-ttu-id="154c8-109">Tür gölgeleme</span><span class="sxs-lookup"><span data-stu-id="154c8-109">Types of Shadowing</span></span>  
 <span data-ttu-id="154c8-110">Bir öğe başka bir öğeye iki farklı şekilde gölge.</span><span class="sxs-lookup"><span data-stu-id="154c8-110">An element can shadow another element in two different ways.</span></span> <span data-ttu-id="154c8-111">Gölgeleme öğesi bir alt bölgeli gölgeleme çalışması gerçekleştirilir gölgeli öğe içeren bölgenin içinde bildirilebilir *kapsam aracılığıyla*.</span><span class="sxs-lookup"><span data-stu-id="154c8-111">The shadowing element can be declared inside a subregion of the region containing the shadowed element, in which case the shadowing is accomplished *through scope*.</span></span> <span data-ttu-id="154c8-112">Veya bir türetilen sınıf gölgeleme çalışması yapılır bir taban sınıfın üyesi bulunabileceğini belirleyebileceğiniz manasına *devralma yoluyla*.</span><span class="sxs-lookup"><span data-stu-id="154c8-112">Or a deriving class can redefine a member of a base class, in which case the shadowing is done *through inheritance*.</span></span>  
  
### <a name="shadowing-through-scope"></a><span data-ttu-id="154c8-113">Kapsam yoluyla gölgeleme</span><span class="sxs-lookup"><span data-stu-id="154c8-113">Shadowing Through Scope</span></span>  
 <span data-ttu-id="154c8-114">Bu modül, sınıf veya yapı aynı ada ancak farklı bir kapsam için öğeleri programlama için mümkündür.</span><span class="sxs-lookup"><span data-stu-id="154c8-114">It is possible for programming elements in the same module, class, or structure to have the same name but different scope.</span></span> <span data-ttu-id="154c8-115">İki öğe, bu şekilde bildirilir ve kod paylaştıkları adıdır, başka bir öğenin öğe daha dar kapsamlı gölgeleri (blok kapsamı olan en düşük).</span><span class="sxs-lookup"><span data-stu-id="154c8-115">When two elements are declared in this manner and the code refers to the name they share, the element with the narrower scope shadows the other element (block scope is the narrowest).</span></span>  
  
 <span data-ttu-id="154c8-116">Örneğin, bir modül tanımlayabilirsiniz bir `Public` adlı değişken `temp`, ve bir yordamda bir modül olarak da adlandırılan bir yerel değişken bildirebilirsiniz `temp`.</span><span class="sxs-lookup"><span data-stu-id="154c8-116">For example, a module can define a `Public` variable named `temp`, and a procedure within the module can declare a local variable also named `temp`.</span></span> <span data-ttu-id="154c8-117">Başvurular `temp` yordam başvurularını sırasında yerel değişken içinden erişmek `temp` gelen yordamı erişim dışında `Public` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="154c8-117">References to `temp` from within the procedure access the local variable, while references to `temp` from outside the procedure access the `Public` variable.</span></span> <span data-ttu-id="154c8-118">Bu durumda, yordam değişken `temp` modülü değişken gölgeleri `temp`.</span><span class="sxs-lookup"><span data-stu-id="154c8-118">In this case, the procedure variable `temp` shadows the module variable `temp`.</span></span>  
  
 <span data-ttu-id="154c8-119">İki değişken aşağıdaki çizimde, hem adlandırılmış `temp`.</span><span class="sxs-lookup"><span data-stu-id="154c8-119">The following illustration shows two variables, both named `temp`.</span></span> <span data-ttu-id="154c8-120">Yerel değişken `temp` üye değişkeni gölgeleri `temp` kendi yordam içinde erişildiğinde `p`.</span><span class="sxs-lookup"><span data-stu-id="154c8-120">The local variable `temp` shadows the member variable `temp` when accessed from within its own procedure `p`.</span></span> <span data-ttu-id="154c8-121">Ancak, `MyClass` anahtar sözcüğü gölgeleme atlar ve üye değişkeni erişir.</span><span class="sxs-lookup"><span data-stu-id="154c8-121">However, the `MyClass` keyword bypasses the shadowing and accesses the member variable.</span></span>  
  
 <span data-ttu-id="154c8-122">![Kapsam yoluyla gölgeleme grafik diyagramı](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowscope.gif "ShadowScope")</span><span class="sxs-lookup"><span data-stu-id="154c8-122">![Graphic diagram of shadowing through scope](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowscope.gif "ShadowScope")</span></span>  
<span data-ttu-id="154c8-123">Kapsam yoluyla gölgeleme</span><span class="sxs-lookup"><span data-stu-id="154c8-123">Shadowing through scope</span></span>  
  
 <span data-ttu-id="154c8-124">Kapsam yoluyla gölgeleme ilişkin bir örnek için bkz [nasıl yapılır: Değişkeninizle aynı ada sahip bir değişkeni gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span><span class="sxs-lookup"><span data-stu-id="154c8-124">For an example of shadowing through scope, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span></span>  
  
### <a name="shadowing-through-inheritance"></a><span data-ttu-id="154c8-125">Devralma üzerinden gölgeleme</span><span class="sxs-lookup"><span data-stu-id="154c8-125">Shadowing Through Inheritance</span></span>  
 <span data-ttu-id="154c8-126">Türetilmiş bir sınıf bir temel sınıftan devralınan bir programlama öğesi'ı yeniden tanımladığı, özgün öğe redefining öğesi gölgeliyor.</span><span class="sxs-lookup"><span data-stu-id="154c8-126">If a derived class redefines a programming element inherited from a base class, the redefining element shadows the original element.</span></span> <span data-ttu-id="154c8-127">Herhangi bir türü ile herhangi bir türde bildirilen öğe veya aşırı yüklenmiş öğeleri kümesi gölge.</span><span class="sxs-lookup"><span data-stu-id="154c8-127">You can shadow any type of declared element, or set of overloaded elements, with any other type.</span></span> <span data-ttu-id="154c8-128">Örneğin, bir `Integer` değişkeni gölge bir `Function` yordamı.</span><span class="sxs-lookup"><span data-stu-id="154c8-128">For example, an `Integer` variable can shadow a `Function` procedure.</span></span> <span data-ttu-id="154c8-129">Başka bir yordam içeren bir yordamı gölge, başka bir parametre listesi ve farklı bir dönüş türü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="154c8-129">If you shadow a procedure with another procedure, you can use a different parameter list and a different return type.</span></span>  
  
 <span data-ttu-id="154c8-130">Aşağıdaki çizimde bir temel sınıf `b` ve türetilmiş bir sınıf `d` öğesinden devralan `b`.</span><span class="sxs-lookup"><span data-stu-id="154c8-130">The following illustration shows a base class `b` and a derived class `d` that inherits from `b`.</span></span> <span data-ttu-id="154c8-131">Adlı bir yordam temel sınıf tanımlar `proc`, ve isteğe bağlı olarak türetilmiş bir sınıf ile aynı ada sahip başka bir yordam gölgeliyor.</span><span class="sxs-lookup"><span data-stu-id="154c8-131">The base class defines a procedure named `proc`, and the derived class shadows it with another procedure of the same name.</span></span> <span data-ttu-id="154c8-132">İlk `Call` deyimi erişen gölgeleme `proc` türetilen sınıfta.</span><span class="sxs-lookup"><span data-stu-id="154c8-132">The first `Call` statement accesses the shadowing `proc` in the derived class.</span></span> <span data-ttu-id="154c8-133">Ancak, `MyBase` anahtar sözcüğü gölgeleme atlar ve temel sınıfta gölgeli yordamı erişir.</span><span class="sxs-lookup"><span data-stu-id="154c8-133">However, the `MyBase` keyword bypasses the shadowing and accesses the shadowed procedure in the base class.</span></span>  
  
 <span data-ttu-id="154c8-134">![Devralma üzerinden gölgeleme grafik diyagramı](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowinherit.gif "ShadowInherit")</span><span class="sxs-lookup"><span data-stu-id="154c8-134">![Graphic diagram of shadowing through inheritance](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowinherit.gif "ShadowInherit")</span></span>  
<span data-ttu-id="154c8-135">Devralma üzerinden gölgeleme</span><span class="sxs-lookup"><span data-stu-id="154c8-135">Shadowing through inheritance</span></span>  
  
 <span data-ttu-id="154c8-136">Devralma üzerinden gölgeleme ilişkin bir örnek için bkz [nasıl yapılır: Değişkeninizle aynı ada sahip bir değişkeni gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) ve [nasıl yapılır: Devralınmış değişkeni gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).</span><span class="sxs-lookup"><span data-stu-id="154c8-136">For an example of shadowing through inheritance, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) and [How to: Hide an Inherited Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).</span></span>  
  
#### <a name="shadowing-and-access-level"></a><span data-ttu-id="154c8-137">Gölgeleme ve erişim düzeyi</span><span class="sxs-lookup"><span data-stu-id="154c8-137">Shadowing and Access Level</span></span>  
 <span data-ttu-id="154c8-138">Gölgeleme öğe her zaman türetilen sınıfın kullanarak koddan erişilebilir değil.</span><span class="sxs-lookup"><span data-stu-id="154c8-138">The shadowing element is not always accessible from the code using the derived class.</span></span> <span data-ttu-id="154c8-139">Örneğin, bu bildirilmesi `Private`.</span><span class="sxs-lookup"><span data-stu-id="154c8-139">For example, it might be declared `Private`.</span></span> <span data-ttu-id="154c8-140">Böyle bir durumda gölgeleme engellenmediğinden ve aynı öğeye sahip herhangi bir referans derleyici çözümler geliştirilmişse gölgeleme yok.</span><span class="sxs-lookup"><span data-stu-id="154c8-140">In such a case, shadowing is defeated and the compiler resolves any reference to the same element it would have if there had been no shadowing.</span></span> <span data-ttu-id="154c8-141">Bu öğe en az derivational adımları geri gölgeleme sınıftan erişilebilir öğedir.</span><span class="sxs-lookup"><span data-stu-id="154c8-141">This element is the accessible element the fewest derivational steps backward from the shadowing class.</span></span> <span data-ttu-id="154c8-142">Gölgeli öğe bir yordam varsa çözümleme en yakın erişilebilir sürüme, parametre listesi, aynı ada sahip olan ve dönüş türü.</span><span class="sxs-lookup"><span data-stu-id="154c8-142">If the shadowed element is a procedure, the resolution is to the closest accessible version with the same name, parameter list, and return type.</span></span>  
  
 <span data-ttu-id="154c8-143">Aşağıdaki örnek, üç sınıfların Devralma Hiyerarşisi gösterir.</span><span class="sxs-lookup"><span data-stu-id="154c8-143">The following example shows an inheritance hierarchy of three classes.</span></span> <span data-ttu-id="154c8-144">Her bir sınıf tanımlayan bir `Sub` yordamı `display`, ve her bir türetilmiş sınıf shadows `display` yordamı temel sınıfındaki.</span><span class="sxs-lookup"><span data-stu-id="154c8-144">Each class defines a `Sub` procedure `display`, and each derived class shadows the `display` procedure in its base class.</span></span>  
  
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
  
 <span data-ttu-id="154c8-145">Yukarıdaki örnekte, türetilen sınıfın `secondClass` shadows `display` ile bir `Private` yordamı.</span><span class="sxs-lookup"><span data-stu-id="154c8-145">In the preceding example, the derived class `secondClass` shadows `display` with a `Private` procedure.</span></span> <span data-ttu-id="154c8-146">Zaman Modülü `callDisplay` çağrıları `display` içinde `secondClass`, çağıran kodun dışında `secondClass` ve özel etkinleştirilemez `display` yordamı.</span><span class="sxs-lookup"><span data-stu-id="154c8-146">When module `callDisplay` calls `display` in `secondClass`, the calling code is outside `secondClass` and therefore cannot access the private `display` procedure.</span></span> <span data-ttu-id="154c8-147">Gölgeleme engellenmediğinden ve derleyicinin temel sınıf başvurusunu çözümler `display` yordamı.</span><span class="sxs-lookup"><span data-stu-id="154c8-147">Shadowing is defeated, and the compiler resolves the reference to the base class `display` procedure.</span></span>  
  
 <span data-ttu-id="154c8-148">Ancak, daha fazla türetilmiş sınıf `thirdClass` bildirir `display` olarak `Public`, bu nedenle kodda `callDisplay` buna erişebilir.</span><span class="sxs-lookup"><span data-stu-id="154c8-148">However, the further derived class `thirdClass` declares `display` as `Public`, so the code in `callDisplay` can access it.</span></span>  
  
## <a name="shadowing-and-overriding"></a><span data-ttu-id="154c8-149">Gölgeleme ve geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="154c8-149">Shadowing and Overriding</span></span>  
 <span data-ttu-id="154c8-150">Geçersiz kılma ile gölgeleme karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="154c8-150">Do not confuse shadowing with overriding.</span></span> <span data-ttu-id="154c8-151">Her ikisi de bir temel sınıftan türetilmiş bir sınıf devralır ve her ikisini de diğerine ile bildirilen bir öğe yeniden kullanılır.</span><span class="sxs-lookup"><span data-stu-id="154c8-151">Both are used when a derived class inherits from a base class, and both redefine one declared element with another.</span></span> <span data-ttu-id="154c8-152">Ancak, ikisi arasındaki önemli farklar vardır.</span><span class="sxs-lookup"><span data-stu-id="154c8-152">But there are significant differences between the two.</span></span> <span data-ttu-id="154c8-153">Bir karşılaştırması için bkz. [arasındaki farklar gölgeleme ve geçersiz kılmak](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).</span><span class="sxs-lookup"><span data-stu-id="154c8-153">For a comparison, see [Differences Between Shadowing and Overriding](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).</span></span>  
  
## <a name="shadowing-and-overloading"></a><span data-ttu-id="154c8-154">Gölgeleme ve aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="154c8-154">Shadowing and Overloading</span></span>  
 <span data-ttu-id="154c8-155">Gölgeleme öğeleri, türetilen bir sınıfta birden fazla öğe ile aynı temel sınıf öğesi gölge, o öğenin aşırı yüklü sürümlerini haline gelir.</span><span class="sxs-lookup"><span data-stu-id="154c8-155">If you shadow the same base class element with more than one element in your derived class, the shadowing elements become overloaded versions of that element.</span></span> <span data-ttu-id="154c8-156">Daha fazla bilgi için [yordam aşırı yüklemesi](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="154c8-156">For more information, see [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span></span>  
  
## <a name="accessing-a-shadowed-element"></a><span data-ttu-id="154c8-157">Gölgeli öğe erişme</span><span class="sxs-lookup"><span data-stu-id="154c8-157">Accessing a Shadowed Element</span></span>  
 <span data-ttu-id="154c8-158">Türetilmiş bir sınıftan bir öğe eriştiğinizde, normalde, türetilmiş sınıfın geçerli örneği üzerinden öğe adı ile uygun olarak bunu `Me` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="154c8-158">When you access an element from a derived class, you normally do so through the current instance of that derived class, by qualifying the element name with the `Me` keyword.</span></span> <span data-ttu-id="154c8-159">Öğenin temel sınıfta türetilmiş sınıfınızın gölgeliyor, temel sınıf öğesi ile uygun erişebilirsiniz `MyBase` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="154c8-159">If your derived class shadows the element in the base class, you can access the base class element by qualifying it with the `MyBase` keyword.</span></span>  
  
 <span data-ttu-id="154c8-160">Gölgeli öğe erişmenin bir örnek için bkz [nasıl yapılır: Türetilmiş sınıf tarafından gizlenen bir değişkene erişme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="154c8-160">For an example of accessing a shadowed element, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
### <a name="declaration-of-the-object-variable"></a><span data-ttu-id="154c8-161">Nesne değişken bildirimi</span><span class="sxs-lookup"><span data-stu-id="154c8-161">Declaration of the Object Variable</span></span>  
 <span data-ttu-id="154c8-162">Nesne değişkeni oluşturma, ayrıca bir gölgeleme gölgeli öğesi veya türetilmiş sınıf erişen olmadığını etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="154c8-162">How you create the object variable can also affect whether the derived class accesses a shadowing element or the shadowed element.</span></span> <span data-ttu-id="154c8-163">Aşağıdaki örnek, iki nesne öğesinden türetilmiş bir sınıf oluşturur, ancak bir nesne, temel sınıf ve türetilen sınıf olarak bildirilir.</span><span class="sxs-lookup"><span data-stu-id="154c8-163">The following example creates two objects from a derived class, but one object is declared as the base class and the other as the derived class.</span></span>  
  
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
  
 <span data-ttu-id="154c8-164">Yukarıdaki örnekte, değişken `basObj` temel sınıf olarak bildirilir.</span><span class="sxs-lookup"><span data-stu-id="154c8-164">In the preceding example, the variable `basObj` is declared as the base class.</span></span> <span data-ttu-id="154c8-165">Atama bir `dervCls` nesnesiyle Genişletme dönüşümü oluşturan ve bu nedenle geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="154c8-165">Assigning a `dervCls` object to it constitutes a widening conversion and is therefore valid.</span></span> <span data-ttu-id="154c8-166">Ancak, temel sınıf değişkeni gölgeleme sürümünü erişemez `z` türetilen sınıfta, böylece derleyici çözümler `basObj.z` özgün değere temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="154c8-166">However, the base class cannot access the shadowing version of the variable `z` in the derived class, so the compiler resolves `basObj.z` to the original base class value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="154c8-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="154c8-167">See also</span></span>
- [<span data-ttu-id="154c8-168">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="154c8-168">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="154c8-169">Visual Basic'de kapsam</span><span class="sxs-lookup"><span data-stu-id="154c8-169">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [<span data-ttu-id="154c8-170">Genişletme ve Daraltma Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="154c8-170">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="154c8-171">Shadows</span><span class="sxs-lookup"><span data-stu-id="154c8-171">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="154c8-172">Overrides</span><span class="sxs-lookup"><span data-stu-id="154c8-172">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="154c8-173">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="154c8-173">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="154c8-174">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="154c8-174">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
