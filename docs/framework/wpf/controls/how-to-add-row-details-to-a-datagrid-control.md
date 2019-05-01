---
title: 'Nasıl yapılır: DataGrid Denetimine Satır Ayrıntıları Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataTemplate [WPF], DataGrid
- row details [WPF], DataGrid
- DataGrid [WPF], row details
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
ms.openlocfilehash: d5b6539f3d379088528b9654861267988b6fc69b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61911407"
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a><span data-ttu-id="9a45f-102">Nasıl yapılır: DataGrid Denetimine Satır Ayrıntıları Ekleme</span><span class="sxs-lookup"><span data-stu-id="9a45f-102">How to: Add Row Details to a DataGrid Control</span></span>
<span data-ttu-id="9a45f-103">Kullanırken <xref:System.Windows.Controls.DataGrid> denetim, satır ayrıntılar bölümüne ekleyerek veri sunumu özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a45f-103">When using the <xref:System.Windows.Controls.DataGrid> control, you can customize the data presentation by adding a row details section.</span></span> <span data-ttu-id="9a45f-104">Satır ayrıntıları bölümü ekleyerek, bazı veriler, isteğe bağlı olarak görünür veya daraltılmış bir şablonu gruplamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="9a45f-104">Adding a row details section enables you to group some data in a template that is optionally visible or collapsed.</span></span> <span data-ttu-id="9a45f-105">Satır ayrıntıları ekleme gibi bir <xref:System.Windows.Controls.DataGrid> veri her satır için yalnızca bir özetini sunar <xref:System.Windows.Controls.DataGrid>, ancak kullanıcı bir satır seçtiğinde, daha fazla veri alanı sunar.</span><span class="sxs-lookup"><span data-stu-id="9a45f-105">For example, you can add row details to a <xref:System.Windows.Controls.DataGrid> that presents only a summary of the data for each row in the <xref:System.Windows.Controls.DataGrid>, but presents more data fields when the user selects a row.</span></span> <span data-ttu-id="9a45f-106">Şablon için satır Ayrıntılar bölümünde tanımladığınız <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="9a45f-106">You define the template for the row details section in the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property.</span></span> <span data-ttu-id="9a45f-107">Satır ayrıntıları bölümü bir örneği aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9a45f-107">The following illustration shows an example of a row details section.</span></span>  
  
 <span data-ttu-id="9a45f-108">![Satır ayrıntıları ile gösterilen DataGrid](./media/ndp-rowdetails.png "NDP_RowDetails")</span><span class="sxs-lookup"><span data-stu-id="9a45f-108">![DataGrid shown with row details](./media/ndp-rowdetails.png "NDP_RowDetails")</span></span>  
  
 <span data-ttu-id="9a45f-109">Satır ayrıntıları şablon satır içi XAML veya bir kaynak olarak tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a45f-109">You define the row details template as either inline XAML or as a resource.</span></span> <span data-ttu-id="9a45f-110">Aşağıdaki yordamlarda her iki yaklaşım gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9a45f-110">Both approaches are shown in the following procedures.</span></span> <span data-ttu-id="9a45f-111">Bir kaynak olarak eklenen veri şablonu şablonu yeniden oluşturmaya gerek kalmadan proje boyunca kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9a45f-111">A data template that is added as a resource can be used throughout the project without re-creating the template.</span></span> <span data-ttu-id="9a45f-112">Satır içi olarak eklenen veri şablonu XAML yalnızca tanımlandığı denetiminden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="9a45f-112">A data template that is added as inline XAML is only accessible from the control where it is defined.</span></span>  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a><span data-ttu-id="9a45f-113">Satır içi XAML kullanarak satır ayrıntıları görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="9a45f-113">To display row details by using inline XAML</span></span>  
  
1. <span data-ttu-id="9a45f-114">Oluşturma bir <xref:System.Windows.Controls.DataGrid> , bir veri kaynağındaki verileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9a45f-114">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2. <span data-ttu-id="9a45f-115">İçinde <xref:System.Windows.Controls.DataGrid> öğe, Ekle bir <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> öğesi.</span><span class="sxs-lookup"><span data-stu-id="9a45f-115">In the <xref:System.Windows.Controls.DataGrid> element, add a <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> element.</span></span>  
  
