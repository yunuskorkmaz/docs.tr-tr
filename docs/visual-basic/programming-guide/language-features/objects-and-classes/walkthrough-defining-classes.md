---
title: Sınıflar (Visual Basic) tanımlama
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
ms.openlocfilehash: 3129824f6e4047420c422503cc366a1c8d28b7e7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59326222"
---
# <a name="walkthrough-defining-classes-visual-basic"></a><span data-ttu-id="7b84f-102">İzlenecek yol: Sınıflar (Visual Basic) tanımlama</span><span class="sxs-lookup"><span data-stu-id="7b84f-102">Walkthrough: Defining Classes (Visual Basic)</span></span>

<span data-ttu-id="7b84f-103">Bu yönerge, ardından nesneleri oluşturmak için kullanabileceğiniz sınıflarını tanımlamak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="7b84f-103">This walkthrough demonstrates how to define classes, which you can then use to create objects.</span></span> <span data-ttu-id="7b84f-104">Ayrıca yeni sınıfa özellikler ve yöntemler eklemek nasıl gösterir ve bir nesneyi başlatmaya gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7b84f-104">It also shows you how to add properties and methods to the new class, and demonstrates how to initialize an object.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a><span data-ttu-id="7b84f-105">Bir sınıf tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="7b84f-105">To define a class</span></span>
  
1. <span data-ttu-id="7b84f-106">Tıklayarak bir proje oluşturun **yeni proje** üzerinde **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="7b84f-106">Create a project by clicking **New Project** on the **File** menu.</span></span> <span data-ttu-id="7b84f-107">**Yeni Proje** iletişim kutusu görünür.</span><span class="sxs-lookup"><span data-stu-id="7b84f-107">The **New Project** dialog box appears.</span></span>  
  
2. <span data-ttu-id="7b84f-108">Windows uygulamasını yeni proje görüntülemek için Visual Basic proje şablonları listesinden seçin.</span><span class="sxs-lookup"><span data-stu-id="7b84f-108">Select Windows Application from the list of Visual Basic project templates to display the new project.</span></span>  
  
3. <span data-ttu-id="7b84f-109">Tıklayarak, projeye yeni bir sınıf ekleyin **sınıfı Ekle** üzerinde **proje** menüsü.</span><span class="sxs-lookup"><span data-stu-id="7b84f-109">Add a new class to the project by clicking **Add Class** on the **Project** menu.</span></span> <span data-ttu-id="7b84f-110">**Yeni Öğe Ekle** iletişim kutusu görünür.</span><span class="sxs-lookup"><span data-stu-id="7b84f-110">The **Add New Item** dialog box appears.</span></span>  
  
4. <span data-ttu-id="7b84f-111">Seçin **sınıfı** şablonu.</span><span class="sxs-lookup"><span data-stu-id="7b84f-111">Select the **Class** template.</span></span>  
  
5. <span data-ttu-id="7b84f-112">Yeni bir sınıf adı `UserNameInfo.vb`ve ardından **Ekle** yeni sınıfı seçerek kodu görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="7b84f-112">Name the new class `UserNameInfo.vb`, and then click **Add** to display the code for the new class.</span></span>  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    >  <span data-ttu-id="7b84f-113">Visual Basic kullanabileceğiniz **Kod Düzenleyicisi** yazarak başlangıç formunuza bir sınıf eklemek için `Class` anahtar ardından yeni sınıfın adı.</span><span class="sxs-lookup"><span data-stu-id="7b84f-113">You can use the Visual Basic **Code Editor** to add a class to your startup form by typing the `Class` keyword followed by the name of the new class.</span></span> <span data-ttu-id="7b84f-114">**Kod Düzenleyicisi** karşılık gelen sağlar `End Class` deyimi sizin için.</span><span class="sxs-lookup"><span data-stu-id="7b84f-114">The **Code Editor** provides a corresponding `End Class` statement for you.</span></span>  
  
