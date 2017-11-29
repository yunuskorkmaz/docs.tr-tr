---
title: "LINQ-SQL örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f39db9e-0e62-42c9-8c98-bb8b54cec98c
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6c05520dccdbf0677569d7fc64f55795e0ddb79b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="linq-to-sql-sample"></a><span data-ttu-id="7af2f-102">LINQ-SQL örneği</span><span class="sxs-lookup"><span data-stu-id="7af2f-102">LINQ to SQL Sample</span></span>
<span data-ttu-id="7af2f-103">Bu örnek, SQL Server veritabanlarını tablolardan SQL sorgu varlıklara LINQ kullanmak için bir etkinlik oluşturmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7af2f-103">This sample demonstrates how to create an activity to use LINQ to SQL query entities from tables in SQL Server databases.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7af2f-104">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Örnekleri zaten yüklenmiş olabilir, makinenizde.</span><span class="sxs-lookup"><span data-stu-id="7af2f-104">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] samples may already be installed on your machine.</span></span> <span data-ttu-id="7af2f-105">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7af2f-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\Samples\WCFWFCardspace`  
>   
>  <span data-ttu-id="7af2f-106">Bu dizin mevcut değilse, bu sayfanın üstündeki örnek bağlantıya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7af2f-106">If this directory does not exist, click the download sample link at the top of this page.</span></span> <span data-ttu-id="7af2f-107">Bu bağlantıyı indirir ve tüm yükler Not [!INCLUDE[wf1](../../../../includes/wf1-md.md)], [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], ve [!INCLUDE[infocard](../../../../includes/infocard-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="7af2f-107">Note that this link downloads and installs all of the [!INCLUDE[wf1](../../../../includes/wf1-md.md)], [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], and [!INCLUDE[infocard](../../../../includes/infocard-md.md)] samples.</span></span> <span data-ttu-id="7af2f-108">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="7af2f-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\Samples\WCFWFCardSpace\WF\Scenario\ActivityLibrary\Linq\LinqToSql`  
  
## <a name="activity-details-for-findinsqltable"></a><span data-ttu-id="7af2f-109">FindInSqlTable etkinliği ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="7af2f-109">Activity details for FindInSqlTable</span></span>  
 <span data-ttu-id="7af2f-110">Bu etkinlik, kullanıcıların LINQ-SQL kullanarak bir veritabanındaki tablolarda bulunan sorgu varlıklara sağlar.</span><span class="sxs-lookup"><span data-stu-id="7af2f-110">This activity allows users to query entities from tables in a database using LINQ to SQL.</span></span> <span data-ttu-id="7af2f-111">Etkinlik kullanıcılarının biçiminde sonuçlara filtre uygulamak için bir lambda ifadesi bir LINQ koşul da sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="7af2f-111">Users of the activity can also provide a LINQ predicate in the form of a lambda expression to filter the results.</span></span> <span data-ttu-id="7af2f-112">Hiçbir koşulu sağlanırsa, tüm tablo döndürülür.</span><span class="sxs-lookup"><span data-stu-id="7af2f-112">If no predicate is provided, the entire table is returned.</span></span> <span data-ttu-id="7af2f-113">Aşağıdaki tabloda özellik ve dönüş değerleri etkinliğinin ayrıntılarını verir.</span><span class="sxs-lookup"><span data-stu-id="7af2f-113">The following table details the property and return values for the activity.</span></span>  
  
|<span data-ttu-id="7af2f-114">Özellik veya dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="7af2f-114">Property or Return Value</span></span>|<span data-ttu-id="7af2f-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7af2f-115">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="7af2f-116">`Collection`özelliği</span><span class="sxs-lookup"><span data-stu-id="7af2f-116">`Collection` property</span></span>|<span data-ttu-id="7af2f-117">Kaynak koleksiyonu belirten gerekli bir özellik.</span><span class="sxs-lookup"><span data-stu-id="7af2f-117">A required property that specifies the source collection.</span></span>|  
|<span data-ttu-id="7af2f-118">`Predicate`özelliği</span><span class="sxs-lookup"><span data-stu-id="7af2f-118">`Predicate` property</span></span>|<span data-ttu-id="7af2f-119">Filtre koleksiyonu için bir lambda ifadesi biçiminde belirtir gerekli bir özellik.</span><span class="sxs-lookup"><span data-stu-id="7af2f-119">A required property that specifies the filter for the collection in the form of a lambda expression.</span></span>|  
|<span data-ttu-id="7af2f-120">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7af2f-120">Return Value</span></span>|<span data-ttu-id="7af2f-121">Filtrelenmiş koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="7af2f-121">The filtered collection.</span></span>|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a><span data-ttu-id="7af2f-122">Özel Etkinlik kullanan örnek kod</span><span class="sxs-lookup"><span data-stu-id="7af2f-122">Code Sample that uses the Custom Activity</span></span>  
 <span data-ttu-id="7af2f-123">Aşağıdaki kod örneğinde `FindInSqlTable` adlı bir SQL Server tablodaki tüm satırları bulmak için özel etkinlik `Employee` nerede `Role` sütun eşittir `SDE`.</span><span class="sxs-lookup"><span data-stu-id="7af2f-123">The following code example uses the `FindInSqlTable` custom activity to find all rows in a SQL Server table named `Employee` where the `Role` column is equal to `SDE`.</span></span>  
  
