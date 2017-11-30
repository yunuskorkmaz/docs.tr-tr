---
title: "Nesne Değişken Bildirimi (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- early binding [Visual Basic]
- declarations [Visual Basic], class
- classes [Visual Basic], declaring
- binding [Visual Basic], late and early
- object variables [Visual Basic], declaring
- variables [Visual Basic], object
- declaring variables [Visual Basic], object variables
- declaring classes [Visual Basic]
- late binding [Visual Basic]
ms.assetid: 2a5a41a3-1aa8-4236-b1f0-2382af7bf715
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cdca188d778e9884f918d97eba492a29c64af826
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="object-variable-declaration-visual-basic"></a><span data-ttu-id="cc320-102">Nesne Değişken Bildirimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc320-102">Object Variable Declaration (Visual Basic)</span></span>
<span data-ttu-id="cc320-103">Bir nesne değişkeni bildirme için normal bildirimi deyimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="cc320-103">You use a normal declaration statement to declare an object variable.</span></span> <span data-ttu-id="cc320-104">Veri türü için ya da belirttiğiniz `Object` (diğer bir deyişle, [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)) ya da nesne olduğu oluşturulacak daha belirli bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="cc320-104">For the data type, you specify either `Object` (that is, the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)) or a more specific class from which the object is to be created.</span></span>  
  
 <span data-ttu-id="cc320-105">Bir değişken olarak bildirme `Object` olarak bildirme aynı <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cc320-105">Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="cc320-106">Belirli nesne sınıfı sahip bir değişken bildirirken tüm yöntemleri ve özellikleri o sınıfı ve devraldığı sınıfları tarafından kullanıma sunulan erişebilir.</span><span class="sxs-lookup"><span data-stu-id="cc320-106">When you declare a variable with a specific object class, it can access all the methods and properties exposed by that class and the classes from which it inherits.</span></span> <span data-ttu-id="cc320-107">Değişkenle bildirirseniz <xref:System.Object>, yalnızca üyeleri erişebilir <xref:System.Object> sınıfı, açmanız sürece `Option Strict Off` geç bağlama izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="cc320-107">If you declare the variable with <xref:System.Object>, it can access only the members of the <xref:System.Object> class, unless you turn `Option Strict Off` to allow late binding.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="cc320-108">Bildirim Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cc320-108">Declaration Syntax</span></span>  
 <span data-ttu-id="cc320-109">Bir nesne değişkeni bildirmek için aşağıdaki sözdizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="cc320-109">Use the following syntax to declare an object variable:</span></span>  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 <span data-ttu-id="cc320-110">Ayrıca belirtebilirsiniz [ortak](../../../../visual-basic/language-reference/modifiers/public.md), [korumalı](../../../../visual-basic/language-reference/modifiers/protected.md), [arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, [özel](../../../../visual-basic/language-reference/modifiers/private.md), [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md), veya [statik](../../../../visual-basic/language-reference/modifiers/static.md) bildirimi.</span><span class="sxs-lookup"><span data-stu-id="cc320-110">You can also specify [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), or [Static](../../../../visual-basic/language-reference/modifiers/static.md) in the declaration.</span></span> <span data-ttu-id="cc320-111">Aşağıdaki örnek bildirimi geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="cc320-111">The following example declarations are valid:</span></span>  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a><span data-ttu-id="cc320-112">Geç bağlama ve erken bağlama</span><span class="sxs-lookup"><span data-stu-id="cc320-112">Late Binding and Early Binding</span></span>  
 <span data-ttu-id="cc320-113">Bazen kodunuzu çalıştırılana kadar belirli bir sınıf bilinmiyor.</span><span class="sxs-lookup"><span data-stu-id="cc320-113">Sometimes the specific class is unknown until your code runs.</span></span> <span data-ttu-id="cc320-114">Bu durumda, ile nesne değişkeni bildirilmelidir `Object` veri türü.</span><span class="sxs-lookup"><span data-stu-id="cc320-114">In this case, you must declare the object variable with the `Object` data type.</span></span> <span data-ttu-id="cc320-115">Bu genel bir başvuru herhangi türde bir nesne oluşturur ve belirli bir sınıf çalışma zamanında atanır.</span><span class="sxs-lookup"><span data-stu-id="cc320-115">This creates a general reference to any type of object, and the specific class is assigned at run time.</span></span> <span data-ttu-id="cc320-116">Bu adlı *geç bağlama*.</span><span class="sxs-lookup"><span data-stu-id="cc320-116">This is called *late binding*.</span></span> <span data-ttu-id="cc320-117">Geç bağlama ek yürütme süresi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="cc320-117">Late binding requires additional execution time.</span></span> <span data-ttu-id="cc320-118">Ayrıca, kodunuzu yöntemlere ve en son kendisine atadığınız sınıfının özelliklerini sınırlar.</span><span class="sxs-lookup"><span data-stu-id="cc320-118">It also limits your code to the methods and properties of the class you have most recently assigned to it.</span></span> <span data-ttu-id="cc320-119">Kodunuzu farklı bir sınıf üyeleri erişmeye çalışırsa bu çalışma zamanı hataları neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="cc320-119">This can cause run-time errors if your code attempts to access members of a different class.</span></span>  
  
 <span data-ttu-id="cc320-120">Belirli bir sınıf derleme zamanında bildiğiniz durumlarda bu sınıfının olması gereken nesne değişkeni bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc320-120">When you know the specific class at compile time, you should declare the object variable to be of that class.</span></span> <span data-ttu-id="cc320-121">Bu adlı *erken bağlama*.</span><span class="sxs-lookup"><span data-stu-id="cc320-121">This is called *early binding*.</span></span> <span data-ttu-id="cc320-122">Erken bağlama performansını artırır ve kod erişiminizi tüm yöntemleri ve özellikleri belirli bir sınıfın güvence altına alır.</span><span class="sxs-lookup"><span data-stu-id="cc320-122">Early binding improves performance and guarantees your code access to all the methods and properties of the specific class.</span></span> <span data-ttu-id="cc320-123">Yukarıdaki örnek bildirimlerden, değişken varsa `objA` yalnızca sınıfın nesnelerini kullanır <xref:System.Windows.Forms.Label?displayProperty=nameWithType>, belirtmeniz gerekir `As System.Windows.Forms.Label` kendi bildirimi.</span><span class="sxs-lookup"><span data-stu-id="cc320-123">In the preceding example declarations, if variable `objA` uses only objects of class <xref:System.Windows.Forms.Label?displayProperty=nameWithType>, you should specify `As System.Windows.Forms.Label` in its declaration.</span></span>  
  
### <a name="advantages-of-early-binding"></a><span data-ttu-id="cc320-124">Erken bağlama avantajları</span><span class="sxs-lookup"><span data-stu-id="cc320-124">Advantages of Early Binding</span></span>  
 <span data-ttu-id="cc320-125">Belirli bir sınıf olarak bir nesne değişkeni bildirme çeşitli avantajları sağlar:</span><span class="sxs-lookup"><span data-stu-id="cc320-125">Declaring an object variable as a specific class gives you several advantages:</span></span>  
  
-   <span data-ttu-id="cc320-126">Otomatik tür denetleme</span><span class="sxs-lookup"><span data-stu-id="cc320-126">Automatic type checking</span></span>  
  
-   <span data-ttu-id="cc320-127">Belirli bir sınıfın tüm üyelerine erişim garanti</span><span class="sxs-lookup"><span data-stu-id="cc320-127">Guaranteed access to all members of the specific class</span></span>  
  
-   <span data-ttu-id="cc320-128">Kod Düzenleyicisi'nde Microsoft IntelliSense desteği</span><span class="sxs-lookup"><span data-stu-id="cc320-128">Microsoft IntelliSense support in the Code Editor</span></span>  
  
-   <span data-ttu-id="cc320-129">Kodunuzu geliştirilmiş okunabilirliğini</span><span class="sxs-lookup"><span data-stu-id="cc320-129">Improved readability of your code</span></span>  
  
-   <span data-ttu-id="cc320-130">Kodunuzu daha az hataları</span><span class="sxs-lookup"><span data-stu-id="cc320-130">Fewer errors in your code</span></span>  
  
-   <span data-ttu-id="cc320-131">Hataları sırasında yakalanan derleme zamanı yerine çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="cc320-131">Errors caught at compile time rather than run time</span></span>  
  
-   <span data-ttu-id="cc320-132">Daha hızlı kodu yürütme</span><span class="sxs-lookup"><span data-stu-id="cc320-132">Faster code execution</span></span>  
  
## <a name="access-to-object-variable-members"></a><span data-ttu-id="cc320-133">Değişken üyeleri nesne erişimi</span><span class="sxs-lookup"><span data-stu-id="cc320-133">Access to Object Variable Members</span></span>  
 <span data-ttu-id="cc320-134">Zaman `Option Strict` açık `On`, bir nesne değişkeninin yalnızca yöntemleri ve hangi bildirdiğiniz onu sınıfının özelliklerine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="cc320-134">When `Option Strict` is turned `On`, an object variable can access only the methods and properties of the class with which you declare it.</span></span> <span data-ttu-id="cc320-135">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="cc320-135">The following example illustrates this.</span></span>  
  
```vb  
' Option statements must precede all other source file lines.  
Option Strict On  
' Imports statement must precede all declarations in the source file.  
Imports System.Windows.Forms  
Public Sub accessMembers()  
    Dim p As Object  
    Dim q As System.Windows.Forms.Label  
    p = New System.Windows.Forms.Label  
    q = New System.Windows.Forms.Label  
    Dim j, k As Integer  
    ' The following statement generates a compiler ERROR.  
    j = p.Left  
    ' The following statement retrieves the left edge of the label in pixels.  
    k = q.Left  
End Sub  
```  
  
 <span data-ttu-id="cc320-136">Bu örnekte, `p` yalnızca üyeleri kullanabilirsiniz <xref:System.Object> sınıfının kendisini, hangi içermeyen `Left` özelliği.</span><span class="sxs-lookup"><span data-stu-id="cc320-136">In this example, `p` can use only the members of the <xref:System.Object> class itself, which do not include the `Left` property.</span></span> <span data-ttu-id="cc320-137">Diğer taraftan, `q` türünde olması bildirildi <xref:System.Windows.Forms.Label>, tüm yöntemleri ve özellikleri kullanabilmesi için <xref:System.Windows.Forms.Label> sınıfını <xref:System.Windows.Forms> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="cc320-137">On the other hand, `q` was declared to be of type <xref:System.Windows.Forms.Label>, so it can use all the methods and properties of the <xref:System.Windows.Forms.Label> class in the <xref:System.Windows.Forms> namespace.</span></span>  
  
## <a name="flexibility-of-object-variables"></a><span data-ttu-id="cc320-138">Nesne değişkenleri esnekliğini</span><span class="sxs-lookup"><span data-stu-id="cc320-138">Flexibility of Object Variables</span></span>  
 <span data-ttu-id="cc320-139">Devralma Hiyerarşisi nesneleri ile çalışırken, nesne değişkenlerini bildirme için kullanılacak hangi sınıfı seçimine sahip.</span><span class="sxs-lookup"><span data-stu-id="cc320-139">When working with objects in an inheritance hierarchy, you have a choice of which class to use for declaring your object variables.</span></span> <span data-ttu-id="cc320-140">Bu seçim yaparken, bir sınıf üyelerine erişimi karşı nesne ataması esnekliğini dengelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc320-140">In making this choice, you must balance flexibility of object assignment against access to members of a class.</span></span> <span data-ttu-id="cc320-141">Örneğin, yol açar Devralma Hiyerarşisi göz önünde bulundurun <xref:System.Windows.Forms.Form?displayProperty=nameWithType> sınıfı:</span><span class="sxs-lookup"><span data-stu-id="cc320-141">For example, consider the inheritance hierarchy that leads to the <xref:System.Windows.Forms.Form?displayProperty=nameWithType> class:</span></span>  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 <span data-ttu-id="cc320-142">Uygulamanızı form adlı bir sınıf tanımlar varsayalım `specialForm`, sınıfından devralan <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="cc320-142">Suppose your application defines a form class called `specialForm`, which inherits from class <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="cc320-143">Özellikle çok başvuran bir nesne değişkeni bildirme `specialForm`, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="cc320-143">You can declare an object variable that refers specifically to `specialForm`, as the following example shows.</span></span>  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 <span data-ttu-id="cc320-144">Önceki örnekte bildirimi değişkeni sınırlar `nextForm` sınıfındaki nesneler için `specialForm`, ancak tüm yöntemleri ve özellikleri de sağlar `specialForm` kullanılabilir `nextForm`, yanı sıra, tüm sınıflar olarak tüm üyeleri `specialForm` devralır.</span><span class="sxs-lookup"><span data-stu-id="cc320-144">The declaration in the preceding example limits the variable `nextForm` to objects of class `specialForm`, but it also makes all the methods and properties of `specialForm` available to `nextForm`, as well as all the members of all the classes from which `specialForm` inherits.</span></span>  
  
 <span data-ttu-id="cc320-145">Daha fazla genel bir nesne değişkeninin türü olmasını bildirerek yapabileceğiniz <xref:System.Windows.Forms.Form>, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="cc320-145">You can make an object variable more general by declaring it to be of type <xref:System.Windows.Forms.Form>, as the following example shows.</span></span>  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 <span data-ttu-id="cc320-146">Önceki örnekte bildirimi için uygulamanızda herhangi bir biçimde atamanıza olanak tanır `anyForm`.</span><span class="sxs-lookup"><span data-stu-id="cc320-146">The declaration in the preceding example lets you assign any form in your application to `anyForm`.</span></span> <span data-ttu-id="cc320-147">Ancak, ancak `anyForm` sınıfın tüm üyeleri erişebilir <xref:System.Windows.Forms.Form>, ek yöntemleri veya gibi belirli formlar için tanımlanan özellikler herhangi birini kullanamazsınız `specialForm`.</span><span class="sxs-lookup"><span data-stu-id="cc320-147">However, although `anyForm` can access all the members of class <xref:System.Windows.Forms.Form>, it cannot use any of the additional methods or properties defined for specific forms such as `specialForm`.</span></span>  
  
 <span data-ttu-id="cc320-148">Bir taban sınıfın tüm üyeleri için türetilen sınıflar kullanılabilir, ancak ek türetilmiş bir sınıf üyeleri için temel sınıf kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="cc320-148">All the members of a base class are available to derived classes, but the additional members of a derived class are unavailable to the base class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc320-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cc320-149">See Also</span></span>  
 [<span data-ttu-id="cc320-150">Nesne değişkenleri</span><span class="sxs-lookup"><span data-stu-id="cc320-150">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="cc320-151">Nesne değişkeni ataması</span><span class="sxs-lookup"><span data-stu-id="cc320-151">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="cc320-152">Nesne değişkeni değerleri</span><span class="sxs-lookup"><span data-stu-id="cc320-152">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [<span data-ttu-id="cc320-153">Nasıl yapılır: bir nesne değişkeni bildirme ve Visual Basic'te bir nesneyi atayın</span><span class="sxs-lookup"><span data-stu-id="cc320-153">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)  
 [<span data-ttu-id="cc320-154">Nasıl yapılır: bir nesnenin üyelerine erişme</span><span class="sxs-lookup"><span data-stu-id="cc320-154">How to: Access Members of an Object</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)  
 [<span data-ttu-id="cc320-155">New işleci</span><span class="sxs-lookup"><span data-stu-id="cc320-155">New Operator</span></span>](../../../../visual-basic/language-reference/operators/new-operator.md)  
 [<span data-ttu-id="cc320-156">Option Strict deyimi</span><span class="sxs-lookup"><span data-stu-id="cc320-156">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="cc320-157">Yerel tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="cc320-157">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
