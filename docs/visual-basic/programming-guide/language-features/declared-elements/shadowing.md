---
description: 'Daha fazla bilgi edinin Visual Basic: gölgeleme'
title: Gölge Kullanım
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
ms.openlocfilehash: 468ad72808d689016cacb8d2be56fa9f9fcd1eec
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434829"
---
# <a name="shadowing-in-visual-basic"></a><span data-ttu-id="fc8d5-103">Visual Basic'de Gölgeleme</span><span class="sxs-lookup"><span data-stu-id="fc8d5-103">Shadowing in Visual Basic</span></span>

<span data-ttu-id="fc8d5-104">İki programlama öğesi aynı adı paylaşıyorsa, bunlardan biri diğer birini gizleyebilir veya *gölgelendirebilir*.</span><span class="sxs-lookup"><span data-stu-id="fc8d5-104">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="fc8d5-105">Böyle bir durumda, gölgelendirilmiş öğe başvuru için kullanılamaz; Bunun yerine, kodunuz öğe adını kullandığında, Visual Basic derleyici onu gölgeleme öğesine çözer.</span><span class="sxs-lookup"><span data-stu-id="fc8d5-105">In such a situation, the shadowed element is not available for reference; instead, when your code uses the element name, the Visual Basic compiler resolves it to the shadowing element.</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="fc8d5-106">Amaç</span><span class="sxs-lookup"><span data-stu-id="fc8d5-106">Purpose</span></span>  

 <span data-ttu-id="fc8d5-107">Gölgeleme için ana amaç, sınıf üyelerinizin tanımını koruyasağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="fc8d5-107">The main purpose of shadowing is to protect the definition of your class members.</span></span> <span data-ttu-id="fc8d5-108">Temel sınıf, zaten tanımlamış olduğunuz adla aynı ada sahip bir öğe oluşturan bir değişikliği olumsuz etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="fc8d5-108">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="fc8d5-109">Bu durumda, değiştirici, `Shadows` sınıfınızın içindeki başvuruyu, yeni temel sınıf öğesi yerine tanımladığınız üyeye çözümlenmeye zorlar.</span><span class="sxs-lookup"><span data-stu-id="fc8d5-109">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>  
  
## <a name="types-of-shadowing"></a><span data-ttu-id="fc8d5-110">Gölgeleme türleri</span><span class="sxs-lookup"><span data-stu-id="fc8d5-110">Types of Shadowing</span></span>  

 <span data-ttu-id="fc8d5-111">Bir öğe, başka bir öğeyi iki farklı şekilde gölgelendirebilir.</span><span class="sxs-lookup"><span data-stu-id="fc8d5-111">An element can shadow another element in two different ways.</span></span> <span data-ttu-id="fc8d5-112">Gölgeleme öğesi, gölgeli öğeyi içeren bölgenin bir alt bölgesi içinde, bu durumda gölgeleme *kapsam aracılığıyla* yapılır.</span><span class="sxs-lookup"><span data-stu-id="fc8d5-112">The shadowing element can be declared inside a subregion of the region containing the shadowed element, in which case the shadowing is accomplished *through scope*.</span></span> <span data-ttu-id="fc8d5-113">Ya da türetilen bir sınıf temel sınıfın bir üyesini yeniden tanımlayabilir, bu durumda gölgeleme *Devralma yoluyla* yapılır.</span><span class="sxs-lookup"><span data-stu-id="fc8d5-113">Or a deriving class can redefine a member of a base class, in which case the shadowing is done *through inheritance*.</span></span>  
  
