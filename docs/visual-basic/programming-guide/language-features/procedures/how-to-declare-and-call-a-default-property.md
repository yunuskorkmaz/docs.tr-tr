---
description: "Hakkında daha fazla bilgi edinin: nasıl yapılır: Visual Basic ' de varsayılan bir özellik bildirme ve çağırma"
title: 'Nasıl yapılır: Varsayılan Bir Özelliği Bildirme ve Çağırma'
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
ms.openlocfilehash: 2a0e82fe89bb89613996f613930ace1aa6e41b7f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472455"
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a><span data-ttu-id="444de-103">Nasıl yapılır: Visual Basic'de Varsayılan Bir Özelliği Bildirme ve Çağırma</span><span class="sxs-lookup"><span data-stu-id="444de-103">How to: Declare and Call a Default Property in Visual Basic</span></span>

<span data-ttu-id="444de-104">*Varsayılan özellik* , kodunuzun onu belirtmeden erişebileceği bir sınıf veya yapı özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="444de-104">A *default property* is a class or structure property that your code can access without specifying it.</span></span> <span data-ttu-id="444de-105">Kod adlarını bir sınıf veya yapıya çağırmak ancak bir özelliği değil ve bağlam bir özelliğe erişim izni veriyorsa, Visual Basic, varsa bu sınıfa veya yapının varsayılan özelliğine erişimi çözer.</span><span class="sxs-lookup"><span data-stu-id="444de-105">When calling code names a class or structure but not a property, and the context allows access to a property, Visual Basic resolves the access to that class or structure's default property if one exists.</span></span>  
  
 <span data-ttu-id="444de-106">Bir sınıf veya yapı en çok bir varsayılan özelliğe sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="444de-106">A class or structure can have at most one default property.</span></span> <span data-ttu-id="444de-107">Ancak, varsayılan bir özelliği aşırı yükleyebilir ve birden fazla sürümüne sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="444de-107">However, you can overload a default property and have more than one version of it.</span></span>  
  
 <span data-ttu-id="444de-108">Daha fazla bilgi için bkz. [Default](../../../language-reference/modifiers/default.md).</span><span class="sxs-lookup"><span data-stu-id="444de-108">For more information, see [Default](../../../language-reference/modifiers/default.md).</span></span>  
  
### <a name="to-declare-a-default-property"></a><span data-ttu-id="444de-109">Varsayılan bir özellik bildirmek için</span><span class="sxs-lookup"><span data-stu-id="444de-109">To declare a default property</span></span>  
  
1. <span data-ttu-id="444de-110">Özelliği normal şekilde bildirin.</span><span class="sxs-lookup"><span data-stu-id="444de-110">Declare the property in the normal way.</span></span> <span data-ttu-id="444de-111">`Shared`Or `Private` anahtar sözcüğünü belirtmeyin.</span><span class="sxs-lookup"><span data-stu-id="444de-111">Do not specify the `Shared` or `Private` keyword.</span></span>  
  
2. <span data-ttu-id="444de-112">`Default`Anahtar sözcüğünü Özellik bildirimine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="444de-112">Include the `Default` keyword in the property declaration.</span></span>  
  
3. <span data-ttu-id="444de-113">Özellik için en az bir parametre belirtin.</span><span class="sxs-lookup"><span data-stu-id="444de-113">Specify at least one parameter for the property.</span></span> <span data-ttu-id="444de-114">En az bir bağımsız değişken almaz varsayılan bir özellik tanımlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="444de-114">You cannot define a default property that does not take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#17)]  
  
### <a name="to-call-a-default-property"></a><span data-ttu-id="444de-115">Varsayılan bir özelliği çağırmak için</span><span class="sxs-lookup"><span data-stu-id="444de-115">To call a default property</span></span>  
  
