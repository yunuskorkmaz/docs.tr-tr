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
ms.openlocfilehash: 616aa5495ec5ec5d3db6f816a96c34b3ac9f3fed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536575"
---
# <a name="how-to-download-a-file-in-the-background"></a><span data-ttu-id="462e8-102">Nasıl Yapılır: Arka Planda Dosya İndirme</span><span class="sxs-lookup"><span data-stu-id="462e8-102">How to: Download a File in the Background</span></span>
<span data-ttu-id="462e8-103">Dosya indirme ortak bir görevdir ve bu büyük olasılıkla uzun süren işlem ayrı bir iş parçacığı üzerinde çalıştırmak genellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="462e8-103">Downloading a file is a common task, and it is often useful to run this potentially time-consuming operation on a separate thread.</span></span> <span data-ttu-id="462e8-104">Kullanım <xref:System.ComponentModel.BackgroundWorker> çok az kod ile bu görevi gerçekleştirmek için bileşen.</span><span class="sxs-lookup"><span data-stu-id="462e8-104">Use the <xref:System.ComponentModel.BackgroundWorker> component to accomplish this task with very little code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="462e8-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="462e8-105">Example</span></span>  
 <span data-ttu-id="462e8-106">Aşağıdaki kod örneğinde nasıl kullanılacağını gösteren bir <xref:System.ComponentModel.BackgroundWorker> bir URL'den bir XML dosyası yüklemek için bileşen.</span><span class="sxs-lookup"><span data-stu-id="462e8-106">The following code example demonstrates how to use a <xref:System.ComponentModel.BackgroundWorker> component to load an XML file from a URL.</span></span> <span data-ttu-id="462e8-107">Kullanıcı tıkladığında **karşıdan** düğmesini <xref:System.Windows.Forms.Control.Click> olay işleyicisi çağrılarını <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> yöntemi bir <xref:System.ComponentModel.BackgroundWorker> bileşeni yükleme işlemini başlatmak üzere.</span><span class="sxs-lookup"><span data-stu-id="462e8-107">When the user clicks the **Download** button, the <xref:System.Windows.Forms.Control.Click> event handler calls the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method of a <xref:System.ComponentModel.BackgroundWorker> component to start the download operation.</span></span> <span data-ttu-id="462e8-108">Düğme için karşıdan yükleme süresini devre dışı ve indirme tamamlandıktan sonra etkin.</span><span class="sxs-lookup"><span data-stu-id="462e8-108">The button is disabled for the duration of the download, and then enabled when the download is complete.</span></span> <span data-ttu-id="462e8-109">A <xref:System.Windows.Forms.MessageBox> dosyasının içeriğini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="462e8-109">A <xref:System.Windows.Forms.MessageBox> displays the contents of the file.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#1)]  
  
 <span data-ttu-id="462e8-110">**Dosya indirme**</span><span class="sxs-lookup"><span data-stu-id="462e8-110">**Downloading the file**</span></span>  
  
 <span data-ttu-id="462e8-111">Dosya karşıdan yüklenir <xref:System.ComponentModel.BackgroundWorker> çalıştıran bileşenin iş parçacığı <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="462e8-111">The file is downloaded on the <xref:System.ComponentModel.BackgroundWorker> component's worker thread, which runs the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span> <span data-ttu-id="462e8-112">Kodunuzu çağırması bu iş parçacığı başladığı <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="462e8-112">This thread starts when your code calls the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#3)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#3)]  
  
 <span data-ttu-id="462e8-113">**Bir BackgroundWorker tamamlanması bekleniyor**</span><span class="sxs-lookup"><span data-stu-id="462e8-113">**Waiting for a BackgroundWorker to finish**</span></span>  
  
 <span data-ttu-id="462e8-114">`downloadButton_Click` Olay işleyicisi bekleme gösteren bir <xref:System.ComponentModel.BackgroundWorker> zaman uyumsuz, görevini tamamlamak için bileşen.</span><span class="sxs-lookup"><span data-stu-id="462e8-114">The `downloadButton_Click` event handler demonstrates how to wait for a <xref:System.ComponentModel.BackgroundWorker> component to finish its asynchronous task.</span></span>  
  
 <span data-ttu-id="462e8-115">Yalnızca uygulama olaylara yanıt vermek istiyorsanız ve arka plan iş parçacığı tamamlanmasını beklerken ana iş parçacığı içinde herhangi bir iş yapmak istiyor musunuz yalnızca işleyici çıkın.</span><span class="sxs-lookup"><span data-stu-id="462e8-115">If you only want the application to respond to events and do not want to do any work in the main thread while you wait for the background thread to complete, just exit the handler.</span></span>  
  
 <span data-ttu-id="462e8-116">Ana iş parçacığında iş yapmadan devam etmek istiyorsanız, kullanmak <xref:System.ComponentModel.BackgroundWorker.IsBusy%2A> belirlemek için özellik isteyip <xref:System.ComponentModel.BackgroundWorker> iş parçacığı hala çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="462e8-116">If you want to continue doing work in the main thread, use the <xref:System.ComponentModel.BackgroundWorker.IsBusy%2A> property to determine whether the <xref:System.ComponentModel.BackgroundWorker> thread is still running.</span></span> <span data-ttu-id="462e8-117">İndirme işlerken örnekte, bir ilerleme çubuğu güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="462e8-117">In the example, a progress bar is updated while the download is processing.</span></span> <span data-ttu-id="462e8-118">Çağırdığınızdan emin olun <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> kullanıcı Arabiriminin yanıt verebilir durumda tutmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="462e8-118">Be sure to call the <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> method to keep the UI responsive.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#2)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#2)]  
  
 <span data-ttu-id="462e8-119">**Sonuç görüntüleme**</span><span class="sxs-lookup"><span data-stu-id="462e8-119">**Displaying the result**</span></span>  
  
 <span data-ttu-id="462e8-120">`backgroundWorker1_RunWorkerCompleted` Yöntemi tanıtıcıları <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> olay ve arka plan işlemi tamamlandıktan sonra çağrılır.</span><span class="sxs-lookup"><span data-stu-id="462e8-120">The `backgroundWorker1_RunWorkerCompleted` method handles the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event and is called when the background operation is completed.</span></span> <span data-ttu-id="462e8-121">Bu yöntem ilk denetler <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="462e8-121">This method first checks the <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="462e8-122">Varsa <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> olan `null`, sonra da bu yöntem dosyanın içeriğini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="462e8-122">If <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> is `null`, then this method displays the contents of the file.</span></span> <span data-ttu-id="462e8-123">Ardından indirme başladığındaki devre dışı bırakıldı, İndir düğmesini etkinleştirir ve ilerleme çubuğu sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="462e8-123">It then enables the download button, which was disabled when the download began, and it resets the progress bar.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#4)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="462e8-124">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="462e8-124">Compiling the Code</span></span>  
 <span data-ttu-id="462e8-125">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="462e8-125">This example requires:</span></span>  
  
