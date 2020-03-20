---
title: İçerik Modeli
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
ms.openlocfilehash: ec4e96c0883489135b77f09a3c19f144cb4d30bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187399"
---
# <a name="wpf-content-model"></a><span data-ttu-id="42891-102">WPF İçerik Modeli</span><span class="sxs-lookup"><span data-stu-id="42891-102">WPF Content Model</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="42891-103">birincil amacı farklı içerik türlerini görüntülemek olan birçok denetim ve denetim benzeri türler sağlayan bir sunum platformudur.</span><span class="sxs-lookup"><span data-stu-id="42891-103">is a presentation platform that provides many controls and control-like types whose primary purpose is to display different types of content.</span></span> <span data-ttu-id="42891-104">Hangi denetimin kullanılacağını veya hangi denetimden türediğinizi belirlemek için, belirli bir denetimin en iyi görüntülenebildiği nesne türlerini anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="42891-104">To determine which control to use or which control to derive from, you should understand the kinds of objects a particular control can best display.</span></span>  
  
 <span data-ttu-id="42891-105">Bu konu, denetim ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetim benzeri türleri için içerik modelini özetler.</span><span class="sxs-lookup"><span data-stu-id="42891-105">This topic summarizes the content model for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] control and control-like types.</span></span> <span data-ttu-id="42891-106">İçerik modeli, denetimde hangi içeriğin kullanılabileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="42891-106">The content model describes what content can be used in a control.</span></span> <span data-ttu-id="42891-107">Bu konu, her içerik modeli için içerik özelliklerini de listeler.</span><span class="sxs-lookup"><span data-stu-id="42891-107">This topic also lists the content properties for each content model.</span></span> <span data-ttu-id="42891-108">İçerik özelliği, nesnenin içeriğini depolamak için kullanılan bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="42891-108">A content property is a property that is used to store the content of the object.</span></span>  

<a name="classes_that_contain_arbitrary_content"></a>
## <a name="classes-that-contain-arbitrary-content"></a><span data-ttu-id="42891-109">Rasgele İçerik İçeren Sınıflar</span><span class="sxs-lookup"><span data-stu-id="42891-109">Classes That Contain Arbitrary Content</span></span>  
 <span data-ttu-id="42891-110">Bazı denetimler, dize, <xref:System.DateTime> nesne veya ek öğeler için <xref:System.Windows.UIElement> kapsayıcı olan bir kapsayıcı gibi herhangi bir türde bir nesne içerebilir.</span><span class="sxs-lookup"><span data-stu-id="42891-110">Some controls can contain an object of any type, such as a string, a <xref:System.DateTime> object, or a <xref:System.Windows.UIElement> that is a container for additional items.</span></span> <span data-ttu-id="42891-111">Örneğin, bir <xref:System.Windows.Controls.Button> resim ve bazı metin içerebilir; veya <xref:System.Windows.Controls.CheckBox> bir değeri <xref:System.DateTime.Now%2A?displayProperty=nameWithType>içerebilir.</span><span class="sxs-lookup"><span data-stu-id="42891-111">For example, a <xref:System.Windows.Controls.Button> can contain an image and some text; or a <xref:System.Windows.Controls.CheckBox> can contain the value of <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.</span></span>  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="42891-112">rasgele içerik içerebilen dört sınıfı vardır.</span><span class="sxs-lookup"><span data-stu-id="42891-112">has four classes that can contain arbitrary content.</span></span> <span data-ttu-id="42891-113">Aşağıdaki tabloda, 'den <xref:System.Windows.Controls.Control>devralınan sınıflar listele</span><span class="sxs-lookup"><span data-stu-id="42891-113">The following table lists the classes, which inherit from <xref:System.Windows.Controls.Control>.</span></span>  
  
