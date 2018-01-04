---
title: "Bir veri kümesine veri yükleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 471a13b5d209def227bf8bc57b1551550b76a0c8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="loading-data-into-a-dataset"></a>Bir veri kümesine veri yükleme
A <xref:System.Data.DataSet> nesnesi, ilk ile üzerinden sorgulayabilirsiniz önce doldurulmalıdır [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. Doldurmak için birkaç farklı yolu vardır <xref:System.Data.DataSet>. Örneğin, kullanabileceğiniz [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] veritabanını sorgulamak ve sonuçları içine yüklemek için <xref:System.Data.DataSet>. Daha fazla bilgi için bkz: [LINQ-SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
 Verileri yüklemek için başka bir yaygın yolu bir <xref:System.Data.DataSet> kullanmaktır <xref:System.Data.Common.DataAdapter> veritabanından veri almak için sınıf. Bu, aşağıdaki örnekte gösterilmiştir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte bir <xref:System.Data.Common.DataAdapter> 2002, yıldan satış bilgileri AdventureWorks veritabanını sorgulamak için ve sonuçları içine yükler bir <xref:System.Data.DataSet>. Sonra <xref:System.Data.DataSet> , bu sorguları kullanarak yazabilirsiniz doldurulmuş olan [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. `FillDataSet` Yöntemi bu örnekte, örnek sorguların kullanılıyor [LINQ-DataSet örnekler](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md). Daha fazla bilgi için bkz: [sorgulama veri kümeleri](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md).  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to DataSet Genel Bakış](../../../../docs/framework/data/adonet/linq-to-dataset-overview.md)  
 [DataSet’leri Sorgulama](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [LINQ to DataSet Örnekleri](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
