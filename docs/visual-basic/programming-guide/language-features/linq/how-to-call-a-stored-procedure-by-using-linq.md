---
title: 'Nasıl yapılır: Bir Saklı Yordamı LINQ Kullanarak Çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
ms.openlocfilehash: 7e5fecf0c4c0d3a561ec7d0c4ac03c9d9ce7f759
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075141"
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a>Nasıl yapılır: Bir Saklı Yordamı LINQ Kullanarak Çağırma (Visual Basic)

Dil ile tümleşik sorgu (LINQ), saklı yordamlar gibi veritabanı nesneleri dahil olmak üzere veritabanı bilgilerine erişmeyi kolaylaştırır.  
  
 Aşağıdaki örnek, bir SQL Server veritabanında saklı yordam çağıran bir uygulamanın nasıl oluşturulacağını gösterir. Örnek, veritabanında iki farklı saklı yordamın nasıl çağrılacağını gösterir. Her yordam bir sorgunun sonuçlarını döndürür. Bir yordam giriş parametrelerini alır ve diğer yordam parametre almaz.  
  
 Bu konudaki örneklerde Northwind örnek veritabanı kullanılır. Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Indirme Merkezi ' nden indirebilirsiniz. Yönergeler için bkz. [örnek veritabanlarını indirme](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>Bir veritabanına bağlantı oluşturmak için  
  
1. Visual Studio 'da, **Server Explorer** / **Database Explorer** Görünüm menüsünde **Sunucu Gezgini** / **veritabanı Gezgini** ' a tıklayarak Sunucu Gezgini veritabanı Gezgini **View** açın.  
  
2. **Sunucu Gezgini**veritabanı Gezgini **veri bağlantıları** ' na sağ tıklayın / **Database Explorer** ve ardından **bağlantı ekle**' ye tıklayın.  
  
3. Northwind örnek veritabanına geçerli bir bağlantı belirtin.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>LINQ to SQL dosyası içeren bir proje eklemek için  
  
1. Visual Studio 'da, **Dosya** menüsünde, **Yeni** ' nin üzerine gelin ve ardından **Proje**' ye tıklayın. Proje türü olarak Visual Basic **Windows Forms uygulaması** ' nı seçin.  
  
2. **Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın. **LINQ to SQL sınıfları** öğe şablonunu seçin.  
  
3. Dosyayı `northwind.dbml` olarak adlandırın. **Ekle**'ye tıklayın. Nesne İlişkisel Tasarımcısı (O/R Designer), Northwind. dbml dosyası için açılır.  
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a>O/R tasarımcısına saklı yordamlar eklemek için  
  
1. **Sunucu Gezgini** / **veritabanı Gezgini**, Northwind veritabanına olan bağlantıyı genişletin. **Saklı yordamlar** klasörünü genişletin.  
  
     O/R tasarımcısını kapattıysanız, daha önce eklediğiniz Northwind. dbml dosyasını çift tıklayarak yeniden açabilirsiniz.  
  
2. **Yıla göre satışlar** saklı yordamına tıklayın ve tasarımcı 'nın sağ bölmesine sürükleyin. **En pahalı on ürün** saklı yordamına tıklayın, tasarımcı 'nın sağ bölmesine sürükleyin.  
  
3. Değişikliklerinizi kaydedin ve tasarımcıyı kapatın.  
  
4. Projenizi kaydedin.  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a>Saklı yordamların sonuçlarını görüntüleyecek kodu eklemek için  
  
1. **Araç kutusundan**, bir <xref:System.Windows.Forms.DataGridView> denetimi projeniz Için varsayılan Windows formu üzerine sürükleyin, Form1.  
  
2. Olayına kod eklemek için Form1 ' e çift tıklayın `Load` .  
  
3. O/R tasarımcısına saklı yordamlar eklediğinizde, tasarımcı <xref:System.Data.Linq.DataContext> projeniz için bir nesne ekledi. Bu nesne, bu yordamlara erişmeniz için sahip olmanız gereken kodu içerir. <xref:System.Data.Linq.DataContext>Projenin nesnesi. dbml dosyasının adına göre adlandırılır. Bu proje için, <xref:System.Data.Linq.DataContext> nesne olarak adlandırılır `northwindDataContext` .  
  
     Kodunuzda bir örneğini oluşturabilir <xref:System.Data.Linq.DataContext> ve O/R Tasarımcısı tarafından belirtilen saklı yordam yöntemlerini çağırabilirsiniz. Nesnesine bağlamak için <xref:System.Windows.Forms.DataGridView> , <xref:System.Linq.Enumerable.ToList%2A> saklı yordamın sonuçlarında yöntemi çağırarak sorguyu hemen yürütmeye zorlamanız gerekebilir.  
  
     `Load`Veri içeriğiniz için yöntemler olarak sunulan saklı yordamlardan birini çağırmak üzere olaya aşağıdaki kodu ekleyin.  
  
     [!code-vb[VbLINQtoSQLHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#1)]  
    [!code-vb[VbLINQtoSQLHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#2)]  
  
4. Projenizi çalıştırmak ve sonuçları görüntülemek için F5 tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ](index.md)
- [Sorgular](../../../language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [DataContext Metotları (O/R Tasarımcısı)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
