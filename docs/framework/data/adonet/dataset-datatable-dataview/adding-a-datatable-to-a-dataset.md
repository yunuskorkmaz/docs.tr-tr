---
title: DataSet'e DataTable ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 556d29a3-8fc9-4e38-b3ee-c188f7e7b155
ms.openlocfilehash: 5f2282b7aea8adf9e7574e2abe86af7cc5a487e8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43505927"
---
# <a name="adding-a-datatable-to-a-dataset"></a>DataSet'e DataTable ekleme
ADO.NET oluşturmanıza olanak sağlar <xref:System.Data.DataTable> nesneleri ve mevcut bir ekleme <xref:System.Data.DataSet>. Kısıtlama bilgi için ayarlayabileceğiniz bir <xref:System.Data.DataTable> kullanarak <xref:System.Data.DataTable.PrimaryKey%2A> ve <xref:System.Data.DataColumn.Unique%2A> özellikleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek oluşturur bir <xref:System.Data.DataSet>, yeni bir ekler <xref:System.Data.DataTable> nesnesini <xref:System.Data.DataSet>ve ardından üç ekler <xref:System.Data.DataColumn> tablosuna nesneleri. Son olarak, kodu bir sütun birincil anahtar sütunu ayarlar.  
  
 [!code-csharp[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/VB/source.vb#1)]  
  
## <a name="case-sensitivity"></a>Büyük/küçük harfe duyarlılık  
 İçinde iki veya daha fazla tablo veya aynı adı taşıyan ancak farklı büyük/küçük harf, ilişkileri varolabilir bir <xref:System.Data.DataSet>. Bu gibi durumlarda, tabloları ve ilişkileri adıyla başvuruları büyük küçük harfe duyarlı. Örneğin, varsa <xref:System.Data.DataSet> **veri kümesi** tabloları içeren **Table1** ve **table1**, başvuru **Table1** ada göre **dataSet.Tables["Table1"]**, ve **table1** olarak **dataSet.Tables["table1"]**. Tablo ya da başvuru girişimi **dataSet.Tables["TABLE1"]** bir özel durum oluşturur.  
  
 Bir tablo veya ilişki belirli bir ada sahip yalnızca büyük küçük harf duyarlılığı davranış geçerli değildir. Örneğin, varsa <xref:System.Data.DataSet> yalnızca **Table1**, kullanarak başvurabilirsiniz **dataSet.Tables["TABLE1"]**.  
  
> [!NOTE]
>  <xref:System.Data.DataSet.CaseSensitive%2A> Özelliği <xref:System.Data.DataSet> bu davranışı etkilemez. <xref:System.Data.DataSet.CaseSensitive%2A> Özellik geçerlidir verilerde <xref:System.Data.DataSet> ve sıralama, arama, filtreleme, zorunlu kısıtlamaları ve benzeri etkiler.  
  
## <a name="namespace-support"></a>Namespace desteği  
 Farklı ad alanlarına olsa bile 2.0 sürümünden öncekileri ADO.NET sürümlerinde aynı adı, iki tablo sahip olamaz. Bu sınırlama, ADO.NET 2. 0'kaldırıldı. A <xref:System.Data.DataSet> aynı olan iki tablo içerebilir <xref:System.Data.DataTable.TableName%2A> özellik değeri farklı ancak <xref:System.Data.DataTable.Namespace%2A> özellik değerleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
