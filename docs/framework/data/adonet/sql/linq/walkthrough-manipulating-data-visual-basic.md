---
title: 'İzlenecek yol: (Visual Basic) verileri düzenleme'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 1f6a54f6-ec33-452a-a37d-48122207bf14
ms.openlocfilehash: 0eab5fe5c9455badb7f538307cb827391b254a95
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626933"
---
# <a name="walkthrough-manipulating-data-visual-basic"></a>İzlenecek yol: (Visual Basic) verileri düzenleme
Bu izlenecek yol sağlayan bir temel için uçtan uca [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] senaryo ekleme, değiştirme ve bir veritabanındaki verileri siliniyor. Örnek Northwind veritabanının bir kopyasını bir müşteri eklemek, bir müşterinin adını değiştirin ve sipariş silmek için kullanın.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Bu izlenecek yol, Visual Basic geliştirme ayarlarını kullanarak yazılmıştır.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yol aşağıdakileri gerektirir:  
  
-   Bu izlenecek yol, dosyaları tutmak için ayrılmış bir klasör ("c:\linqtest2") kullanır. İzlenecek yol başlamadan önce bu klasörü oluşturun.  
  
-   Northwind örnek veritabanı.  
  
     Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Yükleme sitesinden indirebilirsiniz. Yönergeler için [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Veritabanı indirdikten sonra northwnd.mdf dosya c:\linqtest2 klasöre kopyalayın.  
  
-   Northwind veritabanından oluşturulan Visual Basic kod dosyası.  
  
     Bu dosyayı kullanarak oluşturabileceğiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] veya SQLMetal aracı. Bu izlenecek yol, şu komut satırıyla SQLMetal Aracı'nı kullanarak yazılmıştır:  
  
     **sqlmetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" /pluralize**  
  
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
  
1.  Visual Studio **dosya** menüsünü tıklatın **yeni proje**.  
  
2.  İçinde **proje türleri** bölmesinde **yeni proje** iletişim kutusu, tıklayın **Visual Basic**.  
  
3.  İçinde **şablonları** bölmesinde tıklayın **konsol uygulaması**.  
  
4.  İçinde **adı** kutusuna **LinqDataManipulationApp**.  
  
5.  **Tamam**'ı tıklatın.  
  
## <a name="adding-linq-references-and-directives"></a>LINQ başvuruları ve yönergeleri ekleme  
 Bu izlenecek yol, projenizdeki varsayılan olarak yüklü olmayabilir derlemeleri kullanır. Varsa `System.Data.Linq` projenize bir başvuru olarak listelenmemiş (tıklayın **tüm dosyaları göster** içinde **Çözüm Gezgini** genişletin **başvuruları** düğümü), açıklandığı gibi ekleyin Aşağıdaki adımlar.  
  
#### <a name="to-add-systemdatalinq"></a>System.Data.Linq eklemek için  
  
1.  İçinde **Çözüm Gezgini**, sağ **başvuruları**ve ardından **Başvuru Ekle**.  
  
2.  İçinde **Başvuru Ekle** iletişim kutusu, tıklayın **.NET**System.Data.Linq derleme tıklayın ve ardından **Tamam**.  
  
     Derleme, projeye eklenir.  
  
