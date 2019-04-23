---
title: 'Nasıl yapılır: Komut satırından bir Windows Forms uygulaması oluşturma'
ms.date: 03/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce97089ec71fc910079910957e784605387f3e06
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59299881"
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a><span data-ttu-id="1934b-102">Nasıl yapılır: Komut satırından bir Windows Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="1934b-102">How to: Create a Windows Forms application from the command line</span></span>
<span data-ttu-id="1934b-103">Aşağıdaki yordamlar oluşturmak ve komut satırından bir Windows Forms uygulaması çalıştırmak için tamamlamanız gereken temel adımlarda açıklar.</span><span class="sxs-lookup"><span data-stu-id="1934b-103">The following procedures describe the basic steps that you must complete to create and run a Windows Forms application from the command line.</span></span> <span data-ttu-id="1934b-104">Visual Studio'da bu yordamları için kapsamlı desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="1934b-104">There is extensive support for these procedures in Visual Studio.</span></span>  <span data-ttu-id="1934b-105">Ayrıca bkz: [izlenecek yol: WPF içinde Forms Denetimi'ne bir Windows barındırma](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="1934b-105">Also see [Walkthrough: Hosting a Windows Forms Control in WPF](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="1934b-106">Yordam</span><span class="sxs-lookup"><span data-stu-id="1934b-106">Procedure</span></span>  
  
#### <a name="to-create-the-form"></a><span data-ttu-id="1934b-107">Form oluşturma</span><span class="sxs-lookup"><span data-stu-id="1934b-107">To create the form</span></span>  
  
1. <span data-ttu-id="1934b-108">Bir boş bir kod dosyasında, aşağıdaki içeri aktarma veya using deyimlerini yazın:</span><span class="sxs-lookup"><span data-stu-id="1934b-108">In an empty code file, type the following import or using statements:</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2. <span data-ttu-id="1934b-109">Adlı bir sınıf bildirme `Form1` Form sınıfından devralır.</span><span class="sxs-lookup"><span data-stu-id="1934b-109">Declare a class named `Form1` that inherits from the Form class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3. <span data-ttu-id="1934b-110">İçin varsayılan oluşturucu oluşturma `Form1`.</span><span class="sxs-lookup"><span data-stu-id="1934b-110">Create a default constructor for `Form1`.</span></span>  
  
     <span data-ttu-id="1934b-111">Bir sonraki yordamda Oluşturucusu daha fazla kod ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="1934b-111">You will add more code to the constructor in a subsequent procedure.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4. <span data-ttu-id="1934b-112">Ekleme bir `Main` sınıfı için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1934b-112">Add a `Main` method to the class.</span></span>  
  
    1.  <span data-ttu-id="1934b-113">Uygulama <xref:System.STAThreadAttribute> C# `Main` yöntemi, Windows Forms uygulamasının adını belirtin tek kullanımlık apartman.</span><span class="sxs-lookup"><span data-stu-id="1934b-113">Apply the <xref:System.STAThreadAttribute> to the C# `Main` method to specify your Windows Forms application is a single-threaded apartment.</span></span> <span data-ttu-id="1934b-114">(Windows forms uygulamaları Visual Basic ile kullanılacak tek kullanımlık apartman modeli varsayılan olarak geliştirilen beri öznitelik Visual Basic'te, gerekli değildir.)</span><span class="sxs-lookup"><span data-stu-id="1934b-114">(The attribute is not necessary in Visual Basic, since Windows forms applications developed with Visual Basic use a single-threaded apartment model by default.)</span></span>  
  
    2.  <span data-ttu-id="1934b-115">Çağrı <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> uygulamanıza işletim sistemi stilleri uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="1934b-115">Call <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> to apply operating system styles to your application.</span></span>  
  
    3.  <span data-ttu-id="1934b-116">Form örneği oluşturun ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1934b-116">Create an instance of the form and run it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a><span data-ttu-id="1934b-117">Derlemek ve uygulamayı çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="1934b-117">To compile and run the application</span></span>  
  
1. <span data-ttu-id="1934b-118">.NET Framework komut isteminde, oluşturduğunuz dizine gidin `Form1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1934b-118">At the .NET Framework command prompt, navigate to the directory you created the `Form1` class.</span></span>  
  
2. <span data-ttu-id="1934b-119">Form derleyin.</span><span class="sxs-lookup"><span data-stu-id="1934b-119">Compile the form.</span></span>  
  
    -   <span data-ttu-id="1934b-120">C# kullanıyorsanız yazın: `csc form1.cs`</span><span class="sxs-lookup"><span data-stu-id="1934b-120">If you are using C#, type: `csc form1.cs`</span></span>  
  
         `-or-`  
  
    -   <span data-ttu-id="1934b-121">Visual Basic kullanıyorsanız yazın: `vbc form1.vb`</span><span class="sxs-lookup"><span data-stu-id="1934b-121">If you are using Visual Basic, type: `vbc form1.vb`</span></span>  
  
3. <span data-ttu-id="1934b-122">Komut isteminde aşağıdakini yazın: `Form1.exe`</span><span class="sxs-lookup"><span data-stu-id="1934b-122">At the command prompt, type: `Form1.exe`</span></span>  
  
## <a name="adding-a-control-and-handling-an-event"></a><span data-ttu-id="1934b-123">Denetim ekleme ve bir olay işleme</span><span class="sxs-lookup"><span data-stu-id="1934b-123">Adding a Control and Handling an Event</span></span>  
 <span data-ttu-id="1934b-124">Önceki yordamdaki adımları yalnızca derleyen ve çalışan temel bir Windows Form oluşturma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1934b-124">The previous procedure steps demonstrated how to just create a basic Windows Form that compiles and runs.</span></span> <span data-ttu-id="1934b-125">Sonraki yordam oluşturmak ve forma denetim ekleme ve denetim için bir olayı işlemek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="1934b-125">The next procedure will show you how to create and add a control to the form, and handle an event for the control.</span></span> <span data-ttu-id="1934b-126">Windows Forms ekleyebileceğiniz denetimler hakkında daha fazla bilgi için bkz. [Windows Forms denetimleri](./controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="1934b-126">For more information about the controls you can add to Windows Forms, see [Windows Forms Controls](./controls/index.md).</span></span>  
  
 <span data-ttu-id="1934b-127">Windows Forms uygulamalarının nasıl oluşturulacağını anlamanın yanı sıra, olay tabanlı programlama ve kullanıcı girişini işlemek nasıl anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1934b-127">In addition to understanding how to create Windows Forms applications, you should understand event-based programming and how to handle user input.</span></span> <span data-ttu-id="1934b-128">Daha fazla bilgi için [Windows Forms'ta olay işleyicileri oluşturma](creating-event-handlers-in-windows-forms.md), ve [kullanıcı girişini işleme](./controls/handling-user-input.md)</span><span class="sxs-lookup"><span data-stu-id="1934b-128">For more information, see [Creating Event Handlers in Windows Forms](creating-event-handlers-in-windows-forms.md), and [Handling User Input](./controls/handling-user-input.md)</span></span>  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a><span data-ttu-id="1934b-129">Bir düğme denetimi bildirmek ve bunun tıklama olayı işlemek için</span><span class="sxs-lookup"><span data-stu-id="1934b-129">To declare a button control and handle its click event</span></span>  
  
1. <span data-ttu-id="1934b-130">Adlı bir düğme denetimi bildirin `button1`.</span><span class="sxs-lookup"><span data-stu-id="1934b-130">Declare a button control named `button1`.</span></span>  
  
2. <span data-ttu-id="1934b-131">Oluşturucu, düğmeyi oluşturmak ve ayarlamak kendi <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> ve <xref:System.Windows.Forms.Control.Text%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="1934b-131">In the constructor, create the button and set its <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Text%2A> properties.</span></span>  
  
3. <span data-ttu-id="1934b-132">Forma düğme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1934b-132">Add the button to the form.</span></span>  
  
     <span data-ttu-id="1934b-133">Aşağıdaki kod örneği, düğme denetimini nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="1934b-133">The following code example demonstrates how to declare the button control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4. <span data-ttu-id="1934b-134">İşlemek için bir yöntem oluşturma <xref:System.Windows.Forms.Control.Click> düğmesi için olay.</span><span class="sxs-lookup"><span data-stu-id="1934b-134">Create a method to handle the <xref:System.Windows.Forms.Control.Click> event for the button.</span></span>  
  
5. <span data-ttu-id="1934b-135">Click olay işleyicisi, görüntüleme bir <xref:System.Windows.Forms.MessageBox> "Hello World" iletisini ile.</span><span class="sxs-lookup"><span data-stu-id="1934b-135">In the click event handler, display a <xref:System.Windows.Forms.MessageBox> with the message, "Hello World".</span></span>  
  
     <span data-ttu-id="1934b-136">Aşağıdaki kod örneği, düğmeyi işlemek gösterilmiştir denetimin olay'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="1934b-136">The following code example demonstrates how to handle the button control's click event.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6. <span data-ttu-id="1934b-137">İlişkilendirme <xref:System.Windows.Forms.Control.Click> oluşturduğunuz yöntemiyle olay.</span><span class="sxs-lookup"><span data-stu-id="1934b-137">Associate the <xref:System.Windows.Forms.Control.Click> event with the method you created.</span></span>  
  
     <span data-ttu-id="1934b-138">Aşağıdaki kod örneği, olay yöntemi ile ilişkilendirilecek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1934b-138">The following code example demonstrates how to associate the event with the method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7. <span data-ttu-id="1934b-139">Derleme ve önceki yordamda açıklanan şekilde uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1934b-139">Compile and run the application as described in the previous procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1934b-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="1934b-140">Example</span></span>  
 <span data-ttu-id="1934b-141">Aşağıdaki kod örneğine, önceki yordamlarda gelen tam örnektir.</span><span class="sxs-lookup"><span data-stu-id="1934b-141">Following code example is the complete example from the previous procedures.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1934b-142">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="1934b-142">Compiling the Code</span></span>  
  
-   <span data-ttu-id="1934b-143">Kodu derlemek için derlemek ve uygulamayı çalıştırmak nasıl açıklayan devam etmeden yordam yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="1934b-143">To compile the code, follow the instructions in the proceeding procedure that describe how to compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1934b-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1934b-144">See also</span></span>

- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Control>
- [<span data-ttu-id="1934b-145">Windows Forms’un Görünüşünü Değiştirme</span><span class="sxs-lookup"><span data-stu-id="1934b-145">Changing the Appearance of Windows Forms</span></span>](changing-the-appearance-of-windows-forms.md)
- [<span data-ttu-id="1934b-146">Windows Forms Uygulamalarını Geliştirme</span><span class="sxs-lookup"><span data-stu-id="1934b-146">Enhancing Windows Forms Applications</span></span>](./advanced/index.md)
- [<span data-ttu-id="1934b-147">Windows Forms'a Başlarken</span><span class="sxs-lookup"><span data-stu-id="1934b-147">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
