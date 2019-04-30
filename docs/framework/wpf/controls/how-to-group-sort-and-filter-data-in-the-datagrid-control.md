---
title: 'Nasıl yapılır: Gruplandırma, sıralama ve DataGrid denetiminde verileri filtreleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], sort
- DataGrid [WPF], group
- DataGrid [WPF], filter
ms.assetid: 03345e85-89e3-4aec-9ed0-3b80759df770
ms.openlocfilehash: 81fdb0a6d5602f612c55d7e790ca9a0fe56c144e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771102"
---
# <a name="how-to-group-sort-and-filter-data-in-the-datagrid-control"></a><span data-ttu-id="d821f-102">Nasıl yapılır: DataGrid denetiminde filtre verileri gruplandırma, sıralama ve</span><span class="sxs-lookup"><span data-stu-id="d821f-102">How to: Group, sort, and filter data in the DataGrid control</span></span>

<span data-ttu-id="d821f-103">Genellikle verileri görüntülemek için yararlı bir <xref:System.Windows.Controls.DataGrid> gruplandırma, sıralama ve filtreleme verileri tarafından farklı şekillerde.</span><span class="sxs-lookup"><span data-stu-id="d821f-103">It is often useful to view data in a <xref:System.Windows.Controls.DataGrid> in different ways by grouping, sorting, and filtering the data.</span></span> <span data-ttu-id="d821f-104">Grup, sıralama ve verileri filtrelemek için bir <xref:System.Windows.Controls.DataGrid>, kendisine bağlamak bir <xref:System.Windows.Data.CollectionView> , bu işlevleri destekler.</span><span class="sxs-lookup"><span data-stu-id="d821f-104">To group, sort, and filter the data in a <xref:System.Windows.Controls.DataGrid>, you bind it to a <xref:System.Windows.Data.CollectionView> that supports these functions.</span></span> <span data-ttu-id="d821f-105">Ardından verileri ile çalışabilirsiniz <xref:System.Windows.Data.CollectionView> temel kaynak verilerini etkilemeden.</span><span class="sxs-lookup"><span data-stu-id="d821f-105">You can then work with the data in the <xref:System.Windows.Data.CollectionView> without affecting the underlying source data.</span></span> <span data-ttu-id="d821f-106">Koleksiyon görünümü yapılan değişiklikler yansıtılır <xref:System.Windows.Controls.DataGrid> kullanıcı arabirimi (UI).</span><span class="sxs-lookup"><span data-stu-id="d821f-106">The changes in the collection view are reflected in the <xref:System.Windows.Controls.DataGrid> user interface (UI).</span></span>

<span data-ttu-id="d821f-107"><xref:System.Windows.Data.CollectionView> SAX gruplandırmasını ve sıralamasını işlevselliğini uygulayan bir veri kaynağı için <xref:System.Collections.IEnumerable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d821f-107">The <xref:System.Windows.Data.CollectionView> class provides grouping and sorting functionality for a data source that implements the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="d821f-108"><xref:System.Windows.Data.CollectionViewSource> Sınıf özelliklerini ayarlamanıza olanak sağlayan bir <xref:System.Windows.Data.CollectionView> XAML öğesinden.</span><span class="sxs-lookup"><span data-stu-id="d821f-108">The <xref:System.Windows.Data.CollectionViewSource> class enables you to set the properties of a <xref:System.Windows.Data.CollectionView> from XAML.</span></span>

<span data-ttu-id="d821f-109">Bu örnekte, bir koleksiyonu `Task` nesneleri bağlı bir <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="d821f-109">In this example, a collection of `Task` objects is bound to a <xref:System.Windows.Data.CollectionViewSource>.</span></span> <span data-ttu-id="d821f-110"><xref:System.Windows.Data.CollectionViewSource> Olarak kullanılan <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> için <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="d821f-110">The <xref:System.Windows.Data.CollectionViewSource> is used as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="d821f-111">Gruplandırma, sıralama ve filtreleme üzerinde gerçekleştirilir <xref:System.Windows.Data.CollectionViewSource> ve görüntülenen <xref:System.Windows.Controls.DataGrid> kullanıcı Arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d821f-111">Grouping, sorting, and filtering are performed on the <xref:System.Windows.Data.CollectionViewSource> and are displayed in the <xref:System.Windows.Controls.DataGrid> UI.</span></span>

