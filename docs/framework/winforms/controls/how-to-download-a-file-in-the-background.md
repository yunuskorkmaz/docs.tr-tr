---
title: 'Nasıl Yapılır: Arka Planda Dosya İndirme'
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
ms.openlocfilehash: 2396516a0e6c9aeb9b2d64a0bf6e3974d64a5cc5
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44137076"
---
# <a name="how-to-download-a-file-in-the-background"></a><span data-ttu-id="c5643-102">Nasıl Yapılır: Arka Planda Dosya İndirme</span><span class="sxs-lookup"><span data-stu-id="c5643-102">How to: Download a File in the Background</span></span>
<span data-ttu-id="c5643-103">Dosya indirme genel bir görevdir ve genellikle ayrı bir iş parçacığı üzerinde olası zaman bu işlemin çalıştırılması yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="c5643-103">Downloading a file is a common task, and it is often useful to run this potentially time-consuming operation on a separate thread.</span></span> <span data-ttu-id="c5643-104">Kullanım <xref:System.ComponentModel.BackgroundWorker> çok az kod ile bu görevi gerçekleştirmek için bileşen.</span><span class="sxs-lookup"><span data-stu-id="c5643-104">Use the <xref:System.ComponentModel.BackgroundWorker> component to accomplish this task with very little code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5643-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="c5643-105">Example</span></span>  
 <span data-ttu-id="c5643-106">Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir. bir <xref:System.ComponentModel.BackgroundWorker> bileşen bir URL'den XML dosyası yüklenemedi.</span><span class="sxs-lookup"><span data-stu-id="c5643-106">The following code example demonstrates how to use a <xref:System.ComponentModel.BackgroundWorker> component to load an XML file from a URL.</span></span> <span data-ttu-id="c5643-107">Kullanıcı tıkladığında **indirme** düğmesi <xref:System.Windows.Forms.Control.Click> olay işleyicisi çağrılarını <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> yöntemi bir <xref:System.ComponentModel.BackgroundWorker> karşıdan yükleme işlemini başlatmak için bileşen.</span><span class="sxs-lookup"><span data-stu-id="c5643-107">When the user clicks the **Download** button, the <xref:System.Windows.Forms.Control.Click> event handler calls the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method of a <xref:System.ComponentModel.BackgroundWorker> component to start the download operation.</span></span> <span data-ttu-id="c5643-108">Düğme karşıdan yükleme süresi boyunca devre dışı ve indirme işlemi tamamlandıktan sonra etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c5643-108">The button is disabled for the duration of the download, and then enabled when the download is complete.</span></span> <span data-ttu-id="c5643-109">A <xref:System.Windows.Forms.MessageBox> dosyanın içeriğini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c5643-109">A <xref:System.Windows.Forms.MessageBox> displays the contents of the file.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#1)]  
  
 <span data-ttu-id="c5643-110">**Dosya indiriliyor**</span><span class="sxs-lookup"><span data-stu-id="c5643-110">**Downloading the file**</span></span>  
  
 <span data-ttu-id="c5643-111">Dosya indirildiğinde <xref:System.ComponentModel.BackgroundWorker> çalıştığı bileşenin iş parçacığı, <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="c5643-111">The file is downloaded on the <xref:System.ComponentModel.BackgroundWorker> component's worker thread, which runs the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span> <span data-ttu-id="c5643-112">Kodunuzu çağırdığında, bu iş parçacığı başlattığını <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c5643-112">This thread starts when your code calls the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#3)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#3)]  
  
 <span data-ttu-id="c5643-113">**Bir BackgroundWorker tamamlanması bekleniyor**</span><span class="sxs-lookup"><span data-stu-id="c5643-113">**Waiting for a BackgroundWorker to finish**</span></span>  
  
 <span data-ttu-id="c5643-114">`downloadButton_Click` Olay işleyicisi için beklenecek nasıl gösterir bir <xref:System.ComponentModel.BackgroundWorker> , zaman uyumsuz bir görevi tamamlamak için bileşen.</span><span class="sxs-lookup"><span data-stu-id="c5643-114">The `downloadButton_Click` event handler demonstrates how to wait for a <xref:System.ComponentModel.BackgroundWorker> component to finish its asynchronous task.</span></span>  
  
 <span data-ttu-id="c5643-115">Yalnızca uygulama olaylara yanıt vermek istediğiniz ve arka plan iş parçacığı tamamlanmasını beklerken ana iş parçacığı herhangi bir iş yapmak istiyor musunuz, yalnızca işleyici çıkın.</span><span class="sxs-lookup"><span data-stu-id="c5643-115">If you only want the application to respond to events and do not want to do any work in the main thread while you wait for the background thread to complete, just exit the handler.</span></span>  
  
 <span data-ttu-id="c5643-116">Ana iş parçacığında iş yapmaya devam etmesini istiyorsanız, kullanın <xref:System.ComponentModel.BackgroundWorker.IsBusy%2A> belirlemek için özellik isteyip <xref:System.ComponentModel.BackgroundWorker> iş parçacığı hala çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="c5643-116">If you want to continue doing work in the main thread, use the <xref:System.ComponentModel.BackgroundWorker.IsBusy%2A> property to determine whether the <xref:System.ComponentModel.BackgroundWorker> thread is still running.</span></span> <span data-ttu-id="c5643-117">İndirme işlerken örnek bir ilerleme çubuğu güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c5643-117">In the example, a progress bar is updated while the download is processing.</span></span> <span data-ttu-id="c5643-118">Çağırdığınızdan emin olun <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> UI esnek tutmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c5643-118">Be sure to call the <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> method to keep the UI responsive.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#2)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#2)]  
  
 <span data-ttu-id="c5643-119">**Sonuçları görüntüleme**</span><span class="sxs-lookup"><span data-stu-id="c5643-119">**Displaying the result**</span></span>  
  
 <span data-ttu-id="c5643-120">`backgroundWorker1_RunWorkerCompleted` Yöntemi tanıtıcıları <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> olay ve arka plan işlemi tamamlandığında çağırılır.</span><span class="sxs-lookup"><span data-stu-id="c5643-120">The `backgroundWorker1_RunWorkerCompleted` method handles the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event and is called when the background operation is completed.</span></span> <span data-ttu-id="c5643-121">Bu yöntem ilk denetler <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="c5643-121">This method first checks the <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="c5643-122">Varsa <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> olduğu `null`, bu yöntem, dosyanın içeriğini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c5643-122">If <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> is `null`, then this method displays the contents of the file.</span></span> <span data-ttu-id="c5643-123">Ardından indirme başladığında devre dışı bırakıldı, Yükle düğmesini etkinleştirir ve ilerleme çubuğu sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="c5643-123">It then enables the download button, which was disabled when the download began, and it resets the progress bar.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#4)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c5643-124">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="c5643-124">Compiling the Code</span></span>  
 <span data-ttu-id="c5643-125">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="c5643-125">This example requires:</span></span>  
  
