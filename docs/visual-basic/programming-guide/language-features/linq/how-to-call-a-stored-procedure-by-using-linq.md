---
title: "Nasıl yapılır: Bir Saklı Yordamı LINQ Kullanarak Çağırma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8bb7b970d42a44ad925883b7a935aae386b1f1d5
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a>Nasıl yapılır: Bir Saklı Yordamı LINQ Kullanarak Çağırma (Visual Basic)
Dil ile tümleşik sorgu (LINQ) veritabanı gibi depolanan nesneler yordamlarını içeren veritabanı bilgileri erişimi kolay hale getirir.  
  
 Aşağıdaki örnek bir SQL Server veritabanı içinde saklı yordamı çağıran bir uygulamasının nasıl oluşturulacağını gösterir. Örnek veritabanında iki farklı saklı yordam çağrısı gösterilmektedir. Her bir yordam bir sorgunun sonuçlarını döndürür. Bir yordam giriş parametreleri alır ve diğer yordamı parametre almaz.  
  
 Bu konudaki örnekler Northwind örnek veritabanı kullanır. Northwind örnek veritabanı geliştirme bilgisayarınızda yoksa, buradan indirebilirsiniz [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web sitesi. Yönergeler için bkz: [örnek veritabanları yükleme](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>Bir veritabanına bir bağlantı oluşturmak için  
  
1.  Visual Studio'da açın **Sunucu Gezgini**/**Database Explorer** tıklayarak **Sunucu Gezgini**/**veritabanı Explorer** üzerinde **Görünüm** menüsü.  
  
2.  Sağ **veri bağlantıları** içinde **Sunucu Gezgini**/**Database Explorer** ve ardından **Bağlantı Ekle**.  
  
3.  Northwind örnek veritabanı için geçerli bir bağlantı belirtin.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>Bir LINQ to SQL dosyası içeren bir proje eklemek için  
  
1.  Visual Studio'da üzerinde **dosya** menüsündeki **yeni** ve ardından **proje**. Visual Basic seçin **Windows Forms uygulaması** proje türü olarak.  
  
2.  Üzerinde **proje** menüsünde tıklatın **Yeni Öğe Ekle**. Seçin **LINQ'ten SQL'e sınıflarını** öğe şablonu.  
  
3.  Dosya adı `northwind.dbml`. **Ekle**'yi tıklatın. Nesne İlişkisel Tasarımcısı (O/R Tasarımcısı) northwind.dbml dosyası için açıldı.  
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a>Saklı yordamlar için O/R Tasarımcısı eklemek için  
  
1.  İçinde **Sunucu Gezgini**/**Database Explorer**, Northwind veritabanına bağlantı genişletin. Genişletme **saklı yordamlar** klasör.  
  
     O/R Tasarımcısı kapattıysanız, daha önce eklediğiniz northwind.dbml dosyasını çift tıklatarak yeniden açabilirsiniz.  
  
2.  Tıklatın **yıla göre satış** saklı yordamı ve tasarımcı sağ bölmesine sürükleyin. Tıklatın **on en pahalı ürün** saklı yordam, Tasarımcı sağ bölmesinde sürükleyin.  
  
3.  Değişikliklerinizi kaydetmek ve Tasarımcısı'nı kapatın.  
  
4.  Projeyi kaydedin.  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a>Saklı yordamlar sonuçlarını görüntülemek üzere kod eklemek için  
  
1.  Gelen **araç**, sürükleyin bir <xref:System.Windows.Forms.DataGridView> Form1 projeniz için varsayılan Windows Form denetimi.  
  
2.  Form1 kodu eklemek için çift tıklayın, `Load` olay.  
  
3.  O/R Tasarımcısı saklı yordamlar eklendiğinde Tasarımcı eklenen bir <xref:System.Data.Linq.DataContext> projeniz için nesne. Bu nesne, bu yordamlar erişmek için gerekli kod içerir. <xref:System.Data.Linq.DataContext> Nesne proje adlı için .dbml dosya adına dayalı. Bu proje için <xref:System.Data.Linq.DataContext> nesne adlandırılan `northwindDataContext`.  
  
     Bir örneğini oluşturabilirsiniz <xref:System.Data.Linq.DataContext> kod ve çağrı de O/R tasarımcısı tarafından belirtilen saklı yordam yöntemlerinin. Bağlamak için <xref:System.Windows.Forms.DataGridView> nesne çağırarak hemen çalıştırılacak sorgu zorlamak yaptığınız <xref:System.Linq.Enumerable.ToList%2A> saklı yordamı sonuçlarını yöntemi.  
  
     Aşağıdaki kodu ekleyin `Load` veri içeriğiniz için yöntemleri olarak sunulan saklı yordamlardan birini çağrılacak olay.  
  
     [!code-vb[VbLINQtoSQLHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_1.vb)]  
    [!code-vb[VbLINQtoSQLHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_2.vb)]  
  
4.  Projenizi çalıştırma ve sonuçları görüntülemek için F5 tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Sorgular](../../../../visual-basic/language-reference/queries/queries.md)  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
 [DataContext yöntemleri (O/R Tasarımcısı)](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [Nasıl yapılır: güncelleştirme, ekleme ve silme (O/R Tasarımcısı) gerçekleştirmek için saklı yordamlar atayın](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)
