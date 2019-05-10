---
title: 'Nasıl yapılır: Arka Planda Dosya İndirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 9b7bc5ae-051c-4904-9720-18f6667388bd
ms.openlocfilehash: 1d62bbac8550a5e632760e196463285e4c9a14ce
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651763"
---
# <a name="how-to-download-a-file-in-the-background"></a><span data-ttu-id="0d114-102">Nasıl yapılır: Arka Planda Dosya İndirme</span><span class="sxs-lookup"><span data-stu-id="0d114-102">How to: Download a File in the Background</span></span>
<span data-ttu-id="0d114-103">Dosya indirme genel bir görevdir ve genellikle ayrı bir iş parçacığı üzerinde olası zaman bu işlemin çalıştırılması yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="0d114-103">Downloading a file is a common task, and it is often useful to run this potentially time-consuming operation on a separate thread.</span></span> <span data-ttu-id="0d114-104">Kullanım <xref:System.ComponentModel.BackgroundWorker> çok az kod ile bu görevi gerçekleştirmek için bileşen.</span><span class="sxs-lookup"><span data-stu-id="0d114-104">Use the <xref:System.ComponentModel.BackgroundWorker> component to accomplish this task with very little code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d114-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="0d114-105">Example</span></span>  
 <span data-ttu-id="0d114-106">Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir. bir <xref:System.ComponentModel.BackgroundWorker> bileşen bir URL'den XML dosyası yüklenemedi.</span><span class="sxs-lookup"><span data-stu-id="0d114-106">The following code example demonstrates how to use a <xref:System.ComponentModel.BackgroundWorker> component to load an XML file from a URL.</span></span> <span data-ttu-id="0d114-107">Kullanıcı tıkladığında **indirme** düğmesi <xref:System.Windows.Forms.Control.Click> olay işleyicisi çağrılarını <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> yöntemi bir <xref:System.ComponentModel.BackgroundWorker> karşıdan yükleme işlemini başlatmak için bileşen.</span><span class="sxs-lookup"><span data-stu-id="0d114-107">When the user clicks the **Download** button, the <xref:System.Windows.Forms.Control.Click> event handler calls the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method of a <xref:System.ComponentModel.BackgroundWorker> component to start the download operation.</span></span> <span data-ttu-id="0d114-108">Düğme karşıdan yükleme süresi boyunca devre dışı ve indirme işlemi tamamlandıktan sonra etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0d114-108">The button is disabled for the duration of the download, and then enabled when the download is complete.</span></span> <span data-ttu-id="0d114-109">A <xref:System.Windows.Forms.MessageBox> dosyanın içeriğini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0d114-109">A <xref:System.Windows.Forms.MessageBox> displays the contents of the file.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#1)]  
  
 <span data-ttu-id="0d114-110">**Dosya indiriliyor**</span><span class="sxs-lookup"><span data-stu-id="0d114-110">**Downloading the file**</span></span>  
  
 <span data-ttu-id="0d114-111">Dosya indirildiğinde <xref:System.ComponentModel.BackgroundWorker> çalıştığı bileşenin iş parçacığı, <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="0d114-111">The file is downloaded on the <xref:System.ComponentModel.BackgroundWorker> component's worker thread, which runs the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span> <span data-ttu-id="0d114-112">Kodunuzu çağırdığında, bu iş parçacığı başlattığını <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0d114-112">This thread starts when your code calls the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#3)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#3)]  
  
 <span data-ttu-id="0d114-113">**Bir BackgroundWorker tamamlanması bekleniyor**</span><span class="sxs-lookup"><span data-stu-id="0d114-113">**Waiting for a BackgroundWorker to finish**</span></span>  
  
 <span data-ttu-id="0d114-114">`downloadButton_Click` Olay işleyicisi için beklenecek nasıl gösterir bir <xref:System.ComponentModel.BackgroundWorker> , zaman uyumsuz bir görevi tamamlamak için bileşen.</span><span class="sxs-lookup"><span data-stu-id="0d114-114">The `downloadButton_Click` event handler demonstrates how to wait for a <xref:System.ComponentModel.BackgroundWorker> component to finish its asynchronous task.</span></span>  
  
 <span data-ttu-id="0d114-115">Yalnızca uygulama olaylara yanıt vermek istediğiniz ve arka plan iş parçacığı tamamlanmasını beklerken ana iş parçacığı herhangi bir iş yapmak istiyor musunuz, yalnızca işleyici çıkın.</span><span class="sxs-lookup"><span data-stu-id="0d114-115">If you only want the application to respond to events and do not want to do any work in the main thread while you wait for the background thread to complete, just exit the handler.</span></span>  
  
 <span data-ttu-id="0d114-116">Ana iş parçacığında iş yapmaya devam etmesini istiyorsanız, kullanın <xref:System.ComponentModel.BackgroundWorker.IsBusy%2A> belirlemek için özellik isteyip <xref:System.ComponentModel.BackgroundWorker> iş parçacığı hala çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="0d114-116">If you want to continue doing work in the main thread, use the <xref:System.ComponentModel.BackgroundWorker.IsBusy%2A> property to determine whether the <xref:System.ComponentModel.BackgroundWorker> thread is still running.</span></span> <span data-ttu-id="0d114-117">İndirme işlerken örnek bir ilerleme çubuğu güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0d114-117">In the example, a progress bar is updated while the download is processing.</span></span> <span data-ttu-id="0d114-118">Çağırdığınızdan emin olun <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> UI esnek tutmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0d114-118">Be sure to call the <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> method to keep the UI responsive.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#2)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#2)]  
  
 <span data-ttu-id="0d114-119">**Sonuçları görüntüleme**</span><span class="sxs-lookup"><span data-stu-id="0d114-119">**Displaying the result**</span></span>  
  
 <span data-ttu-id="0d114-120">`backgroundWorker1_RunWorkerCompleted` Yöntemi tanıtıcıları <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> olay ve arka plan işlemi tamamlandığında çağırılır.</span><span class="sxs-lookup"><span data-stu-id="0d114-120">The `backgroundWorker1_RunWorkerCompleted` method handles the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event and is called when the background operation is completed.</span></span> <span data-ttu-id="0d114-121">Bu yöntem ilk denetler <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="0d114-121">This method first checks the <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="0d114-122">Varsa <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> olduğu `null`, bu yöntem, dosyanın içeriğini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0d114-122">If <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> is `null`, then this method displays the contents of the file.</span></span> <span data-ttu-id="0d114-123">Ardından indirme başladığında devre dışı bırakıldı, Yükle düğmesini etkinleştirir ve ilerleme çubuğu sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="0d114-123">It then enables the download button, which was disabled when the download began, and it resets the progress bar.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#4)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0d114-124">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="0d114-124">Compiling the Code</span></span>  
 <span data-ttu-id="0d114-125">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="0d114-125">This example requires:</span></span>  
  
