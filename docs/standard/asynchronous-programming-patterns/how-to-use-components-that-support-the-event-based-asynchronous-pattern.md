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
- events [.NET], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET], asynchronous features
- components [.NET], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 35e9549c-1568-4768-ad07-17cc6dff11e1
ms.openlocfilehash: 51394a49f12e8611ac6dba7eb93a6c9a9fae0cd0
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888808"
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a><span data-ttu-id="bb0d8-102">Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bileşenleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="bb0d8-102">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="bb0d8-103">Birçok bileşen, işlerini zaman uyumsuz gerçekleştirme seçeneğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="bb0d8-103">Many components provide you with the option of performing their work asynchronously.</span></span> <span data-ttu-id="bb0d8-104"><xref:System.Media.SoundPlayer>Ve <xref:System.Windows.Forms.PictureBox> bileşenleri, örneğin, ana iş parçacığlarınız kesintiye uğramadan çalışmaya devam ederken, "arka planda" sesler ve görüntüler yüklemeye olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="bb0d8-104">The <xref:System.Media.SoundPlayer> and <xref:System.Windows.Forms.PictureBox> components, for example, enable you to load sounds and images "in the background" while your main thread continues running without interruption.</span></span>  
  
 <span data-ttu-id="bb0d8-105">[Olay tabanlı zaman uyumsuz model genel bakışını](event-based-asynchronous-pattern-overview.md) destekleyen bir sınıfta zaman uyumsuz yöntemlerin kullanılması, diğer herhangi bir olay için yaptığınız gibi bileşenin _MethodName_**tamamlandı** olayına bir olay işleyicisi eklemek kadar basit olabilir.</span><span class="sxs-lookup"><span data-stu-id="bb0d8-105">Using asynchronous methods on a class that supports the [Event-based Asynchronous Pattern Overview](event-based-asynchronous-pattern-overview.md) can be as simple as attaching an event handler to the component's _MethodName_**Completed** event, just as you would for any other event.</span></span> <span data-ttu-id="bb0d8-106">_MethodName_**zaman uyumsuz** yöntemini çağırdığınızda, uygulamanız _MethodName_**tamamlandı** olayı harekete gelinceye kadar kesintiye uğramadan çalışmaya devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="bb0d8-106">When you call the _MethodName_**Async** method, your application will continue running without interruption until the _MethodName_**Completed** event is raised.</span></span> <span data-ttu-id="bb0d8-107">Olay işleyicinizde, <xref:System.ComponentModel.AsyncCompletedEventArgs> zaman uyumsuz işlemin başarıyla tamamlanıp tamamlanmadığını veya iptal edilip edilmediğine ilişkin parametreyi inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bb0d8-107">In your event handler, you can examine the <xref:System.ComponentModel.AsyncCompletedEventArgs> parameter to determine if the asynchronous operation successfully completed or if it was canceled.</span></span>  
  
 <span data-ttu-id="bb0d8-108">Olay işleyicilerini kullanma hakkında daha fazla bilgi için bkz. [olay Işleyicilerine genel bakış](/dotnet/desktop/winforms/event-handlers-overview-windows-forms).</span><span class="sxs-lookup"><span data-stu-id="bb0d8-108">For more information about using event handlers, see [Event Handlers Overview](/dotnet/desktop/winforms/event-handlers-overview-windows-forms).</span></span>  
  
 <span data-ttu-id="bb0d8-109">Aşağıdaki yordamda, bir denetimin zaman uyumsuz görüntü yükleme yeteneğinin nasıl kullanılacağı gösterilmektedir <xref:System.Windows.Forms.PictureBox> .</span><span class="sxs-lookup"><span data-stu-id="bb0d8-109">The following procedure shows how to use the asynchronous image-loading capability of a <xref:System.Windows.Forms.PictureBox> control.</span></span>  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a><span data-ttu-id="bb0d8-110">PictureBox denetimini bir görüntüyü zaman uyumsuz olarak yüklemek üzere etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="bb0d8-110">To enable a PictureBox control to asynchronously load an image</span></span>  
  
1. <span data-ttu-id="bb0d8-111">Formunuzda bileşenin bir örneğini oluşturun <xref:System.Windows.Forms.PictureBox> .</span><span class="sxs-lookup"><span data-stu-id="bb0d8-111">Create an instance of the <xref:System.Windows.Forms.PictureBox> component in your form.</span></span>  
  
2. <span data-ttu-id="bb0d8-112">Olaya bir olay işleyicisi atayın <xref:System.Windows.Forms.PictureBox.LoadCompleted> .</span><span class="sxs-lookup"><span data-stu-id="bb0d8-112">Assign an event handler to the <xref:System.Windows.Forms.PictureBox.LoadCompleted> event.</span></span>  
  
     <span data-ttu-id="bb0d8-113">Zaman uyumsuz indirme sırasında oluşmuş olabilecek hataları kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="bb0d8-113">Check for any errors that may have occurred during the asynchronous download here.</span></span> <span data-ttu-id="bb0d8-114">Ayrıca, iptal için kontrol ettiğiniz yerdir.</span><span class="sxs-lookup"><span data-stu-id="bb0d8-114">This is also where you check for cancellation.</span></span>  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/Form1.vb#5)]  
  
3. <span data-ttu-id="bb0d8-115">Formunuza ve olarak adlandırılan iki düğme ekleyin `loadButton` `cancelLoadButton` .</span><span class="sxs-lookup"><span data-stu-id="bb0d8-115">Add two buttons, called `loadButton` and `cancelLoadButton`, to your form.</span></span> <span data-ttu-id="bb0d8-116"><xref:System.Windows.Forms.Control.Click>Başlamak için olay işleyicileri ekleyin ve indirmeyi iptal edin.</span><span class="sxs-lookup"><span data-stu-id="bb0d8-116">Add <xref:System.Windows.Forms.Control.Click> event handlers to start and cancel the download.</span></span>  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/Form1.vb#4)]  
  
4. <span data-ttu-id="bb0d8-117">Uygulamanızı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bb0d8-117">Run your application.</span></span>  
  
     <span data-ttu-id="bb0d8-118">Görüntü indirme işlemi devam ettikçe formu serbestçe taşıyabilir, simge durumuna küçültebilir ve en üst düzeye çıkarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bb0d8-118">As the image download proceeds, you can move the form freely, minimize it, and maximize it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb0d8-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb0d8-119">See also</span></span>

- [<span data-ttu-id="bb0d8-120">Nasıl yapılır: Arka Planda İşlem Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="bb0d8-120">How to: Run an Operation in the Background</span></span>](/dotnet/desktop/winforms/controls/how-to-run-an-operation-in-the-background)
- [<span data-ttu-id="bb0d8-121">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bb0d8-121">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