|<span data-ttu-id="42891-114">Rasgele içerik içeren sınıf</span><span class="sxs-lookup"><span data-stu-id="42891-114">Class that contains arbitrary content</span></span>|<span data-ttu-id="42891-115">İçerik</span><span class="sxs-lookup"><span data-stu-id="42891-115">Content</span></span>|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="42891-116">Tek bir rasgele nesne.</span><span class="sxs-lookup"><span data-stu-id="42891-116">A single arbitrary object.</span></span>|  
|<xref:System.Windows.Controls.HeaderedContentControl>|<span data-ttu-id="42891-117">Her ikisi de rasgele nesneler olan bir üstbilgi ve tek bir öğe.</span><span class="sxs-lookup"><span data-stu-id="42891-117">A header and a single item, both of which are arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.ItemsControl>|<span data-ttu-id="42891-118">Rasgele nesneler topluluğu.</span><span class="sxs-lookup"><span data-stu-id="42891-118">A collection of arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|<span data-ttu-id="42891-119">Üstbilgi ve öğelerin bir koleksiyon, hepsi rasgele nesnelerdir.</span><span class="sxs-lookup"><span data-stu-id="42891-119">A header and a collection of items, all of which are arbitrary objects.</span></span>|  
  
 <span data-ttu-id="42891-120">Bu sınıflardan devralan denetimler aynı içerik türünü içerebilir ve içeriği aynı şekilde işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="42891-120">Controls that inherit from these classes can contain the same type of content and treat the content in the same way.</span></span> <span data-ttu-id="42891-121">Aşağıdaki resimde, resim ve bazı metin içeren her içerik modelinden bir denetim gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="42891-121">The following illustration shows one control from each content model that contains an image and some text:</span></span>  
  
 ![Her içerik modelinden bir tane olmak üzere dört farklı denetim gösteren ekran görüntüsü.](./media/wpf-content-model/control-content-model-image-text.png)  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a><span data-ttu-id="42891-123">Tek Bir Rasgele Nesne İçeren Denetimler</span><span class="sxs-lookup"><span data-stu-id="42891-123">Controls That Contain a Single Arbitrary Object</span></span>  
 <span data-ttu-id="42891-124">Sınıf, <xref:System.Windows.Controls.ContentControl> tek bir rasgele içerik parçası içerir.</span><span class="sxs-lookup"><span data-stu-id="42891-124">The <xref:System.Windows.Controls.ContentControl> class contains a single piece of arbitrary content.</span></span> <span data-ttu-id="42891-125">İçeriğinin özelliği <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="42891-125">Its content property is <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="42891-126">Aşağıdaki denetimler, <xref:System.Windows.Controls.ContentControl> içerik modelinden devralır ve kullanır:</span><span class="sxs-lookup"><span data-stu-id="42891-126">The following controls inherit from <xref:System.Windows.Controls.ContentControl> and use its content model:</span></span>  
  
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
  
 <span data-ttu-id="42891-127">Aşağıdaki resimde, bir <xref:System.Windows.Controls.ContentControl.Content%2A> dize, bir <xref:System.DateTime> nesne, a <xref:System.Windows.Shapes.Rectangle>, ve <xref:System.Windows.Controls.Panel> a <xref:System.Windows.Shapes.Ellipse> için <xref:System.Windows.Controls.TextBlock>ayarlanmış dört düğme gösterir ve bir:</span><span class="sxs-lookup"><span data-stu-id="42891-127">The following illustration shows four buttons whose <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a string, a <xref:System.DateTime> object, a <xref:System.Windows.Shapes.Rectangle>, and a <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>:</span></span>  
  
 ![Farklı içerik türlerine sahip dört düğme gösteren ekran görüntüsü.](./media/wpf-content-model/control-content-model-buttons.png)  
  
 <span data-ttu-id="42891-129">Özelliğin nasıl ayarlanabildiğini <xref:System.Windows.Controls.ContentControl.Content%2A> öğrenmek <xref:System.Windows.Controls.ContentControl>için bkz.</span><span class="sxs-lookup"><span data-stu-id="42891-129">For an example of how to set the <xref:System.Windows.Controls.ContentControl.Content%2A> property, see <xref:System.Windows.Controls.ContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a><span data-ttu-id="42891-130">Üstbilgi ve Tek Rasgele Nesne İçeren Denetimler</span><span class="sxs-lookup"><span data-stu-id="42891-130">Controls That Contain a Header and a Single Arbitrary Object</span></span>  
 <span data-ttu-id="42891-131">Sınıf, <xref:System.Windows.Controls.HeaderedContentControl> içeriği <xref:System.Windows.Controls.ContentControl> üstbilgiyle devralır ve görüntüler.</span><span class="sxs-lookup"><span data-stu-id="42891-131">The <xref:System.Windows.Controls.HeaderedContentControl> class inherits from <xref:System.Windows.Controls.ContentControl> and displays content with a header.</span></span> <span data-ttu-id="42891-132">İçerik özelliğini devralır <xref:System.Windows.Controls.ContentControl.Content%2A> <xref:System.Windows.Controls.ContentControl> ve türünde <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> <xref:System.Object>olan özelliği tanımlar; bu nedenle, her ikisi de rasgele bir nesne olabilir.</span><span class="sxs-lookup"><span data-stu-id="42891-132">It inherits the content property, <xref:System.Windows.Controls.ContentControl.Content%2A>, from <xref:System.Windows.Controls.ContentControl> and defines the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> property that is of type <xref:System.Object>; therefore, both can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="42891-133">Aşağıdaki denetimler, <xref:System.Windows.Controls.HeaderedContentControl> içerik modelinden devralır ve kullanır:</span><span class="sxs-lookup"><span data-stu-id="42891-133">The following controls inherit from <xref:System.Windows.Controls.HeaderedContentControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.Expander>  
  
