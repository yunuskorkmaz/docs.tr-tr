---
title: Bağlantı Dizesi Oluşturucular
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8434b608-c4d3-43d3-8ae3-6d8c6b726759
ms.openlocfilehash: 8cadeac0bcbf301f7d973e93435885de82052603
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151669"
---
# <a name="connection-string-builders"></a><span data-ttu-id="45a9c-102">Bağlantı Dizesi Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="45a9c-102">Connection String Builders</span></span>
<span data-ttu-id="45a9c-103">ADO.NET önceki sürümlerinde, sıkıştırılmış dize değerlerine sahip bağlantı dizelerinin derleme zamanı denetimi gerçekleşmedi, böylece çalışma <xref:System.ArgumentException>zamanında yanlış bir anahtar kelime bir .</span><span class="sxs-lookup"><span data-stu-id="45a9c-103">In earlier versions of ADO.NET, compile-time checking of connection strings with concatenated string values did not occur, so that at run time, an incorrect keyword generated an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="45a9c-104">.NET Framework veri sağlayıcılarının her biri, bağlantı dizeanahtar kelimeleri için farklı sözdizimini destekleyerek, el ile yapıldığında geçerli bağlantı dizeleri oluşturmayı zorlaştırdı.</span><span class="sxs-lookup"><span data-stu-id="45a9c-104">Each of the .NET Framework data providers supported different syntax for connection string keywords, which made constructing valid connection strings difficult if done manually.</span></span> <span data-ttu-id="45a9c-105">Bu sorunu gidermek için, ADO.NET 2.0 her .NET Framework veri sağlayıcısı için yeni bağlantı dize oluşturucuları tanıttı.</span><span class="sxs-lookup"><span data-stu-id="45a9c-105">To address this problem, ADO.NET 2.0 introduced new connection string builders for each .NET Framework data provider.</span></span> <span data-ttu-id="45a9c-106">Her veri sağlayıcısı, 'den <xref:System.Data.Common.DbConnectionStringBuilder>devralan güçlü bir şekilde yazılan bağlantı dize oluşturucu sınıfiçerir.</span><span class="sxs-lookup"><span data-stu-id="45a9c-106">Each data provider includes a strongly typed connection string builder class that inherits from <xref:System.Data.Common.DbConnectionStringBuilder>.</span></span> <span data-ttu-id="45a9c-107">Aşağıdaki tabloda .NET Framework veri sağlayıcıları ve ilişkili bağlantı dize oluşturucu sınıfları listeleneb..</span><span class="sxs-lookup"><span data-stu-id="45a9c-107">The following table lists the .NET Framework data providers and their associated connection string builder classes.</span></span>  
  
|<span data-ttu-id="45a9c-108">Sağlayıcı</span><span class="sxs-lookup"><span data-stu-id="45a9c-108">Provider</span></span>|<span data-ttu-id="45a9c-109">ConnectionStringBuilder sınıfı</span><span class="sxs-lookup"><span data-stu-id="45a9c-109">ConnectionStringBuilder class</span></span>|  
|--------------|-----------------------------------|  
|<xref:System.Data.SqlClient>|<xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OleDb>|<xref:System.Data.OleDb.OleDbConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.Odbc>|<xref:System.Data.Odbc.OdbcConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OracleClient>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|  
  