<span data-ttu-id="d821f-112">![Gruplandırılmış veri kılavuzundaki](././media/wpf-datagridgroups.png "WPF_DataGridGroups") gruplandırılmış veri kılavuzundaki</span><span class="sxs-lookup"><span data-stu-id="d821f-112">![Grouped data in a DataGrid](././media/wpf-datagridgroups.png "WPF_DataGridGroups") Grouped data in a DataGrid</span></span>

## <a name="using-a-collectionviewsource-as-an-itemssource"></a><span data-ttu-id="d821f-113">Bir Collectionviewsource'a bir ItemsSource kullanma</span><span class="sxs-lookup"><span data-stu-id="d821f-113">Using a CollectionViewSource as an ItemsSource</span></span>

<span data-ttu-id="d821f-114">Gruplandırma, sıralama ve filtre verileri için bir <xref:System.Windows.Controls.DataGrid> denetimi bağlarsanız <xref:System.Windows.Controls.DataGrid> için bir <xref:System.Windows.Data.CollectionView> , bu işlevleri destekler.</span><span class="sxs-lookup"><span data-stu-id="d821f-114">To group, sort, and filter data in a <xref:System.Windows.Controls.DataGrid> control, you bind the <xref:System.Windows.Controls.DataGrid> to a <xref:System.Windows.Data.CollectionView> that supports these functions.</span></span> <span data-ttu-id="d821f-115">Bu örnekte, <xref:System.Windows.Controls.DataGrid> bağlı bir <xref:System.Windows.Data.CollectionViewSource> bu işlevler için sağlayan bir <xref:System.Collections.Generic.List%601> , `Task` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="d821f-115">In this example, the <xref:System.Windows.Controls.DataGrid> is bound to a <xref:System.Windows.Data.CollectionViewSource> that provides these functions for a <xref:System.Collections.Generic.List%601> of `Task` objects.</span></span>

### <a name="to-bind-a-datagrid-to-a-collectionviewsource"></a><span data-ttu-id="d821f-116">Bir DataGrid bir Collectionviewsource'a bağlamak için</span><span class="sxs-lookup"><span data-stu-id="d821f-116">To bind a DataGrid to a CollectionViewSource</span></span>

