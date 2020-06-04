---
title: Arabirimleri Oluşturma ve Uygulama
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
ms.openlocfilehash: 89e8f91a04b25b84bc783d5c4f4b91cf12426f72
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405073"
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a><span data-ttu-id="6e6e0-102">İzlenecek yol: Arabirimleri Oluşturma ve Uygulama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e6e0-102">Walkthrough: Creating and Implementing Interfaces (Visual Basic)</span></span>

<span data-ttu-id="6e6e0-103">Arabirimler özellikler, Yöntemler ve olayların özelliklerini ve uygulama ayrıntılarını yapılar veya sınıflar için bir şekilde bırakır.</span><span class="sxs-lookup"><span data-stu-id="6e6e0-103">Interfaces describe the characteristics of properties, methods, and events, but leave the implementation details up to structures or classes.</span></span>  
  
 <span data-ttu-id="6e6e0-104">Bu izlenecek yol, bir arabirimin nasıl bildirileceğini ve uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e6e0-104">This walkthrough demonstrates how to declare and implement an interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e6e0-105">Bu izlenecek yol, Kullanıcı arabirimi oluşturma hakkında bilgi sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="6e6e0-105">This walkthrough doesn't provide information about how to create a user interface.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-an-interface"></a><span data-ttu-id="6e6e0-106">Bir arabirim tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="6e6e0-106">To define an interface</span></span>
  
1. <span data-ttu-id="6e6e0-107">Yeni bir Visual Basic Windows uygulaması projesi açın.</span><span class="sxs-lookup"><span data-stu-id="6e6e0-107">Open a new Visual Basic Windows Application project.</span></span>  
  
2. <span data-ttu-id="6e6e0-108">**Proje** menüsünde **Modül Ekle** ' ye tıklayarak projeye yeni bir modül ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6e6e0-108">Add a new module to the project by clicking **Add Module** on the **Project** menu.</span></span>  
  
3. <span data-ttu-id="6e6e0-109">Yeni modülü adlandırın `Module1.vb` ve **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6e6e0-109">Name the new module `Module1.vb` and click **Add**.</span></span> <span data-ttu-id="6e6e0-110">Yeni modülün kodu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6e6e0-110">The code for the new module is displayed.</span></span>  
  
4. <span data-ttu-id="6e6e0-111">`TestInterface`Ve deyimleri arasına yazarak içinde adlı bir arabirim tanımlayın `Module1` `Interface TestInterface` `Module` `End Module` ve ardından ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="6e6e0-111">Define an interface named `TestInterface` within `Module1` by typing `Interface TestInterface` between the `Module` and `End Module` statements, and then pressing ENTER.</span></span> <span data-ttu-id="6e6e0-112">**Kod Düzenleyicisi** , `Interface` anahtar sözcüğünü girintiler ve `End Interface` bir kod bloğu oluşturmak için bir ifade ekler.</span><span class="sxs-lookup"><span data-stu-id="6e6e0-112">The **Code Editor** indents the `Interface` keyword and adds an `End Interface` statement to form a code block.</span></span>  
  
5. <span data-ttu-id="6e6e0-113">Aşağıdaki kodu ve deyimleri arasına yerleştirerek arabirim için bir özellik, yöntem ve olay tanımlayın `Interface` `End Interface` :</span><span class="sxs-lookup"><span data-stu-id="6e6e0-113">Define a property, method, and event for the interface by placing the following code between the `Interface` and `End Interface` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#98)]
  
## <a name="implementation"></a><span data-ttu-id="6e6e0-114">Uygulama</span><span class="sxs-lookup"><span data-stu-id="6e6e0-114">Implementation</span></span>

 <span data-ttu-id="6e6e0-115">Arabirim üyelerini bildirmek için kullanılan sözdiziminin, sınıf üyelerini bildirmek için kullanılan sözdiziminden farklı olduğunu fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e6e0-115">You may notice that the syntax used to declare interface members is different from the syntax used to declare class members.</span></span> <span data-ttu-id="6e6e0-116">Bu fark, arabirimlerin uygulama kodu içeremeyeceği gerçeğini yansıtır.</span><span class="sxs-lookup"><span data-stu-id="6e6e0-116">This difference reflects the fact that interfaces cannot contain implementation code.</span></span>  
  
### <a name="to-implement-the-interface"></a><span data-ttu-id="6e6e0-117">Arabirimi uygulamak için</span><span class="sxs-lookup"><span data-stu-id="6e6e0-117">To implement the interface</span></span>
  
