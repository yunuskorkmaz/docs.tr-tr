---
title: L2DBForm.xaml kaynak kodu
ms.date: 10/22/2019
ms.topic: sample
ms.openlocfilehash: 290b00e136f0c49e1b27d4fa1bca7321eebe936e
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920946"
---
# <a name="l2dbformxaml-source-code"></a><span data-ttu-id="169e7-102">L2DBForm.xaml kaynak kodu</span><span class="sxs-lookup"><span data-stu-id="169e7-102">L2DBForm.xaml source code</span></span>

<span data-ttu-id="169e7-103">Bu sayfa, [LINQ to XML örneği kullanılarak WPF veri bağlaması](linq-to-xml-data-binding-sample.md)için xaml kaynak dosyasını içerir ve tanımlar.</span><span class="sxs-lookup"><span data-stu-id="169e7-103">This page contains and describes the XAML source file for the [WPF data binding using LINQ to XML example](linq-to-xml-data-binding-sample.md).</span></span>

## <a name="overall-ui-structure"></a><span data-ttu-id="169e7-104">Genel Kullanıcı arabirimi yapısı</span><span class="sxs-lookup"><span data-stu-id="169e7-104">Overall UI structure</span></span>

<span data-ttu-id="169e7-105">Bir WPF projesi için tipik olduğu gibi, bu dosya, `LinqToXmlDataBinding` ad alanında `L2XDBFrom` türetilmiş sınıfla ilişkili bir <xref:System.Windows.Window> XML öğesi olan bir üst öğe içerir.</span><span class="sxs-lookup"><span data-stu-id="169e7-105">As is typical for a WPF project, this file contains one parent element, a <xref:System.Windows.Window> XML element that's associated with the derived class `L2XDBFrom` in the `LinqToXmlDataBinding` namespace.</span></span>

<span data-ttu-id="169e7-106">İstemci alanı, açık mavi arka plan verilen bir <xref:System.Windows.Controls.StackPanel> içinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="169e7-106">The client area is contained within a <xref:System.Windows.Controls.StackPanel> that's given a light blue background.</span></span> <span data-ttu-id="169e7-107">Bu panel, <xref:System.Windows.Controls.Separator> çubuklarıyla ayrılan dört <xref:System.Windows.Controls.DockPanel> UI bölümü içerir.</span><span class="sxs-lookup"><span data-stu-id="169e7-107">This panel contains four <xref:System.Windows.Controls.DockPanel> UI sections separated by <xref:System.Windows.Controls.Separator> bars.</span></span> <span data-ttu-id="169e7-108">Bu bölümlerin amacı [burada](linq-to-xml-data-binding-sample.md#overview)açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="169e7-108">The purpose of these sections is described [here](linq-to-xml-data-binding-sample.md#overview).</span></span>

<span data-ttu-id="169e7-109">Her bölüm, onu tanımlayan bir etiket içerir.</span><span class="sxs-lookup"><span data-stu-id="169e7-109">Each section contains a label that identifies it.</span></span> <span data-ttu-id="169e7-110">İlk iki bölümde, bu etiket bir <xref:System.Windows.FrameworkElement.LayoutTransform%2A>kullanılarak 90 derece döndürülür.</span><span class="sxs-lookup"><span data-stu-id="169e7-110">In the first two sections, this label is rotated 90 degrees through the use of a <xref:System.Windows.FrameworkElement.LayoutTransform%2A>.</span></span> <span data-ttu-id="169e7-111">Bölümünün geri kalanı, bu bölümün amacına uygun Kullanıcı arabirimi öğelerini içerir, örneğin metin blokları, metin kutuları ve düğmeler.</span><span class="sxs-lookup"><span data-stu-id="169e7-111">The rest of the section contains UI elements appropriate to the purpose of that section, for example, text blocks, text boxes, and buttons.</span></span> <span data-ttu-id="169e7-112">Bazen bu alt denetimleri hizalamak için bir alt <xref:System.Windows.Controls.StackPanel> kullanılır.</span><span class="sxs-lookup"><span data-stu-id="169e7-112">Sometimes a child <xref:System.Windows.Controls.StackPanel> is used to align these child controls.</span></span>

## <a name="window-resource-section"></a><span data-ttu-id="169e7-113">Pencere kaynağı bölümü</span><span class="sxs-lookup"><span data-stu-id="169e7-113">Window resource section</span></span>

<span data-ttu-id="169e7-114">9\. satırdaki açma `<Window.Resources>` etiketi, pencere kaynağı bölümünün başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="169e7-114">The opening `<Window.Resources>` tag on line 9 indicates the start of the window resource section.</span></span> <span data-ttu-id="169e7-115">35 satırındaki kapanış etiketiyle biter.</span><span class="sxs-lookup"><span data-stu-id="169e7-115">It ends with the closing tag on line 35.</span></span>

