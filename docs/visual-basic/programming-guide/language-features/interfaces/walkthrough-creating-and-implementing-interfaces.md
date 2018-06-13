---
title: Oluşturma ve uygulama arabirimler (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
ms.openlocfilehash: af9305deb60637b642d091501e743f2c7a57ccad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653617"
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a><span data-ttu-id="bb2af-102">İzlenecek yol: Arabirimleri Oluşturma ve Uygulama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb2af-102">Walkthrough: Creating and Implementing Interfaces (Visual Basic)</span></span>

<span data-ttu-id="bb2af-103">Arabirimleri özellikleri, yöntemleri ve olay özelliklerini açıklayan, ancak uygulama ayrıntılarını yapıları veya sınıfları kadar bırakın.</span><span class="sxs-lookup"><span data-stu-id="bb2af-103">Interfaces describe the characteristics of properties, methods, and events, but leave the implementation details up to structures or classes.</span></span>  
  
 <span data-ttu-id="bb2af-104">Bu kılavuz, bildirme ve bir arabirim gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="bb2af-104">This walkthrough demonstrates how to declare and implement an interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb2af-105">Bu kılavuz, bir kullanıcı arabirimi oluşturma hakkında bilgi sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="bb2af-105">This walkthrough doesn't provide information about how to create a user interface.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-an-interface"></a><span data-ttu-id="bb2af-106">Bir arabirimi tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="bb2af-106">To define an interface</span></span>
  
1.  <span data-ttu-id="bb2af-107">Yeni bir Visual Basic Windows uygulama projesi açın.</span><span class="sxs-lookup"><span data-stu-id="bb2af-107">Open a new Visual Basic Windows Application project.</span></span>  
  
2.  <span data-ttu-id="bb2af-108">Yeni bir modül projeye tıklayarak ekleyin **Modül Ekle** üzerinde **proje** menüsü.</span><span class="sxs-lookup"><span data-stu-id="bb2af-108">Add a new module to the project by clicking **Add Module** on the **Project** menu.</span></span>  
  
3.  <span data-ttu-id="bb2af-109">Yeni modül adı `Module1.vb` tıklatıp **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="bb2af-109">Name the new module `Module1.vb` and click **Add**.</span></span> <span data-ttu-id="bb2af-110">Yeni modül kodu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="bb2af-110">The code for the new module is displayed.</span></span>  
  
4.  <span data-ttu-id="bb2af-111">Adlı bir arabirim tanımlayın `TestInterface` içinde `Module1` yazarak `Interface TestInterface` arasında `Module` ve `End Module` deyimleri ve sonra ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="bb2af-111">Define an interface named `TestInterface` within `Module1` by typing `Interface TestInterface` between the `Module` and `End Module` statements, and then pressing ENTER.</span></span> <span data-ttu-id="bb2af-112">**Kod düzenleyicisinde** girintileri `Interface` anahtar sözcüğü ve ekleyen bir `End Interface` kod bloğu oluşturmak için ifade.</span><span class="sxs-lookup"><span data-stu-id="bb2af-112">The **Code Editor** indents the `Interface` keyword and adds an `End Interface` statement to form a code block.</span></span>  
  
5.  <span data-ttu-id="bb2af-113">Aşağıdaki kod arasında koyarak özelliği, yöntemi ve olay arabirimi tanımlamak `Interface` ve `End Interface` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="bb2af-113">Define a property, method, and event for the interface by placing the following code between the `Interface` and `End Interface` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#98)]
  
## <a name="implementation"></a><span data-ttu-id="bb2af-114">Uygulama</span><span class="sxs-lookup"><span data-stu-id="bb2af-114">Implementation</span></span>

 <span data-ttu-id="bb2af-115">Arabirim üyeleri bildirmek için kullanılan sözdizimi sınıf üyesi bildirmek için kullanılan sözdiziminden, farklı olduğunu fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bb2af-115">You may notice that the syntax used to declare interface members is different from the syntax used to declare class members.</span></span> <span data-ttu-id="bb2af-116">Bu farkı arabirimler uygulama kodu içeremez olgu yansıtır.</span><span class="sxs-lookup"><span data-stu-id="bb2af-116">This difference reflects the fact that interfaces cannot contain implementation code.</span></span>  
  
### <a name="to-implement-the-interface"></a><span data-ttu-id="bb2af-117">Arabirim uygulamak için</span><span class="sxs-lookup"><span data-stu-id="bb2af-117">To implement the interface</span></span>
  
1.  <span data-ttu-id="bb2af-118">Adlı bir sınıf ekleyin `ImplementationClass` şu deyimi ekleyerek `Module1`, sonra `End Interface` deyimi önce `End Module` deyimi ve sonra ENTER tuşuna basın:</span><span class="sxs-lookup"><span data-stu-id="bb2af-118">Add a class named `ImplementationClass` by adding the following statement to `Module1`, after the `End Interface` statement but before the `End Module` statement, and then pressing ENTER:</span></span>  
  
     [!code-vb[VbVbalrOOP#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#99)]
  
     <span data-ttu-id="bb2af-119">Tümleşik geliştirme ortamında çalışıyorsanız **Kod Düzenleyicisi** eşleşen bir sağlayan `End Class` deyimi ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="bb2af-119">If you are working within the integrated development environment, the **Code Editor** supplies a matching `End Class` statement when you press ENTER.</span></span>  
  
2.  <span data-ttu-id="bb2af-120">Aşağıdakileri ekleyin `Implements` ifadesine `ImplementationClass`, hangi arabirimi sınıfı adları uygular:</span><span class="sxs-lookup"><span data-stu-id="bb2af-120">Add the following `Implements` statement to `ImplementationClass`, which names the interface the class implements:</span></span>  
  
     [!code-vb[VbVbalrOOP#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#100)]
  
     <span data-ttu-id="bb2af-121">Bir sınıf veya yapı, üstündeki diğer öğelerden ayrı olarak listelenen `Implements` deyimi gösteren sınıf veya yapı bir arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="bb2af-121">When listed separately from other items at the top of a class or structure, the `Implements` statement indicates that the class or structure implements an interface.</span></span>  
  
     <span data-ttu-id="bb2af-122">Tümleşik geliştirme ortamında çalışıyorsanız **Kod düzenleyicisinde** gerektirdiği sınıf üyeleri uygulayan `TestInterface` zaman ENTER tuşuna basın ve sonraki adıma atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bb2af-122">If you are working within the integrated development environment, the **Code Editor** implements the class members required by `TestInterface` when you press ENTER, and you can skip the next step.</span></span>  
  
3.  <span data-ttu-id="bb2af-123">Tümleşik geliştirme ortamında çalışmıyorsanız arabirimi tüm üyeleri uygulamalıdır `MyInterface`.</span><span class="sxs-lookup"><span data-stu-id="bb2af-123">If you are not working within the integrated development environment, you must implement all the members of the interface `MyInterface`.</span></span> <span data-ttu-id="bb2af-124">Aşağıdaki kodu ekleyin `ImplementationClass` uygulamak için `Event1`, `Method1`, ve `Prop1`:</span><span class="sxs-lookup"><span data-stu-id="bb2af-124">Add the following code to `ImplementationClass` to implement `Event1`, `Method1`, and `Prop1`:</span></span>  
  
     [!code-vb[VbVbalrOOP#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#101)]
  
     <span data-ttu-id="bb2af-125">`Implements` Deyimi adları uygulanan arabirim üyesini ve arabirim.</span><span class="sxs-lookup"><span data-stu-id="bb2af-125">The `Implements` statement names the interface and interface member being implemented.</span></span>  
  
4.  <span data-ttu-id="bb2af-126">Tanımını tamamlamak `Prop1` özellik değeri depolanan sınıfı için özel bir alan ekleyerek:</span><span class="sxs-lookup"><span data-stu-id="bb2af-126">Complete the definition of `Prop1` by adding a private field to the class that stored the property value:</span></span>  
  
     [!code-vb[VbVbalrOOP#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#102)]
  
     <span data-ttu-id="bb2af-127">Değeri döndürmesi `pval` özelliğinden get erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="bb2af-127">Return the value of the `pval` from the property get accessor.</span></span>  
  
     [!code-vb[VbVbalrOOP#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#103)]
  
     <span data-ttu-id="bb2af-128">Değerini `pval` özelliğinde ayarlama erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="bb2af-128">Set the value of `pval` in the property set accessor.</span></span>  
  
     [!code-vb[VbVbalrOOP#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#104)]
  
5.  <span data-ttu-id="bb2af-129">Tanımını tamamlamak `Method1` aşağıdaki kodu ekleyerek düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="bb2af-129">Complete the definition of `Method1` by adding the following code.</span></span>  
  
     [!code-vb[VbVbalrOOP#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#105)]
  
### <a name="to-test-the-implementation-of-the-interface"></a><span data-ttu-id="bb2af-130">Arabirim uygulanmasını test etmek için</span><span class="sxs-lookup"><span data-stu-id="bb2af-130">To test the implementation of the interface</span></span>
  
1.  <span data-ttu-id="bb2af-131">Projenizde başlangıç formu sağ **Çözüm Gezgini**, tıklatıp **görünümü kodu**.</span><span class="sxs-lookup"><span data-stu-id="bb2af-131">Right-click the startup form for your project in the **Solution Explorer**, and click **View Code**.</span></span> <span data-ttu-id="bb2af-132">Düzenleyici başlangıç formunuz için sınıf görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bb2af-132">The editor displays the class for your startup form.</span></span> <span data-ttu-id="bb2af-133">Varsayılan olarak, başlangıç formu adlı `Form1`.</span><span class="sxs-lookup"><span data-stu-id="bb2af-133">By default, the startup form is called `Form1`.</span></span>  
  
2.  <span data-ttu-id="bb2af-134">Aşağıdakileri ekleyin `testInstance` alanı `Form1` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="bb2af-134">Add the following `testInstance` field to the `Form1` class:</span></span>  
  
     [!code-vb[VbVbalrOOP#120](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#120)]
  
     <span data-ttu-id="bb2af-135">Bildirme tarafından `testInstance` olarak `WithEvents`, `Form1` sınıfı olaylarına işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="bb2af-135">By declaring `testInstance` as `WithEvents`, the `Form1` class can handle its events.</span></span>  
  
3.  <span data-ttu-id="bb2af-136">Aşağıdaki olay işleyicisi ekleme `Form1` tarafından başlatılan olayları işlemek için sınıf `testInstance`:</span><span class="sxs-lookup"><span data-stu-id="bb2af-136">Add the following event handler to the `Form1` class to handle events raised by `testInstance`:</span></span>  
  
     [!code-vb[VbVbalrOOP#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#106)]
  
4.  <span data-ttu-id="bb2af-137">Adlı bir alt yordama ekleme `Test` için `Form1` sınıfı uygulama sınıfı test etmek için:</span><span class="sxs-lookup"><span data-stu-id="bb2af-137">Add a subroutine named `Test` to the `Form1` class to test the implementation class:</span></span>  
  
     [!code-vb[VbVbalrOOP#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#107)]
  
     <span data-ttu-id="bb2af-138">`Test` Yordam uygulayan sınıf örneği oluşturur `MyInterface`, bu örneğe atar `testInstance` alan, bir özelliği ayarlar ve bir yöntem arabirimi aracılığıyla çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="bb2af-138">The `Test` procedure creates an instance of the class that implements `MyInterface`, assigns that instance to the `testInstance` field, sets a property, and runs a method through the interface.</span></span>  
  
5.  <span data-ttu-id="bb2af-139">Çağırmak için kodu ekleyin `Test` yordamdan `Form1 Load` başlangıç formu yordam:</span><span class="sxs-lookup"><span data-stu-id="bb2af-139">Add code to call the `Test` procedure from the `Form1 Load` procedure of your startup form:</span></span>  
  
     [!code-vb[VbVbalrOOP#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#108)]
  
6.  <span data-ttu-id="bb2af-140">Çalıştırma `Test` F5'e basarak yordamı.</span><span class="sxs-lookup"><span data-stu-id="bb2af-140">Run the `Test` procedure by pressing F5.</span></span> <span data-ttu-id="bb2af-141">İleti "Prop1 9 ayarlandı" görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="bb2af-141">The message "Prop1 was set to 9" is displayed.</span></span> <span data-ttu-id="bb2af-142">"X parametresi Method1 için 5." iletisi Tamam ' ı sonra görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="bb2af-142">After you click OK, the message "The X parameter for Method1 is 5" is displayed.</span></span> <span data-ttu-id="bb2af-143">Tamam'ı tıklatın ve "olay olay işleyicisi yakalanan" iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="bb2af-143">Click OK, and the message "The event handler caught the event" is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb2af-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb2af-144">See also</span></span>

 [<span data-ttu-id="bb2af-145">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="bb2af-145">Implements Statement</span></span>](../../../../visual-basic/language-reference/statements/implements-statement.md)  
 [<span data-ttu-id="bb2af-146">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="bb2af-146">Interfaces</span></span>](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)  
 [<span data-ttu-id="bb2af-147">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="bb2af-147">Interface Statement</span></span>](../../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="bb2af-148">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="bb2af-148">Event Statement</span></span>](../../../../visual-basic/language-reference/statements/event-statement.md)  