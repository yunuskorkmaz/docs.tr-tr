---
title: WPF'ye Giriş
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b8d7cf43-d1f2-4f3d-adb0-4f3a6428edc0
dev_langs:
- csharp
- vb
ms.openlocfilehash: d8ea49bbe400c5ec478a94ad7c1adb759af28abb
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454199"
---
# <a name="wpf-overview"></a><span data-ttu-id="84122-102">WPF’ye genel bakış</span><span class="sxs-lookup"><span data-stu-id="84122-102">WPF overview</span></span>

<span data-ttu-id="84122-103">Windows Presentation Foundation (WPF), görsel açıdan etkileyici kullanıcı deneyimleri sayesinde Windows için masaüstü istemci uygulamaları oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="84122-103">Windows Presentation Foundation (WPF) lets you create desktop client applications for Windows with visually stunning user experiences.</span></span>

![Contoso sağlık Kullanıcı arabirimi örneği](media/introduction-to-wpf/wpfintrofigure24.png)

<span data-ttu-id="84122-105">WPF 'nin çekirdeği, modern grafik donanımının avantajlarından yararlanmak için oluşturulmuş, çözünürlükten bağımsız ve vektör tabanlı bir işleme altyapısıdır.</span><span class="sxs-lookup"><span data-stu-id="84122-105">The core of WPF is a resolution-independent and vector-based rendering engine that is built to take advantage of modern graphics hardware.</span></span> <span data-ttu-id="84122-106">WPF, Extensible Application Markup Language (XAML), denetimler, veri bağlama, düzen, 2B ve 3B grafikler, animasyon, stiller, şablonlar, belgeler, medya, metin ve baskı.</span><span class="sxs-lookup"><span data-stu-id="84122-106">WPF extends the core with a comprehensive set of application-development features that include Extensible Application Markup Language (XAML), controls, data binding, layout, 2D and 3D graphics, animation, styles, templates, documents, media, text, and typography.</span></span> <span data-ttu-id="84122-107">WPF .NET 'in bir parçası olduğundan, .NET API 'nin diğer öğelerini birleştiren uygulamalar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84122-107">WPF is part of .NET, so you can build applications that incorporate other elements of the .NET API.</span></span>

<span data-ttu-id="84122-108">Bu genel bakış, Newcomers 'e yöneliktir ve WPF 'in temel yeteneklerini ve kavramlarını ele alır.</span><span class="sxs-lookup"><span data-stu-id="84122-108">This overview is intended for newcomers and covers the key capabilities and concepts of WPF.</span></span>

## <a name="program-with-wpf"></a><span data-ttu-id="84122-109">WPF ile program</span><span class="sxs-lookup"><span data-stu-id="84122-109">Program with WPF</span></span>

<span data-ttu-id="84122-110">WPF, <xref:System.Windows> ad alanında bulunan (en fazla bölüm için) .NET türlerinin bir alt kümesi olarak mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="84122-110">WPF exists as a subset of .NET types that are (for the most part) located in the <xref:System.Windows> namespace.</span></span> <span data-ttu-id="84122-111">Daha önce ASP.NET ve Windows Forms gibi yönetilen teknolojiler kullanarak .NET ile uygulamalar oluşturduysanız, temel WPF programlama deneyimi tanıdık gelmelidir; , C# veya Visual Basic gibi en sevdiğiniz .NET programlama dilini kullanarak sınıfları örnekleyebilirsiniz, özellikleri ayarlar, yöntemleri çağırır ve olayları işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84122-111">If you have previously built applications with .NET using managed technologies like ASP.NET and Windows Forms, the fundamental WPF programming experience should be familiar; you instantiate classes, set properties, call methods, and handle events, using your favorite .NET programming language, such as C# or Visual Basic.</span></span>

<span data-ttu-id="84122-112">WPF, özellikleri ve olayları geliştiren ek programlama yapılarını içerir: [bağımlılık özellikleri](advanced/dependency-properties-overview.md) ve [yönlendirilmiş olaylar](advanced/routed-events-overview.md).</span><span class="sxs-lookup"><span data-stu-id="84122-112">WPF includes additional programming constructs that enhance properties and events: [dependency properties](advanced/dependency-properties-overview.md) and [routed events](advanced/routed-events-overview.md).</span></span>

## <a name="markup-and-code-behind"></a><span data-ttu-id="84122-113">Biçimlendirme ve arka plan kodu</span><span class="sxs-lookup"><span data-stu-id="84122-113">Markup and code-behind</span></span>

<span data-ttu-id="84122-114">WPF, ASP.NET geliştiricilerin tanıdık olması gereken bir deneyim olan hem *biçimlendirme* hem de *arka plan kodu*kullanarak bir uygulama geliştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="84122-114">WPF lets you develop an application using both *markup* and *code-behind*, an experience with which ASP.NET developers should be familiar.</span></span> <span data-ttu-id="84122-115">Genellikle XAML işaretlemesini kullanarak, davranışını uygulamak için yönetilen programlama dillerini (arka plan kod) kullanırken bir uygulamanın görünümünü uygulayın.</span><span class="sxs-lookup"><span data-stu-id="84122-115">You generally use XAML markup to implement the appearance of an application while using managed programming languages (code-behind) to implement its behavior.</span></span> <span data-ttu-id="84122-116">Bu görünüm ve davranışın ayrımı aşağıdaki avantajlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="84122-116">This separation of appearance and behavior has the following benefits:</span></span>

- <span data-ttu-id="84122-117">Görünüme özgü biçimlendirme davranışa özgü kodla sıkı bir şekilde bağlı olmadığından geliştirme ve bakım maliyetleri azaltılır.</span><span class="sxs-lookup"><span data-stu-id="84122-117">Development and maintenance costs are reduced because appearance-specific markup is not tightly coupled with behavior-specific code.</span></span>

- <span data-ttu-id="84122-118">Geliştiriciler uygulamanın davranışını uygulayan geliştiricilerle aynı anda bir uygulamanın görünümünü uygulayabildiğinden geliştirme daha etkilidir.</span><span class="sxs-lookup"><span data-stu-id="84122-118">Development is more efficient because designers can implement an application's appearance simultaneously with developers who are implementing the application's behavior.</span></span>

- <span data-ttu-id="84122-119">WPF uygulamaları için [Genelleştirme ve yerelleştirme](advanced/wpf-globalization-and-localization-overview.md) basitleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="84122-119">[Globalization and localization](advanced/wpf-globalization-and-localization-overview.md) for WPF applications is simplified.</span></span>

### <a name="markup"></a><span data-ttu-id="84122-120">Gösterilemeyen</span><span class="sxs-lookup"><span data-stu-id="84122-120">Markup</span></span>

<span data-ttu-id="84122-121">XAML, uygulamanın görünümünü bildirimli olarak uygulayan XML tabanlı bir biçimlendirme dilidir.</span><span class="sxs-lookup"><span data-stu-id="84122-121">XAML is an XML-based markup language that implements an application's appearance declaratively.</span></span> <span data-ttu-id="84122-122">Genellikle Windows, iletişim kutuları, sayfalar ve Kullanıcı denetimleri oluşturmak ve bunları denetimler, şekiller ve grafiklerle doldurmanız için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="84122-122">You typically use it to create windows, dialog boxes, pages, and user controls, and to fill them with controls, shapes, and graphics.</span></span>

<span data-ttu-id="84122-123">Aşağıdaki örnek, tek bir düğme içeren bir pencerenin görünümünü uygulamak için XAML kullanır:</span><span class="sxs-lookup"><span data-stu-id="84122-123">The following example uses XAML to implement the appearance of a window that contains a single button:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button">Click Me!</Button>

