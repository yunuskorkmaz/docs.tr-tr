---
title: "İzlenecek yol: İlk Dokunmatik Uygulamanızı Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating a touch-sensitive application [WPF]
- touchscreen applications [WPF], creating
- touch-sensitive applications [WPF], creating
- creating a touchscreen application [WPF]
ms.assetid: d69e602e-9a25-4e24-950b-e89eaa2a906b
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 502fb9ae0c488f5f3e438a3ae0a7087538183f1b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-your-first-touch-application"></a><span data-ttu-id="bb81f-102">İzlenecek yol: İlk Dokunmatik Uygulamanızı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bb81f-102">Walkthrough: Creating Your First Touch Application</span></span>
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="bb81f-103">uygulamaları dokunma yanıtlamak için etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="bb81f-103"> enables applications to respond to touch.</span></span> <span data-ttu-id="bb81f-104">Örneğin, birini kullanarak bir uygulama ile etkileşim kurabilir veya dokunmatik aygıtta, bu kılavuzda taşımak kullanıcı sağlayan bir uygulama oluşturur dokunmatik gibi daha fazla parmakları yeniden boyutlandırın veya touch kullanarak tek bir nesneyi döndürme.</span><span class="sxs-lookup"><span data-stu-id="bb81f-104">For example, you can interact with an application by using one or more fingers on a touch-sensitive device, such as a touchscreen This walkthrough creates an application that enables the user to move, resize, or rotate a single object by using touch.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="bb81f-105">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="bb81f-105">Prerequisites</span></span>  
 <span data-ttu-id="bb81f-106">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="bb81f-106">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_ext](../../../../includes/vs-dev10-ext-md.md)]<span data-ttu-id="bb81f-107">.</span><span class="sxs-lookup"><span data-stu-id="bb81f-107">.</span></span>  
  
-   <span data-ttu-id="bb81f-108">Windows 7.</span><span class="sxs-lookup"><span data-stu-id="bb81f-108">Windows 7.</span></span>  
  
