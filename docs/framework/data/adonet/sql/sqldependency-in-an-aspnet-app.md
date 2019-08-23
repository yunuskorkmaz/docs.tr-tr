---
title: Bir ASP.NET Uygulamasında SqlDependency
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
ms.openlocfilehash: a93cb9da44985fa29a4975875564b384117ce76f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938463"
---
# <a name="sqldependency-in-an-aspnet-application"></a>Bir ASP.NET Uygulamasında SqlDependency
Bu bölümdeki örnek, ASP.net <xref:System.Data.SqlClient.SqlDependency> <xref:System.Web.Caching.SqlCacheDependency> nesnesinden yararlanarak dolaylı olarak nasıl kullanılacağını gösterir. Nesnesi bildirimleri dinlemek ve <xref:System.Data.SqlClient.SqlDependency> önbelleği doğru şekilde güncelleştirmek için bir kullanır. <xref:System.Web.Caching.SqlCacheDependency>  
  
> [!NOTE]
> Örnek kod, [sorgu bildirimlerini etkinleştirme](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md)bölümünde betikleri yürüterek sorgu bildirimlerini etkinleştirdiğinizi varsayar.  
  
## <a name="about-the-sample-application"></a>Örnek uygulama hakkında  
 Örnek uygulama, bir <xref:System.Web.UI.WebControls.GridView> denetimdeki **AdventureWorks** SQL Server veritabanından ürün bilgilerini göstermek için tek bir ASP.NET Web sayfası kullanır. Sayfa yüklendiğinde, kod geçerli saati bir <xref:System.Web.UI.WebControls.Label> denetime yazar. Daha sonra bir <xref:System.Web.Caching.SqlCacheDependency> nesnesi tanımlar ve <xref:System.Web.Caching.Cache> nesne üzerindeki özellikleri, en fazla üç dakikalık önbellek verilerini depolayacak şekilde ayarlar. Kod daha sonra veritabanına bağlanır ve verileri alır. Sayfa yüklendiğinde ve uygulama çalışırken ASP.NET, sayfadaki sürenin değişmediğinden emin olarak doğrulayabilmeniz için önbellekteki verileri alır. İzlenen veriler değişirse, ASP.NET önbelleği geçersiz kılar ve denetimi yeni verilerle yeniden, `GridView` `Label` denetimde görüntülenen zamanı güncelleyen şekilde yeniden doldurmak.  
  
## <a name="creating-the-sample-application"></a>Örnek uygulama oluşturma  
 Örnek uygulamayı oluşturmak ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. Yeni bir ASP.NET Web sitesi oluşturun.  
  
2. Default. <xref:System.Web.UI.WebControls.Label> aspx sayfasına <xref:System.Web.UI.WebControls.GridView> bir ve denetimi ekleyin.  
  
3. Sayfanın sınıf modülünü açın ve aşağıdaki yönergeleri ekleyin:  
  
    ```vb  
    Option Strict On  
    Option Explicit On  
  
    Imports System.Data.SqlClient  
    ```  
  
    ```csharp  
    using System.Data.SqlClient;  
    using System.Web.Caching;  
    ```  
  
4. Aşağıdaki kodu sayfanın `Page_Load` olayına ekleyin:  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#1)]
     [!code-vb[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#1)]  
  
5. `GetConnectionString` Ve`GetSQL`olmak üzere iki yardımcı yöntem ekleyin. Tanımlanan bağlantı dizesi tümleşik güvenlik kullanır. Kullandığınız hesabın gerekli veritabanı izinlerine sahip olduğunu ve örnek veritabanının ( **AdventureWorks**), bildirimlerin etkin olduğunu doğrulamanız gerekir.
  
     [!code-csharp[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#2)]
     [!code-vb[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#2)]  
  
### <a name="testing-the-application"></a>Uygulamayı Test Etme  
 Uygulama, Web formunda görünen verileri önbelleğe alır ve etkinlik yoksa her üç dakikada bir yenilenir. Veritabanında bir değişiklik olursa, önbellek hemen yenilenir. Visual Studio 'dan, sayfayı tarayıcıya yükleyen uygulamayı çalıştırın. Görünen önbellek yenileme zamanı, önbelleğin en son ne zaman yenileneceğini gösterir. Üç dakika bekleyin ve ardından sayfayı yenileyerek geri gönderme olayının oluşmasına neden olur. Sayfada görüntülenen saatin değiştiğini unutmayın. Sayfayı üçten az dakikadan kısa bir süre içinde yenilerseniz sayfada görüntülenecek zaman aynı kalır.  
  
 Şimdi Transact-SQL UPDATE komutunu kullanarak veritabanındaki verileri güncelleştirin ve sayfayı yenileyin. Görüntülenen süre, önbelleğin veritabanındaki yeni verilerle yenilendiğini gösterir. Önbellek güncelleştirildiğinden, geri gönderme olayı gerçekleşene kadar sayfada görüntülenen sürenin değişmediğini unutmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server'da Sorgu Bildirimleri](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
