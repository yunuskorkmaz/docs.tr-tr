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
# <a name="connection-string-builders"></a>Bağlantı Dizesi Oluşturucular
Önceki ADO.NET sürümlerinde, birleştirilmiş dize değerleriyle bağlantı dizeleri derleme zamanı denetimi gerçekleşmediğinden, çalışma zamanında yanlış bir anahtar sözcük oluşturulur <xref:System.ArgumentException> . .NET Framework veri sağlayıcılarının her biri, el ile yapıldıysa geçerli bağlantı dizeleri oluşturmak için bağlantı dizesi anahtar sözcükleri için farklı sözdizimi destekliyordu. Bu sorunu gidermek için, ADO.NET 2,0 her bir .NET Framework veri sağlayıcısı için yeni bağlantı dizesi oluşturucuları sunmuştur. Her veri sağlayıcısı, öğesinden devralan türü kesin belirlenmiş bir bağlantı dizesi Oluşturucu sınıfı içerir <xref:System.Data.Common.DbConnectionStringBuilder> . Aşağıdaki tabloda .NET Framework veri sağlayıcıları ve ilişkili bağlantı dizesi Oluşturucu sınıfları listelenmektedir.  
  
|Sağlayıcı|ConnectionStringBuilder sınıfı|  
|--------------|-----------------------------------|  
|<xref:System.Data.SqlClient>|<xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OleDb>|<xref:System.Data.OleDb.OleDbConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.Odbc>|<xref:System.Data.Odbc.OdbcConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OracleClient>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|  
  
## <a name="connection-string-injection-attacks"></a>Bağlantı dizesi ekleme saldırıları  
 Bir bağlantı dizesi ekleme saldırısı, Kullanıcı girişini temel alan bağlantı dizelerini oluşturmak için dinamik dize birleştirme kullanıldığında meydana gelebilir. Dize doğrulanmaz ve kötü amaçlı metin veya karakterler atlanmaz, bir saldırgan sunucudaki hassas verilere veya diğer kaynaklara erişebilir. Örneğin, bir saldırgan noktalı virgül sağlayarak ve ek bir değer ekleyerek bir saldırı bağlayabilir. Bağlantı dizesi bir "son bir WINS" algoritması kullanılarak ayrıştırılır ve saldırgan girişi, meşru bir değer için değiştirilir.  
  
 Bağlantı dizesi Oluşturucu sınıfları, tahmin etmeyi ortadan kaldırmak ve söz dizimi hatalarına ve güvenlik açıklarına karşı korumak için tasarlanmıştır. Her veri sağlayıcısı tarafından izin verilen bilinen anahtar/değer çiftlerine karşılık gelen yöntemleri ve özellikleri sağlarlar. Her sınıf, sabit bir eş anlamlı koleksiyonu saklar ve bir eş anlamadan ilgili iyi bilinen anahtar adına çevirebilir. Geçerli anahtar/değer çiftleri için denetimler gerçekleştirilir ve geçersiz bir çift özel durum oluşturur. Buna ek olarak, eklenen değerler güvenli bir şekilde işlenir.  
  
 Aşağıdaki örnek, <xref:System.Data.SqlClient.SqlConnectionStringBuilder> ayarı için ek bir ek değerin nasıl işlediğini gösterir `Initial Catalog` .  
  
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
  
 Çıktı, bunu, <xref:System.Data.SqlClient.SqlConnectionStringBuilder> bağlantı dizesine yeni bir anahtar/değer çifti olarak eklemek yerine, ek değeri çift tırnak işareti içinde kaçış yoluyla doğru bir şekilde işlendiğini gösterir.  
  
```output  
data source=(local);Integrated Security=True;  
initial catalog="AdventureWorks;NewValue=Bad"  
```  
  
## <a name="building-connection-strings-from-configuration-files"></a>Yapılandırma dosyalarından bağlantı dizeleri oluşturma  
 Bir bağlantı dizesinin belirli öğeleri önceden biliniyorsa, bir yapılandırma dosyasında depolanabilir ve tamamen bir bağlantı dizesi oluşturmak için çalışma zamanında elde edilebilir. Örneğin, veritabanının adı önceden biliniyor olabilir, ancak sunucunun adı değildir. Ya da bir kullanıcının, bağlantı dizesine diğer değerleri ekleyebilmeden çalışma zamanında bir ad ve parola vermesini isteyebilirsiniz.  
  
 Bir bağlantı dizesi oluşturucusunun aşırı yüklenmiş <xref:System.String> oluşturucularından biri, bir bağımsız değişken olarak alır. Bu, daha sonra Kullanıcı girişinden tamamlanabilir kısmi bir bağlantı dizesi sağlamanıza olanak sağlar. Kısmi bağlantı dizesi bir yapılandırma dosyasında depolanabilir ve çalışma zamanında elde edilebilir.  
  
> [!NOTE]
> <xref:System.Configuration>Ad alanı, <xref:System.Web.Configuration.WebConfigurationManager> Web uygulamaları Için ve Windows uygulamaları için kullanan yapılandırma dosyalarına programlı erişim sağlar <xref:System.Configuration.ConfigurationManager> . Bağlantı dizeleri ve yapılandırma dosyalarıyla çalışma hakkında daha fazla bilgi için bkz. [bağlantı dizeleri ve yapılandırma dosyaları](connection-strings-and-configuration-files.md).  
  
### <a name="example"></a>Örnek  
 Bu örnek, bir yapılandırma dosyasından kısmi bağlantı dizesinin alınması ve <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A> öğesinin, ve özelliklerini ayarlayarak tamamlanışını gösterir <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> <xref:System.Data.SqlClient.SqlConnectionStringBuilder> . Yapılandırma dosyası aşağıdaki gibi tanımlanır.  
  
```xml  
<connectionStrings>  
  <clear/>  
  <add name="partialConnectString"
    connectionString="Initial Catalog=Northwind;"  
    providerName="System.Data.SqlClient" />  
</connectionStrings>  
```  
  
> [!NOTE]
> Kodun çalışması için projenizdeki öğesine bir başvuru ayarlamanız gerekir `System.Configuration.dll` .  
  
 [!code-csharp[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/CS/source.cs#1)]
 [!code-vb[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantı dizeleri](connection-strings.md)
- [Gizlilik ve Veri Güvenliği](privacy-and-data-security.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
