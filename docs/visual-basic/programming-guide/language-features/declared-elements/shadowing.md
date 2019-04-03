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
ms.openlocfilehash: 9ad992a53618fa2f410e0b0fb23886c30136384f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839398"
---
# <a name="shadowing-in-visual-basic"></a><span data-ttu-id="2f0f6-102">Visual Basic'de Gölgeleme</span><span class="sxs-lookup"><span data-stu-id="2f0f6-102">Shadowing in Visual Basic</span></span>
<span data-ttu-id="2f0f6-103">Bunlardan biri, iki programlama öğeleri aynı adı paylaşan, gizleyebilirsiniz, veya *gölge*, diğerinde.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-103">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="2f0f6-104">Böyle bir durumda gölgeli öğe başvuru için kullanılabilir değildir; Bunun yerine, kodunuzu öğe adı kullandığında, Visual Basic Derleyicisi, gölgelendirme öğesine çözümler.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-104">In such a situation, the shadowed element is not available for reference; instead, when your code uses the element name, the Visual Basic compiler resolves it to the shadowing element.</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="2f0f6-105">Amaç</span><span class="sxs-lookup"><span data-stu-id="2f0f6-105">Purpose</span></span>  
 <span data-ttu-id="2f0f6-106">Gölgeleme ana amacı, sınıf üyelerinin tanımına korunmasını sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-106">The main purpose of shadowing is to protect the definition of your class members.</span></span> <span data-ttu-id="2f0f6-107">Temel sınıf olarak zaten tanımlanmış aynı ada sahip bir öğe oluşturan bir değişiklik uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-107">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="2f0f6-108">Böyle bir durumda `Shadows` değiştiricisi zorlar başvuruyor, sınıf üyesine çözümlenmesi aracılığıyla tanımlanmış, yerine yeni bir temel sınıf öğe için.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-108">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>  
  
## <a name="types-of-shadowing"></a><span data-ttu-id="2f0f6-109">Tür gölgeleme</span><span class="sxs-lookup"><span data-stu-id="2f0f6-109">Types of Shadowing</span></span>  
 <span data-ttu-id="2f0f6-110">Bir öğe başka bir öğeye iki farklı şekilde gölge.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-110">An element can shadow another element in two different ways.</span></span> <span data-ttu-id="2f0f6-111">Gölgeleme öğesi bir alt bölgeli gölgeleme çalışması gerçekleştirilir gölgeli öğe içeren bölgenin içinde bildirilebilir *kapsam aracılığıyla*.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-111">The shadowing element can be declared inside a subregion of the region containing the shadowed element, in which case the shadowing is accomplished *through scope*.</span></span> <span data-ttu-id="2f0f6-112">Veya bir türetilen sınıf gölgeleme çalışması yapılır bir taban sınıfın üyesi bulunabileceğini belirleyebileceğiniz manasına *devralma yoluyla*.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-112">Or a deriving class can redefine a member of a base class, in which case the shadowing is done *through inheritance*.</span></span>  
  