-   <span data-ttu-id="462e8-126">System.Drawing, System.Windows.Forms ve System.Xml derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="462e8-126">References to the System.Drawing, System.Windows.Forms, and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="462e8-127">Bu örnek visual Basic veya Visual C# için komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="462e8-127">For information about building this example from the command line for visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="462e8-128">Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="462e8-128">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="462e8-129">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="462e8-129">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="462e8-130">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="462e8-130">Robust Programming</span></span>  
 <span data-ttu-id="462e8-131">Her zaman kontrol <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> özelliğinde, <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> erişmeye çalışmadan önce olay işleyicisi <xref:System.ComponentModel.RunWorkerCompletedEventArgs.Result%2A?displayProperty=nameWithType> özelliği veya tarafından etkilenmiş herhangi bir nesne <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="462e8-131">Always check the <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> property in your <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler before attempting to access the <xref:System.ComponentModel.RunWorkerCompletedEventArgs.Result%2A?displayProperty=nameWithType> property or any other object that may have been affected by the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="462e8-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="462e8-132">See Also</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 [<span data-ttu-id="462e8-133">Nasıl Yapılır: Arka Planda İşlem Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="462e8-133">How to: Run an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [<span data-ttu-id="462e8-134">Nasıl yapılır: Arka Plan İşlemi Kullanan Bir Form Uygulama</span><span class="sxs-lookup"><span data-stu-id="462e8-134">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
