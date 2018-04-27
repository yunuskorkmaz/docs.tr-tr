---
title: 'Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bileşenleri Kullanma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 35e9549c-1568-4768-ad07-17cc6dff11e1
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 466c01dd44d217e466c520efba43a3a1d7bbf4c7
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a><span data-ttu-id="38f5a-102">Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bileşenleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="38f5a-102">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="38f5a-103">Birçok bileşen işlerine zaman uyumsuz olarak gerçekleştirme seçeneğini içeren sağlar.</span><span class="sxs-lookup"><span data-stu-id="38f5a-103">Many components provide you with the option of performing their work asynchronously.</span></span> <span data-ttu-id="38f5a-104"><xref:System.Media.SoundPlayer> Ve <xref:System.Windows.Forms.PictureBox> bileşenleri, örneğin, yüklemek için ses ve, ana iş parçacığı kesinti olmadan çalışmaya devam ederken "arka planda" görüntüleri etkinleştir.</span><span class="sxs-lookup"><span data-stu-id="38f5a-104">The <xref:System.Media.SoundPlayer> and <xref:System.Windows.Forms.PictureBox> components, for example, enable you to load sounds and images "in the background" while your main thread continues running without interruption.</span></span>  
  
 <span data-ttu-id="38f5a-105">Zaman uyumsuz yöntemleri destekleyen bir sınıf kullanarak [olay tabanlı zaman uyumsuz desene genel bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) bileşenin olay işleyicisi ekleme olarak kadar basit olabilir *MethodName *** tamamlandı** olayı herhangi bir olay için yaptığınız gibi.</span><span class="sxs-lookup"><span data-stu-id="38f5a-105">Using asynchronous methods on a class that supports the [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) can be as simple as attaching an event handler to the component's *MethodName***Completed** event, just as you would for any other event.</span></span> <span data-ttu-id="38f5a-106">Çağırdığınızda *MethodName *** zaman uyumsuz** yöntemi, uygulamanız çalışmaya devam eder kadar kesintisiz *MethodName *** tamamlandı** olayı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="38f5a-106">When you call the *MethodName***Async** method, your application will continue running without interruption until the *MethodName***Completed** event is raised.</span></span> <span data-ttu-id="38f5a-107">Olay işleyicisi incelemeniz <xref:System.ComponentModel.AsyncCompletedEventArgs> zaman uyumsuz işlemi başarıyla tamamlandı veya iptal edildi belirlemek için parametre.</span><span class="sxs-lookup"><span data-stu-id="38f5a-107">In your event handler, you can examine the <xref:System.ComponentModel.AsyncCompletedEventArgs> parameter to determine if the asynchronous operation successfully completed or if it was canceled.</span></span>  
  
 <span data-ttu-id="38f5a-108">Olay işleyicileri kullanma hakkında daha fazla bilgi için bkz: [olay işleyicilerine genel bakış](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="38f5a-108">For more information about using event handlers, see [Event Handlers Overview](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span></span>  
  
 <span data-ttu-id="38f5a-109">Aşağıdaki yordam zaman uyumsuz resim yükleme yeteneğini kullanmayı gösterir bir <xref:System.Windows.Forms.PictureBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="38f5a-109">The following procedure shows how to use the asynchronous image-loading capability of a <xref:System.Windows.Forms.PictureBox> control.</span></span>  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a><span data-ttu-id="38f5a-110">Zaman uyumsuz olarak bir görüntü yüklemek PictureBox denetimi etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="38f5a-110">To enable a PictureBox control to asynchronously load an image</span></span>  
  
1.  <span data-ttu-id="38f5a-111">Bir örneğini oluşturmak <xref:System.Windows.Forms.PictureBox> formunuzda bileşen.</span><span class="sxs-lookup"><span data-stu-id="38f5a-111">Create an instance of the <xref:System.Windows.Forms.PictureBox> component in your form.</span></span>  
  
2.  <span data-ttu-id="38f5a-112">Bir olay işleyicisi atamak <xref:System.Windows.Forms.PictureBox.LoadCompleted> olay.</span><span class="sxs-lookup"><span data-stu-id="38f5a-112">Assign an event handler to the <xref:System.Windows.Forms.PictureBox.LoadCompleted> event.</span></span>  
  
     <span data-ttu-id="38f5a-113">Zaman uyumsuz indirme sırasında oluşmuş olabilecek hataları denetleyin.</span><span class="sxs-lookup"><span data-stu-id="38f5a-113">Check for any errors that may have occurred during the asynchronous download here.</span></span> <span data-ttu-id="38f5a-114">Burada iptalleri denetlemek budur.</span><span class="sxs-lookup"><span data-stu-id="38f5a-114">This is also where you check for cancellation.</span></span>  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#5)]  
  
3.  <span data-ttu-id="38f5a-115">Adlı iki düğme ekleme `loadButton` ve `cancelLoadButton`, formunuza.</span><span class="sxs-lookup"><span data-stu-id="38f5a-115">Add two buttons, called `loadButton` and `cancelLoadButton`, to your form.</span></span> <span data-ttu-id="38f5a-116">Ekleme <xref:System.Windows.Forms.Control.Click> başlatmak ve yüklemeyi iptal etmek için olay işleyicileri.</span><span class="sxs-lookup"><span data-stu-id="38f5a-116">Add <xref:System.Windows.Forms.Control.Click> event handlers to start and cancel the download.</span></span>  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#4)]  
  
4.  <span data-ttu-id="38f5a-117">Uygulamanızı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="38f5a-117">Run your application.</span></span>  
  
     <span data-ttu-id="38f5a-118">Görüntü yükleme devam ettikçe formun serbestçe hareket, simge durumuna küçültün ve onu en üst düzeye çıkarmak.</span><span class="sxs-lookup"><span data-stu-id="38f5a-118">As the image download proceeds, you can move the form freely, minimize it, and maximize it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38f5a-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="38f5a-119">See Also</span></span>  
 [<span data-ttu-id="38f5a-120">Nasıl Yapılır: Arka Planda İşlem Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="38f5a-120">How to: Run an Operation in the Background</span></span>](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [<span data-ttu-id="38f5a-121">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="38f5a-121">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [<span data-ttu-id="38f5a-122">IN derleme değil: Visual Basic'te çoklu iş parçacığı kullanımı</span><span class="sxs-lookup"><span data-stu-id="38f5a-122">NOT IN BUILD: Multithreading in Visual Basic</span></span>](https://msdn.microsoft.com/library/c731a50c-09c1-4468-9646-54c86b75d269)
