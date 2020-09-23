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
ms.openlocfilehash: e397ccd6fe21caaeb9d56ff3b0cc1ce16032639a
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91084014"
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a>Nasıl yapılır: LINQ Kullanarak Bir Sorgu Sonucunda En Düşük ve En Fazla Değeri Bulma (Visual Basic)

Dil ile tümleşik sorgu (LINQ), veritabanı bilgilerine erişmeyi ve sorguları yürütmeyi kolaylaştırır.  
  
 Aşağıdaki örnek, SQL Server veritabanına karşı sorgu gerçekleştiren yeni bir uygulamanın nasıl oluşturulacağını gösterir. Örnek, `Aggregate` ve yan tümceleri kullanılarak sonuçlar için en düşük ve en büyük değerleri belirler `Group By` . Daha fazla bilgi için bkz. [toplama yan tümcesi](../../../language-reference/queries/aggregate-clause.md) ve [Group by yan tümcesi](../../../language-reference/queries/group-by-clause.md).  
  
 Bu konudaki örneklerde Northwind örnek veritabanı kullanılır. Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Indirme Merkezi ' nden indirebilirsiniz. Yönergeler için bkz. [örnek veritabanlarını indirme](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="create-a-connection-to-a-database"></a>Veritabanına bağlantı oluşturma  
  
1. Visual Studio 'da, **Server Explorer** / **Database Explorer** Görünüm menüsünde **Sunucu Gezgini** / **veritabanı Gezgini** ' a tıklayarak Sunucu Gezgini veritabanı Gezgini **View** açın.  
  
2. **Sunucu Gezgini**veritabanı Gezgini **veri bağlantıları** ' na sağ tıklayın / **Database Explorer** ve ardından **bağlantı ekle**' ye tıklayın.  
  
3. Northwind örnek veritabanına geçerli bir bağlantı belirtin.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>LINQ to SQL dosyası içeren bir proje eklemek için  
  
1. Visual Studio 'da, **Dosya** menüsünde, **Yeni** ' nin üzerine gelin ve ardından **Proje**' ye tıklayın. Proje türü olarak Visual Basic **Windows Forms uygulaması** ' nı seçin.  
  
2. **Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın. **LINQ to SQL sınıfları** öğe şablonunu seçin.  
  
3. Dosyayı `northwind.dbml` olarak adlandırın. **Ekle**'ye tıklayın. Nesne İlişkisel Tasarımcısı (O/R Designer), Northwind. dbml dosyası için açılır.  
  
## <a name="add-tables-to-query-to-the-or-designer"></a>O/R tasarımcısına sorguya tablo ekleme  
  
1. **Sunucu Gezgini** / **veritabanı Gezgini**, Northwind veritabanına olan bağlantıyı genişletin. **Tablolar** klasörünü genişletin.  
  
     O/R tasarımcısını kapattıysanız, daha önce eklediğiniz Northwind. dbml dosyasını çift tıklayarak yeniden açabilirsiniz.  
  
2. Müşteriler tablosuna tıklayın ve tasarımcı 'nın sol bölmesine sürükleyin. Siparişler tablosuna tıklayın ve tasarımcı 'nın sol bölmesine sürükleyin.  
  
     Tasarımcı `Customer` projeniz için yeni ve `Order` nesneler oluşturur. Tasarımcı, tablolar arasındaki ilişkileri otomatik olarak algıladığını ve ilgili nesneler için alt özellikler oluşturduğunu unutmayın. Örneğin IntelliSense, `Customer` nesnenin `Orders` Bu müşteriyle ilgili tüm siparişler için bir özelliğe sahip olduğunu gösterir.  
  
3. Değişikliklerinizi kaydedin ve tasarımcıyı kapatın.  
  
4. Projenizi kaydedin.  
  
## <a name="add-code-to-query-the-database-and-display-the-results"></a>Veritabanını sorgulamak ve sonuçları göstermek için kod ekleyin  
  
1. **Araç kutusundan**, bir <xref:System.Windows.Forms.DataGridView> denetimi projeniz Için varsayılan Windows formu üzerine sürükleyin, Form1.  
  
2. Form olayına kod eklemek için Form1 ' e çift tıklayın `Load` .  
  
3. Tabloları O/R tasarımcısına eklediğinizde, tasarımcı <xref:System.Data.Linq.DataContext> projeniz için bir nesne ekledi. Bu nesne, her tablo için ayrı nesneler ve koleksiyonlara ek olarak bu tablolara erişmeniz gereken kodu içerir. <xref:System.Data.Linq.DataContext>Projeniz için olan nesne,. dbml dosyanızın adına göre adlandırılır. Bu proje için, <xref:System.Data.Linq.DataContext> nesne olarak adlandırılır `northwindDataContext` .  
  
     Kodunuzda ' ın bir örneğini oluşturabilir <xref:System.Data.Linq.DataContext> ve O/R Tasarımcısı tarafından belirtilen tabloları sorgulayabilirsiniz.  
  
     Olayına aşağıdaki kodu ekleyin `Load` . Bu kod, veri bağlamınızın özellikleri olarak gösterilen tabloları sorgular ve sonuçlar için en düşük ve en yüksek değerleri belirler. Örnek, `Aggregate` tek bir sonuç sorgulamak için yan tümcesini ve `Group By` gruplanmış sonuçlar için bir ortalama göstermek için yan tümceyi kullanır.  
  
     [!code-vb[VbLINQToSQLHowTos#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form7.vb#14)]  
  
4. Projenizi çalıştırmak ve sonuçları görüntülemek için **F5** tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ](index.md)
- [Sorgular](../../../language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [DataContext Metotları (O/R Tasarımcısı)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
