---
title: Bağlantı Dizesi Oluşturucular
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8434b608-c4d3-43d3-8ae3-6d8c6b726759
ms.openlocfilehash: a29efbc1b4d886afe4329df011b522e4d589e2ee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949501"
---
# <a name="connection-string-builders"></a><span data-ttu-id="c8efd-102">Bağlantı Dizesi Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="c8efd-102">Connection String Builders</span></span>
<span data-ttu-id="c8efd-103">Önceki ADO.NET sürümlerinde, birleştirilmiş dize değerleriyle bağlantı dizeleri derleme zamanı denetimi gerçekleşmediğinden, çalışma zamanında yanlış bir anahtar sözcük oluşturulur <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="c8efd-103">In earlier versions of ADO.NET, compile-time checking of connection strings with concatenated string values did not occur, so that at run time, an incorrect keyword generated an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="c8efd-104">.NET Framework veri sağlayıcılarının her biri, el ile yapıldıysa geçerli bağlantı dizeleri oluşturmak için bağlantı dizesi anahtar sözcükleri için farklı sözdizimi destekliyordu.</span><span class="sxs-lookup"><span data-stu-id="c8efd-104">Each of the .NET Framework data providers supported different syntax for connection string keywords, which made constructing valid connection strings difficult if done manually.</span></span> <span data-ttu-id="c8efd-105">Bu sorunu gidermek için, ADO.NET 2,0 her bir .NET Framework veri sağlayıcısı için yeni bağlantı dizesi oluşturucuları sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="c8efd-105">To address this problem, ADO.NET 2.0 introduced new connection string builders for each .NET Framework data provider.</span></span> <span data-ttu-id="c8efd-106">Her veri sağlayıcısı, öğesinden <xref:System.Data.Common.DbConnectionStringBuilder>devralan türü kesin belirlenmiş bir bağlantı dizesi Oluşturucu sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="c8efd-106">Each data provider includes a strongly typed connection string builder class that inherits from <xref:System.Data.Common.DbConnectionStringBuilder>.</span></span> <span data-ttu-id="c8efd-107">Aşağıdaki tabloda .NET Framework veri sağlayıcıları ve ilişkili bağlantı dizesi Oluşturucu sınıfları listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="c8efd-107">The following table lists the .NET Framework data providers and their associated connection string builder classes.</span></span>  
  
|<span data-ttu-id="c8efd-108">Sağlayıcı</span><span class="sxs-lookup"><span data-stu-id="c8efd-108">Provider</span></span>|<span data-ttu-id="c8efd-109">ConnectionStringBuilder sınıfı</span><span class="sxs-lookup"><span data-stu-id="c8efd-109">ConnectionStringBuilder class</span></span>|  
|--------------|-----------------------------------|  
|<xref:System.Data.SqlClient>|<xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OleDb>|<xref:System.Data.OleDb.OleDbConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.Odbc>|<xref:System.Data.Odbc.OdbcConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OracleClient>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|  
  
