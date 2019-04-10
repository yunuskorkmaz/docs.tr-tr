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
# <a name="multiple-bulk-copy-operations"></a><span data-ttu-id="1d165-102">Çoklu Toplu Kopyalama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="1d165-102">Multiple Bulk Copy Operations</span></span>
<span data-ttu-id="1d165-103">Tek bir örneğini kullanarak birden çok toplu kopyalama işlemleri gerçekleştirebileceğiniz bir <xref:System.Data.SqlClient.SqlBulkCopy> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1d165-103">You can perform multiple bulk copy operations using a single instance of a <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span> <span data-ttu-id="1d165-104">İşlem parametrelerini (örneğin, hedef tablonun adı) kopyaları arasında değiştirirseniz, bunları önce herhangi bir sonraki çağrılar güncellemelisiniz **WriteToServer** yöntemleri, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="1d165-104">If the operation parameters change between copies (for example, the name of the destination table), you must update them prior to any subsequent calls to any of the **WriteToServer** methods, as demonstrated in the following example.</span></span> <span data-ttu-id="1d165-105">Belirli bir örneği önceki toplu kopyalama işlemi olduğu açıkça değiştirmediğiniz sürece tüm özellik değerlerini aynı kalır.</span><span class="sxs-lookup"><span data-stu-id="1d165-105">Unless explicitly changed, all property values remain the same as they were on the previous bulk copy operation for a given instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d165-106">Aynı örneği kullanarak birden çok toplu kopyalama işlemleri gerçekleştirme <xref:System.Data.SqlClient.SqlBulkCopy> her işlem için ayrı bir örneğini kullanmaya kıyasla genellikle daha verimli olur.</span><span class="sxs-lookup"><span data-stu-id="1d165-106">Performing multiple bulk copy operations using the same instance of <xref:System.Data.SqlClient.SqlBulkCopy> is usually more efficient than using a separate instance for each operation.</span></span>  
  
 <span data-ttu-id="1d165-107">Aynı kullanarak birkaç toplu kopyalama işlemleri gerçekleştirmeniz <xref:System.Data.SqlClient.SqlBulkCopy> nesnesine eşit veya her işlemin farklı kaynak veya hedef bilgi olup kısıtlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="1d165-107">If you perform several bulk copy operations using the same <xref:System.Data.SqlClient.SqlBulkCopy> object, there are no restrictions on whether source or target information is equal or different in each operation.</span></span> <span data-ttu-id="1d165-108">Ancak, sütun ilişki bilgilerini sunucuya yazarken her zaman düzgün ayarlandığından emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1d165-108">However, you must ensure that column association information is properly set each time you write to the server.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1d165-109">Bu örnekte açıklandığı gibi çalışma tabloları oluşturmadığınız sürece çalışmaz [toplu kopyalama örnek Kurulumu](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span><span class="sxs-lookup"><span data-stu-id="1d165-109">This sample will not run unless you have created the work tables as described in [Bulk Copy Example Setup](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span></span> <span data-ttu-id="1d165-110">Bu kodu kullanmaya ilişkin sözdizimini göstermek için sağlanan **SqlBulkCopy** yalnızca.</span><span class="sxs-lookup"><span data-stu-id="1d165-110">This code is provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="1d165-111">Kaynak ve hedef tablo aynı SQL Server örneğinde bulunuyorsa daha kolay ve hızlı bir Transact-SQL kullanmak için bunu `INSERT … SELECT` verileri kopyalamak için deyimi.</span><span class="sxs-lookup"><span data-stu-id="1d165-111">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1d165-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d165-112">See also</span></span>

- [<span data-ttu-id="1d165-113">SQL Server’da Toplu Kopyalama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="1d165-113">Bulk Copy Operations in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)
- [<span data-ttu-id="1d165-114">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="1d165-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
