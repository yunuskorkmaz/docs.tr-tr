---
title: Örnek Veritabanları (LINQ-DataSet) yükleniyor
ms.date: 03/30/2017
ms.assetid: eb42a7af-d410-4b7f-b4a8-13c72ce6fd09
ms.openlocfilehash: f2488b0e1bfc578679a2a2802c332439f374a341
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32763059"
---
# <a name="downloading-sample-databases-linq-to-dataset"></a><span data-ttu-id="30988-102">Örnek Veritabanları (LINQ-DataSet) yükleniyor</span><span class="sxs-lookup"><span data-stu-id="30988-102">Downloading Sample Databases (LINQ to DataSet)</span></span>
<span data-ttu-id="30988-103">Örnekler ve izlenecek yollarda [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] belgeleri AdventureWorks örnek veritabanını kullanın.</span><span class="sxs-lookup"><span data-stu-id="30988-103">The samples and walkthroughs in the [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] documentation use the AdventureWorks sample database.</span></span> <span data-ttu-id="30988-104">Bu ürün ücretsiz Microsoft sitesinden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30988-104">You can download this product free of charge from the Microsoft download site.</span></span> <span data-ttu-id="30988-105">Örnekler ve izlenecek yollarda [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] belgeleri SQL Server veri deposu olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="30988-105">The samples and walkthroughs in the [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] documentation use SQL Server as the data store.</span></span> <span data-ttu-id="30988-106">SQL Server Express ücretsiz kullanılabilir olan Edition yerine SQL Server veri deposu olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="30988-106">SQL Server Express Edition, which is available without charge, can also be used as the data store instead of SQL Server.</span></span>  
  
## <a name="downloading-and-installing-the-adventureworks-database"></a><span data-ttu-id="30988-107">İndirme ve AdventureWorks veritabanını yükleme</span><span class="sxs-lookup"><span data-stu-id="30988-107">Downloading and Installing the AdventureWorks Database</span></span>  
  
#### <a name="to-download-and-install-the-adventureworks-sample-database-for-sql-server"></a><span data-ttu-id="30988-108">İndirmek ve SQL Server için AdventureWorks örnek veritabanını yüklemek için</span><span class="sxs-lookup"><span data-stu-id="30988-108">To download and install the AdventureWorks sample database for SQL Server</span></span>  
  
1.  <span data-ttu-id="30988-109">Internet Explorer’ı açın.</span><span class="sxs-lookup"><span data-stu-id="30988-109">Open Internet Explorer.</span></span>  
  
