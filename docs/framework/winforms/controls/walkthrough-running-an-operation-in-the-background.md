---
title: "İzlenecek yol: Arka Planda İşlem Çalıştırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- background tasks
- forms [Windows Forms], multithreading
- forms [Windows Forms], background operations
- background threads
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], background operations
- background operations
ms.assetid: 1b9a4e0a-f134-48ff-a1be-c461446a31ba
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b9be47fd57e49973c0f77a069c4f3371e4f63194
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-running-an-operation-in-the-background"></a><span data-ttu-id="7dd2a-102">İzlenecek yol: Arka Planda İşlem Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="7dd2a-102">Walkthrough: Running an Operation in the Background</span></span>
<span data-ttu-id="7dd2a-103">Tamamlanması uzun zaman alacağı işleme sahip ve kullanıcı arabiriminde gecikmelere neden istemediğiniz, kullanabileceğiniz <xref:System.ComponentModel.BackgroundWorker> işlemi başka bir iş parçacığında çalıştırmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="7dd2a-103">If you have an operation that will take a long time to complete, and you do not want to cause delays in your user interface, you can use the <xref:System.ComponentModel.BackgroundWorker> class to run the operation on another thread.</span></span>  
  
 <span data-ttu-id="7dd2a-104">Bu örnekte kullanılan kod tam listesi için bkz: [nasıl yapılır: bir işlemi arka planda çalışan](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="7dd2a-104">For a complete listing of the code used in this example, see [How to: Run an Operation in the Background](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7dd2a-105">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="7dd2a-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="7dd2a-106">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="7dd2a-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="7dd2a-107">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="7dd2a-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-run-an-operation-in-the-background"></a><span data-ttu-id="7dd2a-108">Bir işlemi arka planda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="7dd2a-108">To run an operation in the background</span></span>  
  
1.  <span data-ttu-id="7dd2a-109">Windows Forms Tasarımcısı'nda etkin formun ile iki <xref:System.Windows.Forms.Button> gelen denetler **araç** form olarak ayarlayın ve ardından için `Name` ve <xref:System.Windows.Forms.Control.Text%2A> aşağıdaki tabloya göre düğmelerin özelliklerini.</span><span class="sxs-lookup"><span data-stu-id="7dd2a-109">With your form active in the Windows Forms Designer, drag two <xref:System.Windows.Forms.Button> controls from the **Toolbox** to the form, and then set the `Name` and <xref:System.Windows.Forms.Control.Text%2A> properties of the buttons according to the following table.</span></span>  
  
    |<span data-ttu-id="7dd2a-110">Düğme</span><span class="sxs-lookup"><span data-stu-id="7dd2a-110">Button</span></span>|<span data-ttu-id="7dd2a-111">Ad</span><span class="sxs-lookup"><span data-stu-id="7dd2a-111">Name</span></span>|<span data-ttu-id="7dd2a-112">Metin</span><span class="sxs-lookup"><span data-stu-id="7dd2a-112">Text</span></span>|  
    |------------|----------|----------|  
    |`button1`|`startBtn`|<span data-ttu-id="7dd2a-113">**Start**</span><span class="sxs-lookup"><span data-stu-id="7dd2a-113">**Start**</span></span>|  
    |`button2`|`cancelBtn`|<span data-ttu-id="7dd2a-114">**İptal**</span><span class="sxs-lookup"><span data-stu-id="7dd2a-114">**Cancel**</span></span>|  
  
2.  <span data-ttu-id="7dd2a-115">Açık **araç**, tıklatın **bileşenleri** sekmesini tıklatın ve ardından sürükleyin <xref:System.ComponentModel.BackgroundWorker> formunuza bileşen.</span><span class="sxs-lookup"><span data-stu-id="7dd2a-115">Open the **Toolbox**, click the **Components** tab, and then drag the <xref:System.ComponentModel.BackgroundWorker> component onto your form.</span></span>  
  
     <span data-ttu-id="7dd2a-116">`backgroundWorker1` Bileşen görünür **bileşen**.</span><span class="sxs-lookup"><span data-stu-id="7dd2a-116">The `backgroundWorker1` component appears in the **Component Tray**.</span></span>  
  
3.  <span data-ttu-id="7dd2a-117">İçinde **özellikleri** penceresindeki ayarlayın <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="7dd2a-117">In the **Properties** window, set the <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> property to `true`.</span></span>  
  
4.  <span data-ttu-id="7dd2a-118">İçinde **özellikleri** penceresinde tıklatın **olayları** düğmesine tıklayın ve ardından <xref:System.ComponentModel.BackgroundWorker.DoWork> ve <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> olayları olay işleyicileri oluşturma.</span><span class="sxs-lookup"><span data-stu-id="7dd2a-118">In the **Properties** window, click on the **Events** button, and then double-click the <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> events to create event handlers.</span></span>  
  
5.  <span data-ttu-id="7dd2a-119">Uzun süren kodunuza eklemek <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="7dd2a-119">Insert your time-consuming code into the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>  
  
6.  <span data-ttu-id="7dd2a-120">İşlemi gerektirdiği herhangi bir parametre ayıklamak <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> özelliği <xref:System.ComponentModel.DoWorkEventArgs> parametresi.</span><span class="sxs-lookup"><span data-stu-id="7dd2a-120">Extract any parameters required by the operation from the <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> property of the <xref:System.ComponentModel.DoWorkEventArgs> parameter.</span></span>  
  
7.  <span data-ttu-id="7dd2a-121">Hesaplama sonucu atamak <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> özelliği <xref:System.ComponentModel.DoWorkEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="7dd2a-121">Assign the result of the computation to the <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> property of the <xref:System.ComponentModel.DoWorkEventArgs>.</span></span>  
  
     <span data-ttu-id="7dd2a-122">Bu olacak olan kullanılabilir <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="7dd2a-122">This is will be available to the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#2)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#2)]  
  
8.  <span data-ttu-id="7dd2a-123">İşlemin sonucunu almak için kod ekleme <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="7dd2a-123">Insert code for retrieving the result of your operation in the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#3)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#3)]  
  
9. <span data-ttu-id="7dd2a-124">Uygulama `TimeConsumingOperation` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7dd2a-124">Implement the `TimeConsumingOperation` method.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#4)]  
  
10. <span data-ttu-id="7dd2a-125">Windows Forms Tasarımcısı'nda çift `startButton` oluşturmak için <xref:System.Windows.Forms.Control.Click> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="7dd2a-125">In the Windows Forms Designer, double-click `startButton` to create the <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
11. <span data-ttu-id="7dd2a-126">Çağrı <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> yönteminde <xref:System.Windows.Forms.Control.Click> için olay işleyicisini `startButton`.</span><span class="sxs-lookup"><span data-stu-id="7dd2a-126">Call the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method in the <xref:System.Windows.Forms.Control.Click> event handler for `startButton`.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#5)]  
  
12. <span data-ttu-id="7dd2a-127">Windows Forms Tasarımcısı'nda çift `cancelButton` oluşturmak için <xref:System.Windows.Forms.Control.Click> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="7dd2a-127">In the Windows Forms Designer, double-click `cancelButton` to create the <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
13. <span data-ttu-id="7dd2a-128">Çağrı <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> yönteminde <xref:System.Windows.Forms.Control.Click> için olay işleyicisini `cancelButton`.</span><span class="sxs-lookup"><span data-stu-id="7dd2a-128">Call the <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> method in the <xref:System.Windows.Forms.Control.Click> event handler for `cancelButton`.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#6)]  
  
14. <span data-ttu-id="7dd2a-129">Dosyanın üst kısmında, System.ComponentModel ve System.Threading ad içeri aktarın.</span><span class="sxs-lookup"><span data-stu-id="7dd2a-129">At the top of the file, import the System.ComponentModel and System.Threading namespaces.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#7)]  
  
15. <span data-ttu-id="7dd2a-130">Çözümü derlemek için F6 tuşuna basın ve hata ayıklayıcı dışında uygulamayı çalıştırmak için CTRL-F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7dd2a-130">Press F6 to build the solution, and then press CTRL-F5 to run the application outside the debugger.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7dd2a-131">Hata ayıklayıcı altında uygulamayı çalıştırmak için F5 tuşuna basarsanız, özel durum oluşturuldu `TimeConsumingOperation` yöntemi yakalanan ve hata ayıklayıcı tarafından görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7dd2a-131">If you press F5 to run the application under the debugger, the exception raised in the `TimeConsumingOperation` method is caught and displayed by the debugger.</span></span> <span data-ttu-id="7dd2a-132">Hata ayıklayıcı dışında uygulamayı çalıştırdığınızda <xref:System.ComponentModel.BackgroundWorker> özel durumu işler ve içinde önbelleğe <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> özelliği <xref:System.ComponentModel.RunWorkerCompletedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="7dd2a-132">When you run the application outside the debugger, the <xref:System.ComponentModel.BackgroundWorker> handles the exception and caches it in the <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> property of the <xref:System.ComponentModel.RunWorkerCompletedEventArgs>.</span></span>  
  
1.  <span data-ttu-id="7dd2a-133">Tıklatın **Başlat** zaman uyumsuz bir işlem çalıştırmak için düğmesine tıklayın ve ardından **iptal** çalışan zaman uyumsuz işlemi durdurmak için düğmesi.</span><span class="sxs-lookup"><span data-stu-id="7dd2a-133">Click the **Start** button to run an asynchronous operation, and then click the **Cancel** button to stop a running asynchronous operation.</span></span>  
  
     <span data-ttu-id="7dd2a-134">Her bir işlemin sonucunu görüntülenen bir <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="7dd2a-134">The outcome of each operation is displayed in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="7dd2a-135">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="7dd2a-135">Next Steps</span></span>  
  
-   <span data-ttu-id="7dd2a-136">Zaman uyumsuz bir işlem devam ettikçe ilerleme raporları bir form uygulayın.</span><span class="sxs-lookup"><span data-stu-id="7dd2a-136">Implement a form that reports progress as an asynchronous operation proceeds.</span></span> <span data-ttu-id="7dd2a-137">Daha fazla bilgi için bkz: [nasıl yapılır: bir arka plan işlemi kullanan bir Form uygulama](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).</span><span class="sxs-lookup"><span data-stu-id="7dd2a-137">For more information, see [How to: Implement a Form That Uses a Background Operation](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).</span></span>  
  
-   <span data-ttu-id="7dd2a-138">Bileşenleri için zaman uyumsuz deseni destekleyen bir sınıf uygulama.</span><span class="sxs-lookup"><span data-stu-id="7dd2a-138">Implement a class that supports the Asynchronous Pattern for Components.</span></span> <span data-ttu-id="7dd2a-139">Daha fazla bilgi için bkz: [olay tabanlı zaman uyumsuz deseni uygulama](../../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="7dd2a-139">For more information, see [Implementing the Event-based Asynchronous Pattern](../../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dd2a-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7dd2a-140">See Also</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.DoWorkEventArgs>  
 [<span data-ttu-id="7dd2a-141">Nasıl yapılır: Arka Plan İşlemi Kullanan Bir Form Uygulama</span><span class="sxs-lookup"><span data-stu-id="7dd2a-141">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [<span data-ttu-id="7dd2a-142">Nasıl Yapılır: Arka Planda İşlem Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="7dd2a-142">How to: Run an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [<span data-ttu-id="7dd2a-143">BackgroundWorker Bileşeni</span><span class="sxs-lookup"><span data-stu-id="7dd2a-143">BackgroundWorker Component</span></span>](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
