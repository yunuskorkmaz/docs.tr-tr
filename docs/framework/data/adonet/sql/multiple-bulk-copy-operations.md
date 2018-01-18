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
# <a name="multiple-bulk-copy-operations"></a><span data-ttu-id="54a76-102">Birden çok toplu kopyalama işlemleri</span><span class="sxs-lookup"><span data-stu-id="54a76-102">Multiple Bulk Copy Operations</span></span>
<span data-ttu-id="54a76-103">Tek bir örneğini kullanarak birden çok toplu kopyalama işlemleri gerçekleştirebileceğiniz bir <xref:System.Data.SqlClient.SqlBulkCopy> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="54a76-103">You can perform multiple bulk copy operations using a single instance of a <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span> <span data-ttu-id="54a76-104">İşlemi parametreleri (örneğin, hedef tablo adı) kopyaları arasında değiştirirseniz, bunları herhangi biri yapılan sonraki çağrılar önce güncelleştirmelisiniz **WriteToServer** aşağıdaki örnekte gösterildiği gibi yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="54a76-104">If the operation parameters change between copies (for example, the name of the destination table), you must update them prior to any subsequent calls to any of the **WriteToServer** methods, as demonstrated in the following example.</span></span> <span data-ttu-id="54a76-105">Verilen örneği önceki toplu kopyalama işlemi üzerinde oldukları gibi tüm özellik değerlerini açıkça değiştirmediyse, aynı kalır.</span><span class="sxs-lookup"><span data-stu-id="54a76-105">Unless explicitly changed, all property values remain the same as they were on the previous bulk copy operation for a given instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="54a76-106">Aynı örneği kullanarak birden çok toplu kopyalama işlemleri gerçekleştirme <xref:System.Data.SqlClient.SqlBulkCopy> her işlem için ayrı bir örneği kullanmaktan genellikle daha verimli olur.</span><span class="sxs-lookup"><span data-stu-id="54a76-106">Performing multiple bulk copy operations using the same instance of <xref:System.Data.SqlClient.SqlBulkCopy> is usually more efficient than using a separate instance for each operation.</span></span>  
  
 <span data-ttu-id="54a76-107">Aynı kullanarak birkaç toplu kopyalama işlemleri gerçekleştirmek, <xref:System.Data.SqlClient.SqlBulkCopy> nesne, kaynak veya hedef bilgi eşit ya da her işlemde farklı olup üzerinde bir kısıtlama yoktur.</span><span class="sxs-lookup"><span data-stu-id="54a76-107">If you perform several bulk copy operations using the same <xref:System.Data.SqlClient.SqlBulkCopy> object, there are no restrictions on whether source or target information is equal or different in each operation.</span></span> <span data-ttu-id="54a76-108">Ancak, sütun ilişkisi bilgileri sunucuya her yazdığınızda düzgün ayarlandığından emin olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="54a76-108">However, you must ensure that column association information is properly set each time you write to the server.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="54a76-109">Bölümünde açıklandığı gibi iş tabloları oluşturmadıysanız Bu örnek çalışmaz [toplu kopyalama örnek Kurulum](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span><span class="sxs-lookup"><span data-stu-id="54a76-109">This sample will not run unless you have created the work tables as described in [Bulk Copy Example Setup](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span></span> <span data-ttu-id="54a76-110">Bu kodu kullanarak söz dizimi göstermek için sağlanan **SqlBulkCopy** yalnızca.</span><span class="sxs-lookup"><span data-stu-id="54a76-110">This code is provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="54a76-111">Kaynak ve hedef tablolar aynı SQL Server örneğinde bulunuyorsa, daha kolay ve hızlı bir Transact-SQL kullanmak için bunu `INSERT … SELECT` verileri kopyalamak için deyimi.</span><span class="sxs-lookup"><span data-stu-id="54a76-111">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="54a76-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="54a76-112">See Also</span></span>  
 [<span data-ttu-id="54a76-113">SQL Server’da Toplu Kopyalama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="54a76-113">Bulk Copy Operations in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)  
 [<span data-ttu-id="54a76-114">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="54a76-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
