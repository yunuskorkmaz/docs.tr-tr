---
title: 'Nasıl yapılır: DataGrid denetiminde verileri gruplandırma, sıralama ve filtreleme'
description: Windows Presentation Foundation DataGrid denetimini, görünümlerde verileri gruplandırmayı, sıralamayı ve filtrelemeyi destekleyen bir CollectionView 'a bağlamayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], sort
- DataGrid [WPF], group
- DataGrid [WPF], filter
ms.assetid: 03345e85-89e3-4aec-9ed0-3b80759df770
ms.openlocfilehash: 072e5a104a91faa40bb54f2a3fc4ed6188e1112e
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167672"
---
# <a name="how-to-group-sort-and-filter-data-in-the-datagrid-control"></a>Nasıl yapılır: DataGrid denetiminde verileri gruplandırma, sıralama ve filtreleme

Verileri <xref:System.Windows.Controls.DataGrid> gruplandırarak, sıralayarak ve filtreleyerek verileri farklı yollarla görüntülemek genellikle yararlı olur. İçindeki verileri gruplamak, sıralamak ve filtrelemek için <xref:System.Windows.Controls.DataGrid> , <xref:System.Windows.Data.CollectionView> Bu işlevleri destekleyen bir öğesine bağlarsınız. Daha sonra, <xref:System.Windows.Data.CollectionView> temel alınan kaynak verileri etkilemeden içindeki verilerle çalışabilirsiniz. Koleksiyon görünümündeki değişiklikler <xref:System.Windows.Controls.DataGrid> Kullanıcı arabiriminde (UI) yansıtılır.

<xref:System.Windows.Data.CollectionView>Sınıfı, arabirimini uygulayan bir veri kaynağı için gruplandırma ve sıralama işlevi sağlar <xref:System.Collections.IEnumerable> . <xref:System.Windows.Data.CollectionViewSource>Sınıfı, XAML 'nin özelliklerini xaml 'den ayarlamanıza olanak sağlar <xref:System.Windows.Data.CollectionView> .

Bu örnekte, `Task` bir nesne koleksiyonu bir öğesine bağlanır <xref:System.Windows.Data.CollectionViewSource> . , <xref:System.Windows.Data.CollectionViewSource> İçin olarak kullanılır <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.DataGrid> . Gruplandırma, sıralama ve filtreleme, üzerinde gerçekleştirilir <xref:System.Windows.Data.CollectionViewSource> ve <xref:System.Windows.Controls.DataGrid> Kullanıcı arabiriminde görüntülenir.

