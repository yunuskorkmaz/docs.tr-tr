---
title: 'Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bileşenleri Kullanma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: 9ac98b5c576c065f8944714c72b492539e0d2f05
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61870246"
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a><span data-ttu-id="a76bc-102">Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bileşenleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="a76bc-102">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="a76bc-103">Birçok bileşen iş zaman uyumsuz olarak gerçekleştirme seçeneğini içeren sağlar.</span><span class="sxs-lookup"><span data-stu-id="a76bc-103">Many components provide you with the option of performing their work asynchronously.</span></span> <span data-ttu-id="a76bc-104"><xref:System.Media.SoundPlayer> Ve <xref:System.Windows.Forms.PictureBox> bileşenleri, örneğin, yüklemenizi ses ve kesinti olmadan çalışan, ana iş parçacığı devam ederken "arka planda" görüntüleri etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="a76bc-104">The <xref:System.Media.SoundPlayer> and <xref:System.Windows.Forms.PictureBox> components, for example, enable you to load sounds and images "in the background" while your main thread continues running without interruption.</span></span>  
  
 <span data-ttu-id="a76bc-105">Destekleyen bir sınıf üzerinde zaman uyumsuz metotlar kullanma [olay tabanlı zaman uyumsuz desene genel bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) bileşenin bir olay işleyicisi ekleme olarak basit olabilir _MethodName_  **Tamamlanan** olduğu gibi herhangi bir olay için olay.</span><span class="sxs-lookup"><span data-stu-id="a76bc-105">Using asynchronous methods on a class that supports the [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) can be as simple as attaching an event handler to the component's _MethodName_**Completed** event, just as you would for any other event.</span></span> <span data-ttu-id="a76bc-106">Çağırdığınızda _MethodName_**zaman uyumsuz** yöntemi, uygulamanız çalışmaya devam eder kadar kesintisiz _MethodName_**Tamamlandı** olayı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a76bc-106">When you call the _MethodName_**Async** method, your application will continue running without interruption until the _MethodName_**Completed** event is raised.</span></span> <span data-ttu-id="a76bc-107">Olay işleyicisinde, incelemeniz <xref:System.ComponentModel.AsyncCompletedEventArgs> zaman uyumsuz işlem başarıyla tamamlanırsa veya iptal edildi belirlemek için parametre.</span><span class="sxs-lookup"><span data-stu-id="a76bc-107">In your event handler, you can examine the <xref:System.ComponentModel.AsyncCompletedEventArgs> parameter to determine if the asynchronous operation successfully completed or if it was canceled.</span></span>  
  
 <span data-ttu-id="a76bc-108">Olay işleyicileri kullanma hakkında daha fazla bilgi için bkz. [olay işleyicilerine genel bakış](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="a76bc-108">For more information about using event handlers, see [Event Handlers Overview](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span></span>  
  
 <span data-ttu-id="a76bc-109">Aşağıdaki yordam zaman uyumsuz resim yükleme yeteneğini kullanmayı gösterir. bir <xref:System.Windows.Forms.PictureBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="a76bc-109">The following procedure shows how to use the asynchronous image-loading capability of a <xref:System.Windows.Forms.PictureBox> control.</span></span>  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a><span data-ttu-id="a76bc-110">Zaman uyumsuz olarak görüntü yüklemek bir PictureBox denetimini etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="a76bc-110">To enable a PictureBox control to asynchronously load an image</span></span>  
  
1. <span data-ttu-id="a76bc-111">Bir örneğini oluşturmak <xref:System.Windows.Forms.PictureBox> formunuza bileşen.</span><span class="sxs-lookup"><span data-stu-id="a76bc-111">Create an instance of the <xref:System.Windows.Forms.PictureBox> component in your form.</span></span>  
  
2. <span data-ttu-id="a76bc-112">Bir olay işleyicisi atama <xref:System.Windows.Forms.PictureBox.LoadCompleted> olay.</span><span class="sxs-lookup"><span data-stu-id="a76bc-112">Assign an event handler to the <xref:System.Windows.Forms.PictureBox.LoadCompleted> event.</span></span>  
  
     <span data-ttu-id="a76bc-113">Zaman uyumsuz indirme sırasında oluşmuş olabilecek hataları kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="a76bc-113">Check for any errors that may have occurred during the asynchronous download here.</span></span> <span data-ttu-id="a76bc-114">İptalleri denetlemek burada budur.</span><span class="sxs-lookup"><span data-stu-id="a76bc-114">This is also where you check for cancellation.</span></span>  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#5)]  
  
3. <span data-ttu-id="a76bc-115">Adlı iki düğme ekleyin `loadButton` ve `cancelLoadButton`, form.</span><span class="sxs-lookup"><span data-stu-id="a76bc-115">Add two buttons, called `loadButton` and `cancelLoadButton`, to your form.</span></span> <span data-ttu-id="a76bc-116">Ekleme <xref:System.Windows.Forms.Control.Click> başlatmak ve yüklemeyi iptal etmek için olay işleyicileri.</span><span class="sxs-lookup"><span data-stu-id="a76bc-116">Add <xref:System.Windows.Forms.Control.Click> event handlers to start and cancel the download.</span></span>  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#4)]  
  
4. <span data-ttu-id="a76bc-117">Uygulamanızı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a76bc-117">Run your application.</span></span>  
  
     <span data-ttu-id="a76bc-118">Görüntü yükleme devam ettikçe form serbestçe hareket, simge durumuna küçültün ve, en üst düzeye çıkarın.</span><span class="sxs-lookup"><span data-stu-id="a76bc-118">As the image download proceeds, you can move the form freely, minimize it, and maximize it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a76bc-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a76bc-119">See also</span></span>

- [<span data-ttu-id="a76bc-120">Nasıl yapılır: Arka planda işlem çalıştırma</span><span class="sxs-lookup"><span data-stu-id="a76bc-120">How to: Run an Operation in the Background</span></span>](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [<span data-ttu-id="a76bc-121">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a76bc-121">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
