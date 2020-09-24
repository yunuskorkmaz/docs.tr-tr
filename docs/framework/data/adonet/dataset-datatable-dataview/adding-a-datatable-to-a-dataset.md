---
title: DataSet’e DataTable Ekleme
description: DataTable nesneleri oluşturma ve bunları ADO.NET içinde mevcut bir veri kümesine ekleme hakkında bilgi edinmek için bu örnek koda bakın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 556d29a3-8fc9-4e38-b3ee-c188f7e7b155
ms.openlocfilehash: 6a5e3a89870b3959a6ac042b93414694e8a6cc1c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164902"
---
# <a name="adding-a-datatable-to-a-dataset"></a>DataSet’e DataTable Ekleme

ADO.NET, <xref:System.Data.DataTable> nesneleri oluşturmanızı ve bunları var olan bir nesneye eklemenizi sağlar <xref:System.Data.DataSet> . <xref:System.Data.DataTable>Ve özelliklerini kullanarak bir için kısıtlama bilgileri ayarlayabilirsiniz <xref:System.Data.DataTable.PrimaryKey%2A> <xref:System.Data.DataColumn.Unique%2A> .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek bir oluşturur <xref:System.Data.DataSet> , öğesine yeni bir <xref:System.Data.DataTable> nesnesi ekler <xref:System.Data.DataSet> ve ardından <xref:System.Data.DataColumn> tabloya üç nesne ekler. Son olarak, kod bir sütunu birincil anahtar sütunu olarak ayarlar.  
  
 [!code-csharp[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/VB/source.vb#1)]  
  
## <a name="case-sensitivity"></a>Büyük/küçük harf duyarlılığı  

 İki veya daha fazla tablo veya aynı ada sahip, ancak büyük küçük harfe sahip ilişkiler bir içinde bulunabilir <xref:System.Data.DataSet> . Bu gibi durumlarda, tabloya ve ilişkilerde ada göre başvurular büyük/küçük harfe duyarlıdır. Örneğin, <xref:System.Data.DataSet> **veri kümesi** **Table1** ve **Table1**tabloları Içeriyorsa, **Table1** adına ad **DataSet. Tables ["Table1"]** ve **Table1** as **DataSet. Tables ["Table1"]** olarak başvurabilirsiniz. Veri kümesi olarak tablolardan birine başvurulmaya çalışılıyor **. tablolar ["Table1"]** bir özel durum oluşturur.  
  
 Yalnızca bir tablo veya ilişki belirli bir ada sahipse, büyük/küçük harf duyarlılığı davranışı uygulanmaz. Örneğin, <xref:System.Data.DataSet> yalnızca **Table1**ise, **DataSet. Tables ["Table1"]** kullanarak buna başvurabilirsiniz.  
  
> [!NOTE]
> <xref:System.Data.DataSet.CaseSensitive%2A>Öğesinin özelliği <xref:System.Data.DataSet> Bu davranışı etkilemez. <xref:System.Data.DataSet.CaseSensitive%2A>Özelliği, içindeki veriler için geçerlidir <xref:System.Data.DataSet> ve sıralamayı, aramayı, filtrelemeyi, kısıtlamaları zorunlu tutmayı ve benzerlerini etkiler.  
  
## <a name="namespace-support"></a>Ad alanı desteği  

 2,0 'den önceki ADO.NET sürümlerinde, farklı ad boşluklarında olsalar bile, iki tablo aynı ada sahip olamaz. Bu sınırlama, ADO.NET 2,0 ' de kaldırılmıştır. <xref:System.Data.DataSet>, Aynı <xref:System.Data.DataTable.TableName%2A> özellik değerine sahip ancak farklı özellik değerlerine sahip iki tablo içerebilir <xref:System.Data.DataTable.Namespace%2A> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSets, DataTables ve DataViews](index.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