![DataGrid 'de gruplanmış veriler](././media/wpf-datagridgroups.png "WPF_DataGridGroups") DataGrid 'de gruplanmış veriler

## <a name="using-a-collectionviewsource-as-an-itemssource"></a>CollectionViewSource 'u ItemSource olarak kullanma

Bir denetimdeki verileri gruplamak, sıralamak ve filtrelemek için <xref:System.Windows.Controls.DataGrid> , ' yi <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Data.CollectionView> Bu işlevleri destekleyen bir öğesine bağlarsınız. Bu örnekte, bir <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Data.CollectionViewSource> nesne için bu işlevleri sağlayan bir öğesine bağlanır <xref:System.Collections.Generic.List%601> `Task` .

### <a name="to-bind-a-datagrid-to-a-collectionviewsource"></a>Bir DataGrid 'i CollectionViewSource 'a bağlamak için

1. Arabirimini uygulayan bir veri koleksiyonu oluşturun <xref:System.Collections.IEnumerable> .

    <xref:System.Collections.Generic.List%601>Koleksiyonunuzu oluşturmak için kullanırsanız, bir örneğinin örneğini oluşturmak yerine öğesinden devralan yeni bir sınıf oluşturmanız gerekir <xref:System.Collections.Generic.List%601> <xref:System.Collections.Generic.List%601> . Bu, XAML 'de koleksiyona veri bağlamanıza olanak sağlar.

    > [!NOTE]
    > Koleksiyondaki nesneler <xref:System.ComponentModel.INotifyPropertyChanged> <xref:System.ComponentModel.IEditableObject> , <xref:System.Windows.Controls.DataGrid> özelliğinin özellik değişikliklerine ve düzenlemelerine doğru yanıt vermesi için değiştirilen arabirimi ve arabirimi uygulamalıdır. Daha fazla bilgi için bkz. [özellik değişiklik bildirimini uygulama](../data/how-to-implement-property-change-notification.md).

    [!code-csharp[DataGrid_GroupSortFilter#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#101)]
    [!code-vb[DataGrid_GroupSortFilter#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#101)]

2. XAML 'de, koleksiyon sınıfının bir örneğini oluşturun ve [X:Key yönergesini](../../../desktop-wpf/xaml-services/xkey-directive.md)ayarlayın.

3. XAML 'de, sınıfının bir örneğini oluşturun <xref:System.Windows.Data.CollectionViewSource> , [X:Key yönergesini](../../../desktop-wpf/xaml-services/xkey-directive.md)ayarlayın ve koleksiyon sınıfınızın örneğini olarak ayarlayın <xref:System.Windows.Data.CollectionViewSource.Source%2A> .

    [!code-xaml[DataGrid_GroupSortFilter#201](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml#201)]

4. Sınıfının bir örneğini oluşturun <xref:System.Windows.Controls.DataGrid> ve <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliğini olarak ayarlayın <xref:System.Windows.Data.CollectionViewSource> .

    [!code-xaml[DataGrid_GroupSortFilter#002](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#002)]

5. Kodunuzda öğesine erişmek için, <xref:System.Windows.Data.CollectionViewSource> <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> yöntemini kullanarak öğesine bir başvuru alın <xref:System.Windows.Data.CollectionViewSource> .

    [!code-csharp[DataGrid_GroupSortFilter#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#102)]
    [!code-vb[DataGrid_GroupSortFilter#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#102)]

## <a name="grouping-items-in-a-datagrid"></a>DataGrid içinde öğeleri gruplandırma

Öğelerin bir içinde nasıl gruplandığını belirtmek için, <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Data.PropertyGroupDescription> türü kaynak görünümündeki öğeleri gruplandırmak üzere kullanın.

### <a name="to-group-items-in-a-datagrid-using-xaml"></a>XAML kullanarak bir DataGrid içindeki öğeleri gruplandırmak için

1. <xref:System.Windows.Data.PropertyGroupDescription>Gruplandırma ölçütü olan özelliği belirleyen bir oluştur. Özelliği XAML 'de veya kodda belirtebilirsiniz.

   1. XAML 'de, öğesini <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> Gruplandırma ölçütü olan özelliğin adına ayarlayın.

   2. Kod ' da, özelliğin adını oluşturucuya göre grupla geçirin.

2. Öğesini <xref:System.Windows.Data.PropertyGroupDescription> <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> koleksiyona ekleyin.

3. <xref:System.Windows.Data.PropertyGroupDescription> <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> Daha fazla gruplandırma düzeyi eklemek için koleksiyona ek örnekler ekleyin.

    [!code-xaml[DataGrid_GroupSortFilter#012](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#012)]
    [!code-csharp[DataGrid_GroupSortFilter#112](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#112)]
    [!code-vb[DataGrid_GroupSortFilter#112](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#112)]

4. Bir grubu kaldırmak için koleksiyondan ' ı kaldırın <xref:System.Windows.Data.PropertyGroupDescription> <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> .

5. Tüm grupları kaldırmak için <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> koleksiyonun yöntemini çağırın <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> .

    [!code-csharp[DataGrid_GroupSortFilter#114](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#114)]
    [!code-vb[DataGrid_GroupSortFilter#114](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#114)]

Öğeleri içinde gruplandırılırken <xref:System.Windows.Controls.DataGrid> , <xref:System.Windows.Controls.GroupStyle> her grubun görünümünü belirten bir tanımlayabilirsiniz. Öğesini <xref:System.Windows.Controls.GroupStyle> <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> DataGrid 'in koleksiyonuna ekleyerek uygularsınız. Birden çok gruplandırma düzeyine sahipseniz, her grup düzeyine farklı stiller uygulayabilirsiniz. Stiller tanımlandıkları sırayla uygulanır. Örneğin, iki stil tanımlarsanız, ilki en üst düzey satır gruplarına uygulanır. İkinci stil, ikinci düzeyde ve daha düşük tüm satır gruplarına uygulanır. , <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Controls.GroupStyle> <xref:System.Windows.Data.CollectionViewGroup> Grubun temsil ettiği ' dır.

### <a name="to-change-the-appearance-of-row-group-headers"></a>Satır grubu üstbilgilerinin görünümünü değiştirmek için

1. <xref:System.Windows.Controls.GroupStyle>Satır grubunun görünümünü tanımlayan bir oluştur.

2. <xref:System.Windows.Controls.GroupStyle>Etiketlerin içine yerleştirin `<DataGrid.GroupStyle>` .

    [!code-xaml[DataGrid_GroupSortFilter#003](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#003)]

## <a name="sorting-items-in-a-datagrid"></a>DataGrid 'de öğeleri sıralama

Öğelerin bir içinde nasıl sıralanacağını belirtmek için <xref:System.Windows.Controls.DataGrid> , <xref:System.ComponentModel.SortDescription> türü kaynak görünümündeki öğeleri sıralamak üzere kullanın.

### <a name="to-sort-items-in-a-datagrid"></a>DataGrid 'deki öğeleri sıralamak için

1. <xref:System.ComponentModel.SortDescription>Sıralama ölçütü olacak özelliği belirten bir oluştur. Özelliği XAML 'de veya kodda belirtebilirsiniz.

    1. XAML 'de, öğesini <xref:System.ComponentModel.SortDescription.PropertyName%2A> sıralama yapılacak özelliğin adına ayarlayın.

    2. Kod ' da, ' a ve ' a göre sıralanacak özelliğin adını geçirin <xref:System.ComponentModel.ListSortDirection> .

2. Öğesini <xref:System.ComponentModel.SortDescription> <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> koleksiyona ekleyin.

3. <xref:System.ComponentModel.SortDescription> <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> Ek özelliklere göre sıralamak için koleksiyona ek örnekler ekleyin.

    [!code-xaml[DataGrid_GroupSortFilter#011](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#011)]
    [!code-csharp[DataGrid_GroupSortFilter#211](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml.cs#211)]
    [!code-vb[DataGrid_GroupSortFilter#211](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#211)]

## <a name="filtering-items-in-a-datagrid"></a>DataGrid 'de öğeleri filtreleme

Bir kullanarak içindeki öğeleri filtrelemek için <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Data.CollectionViewSource> , etkinliğin işleyicisinde filtreleme mantığını sağlarsınız <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> .

### <a name="to-filter-items-in-a-datagrid"></a>DataGrid 'deki öğeleri filtrelemek için

1. Olay için bir işleyici ekleyin <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> .

2. <xref:System.Windows.Data.CollectionViewSource.Filter>Olay işleyicisinde filtreleme mantığını tanımlayın.

    Bu filtre, görünüm her yenilendiğinde uygulanır.

    [!code-xaml[DataGrid_GroupSortFilter#013](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#013)]
    [!code-csharp[DataGrid_GroupSortFilter#113](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#113)]
    [!code-vb[DataGrid_GroupSortFilter#113](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#113)]

Alternatif olarak, <xref:System.Windows.Controls.DataGrid> filtreleme mantığını sağlayan ve <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> filtreyi uygulamak için özelliğini ayarlayarak bir yöntemi oluşturarak içindeki öğeleri filtreleyebilirsiniz. Bu yöntemin bir örneğini görmek için bkz. [bir görünümdeki verileri filtreleme](../data/how-to-filter-data-in-a-view.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, içindeki verileri gruplandırma, sıralama ve filtreleme işlemlerini `Task` <xref:System.Windows.Data.CollectionViewSource> ve içindeki gruplanmış, sıralanmış ve filtrelenmiş verileri görüntülemeyi gösterir `Task` <xref:System.Windows.Controls.DataGrid> . , <xref:System.Windows.Data.CollectionViewSource> İçin olarak kullanılır <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.DataGrid> . Gruplandırma, sıralama ve filtreleme, üzerinde gerçekleştirilir <xref:System.Windows.Data.CollectionViewSource> ve <xref:System.Windows.Controls.DataGrid> Kullanıcı arabiriminde görüntülenir.

Bu örneği test etmek için DGGroupSortFilterExample adını proje adınızla eşleşecek şekilde ayarlamanız gerekecektir. Visual Basic kullanıyorsanız, için sınıf adını <xref:System.Windows.Window> aşağıdaki şekilde değiştirmeniz gerekir.

`<Window x:Class="MainWindow"`

[!code-xaml[DataGrid_GroupSortFilter#000](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#000)]
[!code-csharp[DataGrid_GroupSortFilter#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#100)]
[!code-vb[DataGrid_GroupSortFilter#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#100)]

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [ObservableCollection oluşturma ve bağlama](../data/how-to-create-and-bind-to-an-observablecollection.md)
- [Görünümdeki verileri filtreleme](../data/how-to-filter-data-in-a-view.md)
- [Görünümdeki verileri sıralama](../data/how-to-sort-data-in-a-view.md)
- [XAML 'de bir görünüm kullanarak verileri sıralama ve gruplandırma](../data/how-to-sort-and-group-data-using-a-view-in-xaml.md)
