---
title: 'Nasıl yapılır: DataGrid Denetiminde Verileri Gruplandırma, Sıralama ve Filtreleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], sort
- DataGrid [WPF], group
- DataGrid [WPF], filter
ms.assetid: 03345e85-89e3-4aec-9ed0-3b80759df770
ms.openlocfilehash: 675c1441201fa1578023d6ed758f389a38f3b79a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557036"
---
# <a name="how-to-group-sort-and-filter-data-in-the-datagrid-control"></a>Nasıl yapılır: DataGrid Denetiminde Verileri Gruplandırma, Sıralama ve Filtreleme
Genellikle verileri görüntülemek için yararlı bir <xref:System.Windows.Controls.DataGrid> gruplandırma, sıralama ve verileri filtreleme, farklı şekillerde. Grup, sıralamak ve verileri filtrelemek için bir <xref:System.Windows.Controls.DataGrid>, onu bağladıktan bir <xref:System.Windows.Data.CollectionView> bu işlevleri destekleyen. Ardından verileri ile çalışabilirsiniz <xref:System.Windows.Data.CollectionView> temel alınan veri kaynağını etkilemeden. Koleksiyon görünümü değişiklikleri yansıtılır <xref:System.Windows.Controls.DataGrid> kullanıcı arabirimi (UI).  
  
 <xref:System.Windows.Data.CollectionView> SAX gruplandırma ve işlevselliği uygulayan bir veri kaynağı için sıralama <xref:System.Collections.IEnumerable> arabirimi. <xref:System.Windows.Data.CollectionViewSource> Sınıf özelliklerini ayarlamanıza olanak sağlayan bir <xref:System.Windows.Data.CollectionView> XAML gelen.  
  
 Bu örnekte, bir koleksiyonu `Task` nesneleri bağlı bir <xref:System.Windows.Data.CollectionViewSource>. <xref:System.Windows.Data.CollectionViewSource> Olarak kullanılan <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> için <xref:System.Windows.Controls.DataGrid>. Gruplandırma, sıralama ve filtreleme üzerinde gerçekleştirilir <xref:System.Windows.Data.CollectionViewSource> ve görüntülenen <xref:System.Windows.Controls.DataGrid> UI.  
  
 ![Gruplandırılmış bir DataGrid verileri](../../../../docs/framework/wpf/controls/media/wpf-datagridgroups.png "WPF_DataGridGroups")  
DataGrid içinde gruplandırılmış veri  
  
## <a name="using-a-collectionviewsource-as-an-itemssource"></a>Bir CollectionViewSource bir ItemsSource kullanma  
 Grup, sıralama ve filtre verilerde bir <xref:System.Windows.Controls.DataGrid> denetimi bağlarsanız <xref:System.Windows.Controls.DataGrid> için bir <xref:System.Windows.Data.CollectionView> bu işlevleri destekleyen. Bu örnekte, <xref:System.Windows.Controls.DataGrid> bağlı bir <xref:System.Windows.Data.CollectionViewSource> için bu işlevler sağlayan bir <xref:System.Collections.Generic.List%601> , `Task` nesneleri.  
  
#### <a name="to-bind-a-datagrid-to-a-collectionviewsource"></a>DataGrid bir CollectionViewSource bağlamak için  
  
