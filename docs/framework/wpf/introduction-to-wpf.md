---
title: WPF'ye Giriş
titleSuffix: ''
description: Windows 'da görsel açıdan etkileyici kullanıcı deneyimleri oluşturun. Windows Presentation Foundation (WPF) temel yeteneklerini ve kavramlarını bulun.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b8d7cf43-d1f2-4f3d-adb0-4f3a6428edc0
dev_langs:
- csharp
- vb
ms.openlocfilehash: 7a79174f5f3aebe90190db45566b37bd5e9fbe3f
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853571"
---
# <a name="wpf-overview"></a><span data-ttu-id="3a4b4-104">WPF’ye genel bakış</span><span class="sxs-lookup"><span data-stu-id="3a4b4-104">WPF overview</span></span>

<span data-ttu-id="3a4b4-105">Windows Presentation Foundation (WPF), görsel açıdan etkileyici kullanıcı deneyimleri sayesinde Windows için masaüstü istemci uygulamaları oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-105">Windows Presentation Foundation (WPF) lets you create desktop client applications for Windows with visually stunning user experiences.</span></span>

![Contoso sağlık Kullanıcı arabirimi örneği](media/introduction-to-wpf/wpfintrofigure24.png)

<span data-ttu-id="3a4b4-107">WPF 'nin çekirdeği, modern grafik donanımının avantajlarından yararlanmak için oluşturulmuş, çözünürlükten bağımsız ve vektör tabanlı bir işleme altyapısıdır.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-107">The core of WPF is a resolution-independent and vector-based rendering engine that is built to take advantage of modern graphics hardware.</span></span> <span data-ttu-id="3a4b4-108">WPF, Extensible Application Markup Language (XAML), denetimler, veri bağlama, düzen, 2B ve 3B grafikler, animasyon, stiller, şablonlar, belgeler, medya, metin ve tipografi içeren kapsamlı bir uygulama geliştirme özellikleri kümesiyle Core 'u genişletir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-108">WPF extends the core with a comprehensive set of application-development features that include Extensible Application Markup Language (XAML), controls, data binding, layout, 2D and 3D graphics, animation, styles, templates, documents, media, text, and typography.</span></span> <span data-ttu-id="3a4b4-109">WPF .NET 'in bir parçası olduğundan, .NET API 'nin diğer öğelerini birleştiren uygulamalar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-109">WPF is part of .NET, so you can build applications that incorporate other elements of the .NET API.</span></span>

<span data-ttu-id="3a4b4-110">Bu genel bakış, Newcomers 'e yöneliktir ve WPF 'in temel yeteneklerini ve kavramlarını ele alır.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-110">This overview is intended for newcomers and covers the key capabilities and concepts of WPF.</span></span>

## <a name="program-with-wpf"></a><span data-ttu-id="3a4b4-111">WPF ile program</span><span class="sxs-lookup"><span data-stu-id="3a4b4-111">Program with WPF</span></span>

<span data-ttu-id="3a4b4-112">WPF, ad alanında bulunan (en fazla bölüm için) .NET türlerinin bir alt kümesi olarak mevcuttur <xref:System.Windows> .</span><span class="sxs-lookup"><span data-stu-id="3a4b4-112">WPF exists as a subset of .NET types that are (for the most part) located in the <xref:System.Windows> namespace.</span></span> <span data-ttu-id="3a4b4-113">Daha önce ASP.NET ve Windows Forms gibi yönetilen teknolojiler kullanarak .NET ile uygulamalar oluşturduysanız, temel WPF programlama deneyimi tanıdık gelmelidir; C# veya Visual Basic gibi en sevdiğiniz .NET programlama dilini kullanarak sınıfları örnekleyin, özellikleri ayarlar, yöntemleri çağırır ve olayları işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-113">If you have previously built applications with .NET using managed technologies like ASP.NET and Windows Forms, the fundamental WPF programming experience should be familiar; you instantiate classes, set properties, call methods, and handle events, using your favorite .NET programming language, such as C# or Visual Basic.</span></span>

