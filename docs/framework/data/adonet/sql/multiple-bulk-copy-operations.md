---
title: "Birden çok toplu kopyalama işlemleri"
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
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 8a753357719f451ce7acc2d7f42c0493ca2357ab
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="multiple-bulk-copy-operations"></a>Birden çok toplu kopyalama işlemleri
Tek bir örneğini kullanarak birden çok toplu kopyalama işlemleri gerçekleştirebileceğiniz bir <xref:System.Data.SqlClient.SqlBulkCopy> sınıfı. İşlemi parametreleri (örneğin, hedef tablo adı) kopyaları arasında değiştirirseniz, bunları herhangi biri yapılan sonraki çağrılar önce güncelleştirmelisiniz **WriteToServer** aşağıdaki örnekte gösterildiği gibi yöntemleri. Verilen örneği önceki toplu kopyalama işlemi üzerinde oldukları gibi tüm özellik değerlerini açıkça değiştirmediyse, aynı kalır.  
  
> [!NOTE]
>  Aynı örneği kullanarak birden çok toplu kopyalama işlemleri gerçekleştirme <xref:System.Data.SqlClient.SqlBulkCopy> her işlem için ayrı bir örneği kullanmaktan genellikle daha verimli olur.  
  
 Aynı kullanarak birkaç toplu kopyalama işlemleri gerçekleştirmek, <xref:System.Data.SqlClient.SqlBulkCopy> nesne, kaynak veya hedef bilgi eşit ya da her işlemde farklı olup üzerinde bir kısıtlama yoktur. Ancak, sütun ilişkisi bilgileri sunucuya her yazdığınızda düzgün ayarlandığından emin olmalısınız.  
  
> [!IMPORTANT]
>  Bölümünde açıklandığı gibi iş tabloları oluşturmadıysanız Bu örnek çalışmaz [toplu kopyalama örnek Kurulum](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Bu kodu kullanarak söz dizimi göstermek için sağlanan **SqlBulkCopy** yalnızca. Kaynak ve hedef tablolar aynı SQL Server örneğinde bulunuyorsa, daha kolay ve hızlı bir Transact-SQL kullanmak için bunu `INSERT … SELECT` verileri kopyalamak için deyimi.  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server’da Toplu Kopyalama İşlemleri](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
