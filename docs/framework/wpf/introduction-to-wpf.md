---
title: WPF'ye Giriş
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b8d7cf43-d1f2-4f3d-adb0-4f3a6428edc0
dev_langs:
- csharp
- vb
ms.openlocfilehash: 759c1ca20ac139ef856df08ec42fb259fc3920d1
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112017"
---
# <a name="wpf-overview"></a><span data-ttu-id="5fc57-102">WPF’ye genel bakış</span><span class="sxs-lookup"><span data-stu-id="5fc57-102">WPF overview</span></span>

<span data-ttu-id="5fc57-103">Windows Sunu Temeli (WPF), görsel olarak çarpıcı kullanıcı deneyimleriyle Windows için masaüstü istemci uygulamaları oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="5fc57-103">Windows Presentation Foundation (WPF) lets you create desktop client applications for Windows with visually stunning user experiences.</span></span>

![Contoso Healthcare UI örneği](media/introduction-to-wpf/wpfintrofigure24.png)

<span data-ttu-id="5fc57-105">WPF'nin çekirdeği, modern grafik donanımLarından yararlanmak için oluşturulmuş çözünürlükten bağımsız ve vektör tabanlı bir işleme motorudur.</span><span class="sxs-lookup"><span data-stu-id="5fc57-105">The core of WPF is a resolution-independent and vector-based rendering engine that is built to take advantage of modern graphics hardware.</span></span> <span data-ttu-id="5fc57-106">WPF genişletilebilir Uygulama Biçimlendirme Dili (XAML), denetimler, veri bağlama, düzen, 2D ve 3D grafikler, animasyon, stiller, şablonlar, belgeler, medya, metin ve içeren kapsamlı bir uygulama geliştirme özellikleri kümesi ile çekirdek genişletir Tipografi.</span><span class="sxs-lookup"><span data-stu-id="5fc57-106">WPF extends the core with a comprehensive set of application-development features that include Extensible Application Markup Language (XAML), controls, data binding, layout, 2D and 3D graphics, animation, styles, templates, documents, media, text, and typography.</span></span> <span data-ttu-id="5fc57-107">WPF .NET'in bir parçasıdır, böylece .NET API'nin diğer öğelerini içeren uygulamalar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fc57-107">WPF is part of .NET, so you can build applications that incorporate other elements of the .NET API.</span></span>

<span data-ttu-id="5fc57-108">Bu genel bakış yeni gelenler için tasarlanmıştır ve WPF'nin temel özelliklerini ve kavramlarını kapsar.</span><span class="sxs-lookup"><span data-stu-id="5fc57-108">This overview is intended for newcomers and covers the key capabilities and concepts of WPF.</span></span>

## <a name="program-with-wpf"></a><span data-ttu-id="5fc57-109">WPF programı</span><span class="sxs-lookup"><span data-stu-id="5fc57-109">Program with WPF</span></span>

<span data-ttu-id="5fc57-110">WPF, ad alanında bulunan (çoğunlukla) .NET türlerinin <xref:System.Windows> bir alt kümesi olarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="5fc57-110">WPF exists as a subset of .NET types that are (for the most part) located in the <xref:System.Windows> namespace.</span></span> <span data-ttu-id="5fc57-111">ASP.NET ve Windows Forms gibi yönetilen teknolojileri kullanarak .NET ile daha önce uygulama inşa ettiyseniz, temel WPF programlama deneyimi tanıdık olmalıdır; C# veya Visual Basic gibi favori .NET programlama dilini kullanarak sınıfları anında ayarlar, özellikleri ayarlar, arama yöntemleri ni çağırır ve olayları işlersiniz.</span><span class="sxs-lookup"><span data-stu-id="5fc57-111">If you have previously built applications with .NET using managed technologies like ASP.NET and Windows Forms, the fundamental WPF programming experience should be familiar; you instantiate classes, set properties, call methods, and handle events, using your favorite .NET programming language, such as C# or Visual Basic.</span></span>

<span data-ttu-id="5fc57-112">WPF özellikleri ve olayları geliştirmek ek programlama yapıları içerir: [bağımlılık özellikleri](advanced/dependency-properties-overview.md) ve [yönlendirilen olaylar.](advanced/routed-events-overview.md)</span><span class="sxs-lookup"><span data-stu-id="5fc57-112">WPF includes additional programming constructs that enhance properties and events: [dependency properties](advanced/dependency-properties-overview.md) and [routed events](advanced/routed-events-overview.md).</span></span>

## <a name="markup-and-code-behind"></a><span data-ttu-id="5fc57-113">Biçimlendirme ve kod arkası</span><span class="sxs-lookup"><span data-stu-id="5fc57-113">Markup and code-behind</span></span>

<span data-ttu-id="5fc57-114">WPF, hem *biçimlendirme* hem de *kod arkası*kullanarak bir uygulama geliştirmenize olanak tanır ve geliştiricilerin ASP.NET aşina olması gereken bir deneyim.</span><span class="sxs-lookup"><span data-stu-id="5fc57-114">WPF lets you develop an application using both *markup* and *code-behind*, an experience with which ASP.NET developers should be familiar.</span></span> <span data-ttu-id="5fc57-115">Genellikle, davranışını uygulamak için yönetilen programlama dillerini (kod arkası) kullanırken bir uygulamanın görünümünü uygulamak için XAML biçimlendirmesini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="5fc57-115">You generally use XAML markup to implement the appearance of an application while using managed programming languages (code-behind) to implement its behavior.</span></span> <span data-ttu-id="5fc57-116">Görünüm ve davranış bu ayrım aşağıdaki yararları vardır:</span><span class="sxs-lookup"><span data-stu-id="5fc57-116">This separation of appearance and behavior has the following benefits:</span></span>

- <span data-ttu-id="5fc57-117">Görünüme özel biçimlendirme davranışa özgü kodla sıkı bir şekilde birleştirilemediği için geliştirme ve bakım maliyetleri azalır.</span><span class="sxs-lookup"><span data-stu-id="5fc57-117">Development and maintenance costs are reduced because appearance-specific markup is not tightly coupled with behavior-specific code.</span></span>

- <span data-ttu-id="5fc57-118">Tasarımcılar, uygulamanın davranışını uygulayan geliştiricilerle aynı anda bir uygulamanın görünümünü uygulayabildiklerinden, geliştirme daha verimlidir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-118">Development is more efficient because designers can implement an application's appearance simultaneously with developers who are implementing the application's behavior.</span></span>

- <span data-ttu-id="5fc57-119">WPF uygulamaları için [küreselleşme ve yerelleştirme](advanced/wpf-globalization-and-localization-overview.md) basitleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-119">[Globalization and localization](advanced/wpf-globalization-and-localization-overview.md) for WPF applications is simplified.</span></span>

### <a name="markup"></a><span data-ttu-id="5fc57-120">İşaretleme</span><span class="sxs-lookup"><span data-stu-id="5fc57-120">Markup</span></span>

<span data-ttu-id="5fc57-121">XAML, bir uygulamanın görünümünü bildirimsel olarak uygulayan XML tabanlı bir biçimlendirme dilidir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-121">XAML is an XML-based markup language that implements an application's appearance declaratively.</span></span> <span data-ttu-id="5fc57-122">Genellikle pencereler, iletişim kutuları, sayfalar ve kullanıcı denetimleri oluşturmak ve bunları denetimler, şekiller ve grafiklerle doldurmak için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="5fc57-122">You typically use it to create windows, dialog boxes, pages, and user controls, and to fill them with controls, shapes, and graphics.</span></span>

<span data-ttu-id="5fc57-123">Aşağıdaki örnek, tek bir düğme içeren bir pencere görünümünü uygulamak için XAML kullanır:</span><span class="sxs-lookup"><span data-stu-id="5fc57-123">The following example uses XAML to implement the appearance of a window that contains a single button:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button">Click Me!</Button>

</Window>
```

<span data-ttu-id="5fc57-124">Özellikle, bu XAML sırasıyla `Window` ve öğeleri kullanarak `Button` bir pencere ve bir düğme tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5fc57-124">Specifically, this XAML defines a window and a button by using the `Window` and `Button` elements, respectively.</span></span> <span data-ttu-id="5fc57-125">Her öğe, pencerenin başlık çubuğu `Window` metnini `Title` belirtmek için öğenin özniteliği gibi özniteliklerle yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="5fc57-125">Each element is configured with attributes, such as the `Window` element's `Title` attribute to specify the window's title-bar text.</span></span> <span data-ttu-id="5fc57-126">Çalışma zamanında, WPF biçimlendirmede tanımlanan öğeleri ve öznitelikleri WPF sınıflarının örneklerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="5fc57-126">At run time, WPF converts the elements and attributes that are defined in markup to instances of WPF classes.</span></span> <span data-ttu-id="5fc57-127">Örneğin, `Window` öğe özelliği öznitelik değeri <xref:System.Windows.Window> <xref:System.Windows.Window.Title%2A> `Title` olan sınıfın bir örneğine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="5fc57-127">For example, the `Window` element is converted to an instance of the <xref:System.Windows.Window> class whose <xref:System.Windows.Window.Title%2A> property is the value of the `Title` attribute.</span></span>

<span data-ttu-id="5fc57-128">Aşağıdaki şekilde, önceki örnekte XAML tarafından tanımlanan kullanıcı arabirimi (UI) gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="5fc57-128">The following figure shows the user interface (UI) that is defined by the XAML in the previous example:</span></span>

![Düğme içeren bir pencere](media/introduction-to-wpf/wpfintrofigure10.png)

<span data-ttu-id="5fc57-130">XAML XML tabanlı olduğundan, onunla oluşturduğunuz [UI, öğe ağacı](advanced/trees-in-wpf.md)olarak bilinen iç içe öğeler hiyerarşisinde bir araya getirilir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-130">Since XAML is XML-based, the UI that you compose with it is assembled in a hierarchy of nested elements known as an [element tree](advanced/trees-in-wpf.md).</span></span> <span data-ttu-id="5fc57-131">Öğe ağacı, Kullanıcı Arabirimi oluşturmak ve yönetmek için mantıklı ve sezgisel bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fc57-131">The element tree provides a logical and intuitive way to create and manage UIs.</span></span>

### <a name="code-behind"></a><span data-ttu-id="5fc57-132">Kod arkası</span><span class="sxs-lookup"><span data-stu-id="5fc57-132">Code-behind</span></span>

<span data-ttu-id="5fc57-133">Bir uygulamanın temel davranışı, olayları işleme (örneğin, bir menü, araç çubuğu nu veya düğmeyi tıklatma) ve yanıt olarak iş mantığı ve veri erişim mantığını çağırmak da dahil olmak üzere kullanıcı etkileşimlerine yanıt veren işlevselliği uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="5fc57-133">The main behavior of an application is to implement the functionality that responds to user interactions, including handling events (for example, clicking a menu, tool bar, or button) and calling business logic and data access logic in response.</span></span> <span data-ttu-id="5fc57-134">WPF'de, bu davranış biçimlendirmeyle ilişkili kodda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="5fc57-134">In WPF, this behavior is implemented in code that is associated with markup.</span></span> <span data-ttu-id="5fc57-135">Bu kod türü kod arkası olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-135">This type of code is known as code-behind.</span></span> <span data-ttu-id="5fc57-136">Aşağıdaki örnek, önceki örnekten güncelleştirilmiş biçimlendirmeyi ve kodun arkasını gösterir:</span><span class="sxs-lookup"><span data-stu-id="5fc57-136">The following example shows the updated markup from the previous example and the code-behind:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.AWindow"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button" Click="button_Click">Click Me!</Button>

</Window>
```

