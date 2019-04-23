---
title: DataReader Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: 8932f393af58f2014f643c5b6ebd6dc7a127b7eb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59122011"
---
# <a name="creating-a-datareader"></a><span data-ttu-id="2afdd-102">DataReader Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2afdd-102">Creating a DataReader</span></span>
<span data-ttu-id="2afdd-103"><xref:System.Data.DataTable> Ve <xref:System.Data.DataSet> sınıfları sahip bir <xref:System.Data.DataTable.CreateDataReader%2A> içeriğini döndüren yöntem <xref:System.Data.DataTable> veya içeriğini <xref:System.Data.DataSet> nesnenin <xref:System.Data.DataSet.Tables%2A> olarak bir veya daha fazla salt okunur, salt iletme sonuç kümeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="2afdd-103">The <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes have a <xref:System.Data.DataTable.CreateDataReader%2A> method that returns the contents of the <xref:System.Data.DataTable> or the contents of the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Tables%2A> collection as one or more read-only, forward-only result sets.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2afdd-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="2afdd-104">Example</span></span>  
 <span data-ttu-id="2afdd-105">Aşağıdaki konsol uygulaması oluşturan bir <xref:System.Data.DataTable> örneği.</span><span class="sxs-lookup"><span data-stu-id="2afdd-105">The following console application creates a <xref:System.Data.DataTable> instance.</span></span> <span data-ttu-id="2afdd-106">Örnek daha sonra doldurulmuş geçirir <xref:System.Data.DataTable> çağırdığı bir yordam için <xref:System.Data.DataTable.CreateDataReader%2A> içindeki sonuçları gezinir yöntemi <xref:System.Data.DataTableReader>.</span><span class="sxs-lookup"><span data-stu-id="2afdd-106">The example then passes the filled <xref:System.Data.DataTable> to a procedure that calls the <xref:System.Data.DataTable.CreateDataReader%2A> method, which iterates through the results contained within the <xref:System.Data.DataTableReader>.</span></span>  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 <span data-ttu-id="2afdd-107">Örnek, konsol penceresinde aşağıdaki çıktıyı görüntüler:</span><span class="sxs-lookup"><span data-stu-id="2afdd-107">The example displays the following output in the console window:</span></span>  
  
```  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a><span data-ttu-id="2afdd-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2afdd-108">See also</span></span>

- <xref:System.Data.DataTable.CreateDataReader%2A>
- <xref:System.Data.DataSet.CreateDataReader%2A>
- [<span data-ttu-id="2afdd-109">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="2afdd-109">DataTableReaders</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)
- [<span data-ttu-id="2afdd-110">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="2afdd-110">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
