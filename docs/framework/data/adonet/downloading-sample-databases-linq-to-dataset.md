---
title: Örnek veritabanları indiriliyor (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: eb42a7af-d410-4b7f-b4a8-13c72ce6fd09
ms.openlocfilehash: c67ee699cf594f476a728c7345b47b0c32dea7ff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795170"
---
# <a name="downloading-sample-databases-linq-to-dataset"></a><span data-ttu-id="0b174-102">Örnek veritabanları indiriliyor (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="0b174-102">Downloading Sample Databases (LINQ to DataSet)</span></span>
<span data-ttu-id="0b174-103">LINQ to DataSet belgelerindeki örnekler ve izlenecek yollar AdventureWorks örnek veritabanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="0b174-103">The samples and walkthroughs in the LINQ to DataSet documentation use the AdventureWorks sample database.</span></span> <span data-ttu-id="0b174-104">Bu ürünü Microsoft Download sitesinden ücretsiz olarak indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b174-104">You can download this product free of charge from the Microsoft download site.</span></span> <span data-ttu-id="0b174-105">LINQ to DataSet belgelerindeki örnekler ve izlenecek yollar veri deposu olarak SQL Server kullanır.</span><span class="sxs-lookup"><span data-stu-id="0b174-105">The samples and walkthroughs in the LINQ to DataSet documentation use SQL Server as the data store.</span></span> <span data-ttu-id="0b174-106">Ücret ödemeden kullanılabilen SQL Server Express sürümü, SQL Server yerine veri deposu olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0b174-106">SQL Server Express Edition, which is available without charge, can also be used as the data store instead of SQL Server.</span></span>  
  
## <a name="downloading-and-installing-the-adventureworks-database"></a><span data-ttu-id="0b174-107">AdventureWorks veritabanını indirme ve yükleme</span><span class="sxs-lookup"><span data-stu-id="0b174-107">Downloading and Installing the AdventureWorks Database</span></span>  
  
#### <a name="to-download-and-install-the-adventureworks-sample-database-for-sql-server"></a><span data-ttu-id="0b174-108">SQL Server için AdventureWorks örnek veritabanını indirmek ve yüklemek için</span><span class="sxs-lookup"><span data-stu-id="0b174-108">To download and install the AdventureWorks sample database for SQL Server</span></span>  
  
1. <span data-ttu-id="0b174-109">Internet Explorer’ı açın.</span><span class="sxs-lookup"><span data-stu-id="0b174-109">Open Internet Explorer.</span></span>  
  
2. <span data-ttu-id="0b174-110">[SQL Server 2005 örnekleri ve örnek veritabanları](https://go.microsoft.com/fwlink/?linkid=31046) Web sitesine gidin.</span><span class="sxs-lookup"><span data-stu-id="0b174-110">Go to the [SQL Server 2005 Samples and Sample Databases](https://go.microsoft.com/fwlink/?linkid=31046) Web site.</span></span>  
  
3. <span data-ttu-id="0b174-111">İşlemci türü (örneğin, AdventureWorksDB. msi) için AdventureWorks örnek veritabanını indirme yönergelerini izleyin ve öğesini kaydedin. MSI dosyasını yerel bilgisayarınıza.</span><span class="sxs-lookup"><span data-stu-id="0b174-111">Follow the instructions for downloading the AdventureWorks sample database for your processor type (such as AdventureWorksDB.msi), and save the .MSI file to your local computer.</span></span>  
  
4. <span data-ttu-id="0b174-112">İndirmenin veya SQL Server Kurulum sırasında yüklü olan bir önceki AdventureWorks sürümüne sahipseniz, AdventureWorks. msi ' yi çalıştırmadan önce bu sürümü kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0b174-112">If you have a previous version of AdventureWorks installed from the download or during the SQL Server setup, you must remove it before running AdventureWorks.msi.</span></span>  
  
#### <a name="to-remove-a-previous-download-of-an-adventureworks-sample-database"></a><span data-ttu-id="0b174-113">AdventureWorks örnek veritabanının önceki bir indirmeyi kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="0b174-113">To remove a previous download of an AdventureWorks sample database</span></span>  
  
1. <span data-ttu-id="0b174-114">AdventureWorks veya AdventureWorksDW veritabanını bırakın.</span><span class="sxs-lookup"><span data-stu-id="0b174-114">Drop the AdventureWorks or AdventureWorksDW database.</span></span>  
  
2. <span data-ttu-id="0b174-115">**Program Ekle veya Kaldır**' dan **AdventureWorksDB** veya **AdventureWorksBI** ' yi seçin ve **Kaldır**' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="0b174-115">From **Add or Remove Programs**, select **AdventureWorksDB** or **AdventureWorksBI** and click **Remove**.</span></span>  
  
#### <a name="to-remove-an-adventureworks-sample-database-previously-installed-using-setup"></a><span data-ttu-id="0b174-116">Daha önce kurulum kullanılarak yüklenen bir AdventureWorks örnek veritabanını kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="0b174-116">To remove an AdventureWorks sample database previously installed using Setup</span></span>  
  
1. <span data-ttu-id="0b174-117">AdventureWorks veya AdventureWorksDW veritabanını bırakın.</span><span class="sxs-lookup"><span data-stu-id="0b174-117">Drop the AdventureWorks or AdventureWorksDW database.</span></span>  
  
2. <span data-ttu-id="0b174-118">**Program Ekle veya Kaldır**' dan **Microsoft SQL Server 2005** ' i seçin ve **Değiştir**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0b174-118">From **Add or Remove Programs**, select **Microsoft SQL Server 2005** and click **Change**.</span></span>  
  
3. <span data-ttu-id="0b174-119">**Bileşen seçimi**' nden **iş istasyonu bileşenleri** ' ni seçin ve **İleri**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0b174-119">From **Component Selection**, select **Workstation Components** and then click **Next**.</span></span>  
  
4. <span data-ttu-id="0b174-120">**SQL Server yükleme sihirbazına hoş geldiniz ' e**tıklayarak **İleri**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0b174-120">From **Welcome to the SQL Server Installation Wizard**, click **Next**.</span></span>  
  
5. <span data-ttu-id="0b174-121">**Sistem yapılandırması denetiminden** **İleri**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0b174-121">From **System Configuration Check**, click **Next**.</span></span>  
  
6. <span data-ttu-id="0b174-122">**Değişiklik veya kaldırma örneğinden**, **yüklü bileşenleri Değiştir**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0b174-122">From **Change or Remove Instance**, click **Change Installed Components**.</span></span>  
  
7. <span data-ttu-id="0b174-123">**Özellik seçimi**' nden **belge, örnekler ve örnek veritabanları** düğümünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="0b174-123">From **Feature Selection**, expand the **Documentation, Samples, and Sample Databases** node.</span></span>  
  
8. <span data-ttu-id="0b174-124">**Örnek kod ve uygulamalar ' ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="0b174-124">Select **Sample Code and Applications**.</span></span> <span data-ttu-id="0b174-125">**Örnek veritabanları**' nı genişletin, kaldırılacak örnek veritabanını seçin ve **Tüm özelliğin devre dışı olacağını**seçin.</span><span class="sxs-lookup"><span data-stu-id="0b174-125">Expand **Sample Databases**, select the sample database to be removed, and select **Entire feature will be unavailable**.</span></span> <span data-ttu-id="0b174-126">**İleri**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0b174-126">Click **Next**.</span></span>  
  
9. <span data-ttu-id="0b174-127">Yükleme **' ye** tıklayın ve yükleme sihirbazını sona erdirin.</span><span class="sxs-lookup"><span data-stu-id="0b174-127">Click **Install** and finish the installation wizard.</span></span>  
  
#### <a name="to-attach-the-adventureworks-sample-database-files-to-an-instance-of-sql-server"></a><span data-ttu-id="0b174-128">AdventureWorks örnek veritabanı dosyalarını bir SQL Server örneğine eklemek için</span><span class="sxs-lookup"><span data-stu-id="0b174-128">To attach the AdventureWorks sample database files to an instance of SQL Server</span></span>  
  
1. <span data-ttu-id="0b174-129">Dosya örnek veritabanı yükleyicisi dosyası indirildikten sonra, veritabanını yüklemek için **AdventureWorksDB. msi** dosyasını (veya indirdiğiniz dosyayı) çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="0b174-129">After the file sample database installer file has downloaded, double-click the **AdventureWorksDB.msi** file (or the file you downloaded) to install the database.</span></span> <span data-ttu-id="0b174-130">Varsayılan olarak, veritabanı c:\Program Files\Microsoft SQL Server\mssql. 1\Mssql\datakonumuna yüklenir.</span><span class="sxs-lookup"><span data-stu-id="0b174-130">By default, the database is installed at c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data.</span></span>  
  
2. <span data-ttu-id="0b174-131">Aşağıdaki betik SQLCMD veya SQL Server Management Studio yürüterek AdventureWorks veritabanı dosyalarını bir SQL Server örneğine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0b174-131">Attach the AdventureWorks database files to an instance of SQL Server by executing the following script SQLCMD or SQL Server Management Studio:</span></span>  
  
    ```sql
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     <span data-ttu-id="0b174-132">Bu dosyaları farklı bir sürücüye veya dizine yüklediyseniz, `sp_attach_db` saklı yordamı yürütmeden önce yolları uygun şekilde düzeltmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0b174-132">If you have installed these files to a different drive or directory, you must revise the paths appropriately before you execute the `sp_attach_db` stored procedure.</span></span>  
  
## <a name="downloading-sql-server-express-edition"></a><span data-ttu-id="0b174-133">SQL Server Express Edition indiriliyor</span><span class="sxs-lookup"><span data-stu-id="0b174-133">Downloading SQL Server Express Edition</span></span>  
 <span data-ttu-id="0b174-134">LINQ to DataSet bölümündeki örnekler ve izlenecek yollar veri deposu olarak SQL Server 2005 kullanır, ancak bunun yerine SQL Server Express Edition kullanacak şekilde değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="0b174-134">The samples and walkthroughs in the LINQ to DataSet section use SQL Server 2005 as the data store but can be modified to use SQL Server Express Edition, instead.</span></span> <span data-ttu-id="0b174-135">SQL Server Express sürüm ücretsiz olarak kullanılabilir ve uygulamalar ile yeniden dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b174-135">SQL Server Express Edition is available without charge, and you can redistribute it with applications.</span></span> <span data-ttu-id="0b174-136">Visual Studio kullanıyorsanız, Pro ve üzeri sürümlerde SQL Server Express Edition bulunur.</span><span class="sxs-lookup"><span data-stu-id="0b174-136">If you are using Visual Studio, SQL Server Express Edition is included in the Pro and higher editions.</span></span>  
  
#### <a name="to-download-and-install-sql-server-express-edition"></a><span data-ttu-id="0b174-137">SQL Server Express sürümünü indirmek ve yüklemek için</span><span class="sxs-lookup"><span data-stu-id="0b174-137">To download and install SQL Server Express Edition</span></span>  
  
1. <span data-ttu-id="0b174-138">Internet Explorer 'ı başlatın.</span><span class="sxs-lookup"><span data-stu-id="0b174-138">Start Internet Explorer.</span></span>  
  
2. <span data-ttu-id="0b174-139">[Microsoft SQL Server 2005 Express Edition](https://go.microsoft.com/fwlink/?LinkID=31070) indirme sayfasına gidin.</span><span class="sxs-lookup"><span data-stu-id="0b174-139">Go to the  [Microsoft SQL Server 2005 Express Edition](https://go.microsoft.com/fwlink/?LinkID=31070) download page.</span></span>  
  
3. <span data-ttu-id="0b174-140">Web sitesindeki yükleme yönergelerini izleyin.</span><span class="sxs-lookup"><span data-stu-id="0b174-140">Follow the installation instructions on the Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b174-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b174-141">See also</span></span>

- [<span data-ttu-id="0b174-142">Başlarken</span><span class="sxs-lookup"><span data-stu-id="0b174-142">Getting Started</span></span>](getting-started-linq-to-dataset.md)
