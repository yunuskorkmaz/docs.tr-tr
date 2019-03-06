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
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365054"
---
# <a name="how-to-group-sort-and-filter-data-in-the-datagrid-control"></a>Nasıl yapılır: DataGrid denetiminde filtre verileri gruplandırma, sıralama ve

Genellikle verileri görüntülemek için yararlı bir <xref:System.Windows.Controls.DataGrid> gruplandırma, sıralama ve filtreleme verileri tarafından farklı şekillerde. Grup, sıralama ve verileri filtrelemek için bir <xref:System.Windows.Controls.DataGrid>, kendisine bağlamak bir <xref:System.Windows.Data.CollectionView> , bu işlevleri destekler. Ardından verileri ile çalışabilirsiniz <xref:System.Windows.Data.CollectionView> temel kaynak verilerini etkilemeden. Koleksiyon görünümü yapılan değişiklikler yansıtılır <xref:System.Windows.Controls.DataGrid> kullanıcı arabirimi (UI).

<xref:System.Windows.Data.CollectionView> SAX gruplandırmasını ve sıralamasını işlevselliğini uygulayan bir veri kaynağı için <xref:System.Collections.IEnumerable> arabirimi. <xref:System.Windows.Data.CollectionViewSource> Sınıf özelliklerini ayarlamanıza olanak sağlayan bir <xref:System.Windows.Data.CollectionView> XAML öğesinden.

Bu örnekte, bir koleksiyonu `Task` nesneleri bağlı bir <xref:System.Windows.Data.CollectionViewSource>. <xref:System.Windows.Data.CollectionViewSource> Olarak kullanılan <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> için <xref:System.Windows.Controls.DataGrid>. Gruplandırma, sıralama ve filtreleme üzerinde gerçekleştirilir <xref:System.Windows.Data.CollectionViewSource> ve görüntülenen <xref:System.Windows.Controls.DataGrid> kullanıcı Arabirimi.

![Gruplandırılmış veri kılavuzundaki](././media/wpf-datagridgroups.png "WPF_DataGridGroups") gruplandırılmış veri kılavuzundaki

## <a name="using-a-collectionviewsource-as-an-itemssource"></a>Bir Collectionviewsource'a bir ItemsSource kullanma

Gruplandırma, sıralama ve filtre verileri için bir <xref:System.Windows.Controls.DataGrid> denetimi bağlarsanız <xref:System.Windows.Controls.DataGrid> için bir <xref:System.Windows.Data.CollectionView> , bu işlevleri destekler. Bu örnekte, <xref:System.Windows.Controls.DataGrid> bağlı bir <xref:System.Windows.Data.CollectionViewSource> bu işlevler için sağlayan bir <xref:System.Collections.Generic.List%601> , `Task` nesneleri.

### <a name="to-bind-a-datagrid-to-a-collectionviewsource"></a>Bir DataGrid bir Collectionviewsource'a bağlamak için

