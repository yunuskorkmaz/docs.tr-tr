---
title: "Nasıl yapılır: komut satırından bir Windows Forms uygulaması oluşturma"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-winforms
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e6ddb27f724e30071be339ac753cfd85599ccd86
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a><span data-ttu-id="3fef3-102">Nasıl yapılır: komut satırından bir Windows Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="3fef3-102">How to: Create a Windows Forms application from the command line</span></span>
<span data-ttu-id="3fef3-103">Aşağıdaki yordamlarda oluşturmak ve komut satırından bir Windows Forms uygulaması çalıştırmak için tamamlamanız gereken temel adımlar açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3fef3-103">The following procedures describe the basic steps that you must complete to create and run a Windows Forms application from the command line.</span></span> <span data-ttu-id="3fef3-104">Visual Studio'da bu yordamları için kapsamlı destek yoktur.</span><span class="sxs-lookup"><span data-stu-id="3fef3-104">There is extensive support for these procedures in Visual Studio.</span></span>  <span data-ttu-id="3fef3-105">Ayrıca bkz. [izlenecek yol: basit bir Windows formu oluşturma](http://msdn.microsoft.com/library/z9w2f38k\(v=vs.100\)).</span><span class="sxs-lookup"><span data-stu-id="3fef3-105">Also see [Walkthrough: Creating a Simple Windows Form](http://msdn.microsoft.com/library/z9w2f38k\(v=vs.100\)).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="3fef3-106">Yordam</span><span class="sxs-lookup"><span data-stu-id="3fef3-106">Procedure</span></span>  
  
#### <a name="to-create-the-form"></a><span data-ttu-id="3fef3-107">Form oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="3fef3-107">To create the form</span></span>  
  
1.  <span data-ttu-id="3fef3-108">Bir boş kod dosyasında aşağıdaki içeri aktarma veya using deyimleri yazın:</span><span class="sxs-lookup"><span data-stu-id="3fef3-108">In an empty code file, type the following import or using statements:</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2.  <span data-ttu-id="3fef3-109">Adlı bir sınıf bildirme `Form1` Form sınıfından devralıyor.</span><span class="sxs-lookup"><span data-stu-id="3fef3-109">Declare a class named `Form1` that inherits from the Form class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3.  <span data-ttu-id="3fef3-110">İçin varsayılan bir Oluşturucu Oluşturma `Form1`.</span><span class="sxs-lookup"><span data-stu-id="3fef3-110">Create a default constructor for `Form1`.</span></span>  
  
     <span data-ttu-id="3fef3-111">Bir sonraki yordamı oluşturucuda daha fazla kod ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="3fef3-111">You will add more code to the constructor in a subsequent procedure.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4.  <span data-ttu-id="3fef3-112">Ekleme bir `Main` sınıfına yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3fef3-112">Add a `Main` method to the class.</span></span>  
  
    1.  <span data-ttu-id="3fef3-113">Uygulama <xref:System.STAThreadAttribute> için `Main` Windows Forms uygulaması belirtmek için yöntemdir bir tek iş parçacıklı.</span><span class="sxs-lookup"><span data-stu-id="3fef3-113">Apply the <xref:System.STAThreadAttribute> to the `Main` method to specify your Windows Forms application is a single threaded apartment.</span></span>  
  
    2.  <span data-ttu-id="3fef3-114">Çağrı <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> uygulamanız için bir Windows XP görünüm vermek için.</span><span class="sxs-lookup"><span data-stu-id="3fef3-114">Call <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> to give a Windows XP appearance to your application.</span></span>  
  
    3.  <span data-ttu-id="3fef3-115">Form örneği oluşturun ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3fef3-115">Create an instance of the form and run it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a><span data-ttu-id="3fef3-116">Uygulamasını derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="3fef3-116">To compile and run the application</span></span>  
  
