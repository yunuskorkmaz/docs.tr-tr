---
title: DataReader Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: 3af6ae3a8f4ecc3ec34c186ce55c1c77c27514a9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202349"
---
# <a name="creating-a-datareader"></a><span data-ttu-id="fc201-102">DataReader Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fc201-102">Creating a DataReader</span></span>

<span data-ttu-id="fc201-103"><xref:System.Data.DataTable>Ve <xref:System.Data.DataSet> sınıflarının, <xref:System.Data.DataTable.CreateDataReader%2A> <xref:System.Data.DataTable> <xref:System.Data.DataSet> <xref:System.Data.DataSet.Tables%2A> bir veya daha fazla salt okuma, salt iletme sonuç kümesi olarak nesnenin koleksiyon içeriğini veya içeriğini döndüren bir yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="fc201-103">The <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes have a <xref:System.Data.DataTable.CreateDataReader%2A> method that returns the contents of the <xref:System.Data.DataTable> or the contents of the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Tables%2A> collection as one or more read-only, forward-only result sets.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc201-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="fc201-104">Example</span></span>  

 <span data-ttu-id="fc201-105">Aşağıdaki konsol uygulaması bir örnek oluşturur <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="fc201-105">The following console application creates a <xref:System.Data.DataTable> instance.</span></span> <span data-ttu-id="fc201-106">Örnek daha sonra <xref:System.Data.DataTable> <xref:System.Data.DataTable.CreateDataReader%2A> , içinde yer alan sonuçlar arasında yineleme yapan yöntemini çağıran bir yordama geçirilir <xref:System.Data.DataTableReader> .</span><span class="sxs-lookup"><span data-stu-id="fc201-106">The example then passes the filled <xref:System.Data.DataTable> to a procedure that calls the <xref:System.Data.DataTable.CreateDataReader%2A> method, which iterates through the results contained within the <xref:System.Data.DataTableReader>.</span></span>  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 <span data-ttu-id="fc201-107">Örnek, konsol penceresinde aşağıdaki çıktıyı görüntüler:</span><span class="sxs-lookup"><span data-stu-id="fc201-107">The example displays the following output in the console window:</span></span>  
  
```output  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a><span data-ttu-id="fc201-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc201-108">See also</span></span>

- <xref:System.Data.DataTable.CreateDataReader%2A>
- <xref:System.Data.DataSet.CreateDataReader%2A>
- [<span data-ttu-id="fc201-109">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="fc201-109">DataTableReaders</span></span>](datatablereaders.md)
- [<span data-ttu-id="fc201-110">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fc201-110">ADO.NET Overview</span></span>](../ado-net-overview.md)
