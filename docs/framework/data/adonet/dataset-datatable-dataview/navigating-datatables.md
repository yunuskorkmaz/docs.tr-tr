---
title: DataTable içinde gezinme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
ms.openlocfilehash: f00e2171c1adf4ff99a669085131ebc8d38f7006
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46696111"
---
# <a name="navigating-datatables"></a>DataTable içinde gezinme
<xref:System.Data.DataTableReader> Bir veya daha fazla içeriğini alır <xref:System.Data.DataTable> nesneleri formunda bir veya daha fazla salt okunur, salt iletme sonuç kümeleri.  
  
 A <xref:System.Data.DataTableReader> kullanarak oluşturulursa, birden çok sonuç kümesi içerebilir <xref:System.Data.DataSet.CreateDataReader%2A> yöntemi. Birden fazla sonuç kümesi olduğunda <xref:System.Data.DataTableReader.NextResult%2A> yöntemi imleci sonraki sonuç kümesine ilerler. Bu yalnızca iletme bir işlemdir. Bir önceki sonuç kümesi için döndürülecek mümkün değildir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `TestConstructor` yöntemi oluşturur iki <xref:System.Data.DataTable> örnekleri. Bu oluşturucu için göstermek için <xref:System.Data.DataTableReader> sınıfı örneği oluşturur Yeni **DataTableReader** iki içeren bir dizisine göre **DataTable**ve basit bir işlem yapar içeriğini konsol penceresine ilk birkaç sütunlarından yazdırma.  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataTableReaders](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
