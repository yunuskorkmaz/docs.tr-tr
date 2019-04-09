---
title: SQL Server (ADO.NET) Numaralandırma Örnekleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
ms.openlocfilehash: a723679fe18352e115df78af72975097dc28b617
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162861"
---
# <a name="enumerating-instances-of-sql-server-adonet"></a><span data-ttu-id="68ecf-102">SQL Server (ADO.NET) Numaralandırma Örnekleri</span><span class="sxs-lookup"><span data-stu-id="68ecf-102">Enumerating Instances of SQL Server (ADO.NET)</span></span>
<span data-ttu-id="68ecf-103">SQL Server, geçerli ağ içinde SQL Server örneklerini bulmak için uygulamaların izin verir.</span><span class="sxs-lookup"><span data-stu-id="68ecf-103">SQL Server permits applications to find SQL Server instances within the current network.</span></span> <span data-ttu-id="68ecf-104"><xref:System.Data.Sql.SqlDataSourceEnumerator> Sınıfı sağlayarak uygulama geliştiricisi, bu bilgileri sunan bir <xref:System.Data.DataTable> görünür olan tüm sunucular hakkında bilgiler içeren.</span><span class="sxs-lookup"><span data-stu-id="68ecf-104">The <xref:System.Data.Sql.SqlDataSourceEnumerator> class exposes this information to the application developer, providing a <xref:System.Data.DataTable> containing information about all the visible servers.</span></span> <span data-ttu-id="68ecf-105">Bu tablo, ağ üzerinde yer alan bir kullanıcı yeni bir bağlantı oluşturmak çalıştığında sağlanan listesiyle eşleşen ve üzerinde kullanılabilen tüm sunucuları içeren aşağı açılan liste genişletir kullanılabilir sunucu örneklerinin bir listesini içeren döndürülen **bağlantı Özellikleri** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="68ecf-105">This returned table contains a list of server instances available on the network that matches the list provided when a user attempts to create a new connection, and expands the drop-down list containing all the available servers on the **Connection Properties** dialog box.</span></span> <span data-ttu-id="68ecf-106">Görüntülenen sonuçlar her zaman eksiksiz değildir.</span><span class="sxs-lookup"><span data-stu-id="68ecf-106">The results displayed are not always complete.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68ecf-107">Olarak çoğu Windows hizmetlerle olabildiğince az ayrıcalıklarıyla SQL Browser hizmeti çalıştırmak en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="68ecf-107">As with most Windows services, it is best to run the SQL Browser service with the least possible privileges.</span></span> <span data-ttu-id="68ecf-108">SQL Browser hizmeti ve davranışını yönetmek nasıl daha fazla bilgi için SQL Server Books Online'a bakın.</span><span class="sxs-lookup"><span data-stu-id="68ecf-108">See SQL Server Books Online for more information on the SQL Browser service, and how to manage its behavior.</span></span>  
  
## <a name="retrieving-an-enumerator-instance"></a><span data-ttu-id="68ecf-109">Numaralandırıcı örnek alıyor</span><span class="sxs-lookup"><span data-stu-id="68ecf-109">Retrieving an Enumerator Instance</span></span>  
 <span data-ttu-id="68ecf-110">Kullanılabilir SQL Server örnekleri hakkında bilgi içeren tablo almak için ilk paylaşılan /'using static Numaralandırıcı alınması gerekir <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> özelliği:</span><span class="sxs-lookup"><span data-stu-id="68ecf-110">In order to retrieve the table containing information about the available SQL Server instances, you must first retrieve an enumerator, using the shared/static <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> property:</span></span>  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =   
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 <span data-ttu-id="68ecf-111">Statik örneği aldıktan sonra çağırabilirsiniz <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> döndüren yöntemi bir <xref:System.Data.DataTable> kullanılabilir sunucular hakkında bilgiler içeren:</span><span class="sxs-lookup"><span data-stu-id="68ecf-111">Once you have retrieved the static instance, you can call the <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> method, which returns a <xref:System.Data.DataTable> containing information about the available servers:</span></span>  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 <span data-ttu-id="68ecf-112">Yöntem çağrısından döndürülen tablo tümünü içeren şu sütunları içeren `string` değerleri:</span><span class="sxs-lookup"><span data-stu-id="68ecf-112">The table returned from the method call contains the following columns, all of which contain `string` values:</span></span>  
  
