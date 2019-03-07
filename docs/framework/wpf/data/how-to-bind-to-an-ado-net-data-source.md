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
ms.openlocfilehash: 08933e67c2cc4b7ccfb6ae0c9dfde34f40e4e5f5
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465555"
---
# <a name="how-to-bind-to-an-adonet-data-source"></a><span data-ttu-id="6ad9c-102">Nasıl yapılır: ADO.NET Veri Kaynağına Bağlama</span><span class="sxs-lookup"><span data-stu-id="6ad9c-102">How to: Bind to an ADO.NET Data Source</span></span>

<span data-ttu-id="6ad9c-103">Bu örnek nasıl bağlanacağını gösterir. bir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> denetimi bir [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="6ad9c-103">This example shows how to bind a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> control to an [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] `DataSet`.</span></span>

## <a name="example"></a><span data-ttu-id="6ad9c-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="6ad9c-104">Example</span></span>

<span data-ttu-id="6ad9c-105">Bu örnekte, bir `OleDbConnection` nesne olan veri kaynağına bağlanmak için kullanılan bir `Access MDB` bağlantı dizesinde belirtilen dosya.</span><span class="sxs-lookup"><span data-stu-id="6ad9c-105">In this example, an `OleDbConnection` object is used to connect to the data source which is an `Access MDB` file that is specified in the connection string.</span></span> <span data-ttu-id="6ad9c-106">Bağlantı kurulduktan sonra bir `OleDbDataAdapter` nesnesi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6ad9c-106">After the connection is established, an `OleDbDataAdapter` object is created.</span></span> <span data-ttu-id="6ad9c-107">`OleDbDataAdapter` Nesne yürüten bir select [!INCLUDE[TLA#tla_sql](../../../../includes/tlasharptla-sql-md.md)] deyimi kayıt veritabanından alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="6ad9c-107">The `OleDbDataAdapter` object executes a select [!INCLUDE[TLA#tla_sql](../../../../includes/tlasharptla-sql-md.md)] statement to retrieve the recordset from the database.</span></span> <span data-ttu-id="6ad9c-108">Sonuçlardan [!INCLUDE[TLA2#tla_sql](../../../../includes/tla2sharptla-sql-md.md)] komut depolanır bir `DataTable` , `DataSet` çağırarak `Fill` yöntemi `OleDbDataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="6ad9c-108">The results from the [!INCLUDE[TLA2#tla_sql](../../../../includes/tla2sharptla-sql-md.md)] command are stored in a `DataTable` of the `DataSet` by calling the `Fill` method of the `OleDbDataAdapter`.</span></span> <span data-ttu-id="6ad9c-109">`DataTable` Bu örnekte adlı `BookTable`.</span><span class="sxs-lookup"><span data-stu-id="6ad9c-109">The `DataTable` in this example is named `BookTable`.</span></span> <span data-ttu-id="6ad9c-110">Bu örnek daha sonra Ayarlar <xref:System.Windows.FrameworkElement.DataContext%2A> özelliği <xref:System.Windows.Controls.ListBox> için `DataSet` nesne.</span><span class="sxs-lookup"><span data-stu-id="6ad9c-110">The example then sets the <xref:System.Windows.FrameworkElement.DataContext%2A> property of the <xref:System.Windows.Controls.ListBox> to the `DataSet` object.</span></span>

[!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
[!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]

<span data-ttu-id="6ad9c-111">Biz sonra bağlayabilirsiniz <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği <xref:System.Windows.Controls.ListBox> için `BookTable` , `DataSet`:</span><span class="sxs-lookup"><span data-stu-id="6ad9c-111">We can then bind the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to `BookTable` of the `DataSet`:</span></span>

[!code-xaml[ADODataSet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]

<span data-ttu-id="6ad9c-112">`BookItemTemplate` olan <xref:System.Windows.DataTemplate> verinin nasıl göründüğünü tanımlar:</span><span class="sxs-lookup"><span data-stu-id="6ad9c-112">`BookItemTemplate` is the <xref:System.Windows.DataTemplate> that defines how the data appears:</span></span>

[!code-xaml[ADODataSet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]

<span data-ttu-id="6ad9c-113">`IntColorConverter` Dönüştürür bir `int` bir renk.</span><span class="sxs-lookup"><span data-stu-id="6ad9c-113">The `IntColorConverter` converts an `int` to a color.</span></span> <span data-ttu-id="6ad9c-114">Bu dönüştürücü kullanarak <xref:System.Windows.Controls.TextBlock.Background%2A> üçüncü rengini <xref:System.Windows.Controls.TextBlock> yeşil görünür değilse değerini `NumPages` Aksi takdirde 350'den küçük ve kırmızı olur.</span><span class="sxs-lookup"><span data-stu-id="6ad9c-114">With the use of this converter, the <xref:System.Windows.Controls.TextBlock.Background%2A> color of the third <xref:System.Windows.Controls.TextBlock> appears green if the value of `NumPages` is less than 350 and red otherwise.</span></span> <span data-ttu-id="6ad9c-115">Dönüştürücü uygulanması burada gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="6ad9c-115">The implementation of the converter is not shown here.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ad9c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ad9c-116">See also</span></span>

- <xref:System.Windows.Data.BindingListCollectionView>
- [<span data-ttu-id="6ad9c-117">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6ad9c-117">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="6ad9c-118">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="6ad9c-118">How-to Topics</span></span>](data-binding-how-to-topics.md)
