---
title: ADO.NET kod örnekleri için örnek SQL Server veritabanlarını edinin
description: ADO.NET belgelerinde kod örneklerinde kullanılan örnek SQL Server veritabanlarının yanı sıra SQL Server ve yönetim araçlarını indirin
ms.date: 01/11/2019
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 19d659cbe8f39d27b71dc59c738355f12fce92a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148393"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a><span data-ttu-id="87684-103">kod örnekleri ADO.NET için örnek veritabanlarını edinin</span><span class="sxs-lookup"><span data-stu-id="87684-103">Get the sample databases for ADO.NET code samples</span></span>

<span data-ttu-id="87684-104">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Belgelerdeki bir dizi örnek ve gözden geçirme de örnek SQL Server veritabanları nı ve SQL Server Express'i kullanır.</span><span class="sxs-lookup"><span data-stu-id="87684-104">A number of examples and walkthroughs in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation use sample SQL Server databases and SQL Server Express.</span></span> <span data-ttu-id="87684-105">Bu ürünleri Microsoft'tan ücretsiz olarak indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87684-105">You can download these products free of charge from Microsoft.</span></span>

## <a name="get-the-northwind-sample-database-for-sql-server"></a><span data-ttu-id="87684-106">SQL Server için Northwind örnek veritabanını edinin</span><span class="sxs-lookup"><span data-stu-id="87684-106">Get the Northwind sample database for SQL Server</span></span>

<span data-ttu-id="87684-107">SQL Server `instnwnd.sql` için Northwind örnek veritabanını oluşturmak ve yüklemek için komut dosyasını aşağıdaki GitHub deposundan indirin:</span><span class="sxs-lookup"><span data-stu-id="87684-107">Download the script `instnwnd.sql` from the following GitHub repository to create and load the Northwind sample database for SQL Server:</span></span>

