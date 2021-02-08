---
description: 'Daha fazla bilgi edinin: çoklu toplu kopyalama Işlemleri'
title: Çoklu Toplu Kopyalama İşlemleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
ms.openlocfilehash: dfc694cfb4a993889bed607be71821bb1f9fddf1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767667"
---
# <a name="multiple-bulk-copy-operations"></a>Çoklu Toplu Kopyalama İşlemleri

Bir sınıfın tek bir örneğini kullanarak birden çok toplu kopyalama işlemi gerçekleştirebilirsiniz <xref:System.Data.SqlClient.SqlBulkCopy> . İşlem parametreleri kopyalar arasında değişiklik içeriyorsa (örneğin, hedef tablonun adı), aşağıdaki örnekte gösterildiği gibi, herhangi bir **WriteToServer** metotından sonraki çağrılardan önce bunları güncelleştirmeniz gerekir. Açıkça değiştirilmediği sürece tüm özellik değerleri, belirli bir örnek için önceki toplu kopyalama işleminde olduğu gibi kalır.  
  
> [!NOTE]
> Aynı örneğini kullanarak birden çok toplu kopyalama işlemi gerçekleştirmek <xref:System.Data.SqlClient.SqlBulkCopy> genellikle her işlem için ayrı bir örnek kullanmaktan daha etkilidir.  
  
 Aynı nesneyi kullanarak birkaç toplu kopyalama işlemi gerçekleştirirseniz <xref:System.Data.SqlClient.SqlBulkCopy> , kaynak veya hedef bilgilerin her bir işlemde eşit veya farklı olup olmadığı konusunda bir kısıtlama yoktur. Ancak, sunucuya her yazdığınızda sütun ilişkilendirme bilgilerinin düzgün şekilde ayarlandığından emin olmanız gerekir.  
  
> [!IMPORTANT]
> Bu örnek, [toplu kopyalama örnek kurulumu](bulk-copy-example-setup.md)bölümünde açıklandığı gibi iş tablolarını oluşturmadığınız sürece çalıştırılmaz. Bu kod, yalnızca **SqlBulkCopy** kullanma sözdizimini göstermek için verilmiştir. Kaynak ve hedef tablolar aynı SQL Server örneğinde yer alıyorsa, verileri kopyalamak için Transact-SQL ifadesinin kullanılması daha kolay ve hızlıdır `INSERT … SELECT` .  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server’da Toplu Kopyalama İşlemleri](bulk-copy-operations-in-sql-server.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
