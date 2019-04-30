---
title: "Nasıl yapılır: Bildirme ve Visual Basic'te bir varsayılan özelliğini çağırın"
ms.date: 07/20/2015
helpviewer_keywords:
- defaults [Visual Basic], properties
- properties [Visual Basic], default
- procedures [Visual Basic], defining
- default properties [Visual Basic], in Visual Basic
- Visual Basic code, procedures
- Visual Basic code, properties
- default properties
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
ms.openlocfilehash: 9ca9a0ccdac3ac13429928233a0c09d58427ce74
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665773"
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a><span data-ttu-id="ba87f-102">Nasıl yapılır: Bildirme ve Visual Basic'te bir varsayılan özelliğini çağırın</span><span class="sxs-lookup"><span data-stu-id="ba87f-102">How to: Declare and Call a Default Property in Visual Basic</span></span>
<span data-ttu-id="ba87f-103">A *varsayılan özellik* kodunuzun bu belirtmeden erişeceği sınıfın veya yapının bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="ba87f-103">A *default property* is a class or structure property that your code can access without specifying it.</span></span> <span data-ttu-id="ba87f-104">Kodu adları çağrılırken bir sınıf veya yapı ancak değil bir özellik ve bağlamı bir özellik erişim sağlar, varsa, Visual Basic erişim o sınıfın veya yapının varsayılan özellik giderir.</span><span class="sxs-lookup"><span data-stu-id="ba87f-104">When calling code names a class or structure but not a property, and the context allows access to a property, Visual Basic resolves the access to that class or structure's default property if one exists.</span></span>  
  
 <span data-ttu-id="ba87f-105">Bir sınıf veya yapı, en fazla bir varsayılan özelliğine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="ba87f-105">A class or structure can have at most one default property.</span></span> <span data-ttu-id="ba87f-106">Ancak, varsayılan bir özelliği aşırı yükleme ve birden fazla sürümüne sahip.</span><span class="sxs-lookup"><span data-stu-id="ba87f-106">However, you can overload a default property and have more than one version of it.</span></span>  
  
 <span data-ttu-id="ba87f-107">Daha fazla bilgi için [varsayılan](../../../../visual-basic/language-reference/modifiers/default.md).</span><span class="sxs-lookup"><span data-stu-id="ba87f-107">For more information, see [Default](../../../../visual-basic/language-reference/modifiers/default.md).</span></span>  
  
### <a name="to-declare-a-default-property"></a><span data-ttu-id="ba87f-108">Varsayılan bir özelliği bildirme</span><span class="sxs-lookup"><span data-stu-id="ba87f-108">To declare a default property</span></span>  
  
1. <span data-ttu-id="ba87f-109">Özelliği, normal bir şekilde bildirin.</span><span class="sxs-lookup"><span data-stu-id="ba87f-109">Declare the property in the normal way.</span></span> <span data-ttu-id="ba87f-110">Belirtmeyin `Shared` veya `Private` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="ba87f-110">Do not specify the `Shared` or `Private` keyword.</span></span>  
  
2. <span data-ttu-id="ba87f-111">Dahil `Default` özelliği bildirimindeki anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="ba87f-111">Include the `Default` keyword in the property declaration.</span></span>  
  
3. <span data-ttu-id="ba87f-112">Bir özellik için en az bir parametre belirtin.</span><span class="sxs-lookup"><span data-stu-id="ba87f-112">Specify at least one parameter for the property.</span></span> <span data-ttu-id="ba87f-113">En az bir bağımsız değişken almaz ve varsayılan bir özellik tanımlanamaz.</span><span class="sxs-lookup"><span data-stu-id="ba87f-113">You cannot define a default property that does not take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#17)]  
  
### <a name="to-call-a-default-property"></a><span data-ttu-id="ba87f-114">Varsayılan özellik çağırmak için</span><span class="sxs-lookup"><span data-stu-id="ba87f-114">To call a default property</span></span>  
  
