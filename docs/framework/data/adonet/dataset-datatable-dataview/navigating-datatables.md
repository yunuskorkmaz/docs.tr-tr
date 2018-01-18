---
title: DataTables gezinme
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
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2233beeab5bc613966375f9a8ccf18c333e9f4c6
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="navigating-datatables"></a><span data-ttu-id="acde4-102">DataTables gezinme</span><span class="sxs-lookup"><span data-stu-id="acde4-102">Navigating DataTables</span></span>
<span data-ttu-id="acde4-103"><xref:System.Data.DataTableReader> Bir veya daha fazla içeriğini alır <xref:System.Data.DataTable> nesneleri bir veya daha fazla salt okunur, yalnızca ileri sonuç kümesi biçiminde.</span><span class="sxs-lookup"><span data-stu-id="acde4-103">The <xref:System.Data.DataTableReader> obtains the contents of one or more <xref:System.Data.DataTable> objects in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="acde4-104">A <xref:System.Data.DataTableReader> kullanarak oluşturulursa, birden çok sonuç kümesi içerebilir <xref:System.Data.DataSet.CreateDataReader%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="acde4-104">A <xref:System.Data.DataTableReader> may contain multiple result sets if it is created by using the <xref:System.Data.DataSet.CreateDataReader%2A> method.</span></span> <span data-ttu-id="acde4-105">Birden çok sonuç kümesi olduğunda <xref:System.Data.DataTableReader.NextResult%2A> yöntemi sonraki sonuç kümesini imleci ilerler.</span><span class="sxs-lookup"><span data-stu-id="acde4-105">When there is more than one result set, the <xref:System.Data.DataTableReader.NextResult%2A> method advances the cursor to the next result set.</span></span> <span data-ttu-id="acde4-106">Bu yalnızca ileri bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="acde4-106">This is a forward-only process.</span></span> <span data-ttu-id="acde4-107">Önceki bir sonuç kümesi döndürmek mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="acde4-107">It is not possible to return to a previous result set.</span></span>  
  
## <a name="example"></a><span data-ttu-id="acde4-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="acde4-108">Example</span></span>  
 <span data-ttu-id="acde4-109">Aşağıdaki örnekte, `TestConstructor` yöntemi iki oluşturur <xref:System.Data.DataTable> örnekleri.</span><span class="sxs-lookup"><span data-stu-id="acde4-109">In the following example, the `TestConstructor` method creates two <xref:System.Data.DataTable> instances.</span></span> <span data-ttu-id="acde4-110">Bu oluşturucu için göstermek için <xref:System.Data.DataTableReader> sınıfı, bir örnek oluşturur Yeni bir **DataTableReader** iki içeren bir dizisine göre **DataTables**ve basit bir işlemi gerçekleştirir içeriği ilk birkaç sütunlarından konsol penceresine yazdırma.</span><span class="sxs-lookup"><span data-stu-id="acde4-110">In order to demonstrate this constructor for the <xref:System.Data.DataTableReader> class, the sample creates a new **DataTableReader** based on an array that contains the two **DataTables**, and performs a simple operation, printing the contents from the first few columns to the console window.</span></span>  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="acde4-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="acde4-111">See Also</span></span>  
 [<span data-ttu-id="acde4-112">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="acde4-112">DataTableReaders</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 [<span data-ttu-id="acde4-113">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="acde4-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
