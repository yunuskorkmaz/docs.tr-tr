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
ms.openlocfilehash: 0b3d7147f45bee5e8abd95bdc51c5f5f695cf830
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458412"
---
# <a name="how-to-bind-to-an-adonet-data-source"></a>Nasıl yapılır: ADO.NET Veri Kaynağına Bağlama

Bu örnekte, bir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> denetiminin bir ADO.NET `DataSet`nasıl bağlanacağı gösterilmektedir.

## <a name="example"></a>Örnek

Bu örnekte, bağlantı dizesinde belirtilen bir `Access MDB` dosyası olan veri kaynağına bağlanmak için bir `OleDbConnection` nesnesi kullanılır. Bağlantı kurulduktan sonra bir `OleDbDataAdapter` nesnesi oluşturulur. `OleDbDataAdapter` nesnesi bir SELECT Yapılandırılmış Sorgu Dili (SQL) ifadesini yürüterek kayıt kümesini veritabanından alır. SQL komutunun sonuçları, `OleDbDataAdapter``Fill` yöntemini çağırarak `DataSet` `DataTable` depolanır. Bu örnekteki `DataTable` `BookTable`olarak adlandırılmıştır. Örnek daha sonra <xref:System.Windows.Controls.ListBox> <xref:System.Windows.FrameworkElement.DataContext%2A> özelliğini `DataSet` nesnesine ayarlar.

[!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
[!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]

Daha sonra <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliğini `DataSet``BookTable` bağlayabiliriz:

[!code-xaml[ADODataSet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]

`BookItemTemplate`, verilerin nasıl göründüğünü tanımlayan <xref:System.Windows.DataTemplate>:

[!code-xaml[ADODataSet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]

`IntColorConverter` bir `int` renge dönüştürür. Bu dönüştürücünün kullanımıyla, `NumPages` değeri 350 ' den küçükse üçüncü <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.TextBlock.Background%2A> rengi yeşil görünür ve aksi takdirde Red olur. Dönüştürücünün uygulanması burada gösterilmez.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Data.BindingListCollectionView>
- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