- <xref:System.Windows.Controls.GroupBox>  
  
- <xref:System.Windows.Controls.TabItem>  
  
 <span data-ttu-id="42891-134">Aşağıdaki resimde iki <xref:System.Windows.Controls.TabItem> nesne gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="42891-134">The following illustration shows two <xref:System.Windows.Controls.TabItem> objects.</span></span> <span data-ttu-id="42891-135">İlk <xref:System.Windows.Controls.TabItem> ve <xref:System.Windows.UIElement> olarak <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> nesneleri <xref:System.Windows.Controls.ContentControl.Content%2A>vardır.</span><span class="sxs-lookup"><span data-stu-id="42891-135">The first <xref:System.Windows.Controls.TabItem> has <xref:System.Windows.UIElement> objects as the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="42891-136">Bir <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> ve bir <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Shapes.Ellipse> içeren bir <xref:System.Windows.Controls.TextBlock>olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="42891-136">The <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="42891-137">A <xref:System.Windows.Controls.ContentControl.Content%2A> ve a <xref:System.Windows.Controls.StackPanel> içeren <xref:System.Windows.Controls.TextBlock> bir <xref:System.Windows.Controls.Label>olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="42891-137">The <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains a <xref:System.Windows.Controls.TextBlock> and a <xref:System.Windows.Controls.Label>.</span></span> <span data-ttu-id="42891-138">İkinci <xref:System.Windows.Controls.TabItem> ve bir <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> <xref:System.Windows.Controls.TextBlock> dize vardır <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="42891-138">The second <xref:System.Windows.Controls.TabItem> has a string in the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and a <xref:System.Windows.Controls.TextBlock> in the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span>  
  
 ![Üstbilgi özelliğinde farklı türleri kullanan Sekme Denetimi.](./media/wpf-content-model/control-content-model-tab.png)  
  
 <span data-ttu-id="42891-140">Nesnelerin nasıl oluşturulabildiğini <xref:System.Windows.Controls.TabItem> görmek için <xref:System.Windows.Controls.HeaderedContentControl>bkz.</span><span class="sxs-lookup"><span data-stu-id="42891-140">For an example of how to create <xref:System.Windows.Controls.TabItem> objects, see <xref:System.Windows.Controls.HeaderedContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a><span data-ttu-id="42891-141">Rasgele Nesneler Topluluğu İçeren Denetimler</span><span class="sxs-lookup"><span data-stu-id="42891-141">Controls That Contain a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="42891-142">Sınıf, <xref:System.Windows.Controls.ItemsControl> dizeleri, nesneleri veya diğer öğeler gibi birden çok öğeden <xref:System.Windows.Controls.Control> devralır ve içerebilir.</span><span class="sxs-lookup"><span data-stu-id="42891-142">The <xref:System.Windows.Controls.ItemsControl> class inherits from <xref:System.Windows.Controls.Control> and can contain multiple items, such as strings, objects, or other elements.</span></span> <span data-ttu-id="42891-143">İçerik özellikleri <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> ve <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span><span class="sxs-lookup"><span data-stu-id="42891-143">Its content properties are <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> and <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span></span> <span data-ttu-id="42891-144"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>genellikle bir veri toplama <xref:System.Windows.Controls.ItemsControl> ile doldurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="42891-144"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> is typically used to populate the <xref:System.Windows.Controls.ItemsControl> with a data collection.</span></span> <span data-ttu-id="42891-145">Doldurmak için bir koleksiyon kullanmak <xref:System.Windows.Controls.ItemsControl>istemiyorsanız, <xref:System.Windows.Controls.ItemsControl.Items%2A> özelliği kullanarak öğeleri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42891-145">If you do not want to use a collection to populate the <xref:System.Windows.Controls.ItemsControl>, you can add items by using the <xref:System.Windows.Controls.ItemsControl.Items%2A> property.</span></span>  
  
 <span data-ttu-id="42891-146">Aşağıdaki denetimler, <xref:System.Windows.Controls.ItemsControl> içerik modelinden devralır ve kullanır:</span><span class="sxs-lookup"><span data-stu-id="42891-146">The following controls inherit from <xref:System.Windows.Controls.ItemsControl> and use its content model:</span></span>  
  
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
  
 <span data-ttu-id="42891-147">Aşağıdaki resimde bu <xref:System.Windows.Controls.ListBox> tür öğeleri içeren bir gösteri:</span><span class="sxs-lookup"><span data-stu-id="42891-147">The following illustration shows a <xref:System.Windows.Controls.ListBox> that contains these types of items:</span></span>  
  