-   <span data-ttu-id="bb81f-109">Dokunma kabul eden bir aygıtı Windows Touch destekleyen bir dokunmatik gibi girin.</span><span class="sxs-lookup"><span data-stu-id="bb81f-109">A device that accepts touch input, such as a touchscreen, that supports Windows Touch.</span></span>  
  
 <span data-ttu-id="bb81f-110">Ayrıca, bir uygulama oluşturmak nasıl temel bir anlayış olmalıdır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], abone ve bir olay işlemek özellikle nasıl.</span><span class="sxs-lookup"><span data-stu-id="bb81f-110">Additionally, you should have a basic understanding of how to create an application in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], especially how to subscribe to and handle an event.</span></span> <span data-ttu-id="bb81f-111">Daha fazla bilgi için bkz: [gözden geçirme: ilk WPF Masaüstü Uygulamam](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="bb81f-111">For more information, see [Walkthrough: My first WPF desktop application](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>  
  
## <a name="creating-the-application"></a><span data-ttu-id="bb81f-112">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="bb81f-112">Creating the Application</span></span>  
  
#### <a name="to-create-the-application"></a><span data-ttu-id="bb81f-113">Uygulama oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="bb81f-113">To create the application</span></span>  
  
1.  <span data-ttu-id="bb81f-114">Visual Basic veya Visual C# adlı yeni bir WPF uygulaması projesi oluşturduğunuzda `BasicManipulation`.</span><span class="sxs-lookup"><span data-stu-id="bb81f-114">Create a new WPF Application project in Visual Basic or Visual C# named `BasicManipulation`.</span></span> <span data-ttu-id="bb81f-115">Daha fazla bilgi için bkz: [nasıl yapılır: yeni bir WPF uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span><span class="sxs-lookup"><span data-stu-id="bb81f-115">For more information, see [How to: Create a New WPF Application Project](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span>  
  
2.  <span data-ttu-id="bb81f-116">MainWindow.xaml içeriğini aşağıdaki XAML ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="bb81f-116">Replace the contents of MainWindow.xaml with the following XAML.</span></span>  
  
     <span data-ttu-id="bb81f-117">Kırmızı içeren basit bir uygulama bu biçimlendirme oluşturur <xref:System.Windows.Shapes.Rectangle> üzerinde bir <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="bb81f-117">This markup creates a simple application that contains a red <xref:System.Windows.Shapes.Rectangle> on a <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="bb81f-118"><xref:System.Windows.UIElement.IsManipulationEnabled%2A> Özelliği <xref:System.Windows.Shapes.Rectangle> işleme olayları alacak böylece true olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="bb81f-118">The <xref:System.Windows.UIElement.IsManipulationEnabled%2A> property of the <xref:System.Windows.Shapes.Rectangle> is set to true so that it will receive manipulation events.</span></span> <span data-ttu-id="bb81f-119">Uygulama abone <xref:System.Windows.UIElement.ManipulationStarting>, <xref:System.Windows.UIElement.ManipulationDelta>, ve <xref:System.Windows.UIElement.ManipulationInertiaStarting> olaylar.</span><span class="sxs-lookup"><span data-stu-id="bb81f-119">The application subscribes to the <xref:System.Windows.UIElement.ManipulationStarting>, <xref:System.Windows.UIElement.ManipulationDelta>, and <xref:System.Windows.UIElement.ManipulationInertiaStarting> events.</span></span> <span data-ttu-id="bb81f-120">Bu olaylar taşımak için mantığı içeren <xref:System.Windows.Shapes.Rectangle> zaman kullanıcı yönetir.</span><span class="sxs-lookup"><span data-stu-id="bb81f-120">These events contain the logic to move the <xref:System.Windows.Shapes.Rectangle> when the user manipulates it.</span></span>  
  
     [!code-xaml[BasicManipulation#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml#ui)]  
  
3.  <span data-ttu-id="bb81f-121">Visual Basic, ilk satırındaki kullanıyorsanız yerine `x:Class="BasicManipulation.MainWindow"` ile `x:Class="MainWindow"`.</span><span class="sxs-lookup"><span data-stu-id="bb81f-121">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="BasicManipulation.MainWindow"` with `x:Class="MainWindow"`.</span></span>  
  
4.  <span data-ttu-id="bb81f-122">İçinde `MainWindow` sınıfında, aşağıdaki ekleyin <xref:System.Windows.UIElement.ManipulationStarting> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="bb81f-122">In the `MainWindow` class, add the following <xref:System.Windows.UIElement.ManipulationStarting> event handler.</span></span>  
  
     <span data-ttu-id="bb81f-123"><xref:System.Windows.UIElement.ManipulationStarting> Olaylarının zaman [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dokunma algılar bir nesneyi düzenlemek için giriş başlar.</span><span class="sxs-lookup"><span data-stu-id="bb81f-123">The <xref:System.Windows.UIElement.ManipulationStarting> event occurs when [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] detects that touch input begins to manipulate an object.</span></span> <span data-ttu-id="bb81f-124">Kod düzenleme konumunu göreli olması gerektiğini belirtir <xref:System.Windows.Window> ayarlayarak <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="bb81f-124">The code specifies that the position of the manipulation should be relative to the <xref:System.Windows.Window> by setting the <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> property.</span></span>  
  
     [!code-csharp[BasicManipulation#ManipulationStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationstarting)]
     [!code-vb[BasicManipulation#ManipulationStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationstarting)]  
  
5.  <span data-ttu-id="bb81f-125">İçinde `MainWindow` sınıfında, aşağıdaki ekleyin <xref:System.Windows.Input.ManipulationDelta> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="bb81f-125">In the `MainWindow` class, add the following <xref:System.Windows.Input.ManipulationDelta> event handler.</span></span>  
  
     <span data-ttu-id="bb81f-126"><xref:System.Windows.Input.ManipulationDelta> Olay oluşur dokunma girişi konumu değiştirdiğinde ve birden çok kez yaptığı değişiklik sırasında ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="bb81f-126">The <xref:System.Windows.Input.ManipulationDelta> event occurs when the touch input changes position and can occur multiple times during a manipulation.</span></span> <span data-ttu-id="bb81f-127">Olay, bir parmak kaldırıldıktan sonra da oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="bb81f-127">The event can also occur after a finger is raised.</span></span> <span data-ttu-id="bb81f-128">Örneğin, kullanıcının bir parmak ekran boyunca sürüklediği <xref:System.Windows.Input.ManipulationDelta> olayı parmak hareket ettikçe birden çok kez oluşur.</span><span class="sxs-lookup"><span data-stu-id="bb81f-128">For example, if the user drags a finger across a screen, the <xref:System.Windows.Input.ManipulationDelta> event occurs multiple times as the finger moves.</span></span> <span data-ttu-id="bb81f-129">Kullanıcı bir parmak ekranından başlatır, <xref:System.Windows.Input.ManipulationDelta> olay eylemsizlik benzetimini yapmak için gerçekleşen tutar.</span><span class="sxs-lookup"><span data-stu-id="bb81f-129">When the user raises a finger from the screen, the <xref:System.Windows.Input.ManipulationDelta> event keeps occurring to simulate inertia.</span></span>  
  
     <span data-ttu-id="bb81f-130">Kod uygular <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> için <xref:System.Windows.UIElement.RenderTransform%2A> , <xref:System.Windows.Shapes.Rectangle> taşımak için kullanıcı dokunma taşınırken giriş.</span><span class="sxs-lookup"><span data-stu-id="bb81f-130">The code applies the <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> to the <xref:System.Windows.UIElement.RenderTransform%2A> of the <xref:System.Windows.Shapes.Rectangle> to move it as the user moves the touch input.</span></span> <span data-ttu-id="bb81f-131">Ayrıca denetler olup olmadığını <xref:System.Windows.Shapes.Rectangle> sınırları dışında <xref:System.Windows.Window> olayı sırasında eylemsizlik oluştuğunda.</span><span class="sxs-lookup"><span data-stu-id="bb81f-131">It also checks whether the <xref:System.Windows.Shapes.Rectangle> is outside the bounds of the <xref:System.Windows.Window> when the event occurs during inertia.</span></span> <span data-ttu-id="bb81f-132">Bu nedenle, uygulama çağırırsa <xref:System.Windows.Input.ManipulationDeltaEventArgs.Complete%2A?displayProperty=nameWithType> düzenlemeyi sonlandırmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="bb81f-132">If so, the application calls the <xref:System.Windows.Input.ManipulationDeltaEventArgs.Complete%2A?displayProperty=nameWithType> method to end the manipulation.</span></span>  
  
     [!code-csharp[BasicManipulation#ManipulationDelta](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationdelta)]
     [!code-vb[BasicManipulation#ManipulationDelta](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationdelta)]  
  
6.  <span data-ttu-id="bb81f-133">İçinde `MainWindow` sınıfında, aşağıdaki ekleyin <xref:System.Windows.UIElement.ManipulationInertiaStarting> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="bb81f-133">In the `MainWindow` class, add the following <xref:System.Windows.UIElement.ManipulationInertiaStarting> event handler.</span></span>  
  
     <span data-ttu-id="bb81f-134"><xref:System.Windows.UIElement.ManipulationInertiaStarting> Kullanıcı ekranından tüm parmakları başlatır olay oluşur.</span><span class="sxs-lookup"><span data-stu-id="bb81f-134">The <xref:System.Windows.UIElement.ManipulationInertiaStarting> event occurs when the user raises all fingers from the screen.</span></span> <span data-ttu-id="bb81f-135">Kod ilk hız ve taşıma, genişletme ve dikdörtgen dönüşünü yavaşlama ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bb81f-135">The code sets the initial velocity and deceleration for the movement, expansion, and rotation of the rectangle.</span></span>  
  
     [!code-csharp[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationinertiastarting)]
     [!code-vb[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationinertiastarting)]  
  
7.  <span data-ttu-id="bb81f-136">Oluşturun ve projeyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bb81f-136">Build and run the project.</span></span>  
  
     <span data-ttu-id="bb81f-137">Penceresinde görünür bir kırmızı kare görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bb81f-137">You should see a red square appear in the window.</span></span>  
  
## <a name="testing-the-application"></a><span data-ttu-id="bb81f-138">Uygulamayı Test Etme</span><span class="sxs-lookup"><span data-stu-id="bb81f-138">Testing the Application</span></span>  
 <span data-ttu-id="bb81f-139">Uygulamayı test etmek için aşağıdaki düzenlemeleri deneyin.</span><span class="sxs-lookup"><span data-stu-id="bb81f-139">To test the application, try the following manipulations.</span></span> <span data-ttu-id="bb81f-140">Aşağıdaki aynı anda birden çok işlemi gerçekleştirebileceğinizi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bb81f-140">Note that you can do more than one of the following at the same time.</span></span>  
  
-   <span data-ttu-id="bb81f-141">Taşımak için <xref:System.Windows.Shapes.Rectangle>, bir parmak yerleştirin <xref:System.Windows.Shapes.Rectangle> ve parmak ekranda hareket ettirin.</span><span class="sxs-lookup"><span data-stu-id="bb81f-141">To move the <xref:System.Windows.Shapes.Rectangle>, put a finger on the <xref:System.Windows.Shapes.Rectangle> and move the finger across the screen.</span></span>  
  
-   <span data-ttu-id="bb81f-142">Yeniden boyutlandırmak için <xref:System.Windows.Shapes.Rectangle>, iki parmakları yerleştirin <xref:System.Windows.Shapes.Rectangle> ve parmakları yakın birlikte veya birbirlerinden uzağına taşıyın.</span><span class="sxs-lookup"><span data-stu-id="bb81f-142">To resize the <xref:System.Windows.Shapes.Rectangle>, put two fingers on the <xref:System.Windows.Shapes.Rectangle> and move the fingers closer together or farther apart from each other.</span></span>  
  
-   <span data-ttu-id="bb81f-143">Döndürmek için <xref:System.Windows.Shapes.Rectangle>, iki parmakları yerleştirin <xref:System.Windows.Shapes.Rectangle> ve parmakları birbiri etrafında döndürün.</span><span class="sxs-lookup"><span data-stu-id="bb81f-143">To rotate the <xref:System.Windows.Shapes.Rectangle>, put two fingers on the <xref:System.Windows.Shapes.Rectangle> and rotate the fingers around each other.</span></span>  
  
 <span data-ttu-id="bb81f-144">Eylemsizlik neden olmak için önceki işlemeleri gerçekleştirme gibi parmakları ekranından hızlı bir şekilde yükseltin.</span><span class="sxs-lookup"><span data-stu-id="bb81f-144">To cause inertia, quickly raise your fingers from the screen as you perform the previous manipulations.</span></span> <span data-ttu-id="bb81f-145"><xref:System.Windows.Shapes.Rectangle> Taşımak, yeniden boyutlandırmak veya durdurulmadan önce birkaç saniye boyunca devam eder.</span><span class="sxs-lookup"><span data-stu-id="bb81f-145">The <xref:System.Windows.Shapes.Rectangle> will continue to move, resize, or rotate for a few seconds before it stops.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb81f-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bb81f-146">See Also</span></span>  
 <xref:System.Windows.UIElement.ManipulationStarting?displayProperty=nameWithType>  
 <xref:System.Windows.UIElement.ManipulationDelta?displayProperty=nameWithType>  
 <xref:System.Windows.UIElement.ManipulationInertiaStarting?displayProperty=nameWithType>
