---
title: DataSet’e Veri Yükleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
ms.openlocfilehash: 53f0f5a589a0033c9612f0465dff090ab04e3fc4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794950"
---
# <a name="loading-data-into-a-dataset"></a>DataSet’e Veri Yükleme
Bir <xref:System.Data.DataSet> nesne, LINQ to DataSet üzerinde sorgu yapabilmeniz için önce doldurulmalıdır. ' Yi doldurmanız <xref:System.Data.DataSet>için birkaç farklı yol vardır. Örneğin, veritabanını sorgulamak ve sonuçları [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.DataSet>öğesine yüklemek için ' yi kullanabilirsiniz. Daha fazla bilgi için bkz. [LINQ to SQL](./sql/linq/index.md).  
  
 Veri <xref:System.Data.DataSet> yüklemeye yönelik başka bir yaygın yol, veritabanından veri almak için <xref:System.Data.Common.DataAdapter> sınıfını kullanmaktır. Bu, aşağıdaki örnekte gösterilmiştir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, 2002 <xref:System.Data.Common.DataAdapter> yılında satış bilgileri için AdventureWorks veritabanını sorgulamak için bir kullanır ve sonuçları bir <xref:System.Data.DataSet>öğesine yükler. <xref:System.Data.DataSet> Doldurulduktan sonra, LINQ to DataSet kullanarak sorgu yazabilirsiniz. Bu örnekteki yöntem LINQ to DataSet örneklerde örnek sorgularda kullanılır. [](linq-to-dataset-examples.md) `FillDataSet` Daha fazla bilgi için bkz. [veri kümelerini sorgulama](querying-datasets-linq-to-dataset.md).  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to DataSet Genel Bakış](linq-to-dataset-overview.md)
- [DataSet’leri Sorgulama](querying-datasets-linq-to-dataset.md)
- [LINQ to DataSet Örnekleri](linq-to-dataset-examples.md)
