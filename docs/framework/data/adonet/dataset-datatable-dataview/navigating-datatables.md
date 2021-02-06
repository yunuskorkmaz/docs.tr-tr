---
description: "Hakkında daha fazla bilgi edinin: DataTable 'a gitme"
title: DataTable İçinde Gezinme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
ms.openlocfilehash: 0564af241adc082ef1b736f2e4a561328fbcc976
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651788"
---
# <a name="navigating-datatables"></a>DataTable İçinde Gezinme

, Bir veya daha fazla <xref:System.Data.DataTableReader> <xref:System.Data.DataTable> nesnenin içeriğini bir veya daha fazla salt okunurdur, salt ileri bir sonuç kümesi biçiminde edinir.  
  
 <xref:System.Data.DataTableReader>, Yöntemi kullanılarak oluşturulduysa, birden çok sonuç kümesi içerebilir <xref:System.Data.DataSet.CreateDataReader%2A> . Birden fazla sonuç kümesi olduğunda, <xref:System.Data.DataTableReader.NextResult%2A> yöntemi imleci bir sonraki sonuç kümesine ilerletir. Bu yalnızca ileri bir işlemdir. Önceki bir sonuç kümesine dönmek mümkün değildir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnekte, `TestConstructor` yöntemi iki <xref:System.Data.DataTable> örnek oluşturur. Sınıf için bu oluşturucuyu göstermek amacıyla örnek, <xref:System.Data.DataTableReader> Iki **DataTable** içeren bir diziyi temel alan yeni bir **DataTableReader** oluşturur ve basit bir işlem gerçekleştirir ve ilk birkaç sütundaki içerikleri konsol penceresine yazdırıyor.  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataTableReaders](datatablereaders.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
