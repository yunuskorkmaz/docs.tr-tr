---
description: 'Daha fazla bilgi edinin: Izlenecek yol: arabirimleri oluşturma ve uygulama (Visual Basic)'
title: Arabirimleri Oluşturma ve Uygulama
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
ms.openlocfilehash: 058011d311fdecba626a59228816f9bced319c97
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468427"
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a><span data-ttu-id="bedb5-103">İzlenecek yol: Arabirimleri Oluşturma ve Uygulama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bedb5-103">Walkthrough: Creating and Implementing Interfaces (Visual Basic)</span></span>

<span data-ttu-id="bedb5-104">Arabirimler özellikler, Yöntemler ve olayların özelliklerini ve uygulama ayrıntılarını yapılar veya sınıflar için bir şekilde bırakır.</span><span class="sxs-lookup"><span data-stu-id="bedb5-104">Interfaces describe the characteristics of properties, methods, and events, but leave the implementation details up to structures or classes.</span></span>  
  
 <span data-ttu-id="bedb5-105">Bu izlenecek yol, bir arabirimin nasıl bildirileceğini ve uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bedb5-105">This walkthrough demonstrates how to declare and implement an interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bedb5-106">Bu izlenecek yol, Kullanıcı arabirimi oluşturma hakkında bilgi sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="bedb5-106">This walkthrough doesn't provide information about how to create a user interface.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-an-interface"></a><span data-ttu-id="bedb5-107">Bir arabirim tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="bedb5-107">To define an interface</span></span>
  
1. <span data-ttu-id="bedb5-108">Yeni bir Visual Basic Windows uygulaması projesi açın.</span><span class="sxs-lookup"><span data-stu-id="bedb5-108">Open a new Visual Basic Windows Application project.</span></span>  
  
2. <span data-ttu-id="bedb5-109">**Proje** menüsünde **Modül Ekle** ' ye tıklayarak projeye yeni bir modül ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bedb5-109">Add a new module to the project by clicking **Add Module** on the **Project** menu.</span></span>  
  
3. <span data-ttu-id="bedb5-110">Yeni modülü adlandırın `Module1.vb` ve **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="bedb5-110">Name the new module `Module1.vb` and click **Add**.</span></span> <span data-ttu-id="bedb5-111">Yeni modülün kodu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="bedb5-111">The code for the new module is displayed.</span></span>  
  
4. <span data-ttu-id="bedb5-112">`TestInterface`Ve deyimleri arasına yazarak içinde adlı bir arabirim tanımlayın `Module1` `Interface TestInterface` `Module` `End Module` ve ardından ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="bedb5-112">Define an interface named `TestInterface` within `Module1` by typing `Interface TestInterface` between the `Module` and `End Module` statements, and then pressing ENTER.</span></span> <span data-ttu-id="bedb5-113">**Kod Düzenleyicisi** , `Interface` anahtar sözcüğünü girintiler ve `End Interface` bir kod bloğu oluşturmak için bir ifade ekler.</span><span class="sxs-lookup"><span data-stu-id="bedb5-113">The **Code Editor** indents the `Interface` keyword and adds an `End Interface` statement to form a code block.</span></span>  
  
5. <span data-ttu-id="bedb5-114">Aşağıdaki kodu ve deyimleri arasına yerleştirerek arabirim için bir özellik, yöntem ve olay tanımlayın `Interface` `End Interface` :</span><span class="sxs-lookup"><span data-stu-id="bedb5-114">Define a property, method, and event for the interface by placing the following code between the `Interface` and `End Interface` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#98)]
  
## <a name="implementation"></a><span data-ttu-id="bedb5-115">Uygulama</span><span class="sxs-lookup"><span data-stu-id="bedb5-115">Implementation</span></span>

 <span data-ttu-id="bedb5-116">Arabirim üyelerini bildirmek için kullanılan sözdiziminin, sınıf üyelerini bildirmek için kullanılan sözdiziminden farklı olduğunu fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bedb5-116">You may notice that the syntax used to declare interface members is different from the syntax used to declare class members.</span></span> <span data-ttu-id="bedb5-117">Bu fark, arabirimlerin uygulama kodu içeremeyeceği gerçeğini yansıtır.</span><span class="sxs-lookup"><span data-stu-id="bedb5-117">This difference reflects the fact that interfaces cannot contain implementation code.</span></span>  
  
### <a name="to-implement-the-interface"></a><span data-ttu-id="bedb5-118">Arabirimi uygulamak için</span><span class="sxs-lookup"><span data-stu-id="bedb5-118">To implement the interface</span></span>
  
