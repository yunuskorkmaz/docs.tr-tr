---
title: DataReader Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: 696eb4dfc334390e1968dd317d441f3c987a1f77
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040119"
---
# <a name="creating-a-datareader"></a><span data-ttu-id="fd6df-102">DataReader Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fd6df-102">Creating a DataReader</span></span>
<span data-ttu-id="fd6df-103"><xref:System.Data.DataTable> ve <xref:System.Data.DataSet> sınıfları, bir veya daha fazla salt okuma, salt iletme sonuç kümesi olarak <xref:System.Data.DataTable> veya <xref:System.Data.DataSet> nesnesinin <xref:System.Data.DataSet.Tables%2A> koleksiyonun içeriğini döndüren bir <xref:System.Data.DataTable.CreateDataReader%2A> yöntemine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="fd6df-103">The <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes have a <xref:System.Data.DataTable.CreateDataReader%2A> method that returns the contents of the <xref:System.Data.DataTable> or the contents of the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Tables%2A> collection as one or more read-only, forward-only result sets.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd6df-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="fd6df-104">Example</span></span>  
 <span data-ttu-id="fd6df-105">Aşağıdaki konsol uygulaması bir <xref:System.Data.DataTable> örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fd6df-105">The following console application creates a <xref:System.Data.DataTable> instance.</span></span> <span data-ttu-id="fd6df-106">Örnek daha sonra, <xref:System.Data.DataTableReader>içindeki sonuçlarla yinelenen <xref:System.Data.DataTable.CreateDataReader%2A> yöntemini çağıran bir yordama doldurulmuş <xref:System.Data.DataTable> geçirir.</span><span class="sxs-lookup"><span data-stu-id="fd6df-106">The example then passes the filled <xref:System.Data.DataTable> to a procedure that calls the <xref:System.Data.DataTable.CreateDataReader%2A> method, which iterates through the results contained within the <xref:System.Data.DataTableReader>.</span></span>  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 <span data-ttu-id="fd6df-107">Örnek, konsol penceresinde aşağıdaki çıktıyı görüntüler:</span><span class="sxs-lookup"><span data-stu-id="fd6df-107">The example displays the following output in the console window:</span></span>  
  
```output  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a><span data-ttu-id="fd6df-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd6df-108">See also</span></span>

- <xref:System.Data.DataTable.CreateDataReader%2A>
- <xref:System.Data.DataSet.CreateDataReader%2A>
- [<span data-ttu-id="fd6df-109">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="fd6df-109">DataTableReaders</span></span>](datatablereaders.md)
- [<span data-ttu-id="fd6df-110">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fd6df-110">ADO.NET Overview</span></span>](../ado-net-overview.md)
