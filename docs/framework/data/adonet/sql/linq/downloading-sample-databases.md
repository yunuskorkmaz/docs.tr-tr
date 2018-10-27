---
title: Örnek veritabanları için ADO.NET kod örnekleri edinin
description: SQL Server ve yönetim araçlarının yanı sıra ADO.NET belgeler, kod örnekleri kullanılan örnek veritabanları indirme
ms.date: 10/18/2018
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 9779300288135cb9332a028d547ce55a07e89471
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188397"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a><span data-ttu-id="f9341-103">Örnek veritabanları için ADO.NET kod örnekleri edinin</span><span class="sxs-lookup"><span data-stu-id="f9341-103">Get the sample databases for ADO.NET code samples</span></span>

<span data-ttu-id="f9341-104">Örnekler ve izlenecek yollar, bir dizi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] örnek veritabanları ve SQL Server Express belgeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="f9341-104">A number of samples and walkthroughs in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation use sample databases and SQL Server Express.</span></span> <span data-ttu-id="f9341-105">Microsoft bu ürünlerin ücretsiz olarak indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9341-105">You can download these products free of charge from Microsoft.</span></span>

## <a name="get-the-northwind-sample-database"></a><span data-ttu-id="f9341-106">Northwind örnek veritabanını almak</span><span class="sxs-lookup"><span data-stu-id="f9341-106">Get the Northwind sample database</span></span>

<span data-ttu-id="f9341-107">Northwind örnek veritabanıyla kurulan Microsoft Download Center'daki şu sayfadan yükleyin:</span><span class="sxs-lookup"><span data-stu-id="f9341-107">Download the Northwind sample database from the following page in the Microsoft Download Center:</span></span>

