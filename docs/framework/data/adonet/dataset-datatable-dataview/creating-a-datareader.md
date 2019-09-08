---
title: DataReader Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: 79cb2ce7ffae81aeba9aaca557e37ba566a8370c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784759"
---
# <a name="creating-a-datareader"></a>DataReader Oluşturma
<xref:System.Data.DataTable> <xref:System.Data.DataTable.CreateDataReader%2A> <xref:System.Data.DataSet> <xref:System.Data.DataSet.Tables%2A> Ve sınıflarının, bir veya daha fazla salt okuma, salt iletme sonuç kümesi olarak nesnenin koleksiyon içeriğini veya içeriğini döndüren bir yöntemi vardır. <xref:System.Data.DataSet> <xref:System.Data.DataTable>  
  
## <a name="example"></a>Örnek  
 Aşağıdaki konsol uygulaması bir <xref:System.Data.DataTable> örnek oluşturur. Örnek daha sonra, <xref:System.Data.DataTable> <xref:System.Data.DataTableReader>içinde yer alan sonuçlar arasında yineleme yapan <xref:System.Data.DataTable.CreateDataReader%2A> yöntemini çağıran bir yordama geçirilir.  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 Örnek, konsol penceresinde aşağıdaki çıktıyı görüntüler:  
  
```  
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
