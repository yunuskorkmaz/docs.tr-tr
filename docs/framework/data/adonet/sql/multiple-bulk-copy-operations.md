---
title: Çoklu Toplu Kopyalama İşlemleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
ms.openlocfilehash: 405a82c625853d242ca68088ffdf81b6bcd7c518
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209768"
---
# <a name="multiple-bulk-copy-operations"></a>Çoklu Toplu Kopyalama İşlemleri
Tek bir örneğini kullanarak birden çok toplu kopyalama işlemleri gerçekleştirebileceğiniz bir <xref:System.Data.SqlClient.SqlBulkCopy> sınıfı. İşlem parametrelerini (örneğin, hedef tablonun adı) kopyaları arasında değiştirirseniz, bunları önce herhangi bir sonraki çağrılar güncellemelisiniz **WriteToServer** yöntemleri, aşağıdaki örnekte gösterildiği gibi. Belirli bir örneği önceki toplu kopyalama işlemi olduğu açıkça değiştirmediğiniz sürece tüm özellik değerlerini aynı kalır.  
  
> [!NOTE]
>  Aynı örneği kullanarak birden çok toplu kopyalama işlemleri gerçekleştirme <xref:System.Data.SqlClient.SqlBulkCopy> her işlem için ayrı bir örneğini kullanmaya kıyasla genellikle daha verimli olur.  
  
 Aynı kullanarak birkaç toplu kopyalama işlemleri gerçekleştirmeniz <xref:System.Data.SqlClient.SqlBulkCopy> nesnesine eşit veya her işlemin farklı kaynak veya hedef bilgi olup kısıtlamalar vardır. Ancak, sütun ilişki bilgilerini sunucuya yazarken her zaman düzgün ayarlandığından emin olmanız gerekir.  
  
> [!IMPORTANT]
>  Bu örnekte açıklandığı gibi çalışma tabloları oluşturmadığınız sürece çalışmaz [toplu kopyalama örnek Kurulumu](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Bu kodu kullanmaya ilişkin sözdizimini göstermek için sağlanan **SqlBulkCopy** yalnızca. Kaynak ve hedef tablo aynı SQL Server örneğinde bulunuyorsa daha kolay ve hızlı bir Transact-SQL kullanmak için bunu `INSERT … SELECT` verileri kopyalamak için deyimi.  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server’da Toplu Kopyalama İşlemleri](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
