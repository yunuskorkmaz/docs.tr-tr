---
title: "WPF İçerik Modeli"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 52cb3a5391d6e24643b03a880d3695a11baceca3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="wpf-content-model"></a><span data-ttu-id="f0df6-102">WPF İçerik Modeli</span><span class="sxs-lookup"><span data-stu-id="f0df6-102">WPF Content Model</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="f0df6-103">birçok denetimleri ve farklı içerik türlerini görüntülemek için birincil amacı olan denetim benzeri türleri sağlayan bir sunu platformudur.</span><span class="sxs-lookup"><span data-stu-id="f0df6-103"> is a presentation platform that provides many controls and control-like types whose primary purpose is to display different types of content.</span></span> <span data-ttu-id="f0df6-104">Kullanılacak hangi denetim veya denetleyen öğesinden türetilen belirlemek için belirli bir denetim en iyi görüntüleme nesne türlerini anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f0df6-104">To determine which control to use or which control to derive from, you should understand the kinds of objects a particular control can best display.</span></span>  
  
 <span data-ttu-id="f0df6-105">Bu konu için içerik modelini özetler [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi ve denetim benzeri türler.</span><span class="sxs-lookup"><span data-stu-id="f0df6-105">This topic summarizes the content model for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] control and control-like types.</span></span> <span data-ttu-id="f0df6-106">İçerik modeli, hangi içerik denetimi kullanılabilir açıklar.</span><span class="sxs-lookup"><span data-stu-id="f0df6-106">The content model describes what content can be used in a control.</span></span> <span data-ttu-id="f0df6-107">Bu konu aynı zamanda her bir içerik modeli için içerik özellikleri listeler.</span><span class="sxs-lookup"><span data-stu-id="f0df6-107">This topic also lists the content properties for each content model.</span></span> <span data-ttu-id="f0df6-108">İçerik özelliği nesnenin içeriğini depolamak için kullanılan bir özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="f0df6-108">A content property is a property that is used to store the content of the object.</span></span>  
  
 
  
<a name="classes_that_contain_arbitrary_content"></a>   
## <a name="classes-that-contain-arbitrary-content"></a><span data-ttu-id="f0df6-109">Rasgele içerik içeren sınıflar</span><span class="sxs-lookup"><span data-stu-id="f0df6-109">Classes That Contain Arbitrary Content</span></span>  
 <span data-ttu-id="f0df6-110">Bazı denetimler, dize gibi herhangi bir türde bir nesne içerebilir bir <xref:System.DateTime> nesnesi veya bir <xref:System.Windows.UIElement> yani ek öğelere ilişkin bir kapsayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="f0df6-110">Some controls can contain an object of any type, such as a string, a <xref:System.DateTime> object, or a <xref:System.Windows.UIElement> that is a container for additional items.</span></span> <span data-ttu-id="f0df6-111">Örneğin, bir <xref:System.Windows.Controls.Button> resim ve bazı metinler; içerebilir veya <xref:System.Windows.Controls.CheckBox> değerini içerebilir <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f0df6-111">For example, a <xref:System.Windows.Controls.Button> can contain an image and some text; or a <xref:System.Windows.Controls.CheckBox> can contain the value of <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.</span></span>  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="f0df6-112">rasgele içerik içerebilir dört sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="f0df6-112"> has four classes that can contain arbitrary content.</span></span> <span data-ttu-id="f0df6-113">Devralınan sınıfları aşağıdaki tabloda listelenmektedir <xref:System.Windows.Controls.Control>.</span><span class="sxs-lookup"><span data-stu-id="f0df6-113">The following table lists the classes, which inherit from <xref:System.Windows.Controls.Control>.</span></span>  
  