</Window>
```

<span data-ttu-id="84122-124">Özellikle, bu XAML, sırasıyla `Window` ve `Button` öğelerini kullanarak bir pencere ve bir düğme tanımlar.</span><span class="sxs-lookup"><span data-stu-id="84122-124">Specifically, this XAML defines a window and a button by using the `Window` and `Button` elements, respectively.</span></span> <span data-ttu-id="84122-125">Her öğe, pencerenin başlık çubuğu metnini belirtmek için `Window` öğenin `Title` özniteliği gibi özniteliklerle yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="84122-125">Each element is configured with attributes, such as the `Window` element's `Title` attribute to specify the window's title-bar text.</span></span> <span data-ttu-id="84122-126">Çalışma zamanında WPF, biçimlendirme içinde tanımlanan öğeleri ve öznitelikleri WPF sınıflarının örneklerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="84122-126">At run time, WPF converts the elements and attributes that are defined in markup to instances of WPF classes.</span></span> <span data-ttu-id="84122-127">Örneğin, `Window` öğesi, <xref:System.Windows.Window.Title%2A> özelliği `Title` özniteliğinin değeri olan <xref:System.Windows.Window> sınıfının bir örneğine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="84122-127">For example, the `Window` element is converted to an instance of the <xref:System.Windows.Window> class whose <xref:System.Windows.Window.Title%2A> property is the value of the `Title` attribute.</span></span>

<span data-ttu-id="84122-128">Aşağıdaki şekilde, önceki örnekte XAML tarafından tanımlanan Kullanıcı arabirimi (UI) gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="84122-128">The following figure shows the user interface (UI) that is defined by the XAML in the previous example:</span></span>

![Düğme içeren pencere](media/introduction-to-wpf/wpfintrofigure10.png)

<span data-ttu-id="84122-130">XAML, XML tabanlı olduğundan, onunla oluşturduğunuz Kullanıcı arabirimi bir [öğe ağacı](advanced/trees-in-wpf.md)olarak bilinen iç içe geçmiş öğelerin hiyerarşisinde toplanır.</span><span class="sxs-lookup"><span data-stu-id="84122-130">Since XAML is XML-based, the UI that you compose with it is assembled in a hierarchy of nested elements known as an [element tree](advanced/trees-in-wpf.md).</span></span> <span data-ttu-id="84122-131">Öğe ağacı, Usıs oluşturmak ve yönetmek için mantıksal ve sezgisel bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="84122-131">The element tree provides a logical and intuitive way to create and manage UIs.</span></span>

### <a name="code-behind"></a><span data-ttu-id="84122-132">Arka plan kodu</span><span class="sxs-lookup"><span data-stu-id="84122-132">Code-behind</span></span>

<span data-ttu-id="84122-133">Bir uygulamanın ana davranışı, olayları işleme (örneğin, bir menü, araç çubuğu veya düğme) ve yanıt olarak iş mantığı ve veri erişim mantığını çağırma dahil olmak üzere kullanıcı etkileşimlerine yanıt veren işlevselliği uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="84122-133">The main behavior of an application is to implement the functionality that responds to user interactions, including handling events (for example, clicking a menu, tool bar, or button) and calling business logic and data access logic in response.</span></span> <span data-ttu-id="84122-134">WPF 'de, bu davranış biçimlendirme ile ilişkili kodda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="84122-134">In WPF, this behavior is implemented in code that is associated with markup.</span></span> <span data-ttu-id="84122-135">Bu tür bir kod, arka plan kodu olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="84122-135">This type of code is known as code-behind.</span></span> <span data-ttu-id="84122-136">Aşağıdaki örnek, önceki örnekteki ve arka plan kodundaki güncelleştirilmiş biçimlendirmeyi gösterir:</span><span class="sxs-lookup"><span data-stu-id="84122-136">The following example shows the updated markup from the previous example and the code-behind:</span></span>

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

<span data-ttu-id="84122-137">Bu örnekte, arka plan kodu <xref:System.Windows.Window> sınıfından türetilen bir sınıf uygular.</span><span class="sxs-lookup"><span data-stu-id="84122-137">In this example, the code-behind implements a class that derives from the <xref:System.Windows.Window> class.</span></span> <span data-ttu-id="84122-138">`x:Class` özniteliği, biçimlendirmeyi arka plan kod sınıfıyla ilişkilendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="84122-138">The `x:Class` attribute is used to associate the markup with the code-behind class.</span></span> <span data-ttu-id="84122-139">`InitializeComponent`, arka plan kod sınıfı ile biçimlendirmede tanımlanan Kullanıcı arabirimini birleştirmek için arka plan kod sınıfından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="84122-139">`InitializeComponent` is called from the code-behind class's constructor to merge the UI that is defined in markup with the code-behind class.</span></span> <span data-ttu-id="84122-140">(`InitializeComponent`, uygulamanızın oluşturulduğu zaman sizin için oluşturulur, bu nedenle el ile uygulamanız gerekmez.) `x:Class` ve `InitializeComponent` birleşimi, uygulamanızın oluşturulduğu her seferinde doğru başlatılmış olmasını sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="84122-140">(`InitializeComponent` is generated for you when your application is built, which is why you don't need to implement it manually.) The combination of `x:Class` and `InitializeComponent` ensure that your implementation is correctly initialized whenever it is created.</span></span> <span data-ttu-id="84122-141">Arka plan kod sınıfı, düğmenin <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayı için bir olay işleyicisi de uygular.</span><span class="sxs-lookup"><span data-stu-id="84122-141">The code-behind class also implements an event handler for the button's <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event.</span></span> <span data-ttu-id="84122-142">Düğmeye tıklandığında, olay işleyicisi <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> yöntemini çağırarak bir ileti kutusu gösterir.</span><span class="sxs-lookup"><span data-stu-id="84122-142">When the button is clicked, the event handler shows a message box by calling the <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> method.</span></span>

<span data-ttu-id="84122-143">Aşağıdaki şekilde düğme tıklandığında sonuç gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="84122-143">The following figure shows the result when the button is clicked:</span></span>

![Bir MessageBox](media/introduction-to-wpf/wpfintrofigure25.png)

## <a name="controls"></a><span data-ttu-id="84122-145">Denetimler</span><span class="sxs-lookup"><span data-stu-id="84122-145">Controls</span></span>

<span data-ttu-id="84122-146">Uygulama modeli tarafından sunulan kullanıcı deneyimleri, oluşturulan denetimlerdir.</span><span class="sxs-lookup"><span data-stu-id="84122-146">The user experiences that are delivered by the application model are constructed controls.</span></span> <span data-ttu-id="84122-147">WPF 'de *Denetim* , bir pencere veya sayfada BARıNDıRıLAN bir WPF sınıfı kategorisi için geçerli olan ve bir kullanıcı arabirimine sahip olan ve bazı davranışları uygulayan bir şemsiye terimidir.</span><span class="sxs-lookup"><span data-stu-id="84122-147">In WPF, *control* is an umbrella term that applies to a category of WPF classes that are hosted in either a window or a page, have a user interface, and implement some behavior.</span></span>

<span data-ttu-id="84122-148">Daha fazla bilgi için bkz. [denetimler](controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="84122-148">For more information, see [Controls](controls/index.md).</span></span>

### <a name="wpf-controls-by-function"></a><span data-ttu-id="84122-149">İşleve göre WPF denetimleri</span><span class="sxs-lookup"><span data-stu-id="84122-149">WPF controls by function</span></span>

<span data-ttu-id="84122-150">Yerleşik WPF denetimleri burada listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="84122-150">The built-in WPF controls are listed here:</span></span>

- <span data-ttu-id="84122-151">**Düğmeler**: <xref:System.Windows.Controls.Button> ve <xref:System.Windows.Controls.Primitives.RepeatButton>.</span><span class="sxs-lookup"><span data-stu-id="84122-151">**Buttons**: <xref:System.Windows.Controls.Button> and <xref:System.Windows.Controls.Primitives.RepeatButton>.</span></span>

- <span data-ttu-id="84122-152">**Veri görüntüleme**: <xref:System.Windows.Controls.DataGrid>, <xref:System.Windows.Controls.ListView>ve <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="84122-152">**Data Display**: <xref:System.Windows.Controls.DataGrid>, <xref:System.Windows.Controls.ListView>, and <xref:System.Windows.Controls.TreeView>.</span></span>

- <span data-ttu-id="84122-153">**Tarih görüntüleme ve seçim**: <xref:System.Windows.Controls.Calendar> ve <xref:System.Windows.Controls.DatePicker>.</span><span class="sxs-lookup"><span data-stu-id="84122-153">**Date Display and Selection**: <xref:System.Windows.Controls.Calendar> and <xref:System.Windows.Controls.DatePicker>.</span></span>

- <span data-ttu-id="84122-154">**Iletişim kutuları**: <xref:Microsoft.Win32.OpenFileDialog>, <xref:System.Windows.Controls.PrintDialog> ve <xref:Microsoft.Win32.SaveFileDialog>.</span><span class="sxs-lookup"><span data-stu-id="84122-154">**Dialog Boxes**: <xref:Microsoft.Win32.OpenFileDialog>, <xref:System.Windows.Controls.PrintDialog>, and <xref:Microsoft.Win32.SaveFileDialog>.</span></span>

- <span data-ttu-id="84122-155">**Dijital mürekkep**: <xref:System.Windows.Controls.InkCanvas> ve <xref:System.Windows.Controls.InkPresenter>.</span><span class="sxs-lookup"><span data-stu-id="84122-155">**Digital Ink**: <xref:System.Windows.Controls.InkCanvas> and <xref:System.Windows.Controls.InkPresenter>.</span></span>

- <span data-ttu-id="84122-156">**Belgeler**: <xref:System.Windows.Controls.DocumentViewer>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentScrollViewer> ve <xref:System.Windows.Controls.StickyNoteControl>.</span><span class="sxs-lookup"><span data-stu-id="84122-156">**Documents**: <xref:System.Windows.Controls.DocumentViewer>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentScrollViewer>, and <xref:System.Windows.Controls.StickyNoteControl>.</span></span>

- <span data-ttu-id="84122-157">**Giriş**: <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox> ve <xref:System.Windows.Controls.PasswordBox>.</span><span class="sxs-lookup"><span data-stu-id="84122-157">**Input**: <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, and <xref:System.Windows.Controls.PasswordBox>.</span></span>

- <span data-ttu-id="84122-158">**Düzen**: <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Primitives.BulletDecorator>, <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Expander>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridSplitter>, <xref:System.Windows.Controls.GroupBox>, <xref:System.Windows.Controls.Panel>, <xref:System.Windows.Controls.Primitives.ResizeGrip>, <xref:System.Windows.Controls.Separator>, <xref:System.Windows.Controls.Primitives.ScrollBar>, <xref:System.Windows.Controls.ScrollViewer>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.Primitives.Thumb>, <xref:System.Windows.Controls.Viewbox>, <xref:System.Windows.Controls.VirtualizingStackPanel>, <xref:System.Windows.Window>ve <xref:System.Windows.Controls.WrapPanel>.</span><span class="sxs-lookup"><span data-stu-id="84122-158">**Layout**: <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Primitives.BulletDecorator>, <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Expander>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridSplitter>, <xref:System.Windows.Controls.GroupBox>, <xref:System.Windows.Controls.Panel>, <xref:System.Windows.Controls.Primitives.ResizeGrip>, <xref:System.Windows.Controls.Separator>, <xref:System.Windows.Controls.Primitives.ScrollBar>, <xref:System.Windows.Controls.ScrollViewer>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.Primitives.Thumb>, <xref:System.Windows.Controls.Viewbox>, <xref:System.Windows.Controls.VirtualizingStackPanel>, <xref:System.Windows.Window>, and <xref:System.Windows.Controls.WrapPanel>.</span></span>

- <span data-ttu-id="84122-159">**Medya**: <xref:System.Windows.Controls.Image>, <xref:System.Windows.Controls.MediaElement> ve <xref:System.Windows.Controls.SoundPlayerAction>.</span><span class="sxs-lookup"><span data-stu-id="84122-159">**Media**: <xref:System.Windows.Controls.Image>, <xref:System.Windows.Controls.MediaElement>, and <xref:System.Windows.Controls.SoundPlayerAction>.</span></span>

- <span data-ttu-id="84122-160">**Menüler**: <xref:System.Windows.Controls.ContextMenu>, <xref:System.Windows.Controls.Menu> ve <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="84122-160">**Menus**: <xref:System.Windows.Controls.ContextMenu>, <xref:System.Windows.Controls.Menu>, and <xref:System.Windows.Controls.ToolBar>.</span></span>

- <span data-ttu-id="84122-161">**Gezinti**: <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow> ve <xref:System.Windows.Controls.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="84122-161">**Navigation**: <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, and <xref:System.Windows.Controls.TabControl>.</span></span>

- <span data-ttu-id="84122-162">**Seçim**: <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.RadioButton> ve <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="84122-162">**Selection**: <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.RadioButton>, and <xref:System.Windows.Controls.Slider>.</span></span>

- <span data-ttu-id="84122-163">**Kullanıcı bilgileri**: <xref:System.Windows.Controls.AccessText>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.ProgressBar>, <xref:System.Windows.Controls.Primitives.StatusBar>, <xref:System.Windows.Controls.TextBlock> ve <xref:System.Windows.Controls.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="84122-163">**User Information**: <xref:System.Windows.Controls.AccessText>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.ProgressBar>, <xref:System.Windows.Controls.Primitives.StatusBar>, <xref:System.Windows.Controls.TextBlock>, and <xref:System.Windows.Controls.ToolTip>.</span></span>

## <a name="input-and-commands"></a><span data-ttu-id="84122-164">Giriş ve komutlar</span><span class="sxs-lookup"><span data-stu-id="84122-164">Input and commands</span></span>

<span data-ttu-id="84122-165">Denetimler çoğu zaman Kullanıcı girişini algılar ve yanıtlar.</span><span class="sxs-lookup"><span data-stu-id="84122-165">Controls most often detect and respond to user input.</span></span> <span data-ttu-id="84122-166">[WPF giriş sistemi](advanced/input-overview.md) metin girişi, odak yönetimi ve fare konumlandırmayı desteklemek için hem doğrudan hem de yönlendirilmiş olayları kullanır.</span><span class="sxs-lookup"><span data-stu-id="84122-166">The [WPF input system](advanced/input-overview.md) uses both direct and routed events to support text input, focus management, and mouse positioning.</span></span>

<span data-ttu-id="84122-167">Uygulamalar genellikle karmaşık giriş gereksinimlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="84122-167">Applications often have complex input requirements.</span></span> <span data-ttu-id="84122-168">WPF, Kullanıcı giriş eylemlerini bu eylemlere yanıt veren koddan ayıran bir [komut sistemi](advanced/commanding-overview.md) sağlar.</span><span class="sxs-lookup"><span data-stu-id="84122-168">WPF provides a [command system](advanced/commanding-overview.md) that separates user-input actions from the code that responds to those actions.</span></span>

## <a name="layout"></a><span data-ttu-id="84122-169">Düzen</span><span class="sxs-lookup"><span data-stu-id="84122-169">Layout</span></span>

<span data-ttu-id="84122-170">Bir kullanıcı arabirimi oluşturduğunuzda, bir düzen oluşturmak için denetimlerinizi konuma ve boyuta göre düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="84122-170">When you create a user interface, you arrange your controls by location and size to form a layout.</span></span> <span data-ttu-id="84122-171">Herhangi bir düzenin önemli bir gereksinimi, pencere boyutu ve görüntüleme ayarlarındaki değişikliklere uyum sağlar.</span><span class="sxs-lookup"><span data-stu-id="84122-171">A key requirement of any layout is to adapt to changes in window size and display settings.</span></span> <span data-ttu-id="84122-172">Bu koşullarda bir düzeni uyarlamak için kodu yazmanızı zorlamak yerine WPF, sizin için birinci sınıf bir Genişletilebilir düzen sistemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="84122-172">Rather than forcing you to write the code to adapt a layout in these circumstances, WPF provides a first-class, extensible layout system for you.</span></span>

<span data-ttu-id="84122-173">Düzen sisteminin temel taşı, değişen pencere ve görüntüleme koşullarına uyum sağlayan göreli konumlardır.</span><span class="sxs-lookup"><span data-stu-id="84122-173">The cornerstone of the layout system is relative positioning, which increases the ability to adapt to changing window and display conditions.</span></span> <span data-ttu-id="84122-174">Ayrıca, Düzen sistemi, düzeni belirleme denetimleri arasındaki anlaşmayı yönetir.</span><span class="sxs-lookup"><span data-stu-id="84122-174">In addition, the layout system manages the negotiation between controls to determine the layout.</span></span> <span data-ttu-id="84122-175">Anlaşma iki adımlı bir işlemdir: ilk olarak, bir denetim üst öğeye gereken konumu ve boyutu söyler; İkincisi, üst öğe denetime ne kadar boşluk yapabileceğini söyler.</span><span class="sxs-lookup"><span data-stu-id="84122-175">The negotiation is a two-step process: first, a control tells its parent what location and size it requires; second, the parent tells the control what space it can have.</span></span>

<span data-ttu-id="84122-176">Düzen sistemi, temel WPF sınıfları aracılığıyla alt denetimlere açıktır.</span><span class="sxs-lookup"><span data-stu-id="84122-176">The layout system is exposed to child controls through base WPF classes.</span></span> <span data-ttu-id="84122-177">WPF, yığınlama ve yerleştirme gibi ortak düzenler için çeşitli düzen denetimleri içerir:</span><span class="sxs-lookup"><span data-stu-id="84122-177">For common layouts such as grids, stacking, and docking, WPF includes several layout controls:</span></span>

- <span data-ttu-id="84122-178"><xref:System.Windows.Controls.Canvas>: alt denetimler kendi düzenlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="84122-178"><xref:System.Windows.Controls.Canvas>: Child controls provide their own layout.</span></span>

- <span data-ttu-id="84122-179"><xref:System.Windows.Controls.DockPanel>: alt denetimler panelin kenarlarına hizalanır.</span><span class="sxs-lookup"><span data-stu-id="84122-179"><xref:System.Windows.Controls.DockPanel>: Child controls are aligned to the edges of the panel.</span></span>

- <span data-ttu-id="84122-180"><xref:System.Windows.Controls.Grid>: alt denetimler satırlara ve sütunlara göre konumlandırılır.</span><span class="sxs-lookup"><span data-stu-id="84122-180"><xref:System.Windows.Controls.Grid>: Child controls are positioned by rows and columns.</span></span>

- <span data-ttu-id="84122-181"><xref:System.Windows.Controls.StackPanel>: alt denetimler dikey ya da yatay olarak yığılır.</span><span class="sxs-lookup"><span data-stu-id="84122-181"><xref:System.Windows.Controls.StackPanel>: Child controls are stacked either vertically or horizontally.</span></span>

- <span data-ttu-id="84122-182"><xref:System.Windows.Controls.VirtualizingStackPanel>: alt denetimler sanallaştırılır ve yatay veya dikey olarak yönelimli tek bir satırda düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="84122-182"><xref:System.Windows.Controls.VirtualizingStackPanel>: Child controls are virtualized and arranged on a single line that is either horizontally or vertically oriented.</span></span>

- <span data-ttu-id="84122-183"><xref:System.Windows.Controls.WrapPanel>: alt denetimler soldan sağa düzende konumlandırılır ve geçerli satırda alanın izin verdiğinden daha fazla denetim olduğunda sonraki satıra kaydırılır.</span><span class="sxs-lookup"><span data-stu-id="84122-183"><xref:System.Windows.Controls.WrapPanel>: Child controls are positioned in left-to-right order and wrapped to the next line when there are more controls on the current line than space allows.</span></span>

<span data-ttu-id="84122-184">Aşağıdaki örnek birkaç <xref:System.Windows.Controls.TextBox> denetimini düzenlemek için bir <xref:System.Windows.Controls.DockPanel> kullanır:</span><span class="sxs-lookup"><span data-stu-id="84122-184">The following example uses a <xref:System.Windows.Controls.DockPanel> to lay out several <xref:System.Windows.Controls.TextBox> controls:</span></span>

[!code-xaml[IntroToWPFSnippets#LayoutMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_1.xaml)]

<span data-ttu-id="84122-185"><xref:System.Windows.Controls.DockPanel>, alt <xref:System.Windows.Controls.TextBox> denetimlerinin nasıl düzenlendiğini anlatmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="84122-185">The <xref:System.Windows.Controls.DockPanel> allows the child <xref:System.Windows.Controls.TextBox> controls to tell it how to arrange them.</span></span> <span data-ttu-id="84122-186">Bunu yapmak için <xref:System.Windows.Controls.DockPanel>, her birinin bir yerleştirme stili belirtmesini sağlamak üzere alt denetimlere açık olan `Dock` iliştirilmiş bir özelliği uygular.</span><span class="sxs-lookup"><span data-stu-id="84122-186">To do this, the <xref:System.Windows.Controls.DockPanel> implements a `Dock` attached property that is exposed to the child controls to allow each of them to specify a dock style.</span></span>

> [!NOTE]
> <span data-ttu-id="84122-187">Alt denetimler tarafından kullanılmak üzere bir üst denetim tarafından uygulanan bir özellik, [iliştirilmiş özelliği](advanced/attached-properties-overview.md)olarak ADLANDıRıLAN bir WPF yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="84122-187">A property that's implemented by a parent control for use by child controls is a WPF construct called an [attached property](advanced/attached-properties-overview.md).</span></span>

<span data-ttu-id="84122-188">Aşağıdaki şekilde, önceki örnekteki XAML biçimlendirmesinin sonucu gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="84122-188">The following figure shows the result of the XAML markup in the preceding example:</span></span>

![DockPanel sayfası](media/introduction-to-wpf/wpfintrofigure11.png)

## <a name="data-binding"></a><span data-ttu-id="84122-190">Veri bağlama</span><span class="sxs-lookup"><span data-stu-id="84122-190">Data binding</span></span>

<span data-ttu-id="84122-191">Birçok uygulama, kullanıcılara verileri görüntüleme ve düzenleme araçlarını sağlamak için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="84122-191">Most applications are created to provide users with the means to view and edit data.</span></span> <span data-ttu-id="84122-192">WPF uygulamaları için, veri depolama ve erişme işi SQL Server ve ADO .NET gibi teknolojiler tarafından zaten sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="84122-192">For WPF applications, the work of storing and accessing data is already provided for by technologies such as SQL Server and ADO .NET.</span></span> <span data-ttu-id="84122-193">Verilere erişildikten ve uygulamanın yönetilen nesnelerine yüklendikten sonra, WPF uygulamalarına yönelik sabit çalışma başlar.</span><span class="sxs-lookup"><span data-stu-id="84122-193">After the data is accessed and loaded into an application's managed objects, the hard work for WPF applications begins.</span></span> <span data-ttu-id="84122-194">Temelde, bu iki şeyi içerir:</span><span class="sxs-lookup"><span data-stu-id="84122-194">Essentially, this involves two things:</span></span>

1. <span data-ttu-id="84122-195">Yönetilen nesnelerden verileri, verilerin görüntülenebildiği ve düzenlenebileceği denetimlere kopyalama.</span><span class="sxs-lookup"><span data-stu-id="84122-195">Copying the data from the managed objects into controls, where the data can be displayed and edited.</span></span>

2. <span data-ttu-id="84122-196">Denetimler kullanılarak verilerde yapılan değişikliklerin, yönetilen nesnelere geri kopyalanmasını sağlamak.</span><span class="sxs-lookup"><span data-stu-id="84122-196">Ensuring that changes made to data by using controls are copied back to the managed objects.</span></span>

<span data-ttu-id="84122-197">WPF, uygulama geliştirmeyi basitleştirmek için, bu adımları otomatik olarak gerçekleştirmek üzere bir veri bağlama altyapısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="84122-197">To simplify application development, WPF provides a data binding engine to automatically perform these steps.</span></span> <span data-ttu-id="84122-198">Veri bağlama altyapısının çekirdek birimi, işi bir denetimi (bağlama hedefi) bir veri nesnesine (bağlama kaynağı) bağlamak olan <xref:System.Windows.Data.Binding> sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="84122-198">The core unit of the data binding engine is the <xref:System.Windows.Data.Binding> class, whose job is to bind a control (the binding target) to a data object (the binding source).</span></span> <span data-ttu-id="84122-199">Bu ilişki aşağıdaki şekilde gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="84122-199">This relationship is illustrated by the following figure:</span></span>

![Temel veri bağlama diyagramı](media/introduction-to-wpf/databindingmostbasic.png)

<span data-ttu-id="84122-201">Sonraki örnekte, bir <xref:System.Windows.Controls.TextBox> özel bir `Person` nesnesinin örneğine nasıl bağlayacağınız gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="84122-201">The next example demonstrates how to bind a <xref:System.Windows.Controls.TextBox> to an instance of a custom `Person` object.</span></span> <span data-ttu-id="84122-202">`Person` uygulama aşağıdaki kodda gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="84122-202">The `Person` implementation is shown in the following code:</span></span>

[!code-vb[SimpleDataBindingSnippets#PersonClassCODE](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_2.vb)]
[!code-csharp[SimpleDataBindingSnippets#PersonClassCODE](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_2.cs)]

<span data-ttu-id="84122-203">Aşağıdaki biçimlendirme <xref:System.Windows.Controls.TextBox> özel bir `Person` nesnesinin örneğine bağlar:</span><span class="sxs-lookup"><span data-stu-id="84122-203">The following markup binds the <xref:System.Windows.Controls.TextBox> to an instance of a custom `Person` object:</span></span>

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

<span data-ttu-id="84122-204">Bu örnekte, `Person` sınıfı arka plan kodunda oluşturulur ve `DataBindingWindow` veri bağlamı olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="84122-204">In this example, the `Person` class is instantiated in code-behind and is set as the data context for the `DataBindingWindow`.</span></span> <span data-ttu-id="84122-205">Biçimlendirme ' de, <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.TextBox.Text%2A> özelliği `Person.Name` özelliğine bağımlıdır ("`{Binding ... }`" XAML sözdizimi kullanılarak).</span><span class="sxs-lookup"><span data-stu-id="84122-205">In markup, the <xref:System.Windows.Controls.TextBox.Text%2A> property of the <xref:System.Windows.Controls.TextBox> is bound to the `Person.Name` property (using the "`{Binding ... }`" XAML syntax).</span></span> <span data-ttu-id="84122-206">Bu XAML, WPF <xref:System.Windows.Controls.TextBox> denetimini pencerenin <xref:System.Windows.FrameworkElement.DataContext%2A> özelliğinde depolanan `Person` nesnesine bağlamasını söyler.</span><span class="sxs-lookup"><span data-stu-id="84122-206">This XAML tells WPF to bind the <xref:System.Windows.Controls.TextBox> control to the `Person` object that is stored in the <xref:System.Windows.FrameworkElement.DataContext%2A> property of the window.</span></span>

<span data-ttu-id="84122-207">WPF veri bağlama altyapısı, doğrulama, sıralama, filtreleme ve gruplamayı içeren ek destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="84122-207">The WPF data binding engine provides additional support that includes validation, sorting, filtering, and grouping.</span></span> <span data-ttu-id="84122-208">Ayrıca, veri bağlama, standart WPF denetimleri tarafından görüntülenecek kullanıcı arabirimi uygun olmadığında, bağlantılı veriler için özel kullanıcı arabirimi oluşturmak üzere veri şablonlarının kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="84122-208">Furthermore, data binding supports the use of data templates to create custom user interface for bound data when the user interface displayed by the standard WPF controls is not appropriate.</span></span>

<span data-ttu-id="84122-209">Daha fazla bilgi için bkz. [veri bağlamaya genel bakış](../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="84122-209">For more information, see [Data binding overview](../../desktop-wpf/data/data-binding-overview.md).</span></span>

## <a name="graphics"></a><span data-ttu-id="84122-210">Grafikler</span><span class="sxs-lookup"><span data-stu-id="84122-210">Graphics</span></span>

<span data-ttu-id="84122-211">WPF, aşağıdaki avantajları içeren kapsamlı, ölçeklenebilir ve esnek bir grafik özellikleri kümesi sunar:</span><span class="sxs-lookup"><span data-stu-id="84122-211">WPF introduces an extensive, scalable, and flexible set of graphics features that have the following benefits:</span></span>

- <span data-ttu-id="84122-212">**Çözünürlükten bağımsız ve cihazdan bağımsız grafikler**.</span><span class="sxs-lookup"><span data-stu-id="84122-212">**Resolution-independent and device-independent graphics**.</span></span> <span data-ttu-id="84122-213">WPF Grafik sistemindeki temel ölçü birimi, gerçek ekran çözünürlüğünden bağımsız olarak bir inç 1/96th olan cihazdan bağımsız pikseldir ve çözünürlükten bağımsız ve cihazdan bağımsız işleme için temel sağlar.</span><span class="sxs-lookup"><span data-stu-id="84122-213">The basic unit of measurement in the WPF graphics system is the device-independent pixel, which is 1/96th of an inch, regardless of actual screen resolution, and provides the foundation for resolution-independent and device-independent rendering.</span></span> <span data-ttu-id="84122-214">Her cihazdan bağımsız piksel, üzerinde oluşturduğu sistemin inç başına nokta (DPI) ayarıyla eşleşecek şekilde otomatik olarak ölçeklendirilir.</span><span class="sxs-lookup"><span data-stu-id="84122-214">Each device-independent pixel automatically scales to match the dots-per-inch (dpi) setting of the system it renders on.</span></span>

- <span data-ttu-id="84122-215">**İyileştirilmiş duyarlık**.</span><span class="sxs-lookup"><span data-stu-id="84122-215">**Improved precision**.</span></span> <span data-ttu-id="84122-216">WPF koordinat sistemi, tek duyarlık yerine çift duyarlıklı kayan noktalı sayılar ile ölçülür.</span><span class="sxs-lookup"><span data-stu-id="84122-216">The WPF coordinate system is measured with double-precision floating-point numbers rather than single-precision.</span></span> <span data-ttu-id="84122-217">Dönüşümler ve opaklık değerleri de çift duyarlıklı olarak ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="84122-217">Transformations and opacity values are also expressed as double-precision.</span></span> <span data-ttu-id="84122-218">WPF ayrıca geniş bir renk gamutu (scRGB) destekler ve farklı renk uzaylarından girişleri yönetmek için tümleşik destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="84122-218">WPF also supports a wide color gamut (scRGB) and provides integrated support for managing inputs from different color spaces.</span></span>

- <span data-ttu-id="84122-219">**Gelişmiş grafikler ve animasyon desteği**.</span><span class="sxs-lookup"><span data-stu-id="84122-219">**Advanced graphics and animation support**.</span></span> <span data-ttu-id="84122-220">WPF, sizin için animasyon sahneleri yöneterek grafik programlamayı basitleştirir; sahne işleme, işleme döngüleri ve Bilinear ilişkilendirme konusunda endişelenmenize gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="84122-220">WPF simplifies graphics programming by managing animation scenes for you; there is no need to worry about scene processing, rendering loops, and bilinear interpolation.</span></span> <span data-ttu-id="84122-221">Ayrıca WPF, isabet testi desteği ve tam alfa birleştirme desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="84122-221">Additionally, WPF provides hit-testing support and full alpha-compositing support.</span></span>

- <span data-ttu-id="84122-222">**Donanım hızlandırma**.</span><span class="sxs-lookup"><span data-stu-id="84122-222">**Hardware acceleration**.</span></span> <span data-ttu-id="84122-223">WPF Grafik sistemi, CPU kullanımını en aza indirmek için grafik donanımından yararlanır.</span><span class="sxs-lookup"><span data-stu-id="84122-223">The WPF graphics system takes advantage of graphics hardware to minimize CPU usage.</span></span>

### <a name="2d-shapes"></a><span data-ttu-id="84122-224">2B şekiller</span><span class="sxs-lookup"><span data-stu-id="84122-224">2D shapes</span></span>

<span data-ttu-id="84122-225">WPF, aşağıdaki çizimde gösterilen dikdörtgenler ve üç nokta gibi yaygın bir vektör çizilmiş 2B şekil kitaplığı sağlar:</span><span class="sxs-lookup"><span data-stu-id="84122-225">WPF provides a library of common vector-drawn 2D shapes, such as the rectangles and ellipses that are shown in the following illustration:</span></span>

![Üç nokta ve dikdörtgen](media/introduction-to-wpf/wpfintrofigure4.PNG)

<span data-ttu-id="84122-227">Şekillerin ilginç bir özelliği yalnızca görüntüleme için değildir; şekiller, klavye ve fare girişi dahil olmak üzere denetimlerden beklediğinizi birçok özelliği uygular.</span><span class="sxs-lookup"><span data-stu-id="84122-227">An interesting capability of shapes is that they are not just for display; shapes implement many of the features that you expect from controls, including keyboard and mouse input.</span></span> <span data-ttu-id="84122-228">Aşağıdaki örnek, işlenmekte olan bir <xref:System.Windows.Shapes.Ellipse> <xref:System.Windows.UIElement.MouseUp> olayını gösterir:</span><span class="sxs-lookup"><span data-stu-id="84122-228">The following example shows the <xref:System.Windows.UIElement.MouseUp> event of an <xref:System.Windows.Shapes.Ellipse> being handled:</span></span>

[!code-xaml[IntroToWPFSnippets#HandleEllipseMouseUpEventMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_7.xaml)]

[!code-vb[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_8.vb)]
[!code-csharp[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_8.cs)]

<span data-ttu-id="84122-229">Aşağıdaki şekilde, önceki kod tarafından üretilen değer gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="84122-229">The following figure shows what is produced by the preceding code:</span></span>

!["Elips&#33;tıkladınız" metnini içeren pencere](media/introduction-to-wpf/wpfintrofigure12.png)

<span data-ttu-id="84122-231">Daha fazla bilgi için bkz. [WPF 'de şekillere ve temel çizime genel bakış](../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="84122-231">For more information, see [Shapes and basic drawing in WPF overview](../../desktop-wpf/data/data-binding-overview.md).</span></span>

### <a name="2d-geometries"></a><span data-ttu-id="84122-232">2B geometriler</span><span class="sxs-lookup"><span data-stu-id="84122-232">2D geometries</span></span>

<span data-ttu-id="84122-233">WPF tarafından sunulan 2B şekiller, temel şekillerin standart kümesini kapsar.</span><span class="sxs-lookup"><span data-stu-id="84122-233">The 2D shapes provided by WPF cover the standard set of basic shapes.</span></span> <span data-ttu-id="84122-234">Ancak, özelleştirilmiş bir kullanıcı arabiriminin tasarımını kolaylaştırmak için özel şekiller oluşturmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="84122-234">However, you may need to create custom shapes to facilitate the design of a customized user interface.</span></span> <span data-ttu-id="84122-235">Bu amaçla WPF, geometriler sağlar.</span><span class="sxs-lookup"><span data-stu-id="84122-235">For this purpose, WPF provides geometries.</span></span> <span data-ttu-id="84122-236">Aşağıdaki şekilde, doğrudan çizilemeyen, fırça olarak kullanılan veya diğer şekilleri ve denetimleri kırpmak için kullanılan özel bir şekil oluşturmak için geometriler kullanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="84122-236">The following figure demonstrates the use of geometries to create a custom shape that can be drawn directly, used as a brush, or used to clip other shapes and controls.</span></span>

<span data-ttu-id="84122-237"><xref:System.Windows.Shapes.Path> nesneler, kapalı veya açık şekiller, birden çok şekil ve hatta eğri şekiller çizmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="84122-237"><xref:System.Windows.Shapes.Path> objects can be used to draw closed or open shapes, multiple shapes, and even curved shapes.</span></span>

<span data-ttu-id="84122-238"><xref:System.Windows.Media.Geometry> nesneler kırpma, isabet testi ve 2B grafik verileri işleme için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="84122-238"><xref:System.Windows.Media.Geometry> objects can be used for clipping, hit-testing, and rendering 2D graphic data.</span></span>

![Yolun çeşitli kullanımları](media/introduction-to-wpf/wpfintrofigure5.png)

<span data-ttu-id="84122-240">Daha fazla bilgi için bkz. [geometriye genel bakış](graphics-multimedia/geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="84122-240">For more information, see [Geometry overview](graphics-multimedia/geometry-overview.md).</span></span>

### <a name="2d-effects"></a><span data-ttu-id="84122-241">2B efektler</span><span class="sxs-lookup"><span data-stu-id="84122-241">2D effects</span></span>

<span data-ttu-id="84122-242">WPF 2B özellikleri alt kümesi degradeler, bit eşlemler, çizimler, videolar, döndürme, ölçeklendirme ve eğriltme gibi görsel etkileri içerir.</span><span class="sxs-lookup"><span data-stu-id="84122-242">A subset of WPF 2D capabilities includes visual effects, such as gradients, bitmaps, drawings, painting with videos, rotation, scaling, and skewing.</span></span> <span data-ttu-id="84122-243">Bunlar fırçalar ile elde edilir; Aşağıdaki şekilde bazı örnekler gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="84122-243">These are all achieved with brushes; the following figure shows some examples:</span></span>

![Farklı fırçaların çizimi](media/introduction-to-wpf/wpfintrofigure6.png)

<span data-ttu-id="84122-245">Daha fazla bilgi için bkz. [WPF Fırçalarına Genel Bakış](graphics-multimedia/wpf-brushes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="84122-245">For more information, see [WPF brushes overview](graphics-multimedia/wpf-brushes-overview.md).</span></span>

### <a name="3d-rendering"></a><span data-ttu-id="84122-246">3B işleme</span><span class="sxs-lookup"><span data-stu-id="84122-246">3D rendering</span></span>

<span data-ttu-id="84122-247">WPF ayrıca, daha heyecan verici ve ilginç Kullanıcı arabirimleri oluşturulmasına olanak tanımak için 2-b grafiklerle tümleştirilen 3B işleme özelliklerini de içerir.</span><span class="sxs-lookup"><span data-stu-id="84122-247">WPF also includes 3D rendering capabilities that integrate with 2-d graphics to allow the creation of more exciting and interesting user interfaces.</span></span> <span data-ttu-id="84122-248">Örneğin, aşağıdaki şekilde 3B şekiller üzerinde işlenen 2D görüntüleri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="84122-248">For example, the following figure shows 2D images rendered onto 3D shapes:</span></span>

![Visual3d değil örnek ekran görüntüsü](media/introduction-to-wpf/wpfintrofigure13.png)

<span data-ttu-id="84122-250">Daha fazla bilgi için bkz. [3B grafiklere genel bakış](graphics-multimedia/3-d-graphics-overview.md).</span><span class="sxs-lookup"><span data-stu-id="84122-250">For more information, see [3D graphics overview](graphics-multimedia/3-d-graphics-overview.md).</span></span>

## <a name="animation"></a><span data-ttu-id="84122-251">Animasyon</span><span class="sxs-lookup"><span data-stu-id="84122-251">Animation</span></span>

<span data-ttu-id="84122-252">WPF animasyon desteği, denetimlerin büyümesi, sallanması, dönmesi ve belirmesini, ilginç sayfa geçişleri oluşturmak ve daha fazlasını yapmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="84122-252">WPF animation support lets you make controls grow, shake, spin, and fade, to create interesting page transitions, and more.</span></span> <span data-ttu-id="84122-253">Birçok WPF sınıfının, hatta özel sınıfların animasyonunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84122-253">You can animate most WPF classes, even custom classes.</span></span> <span data-ttu-id="84122-254">Aşağıdaki şekilde, eylem içinde basit bir animasyon gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="84122-254">The following figure shows a simple animation in action:</span></span>

![Animasyonlu küpün görüntüleri](media/introduction-to-wpf/wpfintrofigure7.png)

<span data-ttu-id="84122-256">Daha fazla bilgi için bkz. [animasyon genel bakış](graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="84122-256">For more information, see [Animation overview](graphics-multimedia/animation-overview.md).</span></span>

## <a name="media"></a><span data-ttu-id="84122-257">Medyasını</span><span class="sxs-lookup"><span data-stu-id="84122-257">Media</span></span>

<span data-ttu-id="84122-258">Zengin içerik iletmenin bir yolu, Audiovisual medyası kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="84122-258">One way to convey rich content is through the use of audiovisual media.</span></span> <span data-ttu-id="84122-259">WPF, görüntüler, videolar ve ses için özel destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="84122-259">WPF provides special support for images, video, and audio.</span></span>

### <a name="images"></a><span data-ttu-id="84122-260">Görüntüler</span><span class="sxs-lookup"><span data-stu-id="84122-260">Images</span></span>

<span data-ttu-id="84122-261">Görüntüler çoğu uygulama için ortaktır ve WPF bunları kullanmak için çeşitli yollar sağlar.</span><span class="sxs-lookup"><span data-stu-id="84122-261">Images are common to most applications, and WPF provides several ways to use them.</span></span> <span data-ttu-id="84122-262">Aşağıdaki şekilde, küçük resim görüntüleri içeren bir liste kutusuyla bir kullanıcı arabirimi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="84122-262">The following figure shows a user interface with a list box that contains thumbnail images.</span></span> <span data-ttu-id="84122-263">Küçük resim seçildiğinde görüntü tam boyut olarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="84122-263">When a thumbnail is selected, the image is shown full-size.</span></span>

![Küçük resim görüntüleri ve tam&#45;boyut görüntüsü](media/introduction-to-wpf/wpfintrofigure8.png)

<span data-ttu-id="84122-265">Daha fazla bilgi için bkz. [Imaging 'e genel bakış](graphics-multimedia/imaging-overview.md).</span><span class="sxs-lookup"><span data-stu-id="84122-265">For more information, see [Imaging overview](graphics-multimedia/imaging-overview.md).</span></span>

### <a name="video-and-audio"></a><span data-ttu-id="84122-266">Video ve ses</span><span class="sxs-lookup"><span data-stu-id="84122-266">Video and audio</span></span>

<span data-ttu-id="84122-267"><xref:System.Windows.Controls.MediaElement> denetimi hem videoyu hem de sesi oynatabilen ve özel bir medya yürütücüsünün temeli olması yeterince esnektir.</span><span class="sxs-lookup"><span data-stu-id="84122-267">The <xref:System.Windows.Controls.MediaElement> control is capable of playing both video and audio, and it is flexible enough to be the basis for a custom media player.</span></span> <span data-ttu-id="84122-268">Aşağıdaki XAML biçimlendirmesi bir medya oynatıcı uygular:</span><span class="sxs-lookup"><span data-stu-id="84122-268">The following XAML markup implements a media player:</span></span>

[!code-xaml[IntroToWPFSnippets#MediaElementMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_9.xaml)]

<span data-ttu-id="84122-269">Aşağıdaki şekilde gösterilen pencerede <xref:System.Windows.Controls.MediaElement> denetim eylemi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="84122-269">The window in the following figure shows the <xref:System.Windows.Controls.MediaElement> control in action:</span></span>

![Ses ve video ile MediaElement denetimi](media/introduction-to-wpf/wpfintrofigure1.png)

<span data-ttu-id="84122-271">Daha fazla bilgi için bkz. [grafik ve multimedya](graphics-multimedia/index.md).</span><span class="sxs-lookup"><span data-stu-id="84122-271">For more information, see [Graphics and multimedia](graphics-multimedia/index.md).</span></span>

## <a name="text-and-typography"></a><span data-ttu-id="84122-272">Metin ve tipografi</span><span class="sxs-lookup"><span data-stu-id="84122-272">Text and typography</span></span>

<span data-ttu-id="84122-273">WPF, yüksek kaliteli metin işlemesini kolaylaştırmak için aşağıdaki özellikleri sunar:</span><span class="sxs-lookup"><span data-stu-id="84122-273">To facilitate high-quality text rendering, WPF offers the following features:</span></span>

- <span data-ttu-id="84122-274">OpenType yazı tipi desteği.</span><span class="sxs-lookup"><span data-stu-id="84122-274">OpenType font support.</span></span>

- <span data-ttu-id="84122-275">ClearType geliştirmeleri.</span><span class="sxs-lookup"><span data-stu-id="84122-275">ClearType enhancements.</span></span>

- <span data-ttu-id="84122-276">Donanım hızlandırmasının avantajlarından yararlanan yüksek performans.</span><span class="sxs-lookup"><span data-stu-id="84122-276">High performance that takes advantage of hardware acceleration.</span></span>

- <span data-ttu-id="84122-277">Medya, grafik ve animasyonla metin tümleştirmesi.</span><span class="sxs-lookup"><span data-stu-id="84122-277">Integration of text with media, graphics, and animation.</span></span>

- <span data-ttu-id="84122-278">Uluslararası yazı tipi desteği ve geri dönüş mekanizmaları.</span><span class="sxs-lookup"><span data-stu-id="84122-278">International font support and fallback mechanisms.</span></span>

<span data-ttu-id="84122-279">Grafiklerle metin tümleştirmesinin bir sunumu olarak aşağıdaki şekil metin düzenlemelerinin uygulamasını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="84122-279">As a demonstration of text integration with graphics, the following figure shows the application of text decorations:</span></span>

![Çeşitli metin süslemeleri içeren metin](media/introduction-to-wpf/wpfintrofigure23.png)

<span data-ttu-id="84122-281">Daha fazla bilgi için bkz. [tipografi Windows Presentation Foundation](advanced/typography-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="84122-281">For more information, see [Typography in Windows Presentation Foundation](advanced/typography-in-wpf.md).</span></span>

## <a name="customize-wpf-apps"></a><span data-ttu-id="84122-282">WPF uygulamalarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="84122-282">Customize WPF apps</span></span>

<span data-ttu-id="84122-283">Bu noktaya kadar, uygulama geliştirmeye yönelik temel WPF yapı taşlarını gördünüz.</span><span class="sxs-lookup"><span data-stu-id="84122-283">Up to this point, you've seen the core WPF building blocks for developing applications.</span></span> <span data-ttu-id="84122-284">Genellikle denetimlerden oluşan uygulama içeriğini barındırmak ve sunmak için uygulama modelini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="84122-284">You use the application model to host and deliver application content, which consists mainly of controls.</span></span> <span data-ttu-id="84122-285">Bir kullanıcı arabirimindeki denetimlerin düzenlemesini basitleştirmek ve düzenlemenin pencere boyutu ve görüntüleme ayarlarında yapılan değişiklikler üzerinde tutulmasını sağlamak için WPF düzen sistemini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="84122-285">To simplify the arrangement of controls in a user interface, and to ensure the arrangement is maintained in the face of changes to window size and display settings, you use the WPF layout system.</span></span> <span data-ttu-id="84122-286">Çoğu uygulama, kullanıcıların verilerle etkileşime girmesine izin vertiğinden, Kullanıcı arabiriminizi verilerle tümleştirme işini azaltmak için veri bağlamayı kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="84122-286">Because most applications let users interact with data, you use data binding to reduce the work of integrating your user interface with data.</span></span> <span data-ttu-id="84122-287">Uygulamanızın görsel görünümünü geliştirmek için WPF tarafından sunulan kapsamlı grafik, animasyon ve medya desteği aralığını kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="84122-287">To enhance the visual appearance of your application, you use the comprehensive range of graphics, animation, and media support provided by WPF.</span></span>

<span data-ttu-id="84122-288">Genellikle, temel bilgiler, gerçekten ayrı ve görsel açıdan etkileyici bir kullanıcı deneyimi oluşturmak ve yönetmek için yeterli değildir.</span><span class="sxs-lookup"><span data-stu-id="84122-288">Often, though, the basics are not enough for creating and managing a truly distinct and visually stunning user experience.</span></span> <span data-ttu-id="84122-289">Standart WPF denetimleri uygulamanızın istenen görünümüyle tümleştirilemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="84122-289">The standard WPF controls might not integrate with the desired appearance of your application.</span></span> <span data-ttu-id="84122-290">Veriler en etkili şekilde görüntülenmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="84122-290">Data might not be displayed in the most effective way.</span></span> <span data-ttu-id="84122-291">Uygulamanızın genel kullanıcı deneyimi, Windows temalarının varsayılan görünümü ve hislerine uygun olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="84122-291">Your application's overall user experience may not be suited to the default look and feel of Windows themes.</span></span> <span data-ttu-id="84122-292">Birçok şekilde, bir sunum teknolojisinin diğer genişletilebilirlik türleri kadar çok görsel genişletilebilirliği olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="84122-292">In many ways, a presentation technology needs visual extensibility as much as any other type of extensibility.</span></span>

<span data-ttu-id="84122-293">Bu nedenle WPF, denetimler, Tetikleyiciler, denetim ve veri şablonları, stiller, Kullanıcı arabirimi kaynakları ve Temalar ve kaplamalar için zengin bir içerik modeli de dahil olmak üzere benzersiz kullanıcı deneyimleri oluşturmak için çeşitli mekanizmalar sunar.</span><span class="sxs-lookup"><span data-stu-id="84122-293">For this reason, WPF provides a variety of mechanisms for creating unique user experiences, including a rich content model for controls, triggers, control and data templates, styles, user interface resources, and themes and skins.</span></span>

### <a name="content-model"></a><span data-ttu-id="84122-294">İçerik modeli</span><span class="sxs-lookup"><span data-stu-id="84122-294">Content model</span></span>

<span data-ttu-id="84122-295">WPF denetimlerinin çoğunluğunun ana amacı içeriği görüntülemektir.</span><span class="sxs-lookup"><span data-stu-id="84122-295">The main purpose of a majority of the WPF controls is to display content.</span></span> <span data-ttu-id="84122-296">WPF içinde, bir denetimin içeriğini oluşturan öğelerin türü ve sayısı denetimin *içerik modeli*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="84122-296">In WPF, the type and number of items that can constitute the content of a control is referred to as the control's *content model*.</span></span> <span data-ttu-id="84122-297">Bazı denetimler, tek bir öğe ve içerik türü içerebilir; Örneğin, bir <xref:System.Windows.Controls.TextBox> içeriği <xref:System.Windows.Controls.TextBox.Text%2A> özelliğine atanan bir dize değeridir.</span><span class="sxs-lookup"><span data-stu-id="84122-297">Some controls can contain a single item and type of content; for example, the content of a <xref:System.Windows.Controls.TextBox> is a string value that is assigned to the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span> <span data-ttu-id="84122-298">Aşağıdaki örnek <xref:System.Windows.Controls.TextBox>içeriğini ayarlar:</span><span class="sxs-lookup"><span data-stu-id="84122-298">The following example sets the content of a <xref:System.Windows.Controls.TextBox>:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.TextBoxContentWindow"
    Title="TextBox Content">

    <TextBox Text="This is the content of a TextBox." />
</Window>
```

