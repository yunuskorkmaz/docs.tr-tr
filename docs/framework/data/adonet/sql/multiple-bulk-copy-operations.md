---
title: Çoklu Toplu Kopyalama İşlemleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
ms.openlocfilehash: 8ee0fdbfc167c819942d8282aca56b7c5168fd87
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946858"
---
# <a name="multiple-bulk-copy-operations"></a>Çoklu Toplu Kopyalama İşlemleri
Bir <xref:System.Data.SqlClient.SqlBulkCopy> sınıfın tek bir örneğini kullanarak birden çok toplu kopyalama işlemi gerçekleştirebilirsiniz. İşlem parametreleri kopyalar arasında değişiklik içeriyorsa (örneğin, hedef tablonun adı), aşağıdaki örnekte gösterildiği gibi, herhangi bir **WriteToServer** metotından sonraki çağrılardan önce bunları güncelleştirmeniz gerekir. Açıkça değiştirilmediği sürece tüm özellik değerleri, belirli bir örnek için önceki toplu kopyalama işleminde olduğu gibi kalır.  
  
> [!NOTE]
> Aynı örneğini <xref:System.Data.SqlClient.SqlBulkCopy> kullanarak birden çok toplu kopyalama işlemi gerçekleştirmek genellikle her işlem için ayrı bir örnek kullanmaktan daha etkilidir.  
  
 Aynı <xref:System.Data.SqlClient.SqlBulkCopy> nesneyi kullanarak birkaç toplu kopyalama işlemi gerçekleştirirseniz, kaynak veya hedef bilgilerin her bir işlemde eşit veya farklı olup olmadığı konusunda bir kısıtlama yoktur. Ancak, sunucuya her yazdığınızda sütun ilişkilendirme bilgilerinin düzgün şekilde ayarlandığından emin olmanız gerekir.  
  
> [!IMPORTANT]
> Bu örnek, [toplu kopyalama örnek kurulumu](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)bölümünde açıklandığı gibi iş tablolarını oluşturmadığınız sürece çalıştırılmaz. Bu kod, yalnızca **SqlBulkCopy** kullanma sözdizimini göstermek için verilmiştir. Kaynak ve hedef tablolar aynı SQL Server örneğinde yer alıyorsa, verileri kopyalamak için Transact-SQL `INSERT … SELECT` ifadesinin kullanılması daha kolay ve hızlıdır.  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server’da Toplu Kopyalama İşlemleri](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