6. <span data-ttu-id="7b84f-115">Arasına aşağıdaki kodu ekleyerek sınıfı için özel bir alan tanımlayın `Class` ve `End Class` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="7b84f-115">Define a private field for the class by adding the following code between the `Class` and `End Class` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     <span data-ttu-id="7b84f-116">Alan olarak bildirme `Private` yalnızca sınıf kullanılabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7b84f-116">Declaring the field as `Private` means it can be used only within the class.</span></span> <span data-ttu-id="7b84f-117">Erişim değiştiricileri gibi kullanarak, alanlar bir sınıfın dışında kullanılabilir yapabilirsiniz `Public` daha fazla erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="7b84f-117">You can make fields available from outside a class by using access modifiers such as `Public` that provide more access.</span></span> <span data-ttu-id="7b84f-118">Daha fazla bilgi için [erişim düzeyini Visual Basic'te](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="7b84f-118">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
7. <span data-ttu-id="7b84f-119">Aşağıdaki kodu ekleyerek sınıfı için bir özellik tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="7b84f-119">Define a property for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8. <span data-ttu-id="7b84f-120">Sınıfı için bir yöntem aşağıdaki kodu ekleyerek tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="7b84f-120">Define a method for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. <span data-ttu-id="7b84f-121">Adlı bir yordam ekleyerek yeni bir sınıf için parametreli bir kurucu tanımlamak `Sub New`:</span><span class="sxs-lookup"><span data-stu-id="7b84f-121">Define a parameterized constructor for the new class by adding a procedure named `Sub New`:</span></span>  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     <span data-ttu-id="7b84f-122">`Sub New` Oluşturucusu bu sınıfına göre bir nesne oluşturulduğunda otomatik olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7b84f-122">The `Sub New` constructor is called automatically when an object based on this class is created.</span></span> <span data-ttu-id="7b84f-123">Bu oluşturucu, kullanıcı adını tutan bir alanın değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7b84f-123">This constructor sets the value of the field that holds the user name.</span></span>  
  
## <a name="to-create-a-button-to-test-the-class"></a><span data-ttu-id="7b84f-124">Test sınıfı için bir düğme oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="7b84f-124">To create a button to test the class</span></span>
  
1. <span data-ttu-id="7b84f-125">Başlangıç formu adına tıklanarak tasarım moduna değiştirin **Çözüm Gezgini** tıklayıp **Görünüm Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="7b84f-125">Change the startup form to design mode by right-clicking its name in **Solution Explorer** and then clicking **View Designer**.</span></span> <span data-ttu-id="7b84f-126">Varsayılan olarak, Windows Uygulama projeleri için başlangıç formu Form1.vb olan.</span><span class="sxs-lookup"><span data-stu-id="7b84f-126">By default, the startup form for Windows Application projects is named Form1.vb.</span></span> <span data-ttu-id="7b84f-127">Ana formu sonra görünür.</span><span class="sxs-lookup"><span data-stu-id="7b84f-127">The main form will then appear.</span></span>  
  
2. <span data-ttu-id="7b84f-128">Ana forma bir düğme ekleyin ve kodunu görüntülemek için çift tıklayın `Button1_Click` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="7b84f-128">Add a button to the main form and double-click it to display the code for the `Button1_Click` event handler.</span></span> <span data-ttu-id="7b84f-129">Test yordamı çağırmak için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7b84f-129">Add the following code to call the test procedure:</span></span>  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a><span data-ttu-id="7b84f-130">Uygulamanızı çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="7b84f-130">To run your application</span></span>
  
1. <span data-ttu-id="7b84f-131">F5 tuşuna basarak uygulamanızı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7b84f-131">Run your application by pressing F5.</span></span> <span data-ttu-id="7b84f-132">Formdaki test yordamı çağırmak için düğmeye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7b84f-132">Click the button on the form to call the test procedure.</span></span> <span data-ttu-id="7b84f-133">Özgün belirten bir ileti görüntüler `UserName` yordamı adında "MOORE, BOBBY", çünkü `Capitalize` nesnesinin yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7b84f-133">It displays a message stating that the original `UserName` is "MOORE, BOBBY", because the procedure called the `Capitalize` method of the object.</span></span>  
  
2. <span data-ttu-id="7b84f-134">Tıklayın **Tamam** ileti kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="7b84f-134">Click **OK** to dismiss the message box.</span></span> <span data-ttu-id="7b84f-135">`Button1 Click` Yordam değerini değiştirir `UserName` özelliği ve yeni değeri belirten bir ileti görüntüler `UserName` "Worden, ALi" olduğu.</span><span class="sxs-lookup"><span data-stu-id="7b84f-135">The `Button1 Click` procedure changes the value of the `UserName` property and displays a message stating that the new value of `UserName` is "Worden, Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b84f-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b84f-136">See also</span></span>

- [<span data-ttu-id="7b84f-137">Nesne odaklı programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b84f-137">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
- [<span data-ttu-id="7b84f-138">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="7b84f-138">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
