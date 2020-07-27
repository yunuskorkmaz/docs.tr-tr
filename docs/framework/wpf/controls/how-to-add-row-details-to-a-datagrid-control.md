---
title: 'Nasıl yapılır: DataGrid Denetimine Satır Ayrıntıları Ekleme'
description: Bir satır ayrıntıları bölümü ekleyerek Windows Presentation Foundation DataGrid denetimini kullanırken veri sunumunu özelleştirmeyi öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataTemplate [WPF], DataGrid
- row details [WPF], DataGrid
- DataGrid [WPF], row details
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
ms.openlocfilehash: 8fd6b07f454681a0eed70d7a6208cfcc426dc920
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164955"
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a><span data-ttu-id="674eb-103">Nasıl yapılır: DataGrid Denetimine Satır Ayrıntıları Ekleme</span><span class="sxs-lookup"><span data-stu-id="674eb-103">How to: Add Row Details to a DataGrid Control</span></span>
<span data-ttu-id="674eb-104"><xref:System.Windows.Controls.DataGrid>Denetimi kullanırken, bir satır ayrıntıları bölümü ekleyerek veri sunumunu özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="674eb-104">When using the <xref:System.Windows.Controls.DataGrid> control, you can customize the data presentation by adding a row details section.</span></span> <span data-ttu-id="674eb-105">Satır ayrıntıları bölümü eklemek, bazı verileri isteğe bağlı olarak görünür veya daraltılmış bir şablonda gruplandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="674eb-105">Adding a row details section enables you to group some data in a template that is optionally visible or collapsed.</span></span> <span data-ttu-id="674eb-106">Örneğin, <xref:System.Windows.Controls.DataGrid> yalnızca içindeki her bir satır için verilerin bir özetini sunan öğesine satır ayrıntıları ekleyebilirsiniz <xref:System.Windows.Controls.DataGrid> , ancak kullanıcı bir satır seçtiğinde daha fazla veri alanı sunar.</span><span class="sxs-lookup"><span data-stu-id="674eb-106">For example, you can add row details to a <xref:System.Windows.Controls.DataGrid> that presents only a summary of the data for each row in the <xref:System.Windows.Controls.DataGrid>, but presents more data fields when the user selects a row.</span></span> <span data-ttu-id="674eb-107">Özelliği içindeki satır ayrıntıları bölümünün şablonunu tanımlarsınız <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> .</span><span class="sxs-lookup"><span data-stu-id="674eb-107">You define the template for the row details section in the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property.</span></span> <span data-ttu-id="674eb-108">Aşağıdaki çizimde, bir satır ayrıntıları Bölümü örneği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="674eb-108">The following illustration shows an example of a row details section.</span></span>  
  
 <span data-ttu-id="674eb-109">![Satır ayrıntılarıyla gösterilen DataGrid](./media/ndp-rowdetails.png "NDP_RowDetails")</span><span class="sxs-lookup"><span data-stu-id="674eb-109">![DataGrid shown with row details](./media/ndp-rowdetails.png "NDP_RowDetails")</span></span>  
  
 <span data-ttu-id="674eb-110">Satır ayrıntıları şablonunu satır içi XAML veya kaynak olarak tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="674eb-110">You define the row details template as either inline XAML or as a resource.</span></span> <span data-ttu-id="674eb-111">Aşağıdaki yordamlarda her iki yaklaşım da gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="674eb-111">Both approaches are shown in the following procedures.</span></span> <span data-ttu-id="674eb-112">Kaynak olarak eklenen bir veri şablonu, şablonu yeniden oluşturmadan proje genelinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="674eb-112">A data template that is added as a resource can be used throughout the project without re-creating the template.</span></span> <span data-ttu-id="674eb-113">Satır içi XAML olarak eklenen bir veri şablonuna yalnızca tanımlandığı denetimden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="674eb-113">A data template that is added as inline XAML is only accessible from the control where it is defined.</span></span>  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a><span data-ttu-id="674eb-114">Satır içi XAML kullanarak satır ayrıntılarını görüntüleme</span><span class="sxs-lookup"><span data-stu-id="674eb-114">To display row details by using inline XAML</span></span>  
  
1. <span data-ttu-id="674eb-115"><xref:System.Windows.Controls.DataGrid>Bir veri kaynağından verileri görüntüleyen bir oluştur.</span><span class="sxs-lookup"><span data-stu-id="674eb-115">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2. <span data-ttu-id="674eb-116"><xref:System.Windows.Controls.DataGrid>Öğesinde, bir <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="674eb-116">In the <xref:System.Windows.Controls.DataGrid> element, add a <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> element.</span></span>  
  
