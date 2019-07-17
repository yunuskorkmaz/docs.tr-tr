---
title: 'Nasıl yapılır: ADO.NET Veri Kaynağına Bağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to ADO.NET data sources
- ADO.NET data sources [WPF], binding to
- binding [WPF], to ADO.NET data sources
ms.assetid: a70c6d7b-7b38-4fdf-b655-4804db7c8315
ms.openlocfilehash: 96f846db3f705972a4749460bf2c410483258572
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238421"
---
# <a name="how-to-bind-to-an-adonet-data-source"></a>Nasıl yapılır: ADO.NET Veri Kaynağına Bağlama

Bu örnek nasıl bağlanacağını gösterir. bir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> ADO.NET denetimine `DataSet`.

## <a name="example"></a>Örnek

Bu örnekte, bir `OleDbConnection` nesne olan veri kaynağına bağlanmak için kullanılan bir `Access MDB` bağlantı dizesinde belirtilen dosya. Bağlantı kurulduktan sonra bir `OleDbDataAdapter` nesnesi oluşturulur. `OleDbDataAdapter` Nesne yürüten bir select [!INCLUDE[TLA#tla_sql](../../../../includes/tlasharptla-sql-md.md)] deyimi kayıt veritabanından alınamıyor. Sonuçlardan [!INCLUDE[TLA2#tla_sql](../../../../includes/tla2sharptla-sql-md.md)] komut depolanır bir `DataTable` , `DataSet` çağırarak `Fill` yöntemi `OleDbDataAdapter`. `DataTable` Bu örnekte adlı `BookTable`. Bu örnek daha sonra Ayarlar <xref:System.Windows.FrameworkElement.DataContext%2A> özelliği <xref:System.Windows.Controls.ListBox> için `DataSet` nesne.

[!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
[!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]

Biz sonra bağlayabilirsiniz <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği <xref:System.Windows.Controls.ListBox> için `BookTable` , `DataSet`:

[!code-xaml[ADODataSet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]

`BookItemTemplate` olan <xref:System.Windows.DataTemplate> verinin nasıl göründüğünü tanımlar:

[!code-xaml[ADODataSet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]

`IntColorConverter` Dönüştürür bir `int` bir renk. Bu dönüştürücü kullanarak <xref:System.Windows.Controls.TextBlock.Background%2A> üçüncü rengini <xref:System.Windows.Controls.TextBlock> yeşil görünür değilse değerini `NumPages` Aksi takdirde 350'den küçük ve kırmızı olur. Dönüştürücü uygulanması burada gösterilmez.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Data.BindingListCollectionView>
- [Veri Bağlamaya Genel Bakış](data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
