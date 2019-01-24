---
title: 'İzlenecek yol: Verileri düzenleme (C#)'
ms.date: 03/30/2017
ms.assetid: 24adfbe0-0ad6-449f-997d-8808e0770d2e
ms.openlocfilehash: a4346479337820f33cc908c0fd191ee7258a3db6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54637313"
---
# <a name="walkthrough-manipulating-data-c"></a>İzlenecek yol: Verileri düzenleme (C#)
Bu izlenecek yol sağlayan bir temel için uçtan uca [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] senaryo ekleme, değiştirme ve bir veritabanındaki verileri siliniyor. Örnek Northwind veritabanının bir kopyasını bir müşteri eklemek, bir müşterinin adını değiştirin ve sipariş silmek için kullanın.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Bu izlenecek yol, Visual kullanılarak yazılmış olduğundan C# geliştirme ayarları.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yol aşağıdakileri gerektirir:  
  
-   Bu izlenecek yol, dosyaları tutmak için ayrılmış bir klasör ("c:\linqtest6") kullanır. İzlenecek yol başlamadan önce bu klasörü oluşturun.  
  
-   Northwind örnek veritabanı.  
  
     Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Yükleme sitesinden indirebilirsiniz. Yönergeler için [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Veritabanı indirdikten sonra northwnd.mdf dosya c:\linqtest6 klasöre kopyalayın.  
  
-   A C# Northwind veritabanından oluşturulan kod dosyası.  
  
     Bu dosyayı kullanarak oluşturabileceğiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] veya SQLMetal aracı. Bu izlenecek yol, şu komut satırıyla SQLMetal Aracı'nı kullanarak yazılmıştır:  
  
     **sqlmetal /code:"c:\linqtest6\northwind.cs" /language:csharp "C:\linqtest6\northwnd.mdf" /pluralize**  
  
     Daha fazla bilgi için [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Genel Bakış  
 Bu kılavuz altı ana görevden oluşur:  
  
-   Oluşturma [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Visual Studio'daki çözüm.  
  
-   Veritabanı kod dosyası projeye ekleniyor.  
  
-   Yeni bir müşteri nesnesi oluşturuluyor.  
  
-   Bir müşteri kişi adını değiştirme.  
  
-   Bir sipariş siliniyor.  
  
-   Bu değişiklikler Northwind veritabanına gönderiliyor.  
  
## <a name="creating-a-linq-to-sql-solution"></a>Bir LINQ to SQL çözümü oluşturma  
 Bu ilk görevde oluşturduğunuz derlemek ve çalıştırmak için gerekli başvuruları içeren bir Visual Studio çözümü bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] proje.  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>Bir LINQ to SQL çözümü oluşturmak için  
  
1.  Visual Studio'da **dosya** menüsünde **yeni**ve ardından **proje**.  
  
2.  İçinde **proje türleri** bölmesinde **yeni proje** iletişim kutusu, tıklayın **Visual C#** .  
  
3.  İçinde **şablonları** bölmesinde tıklayın **konsol uygulaması**.  
  
4.  İçinde **adı** kutusuna **LinqDataManipulationApp**.  
  
5.  İçinde **konumu** kutusunda, proje dosyalarını depolamak istediğiniz doğrulayın.  
  
6.  **Tamam**'ı tıklatın.  
  
## <a name="adding-linq-references-and-directives"></a>LINQ başvuruları ve yönergeleri ekleme  
 Bu izlenecek yol, projenizdeki varsayılan olarak yüklü olmayabilir derlemeleri kullanır. Projenize bir başvuru olarak System.Data.Linq listede yoksa, aşağıdaki adımlarda açıklandığı gibi ekleyin:  
  
#### <a name="to-add-systemdatalinq"></a>System.Data.Linq eklemek için  
  
1.  İçinde **Çözüm Gezgini**, sağ **başvuruları**ve ardından **Başvuru Ekle**.  
  
2.  İçinde **Başvuru Ekle** iletişim kutusu, tıklayın **.NET**System.Data.Linq derleme tıklayın ve ardından **Tamam**.  
  
     Derleme, projeye eklenir.  
  
3.  Aşağıdaki yönergeler, Program.cs dosyasının en üstüne ekleyin:  
  
     [!code-csharp[DLinqWalk3CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>Northwind kod dosyası projeye ekleniyor  
 Bu adımları, Northwind örnek veritabanındaki bir kod dosyası oluşturmak için SQLMetal Aracı'nı kullandığınızı varsayar. Daha fazla bilgi için bu kılavuzda daha önce açıklanan Önkoşullar bölümüne bakın.  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>Northwind kod dosyası projeye eklemek için  
  
1.  Üzerinde **proje** menüsünde tıklatın **varolan öğeyi Ekle**.  
  
2.  İçinde **varolan öğeyi Ekle** iletişim kutusu için c:\linqtest6\northwind.cs gidin ve ardından **Ekle**.  
  
     Northwind.cs dosya projeye eklenir.  
  
## <a name="setting-up-the-database-connection"></a>Veritabanı bağlantısı kurma  
 İlk olarak, veritabanı bağlantınızı test edin. Özellikle veritabanı Northwnd, hiçbir i olduğunu unutmayın. karakter. Sonraki adımlarda hatalar oluşturur, Northwind kısmi sınıf nasıl yazıldığını belirlemek için northwind.cs dosyasını gözden geçirin.  
  
#### <a name="to-set-up-and-test-the-database-connection"></a>Veritabanı bağlantısını test etmek ve ayarlamak için  
  
1.  İçine aşağıdaki kodu yazın veya yapıştırın `Main` Program sınıfına yöntemi:  
  
     [!code-csharp[DLinqWalk3CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#2)]  
  
2.  Bu noktada uygulamayı test etmek için F5 tuşuna basın.  
  
     A **konsol** penceresi açılır.  
  
     Enter tuşuna basarak uygulamayı kapatabilirsiniz **konsol** penceresinde veya tıklayarak **hata ayıklamayı Durdur** Visual Studio **hata ayıklama** menüsü.  
  
## <a name="creating-a-new-entity"></a>Yeni varlık oluşturma  
 Yeni bir varlık oluştururken oldukça basittir. Nesneleri oluşturabilirsiniz (gibi `Customer`) kullanarak `new` anahtar sözcüğü.  
  
 Bu ve aşağıdaki bölümler, yalnızca yerel önbelleğe değişiklikler yaparsınız. Çağırana kadar hiçbir değişiklik veritabanına gönderilmez <xref:System.Data.Linq.DataContext.SubmitChanges%2A> Bu izlenecek yolun sonuna doğru.  
  
#### <a name="to-add-a-new-customer-entity-object"></a>Yeni bir müşteri varlığı nesne eklemek için  
  
1.  Yeni bir `Customer` önce aşağıdaki kodu ekleyerek `Console.ReadLine();` içinde `Main` yöntemi:  
  
     [!code-csharp[DLinqWalk3CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#3)]  
  
2.  Çözüm hata ayıklamak için F5 tuşuna basın.  
  
3.  Enter tuşuna basarak **konsol** penceresi hata ayıklamayı durdurmak ve gözden geçirme devam etmek için.  
  
## <a name="updating-an-entity"></a>Bir varlığı güncelleştirmek  
 Aşağıdaki adımlarda, alacak bir `Customer` nesne ve onun özelliklerden birini değiştirin.  
  
#### <a name="to-change-the-name-of-a-customer"></a>Bir müşteri adını değiştirmek için  
  
-   Yukarıdaki aşağıdaki kodu ekleyin `Console.ReadLine();`:  
  
     [!code-csharp[DLinqWalk3CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#4)]  
  
## <a name="deleting-an-entity"></a>Bir varlığı silme  
 Aynı müşteri nesnesini kullanarak, ilk sırada silebilirsiniz.  
  
 Aşağıdaki kod ilişkileri sever gösterilmektedir satırlar ve veritabanından satır silme arasında. Önce aşağıdaki kodu ekleyin `Console.ReadLine` nesnelerin nasıl silinebilir görmek için:  
  
#### <a name="to-delete-a-row"></a>Bir satırı silmek için  
  
-   Aşağıdaki kodu ekleyin hemen üzerinde `Console.ReadLine();`:  
  
     [!code-csharp[DLinqWalk3CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#5)]  
  
## <a name="submitting-changes-to-the-database"></a>Veritabanına değişiklikleri gönderme  
 Oluşturmak için gereken son güncelleştirme ve silme nesneleri, aslında veritabanına değişiklikleri göndermek için adımdır. Bu adım olmadan yaptığınız değişiklikleri yalnızca yerel ve sorgu sonuçlarında görünmez.  
  
#### <a name="to-submit-changes-to-the-database"></a>Değişiklikleri veritabanına göndermek için  
  
1.  Aşağıdaki kod hemen üstüne INSERT `Console.ReadLine`:  
  
     [!code-csharp[DLinqWalk3CS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#6)]  
  
2.  Aşağıdaki kodu ekleyin (sonra `SubmitChanges`) göstermek için önce ve etkileri değişiklikleri gönderdikten sonra:  
  
     [!code-csharp[DLinqWalk3CS#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#7)]  
  
3.  Çözüm hata ayıklamak için F5 tuşuna basın.  
  
4.  Enter tuşuna basarak **konsol** uygulamayı kapatmak için penceresi.  
  
> [!NOTE]
>  Değişiklikleri göndererek yeni müşteri ekledikten sonra bu çözüm yürütülemez olduğu gibi yeniden. Çözümü yeniden çalıştırmak için Müşteri Kimliği ve müşteri eklenecek adını değiştirin.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek Yollarla Öğrenme](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
