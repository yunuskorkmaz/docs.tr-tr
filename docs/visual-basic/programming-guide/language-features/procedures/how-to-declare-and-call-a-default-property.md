---
title: "Nasıl yapılır: Visual Basic'de Varsayılan Bir Özelliği Bildirme ve Çağırma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- defaults [Visual Basic], properties
- properties [Visual Basic], default
- procedures [Visual Basic], defining
- default properties [Visual Basic], in Visual Basic
- Visual Basic code, procedures
- Visual Basic code, properties
- default properties
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8baa03e37325a6ad7065ec1a60052b3ea6a46c6f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a><span data-ttu-id="f6b1a-102">Nasıl yapılır: Visual Basic'de Varsayılan Bir Özelliği Bildirme ve Çağırma</span><span class="sxs-lookup"><span data-stu-id="f6b1a-102">How to: Declare and Call a Default Property in Visual Basic</span></span>
<span data-ttu-id="f6b1a-103">A *varsayılan özellik* kodunuzu belirtme olmadan erişebileceği bir sınıf veya yapı özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="f6b1a-103">A *default property* is a class or structure property that your code can access without specifying it.</span></span> <span data-ttu-id="f6b1a-104">Kodu çağırma bir sınıf veya yapı ancak bir özellik adları ve bağlam bir özelliğine erişim verir [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] varsa, bu sınıf veya yapısı varsayılan özellik erişim giderir.</span><span class="sxs-lookup"><span data-stu-id="f6b1a-104">When calling code names a class or structure but not a property, and the context allows access to a property, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] resolves the access to that class or structure's default property if one exists.</span></span>  
  
 <span data-ttu-id="f6b1a-105">En çok bir sınıf veya yapı bir varsayılan özelliğine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="f6b1a-105">A class or structure can have at most one default property.</span></span> <span data-ttu-id="f6b1a-106">Ancak, varsayılan bir özellik aşırı yükleme ve birden fazla sürümüne sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f6b1a-106">However, you can overload a default property and have more than one version of it.</span></span>  
  
 <span data-ttu-id="f6b1a-107">Daha fazla bilgi için bkz: [varsayılan](../../../../visual-basic/language-reference/modifiers/default.md).</span><span class="sxs-lookup"><span data-stu-id="f6b1a-107">For more information, see [Default](../../../../visual-basic/language-reference/modifiers/default.md).</span></span>  
  
### <a name="to-declare-a-default-property"></a><span data-ttu-id="f6b1a-108">Varsayılan bir özellik bildirmek için</span><span class="sxs-lookup"><span data-stu-id="f6b1a-108">To declare a default property</span></span>  
  
1.  <span data-ttu-id="f6b1a-109">Özellik normal şekilde bildirin.</span><span class="sxs-lookup"><span data-stu-id="f6b1a-109">Declare the property in the normal way.</span></span> <span data-ttu-id="f6b1a-110">Belirtmeyin `Shared` veya `Private` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="f6b1a-110">Do not specify the `Shared` or `Private` keyword.</span></span>  
  
2.  <span data-ttu-id="f6b1a-111">Dahil `Default` özellik bildirimi anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="f6b1a-111">Include the `Default` keyword in the property declaration.</span></span>  
  
3.  <span data-ttu-id="f6b1a-112">Özelliği için en az bir parametre belirtin.</span><span class="sxs-lookup"><span data-stu-id="f6b1a-112">Specify at least one parameter for the property.</span></span> <span data-ttu-id="f6b1a-113">En az bir bağımsız değişken almaz ve varsayılan bir özellik tanımlanamaz.</span><span class="sxs-lookup"><span data-stu-id="f6b1a-113">You cannot define a default property that does not take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#17](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_1.vb)]  
  
### <a name="to-call-a-default-property"></a><span data-ttu-id="f6b1a-114">Varsayılan bir özellik çağırmak için</span><span class="sxs-lookup"><span data-stu-id="f6b1a-114">To call a default property</span></span>  
  
