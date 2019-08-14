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
ms.openlocfilehash: ef5f14cdbecab8bc780cb7b2a642429970a25316
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972284"
---
# <a name="walkthrough-binding-to-data-in-hybrid-applications"></a>İzlenecek yol: Karma Uygulamalarda Veriye Bağlama

Bir veri kaynağını bir denetime bağlamak, veya [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]kullanarak kullanıcılara temel alınan verilere erişim sağlamak için gereklidir. Bu izlenecek yol, hem hem de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri içeren karma uygulamalarda veri bağlamayı nasıl kullanabileceğinizi gösterir.

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

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Visual Studio.

- Microsoft SQL Server üzerinde çalışan Northwind örnek veritabanına erişim.

## <a name="creating-the-project"></a>Projeyi Oluşturma

### <a name="to-create-and-set-up-the-project"></a>Projeyi oluşturmak ve ayarlamak için

1. Adlı `WPFWithWFAndDatabinding`bir WPF uygulaması projesi oluşturun.

2. Çözüm Gezgini, aşağıdaki derlemelere başvurular ekleyin.

    - WindowsFormsIntegration

    - System.Windows.Forms

3. İçinde MainWindow. xaml ' [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]i açın.

4. Öğesinde, aşağıdaki [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ad alanı eşlemesini ekleyin. <xref:System.Windows.Window>

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. Özelliği atayarak `mainGrid` <xref:System.Windows.Controls.Grid> varsayılanöğeyiadlandırın<xref:System.Windows.FrameworkElement.Name%2A> .

     [!code-xaml[WPFWithWFAndDatabinding#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]

## <a name="defining-the-data-template"></a>Veri şablonunu tanımlama

Müşterilerin ana listesi bir <xref:System.Windows.Controls.ListBox> denetimde görüntülenir. Aşağıdaki kod örneği, <xref:System.Windows.DataTemplate> <xref:System.Windows.Controls.ListBox> denetimin görsel ağacını denetleyen `ListItemsTemplate` adlı bir nesneyi tanımlar. Bu <xref:System.Windows.DataTemplate> , <xref:System.Windows.Controls.ListBox> denetimin<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> özelliğine atanır.

### <a name="to-define-the-data-template"></a>Veri şablonunu tanımlamak için

- Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğenin bildirimine kopyalayın.

     [!code-xaml[WPFWithWFAndDatabinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]

## <a name="specifying-the-form-layout"></a>Form düzeni belirtme

Formun düzeni üç satır ve üç sütunlu bir kılavuz tarafından tanımlanır. <xref:System.Windows.Controls.Label>Müşteriler tablosundaki her bir sütunu tanımlamak için denetimler sağlanır.

### <a name="to-set-up-the-grid-layout"></a>Kılavuz yerleşimini ayarlamak için

- Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğenin bildirimine kopyalayın.

     [!code-xaml[WPFWithWFAndDatabinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]

### <a name="to-set-up-the-label-controls"></a>Etiket denetimlerini ayarlamak için

- Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğenin bildirimine kopyalayın.

     [!code-xaml[WPFWithWFAndDatabinding#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]

## <a name="specifying-data-bindings"></a>Veri bağlamalarını belirtme

Müşterilerin ana listesi bir <xref:System.Windows.Controls.ListBox> denetimde görüntülenir. Ekli `ListItemsTemplate` bir <xref:System.Windows.Controls.TextBlock> denetimi ,veritabanındanalanabağlar.`ContactName`

Her müşteri kaydının ayrıntıları çeşitli <xref:System.Windows.Controls.TextBox> denetimlerde görüntülenir.

### <a name="to-specify-data-bindings"></a>Veri bağlamalarını belirtmek için

- Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğenin bildirimine kopyalayın.

     <xref:System.Windows.Data.Binding> Sınıfı ,<xref:System.Windows.Controls.TextBox> denetimleri veritabanındaki uygun alanlara bağlar.

     [!code-xaml[WPFWithWFAndDatabinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]

## <a name="displaying-data-by-using-interoperation"></a>Birlikte çalışabilirlik kullanarak verileri görüntüleme

Seçilen müşteriye karşılık gelen siparişler adlı <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> `dataGridView1`bir denetimde görüntülenir. `dataGridView1` Denetim, arka plan kod dosyasındaki veri kaynağına bağlanır. Denetim, bu [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimin üst öğesidir. <xref:System.Windows.Forms.Integration.WindowsFormsHost>

### <a name="to-display-data-in-the-datagridview-control"></a>DataGridView denetiminde verileri görüntüleme

- Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğenin bildirimine kopyalayın.

     [!code-xaml[WPFWithWFAndDatabinding#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]

## <a name="adding-the-data-source-to-the-project"></a>Veri kaynağı projeye ekleniyor

Visual Studio ile projenize kolayca veri kaynağı ekleyebilirsiniz. Bu yordam, projenize kesin olarak belirlenmiş bir veri kümesi ekler. Seçili tabloların her biri için tablo bağdaştırıcıları gibi diğer çeşitli destek sınıfları da eklenir.

### <a name="to-add-the-data-source"></a>Veri kaynağını eklemek için

1. **Veri** menüsünde **Yeni veri kaynağı Ekle**' yi seçin.

2. **Veri kaynağı Yapılandırma sihirbazında**, bir veri kümesi kullanarak Northwind veritabanına bir bağlantı oluşturun. Daha fazla bilgi için [nasıl yapılır: Bir veritabanındaki](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120))verilere bağlanın.

3. **Veri kaynağı Yapılandırma Sihirbazı**sorulduğunda, bağlantı dizesini olarak `NorthwindConnectionString`kaydedin.

4. Veritabanı nesnelerinizi seçmeniz istendiğinde, `Customers` ve `Orders` tablolarını seçip oluşturulan veri kümesini `NorthwindDataSet`adlandırın.

## <a name="binding-to-the-data-source"></a>Veri kaynağına bağlama

<xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> Bileşen, uygulamanın veri kaynağı için tekdüzen arabirimi sağlar. Veri kaynağına bağlama, arka plan kod dosyasında uygulanır.

### <a name="to-bind-to-the-data-source"></a>Veri kaynağına bağlamak için

1. MainWindow. xaml. vb veya MainWindow.xaml.cs adlı arka plan kod dosyasını açın.

2. Aşağıdaki kodu `MainWindow` sınıf tanımına kopyalayın.

     Bu kod, <xref:System.Windows.Forms.BindingSource> bileşeni ve veritabanına bağlanan ilişkili yardımcı sınıfları bildirir.

     [!code-csharp[WPFWithWFAndDatabinding#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]

3. Oluşturucuya aşağıdaki kodu kopyalayın.

     Bu kod <xref:System.Windows.Forms.BindingSource> bileşeni oluşturur ve başlatır.

     [!code-csharp[WPFWithWFAndDatabinding#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]

4. MainWindow. xaml ' i açın.

5. Tasarım görünümü veya xaml görünümünde <xref:System.Windows.Window> öğesini seçin.

6. Özellikler penceresi, **Olaylar** sekmesine tıklayın.

7. <xref:System.Windows.FrameworkElement.Loaded> Olaya çift tıklayın.

8. Aşağıdaki kodu <xref:System.Windows.FrameworkElement.Loaded> olay işleyicisine kopyalayın.

     Bu kod, <xref:System.Windows.Forms.BindingSource> bileşeni veri bağlamı olarak atar ve `Customers` ve `Orders` bağdaştırıcı nesnelerini doldurur.

     [!code-csharp[WPFWithWFAndDatabinding#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]

9. Aşağıdaki kodu `MainWindow` sınıf tanımına kopyalayın.

     Bu yöntem, <xref:System.Windows.Data.CollectionView.CurrentChanged> olayı işler ve veri bağlamasının geçerli öğesini güncelleştirir.

     [!code-csharp[WPFWithWFAndDatabinding#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]

10. Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Visual Studio’da XAML tasarlama](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Karma uygulamalarda veri bağlama örneği](https://go.microsoft.com/fwlink/?LinkID=159983)
- [İzlenecek yol: WPF 'de Windows Forms Bileşik denetim barındırma](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [İzlenecek yol: Windows Forms WPF bileşik denetimini barındırma](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