<span data-ttu-id="169e7-116">11 ile 25 arası çizgileri kapsayan `<ObjectDataProvider>` etiketi, kaynak olarak <xref:System.Xml.Linq.XElement> kullanan `LoadedBooks` adlı bir <xref:System.Windows.Data.ObjectDataProvider> bildirir.</span><span class="sxs-lookup"><span data-stu-id="169e7-116">The `<ObjectDataProvider>` tag, which spans lines 11 through 25, declares a <xref:System.Windows.Data.ObjectDataProvider>, named `LoadedBooks`, that uses an <xref:System.Xml.Linq.XElement> as the source.</span></span> <span data-ttu-id="169e7-117"><xref:System.Xml.Linq.XElement>, gömülü bir XML belgesi (bir `CDATA` öğesi) ayrıştırıldığında başlatılır.</span><span class="sxs-lookup"><span data-stu-id="169e7-117">The <xref:System.Xml.Linq.XElement> is initialized by parsing an embedded XML document (a `CDATA` element).</span></span> <span data-ttu-id="169e7-118">Gömülü XML belgesi bildirirken ve ayrıştırıldığında da boşluk korunduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="169e7-118">Notice that white space is preserved when declaring the embedded XML document and also when it's parsed.</span></span> <span data-ttu-id="169e7-119">Ham XML 'yi göstermek için kullanılan <xref:System.Windows.Controls.TextBlock> denetimi özel XML biçimlendirme özelliklerine sahip olmadığı için boşluk korunur.</span><span class="sxs-lookup"><span data-stu-id="169e7-119">White space is preserved because the <xref:System.Windows.Controls.TextBlock> control, which is used to display the raw XML, has no special XML formatting capabilities.</span></span>

<span data-ttu-id="169e7-120">Son olarak, `BookTemplate` adlı bir <xref:System.Windows.DataTemplate> 28 ile 34 arası satırlarda tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="169e7-120">Lastly, a <xref:System.Windows.DataTemplate> named `BookTemplate` is defined on lines 28 through 34.</span></span> <span data-ttu-id="169e7-121">Bu şablon, girdileri **kitap listesi** UI bölümünde göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="169e7-121">This template is used to display the entries in the **Book List** UI section.</span></span> <span data-ttu-id="169e7-122">Aşağıdaki atamalar aracılığıyla kitap KIMLIĞI ve defter adını almak için veri bağlamayı ve dinamik özellikleri LINQ to XML kullanır:</span><span class="sxs-lookup"><span data-stu-id="169e7-122">It uses data binding and LINQ to XML dynamic properties to retrieve the book ID and book name through the following assignments:</span></span>

```xaml
Text="{Binding Path=Attribute[id].Value}"Text="{Binding Path=Value}"
```

## <a name="data-binding-code"></a><span data-ttu-id="169e7-123">Veri bağlama kodu</span><span class="sxs-lookup"><span data-stu-id="169e7-123">Data binding code</span></span>

<span data-ttu-id="169e7-124"><xref:System.Windows.DataTemplate> öğesine ek olarak, veri bağlama bu dosyadaki birçok farklı yerde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="169e7-124">In addition to the <xref:System.Windows.DataTemplate> element, data binding is used in a number of other places in this file.</span></span>

<span data-ttu-id="169e7-125">38 satırındaki açma `<StackPanel>` etiketinde, bu panelin <xref:System.Windows.FrameworkElement.DataContext%2A> özelliği `LoadedBooks` veri sağlayıcısına ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="169e7-125">In the opening `<StackPanel>` tag on line 38, the <xref:System.Windows.FrameworkElement.DataContext%2A> property of this panel is set to the `LoadedBooks` data provider.</span></span>

```xaml
DataContext="{Binding Source={StaticResource LoadedBooks}}
```

<span data-ttu-id="169e7-126">Veri bağlamının ayarlanması, bu veri sağlayıcısının `Xml` özelliğine bağlayarak ham XML 'yi göstermek için `tbRawXml` adlı <xref:System.Windows.Controls.TextBlock> için mümkün hale getirir (46. satırda).</span><span class="sxs-lookup"><span data-stu-id="169e7-126">Setting the data context makes it possible (on line 46) for the <xref:System.Windows.Controls.TextBlock> named `tbRawXml` to display the raw XML by binding to this data provider's `Xml` property:</span></span>

```xaml
Text="{Binding Path=Xml}"
```

