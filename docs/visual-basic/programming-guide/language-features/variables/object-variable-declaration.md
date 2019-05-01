---
title: Nesne Değişken Bildirimi (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 4a3ef3a8254153fa8695ffacd9829ca9316d77a5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61959984"
---
# <a name="object-variable-declaration-visual-basic"></a><span data-ttu-id="8fbef-102">Nesne Değişken Bildirimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8fbef-102">Object Variable Declaration (Visual Basic)</span></span>
<span data-ttu-id="8fbef-103">Bir normal bir bildirim deyiminin bir nesne değişkenini bildirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="8fbef-103">You use a normal declaration statement to declare an object variable.</span></span> <span data-ttu-id="8fbef-104">Veri türü için ya da belirttiğiniz `Object` (diğer bir deyişle, [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)) veya nesne olduğu oluşturulacak daha belirli bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="8fbef-104">For the data type, you specify either `Object` (that is, the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)) or a more specific class from which the object is to be created.</span></span>  
  
 <span data-ttu-id="8fbef-105">Bir değişken olarak bildirme `Object` olarak bildirme aynı <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8fbef-105">Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="8fbef-106">Belirli nesne sınıfı sahip bir değişken bildirdiğinizde tüm yöntemler ve o sınıfın ve devraldığı sınıfları tarafından kullanıma sunulan özellikler erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8fbef-106">When you declare a variable with a specific object class, it can access all the methods and properties exposed by that class and the classes from which it inherits.</span></span> <span data-ttu-id="8fbef-107">Değişkenle bildirirseniz <xref:System.Object>, yalnızca üyelerinin erişebildiğinizi <xref:System.Object> sınıf özelliğini sürece `Option Strict Off` geç bağlamaya izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="8fbef-107">If you declare the variable with <xref:System.Object>, it can access only the members of the <xref:System.Object> class, unless you turn `Option Strict Off` to allow late binding.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="8fbef-108">Bildirim Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8fbef-108">Declaration Syntax</span></span>  
 <span data-ttu-id="8fbef-109">Bir nesne değişkenini bildirmek için aşağıdaki sözdizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="8fbef-109">Use the following syntax to declare an object variable:</span></span>  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 <span data-ttu-id="8fbef-110">Ayrıca belirtebileceğiniz [genel](../../../../visual-basic/language-reference/modifiers/public.md), [korumalı](../../../../visual-basic/language-reference/modifiers/protected.md), [arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, [özel](../../../../visual-basic/language-reference/modifiers/private.md), [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md), veya [statik](../../../../visual-basic/language-reference/modifiers/static.md) bildirimi.</span><span class="sxs-lookup"><span data-stu-id="8fbef-110">You can also specify [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), or [Static](../../../../visual-basic/language-reference/modifiers/static.md) in the declaration.</span></span> <span data-ttu-id="8fbef-111">Aşağıdaki örnek bildirimleri geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="8fbef-111">The following example declarations are valid:</span></span>  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a><span data-ttu-id="8fbef-112">Geç bağlama ve erken bağlama</span><span class="sxs-lookup"><span data-stu-id="8fbef-112">Late Binding and Early Binding</span></span>  
 <span data-ttu-id="8fbef-113">Bazen belirli sınıf kodunuzu çalışana kadar bilinmiyor.</span><span class="sxs-lookup"><span data-stu-id="8fbef-113">Sometimes the specific class is unknown until your code runs.</span></span> <span data-ttu-id="8fbef-114">Bu durumda, nesne değişkeni ile bildirilmelidir `Object` veri türü.</span><span class="sxs-lookup"><span data-stu-id="8fbef-114">In this case, you must declare the object variable with the `Object` data type.</span></span> <span data-ttu-id="8fbef-115">Bu genel bir tür nesneyi başvuru oluşturur ve belirli bir sınıf, çalışma zamanında atanır.</span><span class="sxs-lookup"><span data-stu-id="8fbef-115">This creates a general reference to any type of object, and the specific class is assigned at run time.</span></span> <span data-ttu-id="8fbef-116">Bu adlandırılır *geç bağlama*.</span><span class="sxs-lookup"><span data-stu-id="8fbef-116">This is called *late binding*.</span></span> <span data-ttu-id="8fbef-117">Geç bağlama ek yürütme süresi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8fbef-117">Late binding requires additional execution time.</span></span> <span data-ttu-id="8fbef-118">Ayrıca, kodunuzun en son kendisine atadığınız sınıfının özellikleri ve yöntemleri için sınırlar.</span><span class="sxs-lookup"><span data-stu-id="8fbef-118">It also limits your code to the methods and properties of the class you have most recently assigned to it.</span></span> <span data-ttu-id="8fbef-119">Kodunuzu farklı bir sınıfın üyeleri erişmeye çalışırsa, bu çalışma zamanı hatalarına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="8fbef-119">This can cause run-time errors if your code attempts to access members of a different class.</span></span>  
  
 <span data-ttu-id="8fbef-120">Derleme zamanında belirli sınıf bildiğinizde, bu sınıfı olmasını nesne değişkeni bildirmelidir.</span><span class="sxs-lookup"><span data-stu-id="8fbef-120">When you know the specific class at compile time, you should declare the object variable to be of that class.</span></span> <span data-ttu-id="8fbef-121">Bu adlandırılır *erken bağlama*.</span><span class="sxs-lookup"><span data-stu-id="8fbef-121">This is called *early binding*.</span></span> <span data-ttu-id="8fbef-122">Erken bağlama performansını artırır ve tüm yöntemler ve Özellikler belirli bir sınıfın kod erişiminizi güvence altına alır.</span><span class="sxs-lookup"><span data-stu-id="8fbef-122">Early binding improves performance and guarantees your code access to all the methods and properties of the specific class.</span></span> <span data-ttu-id="8fbef-123">Önceki örnek bildirimlerinde, değişken `objA` yalnızca sınıfın nesneleri kullanan <xref:System.Windows.Forms.Label?displayProperty=nameWithType>, belirtmeniz gerekir `As System.Windows.Forms.Label` kendi bildirimi.</span><span class="sxs-lookup"><span data-stu-id="8fbef-123">In the preceding example declarations, if variable `objA` uses only objects of class <xref:System.Windows.Forms.Label?displayProperty=nameWithType>, you should specify `As System.Windows.Forms.Label` in its declaration.</span></span>  
  
### <a name="advantages-of-early-binding"></a><span data-ttu-id="8fbef-124">Erken bağlama avantajları</span><span class="sxs-lookup"><span data-stu-id="8fbef-124">Advantages of Early Binding</span></span>  
 <span data-ttu-id="8fbef-125">Belirli bir sınıf olarak bir nesne değişkeni bildirme çeşitli avantajlar sağlar:</span><span class="sxs-lookup"><span data-stu-id="8fbef-125">Declaring an object variable as a specific class gives you several advantages:</span></span>  
  
- <span data-ttu-id="8fbef-126">Otomatik tür denetleme</span><span class="sxs-lookup"><span data-stu-id="8fbef-126">Automatic type checking</span></span>  
  
- <span data-ttu-id="8fbef-127">Belirli bir sınıfın tüm üyeleri için erişim garantisi</span><span class="sxs-lookup"><span data-stu-id="8fbef-127">Guaranteed access to all members of the specific class</span></span>  
  
- <span data-ttu-id="8fbef-128">Kod Düzenleyicisi'nde Microsoft IntelliSense desteği</span><span class="sxs-lookup"><span data-stu-id="8fbef-128">Microsoft IntelliSense support in the Code Editor</span></span>  
  
- <span data-ttu-id="8fbef-129">Geliştirilmiş kod okunabilirliğini</span><span class="sxs-lookup"><span data-stu-id="8fbef-129">Improved readability of your code</span></span>  
  
- <span data-ttu-id="8fbef-130">Kodunuzu daha az hataları</span><span class="sxs-lookup"><span data-stu-id="8fbef-130">Fewer errors in your code</span></span>  
  
- <span data-ttu-id="8fbef-131">Hataları sırasında yakalanan derleme zamanı yerine çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="8fbef-131">Errors caught at compile time rather than run time</span></span>  
  
- <span data-ttu-id="8fbef-132">Daha hızlı kod yürütme</span><span class="sxs-lookup"><span data-stu-id="8fbef-132">Faster code execution</span></span>  
  
## <a name="access-to-object-variable-members"></a><span data-ttu-id="8fbef-133">Nesne değişkeni üye erişimi</span><span class="sxs-lookup"><span data-stu-id="8fbef-133">Access to Object Variable Members</span></span>  
 <span data-ttu-id="8fbef-134">Zaman `Option Strict` etkinleştirilmişse `On`, yalnızca yöntemleri ve özellikleri ile kaydedilebilmeniz bu sınıfın bir nesne değişkenine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="8fbef-134">When `Option Strict` is turned `On`, an object variable can access only the methods and properties of the class with which you declare it.</span></span> <span data-ttu-id="8fbef-135">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="8fbef-135">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="8fbef-136">Bu örnekte, `p` yalnızca üyelerinin kullanabileceği <xref:System.Object> kendisi, hangi içermeyen sınıf `Left` özelliği.</span><span class="sxs-lookup"><span data-stu-id="8fbef-136">In this example, `p` can use only the members of the <xref:System.Object> class itself, which do not include the `Left` property.</span></span> <span data-ttu-id="8fbef-137">Öte yandan, `q` türü olarak bildirildi <xref:System.Windows.Forms.Label>, tüm yöntemleri ve özellikleri kullanabilmesi için <xref:System.Windows.Forms.Label> sınıfını <xref:System.Windows.Forms> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="8fbef-137">On the other hand, `q` was declared to be of type <xref:System.Windows.Forms.Label>, so it can use all the methods and properties of the <xref:System.Windows.Forms.Label> class in the <xref:System.Windows.Forms> namespace.</span></span>  
  
## <a name="flexibility-of-object-variables"></a><span data-ttu-id="8fbef-138">Nesne değişkenleri esnekliği</span><span class="sxs-lookup"><span data-stu-id="8fbef-138">Flexibility of Object Variables</span></span>  
 <span data-ttu-id="8fbef-139">Devralma Hiyerarşisi nesneleri ile çalışırken, nesne değişkenini bildirmek için kullanılacak hangi sınıfın vardır.</span><span class="sxs-lookup"><span data-stu-id="8fbef-139">When working with objects in an inheritance hierarchy, you have a choice of which class to use for declaring your object variables.</span></span> <span data-ttu-id="8fbef-140">Bu seçim yaparken, nesne ataması bir sınıf üyelerine erişimi karşı esnekliğini dengelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8fbef-140">In making this choice, you must balance flexibility of object assignment against access to members of a class.</span></span> <span data-ttu-id="8fbef-141">Örneğin, yol açar Devralma Hiyerarşisi düşünün <xref:System.Windows.Forms.Form?displayProperty=nameWithType> sınıfı:</span><span class="sxs-lookup"><span data-stu-id="8fbef-141">For example, consider the inheritance hierarchy that leads to the <xref:System.Windows.Forms.Form?displayProperty=nameWithType> class:</span></span>  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 <span data-ttu-id="8fbef-142">Uygulamanızı form adlı bir sınıf tanımlar varsayalım `specialForm`, sınıfından devralan <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="8fbef-142">Suppose your application defines a form class called `specialForm`, which inherits from class <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="8fbef-143">Özellikle çok başvuran bir nesne değişkeninin bildirebilirsiniz `specialForm`aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="8fbef-143">You can declare an object variable that refers specifically to `specialForm`, as the following example shows.</span></span>  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 <span data-ttu-id="8fbef-144">Değişken bildirimi önceki örnekte sınırlar `nextForm` sınıfındaki nesneler için `specialForm`, ancak tüm yöntemleri ve özellikleri de getirir `specialForm` kullanılabilir `nextForm`, içinden tüm sınıflar gibi tüm üyelerinin yanı sıra `specialForm` devralır.</span><span class="sxs-lookup"><span data-stu-id="8fbef-144">The declaration in the preceding example limits the variable `nextForm` to objects of class `specialForm`, but it also makes all the methods and properties of `specialForm` available to `nextForm`, as well as all the members of all the classes from which `specialForm` inherits.</span></span>  
  
 <span data-ttu-id="8fbef-145">Daha genel bir nesne değişkeninin türü olmasını bildirerek yapabileceğiniz <xref:System.Windows.Forms.Form>aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="8fbef-145">You can make an object variable more general by declaring it to be of type <xref:System.Windows.Forms.Form>, as the following example shows.</span></span>  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 <span data-ttu-id="8fbef-146">Önceki örnekte bildirimi için uygulamanızda herhangi bir biçimde atamanıza olanak sağlar `anyForm`.</span><span class="sxs-lookup"><span data-stu-id="8fbef-146">The declaration in the preceding example lets you assign any form in your application to `anyForm`.</span></span> <span data-ttu-id="8fbef-147">Ancak, ancak `anyForm` sınıfın tüm üyeleri erişebilir <xref:System.Windows.Forms.Form>, herhangi bir ek yöntemleri veya özellikleri gibi özel formlar için tanımlanan kullanamazsınız `specialForm`.</span><span class="sxs-lookup"><span data-stu-id="8fbef-147">However, although `anyForm` can access all the members of class <xref:System.Windows.Forms.Form>, it cannot use any of the additional methods or properties defined for specific forms such as `specialForm`.</span></span>  
  
 <span data-ttu-id="8fbef-148">Türetilen sınıflar için bir taban sınıfın tüm üyeleri kullanılabilir, ancak ek üyeler türetilmiş bir sınıfın temel sınıf için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8fbef-148">All the members of a base class are available to derived classes, but the additional members of a derived class are unavailable to the base class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fbef-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fbef-149">See also</span></span>

- [<span data-ttu-id="8fbef-150">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="8fbef-150">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="8fbef-151">Nesne Değişkeni Ataması</span><span class="sxs-lookup"><span data-stu-id="8fbef-151">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="8fbef-152">Nesne Değişkeni Değerleri</span><span class="sxs-lookup"><span data-stu-id="8fbef-152">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="8fbef-153">Nasıl yapılır: Bir nesne değişkeni bildirme ve Visual Basic'te bir nesne atama</span><span class="sxs-lookup"><span data-stu-id="8fbef-153">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [<span data-ttu-id="8fbef-154">Nasıl yapılır: Bir nesnenin üyelerine erişim</span><span class="sxs-lookup"><span data-stu-id="8fbef-154">How to: Access Members of an Object</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [<span data-ttu-id="8fbef-155">New İşleci</span><span class="sxs-lookup"><span data-stu-id="8fbef-155">New Operator</span></span>](../../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="8fbef-156">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="8fbef-156">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="8fbef-157">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="8fbef-157">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
