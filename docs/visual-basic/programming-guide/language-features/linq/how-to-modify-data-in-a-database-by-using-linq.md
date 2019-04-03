---
title: 'Nasıl yapılır: LINQ (Visual Basic) kullanarak bir veritabanındaki verileri değiştirme'
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
ms.openlocfilehash: c92a94cd6223aad8e4ea3da86a8dd37bd71aad2c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821003"
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a>Nasıl yapılır: LINQ (Visual Basic) kullanarak bir veritabanındaki verileri değiştirme
Dil ile tümleşik sorgu (LINQ) sorguları Veritabanı bilgilerine erişmek ve veritabanını değerleri değiştirmek kolaylaştırır.  
  
 Aşağıdaki örnek, bir SQL Server veritabanında alır, yeni bir uygulama oluşturma ve güncelleştirme bilgilerini gösterir.  
  
 Bu konudaki örnekler, Northwind örnek veritabanını kullanır. Geliştirme bilgisayarınızda bu veritabanı yoksa Microsoft Download Center'dan gelen indirebilirsiniz. Yönergeler için [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
### <a name="to-create-a-connection-to-a-database"></a>Bir veritabanına bir bağlantı oluşturmak için  
  
1.  Visual Studio'da açın **Sunucu Gezgini**/**veritabanı Gezgini** tıklayarak **görünümü** menüsüne ve ardından **SunucuGezgini** / **Veritabanı Gezgini**.  
  
2.  Sağ **veri bağlantıları** içinde **Sunucu Gezgini**/**veritabanı Gezgini**, tıklatıp **Bağlantı Ekle**.  
  
3.  Northwind örnek veritabanıyla kurulan geçerli bir bağlantı belirtin.  
  
### <a name="to-add-a-project-with-a-linq-to-sql-file"></a>Bir proje ile LINQ to SQL dosyası eklemek için  
  
1.  Visual Studio'da üzerinde **dosya** menüsünde **yeni** ve ardından **proje**. Visual Basic seçin **Windows Forms uygulaması** proje türü.  
  
2.  Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle**. Seçin **LINQ to SQL sınıfları** öğe şablonu.  
  
3.  Dosyayı `northwind.dbml` olarak adlandırın. **Ekle**'yi tıklatın. Object Relational Designer (O/R Tasarımcısı) için açıldığında `northwind.dbml` dosya.  
  
### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a>Sorgu ve tasarımcıya değiştirmek için tablolar eklemek için  
  
1.  İçinde **Sunucu Gezgini**/**veritabanı Gezgini**, Northwind veritabanına bağlantı genişletin. Genişletin **tabloları** klasör.  
  
     O/R Tasarımcısı kapattıysanız, onu çift tıklayarak açabilirsiniz `northwind.dbml` daha önce eklediğiniz dosya.  
  
2.  Müşteriler tablosu tıklayın ve tasarımcının sol bölmeye sürükleyin.  
  
     Tasarımcı, projeniz için yeni bir müşteri nesnesi oluşturur.  
  
3.  Değişikliklerinizi kaydetmek ve Tasarımcısı'nı kapatın.  
  
4.  Projenizi kaydedin.  
  
### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a>Veritabanını değiştirme ve sonuçları görüntülemek üzere kod eklemek için  
  
1.  Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.DataGridView> Form1 projeniz için varsayılan Windows Form denetimi.  
  
2.  Tasarımcı tablolar için O/R Tasarımcısı eklendiğinde, eklenen bir <xref:System.Data.Linq.DataContext> projenize nesne. Bu nesne, Müşteriler tablosunu erişmek için kullanabileceğiniz kodu içerir. Ayrıca, yerel bir müşteri nesnesi ve bir tablo için müşteri koleksiyonunun tanımlayan kodu içerir. <xref:System.Data.Linq.DataContext> Nesne projeniz için .dbml dosyanızın adına bağlı. Bu proje için <xref:System.Data.Linq.DataContext> nesne adlı `northwindDataContext`.  
  
     Bir örneği oluşturabilir <xref:System.Data.Linq.DataContext> kodunuz ve sorgu nesnesi ve O/R tasarımcısı tarafından belirtilen müşteri koleksiyonunun değiştirin. Müşteriler koleksiyona yaptığınız değişiklikler değil yansıtılır veritabanında bunları çağırarak göndermek kadar <xref:System.Data.Linq.DataContext.SubmitChanges%2A> yöntemi <xref:System.Data.Linq.DataContext> nesne.  
  
     Windows için kod eklemek için Form1, formu <xref:System.Windows.Forms.Form.Load> sorgu Müşteriler tablosu için olay özelliği olarak sunulan, <xref:System.Data.Linq.DataContext>. Aşağıdaki kodu ekleyin:  
  
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
  
3.  Gelen **araç kutusu**, üç sürükleyin <xref:System.Windows.Forms.Button> form üzerine denetimler. İlk seçin `Button` denetimi. İçinde **özellikleri** penceresinde `Name` , `Button` denetimini `AddButton` ve `Text` için `Add`. İkinci bir düğme seçip ayarlayın `Name` özelliğini `UpdateButton` ve `Text` özelliğini `Update`. Üçüncü düğmeyi seçin ve ayarlayın `Name` özelliğini `DeleteButton` ve `Text` özelliğini `Delete`.  
  
4.  Çift **Ekle** kodu eklemek için Ekle düğmesine kendi `Click` olay. Aşağıdaki kodu ekleyin:  
  
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
  
5.  Çift **güncelleştirme** kodu eklemek için Ekle düğmesine kendi `Click` olay. Aşağıdaki kodu ekleyin:  
  
    ```vb  
    Private Sub UpdateButton_Click(ByVal sender As System.Object, _  
                                   ByVal e As System.EventArgs  
                                  ) Handles UpdateButton.Click  
      Dim updateCust = (From cust In db.Customers   
                        Where cust.CustomerID = "JILLF").ToList()(0)  
  
      updateCust.ContactName = "Jill Shrader"
      updateCust.Country = "Wales"
      updateCust.CompanyName = "Red Yonder Airlines"
      updateCust.City = "Cardiff"
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
6.  Çift **Sil** kodu eklemek için Ekle düğmesine kendi `Click` olay. Aşağıdaki kodu ekleyin:  
  
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
  
7.  Projenizi çalıştırmak için F5 tuşuna basın. Tıklayın **Ekle** yeni bir kayıt eklemek için. Tıklayın **güncelleştirme** yeni bir kaydı değiştirmek için. Tıklayın **Sil** yeni kaydı silinemedi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Sorgular](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [DataContext Metotları (O/R Tasarımcısı)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
