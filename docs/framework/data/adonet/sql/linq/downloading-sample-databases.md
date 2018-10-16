---
title: Örnek veritabanları için ADO.NET kod örnekleri edinin
description: SQL Server ve yönetim araçlarının yanı sıra ADO.NET belgeler, kod örnekleri kullanılan örnek veritabanları indirme
ms.date: 10/12/2018
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 75ae1895d683b669f51b33130fc2f47010e39814
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49347536"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a><span data-ttu-id="3ec4d-103">Örnek veritabanları için ADO.NET kod örnekleri edinin</span><span class="sxs-lookup"><span data-stu-id="3ec4d-103">Get the sample databases for ADO.NET code samples</span></span>

<span data-ttu-id="3ec4d-104">Örnekler ve izlenecek yollar, bir dizi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] örnek veritabanları ve SQL Server Express belgeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="3ec4d-104">A number of samples and walkthroughs in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation use sample databases and SQL Server Express.</span></span> <span data-ttu-id="3ec4d-105">Microsoft bu ürünlerin ücretsiz olarak indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ec4d-105">You can download these products free of charge from Microsoft.</span></span>

## <a name="get-the-adventureworks-sample-database"></a><span data-ttu-id="3ec4d-106">AdventureWorks örnek veritabanını almak</span><span class="sxs-lookup"><span data-stu-id="3ec4d-106">Get the AdventureWorks sample database</span></span>

<span data-ttu-id="3ec4d-107">AdventureWorks örnek veritabanını aşağıdaki GitHub deposundan indirin:</span><span class="sxs-lookup"><span data-stu-id="3ec4d-107">Download the AdventureWorks sample database from the following GitHub repository:</span></span>

