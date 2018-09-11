---
title: İzlenecek yollarla öğrenme
ms.date: 03/30/2017
ms.assetid: a8ae2965-6a49-4155-89b0-7fab2c488ab1
ms.openlocfilehash: 1386d0e8fadddab5cd15818cb616bf331262e654
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44269133"
---
# <a name="learning-by-walkthroughs"></a>İzlenecek yollarla öğrenme
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Belgeler birkaç izlenecek yollar sağlar. Bu konu (sorun giderme dahil) bazı genel kılavuz sorunları ele alır ve hakkında bilgi almak için birkaç adım izlenecek yollar için bağlantılar sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
> [!NOTE]
>  Bu Başlarken bölümünde izlenecek destekleyen temel kod kullanıma [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] teknoloji. Gerçek bir uygulamada genellikle kullanacağınız [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] ve uygulamak için Windows Forms projeleri, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uygulamalar. [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] Belgeler, bu amaç için örnekler ve izlenecek yollar sağlar.  
  
## <a name="getting-started-walkthroughs"></a>Başlarken izlenecek yollar  
 Bu bölümde birkaç izlenecek yollar mevcuttur. Bu kılavuzlar, örnek Northwind veritabanına bağlı ve mevcut [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] en düşük karmaşıklık ile size bir hızda özellikleri.  
  
 Tipik ilerlemeyi izlemek için şu şekilde olacaktır:  
  
|Hedefi|Visual Basic|C#|  
|---------------|------------------|---------|  
|Bir varlık sınıfı oluşturun ve basit bir sorgu yürütün.|[İzlenecek yol: Basit Nesne Modeli ve Sorgu (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md)|[İzlenecek yol: Basit Nesne Modeli ve Sorgu (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md)|  
|İkinci bir sınıf ekleyin ve daha karmaşık bir sorgu yürütün.<br /><br /> (Önceki gözden geçirmede tamamlanmasından gerektirir).|[İzlenecek yol: İlişkilerde Sorgulama (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md)|[İzlenecek yol: İlişkilerde Sorgulama (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md)|  
|Ekleyin, değiştirin ve veritabanındaki öğeleri silin.|[İzlenecek yol: Verileri Düzenleme (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)|[İzlenecek yol: Verileri Düzenleme (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)|  
|Saklı yordamları kullanın.|[İzlenecek yol: Yalnızca Saklı Yordamlar Kullanma (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-visual-basic.md)|[İzlenecek yol: Yalnızca Saklı Yordamları Kullanma (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-csharp.md)|  
  
## <a name="general"></a>Genel  
 Aşağıdaki bilgiler, bu izlenecek yollar için genel ilgilidir:  
  
-   Ortam: Her [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] izlenecek yol, Visual Studio tümleşik geliştirme ortamı (IDE) kullanır.  
  
-   SQL altyapılarını: Bu izlenecek yollar, SQL Server Express kullanarak uygulanacak yazılır. SQL Server Express yoksa, ücretsiz olarak indirebilirsiniz. Daha fazla bilgi için [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
    > [!NOTE]
    >  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] izlenecek yollar, bağlantı dizesi olarak bir dosya adı kullanın. Kolaylık olması açısından olan yalnızca bir dosya adını belirterek, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kullanıcılar için SQL Server Express sağlar. Her zaman güvenlik sorunlarına dikkat edin. Daha fazla bilgi için [LINQ to SQL'de güvenlik](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md).  
  
-   [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] izlenecek yollar, Northwind örnek veritabanıyla kurulan genellikle gerektirir. Daha fazla bilgi için [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
-   İletişim kutuları ve menü komutları kılavuzları gördüğünüz açıklanana Yardım'da, etkin ayarlarınıza ve Visual Studio sürümü bağlı olarak farklı olabilir. Ayarlarınızı değiştirmek için tıklayın **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
-   Çok katmanlı senaryoları izlenecek yollar için geliştirme bilgisayardan ayrı olan bir bilgisayar bir sunucu bulunması gerekir ve sunucuya erişmek için uygun izinlere sahip olmalıdır.  
  
-   Siparişler tablosu Northwind örnek veritabanındaki genellikle temsil eden sınıfı adı `[Order]`. Kaçış gereklidir çünkü `Order` Visual Basic'te bir anahtar sözcüktür.  
  
## <a name="troubleshooting"></a>Sorun giderme  
 Bu izlenecek yollarında kullanılan veritabanları erişmek için yeterli izinlere sahip olmadığınızdan çalışma zamanı hataları oluşabilir. En yaygın olarak bu sorunları gidermek için aşağıdaki adımlara bakın.  
  
### <a name="log-on-issues"></a>Oturum açma sorunları  
 Uygulamanızı kabul etmediği bir veritabanında oturum açma yoluyla veritabanına erişmeye çalışıyor olabilir.  
  
##### <a name="to-verify-or-change-the-database-log-on"></a>Doğrulamak veya değiştirmek için veritabanı oturum açın  
  
1.  Windows üzerinde **Başlat** menüsünde **tüm programlar**, **Microsoft SQL Server 2005**, işaret **yapılandırma araçları**ve ardından **SQL Server Yapılandırma Yöneticisi**.  
  
2.  Sol bölmesinde **SQL Server Configuration Manager**, tıklayın **SQL Server 2005 Services**.  
  
3.  Sağ bölmede, sağ **SQL Server (SQLEXPRESS)** ve ardından **özellikleri**.  
  
4.  Tıklayın **oturum açma** sekme ve nasıl sunucuda oturum çalıştığınız doğrulayın.  
  
     Çoğu durumda **yerel sistem** çalışır.  
  
     Bir değişiklik yaparsanız tıklayın **yeniden** hizmetini yeniden başlatmak için.  
  
### <a name="protocols"></a>Protokolleri  
 Bazen, protokolleri doğru veritabanına erişmek, uygulamanız için ayarlanmamış olabilir. Örneğin, **adlandırılmış kanallar** kılavuzları için gerekli olan protokol [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], varsayılan olarak etkin değildir.  
  
##### <a name="to-enable-the-named-pipes-protocol"></a>Adlandırılmış Kanallar Protokolü etkinleştirmek için  
  
1.  Sol bölmesinde **SQL Server Configuration Manager**, genişletme **SQL Server 2005 ağ yapılandırması**ve ardından **SQLEXPRESS protokolleri**.  
  
2.  Sağ bölmede emin **adlandırılmış kanallar** protokolünün. Yüklü değilse, sağ **Adlandırılmış kanalları** ve ardından **etkinleştirme**.  
  
     Durdurmanız ve hizmeti yeniden başlatmanız gerekir. Sonraki adımları izleyin.  
  
### <a name="stopping-and-restarting-the-service"></a>Durduruluyor ve hizmeti yeniden başlatılıyor  
 Durdur ve değişikliklerinizi gerçekleştirilmeden önce hizmetleri yeniden başlatmanız gerekir.  
  
##### <a name="to-stop-and-restart-the-service"></a>Hizmetini durdurup yeniden başlatmak için  
  
1.  Sol bölmesinde **SQL Server Configuration Manager**, tıklayın **SQL Server 2005 Services**.  
  
2.  Sağ bölmede, sağ **SQL Server (SQLEXPRESS)** ve ardından **Durdur**.  
  
3.  Sağ **SQL Server (SQLEXPRESS)** ve ardından **yeniden**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlarken](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