## <a name="connection-string-injection-attacks"></a><span data-ttu-id="c8efd-110">Bağlantı dizesi ekleme saldırıları</span><span class="sxs-lookup"><span data-stu-id="c8efd-110">Connection String Injection Attacks</span></span>  
 <span data-ttu-id="c8efd-111">Bir bağlantı dizesi ekleme saldırısı, Kullanıcı girişini temel alan bağlantı dizelerini oluşturmak için dinamik dize birleştirme kullanıldığında meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="c8efd-111">A connection string injection attack can occur when dynamic string concatenation is used to build connection strings that are based on user input.</span></span> <span data-ttu-id="c8efd-112">Dize doğrulanmaz ve kötü amaçlı metin veya karakterler atlanmaz, bir saldırgan sunucudaki hassas verilere veya diğer kaynaklara erişebilir.</span><span class="sxs-lookup"><span data-stu-id="c8efd-112">If the string is not validated and malicious text or characters not escaped, an attacker can potentially access sensitive data or other resources on the server.</span></span> <span data-ttu-id="c8efd-113">Örneğin, bir saldırgan noktalı virgül sağlayarak ve ek bir değer ekleyerek bir saldırı bağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="c8efd-113">For example, an attacker could mount an attack by supplying a semicolon and appending an additional value.</span></span> <span data-ttu-id="c8efd-114">Bağlantı dizesi bir "son bir WINS" algoritması kullanılarak ayrıştırılır ve saldırgan girişi, meşru bir değer için değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="c8efd-114">The connection string is parsed by using a "last one wins" algorithm, and the hostile input is substituted for a legitimate value.</span></span>  
  
 <span data-ttu-id="c8efd-115">Bağlantı dizesi Oluşturucu sınıfları, tahmin etmeyi ortadan kaldırmak ve söz dizimi hatalarına ve güvenlik açıklarına karşı korumak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c8efd-115">The connection string builder classes are designed to eliminate guesswork and protect against syntax errors and security vulnerabilities.</span></span> <span data-ttu-id="c8efd-116">Her veri sağlayıcısı tarafından izin verilen bilinen anahtar/değer çiftlerine karşılık gelen yöntemleri ve özellikleri sağlarlar.</span><span class="sxs-lookup"><span data-stu-id="c8efd-116">They provide methods and properties corresponding to the known key/value pairs permitted by each data provider.</span></span> <span data-ttu-id="c8efd-117">Her sınıf, sabit bir eş anlamlı koleksiyonu saklar ve bir eş anlamadan ilgili iyi bilinen anahtar adına çevirebilir.</span><span class="sxs-lookup"><span data-stu-id="c8efd-117">Each class maintains a fixed collection of synonyms and can translate from a synonym to the corresponding well-known key name.</span></span> <span data-ttu-id="c8efd-118">Geçerli anahtar/değer çiftleri için denetimler gerçekleştirilir ve geçersiz bir çift özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c8efd-118">Checks are performed for valid key/value pairs and an invalid pair throws an exception.</span></span> <span data-ttu-id="c8efd-119">Buna ek olarak, eklenen değerler güvenli bir şekilde işlenir.</span><span class="sxs-lookup"><span data-stu-id="c8efd-119">In addition, injected values are handled in a safe manner.</span></span>  
  
 <span data-ttu-id="c8efd-120">Aşağıdaki örnek, <xref:System.Data.SqlClient.SqlConnectionStringBuilder> `Initial Catalog` ayarı için ek bir ek değerin nasıl işlediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8efd-120">The following example demonstrates how the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> handles an inserted extra value for the `Initial Catalog` setting.</span></span>  
  
```vb  
Dim builder As New System.Data.SqlClient.SqlConnectionStringBuilder  
builder("Data Source") = "(local)"  
builder("Integrated Security") = True  
builder("Initial Catalog") = "AdventureWorks;NewValue=Bad"  
Console.WriteLine(builder.ConnectionString)  
```  
  
```csharp  
System.Data.SqlClient.SqlConnectionStringBuilder builder =  
  new System.Data.SqlClient.SqlConnectionStringBuilder();  
builder["Data Source"] = "(local)";  
builder["integrated Security"] = true;  
builder["Initial Catalog"] = "AdventureWorks;NewValue=Bad";  
Console.WriteLine(builder.ConnectionString);  
```  
  
 <span data-ttu-id="c8efd-121">Çıktı, bunu, bağlantı <xref:System.Data.SqlClient.SqlConnectionStringBuilder> dizesine yeni bir anahtar/değer çifti olarak eklemek yerine, ek değeri çift tırnak işareti içinde kaçış yoluyla doğru bir şekilde işlendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8efd-121">The output shows that the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> handled this correctly by escaping the extra value in double quotation marks instead of appending it to the connection string as a new key/value pair.</span></span>  
  
```  
data source=(local);Integrated Security=True;  
initial catalog="AdventureWorks;NewValue=Bad"  
```  
  