## <a name="connection-string-injection-attacks"></a><span data-ttu-id="45a9c-110">Bağlantı String Enjeksiyon Saldırıları</span><span class="sxs-lookup"><span data-stu-id="45a9c-110">Connection String Injection Attacks</span></span>  
 <span data-ttu-id="45a9c-111">Dinamik dize concatenation kullanıcı girişine dayalı bağlantı dizeleri oluşturmak için kullanıldığında bir bağlantı dize enjeksiyon saldırı oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="45a9c-111">A connection string injection attack can occur when dynamic string concatenation is used to build connection strings that are based on user input.</span></span> <span data-ttu-id="45a9c-112">Dize doğrulanmadıysa ve kötü amaçlı metin veya karakterler kaçmazsa, saldırgan hassas verilere veya sunucudaki diğer kaynaklara erişebilir.</span><span class="sxs-lookup"><span data-stu-id="45a9c-112">If the string is not validated and malicious text or characters not escaped, an attacker can potentially access sensitive data or other resources on the server.</span></span> <span data-ttu-id="45a9c-113">Örneğin, bir saldırgan bir yarı kolon sağlayarak ve ek bir değer ekleyerek bir saldırı monte edebilirim.</span><span class="sxs-lookup"><span data-stu-id="45a9c-113">For example, an attacker could mount an attack by supplying a semicolon and appending an additional value.</span></span> <span data-ttu-id="45a9c-114">Bağlantı dizesi "son bir kazanır" algoritması kullanılarak ayrıştırılır ve düşman girişi meşru bir değerle değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="45a9c-114">The connection string is parsed by using a "last one wins" algorithm, and the hostile input is substituted for a legitimate value.</span></span>  
  
 <span data-ttu-id="45a9c-115">Bağlantı dizesi oluşturucu sınıfları, tahmin çalışmalarını ortadan kaldırmak ve sözdizimi hatalarına ve güvenlik açıklarına karşı korumak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="45a9c-115">The connection string builder classes are designed to eliminate guesswork and protect against syntax errors and security vulnerabilities.</span></span> <span data-ttu-id="45a9c-116">Her veri sağlayıcısı tarafından izin verilen bilinen anahtar/değer çiftleri ile karşılık gelen yöntemler ve özellikler sağlarlar.</span><span class="sxs-lookup"><span data-stu-id="45a9c-116">They provide methods and properties corresponding to the known key/value pairs permitted by each data provider.</span></span> <span data-ttu-id="45a9c-117">Her sınıf eşanlamlısabit bir koleksiyon tutar ve ilgili iyi bilinen anahtar adı için eşanlamlı tercüme edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45a9c-117">Each class maintains a fixed collection of synonyms and can translate from a synonym to the corresponding well-known key name.</span></span> <span data-ttu-id="45a9c-118">Geçerli anahtar/değer çiftleri için denetimler yapılır ve geçersiz bir çift bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="45a9c-118">Checks are performed for valid key/value pairs and an invalid pair throws an exception.</span></span> <span data-ttu-id="45a9c-119">Buna ek olarak, enjekte edilen değerler güvenli bir şekilde işlenir.</span><span class="sxs-lookup"><span data-stu-id="45a9c-119">In addition, injected values are handled in a safe manner.</span></span>  
  
 <span data-ttu-id="45a9c-120">Aşağıdaki örnek, <xref:System.Data.SqlClient.SqlConnectionStringBuilder> `Initial Catalog` ayarı için eklenen bir ek değeri nasıl işlettiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="45a9c-120">The following example demonstrates how the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> handles an inserted extra value for the `Initial Catalog` setting.</span></span>  
  
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
  
 <span data-ttu-id="45a9c-121">Çıktı, bağlantı <xref:System.Data.SqlClient.SqlConnectionStringBuilder> dizesine yeni bir anahtar/değer çifti olarak eklemek yerine çift tırnak işaretlerindeki ekstra değerden kaçarak bunu doğru bir şekilde ele aldığımı gösterir.</span><span class="sxs-lookup"><span data-stu-id="45a9c-121">The output shows that the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> handled this correctly by escaping the extra value in double quotation marks instead of appending it to the connection string as a new key/value pair.</span></span>  
  
```output  
data source=(local);Integrated Security=True;  
initial catalog="AdventureWorks;NewValue=Bad"  
```  
  
