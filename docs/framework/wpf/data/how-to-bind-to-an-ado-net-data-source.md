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
# <a name="how-to-bind-to-an-adonet-data-source"></a><span data-ttu-id="3d4c0-102">Nasıl yapılır: ADO.NET Veri Kaynağına Bağlama</span><span class="sxs-lookup"><span data-stu-id="3d4c0-102">How to: Bind to an ADO.NET Data Source</span></span>

<span data-ttu-id="3d4c0-103">Bu örnekte, bir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> denetiminin bir ADO.NET `DataSet`nasıl bağlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3d4c0-103">This example shows how to bind a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> control to an ADO.NET `DataSet`.</span></span>

## <a name="example"></a><span data-ttu-id="3d4c0-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="3d4c0-104">Example</span></span>

<span data-ttu-id="3d4c0-105">Bu örnekte, bağlantı dizesinde belirtilen bir `Access MDB` dosyası olan veri kaynağına bağlanmak için bir `OleDbConnection` nesnesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3d4c0-105">In this example, an `OleDbConnection` object is used to connect to the data source which is an `Access MDB` file that is specified in the connection string.</span></span> <span data-ttu-id="3d4c0-106">Bağlantı kurulduktan sonra bir `OleDbDataAdapter` nesnesi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3d4c0-106">After the connection is established, an `OleDbDataAdapter` object is created.</span></span> <span data-ttu-id="3d4c0-107">`OleDbDataAdapter` nesnesi bir SELECT Yapılandırılmış Sorgu Dili (SQL) ifadesini yürüterek kayıt kümesini veritabanından alır.</span><span class="sxs-lookup"><span data-stu-id="3d4c0-107">The `OleDbDataAdapter` object executes a select Structured Query Language (SQL) statement to retrieve the recordset from the database.</span></span> <span data-ttu-id="3d4c0-108">SQL komutunun sonuçları, `OleDbDataAdapter``Fill` yöntemini çağırarak `DataSet` `DataTable` depolanır.</span><span class="sxs-lookup"><span data-stu-id="3d4c0-108">The results from the SQL command are stored in a `DataTable` of the `DataSet` by calling the `Fill` method of the `OleDbDataAdapter`.</span></span> <span data-ttu-id="3d4c0-109">Bu örnekteki `DataTable` `BookTable`olarak adlandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="3d4c0-109">The `DataTable` in this example is named `BookTable`.</span></span> <span data-ttu-id="3d4c0-110">Örnek daha sonra <xref:System.Windows.Controls.ListBox> <xref:System.Windows.FrameworkElement.DataContext%2A> özelliğini `DataSet` nesnesine ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3d4c0-110">The example then sets the <xref:System.Windows.FrameworkElement.DataContext%2A> property of the <xref:System.Windows.Controls.ListBox> to the `DataSet` object.</span></span>

[!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
[!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]

<span data-ttu-id="3d4c0-111">Daha sonra <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliğini `DataSet``BookTable` bağlayabiliriz:</span><span class="sxs-lookup"><span data-stu-id="3d4c0-111">We can then bind the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to `BookTable` of the `DataSet`:</span></span>

[!code-xaml[ADODataSet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]

<span data-ttu-id="3d4c0-112">`BookItemTemplate`, verilerin nasıl göründüğünü tanımlayan <xref:System.Windows.DataTemplate>:</span><span class="sxs-lookup"><span data-stu-id="3d4c0-112">`BookItemTemplate` is the <xref:System.Windows.DataTemplate> that defines how the data appears:</span></span>

[!code-xaml[ADODataSet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]

<span data-ttu-id="3d4c0-113">`IntColorConverter` bir `int` renge dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="3d4c0-113">The `IntColorConverter` converts an `int` to a color.</span></span> <span data-ttu-id="3d4c0-114">Bu dönüştürücünün kullanımıyla, `NumPages` değeri 350 ' den küçükse üçüncü <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.TextBlock.Background%2A> rengi yeşil görünür ve aksi takdirde Red olur.</span><span class="sxs-lookup"><span data-stu-id="3d4c0-114">With the use of this converter, the <xref:System.Windows.Controls.TextBlock.Background%2A> color of the third <xref:System.Windows.Controls.TextBlock> appears green if the value of `NumPages` is less than 350 and red otherwise.</span></span> <span data-ttu-id="3d4c0-115">Dönüştürücünün uygulanması burada gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="3d4c0-115">The implementation of the converter is not shown here.</span></span>

## <a name="see-also"></a><span data-ttu-id="3d4c0-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d4c0-116">See also</span></span>

- <xref:System.Windows.Data.BindingListCollectionView>
- [<span data-ttu-id="3d4c0-117">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3d4c0-117">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="3d4c0-118">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="3d4c0-118">How-to Topics</span></span>](data-binding-how-to-topics.md)