-   <span data-ttu-id="c5643-126">System.Drawing System.Windows.Forms ve System.Xml derlemesine ilişkin başvurular.</span><span class="sxs-lookup"><span data-stu-id="c5643-126">References to the System.Drawing, System.Windows.Forms, and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="c5643-127">Visual Basic veya Visual C# için komut satırından Bu örnek oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="c5643-127">For information about building this example from the command line for visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="c5643-128">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5643-128">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="c5643-129">Ayrıca bkz: [nasıl yapılır: derleme ve çalıştırma bir tam Windows Formları kod örneği kullanarak Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="c5643-129">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c5643-130">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="c5643-130">Robust Programming</span></span>  
 <span data-ttu-id="c5643-131">Her zaman denetleyin <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> özelliğinde, <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> erişmeye çalışmadan önce olay işleyicisi <xref:System.ComponentModel.RunWorkerCompletedEventArgs.Result%2A?displayProperty=nameWithType> özelliği veya tarafından etkilenmiş herhangi bir nesne <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="c5643-131">Always check the <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> property in your <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler before attempting to access the <xref:System.ComponentModel.RunWorkerCompletedEventArgs.Result%2A?displayProperty=nameWithType> property or any other object that may have been affected by the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5643-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c5643-132">See Also</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 [<span data-ttu-id="c5643-133">Nasıl Yapılır: Arka Planda İşlem Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c5643-133">How to: Run an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [<span data-ttu-id="c5643-134">Nasıl yapılır: Arka Plan İşlemi Kullanan Bir Form Uygulama</span><span class="sxs-lookup"><span data-stu-id="c5643-134">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
