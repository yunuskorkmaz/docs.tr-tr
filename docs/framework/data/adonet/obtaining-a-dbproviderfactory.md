---
title: Bir DbProviderFactory alma
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
ms.assetid: a16e4a4d-6a5b-45db-8635-19570e4572ae
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 379ec77c5a291ff0fcfa535b808f8976bb416d15
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="obtaining-a-dbproviderfactory"></a><span data-ttu-id="c6a31-102">Bir DbProviderFactory alma</span><span class="sxs-lookup"><span data-stu-id="c6a31-102">Obtaining a DbProviderFactory</span></span>
<span data-ttu-id="c6a31-103">Alma işlemi bir <xref:System.Data.Common.DbProviderFactory> bir veri sağlayıcısı hakkında bilgi geçirilmesi ile ilgilidir <xref:System.Data.Common.DbProviderFactories> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c6a31-103">The process of obtaining a <xref:System.Data.Common.DbProviderFactory> involves passing information about a data provider to the <xref:System.Data.Common.DbProviderFactories> class.</span></span> <span data-ttu-id="c6a31-104">Bu bilgilere göre <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> yöntemi, kesin türü belirtilmiş sağlayıcı üreteci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c6a31-104">Based on this information, the <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> method creates a strongly typed provider factory.</span></span> <span data-ttu-id="c6a31-105">Örneğin, oluşturmak için bir <xref:System.Data.SqlClient.SqlClientFactory>, geçirebilirsiniz `GetFactory` "System.Data.SqlClient" Belirtilen sağlayıcı adına sahip bir dize.</span><span class="sxs-lookup"><span data-stu-id="c6a31-105">For example, to create a <xref:System.Data.SqlClient.SqlClientFactory>, you can pass `GetFactory` a string with the provider name specified as "System.Data.SqlClient".</span></span> <span data-ttu-id="c6a31-106">Bir aşırı yüklemesini `GetFactory` geçen bir <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="c6a31-106">The other overload of `GetFactory` takes a <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="c6a31-107">Sağlayıcı fabrikası oluşturduktan sonra ek nesneler oluşturmak için yöntemlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6a31-107">Once you create the provider factory, you can then use its methods to create additional objects.</span></span> <span data-ttu-id="c6a31-108">Bazı yöntemlerinden birini bir `SqlClientFactory` dahil <xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A>, <xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A>, ve <xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A>.</span><span class="sxs-lookup"><span data-stu-id="c6a31-108">Some of the methods of a `SqlClientFactory` include <xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A>, <xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A>, and <xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6a31-109">.NET Framework <xref:System.Data.OracleClient.OracleClientFactory>, <xref:System.Data.Odbc.OdbcFactory>, ve <xref:System.Data.OleDb.OleDbFactory> sınıfları da benzer bir işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6a31-109">The .NET Framework <xref:System.Data.OracleClient.OracleClientFactory>, <xref:System.Data.Odbc.OdbcFactory>, and <xref:System.Data.OleDb.OleDbFactory> classes also provide similar functionality.</span></span>  
  
## <a name="registering-dbproviderfactories"></a><span data-ttu-id="c6a31-110">DbProviderFactories kaydetme</span><span class="sxs-lookup"><span data-stu-id="c6a31-110">Registering DbProviderFactories</span></span>  
 <span data-ttu-id="c6a31-111">Yapılandırma bilgilerini Fabrika tabanlı sınıfı destekleyen her .NET Framework veri sağlayıcısı kaydeder **DbProviderFactories** bölümünü **machine.config** dosyasını yerel bilgisayarda.</span><span class="sxs-lookup"><span data-stu-id="c6a31-111">Each .NET Framework data provider that supports a factory-based class registers configuration information in the **DbProviderFactories** section of the **machine.config** file on the local computer.</span></span> <span data-ttu-id="c6a31-112">Aşağıdaki yapılandırma dosyası parça biçimini ve sözdizimini gösterir <xref:System.Data.SqlClient>.</span><span class="sxs-lookup"><span data-stu-id="c6a31-112">The following configuration file fragment shows the syntax and format for <xref:System.Data.SqlClient>.</span></span>  
  
```xml  
<system.data>  
  <DbProviderFactories>  
    <add name="SqlClient Data Provider"  
     invariant="System.Data.SqlClient"   
     description=".Net Framework Data Provider for SqlServer"   
     type="System.Data.SqlClient.SqlClientFactory, System.Data,   
     Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
    />  
  </DbProviderFactories>  
</system.data>  
```  
  
 <span data-ttu-id="c6a31-113">**Değişmez** özniteliği temel alınan veri sağlayıcı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c6a31-113">The **invariant** attribute identifies the underlying data provider.</span></span> <span data-ttu-id="c6a31-114">Bu üç bölümlük sözdizimini, yeni bir Fabrika oluştururken ve böylece sağlayıcı adı, ilişkili bağlantı dizesi ile birlikte çalışma zamanında alınabilmesi için bir uygulama yapılandırma dosyasında sağlayıcının tanımlamak için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c6a31-114">This three-part naming syntax is also used when creating a new factory and for identifying the provider in an application configuration file so that the provider name, along with its associated connection string, can be retrieved at run time.</span></span>  
  
