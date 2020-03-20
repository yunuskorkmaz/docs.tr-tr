---
title: SQL Server'ın Örneklerini Sıralama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
ms.openlocfilehash: a707df533216613e34d9f357c7b9e035f73b9561
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148692"
---
# <a name="enumerating-instances-of-sql-server-adonet"></a><span data-ttu-id="a7ce3-102">SQL Server (ADO.NET) Numaralandırma Örnekleri</span><span class="sxs-lookup"><span data-stu-id="a7ce3-102">Enumerating Instances of SQL Server (ADO.NET)</span></span>
<span data-ttu-id="a7ce3-103">SQL Server, uygulamaların geçerli ağ içinde SQL Server örneklerini bulmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="a7ce3-103">SQL Server permits applications to find SQL Server instances within the current network.</span></span> <span data-ttu-id="a7ce3-104">Sınıf, <xref:System.Data.Sql.SqlDataSourceEnumerator> bu bilgileri uygulama geliştiricisine açıklayarak <xref:System.Data.DataTable> görünür tüm sunucular hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7ce3-104">The <xref:System.Data.Sql.SqlDataSourceEnumerator> class exposes this information to the application developer, providing a <xref:System.Data.DataTable> containing information about all the visible servers.</span></span> <span data-ttu-id="a7ce3-105">Bu döndürülen tablo, ağda bulunan ve kullanıcı yeni bir bağlantı oluşturmaya çalıştığında sağlanan listeyle eşleşen sunucu örneklerinin bir listesini içerir ve **Bağlantı Özellikleri** iletişim kutusundaki tüm kullanılabilir sunucuları içeren açılır listeyi genişletir.</span><span class="sxs-lookup"><span data-stu-id="a7ce3-105">This returned table contains a list of server instances available on the network that matches the list provided when a user attempts to create a new connection, and expands the drop-down list containing all the available servers on the **Connection Properties** dialog box.</span></span> <span data-ttu-id="a7ce3-106">Görüntülenen sonuçlar her zaman tam değildir.</span><span class="sxs-lookup"><span data-stu-id="a7ce3-106">The results displayed are not always complete.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a7ce3-107">Çoğu Windows hizmetinde olduğu gibi, SQL Browser hizmetini mümkün olan en az ayrıcalıkla çalıştırmak en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="a7ce3-107">As with most Windows services, it is best to run the SQL Browser service with the least possible privileges.</span></span> <span data-ttu-id="a7ce3-108">SQL Browser hizmeti hakkında daha fazla bilgi ve davranışını nasıl yönetirebildiğini öğrenmek için SQL Server Books Online'a bakın.</span><span class="sxs-lookup"><span data-stu-id="a7ce3-108">See SQL Server Books Online for more information on the SQL Browser service, and how to manage its behavior.</span></span>  
  
## <a name="retrieving-an-enumerator-instance"></a><span data-ttu-id="a7ce3-109">Bir Umerator Örneği Alma</span><span class="sxs-lookup"><span data-stu-id="a7ce3-109">Retrieving an Enumerator Instance</span></span>  
 <span data-ttu-id="a7ce3-110">Kullanılabilir SQL Server örnekleri hakkında bilgi içeren tabloyu almak için, paylaşılan/statik <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> özelliği kullanarak önce bir bir yer umeratör almanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="a7ce3-110">In order to retrieve the table containing information about the available SQL Server instances, you must first retrieve an enumerator, using the shared/static <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> property:</span></span>  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 <span data-ttu-id="a7ce3-111">Statik örneği aldıktan sonra, kullanılabilir sunucular <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> hakkında <xref:System.Data.DataTable> bilgi sağlayan yöntemi arayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a7ce3-111">Once you have retrieved the static instance, you can call the <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> method, which returns a <xref:System.Data.DataTable> containing information about the available servers:</span></span>  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 <span data-ttu-id="a7ce3-112">Yöntem çağrısından döndürülen tablo, tümü değerleri içeren `string` aşağıdaki sütunları içerir:</span><span class="sxs-lookup"><span data-stu-id="a7ce3-112">The table returned from the method call contains the following columns, all of which contain `string` values:</span></span>  
  
|<span data-ttu-id="a7ce3-113">Sütun</span><span class="sxs-lookup"><span data-stu-id="a7ce3-113">Column</span></span>|<span data-ttu-id="a7ce3-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7ce3-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a7ce3-115">**Sunucuadı**</span><span class="sxs-lookup"><span data-stu-id="a7ce3-115">**ServerName**</span></span>|<span data-ttu-id="a7ce3-116">Sunucunun adı.</span><span class="sxs-lookup"><span data-stu-id="a7ce3-116">Name of the server.</span></span>|  
|<span data-ttu-id="a7ce3-117">**Örnekadı**</span><span class="sxs-lookup"><span data-stu-id="a7ce3-117">**InstanceName**</span></span>|<span data-ttu-id="a7ce3-118">Sunucu örneğinin adı.</span><span class="sxs-lookup"><span data-stu-id="a7ce3-118">Name of the server instance.</span></span> <span data-ttu-id="a7ce3-119">Sunucu varsayılan örnek olarak çalışıyorsa boş.</span><span class="sxs-lookup"><span data-stu-id="a7ce3-119">Blank if the server is running as the default instance.</span></span>|  
|<span data-ttu-id="a7ce3-120">**ısclustered**</span><span class="sxs-lookup"><span data-stu-id="a7ce3-120">**IsClustered**</span></span>|<span data-ttu-id="a7ce3-121">Sunucunun kümenin bir parçası olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a7ce3-121">Indicates whether the server is part of a cluster.</span></span>|  
|<span data-ttu-id="a7ce3-122">**Sürüm**</span><span class="sxs-lookup"><span data-stu-id="a7ce3-122">**Version**</span></span>|<span data-ttu-id="a7ce3-123">Sunucunun sürümü.</span><span class="sxs-lookup"><span data-stu-id="a7ce3-123">Version of the server.</span></span> <span data-ttu-id="a7ce3-124">Örnek:</span><span class="sxs-lookup"><span data-stu-id="a7ce3-124">For example:</span></span><br /><br /> <span data-ttu-id="a7ce3-125">- 9.00.x (SQL Server 2005)</span><span class="sxs-lookup"><span data-stu-id="a7ce3-125">-   9.00.x (SQL Server 2005)</span></span><br /><span data-ttu-id="a7ce3-126">- 10.0.xx (SQL Server 2008)</span><span class="sxs-lookup"><span data-stu-id="a7ce3-126">-   10.0.xx (SQL Server 2008)</span></span><br /><span data-ttu-id="a7ce3-127">- 10.50.x (SQL Server 2008 R2)</span><span class="sxs-lookup"><span data-stu-id="a7ce3-127">-   10.50.x (SQL Server 2008 R2)</span></span><br /><span data-ttu-id="a7ce3-128">- 11.0.xx (SQL Server 2012)</span><span class="sxs-lookup"><span data-stu-id="a7ce3-128">-   11.0.xx (SQL Server 2012)</span></span>|  
  
