---
title: "DataReader oluşturma"
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
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b603e4fad628d0bb338213420059ffa411acd432
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
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
