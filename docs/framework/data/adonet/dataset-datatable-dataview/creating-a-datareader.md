---
title: DataReader Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: 79cb2ce7ffae81aeba9aaca557e37ba566a8370c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784759"
---
# <a name="creating-a-datareader"></a><span data-ttu-id="82e1b-102">DataReader Oluşturma</span><span class="sxs-lookup"><span data-stu-id="82e1b-102">Creating a DataReader</span></span>
<span data-ttu-id="82e1b-103"><xref:System.Data.DataTable> <xref:System.Data.DataTable.CreateDataReader%2A> <xref:System.Data.DataSet> <xref:System.Data.DataSet.Tables%2A> Ve sınıflarının, bir veya daha fazla salt okuma, salt iletme sonuç kümesi olarak nesnenin koleksiyon içeriğini veya içeriğini döndüren bir yöntemi vardır. <xref:System.Data.DataSet> <xref:System.Data.DataTable></span><span class="sxs-lookup"><span data-stu-id="82e1b-103">The <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes have a <xref:System.Data.DataTable.CreateDataReader%2A> method that returns the contents of the <xref:System.Data.DataTable> or the contents of the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Tables%2A> collection as one or more read-only, forward-only result sets.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82e1b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="82e1b-104">Example</span></span>  
 <span data-ttu-id="82e1b-105">Aşağıdaki konsol uygulaması bir <xref:System.Data.DataTable> örnek oluşturur.</span><span class="sxs-lookup"><span data-stu-id="82e1b-105">The following console application creates a <xref:System.Data.DataTable> instance.</span></span> <span data-ttu-id="82e1b-106">Örnek daha sonra, <xref:System.Data.DataTable> <xref:System.Data.DataTableReader>içinde yer alan sonuçlar arasında yineleme yapan <xref:System.Data.DataTable.CreateDataReader%2A> yöntemini çağıran bir yordama geçirilir.</span><span class="sxs-lookup"><span data-stu-id="82e1b-106">The example then passes the filled <xref:System.Data.DataTable> to a procedure that calls the <xref:System.Data.DataTable.CreateDataReader%2A> method, which iterates through the results contained within the <xref:System.Data.DataTableReader>.</span></span>  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 <span data-ttu-id="82e1b-107">Örnek, konsol penceresinde aşağıdaki çıktıyı görüntüler:</span><span class="sxs-lookup"><span data-stu-id="82e1b-107">The example displays the following output in the console window:</span></span>  
  
```  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a><span data-ttu-id="82e1b-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82e1b-108">See also</span></span>

- <xref:System.Data.DataTable.CreateDataReader%2A>
- <xref:System.Data.DataSet.CreateDataReader%2A>
- [<span data-ttu-id="82e1b-109">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="82e1b-109">DataTableReaders</span></span>](datatablereaders.md)
- [<span data-ttu-id="82e1b-110">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="82e1b-110">ADO.NET Overview</span></span>](../ado-net-overview.md)
