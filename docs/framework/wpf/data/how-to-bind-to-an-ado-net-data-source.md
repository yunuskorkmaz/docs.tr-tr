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
ms.openlocfilehash: dbe34cba8f01320fbf37beea65ed95656e09395c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697137"
---
# <a name="how-to-bind-to-an-adonet-data-source"></a>Nasıl yapılır: ADO.NET Veri Kaynağına Bağlama

Bu örnekte, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> denetiminin bir ADO.NET `DataSet` ' ye nasıl bağlanacağı gösterilmektedir.

## <a name="example"></a>Örnek

Bu örnekte, bağlantı dizesinde belirtilen bir `Access MDB` dosyası olan veri kaynağına bağlanmak için bir `OleDbConnection` nesnesi kullanılır. Bağlantı kurulduktan sonra, `OleDbDataAdapter` nesnesi oluşturulur. @No__t-0 nesnesi bir SELECT Yapılandırılmış Sorgu Dili (SQL) ifadesini yürüterek kayıt kümesini veritabanından alır. SQL komutunun sonuçları, `OleDbDataAdapter` ' ün `Fill` yöntemini çağırarak `DataSet` ' in `DataTable` ' a depolanır. Bu örnekteki `DataTable` `BookTable` olarak adlandırılmıştır. Örnek sonra, <xref:System.Windows.Controls.ListBox> ' in <xref:System.Windows.FrameworkElement.DataContext%2A> özelliğini `DataSet` nesnesine ayarlar.

[!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
[!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]

Daha sonra <xref:System.Windows.Controls.ListBox> ' in <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliğini @no__t 3 ' ün `BookTable` ' ye bağlayabiliriz:

[!code-xaml[ADODataSet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]

`BookItemTemplate`, verilerin nasıl göründüğünü tanımlayan <xref:System.Windows.DataTemplate> ' dir:

[!code-xaml[ADODataSet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]

@No__t-0, bir `int` ' i renge dönüştürür. Bu dönüştürücünün kullanımıyla, `NumPages` değeri 350 ' den küçükse üçüncü <xref:System.Windows.Controls.TextBlock> ' in <xref:System.Windows.Controls.TextBlock.Background%2A> rengi yeşil görünür ve aksi takdirde Red olur. Dönüştürücünün uygulanması burada gösterilmez.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Data.BindingListCollectionView>
- [Veri Bağlamaya Genel Bakış](data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
