---
title: DataReader Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: 696eb4dfc334390e1968dd317d441f3c987a1f77
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040119"
---
# <a name="creating-a-datareader"></a>DataReader Oluşturma
<xref:System.Data.DataTable> ve <xref:System.Data.DataSet> sınıfları, bir veya daha fazla salt okuma, salt iletme sonuç kümesi olarak <xref:System.Data.DataTable> veya <xref:System.Data.DataSet> nesnesinin <xref:System.Data.DataSet.Tables%2A> koleksiyonun içeriğini döndüren bir <xref:System.Data.DataTable.CreateDataReader%2A> yöntemine sahiptir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki konsol uygulaması bir <xref:System.Data.DataTable> örneği oluşturur. Örnek daha sonra, <xref:System.Data.DataTableReader>içindeki sonuçlarla yinelenen <xref:System.Data.DataTable.CreateDataReader%2A> yöntemini çağıran bir yordama doldurulmuş <xref:System.Data.DataTable> geçirir.  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 Örnek, konsol penceresinde aşağıdaki çıktıyı görüntüler:  
  
```output  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataTable.CreateDataReader%2A>
- <xref:System.Data.DataSet.CreateDataReader%2A>
- [DataTableReaders](datatablereaders.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
