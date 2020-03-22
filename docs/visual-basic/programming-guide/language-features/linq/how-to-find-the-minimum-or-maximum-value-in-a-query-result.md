---
title: 'Nasıl yapılır: LINQ Kullanarak Bir Sorgu Sonucunda En Düşük ve En Fazla Değeri Bulma'
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
ms.openlocfilehash: ef5f218cdcc7275f616486110825ad0b9df11cc3
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112368"
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a>Nasıl yapılır: LINQ Kullanarak Bir Sorgu Sonucunda En Düşük ve En Fazla Değeri Bulma (Visual Basic)
Dil-Tümleşik Sorgu (LINQ), veritabanı bilgilerine erişmemi ve sorguları yürütmeyi kolaylaştırır.  
  
 Aşağıdaki örnek, SQL Server veritabanına karşı sorgu gerçekleştiren yeni bir uygulamanın nasıl oluşturulacagını gösterir. Örnek, sonuçlar için en küçük ve maksimum `Aggregate` değerleri `Group By` ve yan tümceleri kullanarak belirler. Daha fazla bilgi için [Bkz. Toplu Yan Tümce](../../../../visual-basic/language-reference/queries/aggregate-clause.md) ve [Grup Yan Tümcesi.](../../../../visual-basic/language-reference/queries/group-by-clause.md)  
  
 Bu konudaki örnekler Northwind örnek veritabanını kullanır. Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft İndirme Merkezi'nden indirebilirsiniz. Talimatlar için [bkz.](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="create-a-connection-to-a-database"></a>Veritabanına bağlantı oluşturma  
  
1. Visual Studio'da, **Görünüm** menüsünde **Server Explorer**/**Database Explorer'ı** tıklatarak Server **Explorer**/**Database Explorer'ı** açın.  
  
2. **Server Explorer**/**Database Explorer'da** **Veri Bağlantıları'nı** sağ tıklatın ve ardından **Bağlantı Ekle'yi**tıklatın.  
  
3. Northwind örnek veritabanına geçerli bir bağlantı belirtin.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>SQL dosyasına LINQ içeren bir proje eklemek için  
  
1. Visual Studio'da, **Dosya** menüsünde **Yeni'yi** işaret edin ve **Project'i**tıklatın. Proje türü olarak Visual Basic **Windows Forms Application'ı** seçin.  
  
2. **Proje** menüsünde **Yeni Öğe Ekle'yi**tıklatın. **LINQ 'dan SQL Sınıflara** öğe şablonu seçin.  
  
3. Dosyayı `northwind.dbml` olarak adlandırın. **Ekle**’ye tıklayın. Object Relational Designer (O/R Designer) northwind.dbml dosyası için açılır.  
  
## <a name="add-tables-to-query-to-the-or-designer"></a>O/R Tasarımcısına sorgu için tablo ekleme  
  
1. **Server Explorer**/**Database Explorer'da,** Northwind veritabanına bağlantıyı genişletin. **Tablolar** klasörünü genişletin.  
  
     O/R Tasarımcısı'nı kapattıysanız, daha önce eklediğiniz northwind.dbml dosyasını çift tıklatarak yeniden açabilirsiniz.  
  
2. Müşteriler tablosunu tıklatın ve tasarımcının sol bölmesine sürükleyin. Siparişler tablosunu tıklatın ve tasarımcının sol bölmesine sürükleyin.  
  
     Tasarımcı, projeniz `Customer` `Order` için yeni ve nesneler oluşturur. Tasarımcının tablolar arasındaki ilişkileri otomatik olarak algıladığını ve ilgili nesneler için alt özellikler oluşturduğuna dikkat edin. Örneğin, IntelliSense nesnenin `Customer` o müşteriyle ilgili tüm siparişler için bir `Orders` özelliğe sahip olduğunu gösterir.  
  
3. Değişikliklerinizi kaydedin ve tasarımcıyı kapatın.  
  
4. Projenizi kaydedin.  
  
## <a name="add-code-to-query-the-database-and-display-the-results"></a>Veritabanını sorgulamak ve sonuçları görüntülemek için kod ekleme  
  
1. Araç **Kutusundan,** projeniz için varsayılan Windows Formu'na bir <xref:System.Windows.Forms.DataGridView> denetim sürükleyin, Form1.  
  
2. Formun `Load` olayına kod eklemek için Form1'i çift tıklatın.  
  
3. O/R Tasarımcısı'na tablo eklediğinizde, tasarımcı <xref:System.Data.Linq.DataContext> projeniz için bir nesne ekledi. Bu nesne, her tablo için tek tek nesneler ve koleksiyonlar ek olarak, bu tablolara erişmek için gereken kodu içerir. Projenizin <xref:System.Data.Linq.DataContext> nesnesi .dbml dosyanızın adına göre adlandırılır. Bu proje için <xref:System.Data.Linq.DataContext> nesne `northwindDataContext`adı verilir.  
  
     Kodunuzdakinin <xref:System.Data.Linq.DataContext> bir örneğini oluşturabilir ve O/R Tasarımcısı tarafından belirtilen tabloları sorgulayabilirsiniz.  
  
     `Load` Olaya aşağıdaki kodu ekleyin. Bu kod, veri bağlamınızın özellikleri olarak ortaya çıkarılan tabloları sorgular ve sonuçlar için en küçük ve maksimum değerleri belirler. Örnek, tek `Aggregate` bir sonuç için sorgu yapmak `Group By` için yan tümceyi ve gruplanmış sonuçlar için bir ortalama göstermek için yan tümceyi kullanır.  
  
     [!code-vb[VbLINQToSQLHowTos#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form7.vb#14)]  
  
4. Projenizi çalıştırmak ve sonuçları görüntülemek için **F5** tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Sorgular](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [DataContext Metotları (O/R Tasarımcısı)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
