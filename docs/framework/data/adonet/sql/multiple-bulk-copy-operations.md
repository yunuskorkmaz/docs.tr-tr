---
title: Çoklu toplu kopyalama işlemleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
ms.openlocfilehash: e6a9a82a49d2db2f1a49420c296be6dbf6d37d67
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520302"
---
# <a name="multiple-bulk-copy-operations"></a>Çoklu toplu kopyalama işlemleri
Tek bir örneğini kullanarak birden çok toplu kopyalama işlemleri gerçekleştirebileceğiniz bir <xref:System.Data.SqlClient.SqlBulkCopy> sınıfı. İşlem parametrelerini (örneğin, hedef tablonun adı) kopyaları arasında değiştirirseniz, bunları önce herhangi bir sonraki çağrılar güncellemelisiniz **WriteToServer** yöntemleri, aşağıdaki örnekte gösterildiği gibi. Belirli bir örneği önceki toplu kopyalama işlemi olduğu açıkça değiştirmediğiniz sürece tüm özellik değerlerini aynı kalır.  
  
> [!NOTE]
>  Aynı örneği kullanarak birden çok toplu kopyalama işlemleri gerçekleştirme <xref:System.Data.SqlClient.SqlBulkCopy> her işlem için ayrı bir örneğini kullanmaya kıyasla genellikle daha verimli olur.  
  
 Aynı kullanarak birkaç toplu kopyalama işlemleri gerçekleştirmeniz <xref:System.Data.SqlClient.SqlBulkCopy> nesnesine eşit veya her işlemin farklı kaynak veya hedef bilgi olup kısıtlamalar vardır. Ancak, sütun ilişki bilgilerini sunucuya yazarken her zaman düzgün ayarlandığından emin olmanız gerekir.  
  
> [!IMPORTANT]
>  Bu örnekte açıklandığı gibi çalışma tabloları oluşturmadığınız sürece çalışmaz [toplu kopyalama örnek Kurulumu](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Bu kodu kullanmaya ilişkin sözdizimini göstermek için sağlanan **SqlBulkCopy** yalnızca. Kaynak ve hedef tablo aynı SQL Server örneğinde bulunuyorsa daha kolay ve hızlı bir Transact-SQL kullanmak için bunu `INSERT … SELECT` verileri kopyalamak için deyimi.  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server’da Toplu Kopyalama İşlemleri](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