|<span data-ttu-id="f0df6-114">Rastgele içeriği sınıfı</span><span class="sxs-lookup"><span data-stu-id="f0df6-114">Class that contains arbitrary content</span></span>|<span data-ttu-id="f0df6-115">İçerik</span><span class="sxs-lookup"><span data-stu-id="f0df6-115">Content</span></span>|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="f0df6-116">Tek bir rasgele nesne.</span><span class="sxs-lookup"><span data-stu-id="f0df6-116">A single arbitrary object.</span></span>|  
|<xref:System.Windows.Controls.HeaderedContentControl>|<span data-ttu-id="f0df6-117">Üstbilgi ve her ikisi de rasgele nesne olan tek bir öğe.</span><span class="sxs-lookup"><span data-stu-id="f0df6-117">A header and a single item, both of which are arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.ItemsControl>|<span data-ttu-id="f0df6-118">Rastgele nesneleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f0df6-118">A collection of arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|<span data-ttu-id="f0df6-119">Üstbilgi ve rasgele nesneler tümü öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f0df6-119">A header and a collection of items, all of which are arbitrary objects.</span></span>|  
  
 <span data-ttu-id="f0df6-120">Bu sınıflardan devralan denetimleri aynı tür içerik içerebilir ve içeriği aynı şekilde ele alın.</span><span class="sxs-lookup"><span data-stu-id="f0df6-120">Controls that inherit from these classes can contain the same type of content and treat the content in the same way.</span></span> <span data-ttu-id="f0df6-121">Aşağıdaki çizimde bir görüntü içeren her bir içerik modeli ve bazı metin bir denetimden gösterir.</span><span class="sxs-lookup"><span data-stu-id="f0df6-121">The following illustration shows one control from each content model that contains an image and some text.</span></span>  
  
 <span data-ttu-id="f0df6-122">![Düğme, GroupBox, Listbax, TreeViewItem](../../../../docs/framework/wpf/controls/media/controlcontentmodelimagetextinto.PNG "ControlContentModelImageTextInto")</span><span class="sxs-lookup"><span data-stu-id="f0df6-122">![Button, GroupBox, Listbax, TreeViewItem](../../../../docs/framework/wpf/controls/media/controlcontentmodelimagetextinto.PNG "ControlContentModelImageTextInto")</span></span>  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a><span data-ttu-id="f0df6-123">Tek bir rasgele nesne içeren denetimler</span><span class="sxs-lookup"><span data-stu-id="f0df6-123">Controls That Contain a Single Arbitrary Object</span></span>  
 <span data-ttu-id="f0df6-124"><xref:System.Windows.Controls.ContentControl> Sınıfı rasgele içeriğin tek bir parçasını içerir.</span><span class="sxs-lookup"><span data-stu-id="f0df6-124">The <xref:System.Windows.Controls.ContentControl> class contains a single piece of arbitrary content.</span></span> <span data-ttu-id="f0df6-125">İçerik özelliği olan <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="f0df6-125">Its content property is <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="f0df6-126">Aşağıdaki denetimleri devralınmalıdır <xref:System.Windows.Controls.ContentControl> ve kendi içerik modelini kullanır:</span><span class="sxs-lookup"><span data-stu-id="f0df6-126">The following controls inherit from <xref:System.Windows.Controls.ContentControl> and use its content model:</span></span>  
  
-   <xref:System.Windows.Controls.Button>  
  
-   <xref:System.Windows.Controls.Primitives.ButtonBase>  
  
-   <xref:System.Windows.Controls.CheckBox>  
  
-   <xref:System.Windows.Controls.ComboBoxItem>  
  
-   <xref:System.Windows.Controls.ContentControl>  
  
-   <xref:System.Windows.Controls.Frame>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeader>  
  
-   <xref:System.Windows.Controls.GroupItem>  
  
-   <xref:System.Windows.Controls.Label>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.ListViewItem>  
  
-   <xref:System.Windows.Navigation.NavigationWindow>  
  
-   <xref:System.Windows.Controls.RadioButton>  
  
-   <xref:System.Windows.Controls.Primitives.RepeatButton>  
  
-   <xref:System.Windows.Controls.ScrollViewer>  
  
-   <xref:System.Windows.Controls.Primitives.StatusBarItem>  
  
-   <xref:System.Windows.Controls.Primitives.ToggleButton>  
  
-   <xref:System.Windows.Controls.ToolTip>  
  
-   <xref:System.Windows.Controls.UserControl>  
  
-   <xref:System.Windows.Window>  
  
 <span data-ttu-id="f0df6-127">Aşağıdaki çizimde gösterildiği dört düğmeleri <xref:System.Windows.Controls.ContentControl.Content%2A> bir dizeye ayarlayın bir <xref:System.DateTime> nesne, bir <xref:System.Windows.Shapes.Rectangle>ve bir <xref:System.Windows.Controls.Panel> içeren bir <xref:System.Windows.Shapes.Ellipse> ve <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="f0df6-127">The following illustration shows four buttons whose <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a string, a <xref:System.DateTime> object, a <xref:System.Windows.Shapes.Rectangle>, and a <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 <span data-ttu-id="f0df6-128">![Dört düğme](../../../../docs/framework/wpf/controls/media/controlcontentmodelbuttons.PNG "ControlContentModelButtons")</span><span class="sxs-lookup"><span data-stu-id="f0df6-128">![Four buttons](../../../../docs/framework/wpf/controls/media/controlcontentmodelbuttons.PNG "ControlContentModelButtons")</span></span>  
