---
title: 'Nasıl yapılır: sorgu sonuçlarını LINQ kullanarak filtreleme'
ms.date: 07/20/2015
helpviewer_keywords:
- filtering [Visual Basic]
- filtering data [LINQ in Visual Basic]
- filtering [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], filtering results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- filtering data [Visual Basic]
ms.assetid: ef103092-9bed-4134-97f4-2db696e83c12
ms.openlocfilehash: 2ea8a852a2f012ddb25ec1198c66e09df880ff47
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344984"
---
# <a name="how-to-filter-query-results-by-using-linq-visual-basic"></a>Nasıl yapılır: Sorgu Sonuçlarını LINQ Kullanarak Filtreleme (Visual Basic)

Dil ile tümleşik sorgu (LINQ), veritabanı bilgilerine erişmeyi ve sorguları yürütmeyi kolaylaştırır.

Aşağıdaki örnek, bir SQL Server veritabanına yönelik sorgular gerçekleştiren ve `Where` yan tümcesini kullanarak sonuçları belirli bir değere filtreleyen yeni bir uygulamanın nasıl oluşturulacağını gösterir. Daha fazla bilgi için bkz. [WHERE yan tümcesi](../../../../visual-basic/language-reference/queries/where-clause.md).

Bu konudaki örneklerde Northwind örnek veritabanı kullanılır. Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Indirme Merkezi ' nden indirebilirsiniz. Yönergeler için bkz. [örnek veritabanlarını indirme](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-connection-to-a-database"></a>Bir veritabanına bağlantı oluşturmak için

1. Visual Studio 'da, **Görünüm** menüsünde **Sunucu Gezgini**/**Veritabanı Gezgini** ' a tıklayarak **Sunucu Gezgini**/**veritabanı Gezgini** açın.

2. **Sunucu Gezgini**/veritabanı Gezgini **veri bağlantıları** ' na sağ tıklayın ve ardından **bağlantı ekle**' ye tıklayın.

3. Northwind örnek veritabanına geçerli bir bağlantı belirtin.

## <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>LINQ to SQL dosyası içeren bir proje eklemek için

1. Visual Studio 'da, **Dosya** menüsünde, **Yeni** ' nin üzerine gelin ve ardından **Proje**' ye tıklayın. Proje türü olarak Visual Basic **Windows Forms uygulaması** ' nı seçin.

2. **Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın. **LINQ to SQL sınıfları** öğe şablonunu seçin.

3. Dosyayı `northwind.dbml`olarak adlandırın. **Ekle**'yi tıklatın. Northwind. dbml dosyası için Nesne İlişkisel Tasarımcısı (O/R Designer) açılır.

## <a name="to-add-tables-to-query-to-the-or-designer"></a>O/R tasarımcısına sorguya tablo eklemek için

1. **Sunucu Gezgini**/**veritabanı Gezgini**, Northwind veritabanına olan bağlantıyı genişletin. **Tablolar** klasörünü genişletin.

     O/R tasarımcısını kapattıysanız, daha önce eklediğiniz Northwind. dbml dosyasını çift tıklayarak yeniden açabilirsiniz.

2. Müşteriler tablosuna tıklayın ve tasarımcı 'nın sol bölmesine sürükleyin. Siparişler tablosuna tıklayın ve tasarımcı 'nın sol bölmesine sürükleyin.

     Tasarımcı projeniz için yeni `Customer` ve `Order` nesneleri oluşturur. Tasarımcı, tablolar arasındaki ilişkileri otomatik olarak algıladığını ve ilgili nesneler için alt özellikler oluşturduğunu unutmayın. Örneğin IntelliSense, `Customer` nesnesinin bu müşteriyle ilgili tüm siparişler için bir `Orders` özelliğine sahip olduğunu gösterir.

3. Değişikliklerinizi kaydedin ve tasarımcıyı kapatın.

4. Projenizi kaydedin.

## <a name="to-add-code-to-query-the-database-and-display-the-results"></a>Veritabanını sorgulamak ve sonuçları göstermek üzere kod eklemek için

1. **Araç kutusundan**bir <xref:System.Windows.Forms.DataGridView> denetimini projeniz Için varsayılan Windows formu üzerine sürükleyin, Form1.

2. Formun `Load` olayına kod eklemek için Form1 ' e çift tıklayın.

3. Tabloları O/R tasarımcısına eklediğinizde, tasarımcı projeniz için bir <xref:System.Data.Linq.DataContext> nesnesi ekledi. Bu nesne, her tablo için ayrı nesneler ve koleksiyonlara ek olarak bu tablolara erişmeniz gereken kodu içerir. Projeniz için <xref:System.Data.Linq.DataContext> nesnesi,. dbml dosyanızın adına göre adlandırılır. Bu proje için <xref:System.Data.Linq.DataContext> nesnesi `northwindDataContext`olarak adlandırılmıştır.

    Kodunuzda <xref:System.Data.Linq.DataContext> bir örneğini oluşturabilir ve O/R Tasarımcısı tarafından belirtilen tabloları sorgulayabilirsiniz.

    Veri bağlamınızın özellikleri olarak gösterilen tabloları sorgulamak için `Load` olayına aşağıdaki kodu ekleyin. Sorgu sonuçlara filtre uygular ve yalnızca `London`bulunan müşterileri döndürür.

    [!code-vb[VbLINQToSQLHowTos#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#11)]

4. Projenizi çalıştırmak ve sonuçları görüntülemek için F5 tuşuna basın.

5. Deneyebileceğiniz bazı diğer filtreler aşağıda verilmiştir.

    [!code-vb[VbLINQToSQLHowTos#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#12)]

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Sorgular](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [DataContext Metotları (O/R Tasarımcısı)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
