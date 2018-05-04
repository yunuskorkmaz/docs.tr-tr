---
title: DataReader oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: c5073a553926fdfdd78b0b6837cdc07b58ac7faf
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="creating-a-datareader"></a>DataReader oluşturma
<xref:System.Data.DataTable> Ve <xref:System.Data.DataSet> sınıflarının bir <xref:System.Data.DataTable.CreateDataReader%2A> içeriğini döndürür yöntemi <xref:System.Data.DataTable> veya içeriğini <xref:System.Data.DataSet> nesnenin <xref:System.Data.DataSet.Tables%2A> bir veya daha fazla salt okunur, yalnızca ileri sonuç kümeleri olarak koleksiyonu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki konsol uygulaması oluşturur bir <xref:System.Data.DataTable> örneği. Bu örnek daha sonra dolu geçirir <xref:System.Data.DataTable> çağıran bir yordamı için <xref:System.Data.DataTable.CreateDataReader%2A> kapsamında yer alan sonuçları dolaşır yöntemi <xref:System.Data.DataTableReader>.  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 Örnek, konsol penceresinde aşağıdaki çıktıyı görüntüler:  
  
```  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.DataTable.CreateDataReader%2A>  
 <xref:System.Data.DataSet.CreateDataReader%2A>  
 [DataTableReaders](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
