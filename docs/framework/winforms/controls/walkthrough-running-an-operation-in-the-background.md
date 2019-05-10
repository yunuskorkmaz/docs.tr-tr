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
ms.openlocfilehash: 6c705c6d6ff9bbd233bbddc3a73acf8aca13a547
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211519"
---
# <a name="walkthrough-running-an-operation-in-the-background"></a><span data-ttu-id="c8589-102">İzlenecek yol: Arka Planda İşlem Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c8589-102">Walkthrough: Running an Operation in the Background</span></span>

<span data-ttu-id="c8589-103">Sahip olduğunuz işleminin tamamlanması uzun sürer ve kullanıcı arabiriminizde gecikmelere neden istiyor musunuz, kullanabileceğiniz <xref:System.ComponentModel.BackgroundWorker> sınıfı, başka bir iş parçacığı üzerinde işlemi çalıştıramadı.</span><span class="sxs-lookup"><span data-stu-id="c8589-103">If you have an operation that will take a long time to complete, and you do not want to cause delays in your user interface, you can use the <xref:System.ComponentModel.BackgroundWorker> class to run the operation on another thread.</span></span>

<span data-ttu-id="c8589-104">Bu örnekte kullanılan kod tam listesi için bkz. [nasıl yapılır: Arka planda işlem çalıştırma](how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="c8589-104">For a complete listing of the code used in this example, see [How to: Run an Operation in the Background](how-to-run-an-operation-in-the-background.md).</span></span>

## <a name="run-an-operation-in-the-background"></a><span data-ttu-id="c8589-105">Arka planda işlem çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c8589-105">Run an operation in the background</span></span>

1. <span data-ttu-id="c8589-106">Formun etkin Windows Form Tasarımcısı'nda Visual Studio ile iki <xref:System.Windows.Forms.Button> denetimler **araç kutusu** form ve ardından `Name` ve <xref:System.Windows.Forms.Control.Text%2A> göre düğmelerinin özellikleri Aşağıdaki tablo.</span><span class="sxs-lookup"><span data-stu-id="c8589-106">With your form active in the Windows Forms Designer in Visual Studio, drag two <xref:System.Windows.Forms.Button> controls from the **Toolbox** to the form, and then set the `Name` and <xref:System.Windows.Forms.Control.Text%2A> properties of the buttons according to the following table.</span></span>

    |<span data-ttu-id="c8589-107">Düğme</span><span class="sxs-lookup"><span data-stu-id="c8589-107">Button</span></span>|<span data-ttu-id="c8589-108">Ad</span><span class="sxs-lookup"><span data-stu-id="c8589-108">Name</span></span>|<span data-ttu-id="c8589-109">Metin</span><span class="sxs-lookup"><span data-stu-id="c8589-109">Text</span></span>|
    |------------|----------|----------|
    |`button1`|`startBtn`|<span data-ttu-id="c8589-110">**Start**</span><span class="sxs-lookup"><span data-stu-id="c8589-110">**Start**</span></span>|
    |`button2`|`cancelBtn`|<span data-ttu-id="c8589-111">**İptal Etme**</span><span class="sxs-lookup"><span data-stu-id="c8589-111">**Cancel**</span></span>|

2. <span data-ttu-id="c8589-112">Açık **araç kutusu**, tıklayın **bileşenleri** sekmesine ve ardından sürükleyin <xref:System.ComponentModel.BackgroundWorker> formunuza bileşen.</span><span class="sxs-lookup"><span data-stu-id="c8589-112">Open the **Toolbox**, click the **Components** tab, and then drag the <xref:System.ComponentModel.BackgroundWorker> component onto your form.</span></span>

     <span data-ttu-id="c8589-113">`backgroundWorker1` Bileşeni görünür **bileşeni Tepsi**.</span><span class="sxs-lookup"><span data-stu-id="c8589-113">The `backgroundWorker1` component appears in the **Component Tray**.</span></span>

3. <span data-ttu-id="c8589-114">İçinde **özellikleri** penceresinde <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="c8589-114">In the **Properties** window, set the <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> property to `true`.</span></span>

4. <span data-ttu-id="c8589-115">İçinde **özellikleri** penceresinde tıklayarak **olayları** düğmesini ve ardından çift <xref:System.ComponentModel.BackgroundWorker.DoWork> ve <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> olayları olay işleyicilerini oluşturma.</span><span class="sxs-lookup"><span data-stu-id="c8589-115">In the **Properties** window, click on the **Events** button, and then double-click the <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> events to create event handlers.</span></span>

5. <span data-ttu-id="c8589-116">Zaman kodunuza ekleyin <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="c8589-116">Insert your time-consuming code into the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>

6. <span data-ttu-id="c8589-117">Ayıklama işlemi tarafından gereken herhangi bir parametre <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> özelliği <xref:System.ComponentModel.DoWorkEventArgs> parametresi.</span><span class="sxs-lookup"><span data-stu-id="c8589-117">Extract any parameters required by the operation from the <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> property of the <xref:System.ComponentModel.DoWorkEventArgs> parameter.</span></span>

7. <span data-ttu-id="c8589-118">Bir hesaplama sonucu atama <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> özelliği <xref:System.ComponentModel.DoWorkEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="c8589-118">Assign the result of the computation to the <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> property of the <xref:System.ComponentModel.DoWorkEventArgs>.</span></span>

     <span data-ttu-id="c8589-119">Bu işlem, kullanılabilir <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="c8589-119">This is will be available to the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler.</span></span>

     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#2)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#2)]

8. <span data-ttu-id="c8589-120">İçinde işlemin sonucunu almak için kod ekleme <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="c8589-120">Insert code for retrieving the result of your operation in the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler.</span></span>

     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#3)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#3)]

9. <span data-ttu-id="c8589-121">Uygulama `TimeConsumingOperation` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c8589-121">Implement the `TimeConsumingOperation` method.</span></span>

     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#4)]

10. <span data-ttu-id="c8589-122">Windows Form Tasarımcısı'nda çift `startButton` oluşturmak için <xref:System.Windows.Forms.Control.Click> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="c8589-122">In the Windows Forms Designer, double-click `startButton` to create the <xref:System.Windows.Forms.Control.Click> event handler.</span></span>

11. <span data-ttu-id="c8589-123">Çağrı <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> yönteminde <xref:System.Windows.Forms.Control.Click> için olay işleyicisi `startButton`.</span><span class="sxs-lookup"><span data-stu-id="c8589-123">Call the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method in the <xref:System.Windows.Forms.Control.Click> event handler for `startButton`.</span></span>

     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#5)]

12. <span data-ttu-id="c8589-124">Windows Form Tasarımcısı'nda çift `cancelButton` oluşturmak için <xref:System.Windows.Forms.Control.Click> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="c8589-124">In the Windows Forms Designer, double-click `cancelButton` to create the <xref:System.Windows.Forms.Control.Click> event handler.</span></span>

13. <span data-ttu-id="c8589-125">Çağrı <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> yönteminde <xref:System.Windows.Forms.Control.Click> için olay işleyicisi `cancelButton`.</span><span class="sxs-lookup"><span data-stu-id="c8589-125">Call the <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> method in the <xref:System.Windows.Forms.Control.Click> event handler for `cancelButton`.</span></span>

     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#6)]

14. <span data-ttu-id="c8589-126">Dosyasının en üstüne System.ComponentModel ve System.Threading ad alanlarını içeri aktarın.</span><span class="sxs-lookup"><span data-stu-id="c8589-126">At the top of the file, import the System.ComponentModel and System.Threading namespaces.</span></span>

     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#7)]

15. <span data-ttu-id="c8589-127">Basın **F6** Çözümü derleyin ve ENTER tuşuna basın **Ctrl**+**F5** hata ayıklayıcı dışında uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c8589-127">Press **F6** to build the solution, and then press **Ctrl**+**F5** to run the application outside the debugger.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c8589-128">Basarsanız **F5** hata ayıklayıcısı altında uygulamayı çalıştırmak için özel durum ortaya `TimeConsumingOperation` yöntemi yakalandı ve hata ayıklayıcı tarafından görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c8589-128">If you press **F5** to run the application under the debugger, the exception raised in the `TimeConsumingOperation` method is caught and displayed by the debugger.</span></span> <span data-ttu-id="c8589-129">Uygulama, hata ayıklayıcı dışında çalıştırırken <xref:System.ComponentModel.BackgroundWorker> içinde önbelleğe alır ve özel durum işleme <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> özelliği <xref:System.ComponentModel.RunWorkerCompletedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="c8589-129">When you run the application outside the debugger, the <xref:System.ComponentModel.BackgroundWorker> handles the exception and caches it in the <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> property of the <xref:System.ComponentModel.RunWorkerCompletedEventArgs>.</span></span>

16. <span data-ttu-id="c8589-130">Tıklayın **Başlat** zaman uyumsuz bir işlemin çalıştırılması için düğmesine ve ardından **iptal** bir çalıştırma zaman uyumsuz işlemi durdurmak için düğmeye.</span><span class="sxs-lookup"><span data-stu-id="c8589-130">Click the **Start** button to run an asynchronous operation, and then click the **Cancel** button to stop a running asynchronous operation.</span></span>

     <span data-ttu-id="c8589-131">Her bir işlemin sonucunu görüntülenen bir <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="c8589-131">The outcome of each operation is displayed in a <xref:System.Windows.Forms.MessageBox>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c8589-132">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="c8589-132">Next steps</span></span>

- <span data-ttu-id="c8589-133">Zaman uyumsuz bir işlem devam ederken, ilerleme durumunu raporlayan bir form uygulama.</span><span class="sxs-lookup"><span data-stu-id="c8589-133">Implement a form that reports progress as an asynchronous operation proceeds.</span></span> <span data-ttu-id="c8589-134">Daha fazla bilgi için [nasıl yapılır: Arka plan işlemi kullanan bir Form uygulama](how-to-implement-a-form-that-uses-a-background-operation.md).</span><span class="sxs-lookup"><span data-stu-id="c8589-134">For more information, see [How to: Implement a Form That Uses a Background Operation](how-to-implement-a-form-that-uses-a-background-operation.md).</span></span>

- <span data-ttu-id="c8589-135">Bileşenler için zaman uyumsuz deseni destekleyen bir sınıf uygulamak.</span><span class="sxs-lookup"><span data-stu-id="c8589-135">Implement a class that supports the Asynchronous Pattern for Components.</span></span> <span data-ttu-id="c8589-136">Daha fazla bilgi için [olay tabanlı zaman uyumsuz deseni uygulama](../../../standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="c8589-136">For more information, see [Implementing the Event-based Asynchronous Pattern](../../../standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c8589-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8589-137">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [<span data-ttu-id="c8589-138">Nasıl yapılır: Arka plan işlemi kullanan bir Form uygulama</span><span class="sxs-lookup"><span data-stu-id="c8589-138">How to: Implement a Form That Uses a Background Operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="c8589-139">Nasıl yapılır: Arka planda işlem çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c8589-139">How to: Run an Operation in the Background</span></span>](how-to-run-an-operation-in-the-background.md)
- [<span data-ttu-id="c8589-140">BackgroundWorker Bileşeni</span><span class="sxs-lookup"><span data-stu-id="c8589-140">BackgroundWorker Component</span></span>](backgroundworker-component.md)
