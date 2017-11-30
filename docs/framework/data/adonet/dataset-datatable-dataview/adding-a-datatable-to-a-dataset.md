---
title: "DataTable bir veri kümesine ekleme"
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
ms.assetid: 556d29a3-8fc9-4e38-b3ee-c188f7e7b155
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f70292794866530de5b7abf7dac1edd09d300c94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="adding-a-datatable-to-a-dataset"></a>DataTable bir veri kümesine ekleme
ADO.NET oluşturmanıza olanak sağlayan <xref:System.Data.DataTable> nesneleri ve var olan eklemesini <xref:System.Data.DataSet>. Kısıtlama bilgi için ayarlayabileceğiniz bir <xref:System.Data.DataTable> kullanarak <xref:System.Data.DataTable.PrimaryKey%2A> ve <xref:System.Data.DataColumn.Unique%2A> özellikleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte oluşturur bir <xref:System.Data.DataSet>, yeni bir ekler <xref:System.Data.DataTable> nesnesini <xref:System.Data.DataSet>ve üç ekler <xref:System.Data.DataColumn> tablosuna nesneleri. Son olarak, bu kod bir sütun birincil anahtar sütunu ayarlar.  
  
 [!code-csharp[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/VB/source.vb#1)]  
  
## <a name="case-sensitivity"></a>Büyük/küçük harfe duyarlılık  
 İki veya daha fazla tablo veya aynı adlı ancak farklı büyük/küçük harf, ilişkileri içinde bulunabilir bir <xref:System.Data.DataSet>. Böyle durumlarda, tabloları ve ilişkileri ada göre başvuruları büyük küçük harf duyarlıdır. Örneğin, varsa <xref:System.Data.DataSet> **dataSet** tabloları içeren **tablo1** ve **tablo1**, başvuru **tablo1** ada göre **dataSet.Tables["Table1"]**, ve **tablo1** olarak **dataSet.Tables["table1"]**. Tablolardan birini başvuru girişimi **dataSet.Tables["TABLE1"]** bir özel durum oluşturur.  
  
 Bir tablo veya ilişki belirli bir ada sahip yalnızca büyük küçük harf duyarlılığı davranış geçerli değildir. Örneğin, varsa <xref:System.Data.DataSet> yalnızca **tablo1**, kullanarak başvuru **dataSet.Tables["TABLE1"]**.  
  
> [!NOTE]
>  <xref:System.Data.DataSet.CaseSensitive%2A> Özelliği <xref:System.Data.DataSet> bu davranışını etkilemez. <xref:System.Data.DataSet.CaseSensitive%2A> Özelliği uygulanır verilerde <xref:System.Data.DataSet> ve sıralama, arama, filtreleme, zorunlu kısıtlamaları ve benzeri etkiler.  
  
## <a name="namespace-support"></a>Namespace desteği  
 Farklı ad alanlarında olsa bile ADO.NET'ın 2.0'den önceki sürümlerinde aynı adlı iki tablo sahip. Bu sınırlama aşağıdaki haller ADO.NET 2.0 kaldırıldı. A <xref:System.Data.DataSet> aynı olan iki tablo içerebilir <xref:System.Data.DataTable.TableName%2A> özellik değeri farklı ancak <xref:System.Data.DataTable.Namespace%2A> özellik değerleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri kümeleri, DataTable ve DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
