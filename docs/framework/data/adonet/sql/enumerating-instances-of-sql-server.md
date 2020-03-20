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
# <a name="enumerating-instances-of-sql-server-adonet"></a>SQL Server (ADO.NET) Numaralandırma Örnekleri
SQL Server, uygulamaların geçerli ağ içinde SQL Server örneklerini bulmasına izin verir. Sınıf, <xref:System.Data.Sql.SqlDataSourceEnumerator> bu bilgileri uygulama geliştiricisine açıklayarak <xref:System.Data.DataTable> görünür tüm sunucular hakkında bilgi sağlar. Bu döndürülen tablo, ağda bulunan ve kullanıcı yeni bir bağlantı oluşturmaya çalıştığında sağlanan listeyle eşleşen sunucu örneklerinin bir listesini içerir ve **Bağlantı Özellikleri** iletişim kutusundaki tüm kullanılabilir sunucuları içeren açılır listeyi genişletir. Görüntülenen sonuçlar her zaman tam değildir.  
  
> [!NOTE]
> Çoğu Windows hizmetinde olduğu gibi, SQL Browser hizmetini mümkün olan en az ayrıcalıkla çalıştırmak en iyisidir. SQL Browser hizmeti hakkında daha fazla bilgi ve davranışını nasıl yönetirebildiğini öğrenmek için SQL Server Books Online'a bakın.  
  
## <a name="retrieving-an-enumerator-instance"></a>Bir Umerator Örneği Alma  
 Kullanılabilir SQL Server örnekleri hakkında bilgi içeren tabloyu almak için, paylaşılan/statik <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> özelliği kullanarak önce bir bir yer umeratör almanız gerekir:  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 Statik örneği aldıktan sonra, kullanılabilir sunucular <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> hakkında <xref:System.Data.DataTable> bilgi sağlayan yöntemi arayabilirsiniz:  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 Yöntem çağrısından döndürülen tablo, tümü değerleri içeren `string` aşağıdaki sütunları içerir:  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Sunucuadı**|Sunucunun adı.|  
|**Örnekadı**|Sunucu örneğinin adı. Sunucu varsayılan örnek olarak çalışıyorsa boş.|  
|**ısclustered**|Sunucunun kümenin bir parçası olup olmadığını gösterir.|  
|**Sürüm**|Sunucunun sürümü. Örnek:<br /><br /> - 9.00.x (SQL Server 2005)<br />- 10.0.xx (SQL Server 2008)<br />- 10.50.x (SQL Server 2008 R2)<br />- 11.0.xx (SQL Server 2012)|  
  
## <a name="enumeration-limitations"></a>Numaralandırma Sınırlamaları  
 Kullanılabilir sunucuların tümü listelenebilir veya listelenmemiş olabilir. Liste, zaman ekmeleri ve ağ trafiği gibi etkenlere bağlı olarak değişebilir. Bu, listenin art arda iki çağrıda farklı olmasını sağlayabilir. Yalnızca aynı ağdaki sunucular listelenir. Yayın paketleri genellikle yönlendiriciler arasında geçiş yapmaz, bu nedenle listelenen bir sunucu göremeyebilirsiniz, ancak aramalar arasında kararlı olacaktır.  
  
 Listelenen sunucular, sürüm ve sürüm `IsClustered` gibi ek bilgilere sahip olabilir veya olmayabilir. Bu, listenin nasıl elde edildiğine bağlıdır. SQL Server tarayıcı hizmeti nde listelenen sunucular, yalnızca adı listeleyen Windows altyapısında bulunanlardan daha fazla ayrıntıya sahip olacaktır.  
  
> [!NOTE]
> Sunucu numaralandırma yalnızca tam güven içinde çalışırken kullanılabilir. <xref:System.Data.SqlClient.SqlClientPermission> Kısmen güvenilen bir ortamda çalışan derlemeler, Kod Erişim Güvenliği (CAS) iznine sahip olsalar bile bu derlemeyi kullanamaz.  
  
 SQL Server, SQL <xref:System.Data.Sql.SqlDataSourceEnumerator> Browser adlı harici bir Windows hizmetinin kullanımı yoluyla bilgi sağlar. Bu hizmet varsayılan olarak etkinleştirilir, ancak yöneticiler sunucu örneğini bu sınıf için görünmez hale getirerek bu hizmeti kapatabilir veya devre dışı bırakabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki konsol uygulaması, görünen TÜM SQL Server örnekleri hakkında bilgi alır ve konsol penceresindeki bilgileri görüntüler.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server ve ADO.NET](index.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
