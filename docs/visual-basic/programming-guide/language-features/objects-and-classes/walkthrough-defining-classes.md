---
description: 'Daha fazla bilgi edinin: Izlenecek yol: sınıfları tanımlama (Visual Basic)'
title: Sınıfları Tanımlama
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
ms.openlocfilehash: a97e04b92db3387966afa410d5697a05b482ae09
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100438794"
---
# <a name="walkthrough-defining-classes-visual-basic"></a><span data-ttu-id="b2cc3-103">İzlenecek Yol: Sınıfları Tanımlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2cc3-103">Walkthrough: Defining Classes (Visual Basic)</span></span>

<span data-ttu-id="b2cc3-104">Bu izlenecek yolda, daha sonra nesneleri oluşturmak için kullanabileceğiniz sınıfların nasıl tanımlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b2cc3-104">This walkthrough demonstrates how to define classes, which you can then use to create objects.</span></span> <span data-ttu-id="b2cc3-105">Ayrıca, yeni sınıfa nasıl özellik ve Yöntem ekleneceğini ve bir nesnenin nasıl başlatılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b2cc3-105">It also shows you how to add properties and methods to the new class, and demonstrates how to initialize an object.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a><span data-ttu-id="b2cc3-106">Bir sınıf tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="b2cc3-106">To define a class</span></span>
  
1. <span data-ttu-id="b2cc3-107">**Dosya** menüsünde **Yeni proje ' ye** tıklayarak bir proje oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b2cc3-107">Create a project by clicking **New Project** on the **File** menu.</span></span> <span data-ttu-id="b2cc3-108">**Yeni Proje** iletişim kutusu görünür.</span><span class="sxs-lookup"><span data-stu-id="b2cc3-108">The **New Project** dialog box appears.</span></span>  
  
2. <span data-ttu-id="b2cc3-109">Yeni projeyi göstermek için Visual Basic proje şablonları listesinden Windows uygulaması ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="b2cc3-109">Select Windows Application from the list of Visual Basic project templates to display the new project.</span></span>  
  
3. <span data-ttu-id="b2cc3-110">**Proje** menüsünde **Sınıf Ekle** ' ye tıklayarak projeye yeni bir sınıf ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b2cc3-110">Add a new class to the project by clicking **Add Class** on the **Project** menu.</span></span> <span data-ttu-id="b2cc3-111">**Yeni Öğe Ekle** iletişim kutusu görünür.</span><span class="sxs-lookup"><span data-stu-id="b2cc3-111">The **Add New Item** dialog box appears.</span></span>  
  
4. <span data-ttu-id="b2cc3-112">**Sınıf** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="b2cc3-112">Select the **Class** template.</span></span>  
  
5. <span data-ttu-id="b2cc3-113">Yeni sınıfı adlandırın `UserNameInfo.vb` ve ardından **Ekle** ' ye tıklayarak yeni sınıf için kodu görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="b2cc3-113">Name the new class `UserNameInfo.vb`, and then click **Add** to display the code for the new class.</span></span>  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    > <span data-ttu-id="b2cc3-114">Anahtar sözcüğünü ve ardından yeni sınıfın adını yazarak başlangıç formunuza bir sınıf eklemek için Visual Basic **kod düzenleyicisini** kullanabilirsiniz `Class` .</span><span class="sxs-lookup"><span data-stu-id="b2cc3-114">You can use the Visual Basic **Code Editor** to add a class to your startup form by typing the `Class` keyword followed by the name of the new class.</span></span> <span data-ttu-id="b2cc3-115">**Kod Düzenleyicisi** sizin için karşılık gelen bir `End Class` bildirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="b2cc3-115">The **Code Editor** provides a corresponding `End Class` statement for you.</span></span>  
  
6. <span data-ttu-id="b2cc3-116">Ve deyimleri arasına aşağıdaki kodu ekleyerek sınıf için özel bir alan tanımlayın `Class` `End Class` :</span><span class="sxs-lookup"><span data-stu-id="b2cc3-116">Define a private field for the class by adding the following code between the `Class` and `End Class` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     <span data-ttu-id="b2cc3-117">Alanı olarak bildirmek, `Private` yalnızca sınıfında kullanılabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b2cc3-117">Declaring the field as `Private` means it can be used only within the class.</span></span> <span data-ttu-id="b2cc3-118">Daha fazla erişim sağlayan gibi erişim değiştiricilerini kullanarak alanları bir sınıfın dışından kullanılabilir hale getirebilirsiniz `Public` .</span><span class="sxs-lookup"><span data-stu-id="b2cc3-118">You can make fields available from outside a class by using access modifiers such as `Public` that provide more access.</span></span> <span data-ttu-id="b2cc3-119">Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="b2cc3-119">For more information, see [Access levels in Visual Basic](../declared-elements/access-levels.md).</span></span>  
  
