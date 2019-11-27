---
title: 'Nasıl yapılır: Bir LINQ Sorgu Sonucunu Belirli Bir Tür Olarak Döndürme'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], specific type returned
- projection [LINQ in Visual Basic]
- anonymous types [Visual Basic]
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
ms.openlocfilehash: 1084743b0c50d381375b76a3116ed7c9e6f9d769
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354208"
---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a>Nasıl yapılır: Bir LINQ Sorgu Sonucunu Belirli Bir Tür Olarak Döndürme (Visual Basic)
Dil ile tümleşik sorgu (LINQ), veritabanı bilgilerine erişmeyi ve sorguları yürütmeyi kolaylaştırır. Varsayılan olarak, LINQ sorguları bir nesne listesini anonim bir tür olarak döndürür. Ayrıca, bir sorgunun `Select` yan tümcesini kullanarak belirli bir türün listesini döndürmesini belirtebilirsiniz.  
  
 Aşağıdaki örnek, SQL Server veritabanına yönelik sorgular gerçekleştiren yeni bir uygulamanın nasıl oluşturulduğunu ve sonuçların belirli bir adlandırılmış tür olarak projede nasıl oluşturulacağını gösterir. Daha fazla bilgi için bkz. [anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) ve [seçim tümcesi](../../../../visual-basic/language-reference/queries/select-clause.md).  
  
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
  
2. Müşteriler tablosuna tıklayın ve tasarımcı 'nın sol bölmesine sürükleyin.  
  
     Tasarımcı projeniz için yeni bir `Customer` nesnesi oluşturur. Bir sorgu sonucunu `Customer` türü veya oluşturduğunuz bir tür olarak proje yapabilirsiniz. Bu örnek, sonraki bir yordamda yeni bir tür oluşturacak ve bu tür olarak bir sorgu sonucunu proje oluşturacak.  
  
3. Değişikliklerinizi kaydedin ve tasarımcıyı kapatın.  
  
4. Projenizi kaydedin.  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>Veritabanını sorgulamak ve sonuçları göstermek üzere kod eklemek için  
  
1. **Araç kutusundan**bir <xref:System.Windows.Forms.DataGridView> denetimini projeniz Için varsayılan Windows formu üzerine sürükleyin, Form1.  
  
2. Form1 sınıfını değiştirmek için Form1 ' e çift tıklayın.  
  
3. Form1 sınıfının `End Class` deyimden sonra, bu örneğe ilişkin sorgu sonuçlarını tutmak üzere bir `CustomerInfo` türü oluşturmak için aşağıdaki kodu ekleyin.  
  
     [!code-vb[VbLINQToSQLHowTos#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#16)]  
  
4. Tabloları O/R tasarımcısına eklediğinizde, tasarımcı projenize bir <xref:System.Data.Linq.DataContext> nesnesi ekledi. Bu nesne, bu tablolara erişmeniz gereken kodu içerir ve her tablo için ayrı nesneler ve koleksiyonlara erişin. Projeniz için <xref:System.Data.Linq.DataContext> nesnesi,. dbml dosyanızın adına göre adlandırılır. Bu proje için <xref:System.Data.Linq.DataContext> nesnesi `northwindDataContext`olarak adlandırılmıştır.  
  
     Kodunuzda <xref:System.Data.Linq.DataContext> bir örneğini oluşturabilir ve O/R Tasarımcısı tarafından belirtilen tabloları sorgulayabilirsiniz.  
  
     Form1 sınıfının `Load` olayında, veri bağlamınızın özellikleri olarak gösterilen tabloları sorgulamak için aşağıdaki kodu ekleyin. Sorgunun `Select` yan tümcesi, sorgu sonucunun her bir öğesi için anonim bir tür yerine yeni bir `CustomerInfo` türü oluşturacak.  
  
     [!code-vb[VbLINQToSQLHowTos#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#15)]  
  
5. Projenizi çalıştırmak ve sonuçları görüntülemek için F5 tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Sorgular](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [DataContext Metotları (O/R Tasarımcısı)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