## <a name="retrieving-provider-information"></a><span data-ttu-id="c6a31-115">Sağlayıcı bilgileri alınıyor</span><span class="sxs-lookup"><span data-stu-id="c6a31-115">Retrieving Provider Information</span></span>  
 <span data-ttu-id="c6a31-116">Tüm kullanarak yerel bilgisayarda yüklü veri sağlayıcıları hakkında bilgi alabilirsiniz <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c6a31-116">You can retrieve information about all of the data providers installed on the local computer by using the <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> method.</span></span> <span data-ttu-id="c6a31-117">Döndürdüğü bir <xref:System.Data.DataTable> adlı **DbProviderFactories** aşağıdaki tabloda açıklanan sütunları içerir.</span><span class="sxs-lookup"><span data-stu-id="c6a31-117">It returns a <xref:System.Data.DataTable> named **DbProviderFactories** that contains the columns described in the following table.</span></span>  
  
|<span data-ttu-id="c6a31-118">Sütun sırası</span><span class="sxs-lookup"><span data-stu-id="c6a31-118">Column ordinal</span></span>|<span data-ttu-id="c6a31-119">Sütun adı</span><span class="sxs-lookup"><span data-stu-id="c6a31-119">Column name</span></span>|<span data-ttu-id="c6a31-120">Örnek çıktı</span><span class="sxs-lookup"><span data-stu-id="c6a31-120">Example output</span></span>|<span data-ttu-id="c6a31-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6a31-121">Description</span></span>|  
|--------------------|-----------------|--------------------|-----------------|  
|<span data-ttu-id="c6a31-122">0</span><span class="sxs-lookup"><span data-stu-id="c6a31-122">0</span></span>|<span data-ttu-id="c6a31-123">**Ad**</span><span class="sxs-lookup"><span data-stu-id="c6a31-123">**Name**</span></span>|<span data-ttu-id="c6a31-124">SqlClient veri sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="c6a31-124">SqlClient Data Provider</span></span>|<span data-ttu-id="c6a31-125">Veri sağlayıcısı için okunabilir adı</span><span class="sxs-lookup"><span data-stu-id="c6a31-125">Readable name for the data provider</span></span>|  
|<span data-ttu-id="c6a31-126">1.</span><span class="sxs-lookup"><span data-stu-id="c6a31-126">1</span></span>|<span data-ttu-id="c6a31-127">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="c6a31-127">**Description**</span></span>|<span data-ttu-id="c6a31-128">SqlServer için .net framework veri sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="c6a31-128">.Net Framework Data Provider for SqlServer</span></span>|<span data-ttu-id="c6a31-129">Veri sağlayıcısı okunabilir açıklaması</span><span class="sxs-lookup"><span data-stu-id="c6a31-129">Readable description of the data provider</span></span>|  
|<span data-ttu-id="c6a31-130">2</span><span class="sxs-lookup"><span data-stu-id="c6a31-130">2</span></span>|<span data-ttu-id="c6a31-131">**InvariantName**</span><span class="sxs-lookup"><span data-stu-id="c6a31-131">**InvariantName**</span></span>|<span data-ttu-id="c6a31-132">System.Data.SqlClient</span><span class="sxs-lookup"><span data-stu-id="c6a31-132">System.Data.SqlClient</span></span>|<span data-ttu-id="c6a31-133">Program aracılığıyla veri sağlayıcısı başvurmak için kullanılabilir adı</span><span class="sxs-lookup"><span data-stu-id="c6a31-133">Name that can be used programmatically to refer to the data provider</span></span>|  
|<span data-ttu-id="c6a31-134">3</span><span class="sxs-lookup"><span data-stu-id="c6a31-134">3</span></span>|<span data-ttu-id="c6a31-135">**AssemblyQualifiedName**</span><span class="sxs-lookup"><span data-stu-id="c6a31-135">**AssemblyQualifiedName**</span></span>|<span data-ttu-id="c6a31-136">System.Data.SqlClient.SqlClientFactory, System.Data, sürüm 2.0.0.0, Culture = neutral, PublicKeyToken = b77a5c561934e089</span><span class="sxs-lookup"><span data-stu-id="c6a31-136">System.Data.SqlClient.SqlClientFactory, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089</span></span>|<span data-ttu-id="c6a31-137">Nesne örneği oluşturmak için yeterli bilgiye sahip Fabrika sınıfın tam adı</span><span class="sxs-lookup"><span data-stu-id="c6a31-137">Fully qualified name of the factory class, which contains enough information to instantiate the object</span></span>|  
  
 <span data-ttu-id="c6a31-138">Bu `DataTable` seçmek bir kullanıcı etkinleştirmek için kullanılan bir <xref:System.Data.DataRow> çalışma zamanında.</span><span class="sxs-lookup"><span data-stu-id="c6a31-138">This `DataTable` can be used to enable a user to select a <xref:System.Data.DataRow> at run time.</span></span> <span data-ttu-id="c6a31-139">Seçili `DataRow` için geçirilebilir <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> kesin türü belirtilmiş oluşturmak için yöntemi <xref:System.Data.Common.DbProviderFactory>.</span><span class="sxs-lookup"><span data-stu-id="c6a31-139">The selected `DataRow` can then be passed to the <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> method to create a strongly typed <xref:System.Data.Common.DbProviderFactory>.</span></span> <span data-ttu-id="c6a31-140">Seçili <xref:System.Data.DataRow> için geçirilen `GetFactory` istenen oluşturmak için yöntemi `DbProviderFactory` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="c6a31-140">A selected <xref:System.Data.DataRow> can be passed to the `GetFactory` method to create the desired `DbProviderFactory` object.</span></span>  
  
