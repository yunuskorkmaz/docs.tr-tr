---
title: Bağlantı Dizesi Oluşturucular
description: ADO.NET ' deki farklı sağlayıcılar için kullanılan bağlantı dizesi Oluşturucu sınıfları hakkında bilgi edinin ve bunların hepsi DbConnectionStringBuilder ' dan devralınır.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8434b608-c4d3-43d3-8ae3-6d8c6b726759
ms.openlocfilehash: e493140b4cf5a939e8ae8f42b617fb739ed09dec
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287070"
---
# <a name="connection-string-builders"></a><span data-ttu-id="941d1-103">Bağlantı Dizesi Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="941d1-103">Connection String Builders</span></span>
<span data-ttu-id="941d1-104">Önceki ADO.NET sürümlerinde, birleştirilmiş dize değerleriyle bağlantı dizeleri derleme zamanı denetimi gerçekleşmediğinden, çalışma zamanında yanlış bir anahtar sözcük oluşturulur <xref:System.ArgumentException> .</span><span class="sxs-lookup"><span data-stu-id="941d1-104">In earlier versions of ADO.NET, compile-time checking of connection strings with concatenated string values did not occur, so that at run time, an incorrect keyword generated an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="941d1-105">.NET Framework veri sağlayıcılarının her biri, el ile yapıldıysa geçerli bağlantı dizeleri oluşturmak için bağlantı dizesi anahtar sözcükleri için farklı sözdizimi destekliyordu.</span><span class="sxs-lookup"><span data-stu-id="941d1-105">Each of the .NET Framework data providers supported different syntax for connection string keywords, which made constructing valid connection strings difficult if done manually.</span></span> <span data-ttu-id="941d1-106">Bu sorunu gidermek için, ADO.NET 2,0 her bir .NET Framework veri sağlayıcısı için yeni bağlantı dizesi oluşturucuları sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="941d1-106">To address this problem, ADO.NET 2.0 introduced new connection string builders for each .NET Framework data provider.</span></span> <span data-ttu-id="941d1-107">Her veri sağlayıcısı, öğesinden devralan türü kesin belirlenmiş bir bağlantı dizesi Oluşturucu sınıfı içerir <xref:System.Data.Common.DbConnectionStringBuilder> .</span><span class="sxs-lookup"><span data-stu-id="941d1-107">Each data provider includes a strongly typed connection string builder class that inherits from <xref:System.Data.Common.DbConnectionStringBuilder>.</span></span> <span data-ttu-id="941d1-108">Aşağıdaki tabloda .NET Framework veri sağlayıcıları ve ilişkili bağlantı dizesi Oluşturucu sınıfları listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="941d1-108">The following table lists the .NET Framework data providers and their associated connection string builder classes.</span></span>  
  
|<span data-ttu-id="941d1-109">Sağlayıcı</span><span class="sxs-lookup"><span data-stu-id="941d1-109">Provider</span></span>|<span data-ttu-id="941d1-110">ConnectionStringBuilder sınıfı</span><span class="sxs-lookup"><span data-stu-id="941d1-110">ConnectionStringBuilder class</span></span>|  
|--------------|-----------------------------------|  
|<xref:System.Data.SqlClient>|<xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OleDb>|<xref:System.Data.OleDb.OleDbConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.Odbc>|<xref:System.Data.Odbc.OdbcConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OracleClient>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|  
  
