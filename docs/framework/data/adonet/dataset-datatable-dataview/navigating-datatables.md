---
title: DataTable İçinde Gezinme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
ms.openlocfilehash: 91db42acb0e09b8fc99b0ee710a60800d40938ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607277"
---
# <a name="navigating-datatables"></a><span data-ttu-id="bb9e7-102">DataTable İçinde Gezinme</span><span class="sxs-lookup"><span data-stu-id="bb9e7-102">Navigating DataTables</span></span>
<span data-ttu-id="bb9e7-103"><xref:System.Data.DataTableReader> Bir veya daha fazla içeriğini alır <xref:System.Data.DataTable> nesneleri formunda bir veya daha fazla salt okunur, salt iletme sonuç kümeleri.</span><span class="sxs-lookup"><span data-stu-id="bb9e7-103">The <xref:System.Data.DataTableReader> obtains the contents of one or more <xref:System.Data.DataTable> objects in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="bb9e7-104">A <xref:System.Data.DataTableReader> kullanarak oluşturulursa, birden çok sonuç kümesi içerebilir <xref:System.Data.DataSet.CreateDataReader%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bb9e7-104">A <xref:System.Data.DataTableReader> may contain multiple result sets if it is created by using the <xref:System.Data.DataSet.CreateDataReader%2A> method.</span></span> <span data-ttu-id="bb9e7-105">Birden fazla sonuç kümesi olduğunda <xref:System.Data.DataTableReader.NextResult%2A> yöntemi imleci sonraki sonuç kümesine ilerler.</span><span class="sxs-lookup"><span data-stu-id="bb9e7-105">When there is more than one result set, the <xref:System.Data.DataTableReader.NextResult%2A> method advances the cursor to the next result set.</span></span> <span data-ttu-id="bb9e7-106">Bu yalnızca iletme bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="bb9e7-106">This is a forward-only process.</span></span> <span data-ttu-id="bb9e7-107">Bir önceki sonuç kümesi için döndürülecek mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="bb9e7-107">It is not possible to return to a previous result set.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb9e7-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="bb9e7-108">Example</span></span>  
 <span data-ttu-id="bb9e7-109">Aşağıdaki örnekte, `TestConstructor` yöntemi oluşturur iki <xref:System.Data.DataTable> örnekleri.</span><span class="sxs-lookup"><span data-stu-id="bb9e7-109">In the following example, the `TestConstructor` method creates two <xref:System.Data.DataTable> instances.</span></span> <span data-ttu-id="bb9e7-110">Bu oluşturucu için göstermek için <xref:System.Data.DataTableReader> sınıfı örneği oluşturur Yeni **DataTableReader** iki içeren bir dizisine göre **DataTable**ve basit bir işlem yapar içeriğini konsol penceresine ilk birkaç sütunlarından yazdırma.</span><span class="sxs-lookup"><span data-stu-id="bb9e7-110">In order to demonstrate this constructor for the <xref:System.Data.DataTableReader> class, the sample creates a new **DataTableReader** based on an array that contains the two **DataTables**, and performs a simple operation, printing the contents from the first few columns to the console window.</span></span>  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="bb9e7-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb9e7-111">See also</span></span>

- [<span data-ttu-id="bb9e7-112">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="bb9e7-112">DataTableReaders</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)
- [<span data-ttu-id="bb9e7-113">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="bb9e7-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
