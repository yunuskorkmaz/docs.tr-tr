---
title: Örnek Veritabanları (LINQ to DataSet) indirme
ms.date: 03/30/2017
ms.assetid: eb42a7af-d410-4b7f-b4a8-13c72ce6fd09
ms.openlocfilehash: 1ef5a5ceac6a7f819551f6221b63197786ab4f09
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61606903"
---
# <a name="downloading-sample-databases-linq-to-dataset"></a><span data-ttu-id="dd577-102">Örnek Veritabanları (LINQ to DataSet) indirme</span><span class="sxs-lookup"><span data-stu-id="dd577-102">Downloading Sample Databases (LINQ to DataSet)</span></span>
<span data-ttu-id="dd577-103">Örnekler ve izlenecek yollarında [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] belgeleri AdventureWorks örnek veritabanını kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd577-103">The samples and walkthroughs in the [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] documentation use the AdventureWorks sample database.</span></span> <span data-ttu-id="dd577-104">Bu ürün ücretsiz olarak Microsoft Yükleme sitesinden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd577-104">You can download this product free of charge from the Microsoft download site.</span></span> <span data-ttu-id="dd577-105">Örnekler ve izlenecek yollarında [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] belgeleri, SQL Server veri deposu olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd577-105">The samples and walkthroughs in the [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] documentation use SQL Server as the data store.</span></span> <span data-ttu-id="dd577-106">SQL Server Express ücret kullanılabilir Edition, SQL Server yerine veri deposu olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dd577-106">SQL Server Express Edition, which is available without charge, can also be used as the data store instead of SQL Server.</span></span>  
  
## <a name="downloading-and-installing-the-adventureworks-database"></a><span data-ttu-id="dd577-107">İndirme ve AdventureWorks veritabanını yükleme</span><span class="sxs-lookup"><span data-stu-id="dd577-107">Downloading and Installing the AdventureWorks Database</span></span>  
  
#### <a name="to-download-and-install-the-adventureworks-sample-database-for-sql-server"></a><span data-ttu-id="dd577-108">İndirmek ve AdventureWorks örnek veritabanı için SQL Server yüklemek için</span><span class="sxs-lookup"><span data-stu-id="dd577-108">To download and install the AdventureWorks sample database for SQL Server</span></span>  
  
1. <span data-ttu-id="dd577-109">Internet Explorer’ı açın.</span><span class="sxs-lookup"><span data-stu-id="dd577-109">Open Internet Explorer.</span></span>  
  
