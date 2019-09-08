---
title: DataTable İçinde Gezinme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
ms.openlocfilehash: 5008f8397b7d396b14fdfe8e24f1e59785c4319d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785260"
---
# <a name="navigating-datatables"></a>DataTable İçinde Gezinme
, <xref:System.Data.DataTableReader> Bir veya daha fazla <xref:System.Data.DataTable> nesnenin içeriğini bir veya daha fazla salt okunurdur, salt ileri bir sonuç kümesi biçiminde edinir.  
  
 <xref:System.Data.DataTableReader> ,<xref:System.Data.DataSet.CreateDataReader%2A> Yöntemi kullanılarak oluşturulduysa, birden çok sonuç kümesi içerebilir. Birden fazla sonuç kümesi olduğunda, <xref:System.Data.DataTableReader.NextResult%2A> yöntemi imleci bir sonraki sonuç kümesine ilerletir. Bu yalnızca ileri bir işlemdir. Önceki bir sonuç kümesine dönmek mümkün değildir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `TestConstructor` yöntemi iki <xref:System.Data.DataTable> örnek oluşturur. <xref:System.Data.DataTableReader> Sınıf için bu oluşturucuyu göstermek amacıyla örnek, iki **DataTable**içeren bir diziyi temel alan yeni bir **DataTableReader** oluşturur ve basit bir işlem gerçekleştirir ve içeriği ilk birkaç kez yazdırıyor Konsol penceresine sütunlar.  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataTableReaders](datatablereaders.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