7. <span data-ttu-id="b2cc3-120">Aşağıdaki kodu ekleyerek sınıf için bir özellik tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="b2cc3-120">Define a property for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8. <span data-ttu-id="b2cc3-121">Aşağıdaki kodu ekleyerek sınıf için bir yöntem tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="b2cc3-121">Define a method for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. <span data-ttu-id="b2cc3-122">Adlı bir yordam ekleyerek yeni sınıf için parametreli bir Oluşturucu tanımlayın `Sub New` :</span><span class="sxs-lookup"><span data-stu-id="b2cc3-122">Define a parameterized constructor for the new class by adding a procedure named `Sub New`:</span></span>  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     <span data-ttu-id="b2cc3-123">`Sub New`Bu sınıfa dayalı bir nesne oluşturulduğunda Oluşturucu otomatik olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b2cc3-123">The `Sub New` constructor is called automatically when an object based on this class is created.</span></span> <span data-ttu-id="b2cc3-124">Bu Oluşturucu, Kullanıcı adını tutan alanın değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b2cc3-124">This constructor sets the value of the field that holds the user name.</span></span>  
  
## <a name="to-create-a-button-to-test-the-class"></a><span data-ttu-id="b2cc3-125">Sınıfı test etmek üzere bir düğme oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="b2cc3-125">To create a button to test the class</span></span>
  
1. <span data-ttu-id="b2cc3-126">Başlangıç formunu, **Çözüm Gezgini** adına sağ tıklayıp **Görünüm Tasarımcısı**' na tıklayarak tasarım moduna değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b2cc3-126">Change the startup form to design mode by right-clicking its name in **Solution Explorer** and then clicking **View Designer**.</span></span> <span data-ttu-id="b2cc3-127">Varsayılan olarak, Windows uygulama projeleri için başlangıç formu Form1. vb olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="b2cc3-127">By default, the startup form for Windows Application projects is named Form1.vb.</span></span> <span data-ttu-id="b2cc3-128">Ana form daha sonra görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b2cc3-128">The main form will then appear.</span></span>  
  
2. <span data-ttu-id="b2cc3-129">Ana forma bir düğme ekleyin ve olay işleyicisi için kodu göstermek üzere çift tıklayın `Button1_Click` .</span><span class="sxs-lookup"><span data-stu-id="b2cc3-129">Add a button to the main form and double-click it to display the code for the `Button1_Click` event handler.</span></span> <span data-ttu-id="b2cc3-130">Test yordamını çağırmak için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b2cc3-130">Add the following code to call the test procedure:</span></span>  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a><span data-ttu-id="b2cc3-131">Uygulamanızı çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="b2cc3-131">To run your application</span></span>
  
1. <span data-ttu-id="b2cc3-132">F5 tuşuna basarak uygulamanızı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b2cc3-132">Run your application by pressing F5.</span></span> <span data-ttu-id="b2cc3-133">Test yordamını çağırmak için formdaki düğmeye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b2cc3-133">Click the button on the form to call the test procedure.</span></span> <span data-ttu-id="b2cc3-134">Bu, `UserName` yordamın nesne yöntemi olarak adlandırıldığından, orijinalin "Moore, BODIRE" olduğunu belirten bir ileti görüntüler `Capitalize` .</span><span class="sxs-lookup"><span data-stu-id="b2cc3-134">It displays a message stating that the original `UserName` is "MOORE, BOBBY", because the procedure called the `Capitalize` method of the object.</span></span>  
  
2. <span data-ttu-id="b2cc3-135">İleti kutusunu kapatmak için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="b2cc3-135">Click **OK** to dismiss the message box.</span></span> <span data-ttu-id="b2cc3-136">`Button1 Click`Yordam, özelliğinin değerini değiştirir `UserName` ve yeni değerinin `UserName` "Worden, ali" olduğunu belirten bir ileti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b2cc3-136">The `Button1 Click` procedure changes the value of the `UserName` property and displays a message stating that the new value of `UserName` is "Worden, Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2cc3-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2cc3-137">See also</span></span>

- [<span data-ttu-id="b2cc3-138">Nesne odaklı programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2cc3-138">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
- [<span data-ttu-id="b2cc3-139">Nesneler ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="b2cc3-139">Objects and Classes</span></span>](index.md)
