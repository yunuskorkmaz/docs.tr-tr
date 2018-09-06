---
title: Bir ASP.NET uygulamasında SqlDependency
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
ms.openlocfilehash: 5465238e4b9deaa13c76cb35122fcaded7acd7f7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43736665"
---
# <a name="sqldependency-in-an-aspnet-application"></a><span data-ttu-id="0f39b-102">Bir ASP.NET uygulamasında SqlDependency</span><span class="sxs-lookup"><span data-stu-id="0f39b-102">SqlDependency in an ASP.NET Application</span></span>
<span data-ttu-id="0f39b-103">Bu bölümdeki örnek nasıl kullanılacağını gösterir <xref:System.Data.SqlClient.SqlDependency> ASP.NET yararlanarak dolaylı olarak <xref:System.Web.Caching.SqlCacheDependency> nesne.</span><span class="sxs-lookup"><span data-stu-id="0f39b-103">The example in this section shows how to use <xref:System.Data.SqlClient.SqlDependency> indirectly by leveraging the ASP.NET <xref:System.Web.Caching.SqlCacheDependency> object.</span></span> <span data-ttu-id="0f39b-104"><xref:System.Web.Caching.SqlCacheDependency> Nesnesini kullanan bir <xref:System.Data.SqlClient.SqlDependency> bildirimlerini dinlemek ve doğru şekilde önbelleği güncelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="0f39b-104">The <xref:System.Web.Caching.SqlCacheDependency> object uses a <xref:System.Data.SqlClient.SqlDependency> to listen for notifications and correctly update the cache.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0f39b-105">Örnek kod, sorgu bildirimleri betiklerde çalıştırarak etkinleştirdiyseniz varsayar [sorgu bildirimleri etkinleştirme](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md).</span><span class="sxs-lookup"><span data-stu-id="0f39b-105">The sample code assumes that you have enabled query notifications by executing the scripts in [Enabling Query Notifications](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md).</span></span>  
  
## <a name="about-the-sample-application"></a><span data-ttu-id="0f39b-106">Örnek uygulama hakkında</span><span class="sxs-lookup"><span data-stu-id="0f39b-106">About the Sample Application</span></span>  
 <span data-ttu-id="0f39b-107">Örnek uygulama, ürün bilgilerini görüntülemek için tek bir ASP.NET Web sayfası kullanır. **AdventureWorks** SQL Server veritabanında bir <xref:System.Web.UI.WebControls.GridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="0f39b-107">The sample application uses a single ASP.NET Web page to display product information from the **AdventureWorks** SQL Server database in a <xref:System.Web.UI.WebControls.GridView> control.</span></span> <span data-ttu-id="0f39b-108">Sayfa yüklendiğinde geçerli saate kod yazan bir <xref:System.Web.UI.WebControls.Label> denetimi.</span><span class="sxs-lookup"><span data-stu-id="0f39b-108">When the page loads, the code writes the current time to a <xref:System.Web.UI.WebControls.Label> control.</span></span> <span data-ttu-id="0f39b-109">Ardından tanımlayan bir <xref:System.Web.Caching.SqlCacheDependency> nesne ve özellikleri ayarlar <xref:System.Web.Caching.Cache> üç dakikaya kadar verileri önbelleğe depolamak için nesne.</span><span class="sxs-lookup"><span data-stu-id="0f39b-109">It then defines a <xref:System.Web.Caching.SqlCacheDependency> object and sets properties on the <xref:System.Web.Caching.Cache> object to store the cache data for up to three minutes.</span></span> <span data-ttu-id="0f39b-110">Kod veritabanına bağlanır ve verileri alır.</span><span class="sxs-lookup"><span data-stu-id="0f39b-110">The code then connects to the database and retrieves the data.</span></span> <span data-ttu-id="0f39b-111">Ne zaman sayfa yüklenen ve ASP.NET uygulamasını çalıştıran sayfasında süresi değişmez'hatalarının ayıklanabileceğini doğrulayabilirsiniz önbellekten veri alır.</span><span class="sxs-lookup"><span data-stu-id="0f39b-111">When the page is loaded and the application is running ASP.NET will retrieve data from the cache, which you can verify by noting that the time on the page does not change.</span></span> <span data-ttu-id="0f39b-112">İzlenen verileri ASP.NET değişip değişmediğini önbellek geçersiz kılar ve derlenmeye `GridView` yeni verilerle görüntülenen saat güncelleştirme denetimi `Label` denetimi.</span><span class="sxs-lookup"><span data-stu-id="0f39b-112">If the data being monitored changes, ASP.NET invalidates the cache and repopulate the `GridView` control with fresh data, updating the time displayed in the `Label` control.</span></span>  
  
## <a name="creating-the-sample-application"></a><span data-ttu-id="0f39b-113">Örnek uygulamayı oluşturma</span><span class="sxs-lookup"><span data-stu-id="0f39b-113">Creating the Sample Application</span></span>  
 <span data-ttu-id="0f39b-114">Oluşturun ve örnek uygulamayı çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="0f39b-114">Follow these steps to create and run the sample application:</span></span>  
  
1.  <span data-ttu-id="0f39b-115">Yeni bir ASP.NET Web sitesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0f39b-115">Create a new ASP.NET Web site.</span></span>  
  
2.  <span data-ttu-id="0f39b-116">Ekleme bir <xref:System.Web.UI.WebControls.Label> ve <xref:System.Web.UI.WebControls.GridView> Default.aspx sayfasında denetimi.</span><span class="sxs-lookup"><span data-stu-id="0f39b-116">Add a <xref:System.Web.UI.WebControls.Label> and a <xref:System.Web.UI.WebControls.GridView> control to the Default.aspx page.</span></span>  
  