1. <span data-ttu-id="d821f-117">Uygulayan bir veri koleksiyonu oluşturma <xref:System.Collections.IEnumerable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d821f-117">Create a data collection that implements the <xref:System.Collections.IEnumerable> interface.</span></span>

    <span data-ttu-id="d821f-118">Kullanırsanız <xref:System.Collections.Generic.List%601> koleksiyonunuzu oluşturmak için devralan yeni bir sınıf oluşturmanız gerekir <xref:System.Collections.Generic.List%601> örneği başlatmak yerine <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="d821f-118">If you use <xref:System.Collections.Generic.List%601> to create your collection, you should create a new class that inherits from <xref:System.Collections.Generic.List%601> instead of instantiating an instance of <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="d821f-119">Bu, XAML koleksiyonda verilerin bağlanacağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d821f-119">This enables you to data bind to the collection in XAML.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d821f-120">Koleksiyondaki nesneleri uygulamalıdır <xref:System.ComponentModel.INotifyPropertyChanged> değiştirilen arabirimi ve <xref:System.ComponentModel.IEditableObject> arabirimi için sırayla <xref:System.Windows.Controls.DataGrid> özellik değişiklikleri ve düzenlemeleri için doğru bir şekilde yanıt vermesi.</span><span class="sxs-lookup"><span data-stu-id="d821f-120">The objects in the collection must implement the <xref:System.ComponentModel.INotifyPropertyChanged> changed interface and the <xref:System.ComponentModel.IEditableObject> interface in order for the <xref:System.Windows.Controls.DataGrid> to respond correctly to property changes and edits.</span></span> <span data-ttu-id="d821f-121">Daha fazla bilgi için [özellik değişikliği bildirimi uygulama](../data/how-to-implement-property-change-notification.md).</span><span class="sxs-lookup"><span data-stu-id="d821f-121">For more information, see [Implement Property Change Notification](../data/how-to-implement-property-change-notification.md).</span></span>

    [!code-csharp[DataGrid_GroupSortFilter#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#101)]
    [!code-vb[DataGrid_GroupSortFilter#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#101)]

2. <span data-ttu-id="d821f-122">XAML, koleksiyon sınıfı bir örneğini oluşturun ve ayarlayın [x: Key yönergesi](../../xaml-services/x-key-directive.md).</span><span class="sxs-lookup"><span data-stu-id="d821f-122">In XAML, create an instance of the collection class and set the [x:Key Directive](../../xaml-services/x-key-directive.md).</span></span>

3. <span data-ttu-id="d821f-123">XAML içinde bir örneğini oluşturmak <xref:System.Windows.Data.CollectionViewSource> sınıfı, Ayarla [x: Key yönergesi](../../xaml-services/x-key-directive.md)ve kümesi koleksiyon sınıfının örneği <xref:System.Windows.Data.CollectionViewSource.Source%2A>.</span><span class="sxs-lookup"><span data-stu-id="d821f-123">In XAML, create an instance of the <xref:System.Windows.Data.CollectionViewSource> class, set the [x:Key Directive](../../xaml-services/x-key-directive.md), and set the instance of your collection class as the <xref:System.Windows.Data.CollectionViewSource.Source%2A>.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#201](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml#201)]

4. <span data-ttu-id="d821f-124">Bir örneğini oluşturmak <xref:System.Windows.Controls.DataGrid> sınıfı ve ayarlama <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliğini <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="d821f-124">Create an instance of the <xref:System.Windows.Controls.DataGrid> class, and set the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property to the <xref:System.Windows.Data.CollectionViewSource>.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#002](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#002)]

5. <span data-ttu-id="d821f-125">Erişim için <xref:System.Windows.Data.CollectionViewSource> kodunuz içinden kullanmak <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> bir başvuru almak için yöntemi <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="d821f-125">To access the <xref:System.Windows.Data.CollectionViewSource> from your code, use the <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> method to get a reference to the <xref:System.Windows.Data.CollectionViewSource>.</span></span>

    [!code-csharp[DataGrid_GroupSortFilter#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#102)]
    [!code-vb[DataGrid_GroupSortFilter#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#102)]

## <a name="grouping-items-in-a-datagrid"></a><span data-ttu-id="d821f-126">DataGrid içinde öğeleri gruplandırma</span><span class="sxs-lookup"><span data-stu-id="d821f-126">Grouping items in a DataGrid</span></span>

<span data-ttu-id="d821f-127">Öğeleri nasıl gruplandırıldığını belirtmek için bir <xref:System.Windows.Controls.DataGrid>, kullandığınız <xref:System.Windows.Data.PropertyGroupDescription> kaynağı görünümündeki öğeleri gruplandırmak için türü.</span><span class="sxs-lookup"><span data-stu-id="d821f-127">To specify how items are grouped in a <xref:System.Windows.Controls.DataGrid>, you use the <xref:System.Windows.Data.PropertyGroupDescription> type to group the items in the source view.</span></span>

### <a name="to-group-items-in-a-datagrid-using-xaml"></a><span data-ttu-id="d821f-128">XAML kullanarak bir DataGrid içinde öğeleri gruplandırma</span><span class="sxs-lookup"><span data-stu-id="d821f-128">To group items in a DataGrid using XAML</span></span>

1. <span data-ttu-id="d821f-129">Oluşturma bir <xref:System.Windows.Data.PropertyGroupDescription> gruplama ölçütü özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="d821f-129">Create a <xref:System.Windows.Data.PropertyGroupDescription> that specifies the property to group by.</span></span> <span data-ttu-id="d821f-130">Özelliği, XAML ya da kod belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d821f-130">You can specify the property in XAML or in code.</span></span>

   1. <span data-ttu-id="d821f-131">XAML içinde ayarlamak <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> gruplama ölçütü özelliğinin adı.</span><span class="sxs-lookup"><span data-stu-id="d821f-131">In XAML, set the <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> to the name of the property to group by.</span></span>

   2. <span data-ttu-id="d821f-132">Kodda, özelliğin adını gruplama ölçütü Oluşturucu geçirin.</span><span class="sxs-lookup"><span data-stu-id="d821f-132">In code, pass the name of the property to group by to the constructor.</span></span>

2. <span data-ttu-id="d821f-133">Ekleme <xref:System.Windows.Data.PropertyGroupDescription> için <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d821f-133">Add the <xref:System.Windows.Data.PropertyGroupDescription> to the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> collection.</span></span>

3. <span data-ttu-id="d821f-134">Ek örneklerini eklemek <xref:System.Windows.Data.PropertyGroupDescription> için <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> daha fazla Gruplandırma düzeyleri eklemek için koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d821f-134">Add additional instances of <xref:System.Windows.Data.PropertyGroupDescription> to the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection to add more levels of grouping.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#012](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#012)]
    [!code-csharp[DataGrid_GroupSortFilter#112](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#112)]
    [!code-vb[DataGrid_GroupSortFilter#112](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#112)]

4. <span data-ttu-id="d821f-135">Bir grubu kaldırmak için <xref:System.Windows.Data.PropertyGroupDescription> gelen <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d821f-135">To remove a group, remove the <xref:System.Windows.Data.PropertyGroupDescription> from the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection.</span></span>

5. <span data-ttu-id="d821f-136">Tüm grupları kaldırmak için çağrı <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> yöntemi <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d821f-136">To remove all groups, call the <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> method of the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection.</span></span>

    [!code-csharp[DataGrid_GroupSortFilter#114](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#114)]
    [!code-vb[DataGrid_GroupSortFilter#114](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#114)]

<span data-ttu-id="d821f-137">Ne zaman öğeleri gruplanır içinde <xref:System.Windows.Controls.DataGrid>, tanımlayabileceğiniz bir <xref:System.Windows.Controls.GroupStyle> her grubu görünümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d821f-137">When items are grouped in the <xref:System.Windows.Controls.DataGrid>, you can define a <xref:System.Windows.Controls.GroupStyle> that specifies the appearance of each group.</span></span> <span data-ttu-id="d821f-138">Uyguladığınız <xref:System.Windows.Controls.GroupStyle> ekleyerek <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> DataGrid koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d821f-138">You apply the <xref:System.Windows.Controls.GroupStyle> by adding it to the <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> collection of the DataGrid.</span></span> <span data-ttu-id="d821f-139">Gruplandırma düzeylerinde varsa, her grup düzeyine farklı stil uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d821f-139">If you have multiple levels of grouping, you can apply different styles to each group level.</span></span> <span data-ttu-id="d821f-140">Stiller içinde tanımlandıkları sırayla uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d821f-140">Styles are applied in the order in which they are defined.</span></span> <span data-ttu-id="d821f-141">Örneğin, iki stilleri tanımlarsanız, ilk üst düzey satır gruplarına uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d821f-141">For example, if you define two styles, the first will be applied to top level row groups.</span></span> <span data-ttu-id="d821f-142">İkinci stili tüm satır grupları ikinci düzeyinde uygulanabilir ve daha düşük olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d821f-142">The second style will be applied to all row groups at the second level and lower.</span></span> <span data-ttu-id="d821f-143"><xref:System.Windows.FrameworkElement.DataContext%2A> , <xref:System.Windows.Controls.GroupStyle> Olduğu <xref:System.Windows.Data.CollectionViewGroup> grubu temsil eden.</span><span class="sxs-lookup"><span data-stu-id="d821f-143">The <xref:System.Windows.FrameworkElement.DataContext%2A> of the <xref:System.Windows.Controls.GroupStyle> is the <xref:System.Windows.Data.CollectionViewGroup> that the group represents.</span></span>

### <a name="to-change-the-appearance-of-row-group-headers"></a><span data-ttu-id="d821f-144">Satır grup başlıklarının görünümünü değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="d821f-144">To change the appearance of row group headers</span></span>

1. <span data-ttu-id="d821f-145">Oluşturma bir <xref:System.Windows.Controls.GroupStyle> , satır grubu görünümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d821f-145">Create a <xref:System.Windows.Controls.GroupStyle> that defines the appearance of the row group.</span></span>

2. <span data-ttu-id="d821f-146">PUT <xref:System.Windows.Controls.GroupStyle> içinde `<DataGrid.GroupStyle>` etiketler.</span><span class="sxs-lookup"><span data-stu-id="d821f-146">Put the <xref:System.Windows.Controls.GroupStyle> inside the `<DataGrid.GroupStyle>` tags.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#003](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#003)]

## <a name="sorting-items-in-a-datagrid"></a><span data-ttu-id="d821f-147">Bir DataGrid içindeki öğeleri sıralama</span><span class="sxs-lookup"><span data-stu-id="d821f-147">Sorting items in a DataGrid</span></span>

<span data-ttu-id="d821f-148">Öğeleri nasıl sıralanacağını belirlemek için bir <xref:System.Windows.Controls.DataGrid>, kullandığınız <xref:System.ComponentModel.SortDescription> kaynağı görünümündeki öğeleri sıralamak için türü.</span><span class="sxs-lookup"><span data-stu-id="d821f-148">To specify how items are sorted in a <xref:System.Windows.Controls.DataGrid>, you use the <xref:System.ComponentModel.SortDescription> type to sort the items in the source view.</span></span>

### <a name="to-sort-items-in-a-datagrid"></a><span data-ttu-id="d821f-149">DataGrid içindeki öğeleri sıralamak için</span><span class="sxs-lookup"><span data-stu-id="d821f-149">To sort items in a DataGrid</span></span>

1. <span data-ttu-id="d821f-150">Oluşturma bir <xref:System.ComponentModel.SortDescription> göre sıralamak için özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="d821f-150">Create a <xref:System.ComponentModel.SortDescription> that specifies the property to sort by.</span></span> <span data-ttu-id="d821f-151">Özelliği, XAML ya da kod belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d821f-151">You can specify the property in XAML or in code.</span></span>

    1. <span data-ttu-id="d821f-152">XAML içinde ayarlamak <xref:System.ComponentModel.SortDescription.PropertyName%2A> sıralanacak özelliğin adı.</span><span class="sxs-lookup"><span data-stu-id="d821f-152">In XAML, set the <xref:System.ComponentModel.SortDescription.PropertyName%2A> to the name of the property to sort by.</span></span>

    2. <span data-ttu-id="d821f-153">Sıralanacak özelliğin adını kodda, geçirin ve <xref:System.ComponentModel.ListSortDirection> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="d821f-153">In code, pass the name of the property to sort by and the <xref:System.ComponentModel.ListSortDirection> to the constructor.</span></span>

2. <span data-ttu-id="d821f-154">Ekleme <xref:System.ComponentModel.SortDescription> için <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d821f-154">Add the <xref:System.ComponentModel.SortDescription> to the <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> collection.</span></span>

3. <span data-ttu-id="d821f-155">Ek örneklerini eklemek <xref:System.ComponentModel.SortDescription> için <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> ek özelliklerine göre sıralamak için koleksiyon.</span><span class="sxs-lookup"><span data-stu-id="d821f-155">Add additional instances of <xref:System.ComponentModel.SortDescription> to the <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> collection to sort by additional properties.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#011](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#011)]
    [!code-csharp[DataGrid_GroupSortFilter#211](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml.cs#211)]
    [!code-vb[DataGrid_GroupSortFilter#211](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#211)]

## <a name="filtering-items-in-a-datagrid"></a><span data-ttu-id="d821f-156">Bir DataGrid öğeleri filtreleme</span><span class="sxs-lookup"><span data-stu-id="d821f-156">Filtering items in a DataGrid</span></span>

<span data-ttu-id="d821f-157">Öğelere filtre uygulamak için bir <xref:System.Windows.Controls.DataGrid> kullanarak bir <xref:System.Windows.Data.CollectionViewSource>, filtreleme mantığı işleyici için sağladığınız <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> olay.</span><span class="sxs-lookup"><span data-stu-id="d821f-157">To filter items in a <xref:System.Windows.Controls.DataGrid> using a <xref:System.Windows.Data.CollectionViewSource>, you provide the filtering logic in the handler for the <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> event.</span></span>

### <a name="to-filter-items-in-a-datagrid"></a><span data-ttu-id="d821f-158">Bir DataGrid içindeki öğeleri filtrelemek için</span><span class="sxs-lookup"><span data-stu-id="d821f-158">To filter items in a DataGrid</span></span>

1. <span data-ttu-id="d821f-159">İçin bir işleyici eklemek <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> olay.</span><span class="sxs-lookup"><span data-stu-id="d821f-159">Add a handler for the <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> event.</span></span>

2. <span data-ttu-id="d821f-160">İçinde <xref:System.Windows.Data.CollectionViewSource.Filter> olay işleyicisi, filtreleme mantığı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="d821f-160">In the <xref:System.Windows.Data.CollectionViewSource.Filter> event handler, define the filtering logic.</span></span>

    <span data-ttu-id="d821f-161">Görünümü her yenilendiğinde filtre uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d821f-161">The filter will be applied every time the view is refreshed.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#013](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#013)]
    [!code-csharp[DataGrid_GroupSortFilter#113](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#113)]
    [!code-vb[DataGrid_GroupSortFilter#113](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#113)]

<span data-ttu-id="d821f-162">Alternatif olarak, öğeleri filtreleyebilirsiniz bir <xref:System.Windows.Controls.DataGrid> filtreleme mantığı ve ayarı sağlayan bir yöntem oluşturarak <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> filtre uygulamak için özellik.</span><span class="sxs-lookup"><span data-stu-id="d821f-162">Alternatively, you can filter items in a <xref:System.Windows.Controls.DataGrid> by creating a method that provides the filtering logic and setting the <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> property to apply the filter.</span></span> <span data-ttu-id="d821f-163">Bu yöntem bir örneğini görmek için bkz: [görünümde veri filtreleme](../data/how-to-filter-data-in-a-view.md).</span><span class="sxs-lookup"><span data-stu-id="d821f-163">To see an example of this method, see [Filter Data in a View](../data/how-to-filter-data-in-a-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d821f-164">Örnek</span><span class="sxs-lookup"><span data-stu-id="d821f-164">Example</span></span>

<span data-ttu-id="d821f-165">Aşağıdaki örnek, gruplandırma, sıralama ve filtreleme gösterir `Task` verilerinde bir <xref:System.Windows.Data.CollectionViewSource> ve sıralanmış ve filtrelenmiş gruplandırılmış, görüntüleme `Task` verilerinde bir <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="d821f-165">The following example demonstrates grouping, sorting, and filtering `Task` data in a <xref:System.Windows.Data.CollectionViewSource> and displaying the grouped, sorted, and filtered `Task` data in a <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="d821f-166"><xref:System.Windows.Data.CollectionViewSource> Olarak kullanılan <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> için <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="d821f-166">The <xref:System.Windows.Data.CollectionViewSource> is used as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="d821f-167">Gruplandırma, sıralama ve filtreleme üzerinde gerçekleştirilir <xref:System.Windows.Data.CollectionViewSource> ve görüntülenen <xref:System.Windows.Controls.DataGrid> kullanıcı Arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d821f-167">Grouping, sorting, and filtering are performed on the <xref:System.Windows.Data.CollectionViewSource> and are displayed in the <xref:System.Windows.Controls.DataGrid> UI.</span></span>

<span data-ttu-id="d821f-168">Bu örnekte test etmek için projenizin adına eşleştirilecek DGGroupSortFilterExample adı ayarlamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="d821f-168">To test this example, you will need to adjust the DGGroupSortFilterExample name to match your project name.</span></span> <span data-ttu-id="d821f-169">Visual Basic kullanıyorsanız, sınıf adını değiştirmeniz gerekir <xref:System.Windows.Window> aşağıdaki.</span><span class="sxs-lookup"><span data-stu-id="d821f-169">If you are using Visual Basic, you will need to change the class name for <xref:System.Windows.Window> to the following.</span></span>

`<Window x:Class="MainWindow"`

[!code-xaml[DataGrid_GroupSortFilter#000](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#000)]
[!code-csharp[DataGrid_GroupSortFilter#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#100)]
[!code-vb[DataGrid_GroupSortFilter#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#100)]

## <a name="see-also"></a><span data-ttu-id="d821f-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d821f-170">See also</span></span>

- [<span data-ttu-id="d821f-171">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d821f-171">Data Binding Overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="d821f-172">ObservableCollection Oluşturma ve Bağlama</span><span class="sxs-lookup"><span data-stu-id="d821f-172">Create and Bind to an ObservableCollection</span></span>](../data/how-to-create-and-bind-to-an-observablecollection.md)
- [<span data-ttu-id="d821f-173">Görünümde Veri Filtreleme</span><span class="sxs-lookup"><span data-stu-id="d821f-173">Filter Data in a View</span></span>](../data/how-to-filter-data-in-a-view.md)
- [<span data-ttu-id="d821f-174">Görünümde Verileri Sıralama</span><span class="sxs-lookup"><span data-stu-id="d821f-174">Sort Data in a View</span></span>](../data/how-to-sort-data-in-a-view.md)
- [<span data-ttu-id="d821f-175">XAML İçerisinde bir Görüntü Kullanarak Verileri Sıralama ve Gruplama</span><span class="sxs-lookup"><span data-stu-id="d821f-175">Sort and Group Data Using a View in XAML</span></span>](../data/how-to-sort-and-group-data-using-a-view-in-xaml.md)