<span data-ttu-id="84122-299">Aşağıdaki şekilde sonuç gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="84122-299">The following figure shows the result:</span></span>

![Metin içeren TextBox denetimi](media/introduction-to-wpf/wpfintrofigure21.png)

<span data-ttu-id="84122-301">Bununla birlikte, diğer denetimler farklı türde içeriklerde birden çok öğe içerebilir; <xref:System.Windows.Controls.ContentControl.Content%2A> özelliği tarafından belirtilen <xref:System.Windows.Controls.Button>içeriği, düzen denetimleri, metin, Resimler ve şekiller gibi çeşitli öğeleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="84122-301">Other controls, however, can contain multiple items of different types of content; the content of a <xref:System.Windows.Controls.Button>, specified by the <xref:System.Windows.Controls.ContentControl.Content%2A> property, can contain a variety of items including layout controls, text, images, and shapes.</span></span> <span data-ttu-id="84122-302">Aşağıdaki örnek, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Border>ve <xref:System.Windows.Controls.MediaElement>içeren içeriğe sahip bir <xref:System.Windows.Controls.Button> gösterir:</span><span class="sxs-lookup"><span data-stu-id="84122-302">The following example shows a <xref:System.Windows.Controls.Button> with content that includes a <xref:System.Windows.Controls.DockPanel>, a <xref:System.Windows.Controls.Label>, a <xref:System.Windows.Controls.Border>, and a <xref:System.Windows.Controls.MediaElement>:</span></span>

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