```csharp
using System.Windows; // Window, RoutedEventArgs, MessageBox

namespace SDKSample
{
    public partial class AWindow : Window
    {
        public AWindow()
        {
            // InitializeComponent call is required to merge the UI
            // that is defined in markup with this class, including  
            // setting properties and registering event handlers
            InitializeComponent();
        }

        void button_Click(object sender, RoutedEventArgs e)
        {
            // Show message box when button is clicked.
            MessageBox.Show("Hello, Windows Presentation Foundation!");
        }
    }
}
```

```vb
Namespace SDKSample

    Partial Public Class AWindow
        Inherits System.Windows.Window

        Public Sub New()

            ' InitializeComponent call is required to merge the UI
            ' that is defined in markup with this class, including  
            ' setting properties and registering event handlers
            InitializeComponent()

        End Sub

        Private Sub button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)

            ' Show message box when button is clicked.
            MessageBox.Show("Hello, Windows Presentation Foundation!")

        End Sub

    End Class

End Namespace
```

<span data-ttu-id="5fc57-137">Bu örnekte, kod arkası <xref:System.Windows.Window> sınıftan türetilen bir sınıf uygular.</span><span class="sxs-lookup"><span data-stu-id="5fc57-137">In this example, the code-behind implements a class that derives from the <xref:System.Windows.Window> class.</span></span> <span data-ttu-id="5fc57-138">Öznitelik, `x:Class` biçimlendirmeyi kod arkası sınıfıyla ilişkilendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5fc57-138">The `x:Class` attribute is used to associate the markup with the code-behind class.</span></span> <span data-ttu-id="5fc57-139">`InitializeComponent`biçimlendirmede tanımlanan UI'yi kod arkası sınıfıyla birleştirmek için kod arkasındaki sınıfın oluşturucusundan çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5fc57-139">`InitializeComponent` is called from the code-behind class's constructor to merge the UI that is defined in markup with the code-behind class.</span></span> <span data-ttu-id="5fc57-140">(`InitializeComponent` uygulamanız oluşturulduğunda sizin için oluşturulur, bu nedenle el ile uygulamanız gerekmez.) Birleşimi `x:Class` ve `InitializeComponent` uygulamanızın oluşturulduğunda doğru şekilde başlatılmasını sağlamak.</span><span class="sxs-lookup"><span data-stu-id="5fc57-140">(`InitializeComponent` is generated for you when your application is built, which is why you don't need to implement it manually.) The combination of `x:Class` and `InitializeComponent` ensure that your implementation is correctly initialized whenever it is created.</span></span> <span data-ttu-id="5fc57-141">Kod arkası sınıfı, düğmenin <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayı için bir olay işleyicisi de uygular.</span><span class="sxs-lookup"><span data-stu-id="5fc57-141">The code-behind class also implements an event handler for the button's <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event.</span></span> <span data-ttu-id="5fc57-142">Düğme tıklatıldığında, olay işleyicisi <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> yöntemi arayarak bir ileti kutusu gösterir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-142">When the button is clicked, the event handler shows a message box by calling the <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> method.</span></span>

<span data-ttu-id="5fc57-143">Aşağıdaki şekil, düğme tıklatıldığında sonucu gösterir:</span><span class="sxs-lookup"><span data-stu-id="5fc57-143">The following figure shows the result when the button is clicked:</span></span>

![Bir MessageBox](media/introduction-to-wpf/wpfintrofigure25.png)

## <a name="controls"></a><span data-ttu-id="5fc57-145">Denetimler</span><span class="sxs-lookup"><span data-stu-id="5fc57-145">Controls</span></span>

<span data-ttu-id="5fc57-146">Uygulama modeli tarafından teslim edilen kullanıcı deneyimleri denetimler oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5fc57-146">The user experiences that are delivered by the application model are constructed controls.</span></span> <span data-ttu-id="5fc57-147">WPF'de *denetim,* pencere veya sayfada barındırılan, kullanıcı arabirimine sahip ve bazı davranışları uygulayan WPF sınıfları kategorisi için geçerli olan bir şemsiye terimdir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-147">In WPF, *control* is an umbrella term that applies to a category of WPF classes that are hosted in either a window or a page, have a user interface, and implement some behavior.</span></span>