1. <span data-ttu-id="6e6e0-118">`ImplementationClass`Aşağıdaki deyimden `Module1` sonra, ifadesinden sonra, öğesinden önce, sonra `End Interface` `End Module` ENTER tuşuna basarak adlı bir sınıf ekleyin:</span><span class="sxs-lookup"><span data-stu-id="6e6e0-118">Add a class named `ImplementationClass` by adding the following statement to `Module1`, after the `End Interface` statement but before the `End Module` statement, and then pressing ENTER:</span></span>  
  
     [!code-vb[VbVbalrOOP#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#99)]
  
     <span data-ttu-id="6e6e0-119">Tümleşik geliştirme ortamı içinde çalışıyorsanız, ENTER tuşuna bastığınızda, **Kod Düzenleyicisi** eşleşen bir ifade sağlar `End Class` .</span><span class="sxs-lookup"><span data-stu-id="6e6e0-119">If you are working within the integrated development environment, the **Code Editor** supplies a matching `End Class` statement when you press ENTER.</span></span>  
  
2. <span data-ttu-id="6e6e0-120">Aşağıdaki `Implements` ifadesini `ImplementationClass` , sınıfının uyguladığı arabirimi isimsiz olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="6e6e0-120">Add the following `Implements` statement to `ImplementationClass`, which names the interface the class implements:</span></span>  
  
     [!code-vb[VbVbalrOOP#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#100)]
  
     <span data-ttu-id="6e6e0-121">Bir sınıfın veya yapının üstündeki diğer öğelerden ayrı olarak listelendiğinde, `Implements` ifade sınıfın veya yapının bir arabirim uyguladığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e6e0-121">When listed separately from other items at the top of a class or structure, the `Implements` statement indicates that the class or structure implements an interface.</span></span>  
  
     <span data-ttu-id="6e6e0-122">Tümleşik geliştirme ortamı içinde çalışıyorsanız, **Kod Düzenleyicisi** , ENTER tuşuna bastığınızda gereken sınıf üyelerini uygular `TestInterface` ve bir sonraki adımı atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e6e0-122">If you are working within the integrated development environment, the **Code Editor** implements the class members required by `TestInterface` when you press ENTER, and you can skip the next step.</span></span>  
  
3. <span data-ttu-id="6e6e0-123">Tümleşik geliştirme ortamı içinde çalışmadıysanız, arabirimin tüm üyelerini uygulamanız gerekir `MyInterface` .</span><span class="sxs-lookup"><span data-stu-id="6e6e0-123">If you are not working within the integrated development environment, you must implement all the members of the interface `MyInterface`.</span></span> <span data-ttu-id="6e6e0-124">`ImplementationClass`,, Ve uygulamak için aşağıdaki kodu `Event1` ekleyin `Method1` `Prop1` :</span><span class="sxs-lookup"><span data-stu-id="6e6e0-124">Add the following code to `ImplementationClass` to implement `Event1`, `Method1`, and `Prop1`:</span></span>  
  
     [!code-vb[VbVbalrOOP#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#101)]
  
     <span data-ttu-id="6e6e0-125">`Implements`İfade, uygulanan arabirimi ve arabirim üyesini adlandırır.</span><span class="sxs-lookup"><span data-stu-id="6e6e0-125">The `Implements` statement names the interface and interface member being implemented.</span></span>  
  
4. <span data-ttu-id="6e6e0-126">`Prop1`Özellik değerini saklı sınıfa bir özel alan ekleyerek tanımını doldurun:</span><span class="sxs-lookup"><span data-stu-id="6e6e0-126">Complete the definition of `Prop1` by adding a private field to the class that stored the property value:</span></span>  
  
     [!code-vb[VbVbalrOOP#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#102)]
  
     <span data-ttu-id="6e6e0-127">`pval`Özellik Al erişimcisinin öğesinden değerini döndürün.</span><span class="sxs-lookup"><span data-stu-id="6e6e0-127">Return the value of the `pval` from the property get accessor.</span></span>  
  
     [!code-vb[VbVbalrOOP#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#103)]
  
     <span data-ttu-id="6e6e0-128">Değerini `pval` özellik kümesi erişimcisinde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6e6e0-128">Set the value of `pval` in the property set accessor.</span></span>  
  
     [!code-vb[VbVbalrOOP#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#104)]
  
5. <span data-ttu-id="6e6e0-129">`Method1`Aşağıdaki kodu ekleyerek tanımını doldurun.</span><span class="sxs-lookup"><span data-stu-id="6e6e0-129">Complete the definition of `Method1` by adding the following code.</span></span>  
  
     [!code-vb[VbVbalrOOP#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#105)]
  
### <a name="to-test-the-implementation-of-the-interface"></a><span data-ttu-id="6e6e0-130">Arabirimin uygulamasını test etmek için</span><span class="sxs-lookup"><span data-stu-id="6e6e0-130">To test the implementation of the interface</span></span>
  
1. <span data-ttu-id="6e6e0-131">**Çözüm Gezgini**projenizin başlangıç formuna sağ tıklayın ve **kodu görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6e6e0-131">Right-click the startup form for your project in the **Solution Explorer**, and click **View Code**.</span></span> <span data-ttu-id="6e6e0-132">Düzenleyici, başlangıç formunuz için sınıfını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6e6e0-132">The editor displays the class for your startup form.</span></span> <span data-ttu-id="6e6e0-133">Varsayılan olarak, başlangıç formu çağırılır `Form1` .</span><span class="sxs-lookup"><span data-stu-id="6e6e0-133">By default, the startup form is called `Form1`.</span></span>  
  
2. <span data-ttu-id="6e6e0-134">`testInstance`Sınıfına aşağıdaki alanı ekleyin `Form1` :</span><span class="sxs-lookup"><span data-stu-id="6e6e0-134">Add the following `testInstance` field to the `Form1` class:</span></span>  
  
     [!code-vb[VbVbalrOOP#120](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#120)]
  
     <span data-ttu-id="6e6e0-135">Olarak bildirerek `testInstance` `WithEvents` , `Form1` sınıfı olaylarını işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="6e6e0-135">By declaring `testInstance` as `WithEvents`, the `Form1` class can handle its events.</span></span>  
  
3. <span data-ttu-id="6e6e0-136">`Form1`Tarafından oluşturulan olayları işlemek için aşağıdaki olay işleyicisini sınıfına ekleyin `testInstance` :</span><span class="sxs-lookup"><span data-stu-id="6e6e0-136">Add the following event handler to the `Form1` class to handle events raised by `testInstance`:</span></span>  
  
     [!code-vb[VbVbalrOOP#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#106)]
  
4. <span data-ttu-id="6e6e0-137">`Test` `Form1` Uygulama sınıfını test etmek için sınıfına adlı bir altyordam ekleyin:</span><span class="sxs-lookup"><span data-stu-id="6e6e0-137">Add a subroutine named `Test` to the `Form1` class to test the implementation class:</span></span>  
  
     [!code-vb[VbVbalrOOP#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#107)]
  
     <span data-ttu-id="6e6e0-138">`Test`Yordam, uygulayan sınıfının bir örneğini oluşturur `MyInterface` , bu örneği alana atar, `testInstance` bir özelliği ayarlar ve arabirim aracılığıyla bir yöntemi çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="6e6e0-138">The `Test` procedure creates an instance of the class that implements `MyInterface`, assigns that instance to the `testInstance` field, sets a property, and runs a method through the interface.</span></span>  
  
5. <span data-ttu-id="6e6e0-139">`Test`Başlangıç formunuzun yordamından yordamı çağırmak için kod ekleyin `Form1 Load` :</span><span class="sxs-lookup"><span data-stu-id="6e6e0-139">Add code to call the `Test` procedure from the `Form1 Load` procedure of your startup form:</span></span>  
  
     [!code-vb[VbVbalrOOP#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#108)]
  
6. <span data-ttu-id="6e6e0-140">`Test`F5 tuşuna basarak yordamı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6e6e0-140">Run the `Test` procedure by pressing F5.</span></span> <span data-ttu-id="6e6e0-141">"Prop1 9 ' a ayarlanmıştır" iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6e6e0-141">The message "Prop1 was set to 9" is displayed.</span></span> <span data-ttu-id="6e6e0-142">Tamam ' a tıkladıktan sonra, "Method1 X parametresi 5 olur" iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6e6e0-142">After you click OK, the message "The X parameter for Method1 is 5" is displayed.</span></span> <span data-ttu-id="6e6e0-143">Tamam ' a tıklayın ve "olay işleyicisi olayı yakalandı" iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6e6e0-143">Click OK, and the message "The event handler caught the event" is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e6e0-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e6e0-144">See also</span></span>

- [<span data-ttu-id="6e6e0-145">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="6e6e0-145">Implements Statement</span></span>](../../../language-reference/statements/implements-statement.md)
- [<span data-ttu-id="6e6e0-146">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="6e6e0-146">Interfaces</span></span>](index.md)
- [<span data-ttu-id="6e6e0-147">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="6e6e0-147">Interface Statement</span></span>](../../../language-reference/statements/interface-statement.md)
- [<span data-ttu-id="6e6e0-148">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="6e6e0-148">Event Statement</span></span>](../../../language-reference/statements/event-statement.md)