[<span data-ttu-id="87684-108">Northwind ve pubörnekleri Microsoft SQL Server için örnek veritabanları</span><span class="sxs-lookup"><span data-stu-id="87684-108">Northwind and pubs sample databases for Microsoft SQL Server</span></span>](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

<span data-ttu-id="87684-109">Northwind veritabanını kullanabilmek için, SQL Server `instnwnd.sql` [Management Studio](#get_ssms) veya benzer bir aracı kullanarak veritabanını SQL Server'ın bir örneğinde yeniden oluşturmak için indirilen komut dosyası dosyasını çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="87684-109">Before you can use the Northwind database, you have to run the downloaded `instnwnd.sql` script file to recreate the database on an instance of SQL Server by using [SQL Server Management Studio](#get_ssms) or a similar tool.</span></span> <span data-ttu-id="87684-110">Depodaki Readme dosyasındaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="87684-110">Follow the instructions in the Readme file in the repository.</span></span>

> [!TIP]
> <span data-ttu-id="87684-111">Microsoft Access için Northwind veritabanını arıyorsanız, [Bkz. Microsoft Access için Northwind örnek veritabanını yükleyin.](#northwind_access)</span><span class="sxs-lookup"><span data-stu-id="87684-111">If you're looking for the Northwind database for Microsoft Access, see [Install the Northwind sample database for Microsoft Access](#northwind_access).</span></span>

## <a name="get-the-northwind-sample-database-for-microsoft-access"></a><a name="northwind_access"></a><span data-ttu-id="87684-112">Microsoft Access için Northwind örnek veritabanını edinin</span><span class="sxs-lookup"><span data-stu-id="87684-112">Get the Northwind sample database for Microsoft Access</span></span>

<span data-ttu-id="87684-113">Microsoft Access için Northwind örnek veritabanı Microsoft İndirme Merkezi'nde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="87684-113">The Northwind sample database for Microsoft Access is not available on the Microsoft Download Center.</span></span> <span data-ttu-id="87684-114">Northwind'i doğrudan Access içinden yüklemek için aşağıdaki leri yapın:</span><span class="sxs-lookup"><span data-stu-id="87684-114">To install Northwind directly from within Access, do the following things:</span></span>

1. <span data-ttu-id="87684-115">Erişimi Aç.</span><span class="sxs-lookup"><span data-stu-id="87684-115">Open Access.</span></span>

1. <span data-ttu-id="87684-116">**Çevrimiçi Şablonları Ara** kutusuna **Northwind'i** girin ve ardından **Enter'u**seçin.</span><span class="sxs-lookup"><span data-stu-id="87684-116">Enter **Northwind** in the **Search for Online Templates** box, and then select **Enter**.</span></span>

1. <span data-ttu-id="87684-117">Sonuçlar ekranında **Northwind'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="87684-117">On the results screen, select **Northwind**.</span></span> <span data-ttu-id="87684-118">Northwind veritabanının açıklamasıyla birlikte yeni bir pencere açılır.</span><span class="sxs-lookup"><span data-stu-id="87684-118">A new window opens with a description of the Northwind database.</span></span>

1. <span data-ttu-id="87684-119">Yeni pencerede, **Dosya Adı** metin kutusunda, Northwind veritabanı kopyanız için bir dosya adı sağlayın.</span><span class="sxs-lookup"><span data-stu-id="87684-119">In the new window, in the **File Name** text box, provide a filename for your copy of the Northwind database.</span></span>

1. <span data-ttu-id="87684-120">**Oluştur'u**seçin.</span><span class="sxs-lookup"><span data-stu-id="87684-120">Select **Create**.</span></span> <span data-ttu-id="87684-121">Access Northwind veritabanını karşıdan yükler ve dosyayı hazırlar.</span><span class="sxs-lookup"><span data-stu-id="87684-121">Access downloads the Northwind database and prepares the file.</span></span>

1. <span data-ttu-id="87684-122">Bu işlem tamamlandığında, veritabanı karşılama ekranıyla açılır.</span><span class="sxs-lookup"><span data-stu-id="87684-122">When this process is complete, the database opens with a Welcome screen.</span></span>

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a><span data-ttu-id="87684-123">SQL Server için AdventureWorks örnek veritabanını edinin</span><span class="sxs-lookup"><span data-stu-id="87684-123">Get the AdventureWorks sample database for SQL Server</span></span>

<span data-ttu-id="87684-124">SQL Server için AdventureWorks örnek veritabanını aşağıdaki GitHub deposundan indirin:</span><span class="sxs-lookup"><span data-stu-id="87684-124">Download the AdventureWorks sample database for SQL Server from the following GitHub repository:</span></span>

[<span data-ttu-id="87684-125">AdventureWorks örnek veritabanları</span><span class="sxs-lookup"><span data-stu-id="87684-125">AdventureWorks sample databases</span></span>](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

<span data-ttu-id="87684-126">Veritabanı yedekleme (.bak)\*dosyalarından birini indirdikten sonra, SQL Server Management Studio (SSMS) kullanarak yedeklemeyi SQL Server örneğine geri yükleyin.</span><span class="sxs-lookup"><span data-stu-id="87684-126">After you download one of the database backup (\*.bak) files, restore the backup to an instance of SQL Server by using SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="87684-127">Bkz. [SQL Server Management Studio alın.](#get_ssms)</span><span class="sxs-lookup"><span data-stu-id="87684-127">See [Get SQL Server Management Studio](#get_ssms).</span></span>

## <a name="get-sql-server-management-studio"></a><a name="get_ssms"></a><span data-ttu-id="87684-128">SQL Server Management Studio alın</span><span class="sxs-lookup"><span data-stu-id="87684-128">Get SQL Server Management Studio</span></span>
<span data-ttu-id="87684-129">İndirdiğiniz bir veritabanını görüntülemek veya değiştirmek istiyorsanız, SQL Server Management Studio 'yı (SSMS) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87684-129">If you want to view or modify a database that you've downloaded, you can use SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="87684-130">Aşağıdaki sayfadan SSMS indirin:</span><span class="sxs-lookup"><span data-stu-id="87684-130">Download SSMS from the following page:</span></span>

[<span data-ttu-id="87684-131">SQL Server Management Studio’yu (SSMS) İndirme</span><span class="sxs-lookup"><span data-stu-id="87684-131">Download SQL Server Management Studio (SSMS)</span></span>](/sql/ssms/download-sql-server-management-studio-ssms)

<span data-ttu-id="87684-132">Ayrıca Visual Studio tümleşik geliştirme ortamında (IDE) veritabanlarını görüntüleyebilir ve yönetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87684-132">You can also view and manage databases in the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="87684-133">[Visual](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)Studio'da, SQL **Server Object Explorer'dan**veritabanına bağlanın veya **Server Explorer'daki**veritabanına bir Veri Bağlantısı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="87684-133">In [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), connect to the database from **SQL Server Object Explorer**, or create a Data Connection to the database in **Server Explorer**.</span></span> <span data-ttu-id="87684-134">Bu gezgin bölmelerini **Görünüm** menüsünden açın.</span><span class="sxs-lookup"><span data-stu-id="87684-134">Open these explorer panes from the **View** menu.</span></span>

## <a name="get-sql-server-express"></a><a name="get_sql"></a><span data-ttu-id="87684-135">SQL Server Express alın</span><span class="sxs-lookup"><span data-stu-id="87684-135">Get SQL Server Express</span></span>

<span data-ttu-id="87684-136">SQL Server Express, SQL Server'ın uygulamalarla yeniden dağıtabileceğiniz ücretsiz, giriş seviyesi bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="87684-136">SQL Server Express is a free, entry-level edition of SQL Server that you can redistribute with applications.</span></span> <span data-ttu-id="87684-137">SQL Server Express'i aşağıdaki sayfadan indirin:</span><span class="sxs-lookup"><span data-stu-id="87684-137">Download SQL Server Express from the following page:</span></span>
  
[<span data-ttu-id="87684-138">SQL Server Express Sürümü</span><span class="sxs-lookup"><span data-stu-id="87684-138">SQL Server Express Edition</span></span>](https://www.microsoft.com/sql-server/sql-server-editions-express)

<span data-ttu-id="87684-139">[Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)kullanıyorsanız, SQL Server Express LocalDB Visual Studio'nun ücretsiz Topluluk baskısına, Professional ve daha yüksek sürümlere dahildir.</span><span class="sxs-lookup"><span data-stu-id="87684-139">If you're using [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB is included in the free Community edition of Visual Studio, as well as the Professional and higher editions.</span></span>  

## <a name="see-also"></a><span data-ttu-id="87684-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87684-140">See also</span></span>

- [<span data-ttu-id="87684-141">Başlarken</span><span class="sxs-lookup"><span data-stu-id="87684-141">Getting Started</span></span>](getting-started.md)
