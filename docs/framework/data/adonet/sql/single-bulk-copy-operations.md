---
title: Tekil toplu kopyalama işlemleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
ms.openlocfilehash: 274a6e87b272002a567fd92605c4e690c03b6e26
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43884175"
---
# <a name="single-bulk-copy-operations"></a>Tekil toplu kopyalama işlemleri
Bir SQL Server toplu kopyalama işlemi gerçekleştirmek için en kolay yaklaşım, bir veritabanında tek bir işlem gerçekleştirmektir. Varsayılan olarak, toplu kopyalama işlemi yalıtılmış bir işlem olarak gerçekleştirilir: yedekleme, geri fırsat ile işlem temelli olmayan bir şekilde, kopyalama işlemi gerçekleşir.  
  
> [!NOTE]
>  Bir hata oluştuğunda toplu kopyalama bir kısmını veya tamamını geri alma gerekiyorsa kullanabilirsiniz bir <xref:System.Data.SqlClient.SqlBulkCopy>-yönetilen işlem veya mevcut bir işlem içinde toplu kopyalama işlemi gerçekleştirin. **SqlBulkCopy** birlikte çalışacağı <xref:System.Transactions> bağlantı (örtük veya açık) olarak kayıtlı değilse bir **System.Transactions** işlem.  
>   
>  Daha fazla bilgi için [işlem ve toplu kopyalama işlemleri](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md).  
  
 Toplu kopyalama işlemi gerçekleştirmeye yönelik genel adımlar aşağıdaki gibidir:  
  
1.  Kaynak sunucuya bağlanın ve kopyalanacak verileri alın. Veri de gelebilir başka kaynaklardan gelen alınamazsa bir <xref:System.Data.IDataReader> veya <xref:System.Data.DataTable> nesne.  
  
2.  Hedef sunucuya (istediğiniz sürece **SqlBulkCopy** sizin için bir bağlantı kurmak için).  
  
3.  Oluşturma bir <xref:System.Data.SqlClient.SqlBulkCopy> nesne, tüm gerekli özellikleri ayarlama.  
  
4.  Ayarlama **DestinationTableName** hedef tablosu için toplu belirtmek için özelliği ekleme işlemi.  
  
5.  Birini çağırın **WriteToServer** yöntemleri.  
  
6.  İsteğe bağlı olarak, özellikleri ve arama güncelleştirmesi **WriteToServer** gerektiği şekilde yeniden.  
  
7.  Çağrı <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>, veya toplu kopyalama işlemleri içinde sarmalamak bir `Using` deyimi.  
  
> [!CAUTION]
>  Kaynak ve hedef sütun veri türlerini eşleşmesini öneririz. Veri türleri eşleşmiyorsa **SqlBulkCopy** her kaynak değeri tarafından kullanılan kuralları kullanarak hedef veri türüne dönüştürmeye çalışır <xref:System.Data.SqlClient.SqlParameter.Value%2A>. Dönüştürmeleri performansını etkileyebilir ve ayrıca beklenmeyen hatalara yol açabilir. Örneğin, bir `Double` veri türüne dönüştürülebilir bir `Decimal` veri türü çoğu zaman ama her zaman kullanılmaz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki konsol uygulaması kullanarak verileri yüklemek gösterilmiştir <xref:System.Data.SqlClient.SqlBulkCopy> sınıfı. Bu örnekte, bir <xref:System.Data.SqlClient.SqlDataReader> veri kopyalamak için kullanılan **Production.Product** tablo SQL Server'daki**AdventureWorks** benzer bir tabloya aynı veritabanında veritabanı.  
  
> [!IMPORTANT]
>  Bu örnekte açıklandığı gibi çalışma tabloları oluşturmadığınız sürece çalışmaz [toplu kopyalama örnek Kurulumu](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Bu kodu kullanmaya ilişkin sözdizimini göstermek için sağlanan **SqlBulkCopy** yalnızca. Kaynak ve hedef tablo aynı SQL Server örneğinde bulunuyorsa daha kolay ve hızlı bir Transact-SQL kullanmak için bunu `INSERT … SELECT` verileri kopyalamak için deyimi.  
  
 [!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
 [!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]  
  
## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a>Transact-SQL ve komut sınıfı kullanarak toplu kopyalama işlemi gerçekleştirme  
 Aşağıdaki örnekte nasıl kullanılacağı gösterilmektedir <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> BULK INSERT deyimini yürütmek için yöntemi.  
  
> [!NOTE]
>  Veri kaynağı için dosya sunucusuna göreli yoludur. Toplu kopyalama işleminin başarılı olması için sunucu işlemi bu yola erişimi olması gerekir.  
  
```vb  
Using connection As SqlConnection = New SqlConnection(connectionString)  
Dim queryString As String = _  
    "BULK INSERT Northwind.dbo.[Order Details] FROM " & _  
    "'f:\mydata\data.tbl' WITH (FORMATFILE='f:\mydata\data.fmt' )"  
connection.Open()  
SqlCommand command = New SqlCommand(queryString, connection);  
  
command.ExecuteNonQuery()  
End Using  
```  
  
```csharp  
using (SqlConnection connection = New SqlConnection(connectionString))  
{  
string queryString =  "BULK INSERT Northwind.dbo.[Order Details] " +  
    "FROM 'f:\mydata\data.tbl' " +  
    "WITH ( FORMATFILE='f:\mydata\data.fmt' )";  
connection.Open();  
SqlCommand command = new SqlCommand(queryString, connection);  
  
command.ExecuteNonQuery();  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server’da Toplu Kopyalama İşlemleri](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
