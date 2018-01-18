---
title: "Öğrenme tarafından izlenecek yollar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8ae2965-6a49-4155-89b0-7fab2c488ab1
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 56852fece0ca1f2dbb70b1bb29c09205b97faf56
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="learning-by-walkthroughs"></a>Öğrenme tarafından izlenecek yollar
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Belgeleri, birkaç izlenecek yollar sağlar. Bu konuda (sorun giderme dahil) bazı genel izlenecek sorunları giderir ve hakkında bilgi almak için birkaç adım talimatlara bağlantılar sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
> [!NOTE]
>  İzlenecek yollar bu Başlarken bölümünde destekleyen temel koda kullanıma [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] teknolojisi. Gerçek bir uygulamada genellikle kullanacağınız [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] ve uygulamak için Windows Forms projeleri, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uygulamalar. [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] Belgeler, bu amaca yönelik örnekler ve izlenecek yollar sağlar.  
  
## <a name="getting-started-walkthroughs"></a>Başlarken izlenecek yollar  
 Bu bölümde, birkaç izlenecek yollar kullanılabilir. Bu izlenecek örnek Northwind veritabanına bağlı ve sunmak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] en düşük karmaşıklık ile size bir hızda özellikleri.  
  
 Tipik ilerlemeyi izlemek için aşağıdaki gibi olur:  
  
|Hedefi|Visual Basic|C#|  
|---------------|------------------|---------|  
|Bir varlık sınıfı oluşturmak ve basit bir sorgu çalıştırın.|[İzlenecek yol: Basit Nesne Modeli ve Sorgu (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md)|[İzlenecek yol: Basit Nesne Modeli ve Sorgu (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md)|  
|İkinci sınıf ekleyin ve daha karmaşık bir sorgu çalıştırın.<br /><br /> (Önceki Kılavuzu tamamlanmasından gerektirir).|[İzlenecek yol: İlişkilerde Sorgulama (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md)|[İzlenecek yol: İlişkilerde Sorgulama (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md)|  
|Ekleyin, değiştirin ve veritabanındaki öğeleri silin.|[İzlenecek yol: Verileri Düzenleme (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)|[İzlenecek yol: Verileri Düzenleme (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)|  
|Saklı yordamları kullanın.|[İzlenecek yol: Yalnızca Saklı Yordamlar Kullanma (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-visual-basic.md)|[İzlenecek yol: Yalnızca Saklı Yordamları Kullanma (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-csharp.md)|  
  
## <a name="general"></a>Genel  
 Aşağıdaki bilgiler Bu talimatlar için genel ilgilidir:  
  
-   Ortam: Her [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] izlenecek kullanan [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] tümleşik geliştirme ortamı (IDE) olarak.  
  
-   SQL motorları: Bu talimatlar SQL Server Express kullanarak uygulanacak yazılır. SQL Server Express yoksa, ücretsiz olarak karşıdan yükleyebilirsiniz. Daha fazla bilgi için bkz: [örnek veritabanları yükleme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
    > [!NOTE]
    >  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]izlenecek yollar bir bağlantı dizesi olarak bir dosya adı kullanın. Yalnızca bir dosya adı belirterek olduğu kolaylık sağlamak amacıyla, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL Server Express kullanıcıları için sağlar. Her zaman güvenlik sorunları dikkat edin. Daha fazla bilgi için bkz: [LINQ-SQL güvenlik](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md).  
  
-   [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]izlenecek yollar genellikle Northwind örnek veritabanı gerektirir. Daha fazla bilgi için bkz: [örnek veritabanları yükleme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
-   İletişim kutuları ve menü komutlarını izlenecek yollarda gördüğünüz açıklanana Yardım'da, etkin ayarlarınıza bağlı olarak farklı olabilir veya [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] sürümü. Ayarlarınızı değiştirmek için tıklatın. **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
-   Çok katmanlı senaryoları adres izlenecek yollar için bir sunucu geliştirme bilgisayardan ayrı olan bir bilgisayarda bulunması gerekir ve sunucuya erişmek için uygun izinlere sahip olmalıdır.  
  
-   Genellikle Northwind örnek veritabanı siparişleri tabloda temsil eden sınıf adı `[Order]`. Kaçış gereklidir çünkü `Order` bir anahtar sözcüktür [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)].  
  
## <a name="troubleshooting"></a>Sorun giderme  
 Bu izlenecek kullanılan veritabanlarına erişmek için yeterli izinlere sahip olmadığınızdan çalışma zamanı hataları oluşabilir. En yaygın olarak bu sorunları gidermek için aşağıdaki adımları bakın.  
  
### <a name="log-on-issues"></a>Oturum açma sorunları  
 Uygulamanızı kabul etmediği bir veritabanı oturum açma yapmamanız veritabanı erişmeye çalışıyor.  
  
##### <a name="to-verify-or-change-the-database-log-on"></a>Doğrulamak veya değiştirmek için veritabanı oturum açın  
  
1.  Windows **Başlat** menüsündeki **tüm programlar**, **Microsoft SQL Server 2005**, işaret **yapılandırma araçları**ve ardından **SQL Server Configuration Manager**.  
  
2.  Sol bölmesinde **SQL Server Configuration Manager**, tıklatın **SQL Server 2005 Services**.  
  
3.  Sağ bölmede sağ **SQL Server (SQLEXPRESS)**ve ardından **özellikleri**.  
  
4.  Tıklatın **oturum açma** sekmesinde ve sunucuya oturum açmak nasıl çalıştığınız doğrulayın.  
  
     Çoğu durumda, **yerel sistem** çalışır.  
  
     Bir değişiklik yaparsanız, tıklatın **yeniden** hizmetini yeniden başlatmak için.  
  
### <a name="protocols"></a>protokolleri  
 Bazen protokolleri doğru veritabanına erişmek, uygulamanız için ayarlanmamış olabilir. Örneğin, **adlandırılmış kanallar** izlenecek yollarda için gerekli olan protokol [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], varsayılan olarak etkin değildir.  
  
##### <a name="to-enable-the-named-pipes-protocol"></a>Adlandırılmış Kanallar Protokolü etkinleştirmek için  
  
1.  Sol bölmesinde **SQL Server Configuration Manager**, genişletin **SQL Server 2005 ağ yapılandırması**ve ardından **SQLEXPRESS protokolleri**.  
  
2.  Sağ bölmede olduğundan emin olun **adlandırılmış kanallar** Protokolü etkindir. Değilse, sağ **adı kanallar** ve ardından **etkinleştirmek**.  
  
     Hizmetini durdurun ve başlatın gerekecektir. Sonraki bloğu içindeki adımları izleyin.  
  
### <a name="stopping-and-restarting-the-service"></a>Hizmetini durdurup yeniden başlatarak  
 Durdurun ve değişikliklerinizi etkili olması hizmetlerini yeniden başlatın.  
  
##### <a name="to-stop-and-restart-the-service"></a>Hizmetini durdurup yeniden başlatmak için  
  
1.  Sol bölmesinde **SQL Server Configuration Manager**, tıklatın **SQL Server 2005 Services**.  
  
2.  Sağ bölmede sağ **SQL Server (SQLEXPRESS)**ve ardından **durdurmak**.  
  
3.  Sağ **SQL Server (SQLEXPRESS)**ve ardından **yeniden**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlarken](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
