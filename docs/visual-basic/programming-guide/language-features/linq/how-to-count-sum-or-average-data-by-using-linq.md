---
title: 'Nasıl yapılır: LINQ kullanarak sayma, toplama veya ortalama veri'
ms.date: 07/20/2015
helpviewer_keywords:
- average operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- queries [LINQ in Visual Basic], sum results
- Aggregate clause [Visual Basic]
- sum operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], counting results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- count operator [LINQ in Visual Basic]
ms.assetid: 51ca1f59-7770-4884-8b76-113002e54fc0
ms.openlocfilehash: 7e105c75653f979f53567ef49f1f4cdeafaa4d0f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345016"
---
# <a name="how-to-count-sum-or-average-data-by-using-linq-visual-basic"></a>Nasıl yapılır: LINQ Kullanarak Count, Sum veya Average Verisi (Visual Basic)
Dil ile tümleşik sorgu (LINQ), veritabanı bilgilerine erişmeyi ve sorguları yürütmeyi kolaylaştırır.  
  
 Aşağıdaki örnek, SQL Server veritabanına karşı sorgu gerçekleştiren yeni bir uygulamanın nasıl oluşturulacağını gösterir. Örnek, `Aggregate` ve `Group By` yan tümcelerini kullanarak sonuçların sayısını sayar, toplar ve ortalamasını alır. Daha fazla bilgi için bkz. [toplama yan tümcesi](../../../../visual-basic/language-reference/queries/aggregate-clause.md) ve [Group by yan tümcesi](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
 Bu konudaki örneklerde Northwind örnek veritabanı kullanılır. Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Indirme Merkezi ' nden indirebilirsiniz. Yönergeler için bkz. [örnek veritabanlarını indirme](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>Bir veritabanına bağlantı oluşturmak için  
  
1. Visual Studio 'da, **Görünüm** menüsünde **Sunucu Gezgini**/**Veritabanı Gezgini** ' a tıklayarak **Sunucu Gezgini**/**veritabanı Gezgini** açın.  
  
2. **Sunucu Gezgini**/veritabanı Gezgini **veri bağlantıları** ' na sağ tıklayın ve ardından **bağlantı ekle**' ye tıklayın.  
  
3. Northwind örnek veritabanına geçerli bir bağlantı belirtin.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>LINQ to SQL dosyası içeren bir proje eklemek için  
  
1. Visual Studio 'da, **Dosya** menüsünde, **Yeni** ' nin üzerine gelin ve ardından **Proje**' ye tıklayın. Proje türü olarak Visual Basic **Windows Forms uygulaması** ' nı seçin.  
  
2. **Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın. **LINQ to SQL sınıfları** öğe şablonunu seçin.  
  
3. Dosyayı `northwind.dbml`olarak adlandırın. **Ekle**'yi tıklatın. Nesne İlişkisel Tasarımcısı (O/R Designer), Northwind. dbml dosyası için açılır.  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>O/R tasarımcısına sorguya tablo eklemek için  
  
1. **Sunucu Gezgini**/**veritabanı Gezgini**, Northwind veritabanına olan bağlantıyı genişletin. **Tablolar** klasörünü genişletin.  
  
     O/R tasarımcısını kapattıysanız, daha önce eklediğiniz Northwind. dbml dosyasını çift tıklayarak yeniden açabilirsiniz.  
  
2. Müşteriler tablosuna tıklayın ve tasarımcı 'nın sol bölmesine sürükleyin. Siparişler tablosuna tıklayın ve tasarımcı 'nın sol bölmesine sürükleyin.  
  
     Tasarımcı projeniz için yeni `Customer` ve `Order` nesneleri oluşturur. Tasarımcı, tablolar arasındaki ilişkileri otomatik olarak algıladığını ve ilgili nesneler için alt özellikler oluşturduğunu unutmayın. Örneğin IntelliSense, `Customer` nesnesinin bu müşteriyle ilgili tüm siparişler için bir `Orders` özelliğine sahip olduğunu gösterir.  
  
3. Değişikliklerinizi kaydedin ve tasarımcıyı kapatın.  
  
4. Projenizi kaydedin.  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>Veritabanını sorgulamak ve sonuçları göstermek üzere kod eklemek için  
  
1. **Araç kutusundan**bir <xref:System.Windows.Forms.DataGridView> denetimini projeniz Için varsayılan Windows formu üzerine sürükleyin, Form1.  
  
2. Formun `Load` olayına kod eklemek için Form1 ' e çift tıklayın.  
  
3. Tabloları O/R tasarımcısına eklediğinizde, tasarımcı projeniz için bir <xref:System.Data.Linq.DataContext> nesnesi ekledi. Bu nesne, bu tablolara erişmeniz gereken kodu içerir ve her tablo için ayrı nesneler ve koleksiyonlara erişin. Projeniz için <xref:System.Data.Linq.DataContext> nesnesi,. dbml dosyanızın adına göre adlandırılır. Bu proje için <xref:System.Data.Linq.DataContext> nesnesi `northwindDataContext`olarak adlandırılmıştır.  
  
     Kodunuzda <xref:System.Data.Linq.DataContext> bir örneğini oluşturabilir ve O/R Tasarımcısı tarafından belirtilen tabloları sorgulayabilirsiniz.  
  
     <xref:System.Data.Linq.DataContext> özellikleri olarak gösterilen tabloları sorgulamak için `Load` olayına aşağıdaki kodu ekleyin ve sonuçların sayımını yapın, toplayın ve ortalamasını yapın. Örnek, tek bir sonuç sorgulamak için `Aggregate` yan tümcesini ve gruplanmış sonuçlara yönelik bir ortalama göstermek için `Group By` yan tümcesini kullanır.  
  
     [!code-vb[VbLINQToSQLHowTos#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form6.vb#13)]  
  
4. Projenizi çalıştırmak ve sonuçları görüntülemek için F5 tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Sorgular](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [DataContext Metotları (O/R Tasarımcısı)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [Aggregate Yan Tümcesi](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Group By Yan Tümcesi](../../../../visual-basic/language-reference/queries/group-by-clause.md)
