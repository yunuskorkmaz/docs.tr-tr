---
title: 'İzlenecek yol: Basit Nesne Modeli ve Sorgu (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: c878e457-f715-46e4-a136-ff14d6c86018
ms.openlocfilehash: 326caf550e8b138b4b968f0021a7fc475dc58c8d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59338078"
---
# <a name="walkthrough-simple-object-model-and-query-visual-basic"></a>İzlenecek yol: Basit Nesne Modeli ve Sorgu (Visual Basic)
Bu izlenecek yol sağlayan bir temel için uçtan uca [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] en düşük karmaşıklık bir senaryodur. Örnek Northwind veritabanındaki Müşteriler tablosunu modeller bir varlık sınıfı oluşturur. Ardından, Londra'da buluna listesi müşteriler için basit bir sorgu oluşturur.  
  
 Bu izlenecek yol, kod odaklı yardımcı olmak için tasarım gereği Göster [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kavramları. Kullanacağınız normalde Konuşmayı [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] , nesne modeli oluşturun.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Bu izlenecek yol, Visual Basic geliştirme ayarlarını kullanarak yazılmıştır.  
  
## <a name="prerequisites"></a>Önkoşullar  
  
-   Bu izlenecek yol, dosyaları tutmak için ayrılmış bir klasör ("c:\linqtest") kullanır. İzlenecek yol başlamadan önce bu klasörü oluşturun.  
  
-   Bu izlenecek yol, Northwind örnek veritabanıyla kurulan gerektirir. Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Yükleme sitesinden indirebilirsiniz. Yönergeler için [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Veritabanı indirdikten sonra dosyayı c:\linqtest klasöre kopyalayın.  
  
## <a name="overview"></a>Genel Bakış  
 Bu kılavuz altı ana görevden oluşur:  
  
-   Oluşturma bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Visual Studio'daki çözüm.  
  
-   Bir sınıf, bir veritabanı tablosuna eşleme.  
  
-   Veritabanı sütunlarını gösteren sınıf özelliklerini belirleme.  
  
-   Northwind veritabanına bir bağlantı belirtme.  
  
-   Veritabanına karşı çalıştırmak için basit bir sorgu oluşturma.  
  
-   Sorguyu yürüten ve sonuçları gözleme.  
  
## <a name="creating-a-linq-to-sql-solution"></a>Bir LINQ to SQL çözümü oluşturma  
 Bu ilk görevde oluşturduğunuz derlemek ve çalıştırmak için gerekli başvuruları içeren bir Visual Studio çözümü bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] proje.  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>Bir LINQ to SQL çözümü oluşturmak için  
  
1. Üzerinde **dosya** menüsünü tıklatın **yeni proje**.  
  
2. İçinde **proje türleri** bölmesinde **yeni proje** iletişim kutusu, tıklayın **Visual Basic**.  
  
3. İçinde **şablonları** bölmesinde tıklayın **konsol uygulaması**.  
  
4. İçinde **adı** kutusuna **LinqConsoleApp**.  
  
5. **Tamam**'ı tıklatın.  
  
## <a name="adding-linq-references-and-directives"></a>LINQ başvuruları ve yönergeleri ekleme  
 Bu izlenecek yol, projenizdeki varsayılan olarak yüklü olmayabilir derlemeleri kullanır. Varsa `System.Data.Linq` projenize bir başvuru olarak listelenmemiş (tıklayın **tüm dosyaları göster** içinde **Çözüm Gezgini** genişletin **başvuruları** düğümü), açıklandığı gibi ekleyin Aşağıdaki adımlar.  
  
#### <a name="to-add-systemdatalinq"></a>System.Data.Linq eklemek için  
  
1. İçinde **Çözüm Gezgini**, sağ **başvuruları**ve ardından **Başvuru Ekle**.  
  
2. İçinde **Başvuru Ekle** iletişim kutusu, tıklayın **.NET**System.Data.Linq derleme tıklayın ve ardından **Tamam**.  
  
     Derleme, projeye eklenir.  
  
3. Ayrıca **Başvuru Ekle** iletişim kutusu, tıklayın **.NET**kaydırın ve System.Windows.Forms öğelerini tıklayın ve ardından **Tamam**.  
  
     İleti kutusu izlenecek yolda destekler, bu derleme, projeye eklenir.  
  
4. Yukarıdaki aşağıdaki yönergeleri ekleme `Module1`:  
  
     [!code-vb[DLinqWalk1VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#1)]  
  
## <a name="mapping-a-class-to-a-database-table"></a>Bir sınıf için bir veritabanı tablosu eşleme  
 Bu adımda, bir sınıf oluşturun ve bir veritabanı tablosuna eşleyin. Bu tür bir sınıf olarak adlandırılır bir *varlık sınıfı*. Eşleme yalnızca ekleyerek gerçekleştirilir Not <xref:System.Data.Linq.Mapping.TableAttribute> özniteliği. <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> Özelliği veritabanında tablo adını belirtir.  
  
#### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a>Bir varlık sınıfı oluşturun ve bir veritabanı tablosuna eşlemek için  
  
-   Yazın veya Module1.vb hemen yukarıdaki aşağıdaki kodu yapıştırın `Sub Main`:  
  
     [!code-vb[DLinqWalk1VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#2)]  
  
## <a name="designating-properties-on-the-class-to-represent-database-columns"></a>Veritabanı sütunlarını gösteren sınıf özelliklerini belirleme  
 Bu adımda, çeşitli görevleri gerçekleştirirsiniz.  
  
-   Kullandığınız <xref:System.Data.Linq.Mapping.ColumnAttribute> belirtmek için özniteliği `CustomerID` ve `City` sınıf özellikleri varlığı temsil eden bir veritabanı tablosundaki sütun olarak.  
  
-   Belirlediğiniz `CustomerID` veritabanı birincil anahtar sütunu temsil eden olarak özelliği.  
  
-   Belirlediğiniz `_CustomerID` ve `_City` özel depolama alanları. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sonra depolayabilir ve iş mantığı içerebilecek ortak erişimciler kullanmak yerine doğrudan değerleri alabilirsiniz.  
  
#### <a name="to-represent-characteristics-of-two-database-columns"></a>İki veritabanı sütun özellikleri temsil etmek için  
  
-   Yazın veya Module1.vb aşağıdaki kodu yapıştırın, hemen önce `End Class`:  
  
     [!code-vb[DLinqWalk1VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#3)]  
  
## <a name="specifying-the-connection-to-the-northwind-database"></a>Northwind veritabanına bir bağlantı belirtme  
 Bu adımda kullandığınız bir <xref:System.Data.Linq.DataContext> , kod tabanlı veri yapıları ve veritabanı arasında bir bağlantı kurmak için nesne. <xref:System.Data.Linq.DataContext> Ana kanal üzerinden veritabanından nesneleri almak ve değişiklikleri gönderme.  
  
 Ayrıca bildirdiğiniz bir `Table(Of Customer)` veritabanındaki Müşteriler tablosunu karşı sorgularınız için mantıksal, belirlenmiş tablosu olarak görev yapacak. Oluşturacak ve sonraki adımlarda aşağıdaki sorguları yürütün.  
  
#### <a name="to-specify-the-database-connection"></a>Veritabanı bağlantısını belirtmek için  
  
-   İçine aşağıdaki kodu yazın veya yapıştırın `Sub Main` yöntemi.  
  
     Unutmayın `northwnd.mdf` linqtest klasörü içinde dosya varsayılır. Daha fazla bilgi için bu kılavuzda daha önce açıklanan Önkoşullar bölümüne bakın.  
  
     [!code-vb[DLinqWalk1VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#4)]  
  
## <a name="creating-a-simple-query"></a>Basit bir sorgu oluşturma  
 Bu adımda, veritabanı Müşteriler tablosundaki hangi müşteriler Londra'da bulmak için bir sorgu oluşturun. Bu adımda sorgu kod yalnızca sorgu açıklar. Bunu yürütmez. Bu yaklaşım olarak da bilinen *ertelenmiş yürütme*. Daha fazla bilgi için [(C#) LINQ sorgularına giriş](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 Ayrıca SQL göstermek için bir günlük çıktı üretebilir komutlarının olacak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] oluşturur. Bu günlük özelliğini (kullanan <xref:System.Data.Linq.DataContext.Log%2A>) hata ayıklama ve doğru bir şekilde veritabanına gönderilen komutları sorgunuzu temsil belirlemede yararlıdır.  
  
#### <a name="to-create-a-simple-query"></a>Basit bir sorgu oluşturmak için  
  
-   İçine aşağıdaki kodu yazın veya yapıştırın `Sub Main` sonrasına `Table(Of Customer)` bildirimi:  
  
     [!code-vb[DLinqWalk1AVB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#5)]  
  
## <a name="executing-the-query"></a>Sorgu yürütülüyor  
 Bu adımda, aslında sorguyu yürütün. Sonuçları gerekli olana kadar önceki adımlarda oluşturulan sorgu ifadeleri değerlendirilmez. Başladığınızda `For Each` yineleme, veritabanında bir SQL komutu yürütülür ve nesneleri gerçekleştirilmiş.  
  
#### <a name="to-execute-the-query"></a>Sorguyu yürütmek için  
  
1. Sonuna aşağıdaki kodu yapıştırın veya yazın `Sub Main` yöntemi (sonra sorgu açıklama):  
  
     [!code-vb[DLinqWalk1AVB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#6)]  
  
2. Uygulamada hata ayıklamak için F5 tuşuna basın.  
  
    > [!NOTE]
    >  Uygulamanızı bir çalışma zamanı hatası oluşturur, sorun giderme bölümüne bakın. [izlenecek yollarla öğrenme](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).  
  
     İleti kutusunda altı Müşteri listesini görüntüler. Konsol penceresinde oluşturulan SQL kodunu görüntüler.  
  
3. Tıklayın **Tamam** ileti kutusunu kapatın.  
  
     Uygulamayı kapatır.  
  
4. Üzerinde **dosya** menüsünü tıklatın **Tümünü Kaydet**.  
  
     Sonraki adım adım kılavuza devam ederseniz, bu uygulama gerekir.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 [İzlenecek yol: İlişkiler üzerinde sorgulama (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md) konu, bu gözden geçirme sona ereceği devam eder. İlişkiler üzerinde sorgulama yönerge gösterir nasıl [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tablolarda, benzer şekilde sorgulayabilirsiniz *birleştirmeler* ilişkisel bir veritabanındaki.  
  
 İlişkiler üzerinde sorgulama Kılavuzu uygulamak istiyorsanız, önkoşul olan çözüm geçirmesini tamamladınız, gözden geçirme için kaydettiğinizden emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek Yollarla Öğrenme](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