3.  <span data-ttu-id="0f39b-117">Sayfanın sınıf modülü açın ve aşağıdaki yönergelerini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0f39b-117">Open the page's class module and add the following directives:</span></span>  
  
    ```vb  
    Option Strict On  
    Option Explicit On  
  
    Imports System.Data.SqlClient  
    ```  
  
    ```csharp  
    using System.Data.SqlClient;  
    using System.Web.Caching;  
    ```  
  
4.  <span data-ttu-id="0f39b-118">Sayfanın içinde aşağıdaki kodu ekleyin `Page_Load` olay:</span><span class="sxs-lookup"><span data-stu-id="0f39b-118">Add the following code in the page's `Page_Load` event:</span></span>  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#1)]
     [!code-vb[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#1)]  
  
5.  <span data-ttu-id="0f39b-119">İki yardımcı yöntemler ekler `GetConnectionString` ve `GetSQL`.</span><span class="sxs-lookup"><span data-stu-id="0f39b-119">Add two helper methods, `GetConnectionString` and `GetSQL`.</span></span> <span data-ttu-id="0f39b-120">Tanımlanan bağlantı dizesi tümleşik güvenliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="0f39b-120">The connection string defined uses integrated security.</span></span> <span data-ttu-id="0f39b-121">Kullandığınız hesabın gerekli veritabanı izinleri olduğunu doğrulamak ihtiyacınız olacak örnek veritabanını **AdventureWorks**, etkin bildirim yok.</span><span class="sxs-lookup"><span data-stu-id="0f39b-121">You will need to verify that the account you are using has the necessary database permissions and that the sample database, **AdventureWorks**, has notifications enabled.</span></span> <span data-ttu-id="0f39b-122">Daha fazla bilgi için [özel dikkat edilecek noktalar kullanarak sorgu bildirimleri](https://msdn.microsoft.com/library/a83c8dc8-4fb9-4ffd-a2a5-c07cf4a203c7).</span><span class="sxs-lookup"><span data-stu-id="0f39b-122">For more information, see [Special Considerations When Using Query Notifications](https://msdn.microsoft.com/library/a83c8dc8-4fb9-4ffd-a2a5-c07cf4a203c7).</span></span>  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#2)]
     [!code-vb[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#2)]  
  
### <a name="testing-the-application"></a><span data-ttu-id="0f39b-123">Uygulamayı Test Etme</span><span class="sxs-lookup"><span data-stu-id="0f39b-123">Testing the Application</span></span>  
 <span data-ttu-id="0f39b-124">Uygulama Web formunda görüntülenen verileri önbelleğe alır ve hiçbir etkinlik yoksa, üç dakikada bir yenilenir.</span><span class="sxs-lookup"><span data-stu-id="0f39b-124">The application caches the data displayed on the Web form and refreshes it every three minutes if there is no activity.</span></span> <span data-ttu-id="0f39b-125">Önbellek veritabanına bir değişiklik meydana gelirse, hemen yenilenir.</span><span class="sxs-lookup"><span data-stu-id="0f39b-125">If a change occurs to the database, the cache is refreshed immediately.</span></span> <span data-ttu-id="0f39b-126">Sayfa tarayıcıya yükleyen Visual Studio'da uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0f39b-126">Run the application from Visual Studio, which loads the page into the browser.</span></span> <span data-ttu-id="0f39b-127">Ne zaman önbelleğe son yenilenme görüntülenen önbellek yenileme zamanı gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f39b-127">The cache refresh time displayed indicates when the cache was last refreshed.</span></span> <span data-ttu-id="0f39b-128">Üç dakika bekleyin ve ardından geri gönderme bir olayın meydana gelmesine neden bu sayfayı yenileyin.</span><span class="sxs-lookup"><span data-stu-id="0f39b-128">Wait three minutes, and then refresh the page, causing a postback event to occur.</span></span> <span data-ttu-id="0f39b-129">Sayfada görüntülenen zaman değiştirildiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="0f39b-129">Note that the time displayed on the page has changed.</span></span> <span data-ttu-id="0f39b-130">Üç dakikadan daha kısa bir süre içinde sayfayı yenileyin, sayfada görüntülenen zaman aynı kalır.</span><span class="sxs-lookup"><span data-stu-id="0f39b-130">If you refresh the page in less than three minutes, the time displayed on the page will remain the same.</span></span>  
  
 <span data-ttu-id="0f39b-131">Artık bir Transact-SQL güncelleştirme komut kullanarak veritabanındaki verileri güncelleştirme ve sayfayı yenileyin.</span><span class="sxs-lookup"><span data-stu-id="0f39b-131">Now update the data in the database, using a Transact-SQL UPDATE command and refresh the page.</span></span> <span data-ttu-id="0f39b-132">Görüntülenen zamanı artık önbellek veritabanından yeni verileri yenilenme gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f39b-132">The time displayed now indicates that the cache was refreshed with the new data from the database.</span></span> <span data-ttu-id="0f39b-133">Önbellek güncelleştirilir olsa da, geri gönderme olayı gerçekleşinceye kadar sayfada görüntülenen zaman değiştirmez unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0f39b-133">Note that although the cache is updated, the time displayed on the page does not change until a postback event occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f39b-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0f39b-134">See Also</span></span>  
 [<span data-ttu-id="0f39b-135">SQL Server'da Sorgu Bildirimleri</span><span class="sxs-lookup"><span data-stu-id="0f39b-135">Query Notifications in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [<span data-ttu-id="0f39b-136">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="0f39b-136">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
