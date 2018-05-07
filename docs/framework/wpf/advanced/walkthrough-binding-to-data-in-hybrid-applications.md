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
ms.openlocfilehash: fe8826a390abd370361b84f99540b8dacbdedc5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-binding-to-data-in-hybrid-applications"></a>İzlenecek yol: Karma Uygulamalarda Veriye Bağlama
Bir veri kaynağı bir denetime bağlama olup, arka plandaki verilere erişimi olan kullanıcılar sağlamak için temel kullanmakta olduğunuz [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] veya [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Bu kılavuzda her ikisini de içeren karma uygulamalarda veri bağlamasını nasıl kullanabileceğinizi gösterir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrol eder.  
  
 Bu örneklerde gösterilen görevler aşağıdakileri içerir:  
  
-   Projeyi oluşturma.  
  
-   Veri şablonu tanımlama.  
  
-   Form düzenini belirtme.  
  
-   Veri bağlamalarını belirtme.  
  
-   Birlikte çalışabilirlik kullanarak verileri görüntüleme.  
  
-   Veri kaynağı projesine ekleniyor.  
  
-   Veri kaynağına bağlama.  
  
 Bu örneklerde gösterilen görevlerin tam kod listesi için bkz: [karma uygulamalar için örnek veri bağlamada](http://go.microsoft.com/fwlink/?LinkID=159983).  
  
 İşiniz bittiğinde, karma uygulamalarda veri bağlama özellikleri anlaşılması gerekir.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
-   Microsoft SQL Server üzerinde çalışan Northwind örnek veritabanı erişimi.  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
  
#### <a name="to-create-and-set-up-the-project"></a>Oluşturun ve projeyi ayarlamak için  
  
1.  Adlı bir WPF uygulaması projesi oluşturduğunuzda `WPFWithWFAndDatabinding`.  
  
2.  Çözüm Gezgini'nde, aşağıdaki derlemeler başvurular ekleyin.  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  MainWindow.xaml içinde açmak [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
4.  İçinde <xref:System.Windows.Window> öğesi, aşağıdaki ekleyin [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ad alanlarını eşleme.  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  Varsayılan ad <xref:System.Windows.Controls.Grid> öğesi `mainGrid` atayarak <xref:System.Windows.FrameworkElement.Name%2A> özelliği.  
  
     [!code-xaml[WPFWithWFAndDatabinding#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]  
  
## <a name="defining-the-data-template"></a>Veri şablonu tanımlama  
 Müşterilerin ana listesi görüntülenir bir <xref:System.Windows.Controls.ListBox> denetim. Aşağıdaki kod örneğinde tanımlayan bir <xref:System.Windows.DataTemplate> adlı nesne `ListItemsTemplate` görsel ağacını denetleyen <xref:System.Windows.Controls.ListBox> denetim. Bu <xref:System.Windows.DataTemplate> atandığı <xref:System.Windows.Controls.ListBox> denetimin <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> özelliği.  
  
#### <a name="to-define-the-data-template"></a>Veri şablonu tanımlamak için  
  
-   Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğenin bildirimi.  
  
     [!code-xaml[WPFWithWFAndDatabinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]  
  
## <a name="specifying-the-form-layout"></a>Form düzenini belirtme  
 Form düzenini üç satır ve üç sütun içeren bir kılavuz olarak tanımlanır. <xref:System.Windows.Controls.Label> denetimleri, müşterilerin tablodaki her sütun tanımlamak için sağlanmıştır.  
  
#### <a name="to-set-up-the-grid-layout"></a>Kılavuz düzeni kurmak için  
  
-   Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğenin bildirimi.  
  
     [!code-xaml[WPFWithWFAndDatabinding#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]  
  
#### <a name="to-set-up-the-label-controls"></a>Etiket denetimlerini kurmak için  
  
-   Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğenin bildirimi.  
  
     [!code-xaml[WPFWithWFAndDatabinding#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]  
  
## <a name="specifying-data-bindings"></a>Veri bağlama belirtme  
 Müşterilerin ana listesi görüntülenir bir <xref:System.Windows.Controls.ListBox> denetim. Ekli `ListItemsTemplate` bağlar bir <xref:System.Windows.Controls.TextBlock> denetimini `ContactName` veritabanından alan.  
  
 Her bir müşteri kaydı ayrıntılarını birkaç içinde görüntülenen <xref:System.Windows.Controls.TextBox> kontrol eder.  
  
#### <a name="to-specify-data-bindings"></a>Veri bağlamalarını belirtmek için  
  
-   Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğenin bildirimi.  
  
     <xref:System.Windows.Data.Binding> Sınıf bağlamalar <xref:System.Windows.Controls.TextBox> veritabanı uygun alanlara denetimleri.  
  
     [!code-xaml[WPFWithWFAndDatabinding#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]  
  
## <a name="displaying-data-by-using-interoperation"></a>Birlikte çalışabilirlik kullanarak verileri görüntüleme  
 Seçili müşteriye karşılık gelen siparişler görüntülenen bir <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> adlı Denetim `dataGridView1`. `dataGridView1` Denetim arka plan kod dosyası içindeki veri kaynağına bağlanır. A <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimidir bu üst [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetim.  
  
#### <a name="to-display-data-in-the-datagridview-control"></a>DataGridView denetiminde verileri görüntülemek için  
  
-   Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğenin bildirimi.  
  
     [!code-xaml[WPFWithWFAndDatabinding#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]  
  
## <a name="adding-the-data-source-to-the-project"></a>Projeye veri kaynağı ekleme  
 Visual Studio ile bir veri kaynağı projenize kolayca ekleyebilirsiniz. Bu yordam, kesin türü belirtilmiş veri kümesi projenize ekler. Seçilen tabloların her biri için tablo bağdaştırıcıları gibi diğer destek sınıfları de eklenir.  
  
#### <a name="to-add-the-data-source"></a>Veri kaynağı eklemek için  
  
1.  Gelen **veri** menüsünde, select **yeni veri kaynağı Ekle**.  
  
2.  İçinde **veri kaynağı Yapılandırma Sihirbazı**, bir veri kümesini kullanarak Northwind veritabanına bağlantı oluşturun. Daha fazla bilgi için bkz: [nasıl yapılır: bir veritabanındaki verilere bağlanma](http://msdn.microsoft.com/library/6c56e54e-8834-4297-85aa-cc1a443ba556).  
  
3.  Tarafından istendiğinde **veri kaynağı Yapılandırma Sihirbazı**, bağlantı dizesi olarak Kaydet `NorthwindConnectionString`.  
  
4.  Veritabanı nesnelerinizi seçin istendiğinde seçin `Customers` ve `Orders` tablolar ve üretilen veri kümesi adı `NorthwindDataSet`.  
  
## <a name="binding-to-the-data-source"></a>Veri kaynağına bağlama  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> Bileşeni, uygulamanın veri kaynağı için Tekdüzen arabirimi sağlar. Veri kaynağına bağlama arka plan kod dosyasına uygulanır.  
  
#### <a name="to-bind-to-the-data-source"></a>Veri kaynağına bağlanmak için  
  
1.  MainWindow.xaml.vb veya MainWindow.xaml.cs adlı arka plan kodu dosyasını açın.  
  
2.  Aşağıdaki kodu kopyalayın `MainWindow` sınıf tanımının.  
  
     Bu kod bildirir <xref:System.Windows.Forms.BindingSource> bileşeni ve veritabanına bağlanan ilişkili yardımcı sınıfları.  
  
     [!code-csharp[WPFWithWFAndDatabinding#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]  
  
3.  Aşağıdaki kod oluşturucuya kopyalayın.  
  
     Bu kod oluşturur ve başlatır <xref:System.Windows.Forms.BindingSource> bileşeni.  
  
     [!code-csharp[WPFWithWFAndDatabinding#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]  
  
4.  MainWindow.xaml açın.  
  
5.  Tasarım görünümü ya da XAML görünümdeki seçmek <xref:System.Windows.Window> öğesi.  
  
6.  Özellikler penceresinde **olayları** sekmesi.  
  
7.  Çift <xref:System.Windows.FrameworkElement.Loaded> olay.  
  
8.  Aşağıdaki kodu kopyalayın <xref:System.Windows.FrameworkElement.Loaded> olay işleyicisi.  
  
     Bu kodu atar <xref:System.Windows.Forms.BindingSource> veri bağlamı olarak bileşen ve doldurur `Customers` ve `Orders` bağdaştırıcısı nesneleri.  
  
     [!code-csharp[WPFWithWFAndDatabinding#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]  
  
9. Aşağıdaki kodu kopyalayın `MainWindow` sınıf tanımının.  
  
     Bu yöntem işleme <xref:System.Windows.Data.CollectionView.CurrentChanged> olay ve veri bağlamanın geçerli öğesini güncelleştirir.  
  
     [!code-csharp[WPFWithWFAndDatabinding#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]  
  
10. Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [WPF Tasarımcısı](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [Veri bağlama karma uygulamalar örneği](http://go.microsoft.com/fwlink/?LinkID=159983)  
 [İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
