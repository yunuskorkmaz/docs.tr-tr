---
title: Çoklu Toplu Kopyalama İşlemleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
ms.openlocfilehash: d447f09fcbfe108346b81a2bced44cf305e2844b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172677"
---
# <a name="multiple-bulk-copy-operations"></a><span data-ttu-id="cd4ce-102">Çoklu Toplu Kopyalama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="cd4ce-102">Multiple Bulk Copy Operations</span></span>

<span data-ttu-id="cd4ce-103">Bir sınıfın tek bir örneğini kullanarak birden çok toplu kopyalama işlemi gerçekleştirebilirsiniz <xref:System.Data.SqlClient.SqlBulkCopy> .</span><span class="sxs-lookup"><span data-stu-id="cd4ce-103">You can perform multiple bulk copy operations using a single instance of a <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span> <span data-ttu-id="cd4ce-104">İşlem parametreleri kopyalar arasında değişiklik içeriyorsa (örneğin, hedef tablonun adı), aşağıdaki örnekte gösterildiği gibi, herhangi bir **WriteToServer** metotından sonraki çağrılardan önce bunları güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cd4ce-104">If the operation parameters change between copies (for example, the name of the destination table), you must update them prior to any subsequent calls to any of the **WriteToServer** methods, as demonstrated in the following example.</span></span> <span data-ttu-id="cd4ce-105">Açıkça değiştirilmediği sürece tüm özellik değerleri, belirli bir örnek için önceki toplu kopyalama işleminde olduğu gibi kalır.</span><span class="sxs-lookup"><span data-stu-id="cd4ce-105">Unless explicitly changed, all property values remain the same as they were on the previous bulk copy operation for a given instance.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cd4ce-106">Aynı örneğini kullanarak birden çok toplu kopyalama işlemi gerçekleştirmek <xref:System.Data.SqlClient.SqlBulkCopy> genellikle her işlem için ayrı bir örnek kullanmaktan daha etkilidir.</span><span class="sxs-lookup"><span data-stu-id="cd4ce-106">Performing multiple bulk copy operations using the same instance of <xref:System.Data.SqlClient.SqlBulkCopy> is usually more efficient than using a separate instance for each operation.</span></span>  
  
 <span data-ttu-id="cd4ce-107">Aynı nesneyi kullanarak birkaç toplu kopyalama işlemi gerçekleştirirseniz <xref:System.Data.SqlClient.SqlBulkCopy> , kaynak veya hedef bilgilerin her bir işlemde eşit veya farklı olup olmadığı konusunda bir kısıtlama yoktur.</span><span class="sxs-lookup"><span data-stu-id="cd4ce-107">If you perform several bulk copy operations using the same <xref:System.Data.SqlClient.SqlBulkCopy> object, there are no restrictions on whether source or target information is equal or different in each operation.</span></span> <span data-ttu-id="cd4ce-108">Ancak, sunucuya her yazdığınızda sütun ilişkilendirme bilgilerinin düzgün şekilde ayarlandığından emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cd4ce-108">However, you must ensure that column association information is properly set each time you write to the server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="cd4ce-109">Bu örnek, [toplu kopyalama örnek kurulumu](bulk-copy-example-setup.md)bölümünde açıklandığı gibi iş tablolarını oluşturmadığınız sürece çalıştırılmaz.</span><span class="sxs-lookup"><span data-stu-id="cd4ce-109">This sample will not run unless you have created the work tables as described in [Bulk Copy Example Setup](bulk-copy-example-setup.md).</span></span> <span data-ttu-id="cd4ce-110">Bu kod, yalnızca **SqlBulkCopy** kullanma sözdizimini göstermek için verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cd4ce-110">This code is provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="cd4ce-111">Kaynak ve hedef tablolar aynı SQL Server örneğinde yer alıyorsa, verileri kopyalamak için Transact-SQL ifadesinin kullanılması daha kolay ve hızlıdır `INSERT … SELECT` .</span><span class="sxs-lookup"><span data-stu-id="cd4ce-111">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="cd4ce-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd4ce-112">See also</span></span>

- [<span data-ttu-id="cd4ce-113">SQL Server’da Toplu Kopyalama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="cd4ce-113">Bulk Copy Operations in SQL Server</span></span>](bulk-copy-operations-in-sql-server.md)
- [<span data-ttu-id="cd4ce-114">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cd4ce-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