|<span data-ttu-id="68ecf-113">Sütun</span><span class="sxs-lookup"><span data-stu-id="68ecf-113">Column</span></span>|<span data-ttu-id="68ecf-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68ecf-114">Description</span></span>|  
|------------|-----------------|  
|**<span data-ttu-id="68ecf-115">ServerName</span><span class="sxs-lookup"><span data-stu-id="68ecf-115">ServerName</span></span>**|<span data-ttu-id="68ecf-116">Sunucusunun adı.</span><span class="sxs-lookup"><span data-stu-id="68ecf-116">Name of the server.</span></span>|  
|**<span data-ttu-id="68ecf-117">InstanceName</span><span class="sxs-lookup"><span data-stu-id="68ecf-117">InstanceName</span></span>**|<span data-ttu-id="68ecf-118">Sunucu örneğinin adı.</span><span class="sxs-lookup"><span data-stu-id="68ecf-118">Name of the server instance.</span></span> <span data-ttu-id="68ecf-119">Sunucu varsayılan örnek olarak çalışıyorsa boş.</span><span class="sxs-lookup"><span data-stu-id="68ecf-119">Blank if the server is running as the default instance.</span></span>|  
|**<span data-ttu-id="68ecf-120">IsClustered</span><span class="sxs-lookup"><span data-stu-id="68ecf-120">IsClustered</span></span>**|<span data-ttu-id="68ecf-121">Sunucu bir kümenin parçası olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="68ecf-121">Indicates whether the server is part of a cluster.</span></span>|  
|**<span data-ttu-id="68ecf-122">Sürüm</span><span class="sxs-lookup"><span data-stu-id="68ecf-122">Version</span></span>**|<span data-ttu-id="68ecf-123">Sunucu sürümü.</span><span class="sxs-lookup"><span data-stu-id="68ecf-123">Version of the server.</span></span> <span data-ttu-id="68ecf-124">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="68ecf-124">For example:</span></span><br /><br /> <span data-ttu-id="68ecf-125">-9.00.x ([!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)])</span><span class="sxs-lookup"><span data-stu-id="68ecf-125">-   9.00.x ([!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)])</span></span><br /><span data-ttu-id="68ecf-126">-   10.0.xx ([!INCLUDE[ssKatmai](../../../../../includes/sskatmai-md.md)])</span><span class="sxs-lookup"><span data-stu-id="68ecf-126">-   10.0.xx ([!INCLUDE[ssKatmai](../../../../../includes/sskatmai-md.md)])</span></span><br /><span data-ttu-id="68ecf-127">-   10.50.x ([!INCLUDE[ssKilimanjaro](../../../../../includes/sskilimanjaro-md.md)])</span><span class="sxs-lookup"><span data-stu-id="68ecf-127">-   10.50.x ([!INCLUDE[ssKilimanjaro](../../../../../includes/sskilimanjaro-md.md)])</span></span><br /><span data-ttu-id="68ecf-128">-   11.0.xx (SQL Server 2012)</span><span class="sxs-lookup"><span data-stu-id="68ecf-128">-   11.0.xx (SQL Server 2012)</span></span>|  
  
