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
# <a name="multiple-bulk-copy-operations"></a><span data-ttu-id="dc1fa-102">Çoklu Toplu Kopyalama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="dc1fa-102">Multiple Bulk Copy Operations</span></span>
<span data-ttu-id="dc1fa-103">Bir <xref:System.Data.SqlClient.SqlBulkCopy> sınıfın tek bir örneğini kullanarak birden çok toplu kopyalama işlemi gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc1fa-103">You can perform multiple bulk copy operations using a single instance of a <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span> <span data-ttu-id="dc1fa-104">İşlem parametreleri kopyalar arasında değişiklik içeriyorsa (örneğin, hedef tablonun adı), aşağıdaki örnekte gösterildiği gibi, herhangi bir **WriteToServer** metotından sonraki çağrılardan önce bunları güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc1fa-104">If the operation parameters change between copies (for example, the name of the destination table), you must update them prior to any subsequent calls to any of the **WriteToServer** methods, as demonstrated in the following example.</span></span> <span data-ttu-id="dc1fa-105">Açıkça değiştirilmediği sürece tüm özellik değerleri, belirli bir örnek için önceki toplu kopyalama işleminde olduğu gibi kalır.</span><span class="sxs-lookup"><span data-stu-id="dc1fa-105">Unless explicitly changed, all property values remain the same as they were on the previous bulk copy operation for a given instance.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dc1fa-106">Aynı örneğini <xref:System.Data.SqlClient.SqlBulkCopy> kullanarak birden çok toplu kopyalama işlemi gerçekleştirmek genellikle her işlem için ayrı bir örnek kullanmaktan daha etkilidir.</span><span class="sxs-lookup"><span data-stu-id="dc1fa-106">Performing multiple bulk copy operations using the same instance of <xref:System.Data.SqlClient.SqlBulkCopy> is usually more efficient than using a separate instance for each operation.</span></span>  
  
 <span data-ttu-id="dc1fa-107">Aynı <xref:System.Data.SqlClient.SqlBulkCopy> nesneyi kullanarak birkaç toplu kopyalama işlemi gerçekleştirirseniz, kaynak veya hedef bilgilerin her bir işlemde eşit veya farklı olup olmadığı konusunda bir kısıtlama yoktur.</span><span class="sxs-lookup"><span data-stu-id="dc1fa-107">If you perform several bulk copy operations using the same <xref:System.Data.SqlClient.SqlBulkCopy> object, there are no restrictions on whether source or target information is equal or different in each operation.</span></span> <span data-ttu-id="dc1fa-108">Ancak, sunucuya her yazdığınızda sütun ilişkilendirme bilgilerinin düzgün şekilde ayarlandığından emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc1fa-108">However, you must ensure that column association information is properly set each time you write to the server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="dc1fa-109">Bu örnek, [toplu kopyalama örnek kurulumu](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)bölümünde açıklandığı gibi iş tablolarını oluşturmadığınız sürece çalıştırılmaz.</span><span class="sxs-lookup"><span data-stu-id="dc1fa-109">This sample will not run unless you have created the work tables as described in [Bulk Copy Example Setup](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span></span> <span data-ttu-id="dc1fa-110">Bu kod, yalnızca **SqlBulkCopy** kullanma sözdizimini göstermek için verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="dc1fa-110">This code is provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="dc1fa-111">Kaynak ve hedef tablolar aynı SQL Server örneğinde yer alıyorsa, verileri kopyalamak için Transact-SQL `INSERT … SELECT` ifadesinin kullanılması daha kolay ve hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="dc1fa-111">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="dc1fa-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc1fa-112">See also</span></span>

- [<span data-ttu-id="dc1fa-113">SQL Server’da Toplu Kopyalama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="dc1fa-113">Bulk Copy Operations in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)
- [<span data-ttu-id="dc1fa-114">ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="dc1fa-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
