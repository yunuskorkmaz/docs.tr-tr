---
title: "Nasıl yapılır: DataGrid Denetimine Satır Ayrıntıları Ekleme"
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
- DataTemplate [WPF], DataGrid
- row details [WPF], DataGrid
- DataGrid [WPF], row details
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f65eb9e916fad83deb1476c1d8f0def4981d08d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a><span data-ttu-id="3a85f-102">Nasıl yapılır: DataGrid Denetimine Satır Ayrıntıları Ekleme</span><span class="sxs-lookup"><span data-stu-id="3a85f-102">How to: Add Row Details to a DataGrid Control</span></span>
<span data-ttu-id="3a85f-103">Kullanırken <xref:System.Windows.Controls.DataGrid> denetimi, bir satır ayrıntıları bölümü ekleyerek veri sunumunu özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a85f-103">When using the <xref:System.Windows.Controls.DataGrid> control, you can customize the data presentation by adding a row details section.</span></span> <span data-ttu-id="3a85f-104">Bir sıra ayrıntıları bölümü ekleyerek, bazı veriler, isteğe bağlı olarak görünür mü yoksa daraltılmış olan bir şablon gruplamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a85f-104">Adding a row details section enables you to group some data in a template that is optionally visible or collapsed.</span></span> <span data-ttu-id="3a85f-105">Örneğin, satır ayrıntıları ekleyebilirsiniz bir <xref:System.Windows.Controls.DataGrid> her satır için verileri yalnızca bir özetini sunar <xref:System.Windows.Controls.DataGrid>, ancak daha fazla veri alanı kullanıcı bir satır seçtiğinde gösterir.</span><span class="sxs-lookup"><span data-stu-id="3a85f-105">For example, you can add row details to a <xref:System.Windows.Controls.DataGrid> that presents only a summary of the data for each row in the <xref:System.Windows.Controls.DataGrid>, but presents more data fields when the user selects a row.</span></span> <span data-ttu-id="3a85f-106">Şablon için satır Ayrıntılar bölümünde tanımladığınız <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="3a85f-106">You define the template for the row details section in the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property.</span></span> <span data-ttu-id="3a85f-107">Aşağıdaki çizimde bir satır ayrıntıları bölümü örneği gösterir.</span><span class="sxs-lookup"><span data-stu-id="3a85f-107">The following illustration shows an example of a row details section.</span></span>  
  
 <span data-ttu-id="3a85f-108">![Satır ayrıntılarıyla gösterilen DataGrid](../../../../docs/framework/wpf/controls/media/ndp-rowdetails.png "NDP_RowDetails")</span><span class="sxs-lookup"><span data-stu-id="3a85f-108">![DataGrid shown with row details](../../../../docs/framework/wpf/controls/media/ndp-rowdetails.png "NDP_RowDetails")</span></span>  
  
 <span data-ttu-id="3a85f-109">Sıra ayrıntıları şablonunu ya da satır içi XAML veya bir kaynak olarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="3a85f-109">You define the row details template as either inline XAML or as a resource.</span></span> <span data-ttu-id="3a85f-110">Her iki yaklaşımın aşağıdaki yordamlarda gösterilir.</span><span class="sxs-lookup"><span data-stu-id="3a85f-110">Both approaches are shown in the following procedures.</span></span> <span data-ttu-id="3a85f-111">Bir kaynak olarak eklenen veri şablonu proje boyunca şablonu yeniden oluşturmaya gerek kalmadan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3a85f-111">A data template that is added as a resource can be used throughout the project without re-creating the template.</span></span> <span data-ttu-id="3a85f-112">Satır içi olarak eklenen veri şablonu XAML yalnızca tanımlandığı denetimden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="3a85f-112">A data template that is added as inline XAML is only accessible from the control where it is defined.</span></span>  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a><span data-ttu-id="3a85f-113">Satır içi XAML kullanarak satır ayrıntıları görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="3a85f-113">To display row details by using inline XAML</span></span>  
  
1.  <span data-ttu-id="3a85f-114">Oluşturma bir <xref:System.Windows.Controls.DataGrid> bir veri kaynağından görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3a85f-114">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2.  <span data-ttu-id="3a85f-115">İçinde <xref:System.Windows.Controls.DataGrid> öğesi ekleme bir <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> öğesi.</span><span class="sxs-lookup"><span data-stu-id="3a85f-115">In the <xref:System.Windows.Controls.DataGrid> element, add a <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> element.</span></span>  
  
