---
title: Tek toplu kopyalama işlemleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
ms.openlocfilehash: 47f89feb90efbafb6c43bbad78f05292213a0c58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365871"
---
# <a name="single-bulk-copy-operations"></a>Tek toplu kopyalama işlemleri
Bir SQL Server toplu kopyalama işlemi gerçekleştirmenin en kolay yaklaşım, tek bir işlemde bir veritabanında gerçekleştirmektir. Varsayılan olarak, yalıtılmış bir işlem olarak bir toplu kopyalama işlemi gerçekleştirilir: Bu çalışırken için fırsat ile geri işlem temelli olmayan bir şekilde, kopyalama işlemi gerçekleşir.  
  
> [!NOTE]
>  Hata oluştuğunda toplu kopyalama bölümünü veya tümünü geri almak gerekiyorsa, kullanabilir bir <xref:System.Data.SqlClient.SqlBulkCopy>-yönetilen işlem ya da var olan bir işlem içinde toplu kopyalama işlemi. **SqlBulkCopy** birlikte çalışacağı <xref:System.Transactions> bağlantı (örtük veya açık olarak) içine kayıtlı değilse bir **System.Transactions** işlem.  
>   
>  Daha fazla bilgi için bkz: [işlem ve toplu kopyalama işlemleri](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md).  
  
 Bir toplu kopyalama işlemi gerçekleştirmeye yönelik genel adımlar aşağıdaki gibidir:  
  
1.  Kaynak sunucuya bağlanın ve kopyalanacak veri alın. Veri da gelebilir diğer kaynaklardan penceresinden alınabilir, bir <xref:System.Data.IDataReader> veya <xref:System.Data.DataTable> nesnesi.  
  
2.  Hedef sunucuya (istediğiniz sürece **SqlBulkCopy** sizin için bir bağlantı kurmak için).  
  
3.  Oluşturma bir <xref:System.Data.SqlClient.SqlBulkCopy> nesnesi, tüm gerekli özellikleri ayarlama.  
  
4.  Ayarlama **DestinationTableName** toplu için hedef tablo belirtmek için özellik ekleme işlemi.  
  
5.  Birini çağırın **WriteToServer** yöntemleri.  
  
6.  İsteğe bağlı olarak, güncelleştirme özellikleri ve çağrı **WriteToServer** yeniden gerektiği.  
  
7.  Çağrı <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>, veya toplu kopyalama işlemleri içinde kaydırma bir `Using` deyimi.  
  
> [!CAUTION]
>  Kaynak ve hedef sütun veri türleri eşleşmesini öneririz. Veri türleri eşleşmiyorsa **SqlBulkCopy** her kaynak değeri tarafından işe kurallarını kullanarak hedef veri türüne dönüştürmek çalışır <xref:System.Data.SqlClient.SqlParameter.Value%2A>. Dönüşümler performansını etkileyebilir ve ayrıca beklenmeyen hatalara yol açabilir. Örneğin, bir `Double` veri türüne dönüştürülebilir bir `Decimal` veri türü çoğu zaman, ancak her zaman.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki konsol uygulaması kullanarak veri yüklemek gösterilmiştir <xref:System.Data.SqlClient.SqlBulkCopy> sınıfı. Bu örnekte, bir <xref:System.Data.SqlClient.SqlDataReader> veri kopyalamak için kullanılan **Production.Product** SQL Server tablosunda**AdventureWorks** benzer bir tabloya aynı veritabanında veritabanı.  
  
> [!IMPORTANT]
>  Bölümünde açıklandığı gibi iş tabloları oluşturmadıysanız Bu örnek çalışmaz [toplu kopyalama örnek Kurulum](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Bu kodu kullanarak söz dizimi göstermek için sağlanan **SqlBulkCopy** yalnızca. Kaynak ve hedef tablolar aynı SQL Server örneğinde bulunuyorsa, daha kolay ve hızlı bir Transact-SQL kullanmak için bunu `INSERT … SELECT` verileri kopyalamak için deyimi.  
  
 [!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
 [!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]  
  
## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a>Transact-SQL ve komut sınıfı kullanılarak bir toplu kopyalama işlemi gerçekleştirme  
 Aşağıdaki örnekte nasıl kullanılacağını anlatan <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> yöntemi BULK INSERT deyimini yürütün.  
  
> [!NOTE]
>  Veri kaynağı için dosya yolu göreli sunucudur. Sunucu işlemi sırada toplu kopyalama işleminin başarılı olması bu yola erişimi olması gerekir.  
  
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
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
