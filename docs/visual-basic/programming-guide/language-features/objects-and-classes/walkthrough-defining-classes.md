---
title: Sınıfları tanımlama (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- execution [Visual Basic], ending
- objects [Visual Basic], initializing
- Initialize event [Visual Basic]
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- objects [Visual Basic], creating
- program termination
- classes [Visual Basic], walkthroughs
- class modules, walkthroughs
- Terminate event [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 07018828-2d49-4cf5-a44b-19fb15d9efea
ms.openlocfilehash: 679f4fd55f142c2c4bb63a556feb95c074960b12
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914728"
---
# <a name="walkthrough-defining-classes-visual-basic"></a><span data-ttu-id="216c2-102">İzlenecek yol: Sınıfları tanımlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="216c2-102">Walkthrough: Defining Classes (Visual Basic)</span></span>

<span data-ttu-id="216c2-103">Bu izlenecek yolda, daha sonra nesneleri oluşturmak için kullanabileceğiniz sınıfların nasıl tanımlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="216c2-103">This walkthrough demonstrates how to define classes, which you can then use to create objects.</span></span> <span data-ttu-id="216c2-104">Ayrıca, yeni sınıfa nasıl özellik ve Yöntem ekleneceğini ve bir nesnenin nasıl başlatılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="216c2-104">It also shows you how to add properties and methods to the new class, and demonstrates how to initialize an object.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a><span data-ttu-id="216c2-105">Bir sınıf tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="216c2-105">To define a class</span></span>
  
1. <span data-ttu-id="216c2-106">**Dosya** menüsünde **Yeni proje ' ye** tıklayarak bir proje oluşturun.</span><span class="sxs-lookup"><span data-stu-id="216c2-106">Create a project by clicking **New Project** on the **File** menu.</span></span> <span data-ttu-id="216c2-107">**Yeni Proje** iletişim kutusu görünür.</span><span class="sxs-lookup"><span data-stu-id="216c2-107">The **New Project** dialog box appears.</span></span>  
  
2. <span data-ttu-id="216c2-108">Yeni projeyi göstermek için Visual Basic proje şablonları listesinden Windows uygulaması ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="216c2-108">Select Windows Application from the list of Visual Basic project templates to display the new project.</span></span>  
  
3. <span data-ttu-id="216c2-109">**Proje** menüsünde **Sınıf Ekle** ' ye tıklayarak projeye yeni bir sınıf ekleyin.</span><span class="sxs-lookup"><span data-stu-id="216c2-109">Add a new class to the project by clicking **Add Class** on the **Project** menu.</span></span> <span data-ttu-id="216c2-110">**Yeni Öğe Ekle** iletişim kutusu görünür.</span><span class="sxs-lookup"><span data-stu-id="216c2-110">The **Add New Item** dialog box appears.</span></span>  
  
4. <span data-ttu-id="216c2-111">**Sınıf** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="216c2-111">Select the **Class** template.</span></span>  
  
5. <span data-ttu-id="216c2-112">Yeni `UserNameInfo.vb`sınıfı adlandırın ve ardından **Ekle** ' ye tıklayarak yeni sınıf için kodu görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="216c2-112">Name the new class `UserNameInfo.vb`, and then click **Add** to display the code for the new class.</span></span>  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    > <span data-ttu-id="216c2-113">`Class` Anahtar sözcüğünü ve ardından yeni sınıfın adını yazarak başlangıç formunuza bir sınıf eklemek için Visual Basic **kod düzenleyicisini** kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="216c2-113">You can use the Visual Basic **Code Editor** to add a class to your startup form by typing the `Class` keyword followed by the name of the new class.</span></span> <span data-ttu-id="216c2-114">**Kod Düzenleyicisi** sizin için karşılık gelen `End Class` bir bildirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="216c2-114">The **Code Editor** provides a corresponding `End Class` statement for you.</span></span>  
  
6. <span data-ttu-id="216c2-115">`Class` Ve`End Class` deyimleri arasına aşağıdaki kodu ekleyerek sınıf için özel bir alan tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="216c2-115">Define a private field for the class by adding the following code between the `Class` and `End Class` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     <span data-ttu-id="216c2-116">Alanı olarak `Private` bildirmek, yalnızca sınıfında kullanılabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="216c2-116">Declaring the field as `Private` means it can be used only within the class.</span></span> <span data-ttu-id="216c2-117">Daha fazla erişim sağlayan gibi `Public` erişim değiştiricilerini kullanarak alanları bir sınıfın dışından kullanılabilir hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="216c2-117">You can make fields available from outside a class by using access modifiers such as `Public` that provide more access.</span></span> <span data-ttu-id="216c2-118">Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="216c2-118">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
7. <span data-ttu-id="216c2-119">Aşağıdaki kodu ekleyerek sınıf için bir özellik tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="216c2-119">Define a property for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8. <span data-ttu-id="216c2-120">Aşağıdaki kodu ekleyerek sınıf için bir yöntem tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="216c2-120">Define a method for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. <span data-ttu-id="216c2-121">Adlı `Sub New`bir yordam ekleyerek yeni sınıf için parametreli bir Oluşturucu tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="216c2-121">Define a parameterized constructor for the new class by adding a procedure named `Sub New`:</span></span>  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     <span data-ttu-id="216c2-122">Bu sınıfa dayalı bir nesne oluşturulduğunda Oluşturucuotomatikolarakçağrılır.`Sub New`</span><span class="sxs-lookup"><span data-stu-id="216c2-122">The `Sub New` constructor is called automatically when an object based on this class is created.</span></span> <span data-ttu-id="216c2-123">Bu Oluşturucu, Kullanıcı adını tutan alanın değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="216c2-123">This constructor sets the value of the field that holds the user name.</span></span>  
  
## <a name="to-create-a-button-to-test-the-class"></a><span data-ttu-id="216c2-124">Sınıfı test etmek üzere bir düğme oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="216c2-124">To create a button to test the class</span></span>
  
1. <span data-ttu-id="216c2-125">Başlangıç formunu, **Çözüm Gezgini** adına sağ tıklayıp **Görünüm Tasarımcısı**' na tıklayarak tasarım moduna değiştirin.</span><span class="sxs-lookup"><span data-stu-id="216c2-125">Change the startup form to design mode by right-clicking its name in **Solution Explorer** and then clicking **View Designer**.</span></span> <span data-ttu-id="216c2-126">Varsayılan olarak, Windows uygulama projeleri için başlangıç formu Form1. vb olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="216c2-126">By default, the startup form for Windows Application projects is named Form1.vb.</span></span> <span data-ttu-id="216c2-127">Ana form daha sonra görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="216c2-127">The main form will then appear.</span></span>  
  
2. <span data-ttu-id="216c2-128">Ana forma bir düğme ekleyin ve `Button1_Click` olay işleyicisi için kodu göstermek üzere çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="216c2-128">Add a button to the main form and double-click it to display the code for the `Button1_Click` event handler.</span></span> <span data-ttu-id="216c2-129">Test yordamını çağırmak için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="216c2-129">Add the following code to call the test procedure:</span></span>  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a><span data-ttu-id="216c2-130">Uygulamanızı çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="216c2-130">To run your application</span></span>
  
1. <span data-ttu-id="216c2-131">F5 tuşuna basarak uygulamanızı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="216c2-131">Run your application by pressing F5.</span></span> <span data-ttu-id="216c2-132">Test yordamını çağırmak için formdaki düğmeye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="216c2-132">Click the button on the form to call the test procedure.</span></span> <span data-ttu-id="216c2-133">Bu, yordamın nesne `UserName` `Capitalize` yöntemi olarak adlandırıldığından, orijinalin "Moore, bodire" olduğunu belirten bir ileti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="216c2-133">It displays a message stating that the original `UserName` is "MOORE, BOBBY", because the procedure called the `Capitalize` method of the object.</span></span>  
  
2. <span data-ttu-id="216c2-134">İleti kutusunu kapatmak için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="216c2-134">Click **OK** to dismiss the message box.</span></span> <span data-ttu-id="216c2-135">Yordam, `UserName` özelliğinin değerini değiştirir ve yeni değerinin `UserName` "Worden, ali" olduğunu belirten bir ileti görüntüler. `Button1 Click`</span><span class="sxs-lookup"><span data-stu-id="216c2-135">The `Button1 Click` procedure changes the value of the `UserName` property and displays a message stating that the new value of `UserName` is "Worden, Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="216c2-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="216c2-136">See also</span></span>

- [<span data-ttu-id="216c2-137">Nesne odaklı programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="216c2-137">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
- [<span data-ttu-id="216c2-138">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="216c2-138">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
