---
title: Bir ASP.NET Uygulamasında SqlDependency
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
ms.openlocfilehash: f3e28adc2cf7c24cee9ee344eb78404f01b79793
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780724"
---
# <a name="sqldependency-in-an-aspnet-application"></a><span data-ttu-id="420ed-102">Bir ASP.NET Uygulamasında SqlDependency</span><span class="sxs-lookup"><span data-stu-id="420ed-102">SqlDependency in an ASP.NET Application</span></span>
<span data-ttu-id="420ed-103">Bu bölümdeki örnek, ASP.net <xref:System.Data.SqlClient.SqlDependency> <xref:System.Web.Caching.SqlCacheDependency> nesnesinden yararlanarak dolaylı olarak nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="420ed-103">The example in this section shows how to use <xref:System.Data.SqlClient.SqlDependency> indirectly by leveraging the ASP.NET <xref:System.Web.Caching.SqlCacheDependency> object.</span></span> <span data-ttu-id="420ed-104">Nesnesi bildirimleri dinlemek ve <xref:System.Data.SqlClient.SqlDependency> önbelleği doğru şekilde güncelleştirmek için bir kullanır. <xref:System.Web.Caching.SqlCacheDependency></span><span class="sxs-lookup"><span data-stu-id="420ed-104">The <xref:System.Web.Caching.SqlCacheDependency> object uses a <xref:System.Data.SqlClient.SqlDependency> to listen for notifications and correctly update the cache.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="420ed-105">Örnek kod, [sorgu bildirimlerini etkinleştirme](enabling-query-notifications.md)bölümünde betikleri yürüterek sorgu bildirimlerini etkinleştirdiğinizi varsayar.</span><span class="sxs-lookup"><span data-stu-id="420ed-105">The sample code assumes that you have enabled query notifications by executing the scripts in [Enabling Query Notifications](enabling-query-notifications.md).</span></span>  
  
## <a name="about-the-sample-application"></a><span data-ttu-id="420ed-106">Örnek uygulama hakkında</span><span class="sxs-lookup"><span data-stu-id="420ed-106">About the Sample Application</span></span>  
 <span data-ttu-id="420ed-107">Örnek uygulama, bir <xref:System.Web.UI.WebControls.GridView> denetimdeki **AdventureWorks** SQL Server veritabanından ürün bilgilerini göstermek için tek bir ASP.NET Web sayfası kullanır.</span><span class="sxs-lookup"><span data-stu-id="420ed-107">The sample application uses a single ASP.NET Web page to display product information from the **AdventureWorks** SQL Server database in a <xref:System.Web.UI.WebControls.GridView> control.</span></span> <span data-ttu-id="420ed-108">Sayfa yüklendiğinde, kod geçerli saati bir <xref:System.Web.UI.WebControls.Label> denetime yazar.</span><span class="sxs-lookup"><span data-stu-id="420ed-108">When the page loads, the code writes the current time to a <xref:System.Web.UI.WebControls.Label> control.</span></span> <span data-ttu-id="420ed-109">Daha sonra bir <xref:System.Web.Caching.SqlCacheDependency> nesnesi tanımlar ve <xref:System.Web.Caching.Cache> nesne üzerindeki özellikleri, en fazla üç dakikalık önbellek verilerini depolayacak şekilde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="420ed-109">It then defines a <xref:System.Web.Caching.SqlCacheDependency> object and sets properties on the <xref:System.Web.Caching.Cache> object to store the cache data for up to three minutes.</span></span> <span data-ttu-id="420ed-110">Kod daha sonra veritabanına bağlanır ve verileri alır.</span><span class="sxs-lookup"><span data-stu-id="420ed-110">The code then connects to the database and retrieves the data.</span></span> <span data-ttu-id="420ed-111">Sayfa yüklendiğinde ve uygulama çalışırken ASP.NET, sayfadaki sürenin değişmediğinden emin olarak doğrulayabilmeniz için önbellekteki verileri alır.</span><span class="sxs-lookup"><span data-stu-id="420ed-111">When the page is loaded and the application is running ASP.NET will retrieve data from the cache, which you can verify by noting that the time on the page does not change.</span></span> <span data-ttu-id="420ed-112">İzlenen veriler değişirse, ASP.NET önbelleği geçersiz kılar ve denetimi yeni verilerle yeniden, `GridView` `Label` denetimde görüntülenen zamanı güncelleyen şekilde yeniden doldurmak.</span><span class="sxs-lookup"><span data-stu-id="420ed-112">If the data being monitored changes, ASP.NET invalidates the cache and repopulate the `GridView` control with fresh data, updating the time displayed in the `Label` control.</span></span>  
  
## <a name="creating-the-sample-application"></a><span data-ttu-id="420ed-113">Örnek uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="420ed-113">Creating the Sample Application</span></span>  
 <span data-ttu-id="420ed-114">Örnek uygulamayı oluşturmak ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="420ed-114">Follow these steps to create and run the sample application:</span></span>  
  
1. <span data-ttu-id="420ed-115">Yeni bir ASP.NET Web sitesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="420ed-115">Create a new ASP.NET Web site.</span></span>  
  
