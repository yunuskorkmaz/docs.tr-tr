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
# <a name="connection-string-builders"></a>Bağlantı Dizesi Oluşturucular
ADO.NET önceki sürümlerinde, sıkıştırılmış dize değerlerine sahip bağlantı dizelerinin derleme zamanı denetimi gerçekleşmedi, böylece çalışma <xref:System.ArgumentException>zamanında yanlış bir anahtar kelime bir . .NET Framework veri sağlayıcılarının her biri, bağlantı dizeanahtar kelimeleri için farklı sözdizimini destekleyerek, el ile yapıldığında geçerli bağlantı dizeleri oluşturmayı zorlaştırdı. Bu sorunu gidermek için, ADO.NET 2.0 her .NET Framework veri sağlayıcısı için yeni bağlantı dize oluşturucuları tanıttı. Her veri sağlayıcısı, 'den <xref:System.Data.Common.DbConnectionStringBuilder>devralan güçlü bir şekilde yazılan bağlantı dize oluşturucu sınıfiçerir. Aşağıdaki tabloda .NET Framework veri sağlayıcıları ve ilişkili bağlantı dize oluşturucu sınıfları listeleneb..  
  
|Sağlayıcı|ConnectionStringBuilder sınıfı|  
|--------------|-----------------------------------|  
|<xref:System.Data.SqlClient>|<xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OleDb>|<xref:System.Data.OleDb.OleDbConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.Odbc>|<xref:System.Data.Odbc.OdbcConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OracleClient>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|  
  
## <a name="connection-string-injection-attacks"></a>Bağlantı String Enjeksiyon Saldırıları  
 Dinamik dize concatenation kullanıcı girişine dayalı bağlantı dizeleri oluşturmak için kullanıldığında bir bağlantı dize enjeksiyon saldırı oluşabilir. Dize doğrulanmadıysa ve kötü amaçlı metin veya karakterler kaçmazsa, saldırgan hassas verilere veya sunucudaki diğer kaynaklara erişebilir. Örneğin, bir saldırgan bir yarı kolon sağlayarak ve ek bir değer ekleyerek bir saldırı monte edebilirim. Bağlantı dizesi "son bir kazanır" algoritması kullanılarak ayrıştırılır ve düşman girişi meşru bir değerle değiştirilir.  
  
 Bağlantı dizesi oluşturucu sınıfları, tahmin çalışmalarını ortadan kaldırmak ve sözdizimi hatalarına ve güvenlik açıklarına karşı korumak için tasarlanmıştır. Her veri sağlayıcısı tarafından izin verilen bilinen anahtar/değer çiftleri ile karşılık gelen yöntemler ve özellikler sağlarlar. Her sınıf eşanlamlısabit bir koleksiyon tutar ve ilgili iyi bilinen anahtar adı için eşanlamlı tercüme edebilirsiniz. Geçerli anahtar/değer çiftleri için denetimler yapılır ve geçersiz bir çift bir özel durum oluşturur. Buna ek olarak, enjekte edilen değerler güvenli bir şekilde işlenir.  
  
 Aşağıdaki örnek, <xref:System.Data.SqlClient.SqlConnectionStringBuilder> `Initial Catalog` ayarı için eklenen bir ek değeri nasıl işlettiğini gösterir.  
  
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
  
 Çıktı, bağlantı <xref:System.Data.SqlClient.SqlConnectionStringBuilder> dizesine yeni bir anahtar/değer çifti olarak eklemek yerine çift tırnak işaretlerindeki ekstra değerden kaçarak bunu doğru bir şekilde ele aldığımı gösterir.  
  
```output  
data source=(local);Integrated Security=True;  
initial catalog="AdventureWorks;NewValue=Bad"  
```  
  
## <a name="building-connection-strings-from-configuration-files"></a>Yapılandırma Dosyalarından Bağlantı Dizeleri Oluşturma  
 Bir bağlantı dizesinin belirli öğeleri önceden biliniyorsa, yapılandırma dosyasında depolanabilir ve tam bir bağlantı dizesi oluşturmak için çalışma zamanında alınabilir. Örneğin, veritabanının adı önceden bilinebilir, ancak sunucunun adı bilinmez. Veya bir kullanıcının bağlantı dizesine diğer değerleri enjekte etmeden çalışma zamanında bir ad ve parola sağlamasını isteyebilirsiniz.  
  
 Bir bağlantı dize oluşturucu için aşırı yüklü <xref:System.String> oluşturucular biri daha sonra kullanıcı girişi tamamlanabilir kısmi bir bağlantı dizesi kaynağı sağlayan bir bağımsız değişken olarak alır. Kısmi bağlantı dizesi bir yapılandırma dosyasında depolanabilir ve çalışma zamanında alınabilir.  
  
> [!NOTE]
> Ad <xref:System.Configuration> alanı, Web uygulamaları ve Windows <xref:System.Web.Configuration.WebConfigurationManager> uygulamaları <xref:System.Configuration.ConfigurationManager> için kullanılan yapılandırma dosyalarına programlı erişim sağlar. Bağlantı dizeleri ve yapılandırma dosyalarıyla çalışma hakkında daha fazla bilgi için [Bağlantı Dizeleri ve Yapılandırma Dosyaları'na](connection-strings-and-configuration-files.md)bakın.  
  
### <a name="example"></a>Örnek  
 Bu örnek, bir yapılandırma dosyasından kısmi bir bağlantı dizesi <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>alma <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>ve <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> , <xref:System.Data.SqlClient.SqlConnectionStringBuilder>, ve özelliklerini ayarlayarak tamamlayarak gösterir . Yapılandırma dosyası aşağıdaki gibi tanımlanır.  
  
```xml  
<connectionStrings>  
  <clear/>  
  <add name="partialConnectString"
    connectionString="Initial Catalog=Northwind;"  
    providerName="System.Data.SqlClient" />  
</connectionStrings>  
```  
  
> [!NOTE]
> Kodun çalışması için `System.Configuration.dll` projenizdeki başvuruyu ayarlamanız gerekir.  
  
 [!code-csharp[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/CS/source.cs#1)]
 [!code-vb[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantı Dizeleri](connection-strings.md)
- [Gizlilik ve Veri Güvenliği](privacy-and-data-security.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
