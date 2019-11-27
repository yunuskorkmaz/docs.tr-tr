---
title: 'Nasıl yapılır: bir saklı yordamı LINQ kullanarak çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
ms.openlocfilehash: f91ccda1842887b3785ce304fd41bdd020a55479
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345021"
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a>Nasıl yapılır: Bir Saklı Yordamı LINQ Kullanarak Çağırma (Visual Basic)
Dil ile tümleşik sorgu (LINQ), saklı yordamlar gibi veritabanı nesneleri dahil olmak üzere veritabanı bilgilerine erişmeyi kolaylaştırır.  
  
 Aşağıdaki örnek, bir SQL Server veritabanında saklı yordam çağıran bir uygulamanın nasıl oluşturulacağını gösterir. Örnek, veritabanında iki farklı saklı yordamın nasıl çağrılacağını gösterir. Her yordam bir sorgunun sonuçlarını döndürür. Bir yordam giriş parametrelerini alır ve diğer yordam parametre almaz.  
  
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
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a>O/R tasarımcısına saklı yordamlar eklemek için  
  
1. **Sunucu Gezgini**/**veritabanı Gezgini**, Northwind veritabanına olan bağlantıyı genişletin. **Saklı yordamlar** klasörünü genişletin.  
  
     O/R tasarımcısını kapattıysanız, daha önce eklediğiniz Northwind. dbml dosyasını çift tıklayarak yeniden açabilirsiniz.  
  
2. **Yıla göre satışlar** saklı yordamına tıklayın ve tasarımcı 'nın sağ bölmesine sürükleyin. **En pahalı on ürün** saklı yordamına tıklayın, tasarımcı 'nın sağ bölmesine sürükleyin.  
  
3. Değişikliklerinizi kaydedin ve tasarımcıyı kapatın.  
  
4. Projenizi kaydedin.  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a>Saklı yordamların sonuçlarını görüntüleyecek kodu eklemek için  
  
1. **Araç kutusundan**bir <xref:System.Windows.Forms.DataGridView> denetimini projeniz Için varsayılan Windows formu üzerine sürükleyin, Form1.  
  
2. `Load` olayına kod eklemek için Form1 ' e çift tıklayın.  
  
3. O/R tasarımcısına saklı yordamlar eklediğinizde tasarımcı projeniz için bir <xref:System.Data.Linq.DataContext> nesnesi ekledi. Bu nesne, bu yordamlara erişmeniz için sahip olmanız gereken kodu içerir. Projenin <xref:System.Data.Linq.DataContext> nesnesi. dbml dosyasının adına göre adlandırılır. Bu proje için <xref:System.Data.Linq.DataContext> nesnesi `northwindDataContext`olarak adlandırılmıştır.  
  
     Kodunuzda <xref:System.Data.Linq.DataContext> bir örneğini oluşturabilir ve O/R Tasarımcısı tarafından belirtilen saklı yordam yöntemlerini çağırabilirsiniz. <xref:System.Windows.Forms.DataGridView> nesnesine bağlamak için, saklı yordamın sonuçlarına <xref:System.Linq.Enumerable.ToList%2A> yöntemini çağırarak sorguyu hemen yürütmeye zorlamanız gerekebilir.  
  
     Veri içeriğiniz için yöntemler olarak sunulan saklı yordamlardan birini çağırmak üzere `Load` olayına aşağıdaki kodu ekleyin.  
  
     [!code-vb[VbLINQtoSQLHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#1)]  
    [!code-vb[VbLINQtoSQLHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#2)]  
  
4. Projenizi çalıştırmak ve sonuçları görüntülemek için F5 tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Sorgular](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [DataContext Metotları (O/R Tasarımcısı)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
