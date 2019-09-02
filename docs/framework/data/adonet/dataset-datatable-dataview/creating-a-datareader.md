---
title: DataReader Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: cb39ead1fe15e3bfcf67370e4675dcae3bbf9801
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203902"
---
# <a name="creating-a-datareader"></a><span data-ttu-id="dde0e-102">DataReader Oluşturma</span><span class="sxs-lookup"><span data-stu-id="dde0e-102">Creating a DataReader</span></span>
<span data-ttu-id="dde0e-103"><xref:System.Data.DataTable> <xref:System.Data.DataTable.CreateDataReader%2A> <xref:System.Data.DataSet> <xref:System.Data.DataSet.Tables%2A> Ve sınıflarının, bir veya daha fazla salt okuma, salt iletme sonuç kümesi olarak nesnenin koleksiyon içeriğini veya içeriğini döndüren bir yöntemi vardır. <xref:System.Data.DataSet> <xref:System.Data.DataTable></span><span class="sxs-lookup"><span data-stu-id="dde0e-103">The <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes have a <xref:System.Data.DataTable.CreateDataReader%2A> method that returns the contents of the <xref:System.Data.DataTable> or the contents of the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Tables%2A> collection as one or more read-only, forward-only result sets.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dde0e-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="dde0e-104">Example</span></span>  
 <span data-ttu-id="dde0e-105">Aşağıdaki konsol uygulaması bir <xref:System.Data.DataTable> örnek oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dde0e-105">The following console application creates a <xref:System.Data.DataTable> instance.</span></span> <span data-ttu-id="dde0e-106">Örnek daha sonra, <xref:System.Data.DataTable> <xref:System.Data.DataTableReader>içinde yer alan sonuçlar arasında yineleme yapan <xref:System.Data.DataTable.CreateDataReader%2A> yöntemini çağıran bir yordama geçirilir.</span><span class="sxs-lookup"><span data-stu-id="dde0e-106">The example then passes the filled <xref:System.Data.DataTable> to a procedure that calls the <xref:System.Data.DataTable.CreateDataReader%2A> method, which iterates through the results contained within the <xref:System.Data.DataTableReader>.</span></span>  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 <span data-ttu-id="dde0e-107">Örnek, konsol penceresinde aşağıdaki çıktıyı görüntüler:</span><span class="sxs-lookup"><span data-stu-id="dde0e-107">The example displays the following output in the console window:</span></span>  
  
```  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a><span data-ttu-id="dde0e-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dde0e-108">See also</span></span>

- <xref:System.Data.DataTable.CreateDataReader%2A>
- <xref:System.Data.DataSet.CreateDataReader%2A>
- [<span data-ttu-id="dde0e-109">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="dde0e-109">DataTableReaders</span></span>](datatablereaders.md)
- [<span data-ttu-id="dde0e-110">ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="dde0e-110">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