[<span data-ttu-id="f9341-108">Northwind ve Pubs örnek veritabanları</span><span class="sxs-lookup"><span data-stu-id="f9341-108">Northwind and Pubs Sample Databases</span></span>](https://go.microsoft.com/fwlink?linkid=64296)

<span data-ttu-id="f9341-109">Dosya indirdi sonra veritabanları ve komut dosyalarını ayıklamak için dosyaya çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f9341-109">After the file has downloaded, double-click the file to extract the databases and scripts.</span></span> <span data-ttu-id="f9341-110">Varsayılan olarak, dosyaların klasöründe yüklü `<drive>:\SQL Server 2000 Sample Databases`.</span><span class="sxs-lookup"><span data-stu-id="f9341-110">By default, the files are installed in the folder `<drive>:\SQL Server 2000 Sample Databases`.</span></span>

<span data-ttu-id="f9341-111">Northwind veritabanı kullanabilmeniz için SQL Server örneği üzerinde veritabanı kullanarak oluşturmanız gerekebilir [SQL Server Management Studio](#get_ssms) veya çalıştırmak için benzer bir araç `instnwnd.sql` yükleme klasöründe betik dosyası.</span><span class="sxs-lookup"><span data-stu-id="f9341-111">Before you can use the Northwind database, you have to recreate the database on an instance of SQL Server by using [SQL Server Management Studio](#get_ssms) or a similar tool to run the `instnwnd.sql` script file in the installation folder.</span></span>

## <a name="get-the-adventureworks-sample-database"></a><span data-ttu-id="f9341-112">AdventureWorks örnek veritabanını almak</span><span class="sxs-lookup"><span data-stu-id="f9341-112">Get the AdventureWorks sample database</span></span>

<span data-ttu-id="f9341-113">AdventureWorks örnek veritabanını aşağıdaki GitHub deposundan indirin:</span><span class="sxs-lookup"><span data-stu-id="f9341-113">Download the AdventureWorks sample database from the following GitHub repository:</span></span>

[<span data-ttu-id="f9341-114">AdventureWorks örnek veritabanları</span><span class="sxs-lookup"><span data-stu-id="f9341-114">AdventureWorks sample databases</span></span>](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

<span data-ttu-id="f9341-115">Bir veritabanı yedeğinin indirdikten sonra (\*.bak) dosyaları, SQL Server örneğine SQL Server Management Studio (SSMS) kullanarak yedeklemeyi geri yükleme.</span><span class="sxs-lookup"><span data-stu-id="f9341-115">After you download one of the database backup (\*.bak) files, restore the backup to an instance of SQL Server by using SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="f9341-116">Bkz: [alma SQL Server Management Studio'yu](#get_ssms).</span><span class="sxs-lookup"><span data-stu-id="f9341-116">See [Get SQL Server Management Studio](#get_ssms).</span></span>

## <a name="get_sql"></a> <span data-ttu-id="f9341-117">SQL Server Express edinin</span><span class="sxs-lookup"><span data-stu-id="f9341-117">Get SQL Server Express</span></span>

<span data-ttu-id="f9341-118">SQL Server Express, SQL Server, uygulamaları yeniden dağıtabilirsiniz, ücretsiz, giriş düzeyi bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="f9341-118">SQL Server Express is a free, entry-level edition of SQL Server that you can redistribute with applications.</span></span> <span data-ttu-id="f9341-119">SQL Server Express'i aşağıdaki sayfadan indirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f9341-119">Download SQL Server Express from the following page:</span></span>
  
[<span data-ttu-id="f9341-120">SQL Server Express sürümleri</span><span class="sxs-lookup"><span data-stu-id="f9341-120">SQL Server Express Editions</span></span>](https://www.microsoft.com/sql-server/sql-server-editions-express)

<span data-ttu-id="f9341-121">Kullanıyorsanız [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB, Professional ve üzeri sürümleri yanı sıra ücretsiz Community sürümü bulunur.</span><span class="sxs-lookup"><span data-stu-id="f9341-121">If you're using [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB is included in the free Community edition as well as the Professional and higher editions.</span></span>  

## <a name="get_ssms"></a> <span data-ttu-id="f9341-122">SQL Server Management Studio'yu edinin</span><span class="sxs-lookup"><span data-stu-id="f9341-122">Get SQL Server Management Studio</span></span>
<span data-ttu-id="f9341-123">Görüntülemek veya karşıdan yüklediğiniz bir veritabanı değiştirmek istiyorsanız, SQL Server Management Studio (SSMS) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9341-123">If you want to view or modify a database that you've downloaded, you can use SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="f9341-124">SSMS aşağıdaki sayfasından indirin:</span><span class="sxs-lookup"><span data-stu-id="f9341-124">Download SSMS from the following page:</span></span>

[<span data-ttu-id="f9341-125">SQL Server Management Studio'yu (SSMS) indirin</span><span class="sxs-lookup"><span data-stu-id="f9341-125">Download SQL Server Management Studio (SSMS)</span></span>](/sql/ssms/download-sql-server-management-studio-ssms) 

<span data-ttu-id="f9341-126">Ayrıca, görüntüleyin ve Visual Studio tümleşik geliştirme ortamı (IDE) veritabanlarında yönetin.</span><span class="sxs-lookup"><span data-stu-id="f9341-126">You can also view and manage databases in the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="f9341-127">İçinde [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), veritabanından bağlanma **SQL Server Nesne Gezgini**, ya da veritabanında veri bağlantısı oluşturma **Sunucu Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="f9341-127">In [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), connect to the database from **SQL Server Object Explorer**, or create a Data Connection to the database in **Server Explorer**.</span></span> <span data-ttu-id="f9341-128">Bu Gezgini bölmeden açın **görünümü** menüsü.</span><span class="sxs-lookup"><span data-stu-id="f9341-128">Open these explorer panes from the **View** menu.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f9341-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9341-129">See also</span></span>

- [<span data-ttu-id="f9341-130">Başlarken</span><span class="sxs-lookup"><span data-stu-id="f9341-130">Getting Started</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