<span data-ttu-id="f0df6-129">Farklı türde içerik sahibi olan dört düğmeleri</span><span class="sxs-lookup"><span data-stu-id="f0df6-129">Four buttons that have different types of content</span></span>  
  
 <span data-ttu-id="f0df6-130">Bir örnek için nasıl ayarlanacağı <xref:System.Windows.Controls.ContentControl.Content%2A> özelliği, bkz: <xref:System.Windows.Controls.ContentControl>.</span><span class="sxs-lookup"><span data-stu-id="f0df6-130">For an example of how to set the <xref:System.Windows.Controls.ContentControl.Content%2A> property, see <xref:System.Windows.Controls.ContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a><span data-ttu-id="f0df6-131">Üstbilgi ve tek bir rasgele nesne içeren denetimler</span><span class="sxs-lookup"><span data-stu-id="f0df6-131">Controls That Contain a Header and a Single Arbitrary Object</span></span>  
 <span data-ttu-id="f0df6-132"><xref:System.Windows.Controls.HeaderedContentControl> Sınıfının devraldığı <xref:System.Windows.Controls.ContentControl> ve bir üstbilgiyle içeriğini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f0df6-132">The <xref:System.Windows.Controls.HeaderedContentControl> class inherits from <xref:System.Windows.Controls.ContentControl> and displays content with a header.</span></span> <span data-ttu-id="f0df6-133">İçerik özelliği devralır <xref:System.Windows.Controls.ContentControl.Content%2A>, gelen <xref:System.Windows.Controls.ContentControl> ve tanımlar <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> türü özelliği <xref:System.Object>; bu nedenle, her ikisi de rasgele bir nesne olabilir.</span><span class="sxs-lookup"><span data-stu-id="f0df6-133">It inherits the content property, <xref:System.Windows.Controls.ContentControl.Content%2A>, from <xref:System.Windows.Controls.ContentControl> and defines the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> property that is of type <xref:System.Object>; therefore, both can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="f0df6-134">Aşağıdaki denetimleri devralınmalıdır <xref:System.Windows.Controls.HeaderedContentControl> ve kendi içerik modelini kullanır:</span><span class="sxs-lookup"><span data-stu-id="f0df6-134">The following controls inherit from <xref:System.Windows.Controls.HeaderedContentControl> and use its content model:</span></span>  
  
-   <xref:System.Windows.Controls.Expander>  
  
-   <xref:System.Windows.Controls.GroupBox>  
  
-   <xref:System.Windows.Controls.TabItem>  
  
 <span data-ttu-id="f0df6-135">Aşağıdaki çizimde iki gösterir <xref:System.Windows.Controls.TabItem> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="f0df6-135">The following illustration shows two <xref:System.Windows.Controls.TabItem> objects.</span></span> <span data-ttu-id="f0df6-136">İlk <xref:System.Windows.Controls.TabItem> sahip <xref:System.Windows.UIElement> olarak nesneleri <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> ve <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="f0df6-136">The first <xref:System.Windows.Controls.TabItem> has <xref:System.Windows.UIElement> objects as the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="f0df6-137"><xref:System.Windows.Controls.HeaderedContentControl.Header%2A> Ayarlanmış bir <xref:System.Windows.Controls.StackPanel> içeren bir <xref:System.Windows.Shapes.Ellipse> ve <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="f0df6-137">The <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="f0df6-138"><xref:System.Windows.Controls.ContentControl.Content%2A> Ayarlanmış bir <xref:System.Windows.Controls.StackPanel> içeren bir <xref:System.Windows.Controls.TextBlock> ve <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="f0df6-138">The <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains a <xref:System.Windows.Controls.TextBlock> and a <xref:System.Windows.Controls.Label>.</span></span> <span data-ttu-id="f0df6-139">İkinci <xref:System.Windows.Controls.TabItem> bir dize olan <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> ve <xref:System.Windows.Controls.TextBlock> içinde <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="f0df6-139">The second <xref:System.Windows.Controls.TabItem> has a string in the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and a <xref:System.Windows.Controls.TextBlock> in the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span>  
  
 <span data-ttu-id="f0df6-140">![TabControl](../../../../docs/framework/wpf/controls/media/controlcontentmodelteabitem.PNG "ControlContentModelTeabItem")</span><span class="sxs-lookup"><span data-stu-id="f0df6-140">![TabControl](../../../../docs/framework/wpf/controls/media/controlcontentmodelteabitem.PNG "ControlContentModelTeabItem")</span></span>  