1. <span data-ttu-id="444de-116">Kapsayan sınıf veya yapı türü için bir değişken bildirin.</span><span class="sxs-lookup"><span data-stu-id="444de-116">Declare a variable of the containing class or structure type.</span></span>  
  
     [!code-vb[VbVbcnProcedures#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#16)]  
  
2. <span data-ttu-id="444de-117">Değişken adını, normalde özellik adını dahil ettiğiniz bir ifadede kullanın.</span><span class="sxs-lookup"><span data-stu-id="444de-117">Use the variable name alone in an expression where you would normally include the property name.</span></span>  
  
     [!code-vb[VbVbcnProcedures#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#21)]  
  
3. <span data-ttu-id="444de-118">Parantez içindeki bir bağımsız değişken listesiyle birlikte değişken adını izleyin.</span><span class="sxs-lookup"><span data-stu-id="444de-118">Follow the variable name with an argument list in parentheses.</span></span> <span data-ttu-id="444de-119">Varsayılan özellik en az bir bağımsız değişken almalıdır.</span><span class="sxs-lookup"><span data-stu-id="444de-119">A default property must take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#20)]  
  
4. <span data-ttu-id="444de-120">Varsayılan özellik değerini almak için, değişken adını bağımsız değişken listesiyle, bir ifadede veya bir `=` atama deyiminde eşittir () işaretinden sonra kullanın.</span><span class="sxs-lookup"><span data-stu-id="444de-120">To retrieve the default property value, use the variable name, with an argument list, in an expression or following the equal (`=`) sign in an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#15)]  
  
5. <span data-ttu-id="444de-121">Varsayılan özellik değerini ayarlamak için, bir atama ifadesinin sol tarafında bir bağımsız değişken listesiyle birlikte değişken adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="444de-121">To set the default property value, use the variable name, with an argument list, on the left side of an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#14)]  
  
6. <span data-ttu-id="444de-122">Herhangi bir özelliğe erişmek için yaptığınız gibi, her zaman varsayılan özellik adını değişken adıyla birlikte belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="444de-122">You can always specify the default property name together with the variable name, just as you would do to access any other property.</span></span>  
  
     [!code-vb[VbVbcnProcedures#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#19)]  
  
## <a name="example"></a><span data-ttu-id="444de-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="444de-123">Example</span></span>  

 <span data-ttu-id="444de-124">Aşağıdaki örnek, bir sınıfında varsayılan bir özellik bildirir.</span><span class="sxs-lookup"><span data-stu-id="444de-124">The following example declares a default property on a class.</span></span>  
  
 [!code-vb[VbVbcnProcedures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="444de-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="444de-125">Example</span></span>  

 <span data-ttu-id="444de-126">Aşağıdaki örnek, sınıfında varsayılan özelliğin nasıl çağrılacağını gösterir `myProperty` `class1` .</span><span class="sxs-lookup"><span data-stu-id="444de-126">The following example demonstrates how to call the default property `myProperty` on class `class1`.</span></span> <span data-ttu-id="444de-127">Üç atama deyimi içindeki değerleri depolar `myProperty` ve <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> çağrı değerleri okur.</span><span class="sxs-lookup"><span data-stu-id="444de-127">The three assignment statements store values in `myProperty`, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> call reads the values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#13)]  
  
 <span data-ttu-id="444de-128">Varsayılan bir özelliğin en yaygın kullanımı, <xref:Microsoft.VisualBasic.Collection.Item%2A> çeşitli koleksiyon sınıflarının özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="444de-128">The most common use of a default property is the <xref:Microsoft.VisualBasic.Collection.Item%2A> property on various collection classes.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="444de-129">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="444de-129">Robust Programming</span></span>  

 <span data-ttu-id="444de-130">Varsayılan Özellikler, kaynak kodu karakterlerinin küçük bir azalmasına neden olabilir, ancak kodunuzun okunmasını zorlaşabilir.</span><span class="sxs-lookup"><span data-stu-id="444de-130">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="444de-131">Çağıran kod sınıfınız veya yapınız hakkında bilgi sahibi değilse, sınıf veya yapı adına bir başvuru yaptığında, başvurunun sınıfa veya yapıya ya da bir varsayılan özelliğe erişim izni verip etmediği kesin olamaz.</span><span class="sxs-lookup"><span data-stu-id="444de-131">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="444de-132">Bu, derleyici hatalarına veya hafif çalışma zamanı mantığı hatalarına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="444de-132">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="444de-133">Derleyici türü denetimini olarak ayarlamak için, her zaman [katı deyimin seçeneğini](../../../language-reference/statements/option-strict-statement.md) kullanarak varsayılan özellik hatalarının olasılığını azaltabilirsiniz `On` .</span><span class="sxs-lookup"><span data-stu-id="444de-133">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="444de-134">Kodunuzda önceden tanımlanmış bir sınıf veya yapı kullanmayı planlıyorsanız, bunun varsayılan bir özelliği olup olmadığını ve varsa adının ne olduğunu belirlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="444de-134">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="444de-135">Bu dezavantajlar nedeniyle varsayılan özellikleri tanımlamamalısınız.</span><span class="sxs-lookup"><span data-stu-id="444de-135">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="444de-136">Kod okunabilirlik için, her zaman tüm özelliklere, hatta varsayılan özelliklere de her zaman başvurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="444de-136">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="444de-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="444de-137">See also</span></span>

- [<span data-ttu-id="444de-138">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="444de-138">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="444de-139">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="444de-139">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="444de-140">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="444de-140">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="444de-141">Varsayılanını</span><span class="sxs-lookup"><span data-stu-id="444de-141">Default</span></span>](../../../language-reference/modifiers/default.md)
- [<span data-ttu-id="444de-142">Visual Basic'de Özellikler ve Değişkenler Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="444de-142">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="444de-143">Nasıl yapılır: Özellik Oluşturma</span><span class="sxs-lookup"><span data-stu-id="444de-143">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="444de-144">Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme</span><span class="sxs-lookup"><span data-stu-id="444de-144">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="444de-145">Nasıl yapılır: Bir Özellik Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="444de-145">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="444de-146">Nasıl yapılır: Bir Özelliğe Değer Ekleme</span><span class="sxs-lookup"><span data-stu-id="444de-146">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="444de-147">Nasıl yapılır: Bir Özellikten Değer Alma</span><span class="sxs-lookup"><span data-stu-id="444de-147">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
