---
title: "Tanımlayan sınıflar (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ec002e1709fa5fe31dfe7744fb91a230c32337a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-defining-classes-visual-basic"></a><span data-ttu-id="b3b75-102">İzlenecek Yol: Sınıfları Tanımlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3b75-102">Walkthrough: Defining Classes (Visual Basic)</span></span>
<span data-ttu-id="b3b75-103">Bu kılavuz, ardından nesneleri oluşturmak için kullanabileceğiniz sınıflarını tanımlamak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b3b75-103">This walkthrough demonstrates how to define classes, which you can then use to create objects.</span></span> <span data-ttu-id="b3b75-104">Ayrıca özellikleri ve yöntemleri yeni sınıfa eklemeyi gösterir ve bir nesneyi başlatmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b3b75-104">It also shows you how to add properties and methods to the new class, and demonstrates how to initialize an object.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-define-a-class"></a><span data-ttu-id="b3b75-105">Bir sınıf tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="b3b75-105">To define a class</span></span>  
  
1.  <span data-ttu-id="b3b75-106">Bir proje oluşturun **yeni proje** üzerinde **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="b3b75-106">Create a project by clicking **New Project** on the **File** menu.</span></span> <span data-ttu-id="b3b75-107">**Yeni proje** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b3b75-107">The **New Project** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="b3b75-108">Windows uygulama listesinden seçin [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] proje şablonlarını yeni proje görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="b3b75-108">Select Windows Application from the list of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] project templates to display the new project.</span></span>  
  
3.  <span data-ttu-id="b3b75-109">Projeye tıklayarak yeni bir sınıf ekleyin **sınıfı Ekle** üzerinde **proje** menüsü.</span><span class="sxs-lookup"><span data-stu-id="b3b75-109">Add a new class to the project by clicking **Add Class** on the **Project** menu.</span></span> <span data-ttu-id="b3b75-110">**Yeni Öğe Ekle** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b3b75-110">The **Add New Item** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="b3b75-111">Seçin **sınıfı** şablonu.</span><span class="sxs-lookup"><span data-stu-id="b3b75-111">Select the **Class** template.</span></span>  
  
