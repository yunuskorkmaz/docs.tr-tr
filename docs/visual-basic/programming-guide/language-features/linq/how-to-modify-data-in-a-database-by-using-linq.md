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
ms.openlocfilehash: ebf0ed1be8d74b60b7e626db996e7cefb1c01131
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524516"
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a>Nasıl yapılır: LINQ Kullanarak Veritabanındaki Verileri Değiştirme (Visual Basic)

Dil ile tümleşik sorgu (LINQ) sorguları, veritabanı bilgilerine erişmeyi ve veritabanındaki değerleri değiştirmeyi kolaylaştırır.

Aşağıdaki örnek, SQL Server bir veritabanında bilgi alıp güncelleştiren yeni bir uygulamanın nasıl oluşturulacağını gösterir.

Bu konudaki örneklerde Northwind örnek veritabanı kullanılır. Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Indirme Merkezi ' nden indirebilirsiniz. Yönergeler için bkz. [örnek veritabanlarını indirme](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).

### <a name="to-create-a-connection-to-a-database"></a>Bir veritabanına bağlantı oluşturmak için

1. Visual Studio 'da, **Görünüm** menüsüne tıklayarak **Sunucu Gezgini** /**Veritabanı Gezgini** açın ve **Sunucu Gezgini** /**veritabanı Gezgini**' yı seçin.

2. **Sunucu Gezgini** / veritabanı Gezgini **veri bağlantıları** ' na sağtıklayın ve **bağlantı ekle**' ye tıklayın.

3. Northwind örnek veritabanına geçerli bir bağlantı belirtin.

### <a name="to-add-a-project-with-a-linq-to-sql-file"></a>LINQ to SQL dosya içeren bir proje eklemek için

1. Visual Studio 'da, **Dosya** menüsünde, **Yeni** ' nin üzerine gelin ve ardından **Proje**' ye tıklayın. Proje türü olarak Visual Basic **Windows Forms uygulaması** ' nı seçin.

2. **Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın. **LINQ to SQL sınıfları** öğe şablonunu seçin.

3. Dosyayı `northwind.dbml` olarak adlandırın. **Ekle**'yi tıklatın. Nesne İlişkisel Tasarımcısı (O/R Designer) `northwind.dbml` dosyası için açılır.

### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a>Sorguya tablo eklemek ve tasarımcıya değiştirmek için

1. **Sunucu Gezgini** /**veritabanı Gezgini**, Northwind veritabanına olan bağlantıyı genişletin. **Tablolar** klasörünü genişletin.

     O/R tasarımcısını kapattıysanız, daha önce eklediğiniz `northwind.dbml` dosyasına çift tıklayarak yeniden açabilirsiniz.

2. Müşteriler tablosuna tıklayın ve tasarımcı 'nın sol bölmesine sürükleyin.

     Tasarımcı projeniz için yeni bir müşteri nesnesi oluşturur.

3. Değişikliklerinizi kaydedin ve tasarımcıyı kapatın.

4. Projenizi kaydedin.

### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a>Veritabanını değiştirmek ve sonuçları göstermek üzere kod eklemek için

1. **Araç kutusundan**bir <xref:System.Windows.Forms.DataGridView> denetimini projeniz Için varsayılan Windows formu üzerine sürükleyin, Form1.

2. Tabloları O/R tasarımcısına eklediğinizde, tasarımcı projenize bir <xref:System.Data.Linq.DataContext> nesnesi ekledi. Bu nesne, Customers tablosuna erişmek için kullanabileceğiniz kodu içerir. Ayrıca, bir yerel müşteri nesnesini ve tablo için bir müşteriler koleksiyonunu tanımlayan kodu içerir. Projeniz için <xref:System.Data.Linq.DataContext> nesnesi,. dbml dosyanızın adına göre adlandırılır. Bu proje için <xref:System.Data.Linq.DataContext> nesnesi `northwindDataContext` olarak adlandırılmıştır.

     Kodunuzda <xref:System.Data.Linq.DataContext> nesnesinin bir örneğini oluşturabilir ve bu, O/R Tasarımcısı tarafından belirtilen müşteriler koleksiyonunu sorgulayabilir ve değiştirebilirsiniz. Müşteriler koleksiyonunda yaptığınız değişiklikler, <xref:System.Data.Linq.DataContext> nesnesinin <xref:System.Data.Linq.DataContext.SubmitChanges%2A> yöntemini çağırarak, veritabanına yansıtılmaz.

     @No__t_1 bir özellik olarak sunulan Customers tablosunu sorgulamak üzere <xref:System.Windows.Forms.Form.Load> olayına kod eklemek için Windows formunu çift tıklayın. Aşağıdaki kodu ekleyin:

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

3. **Araç kutusundan**üç <xref:System.Windows.Forms.Button> denetimini form üzerine sürükleyin. İlk `Button` denetimini seçin. **Özellikler** penceresinde, `Button` denetiminin `Name` `AddButton` ve `Text` `Add` olarak ayarlayın. İkinci düğmeyi seçin ve `Name` özelliğini `UpdateButton` ve `Text` özelliğini `Update` olarak ayarlayın. Üçüncü düğmesini seçin ve `Name` özelliğini `DeleteButton` ve `Text` özelliğini `Delete` olarak ayarlayın.

4. @No__t_1 olayına kod eklemek için **Ekle** düğmesine çift tıklayın. Aşağıdaki kodu ekleyin:

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

5. @No__t_1 olayına kod eklemek için **Güncelleştir** düğmesine çift tıklayın. Aşağıdaki kodu ekleyin:

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

6. @No__t_1 olayına kod eklemek için **Sil** düğmesine çift tıklayın. Aşağıdaki kodu ekleyin:

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

7. Projenizi çalıştırmak için F5 tuşuna basın. Yeni bir kayıt eklemek için **Ekle** ' ye tıklayın. Yeni kaydı değiştirmek için **Güncelleştir** ' e tıklayın. Yeni kaydı silmek için **Sil** ' e tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Sorgular](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [DataContext Metotları (O/R Tasarımcısı)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
