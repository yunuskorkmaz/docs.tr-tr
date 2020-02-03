---
title: İçerik modeli
ms.date: 03/30/2017
helpviewer_keywords:
- UIElement class [WPF], displaying content
- content model [WPF], controls
- controls [WPF], displaying text
- content display [WPF], controls
- controls [WPF], formatting text
- displaying content [WPF]
- arbitrary content classes [WPF], content model
- ContentControl class [WPF], displaying content
ms.assetid: 214da5ef-547a-4cf8-9b07-4aa8a0e52cdd
ms.openlocfilehash: a84ab2e66b4e373591fc9365b1c17d0bb0c66713
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738274"
---
# <a name="wpf-content-model"></a><span data-ttu-id="1c26d-102">WPF İçerik Modeli</span><span class="sxs-lookup"><span data-stu-id="1c26d-102">WPF Content Model</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="1c26d-103">, birincil amacı farklı içerik türlerini görüntülemek olan çok sayıda denetim ve denetim benzeri tür sağlayan bir sunum platformudur.</span><span class="sxs-lookup"><span data-stu-id="1c26d-103">is a presentation platform that provides many controls and control-like types whose primary purpose is to display different types of content.</span></span> <span data-ttu-id="1c26d-104">Hangi denetimin kullanılacağını veya hangi denetimin türetileceğini öğrenmek için, belirli bir denetimin en iyi şekilde görüntüleyeceği nesne türlerini anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1c26d-104">To determine which control to use or which control to derive from, you should understand the kinds of objects a particular control can best display.</span></span>  
  
 <span data-ttu-id="1c26d-105">Bu konu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi ve denetim benzeri türler için içerik modeli özetler.</span><span class="sxs-lookup"><span data-stu-id="1c26d-105">This topic summarizes the content model for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] control and control-like types.</span></span> <span data-ttu-id="1c26d-106">İçerik modeli, bir denetimde hangi içeriğin kullanılabileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="1c26d-106">The content model describes what content can be used in a control.</span></span> <span data-ttu-id="1c26d-107">Bu konu, her bir içerik modeli için içerik özelliklerini de listeler.</span><span class="sxs-lookup"><span data-stu-id="1c26d-107">This topic also lists the content properties for each content model.</span></span> <span data-ttu-id="1c26d-108">İçerik özelliği, nesnenin içeriğini depolamak için kullanılan bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="1c26d-108">A content property is a property that is used to store the content of the object.</span></span>  

<a name="classes_that_contain_arbitrary_content"></a>   
## <a name="classes-that-contain-arbitrary-content"></a><span data-ttu-id="1c26d-109">Rastgele Içerik içeren sınıflar</span><span class="sxs-lookup"><span data-stu-id="1c26d-109">Classes That Contain Arbitrary Content</span></span>  
 <span data-ttu-id="1c26d-110">Bazı denetimler dize, <xref:System.DateTime> nesnesi veya ek öğeler için kapsayıcı olan bir <xref:System.Windows.UIElement> gibi herhangi bir türde bir nesne içerebilir.</span><span class="sxs-lookup"><span data-stu-id="1c26d-110">Some controls can contain an object of any type, such as a string, a <xref:System.DateTime> object, or a <xref:System.Windows.UIElement> that is a container for additional items.</span></span> <span data-ttu-id="1c26d-111">Örneğin, bir <xref:System.Windows.Controls.Button> görüntü ve bazı metinler içerebilir; veya bir <xref:System.Windows.Controls.CheckBox>, <xref:System.DateTime.Now%2A?displayProperty=nameWithType>değerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="1c26d-111">For example, a <xref:System.Windows.Controls.Button> can contain an image and some text; or a <xref:System.Windows.Controls.CheckBox> can contain the value of <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.</span></span>  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="1c26d-112">, rastgele içerik içerebilen dört sınıfa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1c26d-112">has four classes that can contain arbitrary content.</span></span> <span data-ttu-id="1c26d-113">Aşağıdaki tabloda, <xref:System.Windows.Controls.Control>devraldığı sınıflar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="1c26d-113">The following table lists the classes, which inherit from <xref:System.Windows.Controls.Control>.</span></span>  
  
