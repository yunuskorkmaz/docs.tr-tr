---
title: LINQ to SQL örneği
ms.date: 03/30/2017
ms.assetid: 5f39db9e-0e62-42c9-8c98-bb8b54cec98c
ms.openlocfilehash: 83dc8433459f64860baaca2e8309fbc85e2bb3a2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515374"
---
# <a name="linq-to-sql-sample"></a><span data-ttu-id="b213d-102">LINQ to SQL örneği</span><span class="sxs-lookup"><span data-stu-id="b213d-102">LINQ to SQL Sample</span></span>
<span data-ttu-id="b213d-103">Bu örnek, LINQ, SQL Server veritabanlarını tablodan SQL sorgu varlıklara kullanmak için bir etkinlik oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b213d-103">This sample demonstrates how to create an activity to use LINQ to SQL query entities from tables in SQL Server databases.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b213d-104">WCF örnekleri makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="b213d-104">The WCF samples may already be installed on your machine.</span></span> <span data-ttu-id="b213d-105">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b213d-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\Samples\WCFWFCardspace`  
>   
>  <span data-ttu-id="b213d-106">Bu dizin mevcut değil, bu sayfanın üstündeki örnek bağlantıya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b213d-106">If this directory does not exist, click the download sample link at the top of this page.</span></span> <span data-ttu-id="b213d-107">Bu bağlantı indirir ve yükler tüm Not [!INCLUDE[wf1](../../../../includes/wf1-md.md)], WCF, ve [!INCLUDE[infocard](../../../../includes/infocard-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="b213d-107">Note that this link downloads and installs all of the [!INCLUDE[wf1](../../../../includes/wf1-md.md)], WCF, and [!INCLUDE[infocard](../../../../includes/infocard-md.md)] samples.</span></span> <span data-ttu-id="b213d-108">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b213d-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\Samples\WCFWFCardSpace\WF\Scenario\ActivityLibrary\Linq\LinqToSql`  
  
## <a name="activity-details-for-findinsqltable"></a><span data-ttu-id="b213d-109">FindInSqlTable için etkinlik ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="b213d-109">Activity details for FindInSqlTable</span></span>  
 <span data-ttu-id="b213d-110">Bu etkinlik, LINQ to SQL kullanarak bir veritabanındaki tablolarda bulunan sorgu varlıklara kullanıcıların sağlar.</span><span class="sxs-lookup"><span data-stu-id="b213d-110">This activity allows users to query entities from tables in a database using LINQ to SQL.</span></span> <span data-ttu-id="b213d-111">Kullanıcı etkinliğinin bir LINQ koşul sonuçları filtrelemek için bir lambda ifadesinin biçiminde de sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b213d-111">Users of the activity can also provide a LINQ predicate in the form of a lambda expression to filter the results.</span></span> <span data-ttu-id="b213d-112">Hiçbir koşul sağlanırsa, tüm tablo döndürülür.</span><span class="sxs-lookup"><span data-stu-id="b213d-112">If no predicate is provided, the entire table is returned.</span></span> <span data-ttu-id="b213d-113">Aşağıdaki tabloda özellik ve dönüş değerleri etkinliğinin ayrıntıları.</span><span class="sxs-lookup"><span data-stu-id="b213d-113">The following table details the property and return values for the activity.</span></span>  
  
|<span data-ttu-id="b213d-114">Özellik ya da dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="b213d-114">Property or Return Value</span></span>|<span data-ttu-id="b213d-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b213d-115">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="b213d-116">`Collection` Özelliği</span><span class="sxs-lookup"><span data-stu-id="b213d-116">`Collection` property</span></span>|<span data-ttu-id="b213d-117">Kaynak koleksiyonu belirtir. gerekli bir özellik.</span><span class="sxs-lookup"><span data-stu-id="b213d-117">A required property that specifies the source collection.</span></span>|  
|<span data-ttu-id="b213d-118">`Predicate` Özelliği</span><span class="sxs-lookup"><span data-stu-id="b213d-118">`Predicate` property</span></span>|<span data-ttu-id="b213d-119">Filtre koleksiyonu için bir lambda ifadesinin biçiminde belirtir. gerekli bir özellik.</span><span class="sxs-lookup"><span data-stu-id="b213d-119">A required property that specifies the filter for the collection in the form of a lambda expression.</span></span>|  
|<span data-ttu-id="b213d-120">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b213d-120">Return Value</span></span>|<span data-ttu-id="b213d-121">Filtrelenmiş koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="b213d-121">The filtered collection.</span></span>|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a><span data-ttu-id="b213d-122">Özel Etkinlik kullanan kod örneği</span><span class="sxs-lookup"><span data-stu-id="b213d-122">Code Sample that uses the Custom Activity</span></span>  
 <span data-ttu-id="b213d-123">Aşağıdaki kod örneğinde `FindInSqlTable` adlı bir SQL Server tablodaki tüm satırları bulmak için özel etkinlik `Employee` burada `Role` sütun eşittir `SDE`.</span><span class="sxs-lookup"><span data-stu-id="b213d-123">The following code example uses the `FindInSqlTable` custom activity to find all rows in a SQL Server table named `Employee` where the `Role` column is equal to `SDE`.</span></span>  
  
