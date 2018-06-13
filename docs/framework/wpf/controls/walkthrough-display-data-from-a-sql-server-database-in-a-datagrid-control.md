---
title: 'İzlenecek yol: DataGrid Denetimindeki SQL Server Veritabanından Veri Görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], displaying data from SQL Server
- controls [WPF], DataGrid
ms.assetid: 6810b048-0a23-4f86-bfa5-97f92b3cfab4
ms.openlocfilehash: 230d2c6843f9ae80126d9d0a2c949982aae24c76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557465"
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a>İzlenecek yol: DataGrid Denetimindeki SQL Server Veritabanından Veri Görüntüleme
Bu kılavuzda, bir SQL Server veritabanından veri almak ve bu verileri görüntüleyen bir <xref:System.Windows.Controls.DataGrid> denetim. ADO.NET Entity Framework verileri temsil eder ve LINQ varlık sınıfından belirtilen verileri alan bir sorgu yazmak için kullanabileceğiniz varlık sınıfları oluşturmak için kullanın.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
-   SQL Server ya da ekli AdventureWorks örnek veritabanının bulunduğu SQL Server Express'in çalışan örneğine erişim. AdventureWorks veritabanından indirebilirsiniz [GitHub](https://github.com/Microsoft/sql-server-samples/releases).  
  
### <a name="to-create-entity-classes"></a>Varlık sınıfları oluşturmak için  
  
1.  Visual Basic veya C# içinde yeni bir WPF uygulama projesi oluşturun ve adlandırın `DataGridSQLExample`.  
  
2.  Çözüm Gezgini'nde projenize sağ tıklayın, fareyle **Ekle**ve ardından **yeni öğe**.  
  
     Yeni Öğe Ekle iletişim kutusu görüntülenir.  
  
3.  Yüklü Şablonlar bölmesinde seçin **veri** ve şablonları listesinde seçin **ADO.NET Varlık Veri modu**l.  
  
     ![ADO.NET varlık veri modeli seçin](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step1.png "DataGrid_SQL_EF_Step1")  
  
4.  Dosya adı `AdventureWorksModel.edmx` ve ardından **Ekle**.  
  
     Varlık Veri Modeli Sihirbazı görüntülenir.  
  
5.  Model içeriği seçin ekranında şunları seçin **veritabanından Oluştur** ve ardından **sonraki**.  
  
     ![Veritabanı seçeneğinden Oluştur'u seçin](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step2.png "DataGrid_SQL_EF_Step2")  
  
6.  Veri bağlantınızı seçin ekranında, AdventureWorksLT2008 veritabanına bağlantı sağlar. Daha fazla bilgi için bkz: [seçin bilgisayarınızı veri bağlantısı iletişim kutusu](http://go.microsoft.com/fwlink/?LinkId=160190).  
  
     ![Veritabanına bağlantı sağlama](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step3.png "DataGrid_SQL_EF_Step3")  
  
7.  Adı olduğundan emin olun `AdventureWorksLT2008Entities` ve **varlık bağlantı ayarlarını App.Config'de şöyle Kaydet** onay kutusu seçilidir ve ardından **sonraki**.  
  
8.  Veritabanı nesnelerinizi seçin ekranında, tablolar düğümünü genişletin ve seçin **ürün** ve **ProductCategory** tabloları.  
  
     Tüm tablolar için varlık sınıfları oluşturabilirsiniz; Ancak, bu örnekte, yalnızca iki bu tablolardaki verileri.  
  
     ![Ürün ProductCategory tablolardan seçip](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")  
  
9. **Son**'a tıklayın.  
  
     Ürün ve ProductCategory varlıklar, varlık Tasarımcısı'nda görüntülenir.  
  
     ![Ürün ve ProductCategory varlık modelleri](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")  
  
### <a name="to-retrieve-and-present-the-data"></a>Almak ve veri sunmak için  
  
1.  MainWindow.xaml dosyasını açın.  
  
2.  Ayarlama <xref:System.Windows.FrameworkElement.Width%2A> özellikte <xref:System.Windows.Window> 450.  
  
3.  XAML Düzenleyicisi'nde, aşağıdaki ekleyin <xref:System.Windows.Controls.DataGrid> arasında etiketi `<Grid>` ve `</Grid>` ekleme etiketlerle bir <xref:System.Windows.Controls.DataGrid> adlı `dataGrid1`.  
  
     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]  
  
     ![DataGrid penceresiyle](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")  
  
4.  Seçin <xref:System.Windows.Window>.  
  
5.  Özellikler penceresini veya XAML Düzenleyicisi'ni kullanarak oluşturmak için bir olay işleyicisi <xref:System.Windows.Window> adlı `Window_Loaded` için <xref:System.Windows.FrameworkElement.Loaded> olay. Daha fazla bilgi için bkz: [nasıl yapılır: basit bir olay işleyicisi oluşturun](http://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480).  
  
     Aşağıdaki XAML için MainWindow.xaml gösterir.  
  
    > [!NOTE]
    >  Visual Basic, ilk satırındaki kullanıyorsanız yerine `x:Class="DataGridSQLExample.MainWindow"` ile `x:Class="MainWindow"`.  
  
     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]  
  
6.  Arka plan kod dosyasına (MainWindow.xaml.vb veya MainWindow.xaml.cs) açık <xref:System.Windows.Window>.  
  
7.  Birleştirilmiş tablolardaki yalnızca belirli değerleri almak ve ayarlamak için aşağıdaki kodu ekleyin <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği <xref:System.Windows.Controls.DataGrid> sorgu sonuçları.  
  
     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]  
  
8.  Örneği çalıştırın.  
  
     Görmeniz gerekir bir <xref:System.Windows.Controls.DataGrid> verilerini görüntüler.  
  
     ![SQL veritabanı verileriyle DataGrid](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")  
  
## <a name="next-steps"></a>Sonraki Adımlar  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.DataGrid>  
 [I: WPF uygulamalarında Entity Framework ile çalışmaya nasıl başlayabilirim?](http://go.microsoft.com/fwlink/?LinkId=159868)