<span data-ttu-id="f0df6-141">Üstbilgi özelliğinde farklı türlerini kullanan TabControl</span><span class="sxs-lookup"><span data-stu-id="f0df6-141">TabControl that uses different types in the Header property</span></span>  
  
 <span data-ttu-id="f0df6-142">Bir örnek için nasıl oluşturulacağını <xref:System.Windows.Controls.TabItem> nesneleri bkz <xref:System.Windows.Controls.HeaderedContentControl>.</span><span class="sxs-lookup"><span data-stu-id="f0df6-142">For an example of how to create <xref:System.Windows.Controls.TabItem> objects, see <xref:System.Windows.Controls.HeaderedContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a><span data-ttu-id="f0df6-143">Rastgele nesne koleksiyonu içeren denetimler</span><span class="sxs-lookup"><span data-stu-id="f0df6-143">Controls That Contain a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="f0df6-144"><xref:System.Windows.Controls.ItemsControl> Sınıfının devraldığı <xref:System.Windows.Controls.Control> ve dize, nesneleri ve diğer öğeler gibi birden çok öğe içerebilir.</span><span class="sxs-lookup"><span data-stu-id="f0df6-144">The <xref:System.Windows.Controls.ItemsControl> class inherits from <xref:System.Windows.Controls.Control> and can contain multiple items, such as strings, objects, or other elements.</span></span> <span data-ttu-id="f0df6-145">İçerik özellikleri olan <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> ve <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span><span class="sxs-lookup"><span data-stu-id="f0df6-145">Its content properties are <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> and <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span></span> <span data-ttu-id="f0df6-146"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>genellikle doldurmak için kullanılan <xref:System.Windows.Controls.ItemsControl> veri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f0df6-146"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> is typically used to populate the <xref:System.Windows.Controls.ItemsControl> with a data collection.</span></span> <span data-ttu-id="f0df6-147">Doldurmak için bir koleksiyon kullanmak istemiyorsanız <xref:System.Windows.Controls.ItemsControl>, kullanarak öğeleri ekleyebilirsiniz <xref:System.Windows.Controls.ItemsControl.Items%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="f0df6-147">If you do not want to use a collection to populate the <xref:System.Windows.Controls.ItemsControl>, you can add items by using the <xref:System.Windows.Controls.ItemsControl.Items%2A> property.</span></span>  
  
 <span data-ttu-id="f0df6-148">Aşağıdaki denetimleri devralınmalıdır <xref:System.Windows.Controls.ItemsControl> ve kendi içerik modelini kullanır:</span><span class="sxs-lookup"><span data-stu-id="f0df6-148">The following controls inherit from <xref:System.Windows.Controls.ItemsControl> and use its content model:</span></span>  
  
-   <xref:System.Windows.Controls.Menu>  
  
-   <xref:System.Windows.Controls.Primitives.MenuBase>  
  
-   <xref:System.Windows.Controls.ContextMenu>  
  
-   <xref:System.Windows.Controls.ComboBox>  
  
-   <xref:System.Windows.Controls.ItemsControl>  
  
-   <xref:System.Windows.Controls.ListBox>  
  
-   <xref:System.Windows.Controls.ListView>  
  
-   <xref:System.Windows.Controls.TabControl>  
  
-   <xref:System.Windows.Controls.TreeView>  
  
-   <xref:System.Windows.Controls.Primitives.Selector>  
  
-   <xref:System.Windows.Controls.Primitives.StatusBar>  
  
 <span data-ttu-id="f0df6-149">Aşağıdaki çizimde gösterildiği bir <xref:System.Windows.Controls.ListBox> , bu tür öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="f0df6-149">The following illustration shows a <xref:System.Windows.Controls.ListBox> that contains these types of items:</span></span>  
  
-   <span data-ttu-id="f0df6-150">Bir dize.</span><span class="sxs-lookup"><span data-stu-id="f0df6-150">A string.</span></span>  
  
-   <span data-ttu-id="f0df6-151">A <xref:System.DateTime> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="f0df6-151">A <xref:System.DateTime> object.</span></span>  
  
-   <span data-ttu-id="f0df6-152">A <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="f0df6-152">A <xref:System.Windows.UIElement>.</span></span>  
  
