---
title: 'İzlenecek yol: Verileri (C#) düzenleme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 24adfbe0-0ad6-449f-997d-8808e0770d2e
caps.latest.revision: 2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: d1851bd4c358b96cc9b49f274b31f5f69d9b8d7b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-manipulating-data-c"></a>İzlenecek yol: Verileri (C#) düzenleme
Bu kılavuz bir temel uçtan uca sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] senaryosu ekleme, değiştirme ve bir veritabanındaki verileri silme. Bir müşteri ekleyin, bir müşterinin adını değiştirin ve sipariş silmek için örnek Northwind veritabanının bir kopyasını kullanır.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Bu kılavuz, Visual C# geliştirme ayarları kullanılarak yazılmıştır.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu kılavuz aşağıdakileri gerektirir:  
  
-   Bu kılavuzda, dosyaları tutmak için ayrılmış bir klasör ("c:\linqtest6") kullanılır. İzlenecek yol başlamadan önce bu klasörü oluşturun.  
  
-   Northwind örnek veritabanı.  
  
     Bu veritabanı geliştirme bilgisayarınızda yoksa Microsoft sitesinden indirebilirsiniz. Yönergeler için bkz: [örnek veritabanları yükleme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Veritabanı indirdikten sonra northwnd.mdf dosyasını c:\linqtest6 klasörüne kopyalayın.  
  
-   Northwind veritabanından oluşturulan bir C# kod dosyası.  
  
     Bu dosyayı kullanarak oluşturabileceğiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] veya SQLMetal aracı. Bu kılavuz, aşağıdaki komut satırı ile SQLMetal aracı kullanılarak yazılmış olduğundan:  
  
     **sqlmetal /code:"c:\linqtest6\northwind.cs" /language:csharp "C:\linqtest6\northwnd.mdf" /pluralize**  
  
     Daha fazla bilgi için bkz: [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Genel Bakış  
 Bu kılavuz altı ana görevden oluşur:  
  
-   Oluşturma [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Visual Studio'da çözüm.  
  
-   Veritabanı kod dosyası projesine ekleniyor.  
  
-   Yeni bir müşteri nesnesi oluşturma.  
  
-   Bir müşterinin ilgili kişi adı değiştirme.  
  
-   Bir sipariş siliniyor.  
  
-   Bu değişiklikler Northwind veritabanına gönderiliyor.  
  
## <a name="creating-a-linq-to-sql-solution"></a>Bir LINQ to SQL çözümü oluşturma  
 Bu ilk görevde oluşturduğunuz derlemek ve çalıştırmak için gerekli başvuruları içeren bir Visual Studio çözümü bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projesi.  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>Bir LINQ to SQL çözümü oluşturmak için  
  
1.  Visual Studio üzerinde **dosya** menüsündeki **yeni**ve ardından **proje**.  
  
2.  İçinde **proje türleri** bölmesinde **yeni proje** iletişim kutusu, tıklatın **Visual C#**.  
  
3.  İçinde **şablonları** bölmesinde tıklatın **konsol uygulaması**.  
  
4.  İçinde **adı** kutusuna **LinqDataManipulationApp**.  
  
5.  İçinde **konumu** kutusunda, proje dosyalarını depolamak istediğiniz doğrulayın.  
  
6.  **Tamam**'ı tıklatın.  
  
## <a name="adding-linq-references-and-directives"></a>LINQ başvuruları ve yönergeleri ekleme  
 Bu kılavuzda projenizdeki varsayılan olarak yüklü olmayabilir derlemeleri kullanılır. System.Data.Linq projenize başvuru olarak listelenmemişse, aşağıdaki adımlarda açıklandığı gibi ekleyin:  
  
#### <a name="to-add-systemdatalinq"></a>System.Data.Linq eklemek için  
  
1.  İçinde **Çözüm Gezgini**, sağ **başvuruları**ve ardından **Başvuru Ekle**.  
  
2.  İçinde **Başvuru Ekle** iletişim kutusu, tıklatın **.NET**System.Data.Linq derleme'yi tıklayın ve ardından **Tamam**.  
  
     Derleme projeye eklenir.  
  
3.  Aşağıdaki yönergeleri Program.cs üstüne ekleyin:  
  
     [!code-csharp[DLinqWalk3CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>Northwind kod dosyası projeye ekleme  
 Bu adımlarda, SQLMetal aracı Northwind örnek veritabanı'ndaki bir kod dosyası oluşturmak için kullandığınız varsayılır. Daha fazla bilgi için bu kılavuzda daha önce Önkoşullar bölümüne bakın.  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>Northwind kod dosyası projeye eklemek için  
  
1.  Üzerinde **proje** menüsünde tıklatın **varolan öğeyi Ekle**.  
  
2.  İçinde **varolan öğeyi Ekle** iletişim kutusu için c:\linqtest6\northwind.cs gidin ve ardından **Ekle**.  
  
     Northwind.cs dosyası projeye eklenir.  
  
## <a name="setting-up-the-database-connection"></a>Veritabanı bağlantısı kurma  
 İlk olarak, veritabanı bağlantınızı test edin. Özellikle veritabanında Northwnd, hiçbir i olduğunu unutmayın karakter. Sonraki adımlarda hatalara neden Northwind parçalı sınıf nasıl yazıldığını belirlemek için northwind.cs dosyasını gözden geçirin.  
  
#### <a name="to-set-up-and-test-the-database-connection"></a>Ayarlama ve veritabanı bağlantısını test etme  
  
1.  Uygulamasına aşağıdaki kodu yazın veya yapıştırın `Main` Program sınıftaki yöntemi:  
  
     [!code-csharp[DLinqWalk3CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#2)]  
  
2.  Bu noktada uygulamayı test etmek için F5 tuşuna basın.  
  
     A **konsol** penceresi açılır.  
  
     Enter tuşuna basarak uygulamanın kapatabilirsiniz **konsol** penceresinde veya tıklatarak **durdurma hata ayıklama** Visual Studio üzerinde **hata ayıklama** menüsü.  
  
## <a name="creating-a-new-entity"></a>Yeni bir varlık oluşturma  
 Yeni bir varlık oluşturma basittir. Nesne oluşturma (gibi `Customer`) kullanarak `new` anahtar sözcüğü.  
  
 Bu ve aşağıdaki bölümlerde, yalnızca yerel önbelleğe değişiklikler yapıyor. Çağrısı tamamlanana kadar hiçbir değişiklik veritabanına gönderilen <xref:System.Data.Linq.DataContext.SubmitChanges%2A> bu kılavuzda sonuna doğru.  
  
#### <a name="to-add-a-new-customer-entity-object"></a>Yeni bir müşteri varlık nesnesini eklemek için  
  
1.  Yeni bir `Customer` önce aşağıdaki kodu ekleyerek `Console.ReadLine();` içinde `Main` yöntemi:  
  
     [!code-csharp[DLinqWalk3CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#3)]  
  
2.  Çözüm hata ayıklamak için F5 tuşuna basın.  
  
3.  Enter tuşuna basın **konsol** penceresi hata ayıklamayı durdurun ve gözden geçirme devam edin.  
  
## <a name="updating-an-entity"></a>Bir varlık güncelleştiriliyor  
 Aşağıdaki adımlarda, alacak bir `Customer` nesne ve özelliklerinden biri değiştirin.  
  
#### <a name="to-change-the-name-of-a-customer"></a>Bir müşterinin adını değiştirmek için  
  
-   Yukarıdaki aşağıdaki kodu ekleyin `Console.ReadLine();`:  
  
     [!code-csharp[DLinqWalk3CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#4)]  
  
## <a name="deleting-an-entity"></a>Bir varlığı silme  
 Aynı müşteri nesnesini kullanarak, ilk sipariş silebilirsiniz.  
  
 Aşağıdaki kod ilişkileri sever gösterilmiştir satırları ve satır veritabanından silmek nasıl arasında. Önce aşağıdaki kodu ekleyin `Console.ReadLine` nesneler nasıl silinebilir görmek için:  
  
#### <a name="to-delete-a-row"></a>Bir satır silmek için  
  
-   Aşağıdaki kodu ekleyin yukarıdaki `Console.ReadLine();`:  
  
     [!code-csharp[DLinqWalk3CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#5)]  
  
## <a name="submitting-changes-to-the-database"></a>Veritabanı değişiklikleri gönderme  
 Oluşturmak için gereken son güncelleştirme ve silme nesneleri, aslında değişiklikler veritabanına göndermek için adımdır. Bu adım olmadan yaptığınız değişiklikler yalnızca yerel ve sorgu sonuçlarında görünmez.  
  
#### <a name="to-submit-changes-to-the-database"></a>Değişiklikler veritabanına göndermek için  
  
1.  Aşağıdaki kod yalnızca yukarıda INSERT `Console.ReadLine`:  
  
     [!code-csharp[DLinqWalk3CS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#6)]  
  
2.  Aşağıdaki kodu ekleyin (sonra `SubmitChanges`) göstermek için önce ve sonra değişiklikleri gönderme etkilerini:  
  
     [!code-csharp[DLinqWalk3CS#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#7)]  
  
3.  Çözüm hata ayıklamak için F5 tuşuna basın.  
  
4.  Enter tuşuna basın **konsol** uygulamayı kapatmak için penceresi.  
  
> [!NOTE]
>  Değişiklikleri göndererek yeni müşteri ekledikten sonra bu çözüm yürütülemiyor olduğu gibi yeniden. Çözümü yeniden çalıştırmak için Müşteri Kimliği ve müşteri eklenecek adını değiştirin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek Yollarla Öğrenme](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
