---
title: 'İzlenecek yol: Karma Uygulamalarda Veriye Bağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- data binding [WPF interoperability]
ms.assetid: 18997e71-745a-4425-9c69-2cbce1d8669e
ms.openlocfilehash: 99f0e621c7dd56c0a26b51b4725f9fb96ab3cbf9
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197910"
---
# <a name="walkthrough-binding-to-data-in-hybrid-applications"></a>İzlenecek yol: Karma Uygulamalarda Veriye Bağlama

Bir veri kaynağını denetime bağlama, kullanıcıların [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] veya [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]kullanıp kullanmadığını temel verilere erişimi sağlamak için gereklidir. Bu izlenecek yol, hem [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hem de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri içeren karma uygulamalarda veri bağlamayı nasıl kullanabileceğinizi gösterir.

Bu izlenecek yolda gösterilen görevler şunlardır:

- Proje oluşturuluyor.

- Veri şablonunu tanımlama.

- Form düzeni belirtiliyor.

- Veri bağlamalarını belirtme.

- Birlikte çalışabilirlik kullanarak verileri görüntüleme.

- Veri kaynağı projeye ekleniyor.

- Veri kaynağına bağlanıyor.

Bu izlenecek yolda gösterilen görevlerin tüm kod listesi için bkz. [karma uygulamalar Için veri bağlama örneği](https://go.microsoft.com/fwlink/?LinkID=159983).

İşiniz bittiğinde, karma uygulamalardaki veri bağlama özelliklerinin anlaşılmasına sahip olacaksınız.

## <a name="prerequisites"></a>Prerequisites

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Visual Studio.

- Microsoft SQL Server üzerinde çalışan Northwind örnek veritabanına erişim.

## <a name="creating-the-project"></a>Projeyi Oluşturma

### <a name="to-create-and-set-up-the-project"></a>Projeyi oluşturmak ve ayarlamak için

1. `WPFWithWFAndDatabinding`adlı bir WPF uygulaması projesi oluşturun.

2. Çözüm Gezgini, aşağıdaki derlemelere başvurular ekleyin.

    - WindowsFormsIntegration

    - System. Windows. Forms

3. [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]MainWindow. xaml ' i açın.

4. <xref:System.Windows.Window> öğesinde, aşağıdaki [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ad alanı eşlemesini ekleyin.

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. <xref:System.Windows.FrameworkElement.Name%2A> özelliğini atayarak varsayılan <xref:System.Windows.Controls.Grid> öğesi `mainGrid` adlandırın.

     [!code-xaml[WPFWithWFAndDatabinding#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]

## <a name="defining-the-data-template"></a>Veri şablonunu tanımlama

Müşterilerin ana listesi bir <xref:System.Windows.Controls.ListBox> denetiminde görüntülenir. Aşağıdaki kod örneği, <xref:System.Windows.Controls.ListBox> denetiminin görsel ağacını denetleyen `ListItemsTemplate` adlı <xref:System.Windows.DataTemplate> nesnesini tanımlar. Bu <xref:System.Windows.DataTemplate> <xref:System.Windows.Controls.ListBox> denetiminin <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> özelliğine atanır.

### <a name="to-define-the-data-template"></a>Veri şablonunu tanımlamak için

- Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesinin bildirimine kopyalayın.

     [!code-xaml[WPFWithWFAndDatabinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]

## <a name="specifying-the-form-layout"></a>Form düzeni belirtme

Formun düzeni üç satır ve üç sütunlu bir kılavuz tarafından tanımlanır. Müşteriler tablosundaki her sütunu belirlemek için <xref:System.Windows.Controls.Label> denetimleri sağlanır.

### <a name="to-set-up-the-grid-layout"></a>Kılavuz yerleşimini ayarlamak için

- Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesinin bildirimine kopyalayın.

     [!code-xaml[WPFWithWFAndDatabinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]

### <a name="to-set-up-the-label-controls"></a>Etiket denetimlerini ayarlamak için

- Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesinin bildirimine kopyalayın.

     [!code-xaml[WPFWithWFAndDatabinding#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]

## <a name="specifying-data-bindings"></a>Veri bağlamalarını belirtme

Müşterilerin ana listesi bir <xref:System.Windows.Controls.ListBox> denetiminde görüntülenir. Eklenen `ListItemsTemplate`, bir <xref:System.Windows.Controls.TextBlock> denetimini veritabanındaki `ContactName` alanına bağlar.

Her müşteri kaydının ayrıntıları çeşitli <xref:System.Windows.Controls.TextBox> denetimlerinde görüntülenir.

### <a name="to-specify-data-bindings"></a>Veri bağlamalarını belirtmek için

- Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesinin bildirimine kopyalayın.

     <xref:System.Windows.Data.Binding> sınıfı, <xref:System.Windows.Controls.TextBox> denetimlerini veritabanındaki uygun alanlara bağlar.

     [!code-xaml[WPFWithWFAndDatabinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]

## <a name="displaying-data-by-using-interoperation"></a>Birlikte çalışabilirlik kullanarak verileri görüntüleme

Seçilen müşteriye karşılık gelen siparişler, `dataGridView1`adlı <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> denetiminde görüntülenir. `dataGridView1` denetimi, arka plan kod dosyasındaki veri kaynağına bağlanır. <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi bu [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetiminin üst öğesidir.

### <a name="to-display-data-in-the-datagridview-control"></a>DataGridView denetiminde verileri görüntüleme

- Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesinin bildirimine kopyalayın.

     [!code-xaml[WPFWithWFAndDatabinding#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]

## <a name="adding-the-data-source-to-the-project"></a>Veri kaynağı projeye ekleniyor

Visual Studio ile projenize kolayca veri kaynağı ekleyebilirsiniz. Bu yordam, projenize kesin olarak belirlenmiş bir veri kümesi ekler. Seçili tabloların her biri için tablo bağdaştırıcıları gibi diğer çeşitli destek sınıfları da eklenir.

### <a name="to-add-the-data-source"></a>Veri kaynağını eklemek için

1. **Veri** menüsünde **Yeni veri kaynağı Ekle**' yi seçin.

2. **Veri kaynağı Yapılandırma sihirbazında**, bir veri kümesi kullanarak Northwind veritabanına bir bağlantı oluşturun. Daha fazla bilgi için bkz. [nasıl yapılır: veritabanındaki verilere bağlanma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120)).

3. **Veri kaynağı Yapılandırma Sihirbazı**tarafından istendiğinde, bağlantı dizesini `NorthwindConnectionString`olarak kaydedin.

4. Veritabanı nesnelerinizi seçmeniz istendiğinde `Customers` ve `Orders` tabloları seçip oluşturulan veri kümesini `NorthwindDataSet`adlandırın.

## <a name="binding-to-the-data-source"></a>Veri kaynağına bağlama

<xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> bileşeni, uygulamanın veri kaynağı için tekdüzen arabirimi sağlar. Veri kaynağına bağlama, arka plan kod dosyasında uygulanır.

### <a name="to-bind-to-the-data-source"></a>Veri kaynağına bağlamak için

1. MainWindow. xaml. vb veya MainWindow.xaml.cs adlı arka plan kod dosyasını açın.

2. Aşağıdaki kodu `MainWindow` sınıf tanımına kopyalayın.

     Bu kod, <xref:System.Windows.Forms.BindingSource> bileşenini ve veritabanına bağlanan ilişkili yardımcı sınıfları bildirir.

     [!code-csharp[WPFWithWFAndDatabinding#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]

3. Oluşturucuya aşağıdaki kodu kopyalayın.

     Bu kod <xref:System.Windows.Forms.BindingSource> bileşenini oluşturur ve başlatır.

     [!code-csharp[WPFWithWFAndDatabinding#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]

4. MainWindow. xaml ' i açın.

5. Tasarım görünümü veya XAML görünümünde <xref:System.Windows.Window> öğesini seçin.

6. Özellikler penceresi, **Olaylar** sekmesine tıklayın.

7. <xref:System.Windows.FrameworkElement.Loaded> olayına çift tıklayın.

8. Aşağıdaki kodu <xref:System.Windows.FrameworkElement.Loaded> olay işleyicisine kopyalayın.

     Bu kod, <xref:System.Windows.Forms.BindingSource> bileşenini veri bağlamı olarak atar ve `Customers` ve `Orders` bağdaştırıcı nesnelerini doldurur.

     [!code-csharp[WPFWithWFAndDatabinding#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]

9. Aşağıdaki kodu `MainWindow` sınıf tanımına kopyalayın.

     Bu yöntem <xref:System.Windows.Data.CollectionView.CurrentChanged> olayını işler ve veri bağlamasının geçerli öğesini güncelleştirir.

     [!code-csharp[WPFWithWFAndDatabinding#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]

10. Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Visual Studio’da XAML tasarlama](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Karma uygulamalarda veri bağlama örneği](https://go.microsoft.com/fwlink/?LinkID=159983)
- [İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
