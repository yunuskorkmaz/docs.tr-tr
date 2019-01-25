---
title: DataTable içinde gezinme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
ms.openlocfilehash: 710e4bdaeafc483510c4102dc9ac0f6ffaaafce9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528088"
---
# <a name="navigating-datatables"></a><span data-ttu-id="f83d1-102">DataTable içinde gezinme</span><span class="sxs-lookup"><span data-stu-id="f83d1-102">Navigating DataTables</span></span>
<span data-ttu-id="f83d1-103"><xref:System.Data.DataTableReader> Bir veya daha fazla içeriğini alır <xref:System.Data.DataTable> nesneleri formunda bir veya daha fazla salt okunur, salt iletme sonuç kümeleri.</span><span class="sxs-lookup"><span data-stu-id="f83d1-103">The <xref:System.Data.DataTableReader> obtains the contents of one or more <xref:System.Data.DataTable> objects in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="f83d1-104">A <xref:System.Data.DataTableReader> kullanarak oluşturulursa, birden çok sonuç kümesi içerebilir <xref:System.Data.DataSet.CreateDataReader%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f83d1-104">A <xref:System.Data.DataTableReader> may contain multiple result sets if it is created by using the <xref:System.Data.DataSet.CreateDataReader%2A> method.</span></span> <span data-ttu-id="f83d1-105">Birden fazla sonuç kümesi olduğunda <xref:System.Data.DataTableReader.NextResult%2A> yöntemi imleci sonraki sonuç kümesine ilerler.</span><span class="sxs-lookup"><span data-stu-id="f83d1-105">When there is more than one result set, the <xref:System.Data.DataTableReader.NextResult%2A> method advances the cursor to the next result set.</span></span> <span data-ttu-id="f83d1-106">Bu yalnızca iletme bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="f83d1-106">This is a forward-only process.</span></span> <span data-ttu-id="f83d1-107">Bir önceki sonuç kümesi için döndürülecek mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="f83d1-107">It is not possible to return to a previous result set.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f83d1-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="f83d1-108">Example</span></span>  
 <span data-ttu-id="f83d1-109">Aşağıdaki örnekte, `TestConstructor` yöntemi oluşturur iki <xref:System.Data.DataTable> örnekleri.</span><span class="sxs-lookup"><span data-stu-id="f83d1-109">In the following example, the `TestConstructor` method creates two <xref:System.Data.DataTable> instances.</span></span> <span data-ttu-id="f83d1-110">Bu oluşturucu için göstermek için <xref:System.Data.DataTableReader> sınıfı örneği oluşturur Yeni **DataTableReader** iki içeren bir dizisine göre **DataTable**ve basit bir işlem yapar içeriğini konsol penceresine ilk birkaç sütunlarından yazdırma.</span><span class="sxs-lookup"><span data-stu-id="f83d1-110">In order to demonstrate this constructor for the <xref:System.Data.DataTableReader> class, the sample creates a new **DataTableReader** based on an array that contains the two **DataTables**, and performs a simple operation, printing the contents from the first few columns to the console window.</span></span>  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f83d1-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f83d1-111">See also</span></span>
- [<span data-ttu-id="f83d1-112">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="f83d1-112">DataTableReaders</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)
- [<span data-ttu-id="f83d1-113">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="f83d1-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
