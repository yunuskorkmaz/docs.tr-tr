---
title: DataReader oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: 1ede51ed9119051a647fd27d8d02cd2c93e61bbb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510043"
---
# <a name="creating-a-datareader"></a>DataReader oluşturma
<xref:System.Data.DataTable> Ve <xref:System.Data.DataSet> sınıfları sahip bir <xref:System.Data.DataTable.CreateDataReader%2A> içeriğini döndüren yöntem <xref:System.Data.DataTable> veya içeriğini <xref:System.Data.DataSet> nesnenin <xref:System.Data.DataSet.Tables%2A> olarak bir veya daha fazla salt okunur, salt iletme sonuç kümeleri koleksiyonu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki konsol uygulaması oluşturan bir <xref:System.Data.DataTable> örneği. Örnek daha sonra doldurulmuş geçirir <xref:System.Data.DataTable> çağırdığı bir yordam için <xref:System.Data.DataTable.CreateDataReader%2A> içindeki sonuçları gezinir yöntemi <xref:System.Data.DataTableReader>.  
  
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
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
