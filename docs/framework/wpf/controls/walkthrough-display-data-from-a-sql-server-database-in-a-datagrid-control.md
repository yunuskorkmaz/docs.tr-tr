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
ms.openlocfilehash: 1421d076ff202ec87a9d861ab2c7d1c1cdcdc1b7
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43408196"
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a>İzlenecek yol: DataGrid Denetimindeki SQL Server Veritabanından Veri Görüntüleme
Bu kılavuzda, bir SQL Server veritabanından veri almak ve bu verileri görüntüleme bir <xref:System.Windows.Controls.DataGrid> denetimi. ADO.NET varlık çerçevesi veri temsil eder ve bir varlık sınıfı belirtilen verileri alan bir sorgu yazmak için LINQ kullanma varlık sınıfları oluşturmak için kullanın.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
-   Çalışan bir SQL Server veya SQL Server bağlı AdventureWorks örnek veritabanı içeren bir Express örneğine erişim. AdventureWorks veritabanı indirebileceğiniz [GitHub](https://github.com/Microsoft/sql-server-samples/releases).  
  
### <a name="to-create-entity-classes"></a>Varlık sınıfları oluşturmak için  
  
1.  Visual Basic veya C# içinde yeni bir WPF uygulaması projesi oluşturun ve adlandırın `DataGridSQLExample`.  
  
2.  Çözüm Gezgini'nde projenize sağ tıklayın, fareyle **Ekle**ve ardından **yeni öğe**.  
  
     Yeni Öğe Ekle iletişim kutusu görüntülenir.  
  
3.  Yüklü Şablonlar bölmesinde seçin **veri** şablonları listesinde seçip **ADO.NET Varlık Veri modu**m.  
  
     ![ADO.NET varlık veri modeli seçin](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step1.png "DataGrid_SQL_EF_Step1")  
  
4.  Dosya adı `AdventureWorksModel.edmx` ve ardından **Ekle**.  
  
     Varlık Veri Modeli Sihirbazı görüntülenir.  
  
5.  Choose Model Contents ekranında seçin **veritabanından Oluştur** ve ardından **sonraki**.  
  
     ![Veritabanı seçeneği Oluştur'u seçin](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step2.png "DataGrid_SQL_EF_Step2")  
  
6.  Veri bağlantınızı seçin ekranında AdventureWorksLT2008 veritabanınıza bağlantı sağlar. Daha fazla bilgi için [seçin bilgisayarınızı veri bağlantısı iletişim kutusu](https://go.microsoft.com/fwlink/?LinkId=160190).  
  
     ![Veritabanına bağlantı sağlama](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step3.png "DataGrid_SQL_EF_Step3")  
  
7.  Adı olduğundan emin olun `AdventureWorksLT2008Entities` ve **varlığı App.Config dosyasındaki bağlantı ayarlarını Kaydet** onay kutusunun seçili olduğundan ve ardından **sonraki**.  
  
8.  Veritabanı nesnelerinizi seçin ekranında, tablolar düğümünü genişletin ve seçin **ürün** ve **ProductCategory** tablolar.  
  
     Tüm tablolar için varlık sınıfları oluşturabilirsiniz; Ancak, bu örnekte, yalnızca bu iki tablolarından verileri alın.  
  
     ![Product ve ProductCategory tablolarından seçin](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")  
  
9. **Son**'a tıklayın.  
  
     Product ve ProductCategory varlıklar, varlık Tasarımcısı'nda görüntülenir.  
  
     ![Product ve ProductCategory varlık modelleri](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")  
  
### <a name="to-retrieve-and-present-the-data"></a>Almak ve verileri sunmak için  
  
1.  MainWindow.xaml dosyasını açın.  
  
2.  Ayarlama <xref:System.Windows.FrameworkElement.Width%2A> özelliği <xref:System.Windows.Window> 450.  
  
3.  XAML Düzenleyicisi'nde, aşağıdaki ekleyin <xref:System.Windows.Controls.DataGrid> arasında etiketi `<Grid>` ve `</Grid>` eklenecek etiketleri bir <xref:System.Windows.Controls.DataGrid> adlı `dataGrid1`.  
  
     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]  
  
     ![DataGrid penceresiyle](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")  
  
4.  Seçin <xref:System.Windows.Window>.  
  
5.  Özellikler penceresinde veya XAML Düzenleyicisi'ni kullanarak oluşturmak için bir olay işleyicisi <xref:System.Windows.Window> adlı `Window_Loaded` için <xref:System.Windows.FrameworkElement.Loaded> olay. Daha fazla bilgi için [nasıl yapılır: basit bir olay işleyicisi oluşturun](https://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480).  
  
     Aşağıdaki XAML MainWindow.xaml için gösterir.  
  
    > [!NOTE]
    >  Visual Basic kullanıyorsanız MainWindow.xaml öğesinin ilk satırı değiştirin `x:Class="DataGridSQLExample.MainWindow"` ile `x:Class="MainWindow"`.  
  
     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]  
  
6.  Arka plan kod dosyası (MainWindow.xaml.vb veya MainWindow.xaml.cs) açık <xref:System.Windows.Window>.  
  
7.  Yalnızca belirli değerleri birleştirilmiş tablolardaki almak ve ayarlamak için aşağıdaki kodu ekleyin <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği <xref:System.Windows.Controls.DataGrid> sorgu sonuçlarını.  
  
     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]  
  
8.  Örneği çalıştırın.  
  
     Görmelisiniz bir <xref:System.Windows.Controls.DataGrid> , verileri görüntüler.  
  
     ![SQL veritabanındaki verilerle DataGrid](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")  
  
## <a name="next-steps"></a>Sonraki Adımlar  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.DataGrid>  
 [Nasıl Yaparım: WPF uygulamalarında Entity Framework ile çalışmaya?](https://go.microsoft.com/fwlink/?LinkId=159868)