-   <span data-ttu-id="f0df6-153">A <xref:System.Windows.Controls.Panel> içeren bir <xref:System.Windows.Shapes.Ellipse> ve <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="f0df6-153">A <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 <span data-ttu-id="f0df6-154">![Dört tür içerikle ListBox](../../../../docs/framework/wpf/controls/media/controlcontentmodellistbox2.PNG "ControlContentModelListBox2")</span><span class="sxs-lookup"><span data-stu-id="f0df6-154">![ListBox with four types of content](../../../../docs/framework/wpf/controls/media/controlcontentmodellistbox2.PNG "ControlContentModelListBox2")</span></span>  
<span data-ttu-id="f0df6-155">Birçok nesne türünü içeren ListBox</span><span class="sxs-lookup"><span data-stu-id="f0df6-155">ListBox that contains multiple types of objects</span></span>  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a><span data-ttu-id="f0df6-156">Üstbilgi ve rasgele nesneler koleksiyonunu içeren denetimler</span><span class="sxs-lookup"><span data-stu-id="f0df6-156">Controls That Contain a Header and a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="f0df6-157"><xref:System.Windows.Controls.HeaderedItemsControl> Sınıfının devraldığı <xref:System.Windows.Controls.ItemsControl> ve dizeler, nesneler veya diğer öğeleri ve bir üstbilgi gibi birden çok öğe içerebilir.</span><span class="sxs-lookup"><span data-stu-id="f0df6-157">The <xref:System.Windows.Controls.HeaderedItemsControl> class inherits from <xref:System.Windows.Controls.ItemsControl> and can contain multiple items, such as strings, objects, or other elements, and a header.</span></span> <span data-ttu-id="f0df6-158">Devralır <xref:System.Windows.Controls.ItemsControl> içerik özellikleri, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, ve <xref:System.Windows.Controls.ItemsControl.Items%2A>, ve tanımlar <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> rasgele bir nesne olabilir özelliği.</span><span class="sxs-lookup"><span data-stu-id="f0df6-158">It inherits the <xref:System.Windows.Controls.ItemsControl> content properties, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, and <xref:System.Windows.Controls.ItemsControl.Items%2A>, and it defines the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property that can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="f0df6-159">Aşağıdaki denetimleri devralınmalıdır <xref:System.Windows.Controls.HeaderedItemsControl> ve kendi içerik modelini kullanır:</span><span class="sxs-lookup"><span data-stu-id="f0df6-159">The following controls inherit from <xref:System.Windows.Controls.HeaderedItemsControl> and use its content model:</span></span>  
  
-   <xref:System.Windows.Controls.MenuItem>  
  
-   <xref:System.Windows.Controls.ToolBar>  
  
-   <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>   
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a><span data-ttu-id="f0df6-160">UIElement nesnelerinin bir koleksiyonunu içeren sınıflar</span><span class="sxs-lookup"><span data-stu-id="f0df6-160">Classes That Contain a Collection of UIElement Objects</span></span>  
 <span data-ttu-id="f0df6-161"><xref:System.Windows.Controls.Panel> Sınıfı yerleştirir ve alt düzenler <xref:System.Windows.UIElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="f0df6-161">The <xref:System.Windows.Controls.Panel> class positions and arranges child <xref:System.Windows.UIElement> objects.</span></span> <span data-ttu-id="f0df6-162">İçerik özelliği olan <xref:System.Windows.Controls.Panel.Children%2A>.</span><span class="sxs-lookup"><span data-stu-id="f0df6-162">Its content property is <xref:System.Windows.Controls.Panel.Children%2A>.</span></span>  
  
 <span data-ttu-id="f0df6-163">Aşağıdaki sınıflar devralınmalıdır <xref:System.Windows.Controls.Panel> sınıfı ve kendi içerik modelini kullanır:</span><span class="sxs-lookup"><span data-stu-id="f0df6-163">The following classes inherit from the <xref:System.Windows.Controls.Panel> class and use its content model:</span></span>  
  
-   <xref:System.Windows.Controls.Canvas>  
  
-   <xref:System.Windows.Controls.DockPanel>  
  
-   <xref:System.Windows.Controls.Grid>  
  
-   <xref:System.Windows.Controls.Primitives.TabPanel>  
  
-   <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
  
-   <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
  
-   <xref:System.Windows.Controls.Primitives.UniformGrid>  
  
