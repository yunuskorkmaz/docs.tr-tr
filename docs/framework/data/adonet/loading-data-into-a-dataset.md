---
title: DataSet’e Veri Yükleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
ms.openlocfilehash: cb5578d790e5d3f54f75f964bb3288d861c9d7c3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074059"
---
# <a name="loading-data-into-a-dataset"></a>DataSet’e Veri Yükleme
A <xref:System.Data.DataSet> nesne, ilk ile ele sorgulayabilirsiniz önce doldurulmalıdır [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. Doldurmak için birkaç farklı şekilde <xref:System.Data.DataSet>. Örneğin, kullanabileceğiniz [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] sonuçları içine yükleyin ve veritabanını sorgulamak için <xref:System.Data.DataSet>. Daha fazla bilgi için [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
 Verileri yüklemek için başka bir yaygın yolu bir <xref:System.Data.DataSet> kullanmaktır <xref:System.Data.Common.DataAdapter> veritabanından veri almak için sınıf. Bu, aşağıdaki örnekte gösterilmiştir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte bir <xref:System.Data.Common.DataAdapter> 2002, yılın satış bilgi AdventureWorks veritabanını sorgulamak için ve sonuçlara yükleyen bir <xref:System.Data.DataSet>. Sonra <xref:System.Data.DataSet> kullanarak sorgular yazabilirsiniz doldurulmadı [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. `FillDataSet` Yöntemi bu örnekte örnek sorgular, kullanılan [LINQ to DataSet örnekleri](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md). Daha fazla bilgi için [veri kümelerini sorgulama](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md).  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to DataSet Genel Bakış](../../../../docs/framework/data/adonet/linq-to-dataset-overview.md)
- [DataSet’leri Sorgulama](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [LINQ to DataSet Örnekleri](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
