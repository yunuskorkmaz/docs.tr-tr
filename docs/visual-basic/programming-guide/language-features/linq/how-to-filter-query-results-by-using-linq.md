---
title: "Nasıl yapılır: Sorgu Sonuçlarını LINQ Kullanarak Filtreleme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 09f2eb65858853fd759ae033f749151b348c124d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-filter-query-results-by-using-linq-visual-basic"></a>Nasıl yapılır: Sorgu Sonuçlarını LINQ Kullanarak Filtreleme (Visual Basic)
Dil ile tümleşik sorgu (LINQ) Veritabanı bilgilerine erişmek ve sorguları yürütün daha kolay hale getirir.  
  
 Aşağıdaki örnek, bir SQL Server veritabanı sorguları gerçekleştirir ve sonuçları kullanarak belirli bir değerle filtreler yeni bir uygulama oluşturmak nasıl gösterir `Where` yan tümcesi. Daha fazla bilgi için bkz: [Where yan tümcesi](../../../../visual-basic/language-reference/queries/where-clause.md).  
  
 Bu konudaki örnekler Northwind örnek veritabanı kullanır. Northwind örnek veritabanı geliştirme bilgisayarınızda yoksa, buradan indirebilirsiniz [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web sitesi. Yönergeler için bkz: [örnek veritabanları yükleme](https://msdn.microsoft.com/library/bb399411).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>Bir veritabanına bir bağlantı oluşturmak için  
  
1.  Visual Studio'da açın **Sunucu Gezgini**/**Database Explorer** tıklayarak **Sunucu Gezgini**/**veritabanı Explorer** üzerinde **Görünüm** menüsü.  
  
2.  Sağ **veri bağlantıları** içinde **Sunucu Gezgini**/**Database Explorer** ve ardından **Bağlantı Ekle**.  
  
3.  Northwind örnek veritabanı için geçerli bir bağlantı belirtin.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>Bir LINQ to SQL dosyası içeren bir proje eklemek için  
  
1.  Visual Studio'da üzerinde **dosya** menüsündeki **yeni** ve ardından **proje**. Visual Basic seçin **Windows Forms uygulaması** proje türü olarak.  
  
2.  Üzerinde **proje** menüsünde tıklatın **Yeni Öğe Ekle**. Seçin **LINQ'ten SQL'e sınıflarını** öğe şablonu.  
  
3.  Dosya adı `northwind.dbml`. **Ekle**'yi tıklatın. Nesne İlişkisel Tasarımcısı (O/R Tasarımcısı) için northwind.dbml dosyasını açar.  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>O/R Tasarımcısı sorgulamak için tablo eklemek için  
  
1.  İçinde **Sunucu Gezgini**/**Database Explorer**, Northwind veritabanına bağlantı genişletin. Genişletme **tabloları** klasör.  
  
     O/R Tasarımcısı kapattıysanız, daha önce eklediğiniz northwind.dbml dosyasını çift tıklatarak yeniden açabilirsiniz.  
  
2.  Müşteriler tablosunu tıklayın ve tasarımcı sol bölmesine sürükleyin. Siparişler tablosundaki tıklayın ve tasarımcı sol bölmesine sürükleyin.  
  
     Tasarımcı oluşturur Yeni `Customer` ve `Order` projeniz için nesneleri. Tasarımcı otomatik olarak tablolar arasındaki ilişkileri algılar ve alt ilgili nesnelerin özelliklerini oluşturur dikkat edin. IntelliSense, örneğin, gösterecektir `Customer` nesnesi bir `Orders` özelliği tüm siparişler için o müşteri ile ilişkili.  
  
3.  Değişikliklerinizi kaydetmek ve Tasarımcısı'nı kapatın.  
  
4.  Projeyi kaydedin.  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>Veritabanını sorgulamak ve sonuçları görüntülemek üzere kod eklemek için  
  
1.  Gelen **araç**, sürükleyin bir <xref:System.Windows.Forms.DataGridView> Form1 projeniz için varsayılan Windows Form denetimi.  
  
2.  Kodu eklemek için Form1 çift `Load` olay formunun.  
  
3.  O/R Tasarımcısı tabloları eklendiğinde Tasarımcı eklenen bir <xref:System.Data.Linq.DataContext> projeniz için nesne. Bu nesne, ayrı ayrı nesneleri ve koleksiyonları her tablo için ek olarak bu tablolar erişmek zorunda kodunu içerir. <xref:System.Data.Linq.DataContext> Nesne projenizi adlı için .dbml dosyanızı adına dayalı. Bu proje için <xref:System.Data.Linq.DataContext> nesne adlandırılan `northwindDataContext`.  
  
     Bir örneğini oluşturabilirsiniz <xref:System.Data.Linq.DataContext> tabloları, kod ve sorgu O/R tasarımcısı tarafından belirtilen.  
  
     Aşağıdaki kodu ekleyin `Load` veri bağlamı özellikleri olarak sunulur tabloları sorgulamak için olay. Sorgu sonuçları filtreler ve bulunan müşteriler döndürür `London`.  
  
     [!code-vb[VbLINQToSQLHowTos#11](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-filter-query-results-by-using-linq_1.vb)]  
  
4.  Projenizi çalıştırma ve sonuçları görüntülemek için F5 tuşuna basın.  
  
5.  Deneyebileceğiniz diğer bir filtreleri şunlardır.  
  
     [!code-vb[VbLINQToSQLHowTos#12](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-filter-query-results-by-using-linq_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Sorguları](../../../../visual-basic/language-reference/queries/queries.md)  
 [LINQ-SQL](https://msdn.microsoft.com/library/bb386976)  
 [DataContext yöntemleri (O/R Tasarımcısı)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