-   <xref:System.Windows.Controls.StackPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
-   <xref:System.Windows.Controls.WrapPanel>  
  
 <span data-ttu-id="f0df6-164">Daha fazla bilgi için bkz: [paneller genel bakış](../../../../docs/framework/wpf/controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f0df6-164">For more information, see [Panels Overview](../../../../docs/framework/wpf/controls/panels-overview.md).</span></span>  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>   
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a><span data-ttu-id="f0df6-165">UIElement görünümünü etkileyen sınıfları</span><span class="sxs-lookup"><span data-stu-id="f0df6-165">Classes That Affect the Appearance of a UIElement</span></span>  
 <span data-ttu-id="f0df6-166"><xref:System.Windows.Controls.Decorator> Sınıfı uygulanır görsel efektler üzerine veya tek bir alt etrafında <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="f0df6-166">The <xref:System.Windows.Controls.Decorator> class applies visual effects onto or around a single child <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="f0df6-167">İçerik özelliği olan <xref:System.Windows.Controls.Decorator.Child%2A>.</span><span class="sxs-lookup"><span data-stu-id="f0df6-167">Its content property is <xref:System.Windows.Controls.Decorator.Child%2A>.</span></span> <span data-ttu-id="f0df6-168">Aşağıdaki sınıflar devralınmalıdır <xref:System.Windows.Controls.Decorator> ve kendi içerik modelini kullanır:</span><span class="sxs-lookup"><span data-stu-id="f0df6-168">The following classes inherit from <xref:System.Windows.Controls.Decorator> and use its content model:</span></span>  
  
-   <xref:System.Windows.Documents.AdornerDecorator>  
  
-   <xref:System.Windows.Controls.Border>  
  
-   <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
-   <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
-   <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
-   <xref:System.Windows.Controls.InkPresenter>  
  
-   <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
-   <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
-   <xref:System.Windows.Controls.Viewbox>  
  
 <span data-ttu-id="f0df6-169">Aşağıdaki çizimde gösterildiği bir <xref:System.Windows.Controls.TextBox> olan (ile donatılmış) bir <xref:System.Windows.Controls.Border> çevresinde.</span><span class="sxs-lookup"><span data-stu-id="f0df6-169">The following illustration shows a <xref:System.Windows.Controls.TextBox> that has (is decorated with) a <xref:System.Windows.Controls.Border> around it.</span></span>  
  
 <span data-ttu-id="f0df6-170">![Siyah kenarlık kutusuyla](../../../../docs/framework/wpf/controls/media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span><span class="sxs-lookup"><span data-stu-id="f0df6-170">![TextBox with black border](../../../../docs/framework/wpf/controls/media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span></span>  
<span data-ttu-id="f0df6-171">Kenarlığı olan TextBlock</span><span class="sxs-lookup"><span data-stu-id="f0df6-171">TextBlock that has a Border</span></span>  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>   
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a><span data-ttu-id="f0df6-172">UIElement hakkında görsel geribildirim sağlamak sınıfları</span><span class="sxs-lookup"><span data-stu-id="f0df6-172">Classes That Provide Visual Feedback About a UIElement</span></span>  
 <span data-ttu-id="f0df6-173"><xref:System.Windows.Documents.Adorner> Sınıfı, bir kullanıcı için görsel ipuçları sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0df6-173">The <xref:System.Windows.Documents.Adorner> class provides visual cues to a user.</span></span> <span data-ttu-id="f0df6-174">Örneğin, bir <xref:System.Windows.Documents.Adorner> işlevsel tanıtıcıları öğelere eklemek ya da bir denetimi hakkındaki durum bilgilerini sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="f0df6-174">For example, use an <xref:System.Windows.Documents.Adorner> to add functional handles to elements or provide state information about a control.</span></span> <span data-ttu-id="f0df6-175"><xref:System.Windows.Documents.Adorner> Sınıfı, kendi donatıcılarınızı oluşturabilmesi için bir çerçeve sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0df6-175">The <xref:System.Windows.Documents.Adorner> class provides a framework so that you can create your own adorners.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="f0df6-176">hiçbir uygulanmış donatıcı sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="f0df6-176"> does not provide any implemented adorners.</span></span> <span data-ttu-id="f0df6-177">Daha fazla bilgi için bkz: [Donatıcılara Genel Bakış](../../../../docs/framework/wpf/controls/adorners-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f0df6-177">For more information, see [Adorners Overview](../../../../docs/framework/wpf/controls/adorners-overview.md).</span></span>  
  
<a name="classes_that_enable_users_to_enter_text"></a>   
## <a name="classes-that-enable-users-to-enter-text"></a><span data-ttu-id="f0df6-178">Kullanıcıların metin girmesini sağlayan sınıflar</span><span class="sxs-lookup"><span data-stu-id="f0df6-178">Classes That Enable Users to Enter Text</span></span>  
 <span data-ttu-id="f0df6-179">WPF metin girmesini sağlayan üç birincil denetimleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0df6-179">WPF provides three primary controls that enable users to enter text.</span></span> <span data-ttu-id="f0df6-180">Her denetim metni farklı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f0df6-180">Each control displays the text differently.</span></span> <span data-ttu-id="f0df6-181">Aşağıdaki tabloda, bu üç metin ile ilişkili denetimleri, metin ve denetimin metnini içeren özelliklerini görüntülediğinizde yeteneklerini listeler.</span><span class="sxs-lookup"><span data-stu-id="f0df6-181">The following table lists these three text-related controls, their capabilities when they display text, and their properties that contain the control's text.</span></span>  
  
|<span data-ttu-id="f0df6-182">Denetim</span><span class="sxs-lookup"><span data-stu-id="f0df6-182">Control</span></span>|<span data-ttu-id="f0df6-183">Metin olarak görüntülenir</span><span class="sxs-lookup"><span data-stu-id="f0df6-183">Text is displayed as</span></span>|<span data-ttu-id="f0df6-184">İçerik özelliği</span><span class="sxs-lookup"><span data-stu-id="f0df6-184">Content property</span></span>|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|<span data-ttu-id="f0df6-185">Düz metin</span><span class="sxs-lookup"><span data-stu-id="f0df6-185">Plain text</span></span>|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|<span data-ttu-id="f0df6-186">Biçimlendirilmiş metin</span><span class="sxs-lookup"><span data-stu-id="f0df6-186">Formatted text</span></span>|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|<span data-ttu-id="f0df6-187">Gizli metin (karakterler maskelenir)</span><span class="sxs-lookup"><span data-stu-id="f0df6-187">Hidden text (characters are masked)</span></span>|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>   
## <a name="classes-that-display-your-text"></a><span data-ttu-id="f0df6-188">Metninizi görüntülemek sınıfları</span><span class="sxs-lookup"><span data-stu-id="f0df6-188">Classes That Display Your Text</span></span>  
 <span data-ttu-id="f0df6-189">Birden fazla sınıf düz veya biçimlendirilmiş metni görüntülemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f0df6-189">Several classes can be used to display plain or formatted text.</span></span> <span data-ttu-id="f0df6-190">Kullanabileceğiniz <xref:System.Windows.Controls.TextBlock> küçük miktarda metin görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="f0df6-190">You can use <xref:System.Windows.Controls.TextBlock> to display small amounts of text.</span></span> <span data-ttu-id="f0df6-191">Büyük miktarda metin görüntülemek istiyorsanız, kullanmak <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, veya <xref:System.Windows.Controls.FlowDocumentScrollViewer> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="f0df6-191">If you want to display large amounts of text, use the <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, or <xref:System.Windows.Controls.FlowDocumentScrollViewer> controls.</span></span>  
  
 <span data-ttu-id="f0df6-192"><xref:System.Windows.Controls.TextBlock> İki içerik özelliği vardır: <xref:System.Windows.Controls.TextBlock.Text%2A> ve <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span><span class="sxs-lookup"><span data-stu-id="f0df6-192">The <xref:System.Windows.Controls.TextBlock> has two content properties: <xref:System.Windows.Controls.TextBlock.Text%2A> and <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span></span> <span data-ttu-id="f0df6-193">Tutarlı biçimlendirme kullanan metni görüntülemek istediğinizde <xref:System.Windows.Controls.TextBlock.Text%2A> özelliktir genellikle en iyi seçimdir.</span><span class="sxs-lookup"><span data-stu-id="f0df6-193">When you want to display text that uses consistent formatting, the <xref:System.Windows.Controls.TextBlock.Text%2A> property is often your best choice.</span></span> <span data-ttu-id="f0df6-194">Metnin tamamında farklı biçimlendirme kullanmayı planlıyorsanız, kullanmak <xref:System.Windows.Controls.TextBlock.Inlines%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="f0df6-194">If you plan to use different formatting throughout the text, use the <xref:System.Windows.Controls.TextBlock.Inlines%2A> property.</span></span> <span data-ttu-id="f0df6-195"><xref:System.Windows.Controls.TextBlock.Inlines%2A> Özelliktir koleksiyonu <xref:System.Windows.Documents.Inline> metnin nasıl biçimlendirileceğini belirtin nesneleri.</span><span class="sxs-lookup"><span data-stu-id="f0df6-195">The <xref:System.Windows.Controls.TextBlock.Inlines%2A> property is a collection of <xref:System.Windows.Documents.Inline> objects, which specify how to format text.</span></span>  
  
 <span data-ttu-id="f0df6-196">İçerik özelliği için aşağıdaki tabloda listelenmektedir <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, ve <xref:System.Windows.Controls.FlowDocumentScrollViewer> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="f0df6-196">The following table lists the content property for <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, and <xref:System.Windows.Controls.FlowDocumentScrollViewer> classes.</span></span>  
  
|<span data-ttu-id="f0df6-197">Denetim</span><span class="sxs-lookup"><span data-stu-id="f0df6-197">Control</span></span>|<span data-ttu-id="f0df6-198">İçerik özelliği</span><span class="sxs-lookup"><span data-stu-id="f0df6-198">Content property</span></span>|<span data-ttu-id="f0df6-199">İçerik özelliği türü</span><span class="sxs-lookup"><span data-stu-id="f0df6-199">Content property type</span></span>|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|<span data-ttu-id="f0df6-200">Belge</span><span class="sxs-lookup"><span data-stu-id="f0df6-200">Document</span></span>|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|<span data-ttu-id="f0df6-201">Belge</span><span class="sxs-lookup"><span data-stu-id="f0df6-201">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|<span data-ttu-id="f0df6-202">Belge</span><span class="sxs-lookup"><span data-stu-id="f0df6-202">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
  
 <span data-ttu-id="f0df6-203"><xref:System.Windows.Documents.FlowDocument> Uygulayan <xref:System.Windows.Documents.IDocumentPaginatorSource> arabirim; bu nedenle, tüm üç sınıf gerçekleştirebilir bir <xref:System.Windows.Documents.FlowDocument> içeriği.</span><span class="sxs-lookup"><span data-stu-id="f0df6-203">The <xref:System.Windows.Documents.FlowDocument> implements the <xref:System.Windows.Documents.IDocumentPaginatorSource> interface; therefore, all three classes can take a <xref:System.Windows.Documents.FlowDocument> as content.</span></span>  
  
<a name="classes_that_format_text"></a>   
## <a name="classes-that-format-your-text"></a><span data-ttu-id="f0df6-204">Metni Biçimlendir sınıfları</span><span class="sxs-lookup"><span data-stu-id="f0df6-204">Classes That Format Your Text</span></span>  
 <span data-ttu-id="f0df6-205"><xref:System.Windows.Documents.TextElement>ve metin biçimlendirmek, ilgili sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0df6-205"><xref:System.Windows.Documents.TextElement> and its related classes allow you to format text.</span></span> <span data-ttu-id="f0df6-206"><xref:System.Windows.Documents.TextElement>nesneleri içeren ve biçimlendirme metinde <xref:System.Windows.Controls.TextBlock> ve <xref:System.Windows.Documents.FlowDocument> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="f0df6-206"><xref:System.Windows.Documents.TextElement> objects contain and format text in <xref:System.Windows.Controls.TextBlock> and <xref:System.Windows.Documents.FlowDocument> objects.</span></span> <span data-ttu-id="f0df6-207">İki birincil tür <xref:System.Windows.Documents.TextElement> nesneler <xref:System.Windows.Documents.Block> öğeleri ve <xref:System.Windows.Documents.Inline> öğeleri.</span><span class="sxs-lookup"><span data-stu-id="f0df6-207">The two primary types of <xref:System.Windows.Documents.TextElement> objects are <xref:System.Windows.Documents.Block> elements and <xref:System.Windows.Documents.Inline> elements.</span></span> <span data-ttu-id="f0df6-208">A <xref:System.Windows.Documents.Block> öğesi, paragraf veya liste gibi bir metin bloğunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f0df6-208">A <xref:System.Windows.Documents.Block> element represents a block of text, such as a paragraph or list.</span></span> <span data-ttu-id="f0df6-209">Bir <xref:System.Windows.Documents.Inline> öğesi blok içindeki metnin bir bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f0df6-209">An <xref:System.Windows.Documents.Inline> element represents a portion of text in a block.</span></span> <span data-ttu-id="f0df6-210">Birçok <xref:System.Windows.Documents.Inline> sınıfları belirtmek için bunlar uygulanma metin için biçimlendirme.</span><span class="sxs-lookup"><span data-stu-id="f0df6-210">Many <xref:System.Windows.Documents.Inline> classes specify formatting for the text to which they are applied.</span></span> <span data-ttu-id="f0df6-211">Her <xref:System.Windows.Documents.TextElement> kendi içerik modeli vardır.</span><span class="sxs-lookup"><span data-stu-id="f0df6-211">Each <xref:System.Windows.Documents.TextElement> has its own content model.</span></span> <span data-ttu-id="f0df6-212">Daha fazla bilgi için bkz: [TextElement içerik modeli genel bakış](../../../../docs/framework/wpf/advanced/textelement-content-model-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f0df6-212">For more information, see the [TextElement Content Model Overview](../../../../docs/framework/wpf/advanced/textelement-content-model-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0df6-213">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f0df6-213">See Also</span></span>  
 [<span data-ttu-id="f0df6-214">Gelişmiş</span><span class="sxs-lookup"><span data-stu-id="f0df6-214">Advanced</span></span>](../../../../docs/framework/wpf/advanced/index.md)