5.  <span data-ttu-id="b3b75-112">Yeni sınıf `UserNameInfo.vb`ve ardından **Ekle** yeni sınıf kodunu görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="b3b75-112">Name the new class `UserNameInfo.vb`, and then click **Add** to display the code for the new class.</span></span>  
  
     [!code-vb[VbVbalrOOP#5](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_1.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="b3b75-113">Kullanabileceğiniz [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] **Kod düzenleyicisinde** yazarak başlangıç formunuz için bir sınıf eklemek için `Class` anahtar sözcüğü ardından yeni sınıfın adı.</span><span class="sxs-lookup"><span data-stu-id="b3b75-113">You can use the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] **Code Editor** to add a class to your startup form by typing the `Class` keyword followed by the name of the new class.</span></span> <span data-ttu-id="b3b75-114">**Kod düzenleyicisinde** karşılık gelen sağlar `End Class` sizin için deyimi.</span><span class="sxs-lookup"><span data-stu-id="b3b75-114">The **Code Editor** provides a corresponding `End Class` statement for you.</span></span>  
  
6.  <span data-ttu-id="b3b75-115">Aşağıdaki kod arasında ekleyerek sınıfı için özel bir alan tanımlayın `Class` ve `End Class` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="b3b75-115">Define a private field for the class by adding the following code between the `Class` and `End Class` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#7](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_2.vb)]  
  
     <span data-ttu-id="b3b75-116">Alan olarak bildirme `Private` yalnızca sınıfında kullanılabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b3b75-116">Declaring the field as `Private` means it can be used only within the class.</span></span> <span data-ttu-id="b3b75-117">Erişim değiştiricileri gibi kullanarak, alanları sınıf dışındaki kullanılabilir yapabilirsiniz `Public` daha fazla erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="b3b75-117">You can make fields available from outside a class by using access modifiers such as `Public` that provide more access.</span></span> <span data-ttu-id="b3b75-118">Daha fazla bilgi için bkz: [erişim düzeyini Visual Basic'te](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="b3b75-118">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
7.  <span data-ttu-id="b3b75-119">Bir özellik sınıfı için aşağıdaki kodu ekleyerek tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="b3b75-119">Define a property for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#8](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_3.vb)]  
  
8.  <span data-ttu-id="b3b75-120">Sınıfı için bir yöntem, aşağıdaki kodu ekleyerek tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="b3b75-120">Define a method for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#9](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_4.vb)]  
  
9. <span data-ttu-id="b3b75-121">Adlı bir yordam ekleyerek yeni sınıfı için parametreli bir oluşturucu tanımlarsınız `Sub New`:</span><span class="sxs-lookup"><span data-stu-id="b3b75-121">Define a parameterized constructor for the new class by adding a procedure named `Sub New`:</span></span>  
  
     [!code-vb[VbVbalrOOP#10](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_5.vb)]  
  
     <span data-ttu-id="b3b75-122">`Sub New` Oluşturucusu bu sınıfına dayalı bir nesne oluşturulduğunda otomatik olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b3b75-122">The `Sub New` constructor is called automatically when an object based on this class is created.</span></span> <span data-ttu-id="b3b75-123">Bu oluşturucu kullanıcı adı tutan alanın değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b3b75-123">This constructor sets the value of the field that holds the user name.</span></span>  
  
### <a name="to-create-a-button-to-test-the-class"></a><span data-ttu-id="b3b75-124">Sınıfı test etmek için bir düğme oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="b3b75-124">To create a button to test the class</span></span>  
  
1.  <span data-ttu-id="b3b75-125">Başlangıç formu tasarım adını sağ tıklayarak moduna **Çözüm Gezgini** ve ardından **Görünüm Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="b3b75-125">Change the startup form to design mode by right-clicking its name in **Solution Explorer** and then clicking **View Designer**.</span></span> <span data-ttu-id="b3b75-126">Varsayılan olarak, Windows uygulaması projeleri için başlangıç formu Form1.vb olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="b3b75-126">By default, the startup form for Windows Application projects is named Form1.vb.</span></span> <span data-ttu-id="b3b75-127">Ana form sonra görünür.</span><span class="sxs-lookup"><span data-stu-id="b3b75-127">The main form will then appear.</span></span>  
  
2.  <span data-ttu-id="b3b75-128">Kodunu görüntülemek için çift tıklayın ve ana forma düğme ekleme `Button1_Click` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="b3b75-128">Add a button to the main form and double-click it to display the code for the `Button1_Click` event handler.</span></span> <span data-ttu-id="b3b75-129">Test yordam çağrısı için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b3b75-129">Add the following code to call the test procedure:</span></span>  
  
     [!code-vb[VbVbalrOOP#12](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_6.vb)]  
  
### <a name="to-run-your-application"></a><span data-ttu-id="b3b75-130">Uygulamanızı çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="b3b75-130">To run your application</span></span>  
  
1.  <span data-ttu-id="b3b75-131">F5 tuşuna basarak uygulamanızı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b3b75-131">Run your application by pressing F5.</span></span> <span data-ttu-id="b3b75-132">Test yordam çağrısı forma düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b3b75-132">Click the button on the form to call the test procedure.</span></span> <span data-ttu-id="b3b75-133">Özgün belirten bir ileti görüntüler `UserName` yordamı adında "MOORE, BOBBY", çünkü `Capitalize` nesnesinin yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b3b75-133">It displays a message stating that the original `UserName` is "MOORE, BOBBY", because the procedure called the `Capitalize` method of the object.</span></span>  
  
2.  <span data-ttu-id="b3b75-134">Tıklatın **Tamam** ileti kutusu kapatılamadı.</span><span class="sxs-lookup"><span data-stu-id="b3b75-134">Click **OK** to dismiss the message box.</span></span> <span data-ttu-id="b3b75-135">`Button1 Click` Yordam değerini değiştirir `UserName` özelliği ve yeni değeri belirten bir ileti görüntüler `UserName` "Worden, Can" değil.</span><span class="sxs-lookup"><span data-stu-id="b3b75-135">The `Button1 Click` procedure changes the value of the `UserName` property and displays a message stating that the new value of `UserName` is "Worden, Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3b75-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b3b75-136">See Also</span></span>  
 [<span data-ttu-id="b3b75-137">Nesne odaklı programlama</span><span class="sxs-lookup"><span data-stu-id="b3b75-137">Object-Oriented Programming</span></span>](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)  
 [<span data-ttu-id="b3b75-138">Nesneler ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="b3b75-138">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