```csharp  
new FindInSqlTable<Employee>   
{  
    ConnectionString = @"Data Source=.\SQLExpress;Initial Catalog=LinqToSqlSample;Integrated Security=True",                          
    Predicate = new LambdaValue<Func<Employee, bool>>(c => new Func<Employee, bool>(emp => emp.Role.Equals("SDE"))),  
    Result = new OutArgument<IList<Employee>>(employees)  
},  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="b213d-124">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="b213d-124">To use this sample</span></span>  
  
1.  <span data-ttu-id="b213d-125">Bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="b213d-125">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="b213d-126">Bu örnek içeren klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="b213d-126">Navigate to the folder that contains this sample.</span></span>  
  
3.  <span data-ttu-id="b213d-127">Setup.cmd komut dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b213d-127">Run the Setup.cmd command file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b213d-128">Setup.cmd betik, yerel makinenizde SQL Server Express örnek veritabanını yüklemek çalışır.</span><span class="sxs-lookup"><span data-stu-id="b213d-128">The Setup.cmd script attempts to install the sample database in your local machine SQL Server Express.</span></span> <span data-ttu-id="b213d-129">Diğer SQL server örneği'nde yüklemek istiyorsanız, Setup.cmd düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="b213d-129">If you want to install it in other SQL server instance, edit Setup.cmd.</span></span>  
  
     <span data-ttu-id="b213d-130">Setup.cmd komut aşağıdaki eylemleri yapar.:</span><span class="sxs-lookup"><span data-stu-id="b213d-130">The Setup.cmd script does the following actions.:</span></span>  
  
    -   <span data-ttu-id="b213d-131">LinqToSqlSample adlı bir veritabanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b213d-131">Creates a database called LinqToSqlSample.</span></span>  
  
    -   <span data-ttu-id="b213d-132">Roller bir tablo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b213d-132">Creates a Roles table.</span></span>  
  
    -   <span data-ttu-id="b213d-133">Çalışanlar bir tablo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b213d-133">Creates an Employees table.</span></span>  
  
    -   <span data-ttu-id="b213d-134">3 kayıtları rolleri tabloya ekler.</span><span class="sxs-lookup"><span data-stu-id="b213d-134">Inserts 3 records into the Roles table.</span></span>  
  
    -   <span data-ttu-id="b213d-135">12 kayıtları çalışanlar tabloya ekler.</span><span class="sxs-lookup"><span data-stu-id="b213d-135">Inserts 12 records into the Employees table.</span></span>  
  
4.  <span data-ttu-id="b213d-136">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], LinqToSQL.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="b213d-136">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the LinqToSQL.sln solution file.</span></span>  
  
5.  <span data-ttu-id="b213d-137">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="b213d-137">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
6.  <span data-ttu-id="b213d-138">Çözümü çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b213d-138">To run the solution, press F5.</span></span>  
  
#### <a name="to-uninstall-the-linqtosql-sample-database"></a><span data-ttu-id="b213d-139">LinqToSql örnek veritabanını kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="b213d-139">To uninstall the LinqToSql sample database</span></span>  
  
1.  <span data-ttu-id="b213d-140">Bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="b213d-140">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="b213d-141">Bu örnek içeren klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="b213d-141">Navigate to the folder that contains this sample.</span></span>  
  
3.  <span data-ttu-id="b213d-142">Cleanup.cmd komut dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b213d-142">Run the Cleanup.cmd command file.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b213d-143">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="b213d-143">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b213d-144">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b213d-144">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b213d-145">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="b213d-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b213d-146">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b213d-146">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Liiinq\LinqToSql`  
  
## <a name="see-also"></a><span data-ttu-id="b213d-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b213d-147">See Also</span></span>  
 [<span data-ttu-id="b213d-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b213d-148">LINQ to SQL</span></span>](https://go.microsoft.com/fwlink/?LinkId=150376)  
 [<span data-ttu-id="b213d-149">Başlarken (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="b213d-149">Getting Started (LINQ to SQL)</span></span>](https://go.microsoft.com/fwlink/?LinkId=150377)