|<span data-ttu-id="1c26d-114">Rastgele içerik içeren sınıf</span><span class="sxs-lookup"><span data-stu-id="1c26d-114">Class that contains arbitrary content</span></span>|<span data-ttu-id="1c26d-115">İçerik</span><span class="sxs-lookup"><span data-stu-id="1c26d-115">Content</span></span>|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="1c26d-116">Tek bir rastgele nesne.</span><span class="sxs-lookup"><span data-stu-id="1c26d-116">A single arbitrary object.</span></span>|  
|<xref:System.Windows.Controls.HeaderedContentControl>|<span data-ttu-id="1c26d-117">Her ikisi de rastgele nesneler olan üst bilgi ve tek öğe.</span><span class="sxs-lookup"><span data-stu-id="1c26d-117">A header and a single item, both of which are arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.ItemsControl>|<span data-ttu-id="1c26d-118">Rastgele nesnelerden oluşan bir koleksiyon.</span><span class="sxs-lookup"><span data-stu-id="1c26d-118">A collection of arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|<span data-ttu-id="1c26d-119">Hepsi rastgele nesneler olan bir üst bilgi ve öğe koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="1c26d-119">A header and a collection of items, all of which are arbitrary objects.</span></span>|  
  
 <span data-ttu-id="1c26d-120">Bu sınıflardan devralma denetimleri aynı içerik türünü içerebilir ve içeriği aynı şekilde ele alabilir.</span><span class="sxs-lookup"><span data-stu-id="1c26d-120">Controls that inherit from these classes can contain the same type of content and treat the content in the same way.</span></span> <span data-ttu-id="1c26d-121">Aşağıdaki çizimde, bir görüntü ve bazı metinler içeren her bir içerik modelinden bir denetim gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="1c26d-121">The following illustration shows one control from each content model that contains an image and some text:</span></span>  
  
 ![Her içerik modelinden biri olmak üzere dört farklı denetimi gösteren ekran görüntüsü.](./media/wpf-content-model/control-content-model-image-text.png)  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a><span data-ttu-id="1c26d-123">Tek bir rastgele nesne içeren denetimler</span><span class="sxs-lookup"><span data-stu-id="1c26d-123">Controls That Contain a Single Arbitrary Object</span></span>  
 <span data-ttu-id="1c26d-124"><xref:System.Windows.Controls.ContentControl> sınıfı, tek bir rastgele içerik parçası içerir.</span><span class="sxs-lookup"><span data-stu-id="1c26d-124">The <xref:System.Windows.Controls.ContentControl> class contains a single piece of arbitrary content.</span></span> <span data-ttu-id="1c26d-125">İçerik özelliği <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="1c26d-125">Its content property is <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="1c26d-126">Aşağıdaki denetimler <xref:System.Windows.Controls.ContentControl> devralınır ve içerik modelini kullanır:</span><span class="sxs-lookup"><span data-stu-id="1c26d-126">The following controls inherit from <xref:System.Windows.Controls.ContentControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.Button>  
  
- <xref:System.Windows.Controls.Primitives.ButtonBase>  
  
- <xref:System.Windows.Controls.CheckBox>  
  
- <xref:System.Windows.Controls.ComboBoxItem>  
  
- <xref:System.Windows.Controls.ContentControl>  
  
- <xref:System.Windows.Controls.Frame>  
  
- <xref:System.Windows.Controls.GridViewColumnHeader>  
  
- <xref:System.Windows.Controls.GroupItem>  
  
- <xref:System.Windows.Controls.Label>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Navigation.NavigationWindow>  
  
- <xref:System.Windows.Controls.RadioButton>  
  
- <xref:System.Windows.Controls.Primitives.RepeatButton>  
  
- <xref:System.Windows.Controls.ScrollViewer>  
  
- <xref:System.Windows.Controls.Primitives.StatusBarItem>  
  
- <xref:System.Windows.Controls.Primitives.ToggleButton>  
  
- <xref:System.Windows.Controls.ToolTip>  
  
- <xref:System.Windows.Controls.UserControl>  
  
