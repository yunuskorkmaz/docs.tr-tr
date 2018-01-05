---
title: "SQL Server (ADO.NET) örneklerini numaralandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 679196a6cc21705c8cc07e373a928f3c77c6befb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="enumerating-instances-of-sql-server-adonet"></a><span data-ttu-id="dc790-102">SQL Server (ADO.NET) örneklerini numaralandırma</span><span class="sxs-lookup"><span data-stu-id="dc790-102">Enumerating Instances of SQL Server (ADO.NET)</span></span>
[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="dc790-103">bulunacak uygulamaları verir [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] geçerli ağ içindeki örnekleri.</span><span class="sxs-lookup"><span data-stu-id="dc790-103"> permits applications to find [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] instances within the current network.</span></span> <span data-ttu-id="dc790-104"><xref:System.Data.Sql.SqlDataSourceEnumerator> Sınıfı sağlayan uygulama geliştiricisi, bu bilgileri sunan bir <xref:System.Data.DataTable> görünür tüm sunucuları hakkında bilgi içeren.</span><span class="sxs-lookup"><span data-stu-id="dc790-104">The <xref:System.Data.Sql.SqlDataSourceEnumerator> class exposes this information to the application developer, providing a <xref:System.Data.DataTable> containing information about all the visible servers.</span></span> <span data-ttu-id="dc790-105">Bu tablo bir kullanıcı yeni bir bağlantı oluşturmak çalıştığında sağlanan listesiyle eşleşen ve üzerindeki tüm kullanılabilir sunuculara içeren aşağı açılır liste genişleten ağda kullanılabilir sunucu örneklerinin bir listesini içeren döndürülen **bağlantı Özellikler** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="dc790-105">This returned table contains a list of server instances available on the network that matches the list provided when a user attempts to create a new connection, and expands the drop-down list containing all the available servers on the **Connection Properties** dialog box.</span></span> <span data-ttu-id="dc790-106">Gösterilen sonuçları her zaman eksiksiz değildir.</span><span class="sxs-lookup"><span data-stu-id="dc790-106">The results displayed are not always complete.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc790-107">Olarak çoğu Windows Hizmetleri ile mümkün olan en küçük ayrıcalıklarıyla SQL Browser hizmeti çalıştırmak en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="dc790-107">As with most Windows services, it is best to run the SQL Browser service with the least possible privileges.</span></span> <span data-ttu-id="dc790-108">Bkz: [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] SQL Browser hizmeti hakkında daha fazla bilgi için Books Online'a ve davranışını yönetme.</span><span class="sxs-lookup"><span data-stu-id="dc790-108">See [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online for more information on the SQL Browser service, and how to manage its behavior.</span></span>  
  
## <a name="retrieving-an-enumerator-instance"></a><span data-ttu-id="dc790-109">Numaralandırıcı örnek alıyor</span><span class="sxs-lookup"><span data-stu-id="dc790-109">Retrieving an Enumerator Instance</span></span>  
 <span data-ttu-id="dc790-110">Kullanılabilir hakkında bilgi içeren tablo almak için [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] örnekleri, paylaşılan/statik kullanarak bir numaralandırıcı ilk almak gerekir <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> özelliği:</span><span class="sxs-lookup"><span data-stu-id="dc790-110">In order to retrieve the table containing information about the available [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] instances, you must first retrieve an enumerator, using the shared/static <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> property:</span></span>  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =   
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 <span data-ttu-id="dc790-111">Statik örnek aldıktan sonra çağırabilirsiniz <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> döndürür yöntemi bir <xref:System.Data.DataTable> kullanılabilir sunucuları hakkında bilgi içeren:</span><span class="sxs-lookup"><span data-stu-id="dc790-111">Once you have retrieved the static instance, you can call the <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> method, which returns a <xref:System.Data.DataTable> containing information about the available servers:</span></span>  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 <span data-ttu-id="dc790-112">Yöntemi çağrısından döndürülen tablosu da içeren şu sütunları içerir `string` değerler:</span><span class="sxs-lookup"><span data-stu-id="dc790-112">The table returned from the method call contains the following columns, all of which contain `string` values:</span></span>  
  
|<span data-ttu-id="dc790-113">Sütun</span><span class="sxs-lookup"><span data-stu-id="dc790-113">Column</span></span>|<span data-ttu-id="dc790-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dc790-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="dc790-115">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="dc790-115">**ServerName**</span></span>|<span data-ttu-id="dc790-116">Sunucunun adıdır.</span><span class="sxs-lookup"><span data-stu-id="dc790-116">Name of the server.</span></span>|  
|<span data-ttu-id="dc790-117">**InstanceName**</span><span class="sxs-lookup"><span data-stu-id="dc790-117">**InstanceName**</span></span>|<span data-ttu-id="dc790-118">Sunucu örneğinin adı.</span><span class="sxs-lookup"><span data-stu-id="dc790-118">Name of the server instance.</span></span> <span data-ttu-id="dc790-119">Sunucunun varsayılan örneği olarak çalışıyorsa, boş.</span><span class="sxs-lookup"><span data-stu-id="dc790-119">Blank if the server is running as the default instance.</span></span>|  
|<span data-ttu-id="dc790-120">**IsClustered**</span><span class="sxs-lookup"><span data-stu-id="dc790-120">**IsClustered**</span></span>|<span data-ttu-id="dc790-121">Sunucu bir kümenin parçası olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="dc790-121">Indicates whether the server is part of a cluster.</span></span>|  
|<span data-ttu-id="dc790-122">**Sürüm**</span><span class="sxs-lookup"><span data-stu-id="dc790-122">**Version**</span></span>|<span data-ttu-id="dc790-123">Sunucu sürümü.</span><span class="sxs-lookup"><span data-stu-id="dc790-123">Version of the server.</span></span> <span data-ttu-id="dc790-124">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="dc790-124">For example:</span></span><br /><br /> <span data-ttu-id="dc790-125">-9.00.x ([!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)])</span><span class="sxs-lookup"><span data-stu-id="dc790-125">-   9.00.x ([!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)])</span></span><br /><span data-ttu-id="dc790-126">-10.0.xx ([!INCLUDE[ssKatmai](../../../../../includes/sskatmai-md.md)])</span><span class="sxs-lookup"><span data-stu-id="dc790-126">-   10.0.xx ([!INCLUDE[ssKatmai](../../../../../includes/sskatmai-md.md)])</span></span><br /><span data-ttu-id="dc790-127">-10.50.x ([!INCLUDE[ssKilimanjaro](../../../../../includes/sskilimanjaro-md.md)])</span><span class="sxs-lookup"><span data-stu-id="dc790-127">-   10.50.x ([!INCLUDE[ssKilimanjaro](../../../../../includes/sskilimanjaro-md.md)])</span></span><br /><span data-ttu-id="dc790-128">-11.0.xx ([!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012)</span><span class="sxs-lookup"><span data-stu-id="dc790-128">-   11.0.xx ([!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012)</span></span>|  
  
## <a name="enumeration-limitations"></a><span data-ttu-id="dc790-129">Numaralandırma sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="dc790-129">Enumeration Limitations</span></span>  
 <span data-ttu-id="dc790-130">Tüm kullanılabilir sunuculara olabilir ya da listelenmez.</span><span class="sxs-lookup"><span data-stu-id="dc790-130">All of the available servers may or may not be listed.</span></span> <span data-ttu-id="dc790-131">Liste zaman aşımları ve ağ trafiğini gibi etkenlere bağlı olarak değişebilir.</span><span class="sxs-lookup"><span data-stu-id="dc790-131">The list can vary depending on factors such as timeouts and network traffic.</span></span> <span data-ttu-id="dc790-132">Bu listenin iki ardışık çağrılarını farklı olması neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="dc790-132">This can cause the list to be different on two consecutive calls.</span></span> <span data-ttu-id="dc790-133">Yalnızca aynı ağ üzerinde sunucuları listelenir.</span><span class="sxs-lookup"><span data-stu-id="dc790-133">Only servers on the same network will be listed.</span></span> <span data-ttu-id="dc790-134">Yayın paketleri genellikle yönlendiriciler, listelenen bir sunucu göremeyebilirsiniz neden olduğu çapraz olmaz ancak çağrıları arasında dengeli olur.</span><span class="sxs-lookup"><span data-stu-id="dc790-134">Broadcast packets typically won't traverse routers, which is why you may not see a server listed, but it will be stable across calls.</span></span>  
  
 <span data-ttu-id="dc790-135">Listelenen sunucuların olabilir veya ek bilgiler gibi olmayabilir `IsClustered` ve sürüm.</span><span class="sxs-lookup"><span data-stu-id="dc790-135">Listed servers may or may not have additional information such as `IsClustered` and version.</span></span> <span data-ttu-id="dc790-136">Bu listeyi nasıl edinilen bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="dc790-136">This is dependent on how the list was obtained.</span></span> <span data-ttu-id="dc790-137">Aracılığıyla listelenen sunucuları [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Tarayıcı hizmeti, yalnızca adını listeler Windows altyapısı bulunan olandan daha fazla ayrıntı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="dc790-137">Servers listed through the [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] browser service will have more details than those found through the Windows infrastructure, which will list only the name.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc790-138">Sunucu numaralandırma, yalnızca tam güvende çalıştırılırken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dc790-138">Server enumeration is only available when running in full-trust.</span></span> <span data-ttu-id="dc790-139">Kısmen güvenilen bir ortamda çalışan derlemeleri edemeyecek, kullanılacak sahip oldukları olsa bile <xref:System.Data.SqlClient.SqlClientPermission> kod erişim güvenliği (CAS) izni.</span><span class="sxs-lookup"><span data-stu-id="dc790-139">Assemblies running in a partially-trusted environment will not be able to use it, even if they have the <xref:System.Data.SqlClient.SqlClientPermission> Code Access Security (CAS) permission.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="dc790-140">için bilgiler sağlar <xref:System.Data.Sql.SqlDataSourceEnumerator> SQL Browser adlı bir dış Windows hizmeti kullanımı ile.</span><span class="sxs-lookup"><span data-stu-id="dc790-140"> provides information for the <xref:System.Data.Sql.SqlDataSourceEnumerator> through the use of an external Windows service named SQL Browser.</span></span> <span data-ttu-id="dc790-141">Bu hizmet varsayılan olarak etkindir, ancak yöneticilerin kapatın veya, sunucu örneği için bu sınıf görünmez yapma devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="dc790-141">This service is enabled by default, but administrators may turn it off or disable it, making the server instance invisible to this class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc790-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="dc790-142">Example</span></span>  
 <span data-ttu-id="dc790-143">Aşağıdaki konsol uygulaması görünür tüm ilgili bilgileri alır [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] örnekler ve bilgiler konsol penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="dc790-143">The following console application retrieves information about all of the visible [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] instances and displays the information in the console window.</span></span>  
  
```vb  
Imports System.Data.Sql  
  
Module Module1  
  Sub Main()  
    ' Retrieve the enumerator instance and then the data.  
    Dim instance As SqlDataSourceEnumerator = _  
     SqlDataSourceEnumerator.Instance  
    Dim table As System.Data.DataTable = instance.GetDataSources()  
  
    ' Display the contents of the table.  
    DisplayData(table)  
  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Sub  
  
  Private Sub DisplayData(ByVal table As DataTable)  
    For Each row As DataRow In table.Rows  
      For Each col As DataColumn In table.Columns  
        Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
      Next  
      Console.WriteLine("============================")  
    Next  
  End Sub  
End Module  
```  
  
```csharp  
using System.Data.Sql;  
  
class Program  
{  
  static void Main()  
  {  
    // Retrieve the enumerator instance and then the data.  
    SqlDataSourceEnumerator instance =  
      SqlDataSourceEnumerator.Instance;  
    System.Data.DataTable table = instance.GetDataSources();  
  
    // Display the contents of the table.  
    DisplayData(table);  
  
    Console.WriteLine("Press any key to continue.");  
    Console.ReadKey();  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
    foreach (System.Data.DataRow row in table.Rows)  
    {  
      foreach (System.Data.DataColumn col in table.Columns)  
      {  
        Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
      }  
      Console.WriteLine("============================");  
    }  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="dc790-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dc790-144">See Also</span></span>  
 [<span data-ttu-id="dc790-145">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="dc790-145">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="dc790-146">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="dc790-146">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
