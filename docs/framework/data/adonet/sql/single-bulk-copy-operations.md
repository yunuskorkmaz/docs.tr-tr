---
description: 'Daha fazla bilgi edinin: tekli toplu kopyalama Işlemleri'
title: Tekil Toplu Kopyalama İşlemleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
ms.openlocfilehash: f6b046fbd73ad798f3f9f117eea0b72f46e43b37
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767485"
---
# <a name="single-bulk-copy-operations"></a>Tekil Toplu Kopyalama İşlemleri

SQL Server toplu kopyalama işlemi gerçekleştirmeye yönelik en basit yaklaşım, bir veritabanına karşı tek bir işlem gerçekleştirkullanmaktır. Varsayılan olarak, bir toplu kopyalama işlemi yalıtılmış bir işlem olarak gerçekleştirilir: kopyalama işlemi, geri alma için hiçbir fırsat olmadan, işlem temelli olmayan bir şekilde gerçekleşir.

> [!NOTE]
> Bir hata oluştuğunda toplu kopyalama işleminin tamamını veya bir kısmını geri almanız gerekiyorsa, <xref:System.Data.SqlClient.SqlBulkCopy> yönetilen bir işlem kullanabilir ya da mevcut bir işlem içinde toplu kopyalama işlemini gerçekleştirebilirsiniz.  Ayrıca, <xref:System.Transactions> bağlantı kayıtlı (örtük veya açık) bir **System. Transactions** hareketiyle birlikte, SqlBulkCopy ile de çalışacaksınız.
>
> Daha fazla bilgi için bkz. [işlem ve toplu kopyalama işlemleri](transaction-and-bulk-copy-operations.md).

Toplu kopyalama işlemi gerçekleştirmeye yönelik genel adımlar şunlardır:

1. Kaynak sunucuya bağlanın ve kopyalanacak verileri alın. Veriler bir veya nesnesinden alınalınabilmesi için diğer kaynaklardan da gelebilir <xref:System.Data.IDataReader> <xref:System.Data.DataTable> .

2. Hedef sunucuya bağlanın ( **SqlBulkCopy** 'ın sizin için bir bağlantı kurmasını istemediğiniz müddetçe).

3. <xref:System.Data.SqlClient.SqlBulkCopy>Gerekli özellikleri ayarlayarak bir nesne oluşturun.

4. Toplu ekleme işlemi için hedef tabloyu göstermek üzere **DestinationTableName** özelliğini ayarlayın.

5. **WriteToServer** yöntemlerinden birini çağırın.

6. İsteğe bağlı olarak, özellikleri güncelleştirin ve gerekirse **WriteToServer** ' ı çağırın.

7. <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>Bir bildirimde toplu kopyalama işlemlerini çağırın veya sarın `Using` .

> [!CAUTION]
> Kaynak ve hedef sütun veri türlerinin eşleşmesini öneririz. Veri türleri eşleşmiyorsa, **SqlBulkCopy** , tarafından kullanılan kuralları kullanarak her bir kaynak değeri hedef veri türüne dönüştürmeye çalışır <xref:System.Data.SqlClient.SqlParameter.Value%2A> . Dönüşümler performansı etkileyebilir ve ayrıca beklenmeyen hatalara neden olabilir. Örneğin, bir `Double` veri türü `Decimal` çoğu zaman bir veri türüne dönüştürülebilir, ancak her zaman değildir.

## <a name="example"></a>Örnek

Aşağıdaki konsol uygulaması, sınıfını kullanarak nasıl veri yükleneceğini gösterir <xref:System.Data.SqlClient.SqlBulkCopy> . Bu örnekte, <xref:System.Data.SqlClient.SqlDataReader> SQL Server **AdventureWorks** veritabanındaki **Production. Product** tablosundan aynı veritabanındaki benzer bir tabloya veri kopyalamak için kullanılır.

> [!IMPORTANT]
> Bu örnek, [toplu kopyalama örnek kurulumu](bulk-copy-example-setup.md)bölümünde açıklandığı gibi iş tablolarını oluşturmadığınız sürece çalıştırılmaz. Bu kod, yalnızca **SqlBulkCopy** kullanma sözdizimini göstermek için verilmiştir. Kaynak ve hedef tablolar aynı SQL Server örneğinde yer alıyorsa, verileri kopyalamak için Transact-SQL ifadesinin kullanılması daha kolay ve hızlıdır `INSERT … SELECT` .

[!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
[!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]

## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a>Transact-SQL ve komut sınıfını kullanarak toplu kopyalama Işlemi gerçekleştirme

Aşağıdaki örnek, <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> bulk INSERT ifadesini yürütmek için yönteminin nasıl kullanılacağını gösterir.

> [!NOTE]
> Veri kaynağı için dosya yolu sunucuya göredir. Toplu kopyalama işleminin başarılı olabilmesi için sunucu işleminin bu yola erişimi olması gerekir.

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

## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server’da Toplu Kopyalama İşlemleri](bulk-copy-operations-in-sql-server.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