## <a name="building-connection-strings-from-configuration-files"></a><span data-ttu-id="45a9c-122">Yapılandırma Dosyalarından Bağlantı Dizeleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="45a9c-122">Building Connection Strings from Configuration Files</span></span>  
 <span data-ttu-id="45a9c-123">Bir bağlantı dizesinin belirli öğeleri önceden biliniyorsa, yapılandırma dosyasında depolanabilir ve tam bir bağlantı dizesi oluşturmak için çalışma zamanında alınabilir.</span><span class="sxs-lookup"><span data-stu-id="45a9c-123">If certain elements of a connection string are known beforehand, they can be stored in a configuration file and retrieved at run time to construct a complete connection string.</span></span> <span data-ttu-id="45a9c-124">Örneğin, veritabanının adı önceden bilinebilir, ancak sunucunun adı bilinmez.</span><span class="sxs-lookup"><span data-stu-id="45a9c-124">For example, the name of the database might be known in advance, but not the name of the server.</span></span> <span data-ttu-id="45a9c-125">Veya bir kullanıcının bağlantı dizesine diğer değerleri enjekte etmeden çalışma zamanında bir ad ve parola sağlamasını isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45a9c-125">Or you might want a user to supply a name and password at run time without being able to inject other values into the connection string.</span></span>  
  
 <span data-ttu-id="45a9c-126">Bir bağlantı dize oluşturucu için aşırı yüklü <xref:System.String> oluşturucular biri daha sonra kullanıcı girişi tamamlanabilir kısmi bir bağlantı dizesi kaynağı sağlayan bir bağımsız değişken olarak alır.</span><span class="sxs-lookup"><span data-stu-id="45a9c-126">One of the overloaded constructors for a connection string builder takes a <xref:System.String> as an argument, which enables you to supply a partial connection string that can then be completed from user input.</span></span> <span data-ttu-id="45a9c-127">Kısmi bağlantı dizesi bir yapılandırma dosyasında depolanabilir ve çalışma zamanında alınabilir.</span><span class="sxs-lookup"><span data-stu-id="45a9c-127">The partial connection string can be stored in a configuration file and retrieved at run time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="45a9c-128">Ad <xref:System.Configuration> alanı, Web uygulamaları ve Windows <xref:System.Web.Configuration.WebConfigurationManager> uygulamaları <xref:System.Configuration.ConfigurationManager> için kullanılan yapılandırma dosyalarına programlı erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="45a9c-128">The <xref:System.Configuration> namespace allows programmatic access to configuration files that use the <xref:System.Web.Configuration.WebConfigurationManager> for Web applications and the <xref:System.Configuration.ConfigurationManager> for Windows applications.</span></span> <span data-ttu-id="45a9c-129">Bağlantı dizeleri ve yapılandırma dosyalarıyla çalışma hakkında daha fazla bilgi için [Bağlantı Dizeleri ve Yapılandırma Dosyaları'na](connection-strings-and-configuration-files.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="45a9c-129">For more information about working with connection strings and configuration files, see [Connection Strings and Configuration Files](connection-strings-and-configuration-files.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="45a9c-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="45a9c-130">Example</span></span>  
 <span data-ttu-id="45a9c-131">Bu örnek, bir yapılandırma dosyasından kısmi bir bağlantı dizesi <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>alma <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>ve <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> , <xref:System.Data.SqlClient.SqlConnectionStringBuilder>, ve özelliklerini ayarlayarak tamamlayarak gösterir .</span><span class="sxs-lookup"><span data-stu-id="45a9c-131">This example demonstrates retrieving a partial connection string from a configuration file and completing it by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>, and <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> properties of the <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span> <span data-ttu-id="45a9c-132">Yapılandırma dosyası aşağıdaki gibi tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="45a9c-132">The configuration file is defined as follows.</span></span>  
  
```xml  
<connectionStrings>  
  <clear/>  
  <add name="partialConnectString"
    connectionString="Initial Catalog=Northwind;"  
    providerName="System.Data.SqlClient" />  
</connectionStrings>  
```  
  
> [!NOTE]
> <span data-ttu-id="45a9c-133">Kodun çalışması için `System.Configuration.dll` projenizdeki başvuruyu ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="45a9c-133">You must set a reference to the `System.Configuration.dll` in your project for the code to run.</span></span>  
  
 [!code-csharp[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/CS/source.cs#1)]
 [!code-vb[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="45a9c-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45a9c-134">See also</span></span>

- [<span data-ttu-id="45a9c-135">Bağlantı Dizeleri</span><span class="sxs-lookup"><span data-stu-id="45a9c-135">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="45a9c-136">Gizlilik ve Veri Güvenliği</span><span class="sxs-lookup"><span data-stu-id="45a9c-136">Privacy and Data Security</span></span>](privacy-and-data-security.md)
- [<span data-ttu-id="45a9c-137">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="45a9c-137">ADO.NET Overview</span></span>](ado-net-overview.md)
