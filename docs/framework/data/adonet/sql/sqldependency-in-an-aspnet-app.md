---
title: Bir ASP.NET Uygulamasında SqlDependency
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
ms.openlocfilehash: c49d28f42dec311d4a0c35a7115b00d989411358
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073721"
---
# <a name="sqldependency-in-an-aspnet-application"></a>Bir ASP.NET Uygulamasında SqlDependency
Bu bölümdeki örnek nasıl kullanılacağını gösterir <xref:System.Data.SqlClient.SqlDependency> ASP.NET yararlanarak dolaylı olarak <xref:System.Web.Caching.SqlCacheDependency> nesne. <xref:System.Web.Caching.SqlCacheDependency> Nesnesini kullanan bir <xref:System.Data.SqlClient.SqlDependency> bildirimlerini dinlemek ve doğru şekilde önbelleği güncelleştirmek için.  
  
> [!NOTE]
>  Örnek kod, sorgu bildirimleri betiklerde çalıştırarak etkinleştirdiyseniz varsayar [sorgu bildirimleri etkinleştirme](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md).  
  
## <a name="about-the-sample-application"></a>Örnek uygulama hakkında  
 Örnek uygulama, ürün bilgilerini görüntülemek için tek bir ASP.NET Web sayfası kullanır. **AdventureWorks** SQL Server veritabanında bir <xref:System.Web.UI.WebControls.GridView> denetimi. Sayfa yüklendiğinde geçerli saate kod yazan bir <xref:System.Web.UI.WebControls.Label> denetimi. Ardından tanımlayan bir <xref:System.Web.Caching.SqlCacheDependency> nesne ve özellikleri ayarlar <xref:System.Web.Caching.Cache> üç dakikaya kadar verileri önbelleğe depolamak için nesne. Kod veritabanına bağlanır ve verileri alır. Ne zaman sayfa yüklenen ve ASP.NET uygulamasını çalıştıran sayfasında süresi değişmez'hatalarının ayıklanabileceğini doğrulayabilirsiniz önbellekten veri alır. İzlenen verileri ASP.NET değişip değişmediğini önbellek geçersiz kılar ve derlenmeye `GridView` yeni verilerle görüntülenen saat güncelleştirme denetimi `Label` denetimi.  
  
## <a name="creating-the-sample-application"></a>Örnek uygulamayı oluşturma  
 Oluşturun ve örnek uygulamayı çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yeni bir ASP.NET Web sitesi oluşturun.  
  
2.  Ekleme bir <xref:System.Web.UI.WebControls.Label> ve <xref:System.Web.UI.WebControls.GridView> Default.aspx sayfasında denetimi.  
  
3.  Sayfanın sınıf modülü açın ve aşağıdaki yönergelerini ekleyin:  
  
    ```vb  
    Option Strict On  
    Option Explicit On  
  
    Imports System.Data.SqlClient  
    ```  
  
    ```csharp  
    using System.Data.SqlClient;  
    using System.Web.Caching;  
    ```  
  
4.  Sayfanın içinde aşağıdaki kodu ekleyin `Page_Load` olay:  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#1)]
     [!code-vb[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#1)]  
  
5.  İki yardımcı yöntemler ekler `GetConnectionString` ve `GetSQL`. Tanımlanan bağlantı dizesi tümleşik güvenliği kullanır. Kullandığınız hesabın gerekli veritabanı izinleri olduğunu doğrulamak ihtiyacınız olacak örnek veritabanını **AdventureWorks**, etkin bildirim yok.
  
     [!code-csharp[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#2)]
     [!code-vb[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#2)]  
  
### <a name="testing-the-application"></a>Uygulamayı Test Etme  
 Uygulama Web formunda görüntülenen verileri önbelleğe alır ve hiçbir etkinlik yoksa, üç dakikada bir yenilenir. Önbellek veritabanına bir değişiklik meydana gelirse, hemen yenilenir. Sayfa tarayıcıya yükleyen Visual Studio'da uygulamayı çalıştırın. Ne zaman önbelleğe son yenilenme görüntülenen önbellek yenileme zamanı gösterir. Üç dakika bekleyin ve ardından geri gönderme bir olayın meydana gelmesine neden bu sayfayı yenileyin. Sayfada görüntülenen zaman değiştirildiğine dikkat edin. Üç dakikadan daha kısa bir süre içinde sayfayı yenileyin, sayfada görüntülenen zaman aynı kalır.  
  
 Artık bir Transact-SQL güncelleştirme komut kullanarak veritabanındaki verileri güncelleştirme ve sayfayı yenileyin. Görüntülenen zamanı artık önbellek veritabanından yeni verileri yenilenme gösterir. Önbellek güncelleştirilir olsa da, geri gönderme olayı gerçekleşinceye kadar sayfada görüntülenen zaman değiştirmez unutmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server'da Sorgu Bildirimleri](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
