---
title: "İzlenecek yol: Basit bir nesne modeli ve sorgu (C#)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 419961cc-92d6-45f5-ae8a-d485bdde3a37
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 1c118948f0eac8a9df81432b75297511172b10f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-simple-object-model-and-query-c"></a>İzlenecek yol: Basit bir nesne modeli ve sorgu (C#)
Bu kılavuz bir temel uçtan uca sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] en düşük karmaşıklık senaryoyla. Örnek Northwind veritabanı Müşteriler tablosunda modeller bir varlık sınıfı oluşturur. Ardından, Londra'da buluna listesi müşteriler için basit bir sorgu oluşturur.  
  
 Bu kılavuzda kod odaklı yardımcı olmak için tasarım gereği Göster [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kavramları. Kullanacağınız normalde konuşarak [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] nesne modeli oluşturmak için.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Bu kılavuz, Visual C# geliştirme ayarları kullanılarak yazılmıştır.  
  
## <a name="prerequisites"></a>Önkoşullar  
  
-   Bu kılavuzda, dosyaları tutmak için ayrılmış bir klasör ("c:\linqtest5") kullanılır. İzlenecek yol başlamadan önce bu klasörü oluşturun.  
  
-   Bu kılavuz, Northwind örnek veritabanı gerektirir. Bu veritabanı geliştirme bilgisayarınızda yoksa Microsoft sitesinden indirebilirsiniz. Yönergeler için bkz: [örnek veritabanları yükleme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Veritabanı indirdikten sonra dosyanın c:\linqtest5 klasörüne kopyalayın.  
  
## <a name="overview"></a>Genel Bakış  
 Bu kılavuz altı ana görevden oluşur:  
  
-   Oluşturma bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çözümde [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].  
  
-   Bir sınıf bir veritabanı tablosuna eşleme.  
  
-   Veritabanı sütunlarını temsil etmek için sınıfındaki özellikleri belirleme.  
  
-   Northwind veritabanı bağlantısı belirtme.  
  
-   Veritabanına karşı çalıştırmak için basit bir sorgu oluşturma.  
  
-   Sorgu yürütülürken ve sonuçları gözlemleyebilirsiniz.  
  
## <a name="creating-a-linq-to-sql-solution"></a>Bir LINQ to SQL çözümü oluşturma  
 Bu ilk görevde oluşturduğunuz bir [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] derlemek ve çalıştırmak için gerekli başvuruları içeren çözüm bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projesi.  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>Bir LINQ to SQL çözümü oluşturmak için  
  
1.  Üzerinde [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **dosya** menüsündeki **yeni**ve ardından **proje**.  
  
2.  İçinde **proje türleri** bölmesinde **yeni proje** iletişim kutusu, tıklatın **Visual C#**.  
  
3.  İçinde **şablonları** bölmesinde tıklatın **konsol uygulaması**.  
  
4.  İçinde **adı** kutusuna **LinqConsoleApp**.  
  
5.  İçinde **konumu** kutusunda, proje dosyalarını depolamak istediğiniz doğrulayın.  
  
6.  **Tamam**'ı tıklatın.  
  
## <a name="adding-linq-references-and-directives"></a>LINQ başvuruları ve yönergeleri ekleme  
 Bu kılavuzda projenizdeki varsayılan olarak yüklü olmayabilir derlemeleri kullanılır. System.Data.Linq projenize başvuru olarak listeleniyorsa değil (genişletin **başvuruları** düğümünde **Çözüm Gezgini**), bunu, aşağıdaki adımlarda açıklandığı gibi ekleyin.  
  
#### <a name="to-add-systemdatalinq"></a>System.Data.Linq eklemek için  
  
1.  İçinde **Çözüm Gezgini**, sağ **başvuruları**ve ardından **Başvuru Ekle**.  
  
2.  İçinde **Başvuru Ekle** iletişim kutusu, tıklatın **.NET**System.Data.Linq derleme'yi tıklayın ve ardından **Tamam**.  
  
     Derleme projeye eklenir.  
  
3.  Aşağıdaki yönergeleri en üstünde ekleyin **Program.cs**:  
  
     [!code-csharp[DLinqWalk1CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#1)]  
  
## <a name="mapping-a-class-to-a-database-table"></a>Bir sınıf bir veritabanı tablosuna eşleme  
 Bu adımda, bir sınıf oluşturun ve bir veritabanı tablosuna eşleyin. Bu tür bir sınıf olarak adlandırılır bir *varlık sınıfı*. Eşleme yalnızca ekleyerek gerçekleştirilir Not <xref:System.Data.Linq.Mapping.TableAttribute> özniteliği. <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> Özelliği, veritabanında tablonun adını belirtir.  
  
#### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a>Bir varlık sınıfı oluşturmak ve bir veritabanı tablosuna eşlemek için  
  
-   Yazın veya Program.cs hemen yukarıdaki aşağıdaki kodu yapıştırın `Program` sınıf bildiriminin:  
  
     [!code-csharp[DLinqWalk1CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#2)]  
  
## <a name="designating-properties-on-the-class-to-represent-database-columns"></a>Veritabanı sütunlarını temsil etmek için sınıfındaki özellikleri belirleme  
 Bu adımda, çeşitli görevleri yerine getirin.  
  
-   Kullandığınız <xref:System.Data.Linq.Mapping.ColumnAttribute> belirlemek için öznitelik `CustomerID` ve `City` sınıf özellikleri varlık üzerinde veritabanı tablosundaki sütunlarla temsil eden olarak.  
  
-   Belirttiğiniz `CustomerID` veritabanının birincil anahtar sütunu temsil eden olarak özelliği.  
  
-   Belirttiğiniz `_CustomerID` ve `_City` özel depolama alanları. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ardından depolayabilir ve iş mantığı içerebilecek ortak erişimciler kullanmak yerine doğrudan değerleri alabilirsiniz.  
  
#### <a name="to-represent-characteristics-of-two-database-columns"></a>İki veritabanı sütun özelliklerini göstermek için  
  
-   Yazın veya için süslü ayraçlar içinde Program.cs aşağıdaki kodu yapıştırın `Customer` sınıfı.  
  
     [!code-csharp[DLinqWalk1CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#3)]  
  
## <a name="specifying-the-connection-to-the-northwind-database"></a>Northwind veritabanı bağlantısı belirtme  
 Bu adımda, kullandığınız bir <xref:System.Data.Linq.DataContext> nesnesi, kod tabanlı veri yapılarını ve veritabanının kendisi arasında bağlantı kurun. <xref:System.Data.Linq.DataContext> Ana kanal üzerinden veritabanından nesneleri almak ve değişiklikleri gönderir.  
  
 Ayrıca bildirme bir `Table<Customer>` veritabanı Müşteriler tablosunda, sorguları için mantıksal, yazılı tablo olarak hareket edecek. Oluşturacak ve daha sonraki adımlarda bu sorgular yürütün.  
  
#### <a name="to-specify-the-database-connection"></a>Veritabanı bağlantısını belirtmek için  
  
-   Uygulamasına aşağıdaki kodu yazın veya yapıştırın `Main` yöntemi.  
  
     Unutmayın `northwnd.mdf` dosya linqtest5 klasöründe olarak varsayılır. Daha fazla bilgi için bu kılavuzda daha önce Önkoşullar bölümüne bakın.  
  
     [!code-csharp[DLinqWalk1CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#4)]  
  
## <a name="creating-a-simple-query"></a>Basit bir sorgu oluşturma  
 Bu adımda, hangi müşterilerin veritabanı Müşteriler tablosunda Londra'da bulmak için bir sorgu oluşturun. Bu adımda sorgu kod yalnızca sorgu açıklar. Bunu yürütmez. Bu yaklaşım olarak bilinen *yürütme ertelenmiş*. Daha fazla bilgi için bkz: [LINQ sorgularını (C#) giriş](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 Ayrıca bir günlük çıktısı SQL göstermek için üretim komutları, olacak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] oluşturur. Bu günlük kaydı özelliği (kullanan <xref:System.Data.Linq.DataContext.Log%2A>) hata ayıklama ve veritabanına doğru gönderilen komutları sorgunuzu temsil ettiğini belirlemede yararlıdır.  
  
#### <a name="to-create-a-simple-query"></a>Basit bir sorgu oluşturmak için  
  
-   Uygulamasına aşağıdaki kodu yazın veya yapıştırın `Main` sonra yöntemi `Table<Customer>` bildirimi.  
  
     [!code-csharp[DLinqWalk1ACS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#5)]  
  
## <a name="executing-the-query"></a>Sorgu yürütme  
 Bu adımda, aslında sorgu yürütün. Sonuçları gerektiği kadar önceki adımlarda oluşturduğunuz sorgu ifadeleri değerlendirilmez. Başladığınızda `foreach` yineleme, veritabanında bir SQL komutu yürütülür ve nesneleri gerçekleştirilip.  
  
#### <a name="to-execute-the-query"></a>Sorguyu yürütmek için  
  
1.  Yazın veya sonuna aşağıdaki kodu yapıştırın `Main` yöntemi (sonra sorgu açıklama).  
  
     [!code-csharp[DLinqWalk1ACS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#6)]  
  
2.  Uygulamada hata ayıklama için F5 tuşuna basın.  
  
    > [!NOTE]
    >  Uygulamanızı bir çalışma zamanı hatası oluşturur, sorun giderme bölümüne bakın. [tarafından izlenecek yollar öğrenme](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).  
  
     Sorgu sonuçları konsol penceresinde aşağıdaki gibi görünmelidir:  
  
     `ID=AROUT, City=London`  
  
     `ID=BSBEV, City=London`  
  
     `ID=CONSH, City=London`  
  
     `ID=EASTC, City=London`  
  
     `ID=NORTS, City=London`  
  
     `ID=SEVES, City=London`  
  
3.  Konsol penceresinde uygulamayı kapatmak için Enter tuşuna basın.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 [İzlenecek yol: ilişkileri üzerinden sorgulama (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md) konu devam bu kılavuzda bittiği. Sorgu arasında ilişkiler yönergeyi gösterir nasıl [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tabloları, benzer arasında sorgulayabilirsiniz *birleştirmeler* ilişkisel bir veritabanındaki.  
  
 Sorgu arasında ilişkiler izlenecek yapmak istiyorsanız, çözüm geçirmesini tamamladınız, izlenecek yol için bir önkoşul olduğu kaydettiğinizden emin olun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek Yollarla Öğrenme](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
