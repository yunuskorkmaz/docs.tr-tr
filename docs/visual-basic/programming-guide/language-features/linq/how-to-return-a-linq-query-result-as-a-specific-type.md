---
title: 'Nasıl yapılır: Bir LINQ Sorgu sonucunu belirli bir türü (Visual Basic) döndürme'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], specific type returned
- projection [LINQ in Visual Basic]
- anonymous types [Visual Basic]
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
ms.openlocfilehash: 784a848b02e75d2ae9a6c6530141e69a05a9041b
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973502"
---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a>Nasıl yapılır: Bir LINQ Sorgu sonucunu belirli bir türü (Visual Basic) döndürme
Dil ile tümleşik sorgu (LINQ), Veritabanı bilgilerine erişmek ve sorguları yürütmek kolaylaştırır. Varsayılan olarak, LINQ sorguları anonim bir tür nesnelerin bir listesini döndürür. Sorgu kullanarak belirli bir türün bir liste döndürme belirtebilirsiniz `Select` yan tümcesi.  
  
 Aşağıdaki örnek, bir SQL Server veritabanında sorgu gerçekleştirir ve sonuçları belirli bir adlandırılmış tür olarak projelerde yeni bir uygulama oluşturma işlemi gösterilmektedir. Daha fazla bilgi için [anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) ve [Select tümcesi](../../../../visual-basic/language-reference/queries/select-clause.md).  
  
 Bu konudaki örnekler, Northwind örnek veritabanını kullanır. Geliştirme bilgisayarınızda bu veritabanı yoksa Microsoft Download Center'dan gelen indirebilirsiniz. Yönergeler için [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>Bir veritabanına bir bağlantı oluşturmak için  
  
1.  Visual Studio'da açın **Sunucu Gezgini**/**veritabanı Gezgini** tıklayarak **Sunucu Gezgini**/**veritabanı Explorer** üzerinde **görünümü** menüsü.  
  
2.  Sağ **veri bağlantıları** içinde **Sunucu Gezgini**/**veritabanı Gezgini** ve ardından **Bağlantı Ekle**.  
  
3.  Northwind örnek veritabanıyla kurulan geçerli bir bağlantı belirtin.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>LINQ to SQL dosyası içeren bir proje eklemek için  
  
1.  Visual Studio'da üzerinde **dosya** menüsünde **yeni** ve ardından **proje**. Visual Basic seçin **Windows Forms uygulaması** proje türü.  
  
2.  Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle**. Seçin **LINQ to SQL sınıfları** öğe şablonu.  
  
3.  Dosyayı `northwind.dbml` olarak adlandırın. **Ekle**'yi tıklatın. Object Relational Designer (O/R Tasarımcısı) için northwind.dbml dosyası açılır.  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>O/R Tasarımcısı için sorgulamak için tablo eklemek için  
  
1.  İçinde **Sunucu Gezgini**/**veritabanı Gezgini**, Northwind veritabanına bağlantı genişletin. Genişletin **tabloları** klasör.  
  
     O/R Tasarımcısı kapattıysanız, daha önce eklediğiniz northwind.dbml dosyasına çift tıklayarak açabilirsiniz.  
  
2.  Müşteriler tablosu tıklayın ve tasarımcının sol bölmeye sürükleyin.  
  
     Tasarımcı yeni bir oluşturur `Customer` projeniz için nesne. Sorgu sonucu olarak yansıtabilirsiniz `Customer` türü veya oluşturduğunuz bir tür. Bu örnek, daha sonraki bir yordamda yeni türü oluşturun ve bu tür bir sorgu sonucunda proje.  
  
3.  Değişikliklerinizi kaydetmek ve Tasarımcısı'nı kapatın.  
  
4.  Projenizi kaydedin.  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>Veritabanını sorgulama ve sonuçları görüntülemek üzere kod eklemek için  
  
1.  Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.DataGridView> Form1 projeniz için varsayılan Windows Form denetimi.  
  
2.  Form1 Form1 sınıfını değiştirmek için çift tıklayın.  
  
3.  Sonra `End Class` deyimine Form1 sınıfı oluşturmak için aşağıdaki kodu bir `CustomerInfo` Bu örnek için sorgu sonuçlarını tutmak için türü.  
  
     [!code-vb[VbLINQToSQLHowTos#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#16)]  
  
4.  Tasarımcı tablolar için O/R Tasarımcısı eklendiğinde, eklenen bir <xref:System.Data.Linq.DataContext> projenize nesne. Bu nesne bu tablolara erişen ve ayrı nesneler ve Koleksiyonlar her tablo için erişmek için gereken kodu içerir. <xref:System.Data.Linq.DataContext> Nesne projeniz için .dbml dosyanızın adına bağlı. Bu proje için <xref:System.Data.Linq.DataContext> nesne adlı `northwindDataContext`.  
  
     Bir örneği oluşturabilir <xref:System.Data.Linq.DataContext> tabloları, kod ve sorgu O/R tasarımcısı tarafından belirtilen.  
  
     İçinde `Load` olay Form1 sınıfın veri Bağlamınızı özellikleri olarak gösterilen tablolarını sorgulamak için aşağıdaki kodu ekleyin. `Select` Sorgu yan tümcesinde yeni bir oluşturur `CustomerInfo` sorgu sonucunun her öğe için anonim bir tür yerine türü.  
  
     [!code-vb[VbLINQToSQLHowTos#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#15)]  
  
5.  Projenizi çalıştırma ve sonuçları görüntülemek için F5 tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Sorgular](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [DataContext Metotları (O/R Tasarımcısı)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