1. Uygulayan bir veri koleksiyonu oluşturma <xref:System.Collections.IEnumerable> arabirimi.

    Kullanırsanız <xref:System.Collections.Generic.List%601> koleksiyonunuzu oluşturmak için devralan yeni bir sınıf oluşturmanız gerekir <xref:System.Collections.Generic.List%601> örneği başlatmak yerine <xref:System.Collections.Generic.List%601>. Bu, XAML koleksiyonda verilerin bağlanacağı sağlar.

    > [!NOTE]
    > Koleksiyondaki nesneleri uygulamalıdır <xref:System.ComponentModel.INotifyPropertyChanged> değiştirilen arabirimi ve <xref:System.ComponentModel.IEditableObject> arabirimi için sırayla <xref:System.Windows.Controls.DataGrid> özellik değişiklikleri ve düzenlemeleri için doğru bir şekilde yanıt vermesi. Daha fazla bilgi için [özellik değişikliği bildirimi uygulama](../data/how-to-implement-property-change-notification.md).

    [!code-csharp[DataGrid_GroupSortFilter#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#101)]
    [!code-vb[DataGrid_GroupSortFilter#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#101)]

2. XAML, koleksiyon sınıfı bir örneğini oluşturun ve ayarlayın [x: Key yönergesi](../../xaml-services/x-key-directive.md).

3. XAML içinde bir örneğini oluşturmak <xref:System.Windows.Data.CollectionViewSource> sınıfı, Ayarla [x: Key yönergesi](../../xaml-services/x-key-directive.md)ve kümesi koleksiyon sınıfının örneği <xref:System.Windows.Data.CollectionViewSource.Source%2A>.

    [!code-xaml[DataGrid_GroupSortFilter#201](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml#201)]

4. Bir örneğini oluşturmak <xref:System.Windows.Controls.DataGrid> sınıfı ve ayarlama <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliğini <xref:System.Windows.Data.CollectionViewSource>.

    [!code-xaml[DataGrid_GroupSortFilter#002](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#002)]

5. Erişim için <xref:System.Windows.Data.CollectionViewSource> kodunuz içinden kullanmak <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> bir başvuru almak için yöntemi <xref:System.Windows.Data.CollectionViewSource>.

    [!code-csharp[DataGrid_GroupSortFilter#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#102)]
    [!code-vb[DataGrid_GroupSortFilter#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#102)]

## <a name="grouping-items-in-a-datagrid"></a>DataGrid içinde öğeleri gruplandırma

Öğeleri nasıl gruplandırıldığını belirtmek için bir <xref:System.Windows.Controls.DataGrid>, kullandığınız <xref:System.Windows.Data.PropertyGroupDescription> kaynağı görünümündeki öğeleri gruplandırmak için türü.

### <a name="to-group-items-in-a-datagrid-using-xaml"></a>XAML kullanarak bir DataGrid içinde öğeleri gruplandırma

1. Oluşturma bir <xref:System.Windows.Data.PropertyGroupDescription> gruplama ölçütü özelliği belirtir. Özelliği, XAML ya da kod belirtebilirsiniz.

   1. XAML içinde ayarlamak <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> gruplama ölçütü özelliğinin adı.

   2. Kodda, özelliğin adını gruplama ölçütü Oluşturucu geçirin.

2. Ekleme <xref:System.Windows.Data.PropertyGroupDescription> için <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> koleksiyonu.

3. Ek örneklerini eklemek <xref:System.Windows.Data.PropertyGroupDescription> için <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> daha fazla Gruplandırma düzeyleri eklemek için koleksiyonu.

    [!code-xaml[DataGrid_GroupSortFilter#012](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#012)]
    [!code-csharp[DataGrid_GroupSortFilter#112](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#112)]
    [!code-vb[DataGrid_GroupSortFilter#112](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#112)]

4. Bir grubu kaldırmak için <xref:System.Windows.Data.PropertyGroupDescription> gelen <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> koleksiyonu.

5. Tüm grupları kaldırmak için çağrı <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> yöntemi <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> koleksiyonu.

    [!code-csharp[DataGrid_GroupSortFilter#114](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#114)]
    [!code-vb[DataGrid_GroupSortFilter#114](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#114)]

Ne zaman öğeleri gruplanır içinde <xref:System.Windows.Controls.DataGrid>, tanımlayabileceğiniz bir <xref:System.Windows.Controls.GroupStyle> her grubu görünümünü belirtir. Uyguladığınız <xref:System.Windows.Controls.GroupStyle> ekleyerek <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> DataGrid koleksiyonu. Gruplandırma düzeylerinde varsa, her grup düzeyine farklı stil uygulayabilirsiniz. Stiller içinde tanımlandıkları sırayla uygulanır. Örneğin, iki stilleri tanımlarsanız, ilk üst düzey satır gruplarına uygulanır. İkinci stili tüm satır grupları ikinci düzeyinde uygulanabilir ve daha düşük olacaktır. <xref:System.Windows.FrameworkElement.DataContext%2A> , <xref:System.Windows.Controls.GroupStyle> Olduğu <xref:System.Windows.Data.CollectionViewGroup> grubu temsil eden.

### <a name="to-change-the-appearance-of-row-group-headers"></a>Satır grup başlıklarının görünümünü değiştirmek için

1. Oluşturma bir <xref:System.Windows.Controls.GroupStyle> , satır grubu görünümünü tanımlar.

2. PUT <xref:System.Windows.Controls.GroupStyle> içinde `<DataGrid.GroupStyle>` etiketler.

    [!code-xaml[DataGrid_GroupSortFilter#003](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#003)]

## <a name="sorting-items-in-a-datagrid"></a>Bir DataGrid içindeki öğeleri sıralama

Öğeleri nasıl sıralanacağını belirlemek için bir <xref:System.Windows.Controls.DataGrid>, kullandığınız <xref:System.ComponentModel.SortDescription> kaynağı görünümündeki öğeleri sıralamak için türü.

### <a name="to-sort-items-in-a-datagrid"></a>DataGrid içindeki öğeleri sıralamak için

1. Oluşturma bir <xref:System.ComponentModel.SortDescription> göre sıralamak için özelliği belirtir. Özelliği, XAML ya da kod belirtebilirsiniz.

    1. XAML içinde ayarlamak <xref:System.ComponentModel.SortDescription.PropertyName%2A> sıralanacak özelliğin adı.

    2. Sıralanacak özelliğin adını kodda, geçirin ve <xref:System.ComponentModel.ListSortDirection> Oluşturucusu.

2. Ekleme <xref:System.ComponentModel.SortDescription> için <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> koleksiyonu.

3. Ek örneklerini eklemek <xref:System.ComponentModel.SortDescription> için <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> ek özelliklerine göre sıralamak için koleksiyon.

    [!code-xaml[DataGrid_GroupSortFilter#011](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#011)]
    [!code-csharp[DataGrid_GroupSortFilter#211](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml.cs#211)]
    [!code-vb[DataGrid_GroupSortFilter#211](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#211)]

## <a name="filtering-items-in-a-datagrid"></a>Bir DataGrid öğeleri filtreleme

Öğelere filtre uygulamak için bir <xref:System.Windows.Controls.DataGrid> kullanarak bir <xref:System.Windows.Data.CollectionViewSource>, filtreleme mantığı işleyici için sağladığınız <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> olay.

### <a name="to-filter-items-in-a-datagrid"></a>Bir DataGrid içindeki öğeleri filtrelemek için

1. İçin bir işleyici eklemek <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> olay.

2. İçinde <xref:System.Windows.Data.CollectionViewSource.Filter> olay işleyicisi, filtreleme mantığı tanımlayın.

    Görünümü her yenilendiğinde filtre uygulanır.

    [!code-xaml[DataGrid_GroupSortFilter#013](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#013)]
    [!code-csharp[DataGrid_GroupSortFilter#113](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#113)]
    [!code-vb[DataGrid_GroupSortFilter#113](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#113)]

Alternatif olarak, öğeleri filtreleyebilirsiniz bir <xref:System.Windows.Controls.DataGrid> filtreleme mantığı ve ayarı sağlayan bir yöntem oluşturarak <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> filtre uygulamak için özellik. Bu yöntem bir örneğini görmek için bkz: [görünümde veri filtreleme](../data/how-to-filter-data-in-a-view.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, gruplandırma, sıralama ve filtreleme gösterir `Task` verilerinde bir <xref:System.Windows.Data.CollectionViewSource> ve sıralanmış ve filtrelenmiş gruplandırılmış, görüntüleme `Task` verilerinde bir <xref:System.Windows.Controls.DataGrid>. <xref:System.Windows.Data.CollectionViewSource> Olarak kullanılan <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> için <xref:System.Windows.Controls.DataGrid>. Gruplandırma, sıralama ve filtreleme üzerinde gerçekleştirilir <xref:System.Windows.Data.CollectionViewSource> ve görüntülenen <xref:System.Windows.Controls.DataGrid> kullanıcı Arabirimi.

Bu örnekte test etmek için projenizin adına eşleştirilecek DGGroupSortFilterExample adı ayarlamak gerekir. Visual Basic kullanıyorsanız, sınıf adını değiştirmeniz gerekir <xref:System.Windows.Window> aşağıdaki.

`<Window x:Class="MainWindow"`

[!code-xaml[DataGrid_GroupSortFilter#000](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#000)]
[!code-csharp[DataGrid_GroupSortFilter#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#100)]
[!code-vb[DataGrid_GroupSortFilter#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#100)]

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlamaya Genel Bakış](../data/data-binding-overview.md)
- [ObservableCollection Oluşturma ve Bağlama](../data/how-to-create-and-bind-to-an-observablecollection.md)
- [Görünümde Veri Filtreleme](../data/how-to-filter-data-in-a-view.md)
- [Görünümde Verileri Sıralama](../data/how-to-sort-data-in-a-view.md)
- [XAML İçerisinde bir Görüntü Kullanarak Verileri Sıralama ve Gruplama](../data/how-to-sort-and-group-data-using-a-view-in-xaml.md)