- <xref:System.Windows.Window>  
  
 <span data-ttu-id="1c26d-127">Aşağıdaki çizimde <xref:System.Windows.Controls.ContentControl.Content%2A> dize, <xref:System.DateTime> nesnesi, <xref:System.Windows.Shapes.Rectangle>ve <xref:System.Windows.Shapes.Ellipse> ve <xref:System.Windows.Controls.TextBlock>içeren bir <xref:System.Windows.Controls.Panel> olarak ayarlanan dört düğme gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="1c26d-127">The following illustration shows four buttons whose <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a string, a <xref:System.DateTime> object, a <xref:System.Windows.Shapes.Rectangle>, and a <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>:</span></span>  
  
 ![Farklı içerik türleriyle dört düğme gösteren ekran görüntüsü.](./media/wpf-content-model/control-content-model-buttons.png)  
  
 <span data-ttu-id="1c26d-129"><xref:System.Windows.Controls.ContentControl.Content%2A> özelliğinin nasıl ayarlanacağı hakkında bir örnek için bkz. <xref:System.Windows.Controls.ContentControl>.</span><span class="sxs-lookup"><span data-stu-id="1c26d-129">For an example of how to set the <xref:System.Windows.Controls.ContentControl.Content%2A> property, see <xref:System.Windows.Controls.ContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a><span data-ttu-id="1c26d-130">Üst bilgi ve tek bir rastgele nesne içeren denetimler</span><span class="sxs-lookup"><span data-stu-id="1c26d-130">Controls That Contain a Header and a Single Arbitrary Object</span></span>  
 <span data-ttu-id="1c26d-131"><xref:System.Windows.Controls.HeaderedContentControl> sınıfı <xref:System.Windows.Controls.ContentControl> devralır ve üst bilgiyle içerik görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1c26d-131">The <xref:System.Windows.Controls.HeaderedContentControl> class inherits from <xref:System.Windows.Controls.ContentControl> and displays content with a header.</span></span> <span data-ttu-id="1c26d-132"><xref:System.Windows.Controls.ContentControl> ' dan <xref:System.Windows.Controls.ContentControl.Content%2A>içerik özelliğini devralır ve <xref:System.Object>türündeki <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> özelliğini tanımlar. Bu nedenle, her ikisi de rastgele bir nesne olabilir.</span><span class="sxs-lookup"><span data-stu-id="1c26d-132">It inherits the content property, <xref:System.Windows.Controls.ContentControl.Content%2A>, from <xref:System.Windows.Controls.ContentControl> and defines the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> property that is of type <xref:System.Object>; therefore, both can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="1c26d-133">Aşağıdaki denetimler <xref:System.Windows.Controls.HeaderedContentControl> devralınır ve içerik modelini kullanır:</span><span class="sxs-lookup"><span data-stu-id="1c26d-133">The following controls inherit from <xref:System.Windows.Controls.HeaderedContentControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.Expander>  
  
- <xref:System.Windows.Controls.GroupBox>  
  
