---
title: 'İzlenecek yol: Arka Planda İşlem Çalıştırma'
ms.date: 03/30/2017
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
ms.openlocfilehash: c1881ffa1c6fca546b086efea59d2263af853949
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61792177"
---
# <a name="walkthrough-running-an-operation-in-the-background"></a><span data-ttu-id="c879b-102">İzlenecek yol: Arka Planda İşlem Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c879b-102">Walkthrough: Running an Operation in the Background</span></span>
<span data-ttu-id="c879b-103">Sahip olduğunuz işleminin tamamlanması uzun sürer ve kullanıcı arabiriminizde gecikmelere neden istiyor musunuz, kullanabileceğiniz <xref:System.ComponentModel.BackgroundWorker> sınıfı, başka bir iş parçacığı üzerinde işlemi çalıştıramadı.</span><span class="sxs-lookup"><span data-stu-id="c879b-103">If you have an operation that will take a long time to complete, and you do not want to cause delays in your user interface, you can use the <xref:System.ComponentModel.BackgroundWorker> class to run the operation on another thread.</span></span>  
  
 <span data-ttu-id="c879b-104">Bu örnekte kullanılan kod tam listesi için bkz. [nasıl yapılır: Arka planda işlem çalıştırma](how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="c879b-104">For a complete listing of the code used in this example, see [How to: Run an Operation in the Background](how-to-run-an-operation-in-the-background.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c879b-105">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="c879b-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="c879b-106">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="c879b-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="c879b-107">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="c879b-107">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-run-an-operation-in-the-background"></a><span data-ttu-id="c879b-108">Bir işlemi arka planda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="c879b-108">To run an operation in the background</span></span>  
  
1. <span data-ttu-id="c879b-109">Windows Form Tasarımcısı'nda etkin, formunuzu ile iki <xref:System.Windows.Forms.Button> denetimler **araç kutusu** form ve ardından `Name` ve <xref:System.Windows.Forms.Control.Text%2A> özellikleri aşağıdaki tabloya göre düğmelerinin.</span><span class="sxs-lookup"><span data-stu-id="c879b-109">With your form active in the Windows Forms Designer, drag two <xref:System.Windows.Forms.Button> controls from the **Toolbox** to the form, and then set the `Name` and <xref:System.Windows.Forms.Control.Text%2A> properties of the buttons according to the following table.</span></span>  
  
    |<span data-ttu-id="c879b-110">Düğme</span><span class="sxs-lookup"><span data-stu-id="c879b-110">Button</span></span>|<span data-ttu-id="c879b-111">Ad</span><span class="sxs-lookup"><span data-stu-id="c879b-111">Name</span></span>|<span data-ttu-id="c879b-112">Metin</span><span class="sxs-lookup"><span data-stu-id="c879b-112">Text</span></span>|  
    |------------|----------|----------|  
    |`button1`|`startBtn`|<span data-ttu-id="c879b-113">**Start**</span><span class="sxs-lookup"><span data-stu-id="c879b-113">**Start**</span></span>|  
    |`button2`|`cancelBtn`|<span data-ttu-id="c879b-114">**İptal Etme**</span><span class="sxs-lookup"><span data-stu-id="c879b-114">**Cancel**</span></span>|  
  
2. <span data-ttu-id="c879b-115">Açık **araç kutusu**, tıklayın **bileşenleri** sekmesine ve ardından sürükleyin <xref:System.ComponentModel.BackgroundWorker> formunuza bileşen.</span><span class="sxs-lookup"><span data-stu-id="c879b-115">Open the **Toolbox**, click the **Components** tab, and then drag the <xref:System.ComponentModel.BackgroundWorker> component onto your form.</span></span>  
  
     <span data-ttu-id="c879b-116">`backgroundWorker1` Bileşeni görünür **bileşeni Tepsi**.</span><span class="sxs-lookup"><span data-stu-id="c879b-116">The `backgroundWorker1` component appears in the **Component Tray**.</span></span>  
  
3. <span data-ttu-id="c879b-117">İçinde **özellikleri** penceresinde <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="c879b-117">In the **Properties** window, set the <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> property to `true`.</span></span>  
  
4. <span data-ttu-id="c879b-118">İçinde **özellikleri** penceresinde tıklayarak **olayları** düğmesini ve ardından çift <xref:System.ComponentModel.BackgroundWorker.DoWork> ve <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> olayları olay işleyicilerini oluşturma.</span><span class="sxs-lookup"><span data-stu-id="c879b-118">In the **Properties** window, click on the **Events** button, and then double-click the <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> events to create event handlers.</span></span>  
  
5. <span data-ttu-id="c879b-119">Zaman kodunuza ekleyin <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="c879b-119">Insert your time-consuming code into the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>  
  
6. <span data-ttu-id="c879b-120">Ayıklama işlemi tarafından gereken herhangi bir parametre <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> özelliği <xref:System.ComponentModel.DoWorkEventArgs> parametresi.</span><span class="sxs-lookup"><span data-stu-id="c879b-120">Extract any parameters required by the operation from the <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> property of the <xref:System.ComponentModel.DoWorkEventArgs> parameter.</span></span>  
  
7. <span data-ttu-id="c879b-121">Bir hesaplama sonucu atama <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> özelliği <xref:System.ComponentModel.DoWorkEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="c879b-121">Assign the result of the computation to the <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> property of the <xref:System.ComponentModel.DoWorkEventArgs>.</span></span>  
  
     <span data-ttu-id="c879b-122">Bu işlem, kullanılabilir <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="c879b-122">This is will be available to the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#2)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#2)]  
  
8. <span data-ttu-id="c879b-123">İçinde işlemin sonucunu almak için kod ekleme <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="c879b-123">Insert code for retrieving the result of your operation in the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#3)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#3)]  
  
9. <span data-ttu-id="c879b-124">Uygulama `TimeConsumingOperation` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c879b-124">Implement the `TimeConsumingOperation` method.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#4)]  
  
10. <span data-ttu-id="c879b-125">Windows Form Tasarımcısı'nda çift `startButton` oluşturmak için <xref:System.Windows.Forms.Control.Click> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="c879b-125">In the Windows Forms Designer, double-click `startButton` to create the <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
11. <span data-ttu-id="c879b-126">Çağrı <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> yönteminde <xref:System.Windows.Forms.Control.Click> için olay işleyicisi `startButton`.</span><span class="sxs-lookup"><span data-stu-id="c879b-126">Call the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method in the <xref:System.Windows.Forms.Control.Click> event handler for `startButton`.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#5)]  
  
12. <span data-ttu-id="c879b-127">Windows Form Tasarımcısı'nda çift `cancelButton` oluşturmak için <xref:System.Windows.Forms.Control.Click> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="c879b-127">In the Windows Forms Designer, double-click `cancelButton` to create the <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
13. <span data-ttu-id="c879b-128">Çağrı <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> yönteminde <xref:System.Windows.Forms.Control.Click> için olay işleyicisi `cancelButton`.</span><span class="sxs-lookup"><span data-stu-id="c879b-128">Call the <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> method in the <xref:System.Windows.Forms.Control.Click> event handler for `cancelButton`.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#6)]  
  
14. <span data-ttu-id="c879b-129">Dosyasının en üstüne System.ComponentModel ve System.Threading ad alanlarını içeri aktarın.</span><span class="sxs-lookup"><span data-stu-id="c879b-129">At the top of the file, import the System.ComponentModel and System.Threading namespaces.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#7)]  
  
15. <span data-ttu-id="c879b-130">Çözümü derlemek için F6 tuşuna basın ve uygulamayı hata ayıklayıcı dışında çalıştırmak için CTRL-F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c879b-130">Press F6 to build the solution, and then press CTRL-F5 to run the application outside the debugger.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c879b-131">Hata ayıklayıcısı altında uygulamayı çalıştırmak için F5 tuşuna basarsanız, özel durum ortaya `TimeConsumingOperation` yöntemi yakalandı ve hata ayıklayıcı tarafından görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c879b-131">If you press F5 to run the application under the debugger, the exception raised in the `TimeConsumingOperation` method is caught and displayed by the debugger.</span></span> <span data-ttu-id="c879b-132">Uygulama, hata ayıklayıcı dışında çalıştırırken <xref:System.ComponentModel.BackgroundWorker> içinde önbelleğe alır ve özel durum işleme <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> özelliği <xref:System.ComponentModel.RunWorkerCompletedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="c879b-132">When you run the application outside the debugger, the <xref:System.ComponentModel.BackgroundWorker> handles the exception and caches it in the <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> property of the <xref:System.ComponentModel.RunWorkerCompletedEventArgs>.</span></span>  
  
1. <span data-ttu-id="c879b-133">Tıklayın **Başlat** zaman uyumsuz bir işlemin çalıştırılması için düğmesine ve ardından **iptal** bir çalıştırma zaman uyumsuz işlemi durdurmak için düğmeye.</span><span class="sxs-lookup"><span data-stu-id="c879b-133">Click the **Start** button to run an asynchronous operation, and then click the **Cancel** button to stop a running asynchronous operation.</span></span>  
  
     <span data-ttu-id="c879b-134">Her bir işlemin sonucunu görüntülenen bir <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="c879b-134">The outcome of each operation is displayed in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="c879b-135">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="c879b-135">Next Steps</span></span>  
  
- <span data-ttu-id="c879b-136">Zaman uyumsuz bir işlem devam ederken, ilerleme durumunu raporlayan bir form uygulama.</span><span class="sxs-lookup"><span data-stu-id="c879b-136">Implement a form that reports progress as an asynchronous operation proceeds.</span></span> <span data-ttu-id="c879b-137">Daha fazla bilgi için [nasıl yapılır: Arka plan işlemi kullanan bir Form uygulama](how-to-implement-a-form-that-uses-a-background-operation.md).</span><span class="sxs-lookup"><span data-stu-id="c879b-137">For more information, see [How to: Implement a Form That Uses a Background Operation](how-to-implement-a-form-that-uses-a-background-operation.md).</span></span>  
  
- <span data-ttu-id="c879b-138">Bileşenler için zaman uyumsuz deseni destekleyen bir sınıf uygulamak.</span><span class="sxs-lookup"><span data-stu-id="c879b-138">Implement a class that supports the Asynchronous Pattern for Components.</span></span> <span data-ttu-id="c879b-139">Daha fazla bilgi için [olay tabanlı zaman uyumsuz deseni uygulama](../../../standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="c879b-139">For more information, see [Implementing the Event-based Asynchronous Pattern](../../../standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c879b-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c879b-140">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [<span data-ttu-id="c879b-141">Nasıl yapılır: Arka plan işlemi kullanan bir Form uygulama</span><span class="sxs-lookup"><span data-stu-id="c879b-141">How to: Implement a Form That Uses a Background Operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="c879b-142">Nasıl yapılır: Arka planda işlem çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c879b-142">How to: Run an Operation in the Background</span></span>](how-to-run-an-operation-in-the-background.md)
- [<span data-ttu-id="c879b-143">BackgroundWorker Bileşeni</span><span class="sxs-lookup"><span data-stu-id="c879b-143">BackgroundWorker Component</span></span>](backgroundworker-component.md)