```csharp  
new FindInSqlTable<Employee>   
{  
    ConnectionString = @"Data Source=.\SQLExpress;Initial Catalog=LinqToSqlSample;Integrated Security=True",                          
    Predicate = new LambdaValue<Func<Employee, bool>>(c => new Func<Employee, bool>(emp => emp.Role.Equals("SDE"))),  
    Result = new OutArgument<IList<Employee>>(employees)  
},  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="7af2f-124">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="7af2f-124">To use this sample</span></span>  
  
1.  <span data-ttu-id="7af2f-125">Bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="7af2f-125">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="7af2f-126">Bu örnek içeren klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="7af2f-126">Navigate to the folder that contains this sample.</span></span>  
  
3.  <span data-ttu-id="7af2f-127">Setup.cmd komut dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7af2f-127">Run the Setup.cmd command file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7af2f-128">Yerel makinenizde SQL Server Express örnek veritabanını yüklemek Setup.cmd betik çalışır.</span><span class="sxs-lookup"><span data-stu-id="7af2f-128">The Setup.cmd script attempts to install the sample database in your local machine SQL Server Express.</span></span> <span data-ttu-id="7af2f-129">Diğer SQL server örneği yüklemek istiyorsanız, Setup.cmd düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="7af2f-129">If you want to install it in other SQL server instance, edit Setup.cmd.</span></span>  
  
     <span data-ttu-id="7af2f-130">Setup.cmd komut dosyası aşağıdaki eylemleri gerçekleştirir.:</span><span class="sxs-lookup"><span data-stu-id="7af2f-130">The Setup.cmd script does the following actions.:</span></span>  
  
    -   <span data-ttu-id="7af2f-131">LinqToSqlSample adlı bir veritabanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7af2f-131">Creates a database called LinqToSqlSample.</span></span>  
  
    -   <span data-ttu-id="7af2f-132">Rolleri bir tablo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7af2f-132">Creates a Roles table.</span></span>  
  
    -   <span data-ttu-id="7af2f-133">Çalışanlar adında bir tablo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7af2f-133">Creates an Employees table.</span></span>  
  
    -   <span data-ttu-id="7af2f-134">3 kayıtları rolleri tabloya ekler.</span><span class="sxs-lookup"><span data-stu-id="7af2f-134">Inserts 3 records into the Roles table.</span></span>  
  
    -   <span data-ttu-id="7af2f-135">12 kayıtları çalışanların tabloya ekler.</span><span class="sxs-lookup"><span data-stu-id="7af2f-135">Inserts 12 records into the Employees table.</span></span>  
  
4.  <span data-ttu-id="7af2f-136">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], LinqToSQL.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="7af2f-136">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the LinqToSQL.sln solution file.</span></span>  
  
5.  <span data-ttu-id="7af2f-137">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7af2f-137">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
6.  <span data-ttu-id="7af2f-138">Çözümü çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7af2f-138">To run the solution, press F5.</span></span>  
  
#### <a name="to-uninstall-the-linqtosql-sample-database"></a><span data-ttu-id="7af2f-139">LinqToSql örnek veritabanını kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="7af2f-139">To uninstall the LinqToSql sample database</span></span>  
  
1.  <span data-ttu-id="7af2f-140">Bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="7af2f-140">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="7af2f-141">Bu örnek içeren klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="7af2f-141">Navigate to the folder that contains this sample.</span></span>  
  
3.  <span data-ttu-id="7af2f-142">Cleanup.cmd komut dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7af2f-142">Run the Cleanup.cmd command file.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7af2f-143">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="7af2f-143">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7af2f-144">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7af2f-144">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7af2f-145">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="7af2f-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7af2f-146">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="7af2f-146">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Liiinq\LinqToSql`  
  
## <a name="see-also"></a><span data-ttu-id="7af2f-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7af2f-147">See Also</span></span>  
 [<span data-ttu-id="7af2f-148">LINQ-SQL</span><span class="sxs-lookup"><span data-stu-id="7af2f-148">LINQ to SQL</span></span>](http://go.microsoft.com/fwlink/?LinkId=150376)  
 [<span data-ttu-id="7af2f-149">Başlarken (LINQ-SQL)</span><span class="sxs-lookup"><span data-stu-id="7af2f-149">Getting Started (LINQ to SQL)</span></span>](http://go.microsoft.com/fwlink/?LinkId=150377)
