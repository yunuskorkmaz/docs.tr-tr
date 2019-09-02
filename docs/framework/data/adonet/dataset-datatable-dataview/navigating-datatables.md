---
title: DataTable İçinde Gezinme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
ms.openlocfilehash: b5837d647b72f8dd17c4a6d3664faf8976243d36
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204552"
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
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
