---
title: Örnek SQL Server veritabanları için ADO.NET kod örnekleri edinin
description: SQL Server ve yönetim araçlarının yanı sıra ADO.NET belgeler, kod örnekleri kullanılan örnek SQL Server veritabanları indirme
ms.date: 01/11/2019
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 5580f06f3d28ed6d70f75b619498ac8de7bc3326
ms.sourcegitcommit: 75567a3cb437009db55949c6092f4e77ed1a9da4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54307298"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a><span data-ttu-id="a22ca-103">Örnek veritabanları için ADO.NET kod örnekleri edinin</span><span class="sxs-lookup"><span data-stu-id="a22ca-103">Get the sample databases for ADO.NET code samples</span></span>

<span data-ttu-id="a22ca-104">Örnekler ve izlenecek yollar, bir dizi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] örnek SQL Server veritabanları ve SQL Server Express belgeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="a22ca-104">A number of examples and walkthroughs in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation use sample SQL Server databases and SQL Server Express.</span></span> <span data-ttu-id="a22ca-105">Microsoft bu ürünlerin ücretsiz olarak indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a22ca-105">You can download these products free of charge from Microsoft.</span></span>

## <a name="get-the-northwind-sample-database-for-sql-server"></a><span data-ttu-id="a22ca-106">Northwind örnek veritabanını almak için SQL Server</span><span class="sxs-lookup"><span data-stu-id="a22ca-106">Get the Northwind sample database for SQL Server</span></span>

<span data-ttu-id="a22ca-107">Betiği indirin `instnwnd.sql` oluşturmak ve SQL Server için Northwind örnek veritabanını yüklemek için aşağıdaki GitHub deposundan:</span><span class="sxs-lookup"><span data-stu-id="a22ca-107">Download the script `instnwnd.sql` from the following GitHub repository to create and load the Northwind sample database for SQL Server:</span></span>

