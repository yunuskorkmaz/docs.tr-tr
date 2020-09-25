---
title: DataSet’e Veri Yükleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
ms.openlocfilehash: c870cabc875aa0152910ce916819fb1ff1c018f7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166722"
---
# <a name="loading-data-into-a-dataset"></a>DataSet’e Veri Yükleme

Bir <xref:System.Data.DataSet> nesne, LINQ to DataSet üzerinde sorgu yapabilmeniz için önce doldurulmalıdır. ' Yi doldurmanız için birkaç farklı yol vardır <xref:System.Data.DataSet> . Örneğin, [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] veritabanını sorgulamak ve sonuçları öğesine yüklemek için ' yi kullanabilirsiniz <xref:System.Data.DataSet> . Daha fazla bilgi için bkz. [LINQ to SQL](./sql/linq/index.md).  
  
 Veri yüklemeye yönelik başka bir yaygın yol <xref:System.Data.DataSet> , <xref:System.Data.Common.DataAdapter> veritabanından veri almak için sınıfını kullanmaktır. Bu, aşağıdaki örnekte gösterilmiştir.  
  
## <a name="example"></a>Örnek  

 Bu örnek, <xref:System.Data.Common.DataAdapter> 2002 yılında satış bilgileri Için AdventureWorks veritabanını sorgulamak için bir kullanır ve sonuçları bir öğesine yükler <xref:System.Data.DataSet> . <xref:System.Data.DataSet>Doldurulduktan sonra, LINQ to DataSet kullanarak sorgu yazabilirsiniz. `FillDataSet`Bu örnekteki yöntem [LINQ to DataSet örneklerde](linq-to-dataset-examples.md)örnek sorgularda kullanılır. Daha fazla bilgi için bkz. [veri kümelerini sorgulama](querying-datasets-linq-to-dataset.md).  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to DataSet Genel Bakış](linq-to-dataset-overview.md)
- [DataSet’leri Sorgulama](querying-datasets-linq-to-dataset.md)
- [LINQ to DataSet Örnekleri](linq-to-dataset-examples.md)
