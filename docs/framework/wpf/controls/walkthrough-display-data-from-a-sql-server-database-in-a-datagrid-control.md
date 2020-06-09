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
ms.openlocfilehash: 1398d8408a0b85d6603d638312e92ba35c5e77d3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591039"
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a>İzlenecek yol: DataGrid Denetimindeki SQL Server veritabanından veri görüntüleme

Bu kılavuzda, verileri bir SQL Server veritabanından alır ve bu verileri bir denetimde görüntüleriz <xref:System.Windows.Controls.DataGrid> . Verileri temsil eden varlık sınıflarını oluşturmak için ADO.NET Entity Framework kullanır ve bir varlık sınıfından belirtilen verileri alan bir sorgu yazmak için LINQ kullanın.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Visual Studio.

- Üzerinde AdventureWorks örnek veritabanının eklendiği SQL Server veya SQL Server Express çalışan bir örneğine erişim. AdventureWorks veritabanını [GitHub](https://github.com/Microsoft/sql-server-samples/releases)'dan indirebilirsiniz.

## <a name="create-entity-classes"></a>Varlık sınıfları oluşturma

1. Visual Basic veya C# ' de yeni bir WPF uygulaması projesi oluşturun ve bunu adlandırın `DataGridSQLExample` .

2. Çözüm Gezgini, projenize sağ tıklayın, **Ekle**' nin üzerine gelin ve sonra **Yeni öğe**' yi seçin.

     Yeni Öğe Ekle iletişim kutusu görünür.

3. Yüklü şablonlar bölmesinde, **veriler** ' i seçin ve şablonlar listesinde **ADO.net varlık veri modeli**' yi seçin.

     ![ADO.NET Varlık Veri Modeli öğesi şablonu](../../wcf/feature-details/media/ado-net-entity-data-model-item-template.png)

4. Dosyayı adlandırın `AdventureWorksModel.edmx` ve ardından **Ekle**' ye tıklayın.

     Varlık Veri Modeli Sihirbazı görüntülenir.

5. Model Içeriğini seçin ekranında, **veritabanından EF Designer** ' ı seçin ve ardından **İleri**' ye tıklayın.

6. Veri bağlantınızı seçin ekranında AdventureWorksLT2008 veritabanınıza bağlantı sağlayın. Daha fazla bilgi için bkz. [veri bağlantınızı seçme Iletişim kutusu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399244(v=vs.100)).

    Adın olduğundan `AdventureWorksLT2008Entities` ve **app. config dosyasındaki varlık bağlantı ayarlarını kaydet** onay kutusunun seçili olduğundan emin olun ve ardından **İleri**' ye tıklayın.

7. Veritabanı nesnelerinizi seçin ekranında, tablolar düğümünü genişletin ve **Product** ve **ProductCategory** tablolarını seçin.

     Tüm tablolar için varlık sınıfları oluşturabilirsiniz; Ancak, bu örnekte yalnızca bu iki tablodan veri alınır.

     ![Tablolardan Product ve ProductCategory seçin](./media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")

8. **Son**'a tıklayın.

     Product ve ProductCategory varlıkları Entity Desisgner görüntülenir.

     ![Product ve ProductCategory varlık modelleri](./media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")

## <a name="retrieve-and-present-the-data"></a>Verileri alma ve sunma

1. MainWindow. xaml dosyasını açın.

2. <xref:System.Windows.FrameworkElement.Width%2A>Özelliğini <xref:System.Windows.Window> 450 olarak ayarlayın.

3. XAML düzenleyicisinde, <xref:System.Windows.Controls.DataGrid> `<Grid>` `</Grid>` bir adlandırılmış eklemek için ve etiketlerinin arasına aşağıdaki etiketi ekleyin <xref:System.Windows.Controls.DataGrid> `dataGrid1` .

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]

     ![DataGrid ile pencere](./media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")

4. Öğesini seçin <xref:System.Windows.Window> .

5. Özellikler penceresi veya XAML düzenleyicisini kullanarak, <xref:System.Windows.Window> olay için adlandırılmış bir olay işleyicisi oluşturun `Window_Loaded` <xref:System.Windows.FrameworkElement.Loaded> . Daha fazla bilgi için bkz. [nasıl yapılır: basit olay Işleyicisi oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).

     Aşağıda MainWindow. xaml için XAML gösterilmektedir.

    > [!NOTE]
    > Visual Basic kullanıyorsanız, MainWindow. xaml ' in ilk satırında `x:Class="DataGridSQLExample.MainWindow"` ile değiştirin `x:Class="MainWindow"` .

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]

6. İçin arka plan kod dosyasını (MainWindow. xaml. vb veya MainWindow.xaml.cs) açın <xref:System.Windows.Window> .

7. Birleşik tablolardan yalnızca belirli değerleri almak için aşağıdaki kodu ekleyin ve <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> öğesinin özelliğini <xref:System.Windows.Controls.DataGrid> sorgunun sonuçlarına ayarlayın.

     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]

8. Örneği çalıştırın.

     Verileri görüntüleyen bir görmeniz gerekir <xref:System.Windows.Controls.DataGrid> .

     ![SQL veritabanı 'ndan veri içeren DataGrid](./media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.DataGrid>