1. <span data-ttu-id="ba87f-115">Bir değişken içeren bir sınıf veya yapı türü bildirin.</span><span class="sxs-lookup"><span data-stu-id="ba87f-115">Declare a variable of the containing class or structure type.</span></span>  
  
     [!code-vb[VbVbcnProcedures#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#16)]  
  
2. <span data-ttu-id="ba87f-116">Değişken adı bir ifadede tek başına, özellik adı burada normalde verilebilir kullanın.</span><span class="sxs-lookup"><span data-stu-id="ba87f-116">Use the variable name alone in an expression where you would normally include the property name.</span></span>  
  
     [!code-vb[VbVbcnProcedures#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#21)]  
  
3. <span data-ttu-id="ba87f-117">Değişken adı parantez içinde bir bağımsız değişken listesiyle izleyin.</span><span class="sxs-lookup"><span data-stu-id="ba87f-117">Follow the variable name with an argument list in parentheses.</span></span> <span data-ttu-id="ba87f-118">Varsayılan özellik en az bir bağımsız değişken almalıdır.</span><span class="sxs-lookup"><span data-stu-id="ba87f-118">A default property must take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#20)]  
  
4. <span data-ttu-id="ba87f-119">Varsayılan özellik değerini almak için bir bağımsız değişken listesiyle bir ifadede veya eşittir değişken adını kullanın (`=`) bir atama ifadesinde oturum açın.</span><span class="sxs-lookup"><span data-stu-id="ba87f-119">To retrieve the default property value, use the variable name, with an argument list, in an expression or following the equal (`=`) sign in an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#15)]  
  
5. <span data-ttu-id="ba87f-120">Varsayılan özellik değerini ayarlamak için değişken adı, atama deyiminin sol tarafında bir bağımsız değişken listesiyle kullanın.</span><span class="sxs-lookup"><span data-stu-id="ba87f-120">To set the default property value, use the variable name, with an argument list, on the left side of an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#14)]  
  
6. <span data-ttu-id="ba87f-121">Yalnızca diğer herhangi bir özelliğe erişmek için yaptığınız gibi her zaman varsayılan özellik adı değişken adı ile birlikte belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba87f-121">You can always specify the default property name together with the variable name, just as you would do to access any other property.</span></span>  
  
     [!code-vb[VbVbcnProcedures#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#19)]  
  
## <a name="example"></a><span data-ttu-id="ba87f-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="ba87f-122">Example</span></span>  
 <span data-ttu-id="ba87f-123">Aşağıdaki örnek, bir sınıf üzerinde varsayılan bir özelliği bildirir.</span><span class="sxs-lookup"><span data-stu-id="ba87f-123">The following example declares a default property on a class.</span></span>  
  
 [!code-vb[VbVbcnProcedures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="ba87f-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="ba87f-124">Example</span></span>  
 <span data-ttu-id="ba87f-125">Aşağıdaki örnek, varsayılan özellik nasıl çağırılacağını `myProperty` sınıfında `class1`.</span><span class="sxs-lookup"><span data-stu-id="ba87f-125">The following example demonstrates how to call the default property `myProperty` on class `class1`.</span></span> <span data-ttu-id="ba87f-126">Üç atama deyimleri değerleri depolamak `myProperty`ve <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> çağrı değerlerini okur.</span><span class="sxs-lookup"><span data-stu-id="ba87f-126">The three assignment statements store values in `myProperty`, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> call reads the values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#13)]  
  
 <span data-ttu-id="ba87f-127">Varsayılan özellik en yaygın kullanımı <xref:Microsoft.VisualBasic.Collection.Item%2A> çeşitli koleksiyon sınıflarını özelliği.</span><span class="sxs-lookup"><span data-stu-id="ba87f-127">The most common use of a default property is the <xref:Microsoft.VisualBasic.Collection.Item%2A> property on various collection classes.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ba87f-128">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="ba87f-128">Robust Programming</span></span>  
 <span data-ttu-id="ba87f-129">Varsayılan Özellikler kaynak kod-harfler küçük azalmasına neden olabilir, ancak bunlar kodunuzu okunacak daha zor hale getirebilir.</span><span class="sxs-lookup"><span data-stu-id="ba87f-129">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="ba87f-130">Bir sınıf veya yapı adı başvuru yaptığında çağıran kod, sınıf veya yapı, birlikte bilinen değilse, bu başvuruyu sınıf veya yapının kendisi veya varsayılan bir özellik olup erişen belirli olamaz.</span><span class="sxs-lookup"><span data-stu-id="ba87f-130">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="ba87f-131">Bu, derleyici hataları veya Zarif çalışma zamanı mantık hataları neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="ba87f-131">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="ba87f-132">Her zaman kullanarak biraz varsayılan özellik hata olasılığını azaltabilirsiniz [Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md) derleyici tür denetlemesini ayarlanacak `On`.</span><span class="sxs-lookup"><span data-stu-id="ba87f-132">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="ba87f-133">Bir önceden tanımlanmış sınıf veya yapı kodunuzda belirlemeniz gerekir, varsayılan bir özellik sahip olup olmadığını ve bu durumda kullanmayı planlıyorsanız, onun adı nedir?</span><span class="sxs-lookup"><span data-stu-id="ba87f-133">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="ba87f-134">Bu dezavantajların nedeniyle varsayılan özellikleri tanımlamaya değil dikkate almalısınız.</span><span class="sxs-lookup"><span data-stu-id="ba87f-134">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="ba87f-135">Kod okunabilirlik açısından, ayrıca her zaman tüm özelliklere açıkça başvuran göz önünde bulundurun, hatta özellikleri varsayılan.</span><span class="sxs-lookup"><span data-stu-id="ba87f-135">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba87f-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba87f-136">See also</span></span>

- [<span data-ttu-id="ba87f-137">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="ba87f-137">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="ba87f-138">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="ba87f-138">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="ba87f-139">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="ba87f-139">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="ba87f-140">Default</span><span class="sxs-lookup"><span data-stu-id="ba87f-140">Default</span></span>](../../../../visual-basic/language-reference/modifiers/default.md)
- [<span data-ttu-id="ba87f-141">Visual Basic'de özellikler ile değişkenler arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="ba87f-141">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="ba87f-142">Nasıl yapılır: Özellik oluşturma</span><span class="sxs-lookup"><span data-stu-id="ba87f-142">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="ba87f-143">Nasıl yapılır: Bir özelliği karışık erişim düzeyleriyle bildirme</span><span class="sxs-lookup"><span data-stu-id="ba87f-143">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="ba87f-144">Nasıl yapılır: Bir özellik yordamı çağırma</span><span class="sxs-lookup"><span data-stu-id="ba87f-144">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="ba87f-145">Nasıl yapılır: Bir özelliğe değer ekleme</span><span class="sxs-lookup"><span data-stu-id="ba87f-145">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="ba87f-146">Nasıl yapılır: Bir özellikten değer alma</span><span class="sxs-lookup"><span data-stu-id="ba87f-146">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
