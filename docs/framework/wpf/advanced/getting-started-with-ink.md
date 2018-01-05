---
title: "Mürekkep ile Çalışmaya Başlama"
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
- procedural code in lieu of XAML [WPF]
- gradient brush [WPF], animating colors of
- XAML [WPF], procedural code in lieu of
- animation [WPF], gradient brush colors
- brushes [WPF], animating colors of
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c977e8a4a23f9739541cf28d9e34ad9e8db1daf0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-with-ink"></a><span data-ttu-id="22f74-102">Mürekkep ile Çalışmaya Başlama</span><span class="sxs-lookup"><span data-stu-id="22f74-102">Getting Started with Ink</span></span>
<span data-ttu-id="22f74-103">Dijital Mürekkep uygulamalarınıza her zamankinden daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="22f74-103">Incorporating digital ink into your applications is easier than ever.</span></span> <span data-ttu-id="22f74-104">Mürekkep gelişen corollary içinde tam tümleştirmeyi programlamayı COM ve Windows Forms yöntemine olmaktan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="22f74-104">Ink has evolved from being a corollary to the COM and Windows Forms method of programming to achieving full integration into the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="22f74-105">Ayrı SDK veya çalışma zamanı kitaplıkları yüklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="22f74-105">You do not need to install separate SDKs or runtime libraries.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="22f74-106">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="22f74-106">Prerequisites</span></span>  
 <span data-ttu-id="22f74-107">Aşağıdaki örnekler kullanmak için önce Microsoft Visual Studio 2005 yüklemeniz gerekir ve [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)].</span><span class="sxs-lookup"><span data-stu-id="22f74-107">To use the following examples, you must first install Microsoft Visual Studio 2005 and the [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)].</span></span> <span data-ttu-id="22f74-108">Uygulamaları yazmak nasıl anlamanız gerekir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="22f74-108">You should also understand how to write applications for the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="22f74-109">İle çalışmaya başlama hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bkz: [gözden geçirme: ilk WPF Masaüstü Uygulamam](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="22f74-109">For more information about getting started with the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], see [Walkthrough: My first WPF desktop application](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>  
  
## <a name="quick-start"></a><span data-ttu-id="22f74-110">Hızlı Başlangıç</span><span class="sxs-lookup"><span data-stu-id="22f74-110">Quick Start</span></span>  
 <span data-ttu-id="22f74-111">Bu bölüm, basit bir yazmanıza yardımcı olur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Mürekkep toplayan uygulama.</span><span class="sxs-lookup"><span data-stu-id="22f74-111">This section helps you write a simple [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application that collects ink.</span></span>  
  
 <span data-ttu-id="22f74-112">Zaten yapmadıysanız, Microsoft Visual Studio 2005 yükleyin ve [!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)].</span><span class="sxs-lookup"><span data-stu-id="22f74-112">If you haven't already done so, install Microsoft Visual Studio 2005 and the [!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)].</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="22f74-113">uygulamalar genellikle derlenmelidir bunları görüntüleyebilmeniz bunlar tamamen oluşur olsa bile [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="22f74-113"> applications usually must be compiled before you can view them, even if they consist entirely of [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="22f74-114">Ancak, [!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)] uygulama hızlandırmak için tasarlanmış bir uygulama olan, XamlPad'i içeren bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]-UI tabanlı.</span><span class="sxs-lookup"><span data-stu-id="22f74-114">However, the [!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)] includes an application, XamlPad, designed to speed up the process of implementing a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]-based UI.</span></span> <span data-ttu-id="22f74-115">Bu uygulamayı görüntülemek ve bu belgedeki ilk birkaç örneği ile tamir etmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22f74-115">You can use that application to view and tinker with the first few samples in this document.</span></span> <span data-ttu-id="22f74-116">Oluşturma işlemi derlenmiş uygulamalardan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bu belgenin sonraki bölümlerinde ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="22f74-116">The process of creating compiled applications from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] is covered later in this document.</span></span>  
  
 <span data-ttu-id="22f74-117">XamlPad'i başlatmak için tıklatın **Başlat** menüsündeki **tüm programlar**, işaret **Microsoft Winndows SDK**, işaret **Araçları**ve'ı tıklatın **XAMLPad**.</span><span class="sxs-lookup"><span data-stu-id="22f74-117">To launch XAMLPad, click the **Start** menu, point to **All Programs**, point to **Microsoft Winndows SDK**, point to **Tools**, and click **XAMLPad**.</span></span> <span data-ttu-id="22f74-118">İşleme bölmesinde XAMLPad kod bölmesinde yazılan XAML kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="22f74-118">In the rendering pane, XAMLPad renders the XAML code written in the code pane.</span></span> <span data-ttu-id="22f74-119">XAML kodunu düzenleyebilirsiniz ve değişiklikler hemen işleme bölmesinde görünür.</span><span class="sxs-lookup"><span data-stu-id="22f74-119">You can edit the XAML code, and the changes immediately appear in the rendering pane.</span></span>  
  
