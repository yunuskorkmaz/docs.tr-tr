---
title: "Visual Basic uygulamalarındaki verilere erişme"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- data [Visual Basic]
- Visual Basic, data access
ms.assetid: 3086ab38-3be5-4b22-9385-7d0e16b04f6a
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fd4dbc66f37325afa64b7bf9720cad23e08c6bfb
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
---
# <a name="accessing-data-in-visual-basic-applications"></a><span data-ttu-id="a2cfb-102">Visual Basic uygulamalarındaki verilere erişme</span><span class="sxs-lookup"><span data-stu-id="a2cfb-102">Accessing data in Visual Basic applications</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="a2cfb-103">, verilere erişen uygulamalar geliştirmede size yardımcı olmak için çeşitli yeni özellikler içerir.</span><span class="sxs-lookup"><span data-stu-id="a2cfb-103"> includes several new features to assist in developing applications that access data.</span></span> <span data-ttu-id="a2cfb-104">Windows uygulamaları için veri bağlama formları konumundan öğeleri sürükleyerek oluşturulur [veri kaynakları penceresi](/visualstudio/data-tools/add-new-data-sources) forma.</span><span class="sxs-lookup"><span data-stu-id="a2cfb-104">Data-bound forms for Windows applications are created by dragging items from the [Data Sources Window](/visualstudio/data-tools/add-new-data-sources) onto the form.</span></span> <span data-ttu-id="a2cfb-105">Konumundan öğeleri sürükleyerek verilere denetimler bağlama **veri kaynakları penceresi** mevcut denetimleri üzerine.</span><span class="sxs-lookup"><span data-stu-id="a2cfb-105">You bind controls to data by dragging items from the **Data Sources Window** onto existing controls.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a2cfb-106">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="a2cfb-106">Related sections</span></span>  
 [<span data-ttu-id="a2cfb-107">Visual Studio'da veri erişimi</span><span class="sxs-lookup"><span data-stu-id="a2cfb-107">Accessing Data in Visual Studio</span></span>](/visualstudio/data-tools/)  
 <span data-ttu-id="a2cfb-108">Uygulamalarınıza veri erişim işlevini dahil etme konusunun tartışıldığı sayfalara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2cfb-108">Provides links to pages that discuss incorporating data access functionality into your applications.</span></span>

 [<span data-ttu-id="a2cfb-109">.NET için Visual Studio veri araçları</span><span class="sxs-lookup"><span data-stu-id="a2cfb-109">Visual Studio data tools for .NET</span></span>](/visualstudio/data-tools/visual-studio-data-tools-for-dotnet)  
 <span data-ttu-id="a2cfb-110">[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] kullanarak, verilerle çalışan uygulamalar oluşturma hakkındaki sayfalara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2cfb-110">Provides links to pages on creating applications that work with data, using [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].</span></span>  
  
 [<span data-ttu-id="a2cfb-111">LINQ</span><span class="sxs-lookup"><span data-stu-id="a2cfb-111">LINQ</span></span>](../../visual-basic/programming-guide/language-features/linq/index.md)  
 <span data-ttu-id="a2cfb-112">Visual Basic ile LINQ'nun nasıl kullanılacağını açıklayan konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2cfb-112">Provides links to topics that describe how to use LINQ with Visual Basic.</span></span>  
  
 [<span data-ttu-id="a2cfb-113">LINQ-SQL</span><span class="sxs-lookup"><span data-stu-id="a2cfb-113">LINQ to SQL</span></span>](../../../docs/framework/data/adonet/sql/linq/index.md)  
 <span data-ttu-id="a2cfb-114">[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] hakkında bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2cfb-114">Provides information about [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="a2cfb-115">Programlama örnekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="a2cfb-115">Includes programming examples.</span></span>  
  
 [<span data-ttu-id="a2cfb-116">LINQ-SQL Visual Studio Araçları</span><span class="sxs-lookup"><span data-stu-id="a2cfb-116">LINQ to SQL Tools in Visual Studio</span></span>](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)  
 <span data-ttu-id="a2cfb-117">Oluşturmayla ilgili konulara bağlantılar sağlanır bir [LINQ-SQL](../../../docs/framework/data/adonet/sql/linq/index.md) uygulamalarında nesne modeli.</span><span class="sxs-lookup"><span data-stu-id="a2cfb-117">Provides links to topics about how to create a [LINQ to SQL](../../../docs/framework/data/adonet/sql/linq/index.md) object model in applications.</span></span>  
  
 [<span data-ttu-id="a2cfb-118">N katmanlı uygulamalarda veri kümeleriyle çalışma</span><span class="sxs-lookup"><span data-stu-id="a2cfb-118">Work with datasets in n-tier applications</span></span>](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications)  
 <span data-ttu-id="a2cfb-119">Çok verili uygulamaların nasıl oluşturulacağı hakkındaki konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2cfb-119">Provides links to topics about how to create multitiered data applications.</span></span>  
     
 [<span data-ttu-id="a2cfb-120">Yeni bağlantı ekleme</span><span class="sxs-lookup"><span data-stu-id="a2cfb-120">Add new connections</span></span>](/visualstudio/data-tools/add-new-connections)  
 <span data-ttu-id="a2cfb-121">Uygulamanızı [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] kullanarak tasarım zaman araçları ve ADO.NET bağlantı nesneleri ile veriye bağlama hakkındaki sayfalara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2cfb-121">Provides links to pages on connecting your application to data with design-time tools and ADO.NET connection objects, using [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].</span></span>  

 [<span data-ttu-id="a2cfb-122">Visual Studio'da veri kümesi araçları</span><span class="sxs-lookup"><span data-stu-id="a2cfb-122">Dataset Tools in Visual Studio</span></span>](/visualstudio/data-tools/dataset-tools-in-visual-studio)  
 <span data-ttu-id="a2cfb-123">Veri kümeslerine nasıl veri yükleneceğini ve SQL hesap özetlerinin ve depolanan yordamların nasıl yürütüleceğini açıklayan sayfalara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2cfb-123">Provides links to pages describing how to load data into datasets and how to execute SQL statements and stored procedures.</span></span>  
  
 [<span data-ttu-id="a2cfb-124">Visual Studio'da verilere denetimler bağlama</span><span class="sxs-lookup"><span data-stu-id="a2cfb-124">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)  
 <span data-ttu-id="a2cfb-125">Windows Formatında veri sınır denetimleri aracılığıyla nasıl veri görüntülendiğini açıklayan sayfalara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2cfb-125">Provides links to pages that explain how to display data on Windows Forms through data-bound controls.</span></span>  
  
 [<span data-ttu-id="a2cfb-126">Veri kümelerindeki verileri düzenleme</span><span class="sxs-lookup"><span data-stu-id="a2cfb-126">Edit Data in Datasets</span></span>](/visualstudio/data-tools/edit-data-in-datasets)  
 <span data-ttu-id="a2cfb-127">Bir veri kümesinin veri tabloları içindeki verilerin nasıl yönetileceğini açıklayan sayfalara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2cfb-127">Provides links to pages describing how to manipulate the data in the data tables of a dataset.</span></span>  
  
 [<span data-ttu-id="a2cfb-128">Veri kümelerindeki verileri doğrulama</span><span class="sxs-lookup"><span data-stu-id="a2cfb-128">Validate data in datasets</span></span>](/visualstudio/data-tools/validate-data-in-datasets)  
 <span data-ttu-id="a2cfb-129">Sütun ve satır değişiklikleri sırasında bir veri kümesine nasıl doğrulama ekleneceğini açıklayan sayfalara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2cfb-129">Provides links to pages describing how to add validation to a dataset during column and row changes.</span></span>  
  
 [<span data-ttu-id="a2cfb-130">Verileri yeniden veritabanına kaydetme</span><span class="sxs-lookup"><span data-stu-id="a2cfb-130">Save data back to the database</span></span>](/visualstudio/data-tools/save-data-back-to-the-database)  
 <span data-ttu-id="a2cfb-131">Bir uygulamadan veritabanına, güncelleştirilmiş verilerin nasıl gönderildiğini açıklayan sayfalara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2cfb-131">Provides links to pages explaining how to send updated data from an application to the database.</span></span>  
  
 [<span data-ttu-id="a2cfb-132">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a2cfb-132">ADO.NET</span></span>](https://msdn.microsoft.com/library/e80y5yhx.aspx)  
 <span data-ttu-id="a2cfb-133">.NET Framework programcısına veri erişim hizmetlerini gösteren ADO.NET sınıflarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a2cfb-133">Describes the ADO.NET classes, which expose data-access services to the .NET Framework programmer.</span></span>

 [<span data-ttu-id="a2cfb-134">Office Çözümlerindeki Veriler</span><span class="sxs-lookup"><span data-stu-id="a2cfb-134">Data in Office Solutions</span></span>](https://msdn.microsoft.com/library/xx069ybh)  
 <span data-ttu-id="a2cfb-135">Office çözümlerinde, şema yönelimli programlama, veriyi önbelleğe alma ve sunucu tarafı veri erişimi hakkında bilgiler de dahil olmak üzere, verilerin nasıl çalıştığını açıklayan sayfalara bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="a2cfb-135">Contains links to pages that explain how data works in Office solutions, including information about schema-oriented programming, data caching, and server-side data access.</span></span>