- <xref:System.Windows.Controls.TabItem>  
  
 <span data-ttu-id="1c26d-134">Aşağıdaki çizimde iki <xref:System.Windows.Controls.TabItem> nesnesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1c26d-134">The following illustration shows two <xref:System.Windows.Controls.TabItem> objects.</span></span> <span data-ttu-id="1c26d-135">İlk <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> ve <xref:System.Windows.Controls.ContentControl.Content%2A>olarak <xref:System.Windows.UIElement> nesneleri içerir.</span><span class="sxs-lookup"><span data-stu-id="1c26d-135">The first <xref:System.Windows.Controls.TabItem> has <xref:System.Windows.UIElement> objects as the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="1c26d-136"><xref:System.Windows.Controls.HeaderedContentControl.Header%2A>, <xref:System.Windows.Shapes.Ellipse> ve <xref:System.Windows.Controls.TextBlock>içeren bir <xref:System.Windows.Controls.StackPanel> ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="1c26d-136">The <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="1c26d-137"><xref:System.Windows.Controls.ContentControl.Content%2A>, <xref:System.Windows.Controls.TextBlock> ve <xref:System.Windows.Controls.Label>içeren bir <xref:System.Windows.Controls.StackPanel> ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="1c26d-137">The <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains a <xref:System.Windows.Controls.TextBlock> and a <xref:System.Windows.Controls.Label>.</span></span> <span data-ttu-id="1c26d-138">İkinci <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> bir dizeye ve <xref:System.Windows.Controls.ContentControl.Content%2A><xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="1c26d-138">The second <xref:System.Windows.Controls.TabItem> has a string in the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and a <xref:System.Windows.Controls.TextBlock> in the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span>  
  
 ![Üst bilgi özelliğinde farklı türler kullanan TabControl.](./media/wpf-content-model/control-content-model-tab.png)  
  
 <span data-ttu-id="1c26d-140"><xref:System.Windows.Controls.TabItem> nesnelerinin nasıl oluşturulacağı hakkında bir örnek için bkz. <xref:System.Windows.Controls.HeaderedContentControl>.</span><span class="sxs-lookup"><span data-stu-id="1c26d-140">For an example of how to create <xref:System.Windows.Controls.TabItem> objects, see <xref:System.Windows.Controls.HeaderedContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a><span data-ttu-id="1c26d-141">Rastgele nesneler koleksiyonu Içeren denetimler</span><span class="sxs-lookup"><span data-stu-id="1c26d-141">Controls That Contain a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="1c26d-142"><xref:System.Windows.Controls.ItemsControl> sınıfı <xref:System.Windows.Controls.Control> devralır ve dizeler, nesneler veya diğer öğeler gibi birden çok öğe içerebilir.</span><span class="sxs-lookup"><span data-stu-id="1c26d-142">The <xref:System.Windows.Controls.ItemsControl> class inherits from <xref:System.Windows.Controls.Control> and can contain multiple items, such as strings, objects, or other elements.</span></span> <span data-ttu-id="1c26d-143">İçerik özellikleri <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> ve <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span><span class="sxs-lookup"><span data-stu-id="1c26d-143">Its content properties are <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> and <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span></span> <span data-ttu-id="1c26d-144"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, genellikle <xref:System.Windows.Controls.ItemsControl> bir veri koleksiyonuyla doldurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1c26d-144"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> is typically used to populate the <xref:System.Windows.Controls.ItemsControl> with a data collection.</span></span> <span data-ttu-id="1c26d-145"><xref:System.Windows.Controls.ItemsControl>doldurmak için bir koleksiyon kullanmak istemiyorsanız, <xref:System.Windows.Controls.ItemsControl.Items%2A> özelliğini kullanarak öğe ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c26d-145">If you do not want to use a collection to populate the <xref:System.Windows.Controls.ItemsControl>, you can add items by using the <xref:System.Windows.Controls.ItemsControl.Items%2A> property.</span></span>  
  
 <span data-ttu-id="1c26d-146">Aşağıdaki denetimler <xref:System.Windows.Controls.ItemsControl> devralınır ve içerik modelini kullanır:</span><span class="sxs-lookup"><span data-stu-id="1c26d-146">The following controls inherit from <xref:System.Windows.Controls.ItemsControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.Menu>  
  
- <xref:System.Windows.Controls.Primitives.MenuBase>  
  
- <xref:System.Windows.Controls.ContextMenu>  
  
- <xref:System.Windows.Controls.ComboBox>  
  
- <xref:System.Windows.Controls.ItemsControl>  
  
- <xref:System.Windows.Controls.ListBox>  
  
- <xref:System.Windows.Controls.ListView>  
  
- <xref:System.Windows.Controls.TabControl>  
  
- <xref:System.Windows.Controls.TreeView>  
  
- <xref:System.Windows.Controls.Primitives.Selector>  
  
- <xref:System.Windows.Controls.Primitives.StatusBar>  
  
 <span data-ttu-id="1c26d-147">Aşağıdaki çizimde, bu tür öğeleri içeren bir <xref:System.Windows.Controls.ListBox> gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="1c26d-147">The following illustration shows a <xref:System.Windows.Controls.ListBox> that contains these types of items:</span></span>  
  
- <span data-ttu-id="1c26d-148">Bir dize.</span><span class="sxs-lookup"><span data-stu-id="1c26d-148">A string.</span></span>  
  
- <span data-ttu-id="1c26d-149">Bir <xref:System.DateTime> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="1c26d-149">A <xref:System.DateTime> object.</span></span>  
  
- <span data-ttu-id="1c26d-150">Bir <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="1c26d-150">A <xref:System.Windows.UIElement>.</span></span>  
  
