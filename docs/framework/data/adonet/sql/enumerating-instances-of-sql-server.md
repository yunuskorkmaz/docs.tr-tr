---
title: SQL Server (ADO.NET) Numaralandırma Örnekleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
ms.openlocfilehash: a723679fe18352e115df78af72975097dc28b617
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59162861"
---
# <a name="enumerating-instances-of-sql-server-adonet"></a>SQL Server (ADO.NET) Numaralandırma Örnekleri
SQL Server, geçerli ağ içinde SQL Server örneklerini bulmak için uygulamaların izin verir. <xref:System.Data.Sql.SqlDataSourceEnumerator> Sınıfı sağlayarak uygulama geliştiricisi, bu bilgileri sunan bir <xref:System.Data.DataTable> görünür olan tüm sunucular hakkında bilgiler içeren. Bu tablo, ağ üzerinde yer alan bir kullanıcı yeni bir bağlantı oluşturmak çalıştığında sağlanan listesiyle eşleşen ve üzerinde kullanılabilen tüm sunucuları içeren aşağı açılan liste genişletir kullanılabilir sunucu örneklerinin bir listesini içeren döndürülen **bağlantı Özellikleri** iletişim kutusu. Görüntülenen sonuçlar her zaman eksiksiz değildir.  
  
> [!NOTE]
>  Olarak çoğu Windows hizmetlerle olabildiğince az ayrıcalıklarıyla SQL Browser hizmeti çalıştırmak en iyisidir. SQL Browser hizmeti ve davranışını yönetmek nasıl daha fazla bilgi için SQL Server Books Online'a bakın.  
  
## <a name="retrieving-an-enumerator-instance"></a>Numaralandırıcı örnek alıyor  
 Kullanılabilir SQL Server örnekleri hakkında bilgi içeren tablo almak için ilk paylaşılan /'using static Numaralandırıcı alınması gerekir <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> özelliği:  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =   
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 Statik örneği aldıktan sonra çağırabilirsiniz <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> döndüren yöntemi bir <xref:System.Data.DataTable> kullanılabilir sunucular hakkında bilgiler içeren:  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 Yöntem çağrısından döndürülen tablo tümünü içeren şu sütunları içeren `string` değerleri:  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**SunucuAdı**|Sunucusunun adı.|  
|**InstanceName**|Sunucu örneğinin adı. Sunucu varsayılan örnek olarak çalışıyorsa boş.|  
|**IsClustered**|Sunucu bir kümenin parçası olup olmadığını belirtir.|  
|**Sürüm**|Sunucu sürümü. Örneğin:<br /><br /> -9.00.x ([!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)])<br />-   10.0.xx ([!INCLUDE[ssKatmai](../../../../../includes/sskatmai-md.md)])<br />-   10.50.x ([!INCLUDE[ssKilimanjaro](../../../../../includes/sskilimanjaro-md.md)])<br />-   11.0.xx (SQL Server 2012)|  
  
## <a name="enumeration-limitations"></a>Sabit listesi sınırlamaları  
 Tüm kullanılabilir sunucular olabilir ya da listelenmez. Liste, zaman aşımları ve ağ trafiği gibi faktörlere bağlı olarak değişebilir. Bu iki ardışık çağrılarda farklı olacak şekilde liste neden olabilir. Yalnızca aynı ağ üzerinde sunucuları listelenir. Yayın paketleri genellikle yönlendiriciler, listelenen bir sunucu göremeyebilirsiniz neden olduğu geçiş olmaz ancak çağrıları arasında tutarlı olur.  
  
 Listelenen sunucuları gibi ek bilgi olmayabilir veya `IsClustered` ve sürüm. Bu listenin nasıl edinilen bağlıdır. SQL Server browser hizmeti listelenen sunucuları yalnızca adını listeler Windows altyapısı aracılığıyla bulunan olandan daha fazla ayrıntı sahip olur.  
  
> [!NOTE]
>  Sunucu sabit listesi, yalnızca tam güvende çalıştırıldığında, kullanılabilir. Sahip oldukları bile kısmen güvenilen bir ortamda çalışan derlemeler, kullanmanız mümkün olmayacak <xref:System.Data.SqlClient.SqlClientPermission> kod erişim güvenliği (CAS) iznini.  
  
 SQL Server için bilgileri sağlar <xref:System.Data.Sql.SqlDataSourceEnumerator> SQL Browser adlı bir dış Windows hizmet kullanımı. Bu hizmet, varsayılan olarak etkindir, ancak yöneticilerin kapatmak veya, sunucu örneği için bu sınıf görünmez yapma devre dışı bırakın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki konsol uygulamasında tüm görünür SQL Server örnekleri hakkında bilgi alır ve bilgileri konsol penceresinde görüntüler.  
  
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

- [SQL Server ve ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