<span data-ttu-id="3a4b4-114">WPF, özellikleri ve olayları geliştiren ek programlama yapılarını içerir: [bağımlılık özellikleri](advanced/dependency-properties-overview.md) ve [yönlendirilmiş olaylar](advanced/routed-events-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3a4b4-114">WPF includes additional programming constructs that enhance properties and events: [dependency properties](advanced/dependency-properties-overview.md) and [routed events](advanced/routed-events-overview.md).</span></span>

## <a name="markup-and-code-behind"></a><span data-ttu-id="3a4b4-115">Biçimlendirme ve arka plan kodu</span><span class="sxs-lookup"><span data-stu-id="3a4b4-115">Markup and code-behind</span></span>

<span data-ttu-id="3a4b4-116">WPF, ASP.NET geliştiricilerin tanıdık olması gereken bir deneyim olan hem *biçimlendirme* hem de *arka plan kodu*kullanarak bir uygulama geliştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-116">WPF lets you develop an application using both *markup* and *code-behind*, an experience with which ASP.NET developers should be familiar.</span></span> <span data-ttu-id="3a4b4-117">Genellikle XAML işaretlemesini kullanarak, davranışını uygulamak için yönetilen programlama dillerini (arka plan kod) kullanırken bir uygulamanın görünümünü uygulayın.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-117">You generally use XAML markup to implement the appearance of an application while using managed programming languages (code-behind) to implement its behavior.</span></span> <span data-ttu-id="3a4b4-118">Bu görünüm ve davranışın ayrımı aşağıdaki avantajlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="3a4b4-118">This separation of appearance and behavior has the following benefits:</span></span>

- <span data-ttu-id="3a4b4-119">Görünüme özgü biçimlendirme davranışa özgü kodla sıkı bir şekilde bağlı olmadığından geliştirme ve bakım maliyetleri azaltılır.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-119">Development and maintenance costs are reduced because appearance-specific markup is not tightly coupled with behavior-specific code.</span></span>

- <span data-ttu-id="3a4b4-120">Geliştiriciler uygulamanın davranışını uygulayan geliştiricilerle aynı anda bir uygulamanın görünümünü uygulayabildiğinden geliştirme daha etkilidir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-120">Development is more efficient because designers can implement an application's appearance simultaneously with developers who are implementing the application's behavior.</span></span>

- <span data-ttu-id="3a4b4-121">WPF uygulamaları için [Genelleştirme ve yerelleştirme](advanced/wpf-globalization-and-localization-overview.md) basitleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-121">[Globalization and localization](advanced/wpf-globalization-and-localization-overview.md) for WPF applications is simplified.</span></span>

### <a name="markup"></a><span data-ttu-id="3a4b4-122">İşaretleme</span><span class="sxs-lookup"><span data-stu-id="3a4b4-122">Markup</span></span>

<span data-ttu-id="3a4b4-123">XAML, uygulamanın görünümünü bildirimli olarak uygulayan XML tabanlı bir biçimlendirme dilidir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-123">XAML is an XML-based markup language that implements an application's appearance declaratively.</span></span> <span data-ttu-id="3a4b4-124">Genellikle Windows, iletişim kutuları, sayfalar ve Kullanıcı denetimleri oluşturmak ve bunları denetimler, şekiller ve grafiklerle doldurmanız için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-124">You typically use it to create windows, dialog boxes, pages, and user controls, and to fill them with controls, shapes, and graphics.</span></span>

<span data-ttu-id="3a4b4-125">Aşağıdaki örnek, tek bir düğme içeren bir pencerenin görünümünü uygulamak için XAML kullanır:</span><span class="sxs-lookup"><span data-stu-id="3a4b4-125">The following example uses XAML to implement the appearance of a window that contains a single button:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button">Click Me!</Button>

</Window>
```

<span data-ttu-id="3a4b4-126">Özellikle, bu XAML `Window` sırasıyla ve öğelerini kullanarak bir pencere ve bir düğme tanımlar `Button` .</span><span class="sxs-lookup"><span data-stu-id="3a4b4-126">Specifically, this XAML defines a window and a button by using the `Window` and `Button` elements, respectively.</span></span> <span data-ttu-id="3a4b4-127">Her öğe, `Window` `Title` pencerenin başlık çubuğu metnini belirtmek için öğenin özniteliği gibi özniteliklerle yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-127">Each element is configured with attributes, such as the `Window` element's `Title` attribute to specify the window's title-bar text.</span></span> <span data-ttu-id="3a4b4-128">Çalışma zamanında WPF, biçimlendirme içinde tanımlanan öğeleri ve öznitelikleri WPF sınıflarının örneklerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-128">At run time, WPF converts the elements and attributes that are defined in markup to instances of WPF classes.</span></span> <span data-ttu-id="3a4b4-129">Örneğin, `Window` öğesi <xref:System.Windows.Window> <xref:System.Windows.Window.Title%2A> özelliği özniteliğin değeri olan bir sınıfının örneğine dönüştürülür `Title` .</span><span class="sxs-lookup"><span data-stu-id="3a4b4-129">For example, the `Window` element is converted to an instance of the <xref:System.Windows.Window> class whose <xref:System.Windows.Window.Title%2A> property is the value of the `Title` attribute.</span></span>

<span data-ttu-id="3a4b4-130">Aşağıdaki şekilde, önceki örnekte XAML tarafından tanımlanan Kullanıcı arabirimi (UI) gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="3a4b4-130">The following figure shows the user interface (UI) that is defined by the XAML in the previous example:</span></span>

![Düğme içeren pencere](media/introduction-to-wpf/wpfintrofigure10.png)

<span data-ttu-id="3a4b4-132">XAML, XML tabanlı olduğundan, onunla oluşturduğunuz Kullanıcı arabirimi bir [öğe ağacı](advanced/trees-in-wpf.md)olarak bilinen iç içe geçmiş öğelerin hiyerarşisinde toplanır.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-132">Since XAML is XML-based, the UI that you compose with it is assembled in a hierarchy of nested elements known as an [element tree](advanced/trees-in-wpf.md).</span></span> <span data-ttu-id="3a4b4-133">Öğe ağacı, Usıs oluşturmak ve yönetmek için mantıksal ve sezgisel bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-133">The element tree provides a logical and intuitive way to create and manage UIs.</span></span>

### <a name="code-behind"></a><span data-ttu-id="3a4b4-134">Arka plan kodu</span><span class="sxs-lookup"><span data-stu-id="3a4b4-134">Code-behind</span></span>

<span data-ttu-id="3a4b4-135">Bir uygulamanın ana davranışı, olayları işleme (örneğin, bir menü, araç çubuğu veya düğme) ve yanıt olarak iş mantığı ve veri erişim mantığını çağırma dahil olmak üzere kullanıcı etkileşimlerine yanıt veren işlevselliği uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-135">The main behavior of an application is to implement the functionality that responds to user interactions, including handling events (for example, clicking a menu, tool bar, or button) and calling business logic and data access logic in response.</span></span> <span data-ttu-id="3a4b4-136">WPF 'de, bu davranış biçimlendirme ile ilişkili kodda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-136">In WPF, this behavior is implemented in code that is associated with markup.</span></span> <span data-ttu-id="3a4b4-137">Bu tür bir kod, arka plan kodu olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-137">This type of code is known as code-behind.</span></span> <span data-ttu-id="3a4b4-138">Aşağıdaki örnek, önceki örnekteki ve arka plan kodundaki güncelleştirilmiş biçimlendirmeyi gösterir:</span><span class="sxs-lookup"><span data-stu-id="3a4b4-138">The following example shows the updated markup from the previous example and the code-behind:</span></span>

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

<span data-ttu-id="3a4b4-139">Bu örnekte, arka plan kodu sınıfından türetilen bir sınıf uygular <xref:System.Windows.Window> .</span><span class="sxs-lookup"><span data-stu-id="3a4b4-139">In this example, the code-behind implements a class that derives from the <xref:System.Windows.Window> class.</span></span> <span data-ttu-id="3a4b4-140">`x:Class`Özniteliği, biçimlendirmeyi arka plan kod sınıfıyla ilişkilendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-140">The `x:Class` attribute is used to associate the markup with the code-behind class.</span></span> <span data-ttu-id="3a4b4-141">`InitializeComponent`arka plan kod sınıfı ile biçimlendirme içinde tanımlanan Kullanıcı arabirimini birleştirmek için, kod arkasındaki sınıfın oluşturucusundan çağrılır.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-141">`InitializeComponent` is called from the code-behind class's constructor to merge the UI that is defined in markup with the code-behind class.</span></span> <span data-ttu-id="3a4b4-142">( `InitializeComponent` uygulamanızın oluşturulduğu zaman sizin için oluşturulur, bu nedenle el ile uygulamanız gerekmez.) Birleşimi ve uygulamanızın `x:Class` `InitializeComponent` oluşturulduğu her seferinde doğru başlatıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-142">(`InitializeComponent` is generated for you when your application is built, which is why you don't need to implement it manually.) The combination of `x:Class` and `InitializeComponent` ensure that your implementation is correctly initialized whenever it is created.</span></span> <span data-ttu-id="3a4b4-143">Arka plan kod sınıfı, düğmenin olayı için bir olay işleyicisi de uygular <xref:System.Windows.Controls.Primitives.ButtonBase.Click> .</span><span class="sxs-lookup"><span data-stu-id="3a4b4-143">The code-behind class also implements an event handler for the button's <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event.</span></span> <span data-ttu-id="3a4b4-144">Düğmeye tıklandığında, olay işleyicisi yöntemini çağırarak bir ileti kutusu gösterir <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="3a4b4-144">When the button is clicked, the event handler shows a message box by calling the <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> method.</span></span>

<span data-ttu-id="3a4b4-145">Aşağıdaki şekilde düğme tıklandığında sonuç gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="3a4b4-145">The following figure shows the result when the button is clicked:</span></span>

![Bir MessageBox](media/introduction-to-wpf/wpfintrofigure25.png)

## <a name="controls"></a><span data-ttu-id="3a4b4-147">Denetimler</span><span class="sxs-lookup"><span data-stu-id="3a4b4-147">Controls</span></span>

<span data-ttu-id="3a4b4-148">Uygulama modeli tarafından sunulan kullanıcı deneyimleri, oluşturulan denetimlerdir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-148">The user experiences that are delivered by the application model are constructed controls.</span></span> <span data-ttu-id="3a4b4-149">WPF 'de *Denetim* , bir pencere veya sayfada BARıNDıRıLAN bir WPF sınıfı kategorisi için geçerli olan ve bir kullanıcı arabirimine sahip olan ve bazı davranışları uygulayan bir şemsiye terimidir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-149">In WPF, *control* is an umbrella term that applies to a category of WPF classes that are hosted in either a window or a page, have a user interface, and implement some behavior.</span></span>

<span data-ttu-id="3a4b4-150">Daha fazla bilgi için bkz. [denetimler](controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="3a4b4-150">For more information, see [Controls](controls/index.md).</span></span>

### <a name="wpf-controls-by-function"></a><span data-ttu-id="3a4b4-151">İşleve göre WPF denetimleri</span><span class="sxs-lookup"><span data-stu-id="3a4b4-151">WPF controls by function</span></span>

<span data-ttu-id="3a4b4-152">Yerleşik WPF denetimleri burada listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="3a4b4-152">The built-in WPF controls are listed here:</span></span>

- <span data-ttu-id="3a4b4-153">**Düğmeler**: <xref:System.Windows.Controls.Button> ve <xref:System.Windows.Controls.Primitives.RepeatButton> .</span><span class="sxs-lookup"><span data-stu-id="3a4b4-153">**Buttons**: <xref:System.Windows.Controls.Button> and <xref:System.Windows.Controls.Primitives.RepeatButton>.</span></span>

- <span data-ttu-id="3a4b4-154">**Veri görüntüleme**: <xref:System.Windows.Controls.DataGrid> , <xref:System.Windows.Controls.ListView> , ve <xref:System.Windows.Controls.TreeView> .</span><span class="sxs-lookup"><span data-stu-id="3a4b4-154">**Data Display**: <xref:System.Windows.Controls.DataGrid>, <xref:System.Windows.Controls.ListView>, and <xref:System.Windows.Controls.TreeView>.</span></span>

- <span data-ttu-id="3a4b4-155">**Tarih görüntüleme ve seçim**: <xref:System.Windows.Controls.Calendar> ve <xref:System.Windows.Controls.DatePicker> .</span><span class="sxs-lookup"><span data-stu-id="3a4b4-155">**Date Display and Selection**: <xref:System.Windows.Controls.Calendar> and <xref:System.Windows.Controls.DatePicker>.</span></span>

- <span data-ttu-id="3a4b4-156">**İletişim kutuları**: <xref:Microsoft.Win32.OpenFileDialog> , <xref:System.Windows.Controls.PrintDialog> , ve <xref:Microsoft.Win32.SaveFileDialog> .</span><span class="sxs-lookup"><span data-stu-id="3a4b4-156">**Dialog Boxes**: <xref:Microsoft.Win32.OpenFileDialog>, <xref:System.Windows.Controls.PrintDialog>, and <xref:Microsoft.Win32.SaveFileDialog>.</span></span>

- <span data-ttu-id="3a4b4-157">**Dijital mürekkep**: <xref:System.Windows.Controls.InkCanvas> ve <xref:System.Windows.Controls.InkPresenter> .</span><span class="sxs-lookup"><span data-stu-id="3a4b4-157">**Digital Ink**: <xref:System.Windows.Controls.InkCanvas> and <xref:System.Windows.Controls.InkPresenter>.</span></span>

- <span data-ttu-id="3a4b4-158">**Belgeler**: <xref:System.Windows.Controls.DocumentViewer> , <xref:System.Windows.Controls.FlowDocumentPageViewer> , <xref:System.Windows.Controls.FlowDocumentReader> , <xref:System.Windows.Controls.FlowDocumentScrollViewer> ve <xref:System.Windows.Controls.StickyNoteControl> .</span><span class="sxs-lookup"><span data-stu-id="3a4b4-158">**Documents**: <xref:System.Windows.Controls.DocumentViewer>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentScrollViewer>, and <xref:System.Windows.Controls.StickyNoteControl>.</span></span>

- <span data-ttu-id="3a4b4-159">**Giriş**: <xref:System.Windows.Controls.TextBox> , <xref:System.Windows.Controls.RichTextBox> , ve <xref:System.Windows.Controls.PasswordBox> .</span><span class="sxs-lookup"><span data-stu-id="3a4b4-159">**Input**: <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, and <xref:System.Windows.Controls.PasswordBox>.</span></span>

- <span data-ttu-id="3a4b4-160">**Düzen**: <xref:System.Windows.Controls.Border> , <xref:System.Windows.Controls.Primitives.BulletDecorator> ,,, <xref:System.Windows.Controls.Canvas> <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Expander> , <xref:System.Windows.Controls.Grid> , <xref:System.Windows.Controls.GridView> , <xref:System.Windows.Controls.GridSplitter> , <xref:System.Windows.Controls.GroupBox> , <xref:System.Windows.Controls.Panel> , <xref:System.Windows.Controls.Primitives.ResizeGrip> , <xref:System.Windows.Controls.Separator> , <xref:System.Windows.Controls.Primitives.ScrollBar> , <xref:System.Windows.Controls.ScrollViewer> , <xref:System.Windows.Controls.StackPanel> , <xref:System.Windows.Controls.Primitives.Thumb> , <xref:System.Windows.Controls.Viewbox> , <xref:System.Windows.Controls.VirtualizingStackPanel> ,, <xref:System.Windows.Window> ve <xref:System.Windows.Controls.WrapPanel> .</span><span class="sxs-lookup"><span data-stu-id="3a4b4-160">**Layout**: <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Primitives.BulletDecorator>, <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Expander>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridSplitter>, <xref:System.Windows.Controls.GroupBox>, <xref:System.Windows.Controls.Panel>, <xref:System.Windows.Controls.Primitives.ResizeGrip>, <xref:System.Windows.Controls.Separator>, <xref:System.Windows.Controls.Primitives.ScrollBar>, <xref:System.Windows.Controls.ScrollViewer>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.Primitives.Thumb>, <xref:System.Windows.Controls.Viewbox>, <xref:System.Windows.Controls.VirtualizingStackPanel>, <xref:System.Windows.Window>, and <xref:System.Windows.Controls.WrapPanel>.</span></span>

- <span data-ttu-id="3a4b4-161">**Medya**: <xref:System.Windows.Controls.Image> , <xref:System.Windows.Controls.MediaElement> , ve <xref:System.Windows.Controls.SoundPlayerAction> .</span><span class="sxs-lookup"><span data-stu-id="3a4b4-161">**Media**: <xref:System.Windows.Controls.Image>, <xref:System.Windows.Controls.MediaElement>, and <xref:System.Windows.Controls.SoundPlayerAction>.</span></span>

- <span data-ttu-id="3a4b4-162">**Menüler**: <xref:System.Windows.Controls.ContextMenu> , <xref:System.Windows.Controls.Menu> , ve <xref:System.Windows.Controls.ToolBar> .</span><span class="sxs-lookup"><span data-stu-id="3a4b4-162">**Menus**: <xref:System.Windows.Controls.ContextMenu>, <xref:System.Windows.Controls.Menu>, and <xref:System.Windows.Controls.ToolBar>.</span></span>

- <span data-ttu-id="3a4b4-163">**Gezinti**: <xref:System.Windows.Controls.Frame> ,,, <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Controls.Page> <xref:System.Windows.Navigation.NavigationWindow> ve <xref:System.Windows.Controls.TabControl> .</span><span class="sxs-lookup"><span data-stu-id="3a4b4-163">**Navigation**: <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, and <xref:System.Windows.Controls.TabControl>.</span></span>

- <span data-ttu-id="3a4b4-164">**Seçim**: <xref:System.Windows.Controls.CheckBox> , <xref:System.Windows.Controls.ComboBox> , <xref:System.Windows.Controls.ListBox> , <xref:System.Windows.Controls.RadioButton> , ve <xref:System.Windows.Controls.Slider> .</span><span class="sxs-lookup"><span data-stu-id="3a4b4-164">**Selection**: <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.RadioButton>, and <xref:System.Windows.Controls.Slider>.</span></span>

- <span data-ttu-id="3a4b4-165">**Kullanıcı bilgileri**: <xref:System.Windows.Controls.AccessText> , <xref:System.Windows.Controls.Label> , <xref:System.Windows.Controls.Primitives.Popup> , <xref:System.Windows.Controls.ProgressBar> , <xref:System.Windows.Controls.Primitives.StatusBar> , <xref:System.Windows.Controls.TextBlock> , ve <xref:System.Windows.Controls.ToolTip> .</span><span class="sxs-lookup"><span data-stu-id="3a4b4-165">**User Information**: <xref:System.Windows.Controls.AccessText>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.ProgressBar>, <xref:System.Windows.Controls.Primitives.StatusBar>, <xref:System.Windows.Controls.TextBlock>, and <xref:System.Windows.Controls.ToolTip>.</span></span>

## <a name="input-and-commands"></a><span data-ttu-id="3a4b4-166">Giriş ve komutlar</span><span class="sxs-lookup"><span data-stu-id="3a4b4-166">Input and commands</span></span>

<span data-ttu-id="3a4b4-167">Denetimler çoğu zaman Kullanıcı girişini algılar ve yanıtlar.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-167">Controls most often detect and respond to user input.</span></span> <span data-ttu-id="3a4b4-168">[WPF giriş sistemi](advanced/input-overview.md) metin girişi, odak yönetimi ve fare konumlandırmayı desteklemek için hem doğrudan hem de yönlendirilmiş olayları kullanır.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-168">The [WPF input system](advanced/input-overview.md) uses both direct and routed events to support text input, focus management, and mouse positioning.</span></span>

<span data-ttu-id="3a4b4-169">Uygulamalar genellikle karmaşık giriş gereksinimlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-169">Applications often have complex input requirements.</span></span> <span data-ttu-id="3a4b4-170">WPF, Kullanıcı giriş eylemlerini bu eylemlere yanıt veren koddan ayıran bir [komut sistemi](advanced/commanding-overview.md) sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-170">WPF provides a [command system](advanced/commanding-overview.md) that separates user-input actions from the code that responds to those actions.</span></span>

## <a name="layout"></a><span data-ttu-id="3a4b4-171">Layout</span><span class="sxs-lookup"><span data-stu-id="3a4b4-171">Layout</span></span>

<span data-ttu-id="3a4b4-172">Bir kullanıcı arabirimi oluşturduğunuzda, bir düzen oluşturmak için denetimlerinizi konuma ve boyuta göre düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-172">When you create a user interface, you arrange your controls by location and size to form a layout.</span></span> <span data-ttu-id="3a4b4-173">Herhangi bir düzenin önemli bir gereksinimi, pencere boyutu ve görüntüleme ayarlarındaki değişikliklere uyum sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-173">A key requirement of any layout is to adapt to changes in window size and display settings.</span></span> <span data-ttu-id="3a4b4-174">Bu koşullarda bir düzeni uyarlamak için kodu yazmanızı zorlamak yerine WPF, sizin için birinci sınıf bir Genişletilebilir düzen sistemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-174">Rather than forcing you to write the code to adapt a layout in these circumstances, WPF provides a first-class, extensible layout system for you.</span></span>

<span data-ttu-id="3a4b4-175">Düzen sisteminin temel taşı, değişen pencere ve görüntüleme koşullarına uyum sağlayan göreli konumlardır.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-175">The cornerstone of the layout system is relative positioning, which increases the ability to adapt to changing window and display conditions.</span></span> <span data-ttu-id="3a4b4-176">Ayrıca, Düzen sistemi, düzeni belirleme denetimleri arasındaki anlaşmayı yönetir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-176">In addition, the layout system manages the negotiation between controls to determine the layout.</span></span> <span data-ttu-id="3a4b4-177">Anlaşma iki adımlı bir işlemdir: ilk olarak, bir denetim üst öğeye gereken konumu ve boyutu söyler; İkincisi, üst öğe denetime ne kadar boşluk yapabileceğini söyler.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-177">The negotiation is a two-step process: first, a control tells its parent what location and size it requires; second, the parent tells the control what space it can have.</span></span>

<span data-ttu-id="3a4b4-178">Düzen sistemi, temel WPF sınıfları aracılığıyla alt denetimlere açıktır.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-178">The layout system is exposed to child controls through base WPF classes.</span></span> <span data-ttu-id="3a4b4-179">WPF, yığınlama ve yerleştirme gibi ortak düzenler için çeşitli düzen denetimleri içerir:</span><span class="sxs-lookup"><span data-stu-id="3a4b4-179">For common layouts such as grids, stacking, and docking, WPF includes several layout controls:</span></span>

- <span data-ttu-id="3a4b4-180"><xref:System.Windows.Controls.Canvas>: Alt denetimler kendi düzenlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-180"><xref:System.Windows.Controls.Canvas>: Child controls provide their own layout.</span></span>

- <span data-ttu-id="3a4b4-181"><xref:System.Windows.Controls.DockPanel>: Alt denetimler panelin kenarlarına hizalanır.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-181"><xref:System.Windows.Controls.DockPanel>: Child controls are aligned to the edges of the panel.</span></span>

- <span data-ttu-id="3a4b4-182"><xref:System.Windows.Controls.Grid>: Alt denetimler satırlara ve sütunlara göre konumlandırılır.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-182"><xref:System.Windows.Controls.Grid>: Child controls are positioned by rows and columns.</span></span>

- <span data-ttu-id="3a4b4-183"><xref:System.Windows.Controls.StackPanel>: Alt denetimler dikey ya da yatay olarak yığılır.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-183"><xref:System.Windows.Controls.StackPanel>: Child controls are stacked either vertically or horizontally.</span></span>

- <span data-ttu-id="3a4b4-184"><xref:System.Windows.Controls.VirtualizingStackPanel>: Alt denetimler sanallaştırılır ve yatay veya dikey olarak yönelimli tek bir satırda düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-184"><xref:System.Windows.Controls.VirtualizingStackPanel>: Child controls are virtualized and arranged on a single line that is either horizontally or vertically oriented.</span></span>

- <span data-ttu-id="3a4b4-185"><xref:System.Windows.Controls.WrapPanel>: Alt denetimler soldan sağa düzende konumlandırılır ve geçerli satırda alanın izin verdiğinden daha fazla denetim olduğunda sonraki satıra kaydırılır.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-185"><xref:System.Windows.Controls.WrapPanel>: Child controls are positioned in left-to-right order and wrapped to the next line when there are more controls on the current line than space allows.</span></span>

<span data-ttu-id="3a4b4-186">Aşağıdaki örnek, <xref:System.Windows.Controls.DockPanel> çeşitli denetimleri düzenlemek için bir kullanır <xref:System.Windows.Controls.TextBox> :</span><span class="sxs-lookup"><span data-stu-id="3a4b4-186">The following example uses a <xref:System.Windows.Controls.DockPanel> to lay out several <xref:System.Windows.Controls.TextBox> controls:</span></span>

[!code-xaml[IntroToWPFSnippets#LayoutMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_1.xaml)]

<span data-ttu-id="3a4b4-187">, <xref:System.Windows.Controls.DockPanel> Alt <xref:System.Windows.Controls.TextBox> denetimlerin nasıl düzenlendiğini anlatmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-187">The <xref:System.Windows.Controls.DockPanel> allows the child <xref:System.Windows.Controls.TextBox> controls to tell it how to arrange them.</span></span> <span data-ttu-id="3a4b4-188">Bunu yapmak için, <xref:System.Windows.Controls.DockPanel> `Dock` bir yuva stili belirtmesini sağlamak üzere alt denetimlere açık olan iliştirilmiş bir özellik uygular.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-188">To do this, the <xref:System.Windows.Controls.DockPanel> implements a `Dock` attached property that is exposed to the child controls to allow each of them to specify a dock style.</span></span>

> [!NOTE]
> <span data-ttu-id="3a4b4-189">Alt denetimler tarafından kullanılmak üzere bir üst denetim tarafından uygulanan bir özellik, [iliştirilmiş özelliği](advanced/attached-properties-overview.md)olarak ADLANDıRıLAN bir WPF yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-189">A property that's implemented by a parent control for use by child controls is a WPF construct called an [attached property](advanced/attached-properties-overview.md).</span></span>

<span data-ttu-id="3a4b4-190">Aşağıdaki şekilde, önceki örnekteki XAML biçimlendirmesinin sonucu gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="3a4b4-190">The following figure shows the result of the XAML markup in the preceding example:</span></span>

![DockPanel sayfası](media/introduction-to-wpf/wpfintrofigure11.png)

## <a name="data-binding"></a><span data-ttu-id="3a4b4-192">Veri bağlama</span><span class="sxs-lookup"><span data-stu-id="3a4b4-192">Data binding</span></span>

<span data-ttu-id="3a4b4-193">Birçok uygulama, kullanıcılara verileri görüntüleme ve düzenleme araçlarını sağlamak için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-193">Most applications are created to provide users with the means to view and edit data.</span></span> <span data-ttu-id="3a4b4-194">WPF uygulamaları için, veri depolama ve erişme işi SQL Server ve ADO .NET gibi teknolojiler tarafından zaten sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-194">For WPF applications, the work of storing and accessing data is already provided for by technologies such as SQL Server and ADO .NET.</span></span> <span data-ttu-id="3a4b4-195">Verilere erişildikten ve uygulamanın yönetilen nesnelerine yüklendikten sonra, WPF uygulamalarına yönelik sabit çalışma başlar.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-195">After the data is accessed and loaded into an application's managed objects, the hard work for WPF applications begins.</span></span> <span data-ttu-id="3a4b4-196">Temelde, bu iki şeyi içerir:</span><span class="sxs-lookup"><span data-stu-id="3a4b4-196">Essentially, this involves two things:</span></span>

1. <span data-ttu-id="3a4b4-197">Yönetilen nesnelerden verileri, verilerin görüntülenebildiği ve düzenlenebileceği denetimlere kopyalama.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-197">Copying the data from the managed objects into controls, where the data can be displayed and edited.</span></span>

2. <span data-ttu-id="3a4b4-198">Denetimler kullanılarak verilerde yapılan değişikliklerin, yönetilen nesnelere geri kopyalanmasını sağlamak.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-198">Ensuring that changes made to data by using controls are copied back to the managed objects.</span></span>

<span data-ttu-id="3a4b4-199">WPF, uygulama geliştirmeyi basitleştirmek için, bu adımları otomatik olarak gerçekleştirmek üzere bir veri bağlama altyapısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-199">To simplify application development, WPF provides a data binding engine to automatically perform these steps.</span></span> <span data-ttu-id="3a4b4-200">Veri bağlama altyapısının çekirdek birimi, <xref:System.Windows.Data.Binding> işi bir denetimi (bağlama hedefi) bir veri nesnesine (bağlama kaynağı) bağlamak olan sınıftır.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-200">The core unit of the data binding engine is the <xref:System.Windows.Data.Binding> class, whose job is to bind a control (the binding target) to a data object (the binding source).</span></span> <span data-ttu-id="3a4b4-201">Bu ilişki aşağıdaki şekilde gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="3a4b4-201">This relationship is illustrated by the following figure:</span></span>

![Temel veri bağlama diyagramı](media/introduction-to-wpf/databindingmostbasic.png)

<span data-ttu-id="3a4b4-203">Sonraki örnekte, bir <xref:System.Windows.Controls.TextBox> özel nesne örneğine nasıl bağlanacağı gösterilmektedir `Person` .</span><span class="sxs-lookup"><span data-stu-id="3a4b4-203">The next example demonstrates how to bind a <xref:System.Windows.Controls.TextBox> to an instance of a custom `Person` object.</span></span> <span data-ttu-id="3a4b4-204">`Person`Uygulama aşağıdaki kodda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="3a4b4-204">The `Person` implementation is shown in the following code:</span></span>

[!code-vb[SimpleDataBindingSnippets#PersonClassCODE](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_2.vb)]
[!code-csharp[SimpleDataBindingSnippets#PersonClassCODE](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_2.cs)]

<span data-ttu-id="3a4b4-205">Aşağıdaki biçimlendirme, öğesini bir <xref:System.Windows.Controls.TextBox> özel nesne örneğine bağlar `Person` :</span><span class="sxs-lookup"><span data-stu-id="3a4b4-205">The following markup binds the <xref:System.Windows.Controls.TextBox> to an instance of a custom `Person` object:</span></span>

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

<span data-ttu-id="3a4b4-206">Bu örnekte, `Person` sınıfı arka plan kodunda oluşturulur ve için veri bağlamı olarak ayarlanır `DataBindingWindow` .</span><span class="sxs-lookup"><span data-stu-id="3a4b4-206">In this example, the `Person` class is instantiated in code-behind and is set as the data context for the `DataBindingWindow`.</span></span> <span data-ttu-id="3a4b4-207">Biçimlendirme bölümünde <xref:System.Windows.Controls.TextBox.Text%2A> öğesinin özelliği <xref:System.Windows.Controls.TextBox> `Person.Name` özelliğine bağlanır (" `{Binding ... }` " xaml sözdizimi kullanılarak).</span><span class="sxs-lookup"><span data-stu-id="3a4b4-207">In markup, the <xref:System.Windows.Controls.TextBox.Text%2A> property of the <xref:System.Windows.Controls.TextBox> is bound to the `Person.Name` property (using the "`{Binding ... }`" XAML syntax).</span></span> <span data-ttu-id="3a4b4-208">Bu XAML, WPF <xref:System.Windows.Controls.TextBox> `Person` 'in denetimi pencerenin özelliğinde depolanan nesneye bağlamasını söyler <xref:System.Windows.FrameworkElement.DataContext%2A> .</span><span class="sxs-lookup"><span data-stu-id="3a4b4-208">This XAML tells WPF to bind the <xref:System.Windows.Controls.TextBox> control to the `Person` object that is stored in the <xref:System.Windows.FrameworkElement.DataContext%2A> property of the window.</span></span>

<span data-ttu-id="3a4b4-209">WPF veri bağlama altyapısı, doğrulama, sıralama, filtreleme ve gruplamayı içeren ek destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-209">The WPF data binding engine provides additional support that includes validation, sorting, filtering, and grouping.</span></span> <span data-ttu-id="3a4b4-210">Ayrıca, veri bağlama, standart WPF denetimleri tarafından görüntülenecek kullanıcı arabirimi uygun olmadığında, bağlantılı veriler için özel kullanıcı arabirimi oluşturmak üzere veri şablonlarının kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-210">Furthermore, data binding supports the use of data templates to create custom user interface for bound data when the user interface displayed by the standard WPF controls is not appropriate.</span></span>

<span data-ttu-id="3a4b4-211">Daha fazla bilgi için bkz. [veri bağlamaya genel bakış](../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3a4b4-211">For more information, see [Data binding overview](../../desktop-wpf/data/data-binding-overview.md).</span></span>

## <a name="graphics"></a><span data-ttu-id="3a4b4-212">Grafikler</span><span class="sxs-lookup"><span data-stu-id="3a4b4-212">Graphics</span></span>

<span data-ttu-id="3a4b4-213">WPF, aşağıdaki avantajları içeren kapsamlı, ölçeklenebilir ve esnek bir grafik özellikleri kümesi sunar:</span><span class="sxs-lookup"><span data-stu-id="3a4b4-213">WPF introduces an extensive, scalable, and flexible set of graphics features that have the following benefits:</span></span>

- <span data-ttu-id="3a4b4-214">**Çözünürlükten bağımsız ve cihazdan bağımsız grafikler**.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-214">**Resolution-independent and device-independent graphics**.</span></span> <span data-ttu-id="3a4b4-215">WPF Grafik sistemindeki temel ölçü birimi, gerçek ekran çözünürlüğünden bağımsız olarak bir inç 1/96th olan cihazdan bağımsız pikseldir ve çözünürlükten bağımsız ve cihazdan bağımsız işleme için temel sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-215">The basic unit of measurement in the WPF graphics system is the device-independent pixel, which is 1/96th of an inch, regardless of actual screen resolution, and provides the foundation for resolution-independent and device-independent rendering.</span></span> <span data-ttu-id="3a4b4-216">Her cihazdan bağımsız piksel, üzerinde oluşturduğu sistemin inç başına nokta (DPI) ayarıyla eşleşecek şekilde otomatik olarak ölçeklendirilir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-216">Each device-independent pixel automatically scales to match the dots-per-inch (dpi) setting of the system it renders on.</span></span>

- <span data-ttu-id="3a4b4-217">**İyileştirilmiş duyarlık**.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-217">**Improved precision**.</span></span> <span data-ttu-id="3a4b4-218">WPF koordinat sistemi, tek duyarlık yerine çift duyarlıklı kayan noktalı sayılar ile ölçülür.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-218">The WPF coordinate system is measured with double-precision floating-point numbers rather than single-precision.</span></span> <span data-ttu-id="3a4b4-219">Dönüşümler ve opaklık değerleri de çift duyarlıklı olarak ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-219">Transformations and opacity values are also expressed as double-precision.</span></span> <span data-ttu-id="3a4b4-220">WPF ayrıca geniş bir renk gamutu (scRGB) destekler ve farklı renk uzaylarından girişleri yönetmek için tümleşik destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-220">WPF also supports a wide color gamut (scRGB) and provides integrated support for managing inputs from different color spaces.</span></span>

- <span data-ttu-id="3a4b4-221">**Gelişmiş grafikler ve animasyon desteği**.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-221">**Advanced graphics and animation support**.</span></span> <span data-ttu-id="3a4b4-222">WPF, sizin için animasyon sahneleri yöneterek grafik programlamayı basitleştirir; sahne işleme, işleme döngüleri ve Bilinear ilişkilendirme konusunda endişelenmenize gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-222">WPF simplifies graphics programming by managing animation scenes for you; there is no need to worry about scene processing, rendering loops, and bilinear interpolation.</span></span> <span data-ttu-id="3a4b4-223">Ayrıca WPF, isabet testi desteği ve tam alfa birleştirme desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-223">Additionally, WPF provides hit-testing support and full alpha-compositing support.</span></span>

- <span data-ttu-id="3a4b4-224">**Donanım hızlandırma**.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-224">**Hardware acceleration**.</span></span> <span data-ttu-id="3a4b4-225">WPF Grafik sistemi, CPU kullanımını en aza indirmek için grafik donanımından yararlanır.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-225">The WPF graphics system takes advantage of graphics hardware to minimize CPU usage.</span></span>

### <a name="2d-shapes"></a><span data-ttu-id="3a4b4-226">2B şekiller</span><span class="sxs-lookup"><span data-stu-id="3a4b4-226">2D shapes</span></span>

<span data-ttu-id="3a4b4-227">WPF, aşağıdaki çizimde gösterilen dikdörtgenler ve üç nokta gibi yaygın bir vektör çizilmiş 2B şekil kitaplığı sağlar:</span><span class="sxs-lookup"><span data-stu-id="3a4b4-227">WPF provides a library of common vector-drawn 2D shapes, such as the rectangles and ellipses that are shown in the following illustration:</span></span>

![Üç nokta ve dikdörtgen](media/introduction-to-wpf/wpfintrofigure4.PNG)

<span data-ttu-id="3a4b4-229">Şekillerin ilginç bir özelliği yalnızca görüntüleme için değildir; şekiller, klavye ve fare girişi dahil olmak üzere denetimlerden beklediğinizi birçok özelliği uygular.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-229">An interesting capability of shapes is that they are not just for display; shapes implement many of the features that you expect from controls, including keyboard and mouse input.</span></span> <span data-ttu-id="3a4b4-230">Aşağıdaki örnek, <xref:System.Windows.UIElement.MouseUp> işlenmekte olan olayını gösterir <xref:System.Windows.Shapes.Ellipse> :</span><span class="sxs-lookup"><span data-stu-id="3a4b4-230">The following example shows the <xref:System.Windows.UIElement.MouseUp> event of an <xref:System.Windows.Shapes.Ellipse> being handled:</span></span>

[!code-xaml[IntroToWPFSnippets#HandleEllipseMouseUpEventMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_7.xaml)]

[!code-vb[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_8.vb)]
[!code-csharp[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_8.cs)]

<span data-ttu-id="3a4b4-231">Aşağıdaki şekilde, önceki kod tarafından üretilen değer gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="3a4b4-231">The following figure shows what is produced by the preceding code:</span></span>

!["Elips tıkladınız&#33;" metnini içeren pencere](media/introduction-to-wpf/wpfintrofigure12.png)

<span data-ttu-id="3a4b4-233">Daha fazla bilgi için bkz. [WPF 'de şekillere ve temel çizime genel bakış](../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3a4b4-233">For more information, see [Shapes and basic drawing in WPF overview](../../desktop-wpf/data/data-binding-overview.md).</span></span>

### <a name="2d-geometries"></a><span data-ttu-id="3a4b4-234">2B geometriler</span><span class="sxs-lookup"><span data-stu-id="3a4b4-234">2D geometries</span></span>

<span data-ttu-id="3a4b4-235">WPF tarafından sunulan 2B şekiller, temel şekillerin standart kümesini kapsar.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-235">The 2D shapes provided by WPF cover the standard set of basic shapes.</span></span> <span data-ttu-id="3a4b4-236">Ancak, özelleştirilmiş bir kullanıcı arabiriminin tasarımını kolaylaştırmak için özel şekiller oluşturmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-236">However, you may need to create custom shapes to facilitate the design of a customized user interface.</span></span> <span data-ttu-id="3a4b4-237">Bu amaçla WPF, geometriler sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-237">For this purpose, WPF provides geometries.</span></span> <span data-ttu-id="3a4b4-238">Aşağıdaki şekilde, doğrudan çizilemeyen, fırça olarak kullanılan veya diğer şekilleri ve denetimleri kırpmak için kullanılan özel bir şekil oluşturmak için geometriler kullanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-238">The following figure demonstrates the use of geometries to create a custom shape that can be drawn directly, used as a brush, or used to clip other shapes and controls.</span></span>

<span data-ttu-id="3a4b4-239"><xref:System.Windows.Shapes.Path>nesneler, kapalı veya açık şekiller, birden çok şekil ve hatta eğri şekiller çizmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-239"><xref:System.Windows.Shapes.Path> objects can be used to draw closed or open shapes, multiple shapes, and even curved shapes.</span></span>

<span data-ttu-id="3a4b4-240"><xref:System.Windows.Media.Geometry>nesneler kırpma, isabet sınama ve 2B grafik verileri işleme için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-240"><xref:System.Windows.Media.Geometry> objects can be used for clipping, hit-testing, and rendering 2D graphic data.</span></span>

![Yolun çeşitli kullanımları](media/introduction-to-wpf/wpfintrofigure5.png)

<span data-ttu-id="3a4b4-242">Daha fazla bilgi için bkz. [geometriye genel bakış](graphics-multimedia/geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3a4b4-242">For more information, see [Geometry overview](graphics-multimedia/geometry-overview.md).</span></span>

### <a name="2d-effects"></a><span data-ttu-id="3a4b4-243">2B efektler</span><span class="sxs-lookup"><span data-stu-id="3a4b4-243">2D effects</span></span>

<span data-ttu-id="3a4b4-244">WPF 2B özellikleri alt kümesi degradeler, bit eşlemler, çizimler, videolar, döndürme, ölçeklendirme ve eğriltme gibi görsel etkileri içerir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-244">A subset of WPF 2D capabilities includes visual effects, such as gradients, bitmaps, drawings, painting with videos, rotation, scaling, and skewing.</span></span> <span data-ttu-id="3a4b4-245">Bunlar fırçalar ile elde edilir; Aşağıdaki şekilde bazı örnekler gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="3a4b4-245">These are all achieved with brushes; the following figure shows some examples:</span></span>

![Farklı fırçaların çizimi](media/introduction-to-wpf/wpfintrofigure6.png)

<span data-ttu-id="3a4b4-247">Daha fazla bilgi için bkz. [WPF Fırçalarına Genel Bakış](graphics-multimedia/wpf-brushes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3a4b4-247">For more information, see [WPF brushes overview](graphics-multimedia/wpf-brushes-overview.md).</span></span>

### <a name="3d-rendering"></a><span data-ttu-id="3a4b4-248">3B işleme</span><span class="sxs-lookup"><span data-stu-id="3a4b4-248">3D rendering</span></span>

<span data-ttu-id="3a4b4-249">WPF ayrıca, daha heyecan verici ve ilginç Kullanıcı arabirimleri oluşturulmasına olanak tanımak için 2B grafiklerle tümleştirilen 3B işleme özelliklerini de içerir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-249">WPF also includes 3D rendering capabilities that integrate with 2D graphics to allow the creation of more exciting and interesting user interfaces.</span></span> <span data-ttu-id="3a4b4-250">Örneğin, aşağıdaki şekilde 3B şekiller üzerinde işlenen 2D görüntüleri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="3a4b4-250">For example, the following figure shows 2D images rendered onto 3D shapes:</span></span>

![Visual3d değil örnek ekran görüntüsü](media/introduction-to-wpf/wpfintrofigure13.png)

<span data-ttu-id="3a4b4-252">Daha fazla bilgi için bkz. [3B grafiklere genel bakış](graphics-multimedia/3-d-graphics-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3a4b4-252">For more information, see [3D graphics overview](graphics-multimedia/3-d-graphics-overview.md).</span></span>

## <a name="animation"></a><span data-ttu-id="3a4b4-253">Animasyon</span><span class="sxs-lookup"><span data-stu-id="3a4b4-253">Animation</span></span>

<span data-ttu-id="3a4b4-254">WPF animasyon desteği, denetimlerin büyümesi, sallanması, dönmesi ve belirmesini, ilginç sayfa geçişleri oluşturmak ve daha fazlasını yapmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-254">WPF animation support lets you make controls grow, shake, spin, and fade, to create interesting page transitions, and more.</span></span> <span data-ttu-id="3a4b4-255">Birçok WPF sınıfının, hatta özel sınıfların animasyonunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-255">You can animate most WPF classes, even custom classes.</span></span> <span data-ttu-id="3a4b4-256">Aşağıdaki şekilde, eylem içinde basit bir animasyon gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="3a4b4-256">The following figure shows a simple animation in action:</span></span>

![Animasyonlu küpün görüntüleri](media/introduction-to-wpf/wpfintrofigure7.png)

<span data-ttu-id="3a4b4-258">Daha fazla bilgi için bkz. [animasyon genel bakış](graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3a4b4-258">For more information, see [Animation overview](graphics-multimedia/animation-overview.md).</span></span>

## <a name="media"></a><span data-ttu-id="3a4b4-259">Medya</span><span class="sxs-lookup"><span data-stu-id="3a4b4-259">Media</span></span>

<span data-ttu-id="3a4b4-260">Zengin içerik iletmenin bir yolu, Audiovisual medyası kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-260">One way to convey rich content is through the use of audiovisual media.</span></span> <span data-ttu-id="3a4b4-261">WPF, görüntüler, videolar ve ses için özel destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-261">WPF provides special support for images, video, and audio.</span></span>

### <a name="images"></a><span data-ttu-id="3a4b4-262">Görüntüler</span><span class="sxs-lookup"><span data-stu-id="3a4b4-262">Images</span></span>

<span data-ttu-id="3a4b4-263">Görüntüler çoğu uygulama için ortaktır ve WPF bunları kullanmak için çeşitli yollar sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-263">Images are common to most applications, and WPF provides several ways to use them.</span></span> <span data-ttu-id="3a4b4-264">Aşağıdaki şekilde, küçük resim görüntüleri içeren bir liste kutusuyla bir kullanıcı arabirimi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-264">The following figure shows a user interface with a list box that contains thumbnail images.</span></span> <span data-ttu-id="3a4b4-265">Küçük resim seçildiğinde görüntü tam boyut olarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-265">When a thumbnail is selected, the image is shown full-size.</span></span>

![Küçük resim görüntüleri ve tam&#45;boyutu görüntüsü](media/introduction-to-wpf/wpfintrofigure8.png)

<span data-ttu-id="3a4b4-267">Daha fazla bilgi için bkz. [Imaging 'e genel bakış](graphics-multimedia/imaging-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3a4b4-267">For more information, see [Imaging overview](graphics-multimedia/imaging-overview.md).</span></span>

### <a name="video-and-audio"></a><span data-ttu-id="3a4b4-268">Video ve ses</span><span class="sxs-lookup"><span data-stu-id="3a4b4-268">Video and audio</span></span>

<span data-ttu-id="3a4b4-269"><xref:System.Windows.Controls.MediaElement>Denetim hem videoyu hem de sesi oynatabilen ve özel bir medya yürütücüsünün temeli olması yeterince esnektir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-269">The <xref:System.Windows.Controls.MediaElement> control is capable of playing both video and audio, and it is flexible enough to be the basis for a custom media player.</span></span> <span data-ttu-id="3a4b4-270">Aşağıdaki XAML biçimlendirmesi bir medya oynatıcı uygular:</span><span class="sxs-lookup"><span data-stu-id="3a4b4-270">The following XAML markup implements a media player:</span></span>

[!code-xaml[IntroToWPFSnippets#MediaElementMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_9.xaml)]

<span data-ttu-id="3a4b4-271">Aşağıdaki şekilde gösterilen pencerede <xref:System.Windows.Controls.MediaElement> Denetim eylemi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="3a4b4-271">The window in the following figure shows the <xref:System.Windows.Controls.MediaElement> control in action:</span></span>

![Ses ve video ile MediaElement denetimi](media/introduction-to-wpf/wpfintrofigure1.png)

<span data-ttu-id="3a4b4-273">Daha fazla bilgi için bkz. [grafik ve multimedya](graphics-multimedia/index.md).</span><span class="sxs-lookup"><span data-stu-id="3a4b4-273">For more information, see [Graphics and multimedia](graphics-multimedia/index.md).</span></span>

## <a name="text-and-typography"></a><span data-ttu-id="3a4b4-274">Metin ve tipografi</span><span class="sxs-lookup"><span data-stu-id="3a4b4-274">Text and typography</span></span>

<span data-ttu-id="3a4b4-275">WPF, yüksek kaliteli metin işlemesini kolaylaştırmak için aşağıdaki özellikleri sunar:</span><span class="sxs-lookup"><span data-stu-id="3a4b4-275">To facilitate high-quality text rendering, WPF offers the following features:</span></span>

- <span data-ttu-id="3a4b4-276">OpenType yazı tipi desteği.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-276">OpenType font support.</span></span>

- <span data-ttu-id="3a4b4-277">ClearType geliştirmeleri.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-277">ClearType enhancements.</span></span>

- <span data-ttu-id="3a4b4-278">Donanım hızlandırmasının avantajlarından yararlanan yüksek performans.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-278">High performance that takes advantage of hardware acceleration.</span></span>

- <span data-ttu-id="3a4b4-279">Medya, grafik ve animasyonla metin tümleştirmesi.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-279">Integration of text with media, graphics, and animation.</span></span>

- <span data-ttu-id="3a4b4-280">Uluslararası yazı tipi desteği ve geri dönüş mekanizmaları.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-280">International font support and fallback mechanisms.</span></span>

<span data-ttu-id="3a4b4-281">Grafiklerle metin tümleştirmesinin bir sunumu olarak aşağıdaki şekil metin düzenlemelerinin uygulamasını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="3a4b4-281">As a demonstration of text integration with graphics, the following figure shows the application of text decorations:</span></span>

![Çeşitli metin süslemeleri içeren metin](media/introduction-to-wpf/wpfintrofigure23.png)

<span data-ttu-id="3a4b4-283">Daha fazla bilgi için bkz. [tipografi Windows Presentation Foundation](advanced/typography-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="3a4b4-283">For more information, see [Typography in Windows Presentation Foundation](advanced/typography-in-wpf.md).</span></span>

## <a name="customize-wpf-apps"></a><span data-ttu-id="3a4b4-284">WPF uygulamalarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="3a4b4-284">Customize WPF apps</span></span>

<span data-ttu-id="3a4b4-285">Bu noktaya kadar, uygulama geliştirmeye yönelik temel WPF yapı taşlarını gördünüz.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-285">Up to this point, you've seen the core WPF building blocks for developing applications.</span></span> <span data-ttu-id="3a4b4-286">Genellikle denetimlerden oluşan uygulama içeriğini barındırmak ve sunmak için uygulama modelini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-286">You use the application model to host and deliver application content, which consists mainly of controls.</span></span> <span data-ttu-id="3a4b4-287">Bir kullanıcı arabirimindeki denetimlerin düzenlemesini basitleştirmek ve düzenlemenin pencere boyutu ve görüntüleme ayarlarında yapılan değişiklikler üzerinde tutulmasını sağlamak için WPF düzen sistemini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-287">To simplify the arrangement of controls in a user interface, and to ensure the arrangement is maintained in the face of changes to window size and display settings, you use the WPF layout system.</span></span> <span data-ttu-id="3a4b4-288">Çoğu uygulama, kullanıcıların verilerle etkileşime girmesine izin vertiğinden, Kullanıcı arabiriminizi verilerle tümleştirme işini azaltmak için veri bağlamayı kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-288">Because most applications let users interact with data, you use data binding to reduce the work of integrating your user interface with data.</span></span> <span data-ttu-id="3a4b4-289">Uygulamanızın görsel görünümünü geliştirmek için WPF tarafından sunulan kapsamlı grafik, animasyon ve medya desteği aralığını kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-289">To enhance the visual appearance of your application, you use the comprehensive range of graphics, animation, and media support provided by WPF.</span></span>

<span data-ttu-id="3a4b4-290">Genellikle, temel bilgiler, gerçekten ayrı ve görsel açıdan etkileyici bir kullanıcı deneyimi oluşturmak ve yönetmek için yeterli değildir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-290">Often, though, the basics are not enough for creating and managing a truly distinct and visually stunning user experience.</span></span> <span data-ttu-id="3a4b4-291">Standart WPF denetimleri uygulamanızın istenen görünümüyle tümleştirilemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-291">The standard WPF controls might not integrate with the desired appearance of your application.</span></span> <span data-ttu-id="3a4b4-292">Veriler en etkili şekilde görüntülenmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-292">Data might not be displayed in the most effective way.</span></span> <span data-ttu-id="3a4b4-293">Uygulamanızın genel kullanıcı deneyimi, Windows temalarının varsayılan görünümü ve hislerine uygun olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-293">Your application's overall user experience may not be suited to the default look and feel of Windows themes.</span></span> <span data-ttu-id="3a4b4-294">Birçok şekilde, bir sunum teknolojisinin diğer genişletilebilirlik türleri kadar çok görsel genişletilebilirliği olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-294">In many ways, a presentation technology needs visual extensibility as much as any other type of extensibility.</span></span>

<span data-ttu-id="3a4b4-295">Bu nedenle WPF, denetimler, Tetikleyiciler, denetim ve veri şablonları, stiller, Kullanıcı arabirimi kaynakları ve Temalar ve kaplamalar için zengin bir içerik modeli de dahil olmak üzere benzersiz kullanıcı deneyimleri oluşturmak için çeşitli mekanizmalar sunar.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-295">For this reason, WPF provides a variety of mechanisms for creating unique user experiences, including a rich content model for controls, triggers, control and data templates, styles, user interface resources, and themes and skins.</span></span>

### <a name="content-model"></a><span data-ttu-id="3a4b4-296">İçerik modeli</span><span class="sxs-lookup"><span data-stu-id="3a4b4-296">Content model</span></span>

<span data-ttu-id="3a4b4-297">WPF denetimlerinin çoğunluğunun ana amacı içeriği görüntülemektir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-297">The main purpose of a majority of the WPF controls is to display content.</span></span> <span data-ttu-id="3a4b4-298">WPF içinde, bir denetimin içeriğini oluşturan öğelerin türü ve sayısı denetimin *içerik modeli*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-298">In WPF, the type and number of items that can constitute the content of a control is referred to as the control's *content model*.</span></span> <span data-ttu-id="3a4b4-299">Bazı denetimler, tek bir öğe ve içerik türü içerebilir; Örneğin, öğesinin içeriği <xref:System.Windows.Controls.TextBox> özelliğine atanan bir dize değeridir <xref:System.Windows.Controls.TextBox.Text%2A> .</span><span class="sxs-lookup"><span data-stu-id="3a4b4-299">Some controls can contain a single item and type of content; for example, the content of a <xref:System.Windows.Controls.TextBox> is a string value that is assigned to the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span> <span data-ttu-id="3a4b4-300">Aşağıdaki örnek bir öğesinin içeriğini ayarlar <xref:System.Windows.Controls.TextBox> :</span><span class="sxs-lookup"><span data-stu-id="3a4b4-300">The following example sets the content of a <xref:System.Windows.Controls.TextBox>:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.TextBoxContentWindow"
    Title="TextBox Content">

    <TextBox Text="This is the content of a TextBox." />
</Window>
```

<span data-ttu-id="3a4b4-301">Aşağıdaki şekilde sonuç gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="3a4b4-301">The following figure shows the result:</span></span>

![Metin içeren TextBox denetimi](media/introduction-to-wpf/wpfintrofigure21.png)

<span data-ttu-id="3a4b4-303">Bununla birlikte, diğer denetimler farklı türde içeriklerde birden çok öğe içerebilir; özelliği tarafından belirtilen bir öğesinin içeriği, <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.ContentControl.Content%2A> düzen denetimleri, metin, Resimler ve şekiller gibi çeşitli öğeleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-303">Other controls, however, can contain multiple items of different types of content; the content of a <xref:System.Windows.Controls.Button>, specified by the <xref:System.Windows.Controls.ContentControl.Content%2A> property, can contain a variety of items including layout controls, text, images, and shapes.</span></span> <span data-ttu-id="3a4b4-304">Aşağıdaki örnek, bir,, <xref:System.Windows.Controls.Button> a ve içeren içeriği içeren bir gösterir <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.Border> <xref:System.Windows.Controls.MediaElement> :</span><span class="sxs-lookup"><span data-stu-id="3a4b4-304">The following example shows a <xref:System.Windows.Controls.Button> with content that includes a <xref:System.Windows.Controls.DockPanel>, a <xref:System.Windows.Controls.Label>, a <xref:System.Windows.Controls.Border>, and a <xref:System.Windows.Controls.MediaElement>:</span></span>

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

<span data-ttu-id="3a4b4-305">Aşağıdaki şekilde bu düğmenin içeriği gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="3a4b4-305">The following figure shows the content of this button:</span></span>

![Birden çok türde içerik içeren bir düğme](media/introduction-to-wpf/wpfintrofigure22.png)

<span data-ttu-id="3a4b4-307">Çeşitli denetimler tarafından desteklenen içerik türleri hakkında daha fazla bilgi için bkz. [WPF içerik modeli](controls/wpf-content-model.md).</span><span class="sxs-lookup"><span data-stu-id="3a4b4-307">For more information on the kinds of content that is supported by various controls, see [WPF content model](controls/wpf-content-model.md).</span></span>

### <a name="triggers"></a><span data-ttu-id="3a4b4-308">Tetikleyiciler</span><span class="sxs-lookup"><span data-stu-id="3a4b4-308">Triggers</span></span>

<span data-ttu-id="3a4b4-309">XAML biçimlendirmesinin ana amacı uygulamanın görünümünü uygulamak olsa da, bir uygulamanın davranışının bazı yönlerini uygulamak için XAML de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-309">Although the main purpose of XAML markup is to implement an application's appearance, you can also use XAML to implement some aspects of an application's behavior.</span></span> <span data-ttu-id="3a4b4-310">Bir örnek, bir uygulamanın görünümünü kullanıcı etkileşimlerine göre değiştirmek için tetikleyicilerin kullanılması.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-310">One example is the use of triggers to change an application's appearance based on user interactions.</span></span> <span data-ttu-id="3a4b4-311">Daha fazla bilgi için bkz. [Stiller ve şablonlar](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3a4b4-311">For more information, see [Styles and templates](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

### <a name="control-templates"></a><span data-ttu-id="3a4b4-312">Denetim şablonları</span><span class="sxs-lookup"><span data-stu-id="3a4b4-312">Control templates</span></span>

<span data-ttu-id="3a4b4-313">WPF denetimleri için varsayılan kullanıcı arabirimleri genellikle diğer denetimlerden ve şekillerden oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-313">The default user interfaces for WPF controls are typically constructed from other controls and shapes.</span></span> <span data-ttu-id="3a4b4-314">Örneğin, bir, <xref:System.Windows.Controls.Button> <xref:Microsoft.Windows.Themes.ButtonChrome> ve <xref:System.Windows.Controls.ContentPresenter> denetimlerinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-314">For example, a <xref:System.Windows.Controls.Button> is composed of both <xref:Microsoft.Windows.Themes.ButtonChrome> and <xref:System.Windows.Controls.ContentPresenter> controls.</span></span> <span data-ttu-id="3a4b4-315">, <xref:Microsoft.Windows.Themes.ButtonChrome> Standart düğme görünümünü sağlar, ancak <xref:System.Windows.Controls.ContentPresenter> düğme içeriğini özelliği tarafından belirtilen şekilde görüntüler <xref:System.Windows.Controls.ContentControl.Content%2A> .</span><span class="sxs-lookup"><span data-stu-id="3a4b4-315">The <xref:Microsoft.Windows.Themes.ButtonChrome> provides the standard button appearance, while the <xref:System.Windows.Controls.ContentPresenter> displays the button's content, as specified by the <xref:System.Windows.Controls.ContentControl.Content%2A> property.</span></span>

<span data-ttu-id="3a4b4-316">Bazen bir denetimin varsayılan görünümü bir uygulamanın genel görünümüyle birlikte kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-316">Sometimes the default appearance of a control may be incongruent with the overall appearance of an application.</span></span> <span data-ttu-id="3a4b4-317">Bu durumda, <xref:System.Windows.Controls.ControlTemplate> içeriğini ve davranışını değiştirmeden denetimin kullanıcı arabiriminin görünümünü değiştirmek için bir kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-317">In this case, you can use a <xref:System.Windows.Controls.ControlTemplate> to change the appearance of the control's user interface without changing its content and behavior.</span></span>

<span data-ttu-id="3a4b4-318">Aşağıdaki örnek, öğesinin görünümünü kullanarak nasıl değiştirileceğini göstermektedir <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.ControlTemplate> :</span><span class="sxs-lookup"><span data-stu-id="3a4b4-318">The following example shows how to change the appearance of a <xref:System.Windows.Controls.Button> by using a <xref:System.Windows.Controls.ControlTemplate>:</span></span>

[!code-xaml[IntroToWPFSnippets#ButtonControlTemplateWindowMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_16.xaml)]

[!code-csharp[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_17.cs)]
[!code-vb[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_17.vb)]

<span data-ttu-id="3a4b4-319">Bu örnekte, varsayılan düğme Kullanıcı arabirimi <xref:System.Windows.Shapes.Ellipse> koyu mavi kenarlığa sahip olan ve kullanılarak doldurulmuş bir ile değiştirilmiştir <xref:System.Windows.Media.RadialGradientBrush> .</span><span class="sxs-lookup"><span data-stu-id="3a4b4-319">In this example, the default button user interface has been replaced with an <xref:System.Windows.Shapes.Ellipse> that has a dark blue border and is filled using a <xref:System.Windows.Media.RadialGradientBrush>.</span></span> <span data-ttu-id="3a4b4-320"><xref:System.Windows.Controls.ContentPresenter>Denetimde içeriğini görüntüleyen denetim <xref:System.Windows.Controls.Button> , "bana tıklama!"</span><span class="sxs-lookup"><span data-stu-id="3a4b4-320">The <xref:System.Windows.Controls.ContentPresenter> control displays the content of the <xref:System.Windows.Controls.Button>, "Click Me!"</span></span> <span data-ttu-id="3a4b4-321"><xref:System.Windows.Controls.Button>Tıklandığında <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay, denetimin varsayılan davranışının bir parçası olarak yine de oluşturulur <xref:System.Windows.Controls.Button> .</span><span class="sxs-lookup"><span data-stu-id="3a4b4-321">When the <xref:System.Windows.Controls.Button> is clicked, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event is still raised as part of the <xref:System.Windows.Controls.Button> control's default behavior.</span></span> <span data-ttu-id="3a4b4-322">Sonuç aşağıdaki şekilde gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="3a4b4-322">The result is shown in the following figure:</span></span>

![Elips düğme ve ikinci bir pencere](media/introduction-to-wpf/wpfintrofigure2.png)

### <a name="data-templates"></a><span data-ttu-id="3a4b4-324">Veri şablonları</span><span class="sxs-lookup"><span data-stu-id="3a4b4-324">Data templates</span></span>

<span data-ttu-id="3a4b4-325">Bir denetim şablonu bir denetimin görünümünü belirtmenize izin verirken, bir veri şablonu bir denetimin içeriğinin görünümünü belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-325">Whereas a control template lets you specify the appearance of a control, a data template lets you specify the appearance of a control's content.</span></span> <span data-ttu-id="3a4b4-326">Veri şablonları genellikle, bağlantılı verilerin nasıl görüntülendiğini iyileştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-326">Data templates are frequently used to enhance how bound data is displayed.</span></span> <span data-ttu-id="3a4b4-327">Aşağıdaki şekilde, <xref:System.Windows.Controls.ListBox> `Task` her görevin bir adı, açıklaması ve önceliği olduğu bir nesne koleksiyonuna bağlanan bir için varsayılan görünüm gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="3a4b4-327">The following figure shows the default appearance for a <xref:System.Windows.Controls.ListBox> that is bound to a collection of `Task` objects, where each task has a name, description, and priority:</span></span>

![Varsayılan görünümü içeren bir liste kutusu](media/introduction-to-wpf/wpfintrofigure18.png)

<span data-ttu-id="3a4b4-329">Varsayılan görünüm, bir ' dan beklediğiniz şeydir <xref:System.Windows.Controls.ListBox> .</span><span class="sxs-lookup"><span data-stu-id="3a4b4-329">The default appearance is what you would expect from a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="3a4b4-330">Ancak, her görevin varsayılan görünümü yalnızca görev adını içerir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-330">However, the default appearance of each task contains only the task name.</span></span> <span data-ttu-id="3a4b4-331">Görev adını, açıklamasını ve önceliğini göstermek için, <xref:System.Windows.Controls.ListBox> denetimin bağlantılı liste öğelerinin varsayılan görünümünün bir kullanılarak değiştirilmesi gerekir <xref:System.Windows.DataTemplate> .</span><span class="sxs-lookup"><span data-stu-id="3a4b4-331">To show the task name, description, and priority, the default appearance of the <xref:System.Windows.Controls.ListBox> control's bound list items must be changed by using a <xref:System.Windows.DataTemplate>.</span></span> <span data-ttu-id="3a4b4-332">Aşağıdaki XAML, bu tür bir <xref:System.Windows.DataTemplate> , özniteliği kullanılarak her bir göreve uygulanan böyle bir tanımlar <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> :</span><span class="sxs-lookup"><span data-stu-id="3a4b4-332">The following XAML defines such a <xref:System.Windows.DataTemplate>, which is applied to each task by using the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> attribute:</span></span>

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

<span data-ttu-id="3a4b4-333">Aşağıdaki şekilde, bu kodun etkisi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="3a4b4-333">The following figure shows the effect of this code:</span></span>

![Veri şablonu kullanan liste kutusu](media/introduction-to-wpf/wpfintrofigure19.png)

<span data-ttu-id="3a4b4-335">Öğesinin <xref:System.Windows.Controls.ListBox> davranışını ve genel görünümünü beklediğine ve yalnızca liste kutusu tarafından görüntülenen içeriğin görünümü değiştiği unutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-335">Note that the <xref:System.Windows.Controls.ListBox> has retained its behavior and overall appearance; only the appearance of the content being displayed by the list box has changed.</span></span>

<span data-ttu-id="3a4b4-336">Daha fazla bilgi için bkz. [veri şablonu oluşturmaya genel bakış](data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3a4b4-336">For more information, see [Data templating overview](data/data-templating-overview.md).</span></span>

### <a name="styles"></a><span data-ttu-id="3a4b4-337">Stiller</span><span class="sxs-lookup"><span data-stu-id="3a4b4-337">Styles</span></span>

<span data-ttu-id="3a4b4-338">Stiller, geliştiricilerin ve tasarımcıların ürünlerinin belirli bir görünümünü standartlaştırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-338">Styles enable developers and designers to standardize on a particular appearance for their product.</span></span> <span data-ttu-id="3a4b4-339">WPF, öğesi olan bir güçlü stil modeli sunar <xref:System.Windows.Style> .</span><span class="sxs-lookup"><span data-stu-id="3a4b4-339">WPF provides a strong style model, the foundation of which is the <xref:System.Windows.Style> element.</span></span> <span data-ttu-id="3a4b4-340">Aşağıdaki örnek, her bir pencerede için arka plan rengini ayarlayan bir stil oluşturur <xref:System.Windows.Controls.Button> `Orange` :</span><span class="sxs-lookup"><span data-stu-id="3a4b4-340">The following example creates a style that sets the background color for every <xref:System.Windows.Controls.Button> on a window to `Orange`:</span></span>

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

<span data-ttu-id="3a4b4-341">Bu stil tüm denetimleri hedeflediğinden <xref:System.Windows.Controls.Button> , stil, aşağıdaki şekilde gösterildiği gibi penceredeki tüm düğmelere otomatik olarak uygulanır:</span><span class="sxs-lookup"><span data-stu-id="3a4b4-341">Because this style targets all <xref:System.Windows.Controls.Button> controls, the style is automatically applied to all the buttons in the window, as shown in the following figure:</span></span>

![İki turuncu düğme](media/introduction-to-wpf/wpfintrofigure20.png)

<span data-ttu-id="3a4b4-343">Daha fazla bilgi için bkz. [Stiller ve şablonlar](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3a4b4-343">For more information, see [Styles and templates](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

### <a name="resources"></a><span data-ttu-id="3a4b4-344">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="3a4b4-344">Resources</span></span>

<span data-ttu-id="3a4b4-345">Bir uygulamadaki denetimler aynı görünümü paylaşmalıdır. Bu, yazı tiplerinden ve arka plan renklerinden şablonları, veri şablonlarını ve stilleri denetleyebilen herhangi bir şeyi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-345">Controls in an application should share the same appearance, which can include anything from fonts and background colors to control templates, data templates, and styles.</span></span> <span data-ttu-id="3a4b4-346">Bu kaynakları yeniden kullanım için tek bir konumda kapsüllemek üzere, WPF 'nin Kullanıcı arabirimi kaynakları desteğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-346">You can use WPF's support for user interface resources to encapsulate these resources in a single location for reuse.</span></span>

<span data-ttu-id="3a4b4-347">Aşağıdaki örnek, ve tarafından paylaşılan ortak bir arka plan rengi tanımlar <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Label> :</span><span class="sxs-lookup"><span data-stu-id="3a4b4-347">The following example defines a common background color that is shared by a <xref:System.Windows.Controls.Button> and a <xref:System.Windows.Controls.Label>:</span></span>

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

<span data-ttu-id="3a4b4-348">Bu örnek, özellik öğesini kullanarak bir arka plan rengi kaynağı uygular `Window.Resources` .</span><span class="sxs-lookup"><span data-stu-id="3a4b4-348">This example implements a background color resource by using the `Window.Resources` property element.</span></span> <span data-ttu-id="3a4b4-349">Bu kaynak, öğesinin tüm alt öğeleri için kullanılabilir <xref:System.Windows.Window> .</span><span class="sxs-lookup"><span data-stu-id="3a4b4-349">This resource is available to all children of the <xref:System.Windows.Window>.</span></span> <span data-ttu-id="3a4b4-350">Aşağıdakiler de dahil olmak üzere çeşitli kaynak kapsamları çözümlendikleri sırayla listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="3a4b4-350">There are a variety of resource scopes, including the following, listed in the order in which they are resolved:</span></span>

1. <span data-ttu-id="3a4b4-351">Tek bir denetim (devralınan özelliği kullanarak <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> ).</span><span class="sxs-lookup"><span data-stu-id="3a4b4-351">An individual control (using the inherited <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> property).</span></span>

2. <span data-ttu-id="3a4b4-352">A <xref:System.Windows.Window> veya a <xref:System.Windows.Controls.Page> (devralınan özelliği de kullanılarak <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> ).</span><span class="sxs-lookup"><span data-stu-id="3a4b4-352">A <xref:System.Windows.Window> or a <xref:System.Windows.Controls.Page> (also using the inherited <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> property).</span></span>

3. <span data-ttu-id="3a4b4-353">Bir <xref:System.Windows.Application> (özelliğini kullanarak <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> ).</span><span class="sxs-lookup"><span data-stu-id="3a4b4-353">An <xref:System.Windows.Application> (using the <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> property).</span></span>

<span data-ttu-id="3a4b4-354">Çeşitli kapsamlar, kaynaklarınızı tanımladığınız ve paylaştığınız yönteme göre esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-354">The variety of scopes gives you flexibility with respect to the way in which you define and share your resources.</span></span>

<span data-ttu-id="3a4b4-355">Kaynaklarınızın belirli bir kapsamla doğrudan ilişkilendirilmesi için alternatif olarak, bir veya daha fazla kaynağı, <xref:System.Windows.ResourceDictionary> uygulamanın diğer bölümlerinde başvurulabilen ayrı bir kullanarak paketleyebilir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-355">As an alternative to directly associating your resources with a particular scope, you can package one or more resources by using a separate <xref:System.Windows.ResourceDictionary> that can be referenced in other parts of an application.</span></span> <span data-ttu-id="3a4b4-356">Örneğin, aşağıdaki örnek bir kaynak sözlüğünde varsayılan bir arka plan rengi tanımlar:</span><span class="sxs-lookup"><span data-stu-id="3a4b4-356">For example, the following example defines a default background color in a resource dictionary:</span></span>

```xaml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">

  <!-- Define background color resource -->
  <SolidColorBrush x:Key="defaultBackground" Color="Red" />

  <!-- Define other resources -->
</ResourceDictionary>
```

<span data-ttu-id="3a4b4-357">Aşağıdaki örnek, bir uygulama genelinde paylaşılmak üzere önceki örnekte tanımlanan kaynak sözlüğüne başvurur:</span><span class="sxs-lookup"><span data-stu-id="3a4b4-357">The following example references the resource dictionary defined in the previous example so that it is shared across an application:</span></span>

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

<span data-ttu-id="3a4b4-358">Kaynaklar ve kaynak sözlükleri, Temalar ve kaplamalar için WPF desteğinin temelini içerir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-358">Resources and resource dictionaries are the foundation of WPF support for themes and skins.</span></span>

<span data-ttu-id="3a4b4-359">Daha fazla bilgi için bkz. [kaynaklar](../../desktop-wpf/fundamentals/xaml-resources-define.md).</span><span class="sxs-lookup"><span data-stu-id="3a4b4-359">For more information, see [Resources](../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>

### <a name="custom-controls"></a><span data-ttu-id="3a4b4-360">Özel denetimler</span><span class="sxs-lookup"><span data-stu-id="3a4b4-360">Custom controls</span></span>

<span data-ttu-id="3a4b4-361">WPF, özelleştirme desteği sunan bir konak sağlasa da, mevcut WPF denetimlerinin uygulamanızın veya kullanıcılarınızın ihtiyaçlarını karşılamadığında karşılaşabileceğiniz durumlarla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-361">Although WPF provides a host of customization support, you may encounter situations where existing WPF controls do not meet the needs of either your application or its users.</span></span> <span data-ttu-id="3a4b4-362">Bu durum şu durumlarda oluşabilir:</span><span class="sxs-lookup"><span data-stu-id="3a4b4-362">This can occur when:</span></span>

- <span data-ttu-id="3a4b4-363">İhtiyaç duyduğunuz Kullanıcı arabirimi, mevcut WPF uygulamalarının görünümü özelleştirilerek oluşturulamaz.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-363">The user interface that you require cannot be created by customizing the look and feel of existing WPF implementations.</span></span>

- <span data-ttu-id="3a4b4-364">Gerekli olan davranış, mevcut WPF uygulamaları tarafından desteklenmez (veya kolayca desteklenmez).</span><span class="sxs-lookup"><span data-stu-id="3a4b4-364">The behavior that you require is not supported (or not easily supported) by existing WPF implementations.</span></span>

<span data-ttu-id="3a4b4-365">Ancak, bu noktada, yeni bir denetim oluşturmak için üç WPF modelinden birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-365">At this point, however, you can take advantage of one of three WPF models to create a new control.</span></span> <span data-ttu-id="3a4b4-366">Her model belirli bir senaryoyu hedefler ve özel denetiminizin belirli bir WPF Taban sınıfından türemesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-366">Each model targets a specific scenario and requires your custom control to derive from a particular WPF base class.</span></span> <span data-ttu-id="3a4b4-367">Üç model burada listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="3a4b4-367">The three models are listed here:</span></span>

- <span data-ttu-id="3a4b4-368">**Kullanıcı denetimi modeli**.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-368">**User Control Model**.</span></span> <span data-ttu-id="3a4b4-369">Özel denetim, öğesinden türetilir <xref:System.Windows.Controls.UserControl> ve bir veya daha fazla denetimden oluşur.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-369">A custom control derives from <xref:System.Windows.Controls.UserControl> and is composed of one or more other controls.</span></span>

- <span data-ttu-id="3a4b4-370">**Denetim modeli**.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-370">**Control Model**.</span></span> <span data-ttu-id="3a4b4-371">Özel bir denetim, ' dan türetilir <xref:System.Windows.Controls.Control> ve, WPF denetimlerinin çoğunluğunda olduğu gibi, davranışlarını, şablonlarının görünümlerini kullanarak ayıran uygulamalar oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-371">A custom control derives from <xref:System.Windows.Controls.Control> and is used to build implementations that separate their behavior from their appearance using templates, much like the majority of WPF controls.</span></span> <span data-ttu-id="3a4b4-372">Öğesinden türetme <xref:System.Windows.Controls.Control> , Kullanıcı denetimlerinden özel bir kullanıcı arabirimi oluşturmak için daha fazla özgürlük sağlar, ancak daha fazla çaba gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-372">Deriving from <xref:System.Windows.Controls.Control> allows you more freedom for creating a custom user interface than user controls, but it may require more effort.</span></span>

- <span data-ttu-id="3a4b4-373">**Framework öğe modeli**.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-373">**Framework Element Model**.</span></span> <span data-ttu-id="3a4b4-374">Özel denetim, <xref:System.Windows.FrameworkElement> görünümü özel işleme mantığı (şablon değil) tarafından tanımlandığında öğesinden türetilir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-374">A custom control derives from <xref:System.Windows.FrameworkElement> when its appearance is defined by custom rendering logic (not templates).</span></span>

<span data-ttu-id="3a4b4-375">Aşağıdaki örnek, öğesinden türetilen özel bir sayısal yukarı/aşağı denetimi göstermektedir <xref:System.Windows.Controls.UserControl> :</span><span class="sxs-lookup"><span data-stu-id="3a4b4-375">The following example shows a custom numeric up/down control that derives from <xref:System.Windows.Controls.UserControl>:</span></span>

[!code-xaml[IntroToWPFSnippets#UserControlMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_33.xaml)]

[!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND1](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_34.cs)]
[!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND1](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_34.vb)]

<span data-ttu-id="3a4b4-376">Aşağıdaki örnek, Kullanıcı denetimini öğesine eklemek için gereken XAML 'yi göstermektedir <xref:System.Windows.Window> :</span><span class="sxs-lookup"><span data-stu-id="3a4b4-376">The following example illustrates the XAML that is required to incorporate the user control into a <xref:System.Windows.Window>:</span></span>

[!code-xaml[IntroToWPFSnippets#UserControlWindowMARKUP1](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_37.xaml)]

<span data-ttu-id="3a4b4-377">Aşağıdaki şekilde, `NumericUpDown` içinde barındırılan denetim gösterilmektedir <xref:System.Windows.Window> :</span><span class="sxs-lookup"><span data-stu-id="3a4b4-377">The following figure shows the `NumericUpDown` control hosted in a <xref:System.Windows.Window>:</span></span>

![Özel bir UserControl](media/introduction-to-wpf/wpfintrofigure3.png)

<span data-ttu-id="3a4b4-379">Özel denetimler hakkında daha fazla bilgi için bkz. [Denetim yazma genel bakış](controls/control-authoring-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3a4b4-379">For more information on custom controls, see [Control authoring overview](controls/control-authoring-overview.md).</span></span>

## <a name="wpf-best-practices"></a><span data-ttu-id="3a4b4-380">WPF en iyi uygulamaları</span><span class="sxs-lookup"><span data-stu-id="3a4b4-380">WPF best practices</span></span>

<span data-ttu-id="3a4b4-381">Her türlü geliştirme platformunda olduğu gibi, WPF istenen sonuca ulaşmak için çeşitli yollarla kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-381">As with any development platform, WPF can be used in a variety of ways to achieve the desired result.</span></span> <span data-ttu-id="3a4b4-382">WPF uygulamalarınızın gerekli Kullanıcı deneyimini sağlayıp, genel olarak hedef kitle taleplerini karşıladığından emin olmanın bir yolu olarak erişilebilirlik, Genelleştirme ve yerelleştirme ve performans için önerilen en iyi uygulamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-382">As a way of ensuring that your WPF applications provide the required user experience and meet the demands of the audience in general, there are recommended best practices for accessibility, globalization and localization, and performance.</span></span> <span data-ttu-id="3a4b4-383">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-383">For more information, see:</span></span>

- [<span data-ttu-id="3a4b4-384">Erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="3a4b4-384">Accessibility</span></span>](../ui-automation/accessibility-best-practices.md)
- [<span data-ttu-id="3a4b4-385">WPF Genelleştirme ve yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="3a4b4-385">WPF globalization and localization</span></span>](advanced/wpf-globalization-and-localization-overview.md)
- [<span data-ttu-id="3a4b4-386">WPF uygulama performansı</span><span class="sxs-lookup"><span data-stu-id="3a4b4-386">WPF app performance</span></span>](advanced/optimizing-wpf-application-performance.md)
- [<span data-ttu-id="3a4b4-387">WPF güvenliği</span><span class="sxs-lookup"><span data-stu-id="3a4b4-387">WPF security</span></span>](security-wpf.md)

## <a name="next-steps"></a><span data-ttu-id="3a4b4-388">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="3a4b4-388">Next steps</span></span>

<span data-ttu-id="3a4b4-389">WPF 'nin temel özelliklerine baktık.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-389">We've looked at the key features of WPF.</span></span> <span data-ttu-id="3a4b4-390">Şimdi ilk WPF uygulamanızı oluşturma zamanı.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-390">Now it's time to build your first WPF app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3a4b4-391">İzlenecek yol: ilk WPF Masaüstü Uygulamam</span><span class="sxs-lookup"><span data-stu-id="3a4b4-391">Walkthrough: My first WPF desktop app</span></span>](getting-started/walkthrough-my-first-wpf-desktop-application.md)

## <a name="see-also"></a><span data-ttu-id="3a4b4-392">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a4b4-392">See also</span></span>

- [<span data-ttu-id="3a4b4-393">WPF kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="3a4b4-393">Get started with WPF</span></span>](getting-started/index.md)
- [<span data-ttu-id="3a4b4-394">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="3a4b4-394">Windows Presentation Foundation</span></span>](index.md)
- [<span data-ttu-id="3a4b4-395">WPF topluluk kaynakları</span><span class="sxs-lookup"><span data-stu-id="3a4b4-395">WPF community resources</span></span>](getting-started/community-feedback.md)
