---
title: DataSet’e Veri Yükleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
ms.openlocfilehash: 26b77269b21e1b365f81746ba2df66d7df91677e
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504323"
---
# <a name="loading-data-into-a-dataset"></a>DataSet’e Veri Yükleme
A <xref:System.Data.DataSet> nesne, ilk ile LINQ to DataSet üzerinde sorgulayabilirsiniz önce doldurulmalıdır. Doldurmak için birkaç farklı şekilde <xref:System.Data.DataSet>. Örneğin, kullanabileceğiniz [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] sonuçları içine yükleyin ve veritabanını sorgulamak için <xref:System.Data.DataSet>. Daha fazla bilgi için [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
 Verileri yüklemek için başka bir yaygın yolu bir <xref:System.Data.DataSet> kullanmaktır <xref:System.Data.Common.DataAdapter> veritabanından veri almak için sınıf. Bu, aşağıdaki örnekte gösterilmiştir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte bir <xref:System.Data.Common.DataAdapter> 2002, yılın satış bilgi AdventureWorks veritabanını sorgulamak için ve sonuçlara yükleyen bir <xref:System.Data.DataSet>. Sonra <xref:System.Data.DataSet> olmuştur doldurulmuş, sorgular LINQ to DataSet kullanarak yazabilirsiniz. `FillDataSet` Yöntemi bu örnekte örnek sorgular, kullanılan [LINQ to DataSet örnekleri](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md). Daha fazla bilgi için [veri kümelerini sorgulama](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md).  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to DataSet Genel Bakış](../../../../docs/framework/data/adonet/linq-to-dataset-overview.md)
- [DataSet’leri Sorgulama](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [LINQ to DataSet Örnekleri](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