## <a name="building-connection-strings-from-configuration-files"></a><span data-ttu-id="c8efd-122">Yapılandırma dosyalarından bağlantı dizeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="c8efd-122">Building Connection Strings from Configuration Files</span></span>  
 <span data-ttu-id="c8efd-123">Bir bağlantı dizesinin belirli öğeleri önceden biliniyorsa, bir yapılandırma dosyasında depolanabilir ve tamamen bir bağlantı dizesi oluşturmak için çalışma zamanında elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="c8efd-123">If certain elements of a connection string are known beforehand, they can be stored in a configuration file and retrieved at run time to construct a complete connection string.</span></span> <span data-ttu-id="c8efd-124">Örneğin, veritabanının adı önceden biliniyor olabilir, ancak sunucunun adı değildir.</span><span class="sxs-lookup"><span data-stu-id="c8efd-124">For example, the name of the database might be known in advance, but not the name of the server.</span></span> <span data-ttu-id="c8efd-125">Ya da bir kullanıcının, bağlantı dizesine diğer değerleri ekleyebilmeden çalışma zamanında bir ad ve parola vermesini isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8efd-125">Or you might want a user to supply a name and password at run time without being able to inject other values into the connection string.</span></span>  
  
 <span data-ttu-id="c8efd-126">Bir bağlantı dizesi oluşturucusunun aşırı yüklenmiş oluşturucularından biri, bir <xref:System.String> bağımsız değişken olarak alır. Bu, daha sonra Kullanıcı girişinden tamamlanabilir kısmi bir bağlantı dizesi sağlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8efd-126">One of the overloaded constructors for a connection string builder takes a <xref:System.String> as an argument, which enables you to supply a partial connection string that can then be completed from user input.</span></span> <span data-ttu-id="c8efd-127">Kısmi bağlantı dizesi bir yapılandırma dosyasında depolanabilir ve çalışma zamanında elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="c8efd-127">The partial connection string can be stored in a configuration file and retrieved at run time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c8efd-128">Ad alanı, Web uygulamaları <xref:System.Web.Configuration.WebConfigurationManager> <xref:System.Configuration.ConfigurationManager> için ve Windows uygulamaları için kullanan yapılandırma dosyalarına programlı erişim sağlar. <xref:System.Configuration></span><span class="sxs-lookup"><span data-stu-id="c8efd-128">The <xref:System.Configuration> namespace allows programmatic access to configuration files that use the <xref:System.Web.Configuration.WebConfigurationManager> for Web applications and the <xref:System.Configuration.ConfigurationManager> for Windows applications.</span></span> <span data-ttu-id="c8efd-129">Bağlantı dizeleri ve yapılandırma dosyalarıyla çalışma hakkında daha fazla bilgi için bkz. [bağlantı dizeleri ve yapılandırma dosyaları](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="c8efd-129">For more information about working with connection strings and configuration files, see [Connection Strings and Configuration Files](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="c8efd-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="c8efd-130">Example</span></span>  
 <span data-ttu-id="c8efd-131">Bu örnek, bir yapılandırma dosyasından kısmi bağlantı dizesinin alınması <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>ve öğesinin <xref:System.Data.SqlClient.SqlConnectionStringBuilder>, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>ve <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> özelliklerini ayarlayarak tamamlanışını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8efd-131">This example demonstrates retrieving a partial connection string from a configuration file and completing it by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>, and <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> properties of the <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span> <span data-ttu-id="c8efd-132">Yapılandırma dosyası aşağıdaki gibi tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="c8efd-132">The configuration file is defined as follows.</span></span>  
  
```xml  
<connectionStrings>  
  <clear/>  
  <add name="partialConnectString"   
    connectionString="Initial Catalog=Northwind;"  
    providerName="System.Data.SqlClient" />  
</connectionStrings>  
```  
  
> [!NOTE]
> <span data-ttu-id="c8efd-133">Kodun çalışması için projenizdeki öğesine `System.Configuration.dll` bir başvuru ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c8efd-133">You must set a reference to the `System.Configuration.dll` in your project for the code to run.</span></span>  
  
 [!code-csharp[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/CS/source.cs#1)]
 [!code-vb[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c8efd-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8efd-134">See also</span></span>

- [<span data-ttu-id="c8efd-135">Bağlantı Dizeleri</span><span class="sxs-lookup"><span data-stu-id="c8efd-135">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)
- [<span data-ttu-id="c8efd-136">Gizlilik ve Veri Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c8efd-136">Privacy and Data Security</span></span>](../../../../docs/framework/data/adonet/privacy-and-data-security.md)
- [<span data-ttu-id="c8efd-137">ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="c8efd-137">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