- <span data-ttu-id="42891-148">Bir ip.</span><span class="sxs-lookup"><span data-stu-id="42891-148">A string.</span></span>  
  
- <span data-ttu-id="42891-149">Bir <xref:System.DateTime> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="42891-149">A <xref:System.DateTime> object.</span></span>  
  
- <span data-ttu-id="42891-150">Bir <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="42891-150">A <xref:System.Windows.UIElement>.</span></span>  
  
- <span data-ttu-id="42891-151">A <xref:System.Windows.Controls.Panel> ve <xref:System.Windows.Shapes.Ellipse> bir <xref:System.Windows.Controls.TextBlock>içerir.</span><span class="sxs-lookup"><span data-stu-id="42891-151">A <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 ![Dört tür içeriğe sahip bir ListBox gösteren ekran görüntüsü.](./media/wpf-content-model/control-content-model-listbox.png)  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a><span data-ttu-id="42891-153">Üstbilgi ve Rasgele Nesneler Topluluğu İçeren Denetimler</span><span class="sxs-lookup"><span data-stu-id="42891-153">Controls That Contain a Header and a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="42891-154">Sınıf, <xref:System.Windows.Controls.HeaderedItemsControl> dizeleri, nesneler veya diğer öğeler ve bir üstbilgi gibi birden çok öğeden <xref:System.Windows.Controls.ItemsControl> devralır ve içerebilir.</span><span class="sxs-lookup"><span data-stu-id="42891-154">The <xref:System.Windows.Controls.HeaderedItemsControl> class inherits from <xref:System.Windows.Controls.ItemsControl> and can contain multiple items, such as strings, objects, or other elements, and a header.</span></span> <span data-ttu-id="42891-155">İçerik özelliklerini <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>devralır ve <xref:System.Windows.Controls.ItemsControl.Items%2A>rasgele bir nesne <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> olabilecek özelliği tanımlar. <xref:System.Windows.Controls.ItemsControl></span><span class="sxs-lookup"><span data-stu-id="42891-155">It inherits the <xref:System.Windows.Controls.ItemsControl> content properties, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, and <xref:System.Windows.Controls.ItemsControl.Items%2A>, and it defines the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property that can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="42891-156">Aşağıdaki denetimler, <xref:System.Windows.Controls.HeaderedItemsControl> içerik modelinden devralır ve kullanır:</span><span class="sxs-lookup"><span data-stu-id="42891-156">The following controls inherit from <xref:System.Windows.Controls.HeaderedItemsControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.MenuItem>  
  