2. <span data-ttu-id="420ed-116">Default. <xref:System.Web.UI.WebControls.Label> aspx sayfasına <xref:System.Web.UI.WebControls.GridView> bir ve denetimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="420ed-116">Add a <xref:System.Web.UI.WebControls.Label> and a <xref:System.Web.UI.WebControls.GridView> control to the Default.aspx page.</span></span>  
  
3. <span data-ttu-id="420ed-117">Sayfanın sınıf modülünü açın ve aşağıdaki yönergeleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="420ed-117">Open the page's class module and add the following directives:</span></span>  
  
    ```vb  
    Option Strict On  
    Option Explicit On  
  
    Imports System.Data.SqlClient  
    ```  
  
    ```csharp  
    using System.Data.SqlClient;  
    using System.Web.Caching;  
    ```  
  
4. <span data-ttu-id="420ed-118">Aşağıdaki kodu sayfanın `Page_Load` olayına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="420ed-118">Add the following code in the page's `Page_Load` event:</span></span>  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#1)]
     [!code-vb[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#1)]  
  
5. <span data-ttu-id="420ed-119">`GetConnectionString` Ve`GetSQL`olmak üzere iki yardımcı yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="420ed-119">Add two helper methods, `GetConnectionString` and `GetSQL`.</span></span> <span data-ttu-id="420ed-120">Tanımlanan bağlantı dizesi tümleşik güvenlik kullanır.</span><span class="sxs-lookup"><span data-stu-id="420ed-120">The connection string defined uses integrated security.</span></span> <span data-ttu-id="420ed-121">Kullandığınız hesabın gerekli veritabanı izinlerine sahip olduğunu ve örnek veritabanının ( **AdventureWorks**), bildirimlerin etkin olduğunu doğrulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="420ed-121">You will need to verify that the account you are using has the necessary database permissions and that the sample database, **AdventureWorks**, has notifications enabled.</span></span>
  
     [!code-csharp[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#2)]
     [!code-vb[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#2)]  
  
### <a name="testing-the-application"></a><span data-ttu-id="420ed-122">Uygulamayı Test Etme</span><span class="sxs-lookup"><span data-stu-id="420ed-122">Testing the Application</span></span>  
 <span data-ttu-id="420ed-123">Uygulama, Web formunda görünen verileri önbelleğe alır ve etkinlik yoksa her üç dakikada bir yenilenir.</span><span class="sxs-lookup"><span data-stu-id="420ed-123">The application caches the data displayed on the Web form and refreshes it every three minutes if there is no activity.</span></span> <span data-ttu-id="420ed-124">Veritabanında bir değişiklik olursa, önbellek hemen yenilenir.</span><span class="sxs-lookup"><span data-stu-id="420ed-124">If a change occurs to the database, the cache is refreshed immediately.</span></span> <span data-ttu-id="420ed-125">Visual Studio 'dan, sayfayı tarayıcıya yükleyen uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="420ed-125">Run the application from Visual Studio, which loads the page into the browser.</span></span> <span data-ttu-id="420ed-126">Görünen önbellek yenileme zamanı, önbelleğin en son ne zaman yenileneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="420ed-126">The cache refresh time displayed indicates when the cache was last refreshed.</span></span> <span data-ttu-id="420ed-127">Üç dakika bekleyin ve ardından sayfayı yenileyerek geri gönderme olayının oluşmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="420ed-127">Wait three minutes, and then refresh the page, causing a postback event to occur.</span></span> <span data-ttu-id="420ed-128">Sayfada görüntülenen saatin değiştiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="420ed-128">Note that the time displayed on the page has changed.</span></span> <span data-ttu-id="420ed-129">Sayfayı üçten az dakikadan kısa bir süre içinde yenilerseniz sayfada görüntülenecek zaman aynı kalır.</span><span class="sxs-lookup"><span data-stu-id="420ed-129">If you refresh the page in less than three minutes, the time displayed on the page will remain the same.</span></span>  
  
 <span data-ttu-id="420ed-130">Şimdi Transact-SQL UPDATE komutunu kullanarak veritabanındaki verileri güncelleştirin ve sayfayı yenileyin.</span><span class="sxs-lookup"><span data-stu-id="420ed-130">Now update the data in the database, using a Transact-SQL UPDATE command and refresh the page.</span></span> <span data-ttu-id="420ed-131">Görüntülenen süre, önbelleğin veritabanındaki yeni verilerle yenilendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="420ed-131">The time displayed now indicates that the cache was refreshed with the new data from the database.</span></span> <span data-ttu-id="420ed-132">Önbellek güncelleştirildiğinden, geri gönderme olayı gerçekleşene kadar sayfada görüntülenen sürenin değişmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="420ed-132">Note that although the cache is updated, the time displayed on the page does not change until a postback event occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="420ed-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="420ed-133">See also</span></span>

- [<span data-ttu-id="420ed-134">SQL Server'da Sorgu Bildirimleri</span><span class="sxs-lookup"><span data-stu-id="420ed-134">Query Notifications in SQL Server</span></span>](query-notifications-in-sql-server.md)
- [<span data-ttu-id="420ed-135">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="420ed-135">ADO.NET Overview</span></span>](../ado-net-overview.md)
