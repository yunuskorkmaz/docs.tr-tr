---
title: Visual Studio 'da WPF uygulamasında bir InkCanvas oluşturma
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- procedural code in lieu of XAML [WPF]
- XAML [WPF], procedural code in lieu of
- InkCanvas (WPF)
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
ms.openlocfilehash: ebbf25037921e7802b2bfcb6ffa562d16a849ffa
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920245"
---
# <a name="get-started-with-ink-in-wpf"></a><span data-ttu-id="e4e6c-102">WPF 'de mürekkeple çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="e4e6c-102">Get Started with Ink in WPF</span></span>

<span data-ttu-id="e4e6c-103">Windows Presentation Foundation (WPF), uygulamanıza dijital mürekkep eklemenizi kolaylaştıran bir mürekkep özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e4e6c-103">Windows Presentation Foundation (WPF) has an ink feature that makes it easy to incorporate digital ink into your app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e4e6c-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="e4e6c-104">Prerequisites</span></span>

<span data-ttu-id="e4e6c-105">Aşağıdaki örnekleri kullanmak için, önce [Visual Studio 'yu](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e4e6c-105">To use the following examples, first install [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019).</span></span> <span data-ttu-id="e4e6c-106">Ayrıca, temel WPF uygulamalarının nasıl yazılacağını öğrenmenize de yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="e4e6c-106">It also helps to know how to write basic WPF apps.</span></span> <span data-ttu-id="e4e6c-107">WPF kullanmaya başlarken yardım için bkz. [Izlenecek yol: Ilk WPF Masaüstü](../getting-started/walkthrough-my-first-wpf-desktop-application.md)Uygulamam.</span><span class="sxs-lookup"><span data-stu-id="e4e6c-107">For help getting started with WPF, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

## <a name="quick-start"></a><span data-ttu-id="e4e6c-108">hızlı başlangıç</span><span class="sxs-lookup"><span data-stu-id="e4e6c-108">Quick Start</span></span>

<span data-ttu-id="e4e6c-109">Bu bölüm, mürekkep toplayan basit bir WPF uygulaması yazmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="e4e6c-109">This section helps you write a simple WPF application that collects ink.</span></span>

### <a name="got-ink"></a><span data-ttu-id="e4e6c-110">Mürekkep mi var?</span><span class="sxs-lookup"><span data-stu-id="e4e6c-110">Got Ink?</span></span>

<span data-ttu-id="e4e6c-111">Mürekkebi destekleyen bir WPF uygulaması oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="e4e6c-111">To create a WPF app that supports ink:</span></span>

1. <span data-ttu-id="e4e6c-112">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="e4e6c-112">Open Visual Studio.</span></span>

2. <span data-ttu-id="e4e6c-113">Yeni bir **WPF uygulaması**oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e4e6c-113">Create a new **WPF App**.</span></span>

   <span data-ttu-id="e4e6c-114">**Yeni proje** iletişim kutusunda, **yüklü** > **Visual C#**  veya **Visual Basic** > **Windows Masaüstü** kategorisini genişletin.</span><span class="sxs-lookup"><span data-stu-id="e4e6c-114">In the **New Project** dialog, expand the **Installed** > **Visual C#** or **Visual Basic** > **Windows Desktop** category.</span></span> <span data-ttu-id="e4e6c-115">Ardından, **WPF uygulaması (.NET Framework)** uygulama şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="e4e6c-115">Then, select the **WPF App (.NET Framework)** app template.</span></span> <span data-ttu-id="e4e6c-116">Bir ad girin ve **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="e4e6c-116">Enter a name, and then select **OK**.</span></span>

   <span data-ttu-id="e4e6c-117">Visual Studio projeyi oluşturur ve *MainWindow. xaml* tasarımcıda açılır.</span><span class="sxs-lookup"><span data-stu-id="e4e6c-117">Visual Studio creates the project, and *MainWindow.xaml* opens in the designer.</span></span>

3. <span data-ttu-id="e4e6c-118">`<Grid>` etiketleri arasına `<InkCanvas/>` yazın.</span><span class="sxs-lookup"><span data-stu-id="e4e6c-118">Type `<InkCanvas/>` between the `<Grid>` tags.</span></span>

   ![InkCanvas etiketiyle XAML Tasarımcısı](./media/getting-started-with-ink/inkcanvas-xaml.png)

4. <span data-ttu-id="e4e6c-120">Uygulamanızı hata ayıklayıcıda başlatmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e4e6c-120">Press **F5** to launch your application in the debugger.</span></span>

5. <span data-ttu-id="e4e6c-121">Ekran kalemi veya fare kullanarak pencerede **Merhaba Dünya** yazın.</span><span class="sxs-lookup"><span data-stu-id="e4e6c-121">Using a stylus or mouse, write **hello world** in the window.</span></span>

<span data-ttu-id="e4e6c-122">Bir "Hello World" uygulamasının mürekkep eşdeğerini yalnızca 12 tuş vuruşu ile yazmış oldunuz!</span><span class="sxs-lookup"><span data-stu-id="e4e6c-122">You've written the ink equivalent of a "hello world" application with only 12 keystrokes!</span></span>

### <a name="spice-up-your-app"></a><span data-ttu-id="e4e6c-123">Uygulamanızı artırma</span><span class="sxs-lookup"><span data-stu-id="e4e6c-123">Spice Up Your App</span></span>

<span data-ttu-id="e4e6c-124">WPF 'nin bazı özelliklerinden faydalanalım.</span><span class="sxs-lookup"><span data-stu-id="e4e6c-124">Let’s take advantage of some features of the WPF.</span></span> <span data-ttu-id="e4e6c-125">Açma ve kapatma \<pencere > etiketleri arasındaki her şeyi aşağıdaki biçimlendirme ile değiştirin:</span><span class="sxs-lookup"><span data-stu-id="e4e6c-125">Replace everything between the opening and closing \<Window> tags with the following markup:</span></span>

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

<span data-ttu-id="e4e6c-126">Bu XAML, mürekkep yüzeyiniz üzerinde bir gradyan fırçası arka planı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e4e6c-126">This XAML creates a gradient brush background on your inking surface.</span></span>

![WPF uygulamasında mürekkep yüzeyinde gradyan renkler](./media/getting-started-with-ink/gradient-colors.png)

### <a name="add-some-code-behind-the-xaml"></a><span data-ttu-id="e4e6c-128">XAML 'nin arkasında kod ekleme</span><span class="sxs-lookup"><span data-stu-id="e4e6c-128">Add Some Code Behind the XAML</span></span>

<span data-ttu-id="e4e6c-129">XAML Kullanıcı arabirimini tasarlamayı çok kolay hale getirir, ancak herhangi bir gerçek dünya uygulamasının olayları işlemek için kod eklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e4e6c-129">While XAML makes it very easy to design the user interface, any real-world application needs to add code to handle events.</span></span> <span data-ttu-id="e4e6c-130">Bir farede sağ tıklaa yanıt olarak mürekkebe yakınlaşarak bir basit örnek aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e4e6c-130">Here is a simple example that zooms in on the ink in response to a right-click from a mouse.</span></span>

1. <span data-ttu-id="e4e6c-131">XAML 'de `MouseRightButtonUp` işleyicisini ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="e4e6c-131">Set the `MouseRightButtonUp` handler in your XAML:</span></span>

   [!code-xaml[DigitalInkTopics#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]

1. <span data-ttu-id="e4e6c-132">**Çözüm Gezgini**, MainWindow. xaml ' i genişletin ve arka plan kod dosyasını (MainWindow.xaml.cs veya MainWindow. xaml. vb) açın.</span><span class="sxs-lookup"><span data-stu-id="e4e6c-132">In **Solution Explorer**, expand MainWindow.xaml and open the code-behind file (MainWindow.xaml.cs or MainWindow.xaml.vb).</span></span> <span data-ttu-id="e4e6c-133">Aşağıdaki olay işleyici kodunu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e4e6c-133">Add the following event handler code:</span></span>

   [!code-csharp[DigitalInkTopics#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
   [!code-vb[DigitalInkTopics#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]

1. <span data-ttu-id="e4e6c-134">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e4e6c-134">Run the application.</span></span> <span data-ttu-id="e4e6c-135">Biraz mürekkep ekleyin ve fareyle sağ tıklayın veya ekran kalemiyle bir basma ve bekletme eşdeğeri gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="e4e6c-135">Add some ink, and then right-click with the mouse or perform a press-and-hold equivalent with a stylus.</span></span>

   <span data-ttu-id="e4e6c-136">Ekran, sağ fare düğmesine her tıkladığınızda yakınlaştırılır.</span><span class="sxs-lookup"><span data-stu-id="e4e6c-136">The display zooms in each time you click with the right mouse button.</span></span>

### <a name="use-procedural-code-instead-of-xaml"></a><span data-ttu-id="e4e6c-137">XAML yerine yordamsal kodu kullanın</span><span class="sxs-lookup"><span data-stu-id="e4e6c-137">Use Procedural Code Instead of XAML</span></span>

<span data-ttu-id="e4e6c-138">Yordamsal koddan tüm WPF özelliklerine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4e6c-138">You can access all WPF features from procedural code.</span></span> <span data-ttu-id="e4e6c-139">Her türlü XAML kullanmayan WPF için "Merhaba mürekkep dünyası" uygulaması oluşturmak için bu adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="e4e6c-139">Follow these steps to create a "Hello Ink World" application for WPF that doesn’t use any XAML at all.</span></span>

1. <span data-ttu-id="e4e6c-140">Visual Studio 'da yeni bir konsol uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e4e6c-140">Create a new console application project in Visual Studio.</span></span>

   <span data-ttu-id="e4e6c-141">**Yeni proje** iletişim kutusunda, **yüklü** > **Visual C#**  veya **Visual Basic** > **Windows Masaüstü** kategorisini genişletin.</span><span class="sxs-lookup"><span data-stu-id="e4e6c-141">In the **New Project** dialog, expand the **Installed** > **Visual C#** or **Visual Basic** > **Windows Desktop** category.</span></span> <span data-ttu-id="e4e6c-142">Ardından **konsol uygulaması (.NET Framework)** uygulama şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="e4e6c-142">Then, select the **Console App (.NET Framework)** app template.</span></span> <span data-ttu-id="e4e6c-143">Bir ad girin ve **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="e4e6c-143">Enter a name, and then select **OK**.</span></span>

1. <span data-ttu-id="e4e6c-144">Aşağıdaki kodu Program.cs veya program. vb dosyasına yapıştırın:</span><span class="sxs-lookup"><span data-stu-id="e4e6c-144">Paste the following code into the Program.cs or Program.vb file:</span></span>

   [!code-csharp[InkCanvasConsoleApp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
   [!code-vb[InkCanvasConsoleApp#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]

1. <span data-ttu-id="e4e6c-145">**Çözüm Gezgini** **Başvurular** ' a sağ tıklayıp **Başvuru Ekle**' yi seçerek PresentationCore, PresentationFramework ve WindowsBase derlemelerine başvurular ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e4e6c-145">Add references to the PresentationCore, PresentationFramework, and WindowsBase assemblies by right-clicking on **References** in **Solution Explorer** and choosing **Add Reference**.</span></span>

   ![PresentationCore ve PresentationFramework gösteren başvuru Yöneticisi](./media/getting-started-with-ink/reference-manager-presentationcore-presentationframework.png)

1. <span data-ttu-id="e4e6c-147">**F5**tuşuna basarak uygulamayı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e4e6c-147">Build the application by pressing **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="e4e6c-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4e6c-148">See also</span></span>

- [<span data-ttu-id="e4e6c-149">Dijital Mürekkep</span><span class="sxs-lookup"><span data-stu-id="e4e6c-149">Digital Ink</span></span>](digital-ink.md)
- [<span data-ttu-id="e4e6c-150">Mürekkep Toplama</span><span class="sxs-lookup"><span data-stu-id="e4e6c-150">Collecting Ink</span></span>](collecting-ink.md)
- [<span data-ttu-id="e4e6c-151">El Yazısı Tanıma</span><span class="sxs-lookup"><span data-stu-id="e4e6c-151">Handwriting Recognition</span></span>](handwriting-recognition.md)
- [<span data-ttu-id="e4e6c-152">Mürekkep Depolama</span><span class="sxs-lookup"><span data-stu-id="e4e6c-152">Storing Ink</span></span>](storing-ink.md)
