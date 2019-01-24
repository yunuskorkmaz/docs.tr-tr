---
title: 'Nasıl yapılır: LINQ (Visual Basic) kullanarak veritabanını sorgulama'
ms.date: 07/20/2015
helpviewer_keywords:
- query samples [LINQ]
- database querying [LINQ]
- queries [LINQ in Visual Basic], database querying
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: bcf5e9c3-a236-4399-9a7f-3991eca7cf56
ms.openlocfilehash: a76eb5a010c8c5f750336935f0044e8dcc4322f5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514861"
---
# <a name="how-to-query-a-database-by-using-linq-visual-basic"></a>Nasıl yapılır: LINQ (Visual Basic) kullanarak veritabanını sorgulama
Dil ile tümleşik sorgu (LINQ), Veritabanı bilgilerine erişmek ve sorguları yürütmek kolaylaştırır.  
  
 Aşağıdaki örnek, bir SQL Server veritabanında sorgu gerçekleştiren yeni bir uygulama oluşturma işlemi gösterilmektedir.  
  
 Bu konudaki örnekler, Northwind örnek veritabanını kullanır. Geliştirme bilgisayarınızda bu veritabanı yoksa Microsoft Download Center'dan gelen indirebilirsiniz. Yönergeler için [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-create-a-connection-to-a-database"></a>Bir veritabanına bir bağlantı oluşturmak için  
  
1.  Visual Studio'da açın **Sunucu Gezgini**/**veritabanı Gezgini** tıklayarak **Sunucu Gezgini**/**veritabanı Explorer** üzerinde **görünümü** menüsü.  
  
2.  Sağ **veri bağlantıları** içinde **Sunucu Gezgini**/**veritabanı Gezgini** ve ardından **Bağlantı Ekle**.  
  
3.  Northwind örnek veritabanıyla kurulan geçerli bir bağlantı belirtin.  
  
## <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>LINQ to SQL dosyası içeren bir proje eklemek için  
  
1.  Visual Studio'da üzerinde **dosya** menüsünde **yeni** ve ardından **proje**. Visual Basic seçin **Windows Forms uygulaması** proje türü.  
  
2.  Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle**. Seçin **LINQ to SQL sınıfları** öğe şablonu.  
  
3.  Dosyayı `northwind.dbml` olarak adlandırın. **Ekle**'yi tıklatın. Object Relational Designer (O/R Tasarımcısı) için northwind.dbml dosyası açılır.  
  
## <a name="to-add-tables-to-query-to-the-or-designer"></a>O/R Tasarımcısı için sorgulamak için tablo eklemek için  
  
1.  İçinde **Sunucu Gezgini**/**veritabanı Gezgini**, Northwind veritabanına bağlantı genişletin. Genişletin **tabloları** klasör.  
  
     O/R Tasarımcısı kapattıysanız, daha önce eklediğiniz northwind.dbml dosyasına çift tıklayarak açabilirsiniz.  
  
2.  Müşteriler tablosu tıklayın ve tasarımcının sol bölmeye sürükleyin. Siparişler tablosu tıklayın ve tasarımcının sol bölmeye sürükleyin.  
  
     Tasarımcı yeni oluşturur `Customer` ve `Order` projeniz için nesneleri. Tasarımcı otomatik olarak tablolar arasındaki ilişkileri algılar ve alt ilgili nesnelerin özelliklerini oluşturur dikkat edin. Örneğin, IntelliSense, gösterilir `Customer` nesnesinin bir `Orders` özelliği için tüm siparişleri o müşteri ile ilgili.  
  
3.  Değişikliklerinizi kaydetmek ve Tasarımcısı'nı kapatın.  
  
4.  Projenizi kaydedin.  
  
## <a name="to-add-code-to-query-the-database-and-display-the-results"></a>Veritabanını sorgulama ve sonuçları görüntülemek üzere kod eklemek için  
  
1.  Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.DataGridView> Form1 projeniz için varsayılan Windows Form denetimi.  
  
2.  Form1 kod eklemek için çift `Load` formun olay.  
  
3.  Tasarımcı tablolar için O/R Tasarımcısı eklendiğinde, eklenen bir <xref:System.Data.Linq.DataContext> projeniz için nesne. Bu nesne, ayrı ayrı nesneleri ve koleksiyonları her tablo için ek olarak bu tablolar erişmek için gereken kodu içerir. <xref:System.Data.Linq.DataContext> Nesne projeniz için .dbml dosyanızın adına bağlı. Bu proje için <xref:System.Data.Linq.DataContext> nesne adlı `northwindDataContext`.  
  
     Bir örneği oluşturabilir <xref:System.Data.Linq.DataContext> tabloları, kod ve sorgu O/R tasarımcısı tarafından belirtilen.  
  
     Aşağıdaki kodu ekleyin `Load` veri Bağlamınızı özellikleri olarak gösterilen tablolarını sorgulamak için olay.  
  
     [!code-vb[VbLINQToSQLHowTos#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-query-a-database-by-using-linq_1.vb)]  
  
4.  Projenizi çalıştırma ve sonuçları görüntülemek için F5 tuşuna basın.  
  
5.  Deneyebileceğiniz bazı ek sorgular şunlardır:  
  
     [!code-vb[VbLINQToSQLHowTos#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-query-a-database-by-using-linq_2.vb)]  
    [!code-vb[VbLINQToSQLHowTos#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-query-a-database-by-using-linq_3.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Sorgular](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [DataContext Metotları (O/R Tasarımcısı)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
