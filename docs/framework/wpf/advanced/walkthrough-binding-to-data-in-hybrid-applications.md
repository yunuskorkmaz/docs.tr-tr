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
ms.openlocfilehash: f6fd1f2f5d0a729ee5610b81d4bfdca052a6e01e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61981818"
---
# <a name="walkthrough-binding-to-data-in-hybrid-applications"></a>İzlenecek yol: Karma Uygulamalarda Veriye Bağlama
Bir veri kaynağı bir denetime bağlama olup, temel alınan verilere erişimi olan kullanıcılar sağlamak için gerekli kullanmakta olduğunuz [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] veya [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Bu izlenecek yol, veri bağlama iki dahil karma uygulamalarda nasıl kullanabileceğinizi gösterir. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrol eder.  
  
 Bu kılavuzda gösterilen görevler aşağıdakileri içerir:  
  
- Proje oluşturuluyor.  
  
- Veri şablonu tanımlama.  
  
- Form düzenini belirtme.  
  
- Veri bağlamaları belirtme.  
  
- Birlikte çalışması kullanarak veri görüntüleme.  
  
- Veri kaynağı projeye ekleniyor.  
  
- Veri kaynağına bağlama.  
  
 Bu izlenecek yolda gösterilen görevler tam kod listesi için bkz. [karma uygulamalar için örnek veri bağlama](https://go.microsoft.com/fwlink/?LinkID=159983).  
  
 İşlemi tamamladığınızda, karma uygulamalarda veri bağlama özellikleri bir anlayışa sahip olacaksınız.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
- Visual Studio.  
  
- Microsoft SQL Server üzerinde çalışan Northwind örnek veritabanına erişim.  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
  
#### <a name="to-create-and-set-up-the-project"></a>Oluşturma ve projesi kurun  
  
1. Adlı bir WPF uygulaması projesi oluşturmak `WPFWithWFAndDatabinding`.  
  
2. Çözüm Gezgini'nde, aşağıdaki derlemelere başvurular ekleyin.  
  
    - WindowsFormsIntegration  
  
    - System.Windows.Forms  
  
3. İçinde MainWindow.xaml açın [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
4. İçinde <xref:System.Windows.Window> öğesi, aşağıdaki [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ad alanlarını eşleme.  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5. Varsayılan ad <xref:System.Windows.Controls.Grid> öğesi `mainGrid` atayarak <xref:System.Windows.FrameworkElement.Name%2A> özelliği.  
  
     [!code-xaml[WPFWithWFAndDatabinding#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]  
  
## <a name="defining-the-data-template"></a>Veri şablonu tanımlama  
 Müşteriler ana listesinde görüntülenen bir <xref:System.Windows.Controls.ListBox> denetimi. Aşağıdaki kod örneği tanımlayan bir <xref:System.Windows.DataTemplate> adlı nesne `ListItemsTemplate` görsel ağacını denetimleri <xref:System.Windows.Controls.ListBox> denetimi. Bu <xref:System.Windows.DataTemplate> atandığı <xref:System.Windows.Controls.ListBox> denetimin <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> özelliği.  
  
#### <a name="to-define-the-data-template"></a>Veri şablonu tanımlamak için  
  
- İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğenin bildirimi.  
  
     [!code-xaml[WPFWithWFAndDatabinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]  
  
## <a name="specifying-the-form-layout"></a>Form düzenini belirtme  
 Formun yerleşimini üç satır ve üç sütun içeren bir kılavuz olarak tanımlanır. <xref:System.Windows.Controls.Label> denetimleri Müşteriler tablosundaki her bir sütunu tanımlamak için sağlanmıştır.  
  
#### <a name="to-set-up-the-grid-layout"></a>Kılavuz düzeni'kurmak için  
  
- İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğenin bildirimi.  
  
     [!code-xaml[WPFWithWFAndDatabinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]  
  
#### <a name="to-set-up-the-label-controls"></a>Etiket denetimleri ayarlamak için  
  
- İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğenin bildirimi.  
  
     [!code-xaml[WPFWithWFAndDatabinding#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]  
  
## <a name="specifying-data-bindings"></a>Veri bağlama belirtme  
 Müşteriler ana listesinde görüntülenen bir <xref:System.Windows.Controls.ListBox> denetimi. Ekli `ListItemsTemplate` bağlayan bir <xref:System.Windows.Controls.TextBlock> denetimini `ContactName` veritabanından alan.  
  
 Her müşteri kaydın ayrıntılarını çeşitli görüntülenen <xref:System.Windows.Controls.TextBox> kontrol eder.  
  
#### <a name="to-specify-data-bindings"></a>Veri bağlamaları belirtmek için  
  
- İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğenin bildirimi.  
  
     <xref:System.Windows.Data.Binding> Sınıfı bağlamalar <xref:System.Windows.Controls.TextBox> veritabanında uygun alanlara denetimleri.  
  
     [!code-xaml[WPFWithWFAndDatabinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]  
  
## <a name="displaying-data-by-using-interoperation"></a>Birlikte çalışması kullanarak verileri görüntüleme  
 İse seçili müşterilerle ilgili Siparişler görüntülenen bir <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> adlı Denetim `dataGridView1`. `dataGridView1` Denetim arka plan kod dosyası veri kaynağına bağlanır. A <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimidir bu üst [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi.  
  
#### <a name="to-display-data-in-the-datagridview-control"></a>DataGridView denetiminde verileri görüntülemek için  
  
- İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğenin bildirimi.  
  
     [!code-xaml[WPFWithWFAndDatabinding#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]  
  
## <a name="adding-the-data-source-to-the-project"></a>Veri kaynağı projeye ekleniyor  
 Visual Studio ile kolayca projenize bir veri kaynağı ekleyebilirsiniz. Bu yordam, kesin türü belirtilmiş veri kümesi projenize ekler. Seçilen tabloların her biri için tablo bağdaştırıcıları gibi diğer destek sınıfları da eklenir.  
  
#### <a name="to-add-the-data-source"></a>Veri kaynağı eklemek için  
  
1. Gelen **veri** menüsünde **yeni veri kaynağı Ekle**.  
  
2. İçinde **veri kaynağı Yapılandırma Sihirbazı**, bir veri kümesini kullanarak Northwind veritabanına bağlantı oluşturun. Daha fazla bilgi için [nasıl yapılır: Bir veritabanındaki verilere bağlanma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120)).  
  
3. Tarafından istendiğinde **veri kaynağı Yapılandırma Sihirbazı**, bağlantı dizesi olarak Kaydet `NorthwindConnectionString`.  
  
4. Veritabanı nesnelerinizi seçin. sorulduğunda `Customers` ve `Orders` tabloları ve oluşturulan veri kümesi adı `NorthwindDataSet`.  
  
## <a name="binding-to-the-data-source"></a>Veri kaynağına bağlama  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> Bileşeni, uygulamanın veri kaynağı için tek tip arabirim sağlar. Veri kaynağına bağlama arka plan kod dosyasında uygulanır.  
  
#### <a name="to-bind-to-the-data-source"></a>Veri kaynağına bağlamak için  
  
1. MainWindow.xaml.vb veya MainWindow.xaml.cs adlı arka plan kod dosyasını açın.  
  
2. Aşağıdaki kodu kopyalayın `MainWindow` sınıf tanımını.  
  
     Bu kod bildirir <xref:System.Windows.Forms.BindingSource> bileşeni ve veritabanı'na bağlanma ilişkili yardımcı sınıfları.  
  
     [!code-csharp[WPFWithWFAndDatabinding#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]

3. Aşağıdaki kod oluşturucuya kopyalayın.

     Bu kod oluşturur ve başlatır <xref:System.Windows.Forms.BindingSource> bileşeni.

     [!code-csharp[WPFWithWFAndDatabinding#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]

4. Open MainWindow.xaml.

5. Tasarım görünümü veya XAML görünümünde seçin <xref:System.Windows.Window> öğesi.

6. Özellikler penceresinde tıklayın **olayları** sekmesi.

7. Çift <xref:System.Windows.FrameworkElement.Loaded> olay.

8. Aşağıdaki kodu kopyalayın <xref:System.Windows.FrameworkElement.Loaded> olay işleyicisi.

     Bu kod atar <xref:System.Windows.Forms.BindingSource> veri bağlamı olarak bileşen ve dolduran `Customers` ve `Orders` bağdaştırıcısı nesneleri.

     [!code-csharp[WPFWithWFAndDatabinding#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]

9. Aşağıdaki kodu kopyalayın `MainWindow` sınıf tanımını.

     Bu yöntem işleme <xref:System.Windows.Data.CollectionView.CurrentChanged> olay ve geçerli veri bağlama öğesini güncelleştirir.

     [!code-csharp[WPFWithWFAndDatabinding#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]  
  
10. Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Visual Studio’da XAML tasarlama](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Veri bağlama karma uygulamaları örneği](https://go.microsoft.com/fwlink/?LinkID=159983)
- [İzlenecek yol: WPF'de Windows Forms bileşik denetimini barındırma](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [İzlenecek yol: WPF bileşik denetimini Windows Forms içinde barındırma](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