### <a name="shadowing-through-scope"></a><span data-ttu-id="fc8d5-114">Kapsam üzerinden gölgeleme</span><span class="sxs-lookup"><span data-stu-id="fc8d5-114">Shadowing Through Scope</span></span>  

 <span data-ttu-id="fc8d5-115">Aynı modül, sınıf veya yapıdaki öğelerin aynı ada ancak farklı kapsama sahip olması için programlama mümkündür.</span><span class="sxs-lookup"><span data-stu-id="fc8d5-115">It is possible for programming elements in the same module, class, or structure to have the same name but different scope.</span></span> <span data-ttu-id="fc8d5-116">İki öğe bu şekilde bildirildiğinde ve kod paylaştıkları ada başvuruyorsa, dar kapsamdaki öğe diğer öğeyi (blok kapsamı en dar).</span><span class="sxs-lookup"><span data-stu-id="fc8d5-116">When two elements are declared in this manner and the code refers to the name they share, the element with the narrower scope shadows the other element (block scope is the narrowest).</span></span>  
  
 <span data-ttu-id="fc8d5-117">Örneğin, bir modül adlı bir değişken tanımlayabilir `Public` `temp` ve modül içindeki bir yordam de adında bir yerel değişken bildirebilir `temp` .</span><span class="sxs-lookup"><span data-stu-id="fc8d5-117">For example, a module can define a `Public` variable named `temp`, and a procedure within the module can declare a local variable also named `temp`.</span></span> <span data-ttu-id="fc8d5-118">Yordamın içinden öğesine yapılan başvurular, `temp` `temp` değişkene erişen yordamın dışından yapılan başvurular için yerel değişkene erişir `Public` .</span><span class="sxs-lookup"><span data-stu-id="fc8d5-118">References to `temp` from within the procedure access the local variable, while references to `temp` from outside the procedure access the `Public` variable.</span></span> <span data-ttu-id="fc8d5-119">Bu durumda, yordam değişkeni `temp` Modül değişkenini gölgeliyor `temp` .</span><span class="sxs-lookup"><span data-stu-id="fc8d5-119">In this case, the procedure variable `temp` shadows the module variable `temp`.</span></span>  
  
 <span data-ttu-id="fc8d5-120">Aşağıdaki çizimde, adında iki değişken gösterilmektedir `temp` .</span><span class="sxs-lookup"><span data-stu-id="fc8d5-120">The following illustration shows two variables, both named `temp`.</span></span> <span data-ttu-id="fc8d5-121">Yerel değişken, `temp` `temp` kendi yordamı içinde erişildiğinde üye değişkenini gölgeliyor `p` .</span><span class="sxs-lookup"><span data-stu-id="fc8d5-121">The local variable `temp` shadows the member variable `temp` when accessed from within its own procedure `p`.</span></span> <span data-ttu-id="fc8d5-122">Ancak `MyClass` anahtar sözcüğü, gölgelendirmeyi atlar ve üye değişkenine erişir.</span><span class="sxs-lookup"><span data-stu-id="fc8d5-122">However, the `MyClass` keyword bypasses the shadowing and accesses the member variable.</span></span>  
  
 ![Kapsam aracılığıyla gölgelendirmeyi gösteren grafik.](./media/shadowing/shadow-scope-diagram.gif)
  
 <span data-ttu-id="fc8d5-124">Kapsam üzerinden gölgeleme örneği için bkz. [nasıl yapılır: Değişkeninizle Aynı ada sahip bir değişkeni gizleme](how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span><span class="sxs-lookup"><span data-stu-id="fc8d5-124">For an example of shadowing through scope, see [How to: Hide a Variable with the Same Name as Your Variable](how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span></span>  
  
### <a name="shadowing-through-inheritance"></a><span data-ttu-id="fc8d5-125">Devralma yoluyla gölgeleme</span><span class="sxs-lookup"><span data-stu-id="fc8d5-125">Shadowing Through Inheritance</span></span>  

 <span data-ttu-id="fc8d5-126">Türetilmiş bir sınıf, temel sınıftan devralınan bir programlama öğesini yeniden tanımlar, yeniden tanımlama öğesi orijinal öğeyi gölmelidir.</span><span class="sxs-lookup"><span data-stu-id="fc8d5-126">If a derived class redefines a programming element inherited from a base class, the redefining element shadows the original element.</span></span> <span data-ttu-id="fc8d5-127">Herhangi bir tür tanımlanmış öğeyi veya daha fazla öğe kümesini başka herhangi bir türle gölgelendirebilir.</span><span class="sxs-lookup"><span data-stu-id="fc8d5-127">You can shadow any type of declared element, or set of overloaded elements, with any other type.</span></span> <span data-ttu-id="fc8d5-128">Örneğin, bir `Integer` değişken bir yordamı gölgelendirebilir `Function` .</span><span class="sxs-lookup"><span data-stu-id="fc8d5-128">For example, an `Integer` variable can shadow a `Function` procedure.</span></span> <span data-ttu-id="fc8d5-129">Bir yordamı başka bir yordamla gölgelendirmek istiyorsanız farklı bir parametre listesi ve farklı bir dönüş türü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc8d5-129">If you shadow a procedure with another procedure, you can use a different parameter list and a different return type.</span></span>  
  
 <span data-ttu-id="fc8d5-130">Aşağıdaki çizimde, bir temel sınıf `b` ve öğesinden devralan türetilmiş bir sınıf gösterilmektedir `d` `b` .</span><span class="sxs-lookup"><span data-stu-id="fc8d5-130">The following illustration shows a base class `b` and a derived class `d` that inherits from `b`.</span></span> <span data-ttu-id="fc8d5-131">Temel sınıf adlı bir yordamı tanımlar `proc` ve türetilmiş sınıf onu aynı ada sahip başka bir yordamla birlikte gölgeler.</span><span class="sxs-lookup"><span data-stu-id="fc8d5-131">The base class defines a procedure named `proc`, and the derived class shadows it with another procedure of the same name.</span></span> <span data-ttu-id="fc8d5-132">İlk `Call` ifade, türetilmiş sınıftaki gölgelendirme erişir `proc` .</span><span class="sxs-lookup"><span data-stu-id="fc8d5-132">The first `Call` statement accesses the shadowing `proc` in the derived class.</span></span> <span data-ttu-id="fc8d5-133">Ancak `MyBase` anahtar sözcüğü, gölgelendirmeyi atlar ve temel sınıftaki gölgelendirilmiş yordama erişir.</span><span class="sxs-lookup"><span data-stu-id="fc8d5-133">However, the `MyBase` keyword bypasses the shadowing and accesses the shadowed procedure in the base class.</span></span>  
  
 ![Devralma yoluyla gölgeleme grafik Diyagramı](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 <span data-ttu-id="fc8d5-135">Devralma yoluyla gölgeleme örneği için bkz. [nasıl yapılır: Değişkeninizle Aynı ada sahip bir değişkeni gizleme](how-to-hide-a-variable-with-the-same-name-as-your-variable.md) ve [nasıl yapılır: devralınan bir değişkeni gizleme](how-to-hide-an-inherited-variable.md).</span><span class="sxs-lookup"><span data-stu-id="fc8d5-135">For an example of shadowing through inheritance, see [How to: Hide a Variable with the Same Name as Your Variable](how-to-hide-a-variable-with-the-same-name-as-your-variable.md) and [How to: Hide an Inherited Variable](how-to-hide-an-inherited-variable.md).</span></span>  
  
#### <a name="shadowing-and-access-level"></a><span data-ttu-id="fc8d5-136">Gölgeleme ve erişim düzeyi</span><span class="sxs-lookup"><span data-stu-id="fc8d5-136">Shadowing and Access Level</span></span>  

 <span data-ttu-id="fc8d5-137">Gölgeleme öğesine, türetilmiş sınıf kullanılarak her zaman koddan erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="fc8d5-137">The shadowing element is not always accessible from the code using the derived class.</span></span> <span data-ttu-id="fc8d5-138">Örneğin, bu durum bildirilmiştir `Private` .</span><span class="sxs-lookup"><span data-stu-id="fc8d5-138">For example, it might be declared `Private`.</span></span> <span data-ttu-id="fc8d5-139">Böyle bir durumda, gölgeleme ertelenmiş olur ve bir gölgeleme yoksa, derleyici aynı öğeye yapılan herhangi bir başvuruyu çözer.</span><span class="sxs-lookup"><span data-stu-id="fc8d5-139">In such a case, shadowing is defeated and the compiler resolves any reference to the same element it would have if there had been no shadowing.</span></span> <span data-ttu-id="fc8d5-140">Bu öğe, gölgeleme sınıfından en az bir adım daha doğru olan erişilebilir öğedir.</span><span class="sxs-lookup"><span data-stu-id="fc8d5-140">This element is the accessible element the fewest derivational steps backward from the shadowing class.</span></span> <span data-ttu-id="fc8d5-141">Gölgelendirilmiş öğe bir yordamdır, çözüm aynı ada, parametre listesine ve dönüş türüne sahip en yakın erişilebilir sürüme göre yapılır.</span><span class="sxs-lookup"><span data-stu-id="fc8d5-141">If the shadowed element is a procedure, the resolution is to the closest accessible version with the same name, parameter list, and return type.</span></span>  
  
 <span data-ttu-id="fc8d5-142">Aşağıdaki örnekte, üç sınıfın devralma hiyerarşisi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fc8d5-142">The following example shows an inheritance hierarchy of three classes.</span></span> <span data-ttu-id="fc8d5-143">Her sınıf bir `Sub` yordamı tanımlar `display` ve türetilmiş her sınıf, `display` yordamı temel sınıfında gölmelidir.</span><span class="sxs-lookup"><span data-stu-id="fc8d5-143">Each class defines a `Sub` procedure `display`, and each derived class shadows the `display` procedure in its base class.</span></span>  
  
```vb  
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
  
 <span data-ttu-id="fc8d5-144">Önceki örnekte, türetilmiş sınıf `secondClass` `display` bir yordam ile gölgeler `Private` .</span><span class="sxs-lookup"><span data-stu-id="fc8d5-144">In the preceding example, the derived class `secondClass` shadows `display` with a `Private` procedure.</span></span> <span data-ttu-id="fc8d5-145">Modül `callDisplay` içinde çağırdığında `display` `secondClass` , çağıran kod dışarıda olur `secondClass` ve bu nedenle özel `display` yordama erişemez.</span><span class="sxs-lookup"><span data-stu-id="fc8d5-145">When module `callDisplay` calls `display` in `secondClass`, the calling code is outside `secondClass` and therefore cannot access the private `display` procedure.</span></span> <span data-ttu-id="fc8d5-146">Gölgeleme ertelenmiş ve derleyici, temel sınıf yordamının başvurusunu çözümlüyor `display` .</span><span class="sxs-lookup"><span data-stu-id="fc8d5-146">Shadowing is defeated, and the compiler resolves the reference to the base class `display` procedure.</span></span>  
  
 <span data-ttu-id="fc8d5-147">Bununla birlikte, diğer türetilmiş sınıf `thirdClass` `display` olarak bildirilir `Public` , bu nedenle içindeki kod `callDisplay` buna erişebilir.</span><span class="sxs-lookup"><span data-stu-id="fc8d5-147">However, the further derived class `thirdClass` declares `display` as `Public`, so the code in `callDisplay` can access it.</span></span>  
  
## <a name="shadowing-and-overriding"></a><span data-ttu-id="fc8d5-148">Gölgeleme ve geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="fc8d5-148">Shadowing and Overriding</span></span>  

 <span data-ttu-id="fc8d5-149">Geçersiz kılma ile gölgelendirmeyi karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="fc8d5-149">Do not confuse shadowing with overriding.</span></span> <span data-ttu-id="fc8d5-150">Her ikisi de türetilmiş bir sınıf temel sınıftan devralındığında ve her ikisi de bir beyan edilen öğeyi başka bir ile yeniden tanımlayarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fc8d5-150">Both are used when a derived class inherits from a base class, and both redefine one declared element with another.</span></span> <span data-ttu-id="fc8d5-151">Ancak ikisi arasında önemli farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="fc8d5-151">But there are significant differences between the two.</span></span> <span data-ttu-id="fc8d5-152">Karşılaştırma için bkz. [gölgeleme ve geçersiz kılma arasındaki farklar](differences-between-shadowing-and-overriding.md).</span><span class="sxs-lookup"><span data-stu-id="fc8d5-152">For a comparison, see [Differences Between Shadowing and Overriding](differences-between-shadowing-and-overriding.md).</span></span>  
  
## <a name="shadowing-and-overloading"></a><span data-ttu-id="fc8d5-153">Gölgeleme ve aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="fc8d5-153">Shadowing and Overloading</span></span>  

 <span data-ttu-id="fc8d5-154">Türetilmiş sınıfınıza birden fazla öğe ile aynı temel sınıf öğesini gölgelendirebiliyorsanız, gölgeleme öğeleri o öğenin aşırı yüklenmiş sürümleri haline gelir.</span><span class="sxs-lookup"><span data-stu-id="fc8d5-154">If you shadow the same base class element with more than one element in your derived class, the shadowing elements become overloaded versions of that element.</span></span> <span data-ttu-id="fc8d5-155">Daha fazla bilgi için bkz. [yordam aşırı yüklemesi](../procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="fc8d5-155">For more information, see [Procedure Overloading](../procedures/procedure-overloading.md).</span></span>  
  
## <a name="accessing-a-shadowed-element"></a><span data-ttu-id="fc8d5-156">Gölgelendirilmiş bir öğeye erişme</span><span class="sxs-lookup"><span data-stu-id="fc8d5-156">Accessing a Shadowed Element</span></span>  

 <span data-ttu-id="fc8d5-157">Türetilmiş bir sınıftan bir öğeye eriştiğinizde, genellikle bu türetilmiş sınıfın geçerli örneği aracılığıyla, öğe adını anahtar sözcüğüyle niteleyerek yapabilirsiniz `Me` .</span><span class="sxs-lookup"><span data-stu-id="fc8d5-157">When you access an element from a derived class, you normally do so through the current instance of that derived class, by qualifying the element name with the `Me` keyword.</span></span> <span data-ttu-id="fc8d5-158">Türetilmiş sınıfınız temel sınıftaki öğesini göltiği, anahtar sözcüğü ile niteleyerek temel sınıf öğesine erişebilirsiniz `MyBase` .</span><span class="sxs-lookup"><span data-stu-id="fc8d5-158">If your derived class shadows the element in the base class, you can access the base class element by qualifying it with the `MyBase` keyword.</span></span>  
  
 <span data-ttu-id="fc8d5-159">Gölgelendirilmiş bir öğeye erişme örneği için bkz. [nasıl yapılır: türetilmiş bir sınıf tarafından gizlenen bir değişkene erişme](how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="fc8d5-159">For an example of accessing a shadowed element, see [How to: Access a Variable Hidden by a Derived Class](how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
### <a name="declaration-of-the-object-variable"></a><span data-ttu-id="fc8d5-160">Nesne değişkeninin bildirimi</span><span class="sxs-lookup"><span data-stu-id="fc8d5-160">Declaration of the Object Variable</span></span>  

 <span data-ttu-id="fc8d5-161">Nesne değişkenini nasıl oluşturacağınız, türetilmiş sınıfın bir gölgeleme öğesine mi yoksa gölgelendirilmiş öğeye mi eriştiğini de etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="fc8d5-161">How you create the object variable can also affect whether the derived class accesses a shadowing element or the shadowed element.</span></span> <span data-ttu-id="fc8d5-162">Aşağıdaki örnek, türetilmiş bir sınıftan iki nesne oluşturur, ancak bir nesne temel sınıf olarak ve diğeri türetilmiş sınıf olarak bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fc8d5-162">The following example creates two objects from a derived class, but one object is declared as the base class and the other as the derived class.</span></span>  
  
```vb  
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
  
 <span data-ttu-id="fc8d5-163">Önceki örnekte, değişkeni `basObj` temel sınıf olarak bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fc8d5-163">In the preceding example, the variable `basObj` is declared as the base class.</span></span> <span data-ttu-id="fc8d5-164">Nesnesine bir `dervCls` nesne atamak, genişleyen dönüştürme oluşturur ve bu nedenle geçerli olur.</span><span class="sxs-lookup"><span data-stu-id="fc8d5-164">Assigning a `dervCls` object to it constitutes a widening conversion and is therefore valid.</span></span> <span data-ttu-id="fc8d5-165">Ancak, temel sınıf türetilmiş sınıftaki değişkeninin gölgeleme sürümüne erişemez `z` , bu nedenle derleyici `basObj.z` özgün temel sınıf değerine çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="fc8d5-165">However, the base class cannot access the shadowing version of the variable `z` in the derived class, so the compiler resolves `basObj.z` to the original base class value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc8d5-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc8d5-166">See also</span></span>

- [<span data-ttu-id="fc8d5-167">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="fc8d5-167">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="fc8d5-168">Visual Basic'de Kapsam</span><span class="sxs-lookup"><span data-stu-id="fc8d5-168">Scope in Visual Basic</span></span>](scope.md)
- [<span data-ttu-id="fc8d5-169">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="fc8d5-169">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="fc8d5-170">Shadows</span><span class="sxs-lookup"><span data-stu-id="fc8d5-170">Shadows</span></span>](../../../language-reference/modifiers/shadows.md)
- [<span data-ttu-id="fc8d5-171">Geçersiz Kılmalar</span><span class="sxs-lookup"><span data-stu-id="fc8d5-171">Overrides</span></span>](../../../language-reference/modifiers/overrides.md)
- [<span data-ttu-id="fc8d5-172">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="fc8d5-172">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="fc8d5-173">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="fc8d5-173">Inheritance Basics</span></span>](../objects-and-classes/inheritance-basics.md)