## <a name="connection-string-injection-attacks"></a><span data-ttu-id="941d1-111">Bağlantı dizesi ekleme saldırıları</span><span class="sxs-lookup"><span data-stu-id="941d1-111">Connection String Injection Attacks</span></span>  
 <span data-ttu-id="941d1-112">Bir bağlantı dizesi ekleme saldırısı, Kullanıcı girişini temel alan bağlantı dizelerini oluşturmak için dinamik dize birleştirme kullanıldığında meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="941d1-112">A connection string injection attack can occur when dynamic string concatenation is used to build connection strings that are based on user input.</span></span> <span data-ttu-id="941d1-113">Dize doğrulanmaz ve kötü amaçlı metin veya karakterler atlanmaz, bir saldırgan sunucudaki hassas verilere veya diğer kaynaklara erişebilir.</span><span class="sxs-lookup"><span data-stu-id="941d1-113">If the string is not validated and malicious text or characters not escaped, an attacker can potentially access sensitive data or other resources on the server.</span></span> <span data-ttu-id="941d1-114">Örneğin, bir saldırgan noktalı virgül sağlayarak ve ek bir değer ekleyerek bir saldırı bağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="941d1-114">For example, an attacker could mount an attack by supplying a semicolon and appending an additional value.</span></span> <span data-ttu-id="941d1-115">Bağlantı dizesi bir "son bir WINS" algoritması kullanılarak ayrıştırılır ve saldırgan girişi, meşru bir değer için değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="941d1-115">The connection string is parsed by using a "last one wins" algorithm, and the hostile input is substituted for a legitimate value.</span></span>  
  
 <span data-ttu-id="941d1-116">Bağlantı dizesi Oluşturucu sınıfları, tahmin etmeyi ortadan kaldırmak ve söz dizimi hatalarına ve güvenlik açıklarına karşı korumak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="941d1-116">The connection string builder classes are designed to eliminate guesswork and protect against syntax errors and security vulnerabilities.</span></span> <span data-ttu-id="941d1-117">Her veri sağlayıcısı tarafından izin verilen bilinen anahtar/değer çiftlerine karşılık gelen yöntemleri ve özellikleri sağlarlar.</span><span class="sxs-lookup"><span data-stu-id="941d1-117">They provide methods and properties corresponding to the known key/value pairs permitted by each data provider.</span></span> <span data-ttu-id="941d1-118">Her sınıf, sabit bir eş anlamlı koleksiyonu saklar ve bir eş anlamadan ilgili iyi bilinen anahtar adına çevirebilir.</span><span class="sxs-lookup"><span data-stu-id="941d1-118">Each class maintains a fixed collection of synonyms and can translate from a synonym to the corresponding well-known key name.</span></span> <span data-ttu-id="941d1-119">Geçerli anahtar/değer çiftleri için denetimler gerçekleştirilir ve geçersiz bir çift özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="941d1-119">Checks are performed for valid key/value pairs and an invalid pair throws an exception.</span></span> <span data-ttu-id="941d1-120">Buna ek olarak, eklenen değerler güvenli bir şekilde işlenir.</span><span class="sxs-lookup"><span data-stu-id="941d1-120">In addition, injected values are handled in a safe manner.</span></span>  
  
 <span data-ttu-id="941d1-121">Aşağıdaki örnek, <xref:System.Data.SqlClient.SqlConnectionStringBuilder> ayarı için ek bir ek değerin nasıl işlediğini gösterir `Initial Catalog` .</span><span class="sxs-lookup"><span data-stu-id="941d1-121">The following example demonstrates how the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> handles an inserted extra value for the `Initial Catalog` setting.</span></span>  
  
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
  
 <span data-ttu-id="941d1-122">Çıktı, bunu, <xref:System.Data.SqlClient.SqlConnectionStringBuilder> bağlantı dizesine yeni bir anahtar/değer çifti olarak eklemek yerine, ek değeri çift tırnak işareti içinde kaçış yoluyla doğru bir şekilde işlendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="941d1-122">The output shows that the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> handled this correctly by escaping the extra value in double quotation marks instead of appending it to the connection string as a new key/value pair.</span></span>  
  
```output  
data source=(local);Integrated Security=True;  
initial catalog="AdventureWorks;NewValue=Bad"  
```  
  