## <a name="enumeration-limitations"></a><span data-ttu-id="a7ce3-129">Numaralandırma Sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="a7ce3-129">Enumeration Limitations</span></span>  
 <span data-ttu-id="a7ce3-130">Kullanılabilir sunucuların tümü listelenebilir veya listelenmemiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="a7ce3-130">All of the available servers may or may not be listed.</span></span> <span data-ttu-id="a7ce3-131">Liste, zaman ekmeleri ve ağ trafiği gibi etkenlere bağlı olarak değişebilir.</span><span class="sxs-lookup"><span data-stu-id="a7ce3-131">The list can vary depending on factors such as timeouts and network traffic.</span></span> <span data-ttu-id="a7ce3-132">Bu, listenin art arda iki çağrıda farklı olmasını sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a7ce3-132">This can cause the list to be different on two consecutive calls.</span></span> <span data-ttu-id="a7ce3-133">Yalnızca aynı ağdaki sunucular listelenir.</span><span class="sxs-lookup"><span data-stu-id="a7ce3-133">Only servers on the same network will be listed.</span></span> <span data-ttu-id="a7ce3-134">Yayın paketleri genellikle yönlendiriciler arasında geçiş yapmaz, bu nedenle listelenen bir sunucu göremeyebilirsiniz, ancak aramalar arasında kararlı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a7ce3-134">Broadcast packets typically won't traverse routers, which is why you may not see a server listed, but it will be stable across calls.</span></span>  
  
 <span data-ttu-id="a7ce3-135">Listelenen sunucular, sürüm ve sürüm `IsClustered` gibi ek bilgilere sahip olabilir veya olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="a7ce3-135">Listed servers may or may not have additional information such as `IsClustered` and version.</span></span> <span data-ttu-id="a7ce3-136">Bu, listenin nasıl elde edildiğine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a7ce3-136">This is dependent on how the list was obtained.</span></span> <span data-ttu-id="a7ce3-137">SQL Server tarayıcı hizmeti nde listelenen sunucular, yalnızca adı listeleyen Windows altyapısında bulunanlardan daha fazla ayrıntıya sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a7ce3-137">Servers listed through the SQL Server browser service will have more details than those found through the Windows infrastructure, which will list only the name.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a7ce3-138">Sunucu numaralandırma yalnızca tam güven içinde çalışırken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a7ce3-138">Server enumeration is only available when running in full-trust.</span></span> <span data-ttu-id="a7ce3-139"><xref:System.Data.SqlClient.SqlClientPermission> Kısmen güvenilen bir ortamda çalışan derlemeler, Kod Erişim Güvenliği (CAS) iznine sahip olsalar bile bu derlemeyi kullanamaz.</span><span class="sxs-lookup"><span data-stu-id="a7ce3-139">Assemblies running in a partially-trusted environment will not be able to use it, even if they have the <xref:System.Data.SqlClient.SqlClientPermission> Code Access Security (CAS) permission.</span></span>  
  
 <span data-ttu-id="a7ce3-140">SQL Server, SQL <xref:System.Data.Sql.SqlDataSourceEnumerator> Browser adlı harici bir Windows hizmetinin kullanımı yoluyla bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7ce3-140">SQL Server provides information for the <xref:System.Data.Sql.SqlDataSourceEnumerator> through the use of an external Windows service named SQL Browser.</span></span> <span data-ttu-id="a7ce3-141">Bu hizmet varsayılan olarak etkinleştirilir, ancak yöneticiler sunucu örneğini bu sınıf için görünmez hale getirerek bu hizmeti kapatabilir veya devre dışı bırakabilir.</span><span class="sxs-lookup"><span data-stu-id="a7ce3-141">This service is enabled by default, but administrators may turn it off or disable it, making the server instance invisible to this class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7ce3-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="a7ce3-142">Example</span></span>  
 <span data-ttu-id="a7ce3-143">Aşağıdaki konsol uygulaması, görünen TÜM SQL Server örnekleri hakkında bilgi alır ve konsol penceresindeki bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a7ce3-143">The following console application retrieves information about all of the visible SQL Server instances and displays the information in the console window.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a7ce3-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7ce3-144">See also</span></span>

- [<span data-ttu-id="a7ce3-145">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a7ce3-145">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="a7ce3-146">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a7ce3-146">ADO.NET Overview</span></span>](../ado-net-overview.md)