1.  <span data-ttu-id="3fef3-117">.NET Framework komut isteminde, oluşturduğunuz dizine gidin `Form1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3fef3-117">At the .NET Framework command prompt, navigate to the directory you created the `Form1` class.</span></span>  
  
2.  <span data-ttu-id="3fef3-118">Formun derleyin.</span><span class="sxs-lookup"><span data-stu-id="3fef3-118">Compile the form.</span></span>  
  
    -   <span data-ttu-id="3fef3-119">C# kullanıyorsanız yazın:`csc form1.cs`</span><span class="sxs-lookup"><span data-stu-id="3fef3-119">If you are using C#, type: `csc form1.cs`</span></span>  
  
         `-or-`  
  
    -   <span data-ttu-id="3fef3-120">Visual Basic kullanıyorsanız, yazın:`vbc form1.vb /r:system.dll,system.drawing.dll,system.windows.forms.dll`</span><span class="sxs-lookup"><span data-stu-id="3fef3-120">If you are using Visual Basic, type: `vbc form1.vb /r:system.dll,system.drawing.dll,system.windows.forms.dll`</span></span>  
  
3.  <span data-ttu-id="3fef3-121">Komut istemine yazın:`Form1.exe`</span><span class="sxs-lookup"><span data-stu-id="3fef3-121">At the command prompt, type: `Form1.exe`</span></span>  
  
## <a name="adding-a-control-and-handling-an-event"></a><span data-ttu-id="3fef3-122">Denetim ekleme ve bir olay işleme</span><span class="sxs-lookup"><span data-stu-id="3fef3-122">Adding a Control and Handling an Event</span></span>  
 <span data-ttu-id="3fef3-123">Önceki yordamdaki adımları yalnızca derler ve çalışan temel bir Windows formu oluşturma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3fef3-123">The previous procedure steps demonstrated how to just create a basic Windows Form that compiles and runs.</span></span> <span data-ttu-id="3fef3-124">Sonraki yordam oluşturmak ve forma denetim ekleme ve denetim için bir olay işlemek nasıl yapacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="3fef3-124">The next procedure will show you how to create and add a control to the form, and handle an event for the control.</span></span> <span data-ttu-id="3fef3-125">Windows Forms'a ekleme yapabilir denetimler hakkında daha fazla bilgi için bkz: [Windows Forms denetimleri](../../../docs/framework/winforms/controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="3fef3-125">For more information about the controls you can add to Windows Forms, see [Windows Forms Controls](../../../docs/framework/winforms/controls/index.md).</span></span>  
  
 <span data-ttu-id="3fef3-126">Windows Forms uygulamaları oluşturmak nasıl anlamanın yanı sıra, olay tabanlı programlama ve kullanıcı girişi nasıl ele alınacağını anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3fef3-126">In addition to understanding how to create Windows Forms applications, you should understand event-based programming and how to handle user input.</span></span> <span data-ttu-id="3fef3-127">Daha fazla bilgi için bkz: [Windows Forms'ta olay işleyicileri oluşturma](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md), ve [kullanıcı girişini işleme](../../../docs/framework/winforms/controls/handling-user-input.md)</span><span class="sxs-lookup"><span data-stu-id="3fef3-127">For more information, see [Creating Event Handlers in Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md), and [Handling User Input](../../../docs/framework/winforms/controls/handling-user-input.md)</span></span>  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a><span data-ttu-id="3fef3-128">Düğme denetimi bildirme ve click olayını işlemek için</span><span class="sxs-lookup"><span data-stu-id="3fef3-128">To declare a button control and handle its click event</span></span>  
  
1.  <span data-ttu-id="3fef3-129">Adlı bir düğme denetimi bildirin `button1`.</span><span class="sxs-lookup"><span data-stu-id="3fef3-129">Declare a button control named `button1`.</span></span>  
  
2.  <span data-ttu-id="3fef3-130">Oluşturucu, düğme oluşturma ve ayarlama kendi <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> ve <xref:System.Windows.Forms.Control.Text%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="3fef3-130">In the constructor, create the button and set its <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Text%2A> properties.</span></span>  
  
3.  <span data-ttu-id="3fef3-131">Düğme forma ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3fef3-131">Add the button to the form.</span></span>  
  
     <span data-ttu-id="3fef3-132">Aşağıdaki kod örneğinde, düğme denetimi bildirin gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3fef3-132">The following code example demonstrates how to declare the button control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4.  <span data-ttu-id="3fef3-133">İşlemek için bir yöntem oluşturma <xref:System.Windows.Forms.Control.Click> düğme için olay.</span><span class="sxs-lookup"><span data-stu-id="3fef3-133">Create a method to handle the <xref:System.Windows.Forms.Control.Click> event for the button.</span></span>  
  
5.  <span data-ttu-id="3fef3-134">Click olay işleyicisi görüntülemek bir <xref:System.Windows.Forms.MessageBox> "Hello World" iletisi.</span><span class="sxs-lookup"><span data-stu-id="3fef3-134">In the click event handler, display a <xref:System.Windows.Forms.MessageBox> with the message, "Hello World".</span></span>  
  
     <span data-ttu-id="3fef3-135">Aşağıdaki kod örneğinde düğmesi nasıl ele alınacağını gösteren denetimin, olay'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="3fef3-135">The following code example demonstrates how to handle the button control's click event.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6.  <span data-ttu-id="3fef3-136">İlişkilendirme <xref:System.Windows.Forms.Control.Click> oluşturduğunuz yöntemiyle olay.</span><span class="sxs-lookup"><span data-stu-id="3fef3-136">Associate the <xref:System.Windows.Forms.Control.Click> event with the method you created.</span></span>  
  
     <span data-ttu-id="3fef3-137">Aşağıdaki kod örneği, olay yöntemi ile ilişkilendirmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3fef3-137">The following code example demonstrates how to associate the event with the method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7.  <span data-ttu-id="3fef3-138">Derleme ve önceki yordamda açıklandığı şekilde uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3fef3-138">Compile and run the application as described in the previous procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fef3-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="3fef3-139">Example</span></span>  
 <span data-ttu-id="3fef3-140">Aşağıdaki kod örneğine, önceki yordamlarda gelen tam örnektir.</span><span class="sxs-lookup"><span data-stu-id="3fef3-140">Following code example is the complete example from the previous procedures.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3fef3-141">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="3fef3-141">Compiling the Code</span></span>  
  
-   <span data-ttu-id="3fef3-142">Kodu derlemek için devam etmeden yordamdaki uygulamasını derlemek ve çalıştırmak açıklar yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="3fef3-142">To compile the code, follow the instructions in the proceeding procedure that describe how to compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fef3-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3fef3-143">See Also</span></span>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.Windows.Forms.Control>  
 [<span data-ttu-id="3fef3-144">Windows formlarının görünüşünü değiştirme</span><span class="sxs-lookup"><span data-stu-id="3fef3-144">Changing the Appearance of Windows Forms</span></span>](../../../docs/framework/winforms/changing-the-appearance-of-windows-forms.md)  
 [<span data-ttu-id="3fef3-145">Windows Forms uygulamalarını geliştirme</span><span class="sxs-lookup"><span data-stu-id="3fef3-145">Enhancing Windows Forms Applications</span></span>](../../../docs/framework/winforms/advanced/index.md)  
 [<span data-ttu-id="3fef3-146">Windows Forms'a Başlarken</span><span class="sxs-lookup"><span data-stu-id="3fef3-146">Getting Started with Windows Forms</span></span>](../../../docs/framework/winforms/getting-started-with-windows-forms.md)
