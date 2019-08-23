---
title: DataSet’e DataTable Ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 556d29a3-8fc9-4e38-b3ee-c188f7e7b155
ms.openlocfilehash: 2bc0bca55dcdc350537f0826ab3a675747ee5497
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951323"
---
# <a name="adding-a-datatable-to-a-dataset"></a>DataSet’e DataTable Ekleme
ADO.net, nesneleri oluşturmanızı <xref:System.Data.DataTable> ve bunları var olan <xref:System.Data.DataSet>bir nesneye eklemenizi sağlar. Ve<xref:System.Data.DataTable.PrimaryKey%2A> <xref:System.Data.DataTable> özelliklerinikullanarakbiriçin<xref:System.Data.DataColumn.Unique%2A> kısıtlama bilgileri ayarlayabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir <xref:System.Data.DataSet>oluşturur, <xref:System.Data.DataSet>öğesine yeni <xref:System.Data.DataTable> bir nesnesi ekler ve ardından tabloya üç <xref:System.Data.DataColumn> nesne ekler. Son olarak, kod bir sütunu birincil anahtar sütunu olarak ayarlar.  
  
 [!code-csharp[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/VB/source.vb#1)]  
  
## <a name="case-sensitivity"></a>Büyük/küçük harf duyarlılığı  
 İki veya daha fazla tablo veya aynı ada sahip, ancak büyük küçük harfe sahip ilişkiler bir <xref:System.Data.DataSet>içinde bulunabilir. Bu gibi durumlarda, tabloya ve ilişkilerde ada göre başvurular büyük/küçük harfe duyarlıdır. Örneğin, <xref:System.Data.DataSet> **veri kümesi** **Table1** ve **Table1**tabloları içeriyorsa, **Table1** adına ad **DataSet. Tables ["Table1"]** ve **Table1** as **DataSet. Tables ["Table1"]** olarak başvurabilirsiniz. Veri kümesi olarak tablolardan birine başvurulmaya çalışılıyor **. tablolar ["Table1"]** bir özel durum oluşturur.  
  
 Yalnızca bir tablo veya ilişki belirli bir ada sahipse, büyük/küçük harf duyarlılığı davranışı uygulanmaz. Örneğin, yalnızca **Table1**ise <xref:System.Data.DataSet> , **DataSet. Tables ["Table1"]** kullanarak buna başvurabilirsiniz.  
  
> [!NOTE]
> <xref:System.Data.DataSet.CaseSensitive%2A> Öğesinin<xref:System.Data.DataSet> özelliği bu davranışı etkilemez. <xref:System.Data.DataSet.CaseSensitive%2A> Özelliği ,<xref:System.Data.DataSet> içindeki veriler için geçerlidir ve sıralamayı, aramayı, filtrelemeyi, kısıtlamaları zorunlu tutmayı ve benzerlerini etkiler.  
  
## <a name="namespace-support"></a>Ad alanı desteği  
 2,0 'den önceki ADO.NET sürümlerinde, farklı ad boşluklarında olsalar bile, iki tablo aynı ada sahip olamaz. Bu sınırlama, ADO.NET 2,0 ' de kaldırılmıştır. , Aynı <xref:System.Data.DataTable.TableName%2A> özellik değerine sahip ancak farklı <xref:System.Data.DataTable.Namespace%2A> özellik değerlerine sahip iki tablo içerebilir. <xref:System.Data.DataSet>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