3. <span data-ttu-id="9a45f-116">Oluşturma bir <xref:System.Windows.DataTemplate> , satır ayrıntıları bölümü görünümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9a45f-116">Create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="9a45f-117">Aşağıdaki XAML gösterildiği <xref:System.Windows.Controls.DataGrid> ve nasıl tanımlanacağını <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> satır içi.</span><span class="sxs-lookup"><span data-stu-id="9a45f-117">The following XAML shows the <xref:System.Windows.Controls.DataGrid> and how to define the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> inline.</span></span> <span data-ttu-id="9a45f-118"><xref:System.Windows.Controls.DataGrid> Görüntüler üç değer her satır ve üç daha fazla değer satır seçildiğinde.</span><span class="sxs-lookup"><span data-stu-id="9a45f-118">The <xref:System.Windows.Controls.DataGrid> displays three values in each row and three more values when the row is selected.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#1](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     <span data-ttu-id="9a45f-119">Aşağıdaki kod görüntülenen verileri seçmek için kullanılan sorgu gösterir <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="9a45f-119">The following code shows the query that is used to select the data that is displayed in the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="9a45f-120">Bu örnekte sorgu, müşteri bilgilerini içeren bir varlıktan veri seçer.</span><span class="sxs-lookup"><span data-stu-id="9a45f-120">In this example, the query selects data from an entity that contains customer information.</span></span>  
  
     [!code-csharp[DataGrid_RowDetails#2](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a><span data-ttu-id="9a45f-121">Bir kaynağı kullanarak satır ayrıntıları görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="9a45f-121">To display row details by using a resource</span></span>  
  
1. <span data-ttu-id="9a45f-122">Oluşturma bir <xref:System.Windows.Controls.DataGrid> , bir veri kaynağındaki verileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9a45f-122">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2. <span data-ttu-id="9a45f-123">Ekleme bir <xref:System.Windows.FrameworkElement.Resources%2A> öğesi kök öğe gibi bir <xref:System.Windows.Window> denetim veya bir <xref:System.Windows.Controls.Page> denetlemek ya da ekleme bir <xref:System.Windows.Application.Resources%2A> öğesine <xref:System.Windows.Application> App.xaml (veya Application.xaml) dosyasında sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9a45f-123">Add a <xref:System.Windows.FrameworkElement.Resources%2A> element to the root element, such as a <xref:System.Windows.Window> control or a <xref:System.Windows.Controls.Page> control, or add a <xref:System.Windows.Application.Resources%2A> element to the <xref:System.Windows.Application> class in the App.xaml (or Application.xaml) file.</span></span>  
  
3. <span data-ttu-id="9a45f-124">Kaynaklar öğesinde oluşturma bir <xref:System.Windows.DataTemplate> , satır ayrıntıları bölümü görünümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9a45f-124">In the resources element, create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="9a45f-125">Aşağıdaki XAML gösterildiği <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> tanımlanan <xref:System.Windows.Application> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9a45f-125">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> defined in the <xref:System.Windows.Application> class.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#3](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4. <span data-ttu-id="9a45f-126">Üzerinde <xref:System.Windows.DataTemplate>ayarlayın [x: Key yönergesi](../../xaml-services/x-key-directive.md) için veri şablonunu benzersiz olarak tanımlayan bir değer.</span><span class="sxs-lookup"><span data-stu-id="9a45f-126">On the <xref:System.Windows.DataTemplate>, set the [x:Key Directive](../../xaml-services/x-key-directive.md) to a value that uniquely identifies the data template.</span></span>  
  
5. <span data-ttu-id="9a45f-127">İçinde <xref:System.Windows.Controls.DataGrid> öğe, ayarladığınız <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> önceki adımlarda tanımlanan kaynak için özellik.</span><span class="sxs-lookup"><span data-stu-id="9a45f-127">In the <xref:System.Windows.Controls.DataGrid> element, set the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property to the resource defined in the previous steps.</span></span> <span data-ttu-id="9a45f-128">Kaynak statik bir kaynak olarak atayın.</span><span class="sxs-lookup"><span data-stu-id="9a45f-128">Assign the resource as a static resource.</span></span>  
  
     <span data-ttu-id="9a45f-129">Aşağıdaki XAML gösterildiği <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> özelliği önceki örnekte kaynak olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9a45f-129">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property set to the resource from the previous example.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#4](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a><span data-ttu-id="9a45f-130">Görünürlük ve önlemek için satır ayrıntıları yatay kaydırma</span><span class="sxs-lookup"><span data-stu-id="9a45f-130">To set visibility and prevent horizontal scrolling for row details</span></span>  
  
1. <span data-ttu-id="9a45f-131">Gerekirse, ayarlama <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> özelliğini bir <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> değeri.</span><span class="sxs-lookup"><span data-stu-id="9a45f-131">If needed, set the <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> property to a <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> value.</span></span>  
  
     <span data-ttu-id="9a45f-132">Varsayılan olarak, değeri şuna ayarlı <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>.</span><span class="sxs-lookup"><span data-stu-id="9a45f-132">By default, the value is set to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>.</span></span> <span data-ttu-id="9a45f-133">Ayarlayabilirsiniz <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> tüm satırlar için ayrıntıları göstermek için veya <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> tüm satırları ayrıntılarını gizlemek için.</span><span class="sxs-lookup"><span data-stu-id="9a45f-133">You can set it to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> to show the details for all of the rows or <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> to hide the details for all rows.</span></span>  
  
2. <span data-ttu-id="9a45f-134">Gerekirse, ayarlama <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> özelliğini `true` ayrıntıları yatay kaydırma gelen bölüm satır önlemek için.</span><span class="sxs-lookup"><span data-stu-id="9a45f-134">If needed, set the <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> property to `true` to prevent the row details section from scrolling horizontally.</span></span>
