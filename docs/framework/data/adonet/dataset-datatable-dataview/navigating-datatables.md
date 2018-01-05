---
title: DataTables gezinme
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
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: de3d0125adc6f18ebebf13ff3cf2fa5119ec17df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="navigating-datatables"></a>DataTables gezinme
<xref:System.Data.DataTableReader> Bir veya daha fazla içeriğini alır <xref:System.Data.DataTable> nesneleri bir veya daha fazla salt okunur, yalnızca ileri sonuç kümesi biçiminde.  
  
 A <xref:System.Data.DataTableReader> kullanarak oluşturulursa, birden çok sonuç kümesi içerebilir <xref:System.Data.DataSet.CreateDataReader%2A> yöntemi. Birden çok sonuç kümesi olduğunda <xref:System.Data.DataTableReader.NextResult%2A> yöntemi sonraki sonuç kümesini imleci ilerler. Bu yalnızca ileri bir işlemdir. Önceki bir sonuç kümesi döndürmek mümkün değildir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `TestConstructor` yöntemi iki oluşturur <xref:System.Data.DataTable> örnekleri. Bu oluşturucu için göstermek için <xref:System.Data.DataTableReader> sınıfı, bir örnek oluşturur Yeni bir **DataTableReader** iki içeren bir dizisine göre **DataTables**ve basit bir işlemi gerçekleştirir içeriği ilk birkaç sütunlarından konsol penceresine yazdırma.  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataTableReaders](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