1.  <span data-ttu-id="f6b1a-115">İçeren sınıf veya yapı türünde bir değişken bildirin.</span><span class="sxs-lookup"><span data-stu-id="f6b1a-115">Declare a variable of the containing class or structure type.</span></span>  
  
     [!code-vb[VbVbcnProcedures#16](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_2.vb)]  
  
2.  <span data-ttu-id="f6b1a-116">Burada normal olarak özellik adını içerir bir ifadede tek başına değişken adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="f6b1a-116">Use the variable name alone in an expression where you would normally include the property name.</span></span>  
  
     [!code-vb[VbVbcnProcedures#21](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_3.vb)]  
  
3.  <span data-ttu-id="f6b1a-117">Bir bağımsız değişken listesi parantez içinde değişken adıyla izleyin.</span><span class="sxs-lookup"><span data-stu-id="f6b1a-117">Follow the variable name with an argument list in parentheses.</span></span> <span data-ttu-id="f6b1a-118">Varsayılan bir özellik en az bir değişken almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6b1a-118">A default property must take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#20](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_4.vb)]  
  
4.  <span data-ttu-id="f6b1a-119">Varsayılan özellik değerini almak için bir bağımsız değişken listesiyle bir ifadede ya da eşit aşağıdaki değişken adını kullanın (`=`) bir atama deyiminde oturum açın.</span><span class="sxs-lookup"><span data-stu-id="f6b1a-119">To retrieve the default property value, use the variable name, with an argument list, in an expression or following the equal (`=`) sign in an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#15](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_5.vb)]  
  
5.  <span data-ttu-id="f6b1a-120">Varsayılan özellik değerini ayarlamak için bir atama deyimi sol tarafındaki bir bağımsız değişken listesiyle değişken adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="f6b1a-120">To set the default property value, use the variable name, with an argument list, on the left side of an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#14](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_6.vb)]  
  
6.  <span data-ttu-id="f6b1a-121">Yalnızca diğer herhangi bir özelliğe erişmek için yaptığınız gibi her zaman varsayılan özellik adı değişken adı ile birlikte belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6b1a-121">You can always specify the default property name together with the variable name, just as you would do to access any other property.</span></span>  
  
     [!code-vb[VbVbcnProcedures#19](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_7.vb)]  
  
## <a name="example"></a><span data-ttu-id="f6b1a-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="f6b1a-122">Example</span></span>  
 <span data-ttu-id="f6b1a-123">Aşağıdaki örnek, bir sınıf üzerinde varsayılan bir özellik bildirir.</span><span class="sxs-lookup"><span data-stu-id="f6b1a-123">The following example declares a default property on a class.</span></span>  
  
 [!code-vb[VbVbcnProcedures#12](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_8.vb)]  
  
## <a name="example"></a><span data-ttu-id="f6b1a-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="f6b1a-124">Example</span></span>  
 <span data-ttu-id="f6b1a-125">Aşağıdaki örnek varsayılan özellik nasıl çağırılacağını `myProperty` sınıfındaki `class1`.</span><span class="sxs-lookup"><span data-stu-id="f6b1a-125">The following example demonstrates how to call the default property `myProperty` on class `class1`.</span></span> <span data-ttu-id="f6b1a-126">Üç atama deyimleri değerlerini depolamak `myProperty`ve <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> çağrısı değerleri okur.</span><span class="sxs-lookup"><span data-stu-id="f6b1a-126">The three assignment statements store values in `myProperty`, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> call reads the values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#13](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_9.vb)]  
  
 <span data-ttu-id="f6b1a-127">Varsayılan bir özellik en yaygın kullanımı <xref:Microsoft.VisualBasic.Collection.Item%2A> çeşitli koleksiyon sınıfları özelliği.</span><span class="sxs-lookup"><span data-stu-id="f6b1a-127">The most common use of a default property is the <xref:Microsoft.VisualBasic.Collection.Item%2A> property on various collection classes.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f6b1a-128">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="f6b1a-128">Robust Programming</span></span>  
 <span data-ttu-id="f6b1a-129">Varsayılan Özellikler kaynak kod-karakterlerini küçük azalmasına neden olabilir, ancak bunlar kodunuzu okumak daha zor hale getirebilir.</span><span class="sxs-lookup"><span data-stu-id="f6b1a-129">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="f6b1a-130">Sınıf veya yapı adı için bir başvuru yaptığında, çağrıyı yapan kod, sınıf veya yapı, bilinen değilse, bu başvuru sınıf veya yapı kendisini veya varsayılan bir özellik mi erişen belirli olamaz.</span><span class="sxs-lookup"><span data-stu-id="f6b1a-130">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="f6b1a-131">Bu derleyici hataları veya Zarif çalışma zamanı mantık hataları neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f6b1a-131">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="f6b1a-132">Her zaman kullanarak varsayılan özellik hataları olasılığını biraz azaltabilir [Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md) denetlemesini derleyici türünü ayarlamak için `On`.</span><span class="sxs-lookup"><span data-stu-id="f6b1a-132">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="f6b1a-133">Önceden tanımlanmış sınıf veya yapı kodunuzda belirlemeniz gerekir varsayılan bir özellik olup olmadığını ve bu durumda kullanmayı planlıyorsanız, ne adıdır.</span><span class="sxs-lookup"><span data-stu-id="f6b1a-133">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="f6b1a-134">Bu olumsuzlukları nedeniyle varsayılan özellikleri tanımlamaya değil göz önünde bulundurmalısınız.</span><span class="sxs-lookup"><span data-stu-id="f6b1a-134">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="f6b1a-135">Kod okunabilirlik için ayrıca her zaman tüm özelliklerini açıkça başvuran göz önünde bulundurun, hatta özellikleri varsayılan.</span><span class="sxs-lookup"><span data-stu-id="f6b1a-135">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6b1a-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f6b1a-136">See Also</span></span>  
 [<span data-ttu-id="f6b1a-137">Özellik yordamları</span><span class="sxs-lookup"><span data-stu-id="f6b1a-137">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="f6b1a-138">Parametreler ve bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="f6b1a-138">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="f6b1a-139">Property deyimi</span><span class="sxs-lookup"><span data-stu-id="f6b1a-139">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="f6b1a-140">Varsayılan</span><span class="sxs-lookup"><span data-stu-id="f6b1a-140">Default</span></span>](../../../../visual-basic/language-reference/modifiers/default.md)  
 [<span data-ttu-id="f6b1a-141">Visual Basic'de özellikler ve değişkenler arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="f6b1a-141">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="f6b1a-142">Nasıl yapılır: özellik oluşturma</span><span class="sxs-lookup"><span data-stu-id="f6b1a-142">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="f6b1a-143">Nasıl yapılır: bir özelliği karışık erişim düzeyleriyle bildirme</span><span class="sxs-lookup"><span data-stu-id="f6b1a-143">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="f6b1a-144">Nasıl yapılır: bir özellik yordamı çağırma</span><span class="sxs-lookup"><span data-stu-id="f6b1a-144">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="f6b1a-145">Nasıl yapılır: bir özelliğe değer ekleme</span><span class="sxs-lookup"><span data-stu-id="f6b1a-145">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)  
 [<span data-ttu-id="f6b1a-146">Nasıl yapılır: bir özellikten değer alma</span><span class="sxs-lookup"><span data-stu-id="f6b1a-146">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