### <a name="shadowing-through-scope"></a><span data-ttu-id="2f0f6-113">Kapsam yoluyla gölgeleme</span><span class="sxs-lookup"><span data-stu-id="2f0f6-113">Shadowing Through Scope</span></span>  
 <span data-ttu-id="2f0f6-114">Bu modül, sınıf veya yapı aynı ada ancak farklı bir kapsam için öğeleri programlama için mümkündür.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-114">It is possible for programming elements in the same module, class, or structure to have the same name but different scope.</span></span> <span data-ttu-id="2f0f6-115">İki öğe, bu şekilde bildirilir ve kod paylaştıkları adıdır, başka bir öğenin öğe daha dar kapsamlı gölgeleri (blok kapsamı olan en düşük).</span><span class="sxs-lookup"><span data-stu-id="2f0f6-115">When two elements are declared in this manner and the code refers to the name they share, the element with the narrower scope shadows the other element (block scope is the narrowest).</span></span>  
  
 <span data-ttu-id="2f0f6-116">Örneğin, bir modül tanımlayabilirsiniz bir `Public` adlı değişken `temp`, ve bir yordamda bir modül olarak da adlandırılan bir yerel değişken bildirebilirsiniz `temp`.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-116">For example, a module can define a `Public` variable named `temp`, and a procedure within the module can declare a local variable also named `temp`.</span></span> <span data-ttu-id="2f0f6-117">Başvurular `temp` yordam başvurularını sırasında yerel değişken içinden erişmek `temp` gelen yordamı erişim dışında `Public` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-117">References to `temp` from within the procedure access the local variable, while references to `temp` from outside the procedure access the `Public` variable.</span></span> <span data-ttu-id="2f0f6-118">Bu durumda, yordam değişken `temp` modülü değişken gölgeleri `temp`.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-118">In this case, the procedure variable `temp` shadows the module variable `temp`.</span></span>  
  
 <span data-ttu-id="2f0f6-119">İki değişken aşağıdaki çizimde, hem adlandırılmış `temp`.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-119">The following illustration shows two variables, both named `temp`.</span></span> <span data-ttu-id="2f0f6-120">Yerel değişken `temp` üye değişkeni gölgeleri `temp` kendi yordam içinde erişildiğinde `p`.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-120">The local variable `temp` shadows the member variable `temp` when accessed from within its own procedure `p`.</span></span> <span data-ttu-id="2f0f6-121">Ancak, `MyClass` anahtar sözcüğü gölgeleme atlar ve üye değişkeni erişir.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-121">However, the `MyClass` keyword bypasses the shadowing and accesses the member variable.</span></span>  
  
 ![Kapsam yoluyla gölgeleme gösteren grafik.](./media/shadowing/shadow-scope-diagram.gif)
  
 <span data-ttu-id="2f0f6-123">Kapsam yoluyla gölgeleme ilişkin bir örnek için bkz [nasıl yapılır: Değişkeninizle aynı ada sahip bir değişkeni gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span><span class="sxs-lookup"><span data-stu-id="2f0f6-123">For an example of shadowing through scope, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span></span>  
  
### <a name="shadowing-through-inheritance"></a><span data-ttu-id="2f0f6-124">Devralma üzerinden gölgeleme</span><span class="sxs-lookup"><span data-stu-id="2f0f6-124">Shadowing Through Inheritance</span></span>  
 <span data-ttu-id="2f0f6-125">Türetilmiş bir sınıf bir temel sınıftan devralınan bir programlama öğesi'ı yeniden tanımladığı, özgün öğe redefining öğesi gölgeliyor.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-125">If a derived class redefines a programming element inherited from a base class, the redefining element shadows the original element.</span></span> <span data-ttu-id="2f0f6-126">Herhangi bir türü ile herhangi bir türde bildirilen öğe veya aşırı yüklenmiş öğeleri kümesi gölge.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-126">You can shadow any type of declared element, or set of overloaded elements, with any other type.</span></span> <span data-ttu-id="2f0f6-127">Örneğin, bir `Integer` değişkeni gölge bir `Function` yordamı.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-127">For example, an `Integer` variable can shadow a `Function` procedure.</span></span> <span data-ttu-id="2f0f6-128">Başka bir yordam içeren bir yordamı gölge, başka bir parametre listesi ve farklı bir dönüş türü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-128">If you shadow a procedure with another procedure, you can use a different parameter list and a different return type.</span></span>  
  
 <span data-ttu-id="2f0f6-129">Aşağıdaki çizimde bir temel sınıf `b` ve türetilmiş bir sınıf `d` öğesinden devralan `b`.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-129">The following illustration shows a base class `b` and a derived class `d` that inherits from `b`.</span></span> <span data-ttu-id="2f0f6-130">Adlı bir yordam temel sınıf tanımlar `proc`, ve isteğe bağlı olarak türetilmiş bir sınıf ile aynı ada sahip başka bir yordam gölgeliyor.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-130">The base class defines a procedure named `proc`, and the derived class shadows it with another procedure of the same name.</span></span> <span data-ttu-id="2f0f6-131">İlk `Call` deyimi erişen gölgeleme `proc` türetilen sınıfta.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-131">The first `Call` statement accesses the shadowing `proc` in the derived class.</span></span> <span data-ttu-id="2f0f6-132">Ancak, `MyBase` anahtar sözcüğü gölgeleme atlar ve temel sınıfta gölgeli yordamı erişir.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-132">However, the `MyBase` keyword bypasses the shadowing and accesses the shadowed procedure in the base class.</span></span>  
  
 ![Devralma üzerinden gölgeleme grafik diyagramı](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 <span data-ttu-id="2f0f6-134">Devralma üzerinden gölgeleme ilişkin bir örnek için bkz [nasıl yapılır: Değişkeninizle aynı ada sahip bir değişkeni gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) ve [nasıl yapılır: Devralınmış değişkeni gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).</span><span class="sxs-lookup"><span data-stu-id="2f0f6-134">For an example of shadowing through inheritance, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) and [How to: Hide an Inherited Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).</span></span>  
  
#### <a name="shadowing-and-access-level"></a><span data-ttu-id="2f0f6-135">Gölgeleme ve erişim düzeyi</span><span class="sxs-lookup"><span data-stu-id="2f0f6-135">Shadowing and Access Level</span></span>  
 <span data-ttu-id="2f0f6-136">Gölgeleme öğe her zaman türetilen sınıfın kullanarak koddan erişilebilir değil.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-136">The shadowing element is not always accessible from the code using the derived class.</span></span> <span data-ttu-id="2f0f6-137">Örneğin, bu bildirilmesi `Private`.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-137">For example, it might be declared `Private`.</span></span> <span data-ttu-id="2f0f6-138">Böyle bir durumda gölgeleme engellenmediğinden ve aynı öğeye sahip herhangi bir referans derleyici çözümler geliştirilmişse gölgeleme yok.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-138">In such a case, shadowing is defeated and the compiler resolves any reference to the same element it would have if there had been no shadowing.</span></span> <span data-ttu-id="2f0f6-139">Bu öğe en az derivational adımları geri gölgeleme sınıftan erişilebilir öğedir.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-139">This element is the accessible element the fewest derivational steps backward from the shadowing class.</span></span> <span data-ttu-id="2f0f6-140">Gölgeli öğe bir yordam varsa çözümleme en yakın erişilebilir sürüme, parametre listesi, aynı ada sahip olan ve dönüş türü.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-140">If the shadowed element is a procedure, the resolution is to the closest accessible version with the same name, parameter list, and return type.</span></span>  
  
 <span data-ttu-id="2f0f6-141">Aşağıdaki örnek, üç sınıfların Devralma Hiyerarşisi gösterir.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-141">The following example shows an inheritance hierarchy of three classes.</span></span> <span data-ttu-id="2f0f6-142">Her bir sınıf tanımlayan bir `Sub` yordamı `display`, ve her bir türetilmiş sınıf shadows `display` yordamı temel sınıfındaki.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-142">Each class defines a `Sub` procedure `display`, and each derived class shadows the `display` procedure in its base class.</span></span>  
  
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
  
 <span data-ttu-id="2f0f6-143">Yukarıdaki örnekte, türetilen sınıfın `secondClass` shadows `display` ile bir `Private` yordamı.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-143">In the preceding example, the derived class `secondClass` shadows `display` with a `Private` procedure.</span></span> <span data-ttu-id="2f0f6-144">Zaman Modülü `callDisplay` çağrıları `display` içinde `secondClass`, çağıran kodun dışında `secondClass` ve özel etkinleştirilemez `display` yordamı.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-144">When module `callDisplay` calls `display` in `secondClass`, the calling code is outside `secondClass` and therefore cannot access the private `display` procedure.</span></span> <span data-ttu-id="2f0f6-145">Gölgeleme engellenmediğinden ve derleyicinin temel sınıf başvurusunu çözümler `display` yordamı.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-145">Shadowing is defeated, and the compiler resolves the reference to the base class `display` procedure.</span></span>  
  
 <span data-ttu-id="2f0f6-146">Ancak, daha fazla türetilmiş sınıf `thirdClass` bildirir `display` olarak `Public`, bu nedenle kodda `callDisplay` buna erişebilir.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-146">However, the further derived class `thirdClass` declares `display` as `Public`, so the code in `callDisplay` can access it.</span></span>  
  
## <a name="shadowing-and-overriding"></a><span data-ttu-id="2f0f6-147">Gölgeleme ve geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="2f0f6-147">Shadowing and Overriding</span></span>  
 <span data-ttu-id="2f0f6-148">Geçersiz kılma ile gölgeleme karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-148">Do not confuse shadowing with overriding.</span></span> <span data-ttu-id="2f0f6-149">Her ikisi de bir temel sınıftan türetilmiş bir sınıf devralır ve her ikisini de diğerine ile bildirilen bir öğe yeniden kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-149">Both are used when a derived class inherits from a base class, and both redefine one declared element with another.</span></span> <span data-ttu-id="2f0f6-150">Ancak, ikisi arasındaki önemli farklar vardır.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-150">But there are significant differences between the two.</span></span> <span data-ttu-id="2f0f6-151">Bir karşılaştırması için bkz. [arasındaki farklar gölgeleme ve geçersiz kılmak](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).</span><span class="sxs-lookup"><span data-stu-id="2f0f6-151">For a comparison, see [Differences Between Shadowing and Overriding](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).</span></span>  
  
## <a name="shadowing-and-overloading"></a><span data-ttu-id="2f0f6-152">Gölgeleme ve aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="2f0f6-152">Shadowing and Overloading</span></span>  
 <span data-ttu-id="2f0f6-153">Gölgeleme öğeleri, türetilen bir sınıfta birden fazla öğe ile aynı temel sınıf öğesi gölge, o öğenin aşırı yüklü sürümlerini haline gelir.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-153">If you shadow the same base class element with more than one element in your derived class, the shadowing elements become overloaded versions of that element.</span></span> <span data-ttu-id="2f0f6-154">Daha fazla bilgi için [yordam aşırı yüklemesi](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="2f0f6-154">For more information, see [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span></span>  
  
## <a name="accessing-a-shadowed-element"></a><span data-ttu-id="2f0f6-155">Gölgeli öğe erişme</span><span class="sxs-lookup"><span data-stu-id="2f0f6-155">Accessing a Shadowed Element</span></span>  
 <span data-ttu-id="2f0f6-156">Türetilmiş bir sınıftan bir öğe eriştiğinizde, normalde, türetilmiş sınıfın geçerli örneği üzerinden öğe adı ile uygun olarak bunu `Me` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-156">When you access an element from a derived class, you normally do so through the current instance of that derived class, by qualifying the element name with the `Me` keyword.</span></span> <span data-ttu-id="2f0f6-157">Öğenin temel sınıfta türetilmiş sınıfınızın gölgeliyor, temel sınıf öğesi ile uygun erişebilirsiniz `MyBase` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-157">If your derived class shadows the element in the base class, you can access the base class element by qualifying it with the `MyBase` keyword.</span></span>  
  
 <span data-ttu-id="2f0f6-158">Gölgeli öğe erişmenin bir örnek için bkz [nasıl yapılır: Türetilmiş sınıf tarafından gizlenen bir değişkene erişme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="2f0f6-158">For an example of accessing a shadowed element, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
### <a name="declaration-of-the-object-variable"></a><span data-ttu-id="2f0f6-159">Nesne değişken bildirimi</span><span class="sxs-lookup"><span data-stu-id="2f0f6-159">Declaration of the Object Variable</span></span>  
 <span data-ttu-id="2f0f6-160">Nesne değişkeni oluşturma, ayrıca bir gölgeleme gölgeli öğesi veya türetilmiş sınıf erişen olmadığını etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-160">How you create the object variable can also affect whether the derived class accesses a shadowing element or the shadowed element.</span></span> <span data-ttu-id="2f0f6-161">Aşağıdaki örnek, iki nesne öğesinden türetilmiş bir sınıf oluşturur, ancak bir nesne, temel sınıf ve türetilen sınıf olarak bildirilir.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-161">The following example creates two objects from a derived class, but one object is declared as the base class and the other as the derived class.</span></span>  
  
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
  
 <span data-ttu-id="2f0f6-162">Yukarıdaki örnekte, değişken `basObj` temel sınıf olarak bildirilir.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-162">In the preceding example, the variable `basObj` is declared as the base class.</span></span> <span data-ttu-id="2f0f6-163">Atama bir `dervCls` nesnesiyle Genişletme dönüşümü oluşturan ve bu nedenle geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-163">Assigning a `dervCls` object to it constitutes a widening conversion and is therefore valid.</span></span> <span data-ttu-id="2f0f6-164">Ancak, temel sınıf değişkeni gölgeleme sürümünü erişemez `z` türetilen sınıfta, böylece derleyici çözümler `basObj.z` özgün değere temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-164">However, the base class cannot access the shadowing version of the variable `z` in the derived class, so the compiler resolves `basObj.z` to the original base class value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f0f6-165">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f0f6-165">See also</span></span>

- [<span data-ttu-id="2f0f6-166">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="2f0f6-166">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="2f0f6-167">Visual Basic'de kapsam</span><span class="sxs-lookup"><span data-stu-id="2f0f6-167">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [<span data-ttu-id="2f0f6-168">Genişletme ve Daraltma Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="2f0f6-168">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="2f0f6-169">Shadows</span><span class="sxs-lookup"><span data-stu-id="2f0f6-169">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="2f0f6-170">Overrides</span><span class="sxs-lookup"><span data-stu-id="2f0f6-170">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="2f0f6-171">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="2f0f6-171">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="2f0f6-172">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="2f0f6-172">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