#### <a name="got-ink"></a><span data-ttu-id="22f74-120">Mürekkep var mı?</span><span class="sxs-lookup"><span data-stu-id="22f74-120">Got Ink?</span></span>  
 <span data-ttu-id="22f74-121">İlk başlatmak için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Mürekkep destekleyen uygulama:</span><span class="sxs-lookup"><span data-stu-id="22f74-121">To start your first [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application that supports ink:</span></span>  
  
1.  <span data-ttu-id="22f74-122">Microsoft Visual Studio 2005 açın</span><span class="sxs-lookup"><span data-stu-id="22f74-122">Open Microsoft Visual Studio 2005</span></span>  
  
2.  <span data-ttu-id="22f74-123">Yeni bir **Windows uygulaması (WPF)**</span><span class="sxs-lookup"><span data-stu-id="22f74-123">Create a new **Windows Application (WPF)**</span></span>  
  
3.  <span data-ttu-id="22f74-124">Tür `<InkCanvas/>` arasında `<Grid>` etiketleri</span><span class="sxs-lookup"><span data-stu-id="22f74-124">Type `<InkCanvas/>` between the `<Grid>` tags</span></span>  
  
4.  <span data-ttu-id="22f74-125">Tuşuna **F5** hata ayıklayıcı uygulamanızda başlatmak için</span><span class="sxs-lookup"><span data-stu-id="22f74-125">Press **F5** to launch your application in the debugger</span></span>  
  
5.  <span data-ttu-id="22f74-126">Kalem veya fare kullanarak yazma **Merhaba Dünya** penceresinde</span><span class="sxs-lookup"><span data-stu-id="22f74-126">Using a stylus or mouse, write **hello world** in the window</span></span>  
  
 <span data-ttu-id="22f74-127">"Hello world" uygulama yalnızca 12 tuş mürekkep denk yazdıktan!</span><span class="sxs-lookup"><span data-stu-id="22f74-127">You've written the ink equivalent of a "hello world" application with only 12 keystrokes!</span></span>  
  
#### <a name="spice-up-your-application"></a><span data-ttu-id="22f74-128">Uygulamanızı renklendirin</span><span class="sxs-lookup"><span data-stu-id="22f74-128">Spice Up Your Application</span></span>  
 <span data-ttu-id="22f74-129">Bazı özellikleri avantajlarından atalım [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="22f74-129">Let’s take advantage of some features of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span>  <span data-ttu-id="22f74-130">Açılış arasındaki her şeyi değiştirin \<penceresi > ve kapatma \</Window > gradyan fırçası arka plan içindekine yüzeyinizi almak için aşağıdaki biçimlendirme etiketleriyle.</span><span class="sxs-lookup"><span data-stu-id="22f74-130">Replace everything between the opening \<Window> and closing \</Window> tags with the following markup to get a gradient brush background on your inking surface.</span></span>  
  
 [!code-xaml[DigitalInkTopics#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#1)]  
[!code-xaml[DigitalInkTopics#1a](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#1a)]  
  
#### <a name="using-animation"></a><span data-ttu-id="22f74-131">Animasyon kullanma</span><span class="sxs-lookup"><span data-stu-id="22f74-131">Using Animation</span></span>  
 <span data-ttu-id="22f74-132">Fun için gradyan fırçası renkleri şimdi animasyon.</span><span class="sxs-lookup"><span data-stu-id="22f74-132">For fun, let's animate the colors of the gradient brush.</span></span> <span data-ttu-id="22f74-133">Aşağıdakileri ekleyin [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kapatma sonra `</InkCanvas>` etiketi ancak kapatmadan önce `</Page>` etiketi.</span><span class="sxs-lookup"><span data-stu-id="22f74-133">Add the following [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] after the closing `</InkCanvas>` tag but before the closing `</Page>` tag.</span></span>  
  
 [!code-xaml[DigitalInkTopics#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#2)]  
  
#### <a name="adding-some-code-behind-the-xaml"></a><span data-ttu-id="22f74-134">XAML arkasına bazı kod ekleme</span><span class="sxs-lookup"><span data-stu-id="22f74-134">Adding Some Code Behind the XAML</span></span>  
 <span data-ttu-id="22f74-135">XAML kullanıcı arabirimi tasarlamak çok kolay olmasını sağlarken olayları işlemek üzere kod eklemek herhangi bir gerçek uygulama gerekir.</span><span class="sxs-lookup"><span data-stu-id="22f74-135">While XAML makes it very easy to design the user interface, any real-world application needs to add code to handle events.</span></span> <span data-ttu-id="22f74-136">Fare gelen yanıt sağ tıklatma olarak mürekkep yakınlaştırır basit bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="22f74-136">Here is a simple example that zooms in on the ink in response to a right-click from a mouse:</span></span>  
  
 <span data-ttu-id="22f74-137">Ayarlama `MouseRightButtonUp` işleyicisinde, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="22f74-137">Set the `MouseRightButtonUp` handler in your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]:</span></span>  
  
 [!code-xaml[DigitalInkTopics#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]  
  
 <span data-ttu-id="22f74-138">Visual Studio'nun Çözüm Gezgini'nde, Windows1.XAML'i genişletin ve arka plan kod dosyası, Window1.xaml.cs veya Visual Basic kullanıyorsanız Window1.xaml.vb'yi açın.</span><span class="sxs-lookup"><span data-stu-id="22f74-138">In Visual Studio’s Solution Explorer, expand Windows1.xaml and open the code-behind file, Window1.xaml.cs or Window1.xaml.vb if you are using Visual Basic.</span></span> <span data-ttu-id="22f74-139">Aşağıdaki olay işleyici kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="22f74-139">Add the following event handler code:</span></span>  
  
 [!code-csharp[DigitalInkTopics#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
 [!code-vb[DigitalInkTopics#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]  
  
 <span data-ttu-id="22f74-140">Artık, uygulamanızı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="22f74-140">Now, run your application.</span></span> <span data-ttu-id="22f74-141">Bazı mürekkep ekleyin ve ardından fareyle sağ tıklayın veya ve tutma eşdeğer kalem ile gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="22f74-141">Add some ink and then right-click with the mouse or perform a press-and-hold equivalent with a stylus.</span></span>  
  
#### <a name="using-procedural-code-instead-of-xaml"></a><span data-ttu-id="22f74-142">XAML yerine yordam kodu kullanma</span><span class="sxs-lookup"><span data-stu-id="22f74-142">Using Procedural Code Instead of XAML</span></span>  
 <span data-ttu-id="22f74-143">Tüm erişebilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özelliklerine yordamsal koddan.</span><span class="sxs-lookup"><span data-stu-id="22f74-143">You can access all [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] features from procedural code.</span></span> <span data-ttu-id="22f74-144">"Hello mürekkep World" uygulaması için işte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] herhangi kullanmayan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] hiç.</span><span class="sxs-lookup"><span data-stu-id="22f74-144">Here is a "Hello Ink World" application for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] that doesn’t use any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] at all.</span></span> <span data-ttu-id="22f74-145">Visual Studio'da boş bir konsol uygulamasına aşağıdaki kodu yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="22f74-145">Paste the code below into an empty Console Application in Visual Studio.</span></span> <span data-ttu-id="22f74-146">PresentationCore, PresentationFramework ve WindowsBase derlemelerine başvurular ekleyin ve tuşlarına basarak uygulamayı derlediğinizde **F5**:</span><span class="sxs-lookup"><span data-stu-id="22f74-146">Add references to the PresentationCore, PresentationFramework, and WindowsBase assemblies, and build the application by pressing **F5**:</span></span>  
  
 [!code-csharp[InkCanvasConsoleApp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
 [!code-vb[InkCanvasConsoleApp#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="22f74-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="22f74-147">See Also</span></span>  
 [<span data-ttu-id="22f74-148">Dijital Mürekkep</span><span class="sxs-lookup"><span data-stu-id="22f74-148">Digital Ink</span></span>](../../../../docs/framework/wpf/advanced/digital-ink.md)  
 [<span data-ttu-id="22f74-149">Mürekkep Toplama</span><span class="sxs-lookup"><span data-stu-id="22f74-149">Collecting Ink</span></span>](../../../../docs/framework/wpf/advanced/collecting-ink.md)  
 [<span data-ttu-id="22f74-150">El Yazısı Tanıma</span><span class="sxs-lookup"><span data-stu-id="22f74-150">Handwriting Recognition</span></span>](../../../../docs/framework/wpf/advanced/handwriting-recognition.md)  
 [<span data-ttu-id="22f74-151">Mürekkep Depolama</span><span class="sxs-lookup"><span data-stu-id="22f74-151">Storing Ink</span></span>](../../../../docs/framework/wpf/advanced/storing-ink.md)
