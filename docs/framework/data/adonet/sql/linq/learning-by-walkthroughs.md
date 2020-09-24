---
title: İzlenecek Yollarla Öğrenme
ms.date: 03/30/2017
ms.assetid: a8ae2965-6a49-4155-89b0-7fab2c488ab1
ms.openlocfilehash: f3d313fd50108420b631cff783708191f97a8b04
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158246"
---
# <a name="learning-by-walkthroughs"></a>İzlenecek Yollarla Öğrenme

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Belgeler birkaç izlenecek yol sağlar. Bu konu başlığı altında, bazı genel izlenecek yol sorunları ele alınmaktadır (sorun giderme dahil) ve hakkında bilgi almak için çeşitli giriş düzeyi talimatlarına bağlantılar sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .  
  
> [!NOTE]
> Bu Başlarken bölümündeki izlenecek yollar sizi teknolojiyi destekleyen temel kodu kullanıma sunar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . Gerçek uygulamada, uygulamalarınızı uygulamak için genellikle Nesne İlişkisel Tasarımcısı ve Windows Forms projelerini kullanacaksınız [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . O/R Designer belgeleri, bu amaçla örnekler ve izlenecek yollar sağlar.  
  
## <a name="getting-started-walkthroughs"></a>Başlarken Izlenecek yollar  

 Bu bölümde birkaç izlenecek yol bulunmaktadır. Bu izlenecek yollar, örnek Northwind veritabanına dayalıdır ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] en az karmaşıklıklarla genlik hızda özellikler sunar.  
  
 İzlenecek tipik ilerleme aşağıdaki gibidir:  
  