[<span data-ttu-id="a22ca-108">Northwind ve pubs örnek veritabanlarını Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="a22ca-108">Northwind and pubs sample databases for Microsoft SQL Server</span></span>](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

<span data-ttu-id="a22ca-109">Northwind veritabanı kullanabilmeniz için indirilen çalıştırmak zorunda `instnwnd.sql` komut dosyası kullanarak SQL Server örneği üzerinde veritabanı yeniden [SQL Server Management Studio](#get_ssms) veya benzer bir araç.</span><span class="sxs-lookup"><span data-stu-id="a22ca-109">Before you can use the Northwind database, you have to run the downloaded `instnwnd.sql` script file to recreate the database on an instance of SQL Server by using [SQL Server Management Studio](#get_ssms) or a similar tool.</span></span> <span data-ttu-id="a22ca-110">Depodaki benioku dosyasındaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="a22ca-110">Follow the instructions in the Readme file in the repository.</span></span>

> [!TIP]
> <span data-ttu-id="a22ca-111">Microsoft Access için Northwind veritabanı arıyorsanız bkz [Microsoft Access için Northwind örnek veritabanını yüklemek](#northwind_access).</span><span class="sxs-lookup"><span data-stu-id="a22ca-111">If you're looking for the Northwind database for Microsoft Access, see [Install the Northwind sample database for Microsoft Access](#northwind_access).</span></span>

## <a name="northwind_access"></a> <span data-ttu-id="a22ca-112">Microsoft Access için Northwind örnek veritabanıyla kurulan Al</span><span class="sxs-lookup"><span data-stu-id="a22ca-112">Get the Northwind sample database for Microsoft Access</span></span>

<span data-ttu-id="a22ca-113">Microsoft Access için Northwind örnek veritabanı Microsoft Download Center kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="a22ca-113">The Northwind sample database for Microsoft Access is not available on the Microsoft Download Center.</span></span> <span data-ttu-id="a22ca-114">Northwind doğrudan erişim içinde yüklemek için şunları yapın:</span><span class="sxs-lookup"><span data-stu-id="a22ca-114">To install Northwind directly from within Access, do the following things:</span></span>

1. <span data-ttu-id="a22ca-115">Erişimi'ni açın.</span><span class="sxs-lookup"><span data-stu-id="a22ca-115">Open Access.</span></span>

1. <span data-ttu-id="a22ca-116">ENTER **Northwind** içinde **çevrimiçi şablonlar için arama** kutusuna ve ardından **Enter**.</span><span class="sxs-lookup"><span data-stu-id="a22ca-116">Enter **Northwind** in the **Search for Online Templates** box, and then select **Enter**.</span></span>

1. <span data-ttu-id="a22ca-117">Sonuçlar ekranda işaretleyin **Northwind**.</span><span class="sxs-lookup"><span data-stu-id="a22ca-117">On the results screen, select **Northwind**.</span></span> <span data-ttu-id="a22ca-118">Northwind veritabanı açıklaması ile yeni bir pencere açılır.</span><span class="sxs-lookup"><span data-stu-id="a22ca-118">A new window opens with a description of the Northwind database.</span></span>

1. <span data-ttu-id="a22ca-119">Yeni pencerede, **dosya adı** metin kutusunda, Northwind veritabanı kopyası için bir dosya adı sağlayın.</span><span class="sxs-lookup"><span data-stu-id="a22ca-119">In the new window, in the **File Name** text box, provide a filename for your copy of the Northwind database.</span></span>

1. <span data-ttu-id="a22ca-120">**Oluştur**’u seçin.</span><span class="sxs-lookup"><span data-stu-id="a22ca-120">Select **Create**.</span></span> <span data-ttu-id="a22ca-121">Erişim, Northwind veritabanına yükler ve dosya hazırlar.</span><span class="sxs-lookup"><span data-stu-id="a22ca-121">Access downloads the Northwind database and prepares the file.</span></span>

1. <span data-ttu-id="a22ca-122">Bu işlem tamamlandığında veritabanı ile bir Hoş Geldiniz ekranı açılır.</span><span class="sxs-lookup"><span data-stu-id="a22ca-122">When this process is complete, the database opens with a Welcome screen.</span></span>

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a><span data-ttu-id="a22ca-123">AdventureWorks örnek veritabanını almak için SQL Server</span><span class="sxs-lookup"><span data-stu-id="a22ca-123">Get the AdventureWorks sample database for SQL Server</span></span>

<span data-ttu-id="a22ca-124">AdventureWorks örnek veritabanını SQL Server aşağıdaki GitHub deposundan indirin:</span><span class="sxs-lookup"><span data-stu-id="a22ca-124">Download the AdventureWorks sample database for SQL Server from the following GitHub repository:</span></span>

[<span data-ttu-id="a22ca-125">AdventureWorks örnek veritabanları</span><span class="sxs-lookup"><span data-stu-id="a22ca-125">AdventureWorks sample databases</span></span>](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

<span data-ttu-id="a22ca-126">Bir veritabanı yedeğinin indirdikten sonra (\*.bak) dosyaları, SQL Server örneğine SQL Server Management Studio (SSMS) kullanarak yedeklemeyi geri yükleme.</span><span class="sxs-lookup"><span data-stu-id="a22ca-126">After you download one of the database backup (\*.bak) files, restore the backup to an instance of SQL Server by using SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="a22ca-127">Bkz: [alma SQL Server Management Studio'yu](#get_ssms).</span><span class="sxs-lookup"><span data-stu-id="a22ca-127">See [Get SQL Server Management Studio](#get_ssms).</span></span>

## <a name="get_ssms"></a> <span data-ttu-id="a22ca-128">SQL Server Management Studio'yu edinin</span><span class="sxs-lookup"><span data-stu-id="a22ca-128">Get SQL Server Management Studio</span></span>
<span data-ttu-id="a22ca-129">Görüntülemek veya karşıdan yüklediğiniz bir veritabanı değiştirmek istiyorsanız, SQL Server Management Studio (SSMS) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a22ca-129">If you want to view or modify a database that you've downloaded, you can use SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="a22ca-130">SSMS aşağıdaki sayfasından indirin:</span><span class="sxs-lookup"><span data-stu-id="a22ca-130">Download SSMS from the following page:</span></span>

[<span data-ttu-id="a22ca-131">SQL Server Management Studio'yu (SSMS) indirin</span><span class="sxs-lookup"><span data-stu-id="a22ca-131">Download SQL Server Management Studio (SSMS)</span></span>](/sql/ssms/download-sql-server-management-studio-ssms) 

<span data-ttu-id="a22ca-132">Ayrıca, görüntüleyin ve Visual Studio tümleşik geliştirme ortamı (IDE) veritabanlarında yönetin.</span><span class="sxs-lookup"><span data-stu-id="a22ca-132">You can also view and manage databases in the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="a22ca-133">İçinde [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), veritabanından bağlanma **SQL Server Nesne Gezgini**, ya da veritabanında veri bağlantısı oluşturma **Sunucu Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="a22ca-133">In [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), connect to the database from **SQL Server Object Explorer**, or create a Data Connection to the database in **Server Explorer**.</span></span> <span data-ttu-id="a22ca-134">Bu Gezgini bölmeden açın **görünümü** menüsü.</span><span class="sxs-lookup"><span data-stu-id="a22ca-134">Open these explorer panes from the **View** menu.</span></span>

## <a name="get_sql"></a> <span data-ttu-id="a22ca-135">SQL Server Express edinin</span><span class="sxs-lookup"><span data-stu-id="a22ca-135">Get SQL Server Express</span></span>

<span data-ttu-id="a22ca-136">SQL Server Express, SQL Server, uygulamaları yeniden dağıtabilirsiniz, ücretsiz, giriş düzeyi bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="a22ca-136">SQL Server Express is a free, entry-level edition of SQL Server that you can redistribute with applications.</span></span> <span data-ttu-id="a22ca-137">SQL Server Express'i aşağıdaki sayfadan indirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a22ca-137">Download SQL Server Express from the following page:</span></span>
  
[<span data-ttu-id="a22ca-138">SQL Server Express Edition</span><span class="sxs-lookup"><span data-stu-id="a22ca-138">SQL Server Express Edition</span></span>](https://www.microsoft.com/sql-server/sql-server-editions-express)

<span data-ttu-id="a22ca-139">Kullanıyorsanız [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB Visual Studio'nun Ücretsiz Community edition, ek olarak profesyonel ve üzeri sürümleri dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="a22ca-139">If you're using [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB is included in the free Community edition of Visual Studio, as well as the Professional and higher editions.</span></span>  

## <a name="see-also"></a><span data-ttu-id="a22ca-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a22ca-140">See also</span></span>

- [<span data-ttu-id="a22ca-141">Başlarken</span><span class="sxs-lookup"><span data-stu-id="a22ca-141">Getting Started</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