- <span data-ttu-id="1c26d-151">Bir <xref:System.Windows.Shapes.Ellipse> ve <xref:System.Windows.Controls.TextBlock>içeren bir <xref:System.Windows.Controls.Panel>.</span><span class="sxs-lookup"><span data-stu-id="1c26d-151">A <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 ![Dört tür içerik içeren bir ListBox gösteren ekran görüntüsü.](./media/wpf-content-model/control-content-model-listbox.png)  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a><span data-ttu-id="1c26d-153">Bir üst bilgi ve rastgele nesneler koleksiyonu içeren denetimler</span><span class="sxs-lookup"><span data-stu-id="1c26d-153">Controls That Contain a Header and a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="1c26d-154"><xref:System.Windows.Controls.HeaderedItemsControl> sınıfı <xref:System.Windows.Controls.ItemsControl> devralır ve dizeler, nesneler veya diğer öğeler ve bir üst bilgi gibi birden çok öğe içerebilir.</span><span class="sxs-lookup"><span data-stu-id="1c26d-154">The <xref:System.Windows.Controls.HeaderedItemsControl> class inherits from <xref:System.Windows.Controls.ItemsControl> and can contain multiple items, such as strings, objects, or other elements, and a header.</span></span> <span data-ttu-id="1c26d-155"><xref:System.Windows.Controls.ItemsControl> içerik özelliklerini, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>ve <xref:System.Windows.Controls.ItemsControl.Items%2A>devralır ve rastgele bir nesne olabilecek <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> özelliğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1c26d-155">It inherits the <xref:System.Windows.Controls.ItemsControl> content properties, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, and <xref:System.Windows.Controls.ItemsControl.Items%2A>, and it defines the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property that can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="1c26d-156">Aşağıdaki denetimler <xref:System.Windows.Controls.HeaderedItemsControl> devralınır ve içerik modelini kullanır:</span><span class="sxs-lookup"><span data-stu-id="1c26d-156">The following controls inherit from <xref:System.Windows.Controls.HeaderedItemsControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.MenuItem>  
  
- <xref:System.Windows.Controls.ToolBar>  
  
- <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>   
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a><span data-ttu-id="1c26d-157">UIElement nesnelerinin bir koleksiyonunu Içeren Sınıflar</span><span class="sxs-lookup"><span data-stu-id="1c26d-157">Classes That Contain a Collection of UIElement Objects</span></span>  
 <span data-ttu-id="1c26d-158"><xref:System.Windows.Controls.Panel> sınıfı, alt <xref:System.Windows.UIElement> nesnelerini konumlandırır ve düzenler.</span><span class="sxs-lookup"><span data-stu-id="1c26d-158">The <xref:System.Windows.Controls.Panel> class positions and arranges child <xref:System.Windows.UIElement> objects.</span></span> <span data-ttu-id="1c26d-159">İçerik özelliği <xref:System.Windows.Controls.Panel.Children%2A>.</span><span class="sxs-lookup"><span data-stu-id="1c26d-159">Its content property is <xref:System.Windows.Controls.Panel.Children%2A>.</span></span>  
  
 <span data-ttu-id="1c26d-160">Aşağıdaki sınıflar <xref:System.Windows.Controls.Panel> sınıfından devralınır ve onun içerik modelini kullanır:</span><span class="sxs-lookup"><span data-stu-id="1c26d-160">The following classes inherit from the <xref:System.Windows.Controls.Panel> class and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.Canvas>  
  
- <xref:System.Windows.Controls.DockPanel>  
  
- <xref:System.Windows.Controls.Grid>  
  
- <xref:System.Windows.Controls.Primitives.TabPanel>  
  
- <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
  
- <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
  
- <xref:System.Windows.Controls.Primitives.UniformGrid>  
  
- <xref:System.Windows.Controls.StackPanel>  
  
- <xref:System.Windows.Controls.VirtualizingPanel>  
  
