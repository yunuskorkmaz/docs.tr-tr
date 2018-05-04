---
title: DataTable bir veri kümesine ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 556d29a3-8fc9-4e38-b3ee-c188f7e7b155
ms.openlocfilehash: 3554790bb65310031b00ca5fb320aa4c111e1e11
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
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
 [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