3. <span data-ttu-id="674eb-117"><xref:System.Windows.DataTemplate>Satır ayrıntıları bölümünün görünümünü tanımlayan bir oluştur.</span><span class="sxs-lookup"><span data-stu-id="674eb-117">Create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="674eb-118">Aşağıdaki XAML, <xref:System.Windows.Controls.DataGrid> ve satır içi 'nin nasıl tanımlanacağını gösterir <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> .</span><span class="sxs-lookup"><span data-stu-id="674eb-118">The following XAML shows the <xref:System.Windows.Controls.DataGrid> and how to define the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> inline.</span></span> <span data-ttu-id="674eb-119"><xref:System.Windows.Controls.DataGrid>Her satırda üç değer ve satır seçildiğinde üç daha fazla değer görüntüler.</span><span class="sxs-lookup"><span data-stu-id="674eb-119">The <xref:System.Windows.Controls.DataGrid> displays three values in each row and three more values when the row is selected.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#1](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     <span data-ttu-id="674eb-120">Aşağıdaki kod, içinde görüntülenen verileri seçmek için kullanılan sorguyu gösterir <xref:System.Windows.Controls.DataGrid> .</span><span class="sxs-lookup"><span data-stu-id="674eb-120">The following code shows the query that is used to select the data that is displayed in the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="674eb-121">Bu örnekte sorgu, müşteri bilgilerini içeren bir varlıktan veri seçer.</span><span class="sxs-lookup"><span data-stu-id="674eb-121">In this example, the query selects data from an entity that contains customer information.</span></span>  
  
     [!code-csharp[DataGrid_RowDetails#2](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a><span data-ttu-id="674eb-122">Kaynak kullanarak satır ayrıntılarını görüntüleme</span><span class="sxs-lookup"><span data-stu-id="674eb-122">To display row details by using a resource</span></span>  
  
1. <span data-ttu-id="674eb-123"><xref:System.Windows.Controls.DataGrid>Bir veri kaynağından verileri görüntüleyen bir oluştur.</span><span class="sxs-lookup"><span data-stu-id="674eb-123">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2. <span data-ttu-id="674eb-124">Bir <xref:System.Windows.FrameworkElement.Resources%2A> Denetim veya denetim gibi kök öğeye bir öğe ekleyin <xref:System.Windows.Window> <xref:System.Windows.Controls.Page> veya <xref:System.Windows.Application.Resources%2A> <xref:System.Windows.Application> app. xaml (veya Application. xaml) dosyasındaki sınıfa bir öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="674eb-124">Add a <xref:System.Windows.FrameworkElement.Resources%2A> element to the root element, such as a <xref:System.Windows.Window> control or a <xref:System.Windows.Controls.Page> control, or add a <xref:System.Windows.Application.Resources%2A> element to the <xref:System.Windows.Application> class in the App.xaml (or Application.xaml) file.</span></span>  
  
3. <span data-ttu-id="674eb-125">Resources öğesinde, <xref:System.Windows.DataTemplate> satır ayrıntıları bölümünün görünümünü tanımlayan bir oluştur.</span><span class="sxs-lookup"><span data-stu-id="674eb-125">In the resources element, create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="674eb-126">Aşağıdaki XAML, <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> sınıfında tanımlanan öğesini gösterir <xref:System.Windows.Application> .</span><span class="sxs-lookup"><span data-stu-id="674eb-126">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> defined in the <xref:System.Windows.Application> class.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#3](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4. <span data-ttu-id="674eb-127">Üzerinde <xref:System.Windows.DataTemplate> , [X:Key yönergesini](../../../desktop-wpf/xaml-services/xkey-directive.md) veri şablonunu benzersiz bir şekilde tanımlayan bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="674eb-127">On the <xref:System.Windows.DataTemplate>, set the [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) to a value that uniquely identifies the data template.</span></span>  
  
5. <span data-ttu-id="674eb-128"><xref:System.Windows.Controls.DataGrid>Öğesinde, <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> özelliğini önceki adımlarda tanımlanan kaynak olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="674eb-128">In the <xref:System.Windows.Controls.DataGrid> element, set the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property to the resource defined in the previous steps.</span></span> <span data-ttu-id="674eb-129">Kaynağı bir statik kaynak olarak atayın.</span><span class="sxs-lookup"><span data-stu-id="674eb-129">Assign the resource as a static resource.</span></span>  
  
     <span data-ttu-id="674eb-130">Aşağıdaki XAML, <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> önceki örnekteki kaynak olarak ayarlanan özelliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="674eb-130">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property set to the resource from the previous example.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#4](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a><span data-ttu-id="674eb-131">Görünürlük ayarlamak ve satır ayrıntıları için yatay kaydırmayı engellemek için</span><span class="sxs-lookup"><span data-stu-id="674eb-131">To set visibility and prevent horizontal scrolling for row details</span></span>  
  
1. <span data-ttu-id="674eb-132">Gerekirse, <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> özelliği bir değer olarak ayarlayın <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> .</span><span class="sxs-lookup"><span data-stu-id="674eb-132">If needed, set the <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> property to a <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> value.</span></span>  
  
     <span data-ttu-id="674eb-133">Varsayılan olarak, değeri olarak ayarlanır <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected> .</span><span class="sxs-lookup"><span data-stu-id="674eb-133">By default, the value is set to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>.</span></span> <span data-ttu-id="674eb-134">Tüm <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> satırların ayrıntılarını gösterecek şekilde veya <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> tüm satırların ayrıntılarını gizleyecek şekilde ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="674eb-134">You can set it to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> to show the details for all of the rows or <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> to hide the details for all rows.</span></span>  
  
2. <span data-ttu-id="674eb-135">Gerekirse, <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> `true` satır ayrıntıları bölümünün yatay olarak kaymasını engellemek için özelliğini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="674eb-135">If needed, set the <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> property to `true` to prevent the row details section from scrolling horizontally.</span></span>