## <a name="enumeration-limitations"></a><span data-ttu-id="68ecf-129">Sabit listesi sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="68ecf-129">Enumeration Limitations</span></span>  
 <span data-ttu-id="68ecf-130">Tüm kullanılabilir sunucular olabilir ya da listelenmez.</span><span class="sxs-lookup"><span data-stu-id="68ecf-130">All of the available servers may or may not be listed.</span></span> <span data-ttu-id="68ecf-131">Liste, zaman aşımları ve ağ trafiği gibi faktörlere bağlı olarak değişebilir.</span><span class="sxs-lookup"><span data-stu-id="68ecf-131">The list can vary depending on factors such as timeouts and network traffic.</span></span> <span data-ttu-id="68ecf-132">Bu iki ardışık çağrılarda farklı olacak şekilde liste neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="68ecf-132">This can cause the list to be different on two consecutive calls.</span></span> <span data-ttu-id="68ecf-133">Yalnızca aynı ağ üzerinde sunucuları listelenir.</span><span class="sxs-lookup"><span data-stu-id="68ecf-133">Only servers on the same network will be listed.</span></span> <span data-ttu-id="68ecf-134">Yayın paketleri genellikle yönlendiriciler, listelenen bir sunucu göremeyebilirsiniz neden olduğu geçiş olmaz ancak çağrıları arasında tutarlı olur.</span><span class="sxs-lookup"><span data-stu-id="68ecf-134">Broadcast packets typically won't traverse routers, which is why you may not see a server listed, but it will be stable across calls.</span></span>  
  
 <span data-ttu-id="68ecf-135">Listelenen sunucuları gibi ek bilgi olmayabilir veya `IsClustered` ve sürüm.</span><span class="sxs-lookup"><span data-stu-id="68ecf-135">Listed servers may or may not have additional information such as `IsClustered` and version.</span></span> <span data-ttu-id="68ecf-136">Bu listenin nasıl edinilen bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="68ecf-136">This is dependent on how the list was obtained.</span></span> <span data-ttu-id="68ecf-137">SQL Server browser hizmeti listelenen sunucuları yalnızca adını listeler Windows altyapısı aracılığıyla bulunan olandan daha fazla ayrıntı sahip olur.</span><span class="sxs-lookup"><span data-stu-id="68ecf-137">Servers listed through the SQL Server browser service will have more details than those found through the Windows infrastructure, which will list only the name.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68ecf-138">Sunucu sabit listesi, yalnızca tam güvende çalıştırıldığında, kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="68ecf-138">Server enumeration is only available when running in full-trust.</span></span> <span data-ttu-id="68ecf-139">Sahip oldukları bile kısmen güvenilen bir ortamda çalışan derlemeler, kullanmanız mümkün olmayacak <xref:System.Data.SqlClient.SqlClientPermission> kod erişim güvenliği (CAS) iznini.</span><span class="sxs-lookup"><span data-stu-id="68ecf-139">Assemblies running in a partially-trusted environment will not be able to use it, even if they have the <xref:System.Data.SqlClient.SqlClientPermission> Code Access Security (CAS) permission.</span></span>  
  
 <span data-ttu-id="68ecf-140">SQL Server için bilgileri sağlar <xref:System.Data.Sql.SqlDataSourceEnumerator> SQL Browser adlı bir dış Windows hizmet kullanımı.</span><span class="sxs-lookup"><span data-stu-id="68ecf-140">SQL Server provides information for the <xref:System.Data.Sql.SqlDataSourceEnumerator> through the use of an external Windows service named SQL Browser.</span></span> <span data-ttu-id="68ecf-141">Bu hizmet, varsayılan olarak etkindir, ancak yöneticilerin kapatmak veya, sunucu örneği için bu sınıf görünmez yapma devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="68ecf-141">This service is enabled by default, but administrators may turn it off or disable it, making the server instance invisible to this class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68ecf-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="68ecf-142">Example</span></span>  
 <span data-ttu-id="68ecf-143">Aşağıdaki konsol uygulamasında tüm görünür SQL Server örnekleri hakkında bilgi alır ve bilgileri konsol penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="68ecf-143">The following console application retrieves information about all of the visible SQL Server instances and displays the information in the console window.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="68ecf-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68ecf-144">See also</span></span>

- [<span data-ttu-id="68ecf-145">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="68ecf-145">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)
- [<span data-ttu-id="68ecf-146">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="68ecf-146">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
