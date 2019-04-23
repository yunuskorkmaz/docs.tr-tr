---
title: 'Nasıl yapılır: LINQ (Visual Basic) kullanarak bir sorgu sonucunda en düşük ve en fazla değeri bulma'
ms.date: 07/20/2015
helpviewer_keywords:
- max operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- minimum values [LINQ in Visual Basic]
- min operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], minimum and maximum values
- Max property
- maximum values [LINQ in Visual Basic]
- Aggregate clause [Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 238b763b-7dcd-4b14-8050-b65500a4f71c
ms.openlocfilehash: af5f4bf829664057c40004a842df95d927cc5d71
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59337480"
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a>Nasıl yapılır: LINQ (Visual Basic) kullanarak bir sorgu sonucunda en düşük ve en fazla değeri bulma
Dil ile tümleşik sorgu (LINQ), Veritabanı bilgilerine erişmek ve sorguları yürütmek kolaylaştırır.  
  
 Aşağıdaki örnek, bir SQL Server veritabanında sorgu gerçekleştiren yeni bir uygulama oluşturma işlemi gösterilmektedir. Örnek sonuçlar için minimum ve maksimum değerleri kullanarak belirler `Aggregate` ve `Group By` yan tümceleri. Daha fazla bilgi için [Aggregate tümcesi](../../../../visual-basic/language-reference/queries/aggregate-clause.md) ve [Group yan tümcesi tarafından](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
 Bu konudaki örnekler, Northwind örnek veritabanını kullanır. Geliştirme bilgisayarınızda bu veritabanı yoksa Microsoft Download Center'dan gelen indirebilirsiniz. Yönergeler için [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>Bir veritabanına bir bağlantı oluşturmak için  
  
1. Visual Studio'da açın **Sunucu Gezgini**/**veritabanı Gezgini** tıklayarak **Sunucu Gezgini**/**veritabanı Explorer** üzerinde **görünümü** menüsü.  
  
2. Sağ **veri bağlantıları** içinde **Sunucu Gezgini**/**veritabanı Gezgini** ve ardından **Bağlantı Ekle**.  
  
3. Northwind örnek veritabanıyla kurulan geçerli bir bağlantı belirtin.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>LINQ to SQL dosyası içeren bir proje eklemek için  
  
1. Visual Studio'da üzerinde **dosya** menüsünde **yeni** ve ardından **proje**. Visual Basic seçin **Windows Forms uygulaması** proje türü.  
  
2. Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle**. Seçin **LINQ to SQL sınıfları** öğe şablonu.  
  
3. Dosyayı `northwind.dbml` olarak adlandırın. **Ekle**'yi tıklatın. Object Relational Designer (O/R Tasarımcısı) için northwind.dbml dosyası açılır.  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>O/R Tasarımcısı için sorgulamak için tablo eklemek için  
  
1. İçinde **Sunucu Gezgini**/**veritabanı Gezgini**, Northwind veritabanına bağlantı genişletin. Genişletin **tabloları** klasör.  
  
     O/R Tasarımcısı kapattıysanız, daha önce eklediğiniz northwind.dbml dosyasına çift tıklayarak açabilirsiniz.  
  
2. Müşteriler tablosu tıklayın ve tasarımcının sol bölmeye sürükleyin. Siparişler tablosu tıklayın ve tasarımcının sol bölmeye sürükleyin.  
  
     Tasarımcı yeni oluşturur `Customer` ve `Order` projeniz için nesneleri. Tasarımcı otomatik olarak tablolar arasındaki ilişkileri algılar ve alt ilgili nesnelerin özelliklerini oluşturur dikkat edin. Örneğin, IntelliSense, gösterilir `Customer` nesnesinin bir `Orders` özelliği için tüm siparişleri o müşteri ile ilgili.  
  
3. Değişikliklerinizi kaydetmek ve Tasarımcısı'nı kapatın.  
  
4. Projenizi kaydedin.  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>Veritabanını sorgulama ve sonuçları görüntülemek üzere kod eklemek için  
  
1. Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.DataGridView> Form1 projeniz için varsayılan Windows Form denetimi.  
  
2. Form1 kod eklemek için çift `Load` formun olay.  
  
3. Tasarımcı tablolar için O/R Tasarımcısı eklendiğinde, eklenen bir <xref:System.Data.Linq.DataContext> projeniz için nesne. Bu nesne, ayrı ayrı nesneleri ve koleksiyonları her tablo için ek olarak bu tablolar erişmek için gereken kodu içerir. <xref:System.Data.Linq.DataContext> Nesne projeniz için .dbml dosyanızın adına bağlı. Bu proje için <xref:System.Data.Linq.DataContext> nesne adlı `northwindDataContext`.  
  
     Bir örneği oluşturabilir <xref:System.Data.Linq.DataContext> tabloları, kod ve sorgu O/R tasarımcısı tarafından belirtilen.  
  
     Aşağıdaki kodu ekleyin `Load` olay. Bu kod, veri bağlamının özellikleri olarak sunulur ve sonuçlar için minimum ve maksimum değerleri belirler tabloları sorgular. Örnek kullanır kendisinin `Aggregate` tek bir sonuç için sorgu yan tümcesinin ve `Group By` yan tümcesi için ortalama gösterilecek gruplandırılmış sonuçları.  
  
     [!code-vb[VbLINQToSQLHowTos#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form7.vb#14)]  
  
4. Projenizi çalıştırma ve sonuçları görüntülemek için F5 tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Sorgular](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [DataContext Metotları (O/R Tasarımcısı)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