<span data-ttu-id="84122-303">Aşağıdaki şekilde bu düğmenin içeriği gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="84122-303">The following figure shows the content of this button:</span></span>

![Birden çok türde içerik içeren bir düğme](media/introduction-to-wpf/wpfintrofigure22.png)

<span data-ttu-id="84122-305">Çeşitli denetimler tarafından desteklenen içerik türleri hakkında daha fazla bilgi için bkz. [WPF içerik modeli](controls/wpf-content-model.md).</span><span class="sxs-lookup"><span data-stu-id="84122-305">For more information on the kinds of content that is supported by various controls, see [WPF content model](controls/wpf-content-model.md).</span></span>

### <a name="triggers"></a><span data-ttu-id="84122-306">Tetikleyiciler</span><span class="sxs-lookup"><span data-stu-id="84122-306">Triggers</span></span>

<span data-ttu-id="84122-307">XAML biçimlendirmesinin ana amacı uygulamanın görünümünü uygulamak olsa da, bir uygulamanın davranışının bazı yönlerini uygulamak için XAML de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84122-307">Although the main purpose of XAML markup is to implement an application's appearance, you can also use XAML to implement some aspects of an application's behavior.</span></span> <span data-ttu-id="84122-308">Bir örnek, bir uygulamanın görünümünü kullanıcı etkileşimlerine göre değiştirmek için tetikleyicilerin kullanılması.</span><span class="sxs-lookup"><span data-stu-id="84122-308">One example is the use of triggers to change an application's appearance based on user interactions.</span></span> <span data-ttu-id="84122-309">Daha fazla bilgi için bkz. [Stiller ve şablonlar](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="84122-309">For more information, see [Styles and templates](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

