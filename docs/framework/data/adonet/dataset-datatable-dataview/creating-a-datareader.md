---
description: 'Daha fazla bilgi edinin: DataReader oluşturma'
title: DataReader Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: 3a9f47ce90beaa3da4c2835f8b75e770a6179a9e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725109"
---
# <a name="creating-a-datareader"></a><span data-ttu-id="375f1-103">DataReader Oluşturma</span><span class="sxs-lookup"><span data-stu-id="375f1-103">Creating a DataReader</span></span>

<span data-ttu-id="375f1-104"><xref:System.Data.DataTable>Ve <xref:System.Data.DataSet> sınıflarının, <xref:System.Data.DataTable.CreateDataReader%2A> <xref:System.Data.DataTable> <xref:System.Data.DataSet> <xref:System.Data.DataSet.Tables%2A> bir veya daha fazla salt okuma, salt iletme sonuç kümesi olarak nesnenin koleksiyon içeriğini veya içeriğini döndüren bir yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="375f1-104">The <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes have a <xref:System.Data.DataTable.CreateDataReader%2A> method that returns the contents of the <xref:System.Data.DataTable> or the contents of the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Tables%2A> collection as one or more read-only, forward-only result sets.</span></span>  
  
## <a name="example"></a><span data-ttu-id="375f1-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="375f1-105">Example</span></span>  

 <span data-ttu-id="375f1-106">Aşağıdaki konsol uygulaması bir örnek oluşturur <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="375f1-106">The following console application creates a <xref:System.Data.DataTable> instance.</span></span> <span data-ttu-id="375f1-107">Örnek daha sonra <xref:System.Data.DataTable> <xref:System.Data.DataTable.CreateDataReader%2A> , içinde yer alan sonuçlar arasında yineleme yapan yöntemini çağıran bir yordama geçirilir <xref:System.Data.DataTableReader> .</span><span class="sxs-lookup"><span data-stu-id="375f1-107">The example then passes the filled <xref:System.Data.DataTable> to a procedure that calls the <xref:System.Data.DataTable.CreateDataReader%2A> method, which iterates through the results contained within the <xref:System.Data.DataTableReader>.</span></span>  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 <span data-ttu-id="375f1-108">Örnek, konsol penceresinde aşağıdaki çıktıyı görüntüler:</span><span class="sxs-lookup"><span data-stu-id="375f1-108">The example displays the following output in the console window:</span></span>  
  
```output  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a><span data-ttu-id="375f1-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="375f1-109">See also</span></span>

- <xref:System.Data.DataTable.CreateDataReader%2A>
- <xref:System.Data.DataSet.CreateDataReader%2A>
- [<span data-ttu-id="375f1-110">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="375f1-110">DataTableReaders</span></span>](datatablereaders.md)
- [<span data-ttu-id="375f1-111">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="375f1-111">ADO.NET Overview</span></span>](../ado-net-overview.md)