## <a name="listing-the-installed-provider-factory-classes"></a><span data-ttu-id="c6a31-141">Yüklü sağlayıcı Üreteç sınıflarını listeleme</span><span class="sxs-lookup"><span data-stu-id="c6a31-141">Listing the Installed Provider Factory Classes</span></span>  
 <span data-ttu-id="c6a31-142">Bu örnek nasıl kullanılacağı ortaya <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> döndürülecek yöntemi bir <xref:System.Data.DataTable> yüklü sağlayıcıları hakkında bilgi içeren.</span><span class="sxs-lookup"><span data-stu-id="c6a31-142">This example demonstrates how to use the <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> method to return a <xref:System.Data.DataTable> containing information about the installed providers.</span></span> <span data-ttu-id="c6a31-143">Her satır kod dolaşır `DataTable`, bilgi yüklü her sağlayıcı için konsol penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c6a31-143">The code iterates through each row in the `DataTable`, displaying information for each installed provider in the console window.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/VB/source.vb#1)]  
  
## <a name="using-application-configuration-files-to-store-factory-information"></a><span data-ttu-id="c6a31-144">Fabrika bilgilerini depolamak için uygulama yapılandırma dosyalarını kullanma</span><span class="sxs-lookup"><span data-stu-id="c6a31-144">Using Application Configuration Files to Store Factory Information</span></span>  
 <span data-ttu-id="c6a31-145">Oluşturucuları ile çalışmak için kullanılan tasarım deseni kapsar sağlayıcısı ve bağlantı dizesi bilgileri gibi bir uygulama yapılandırma dosyasında depolamak **app.config** bir Windows uygulaması için ve **web.config**  bir ASP.NET uygulaması için.</span><span class="sxs-lookup"><span data-stu-id="c6a31-145">The design pattern used for working with factories entails storing provider and connection string information in an application configuration file, such as **app.config** for a Windows application, and **web.config** for an ASP.NET application.</span></span>  
  
 <span data-ttu-id="c6a31-146">Aşağıdaki yapılandırma dosyası parça iki adlandırılmış bağlantı dizeleri nasıl kaydedileceği SQL Server'da Northwind veritabanına bir bağlantı için "NorthwindSQL" ve "NorthwindAccess" erişim/Jet Northwind veritabanına bir bağlantı için gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c6a31-146">The following configuration file fragment demonstrates how to save two named connection strings, "NorthwindSQL" for a connection to the Northwind database in SQL Server, and "NorthwindAccess" for a connection to the Northwind database in Access/Jet.</span></span> <span data-ttu-id="c6a31-147">**Değişmez** adı için kullanıldığından **providerName** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c6a31-147">The **invariant** name is used for the **providerName** attribute.</span></span>  
  
```xml  
<configuration>  
  <connectionStrings>  
    <clear/>  
    <add name="NorthwindSQL"   
     providerName="System.Data.SqlClient"   
     connectionString=  
     "Data Source=MSSQL1;Initial Catalog=Northwind;Integrated Security=true"  
    />  
  
    <add name="NorthwindAccess"   
     providerName="System.Data.OleDb"   
     connectionString=  
     "Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Data\Northwind.mdb;"  
    />  
  </connectionStrings>  
</configuration>  
```  
  