### <a name="control-templates"></a><span data-ttu-id="84122-310">Denetim şablonları</span><span class="sxs-lookup"><span data-stu-id="84122-310">Control templates</span></span>

<span data-ttu-id="84122-311">WPF denetimleri için varsayılan kullanıcı arabirimleri genellikle diğer denetimlerden ve şekillerden oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="84122-311">The default user interfaces for WPF controls are typically constructed from other controls and shapes.</span></span> <span data-ttu-id="84122-312">Örneğin, bir <xref:System.Windows.Controls.Button> hem <xref:Microsoft.Windows.Themes.ButtonChrome> hem de <xref:System.Windows.Controls.ContentPresenter> denetimlerinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="84122-312">For example, a <xref:System.Windows.Controls.Button> is composed of both <xref:Microsoft.Windows.Themes.ButtonChrome> and <xref:System.Windows.Controls.ContentPresenter> controls.</span></span> <span data-ttu-id="84122-313"><xref:Microsoft.Windows.Themes.ButtonChrome>, standart düğme görünümünü sağlar. <xref:System.Windows.Controls.ContentPresenter>, düğme içeriğini <xref:System.Windows.Controls.ContentControl.Content%2A> özelliği tarafından belirtilen şekilde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="84122-313">The <xref:Microsoft.Windows.Themes.ButtonChrome> provides the standard button appearance, while the <xref:System.Windows.Controls.ContentPresenter> displays the button's content, as specified by the <xref:System.Windows.Controls.ContentControl.Content%2A> property.</span></span>