<span data-ttu-id="169e7-127">**Kitap listesi** Kullanıcı arabirimi bölümündeki <xref:System.Windows.Controls.ListBox>, 58 ile 62 arası satırlarda, görüntüleme öğelerinin şablonunu pencere kaynağı bölümünde tanımlanan `BookTemplate` olarak ayarlar:</span><span class="sxs-lookup"><span data-stu-id="169e7-127">The <xref:System.Windows.Controls.ListBox> in the **Book List** UI section, on lines 58 through 62, sets the template for its display items to the `BookTemplate` defined in the window resource section:</span></span>

```xaml
ItemTemplate ="{StaticResource BookTemplate}"
```

<span data-ttu-id="169e7-128">Ardından, 59 ile 62 arasındaki satırlarda, kitapların gerçek değerleri bu liste kutusuna bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="169e7-128">Then, on lines 59 through 62, the actual values of the books are bound to this list box:</span></span>

```xaml
<ListBox.ItemsSource>
    <Binding Path="Elements[{http://www.mybooks.com}book]"/>
</ListBox.ItemsSource>
```

<span data-ttu-id="169e7-129">Üçüncü Kullanıcı arabirimi bölümü, **Seçili kitabı Düzenle**, önce üst <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.FrameworkElement.DataContext%2A>, **kitap listesi** Kullanıcı arabirimi bölümünden içindeki seçili olan öğeye bağlar (satır 82):</span><span class="sxs-lookup"><span data-stu-id="169e7-129">The third UI section, **Edit Selected Book**, first binds the <xref:System.Windows.FrameworkElement.DataContext%2A> of the parent <xref:System.Windows.Controls.StackPanel> to the currently selected item in from the **Book List** UI section (line 82):</span></span>

```xaml
DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}"
```

<span data-ttu-id="169e7-130">Daha sonra iki yönlü veri bağlamayı kullanır, böylece kitap öğelerinin geçerli değerleri bu paneldeki iki metin kutusunu olarak görüntülenir ve ' den güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="169e7-130">It then uses two-way data binding, so that the current values of the book elements are displayed to, and updated from, the two text boxes in this panel.</span></span> <span data-ttu-id="169e7-131">Dinamik özelliklere veri bağlama, `BookTemplate` veri şablonunda kullanılan veri bağlamasına benzerdir:</span><span class="sxs-lookup"><span data-stu-id="169e7-131">Data binding to dynamic properties is similar to the data binding used in the `BookTemplate` data template:</span></span>

```xaml
Text="{Binding Path=Attribute[id].Value}"...Text="{Binding Path=Value}"
```

<span data-ttu-id="169e7-132">Son Kullanıcı arabirimi bölümü, **Yeni kitap ekle**, XAML kodunda veri bağlamayı kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="169e7-132">The last UI section, **Add New Book**, doesn't use data binding in its XAML code.</span></span> <span data-ttu-id="169e7-133">Bunun yerine, veri bağlama *L2DBForm.xaml.cs*dosyasında olay işleme kodudur.</span><span class="sxs-lookup"><span data-stu-id="169e7-133">Instead, data binding is in its event handling code in the file *L2DBForm.xaml.cs*.</span></span>

## <a name="example"></a><span data-ttu-id="169e7-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="169e7-134">Example</span></span>

### <a name="description"></a><span data-ttu-id="169e7-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="169e7-135">Description</span></span>

> [!NOTE]
> <span data-ttu-id="169e7-136">Satır numaralarının izlenmesi daha kolay olması için aşağıdaki kodu, Visual Studio 'daki C# kaynak kodu Düzenleyicisi gibi bir kod düzenleyicisine kopyalamanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="169e7-136">We recommend that you copy the following code below into a code editor, such as the C# source code editor in Visual Studio, so that line numbers will be easier to track.</span></span>

### <a name="code"></a><span data-ttu-id="169e7-137">Kod</span><span class="sxs-lookup"><span data-stu-id="169e7-137">Code</span></span>