- <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
- <xref:System.Windows.Controls.WrapPanel>  
  
 <span data-ttu-id="1c26d-161">Daha fazla bilgi için bkz. [panellere genel bakış](panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1c26d-161">For more information, see [Panels Overview](panels-overview.md).</span></span>  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>   
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a><span data-ttu-id="1c26d-162">UIElement görünümünü etkileyen sınıflar</span><span class="sxs-lookup"><span data-stu-id="1c26d-162">Classes That Affect the Appearance of a UIElement</span></span>  
 <span data-ttu-id="1c26d-163"><xref:System.Windows.Controls.Decorator> sınıfı, tek bir alt <xref:System.Windows.UIElement>üzerinde veya çevresinde görsel etkiler uygular.</span><span class="sxs-lookup"><span data-stu-id="1c26d-163">The <xref:System.Windows.Controls.Decorator> class applies visual effects onto or around a single child <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="1c26d-164">İçerik özelliği <xref:System.Windows.Controls.Decorator.Child%2A>.</span><span class="sxs-lookup"><span data-stu-id="1c26d-164">Its content property is <xref:System.Windows.Controls.Decorator.Child%2A>.</span></span> <span data-ttu-id="1c26d-165">Aşağıdaki sınıflar <xref:System.Windows.Controls.Decorator> devralınır ve içerik modelini kullanır:</span><span class="sxs-lookup"><span data-stu-id="1c26d-165">The following classes inherit from <xref:System.Windows.Controls.Decorator> and use its content model:</span></span>  
  
- <xref:System.Windows.Documents.AdornerDecorator>  
  
- <xref:System.Windows.Controls.Border>  
  
- <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
- <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
- <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
- <xref:System.Windows.Controls.InkPresenter>  
  
- <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
- <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
- <xref:System.Windows.Controls.Viewbox>  
  
 <span data-ttu-id="1c26d-166">Aşağıdaki çizimde, etrafında bir <xref:System.Windows.Controls.Border> olan (ile donatılmış) bir <xref:System.Windows.Controls.TextBox> gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1c26d-166">The following illustration shows a <xref:System.Windows.Controls.TextBox> that has (is decorated with) a <xref:System.Windows.Controls.Border> around it.</span></span>  
  
 <span data-ttu-id="1c26d-167">![Siyah kenarlıklı metin kutusu](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span><span class="sxs-lookup"><span data-stu-id="1c26d-167">![TextBox with black border](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span></span>  
<span data-ttu-id="1c26d-168">Kenarlığı olan TextBlock</span><span class="sxs-lookup"><span data-stu-id="1c26d-168">TextBlock that has a Border</span></span>  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>   
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a><span data-ttu-id="1c26d-169">UIElement hakkında görsel geri bildirim sağlayan sınıflar</span><span class="sxs-lookup"><span data-stu-id="1c26d-169">Classes That Provide Visual Feedback About a UIElement</span></span>  
 <span data-ttu-id="1c26d-170"><xref:System.Windows.Documents.Adorner> sınıfı bir kullanıcıya görsel ipucu sağlar.</span><span class="sxs-lookup"><span data-stu-id="1c26d-170">The <xref:System.Windows.Documents.Adorner> class provides visual cues to a user.</span></span> <span data-ttu-id="1c26d-171">Örneğin, öğelere işlevsel işleyiciler eklemek veya bir denetimle ilgili durum bilgilerini sağlamak için bir <xref:System.Windows.Documents.Adorner> kullanın.</span><span class="sxs-lookup"><span data-stu-id="1c26d-171">For example, use an <xref:System.Windows.Documents.Adorner> to add functional handles to elements or provide state information about a control.</span></span> <span data-ttu-id="1c26d-172"><xref:System.Windows.Documents.Adorner> sınıfı, kendi donatıcıları oluşturabilmeniz için bir çerçeve sağlar.</span><span class="sxs-lookup"><span data-stu-id="1c26d-172">The <xref:System.Windows.Documents.Adorner> class provides a framework so that you can create your own adorners.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="1c26d-173">, uygulanan hiçbir donatıcıları sağlamıyor.</span><span class="sxs-lookup"><span data-stu-id="1c26d-173">does not provide any implemented adorners.</span></span> <span data-ttu-id="1c26d-174">Daha fazla bilgi için bkz. [donatıcıları genel bakış](adorners-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1c26d-174">For more information, see [Adorners Overview](adorners-overview.md).</span></span>  
  
<a name="classes_that_enable_users_to_enter_text"></a>   
## <a name="classes-that-enable-users-to-enter-text"></a><span data-ttu-id="1c26d-175">Kullanıcıların metin girmesini sağlayan sınıflar</span><span class="sxs-lookup"><span data-stu-id="1c26d-175">Classes That Enable Users to Enter Text</span></span>  
 <span data-ttu-id="1c26d-176">WPF, kullanıcıların metin girmesini sağlayan üç birincil denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="1c26d-176">WPF provides three primary controls that enable users to enter text.</span></span> <span data-ttu-id="1c26d-177">Her denetim, metni farklı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1c26d-177">Each control displays the text differently.</span></span> <span data-ttu-id="1c26d-178">Aşağıdaki tabloda, metin ile ilgili bu üç denetim, metin görüntüleme özellikleri ve denetimin metnini içeren özellikler listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="1c26d-178">The following table lists these three text-related controls, their capabilities when they display text, and their properties that contain the control's text.</span></span>  
  
|<span data-ttu-id="1c26d-179">Denetim</span><span class="sxs-lookup"><span data-stu-id="1c26d-179">Control</span></span>|<span data-ttu-id="1c26d-180">Metin şöyle görüntülenir</span><span class="sxs-lookup"><span data-stu-id="1c26d-180">Text is displayed as</span></span>|<span data-ttu-id="1c26d-181">İçerik özelliği</span><span class="sxs-lookup"><span data-stu-id="1c26d-181">Content property</span></span>|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|<span data-ttu-id="1c26d-182">Düz metin</span><span class="sxs-lookup"><span data-stu-id="1c26d-182">Plain text</span></span>|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|<span data-ttu-id="1c26d-183">Biçimlendirilmiş metin</span><span class="sxs-lookup"><span data-stu-id="1c26d-183">Formatted text</span></span>|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|<span data-ttu-id="1c26d-184">Gizli metin (karakterler maskelenir)</span><span class="sxs-lookup"><span data-stu-id="1c26d-184">Hidden text (characters are masked)</span></span>|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>   
## <a name="classes-that-display-your-text"></a><span data-ttu-id="1c26d-185">Metninizi görüntüleyen sınıflar</span><span class="sxs-lookup"><span data-stu-id="1c26d-185">Classes That Display Your Text</span></span>  
 <span data-ttu-id="1c26d-186">Düz veya biçimli metinleri göstermek için birkaç sınıf kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1c26d-186">Several classes can be used to display plain or formatted text.</span></span> <span data-ttu-id="1c26d-187">Küçük miktarlarda metin göstermek için <xref:System.Windows.Controls.TextBlock> kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c26d-187">You can use <xref:System.Windows.Controls.TextBlock> to display small amounts of text.</span></span> <span data-ttu-id="1c26d-188">Büyük miktarlarda metin göstermek istiyorsanız <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>veya <xref:System.Windows.Controls.FlowDocumentScrollViewer> denetimlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1c26d-188">If you want to display large amounts of text, use the <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, or <xref:System.Windows.Controls.FlowDocumentScrollViewer> controls.</span></span>  
  
 <span data-ttu-id="1c26d-189"><xref:System.Windows.Controls.TextBlock> iki içerik özelliği vardır: <xref:System.Windows.Controls.TextBlock.Text%2A> ve <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span><span class="sxs-lookup"><span data-stu-id="1c26d-189">The <xref:System.Windows.Controls.TextBlock> has two content properties: <xref:System.Windows.Controls.TextBlock.Text%2A> and <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span></span> <span data-ttu-id="1c26d-190">Tutarlı biçimlendirme kullanan metni göstermek istediğinizde, <xref:System.Windows.Controls.TextBlock.Text%2A> özelliği genellikle en iyi seçimdir.</span><span class="sxs-lookup"><span data-stu-id="1c26d-190">When you want to display text that uses consistent formatting, the <xref:System.Windows.Controls.TextBlock.Text%2A> property is often your best choice.</span></span> <span data-ttu-id="1c26d-191">Metnin tamamında farklı biçimlendirme kullanmayı planlıyorsanız <xref:System.Windows.Controls.TextBlock.Inlines%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1c26d-191">If you plan to use different formatting throughout the text, use the <xref:System.Windows.Controls.TextBlock.Inlines%2A> property.</span></span> <span data-ttu-id="1c26d-192"><xref:System.Windows.Controls.TextBlock.Inlines%2A> özelliği, metnin nasıl biçimlendirileceğini belirten bir <xref:System.Windows.Documents.Inline> nesneleri koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="1c26d-192">The <xref:System.Windows.Controls.TextBlock.Inlines%2A> property is a collection of <xref:System.Windows.Documents.Inline> objects, which specify how to format text.</span></span>  
  
 <span data-ttu-id="1c26d-193">Aşağıdaki tabloda <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>ve <xref:System.Windows.Controls.FlowDocumentScrollViewer> sınıflarının içerik özelliği listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="1c26d-193">The following table lists the content property for <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, and <xref:System.Windows.Controls.FlowDocumentScrollViewer> classes.</span></span>  
  
|<span data-ttu-id="1c26d-194">Denetim</span><span class="sxs-lookup"><span data-stu-id="1c26d-194">Control</span></span>|<span data-ttu-id="1c26d-195">İçerik özelliği</span><span class="sxs-lookup"><span data-stu-id="1c26d-195">Content property</span></span>|<span data-ttu-id="1c26d-196">İçerik özelliği türü</span><span class="sxs-lookup"><span data-stu-id="1c26d-196">Content property type</span></span>|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|<span data-ttu-id="1c26d-197">Belge</span><span class="sxs-lookup"><span data-stu-id="1c26d-197">Document</span></span>|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|<span data-ttu-id="1c26d-198">Belge</span><span class="sxs-lookup"><span data-stu-id="1c26d-198">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|<span data-ttu-id="1c26d-199">Belge</span><span class="sxs-lookup"><span data-stu-id="1c26d-199">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
  
 <span data-ttu-id="1c26d-200"><xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.IDocumentPaginatorSource> arabirimini uygular; Bu nedenle, üç sınıfın hepsi içerik olarak <xref:System.Windows.Documents.FlowDocument> alabilir.</span><span class="sxs-lookup"><span data-stu-id="1c26d-200">The <xref:System.Windows.Documents.FlowDocument> implements the <xref:System.Windows.Documents.IDocumentPaginatorSource> interface; therefore, all three classes can take a <xref:System.Windows.Documents.FlowDocument> as content.</span></span>  
  
<a name="classes_that_format_text"></a>   
## <a name="classes-that-format-your-text"></a><span data-ttu-id="1c26d-201">Metninizi biçimlendirmek için sınıflar</span><span class="sxs-lookup"><span data-stu-id="1c26d-201">Classes That Format Your Text</span></span>  
 <span data-ttu-id="1c26d-202"><xref:System.Windows.Documents.TextElement> ve ilgili sınıfları metni biçimlendirmeye izin verir.</span><span class="sxs-lookup"><span data-stu-id="1c26d-202"><xref:System.Windows.Documents.TextElement> and its related classes allow you to format text.</span></span> <span data-ttu-id="1c26d-203"><xref:System.Windows.Documents.TextElement> nesneler <xref:System.Windows.Controls.TextBlock> ve <xref:System.Windows.Documents.FlowDocument> nesnelerinde metin içerir ve biçimlendirir.</span><span class="sxs-lookup"><span data-stu-id="1c26d-203"><xref:System.Windows.Documents.TextElement> objects contain and format text in <xref:System.Windows.Controls.TextBlock> and <xref:System.Windows.Documents.FlowDocument> objects.</span></span> <span data-ttu-id="1c26d-204"><xref:System.Windows.Documents.TextElement> nesnelerinin iki birincil türü <xref:System.Windows.Documents.Block> öğeler ve <xref:System.Windows.Documents.Inline> öğelerdir.</span><span class="sxs-lookup"><span data-stu-id="1c26d-204">The two primary types of <xref:System.Windows.Documents.TextElement> objects are <xref:System.Windows.Documents.Block> elements and <xref:System.Windows.Documents.Inline> elements.</span></span> <span data-ttu-id="1c26d-205">Bir <xref:System.Windows.Documents.Block> öğesi paragraf veya liste gibi bir metin bloğunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1c26d-205">A <xref:System.Windows.Documents.Block> element represents a block of text, such as a paragraph or list.</span></span> <span data-ttu-id="1c26d-206">Bir <xref:System.Windows.Documents.Inline> öğesi bir bloğundaki metnin bir bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1c26d-206">An <xref:System.Windows.Documents.Inline> element represents a portion of text in a block.</span></span> <span data-ttu-id="1c26d-207">Birçok <xref:System.Windows.Documents.Inline> sınıfı, uygulandıkları metin için biçimlendirme belirler.</span><span class="sxs-lookup"><span data-stu-id="1c26d-207">Many <xref:System.Windows.Documents.Inline> classes specify formatting for the text to which they are applied.</span></span> <span data-ttu-id="1c26d-208">Her <xref:System.Windows.Documents.TextElement> kendi içerik modeline sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1c26d-208">Each <xref:System.Windows.Documents.TextElement> has its own content model.</span></span> <span data-ttu-id="1c26d-209">Daha fazla bilgi için bkz. [TextElement Içerik modeline genel bakış](../advanced/textelement-content-model-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1c26d-209">For more information, see the [TextElement Content Model Overview](../advanced/textelement-content-model-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c26d-210">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c26d-210">See also</span></span>

- [<span data-ttu-id="1c26d-211">Gelişmiş</span><span class="sxs-lookup"><span data-stu-id="1c26d-211">Advanced</span></span>](../advanced/index.md)
