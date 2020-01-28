---
title: Komut satırından bir Windows Forms uygulaması oluşturma
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
ms.openlocfilehash: da6b9da53a36a44233dde4f0d1c4f147d913c7cf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739528"
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a><span data-ttu-id="07458-102">Nasıl yapılır: komut satırından Windows Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="07458-102">How to: Create a Windows Forms application from the command line</span></span>

<span data-ttu-id="07458-103">Aşağıdaki yordamlarda, komut satırından bir Windows Forms uygulaması oluşturmak ve çalıştırmak için gerçekleştirmeniz gereken temel adımlar açıklanır.</span><span class="sxs-lookup"><span data-stu-id="07458-103">The following procedures describe the basic steps that you must complete to create and run a Windows Forms application from the command line.</span></span> <span data-ttu-id="07458-104">Visual Studio 'da Bu yordamlar için kapsamlı destek vardır.</span><span class="sxs-lookup"><span data-stu-id="07458-104">There is extensive support for these procedures in Visual Studio.</span></span>  <span data-ttu-id="07458-105">Ayrıca bkz. [Izlenecek yol: WPF 'de Windows Forms denetimi barındırma](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="07458-105">Also see [Walkthrough: Hosting a Windows Forms Control in WPF](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>
  
## <a name="procedure"></a><span data-ttu-id="07458-106">Yordam</span><span class="sxs-lookup"><span data-stu-id="07458-106">Procedure</span></span>  
  
#### <a name="to-create-the-form"></a><span data-ttu-id="07458-107">Formu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="07458-107">To create the form</span></span>  
  
1. <span data-ttu-id="07458-108">Boş bir kod dosyasında aşağıdaki `Imports` veya `using` deyimlerini yazın:</span><span class="sxs-lookup"><span data-stu-id="07458-108">In an empty code file, type the following `Imports` or `using` statements:</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2. <span data-ttu-id="07458-109">Form sınıfından devralan `Form1` adlı bir sınıf bildirin:</span><span class="sxs-lookup"><span data-stu-id="07458-109">Declare a class named `Form1` that inherits from the Form class:</span></span>
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3. <span data-ttu-id="07458-110">`Form1`için parametresiz bir Oluşturucu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="07458-110">Create a parameterless constructor for `Form1`.</span></span>
  
     <span data-ttu-id="07458-111">Sonraki yordamda oluşturucuya daha fazla kod ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="07458-111">You will add more code to the constructor in a subsequent procedure.</span></span>
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4. <span data-ttu-id="07458-112">Sınıfa bir `Main` yöntemi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="07458-112">Add a `Main` method to the class.</span></span>
  
    1. <span data-ttu-id="07458-113">Windows Forms uygulamanızın tek iş parçacıklı C# bir grup olduğunu belirtmek için <xref:System.STAThreadAttribute> `Main` yöntemine uygulayın.</span><span class="sxs-lookup"><span data-stu-id="07458-113">Apply the <xref:System.STAThreadAttribute> to the C# `Main` method to specify your Windows Forms application is a single-threaded apartment.</span></span> <span data-ttu-id="07458-114">(Visual Basic ile geliştirilen Windows Forms uygulamaları varsayılan olarak tek iş parçacıklı bir Grup modeli kullandığından, bu öznitelik Visual Basic için gerekli değildir.)</span><span class="sxs-lookup"><span data-stu-id="07458-114">(The attribute is not necessary in Visual Basic, since Windows forms applications developed with Visual Basic use a single-threaded apartment model by default.)</span></span>  
  
    2. <span data-ttu-id="07458-115">Uygulamanıza işletim sistemi stilleri uygulamak için <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> çağırın.</span><span class="sxs-lookup"><span data-stu-id="07458-115">Call <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> to apply operating system styles to your application.</span></span>  
  
    3. <span data-ttu-id="07458-116">Formun bir örneğini oluşturun ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="07458-116">Create an instance of the form and run it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a><span data-ttu-id="07458-117">Uygulamayı derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="07458-117">To compile and run the application</span></span>  
  
1. <span data-ttu-id="07458-118">.NET Framework komut isteminde, `Form1` sınıfını oluşturduğunuz dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="07458-118">At the .NET Framework command prompt, navigate to the directory you created the `Form1` class.</span></span>  
  
2. <span data-ttu-id="07458-119">Formu derleyin.</span><span class="sxs-lookup"><span data-stu-id="07458-119">Compile the form.</span></span>  
  
    - <span data-ttu-id="07458-120">Kullanıyorsanız C#, şunu yazın: `csc form1.cs`</span><span class="sxs-lookup"><span data-stu-id="07458-120">If you are using C#, type: `csc form1.cs`</span></span>  
  
         `-or-`  
  
    - <span data-ttu-id="07458-121">Visual Basic kullanıyorsanız, şunu yazın: `vbc form1.vb`</span><span class="sxs-lookup"><span data-stu-id="07458-121">If you are using Visual Basic, type: `vbc form1.vb`</span></span>  
  
3. <span data-ttu-id="07458-122">Komut isteminde şunu yazın: `Form1.exe`</span><span class="sxs-lookup"><span data-stu-id="07458-122">At the command prompt, type: `Form1.exe`</span></span>  
  
## <a name="adding-a-control-and-handling-an-event"></a><span data-ttu-id="07458-123">Bir denetim ekleme ve olay işleme</span><span class="sxs-lookup"><span data-stu-id="07458-123">Adding a control and handling an event</span></span>

<span data-ttu-id="07458-124">Önceki yordam adımları, derlenen ve çalışan basit bir Windows formu oluşturmayı gösteren bir adım.</span><span class="sxs-lookup"><span data-stu-id="07458-124">The previous procedure steps demonstrated how to just create a basic Windows Form that compiles and runs.</span></span> <span data-ttu-id="07458-125">Sonraki yordamda, form üzerinde bir denetim oluşturma ve ekleme ve denetim için bir olay işleme işlemi gösterilir.</span><span class="sxs-lookup"><span data-stu-id="07458-125">The next procedure will show you how to create and add a control to the form, and handle an event for the control.</span></span> <span data-ttu-id="07458-126">Windows Forms ekleyebileceğiniz denetimler hakkında daha fazla bilgi için bkz. [Windows Forms denetimleri](./controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="07458-126">For more information about the controls you can add to Windows Forms, see [Windows Forms Controls](./controls/index.md).</span></span>
  
 <span data-ttu-id="07458-127">Windows Forms uygulamalarının nasıl oluşturulacağını anlamanın yanı sıra, olay tabanlı programlamayı ve Kullanıcı girişini nasıl işleyeceğinizi anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="07458-127">In addition to understanding how to create Windows Forms applications, you should understand event-based programming and how to handle user input.</span></span> <span data-ttu-id="07458-128">Daha fazla bilgi için bkz. [Windows Forms olay Işleyicileri oluşturma](creating-event-handlers-in-windows-forms.md)ve [Kullanıcı girişini işleme](./controls/handling-user-input.md)</span><span class="sxs-lookup"><span data-stu-id="07458-128">For more information, see [Creating Event Handlers in Windows Forms](creating-event-handlers-in-windows-forms.md), and [Handling User Input](./controls/handling-user-input.md)</span></span>  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a><span data-ttu-id="07458-129">Düğme denetimi bildirmek ve Click olayını işlemek için</span><span class="sxs-lookup"><span data-stu-id="07458-129">To declare a button control and handle its click event</span></span>  
  
1. <span data-ttu-id="07458-130">`button1`adlı bir düğme denetimi bildirin.</span><span class="sxs-lookup"><span data-stu-id="07458-130">Declare a button control named `button1`.</span></span>  
  
2. <span data-ttu-id="07458-131">Oluşturucuda, düğmeyi oluşturun ve <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> ve <xref:System.Windows.Forms.Control.Text%2A> özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="07458-131">In the constructor, create the button and set its <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Text%2A> properties.</span></span>  
  
3. <span data-ttu-id="07458-132">Forma düğme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="07458-132">Add the button to the form.</span></span>  
  
     <span data-ttu-id="07458-133">Aşağıdaki kod örneği, düğme denetiminin nasıl bildirileceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="07458-133">The following code example demonstrates how to declare the button control:</span></span>
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4. <span data-ttu-id="07458-134">Düğme için <xref:System.Windows.Forms.Control.Click> olayını işlemek üzere bir yöntem oluşturun.</span><span class="sxs-lookup"><span data-stu-id="07458-134">Create a method to handle the <xref:System.Windows.Forms.Control.Click> event for the button.</span></span>  
  
5. <span data-ttu-id="07458-135">Click olay işleyicisinde, "Merhaba Dünya" iletisiyle bir <xref:System.Windows.Forms.MessageBox> görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="07458-135">In the click event handler, display a <xref:System.Windows.Forms.MessageBox> with the message, "Hello World".</span></span>  
  
     <span data-ttu-id="07458-136">Aşağıdaki kod örneği, düğme denetiminin Click olayının nasıl işleneceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="07458-136">The following code example demonstrates how to handle the button control's click event:</span></span>
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6. <span data-ttu-id="07458-137"><xref:System.Windows.Forms.Control.Click> olayını oluşturduğunuz yöntemle ilişkilendirin.</span><span class="sxs-lookup"><span data-stu-id="07458-137">Associate the <xref:System.Windows.Forms.Control.Click> event with the method you created.</span></span>  
  
     <span data-ttu-id="07458-138">Aşağıdaki kod örneği, olayının yöntemiyle nasıl ilişkilendirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="07458-138">The following code example demonstrates how to associate the event with the method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7. <span data-ttu-id="07458-139">Önceki yordamda açıklandığı gibi uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="07458-139">Compile and run the application as described in the previous procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07458-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="07458-140">Example</span></span>  
 
<span data-ttu-id="07458-141">Aşağıdaki kod örneği, önceki yordamlardan alınan tüm örnektir:</span><span class="sxs-lookup"><span data-stu-id="07458-141">The following code example is the complete example from the previous procedures:</span></span>
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="07458-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07458-142">See also</span></span>

- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Control>
- [<span data-ttu-id="07458-143">Windows Forms’un Görünüşünü Değiştirme</span><span class="sxs-lookup"><span data-stu-id="07458-143">Changing the Appearance of Windows Forms</span></span>](changing-the-appearance-of-windows-forms.md)
- [<span data-ttu-id="07458-144">Windows Forms Uygulamalarını Geliştirme</span><span class="sxs-lookup"><span data-stu-id="07458-144">Enhancing Windows Forms Applications</span></span>](./advanced/index.md)
- [<span data-ttu-id="07458-145">Windows Forms'a Başlarken</span><span class="sxs-lookup"><span data-stu-id="07458-145">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
