---
title: Bağlantı Dizesi Oluşturucular
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8434b608-c4d3-43d3-8ae3-6d8c6b726759
ms.openlocfilehash: afafe5d1eaddaef3b9f0069908b365e40ea4ed29
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785689"
---
# <a name="connection-string-builders"></a>Bağlantı Dizesi Oluşturucular
Önceki ADO.NET sürümlerinde, birleştirilmiş dize değerleriyle bağlantı dizeleri derleme zamanı denetimi gerçekleşmediğinden, çalışma zamanında yanlış bir anahtar sözcük oluşturulur <xref:System.ArgumentException>. .NET Framework veri sağlayıcılarının her biri, el ile yapıldıysa geçerli bağlantı dizeleri oluşturmak için bağlantı dizesi anahtar sözcükleri için farklı sözdizimi destekliyordu. Bu sorunu gidermek için, ADO.NET 2,0 her bir .NET Framework veri sağlayıcısı için yeni bağlantı dizesi oluşturucuları sunmuştur. Her veri sağlayıcısı, öğesinden <xref:System.Data.Common.DbConnectionStringBuilder>devralan türü kesin belirlenmiş bir bağlantı dizesi Oluşturucu sınıfı içerir. Aşağıdaki tabloda .NET Framework veri sağlayıcıları ve ilişkili bağlantı dizesi Oluşturucu sınıfları listelenmektedir.  
  
|Sağlayıcı|ConnectionStringBuilder sınıfı|  
|--------------|-----------------------------------|  
|<xref:System.Data.SqlClient>|<xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OleDb>|<xref:System.Data.OleDb.OleDbConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.Odbc>|<xref:System.Data.Odbc.OdbcConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OracleClient>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|  
  
## <a name="connection-string-injection-attacks"></a>Bağlantı dizesi ekleme saldırıları  
 Bir bağlantı dizesi ekleme saldırısı, Kullanıcı girişini temel alan bağlantı dizelerini oluşturmak için dinamik dize birleştirme kullanıldığında meydana gelebilir. Dize doğrulanmaz ve kötü amaçlı metin veya karakterler atlanmaz, bir saldırgan sunucudaki hassas verilere veya diğer kaynaklara erişebilir. Örneğin, bir saldırgan noktalı virgül sağlayarak ve ek bir değer ekleyerek bir saldırı bağlayabilir. Bağlantı dizesi bir "son bir WINS" algoritması kullanılarak ayrıştırılır ve saldırgan girişi, meşru bir değer için değiştirilir.  
  
 Bağlantı dizesi Oluşturucu sınıfları, tahmin etmeyi ortadan kaldırmak ve söz dizimi hatalarına ve güvenlik açıklarına karşı korumak için tasarlanmıştır. Her veri sağlayıcısı tarafından izin verilen bilinen anahtar/değer çiftlerine karşılık gelen yöntemleri ve özellikleri sağlarlar. Her sınıf, sabit bir eş anlamlı koleksiyonu saklar ve bir eş anlamadan ilgili iyi bilinen anahtar adına çevirebilir. Geçerli anahtar/değer çiftleri için denetimler gerçekleştirilir ve geçersiz bir çift özel durum oluşturur. Buna ek olarak, eklenen değerler güvenli bir şekilde işlenir.  
  
 Aşağıdaki örnek, <xref:System.Data.SqlClient.SqlConnectionStringBuilder> `Initial Catalog` ayarı için ek bir ek değerin nasıl işlediğini gösterir.  
  
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
  
 Çıktı, bunu, bağlantı <xref:System.Data.SqlClient.SqlConnectionStringBuilder> dizesine yeni bir anahtar/değer çifti olarak eklemek yerine, ek değeri çift tırnak işareti içinde kaçış yoluyla doğru bir şekilde işlendiğini gösterir.  
  
```  
data source=(local);Integrated Security=True;  
initial catalog="AdventureWorks;NewValue=Bad"  
```  
  
## <a name="building-connection-strings-from-configuration-files"></a>Yapılandırma dosyalarından bağlantı dizeleri oluşturma  
 Bir bağlantı dizesinin belirli öğeleri önceden biliniyorsa, bir yapılandırma dosyasında depolanabilir ve tamamen bir bağlantı dizesi oluşturmak için çalışma zamanında elde edilebilir. Örneğin, veritabanının adı önceden biliniyor olabilir, ancak sunucunun adı değildir. Ya da bir kullanıcının, bağlantı dizesine diğer değerleri ekleyebilmeden çalışma zamanında bir ad ve parola vermesini isteyebilirsiniz.  
  
 Bir bağlantı dizesi oluşturucusunun aşırı yüklenmiş oluşturucularından biri, bir <xref:System.String> bağımsız değişken olarak alır. Bu, daha sonra Kullanıcı girişinden tamamlanabilir kısmi bir bağlantı dizesi sağlamanıza olanak sağlar. Kısmi bağlantı dizesi bir yapılandırma dosyasında depolanabilir ve çalışma zamanında elde edilebilir.  
  
> [!NOTE]
> Ad alanı, Web uygulamaları <xref:System.Web.Configuration.WebConfigurationManager> <xref:System.Configuration.ConfigurationManager> için ve Windows uygulamaları için kullanan yapılandırma dosyalarına programlı erişim sağlar. <xref:System.Configuration> Bağlantı dizeleri ve yapılandırma dosyalarıyla çalışma hakkında daha fazla bilgi için bkz. [bağlantı dizeleri ve yapılandırma dosyaları](connection-strings-and-configuration-files.md).  
  
### <a name="example"></a>Örnek  
 Bu örnek, bir yapılandırma dosyasından kısmi bağlantı dizesinin alınması <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>ve öğesinin <xref:System.Data.SqlClient.SqlConnectionStringBuilder>, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>ve <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> özelliklerini ayarlayarak tamamlanışını gösterir. Yapılandırma dosyası aşağıdaki gibi tanımlanır.  
  
```xml  
<connectionStrings>  
  <clear/>  
  <add name="partialConnectString"   
    connectionString="Initial Catalog=Northwind;"  
    providerName="System.Data.SqlClient" />  
</connectionStrings>  
```  
  
> [!NOTE]
> Kodun çalışması için projenizdeki öğesine `System.Configuration.dll` bir başvuru ayarlamanız gerekir.  
  
 [!code-csharp[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/CS/source.cs#1)]
 [!code-vb[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantı Dizeleri](connection-strings.md)
- [Gizlilik ve Veri Güvenliği](privacy-and-data-security.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
