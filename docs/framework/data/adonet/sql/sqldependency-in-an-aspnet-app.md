---
title: Bir ASP.NET Uygulamasında SqlDependency
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
ms.openlocfilehash: 2ec9415f63151443d5008fbce471fabeb89cdb91
ms.sourcegitcommit: 1e8382d0ce8b5515864f8fbb178b9fd692a7503f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89656177"
---
# <a name="sqldependency-in-an-aspnet-application"></a>Bir ASP.NET Uygulamasında SqlDependency
Bu bölümdeki örnek, <xref:System.Data.SqlClient.SqlDependency> ASP.net nesnesinden yararlanarak dolaylı olarak nasıl kullanılacağını gösterir <xref:System.Web.Caching.SqlCacheDependency> . <xref:System.Web.Caching.SqlCacheDependency>Nesnesi <xref:System.Data.SqlClient.SqlDependency> bildirimleri dinlemek ve önbelleği doğru şekilde güncelleştirmek için bir kullanır.  
  
> [!NOTE]
> Örnek kod, [sorgu bildirimlerini etkinleştirme](enabling-query-notifications.md)bölümünde betikleri yürüterek sorgu bildirimlerini etkinleştirdiğinizi varsayar.  
  
## <a name="about-the-sample-application"></a>Örnek uygulama hakkında  
 Örnek uygulama, bir denetimdeki **AdventureWorks** SQL Server veritabanından ürün bilgilerini göstermek için tek bir ASP.NET Web sayfası kullanır <xref:System.Web.UI.WebControls.GridView> . Sayfa yüklendiğinde, kod geçerli saati bir <xref:System.Web.UI.WebControls.Label> denetime yazar. Daha sonra bir <xref:System.Web.Caching.SqlCacheDependency> nesnesi tanımlar ve nesne üzerindeki özellikleri <xref:System.Web.Caching.Cache> , en fazla üç dakikalık önbellek verilerini depolayacak şekilde ayarlar. Kod daha sonra veritabanına bağlanır ve verileri alır. Sayfa yüklendiğinde ve uygulama çalışırken ASP.NET, sayfadaki sürenin değişmediğinden emin olarak doğrulayabilmeniz için önbellekteki verileri alır. İzlenen veriler değişirse, ASP.NET önbelleği geçersiz kılar ve denetimi `GridView` yeni verilerle yeniden, denetimde görüntülenen zamanı güncelleyen şekilde yeniden doldurmak `Label` .  
  
## <a name="creating-the-sample-application"></a>Örnek uygulama oluşturma  
 Örnek uygulamayı oluşturmak ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. Yeni bir ASP.NET Web sitesi oluşturun.  
  
2. <xref:System.Web.UI.WebControls.Label> <xref:System.Web.UI.WebControls.GridView> Default. aspx sayfasına bir ve denetimi ekleyin.  
  
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
  
5. Ve olmak üzere iki yardımcı yöntem ekleyin `GetConnectionString` `GetSQL` . Tanımlanan bağlantı dizesi tümleşik güvenlik kullanır. Kullandığınız hesabın gerekli veritabanı izinlerine sahip olduğunu ve örnek veritabanının ( **AdventureWorks**), bildirimlerin etkin olduğunu doğrulamanız gerekir.
  
     [!code-csharp[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#2)]
     [!code-vb[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#2)]  
  
### <a name="testing-the-application"></a>Uygulamayı Test Etme  
 Uygulama, Web formunda görünen verileri önbelleğe alır ve etkinlik yoksa her üç dakikada bir yenilenir. Veritabanında bir değişiklik olursa, önbellek hemen yenilenir. Visual Studio 'dan, sayfayı tarayıcıya yükleyen uygulamayı çalıştırın. Görünen önbellek yenileme zamanı, önbelleğin en son ne zaman yenileneceğini gösterir. Üç dakika bekleyin ve ardından sayfayı yenileyerek geri gönderme olayının oluşmasına neden olur. Sayfada görüntülenen saatin değiştiğini unutmayın. Sayfayı üçten az dakikadan kısa bir süre içinde yenilerseniz sayfada görüntülenecek zaman aynı kalır.  
  
 Şimdi Transact-SQL UPDATE komutunu kullanarak veritabanındaki verileri güncelleştirin ve sayfayı yenileyin. Görüntülenen süre, önbelleğin veritabanındaki yeni verilerle yenilendiğini gösterir. Önbellek güncelleştirildiğinden, geri gönderme olayı gerçekleşene kadar sayfada görüntülenen sürenin değişmediğini unutmayın.  

## <a name="distributed-cache-synchronization-using-sql-dependency"></a>SQL bağımlılığı kullanılarak dağıtılmış önbellek eşitlemesi

[NCache](https://www.alachisoft.com/ncache) gibi bazı üçüncü taraf dağıtılmış önbellekler SQL [bağımlılığını](https://www.alachisoft.com/resources/docs/ncache/prog-guide/sql-dependency.html)kullanarak SQL veritabanını ve önbelleğini eşitlemeye yönelik destek sağlar. Daha fazla bilgi ve örnek kaynak kodu uygulama için bkz. [Dağıtılmış önbellek SQL bağımlılığı örneği](https://github.com/Alachisoft/NCache-Samples/tree/master/dotnet/Dependencies/SQLDependency).

## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server'da Sorgu Bildirimleri](query-notifications-in-sql-server.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