- <span data-ttu-id="0d114-126">System.Drawing System.Windows.Forms ve System.Xml derlemesine ilişkin başvurular.</span><span class="sxs-lookup"><span data-stu-id="0d114-126">References to the System.Drawing, System.Windows.Forms, and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="0d114-127">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="0d114-127">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="0d114-128">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d114-128">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="0d114-129">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="0d114-129">Robust Programming</span></span>  
 <span data-ttu-id="0d114-130">Her zaman denetleyin <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> özelliğinde, <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> erişmeye çalışmadan önce olay işleyicisi <xref:System.ComponentModel.RunWorkerCompletedEventArgs.Result%2A?displayProperty=nameWithType> özelliği veya tarafından etkilenmiş herhangi bir nesne <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="0d114-130">Always check the <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> property in your <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler before attempting to access the <xref:System.ComponentModel.RunWorkerCompletedEventArgs.Result%2A?displayProperty=nameWithType> property or any other object that may have been affected by the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d114-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d114-131">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- [<span data-ttu-id="0d114-132">Nasıl yapılır: Arka planda işlem çalıştırma</span><span class="sxs-lookup"><span data-stu-id="0d114-132">How to: Run an Operation in the Background</span></span>](how-to-run-an-operation-in-the-background.md)
- [<span data-ttu-id="0d114-133">Nasıl yapılır: Arka plan işlemi kullanan bir Form uygulama</span><span class="sxs-lookup"><span data-stu-id="0d114-133">How to: Implement a Form That Uses a Background Operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)
