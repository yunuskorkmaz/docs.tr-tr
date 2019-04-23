---
title: Bir InkCanvas Visual Studio'da WPF uygulaması oluşturma
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- procedural code in lieu of XAML [WPF]
- XAML [WPF], procedural code in lieu of
- InkCanvas (WPF)
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
ms.openlocfilehash: 4309b1108b2ea96eb298ff3bb876a0f63b80dc32
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59343603"
---
# <a name="get-started-with-ink-in-wpf"></a><span data-ttu-id="5989d-102">WPF mürekkep ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="5989d-102">Get Started with Ink in WPF</span></span>

<span data-ttu-id="5989d-103">Windows Presentation Foundation (WPF), dijital mürekkep uygulamanıza eklemenizi kolaylaştırır bir mürekkep özelliği vardır.</span><span class="sxs-lookup"><span data-stu-id="5989d-103">Windows Presentation Foundation (WPF) has an ink feature that makes it easy to incorporate digital ink into your app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5989d-104">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="5989d-104">Prerequisites</span></span>

<span data-ttu-id="5989d-105">Aşağıdaki örnekleri kullanmak için önce yükleme [Microsoft Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="5989d-105">To use the following examples, first install [Microsoft Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019).</span></span> <span data-ttu-id="5989d-106">Ayrıca temel WPF uygulamaları yazmak nasıl yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="5989d-106">It also helps to know how to write basic WPF apps.</span></span> <span data-ttu-id="5989d-107">WPF ile çalışmaya başlama konusunda yardım için bkz. [izlenecek yol: İlk WPF Masaüstü Uygulamam](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="5989d-107">For help getting started with WPF, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

## <a name="quick-start"></a><span data-ttu-id="5989d-108">Hızlı Başlangıç</span><span class="sxs-lookup"><span data-stu-id="5989d-108">Quick Start</span></span>

<span data-ttu-id="5989d-109">Bu bölümde Mürekkep toplayan Basit WPF uygulaması yazmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="5989d-109">This section helps you write a simple WPF application that collects ink.</span></span>

### <a name="got-ink"></a><span data-ttu-id="5989d-110">Mürekkep var mı?</span><span class="sxs-lookup"><span data-stu-id="5989d-110">Got Ink?</span></span>

<span data-ttu-id="5989d-111">Mürekkep destekleyen bir WPF uygulaması oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="5989d-111">To create a WPF app that supports ink:</span></span>

1. <span data-ttu-id="5989d-112">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="5989d-112">Open Visual Studio.</span></span>

2. <span data-ttu-id="5989d-113">Yeni bir **WPF uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="5989d-113">Create a new **WPF App**.</span></span>

   <span data-ttu-id="5989d-114">İçinde **yeni proje** iletişim kutusunda Genişlet **yüklü** > **Visual C#** veya **Visual Basic**  >   **Windows Masaüstü** kategorisi.</span><span class="sxs-lookup"><span data-stu-id="5989d-114">In the **New Project** dialog, expand the **Installed** > **Visual C#** or **Visual Basic** > **Windows Desktop** category.</span></span> <span data-ttu-id="5989d-115">Ardından, **WPF uygulaması (.NET Framework)** uygulaması şablonu.</span><span class="sxs-lookup"><span data-stu-id="5989d-115">Then, select the **WPF App (.NET Framework)** app template.</span></span> <span data-ttu-id="5989d-116">Bir ad girin ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="5989d-116">Enter a name, and then select **OK**.</span></span>

   <span data-ttu-id="5989d-117">Visual Studio projesi oluşturur ve *MainWindow.xaml* Tasarımcısı'nda açılır.</span><span class="sxs-lookup"><span data-stu-id="5989d-117">Visual Studio creates the project, and *MainWindow.xaml* opens in the designer.</span></span>

3. <span data-ttu-id="5989d-118">Tür `<InkCanvas/>` arasında `<Grid>` etiketler.</span><span class="sxs-lookup"><span data-stu-id="5989d-118">Type `<InkCanvas/>` between the `<Grid>` tags.</span></span>

   ![InkCanvas etiketi ile XAML Tasarımcısı](./media/getting-started-with-ink/inkcanvas-xaml.png)

4. <span data-ttu-id="5989d-120">Tuşuna **F5** uygulamanızda hata ayıklayıcıyı başlatmak için.</span><span class="sxs-lookup"><span data-stu-id="5989d-120">Press **F5** to launch your application in the debugger.</span></span>

5. <span data-ttu-id="5989d-121">Ekran kalemi veya fare kullanarak yazma **Merhaba Dünya** penceresinde.</span><span class="sxs-lookup"><span data-stu-id="5989d-121">Using a stylus or mouse, write **hello world** in the window.</span></span>

<span data-ttu-id="5989d-122">Bir "hello world" uygulaması yalnızca 12 tuş mürekkep denk yazdığınız!</span><span class="sxs-lookup"><span data-stu-id="5989d-122">You've written the ink equivalent of a "hello world" application with only 12 keystrokes!</span></span>

### <a name="spice-up-your-app"></a><span data-ttu-id="5989d-123">Uygulamanızı renklendirin</span><span class="sxs-lookup"><span data-stu-id="5989d-123">Spice Up Your App</span></span>

<span data-ttu-id="5989d-124">Bazı WPF özelliklerinden ele alalım.</span><span class="sxs-lookup"><span data-stu-id="5989d-124">Let’s take advantage of some features of the WPF.</span></span> <span data-ttu-id="5989d-125">Her şey açılış ve kapanış arasında Değiştir \<penceresi > aşağıdaki işaretlemeyle etiketler:</span><span class="sxs-lookup"><span data-stu-id="5989d-125">Replace everything between the opening and closing \<Window> tags with the following markup:</span></span>

```xaml
<Page>
  <InkCanvas Name="myInkCanvas" MouseRightButtonUp="RightMouseUpHandler">
    <InkCanvas.Background>
      <LinearGradientBrush>
        <GradientStop Color="Yellow" Offset="0.0" />
          <GradientStop Color="Blue" Offset="0.5" />
            <GradientStop Color="HotPink" Offset="1.0" />
              </LinearGradientBrush>
    </InkCanvas.Background>
  </InkCanvas>
</Page>
```

<span data-ttu-id="5989d-126">Bu XAML arka plan gradyan fırçası Mürekkep yüzeyiniz oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5989d-126">This XAML creates a gradient brush background on your inking surface.</span></span>

![WPF uygulaması yüzeyini mürekkep üzerinde Gradyan renklerini](./media/getting-started-with-ink/gradient-colors.png)

### <a name="add-some-code-behind-the-xaml"></a><span data-ttu-id="5989d-128">XAML arkasındaki kod ekleyin</span><span class="sxs-lookup"><span data-stu-id="5989d-128">Add Some Code Behind the XAML</span></span>

<span data-ttu-id="5989d-129">XAML kullanıcı arabirimi tasarlamak çok kolay hale karşın, olayları işlemek üzere kod eklemek herhangi bir gerçek yaşam uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5989d-129">While XAML makes it very easy to design the user interface, any real-world application needs to add code to handle events.</span></span> <span data-ttu-id="5989d-130">Yanıtta bir sağ tıklama fare tarafından mürekkep yakınlaştırır basit bir örnek aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5989d-130">Here is a simple example that zooms in on the ink in response to a right-click from a mouse.</span></span>

1. <span data-ttu-id="5989d-131">Ayarlama `MouseRightButtonUp` , XAML işleyicisinde:</span><span class="sxs-lookup"><span data-stu-id="5989d-131">Set the `MouseRightButtonUp` handler in your XAML:</span></span>

   [!code-xaml[DigitalInkTopics#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]

1. <span data-ttu-id="5989d-132">İçinde **Çözüm Gezgini**MainWindow.XAML'yi genişletin ve (MainWindow.xaml.cs veya MainWindow.xaml.vb) arka plan kod dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="5989d-132">In **Solution Explorer**, expand MainWindow.xaml and open the code-behind file (MainWindow.xaml.cs or MainWindow.xaml.vb).</span></span> <span data-ttu-id="5989d-133">Aşağıdaki olay işleyicisini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5989d-133">Add the following event handler code:</span></span>

   [!code-csharp[DigitalInkTopics#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
   [!code-vb[DigitalInkTopics#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]

1. <span data-ttu-id="5989d-134">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5989d-134">Run the application.</span></span> <span data-ttu-id="5989d-135">Bazı mürekkep ekleyebilir ve ardından fareyle sağ tıklayın ya da tuşuna basın ve basılı eşdeğer bir ekran kalemi ile gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="5989d-135">Add some ink, and then right-click with the mouse or perform a press-and-hold equivalent with a stylus.</span></span>

   <span data-ttu-id="5989d-136">Farenin sağ düğmesiyle tıklatın her zaman görünümü yakınlaştırır.</span><span class="sxs-lookup"><span data-stu-id="5989d-136">The display zooms in each time you click with the right mouse button.</span></span>

### <a name="use-procedural-code-instead-of-xaml"></a><span data-ttu-id="5989d-137">XAML yerine yordam kodu kullanın</span><span class="sxs-lookup"><span data-stu-id="5989d-137">Use Procedural Code Instead of XAML</span></span>

<span data-ttu-id="5989d-138">Yordam kodundan tüm WPF özelliklerine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5989d-138">You can access all WPF features from procedural code.</span></span> <span data-ttu-id="5989d-139">Tüm XAML kullanmayan WPF için bir "Hello mürekkep World" uygulaması oluşturmak için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="5989d-139">Follow these steps to create a "Hello Ink World" application for WPF that doesn’t use any XAML at all.</span></span>

1. <span data-ttu-id="5989d-140">Visual Studio'da yeni bir konsol uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5989d-140">Create a new console application project in Visual Studio.</span></span>

   <span data-ttu-id="5989d-141">İçinde **yeni proje** iletişim kutusunda Genişlet **yüklü** > **Visual C#** veya **Visual Basic**  >   **Windows Masaüstü** kategorisi.</span><span class="sxs-lookup"><span data-stu-id="5989d-141">In the **New Project** dialog, expand the **Installed** > **Visual C#** or **Visual Basic** > **Windows Desktop** category.</span></span> <span data-ttu-id="5989d-142">Ardından, **konsol uygulaması (.NET Framework)** uygulaması şablonu.</span><span class="sxs-lookup"><span data-stu-id="5989d-142">Then, select the **Console App (.NET Framework)** app template.</span></span> <span data-ttu-id="5989d-143">Bir ad girin ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="5989d-143">Enter a name, and then select **OK**.</span></span>

1. <span data-ttu-id="5989d-144">Program.cs veya Program.vb dosyaya aşağıdaki kodu yapıştırın:</span><span class="sxs-lookup"><span data-stu-id="5989d-144">Paste the following code into the Program.cs or Program.vb file:</span></span>

   [!code-csharp[InkCanvasConsoleApp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
   [!code-vb[InkCanvasConsoleApp#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]

1. <span data-ttu-id="5989d-145">Sağ tıklayarak PresentationCore PresentationFramework ve WindowsBase derlemelere başvurular ekleyin **başvuruları** içinde **Çözüm Gezgini** seçip **BaşvuruEkle**.</span><span class="sxs-lookup"><span data-stu-id="5989d-145">Add references to the PresentationCore, PresentationFramework, and WindowsBase assemblies by right-clicking on **References** in **Solution Explorer** and choosing **Add Reference**.</span></span>

   ![Başvuru Yöneticisi PresentationCore ve PresentationFramework gösteriliyor](./media/getting-started-with-ink/references.png)

1. <span data-ttu-id="5989d-147">Tuşlarına basarak uygulamayı derleyin **F5**.</span><span class="sxs-lookup"><span data-stu-id="5989d-147">Build the application by pressing **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="5989d-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5989d-148">See also</span></span>

- [<span data-ttu-id="5989d-149">Dijital Mürekkep</span><span class="sxs-lookup"><span data-stu-id="5989d-149">Digital Ink</span></span>](digital-ink.md)
- [<span data-ttu-id="5989d-150">Mürekkep Toplama</span><span class="sxs-lookup"><span data-stu-id="5989d-150">Collecting Ink</span></span>](collecting-ink.md)
- [<span data-ttu-id="5989d-151">El Yazısı Tanıma</span><span class="sxs-lookup"><span data-stu-id="5989d-151">Handwriting Recognition</span></span>](handwriting-recognition.md)
- [<span data-ttu-id="5989d-152">Mürekkep Depolama</span><span class="sxs-lookup"><span data-stu-id="5989d-152">Storing Ink</span></span>](storing-ink.md)
