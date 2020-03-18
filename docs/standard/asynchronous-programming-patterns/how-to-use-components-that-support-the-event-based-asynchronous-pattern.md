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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "61870246"
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a><span data-ttu-id="777f4-102">Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bileşenleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="777f4-102">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="777f4-103">Birçok bileşen, işlerini eşit bir şekilde gerçekleştirme seçeneği sunar.</span><span class="sxs-lookup"><span data-stu-id="777f4-103">Many components provide you with the option of performing their work asynchronously.</span></span> <span data-ttu-id="777f4-104">Ve <xref:System.Media.SoundPlayer> <xref:System.Windows.Forms.PictureBox> bileşenleri, örneğin, ana iş parçacığı kesintisiz çalışmaya devam ederken "arka planda" sesleri ve görüntüleri yüklemek için izin.</span><span class="sxs-lookup"><span data-stu-id="777f4-104">The <xref:System.Media.SoundPlayer> and <xref:System.Windows.Forms.PictureBox> components, for example, enable you to load sounds and images "in the background" while your main thread continues running without interruption.</span></span>  
  
 <span data-ttu-id="777f4-105">[Olay tabanlı Asynchronous Desen Genel Bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) destekleyen bir sınıfta eşzamanlı yöntemler kullanmak, diğer tüm etkinlikte olduğu gibi, bileşenin _MethodName_**Tamamlanan** olayına bir olay işleyicisi eklemek kadar basit olabilir.</span><span class="sxs-lookup"><span data-stu-id="777f4-105">Using asynchronous methods on a class that supports the [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) can be as simple as attaching an event handler to the component's _MethodName_**Completed** event, just as you would for any other event.</span></span> <span data-ttu-id="777f4-106">_MethodName_**Async** yöntemini aradiğinizde, _UygulamaAdı_**Tamamlanan** olay yükseltilene kadar uygulamanız kesintisiz olarak çalışmaya devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="777f4-106">When you call the _MethodName_**Async** method, your application will continue running without interruption until the _MethodName_**Completed** event is raised.</span></span> <span data-ttu-id="777f4-107">Olay işleyicinizde, eşzamanlı işlemin <xref:System.ComponentModel.AsyncCompletedEventArgs> başarıyla tamamlanıp tamamlanmadığını veya iptal edilip edilip edilemediğinizi belirlemek için parametreyi inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="777f4-107">In your event handler, you can examine the <xref:System.ComponentModel.AsyncCompletedEventArgs> parameter to determine if the asynchronous operation successfully completed or if it was canceled.</span></span>  
  
 <span data-ttu-id="777f4-108">Olay işleyicilerini kullanma hakkında daha fazla bilgi için [Olay İşleyicilerine Genel Bakış'a](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="777f4-108">For more information about using event handlers, see [Event Handlers Overview](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span></span>  
  
 <span data-ttu-id="777f4-109">Aşağıdaki yordam, bir <xref:System.Windows.Forms.PictureBox> denetimin eşzamanlı görüntü yükleme yeteneğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="777f4-109">The following procedure shows how to use the asynchronous image-loading capability of a <xref:System.Windows.Forms.PictureBox> control.</span></span>  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a><span data-ttu-id="777f4-110">Bir görüntüyü eşit bir şekilde yüklemek için PictureBox denetimini etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="777f4-110">To enable a PictureBox control to asynchronously load an image</span></span>  
  
1. <span data-ttu-id="777f4-111">Formunuzda bileşenin <xref:System.Windows.Forms.PictureBox> bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="777f4-111">Create an instance of the <xref:System.Windows.Forms.PictureBox> component in your form.</span></span>  
  
2. <span data-ttu-id="777f4-112">Olay için bir olay <xref:System.Windows.Forms.PictureBox.LoadCompleted> işleyicisi atayın.</span><span class="sxs-lookup"><span data-stu-id="777f4-112">Assign an event handler to the <xref:System.Windows.Forms.PictureBox.LoadCompleted> event.</span></span>  
  
     <span data-ttu-id="777f4-113">Burada asynchronous indirme sırasında oluşmuş olabilecek hataları denetleyin.</span><span class="sxs-lookup"><span data-stu-id="777f4-113">Check for any errors that may have occurred during the asynchronous download here.</span></span> <span data-ttu-id="777f4-114">Burası aynı zamanda iptal olup olmadığını kontrol ettiğiniz yerdir.</span><span class="sxs-lookup"><span data-stu-id="777f4-114">This is also where you check for cancellation.</span></span>  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#5)]  
  
3. <span data-ttu-id="777f4-115">Forunuzda iki `loadButton` `cancelLoadButton`düğme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="777f4-115">Add two buttons, called `loadButton` and `cancelLoadButton`, to your form.</span></span> <span data-ttu-id="777f4-116">İndirme başlatmak ve iptal etmek için olay işleyicileri ekleyin. <xref:System.Windows.Forms.Control.Click></span><span class="sxs-lookup"><span data-stu-id="777f4-116">Add <xref:System.Windows.Forms.Control.Click> event handlers to start and cancel the download.</span></span>  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#4)]  
  
4. <span data-ttu-id="777f4-117">Başvurunuzu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="777f4-117">Run your application.</span></span>  
  
     <span data-ttu-id="777f4-118">Görüntü indirme ilerledikçe, formu serbestçe taşıyabilir, simge durumuna küçültebilir ve en üst düzeye çıkarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="777f4-118">As the image download proceeds, you can move the form freely, minimize it, and maximize it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="777f4-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="777f4-119">See also</span></span>

- [<span data-ttu-id="777f4-120">Nasıl Yapılır: Arka Planda İşlem Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="777f4-120">How to: Run an Operation in the Background</span></span>](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [<span data-ttu-id="777f4-121">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="777f4-121">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