2.  <span data-ttu-id="30988-110">Git [SQL Server 2005 örnekler ve örnek veritabanları](http://go.microsoft.com/fwlink/?linkid=31046) Web sitesi.</span><span class="sxs-lookup"><span data-stu-id="30988-110">Go to the [SQL Server 2005 Samples and Sample Databases](http://go.microsoft.com/fwlink/?linkid=31046) Web site.</span></span>  
  
3.  <span data-ttu-id="30988-111">AdventureWorks örnek veritabanı, işlemci türü (örneğin, AdventureWorksDB.msi) için karşıdan yüklemek için yönergeleri izleyin ve kaydedin. MSI dosyası yerel bilgisayarınızda.</span><span class="sxs-lookup"><span data-stu-id="30988-111">Follow the instructions for downloading the AdventureWorks sample database for your processor type (such as AdventureWorksDB.msi), and save the .MSI file to your local computer.</span></span>  
  
4.  <span data-ttu-id="30988-112">Karşıdan yükleme veya SQL Server Kurulumu sırasında yüklenen AdventureWorks önceki bir sürümü varsa, AdventureWorks.msi çalıştırmadan önce kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="30988-112">If you have a previous version of AdventureWorks installed from the download or during the SQL Server setup, you must remove it before running AdventureWorks.msi.</span></span>  
  
#### <a name="to-remove-a-previous-download-of-an-adventureworks-sample-database"></a><span data-ttu-id="30988-113">Önceki bir yükleme AdventureWorks örnek veritabanını kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="30988-113">To remove a previous download of an AdventureWorks sample database</span></span>  
  
1.  <span data-ttu-id="30988-114">AdventureWorks veya AdventureWorksDW veritabanını bırakın.</span><span class="sxs-lookup"><span data-stu-id="30988-114">Drop the AdventureWorks or AdventureWorksDW database.</span></span>  
  
2.  <span data-ttu-id="30988-115">Gelen **Program Ekle veya Kaldır**seçin **AdventureWorksDB** veya **AdventureWorksBI** tıklatıp **kaldırmak**.</span><span class="sxs-lookup"><span data-stu-id="30988-115">From **Add or Remove Programs**, select **AdventureWorksDB** or **AdventureWorksBI** and click **Remove**.</span></span>  
  
#### <a name="to-remove-an-adventureworks-sample-database-previously-installed-using-setup"></a><span data-ttu-id="30988-116">Kurulum'u kullanarak daha önce yüklenmiş bir AdventureWorks örnek veritabanını kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="30988-116">To remove an AdventureWorks sample database previously installed using Setup</span></span>  
  
1.  <span data-ttu-id="30988-117">AdventureWorks veya AdventureWorksDW veritabanını bırakın.</span><span class="sxs-lookup"><span data-stu-id="30988-117">Drop the AdventureWorks or AdventureWorksDW database.</span></span>  
  
2.  <span data-ttu-id="30988-118">Gelen **Program Ekle veya Kaldır**seçin **Microsoft SQL Server 2005** tıklatıp **değişiklik**.</span><span class="sxs-lookup"><span data-stu-id="30988-118">From **Add or Remove Programs**, select **Microsoft SQL Server 2005** and click **Change**.</span></span>  
  
3.  <span data-ttu-id="30988-119">Gelen **Bileşen Seçimi**seçin **iş istasyonu bileşenleri** ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="30988-119">From **Component Selection**, select **Workstation Components** and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="30988-120">Gelen **SQL Server yükleme Sihirbazına Hoş Geldiniz**, tıklatın **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="30988-120">From **Welcome to the SQL Server Installation Wizard**, click **Next**.</span></span>  
  
5.  <span data-ttu-id="30988-121">Gelen **sistem yapılandırma denetimi**, tıklatın **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="30988-121">From **System Configuration Check**, click **Next**.</span></span>  
  
6.  <span data-ttu-id="30988-122">Gelen **Değiştir veya Kaldır örnek**, tıklatın **değişiklik bileşenlerinin yüklü**.</span><span class="sxs-lookup"><span data-stu-id="30988-122">From **Change or Remove Instance**, click **Change Installed Components**.</span></span>  
  
7.  <span data-ttu-id="30988-123">Gelen **özellik seçimi**, genişletin **belgeler, örnekler ve örnek veritabanları** düğümü.</span><span class="sxs-lookup"><span data-stu-id="30988-123">From **Feature Selection**, expand the **Documentation, Samples, and Sample Databases** node.</span></span>  
  
8.  <span data-ttu-id="30988-124">Seçin **örnek kod ve uygulamaları**.</span><span class="sxs-lookup"><span data-stu-id="30988-124">Select **Sample Code and Applications**.</span></span> <span data-ttu-id="30988-125">Genişletme **örnek veritabanları**, kaldırılması ve seçmek için örnek veritabanını seçin **tüm özelliği kullanılamaz**.</span><span class="sxs-lookup"><span data-stu-id="30988-125">Expand **Sample Databases**, select the sample database to be removed, and select **Entire feature will be unavailable**.</span></span> <span data-ttu-id="30988-126">**İleri**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="30988-126">Click **Next**.</span></span>  
  
9. <span data-ttu-id="30988-127">Tıklatın **yükleme** ve Yükleme Sihirbazı'nı tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="30988-127">Click **Install** and finish the installation wizard.</span></span>  
  
#### <a name="to-attach-the-adventureworks-sample-database-files-to-an-instance-of-sql-server"></a><span data-ttu-id="30988-128">SQL Server örneğine AdventureWorks örnek veritabanı dosyalarını eklemek için</span><span class="sxs-lookup"><span data-stu-id="30988-128">To attach the AdventureWorks sample database files to an instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="30988-129">Örnek veritabanı yükleyici dosyası indirilmeden sonra çift tıklayarak **AdventureWorksDB.msi** dosyası (veya indirdiğiniz dosyası) veritabanını yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="30988-129">After the file sample database installer file has downloaded, double-click the **AdventureWorksDB.msi** file (or the file you downloaded) to install the database.</span></span> <span data-ttu-id="30988-130">Varsayılan olarak, veritabanı c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data sırasında yüklenir.</span><span class="sxs-lookup"><span data-stu-id="30988-130">By default, the database is installed at c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data.</span></span>  
  
2.  <span data-ttu-id="30988-131">AdventureWorks veritabanı dosyaları, aşağıdaki komut dosyası SQLCMD veya SQL Server Management Studio yürüterek SQL Server örneğine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="30988-131">Attach the AdventureWorks database files to an instance of SQL Server by executing the following script SQLCMD or SQL Server Management Studio:</span></span>  
  
    ```  
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     <span data-ttu-id="30988-132">Bu dosyalar farklı bir sürücü veya dizin yüklediyseniz, çalıştırmadan önce yolları uygun şekilde düzeltmeniz gerekir `sp_attach_db` saklı yordamı.</span><span class="sxs-lookup"><span data-stu-id="30988-132">If you have installed these files to a different drive or directory, you must revise the paths appropriately before you execute the `sp_attach_db` stored procedure.</span></span>  
  
## <a name="downloading-sql-server-express-edition"></a><span data-ttu-id="30988-133">SQL Server Express sürümü indirme</span><span class="sxs-lookup"><span data-stu-id="30988-133">Downloading SQL Server Express Edition</span></span>  
 <span data-ttu-id="30988-134">Örnekler ve izlenecek yollarda [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] bölüm veri deposu olarak SQL Server 2005 kullanır ancak SQL Server Express Edition kullanmayı değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="30988-134">The samples and walkthroughs in the [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] section use SQL Server 2005 as the data store but can be modified to use SQL Server Express Edition, instead.</span></span> <span data-ttu-id="30988-135">SQL Server Express Edition ücretsiz kullanılabilir ve uygulamalarla yeniden dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30988-135">SQL Server Express Edition is available without charge, and you can redistribute it with applications.</span></span> <span data-ttu-id="30988-136">Visual Studio kullanıyorsanız, SQL Server Express Edition Pro ve sonraki sürümlerinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="30988-136">If you are using Visual Studio, SQL Server Express Edition is included in the Pro and higher editions.</span></span>  
  
#### <a name="to-download-and-install-sql-server-express-edition"></a><span data-ttu-id="30988-137">SQL Server Express sürümünü karşıdan yükleyip</span><span class="sxs-lookup"><span data-stu-id="30988-137">To download and install SQL Server Express Edition</span></span>  
  
1.  <span data-ttu-id="30988-138">Internet Explorer'ı başlatın.</span><span class="sxs-lookup"><span data-stu-id="30988-138">Start Internet Explorer.</span></span>  
  
2.  <span data-ttu-id="30988-139">Git [Microsoft SQL Server 2005 Express Edition](http://go.microsoft.com/fwlink/?LinkID=31070) sayfa indirin.</span><span class="sxs-lookup"><span data-stu-id="30988-139">Go to the  [Microsoft SQL Server 2005 Express Edition](http://go.microsoft.com/fwlink/?LinkID=31070) download page.</span></span>  
  
3.  <span data-ttu-id="30988-140">Web sitesindeki yükleme yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="30988-140">Follow the installation instructions on the Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30988-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="30988-141">See Also</span></span>  
 [<span data-ttu-id="30988-142">Başlarken</span><span class="sxs-lookup"><span data-stu-id="30988-142">Getting Started</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)
