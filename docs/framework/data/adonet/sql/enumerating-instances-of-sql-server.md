---
title: "SQL Server (ADO.NET) örneklerini numaralandırma"
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
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
caps.latest.revision: "8"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 7b0a81fd9b92e626b52c5a74c65798ddedbd94a9
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="enumerating-instances-of-sql-server-adonet"></a>SQL Server (ADO.NET) örneklerini numaralandırma
[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]bulunacak uygulamaları verir [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] geçerli ağ içindeki örnekleri. <xref:System.Data.Sql.SqlDataSourceEnumerator> Sınıfı sağlayan uygulama geliştiricisi, bu bilgileri sunan bir <xref:System.Data.DataTable> görünür tüm sunucuları hakkında bilgi içeren. Bu tablo bir kullanıcı yeni bir bağlantı oluşturmak çalıştığında sağlanan listesiyle eşleşen ve üzerindeki tüm kullanılabilir sunuculara içeren aşağı açılır liste genişleten ağda kullanılabilir sunucu örneklerinin bir listesini içeren döndürülen **bağlantı Özellikler** iletişim kutusu. Gösterilen sonuçları her zaman eksiksiz değildir.  
  
> [!NOTE]
>  Olarak çoğu Windows Hizmetleri ile mümkün olan en küçük ayrıcalıklarıyla SQL Browser hizmeti çalıştırmak en iyisidir. Bkz: [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] SQL Browser hizmeti hakkında daha fazla bilgi için Books Online'a ve davranışını yönetme.  
  
## <a name="retrieving-an-enumerator-instance"></a>Numaralandırıcı örnek alıyor  
 Kullanılabilir hakkında bilgi içeren tablo almak için [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] örnekleri, paylaşılan/statik kullanarak bir numaralandırıcı ilk almak gerekir <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> özelliği:  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =   
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 Statik örnek aldıktan sonra çağırabilirsiniz <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> döndürür yöntemi bir <xref:System.Data.DataTable> kullanılabilir sunucuları hakkında bilgi içeren:  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 Yöntemi çağrısından döndürülen tablosu da içeren şu sütunları içerir `string` değerler:  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**ServerName**|Sunucunun adıdır.|  
|**InstanceName**|Sunucu örneğinin adı. Sunucunun varsayılan örneği olarak çalışıyorsa, boş.|  
|**IsClustered**|Sunucu bir kümenin parçası olup olmadığını gösterir.|  
|**Sürüm**|Sunucu sürümü. Örneğin:<br /><br /> -   9.00.x ([!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)])<br />-   10.0.xx ([!INCLUDE[ssKatmai](../../../../../includes/sskatmai-md.md)])<br />-   10.50.x ([!INCLUDE[ssKilimanjaro](../../../../../includes/sskilimanjaro-md.md)])<br />-   11.0.xx ([!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012)|  
  
## <a name="enumeration-limitations"></a>Numaralandırma sınırlamaları  
 Tüm kullanılabilir sunuculara olabilir ya da listelenmez. Liste zaman aşımları ve ağ trafiğini gibi etkenlere bağlı olarak değişebilir. Bu listenin iki ardışık çağrılarını farklı olması neden olabilir. Yalnızca aynı ağ üzerinde sunucuları listelenir. Yayın paketleri genellikle yönlendiriciler, listelenen bir sunucu göremeyebilirsiniz neden olduğu çapraz olmaz ancak çağrıları arasında dengeli olur.  
  
 Listelenen sunucuların olabilir veya ek bilgiler gibi olmayabilir `IsClustered` ve sürüm. Bu listeyi nasıl edinilen bağlıdır. Aracılığıyla listelenen sunucuları [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Tarayıcı hizmeti, yalnızca adını listeler Windows altyapısı bulunan olandan daha fazla ayrıntı olacaktır.  
  
> [!NOTE]
>  Sunucu numaralandırma, yalnızca tam güvende çalıştırılırken kullanılabilir. Kısmen güvenilen bir ortamda çalışan derlemeleri edemeyecek, kullanılacak sahip oldukları olsa bile <xref:System.Data.SqlClient.SqlClientPermission> kod erişim güvenliği (CAS) izni.  
  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]için bilgiler sağlar <xref:System.Data.Sql.SqlDataSourceEnumerator> SQL Browser adlı bir dış Windows hizmeti kullanımı ile. Bu hizmet varsayılan olarak etkindir, ancak yöneticilerin kapatın veya, sunucu örneği için bu sınıf görünmez yapma devre dışı bırakın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki konsol uygulaması görünür tüm ilgili bilgileri alır [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] örnekler ve bilgiler konsol penceresinde görüntüler.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server ve ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