```xml
<Window x:Class="LinqToXmlDataBinding.L2XDBForm"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:system="clr-namespace:System;assembly=mscorlib"
    xmlns:xlinq="clr-namespace:System.Xml.Linq;assembly=System.Xml.Linq"
    xmlns:local="clr-namespace:LinqToXmlDataBinding"
    Title="WPF Data Binding using LINQ-to-XML" Height="665" Width="500" ResizeMode="NoResize">

    <Window.Resources>
        <!-- Books provider and inline data -->
        <ObjectDataProvider x:Key="LoadedBooks" ObjectType="{x:Type xlinq:XElement}" MethodName="Parse">
            <ObjectDataProvider.MethodParameters>
                <system:String xml:space="preserve">
<![CDATA[
<books xmlns="http://www.mybooks.com">
  <book id="0">book zero</book>
  <book id="1">book one</book>
  <book id="2">book two</book>
  <book id="3">book three</book>
</books>
]]>
                </system:String>
                <xlinq:LoadOptions>PreserveWhitespace</xlinq:LoadOptions>
            </ObjectDataProvider.MethodParameters>
        </ObjectDataProvider>

        <!-- Template for use in Books List listbox. -->
        <DataTemplate x:Key="BookTemplate">
            <StackPanel Orientation="Horizontal">
                <TextBlock Margin="3" Text="{Binding Path=Attribute[id].Value}"/>
                <TextBlock Margin="3" Text="-"/>
                <TextBlock Margin="3" Text="{Binding Path=Value}"/>
            </StackPanel>
        </DataTemplate>
    </Window.Resources>

    <!-- Main visual content container -->
    <StackPanel Background="lightblue" DataContext="{Binding Source={StaticResource LoadedBooks}}">
        <!-- Raw XML display section -->
        <DockPanel Margin="5">
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">XML
            <Label.LayoutTransform>
                <RotateTransform Angle="90"/>
            </Label.LayoutTransform>
            </Label>
            <TextBlock Name="tbRawXml" Height="200" Background="LightGray" Text="{Binding Path=Xml}" TextTrimming="CharacterEllipsis" />
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- List box to display all books section -->
        <DockPanel Margin="5">
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">Book List
                <Label.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </Label.LayoutTransform>
            </Label>
            <ListBox Name="lbBooks" Height="200" Width="415" ItemTemplate ="{StaticResource BookTemplate}">
                <ListBox.ItemsSource>
                    <Binding Path="Elements[{http://www.mybooks.com}book]"/>
                </ListBox.ItemsSource>
            </ListBox>
            <Button Margin="5" DockPanel.Dock="Right" Height="30" Width ="130" Content="Remove Selected Book" Click="OnRemoveBook">
            <Button.LayoutTransform>
                <RotateTransform Angle="90"/>
            </Button.LayoutTransform>
            </Button>
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- Edit current selection section -->
        <DockPanel Margin="5">
            <TextBlock Margin="5" Height="30" Width="65" DockPanel.Dock="Right" Background="LightGray" TextWrapping="Wrap" TextAlignment="Center">
                    Changes are live!
                <TextBlock.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </TextBlock.LayoutTransform>
            </TextBlock>
            <StackPanel>
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Edit Selected Book</Label>
                <StackPanel Margin="1" DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}">
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">ID:</Label>
                        <TextBox Name="editAttributeTextBox" Width="410" Text="{Binding Path=Attribute[id].Value}">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Edit the selected book ID and see it changed.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">Value:</Label>
                        <TextBox Name="editValueTextBox" Width="410" Text="{Binding Path=Value}" Height="25">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Edit the selected book Value and see it changed.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                </StackPanel>
            </StackPanel>
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- Add new book section -->
        <DockPanel Margin="5">
            <Button Margin="5" Height="30" DockPanel.Dock="Right" Click ="OnAddBook">Add Book
                <Button.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </Button.LayoutTransform>
            </Button>
            <StackPanel>
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Add New Book</Label>
                <StackPanel Margin="1">
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">ID:</Label>
                        <TextBox Name="tbAddID" Width="410">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">Value:</Label>
                        <TextBox Name="tbAddValue" Width="410" Height="25">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="UltraBold" TextAlignment="Center">
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                </StackPanel>
            </StackPanel>
        </DockPanel>
    </StackPanel>
</Window>
```

### <a name="comments"></a><span data-ttu-id="169e7-138">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="169e7-138">Comments</span></span>

<span data-ttu-id="169e7-139">WPF UI C# öğeleriyle ilişkili olay işleyicilerinin kaynak kodu için bkz. [L2DBForm.xaml.cs kaynak kodu](l2dbform-xaml-cs-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="169e7-139">For the C# source code for the event handlers associated with the WPF UI elements, see [L2DBForm.xaml.cs source code](l2dbform-xaml-cs-source-code.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="169e7-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="169e7-140">See also</span></span>

- [<span data-ttu-id="169e7-141">İzlenecek yol: LinqToXmlDataBinding örneği</span><span class="sxs-lookup"><span data-stu-id="169e7-141">Walkthrough: LinqToXmlDataBinding example</span></span>](linq-to-xml-data-binding-sample.md)
- [<span data-ttu-id="169e7-142">L2DBForm.xaml.cs kaynak kodu</span><span class="sxs-lookup"><span data-stu-id="169e7-142">L2DBForm.xaml.cs source code</span></span>](l2dbform-xaml-cs-source-code.md)