1. <span data-ttu-id="bedb5-119">`ImplementationClass`Aşağıdaki deyimden `Module1` sonra, ifadesinden sonra, öğesinden önce, sonra `End Interface` `End Module` ENTER tuşuna basarak adlı bir sınıf ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bedb5-119">Add a class named `ImplementationClass` by adding the following statement to `Module1`, after the `End Interface` statement but before the `End Module` statement, and then pressing ENTER:</span></span>  
  
     [!code-vb[VbVbalrOOP#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#99)]
  
     <span data-ttu-id="bedb5-120">Tümleşik geliştirme ortamı içinde çalışıyorsanız, ENTER tuşuna bastığınızda, **Kod Düzenleyicisi** eşleşen bir ifade sağlar `End Class` .</span><span class="sxs-lookup"><span data-stu-id="bedb5-120">If you are working within the integrated development environment, the **Code Editor** supplies a matching `End Class` statement when you press ENTER.</span></span>  
  
2. <span data-ttu-id="bedb5-121">Aşağıdaki `Implements` ifadesini `ImplementationClass` , sınıfının uyguladığı arabirimi isimsiz olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bedb5-121">Add the following `Implements` statement to `ImplementationClass`, which names the interface the class implements:</span></span>  
  
     [!code-vb[VbVbalrOOP#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#100)]
  
     <span data-ttu-id="bedb5-122">Bir sınıfın veya yapının üstündeki diğer öğelerden ayrı olarak listelendiğinde, `Implements` ifade sınıfın veya yapının bir arabirim uyguladığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bedb5-122">When listed separately from other items at the top of a class or structure, the `Implements` statement indicates that the class or structure implements an interface.</span></span>  
  
     <span data-ttu-id="bedb5-123">Tümleşik geliştirme ortamı içinde çalışıyorsanız, **Kod Düzenleyicisi** , ENTER tuşuna bastığınızda gereken sınıf üyelerini uygular `TestInterface` ve bir sonraki adımı atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bedb5-123">If you are working within the integrated development environment, the **Code Editor** implements the class members required by `TestInterface` when you press ENTER, and you can skip the next step.</span></span>  
  
3. <span data-ttu-id="bedb5-124">Tümleşik geliştirme ortamı içinde çalışmadıysanız, arabirimin tüm üyelerini uygulamanız gerekir `MyInterface` .</span><span class="sxs-lookup"><span data-stu-id="bedb5-124">If you are not working within the integrated development environment, you must implement all the members of the interface `MyInterface`.</span></span> <span data-ttu-id="bedb5-125">`ImplementationClass`,, Ve uygulamak için aşağıdaki kodu `Event1` ekleyin `Method1` `Prop1` :</span><span class="sxs-lookup"><span data-stu-id="bedb5-125">Add the following code to `ImplementationClass` to implement `Event1`, `Method1`, and `Prop1`:</span></span>  
  
     [!code-vb[VbVbalrOOP#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#101)]
  
     <span data-ttu-id="bedb5-126">`Implements`İfade, uygulanan arabirimi ve arabirim üyesini adlandırır.</span><span class="sxs-lookup"><span data-stu-id="bedb5-126">The `Implements` statement names the interface and interface member being implemented.</span></span>  
  
4. <span data-ttu-id="bedb5-127">`Prop1`Özellik değerini saklı sınıfa bir özel alan ekleyerek tanımını doldurun:</span><span class="sxs-lookup"><span data-stu-id="bedb5-127">Complete the definition of `Prop1` by adding a private field to the class that stored the property value:</span></span>  
  
     [!code-vb[VbVbalrOOP#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#102)]
  
     <span data-ttu-id="bedb5-128">`pval`Özellik Al erişimcisinin öğesinden değerini döndürün.</span><span class="sxs-lookup"><span data-stu-id="bedb5-128">Return the value of the `pval` from the property get accessor.</span></span>  
  
     [!code-vb[VbVbalrOOP#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#103)]
  
     <span data-ttu-id="bedb5-129">Değerini `pval` özellik kümesi erişimcisinde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bedb5-129">Set the value of `pval` in the property set accessor.</span></span>  
  
     [!code-vb[VbVbalrOOP#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#104)]
  
5. <span data-ttu-id="bedb5-130">`Method1`Aşağıdaki kodu ekleyerek tanımını doldurun.</span><span class="sxs-lookup"><span data-stu-id="bedb5-130">Complete the definition of `Method1` by adding the following code.</span></span>  
  
     [!code-vb[VbVbalrOOP#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#105)]
  
### <a name="to-test-the-implementation-of-the-interface"></a><span data-ttu-id="bedb5-131">Arabirimin uygulamasını test etmek için</span><span class="sxs-lookup"><span data-stu-id="bedb5-131">To test the implementation of the interface</span></span>
  
1. <span data-ttu-id="bedb5-132">**Çözüm Gezgini** projenizin başlangıç formuna sağ tıklayın ve **kodu görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="bedb5-132">Right-click the startup form for your project in the **Solution Explorer**, and click **View Code**.</span></span> <span data-ttu-id="bedb5-133">Düzenleyici, başlangıç formunuz için sınıfını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bedb5-133">The editor displays the class for your startup form.</span></span> <span data-ttu-id="bedb5-134">Varsayılan olarak, başlangıç formu çağırılır `Form1` .</span><span class="sxs-lookup"><span data-stu-id="bedb5-134">By default, the startup form is called `Form1`.</span></span>  
  
2. <span data-ttu-id="bedb5-135">`testInstance`Sınıfına aşağıdaki alanı ekleyin `Form1` :</span><span class="sxs-lookup"><span data-stu-id="bedb5-135">Add the following `testInstance` field to the `Form1` class:</span></span>  
  
     [!code-vb[VbVbalrOOP#120](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#120)]
  
     <span data-ttu-id="bedb5-136">Olarak bildirerek `testInstance` `WithEvents` , `Form1` sınıfı olaylarını işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="bedb5-136">By declaring `testInstance` as `WithEvents`, the `Form1` class can handle its events.</span></span>  
  
3. <span data-ttu-id="bedb5-137">`Form1`Tarafından oluşturulan olayları işlemek için aşağıdaki olay işleyicisini sınıfına ekleyin `testInstance` :</span><span class="sxs-lookup"><span data-stu-id="bedb5-137">Add the following event handler to the `Form1` class to handle events raised by `testInstance`:</span></span>  
  
     [!code-vb[VbVbalrOOP#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#106)]
  
4. <span data-ttu-id="bedb5-138">`Test` `Form1` Uygulama sınıfını test etmek için sınıfına adlı bir altyordam ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bedb5-138">Add a subroutine named `Test` to the `Form1` class to test the implementation class:</span></span>  
  
     [!code-vb[VbVbalrOOP#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#107)]
  
     <span data-ttu-id="bedb5-139">`Test`Yordam, uygulayan sınıfının bir örneğini oluşturur `MyInterface` , bu örneği alana atar, `testInstance` bir özelliği ayarlar ve arabirim aracılığıyla bir yöntemi çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="bedb5-139">The `Test` procedure creates an instance of the class that implements `MyInterface`, assigns that instance to the `testInstance` field, sets a property, and runs a method through the interface.</span></span>  
  
5. <span data-ttu-id="bedb5-140">`Test`Başlangıç formunuzun yordamından yordamı çağırmak için kod ekleyin `Form1 Load` :</span><span class="sxs-lookup"><span data-stu-id="bedb5-140">Add code to call the `Test` procedure from the `Form1 Load` procedure of your startup form:</span></span>  
  
     [!code-vb[VbVbalrOOP#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#108)]
  
6. <span data-ttu-id="bedb5-141">`Test`F5 tuşuna basarak yordamı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bedb5-141">Run the `Test` procedure by pressing F5.</span></span> <span data-ttu-id="bedb5-142">"Prop1 9 ' a ayarlanmıştır" iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="bedb5-142">The message "Prop1 was set to 9" is displayed.</span></span> <span data-ttu-id="bedb5-143">Tamam ' a tıkladıktan sonra, "Method1 X parametresi 5 olur" iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="bedb5-143">After you click OK, the message "The X parameter for Method1 is 5" is displayed.</span></span> <span data-ttu-id="bedb5-144">Tamam ' a tıklayın ve "olay işleyicisi olayı yakalandı" iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="bedb5-144">Click OK, and the message "The event handler caught the event" is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bedb5-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bedb5-145">See also</span></span>

- [<span data-ttu-id="bedb5-146">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="bedb5-146">Implements Statement</span></span>](../../../language-reference/statements/implements-statement.md)
- [<span data-ttu-id="bedb5-147">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="bedb5-147">Interfaces</span></span>](index.md)
- [<span data-ttu-id="bedb5-148">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="bedb5-148">Interface Statement</span></span>](../../../language-reference/statements/interface-statement.md)
- [<span data-ttu-id="bedb5-149">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="bedb5-149">Event Statement</span></span>](../../../language-reference/statements/event-statement.md)
