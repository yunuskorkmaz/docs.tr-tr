---
title: 'Nasıl yapılır: DataGrid denetiminde verileri gruplandırma, sıralama ve filtreleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], sort
- DataGrid [WPF], group
- DataGrid [WPF], filter
ms.assetid: 03345e85-89e3-4aec-9ed0-3b80759df770
ms.openlocfilehash: 2632566b5b55ae641d2750e903bf94cdc681f8f8
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460244"
---
# <a name="how-to-group-sort-and-filter-data-in-the-datagrid-control"></a>Nasıl yapılır: DataGrid denetiminde verileri gruplandırma, sıralama ve filtreleme

Verileri gruplandırarak, sıralayarak ve filtreleyerek <xref:System.Windows.Controls.DataGrid> verileri farklı yollarla görüntülemek genellikle yararlı olur. <xref:System.Windows.Controls.DataGrid>verileri gruplamak, sıralamak ve filtrelemek için, bu işlevleri destekleyen bir <xref:System.Windows.Data.CollectionView> bağlarsınız. Daha sonra, temel alınan kaynak verileri etkilemeden <xref:System.Windows.Data.CollectionView> verilerle çalışabilirsiniz. Koleksiyon görünümündeki değişiklikler <xref:System.Windows.Controls.DataGrid> Kullanıcı arabiriminde (UI) yansıtılır.

<xref:System.Windows.Data.CollectionView> sınıfı, <xref:System.Collections.IEnumerable> arabirimini uygulayan bir veri kaynağı için gruplandırma ve sıralama işlevi sağlar. <xref:System.Windows.Data.CollectionViewSource> sınıfı, XAML 'den bir <xref:System.Windows.Data.CollectionView> özelliklerini ayarlamanıza olanak sağlar.

Bu örnekte, bir `Task` nesneleri koleksiyonu bir <xref:System.Windows.Data.CollectionViewSource>bağlanır. <xref:System.Windows.Data.CollectionViewSource>, <xref:System.Windows.Controls.DataGrid><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> olarak kullanılır. Gruplandırma, sıralama ve filtreleme <xref:System.Windows.Data.CollectionViewSource> gerçekleştirilir ve <xref:System.Windows.Controls.DataGrid> Kullanıcı arabiriminde görüntülenir.