2. <span data-ttu-id="dd577-110">Git [SQL Server 2005 örnekleri ve örnek veritabanları](https://go.microsoft.com/fwlink/?linkid=31046) Web sitesi.</span><span class="sxs-lookup"><span data-stu-id="dd577-110">Go to the [SQL Server 2005 Samples and Sample Databases](https://go.microsoft.com/fwlink/?linkid=31046) Web site.</span></span>  
  
3. <span data-ttu-id="dd577-111">AdventureWorks örnek veritabanını (örneğin, AdventureWorksDB.msi) işlemci türünüz için yükleme yönergelerini izleyin ve kaydedin. MSI dosyası yerel bilgisayarınıza.</span><span class="sxs-lookup"><span data-stu-id="dd577-111">Follow the instructions for downloading the AdventureWorks sample database for your processor type (such as AdventureWorksDB.msi), and save the .MSI file to your local computer.</span></span>  
  
4. <span data-ttu-id="dd577-112">Karşıdan yükleme ya da SQL Server Kurulumu sırasında yüklenen AdventureWorks önceki bir sürümü varsa, AdventureWorks.msi çalıştırmadan önce kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="dd577-112">If you have a previous version of AdventureWorks installed from the download or during the SQL Server setup, you must remove it before running AdventureWorks.msi.</span></span>  
  
#### <a name="to-remove-a-previous-download-of-an-adventureworks-sample-database"></a><span data-ttu-id="dd577-113">AdventureWorks örnek veritabanı önceki bir yükleme kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="dd577-113">To remove a previous download of an AdventureWorks sample database</span></span>  
  
1. <span data-ttu-id="dd577-114">AdventureWorks veya AdventureWorksDW veritabanını bırakın.</span><span class="sxs-lookup"><span data-stu-id="dd577-114">Drop the AdventureWorks or AdventureWorksDW database.</span></span>  
  
2. <span data-ttu-id="dd577-115">Gelen **Program Ekle veya Kaldır**seçin **AdventureWorksDB** veya **AdventureWorksBI** tıklatıp **Kaldır**.</span><span class="sxs-lookup"><span data-stu-id="dd577-115">From **Add or Remove Programs**, select **AdventureWorksDB** or **AdventureWorksBI** and click **Remove**.</span></span>  
  
#### <a name="to-remove-an-adventureworks-sample-database-previously-installed-using-setup"></a><span data-ttu-id="dd577-116">Kurulum'u kullanarak daha önce yüklenmiş bir AdventureWorks örnek veritabanını kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="dd577-116">To remove an AdventureWorks sample database previously installed using Setup</span></span>  
  
1. <span data-ttu-id="dd577-117">AdventureWorks veya AdventureWorksDW veritabanını bırakın.</span><span class="sxs-lookup"><span data-stu-id="dd577-117">Drop the AdventureWorks or AdventureWorksDW database.</span></span>  
  
2. <span data-ttu-id="dd577-118">Gelen **Program Ekle veya Kaldır**seçin **Microsoft SQL Server 2005** tıklatıp **değişiklik**.</span><span class="sxs-lookup"><span data-stu-id="dd577-118">From **Add or Remove Programs**, select **Microsoft SQL Server 2005** and click **Change**.</span></span>  
  
3. <span data-ttu-id="dd577-119">Gelen **Bileşen Seçimi**seçin **iş istasyonu bileşenleri** ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="dd577-119">From **Component Selection**, select **Workstation Components** and then click **Next**.</span></span>  
  
4. <span data-ttu-id="dd577-120">Gelen **SQL Server yükleme Sihirbazına Hoş Geldiniz**, tıklayın **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="dd577-120">From **Welcome to the SQL Server Installation Wizard**, click **Next**.</span></span>  
  
5. <span data-ttu-id="dd577-121">Gelen **sistem yapılandırma denetimi**, tıklayın **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="dd577-121">From **System Configuration Check**, click **Next**.</span></span>  
  
6. <span data-ttu-id="dd577-122">Gelen **değiştirme veya kaldırma örneği**, tıklayın **değişiklik bileşenlerin yüklü**.</span><span class="sxs-lookup"><span data-stu-id="dd577-122">From **Change or Remove Instance**, click **Change Installed Components**.</span></span>  
  
7. <span data-ttu-id="dd577-123">Gelen **özellik seçimi**, genişletme **belgeler, örnekler ve örnek veritabanları** düğümü.</span><span class="sxs-lookup"><span data-stu-id="dd577-123">From **Feature Selection**, expand the **Documentation, Samples, and Sample Databases** node.</span></span>  
  
8. <span data-ttu-id="dd577-124">Seçin **örnek kod ve uygulamaları**.</span><span class="sxs-lookup"><span data-stu-id="dd577-124">Select **Sample Code and Applications**.</span></span> <span data-ttu-id="dd577-125">Genişletin **örnek veritabanları**, kaldırılacak ve örnek veritabanını seçmeniz **tüm özellik kullanılamaz**.</span><span class="sxs-lookup"><span data-stu-id="dd577-125">Expand **Sample Databases**, select the sample database to be removed, and select **Entire feature will be unavailable**.</span></span> <span data-ttu-id="dd577-126">**İleri**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="dd577-126">Click **Next**.</span></span>  
  
9. <span data-ttu-id="dd577-127">Tıklayın **yükleme** ve Yükleme Sihirbazı'nı tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="dd577-127">Click **Install** and finish the installation wizard.</span></span>  
  
#### <a name="to-attach-the-adventureworks-sample-database-files-to-an-instance-of-sql-server"></a><span data-ttu-id="dd577-128">SQL Server örneğine AdventureWorks örnek veritabanı dosyalarını eklemek için</span><span class="sxs-lookup"><span data-stu-id="dd577-128">To attach the AdventureWorks sample database files to an instance of SQL Server</span></span>  
  
1. <span data-ttu-id="dd577-129">Örnek veritabanı yükleyici dosyası indirilmeden sonra çift **AdventureWorksDB.msi** dosya (veya indirdiğiniz dosyanın) veritabanını yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="dd577-129">After the file sample database installer file has downloaded, double-click the **AdventureWorksDB.msi** file (or the file you downloaded) to install the database.</span></span> <span data-ttu-id="dd577-130">Varsayılan olarak, c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data veritabanı yüklenir.</span><span class="sxs-lookup"><span data-stu-id="dd577-130">By default, the database is installed at c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data.</span></span>  
  
2. <span data-ttu-id="dd577-131">AdventureWorks veritabanı dosyaları, SQL Server örneğine SQLCMD veya SQL Server Management Studio aşağıdaki betiği çalıştırarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="dd577-131">Attach the AdventureWorks database files to an instance of SQL Server by executing the following script SQLCMD or SQL Server Management Studio:</span></span>  
  
    ```sql
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     <span data-ttu-id="dd577-132">Bu dosyalar farklı bir sürücü veya dizin yüklediyseniz, yürütmeden önce yolların uygun şekilde düzeltmeniz gerekir `sp_attach_db` saklı yordamı.</span><span class="sxs-lookup"><span data-stu-id="dd577-132">If you have installed these files to a different drive or directory, you must revise the paths appropriately before you execute the `sp_attach_db` stored procedure.</span></span>  
  
## <a name="downloading-sql-server-express-edition"></a><span data-ttu-id="dd577-133">SQL Server Express sürümü indiriliyor</span><span class="sxs-lookup"><span data-stu-id="dd577-133">Downloading SQL Server Express Edition</span></span>  
 <span data-ttu-id="dd577-134">Örnekler ve izlenecek yollarında [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] bölümü SQL Server 2005 veri deposu olarak kullanabilirsiniz, ancak SQL Server Express Edition kullanmayı değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="dd577-134">The samples and walkthroughs in the [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] section use SQL Server 2005 as the data store but can be modified to use SQL Server Express Edition, instead.</span></span> <span data-ttu-id="dd577-135">SQL Server Express Edition ücretsiz kullanılabilir ve uygulamaları yeniden dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd577-135">SQL Server Express Edition is available without charge, and you can redistribute it with applications.</span></span> <span data-ttu-id="dd577-136">Visual Studio kullanıyorsanız, SQL Server Express Edition Pro ve üzeri sürümlerinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="dd577-136">If you are using Visual Studio, SQL Server Express Edition is included in the Pro and higher editions.</span></span>  
  
#### <a name="to-download-and-install-sql-server-express-edition"></a><span data-ttu-id="dd577-137">SQL Server Express Edition'ı indirip</span><span class="sxs-lookup"><span data-stu-id="dd577-137">To download and install SQL Server Express Edition</span></span>  
  
1. <span data-ttu-id="dd577-138">Start Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="dd577-138">Start Internet Explorer.</span></span>  
  
2. <span data-ttu-id="dd577-139">Git [Microsoft SQL Server 2005 Express Edition](https://go.microsoft.com/fwlink/?LinkID=31070) indirme sayfası.</span><span class="sxs-lookup"><span data-stu-id="dd577-139">Go to the  [Microsoft SQL Server 2005 Express Edition](https://go.microsoft.com/fwlink/?LinkID=31070) download page.</span></span>  
  
3. <span data-ttu-id="dd577-140">Web sitesi yükleme yönergelerini izleyin.</span><span class="sxs-lookup"><span data-stu-id="dd577-140">Follow the installation instructions on the Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd577-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd577-141">See also</span></span>

- [<span data-ttu-id="dd577-142">Başlarken</span><span class="sxs-lookup"><span data-stu-id="dd577-142">Getting Started</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)