<span data-ttu-id="84122-314">Bazen bir denetimin varsayılan görünümü bir uygulamanın genel görünümüyle birlikte kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="84122-314">Sometimes the default appearance of a control may be incongruent with the overall appearance of an application.</span></span> <span data-ttu-id="84122-315">Bu durumda, içeriğini ve davranışını değiştirmeden denetimin kullanıcı arabiriminin görünümünü değiştirmek için bir <xref:System.Windows.Controls.ControlTemplate> kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84122-315">In this case, you can use a <xref:System.Windows.Controls.ControlTemplate> to change the appearance of the control's user interface without changing its content and behavior.</span></span>

<span data-ttu-id="84122-316">Aşağıdaki örnek, <xref:System.Windows.Controls.ControlTemplate>kullanarak <xref:System.Windows.Controls.Button> görünümünün nasıl değiştirileceğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="84122-316">The following example shows how to change the appearance of a <xref:System.Windows.Controls.Button> by using a <xref:System.Windows.Controls.ControlTemplate>:</span></span>

[!code-xaml[IntroToWPFSnippets#ButtonControlTemplateWindowMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_16.xaml)]

[!code-csharp[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_17.cs)]
[!code-vb[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_17.vb)]

<span data-ttu-id="84122-317">Bu örnekte, varsayılan düğme Kullanıcı arabirimi koyu mavi kenarlığa sahip bir <xref:System.Windows.Shapes.Ellipse> değiştirilmiştir ve <xref:System.Windows.Media.RadialGradientBrush> kullanılarak doldurulmuştur.</span><span class="sxs-lookup"><span data-stu-id="84122-317">In this example, the default button user interface has been replaced with an <xref:System.Windows.Shapes.Ellipse> that has a dark blue border and is filled using a <xref:System.Windows.Media.RadialGradientBrush>.</span></span> <span data-ttu-id="84122-318"><xref:System.Windows.Controls.ContentPresenter> denetim <xref:System.Windows.Controls.Button>içeriğini görüntüler, "bana tıklayın!"</span><span class="sxs-lookup"><span data-stu-id="84122-318">The <xref:System.Windows.Controls.ContentPresenter> control displays the content of the <xref:System.Windows.Controls.Button>, "Click Me!"</span></span> <span data-ttu-id="84122-319"><xref:System.Windows.Controls.Button> tıklandığında, <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay <xref:System.Windows.Controls.Button> denetiminin varsayılan davranışının parçası olarak yine de oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="84122-319">When the <xref:System.Windows.Controls.Button> is clicked, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event is still raised as part of the <xref:System.Windows.Controls.Button> control's default behavior.</span></span> <span data-ttu-id="84122-320">Sonuç aşağıdaki şekilde gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="84122-320">The result is shown in the following figure:</span></span>

![Elips düğme ve ikinci bir pencere](media/introduction-to-wpf/wpfintrofigure2.png)

### <a name="data-templates"></a><span data-ttu-id="84122-322">Veri şablonları</span><span class="sxs-lookup"><span data-stu-id="84122-322">Data templates</span></span>

<span data-ttu-id="84122-323">Bir denetim şablonu bir denetimin görünümünü belirtmenize izin verirken, bir veri şablonu bir denetimin içeriğinin görünümünü belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="84122-323">Whereas a control template lets you specify the appearance of a control, a data template lets you specify the appearance of a control's content.</span></span> <span data-ttu-id="84122-324">Veri şablonları genellikle, bağlantılı verilerin nasıl görüntülendiğini iyileştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="84122-324">Data templates are frequently used to enhance how bound data is displayed.</span></span> <span data-ttu-id="84122-325">Aşağıdaki şekilde, her görevin bir ad, açıklama ve önceliğe sahip olduğu bir `Task` nesneleri koleksiyonuna bağlanan bir <xref:System.Windows.Controls.ListBox> için varsayılan görünüm gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="84122-325">The following figure shows the default appearance for a <xref:System.Windows.Controls.ListBox> that is bound to a collection of `Task` objects, where each task has a name, description, and priority:</span></span>

![Varsayılan görünümü içeren bir liste kutusu](media/introduction-to-wpf/wpfintrofigure18.png)

<span data-ttu-id="84122-327">Varsayılan görünüm, <xref:System.Windows.Controls.ListBox> beklediğiniz şeydir.</span><span class="sxs-lookup"><span data-stu-id="84122-327">The default appearance is what you would expect from a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="84122-328">Ancak, her görevin varsayılan görünümü yalnızca görev adını içerir.</span><span class="sxs-lookup"><span data-stu-id="84122-328">However, the default appearance of each task contains only the task name.</span></span> <span data-ttu-id="84122-329">Görev adını, açıklamasını ve önceliğini göstermek için, <xref:System.Windows.Controls.ListBox> denetiminin bağlantılı liste öğelerinin varsayılan görünümünün bir <xref:System.Windows.DataTemplate> kullanılarak değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="84122-329">To show the task name, description, and priority, the default appearance of the <xref:System.Windows.Controls.ListBox> control's bound list items must be changed by using a <xref:System.Windows.DataTemplate>.</span></span> <span data-ttu-id="84122-330">Aşağıdaki XAML, <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> özniteliği kullanılarak her bir göreve uygulanan böyle bir <xref:System.Windows.DataTemplate>tanımlar:</span><span class="sxs-lookup"><span data-stu-id="84122-330">The following XAML defines such a <xref:System.Windows.DataTemplate>, which is applied to each task by using the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> attribute:</span></span>

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

<span data-ttu-id="84122-331">Aşağıdaki şekilde, bu kodun etkisi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="84122-331">The following figure shows the effect of this code:</span></span>

![Veri şablonu kullanan liste kutusu](media/introduction-to-wpf/wpfintrofigure19.png)

<span data-ttu-id="84122-333"><xref:System.Windows.Controls.ListBox> davranışını ve genel görünümünü beklediğini unutmayın; yalnızca liste kutusu tarafından görüntülenmekte olan içeriğin görünümü değişmiştir.</span><span class="sxs-lookup"><span data-stu-id="84122-333">Note that the <xref:System.Windows.Controls.ListBox> has retained its behavior and overall appearance; only the appearance of the content being displayed by the list box has changed.</span></span>

<span data-ttu-id="84122-334">Daha fazla bilgi için bkz. [veri şablonu oluşturmaya genel bakış](data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="84122-334">For more information, see [Data templating overview](data/data-templating-overview.md).</span></span>

### <a name="styles"></a><span data-ttu-id="84122-335">Stiller</span><span class="sxs-lookup"><span data-stu-id="84122-335">Styles</span></span>

<span data-ttu-id="84122-336">Stiller, geliştiricilerin ve tasarımcıların ürünlerinin belirli bir görünümünü standartlaştırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="84122-336">Styles enable developers and designers to standardize on a particular appearance for their product.</span></span> <span data-ttu-id="84122-337">WPF, <xref:System.Windows.Style> öğesi olan bir güçlü stil modeli sunar.</span><span class="sxs-lookup"><span data-stu-id="84122-337">WPF provides a strong style model, the foundation of which is the <xref:System.Windows.Style> element.</span></span> <span data-ttu-id="84122-338">Aşağıdaki örnek, bir penceredeki her <xref:System.Windows.Controls.Button> için arka plan rengini `Orange`olacak şekilde ayarlayan bir stil oluşturur:</span><span class="sxs-lookup"><span data-stu-id="84122-338">The following example creates a style that sets the background color for every <xref:System.Windows.Controls.Button> on a window to `Orange`:</span></span>

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

<span data-ttu-id="84122-339">Bu stil tüm <xref:System.Windows.Controls.Button> denetimlerini hedeflediğinden, stil aşağıdaki şekilde gösterildiği gibi penceredeki tüm düğmelere otomatik olarak uygulanır:</span><span class="sxs-lookup"><span data-stu-id="84122-339">Because this style targets all <xref:System.Windows.Controls.Button> controls, the style is automatically applied to all the buttons in the window, as shown in the following figure:</span></span>

![İki turuncu düğme](media/introduction-to-wpf/wpfintrofigure20.png)

<span data-ttu-id="84122-341">Daha fazla bilgi için bkz. [Stiller ve şablonlar](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="84122-341">For more information, see [Styles and templates](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

### <a name="resources"></a><span data-ttu-id="84122-342">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="84122-342">Resources</span></span>

<span data-ttu-id="84122-343">Bir uygulamadaki denetimler aynı görünümü paylaşmalıdır. Bu, yazı tiplerinden ve arka plan renklerinden şablonları, veri şablonlarını ve stilleri denetleyebilen herhangi bir şeyi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="84122-343">Controls in an application should share the same appearance, which can include anything from fonts and background colors to control templates, data templates, and styles.</span></span> <span data-ttu-id="84122-344">Bu kaynakları yeniden kullanım için tek bir konumda kapsüllemek üzere, WPF 'nin Kullanıcı arabirimi kaynakları desteğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84122-344">You can use WPF's support for user interface resources to encapsulate these resources in a single location for reuse.</span></span>

<span data-ttu-id="84122-345">Aşağıdaki örnek, bir <xref:System.Windows.Controls.Button> ve <xref:System.Windows.Controls.Label>tarafından paylaşılan ortak bir arka plan rengi tanımlar:</span><span class="sxs-lookup"><span data-stu-id="84122-345">The following example defines a common background color that is shared by a <xref:System.Windows.Controls.Button> and a <xref:System.Windows.Controls.Label>:</span></span>

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

<span data-ttu-id="84122-346">Bu örnek `Window.Resources` Property öğesini kullanarak bir arka plan rengi kaynağı uygular.</span><span class="sxs-lookup"><span data-stu-id="84122-346">This example implements a background color resource by using the `Window.Resources` property element.</span></span> <span data-ttu-id="84122-347">Bu kaynak <xref:System.Windows.Window> tüm alt öğeleri için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="84122-347">This resource is available to all children of the <xref:System.Windows.Window>.</span></span> <span data-ttu-id="84122-348">Aşağıdakiler de dahil olmak üzere çeşitli kaynak kapsamları çözümlendikleri sırayla listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="84122-348">There are a variety of resource scopes, including the following, listed in the order in which they are resolved:</span></span>

1. <span data-ttu-id="84122-349">Tek bir denetim (devralınan <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> özelliğini kullanarak).</span><span class="sxs-lookup"><span data-stu-id="84122-349">An individual control (using the inherited <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> property).</span></span>

2. <span data-ttu-id="84122-350">Bir <xref:System.Windows.Window> veya <xref:System.Windows.Controls.Page> (devralınan <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> özelliğini de kullanarak).</span><span class="sxs-lookup"><span data-stu-id="84122-350">A <xref:System.Windows.Window> or a <xref:System.Windows.Controls.Page> (also using the inherited <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> property).</span></span>

3. <span data-ttu-id="84122-351">Bir <xref:System.Windows.Application> (<xref:System.Windows.Application.Resources%2A?displayProperty=fullName> özelliğini kullanarak).</span><span class="sxs-lookup"><span data-stu-id="84122-351">An <xref:System.Windows.Application> (using the <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> property).</span></span>

<span data-ttu-id="84122-352">Çeşitli kapsamlar, kaynaklarınızı tanımladığınız ve paylaştığınız yönteme göre esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="84122-352">The variety of scopes gives you flexibility with respect to the way in which you define and share your resources.</span></span>

<span data-ttu-id="84122-353">Kaynaklarınızın belirli bir kapsamla doğrudan ilişkilendirilmesi için alternatif olarak, bir veya daha fazla kaynağı, uygulamanın diğer bölümlerinde başvurulabilen ayrı bir <xref:System.Windows.ResourceDictionary> kullanarak paketleyebilir.</span><span class="sxs-lookup"><span data-stu-id="84122-353">As an alternative to directly associating your resources with a particular scope, you can package one or more resources by using a separate <xref:System.Windows.ResourceDictionary> that can be referenced in other parts of an application.</span></span> <span data-ttu-id="84122-354">Örneğin, aşağıdaki örnek bir kaynak sözlüğünde varsayılan bir arka plan rengi tanımlar:</span><span class="sxs-lookup"><span data-stu-id="84122-354">For example, the following example defines a default background color in a resource dictionary:</span></span>

```xaml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">

  <!-- Define background color resource -->
  <SolidColorBrush x:Key="defaultBackground" Color="Red" />

  <!-- Define other resources -->
</ResourceDictionary>
```

<span data-ttu-id="84122-355">Aşağıdaki örnek, bir uygulama genelinde paylaşılmak üzere önceki örnekte tanımlanan kaynak sözlüğüne başvurur:</span><span class="sxs-lookup"><span data-stu-id="84122-355">The following example references the resource dictionary defined in the previous example so that it is shared across an application:</span></span>

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

<span data-ttu-id="84122-356">Kaynaklar ve kaynak sözlükleri, Temalar ve kaplamalar için WPF desteğinin temelini içerir.</span><span class="sxs-lookup"><span data-stu-id="84122-356">Resources and resource dictionaries are the foundation of WPF support for themes and skins.</span></span>

<span data-ttu-id="84122-357">Daha fazla bilgi için bkz. [kaynaklar](../../desktop-wpf/fundamentals/xaml-resources-define.md).</span><span class="sxs-lookup"><span data-stu-id="84122-357">For more information, see [Resources](../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>

### <a name="custom-controls"></a><span data-ttu-id="84122-358">Özel denetimler</span><span class="sxs-lookup"><span data-stu-id="84122-358">Custom controls</span></span>

<span data-ttu-id="84122-359">WPF, özelleştirme desteği sunan bir konak sağlasa da, mevcut WPF denetimlerinin uygulamanızın veya kullanıcılarınızın ihtiyaçlarını karşılamadığında karşılaşabileceğiniz durumlarla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84122-359">Although WPF provides a host of customization support, you may encounter situations where existing WPF controls do not meet the needs of either your application or its users.</span></span> <span data-ttu-id="84122-360">Bu durum şu durumlarda oluşabilir:</span><span class="sxs-lookup"><span data-stu-id="84122-360">This can occur when:</span></span>

- <span data-ttu-id="84122-361">İhtiyaç duyduğunuz Kullanıcı arabirimi, mevcut WPF uygulamalarının görünümü özelleştirilerek oluşturulamaz.</span><span class="sxs-lookup"><span data-stu-id="84122-361">The user interface that you require cannot be created by customizing the look and feel of existing WPF implementations.</span></span>

- <span data-ttu-id="84122-362">Gerekli olan davranış, mevcut WPF uygulamaları tarafından desteklenmez (veya kolayca desteklenmez).</span><span class="sxs-lookup"><span data-stu-id="84122-362">The behavior that you require is not supported (or not easily supported) by existing WPF implementations.</span></span>

<span data-ttu-id="84122-363">Ancak, bu noktada, yeni bir denetim oluşturmak için üç WPF modelinden birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84122-363">At this point, however, you can take advantage of one of three WPF models to create a new control.</span></span> <span data-ttu-id="84122-364">Her model belirli bir senaryoyu hedefler ve özel denetiminizin belirli bir WPF Taban sınıfından türemesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="84122-364">Each model targets a specific scenario and requires your custom control to derive from a particular WPF base class.</span></span> <span data-ttu-id="84122-365">Üç model burada listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="84122-365">The three models are listed here:</span></span>

- <span data-ttu-id="84122-366">**Kullanıcı denetimi modeli**.</span><span class="sxs-lookup"><span data-stu-id="84122-366">**User Control Model**.</span></span> <span data-ttu-id="84122-367">Özel denetim <xref:System.Windows.Controls.UserControl> türetilir ve bir veya daha fazla denetimden oluşur.</span><span class="sxs-lookup"><span data-stu-id="84122-367">A custom control derives from <xref:System.Windows.Controls.UserControl> and is composed of one or more other controls.</span></span>

- <span data-ttu-id="84122-368">**Denetim modeli**.</span><span class="sxs-lookup"><span data-stu-id="84122-368">**Control Model**.</span></span> <span data-ttu-id="84122-369">Özel bir denetim <xref:System.Windows.Controls.Control> türetilir ve davranışlarını, WPF denetimlerinin çoğunluğuna benzer şekilde, şablonları kullanarak görünüşlerinden ayıran uygulamalar oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="84122-369">A custom control derives from <xref:System.Windows.Controls.Control> and is used to build implementations that separate their behavior from their appearance using templates, much like the majority of WPF controls.</span></span> <span data-ttu-id="84122-370"><xref:System.Windows.Controls.Control> türetmek, Kullanıcı denetimlerinden özel bir kullanıcı arabirimi oluşturmak için daha fazla özgürlük sağlar, ancak daha fazla çaba gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="84122-370">Deriving from <xref:System.Windows.Controls.Control> allows you more freedom for creating a custom user interface than user controls, but it may require more effort.</span></span>

- <span data-ttu-id="84122-371">**Framework öğe modeli**.</span><span class="sxs-lookup"><span data-stu-id="84122-371">**Framework Element Model**.</span></span> <span data-ttu-id="84122-372">Özel bir denetim, görünümü özel işleme mantığı (şablon değil) tarafından tanımlandığında <xref:System.Windows.FrameworkElement> türetilir.</span><span class="sxs-lookup"><span data-stu-id="84122-372">A custom control derives from <xref:System.Windows.FrameworkElement> when its appearance is defined by custom rendering logic (not templates).</span></span>

<span data-ttu-id="84122-373">Aşağıdaki örnek, <xref:System.Windows.Controls.UserControl>türetilen özel bir sayısal yukarı/aşağı denetimi gösterir:</span><span class="sxs-lookup"><span data-stu-id="84122-373">The following example shows a custom numeric up/down control that derives from <xref:System.Windows.Controls.UserControl>:</span></span>

[!code-xaml[IntroToWPFSnippets#UserControlMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_33.xaml)]

[!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND1](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_34.cs)]
[!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND1](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_34.vb)]

<span data-ttu-id="84122-374">Aşağıdaki örnek, Kullanıcı denetimini bir <xref:System.Windows.Window>eklemek için gereken XAML 'yi göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="84122-374">The following example illustrates the XAML that is required to incorporate the user control into a <xref:System.Windows.Window>:</span></span>

[!code-xaml[IntroToWPFSnippets#UserControlWindowMARKUP1](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_37.xaml)]

<span data-ttu-id="84122-375">Aşağıdaki şekilde, <xref:System.Windows.Window>barındırılan `NumericUpDown` denetimi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="84122-375">The following figure shows the `NumericUpDown` control hosted in a <xref:System.Windows.Window>:</span></span>

![Özel bir UserControl](media/introduction-to-wpf/wpfintrofigure3.png)

<span data-ttu-id="84122-377">Özel denetimler hakkında daha fazla bilgi için bkz. [Denetim yazma genel bakış](controls/control-authoring-overview.md).</span><span class="sxs-lookup"><span data-stu-id="84122-377">For more information on custom controls, see [Control authoring overview](controls/control-authoring-overview.md).</span></span>

## <a name="wpf-best-practices"></a><span data-ttu-id="84122-378">WPF en iyi uygulamaları</span><span class="sxs-lookup"><span data-stu-id="84122-378">WPF best practices</span></span>

<span data-ttu-id="84122-379">Her türlü geliştirme platformunda olduğu gibi, WPF istenen sonuca ulaşmak için çeşitli yollarla kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="84122-379">As with any development platform, WPF can be used in a variety of ways to achieve the desired result.</span></span> <span data-ttu-id="84122-380">WPF uygulamalarınızın gerekli Kullanıcı deneyimini sağlayıp, genel olarak hedef kitle taleplerini karşıladığından emin olmanın bir yolu olarak erişilebilirlik, Genelleştirme ve yerelleştirme ve performans için önerilen en iyi uygulamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="84122-380">As a way of ensuring that your WPF applications provide the required user experience and meet the demands of the audience in general, there are recommended best practices for accessibility, globalization and localization, and performance.</span></span> <span data-ttu-id="84122-381">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="84122-381">For more information, see:</span></span>

- [<span data-ttu-id="84122-382">Erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="84122-382">Accessibility</span></span>](../ui-automation/accessibility-best-practices.md)
- [<span data-ttu-id="84122-383">WPF Genelleştirme ve yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="84122-383">WPF globalization and localization</span></span>](advanced/wpf-globalization-and-localization-overview.md)
- [<span data-ttu-id="84122-384">WPF uygulama performansı</span><span class="sxs-lookup"><span data-stu-id="84122-384">WPF app performance</span></span>](advanced/optimizing-wpf-application-performance.md)
- [<span data-ttu-id="84122-385">WPF güvenliği</span><span class="sxs-lookup"><span data-stu-id="84122-385">WPF security</span></span>](security-wpf.md)

## <a name="next-steps"></a><span data-ttu-id="84122-386">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="84122-386">Next steps</span></span>

<span data-ttu-id="84122-387">WPF 'nin temel özelliklerine baktık.</span><span class="sxs-lookup"><span data-stu-id="84122-387">We've looked at the key features of WPF.</span></span> <span data-ttu-id="84122-388">Şimdi ilk WPF uygulamanızı oluşturma zamanı.</span><span class="sxs-lookup"><span data-stu-id="84122-388">Now it's time to build your first WPF app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="84122-389">İzlenecek yol: ilk WPF Masaüstü Uygulamam</span><span class="sxs-lookup"><span data-stu-id="84122-389">Walkthrough: My first WPF desktop app</span></span>](getting-started/walkthrough-my-first-wpf-desktop-application.md)

## <a name="see-also"></a><span data-ttu-id="84122-390">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84122-390">See also</span></span>

- [<span data-ttu-id="84122-391">WPF kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="84122-391">Get started with WPF</span></span>](getting-started/index.md)
- [<span data-ttu-id="84122-392">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="84122-392">Windows Presentation Foundation</span></span>](index.md)
- [<span data-ttu-id="84122-393">WPF topluluk kaynakları</span><span class="sxs-lookup"><span data-stu-id="84122-393">WPF community resources</span></span>](getting-started/community-feedback.md)