1.  Arabirimini uygulayan bir veri toplama oluşturma <xref:System.Collections.IEnumerable> arabirimi.  
  
     Kullanırsanız <xref:System.Collections.Generic.List%601> koleksiyonunuzu oluşturmak için devraldığı yeni bir sınıf oluşturmalısınız <xref:System.Collections.Generic.List%601> örneği başlatmasını yerine <xref:System.Collections.Generic.List%601>. Bu, veri bağlamak için XAML koleksiyonunda sağlar.  
  
    > [!NOTE]
    >  Koleksiyonundaki nesneleri uygulamalıdır <xref:System.ComponentModel.INotifyPropertyChanged> değiştirilen arabirimi ve <xref:System.ComponentModel.IEditableObject> arabirimi sırayla <xref:System.Windows.Controls.DataGrid> özellik değişikliklerini ve düzenlemeleri için doğru şekilde yanıt vermesi. Daha fazla bilgi için bkz: [uygulama özellik değişikliği bildirimi](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).  
  
     [!code-csharp[DataGrid_GroupSortFilter#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#101)]
     [!code-vb[DataGrid_GroupSortFilter#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#101)]  
  
2.  XAML'de koleksiyonu sınıfının bir örneğini oluşturup [x: Key yönergesi](../../../../docs/framework/xaml-services/x-key-directive.md).  
  
3.  XAML'de bir örneğini oluşturmak <xref:System.Windows.Data.CollectionViewSource> sınıfı, Ayarla [x: Key yönergesi](../../../../docs/framework/xaml-services/x-key-directive.md)ve koleksiyon sınıfınızın örneğini ayarlamak <xref:System.Windows.Data.CollectionViewSource.Source%2A>.  
  
     [!code-xaml[DataGrid_GroupSortFilter#201](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml#201)]  
  
4.  Bir örneğini oluşturmak <xref:System.Windows.Controls.DataGrid> sınıfı ve ayarlayın <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliğine <xref:System.Windows.Data.CollectionViewSource>.  
  
     [!code-xaml[DataGrid_GroupSortFilter#002](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#002)]  
  
5.  Erişim için <xref:System.Windows.Data.CollectionViewSource> da kodunuzdan kullanmak <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> bir başvuru almak için yöntemi <xref:System.Windows.Data.CollectionViewSource>.  
  
     [!code-csharp[DataGrid_GroupSortFilter#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#102)]
     [!code-vb[DataGrid_GroupSortFilter#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#102)]  
  
## <a name="grouping-items-in-a-datagrid"></a>DataGrid öğeleri gruplandırma  
 Öğeleri nasıl gruplandırılacağını belirlemek için bir <xref:System.Windows.Controls.DataGrid>, kullandığınız <xref:System.Windows.Data.PropertyGroupDescription> kaynağı görünümündeki öğeleri gruplandırmak için türü.  
  
#### <a name="to-group-items-in-a-datagrid-using-xaml"></a>XAML kullanılarak DataGrid'de öğeleri gruplandırmak için  
  
1.  Oluşturma bir <xref:System.Windows.Data.PropertyGroupDescription> grupla özelliğine belirtir. XAML veya kod özelliği belirtebilirsiniz.  
  
    1.  XAML'de ayarlamak <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> göre gruplamak için özellik adı.  
  
    2.  Kodda, özelliğin adını oluşturucusu tarafından grubuna geçirin.  
  
2.  Ekleme <xref:System.Windows.Data.PropertyGroupDescription> için <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> koleksiyonu.  
  
3.  Ek örneklerini eklemek <xref:System.Windows.Data.PropertyGroupDescription> için <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> daha fazla Gruplandırma düzeyleri eklemek için koleksiyonu.  
  
     [!code-xaml[DataGrid_GroupSortFilter#012](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#012)]  
  
     [!code-csharp[DataGrid_GroupSortFilter#112](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#112)]
     [!code-vb[DataGrid_GroupSortFilter#112](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#112)]  
  
4.  Bir grubu kaldırmak için <xref:System.Windows.Data.PropertyGroupDescription> gelen <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> koleksiyonu.  
  
5.  Tüm grupları kaldırmak için arama <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> yöntemi <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> koleksiyonu.  
  
     [!code-csharp[DataGrid_GroupSortFilter#114](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#114)]
     [!code-vb[DataGrid_GroupSortFilter#114](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#114)]  
  
 Ne zaman öğeleri gruplandırılır içinde <xref:System.Windows.Controls.DataGrid>, tanımlayabileceğiniz bir <xref:System.Windows.Controls.GroupStyle> her grubu görünümünü belirtir. Uyguladığınız <xref:System.Windows.Controls.GroupStyle> ekleyerek <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> DataGrid koleksiyonu. Gruplandırma birden çok düzeyi varsa, her grup düzeyine farklı stilleri uygulayabilirsiniz. Stilleri tanımlı sırayla uygulanır. Örneğin, iki stili tanımlarsanız, ilk üst düzey satır gruplarına uygulanır. İkinci stili ikinci düzeyde tüm satır grupları uygulanan ve daha düşük olacaktır. <xref:System.Windows.FrameworkElement.DataContext%2A> , <xref:System.Windows.Controls.GroupStyle> Olan <xref:System.Windows.Data.CollectionViewGroup> grubu temsil eden.  
  
#### <a name="to-change-the-appearance-of-row-group-headers"></a>Satır grup üstbilgileri görünümünü değiştirmek için  
  
1.  Oluşturma bir <xref:System.Windows.Controls.GroupStyle> , satır grubu görünümünü tanımlar.  
  
2.  PUT <xref:System.Windows.Controls.GroupStyle> içinde `<DataGrid.GroupStyle>` etiketler.  
  
     [!code-xaml[DataGrid_GroupSortFilter#003](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#003)]  
  
## <a name="sorting-items-in-a-datagrid"></a>DataGrid öğeleri sıralama  
 Öğeleri nasıl sıralanacağını belirtmek için bir <xref:System.Windows.Controls.DataGrid>, kullandığınız <xref:System.ComponentModel.SortDescription> kaynağı görünümündeki öğeleri sıralama türü.  
  
#### <a name="to-sort-items-in-a-datagrid"></a>DataGrid içindeki öğeleri sıralamak için  
  
1.  Oluşturma bir <xref:System.ComponentModel.SortDescription> göre sıralamak için özelliğini belirtir. XAML veya kod özelliği belirtebilirsiniz.  
  
    1.  XAML'de ayarlamak <xref:System.ComponentModel.SortDescription.PropertyName%2A> göre sıralamak için özelliğinin adı.  
  
    2.  Kod içinde göre sıralamak için özellik adını geçirmek ve <xref:System.ComponentModel.ListSortDirection> Oluşturucusu.  
  
2.  Ekleme <xref:System.ComponentModel.SortDescription> için <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> koleksiyonu.  
  
3.  Ek örneklerini eklemek <xref:System.ComponentModel.SortDescription> için <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> ek bir özelliğe göre sıralamak için koleksiyonu.  
  
     [!code-xaml[DataGrid_GroupSortFilter#011](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#011)]  
  
     [!code-csharp[DataGrid_GroupSortFilter#211](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml.cs#211)]
     [!code-vb[DataGrid_GroupSortFilter#211](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#211)]  
  
## <a name="filtering-items-in-a-datagrid"></a>DataGrid öğelerinin filtreleme  
 Öğelere filtre uygulamak için bir <xref:System.Windows.Controls.DataGrid> kullanarak bir <xref:System.Windows.Data.CollectionViewSource>, işleyicisi filtreleme mantık sağlayan <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> olay.  
  
#### <a name="to-filter-items-in-a-datagrid"></a>DataGrid öğelerinin filtre uygulamak için  
  
1.  İçin bir işleyici ekleyin <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> olay.  
  
2.  İçinde <xref:System.Windows.Data.CollectionViewSource.Filter> olay işleyicisi filtreleme mantığı tanımlayın.  
  
     Filtre görünümü her yenilendiğinde uygulanacak.  
  
     [!code-xaml[DataGrid_GroupSortFilter#013](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#013)]  
  
     [!code-csharp[DataGrid_GroupSortFilter#113](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#113)]
     [!code-vb[DataGrid_GroupSortFilter#113](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#113)]  
  
 Alternatif olarak, öğeleri filtreleyebilirsiniz bir <xref:System.Windows.Controls.DataGrid> filtreleme mantığı ve ayarı sağlayan bir yöntem oluşturarak <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> özellik filtresini uygulayın. Bu yöntemin bir örnek için bkz [görünümünde filtre veri](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, gruplandırma, sıralama ve filtreleme gösterir `Task` verileri bir <xref:System.Windows.Data.CollectionViewSource> ve sıralanmış ve filtre uygulanmış gruplandırılmış, görüntüleme `Task` verileri bir <xref:System.Windows.Controls.DataGrid>. <xref:System.Windows.Data.CollectionViewSource> Olarak kullanılan <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> için <xref:System.Windows.Controls.DataGrid>. Gruplandırma, sıralama ve filtreleme üzerinde gerçekleştirilir <xref:System.Windows.Data.CollectionViewSource> ve görüntülenen <xref:System.Windows.Controls.DataGrid> UI.  
  
 Bu örneği test etmek için proje adı ile eşleşmesi için DGGroupSortFilterExample adı ayarlamak gerekir. Visual Basic kullanıyorsanız, sınıf adını değiştirmeniz gerekir <xref:System.Windows.Window> şu.  
  
 `<Window x:Class="MainWindow"`  
  
 [!code-xaml[DataGrid_GroupSortFilter#000](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#000)]  
  
 [!code-csharp[DataGrid_GroupSortFilter#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#100)]
 [!code-vb[DataGrid_GroupSortFilter#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#100)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-  
  
## <a name="robust-programming"></a>Güçlü Programlama  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [ObservableCollection Oluşturma ve Bağlama](../../../../docs/framework/wpf/data/how-to-create-and-bind-to-an-observablecollection.md)  
 [Görünümde Veri Filtreleme](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)  
 [Görünümde Verileri Sıralama](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)  
 [XAML İçerisinde bir Görüntü Kullanarak Verileri Sıralama ve Gruplama](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)
