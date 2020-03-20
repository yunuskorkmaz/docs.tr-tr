---
title: Komut satırından Windows Forms uygulaması oluşturma
titleSuffix: ''
ms.date: 03/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
ms.openlocfilehash: 7bd3add526a6b60d628b05d46eca22ce407c36b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181980"
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a><span data-ttu-id="67ef9-102">Nasıl yapılır: Komut satırından Windows Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="67ef9-102">How to: Create a Windows Forms application from the command line</span></span>

<span data-ttu-id="67ef9-103">Aşağıdaki yordamlar, komut satırından bir Windows Forms uygulaması oluşturmak ve çalıştırmak için tamamlamanız gereken temel adımları açıklar.</span><span class="sxs-lookup"><span data-stu-id="67ef9-103">The following procedures describe the basic steps that you must complete to create and run a Windows Forms application from the command line.</span></span> <span data-ttu-id="67ef9-104">Visual Studio'da bu prosedürler için kapsamlı bir destek vardır.</span><span class="sxs-lookup"><span data-stu-id="67ef9-104">There is extensive support for these procedures in Visual Studio.</span></span>  <span data-ttu-id="67ef9-105">Ayrıca [bkz: Walkthrough: WPF'de Windows Formları Denetimi Barındırma.](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)</span><span class="sxs-lookup"><span data-stu-id="67ef9-105">Also see [Walkthrough: Hosting a Windows Forms Control in WPF](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>
  
## <a name="procedure"></a><span data-ttu-id="67ef9-106">Yordam</span><span class="sxs-lookup"><span data-stu-id="67ef9-106">Procedure</span></span>  
  
#### <a name="to-create-the-form"></a><span data-ttu-id="67ef9-107">Formu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="67ef9-107">To create the form</span></span>  
  
1. <span data-ttu-id="67ef9-108">Boş bir kod dosyasında, `Imports` `using` aşağıdakileri veya ifadeleri yazın:</span><span class="sxs-lookup"><span data-stu-id="67ef9-108">In an empty code file, type the following `Imports` or `using` statements:</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2. <span data-ttu-id="67ef9-109">Form sınıfından `Form1` devralınan adlandırılmış bir sınıf bildirin:</span><span class="sxs-lookup"><span data-stu-id="67ef9-109">Declare a class named `Form1` that inherits from the Form class:</span></span>
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3. <span data-ttu-id="67ef9-110">Için `Form1`parametresiz bir oluşturucu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="67ef9-110">Create a parameterless constructor for `Form1`.</span></span>
  
     <span data-ttu-id="67ef9-111">Sonraki yordamda oluşturucuya daha fazla kod eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="67ef9-111">You will add more code to the constructor in a subsequent procedure.</span></span>
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4. <span data-ttu-id="67ef9-112">Sınıfa `Main` bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="67ef9-112">Add a `Main` method to the class.</span></span>
  
    1. <span data-ttu-id="67ef9-113"><xref:System.STAThreadAttribute> Windows Forms uygulamanızın `Main` tek dişli bir daire olduğunu belirtmek için C# yöntemini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="67ef9-113">Apply the <xref:System.STAThreadAttribute> to the C# `Main` method to specify your Windows Forms application is a single-threaded apartment.</span></span> <span data-ttu-id="67ef9-114">(Visual Basic ile geliştirilen Windows formları uygulamaları varsayılan olarak tek iş parçacığı daire modeli kullandığından Visual Basic'te öznitelik gerekli değildir.)</span><span class="sxs-lookup"><span data-stu-id="67ef9-114">(The attribute is not necessary in Visual Basic, since Windows forms applications developed with Visual Basic use a single-threaded apartment model by default.)</span></span>  
  
    2. <span data-ttu-id="67ef9-115">Uygulamanız için işletim sistemi stilleri uygulamak için arayın. <xref:System.Windows.Forms.Application.EnableVisualStyles%2A></span><span class="sxs-lookup"><span data-stu-id="67ef9-115">Call <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> to apply operating system styles to your application.</span></span>  
  
    3. <span data-ttu-id="67ef9-116">Formun bir örneğini oluşturun ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="67ef9-116">Create an instance of the form and run it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a><span data-ttu-id="67ef9-117">Uygulamayı derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="67ef9-117">To compile and run the application</span></span>  
  
1. <span data-ttu-id="67ef9-118">.NET Framework komut isteminde, `Form1` sınıfı oluşturduğunuz dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="67ef9-118">At the .NET Framework command prompt, navigate to the directory you created the `Form1` class.</span></span>  
  
2. <span data-ttu-id="67ef9-119">Formu derle.</span><span class="sxs-lookup"><span data-stu-id="67ef9-119">Compile the form.</span></span>  
  
    - <span data-ttu-id="67ef9-120">C# kullanıyorsanız, yazın:`csc form1.cs`</span><span class="sxs-lookup"><span data-stu-id="67ef9-120">If you are using C#, type: `csc form1.cs`</span></span>  
  
         `-or-`  
  
    - <span data-ttu-id="67ef9-121">Visual Basic kullanıyorsanız, yazın:`vbc form1.vb`</span><span class="sxs-lookup"><span data-stu-id="67ef9-121">If you are using Visual Basic, type: `vbc form1.vb`</span></span>  
  
3. <span data-ttu-id="67ef9-122">Komut isteminde, yazın:`Form1.exe`</span><span class="sxs-lookup"><span data-stu-id="67ef9-122">At the command prompt, type: `Form1.exe`</span></span>  
  
## <a name="adding-a-control-and-handling-an-event"></a><span data-ttu-id="67ef9-123">Denetim ekleme ve olayı işleme</span><span class="sxs-lookup"><span data-stu-id="67ef9-123">Adding a control and handling an event</span></span>

<span data-ttu-id="67ef9-124">Önceki yordam adımları, derleyen ve çalışan temel bir Windows Formu'nun nasıl oluşturulabildiğini gösterdi.</span><span class="sxs-lookup"><span data-stu-id="67ef9-124">The previous procedure steps demonstrated how to just create a basic Windows Form that compiles and runs.</span></span> <span data-ttu-id="67ef9-125">Sonraki yordam, forma nasıl bir denetim oluşturup ekleyeceğiniz ve denetim için bir olayı nasıl işleyeceğiniz gösterecektir.</span><span class="sxs-lookup"><span data-stu-id="67ef9-125">The next procedure will show you how to create and add a control to the form, and handle an event for the control.</span></span> <span data-ttu-id="67ef9-126">Windows Formlar'a ekleyebileceğiniz denetimler hakkında daha fazla bilgi için [Windows Forms Denetimleri'ne](./controls/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="67ef9-126">For more information about the controls you can add to Windows Forms, see [Windows Forms Controls](./controls/index.md).</span></span>
  
 <span data-ttu-id="67ef9-127">Windows Forms uygulamalarının nasıl oluşturulup oluşturulacagın yanı sıra, olay tabanlı programlamayı ve kullanıcı girişini nasıl işleyeceğinizkonusunda da anlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="67ef9-127">In addition to understanding how to create Windows Forms applications, you should understand event-based programming and how to handle user input.</span></span> <span data-ttu-id="67ef9-128">Daha fazla bilgi için [Windows Formlarında Olay İşleyicileri Oluşturma](creating-event-handlers-in-windows-forms.md)ve [Kullanıcı Girişi'ni Işleme](./controls/handling-user-input.md)</span><span class="sxs-lookup"><span data-stu-id="67ef9-128">For more information, see [Creating Event Handlers in Windows Forms](creating-event-handlers-in-windows-forms.md), and [Handling User Input](./controls/handling-user-input.md)</span></span>  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a><span data-ttu-id="67ef9-129">Düğme denetimini bildirmek ve tıklama olayını işlemek için</span><span class="sxs-lookup"><span data-stu-id="67ef9-129">To declare a button control and handle its click event</span></span>  
  
1. <span data-ttu-id="67ef9-130">'' adlı `button1`bir düğme denetimi bildirin.</span><span class="sxs-lookup"><span data-stu-id="67ef9-130">Declare a button control named `button1`.</span></span>  
  
2. <span data-ttu-id="67ef9-131">Oluşturucuolarak, düğmeyi oluşturun ve <xref:System.Windows.Forms.Control.Size%2A> <xref:System.Windows.Forms.Control.Location%2A> onun <xref:System.Windows.Forms.Control.Text%2A> ve özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="67ef9-131">In the constructor, create the button and set its <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Text%2A> properties.</span></span>  
  
3. <span data-ttu-id="67ef9-132">Düğmeye formun ekleyin.</span><span class="sxs-lookup"><span data-stu-id="67ef9-132">Add the button to the form.</span></span>  
  
     <span data-ttu-id="67ef9-133">Aşağıdaki kod örneği, düğme denetiminin nasıl bildirilen şekli gösterir:</span><span class="sxs-lookup"><span data-stu-id="67ef9-133">The following code example demonstrates how to declare the button control:</span></span>
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4. <span data-ttu-id="67ef9-134">Düğme için <xref:System.Windows.Forms.Control.Click> olayı işlemek için bir yöntem oluşturun.</span><span class="sxs-lookup"><span data-stu-id="67ef9-134">Create a method to handle the <xref:System.Windows.Forms.Control.Click> event for the button.</span></span>  
  
5. <span data-ttu-id="67ef9-135">Tıklama olay işleyicisinde, <xref:System.Windows.Forms.MessageBox> "Merhaba Dünya" iletisiyle bir görüntüle.</span><span class="sxs-lookup"><span data-stu-id="67ef9-135">In the click event handler, display a <xref:System.Windows.Forms.MessageBox> with the message, "Hello World".</span></span>  
  
     <span data-ttu-id="67ef9-136">Aşağıdaki kod örneği, düğme denetiminin tıklama olayının nasıl işleyeceğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="67ef9-136">The following code example demonstrates how to handle the button control's click event:</span></span>
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6. <span data-ttu-id="67ef9-137"><xref:System.Windows.Forms.Control.Click> Olayı oluşturduğunuz yöntemle ilişkilendirin.</span><span class="sxs-lookup"><span data-stu-id="67ef9-137">Associate the <xref:System.Windows.Forms.Control.Click> event with the method you created.</span></span>  
  
     <span data-ttu-id="67ef9-138">Aşağıdaki kod örneği, olayın yöntemle nasıl ilişkilendirilen gösteriş olduğunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="67ef9-138">The following code example demonstrates how to associate the event with the method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7. <span data-ttu-id="67ef9-139">Uygulamayı önceki yordamda açıklandığı şekilde derleyip çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="67ef9-139">Compile and run the application as described in the previous procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67ef9-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="67ef9-140">Example</span></span>  

<span data-ttu-id="67ef9-141">Aşağıdaki kod örneği önceki yordamlardan tam örnektir:</span><span class="sxs-lookup"><span data-stu-id="67ef9-141">The following code example is the complete example from the previous procedures:</span></span>
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="67ef9-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67ef9-142">See also</span></span>

- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Control>
- [<span data-ttu-id="67ef9-143">Windows Formlarının Görünüşünü Değiştirme</span><span class="sxs-lookup"><span data-stu-id="67ef9-143">Changing the Appearance of Windows Forms</span></span>](changing-the-appearance-of-windows-forms.md)
- [<span data-ttu-id="67ef9-144">Windows Forms Uygulamalarını Geliştirme</span><span class="sxs-lookup"><span data-stu-id="67ef9-144">Enhancing Windows Forms Applications</span></span>](./advanced/index.md)
- [<span data-ttu-id="67ef9-145">Windows Forms'a Başlarken</span><span class="sxs-lookup"><span data-stu-id="67ef9-145">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