![DataGrid 'de gruplanmış veriler](././media/wpf-datagridgroups.png "WPF_DataGridGroups") DataGrid 'de gruplanmış veriler

## <a name="using-a-collectionviewsource-as-an-itemssource"></a>CollectionViewSource 'u ItemSource olarak kullanma

<xref:System.Windows.Controls.DataGrid> denetimindeki verileri gruplamak, sıralamak ve filtrelemek için, bu işlevleri destekleyen bir <xref:System.Windows.Data.CollectionView> <xref:System.Windows.Controls.DataGrid> bağlarsınız. Bu örnekte <xref:System.Windows.Controls.DataGrid>, `Task` nesneleri <xref:System.Collections.Generic.List%601> için bu işlevleri sağlayan bir <xref:System.Windows.Data.CollectionViewSource> bağımlıdır.

### <a name="to-bind-a-datagrid-to-a-collectionviewsource"></a>Bir DataGrid 'i CollectionViewSource 'a bağlamak için

1. <xref:System.Collections.IEnumerable> arabirimini uygulayan bir veri koleksiyonu oluşturun.

    Koleksiyonunuzu oluşturmak için <xref:System.Collections.Generic.List%601> kullanıyorsanız, <xref:System.Collections.Generic.List%601>örneğini başlatmak yerine <xref:System.Collections.Generic.List%601> devralan yeni bir sınıf oluşturmanız gerekir. Bu, XAML 'de koleksiyona veri bağlamanıza olanak sağlar.

    > [!NOTE]
    > Koleksiyondaki nesneler, <xref:System.Windows.Controls.DataGrid> Özellik değişiklikleri ve düzenlemelerine doğru yanıt vermesi için <xref:System.ComponentModel.INotifyPropertyChanged> değiştirilen arabirimi ve <xref:System.ComponentModel.IEditableObject> arabirimini uygulamalıdır. Daha fazla bilgi için bkz. [özellik değişiklik bildirimini uygulama](../data/how-to-implement-property-change-notification.md).

    [!code-csharp[DataGrid_GroupSortFilter#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#101)]
    [!code-vb[DataGrid_GroupSortFilter#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#101)]

2. XAML 'de, koleksiyon sınıfının bir örneğini oluşturun ve [X:Key yönergesini](../../xaml-services/x-key-directive.md)ayarlayın.

3. XAML 'de <xref:System.Windows.Data.CollectionViewSource> sınıfının bir örneğini oluşturun, [X:Key yönergesini](../../xaml-services/x-key-directive.md)ayarlayın ve koleksiyon sınıfınızın örneğini <xref:System.Windows.Data.CollectionViewSource.Source%2A>olarak ayarlayın.

    [!code-xaml[DataGrid_GroupSortFilter#201](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml#201)]

4. <xref:System.Windows.Controls.DataGrid> sınıfının bir örneğini oluşturun ve <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliğini <xref:System.Windows.Data.CollectionViewSource>olarak ayarlayın.

    [!code-xaml[DataGrid_GroupSortFilter#002](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#002)]

5. Kodunuzda <xref:System.Windows.Data.CollectionViewSource> erişmek için, <xref:System.Windows.Data.CollectionViewSource>bir başvuru almak için <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> metodunu kullanın.

    [!code-csharp[DataGrid_GroupSortFilter#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#102)]
    [!code-vb[DataGrid_GroupSortFilter#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#102)]

## <a name="grouping-items-in-a-datagrid"></a>DataGrid içinde öğeleri gruplandırma

Öğelerin bir <xref:System.Windows.Controls.DataGrid>nasıl gruplandığını belirtmek için, kaynak görünümündeki öğeleri gruplandırmak üzere <xref:System.Windows.Data.PropertyGroupDescription> türünü kullanın.

### <a name="to-group-items-in-a-datagrid-using-xaml"></a>XAML kullanarak bir DataGrid içindeki öğeleri gruplandırmak için

1. Gruplandırma ölçütü olan özelliği belirten bir <xref:System.Windows.Data.PropertyGroupDescription> oluşturun. Özelliği XAML 'de veya kodda belirtebilirsiniz.

   1. XAML 'de, <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A>, gruplandırma ölçütü olan özelliğin adı olarak ayarlayın.

   2. Kod ' da, özelliğin adını oluşturucuya göre grupla geçirin.

2. <xref:System.Windows.Data.PropertyGroupDescription> <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> koleksiyonuna ekleyin.

3. Daha fazla gruplandırma düzeyi eklemek için <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> koleksiyonuna <xref:System.Windows.Data.PropertyGroupDescription> ek örnekler ekleyin.

    [!code-xaml[DataGrid_GroupSortFilter#012](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#012)]
    [!code-csharp[DataGrid_GroupSortFilter#112](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#112)]
    [!code-vb[DataGrid_GroupSortFilter#112](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#112)]

4. Bir grubu kaldırmak için <xref:System.Windows.Data.PropertyGroupDescription> <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> koleksiyonundan kaldırın.

5. Tüm grupları kaldırmak için <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> koleksiyonunun <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> yöntemini çağırın.

    [!code-csharp[DataGrid_GroupSortFilter#114](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#114)]
    [!code-vb[DataGrid_GroupSortFilter#114](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#114)]

Öğeler <xref:System.Windows.Controls.DataGrid>gruplandırılırken, her grubun görünümünü belirten bir <xref:System.Windows.Controls.GroupStyle> tanımlayabilirsiniz. <xref:System.Windows.Controls.GroupStyle> DataGrid 'in <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> koleksiyonuna ekleyerek uygularsınız. Birden çok gruplandırma düzeyine sahipseniz, her grup düzeyine farklı stiller uygulayabilirsiniz. Stiller tanımlandıkları sırayla uygulanır. Örneğin, iki stil tanımlarsanız, ilki en üst düzey satır gruplarına uygulanır. İkinci stil, ikinci düzeyde ve daha düşük tüm satır gruplarına uygulanır. <xref:System.Windows.Controls.GroupStyle> <xref:System.Windows.FrameworkElement.DataContext%2A>, grubun temsil ettiği <xref:System.Windows.Data.CollectionViewGroup>.

### <a name="to-change-the-appearance-of-row-group-headers"></a>Satır grubu üstbilgilerinin görünümünü değiştirmek için

1. Satır grubunun görünümünü tanımlayan bir <xref:System.Windows.Controls.GroupStyle> oluşturun.

2. <xref:System.Windows.Controls.GroupStyle> `<DataGrid.GroupStyle>` etiketlerinin içine koyun.

    [!code-xaml[DataGrid_GroupSortFilter#003](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#003)]

## <a name="sorting-items-in-a-datagrid"></a>DataGrid 'de öğeleri sıralama

Öğelerin bir <xref:System.Windows.Controls.DataGrid>nasıl sıralanacağını belirtmek için, kaynak görünümündeki öğeleri sıralamak üzere <xref:System.ComponentModel.SortDescription> türünü kullanın.

### <a name="to-sort-items-in-a-datagrid"></a>DataGrid 'deki öğeleri sıralamak için

1. Sıralama yapılacak özelliği belirten bir <xref:System.ComponentModel.SortDescription> oluşturun. Özelliği XAML 'de veya kodda belirtebilirsiniz.

    1. XAML 'de, <xref:System.ComponentModel.SortDescription.PropertyName%2A> sıralama yapılacak özelliğin adı olarak ayarlayın.

    2. Kod içinde, sıralama için özelliğin adını ve oluşturucuya <xref:System.ComponentModel.ListSortDirection> geçirin.

2. <xref:System.ComponentModel.SortDescription> <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> koleksiyonuna ekleyin.

3. Ek özelliklere göre sıralamak için <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> koleksiyonuna ek <xref:System.ComponentModel.SortDescription> örnekleri ekleyin.

    [!code-xaml[DataGrid_GroupSortFilter#011](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#011)]
    [!code-csharp[DataGrid_GroupSortFilter#211](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml.cs#211)]
    [!code-vb[DataGrid_GroupSortFilter#211](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#211)]

## <a name="filtering-items-in-a-datagrid"></a>DataGrid 'de öğeleri filtreleme

Bir <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Data.CollectionViewSource>kullanarak öğeleri filtrelemek için, <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> olayının işleyicisindeki filtreleme mantığını sağlarsınız.

### <a name="to-filter-items-in-a-datagrid"></a>DataGrid 'deki öğeleri filtrelemek için

1. <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> olayı için bir işleyici ekleyin.

2. <xref:System.Windows.Data.CollectionViewSource.Filter> olay işleyicisinde filtreleme mantığını tanımlayın.

    Bu filtre, görünüm her yenilendiğinde uygulanır.

    [!code-xaml[DataGrid_GroupSortFilter#013](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#013)]
    [!code-csharp[DataGrid_GroupSortFilter#113](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#113)]
    [!code-vb[DataGrid_GroupSortFilter#113](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#113)]

Alternatif olarak, filtreleme mantığını sağlayan bir yöntem oluşturarak ve filtreyi uygulamak için <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> özelliğini ayarlayarak bir <xref:System.Windows.Controls.DataGrid> öğeleri filtreleyebilirsiniz. Bu yöntemin bir örneğini görmek için bkz. [bir görünümdeki verileri filtreleme](../data/how-to-filter-data-in-a-view.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir <xref:System.Windows.Data.CollectionViewSource> `Task` verileri gruplandırma, sıralama ve filtreleme işlemlerini ve gruplanmış, sıralanmış ve filtrelenmiş `Task` verilerini bir <xref:System.Windows.Controls.DataGrid>görüntülemeyi gösterir. <xref:System.Windows.Data.CollectionViewSource>, <xref:System.Windows.Controls.DataGrid><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> olarak kullanılır. Gruplandırma, sıralama ve filtreleme <xref:System.Windows.Data.CollectionViewSource> gerçekleştirilir ve <xref:System.Windows.Controls.DataGrid> Kullanıcı arabiriminde görüntülenir.

Bu örneği test etmek için DGGroupSortFilterExample adını proje adınızla eşleşecek şekilde ayarlamanız gerekecektir. Visual Basic kullanıyorsanız, <xref:System.Windows.Window> için sınıf adını aşağıdaki şekilde değiştirmeniz gerekir.

`<Window x:Class="MainWindow"`

[!code-xaml[DataGrid_GroupSortFilter#000](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#000)]
[!code-csharp[DataGrid_GroupSortFilter#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#100)]
[!code-vb[DataGrid_GroupSortFilter#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#100)]

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [ObservableCollection Oluşturma ve Bağlama](../data/how-to-create-and-bind-to-an-observablecollection.md)
- [Görünümde Veri Filtreleme](../data/how-to-filter-data-in-a-view.md)
- [Görünümde Verileri Sıralama](../data/how-to-sort-data-in-a-view.md)
- [XAML İçerisinde bir Görüntü Kullanarak Verileri Sıralama ve Gruplama](../data/how-to-sort-and-group-data-using-a-view-in-xaml.md)
