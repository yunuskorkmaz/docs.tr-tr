---
title: 'Nasıl yapılır: LINQ Kullanarak Veritabanındaki Verileri Değiştirme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inserting rows [LINQ to SQL]
- deleting rows [LINQ to SQL]
- updating rows [LINQ to SQL]
- inserting data [Visual Basic]
- deleting data
- data [Visual Basic], updating
- updating data [LINQ]
- queries [LINQ in Visual Basic], data changes in database
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: cf52635f-0c1b-46c3-aff1-bdf181cf19b1
ms.openlocfilehash: c0c00c15756ab4d488096d4311bb47986a5eb25e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a>Nasıl yapılır: LINQ Kullanarak Veritabanındaki Verileri Değiştirme (Visual Basic)
Dil ile tümleşik sorgu (LINQ) sorgularını Veritabanı bilgilerine erişmek ve veritabanını değerleri değiştirmek kolaylaştırır.  
  
 Aşağıdaki örnek, bir SQL Server veritabanında alır yeni bir uygulama oluşturma ve güncelleştirme bilgilerini gösterir.  
  
 Bu konudaki örnekler Northwind örnek veritabanı kullanır. Northwind örnek veritabanı geliştirme bilgisayarınızda yoksa, buradan indirebilirsiniz [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web sitesi. Yönergeler için bkz: [örnek veritabanları yükleme](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
### <a name="to-create-a-connection-to-a-database"></a>Bir veritabanına bir bağlantı oluşturmak için  
  
1.  Visual Studio'da açın **Sunucu Gezgini**/**Database Explorer** tıklayarak **Görünüm** menüsüne ve ardından **Sunucu Gezgini** / **Veritabanı Gezgini**.  
  
2.  Sağ **veri bağlantıları** içinde **Sunucu Gezgini**/**Database Explorer**, tıklatıp **Bağlantı Ekle**.  
  
3.  Northwind örnek veritabanı için geçerli bir bağlantı belirtin.  
  
### <a name="to-add-a-project-with-a-linq-to-sql-file"></a>SQL dosyasına bir LINQ sahip bir proje eklemek için  
  
1.  Visual Studio'da üzerinde **dosya** menüsündeki **yeni** ve ardından **proje**. Visual Basic seçin **Windows Forms uygulaması** proje türü olarak.  
  
2.  Üzerinde **proje** menüsünde tıklatın **Yeni Öğe Ekle**. Seçin **LINQ'ten SQL'e sınıflarını** öğe şablonu.  
  
3.  Dosya adı `northwind.dbml`. **Ekle**'yi tıklatın. Nesne İlişkisel Tasarımcısı (O/R Tasarımcısı) için açıldığında `northwind.dbml` dosya.  
  
### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a>Sorgulamak ve Designer'a değiştirmek için tabloları eklemek için  
  
1.  İçinde **Sunucu Gezgini**/**Database Explorer**, Northwind veritabanına bağlantı genişletin. Genişletme **tabloları** klasör.  
  
     O/R Tasarımcısı kapattıysanız, belgeyi çift tıklatarak yeniden açabilirsiniz `northwind.dbml` daha önce eklediğiniz dosya.  
  
2.  Müşteriler tablosunu tıklayın ve tasarımcı sol bölmesine sürükleyin.  
  
     Tasarımcı projeniz için yeni bir müşteri nesnesi oluşturur.  
  
3.  Değişikliklerinizi kaydetmek ve Tasarımcısı'nı kapatın.  
  
4.  Projeyi kaydedin.  
  
### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a>Veritabanını değiştirme ve sonuçları görüntülemek üzere kod eklemek için  
  
1.  Gelen **araç**, sürükleyin bir <xref:System.Windows.Forms.DataGridView> Form1 projeniz için varsayılan Windows Form denetimi.  
  
2.  O/R Tasarımcısı tabloları eklendiğinde Tasarımcı eklenen bir <xref:System.Data.Linq.DataContext> projenize nesnesi. Bu nesne Müşteriler tablosunu erişmek için kullanabileceğiniz kodu içerir. Ayrıca, yerel bir müşteri nesnesi ve tablo müşteriler koleksiyonu tanımlayan kodu içerir. <xref:System.Data.Linq.DataContext> Nesne projenizi adlı için .dbml dosyanızı adına dayalı. Bu proje için <xref:System.Data.Linq.DataContext> nesne adlandırılan `northwindDataContext`.  
  
     Bir örneğini oluşturabilirsiniz <xref:System.Data.Linq.DataContext> nesne, kod ve sorgu ve O/R tasarımcısı tarafından belirtilen müşteriler koleksiyonunu Değiştir. Müşteriler koleksiyona yaptığınız değişiklikler değil yansıtılır veritabanında bunları çağırarak gönderme kadar <xref:System.Data.Linq.DataContext.SubmitChanges%2A> yöntemi <xref:System.Data.Linq.DataContext> nesnesi.  
  
     Windows için kod eklemek için Form1, formu <xref:System.Windows.Forms.Form.Load> müşterilerin Tablo Sorgu olaya özelliği olarak gösterilir, <xref:System.Data.Linq.DataContext>. Aşağıdaki kodu ekleyin:  
  
    ```vb  
    Private db As northwindDataContext  
  
    Private Sub Form1_Load(ByVal sender As System.Object,   
                           ByVal e As System.EventArgs  
                          ) Handles MyBase.Load  
      db = New northwindDataContext()  
  
      RefreshData()  
    End Sub  
  
    Private Sub RefreshData()  
      Dim customers = From cust In db.Customers   
                      Where cust.City(0) = "W"   
                      Select cust  
  
      DataGridView1.DataSource = customers  
    End Sub  
    ```  
  
3.  Gelen **araç**, üç sürükleyin <xref:System.Windows.Forms.Button> forma kontrol eder. İlk seçin `Button` denetim. İçinde **özellikleri** penceresindeki ayarlayın `Name` , `Button` denetimini `AddButton` ve `Text` için `Add`. İkinci düğmesini seçin ve ayarlayın `Name` özelliğine `UpdateButton` ve `Text` özelliğine `Update`. Üçüncü düğmesini seçin ve ayarlayın `Name` özelliğine `DeleteButton` ve `Text` özelliğine `Delete`.  
  
4.  Çift **Ekle** kodu eklemek için düğmeyi kendi `Click` olay. Aşağıdaki kodu ekleyin:  
  
    ```vb  
    Private Sub AddButton_Click(ByVal sender As System.Object,   
                                ByVal e As System.EventArgs  
                               ) Handles AddButton.Click  
      Dim cust As New Customer With {   
        .City = "Wellington",   
        .CompanyName = "Blue Yonder Airlines",   
        .ContactName = "Jill Frank",   
        .Country = "New Zealand",   
        .CustomerID = "JILLF"}  
  
      db.Customers.InsertOnSubmit(cust)  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
5.  Çift **güncelleştirme** kodu eklemek için düğmeyi kendi `Click` olay. Aşağıdaki kodu ekleyin:  
  
    ```vb  
    Private Sub UpdateButton_Click(ByVal sender As System.Object, _  
                                   ByVal e As System.EventArgs  
                                  ) Handles UpdateButton.Click  
      Dim updateCust = (From cust In db.Customers   
                        Where cust.CustomerID = "JILLF").ToList()(0)  
  
      updateCust.ContactName = "Jill Shrader"  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
6.  Çift **silmek** kodu eklemek için düğmeyi kendi `Click` olay. Aşağıdaki kodu ekleyin:  
  
    ```vb  
    Private Sub DeleteButton_Click(ByVal sender As System.Object, _  
                                   ByVal e As System.EventArgs  
                                  ) Handles DeleteButton.Click  
      Dim deleteCust = (From cust In db.Customers   
                        Where cust.CustomerID = "JILLF").ToList()(0)  
  
      db.Customers.DeleteOnSubmit(deleteCust)  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
7.  Projenizi çalıştırmak için F5 tuşuna basın. Tıklatın **Ekle** yeni bir kayıt eklemek için. Tıklatın **güncelleştirme** yeni kayıttaki değiştirmek için. Tıklatın **silmek** yeni kaydı silinemiyor.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Sorgular](../../../../visual-basic/language-reference/queries/queries.md)  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
 [DataContext yöntemleri (O/R Tasarımcısı)](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [Nasıl yapılır: güncelleştirme, ekleme ve silme (O/R Tasarımcısı) gerçekleştirmek için saklı yordamlar atayın](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)