3.  Kod Düzenleyicisi'nde, aşağıdaki yönergeleri yukarıdaki Ekle **Module1**:  
  
     [!code-vb[DLinqWalk3VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>Northwind kod dosyası projeye ekleniyor  
 Bu adımları, Northwind örnek veritabanındaki bir kod dosyası oluşturmak için SQLMetal Aracı'nı kullandığınızı varsayar. Daha fazla bilgi için bu kılavuzda daha önce açıklanan Önkoşullar bölümüne bakın.  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>Northwind kod dosyası projeye eklemek için  
  
1.  Üzerinde **proje** menüsünde tıklatın **varolan öğeyi Ekle**.  
  
2.  İçinde **varolan öğeyi Ekle** iletişim kutusu için c:\linqtest2\northwind.vb gidin ve ardından **Ekle**.  
  
     Northwind.vb dosya projeye eklenir.  
  
## <a name="setting-up-the-database-connection"></a>Veritabanı bağlantısı kurma  
 İlk olarak, veritabanı bağlantınızı test edin. Özellikle Northwnd, veritabanının adı yok i olduğunu unutmayın. karakter. Sonraki adımlarda hatalar oluşturur, Northwind kısmi sınıf nasıl yazıldığını belirlemek için northwind.vb dosyasını gözden geçirin.  
  
#### <a name="to-set-up-and-test-the-database-connection"></a>Veritabanı bağlantısını test etmek ve ayarlamak için  
  
1.  İçine aşağıdaki kodu yazın veya yapıştırın `Sub Main`:  
  
     [!code-vb[DLinqWalk3VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#2)]  
  
2.  Bu noktada uygulamayı test etmek için F5 tuşuna basın.  
  
     A **konsol** penceresi açılır.  
  
     Enter tuşuna basarak uygulamayı kapatmak **konsol** penceresinde veya tıklayarak **hata ayıklamayı Durdur** Visual Studio **hata ayıklama** menüsü.  
  
## <a name="creating-a-new-entity"></a>Yeni varlık oluşturma  
 Yeni bir varlık oluştururken oldukça basittir. Nesneleri oluşturabilirsiniz (gibi `Customer`) kullanarak `New` anahtar sözcüğü.  
  
 Bu ve aşağıdaki bölümler, yalnızca yerel önbelleğe değişiklikler yaparsınız. Çağırana kadar hiçbir değişiklik veritabanına gönderilmez <xref:System.Data.Linq.DataContext.SubmitChanges%2A> Bu izlenecek yolun sonuna doğru.  
  
#### <a name="to-add-a-new-customer-entity-object"></a>Yeni bir müşteri varlığı nesne eklemek için  
  
1.  Yeni bir `Customer` önce aşağıdaki kodu ekleyerek `Console.ReadLine` içinde `Sub Main`:  
  
     [!code-vb[DLinqWalk3VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#3)]  
  
2.  Çözüm hata ayıklamak için F5 tuşuna basın.  
  
     Konsol penceresinde gösterilen sonuçları aşağıdaki gibidir:  
  
     `Customers matching CA before insert:`  
  
     `Customer ID: CACTU`  
  
     `Customer ID: RICAR`  
  
     Yeni satır sonuçlarında görünmez unutmayın. Veritabanına yeni veriler henüz gönderilmedi.  
  
3.  Enter tuşuna basarak **konsol** penceresi hata ayıklamayı durdurmak için.  
  
## <a name="updating-an-entity"></a>Bir varlığı güncelleştirmek  
 Aşağıdaki adımlarda, alacak bir `Customer` nesne ve onun özelliklerden birini değiştirin.  
  
#### <a name="to-change-the-name-of-a-customer"></a>Bir müşteri adını değiştirmek için  
  
-   Yukarıdaki aşağıdaki kodu ekleyin `Console.ReadLine()`:  
  
     [!code-vb[DLinqWalk3VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#4)]  
  
## <a name="deleting-an-entity"></a>Bir varlığı silme  
 Aynı müşteri nesnesini kullanarak, ilk sırada silebilirsiniz.  
  
 Aşağıdaki kod ilişkileri sever gösterilmektedir satırlar ve veritabanından satır silme arasında.  
  
#### <a name="to-delete-a-row"></a>Bir satırı silmek için  
  
-   Aşağıdaki kodu ekleyin hemen üzerinde `Console.ReadLine()`:  
  
     [!code-vb[DLinqWalk3VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#5)]  
  
## <a name="submitting-changes-to-the-database"></a>Veritabanına değişiklikleri gönderme  
 Son adım gereklidir oluşturmak için güncelleştirme ve silme nesneleri gerçekten veritabanına değişiklikleri göndermek için. Bu adım olmadan yaptığınız değişiklikleri yalnızca yerel ve sorgu sonuçlarında görünmez.  
  
#### <a name="to-submit-changes-to-the-database"></a>Değişiklikleri veritabanına göndermek için  
  
1.  Aşağıdaki kod hemen üstüne INSERT `Console.ReadLine`:  
  
     [!code-vb[DLinqWalk3VB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#6)]  
  
2.  Aşağıdaki kodu ekleyin (sonra `SubmitChanges`) göstermek için önce ve etkileri değişiklikleri gönderdikten sonra:  
  
     [!code-vb[DLinqWalk3VB#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#7)]  
  
3.  Çözüm hata ayıklamak için F5 tuşuna basın.  
  
     Konsol penceresinde aşağıdaki gibi görünür:  
  
    ```  
    Customers matching CA before update:  
    Customer ID: CACTU  
    Customer ID: RICAR  
  
    The Order Detail to be deleted is: OrderID = 10643  
  
    Customers matching CA after update:  
    Customer ID: A3VCA  
    Customer ID: CACTU  
    Customer ID: RICAR  
    ```  
  
4.  Enter tuşuna basarak **konsol** penceresi hata ayıklamayı durdurmak için.  
  
> [!NOTE]
>  Değişiklikleri göndererek yeni müşteri ekledikten sonra bu çözüm yürütülemiyor yeniden olduğu gibi aynı müşteriye tekrar ekleyemezsiniz olmasıdır. Çözümü yeniden çalıştırmak için eklenecek müşteri Kimliğini değiştirin.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek Yollarla Öğrenme](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
