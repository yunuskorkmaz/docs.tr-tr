---
description: 'Daha fazla bilgi edinin: DataReader oluşturma'
title: DataReader Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: 3a9f47ce90beaa3da4c2835f8b75e770a6179a9e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725109"
---
# <a name="creating-a-datareader"></a>DataReader Oluşturma

<xref:System.Data.DataTable>Ve <xref:System.Data.DataSet> sınıflarının, <xref:System.Data.DataTable.CreateDataReader%2A> <xref:System.Data.DataTable> <xref:System.Data.DataSet> <xref:System.Data.DataSet.Tables%2A> bir veya daha fazla salt okuma, salt iletme sonuç kümesi olarak nesnenin koleksiyon içeriğini veya içeriğini döndüren bir yöntemi vardır.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki konsol uygulaması bir örnek oluşturur <xref:System.Data.DataTable> . Örnek daha sonra <xref:System.Data.DataTable> <xref:System.Data.DataTable.CreateDataReader%2A> , içinde yer alan sonuçlar arasında yineleme yapan yöntemini çağıran bir yordama geçirilir <xref:System.Data.DataTableReader> .  
  
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