[<span data-ttu-id="3ec4d-108">AdventureWorks örnek veritabanları</span><span class="sxs-lookup"><span data-stu-id="3ec4d-108">AdventureWorks sample databases</span></span>](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

<span data-ttu-id="3ec4d-109">Bir veritabanı yedeğinin indirdikten sonra (\*.bak) dosyaları, SQL Server örneğine SQL Server Management Studio (SSMS) kullanarak yedeklemeyi geri yükleme.</span><span class="sxs-lookup"><span data-stu-id="3ec4d-109">After you download one of the database backup (\*.bak) files, restore the backup to an instance of SQL Server by using SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="3ec4d-110">Bkz: [alma SQL Server Management Studio'yu](#get_ssms).</span><span class="sxs-lookup"><span data-stu-id="3ec4d-110">See [Get SQL Server Management Studio](#get_ssms).</span></span>

## <a name="get-the-northwind-sample-database"></a><span data-ttu-id="3ec4d-111">Northwind örnek veritabanını almak</span><span class="sxs-lookup"><span data-stu-id="3ec4d-111">Get the Northwind sample database</span></span>

<span data-ttu-id="3ec4d-112">Northwind örnek veritabanıyla kurulan Microsoft Download Center'daki şu sayfadan yükleyin:</span><span class="sxs-lookup"><span data-stu-id="3ec4d-112">Download the Northwind sample database from the following page in the Microsoft Download Center:</span></span>

[<span data-ttu-id="3ec4d-113">Northwind ve Pubs örnek veritabanları</span><span class="sxs-lookup"><span data-stu-id="3ec4d-113">Northwind and Pubs Sample Databases</span></span>](https://go.microsoft.com/fwlink?linkid=64296)

<span data-ttu-id="3ec4d-114">Dosya indirdi sonra veritabanları ve komut dosyalarını ayıklamak için dosyaya çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="3ec4d-114">After the file has downloaded, double-click the file to extract the databases and scripts.</span></span> <span data-ttu-id="3ec4d-115">Varsayılan olarak, dosyaların klasöründe yüklü `<drive>:\SQL Server 2000 Sample Databases`.</span><span class="sxs-lookup"><span data-stu-id="3ec4d-115">By default, the files are installed in the folder `<drive>:\SQL Server 2000 Sample Databases`.</span></span>

<span data-ttu-id="3ec4d-116">Northwind veritabanı kullanabilmeniz için aşağıdakilerden birini yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="3ec4d-116">Before you can use the Northwind database, you have to do one of the following things:</span></span>

- <span data-ttu-id="3ec4d-117">Veritabanı bir SQL Server örneği üzerinde çalıştırarak yeniden `instnwnd.sql` yükleme klasöründe betik dosyası.</span><span class="sxs-lookup"><span data-stu-id="3ec4d-117">Recreate the database on an instance of SQL Server by running the `instnwnd.sql` script file in the installation folder.</span></span>

- <span data-ttu-id="3ec4d-118">Ekleme `northwnd.mdf` ile kendi karşılık gelen dosya `*.ldf` günlük dosyası için bir SQL Server örneği.</span><span class="sxs-lookup"><span data-stu-id="3ec4d-118">Attach the `northwnd.mdf` file with its corresponding `*.ldf` log file to an instance of SQL Server.</span></span>

## <a name="get_sql"></a> <span data-ttu-id="3ec4d-119">SQL Server Express edinin</span><span class="sxs-lookup"><span data-stu-id="3ec4d-119">Get SQL Server Express</span></span>

<span data-ttu-id="3ec4d-120">SQL Server Express, SQL Server, uygulamaları yeniden dağıtabilirsiniz, ücretsiz, giriş düzeyi bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="3ec4d-120">SQL Server Express is a free, entry-level edition of SQL Server that you can redistribute with applications.</span></span> <span data-ttu-id="3ec4d-121">SQL Server Express'i aşağıdaki sayfadan indirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3ec4d-121">Download SQL Server Express from the following page:</span></span>
  
[<span data-ttu-id="3ec4d-122">SQL Server Express sürümleri</span><span class="sxs-lookup"><span data-stu-id="3ec4d-122">SQL Server Express Editions</span></span>](https://www.microsoft.com/sql-server/sql-server-editions-express)

<span data-ttu-id="3ec4d-123">Kullanıyorsanız [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB, Professional ve üzeri sürümleri yanı sıra Community sürümü bulunur.</span><span class="sxs-lookup"><span data-stu-id="3ec4d-123">If you're using [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB is included in the Community edition as well as the Professional and higher editions.</span></span>  

## <a name="get_ssms"></a> <span data-ttu-id="3ec4d-124">SQL Server Management Studio'yu edinin</span><span class="sxs-lookup"><span data-stu-id="3ec4d-124">Get SQL Server Management Studio</span></span>
<span data-ttu-id="3ec4d-125">Görüntülemek veya karşıdan yüklediğiniz bir veritabanı değiştirmek istiyorsanız, SQL Server Management Studio (SSMS) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ec4d-125">If you want to view or modify a database that you've downloaded, you can use SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="3ec4d-126">SSMS aşağıdaki sayfasından indirin:</span><span class="sxs-lookup"><span data-stu-id="3ec4d-126">Download SSMS from the following page:</span></span>

[<span data-ttu-id="3ec4d-127">SQL Server Management Studio'yu (SSMS) indirin</span><span class="sxs-lookup"><span data-stu-id="3ec4d-127">Download SQL Server Management Studio (SSMS)</span></span>](/sql/ssms/download-sql-server-management-studio-ssms) 

<span data-ttu-id="3ec4d-128">Ayrıca, görüntüleyin ve Visual Studio tümleşik geliştirme ortamı (IDE) veritabanlarında yönetin.</span><span class="sxs-lookup"><span data-stu-id="3ec4d-128">You can also view and manage databases in the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="3ec4d-129">İçinde [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), veritabanından bağlanma **SQL Server Nesne Gezgini**, ya da veritabanında veri bağlantısı oluşturma **Sunucu Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="3ec4d-129">In [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), connect to the database from **SQL Server Object Explorer**, or create a Data Connection to the database in **Server Explorer**.</span></span> <span data-ttu-id="3ec4d-130">Bu Gezgini bölmeden açın **görünümü** menüsü.</span><span class="sxs-lookup"><span data-stu-id="3ec4d-130">Open these explorer panes from the **View** menu.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3ec4d-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ec4d-131">See also</span></span>

- [<span data-ttu-id="3ec4d-132">Başlarken</span><span class="sxs-lookup"><span data-stu-id="3ec4d-132">Getting Started</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