|Amaç|Visual Basic|C#|  
|---------------|------------------|---------|  
|Bir varlık sınıfı oluşturun ve basit bir sorgu yürütün.|[İzlenecek yol: Basit Nesne Modeli ve Sorgu (Visual Basic)](walkthrough-simple-object-model-and-query-visual-basic.md)|[İzlenecek yol: Basit Nesne Modeli ve Sorgu (C#)](walkthrough-simple-object-model-and-query-csharp.md)|  
|İkinci bir sınıf ekleyin ve daha karmaşık bir sorgu yürütün.<br /><br /> (Önceki izlenecek yolun tamamlanmasını gerektirir).|[İzlenecek yol: İlişkilerde Sorgulama (Visual Basic)](walkthrough-querying-across-relationships-visual-basic.md)|[İzlenecek yol: İlişkilerde Sorgulama (C#)](walkthrough-querying-across-relationships-csharp.md)|  
|Veritabanına öğe ekleyin, değiştirin ve silin.|[İzlenecek yol: Verileri Düzenleme (Visual Basic)](walkthrough-manipulating-data-visual-basic.md)|[İzlenecek yol: Verileri Düzenleme (C#)](walkthrough-manipulating-data-csharp.md)|  
|Saklı yordamları kullanın.|[İzlenecek yol: Yalnızca Saklı Yordamlar Kullanma (Visual Basic)](walkthrough-using-only-stored-procedures-visual-basic.md)|[İzlenecek yol: Yalnızca Saklı Yordamları Kullanma (C#)](walkthrough-using-only-stored-procedures-csharp.md)|  
  
## <a name="general"></a>Genel  

 Aşağıdaki bilgiler genel olarak bu talimatlara aittir:  
  
- Ortam: her bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] anlatım tümleşik geliştirme ortamı (IDE) olarak Visual Studio 'yu kullanır.  
  
- SQL motorları: Bu izlenecek yollar, SQL Server Express kullanılarak uygulanacak şekilde yazılmıştır. SQL Server Express yoksa ücretsiz olarak indirebilirsiniz. Daha fazla bilgi için bkz. [örnek veritabanlarını indirme](downloading-sample-databases.md).  
  
    > [!NOTE]
    > [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] izlenecek yollar bir dosya adını bağlantı dizesi olarak kullanır. Yalnızca bir dosya adı belirtmenin [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL Server Express kullanıcılara sağladığı bir kolaylık vardır. Her zaman güvenlik sorunlarına dikkat edin. Daha fazla bilgi için bkz. [LINQ to SQL güvenlik](security-in-linq-to-sql.md).  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] izlenecek yollar genellikle Northwind örnek veritabanı gerektirir. Daha fazla bilgi için bkz. [örnek veritabanlarını indirme](downloading-sample-databases.md).  
  
- İzlenecek yollarda gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza veya Visual Studio sürümüne bağlı olarak yardım bölümünde açıklananlardan farklılık gösterebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' na tıklayın. Daha fazla bilgi için bkz. [Visual STUDIO IDE 'Yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
- Çok katmanlı senaryolara yönelik olan yönergeler için, bir sunucunun geliştirme bilgisayarından farklı bir bilgisayarda bulunması ve sunucuya erişmek için uygun izinlere sahip olmanız gerekir.  
  
- Genellikle Northwind örnek veritabanındaki Orders tablosunu temsil eden sınıfın adı `[Order]` . Kaçış gereklidir çünkü `Order` Visual Basic bir anahtar sözcük.  
  
## <a name="troubleshooting"></a>Sorun giderme  

 Çalışma zamanı hataları oluşabilir çünkü bu izlenecek yollarda kullanılan veritabanlarına erişmek için yeterli izinlere sahip değilsiniz. Bu sorunların en yaygın olarak giderilmesine yardımcı olması için aşağıdaki adımlara bakın.  
  
### <a name="log-on-issues"></a>Oturum açma sorunları  

 Uygulamanız, kabul edilemez bir veritabanı oturum açma yöntemiyle veritabanına erişmeye çalışıyor olabilir.  
  
##### <a name="to-verify-or-change-the-database-log-on"></a>Veritabanı oturumunu doğrulamak veya değiştirmek için  
  
1. Windows **Başlat** menüsünde **tüm programlar**' ın üzerine gelin, **Microsoft SQL Server 2005**, **yapılandırma araçları**üzerine gelin ve **SQL Server Yapılandırma Yöneticisi**' ye tıklayın.  
  
2. **SQL Server Yapılandırma Yöneticisi**sol bölmesinde **SQL Server 2005 Hizmetleri**' ne tıklayın.  
  
3. Sağ bölmede **SQL Server (SQLEXPRESS)** öğesine sağ tıklayın ve ardından **Özellikler**' e tıklayın.  
  
4. **Oturum açma** sekmesine tıklayın ve sunucuda nasıl oturum açmaya çalışırken emin olun.  
  
     Çoğu durumda, **yerel sistem** çalışmaktadır.  
  
     Bir değişiklik yaparsanız, hizmeti yeniden başlatmak için **Yeniden Başlat** ' a tıklayın.  
  
### <a name="protocols"></a>Protokoller  

 Bazen, uygulamanızın veritabanına erişmesi için protokoller doğru ayarlanmamış olabilir. Örneğin, içinde izlenecek yollar için gerekli olan **adlandırılmış kanallar** Protokolü [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , varsayılan olarak etkin değildir.  
  
##### <a name="to-enable-the-named-pipes-protocol"></a>Adlandırılmış kanallar protokolünü etkinleştirmek için  
  
1. **SQL Server Yapılandırma Yöneticisi**sol bölmesinde, **SQL Server 2005 ağ yapılandırması**' nı genişletin ve ardından **SQLExpress protokolleri**' ne tıklayın.  
  
2. Sağ bölmede, **adlandırılmış kanallar** protokolünün etkinleştirildiğinden emin olun. Değilse, **ad kanalları** ' na sağ tıklayın ve ardından **Etkinleştir**' e tıklayın.  
  
     Hizmeti durdurup yeniden başlatmanız gerekir. Sonraki bloktaki adımları izleyin.  
  
### <a name="stopping-and-restarting-the-service"></a>Hizmeti durdurma ve yeniden başlatma  

 Değişikliklerinizin etkili olabilmesi için hizmetleri durdurup yeniden başlatmanız gerekir.  
  
##### <a name="to-stop-and-restart-the-service"></a>Hizmeti durdurmak ve yeniden başlatmak için  
  
1. **SQL Server Yapılandırma Yöneticisi**sol bölmesinde **SQL Server 2005 Hizmetleri**' ne tıklayın.  
  
2. Sağ bölmede **SQL Server (SQLEXPRESS)** öğesine sağ tıklayın ve ardından **Durdur**' a tıklayın.  
  
3. **SQL Server (SQLEXPRESS)** öğesine sağ tıklayın ve ardından **Yeniden Başlat**' a tıklayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken](getting-started.md)