## <a name="building-connection-strings-from-configuration-files"></a><span data-ttu-id="941d1-123">Yapılandırma dosyalarından bağlantı dizeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="941d1-123">Building Connection Strings from Configuration Files</span></span>  
 <span data-ttu-id="941d1-124">Bir bağlantı dizesinin belirli öğeleri önceden biliniyorsa, bir yapılandırma dosyasında depolanabilir ve tamamen bir bağlantı dizesi oluşturmak için çalışma zamanında elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="941d1-124">If certain elements of a connection string are known beforehand, they can be stored in a configuration file and retrieved at run time to construct a complete connection string.</span></span> <span data-ttu-id="941d1-125">Örneğin, veritabanının adı önceden biliniyor olabilir, ancak sunucunun adı değildir.</span><span class="sxs-lookup"><span data-stu-id="941d1-125">For example, the name of the database might be known in advance, but not the name of the server.</span></span> <span data-ttu-id="941d1-126">Ya da bir kullanıcının, bağlantı dizesine diğer değerleri ekleyebilmeden çalışma zamanında bir ad ve parola vermesini isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="941d1-126">Or you might want a user to supply a name and password at run time without being able to inject other values into the connection string.</span></span>  
  
 <span data-ttu-id="941d1-127">Bir bağlantı dizesi oluşturucusunun aşırı yüklenmiş <xref:System.String> oluşturucularından biri, bir bağımsız değişken olarak alır. Bu, daha sonra Kullanıcı girişinden tamamlanabilir kısmi bir bağlantı dizesi sağlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="941d1-127">One of the overloaded constructors for a connection string builder takes a <xref:System.String> as an argument, which enables you to supply a partial connection string that can then be completed from user input.</span></span> <span data-ttu-id="941d1-128">Kısmi bağlantı dizesi bir yapılandırma dosyasında depolanabilir ve çalışma zamanında elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="941d1-128">The partial connection string can be stored in a configuration file and retrieved at run time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="941d1-129"><xref:System.Configuration>Ad alanı, <xref:System.Web.Configuration.WebConfigurationManager> Web uygulamaları Için ve Windows uygulamaları için kullanan yapılandırma dosyalarına programlı erişim sağlar <xref:System.Configuration.ConfigurationManager> .</span><span class="sxs-lookup"><span data-stu-id="941d1-129">The <xref:System.Configuration> namespace allows programmatic access to configuration files that use the <xref:System.Web.Configuration.WebConfigurationManager> for Web applications and the <xref:System.Configuration.ConfigurationManager> for Windows applications.</span></span> <span data-ttu-id="941d1-130">Bağlantı dizeleri ve yapılandırma dosyalarıyla çalışma hakkında daha fazla bilgi için bkz. [bağlantı dizeleri ve yapılandırma dosyaları](connection-strings-and-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="941d1-130">For more information about working with connection strings and configuration files, see [Connection Strings and Configuration Files](connection-strings-and-configuration-files.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="941d1-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="941d1-131">Example</span></span>  
 <span data-ttu-id="941d1-132">Bu örnek, bir yapılandırma dosyasından kısmi bağlantı dizesinin alınması ve <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A> öğesinin, ve özelliklerini ayarlayarak tamamlanışını gösterir <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> <xref:System.Data.SqlClient.SqlConnectionStringBuilder> .</span><span class="sxs-lookup"><span data-stu-id="941d1-132">This example demonstrates retrieving a partial connection string from a configuration file and completing it by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>, and <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> properties of the <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span> <span data-ttu-id="941d1-133">Yapılandırma dosyası aşağıdaki gibi tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="941d1-133">The configuration file is defined as follows.</span></span>  
  
```xml  
<connectionStrings>  
  <clear/>  
  <add name="partialConnectString"
    connectionString="Initial Catalog=Northwind;"  
    providerName="System.Data.SqlClient" />  
</connectionStrings>  
```  
  
> [!NOTE]
> <span data-ttu-id="941d1-134">Kodun çalışması için projenizdeki öğesine bir başvuru ayarlamanız gerekir `System.Configuration.dll` .</span><span class="sxs-lookup"><span data-stu-id="941d1-134">You must set a reference to the `System.Configuration.dll` in your project for the code to run.</span></span>  
  
 [!code-csharp[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/CS/source.cs#1)]
 [!code-vb[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="941d1-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="941d1-135">See also</span></span>

- [<span data-ttu-id="941d1-136">Bağlantı dizeleri</span><span class="sxs-lookup"><span data-stu-id="941d1-136">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="941d1-137">Gizlilik ve Veri Güvenliği</span><span class="sxs-lookup"><span data-stu-id="941d1-137">Privacy and Data Security</span></span>](privacy-and-data-security.md)
- [<span data-ttu-id="941d1-138">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="941d1-138">ADO.NET Overview</span></span>](ado-net-overview.md)