### <a name="retrieving-a-connection-string-by-provider-name"></a><span data-ttu-id="c6a31-148">Bir bağlantı dizesi sağlayıcı ada göre alma</span><span class="sxs-lookup"><span data-stu-id="c6a31-148">Retrieving a Connection String by Provider Name</span></span>  
 <span data-ttu-id="c6a31-149">Sağlayıcı fabrikası oluşturmak için bir bağlantı dizesi ve bunun yanı sıra sağlayıcı adı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c6a31-149">In order to create a provider factory, you must supply a connection string as well as the provider name.</span></span> <span data-ttu-id="c6a31-150">Bu örnek, sağlayıcı adı değişmez biçiminde geçirerek bir uygulama yapılandırma dosyasından bağlantı dizesini almak gösterilmiştir "*System.Data.ProviderName*".</span><span class="sxs-lookup"><span data-stu-id="c6a31-150">This example demonstrates how to retrieve a connection string from an application configuration file by passing the provider name in the invariant format "*System.Data.ProviderName*".</span></span> <span data-ttu-id="c6a31-151">Kod dolaşır <xref:System.Configuration.ConnectionStringSettingsCollection>.</span><span class="sxs-lookup"><span data-stu-id="c6a31-151">The code iterates through the <xref:System.Configuration.ConnectionStringSettingsCollection>.</span></span> <span data-ttu-id="c6a31-152">Döndürdüğü <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> başarı; Aksi halde `null` (`Nothing` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="c6a31-152">It returns the <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> on success; otherwise `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="c6a31-153">Sağlayıcı için birden fazla giriş varsa, ilk döndürülür.</span><span class="sxs-lookup"><span data-stu-id="c6a31-153">If there are multiple entries for a provider, the first one found is returned.</span></span> <span data-ttu-id="c6a31-154">Daha fazla bilgi ve örnekler bağlantı dizelerini yapılandırma dosyalarından alınması için bkz: [bağlantı dizeleri ve yapılandırma dosyalarını](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="c6a31-154">For more information and examples of retrieving connection strings from configuration files, see [Connection Strings and Configuration Files](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6a31-155">Bir başvuru `System.Configuration.dll` sırayla çalıştırmak için kod için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c6a31-155">A reference to `System.Configuration.dll` is required in order for the code to run.</span></span>  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="creating-the-dbproviderfactory-and-dbconnection"></a><span data-ttu-id="c6a31-156">DbConnection ve DbProviderFactory oluşturma</span><span class="sxs-lookup"><span data-stu-id="c6a31-156">Creating the DbProviderFactory and DbConnection</span></span>  
 <span data-ttu-id="c6a31-157">Bu örnek nasıl oluşturulduğunu gösteren bir <xref:System.Data.Common.DbProviderFactory> ve <xref:System.Data.Common.DbConnection> sağlayıcı adı biçiminde geçirerek nesne "*System.Data.ProviderName*" ve bir bağlantı dizesi.</span><span class="sxs-lookup"><span data-stu-id="c6a31-157">This example demonstrates how to create a <xref:System.Data.Common.DbProviderFactory> and <xref:System.Data.Common.DbConnection> object by passing it the provider name in the format "*System.Data.ProviderName*" and a connection string.</span></span> <span data-ttu-id="c6a31-158">A `DbConnection` nesne başarı; döndürdü `null` (`Nothing` Visual Basic'te) tüm hata.</span><span class="sxs-lookup"><span data-stu-id="c6a31-158">A `DbConnection` object is returned on success; `null` (`Nothing` in Visual Basic) on any error.</span></span>  
  
 <span data-ttu-id="c6a31-159">Kod edinir `DbProviderFactory` çağırarak <xref:System.Data.Common.DbProviderFactories.GetFactory%2A>.</span><span class="sxs-lookup"><span data-stu-id="c6a31-159">The code obtains the `DbProviderFactory` by calling <xref:System.Data.Common.DbProviderFactories.GetFactory%2A>.</span></span> <span data-ttu-id="c6a31-160">Ardından <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> yöntemi oluşturur <xref:System.Data.Common.DbConnection> nesne ve <xref:System.Data.Common.DbConnection.ConnectionString%2A> özelliğini bağlantı dizesine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c6a31-160">Then the <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> method creates the <xref:System.Data.Common.DbConnection> object and the <xref:System.Data.Common.DbConnection.ConnectionString%2A> property is set to the connection string.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c6a31-161">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c6a31-161">See Also</span></span>  
 [<span data-ttu-id="c6a31-162">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="c6a31-162">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 [<span data-ttu-id="c6a31-163">Bağlantı Dizeleri</span><span class="sxs-lookup"><span data-stu-id="c6a31-163">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 [<span data-ttu-id="c6a31-164">Yapılandırma sınıflarını kullanma</span><span class="sxs-lookup"><span data-stu-id="c6a31-164">Using the Configuration Classes</span></span>](http://msdn.microsoft.com/library/98d2b386-baf6-4a17-974b-76e3b4c87acc)  
 [<span data-ttu-id="c6a31-165">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="c6a31-165">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