3.  <span data-ttu-id="3a85f-116">Oluşturma bir <xref:System.Windows.DataTemplate> satır ayrıntıları bölümü görünümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3a85f-116">Create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="3a85f-117">Aşağıdaki XAML gösterildiği <xref:System.Windows.Controls.DataGrid> ve nasıl tanımlanacağını <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> satır içi.</span><span class="sxs-lookup"><span data-stu-id="3a85f-117">The following XAML shows the <xref:System.Windows.Controls.DataGrid> and how to define the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> inline.</span></span> <span data-ttu-id="3a85f-118"><xref:System.Windows.Controls.DataGrid> Görüntüler üç değerleri her satır, üç daha fazla değer satır seçili olduğunda.</span><span class="sxs-lookup"><span data-stu-id="3a85f-118">The <xref:System.Windows.Controls.DataGrid> displays three values in each row and three more values when the row is selected.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     <span data-ttu-id="3a85f-119">Aşağıdaki kod görüntülenen verileri seçmek için kullanılan sorgu gösterir <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="3a85f-119">The following code shows the query that is used to select the data that is displayed in the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="3a85f-120">Bu örnekte sorgu müşteri bilgilerini içeren bir varlık veri seçer.</span><span class="sxs-lookup"><span data-stu-id="3a85f-120">In this example, the query selects data from an entity that contains customer information.</span></span>  
  
     [!code-csharp[DataGrid_RowDetails#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a><span data-ttu-id="3a85f-121">Bir kaynağı kullanarak satır ayrıntıları görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="3a85f-121">To display row details by using a resource</span></span>  
  
1.  <span data-ttu-id="3a85f-122">Oluşturma bir <xref:System.Windows.Controls.DataGrid> bir veri kaynağından görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3a85f-122">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2.  <span data-ttu-id="3a85f-123">Ekleme bir <xref:System.Windows.FrameworkElement.Resources%2A> öğesi kök öğesi için gibi bir <xref:System.Windows.Window> denetim veya <xref:System.Windows.Controls.Page> denetlemek veya ekleme bir <xref:System.Windows.Application.Resources%2A> öğesine <xref:System.Windows.Application> App.xaml (veya Application.xaml) dosyasındaki sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3a85f-123">Add a <xref:System.Windows.FrameworkElement.Resources%2A> element to the root element, such as a <xref:System.Windows.Window> control or a <xref:System.Windows.Controls.Page> control, or add a <xref:System.Windows.Application.Resources%2A> element to the <xref:System.Windows.Application> class in the App.xaml (or Application.xaml) file.</span></span>  
  
3.  <span data-ttu-id="3a85f-124">Kaynaklar öğesinde oluşturma bir <xref:System.Windows.DataTemplate> satır ayrıntıları bölümü görünümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3a85f-124">In the resources element, create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="3a85f-125">Aşağıdaki XAML gösterildiği <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> tanımlanan <xref:System.Windows.Application> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3a85f-125">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> defined in the <xref:System.Windows.Application> class.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4.  <span data-ttu-id="3a85f-126">Üzerinde <xref:System.Windows.DataTemplate>ayarlayın [x: Key yönergesi](../../../../docs/framework/xaml-services/x-key-directive.md) veri şablonunu benzersiz olarak tanımlayan bir değer.</span><span class="sxs-lookup"><span data-stu-id="3a85f-126">On the <xref:System.Windows.DataTemplate>, set the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) to a value that uniquely identifies the data template.</span></span>  
  
5.  <span data-ttu-id="3a85f-127">İçinde <xref:System.Windows.Controls.DataGrid> öğe, ayarladığınız <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> önceki adımlarda tanımlanan kaynağa özelliği.</span><span class="sxs-lookup"><span data-stu-id="3a85f-127">In the <xref:System.Windows.Controls.DataGrid> element, set the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property to the resource defined in the previous steps.</span></span> <span data-ttu-id="3a85f-128">Kaynak statik bir kaynak olarak atayın.</span><span class="sxs-lookup"><span data-stu-id="3a85f-128">Assign the resource as a static resource.</span></span>  
  
     <span data-ttu-id="3a85f-129">Aşağıdaki XAML gösterildiği <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> önceki örnekten kaynağa nasıl ayarlanacağını özelliği.</span><span class="sxs-lookup"><span data-stu-id="3a85f-129">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property set to the resource from the previous example.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a><span data-ttu-id="3a85f-130">Görünürlüğü ayarlamak ve yatay satır ayrıntılarını kaydırmayı önlemek için</span><span class="sxs-lookup"><span data-stu-id="3a85f-130">To set visibility and prevent horizontal scrolling for row details</span></span>  
  
1.  <span data-ttu-id="3a85f-131">Gerekirse, ayarlayın <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> özelliğine bir <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> değeri.</span><span class="sxs-lookup"><span data-stu-id="3a85f-131">If needed, set the <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> property to a <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> value.</span></span>  
  
     <span data-ttu-id="3a85f-132">Varsayılan değer ayarlamak <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>.</span><span class="sxs-lookup"><span data-stu-id="3a85f-132">By default, the value is set to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>.</span></span> <span data-ttu-id="3a85f-133">Ayarlayabilirsiniz <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> tüm satırların ayrıntılarını göstermek için veya <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> tüm satırların ayrıntılarını gizlemek için.</span><span class="sxs-lookup"><span data-stu-id="3a85f-133">You can set it to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> to show the details for all of the rows or <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> to hide the details for all rows.</span></span>  
  
2.  <span data-ttu-id="3a85f-134">Gerekirse, ayarlayın <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> özelliğine `true` satır önlemek için yatay olarak kaymasını bölüm ayrıntıları.</span><span class="sxs-lookup"><span data-stu-id="3a85f-134">If needed, set the <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> property to `true` to prevent the row details section from scrolling horizontally.</span></span>