- <xref:System.Windows.Controls.ToolBar>  
  
- <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a><span data-ttu-id="42891-157">UIElement Nesnelerinin Bir Koleksiyonunu İçeren Sınıflar</span><span class="sxs-lookup"><span data-stu-id="42891-157">Classes That Contain a Collection of UIElement Objects</span></span>  
 <span data-ttu-id="42891-158">Sınıf <xref:System.Windows.Controls.Panel> konumları ve <xref:System.Windows.UIElement> alt nesneleri düzenler.</span><span class="sxs-lookup"><span data-stu-id="42891-158">The <xref:System.Windows.Controls.Panel> class positions and arranges child <xref:System.Windows.UIElement> objects.</span></span> <span data-ttu-id="42891-159">İçeriğinin özelliği <xref:System.Windows.Controls.Panel.Children%2A>.</span><span class="sxs-lookup"><span data-stu-id="42891-159">Its content property is <xref:System.Windows.Controls.Panel.Children%2A>.</span></span>  
  
 <span data-ttu-id="42891-160">Aşağıdaki sınıflar <xref:System.Windows.Controls.Panel> sınıftan devralır ve içerik modelini kullanır:</span><span class="sxs-lookup"><span data-stu-id="42891-160">The following classes inherit from the <xref:System.Windows.Controls.Panel> class and use its content model:</span></span>  
  
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
  
 <span data-ttu-id="42891-161">Daha fazla bilgi için [Paneller Genel Bakış'a](panels-overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="42891-161">For more information, see [Panels Overview](panels-overview.md).</span></span>  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a><span data-ttu-id="42891-162">Bir UIElement görünümünü etkileyen sınıflar</span><span class="sxs-lookup"><span data-stu-id="42891-162">Classes That Affect the Appearance of a UIElement</span></span>  
 <span data-ttu-id="42891-163">Sınıf, <xref:System.Windows.Controls.Decorator> tek bir çocuğun <xref:System.Windows.UIElement>üzerine veya çevresine görsel efektler uygular.</span><span class="sxs-lookup"><span data-stu-id="42891-163">The <xref:System.Windows.Controls.Decorator> class applies visual effects onto or around a single child <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="42891-164">İçeriğinin özelliği <xref:System.Windows.Controls.Decorator.Child%2A>.</span><span class="sxs-lookup"><span data-stu-id="42891-164">Its content property is <xref:System.Windows.Controls.Decorator.Child%2A>.</span></span> <span data-ttu-id="42891-165">Aşağıdaki sınıflar, <xref:System.Windows.Controls.Decorator> içerik modelinden devralır ve kullanır:</span><span class="sxs-lookup"><span data-stu-id="42891-165">The following classes inherit from <xref:System.Windows.Controls.Decorator> and use its content model:</span></span>  
  
- <xref:System.Windows.Documents.AdornerDecorator>  
  
- <xref:System.Windows.Controls.Border>  
  
- <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
- <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
- <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
- <xref:System.Windows.Controls.InkPresenter>  
  
- <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
- <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
- <xref:System.Windows.Controls.Viewbox>  
  
 <span data-ttu-id="42891-166">Aşağıdaki resimde, <xref:System.Windows.Controls.TextBox> etrafında bir (ile süslenmiş) <xref:System.Windows.Controls.Border> bir gösterir.</span><span class="sxs-lookup"><span data-stu-id="42891-166">The following illustration shows a <xref:System.Windows.Controls.TextBox> that has (is decorated with) a <xref:System.Windows.Controls.Border> around it.</span></span>  
  
 <span data-ttu-id="42891-167">![Kara kenarlıklı TextBox](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span><span class="sxs-lookup"><span data-stu-id="42891-167">![TextBox with black border](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span></span>  
<span data-ttu-id="42891-168">Kenarlık olan TextBlock</span><span class="sxs-lookup"><span data-stu-id="42891-168">TextBlock that has a Border</span></span>  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a><span data-ttu-id="42891-169">UIElement Hakkında Görsel Geri Bildirim Sağlayan Sınıflar</span><span class="sxs-lookup"><span data-stu-id="42891-169">Classes That Provide Visual Feedback About a UIElement</span></span>  
 <span data-ttu-id="42891-170">Sınıf, <xref:System.Windows.Documents.Adorner> kullanıcıya görsel ipuçları sağlar.</span><span class="sxs-lookup"><span data-stu-id="42891-170">The <xref:System.Windows.Documents.Adorner> class provides visual cues to a user.</span></span> <span data-ttu-id="42891-171">Örneğin, öğelere <xref:System.Windows.Documents.Adorner> işlevsel işletmeler eklemek veya denetim hakkında durum bilgileri sağlamak için bir kullanın.</span><span class="sxs-lookup"><span data-stu-id="42891-171">For example, use an <xref:System.Windows.Documents.Adorner> to add functional handles to elements or provide state information about a control.</span></span> <span data-ttu-id="42891-172">Sınıf, <xref:System.Windows.Documents.Adorner> kendi süsleyicilerinizi oluşturabilmeniz için bir çerçeve sağlar.</span><span class="sxs-lookup"><span data-stu-id="42891-172">The <xref:System.Windows.Documents.Adorner> class provides a framework so that you can create your own adorners.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="42891-173">uygulanan süsleyiciler sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="42891-173">does not provide any implemented adorners.</span></span> <span data-ttu-id="42891-174">Daha fazla bilgi için [Bkz. Adorners Genel Bakış.](adorners-overview.md)</span><span class="sxs-lookup"><span data-stu-id="42891-174">For more information, see [Adorners Overview](adorners-overview.md).</span></span>  
  
<a name="classes_that_enable_users_to_enter_text"></a>
## <a name="classes-that-enable-users-to-enter-text"></a><span data-ttu-id="42891-175">Kullanıcıların Metin Girmesini Sağlayan Sınıflar</span><span class="sxs-lookup"><span data-stu-id="42891-175">Classes That Enable Users to Enter Text</span></span>  
 <span data-ttu-id="42891-176">WPF, kullanıcıların metin girmesini sağlayan üç birincil denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="42891-176">WPF provides three primary controls that enable users to enter text.</span></span> <span data-ttu-id="42891-177">Her denetim metni farklı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="42891-177">Each control displays the text differently.</span></span> <span data-ttu-id="42891-178">Aşağıdaki tabloda bu üç metinle ilgili denetim, metni görüntülediklerinde ki yetenekleri ve denetimmetnini içeren özellikleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="42891-178">The following table lists these three text-related controls, their capabilities when they display text, and their properties that contain the control's text.</span></span>  
  
|<span data-ttu-id="42891-179">Denetim</span><span class="sxs-lookup"><span data-stu-id="42891-179">Control</span></span>|<span data-ttu-id="42891-180">Metin olarak görüntülenir</span><span class="sxs-lookup"><span data-stu-id="42891-180">Text is displayed as</span></span>|<span data-ttu-id="42891-181">İçerik özelliği</span><span class="sxs-lookup"><span data-stu-id="42891-181">Content property</span></span>|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|<span data-ttu-id="42891-182">Düz metin</span><span class="sxs-lookup"><span data-stu-id="42891-182">Plain text</span></span>|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|<span data-ttu-id="42891-183">Biçimlendirilmiş metin</span><span class="sxs-lookup"><span data-stu-id="42891-183">Formatted text</span></span>|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|<span data-ttu-id="42891-184">Gizli metin (karakterler maskelenir)</span><span class="sxs-lookup"><span data-stu-id="42891-184">Hidden text (characters are masked)</span></span>|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>
## <a name="classes-that-display-your-text"></a><span data-ttu-id="42891-185">Metninizi Görüntüleyen Sınıflar</span><span class="sxs-lookup"><span data-stu-id="42891-185">Classes That Display Your Text</span></span>  
 <span data-ttu-id="42891-186">Düz veya biçimlendirilmiş metni görüntülemek için çeşitli sınıflar kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="42891-186">Several classes can be used to display plain or formatted text.</span></span> <span data-ttu-id="42891-187">Küçük miktarda <xref:System.Windows.Controls.TextBlock> metin görüntülemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42891-187">You can use <xref:System.Windows.Controls.TextBlock> to display small amounts of text.</span></span> <span data-ttu-id="42891-188">Büyük miktarda metin görüntülemek istiyorsanız, <xref:System.Windows.Controls.FlowDocumentReader>", <xref:System.Windows.Controls.FlowDocumentPageViewer>" <xref:System.Windows.Controls.FlowDocumentScrollViewer> veya denetimleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="42891-188">If you want to display large amounts of text, use the <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, or <xref:System.Windows.Controls.FlowDocumentScrollViewer> controls.</span></span>  
  
 <span data-ttu-id="42891-189">İki <xref:System.Windows.Controls.TextBlock> içerik özelliği <xref:System.Windows.Controls.TextBlock.Text%2A> vardır: ve <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span><span class="sxs-lookup"><span data-stu-id="42891-189">The <xref:System.Windows.Controls.TextBlock> has two content properties: <xref:System.Windows.Controls.TextBlock.Text%2A> and <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span></span> <span data-ttu-id="42891-190">Tutarlı biçimlendirme kullanan metni görüntülemek istediğinizde, <xref:System.Windows.Controls.TextBlock.Text%2A> özellik genellikle en iyi seçimdir.</span><span class="sxs-lookup"><span data-stu-id="42891-190">When you want to display text that uses consistent formatting, the <xref:System.Windows.Controls.TextBlock.Text%2A> property is often your best choice.</span></span> <span data-ttu-id="42891-191">Metin boyunca farklı biçimlendirme kullanmayı planlıyorsanız, <xref:System.Windows.Controls.TextBlock.Inlines%2A> özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="42891-191">If you plan to use different formatting throughout the text, use the <xref:System.Windows.Controls.TextBlock.Inlines%2A> property.</span></span> <span data-ttu-id="42891-192">Özellik, <xref:System.Windows.Controls.TextBlock.Inlines%2A> metnin <xref:System.Windows.Documents.Inline> nasıl biçimlendirilenini belirten nesneler topluluğudur.</span><span class="sxs-lookup"><span data-stu-id="42891-192">The <xref:System.Windows.Controls.TextBlock.Inlines%2A> property is a collection of <xref:System.Windows.Documents.Inline> objects, which specify how to format text.</span></span>  
  
 <span data-ttu-id="42891-193">Aşağıdaki tabloda, ve <xref:System.Windows.Controls.FlowDocumentReader> <xref:System.Windows.Controls.FlowDocumentPageViewer> <xref:System.Windows.Controls.FlowDocumentScrollViewer> sınıflar için içerik özelliği listeleniztir.</span><span class="sxs-lookup"><span data-stu-id="42891-193">The following table lists the content property for <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, and <xref:System.Windows.Controls.FlowDocumentScrollViewer> classes.</span></span>  
  
|<span data-ttu-id="42891-194">Denetim</span><span class="sxs-lookup"><span data-stu-id="42891-194">Control</span></span>|<span data-ttu-id="42891-195">İçerik özelliği</span><span class="sxs-lookup"><span data-stu-id="42891-195">Content property</span></span>|<span data-ttu-id="42891-196">İçerik özellik türü</span><span class="sxs-lookup"><span data-stu-id="42891-196">Content property type</span></span>|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|<span data-ttu-id="42891-197">Belge</span><span class="sxs-lookup"><span data-stu-id="42891-197">Document</span></span>|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|<span data-ttu-id="42891-198">Belge</span><span class="sxs-lookup"><span data-stu-id="42891-198">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|<span data-ttu-id="42891-199">Belge</span><span class="sxs-lookup"><span data-stu-id="42891-199">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
  
 <span data-ttu-id="42891-200"><xref:System.Windows.Documents.IDocumentPaginatorSource> Arabirimi <xref:System.Windows.Documents.FlowDocument> uygular; bu nedenle, her üç <xref:System.Windows.Documents.FlowDocument> sınıf bir içerik olarak alabilir.</span><span class="sxs-lookup"><span data-stu-id="42891-200">The <xref:System.Windows.Documents.FlowDocument> implements the <xref:System.Windows.Documents.IDocumentPaginatorSource> interface; therefore, all three classes can take a <xref:System.Windows.Documents.FlowDocument> as content.</span></span>  
  
<a name="classes_that_format_text"></a>
## <a name="classes-that-format-your-text"></a><span data-ttu-id="42891-201">Metninizi Biçimlendiren Sınıflar</span><span class="sxs-lookup"><span data-stu-id="42891-201">Classes That Format Your Text</span></span>  
 <span data-ttu-id="42891-202"><xref:System.Windows.Documents.TextElement>ve ilgili sınıfları metni biçimlendirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="42891-202"><xref:System.Windows.Documents.TextElement> and its related classes allow you to format text.</span></span> <span data-ttu-id="42891-203"><xref:System.Windows.Documents.TextElement>nesneler metin <xref:System.Windows.Controls.TextBlock> içerir ve <xref:System.Windows.Documents.FlowDocument> biçimlendirin ve nesneler.</span><span class="sxs-lookup"><span data-stu-id="42891-203"><xref:System.Windows.Documents.TextElement> objects contain and format text in <xref:System.Windows.Controls.TextBlock> and <xref:System.Windows.Documents.FlowDocument> objects.</span></span> <span data-ttu-id="42891-204">İki birincil <xref:System.Windows.Documents.TextElement> nesne türü <xref:System.Windows.Documents.Block> öğeler <xref:System.Windows.Documents.Inline> ve öğelerdir.</span><span class="sxs-lookup"><span data-stu-id="42891-204">The two primary types of <xref:System.Windows.Documents.TextElement> objects are <xref:System.Windows.Documents.Block> elements and <xref:System.Windows.Documents.Inline> elements.</span></span> <span data-ttu-id="42891-205">Öğe, <xref:System.Windows.Documents.Block> paragraf veya liste gibi bir metin bloğunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="42891-205">A <xref:System.Windows.Documents.Block> element represents a block of text, such as a paragraph or list.</span></span> <span data-ttu-id="42891-206">Öğe, <xref:System.Windows.Documents.Inline> bloğun metninin bir bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="42891-206">An <xref:System.Windows.Documents.Inline> element represents a portion of text in a block.</span></span> <span data-ttu-id="42891-207">Birçok <xref:System.Windows.Documents.Inline> sınıf, uygulandıkları metin için biçimlendirme belirtir.</span><span class="sxs-lookup"><span data-stu-id="42891-207">Many <xref:System.Windows.Documents.Inline> classes specify formatting for the text to which they are applied.</span></span> <span data-ttu-id="42891-208">Her <xref:System.Windows.Documents.TextElement> birinin kendi içerik modeli vardır.</span><span class="sxs-lookup"><span data-stu-id="42891-208">Each <xref:System.Windows.Documents.TextElement> has its own content model.</span></span> <span data-ttu-id="42891-209">Daha fazla bilgi için [TextElement İçerik Modeline Genel Bakış'a](../advanced/textelement-content-model-overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="42891-209">For more information, see the [TextElement Content Model Overview](../advanced/textelement-content-model-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42891-210">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42891-210">See also</span></span>

- [<span data-ttu-id="42891-211">Gelişmiş</span><span class="sxs-lookup"><span data-stu-id="42891-211">Advanced</span></span>](../advanced/index.md)