<span data-ttu-id="5fc57-148">Daha fazla bilgi için [Denetimler'e](controls/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="5fc57-148">For more information, see [Controls](controls/index.md).</span></span>

### <a name="wpf-controls-by-function"></a><span data-ttu-id="5fc57-149">Fonksiyona göre WPF kontrolleri</span><span class="sxs-lookup"><span data-stu-id="5fc57-149">WPF controls by function</span></span>

<span data-ttu-id="5fc57-150">Yerleşik WPF denetimleri burada listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="5fc57-150">The built-in WPF controls are listed here:</span></span>

- <span data-ttu-id="5fc57-151">**Düğmeler** <xref:System.Windows.Controls.Button> : <xref:System.Windows.Controls.Primitives.RepeatButton>ve .</span><span class="sxs-lookup"><span data-stu-id="5fc57-151">**Buttons**: <xref:System.Windows.Controls.Button> and <xref:System.Windows.Controls.Primitives.RepeatButton>.</span></span>

- <span data-ttu-id="5fc57-152">**Veri**Ekranı <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Controls.ListView>: <xref:System.Windows.Controls.TreeView>, , ve .</span><span class="sxs-lookup"><span data-stu-id="5fc57-152">**Data Display**: <xref:System.Windows.Controls.DataGrid>, <xref:System.Windows.Controls.ListView>, and <xref:System.Windows.Controls.TreeView>.</span></span>

- <span data-ttu-id="5fc57-153">**Tarih Görüntüleme**ve <xref:System.Windows.Controls.Calendar> <xref:System.Windows.Controls.DatePicker>Seçim : ve .</span><span class="sxs-lookup"><span data-stu-id="5fc57-153">**Date Display and Selection**: <xref:System.Windows.Controls.Calendar> and <xref:System.Windows.Controls.DatePicker>.</span></span>

- <span data-ttu-id="5fc57-154">**İletişim Kutuları** <xref:Microsoft.Win32.OpenFileDialog>: <xref:System.Windows.Controls.PrintDialog>, <xref:Microsoft.Win32.SaveFileDialog>, ve .</span><span class="sxs-lookup"><span data-stu-id="5fc57-154">**Dialog Boxes**: <xref:Microsoft.Win32.OpenFileDialog>, <xref:System.Windows.Controls.PrintDialog>, and <xref:Microsoft.Win32.SaveFileDialog>.</span></span>

- <span data-ttu-id="5fc57-155">**Dijital Mürekkep** <xref:System.Windows.Controls.InkCanvas> : <xref:System.Windows.Controls.InkPresenter>ve .</span><span class="sxs-lookup"><span data-stu-id="5fc57-155">**Digital Ink**: <xref:System.Windows.Controls.InkCanvas> and <xref:System.Windows.Controls.InkPresenter>.</span></span>

- <span data-ttu-id="5fc57-156">**Belgeler** <xref:System.Windows.Controls.DocumentViewer>: <xref:System.Windows.Controls.FlowDocumentPageViewer> <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentScrollViewer>, <xref:System.Windows.Controls.StickyNoteControl>, ve .</span><span class="sxs-lookup"><span data-stu-id="5fc57-156">**Documents**: <xref:System.Windows.Controls.DocumentViewer>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentScrollViewer>, and <xref:System.Windows.Controls.StickyNoteControl>.</span></span>

- <span data-ttu-id="5fc57-157">**Giriş**: <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox>, <xref:System.Windows.Controls.PasswordBox>, ve .</span><span class="sxs-lookup"><span data-stu-id="5fc57-157">**Input**: <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, and <xref:System.Windows.Controls.PasswordBox>.</span></span>

- <span data-ttu-id="5fc57-158">**Düzen** <xref:System.Windows.Controls.Border>: <xref:System.Windows.Controls.Primitives.BulletDecorator> <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Expander>, <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridSplitter> <xref:System.Windows.Controls.GroupBox>, <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Primitives.ResizeGrip>, <xref:System.Windows.Controls.Separator> <xref:System.Windows.Controls.Primitives.ScrollBar>, <xref:System.Windows.Controls.ScrollViewer> <xref:System.Windows.Controls.VirtualizingStackPanel> <xref:System.Windows.Window>, , , <xref:System.Windows.Controls.WrapPanel>, , , , , , , ve . <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.Primitives.Thumb> <xref:System.Windows.Controls.Viewbox></span><span class="sxs-lookup"><span data-stu-id="5fc57-158">**Layout**: <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Primitives.BulletDecorator>, <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Expander>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridSplitter>, <xref:System.Windows.Controls.GroupBox>, <xref:System.Windows.Controls.Panel>, <xref:System.Windows.Controls.Primitives.ResizeGrip>, <xref:System.Windows.Controls.Separator>, <xref:System.Windows.Controls.Primitives.ScrollBar>, <xref:System.Windows.Controls.ScrollViewer>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.Primitives.Thumb>, <xref:System.Windows.Controls.Viewbox>, <xref:System.Windows.Controls.VirtualizingStackPanel>, <xref:System.Windows.Window>, and <xref:System.Windows.Controls.WrapPanel>.</span></span>

- <span data-ttu-id="5fc57-159">**Medya** <xref:System.Windows.Controls.Image>: <xref:System.Windows.Controls.MediaElement>, <xref:System.Windows.Controls.SoundPlayerAction>, ve .</span><span class="sxs-lookup"><span data-stu-id="5fc57-159">**Media**: <xref:System.Windows.Controls.Image>, <xref:System.Windows.Controls.MediaElement>, and <xref:System.Windows.Controls.SoundPlayerAction>.</span></span>

- <span data-ttu-id="5fc57-160">**Menüler** <xref:System.Windows.Controls.ContextMenu>: <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.ToolBar>, ve .</span><span class="sxs-lookup"><span data-stu-id="5fc57-160">**Menus**: <xref:System.Windows.Controls.ContextMenu>, <xref:System.Windows.Controls.Menu>, and <xref:System.Windows.Controls.ToolBar>.</span></span>

- <span data-ttu-id="5fc57-161">**Navigasyon** <xref:System.Windows.Controls.Frame>: <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.TabControl>, ve .</span><span class="sxs-lookup"><span data-stu-id="5fc57-161">**Navigation**: <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, and <xref:System.Windows.Controls.TabControl>.</span></span>

- <span data-ttu-id="5fc57-162">**Seçim** <xref:System.Windows.Controls.CheckBox>: <xref:System.Windows.Controls.ComboBox> <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.Slider>, ve .</span><span class="sxs-lookup"><span data-stu-id="5fc57-162">**Selection**: <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.RadioButton>, and <xref:System.Windows.Controls.Slider>.</span></span>

- <span data-ttu-id="5fc57-163">**Kullanıcı**Bilgileri <xref:System.Windows.Controls.AccessText> <xref:System.Windows.Controls.Label>: <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.ProgressBar>, <xref:System.Windows.Controls.Primitives.StatusBar> <xref:System.Windows.Controls.TextBlock>, <xref:System.Windows.Controls.ToolTip>, , , , ve .</span><span class="sxs-lookup"><span data-stu-id="5fc57-163">**User Information**: <xref:System.Windows.Controls.AccessText>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.ProgressBar>, <xref:System.Windows.Controls.Primitives.StatusBar>, <xref:System.Windows.Controls.TextBlock>, and <xref:System.Windows.Controls.ToolTip>.</span></span>

## <a name="input-and-commands"></a><span data-ttu-id="5fc57-164">Giriş ve komutlar</span><span class="sxs-lookup"><span data-stu-id="5fc57-164">Input and commands</span></span>

<span data-ttu-id="5fc57-165">Denetimler en sık kullanıcı girişini algılar ve bunlara yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-165">Controls most often detect and respond to user input.</span></span> <span data-ttu-id="5fc57-166">[WPF giriş sistemi](advanced/input-overview.md) metin girişi, odak yönetimi ve fare konumlandırmasını desteklemek için hem doğrudan hem de yönlendirilmiş olayları kullanır.</span><span class="sxs-lookup"><span data-stu-id="5fc57-166">The [WPF input system](advanced/input-overview.md) uses both direct and routed events to support text input, focus management, and mouse positioning.</span></span>

<span data-ttu-id="5fc57-167">Uygulamalar genellikle karmaşık giriş gereksinimlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-167">Applications often have complex input requirements.</span></span> <span data-ttu-id="5fc57-168">WPF, kullanıcı giriş eylemlerini bu eylemlere yanıt veren koddan ayıran bir [komut sistemi](advanced/commanding-overview.md) sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fc57-168">WPF provides a [command system](advanced/commanding-overview.md) that separates user-input actions from the code that responds to those actions.</span></span>

## <a name="layout"></a><span data-ttu-id="5fc57-169">Düzen</span><span class="sxs-lookup"><span data-stu-id="5fc57-169">Layout</span></span>

<span data-ttu-id="5fc57-170">Bir kullanıcı arabirimi oluşturduğunuzda, denetimlerinizi bir düzen oluşturmak için konuma ve boyuta göre düzenlersiniz.</span><span class="sxs-lookup"><span data-stu-id="5fc57-170">When you create a user interface, you arrange your controls by location and size to form a layout.</span></span> <span data-ttu-id="5fc57-171">Herhangi bir düzenin temel gereksinimi, pencere boyutu ve görüntü ayarlarındaki değişikliklere uyum sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="5fc57-171">A key requirement of any layout is to adapt to changes in window size and display settings.</span></span> <span data-ttu-id="5fc57-172">WPF, bu koşullarda bir düzeni uyarlamak için kodu yazmaya zorlamak yerine, sizin için birinci sınıf, genişletilebilir bir düzen sistemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fc57-172">Rather than forcing you to write the code to adapt a layout in these circumstances, WPF provides a first-class, extensible layout system for you.</span></span>

<span data-ttu-id="5fc57-173">Düzen sisteminin temel taşı, değişen pencere ve görüntü koşullarına uyum sağlama yeteneğini artıran göreli konumlandırmadır.</span><span class="sxs-lookup"><span data-stu-id="5fc57-173">The cornerstone of the layout system is relative positioning, which increases the ability to adapt to changing window and display conditions.</span></span> <span data-ttu-id="5fc57-174">Buna ek olarak, düzen sistemi düzeni belirlemek için denetimler arasındaki anlaşma yönetir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-174">In addition, the layout system manages the negotiation between controls to determine the layout.</span></span> <span data-ttu-id="5fc57-175">Müzakere iki aşamalı bir süreçtir: Birincisi, bir denetim ebeveynine hangi konum ve boyutu gerektirdiğini söyler; ikincisi, üst öğe denetime hangi alana sahip olabileceğini söyler.</span><span class="sxs-lookup"><span data-stu-id="5fc57-175">The negotiation is a two-step process: first, a control tells its parent what location and size it requires; second, the parent tells the control what space it can have.</span></span>

<span data-ttu-id="5fc57-176">Düzen sistemi temel WPF sınıfları aracılığıyla alt denetimlere maruz kalır.</span><span class="sxs-lookup"><span data-stu-id="5fc57-176">The layout system is exposed to child controls through base WPF classes.</span></span> <span data-ttu-id="5fc57-177">Kılavuzlar, istifleme ve yerleştirme gibi yaygın düzenler için WPF birkaç düzen denetimi içerir:</span><span class="sxs-lookup"><span data-stu-id="5fc57-177">For common layouts such as grids, stacking, and docking, WPF includes several layout controls:</span></span>

- <span data-ttu-id="5fc57-178"><xref:System.Windows.Controls.Canvas>: Alt denetimler kendi düzenini sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fc57-178"><xref:System.Windows.Controls.Canvas>: Child controls provide their own layout.</span></span>

- <span data-ttu-id="5fc57-179"><xref:System.Windows.Controls.DockPanel>: Alt denetimler panelin kenarlarına hizalanır.</span><span class="sxs-lookup"><span data-stu-id="5fc57-179"><xref:System.Windows.Controls.DockPanel>: Child controls are aligned to the edges of the panel.</span></span>

- <span data-ttu-id="5fc57-180"><xref:System.Windows.Controls.Grid>: Alt denetimler satır ve sütunlara göre konumlandırılır.</span><span class="sxs-lookup"><span data-stu-id="5fc57-180"><xref:System.Windows.Controls.Grid>: Child controls are positioned by rows and columns.</span></span>

- <span data-ttu-id="5fc57-181"><xref:System.Windows.Controls.StackPanel>: Alt denetimler dikey veya yatay olarak istiflenir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-181"><xref:System.Windows.Controls.StackPanel>: Child controls are stacked either vertically or horizontally.</span></span>

- <span data-ttu-id="5fc57-182"><xref:System.Windows.Controls.VirtualizingStackPanel>: Alt denetimler sanallaştırılır ve yatay veya dikey olarak yönlendirilmiş tek bir satır üzerinde düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-182"><xref:System.Windows.Controls.VirtualizingStackPanel>: Child controls are virtualized and arranged on a single line that is either horizontally or vertically oriented.</span></span>

- <span data-ttu-id="5fc57-183"><xref:System.Windows.Controls.WrapPanel>: Alt kontroller soldan sağa doğru konumlandırılır ve geçerli hatta boşluktan daha fazla kontrol olduğunda bir sonraki satıra sarılır.</span><span class="sxs-lookup"><span data-stu-id="5fc57-183"><xref:System.Windows.Controls.WrapPanel>: Child controls are positioned in left-to-right order and wrapped to the next line when there are more controls on the current line than space allows.</span></span>

<span data-ttu-id="5fc57-184">Aşağıdaki örnek, <xref:System.Windows.Controls.DockPanel> a'yı <xref:System.Windows.Controls.TextBox> çeşitli denetimleri düzenlemek için kullanır:</span><span class="sxs-lookup"><span data-stu-id="5fc57-184">The following example uses a <xref:System.Windows.Controls.DockPanel> to lay out several <xref:System.Windows.Controls.TextBox> controls:</span></span>

[!code-xaml[IntroToWPFSnippets#LayoutMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_1.xaml)]

<span data-ttu-id="5fc57-185">Çocuk <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.TextBox> kontrolleri onları düzenlemek için nasıl söylemek için izin verir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-185">The <xref:System.Windows.Controls.DockPanel> allows the child <xref:System.Windows.Controls.TextBox> controls to tell it how to arrange them.</span></span> <span data-ttu-id="5fc57-186">Bunu yapmak için, her `Dock` biri bir dock stili belirtmek için izin vermek için alt denetimleri maruz kalan ekli bir özellik <xref:System.Windows.Controls.DockPanel> uygular.</span><span class="sxs-lookup"><span data-stu-id="5fc57-186">To do this, the <xref:System.Windows.Controls.DockPanel> implements a `Dock` attached property that is exposed to the child controls to allow each of them to specify a dock style.</span></span>

> [!NOTE]
> <span data-ttu-id="5fc57-187">Alt denetimler tarafından kullanılmak üzere bir üst denetim tarafından uygulanan bir [özellik, ekli özellik](advanced/attached-properties-overview.md)olarak adlandırılan bir WPF yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="5fc57-187">A property that's implemented by a parent control for use by child controls is a WPF construct called an [attached property](advanced/attached-properties-overview.md).</span></span>

<span data-ttu-id="5fc57-188">Aşağıdaki şekil, önceki örnekte XAML biçimlendirmesinin sonucunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="5fc57-188">The following figure shows the result of the XAML markup in the preceding example:</span></span>

![DockPanel sayfası](media/introduction-to-wpf/wpfintrofigure11.png)

## <a name="data-binding"></a><span data-ttu-id="5fc57-190">Veri bağlama</span><span class="sxs-lookup"><span data-stu-id="5fc57-190">Data binding</span></span>

<span data-ttu-id="5fc57-191">Çoğu uygulama, kullanıcılara verileri görüntüleme ve görüntüleme araçları sağlamak için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5fc57-191">Most applications are created to provide users with the means to view and edit data.</span></span> <span data-ttu-id="5fc57-192">WPF uygulamaları için, sql server ve ADO .NET gibi teknolojiler tarafından veri depolama ve bunlara erişim çalışmaları zaten sağlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="5fc57-192">For WPF applications, the work of storing and accessing data is already provided for by technologies such as SQL Server and ADO .NET.</span></span> <span data-ttu-id="5fc57-193">Verilere erişildikten ve bir uygulamanın yönetilen nesnelerine yüklendikten sonra, WPF uygulamaları için zor iş başlar.</span><span class="sxs-lookup"><span data-stu-id="5fc57-193">After the data is accessed and loaded into an application's managed objects, the hard work for WPF applications begins.</span></span> <span data-ttu-id="5fc57-194">Esasen, bu iki şey içerir:</span><span class="sxs-lookup"><span data-stu-id="5fc57-194">Essentially, this involves two things:</span></span>

1. <span data-ttu-id="5fc57-195">Yönetilen nesnelerden verileri, verilerin görüntülenebileceği ve düzenlenebileceği denetimlere kopyalama.</span><span class="sxs-lookup"><span data-stu-id="5fc57-195">Copying the data from the managed objects into controls, where the data can be displayed and edited.</span></span>

2. <span data-ttu-id="5fc57-196">Denetimler kullanılarak verilerde yapılan değişikliklerin yönetilen nesnelere kopyalanmasını sağlamak.</span><span class="sxs-lookup"><span data-stu-id="5fc57-196">Ensuring that changes made to data by using controls are copied back to the managed objects.</span></span>

<span data-ttu-id="5fc57-197">Uygulama geliştirmeyi kolaylaştırmak için WPF, bu adımları otomatik olarak gerçekleştirmek için bir veri bağlama altyapısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fc57-197">To simplify application development, WPF provides a data binding engine to automatically perform these steps.</span></span> <span data-ttu-id="5fc57-198">Veri bağlama altyapısının temel birimi, işi bir denetimi (bağlayıcı hedef) bir veri nesnesine (bağlayıcı kaynak) bağlamak olan <xref:System.Windows.Data.Binding> sınıftır.</span><span class="sxs-lookup"><span data-stu-id="5fc57-198">The core unit of the data binding engine is the <xref:System.Windows.Data.Binding> class, whose job is to bind a control (the binding target) to a data object (the binding source).</span></span> <span data-ttu-id="5fc57-199">Bu ilişki aşağıdaki şekille gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5fc57-199">This relationship is illustrated by the following figure:</span></span>

![Temel veri bağlama diyagramı](media/introduction-to-wpf/databindingmostbasic.png)

<span data-ttu-id="5fc57-201">Sonraki örnek, a'nın <xref:System.Windows.Controls.TextBox> özel `Person` bir nesne örneğine nasıl bağlanılmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-201">The next example demonstrates how to bind a <xref:System.Windows.Controls.TextBox> to an instance of a custom `Person` object.</span></span> <span data-ttu-id="5fc57-202">Uygulama `Person` aşağıdaki kodda gösterilir:</span><span class="sxs-lookup"><span data-stu-id="5fc57-202">The `Person` implementation is shown in the following code:</span></span>

[!code-vb[SimpleDataBindingSnippets#PersonClassCODE](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_2.vb)]
[!code-csharp[SimpleDataBindingSnippets#PersonClassCODE](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_2.cs)]

<span data-ttu-id="5fc57-203">Aşağıdaki biçimlendirme özel <xref:System.Windows.Controls.TextBox> `Person` bir nesnenin bir örneğine bağlanır:</span><span class="sxs-lookup"><span data-stu-id="5fc57-203">The following markup binds the <xref:System.Windows.Controls.TextBox> to an instance of a custom `Person` object:</span></span>

```xaml
 <Window
     xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
     xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
     x:Class="SDKSample.DataBindingWindow">

   <!-- Bind the TextBox to the data source (TextBox.Text to Person.Name) -->
   <TextBox Name="personNameTextBox" Text="{Binding Path=Name}" />

 </Window>
```

[!code-vb[SimpleDataBindingSnippets#DataBindingCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_6.vb)]
[!code-csharp[SimpleDataBindingSnippets#DataBindingCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_6.cs)]

<span data-ttu-id="5fc57-204">Bu örnekte, `Person` sınıf kod arkasında anında ve veri bağlamı olarak `DataBindingWindow`ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="5fc57-204">In this example, the `Person` class is instantiated in code-behind and is set as the data context for the `DataBindingWindow`.</span></span> <span data-ttu-id="5fc57-205">Biçimlendirmede, <xref:System.Windows.Controls.TextBox.Text%2A> <xref:System.Windows.Controls.TextBox> özelliği `Person.Name` özelliğe bağlıdır (" XAML`{Binding ... }`sözdizimi kullanılarak).</span><span class="sxs-lookup"><span data-stu-id="5fc57-205">In markup, the <xref:System.Windows.Controls.TextBox.Text%2A> property of the <xref:System.Windows.Controls.TextBox> is bound to the `Person.Name` property (using the "`{Binding ... }`" XAML syntax).</span></span> <span data-ttu-id="5fc57-206">Bu XAML, WPF'ye <xref:System.Windows.Controls.TextBox> denetimi `Person` pencerenin <xref:System.Windows.FrameworkElement.DataContext%2A> özelliğinde depolanan nesneye bağlamasını söyler.</span><span class="sxs-lookup"><span data-stu-id="5fc57-206">This XAML tells WPF to bind the <xref:System.Windows.Controls.TextBox> control to the `Person` object that is stored in the <xref:System.Windows.FrameworkElement.DataContext%2A> property of the window.</span></span>

<span data-ttu-id="5fc57-207">WPF veri bağlama altyapısı doğrulama, sıralama, filtreleme ve gruplandırma içeren ek destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fc57-207">The WPF data binding engine provides additional support that includes validation, sorting, filtering, and grouping.</span></span> <span data-ttu-id="5fc57-208">Ayrıca, standart WPF denetimleri tarafından görüntülenen kullanıcı arabirimi uygun olmadığında, bağlı veriler için özel kullanıcı arabirimi oluşturmak için veri şablonlarının kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="5fc57-208">Furthermore, data binding supports the use of data templates to create custom user interface for bound data when the user interface displayed by the standard WPF controls is not appropriate.</span></span>

<span data-ttu-id="5fc57-209">Daha fazla bilgi için bkz: [Veri bağlama genel bakışı.](../../desktop-wpf/data/data-binding-overview.md)</span><span class="sxs-lookup"><span data-stu-id="5fc57-209">For more information, see [Data binding overview](../../desktop-wpf/data/data-binding-overview.md).</span></span>

## <a name="graphics"></a><span data-ttu-id="5fc57-210">Grafikler</span><span class="sxs-lookup"><span data-stu-id="5fc57-210">Graphics</span></span>

<span data-ttu-id="5fc57-211">WPF, aşağıdaki avantajlara sahip kapsamlı, ölçeklenebilir ve esnek grafik özellikleri kümesini sunar:</span><span class="sxs-lookup"><span data-stu-id="5fc57-211">WPF introduces an extensive, scalable, and flexible set of graphics features that have the following benefits:</span></span>

- <span data-ttu-id="5fc57-212">**Çözünürlük-bağımsız ve cihazbağımsız grafikler.**</span><span class="sxs-lookup"><span data-stu-id="5fc57-212">**Resolution-independent and device-independent graphics**.</span></span> <span data-ttu-id="5fc57-213">WPF grafik sistemindeki temel ölçüm birimi, gerçek ekran çözünürlüğüne bakılmaksızın bir inçin 1/96th'si olan ve çözünürlükten bağımsız ve aygıttan bağımsız görüntülemenin temelini oluşturan aygıttan bağımsız pikseldir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-213">The basic unit of measurement in the WPF graphics system is the device-independent pixel, which is 1/96th of an inch, regardless of actual screen resolution, and provides the foundation for resolution-independent and device-independent rendering.</span></span> <span data-ttu-id="5fc57-214">Her aygıttan bağımsız piksel, işlettiginsistemin inç başına nokta (dpi) ayarına uyacak şekilde otomatik olarak ölçeklenir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-214">Each device-independent pixel automatically scales to match the dots-per-inch (dpi) setting of the system it renders on.</span></span>

- <span data-ttu-id="5fc57-215">**Geliştirilmiş hassasiyet.**</span><span class="sxs-lookup"><span data-stu-id="5fc57-215">**Improved precision**.</span></span> <span data-ttu-id="5fc57-216">WPF koordinat sistemi, tek hassasiyetli değil, çift duyarlıklı kayan nokta numaralarıyla ölçülür.</span><span class="sxs-lookup"><span data-stu-id="5fc57-216">The WPF coordinate system is measured with double-precision floating-point numbers rather than single-precision.</span></span> <span data-ttu-id="5fc57-217">Dönüşümler ve opaklık değerleri de çift duyarlıklı olarak ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-217">Transformations and opacity values are also expressed as double-precision.</span></span> <span data-ttu-id="5fc57-218">WPF ayrıca geniş bir renk gamı (scRGB) destekler ve farklı renk alanlarından girişleri yönetmek için entegre destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fc57-218">WPF also supports a wide color gamut (scRGB) and provides integrated support for managing inputs from different color spaces.</span></span>

- <span data-ttu-id="5fc57-219">**Gelişmiş grafik ve animasyon desteği.**</span><span class="sxs-lookup"><span data-stu-id="5fc57-219">**Advanced graphics and animation support**.</span></span> <span data-ttu-id="5fc57-220">WPF sizin için animasyon sahneleri yöneterek grafik programlama kolaylaştırır; sahne işleme, döngüoluşturma ve çift doğrusal enterpolasyon konusunda endişelenmenize gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="5fc57-220">WPF simplifies graphics programming by managing animation scenes for you; there is no need to worry about scene processing, rendering loops, and bilinear interpolation.</span></span> <span data-ttu-id="5fc57-221">Ayrıca, WPF isabet testi desteği ve tam alfa birleştirme desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fc57-221">Additionally, WPF provides hit-testing support and full alpha-compositing support.</span></span>

- <span data-ttu-id="5fc57-222">**Donanım ivmesi.**</span><span class="sxs-lookup"><span data-stu-id="5fc57-222">**Hardware acceleration**.</span></span> <span data-ttu-id="5fc57-223">WPF grafik sistemi, CPU kullanımını en aza indirmek için grafik donanımından yararlanır.</span><span class="sxs-lookup"><span data-stu-id="5fc57-223">The WPF graphics system takes advantage of graphics hardware to minimize CPU usage.</span></span>

### <a name="2d-shapes"></a><span data-ttu-id="5fc57-224">2B şekiller</span><span class="sxs-lookup"><span data-stu-id="5fc57-224">2D shapes</span></span>

<span data-ttu-id="5fc57-225">WPF, aşağıdaki resimde gösterilen dikdörtgenler ve elipsler gibi ortak vektör çizilmiş 2B şekiller kitaplığı sağlar:</span><span class="sxs-lookup"><span data-stu-id="5fc57-225">WPF provides a library of common vector-drawn 2D shapes, such as the rectangles and ellipses that are shown in the following illustration:</span></span>

![Elipsler ve dikdörtgenler](media/introduction-to-wpf/wpfintrofigure4.PNG)

<span data-ttu-id="5fc57-227">Şekillerin ilginç bir yeteneği sadece görüntülemek için değil; şekiller, klavye ve fare girişi de dahil olmak üzere denetimlerden beklediğiniz birçok özelliği uygular.</span><span class="sxs-lookup"><span data-stu-id="5fc57-227">An interesting capability of shapes is that they are not just for display; shapes implement many of the features that you expect from controls, including keyboard and mouse input.</span></span> <span data-ttu-id="5fc57-228">Aşağıdaki örnek, <xref:System.Windows.UIElement.MouseUp> bir <xref:System.Windows.Shapes.Ellipse> işlenme olayını gösterir:</span><span class="sxs-lookup"><span data-stu-id="5fc57-228">The following example shows the <xref:System.Windows.UIElement.MouseUp> event of an <xref:System.Windows.Shapes.Ellipse> being handled:</span></span>

[!code-xaml[IntroToWPFSnippets#HandleEllipseMouseUpEventMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_7.xaml)]

[!code-vb[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_8.vb)]
[!code-csharp[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_8.cs)]

<span data-ttu-id="5fc57-229">Aşağıdaki şekil, önceki kod tarafından nelerin üretildiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="5fc57-229">The following figure shows what is produced by the preceding code:</span></span>

!["Elips&#33; tıkladınız" metninin yer verdiği bir pencere](media/introduction-to-wpf/wpfintrofigure12.png)

<span data-ttu-id="5fc57-231">Daha fazla bilgi için [WPF'ye genel bakışta Şekiller ve temel çizime](../../desktop-wpf/data/data-binding-overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="5fc57-231">For more information, see [Shapes and basic drawing in WPF overview](../../desktop-wpf/data/data-binding-overview.md).</span></span>

### <a name="2d-geometries"></a><span data-ttu-id="5fc57-232">2B geometriler</span><span class="sxs-lookup"><span data-stu-id="5fc57-232">2D geometries</span></span>

<span data-ttu-id="5fc57-233">WPF tarafından sağlanan 2B şekiller standart temel şekil kümesini kapsar.</span><span class="sxs-lookup"><span data-stu-id="5fc57-233">The 2D shapes provided by WPF cover the standard set of basic shapes.</span></span> <span data-ttu-id="5fc57-234">Ancak, özelleştirilmiş bir kullanıcı arabiriminin tasarımını kolaylaştırmak için özel şekiller oluşturmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-234">However, you may need to create custom shapes to facilitate the design of a customized user interface.</span></span> <span data-ttu-id="5fc57-235">Bu amaçla, WPF geometrisağlar.</span><span class="sxs-lookup"><span data-stu-id="5fc57-235">For this purpose, WPF provides geometries.</span></span> <span data-ttu-id="5fc57-236">Aşağıdaki şekil, doğrudan çizilebilen, fırça olarak kullanılabilen veya diğer şekil ve denetimleri kesmek için kullanılabilecek özel bir şekil oluşturmak için geometrilerin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-236">The following figure demonstrates the use of geometries to create a custom shape that can be drawn directly, used as a brush, or used to clip other shapes and controls.</span></span>

<span data-ttu-id="5fc57-237"><xref:System.Windows.Shapes.Path>nesneler kapalı veya açık şekiller, birden çok şekil ve hatta eğri şekiller çizmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-237"><xref:System.Windows.Shapes.Path> objects can be used to draw closed or open shapes, multiple shapes, and even curved shapes.</span></span>

<span data-ttu-id="5fc57-238"><xref:System.Windows.Media.Geometry>nesneler kırpma, isabet testi ve 2B grafik verilerini işlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-238"><xref:System.Windows.Media.Geometry> objects can be used for clipping, hit-testing, and rendering 2D graphic data.</span></span>

![Bir yolun çeşitli kullanımları](media/introduction-to-wpf/wpfintrofigure5.png)

<span data-ttu-id="5fc57-240">Daha fazla bilgi için [Geometri'ye genel bakış](graphics-multimedia/geometry-overview.md)bilgisine bakın.</span><span class="sxs-lookup"><span data-stu-id="5fc57-240">For more information, see [Geometry overview](graphics-multimedia/geometry-overview.md).</span></span>

### <a name="2d-effects"></a><span data-ttu-id="5fc57-241">2B efektler</span><span class="sxs-lookup"><span data-stu-id="5fc57-241">2D effects</span></span>

<span data-ttu-id="5fc57-242">WPF 2D yeteneklerinin bir alt kümesi, degradeler, bit eşlemler, çizimler, videolarla boyama, döndürme, ölçekleme ve eğrilme gibi görsel efektler içerir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-242">A subset of WPF 2D capabilities includes visual effects, such as gradients, bitmaps, drawings, painting with videos, rotation, scaling, and skewing.</span></span> <span data-ttu-id="5fc57-243">Bunların hepsi fırçalarla elde edilir; aşağıdaki şekil bazı örnekler gösterir:</span><span class="sxs-lookup"><span data-stu-id="5fc57-243">These are all achieved with brushes; the following figure shows some examples:</span></span>

![Farklı fırçaların çizimi](media/introduction-to-wpf/wpfintrofigure6.png)

<span data-ttu-id="5fc57-245">Daha fazla bilgi için [WPF fırçaları genel bakış](graphics-multimedia/wpf-brushes-overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="5fc57-245">For more information, see [WPF brushes overview](graphics-multimedia/wpf-brushes-overview.md).</span></span>

### <a name="3d-rendering"></a><span data-ttu-id="5fc57-246">3B işleme</span><span class="sxs-lookup"><span data-stu-id="5fc57-246">3D rendering</span></span>

<span data-ttu-id="5fc57-247">WPF ayrıca daha heyecan verici ve ilginç kullanıcı arabirimleri oluşturulmasına izin vermek için 2B grafik ile entegre 3D render yetenekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-247">WPF also includes 3D rendering capabilities that integrate with 2D graphics to allow the creation of more exciting and interesting user interfaces.</span></span> <span data-ttu-id="5fc57-248">Örneğin, aşağıdaki şekilde 3B şekiller üzerine işlenen 2B görüntüler gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="5fc57-248">For example, the following figure shows 2D images rendered onto 3D shapes:</span></span>

![Visual3D örnek ekran görüntüsü](media/introduction-to-wpf/wpfintrofigure13.png)

<span data-ttu-id="5fc57-250">Daha fazla bilgi için [3B grafiklere genel bakış](graphics-multimedia/3-d-graphics-overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="5fc57-250">For more information, see [3D graphics overview](graphics-multimedia/3-d-graphics-overview.md).</span></span>

## <a name="animation"></a><span data-ttu-id="5fc57-251">Animasyon</span><span class="sxs-lookup"><span data-stu-id="5fc57-251">Animation</span></span>

<span data-ttu-id="5fc57-252">WPF animasyon desteği, ilginç sayfa geçişleri ve daha fazlası oluşturmak için denetimlerin büyümesini, titremesini, dönmesini ve solmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fc57-252">WPF animation support lets you make controls grow, shake, spin, and fade, to create interesting page transitions, and more.</span></span> <span data-ttu-id="5fc57-253">Çoğu WPF sınıflarını, hatta özel sınıfları canlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fc57-253">You can animate most WPF classes, even custom classes.</span></span> <span data-ttu-id="5fc57-254">Aşağıdaki şekil, eylem basit bir animasyon gösterir:</span><span class="sxs-lookup"><span data-stu-id="5fc57-254">The following figure shows a simple animation in action:</span></span>

![Animasyonlu küpün görüntüleri](media/introduction-to-wpf/wpfintrofigure7.png)

<span data-ttu-id="5fc57-256">Daha fazla bilgi için [Animasyona genel bakış](graphics-multimedia/animation-overview.md)bilgisine bakın.</span><span class="sxs-lookup"><span data-stu-id="5fc57-256">For more information, see [Animation overview](graphics-multimedia/animation-overview.md).</span></span>

## <a name="media"></a><span data-ttu-id="5fc57-257">Medya</span><span class="sxs-lookup"><span data-stu-id="5fc57-257">Media</span></span>

<span data-ttu-id="5fc57-258">Zengin içerik iletmek için bir yolu görsel-işitsel medya kullanımı geçer.</span><span class="sxs-lookup"><span data-stu-id="5fc57-258">One way to convey rich content is through the use of audiovisual media.</span></span> <span data-ttu-id="5fc57-259">WPF görüntüler, video ve ses için özel destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fc57-259">WPF provides special support for images, video, and audio.</span></span>

### <a name="images"></a><span data-ttu-id="5fc57-260">Görüntüler</span><span class="sxs-lookup"><span data-stu-id="5fc57-260">Images</span></span>

<span data-ttu-id="5fc57-261">Görüntüler çoğu uygulamada yaygındır ve WPF bunları kullanmak için çeşitli yollar sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fc57-261">Images are common to most applications, and WPF provides several ways to use them.</span></span> <span data-ttu-id="5fc57-262">Aşağıdaki şekilde küçük resim görüntüleri içeren bir liste kutusu ile bir kullanıcı arabirimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-262">The following figure shows a user interface with a list box that contains thumbnail images.</span></span> <span data-ttu-id="5fc57-263">Küçük resim seçildiğinde, görüntü tam boyutlu olarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-263">When a thumbnail is selected, the image is shown full-size.</span></span>

![Küçük resim görüntüleri ve tam&#45;boyutunda görüntü](media/introduction-to-wpf/wpfintrofigure8.png)

<span data-ttu-id="5fc57-265">Daha fazla bilgi için [Görüntüleme genel görünümüne](graphics-multimedia/imaging-overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="5fc57-265">For more information, see [Imaging overview](graphics-multimedia/imaging-overview.md).</span></span>

### <a name="video-and-audio"></a><span data-ttu-id="5fc57-266">Video ve ses</span><span class="sxs-lookup"><span data-stu-id="5fc57-266">Video and audio</span></span>

<span data-ttu-id="5fc57-267">Denetim <xref:System.Windows.Controls.MediaElement> hem video hem de ses oynatma yeteneğine sahiptir ve özel bir medya oynatıcı için temel olacak kadar esnektir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-267">The <xref:System.Windows.Controls.MediaElement> control is capable of playing both video and audio, and it is flexible enough to be the basis for a custom media player.</span></span> <span data-ttu-id="5fc57-268">Aşağıdaki XAML biçimlendirmesi bir ortam oynatıcı uygular:</span><span class="sxs-lookup"><span data-stu-id="5fc57-268">The following XAML markup implements a media player:</span></span>

[!code-xaml[IntroToWPFSnippets#MediaElementMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_9.xaml)]

<span data-ttu-id="5fc57-269">Aşağıdaki şekildeki pencere, <xref:System.Windows.Controls.MediaElement> eylem denetimini gösterir:</span><span class="sxs-lookup"><span data-stu-id="5fc57-269">The window in the following figure shows the <xref:System.Windows.Controls.MediaElement> control in action:</span></span>

![Ses ve video ile MediaElement kontrolü](media/introduction-to-wpf/wpfintrofigure1.png)

<span data-ttu-id="5fc57-271">Daha fazla bilgi için [Grafik ve multimedya](graphics-multimedia/index.md)ya da</span><span class="sxs-lookup"><span data-stu-id="5fc57-271">For more information, see [Graphics and multimedia](graphics-multimedia/index.md).</span></span>

## <a name="text-and-typography"></a><span data-ttu-id="5fc57-272">Metin ve tipografi</span><span class="sxs-lookup"><span data-stu-id="5fc57-272">Text and typography</span></span>

<span data-ttu-id="5fc57-273">WPF, yüksek kaliteli metin oluşturmayı kolaylaştırmak için aşağıdaki özellikleri sunar:</span><span class="sxs-lookup"><span data-stu-id="5fc57-273">To facilitate high-quality text rendering, WPF offers the following features:</span></span>

- <span data-ttu-id="5fc57-274">OpenType yazı tipi desteği.</span><span class="sxs-lookup"><span data-stu-id="5fc57-274">OpenType font support.</span></span>

- <span data-ttu-id="5fc57-275">ClearType geliştirmeleri.</span><span class="sxs-lookup"><span data-stu-id="5fc57-275">ClearType enhancements.</span></span>

- <span data-ttu-id="5fc57-276">Donanım ivmesi avantajlarından yararlanan yüksek performans.</span><span class="sxs-lookup"><span data-stu-id="5fc57-276">High performance that takes advantage of hardware acceleration.</span></span>

- <span data-ttu-id="5fc57-277">Metnin medya, grafik ve animasyonla bütünleştirilmesi.</span><span class="sxs-lookup"><span data-stu-id="5fc57-277">Integration of text with media, graphics, and animation.</span></span>

- <span data-ttu-id="5fc57-278">Uluslararası yazı tipi desteği ve geri dönüş mekanizmaları.</span><span class="sxs-lookup"><span data-stu-id="5fc57-278">International font support and fallback mechanisms.</span></span>

<span data-ttu-id="5fc57-279">Grafikile metin entegrasyonunun bir göstergesi olarak, aşağıdaki şekil metin süslemeleri uygulamasını gösterir:</span><span class="sxs-lookup"><span data-stu-id="5fc57-279">As a demonstration of text integration with graphics, the following figure shows the application of text decorations:</span></span>

![Çeşitli metin süslemeleri ile Metin](media/introduction-to-wpf/wpfintrofigure23.png)

<span data-ttu-id="5fc57-281">Daha fazla bilgi için [Windows Presentation Foundation'da Tipografi'ye](advanced/typography-in-wpf.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="5fc57-281">For more information, see [Typography in Windows Presentation Foundation](advanced/typography-in-wpf.md).</span></span>

## <a name="customize-wpf-apps"></a><span data-ttu-id="5fc57-282">WPF uygulamalarını özelleştirin</span><span class="sxs-lookup"><span data-stu-id="5fc57-282">Customize WPF apps</span></span>

<span data-ttu-id="5fc57-283">Bu noktaya kadar, uygulamaları geliştirmek için temel WPF yapı taşlarını gördünüz.</span><span class="sxs-lookup"><span data-stu-id="5fc57-283">Up to this point, you've seen the core WPF building blocks for developing applications.</span></span> <span data-ttu-id="5fc57-284">Uygulama modelini, çoğunlukla denetimlerden oluşan uygulama içeriğini barındırmak ve sunmak için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="5fc57-284">You use the application model to host and deliver application content, which consists mainly of controls.</span></span> <span data-ttu-id="5fc57-285">Kullanıcı arabirimindeki denetimlerin düzenlenmesini kolaylaştırmak ve düzenlemenin pencere boyutu ve ekran ayarlarındaki değişiklikler karşısında tutulmasını sağlamak için WPF düzen sistemini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="5fc57-285">To simplify the arrangement of controls in a user interface, and to ensure the arrangement is maintained in the face of changes to window size and display settings, you use the WPF layout system.</span></span> <span data-ttu-id="5fc57-286">Çoğu uygulama kullanıcıların verilerle etkileşimkurmasına izin verdiğinden, kullanıcı arabiriminizi verilerle tümleştirme işini azaltmak için veri bağlamayı kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="5fc57-286">Because most applications let users interact with data, you use data binding to reduce the work of integrating your user interface with data.</span></span> <span data-ttu-id="5fc57-287">Uygulamanızın görsel görünümünü geliştirmek için WPF tarafından sağlanan kapsamlı grafik, animasyon ve ortam desteğini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="5fc57-287">To enhance the visual appearance of your application, you use the comprehensive range of graphics, animation, and media support provided by WPF.</span></span>

<span data-ttu-id="5fc57-288">Çoğu zaman, ancak, temel oluşturma ve gerçekten farklı ve görsel olarak çarpıcı kullanıcı deneyimi yönetmek için yeterli değildir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-288">Often, though, the basics are not enough for creating and managing a truly distinct and visually stunning user experience.</span></span> <span data-ttu-id="5fc57-289">Standart WPF denetimleri uygulamanızın istenen görünümüyle bütünleşmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-289">The standard WPF controls might not integrate with the desired appearance of your application.</span></span> <span data-ttu-id="5fc57-290">Veriler en etkili şekilde görüntülenmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-290">Data might not be displayed in the most effective way.</span></span> <span data-ttu-id="5fc57-291">Uygulamanızın genel kullanıcı deneyimi, Windows temalarının varsayılan görünümüne ve hissine uygun olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-291">Your application's overall user experience may not be suited to the default look and feel of Windows themes.</span></span> <span data-ttu-id="5fc57-292">Birçok yönden, bir sunum teknolojisi kadar genişletilebilirlik diğer tür olarak görsel genişletilebilirlik gerekir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-292">In many ways, a presentation technology needs visual extensibility as much as any other type of extensibility.</span></span>

<span data-ttu-id="5fc57-293">Bu nedenle WPF, denetimler, tetikleyiciler, denetim ve veri şablonları, stiller, kullanıcı arabirimi kaynakları ve temalar ve görünümler için zengin bir içerik modeli de dahil olmak üzere benzersiz kullanıcı deneyimleri oluşturmak için çeşitli mekanizmalar sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fc57-293">For this reason, WPF provides a variety of mechanisms for creating unique user experiences, including a rich content model for controls, triggers, control and data templates, styles, user interface resources, and themes and skins.</span></span>

### <a name="content-model"></a><span data-ttu-id="5fc57-294">İçerik modeli</span><span class="sxs-lookup"><span data-stu-id="5fc57-294">Content model</span></span>

<span data-ttu-id="5fc57-295">WPF denetimlerinin çoğunluğunun temel amacı içeriği görüntülemektir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-295">The main purpose of a majority of the WPF controls is to display content.</span></span> <span data-ttu-id="5fc57-296">WPF'de, denetimin içeriğini oluşturabilecek öğelerin türü ve sayısı denetimin *içerik modeli*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="5fc57-296">In WPF, the type and number of items that can constitute the content of a control is referred to as the control's *content model*.</span></span> <span data-ttu-id="5fc57-297">Bazı denetimler tek bir öğe ve içerik türü içerebilir; örneğin, a <xref:System.Windows.Controls.TextBox> içeriği <xref:System.Windows.Controls.TextBox.Text%2A> özelliğine atanan bir dize değeridir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-297">Some controls can contain a single item and type of content; for example, the content of a <xref:System.Windows.Controls.TextBox> is a string value that is assigned to the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span> <span data-ttu-id="5fc57-298">Aşağıdaki örnekte bir <xref:System.Windows.Controls.TextBox>içeriği n</span><span class="sxs-lookup"><span data-stu-id="5fc57-298">The following example sets the content of a <xref:System.Windows.Controls.TextBox>:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.TextBoxContentWindow"
    Title="TextBox Content">

    <TextBox Text="This is the content of a TextBox." />
</Window>
```

<span data-ttu-id="5fc57-299">Aşağıdaki şekil sonucu gösterir:</span><span class="sxs-lookup"><span data-stu-id="5fc57-299">The following figure shows the result:</span></span>

![Metin içeren textbox denetimi](media/introduction-to-wpf/wpfintrofigure21.png)

<span data-ttu-id="5fc57-301">Ancak diğer denetimler, farklı içerik türlerinde birden çok öğe içerebilir; özellik tarafından <xref:System.Windows.Controls.Button>belirtilen bir içeriğin içeriği, düzen denetimleri, metin, resim ve şekiller de dahil olmak üzere çeşitli öğeler içerebilir. <xref:System.Windows.Controls.ContentControl.Content%2A></span><span class="sxs-lookup"><span data-stu-id="5fc57-301">Other controls, however, can contain multiple items of different types of content; the content of a <xref:System.Windows.Controls.Button>, specified by the <xref:System.Windows.Controls.ContentControl.Content%2A> property, can contain a variety of items including layout controls, text, images, and shapes.</span></span> <span data-ttu-id="5fc57-302">Aşağıdaki örnek, <xref:System.Windows.Controls.Button> a , a <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Border>a ve <xref:System.Windows.Controls.MediaElement>a içeren içerikli bir</span><span class="sxs-lookup"><span data-stu-id="5fc57-302">The following example shows a <xref:System.Windows.Controls.Button> with content that includes a <xref:System.Windows.Controls.DockPanel>, a <xref:System.Windows.Controls.Label>, a <xref:System.Windows.Controls.Border>, and a <xref:System.Windows.Controls.MediaElement>:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.ButtonContentWindow"
    Title="Button Content">

  <Button Margin="20">
    <!-- Button Content -->
    <DockPanel Width="200" Height="180">
      <Label DockPanel.Dock="Top" HorizontalAlignment="Center">Click Me!</Label>
      <Border Background="Black" BorderBrush="Yellow" BorderThickness="2"
        CornerRadius="2" Margin="5">
        <MediaElement Source="media/wpf.wmv" Stretch="Fill" />
      </Border>
    </DockPanel>
  </Button>
</Window>
```

<span data-ttu-id="5fc57-303">Aşağıdaki şekil bu düğmenin içeriğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="5fc57-303">The following figure shows the content of this button:</span></span>

![Birden çok içerik türü içeren bir düğme](media/introduction-to-wpf/wpfintrofigure22.png)

<span data-ttu-id="5fc57-305">Çeşitli denetimler tarafından desteklenen içerik türleri hakkında daha fazla bilgi için [WPF içerik modeline](controls/wpf-content-model.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="5fc57-305">For more information on the kinds of content that is supported by various controls, see [WPF content model](controls/wpf-content-model.md).</span></span>

### <a name="triggers"></a><span data-ttu-id="5fc57-306">Tetikleyiciler</span><span class="sxs-lookup"><span data-stu-id="5fc57-306">Triggers</span></span>

<span data-ttu-id="5fc57-307">XAML biçimlendirmesinin temel amacı bir uygulamanın görünümünü uygulamak olsa da, bir uygulamanın davranışının bazı yönlerini uygulamak için XAML'yi de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fc57-307">Although the main purpose of XAML markup is to implement an application's appearance, you can also use XAML to implement some aspects of an application's behavior.</span></span> <span data-ttu-id="5fc57-308">Bir örnek, kullanıcı etkileşimlerine dayalı olarak bir uygulamanın görünümünü değiştirmek için tetikleyicilerin kullanılmasıdır.</span><span class="sxs-lookup"><span data-stu-id="5fc57-308">One example is the use of triggers to change an application's appearance based on user interactions.</span></span> <span data-ttu-id="5fc57-309">Daha fazla bilgi için [Stiller ve şablonlara](../../desktop-wpf/fundamentals/styles-templates-overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="5fc57-309">For more information, see [Styles and templates](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

### <a name="control-templates"></a><span data-ttu-id="5fc57-310">Denetim şablonları</span><span class="sxs-lookup"><span data-stu-id="5fc57-310">Control templates</span></span>

<span data-ttu-id="5fc57-311">WPF denetimleri için varsayılan kullanıcı arabirimleri genellikle diğer denetimlerden ve şekillerden oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5fc57-311">The default user interfaces for WPF controls are typically constructed from other controls and shapes.</span></span> <span data-ttu-id="5fc57-312">Örneğin, a <xref:System.Windows.Controls.Button> hem de <xref:Microsoft.Windows.Themes.ButtonChrome> <xref:System.Windows.Controls.ContentPresenter> denetimlerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="5fc57-312">For example, a <xref:System.Windows.Controls.Button> is composed of both <xref:Microsoft.Windows.Themes.ButtonChrome> and <xref:System.Windows.Controls.ContentPresenter> controls.</span></span> <span data-ttu-id="5fc57-313">Standart <xref:Microsoft.Windows.Themes.ButtonChrome> düğme görünümü sağlarken, <xref:System.Windows.Controls.ContentPresenter> özellik tarafından <xref:System.Windows.Controls.ContentControl.Content%2A> belirtildiği gibi düğmenin içeriğini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5fc57-313">The <xref:Microsoft.Windows.Themes.ButtonChrome> provides the standard button appearance, while the <xref:System.Windows.Controls.ContentPresenter> displays the button's content, as specified by the <xref:System.Windows.Controls.ContentControl.Content%2A> property.</span></span>

<span data-ttu-id="5fc57-314">Bazen denetimin varsayılan görünümü, bir uygulamanın genel görünümüyle uyumsuz olabilir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-314">Sometimes the default appearance of a control may be incongruent with the overall appearance of an application.</span></span> <span data-ttu-id="5fc57-315">Bu durumda, a'yı, <xref:System.Windows.Controls.ControlTemplate> içeriğini ve davranışını değiştirmeden denetimin kullanıcı arabiriminin görünümünü değiştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fc57-315">In this case, you can use a <xref:System.Windows.Controls.ControlTemplate> to change the appearance of the control's user interface without changing its content and behavior.</span></span>

<span data-ttu-id="5fc57-316">Aşağıdaki örnek, bir <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.ControlTemplate>aşağıdakileri kullanarak görünümün nasıl değiştirilebildiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="5fc57-316">The following example shows how to change the appearance of a <xref:System.Windows.Controls.Button> by using a <xref:System.Windows.Controls.ControlTemplate>:</span></span>

[!code-xaml[IntroToWPFSnippets#ButtonControlTemplateWindowMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_16.xaml)]

[!code-csharp[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_17.cs)]
[!code-vb[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_17.vb)]

<span data-ttu-id="5fc57-317">Bu örnekte, varsayılan düğme kullanıcı arabirimi <xref:System.Windows.Shapes.Ellipse> koyu mavi kenarlık lı bir <xref:System.Windows.Media.RadialGradientBrush>ile değiştirildi ve bir .</span><span class="sxs-lookup"><span data-stu-id="5fc57-317">In this example, the default button user interface has been replaced with an <xref:System.Windows.Shapes.Ellipse> that has a dark blue border and is filled using a <xref:System.Windows.Media.RadialGradientBrush>.</span></span> <span data-ttu-id="5fc57-318"><xref:System.Windows.Controls.Button>Denetim, <xref:System.Windows.Controls.ContentPresenter> "Beni tıklatın!" içeriğini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5fc57-318">The <xref:System.Windows.Controls.ContentPresenter> control displays the content of the <xref:System.Windows.Controls.Button>, "Click Me!"</span></span> <span data-ttu-id="5fc57-319"><xref:System.Windows.Controls.Button> Tıklatıldığında, olay denetimin <xref:System.Windows.Controls.Primitives.ButtonBase.Click> varsayılan davranışının <xref:System.Windows.Controls.Button> bir parçası olarak yine de yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-319">When the <xref:System.Windows.Controls.Button> is clicked, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event is still raised as part of the <xref:System.Windows.Controls.Button> control's default behavior.</span></span> <span data-ttu-id="5fc57-320">Sonuç aşağıdaki şekilde gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5fc57-320">The result is shown in the following figure:</span></span>

![Bir eliptik düğme ve ikinci bir pencere](media/introduction-to-wpf/wpfintrofigure2.png)

### <a name="data-templates"></a><span data-ttu-id="5fc57-322">Veri şablonları</span><span class="sxs-lookup"><span data-stu-id="5fc57-322">Data templates</span></span>

<span data-ttu-id="5fc57-323">Denetim şablonu denetimin görünümünü belirtmenize olanak sağlarken, veri şablonu denetimin içeriğinin görünümünü belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="5fc57-323">Whereas a control template lets you specify the appearance of a control, a data template lets you specify the appearance of a control's content.</span></span> <span data-ttu-id="5fc57-324">Veri şablonları, bağlı verilerin nasıl görüntüleneceğini geliştirmek için sık sık kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5fc57-324">Data templates are frequently used to enhance how bound data is displayed.</span></span> <span data-ttu-id="5fc57-325">Aşağıdaki şekil, her görevin <xref:System.Windows.Controls.ListBox> `Task` bir adı, açıklaması ve önceliği olan nesneler koleksiyonuna bağlı bir nesne için varsayılan görünümü gösterir:</span><span class="sxs-lookup"><span data-stu-id="5fc57-325">The following figure shows the default appearance for a <xref:System.Windows.Controls.ListBox> that is bound to a collection of `Task` objects, where each task has a name, description, and priority:</span></span>

![Varsayılan görünüme sahip bir liste kutusu](media/introduction-to-wpf/wpfintrofigure18.png)

<span data-ttu-id="5fc57-327">Varsayılan görünüm, bir <xref:System.Windows.Controls.ListBox>.'den beklediğiniz şeydir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-327">The default appearance is what you would expect from a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="5fc57-328">Ancak, her görevin varsayılan görünümü yalnızca görev adını içerir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-328">However, the default appearance of each task contains only the task name.</span></span> <span data-ttu-id="5fc57-329">Görev adını, açıklamayı ve önceliği göstermek için, <xref:System.Windows.Controls.ListBox> denetimin bağlı liste öğelerinin varsayılan <xref:System.Windows.DataTemplate>görünümünün bir .</span><span class="sxs-lookup"><span data-stu-id="5fc57-329">To show the task name, description, and priority, the default appearance of the <xref:System.Windows.Controls.ListBox> control's bound list items must be changed by using a <xref:System.Windows.DataTemplate>.</span></span> <span data-ttu-id="5fc57-330">Aşağıdaki XAML, özniteliği <xref:System.Windows.DataTemplate>kullanarak <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> her göreve uygulanan böyle bir , tanımlar:</span><span class="sxs-lookup"><span data-stu-id="5fc57-330">The following XAML defines such a <xref:System.Windows.DataTemplate>, which is applied to each task by using the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> attribute:</span></span>

```xaml
<Window
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  x:Class="SDKSample.DataTemplateWindow"
  Title="With a Data Template">
  <Window.Resources>
    <!-- Data Template (applied to each bound task item in the task collection) -->
    <DataTemplate x:Key="myTaskTemplate">
      <Border Name="border" BorderBrush="DarkSlateBlue" BorderThickness="2"
        CornerRadius="2" Padding="5" Margin="5">
        <Grid>
          <Grid.RowDefinitions>
            <RowDefinition/>
            <RowDefinition/>
            <RowDefinition/>
          </Grid.RowDefinitions>
          <Grid.ColumnDefinitions>
            <ColumnDefinition Width="Auto" />
            <ColumnDefinition />
          </Grid.ColumnDefinitions>
          <TextBlock Grid.Row="0" Grid.Column="0" Padding="0,0,5,0" Text="Task Name:"/>
          <TextBlock Grid.Row="0" Grid.Column="1" Text="{Binding Path=TaskName}"/>
          <TextBlock Grid.Row="1" Grid.Column="0" Padding="0,0,5,0" Text="Description:"/>
          <TextBlock Grid.Row="1" Grid.Column="1" Text="{Binding Path=Description}"/>
          <TextBlock Grid.Row="2" Grid.Column="0" Padding="0,0,5,0" Text="Priority:"/>
          <TextBlock Grid.Row="2" Grid.Column="1" Text="{Binding Path=Priority}"/>
        </Grid>
      </Border>
    </DataTemplate>
  </Window.Resources>

  <!-- UI -->
  <DockPanel>
    <!-- Title -->
    <Label DockPanel.Dock="Top" FontSize="18" Margin="5" Content="My Task List:"/>

    <!-- Data template is specified by the ItemTemplate attribute -->
    <ListBox
      ItemsSource="{Binding}"
      ItemTemplate="{StaticResource myTaskTemplate}"
      HorizontalContentAlignment="Stretch"
      IsSynchronizedWithCurrentItem="True"
      Margin="5,0,5,5" />

 </DockPanel>
</Window>
```

<span data-ttu-id="5fc57-331">Aşağıdaki şekil bu kodun etkisini gösterir:</span><span class="sxs-lookup"><span data-stu-id="5fc57-331">The following figure shows the effect of this code:</span></span>

![Veri şablonu kullanan liste kutusu](media/introduction-to-wpf/wpfintrofigure19.png)

<span data-ttu-id="5fc57-333">Davranışının <xref:System.Windows.Controls.ListBox> ve genel görünümünükoruduğunu unutmayın; yalnızca liste kutusu tarafından görüntülenen içeriğin görünümü değişti.</span><span class="sxs-lookup"><span data-stu-id="5fc57-333">Note that the <xref:System.Windows.Controls.ListBox> has retained its behavior and overall appearance; only the appearance of the content being displayed by the list box has changed.</span></span>

<span data-ttu-id="5fc57-334">Daha fazla bilgi için [bkz.](data/data-templating-overview.md)</span><span class="sxs-lookup"><span data-stu-id="5fc57-334">For more information, see [Data templating overview](data/data-templating-overview.md).</span></span>

### <a name="styles"></a><span data-ttu-id="5fc57-335">Stiller</span><span class="sxs-lookup"><span data-stu-id="5fc57-335">Styles</span></span>

<span data-ttu-id="5fc57-336">Stiller, geliştiricilerin ve tasarımcıların ürünleri için belirli bir görünümde standartlaştırmalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fc57-336">Styles enable developers and designers to standardize on a particular appearance for their product.</span></span> <span data-ttu-id="5fc57-337">WPF, temeli <xref:System.Windows.Style> öğe olan güçlü bir stil modeli sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fc57-337">WPF provides a strong style model, the foundation of which is the <xref:System.Windows.Style> element.</span></span> <span data-ttu-id="5fc57-338">Aşağıdaki örnek, penceredeki her biri <xref:System.Windows.Controls.Button> için arka plan `Orange`rengini aşağıdakilere ayarlayan bir stil oluşturur:</span><span class="sxs-lookup"><span data-stu-id="5fc57-338">The following example creates a style that sets the background color for every <xref:System.Windows.Controls.Button> on a window to `Orange`:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.StyleWindow"
    Title="Styles">
  <!-- Style that will be applied to all buttons -->
  <Style TargetType="{x:Type Button}">
    <Setter Property="Background" Value="Orange" />
    <Setter Property="BorderBrush" Value="Crimson" />
    <Setter Property="FontSize" Value="20" />
    <Setter Property="FontWeight" Value="Bold" />
    <Setter Property="Margin" Value="5" />
  </Style>
  <!-- This button will have the style applied to it -->
  <Button>Click Me!</Button>

  <!-- This label will not have the style applied to it -->
  <Label>Don't Click Me!</Label>

  <!-- This button will have the style applied to it -->
  <Button>Click Me!</Button>
</Window>
```

<span data-ttu-id="5fc57-339">Bu stil tüm <xref:System.Windows.Controls.Button> denetimleri hedeflediğinden, stil aşağıdaki şekilde gösterildiği gibi penceredeki tüm düğmelere otomatik olarak uygulanır:</span><span class="sxs-lookup"><span data-stu-id="5fc57-339">Because this style targets all <xref:System.Windows.Controls.Button> controls, the style is automatically applied to all the buttons in the window, as shown in the following figure:</span></span>

![İki turuncu düğme](media/introduction-to-wpf/wpfintrofigure20.png)

<span data-ttu-id="5fc57-341">Daha fazla bilgi için [Stiller ve şablonlara](../../desktop-wpf/fundamentals/styles-templates-overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="5fc57-341">For more information, see [Styles and templates](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

### <a name="resources"></a><span data-ttu-id="5fc57-342">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="5fc57-342">Resources</span></span>

<span data-ttu-id="5fc57-343">Bir uygulamadaki denetimler, yazı tiplerinden arka plan renklerinden şablonları, veri şablonlarını ve stilleri denetlemeye kadar her şeyi içerebilen aynı görünümü paylaşmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5fc57-343">Controls in an application should share the same appearance, which can include anything from fonts and background colors to control templates, data templates, and styles.</span></span> <span data-ttu-id="5fc57-344">WPF'nin kullanıcı arabirimi kaynakları için desteğini kullanarak bu kaynakları yeniden kullanmak üzere tek bir konumda saklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fc57-344">You can use WPF's support for user interface resources to encapsulate these resources in a single location for reuse.</span></span>

<span data-ttu-id="5fc57-345">Aşağıdaki örnek, a ve a <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Label>tarafından paylaşılan ortak bir arka plan rengini tanımlar:</span><span class="sxs-lookup"><span data-stu-id="5fc57-345">The following example defines a common background color that is shared by a <xref:System.Windows.Controls.Button> and a <xref:System.Windows.Controls.Label>:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.ResourcesWindow"
    Title="Resources Window">

  <!-- Define window-scoped background color resource -->
  <Window.Resources>
    <SolidColorBrush x:Key="defaultBackground" Color="Red" />
  </Window.Resources>

  <!-- Button background is defined by window-scoped resource -->
  <Button Background="{StaticResource defaultBackground}">One Button</Button>

  <!-- Label background is defined by window-scoped resource -->
  <Label Background="{StaticResource defaultBackground}">One Label</Label>
</Window>
```

<span data-ttu-id="5fc57-346">Bu örnek, özellik öğesini `Window.Resources` kullanarak bir arka plan renk kaynağı uygular.</span><span class="sxs-lookup"><span data-stu-id="5fc57-346">This example implements a background color resource by using the `Window.Resources` property element.</span></span> <span data-ttu-id="5fc57-347">Bu kaynak tüm çocuklar için <xref:System.Windows.Window>kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-347">This resource is available to all children of the <xref:System.Windows.Window>.</span></span> <span data-ttu-id="5fc57-348">Çözümlenme sırasına göre listelenen aşağıdakiler de dahil olmak üzere çeşitli kaynak kapsamları vardır:</span><span class="sxs-lookup"><span data-stu-id="5fc57-348">There are a variety of resource scopes, including the following, listed in the order in which they are resolved:</span></span>

1. <span data-ttu-id="5fc57-349">Bireysel denetim (devralınan <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> özelliği kullanarak).</span><span class="sxs-lookup"><span data-stu-id="5fc57-349">An individual control (using the inherited <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> property).</span></span>

2. <span data-ttu-id="5fc57-350">A <xref:System.Windows.Window> veya <xref:System.Windows.Controls.Page> a (ayrıca <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> devralınan özelliği kullanarak).</span><span class="sxs-lookup"><span data-stu-id="5fc57-350">A <xref:System.Windows.Window> or a <xref:System.Windows.Controls.Page> (also using the inherited <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> property).</span></span>

3. <span data-ttu-id="5fc57-351">Bir <xref:System.Windows.Application> <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> (özelliği kullanarak).</span><span class="sxs-lookup"><span data-stu-id="5fc57-351">An <xref:System.Windows.Application> (using the <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> property).</span></span>

<span data-ttu-id="5fc57-352">Kapsamların çeşitliliği, kaynaklarınızı tanımlama ve paylaşma biçiminize göre esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fc57-352">The variety of scopes gives you flexibility with respect to the way in which you define and share your resources.</span></span>

<span data-ttu-id="5fc57-353">Kaynaklarınızı belirli bir kapsamla doğrudan ilişkilendirmeye alternatif olarak, bir uygulamanın diğer <xref:System.Windows.ResourceDictionary> bölümlerinde başvurulabilecek ayrı bir kaynak kullanarak bir veya daha fazla kaynağı paketleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fc57-353">As an alternative to directly associating your resources with a particular scope, you can package one or more resources by using a separate <xref:System.Windows.ResourceDictionary> that can be referenced in other parts of an application.</span></span> <span data-ttu-id="5fc57-354">Örneğin, aşağıdaki örnek, kaynak sözlüğünde varsayılan arka plan rengini tanımlar:</span><span class="sxs-lookup"><span data-stu-id="5fc57-354">For example, the following example defines a default background color in a resource dictionary:</span></span>

```xaml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">

  <!-- Define background color resource -->
  <SolidColorBrush x:Key="defaultBackground" Color="Red" />

  <!-- Define other resources -->
</ResourceDictionary>
```

<span data-ttu-id="5fc57-355">Aşağıdaki örnek, bir uygulama arasında paylaşılabilmek için önceki örnekte tanımlanan kaynak sözlüğüne başvurur:</span><span class="sxs-lookup"><span data-stu-id="5fc57-355">The following example references the resource dictionary defined in the previous example so that it is shared across an application:</span></span>

```xaml
<Application
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.App">

  <Application.Resources>
    <ResourceDictionary>
      <ResourceDictionary.MergedDictionaries>
        <ResourceDictionary Source="BackgroundColorResources.xaml"/>
      </ResourceDictionary.MergedDictionaries>
    </ResourceDictionary>
  </Application.Resources>
</Application>
```

<span data-ttu-id="5fc57-356">Kaynaklar ve kaynak sözlükleri temalar ve görünümler için WPF desteğinin temelidir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-356">Resources and resource dictionaries are the foundation of WPF support for themes and skins.</span></span>

<span data-ttu-id="5fc57-357">Daha fazla bilgi için [Kaynaklar'a](../../desktop-wpf/fundamentals/xaml-resources-define.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="5fc57-357">For more information, see [Resources](../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>

### <a name="custom-controls"></a><span data-ttu-id="5fc57-358">Özel denetimler</span><span class="sxs-lookup"><span data-stu-id="5fc57-358">Custom controls</span></span>

<span data-ttu-id="5fc57-359">WPF bir dizi özelleştirme desteği sağlasa da, varolan WPF denetimlerinin uygulamanızın veya kullanıcılarının gereksinimlerini karşılamadığı durumlarla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fc57-359">Although WPF provides a host of customization support, you may encounter situations where existing WPF controls do not meet the needs of either your application or its users.</span></span> <span data-ttu-id="5fc57-360">Bu, şu anda oluşabilir:</span><span class="sxs-lookup"><span data-stu-id="5fc57-360">This can occur when:</span></span>

- <span data-ttu-id="5fc57-361">Gereksinim duyduğunuz kullanıcı arabirimi, varolan WPF uygulamalarının görünümünü ve hissini özelleştirerek oluşturulamaz.</span><span class="sxs-lookup"><span data-stu-id="5fc57-361">The user interface that you require cannot be created by customizing the look and feel of existing WPF implementations.</span></span>

- <span data-ttu-id="5fc57-362">Gereksinim duyduğunuz davranış, varolan WPF uygulamaları tarafından desteklenmez (veya kolayca desteklenmez).</span><span class="sxs-lookup"><span data-stu-id="5fc57-362">The behavior that you require is not supported (or not easily supported) by existing WPF implementations.</span></span>

<span data-ttu-id="5fc57-363">Ancak bu noktada, yeni bir denetim oluşturmak için üç WPF modelinden birinden yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fc57-363">At this point, however, you can take advantage of one of three WPF models to create a new control.</span></span> <span data-ttu-id="5fc57-364">Her model belirli bir senaryoyu hedefler ve belirli bir WPF taban sınıfından türeyen özel denetiminizin gerekli olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-364">Each model targets a specific scenario and requires your custom control to derive from a particular WPF base class.</span></span> <span data-ttu-id="5fc57-365">Üç model burada listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="5fc57-365">The three models are listed here:</span></span>

- <span data-ttu-id="5fc57-366">**Kullanıcı Kontrol Modeli**.</span><span class="sxs-lookup"><span data-stu-id="5fc57-366">**User Control Model**.</span></span> <span data-ttu-id="5fc57-367">Özel denetim, bir <xref:System.Windows.Controls.UserControl> veya daha fazla denetimden kaynaklanır ve bu denetimlerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="5fc57-367">A custom control derives from <xref:System.Windows.Controls.UserControl> and is composed of one or more other controls.</span></span>

- <span data-ttu-id="5fc57-368">**Kontrol Modeli**.</span><span class="sxs-lookup"><span data-stu-id="5fc57-368">**Control Model**.</span></span> <span data-ttu-id="5fc57-369">Özel denetim, WPF <xref:System.Windows.Controls.Control> denetimlerinin çoğu gibi şablonları kullanarak davranışlarını görünümlerinden ayıran uygulamalardan kaynaklanır ve oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5fc57-369">A custom control derives from <xref:System.Windows.Controls.Control> and is used to build implementations that separate their behavior from their appearance using templates, much like the majority of WPF controls.</span></span> <span data-ttu-id="5fc57-370">Türeyen <xref:System.Windows.Controls.Control> kaynak, kullanıcı denetimlerinden daha özel bir kullanıcı arabirimi oluşturmanıza daha fazla özgürlük sağlar, ancak daha fazla çaba gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-370">Deriving from <xref:System.Windows.Controls.Control> allows you more freedom for creating a custom user interface than user controls, but it may require more effort.</span></span>

- <span data-ttu-id="5fc57-371">**Çerçeve Öğesi Modeli**.</span><span class="sxs-lookup"><span data-stu-id="5fc57-371">**Framework Element Model**.</span></span> <span data-ttu-id="5fc57-372">Özel denetim, görünümünün <xref:System.Windows.FrameworkElement> özel işleme mantığıyla (şablonlar değil) tanımlandığından kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="5fc57-372">A custom control derives from <xref:System.Windows.FrameworkElement> when its appearance is defined by custom rendering logic (not templates).</span></span>

<span data-ttu-id="5fc57-373">Aşağıdaki örnek, aşağıdakilerden <xref:System.Windows.Controls.UserControl>türeyen özel bir sayısal yukarı/aşağı denetimi gösterir:</span><span class="sxs-lookup"><span data-stu-id="5fc57-373">The following example shows a custom numeric up/down control that derives from <xref:System.Windows.Controls.UserControl>:</span></span>

[!code-xaml[IntroToWPFSnippets#UserControlMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_33.xaml)]

[!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND1](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_34.cs)]
[!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND1](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_34.vb)]

<span data-ttu-id="5fc57-374">Aşağıdaki örnek, kullanıcı denetimini aşağıdaki <xref:System.Windows.Window>lere dahil etmek için gereken XAML'yi göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="5fc57-374">The following example illustrates the XAML that is required to incorporate the user control into a <xref:System.Windows.Window>:</span></span>

[!code-xaml[IntroToWPFSnippets#UserControlWindowMARKUP1](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_37.xaml)]

<span data-ttu-id="5fc57-375">Aşağıdaki şekilde barındırılan `NumericUpDown` denetim <xref:System.Windows.Window>gösterir:</span><span class="sxs-lookup"><span data-stu-id="5fc57-375">The following figure shows the `NumericUpDown` control hosted in a <xref:System.Windows.Window>:</span></span>

![Özel Bir UserControl](media/introduction-to-wpf/wpfintrofigure3.png)

<span data-ttu-id="5fc57-377">Özel denetimler hakkında daha fazla bilgi için [bkz.](controls/control-authoring-overview.md)</span><span class="sxs-lookup"><span data-stu-id="5fc57-377">For more information on custom controls, see [Control authoring overview](controls/control-authoring-overview.md).</span></span>

## <a name="wpf-best-practices"></a><span data-ttu-id="5fc57-378">WPF en iyi uygulamaları</span><span class="sxs-lookup"><span data-stu-id="5fc57-378">WPF best practices</span></span>

<span data-ttu-id="5fc57-379">Herhangi bir geliştirme platformunda olduğu gibi, WPF istenilen sonucu elde etmek için çeşitli şekillerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5fc57-379">As with any development platform, WPF can be used in a variety of ways to achieve the desired result.</span></span> <span data-ttu-id="5fc57-380">WPF uygulamalarınızın gerekli kullanıcı deneyimini sağlamasını ve genel olarak hedef kitlenin taleplerini karşılamasını sağlamanın bir yolu olarak, erişilebilirlik, küreselleşme ve yerelleştirme ve performans için önerilen en iyi uygulamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="5fc57-380">As a way of ensuring that your WPF applications provide the required user experience and meet the demands of the audience in general, there are recommended best practices for accessibility, globalization and localization, and performance.</span></span> <span data-ttu-id="5fc57-381">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="5fc57-381">For more information, see:</span></span>

- [<span data-ttu-id="5fc57-382">Erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="5fc57-382">Accessibility</span></span>](../ui-automation/accessibility-best-practices.md)
- [<span data-ttu-id="5fc57-383">WPF küreselleşmeve yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="5fc57-383">WPF globalization and localization</span></span>](advanced/wpf-globalization-and-localization-overview.md)
- [<span data-ttu-id="5fc57-384">WPF uygulama performansı</span><span class="sxs-lookup"><span data-stu-id="5fc57-384">WPF app performance</span></span>](advanced/optimizing-wpf-application-performance.md)
- [<span data-ttu-id="5fc57-385">WPF güvenliği</span><span class="sxs-lookup"><span data-stu-id="5fc57-385">WPF security</span></span>](security-wpf.md)

## <a name="next-steps"></a><span data-ttu-id="5fc57-386">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="5fc57-386">Next steps</span></span>

<span data-ttu-id="5fc57-387">WPF'nin temel özelliklerine baktık.</span><span class="sxs-lookup"><span data-stu-id="5fc57-387">We've looked at the key features of WPF.</span></span> <span data-ttu-id="5fc57-388">Şimdi ilk WPF uygulamanızı oluşturma zamanı.</span><span class="sxs-lookup"><span data-stu-id="5fc57-388">Now it's time to build your first WPF app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5fc57-389">Walkthrough: İlk WPF masaüstü uygulamam</span><span class="sxs-lookup"><span data-stu-id="5fc57-389">Walkthrough: My first WPF desktop app</span></span>](getting-started/walkthrough-my-first-wpf-desktop-application.md)

## <a name="see-also"></a><span data-ttu-id="5fc57-390">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5fc57-390">See also</span></span>

- [<span data-ttu-id="5fc57-391">WPF kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="5fc57-391">Get started with WPF</span></span>](getting-started/index.md)
- [<span data-ttu-id="5fc57-392">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="5fc57-392">Windows Presentation Foundation</span></span>](index.md)
- [<span data-ttu-id="5fc57-393">WPF topluluk kaynakları</span><span class="sxs-lookup"><span data-stu-id="5fc57-393">WPF community resources</span></span>](getting-started/community-feedback.md)
