---
title: Verileri Sıralama ve Filtreleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
ms.openlocfilehash: 89e2fdf656fb06ee545ba936f033646ad86182d4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183383"
---
# <a name="sorting-and-filtering-data"></a>Verileri Sıralama ve Filtreleme

, <xref:System.Data.DataView> Bir içindeki verileri sıralamak ve filtrelemek için çeşitli yollar sağlar <xref:System.Data.DataTable> :  
  
- <xref:System.Data.DataView.Sort%2A>Özelliğini kullanarak tek veya birden çok sütun sıralama düzeni belirtebilir ve ASC (artan) ve DESC (azalan) parametreleri dahil edebilirsiniz.  
  
- <xref:System.Data.DataView.ApplyDefaultSort%2A>Özelliğini, tablonun birincil anahtar sütununa veya sütunlarına göre artan sırada otomatik olarak bir sıralama düzeni oluşturmak için kullanabilirsiniz. <xref:System.Data.DataView.ApplyDefaultSort%2A> yalnızca **sıralama** özelliği null veya boş bir dize olduğunda ve tablonun tanımlı bir birincil anahtarı olduğunda geçerlidir.  
  
- <xref:System.Data.DataView.RowFilter%2A>Özelliğini, sütun değerlerine göre satır alt kümelerini belirtmek için kullanabilirsiniz. **RowFilter** özelliği için geçerli ifadeler hakkında daha fazla bilgi için, sınıfının özelliği için başvuru bilgilerine bakın <xref:System.Data.DataColumn.Expression%2A> <xref:System.Data.DataColumn> .  
  
     Verilerin bir alt kümesinin dinamik görünümünü sağlamanın aksine veriler üzerinde belirli bir sorgunun sonuçlarını döndürmek istiyorsanız, <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> **RowFilter** özelliğini ayarlamak yerine en iyi performansı elde etmek için **DataView** 'ın veya yöntemlerini kullanın. **RowFilter** özelliğinin ayarlanması, verilerin dizinini yeniden oluşturur, uygulamanıza ek yük ekler ve performansı azaltır. **RowFilter** özelliği, bir bağlantılı denetimin filtrelenmiş sonuçları görüntülediği veriye dayalı bir uygulamada en iyi şekilde kullanılır. **Find** ve **FindRows** yöntemleri, dizinin yeniden oluşturulmasını gerektirmeden geçerli dizinden yararlanır. **Find** ve **FindRows** yöntemleri hakkında daha fazla bilgi Için bkz. [satırları bulma](finding-rows.md).  
  
- <xref:System.Data.DataView.RowStateFilter%2A>Hangi satır sürümlerinin görüntüleneceği belirlemek için özelliğini kullanabilirsiniz. **DataView** , temel alınan satırın **RowState** öğesine bağlı olarak hangi satır sürümünün sergileceğini dolaylı olarak yönetir. Örneğin, **RowStateFilter** , **DataViewRowState. Deleted**olarak ayarlandıysa, **geçerli** satır sürümü bulunmadığından **DataView** , **silinen** tüm satırların **orijinal** satır sürümünü kullanıma sunar. **DataRowView**'ın **ROWVERSION** özelliğini kullanarak bir satırın hangi satır sürümünün gösterilmesini belirleyebilirsiniz.  
  
     Aşağıdaki tabloda, **DataViewRowState**seçenekleri gösterilmektedir.  
  
    |DataViewRowState seçenekleri|Açıklama|  
    |------------------------------|-----------------|  
    |**CurrentRows**|Tüm **değişmemiş**, **eklenen**ve **değiştirilen** satırların **geçerli** satır sürümü. Bu varsayılan seçenektir.|  
    |**Eklenirse**|Tüm **eklenen** satırların **geçerli** satır sürümü.|  
    |**Silindi**|**Silinen** tüm satırların **orijinal** satır sürümü.|  
    |**ModifiedCurrent**|**Değiştirilen** tüm satırların **geçerli** satır sürümü.|  
    |**Modifiedorijinal**|**Değiştirilen** tüm satırların **orijinal** satır sürümü.|  
    |**Hiçbiri**|Satır yok.|  
    |**OriginalRows**|Tüm **değişmemiş**, **değiştirilen**ve **silinen** satırların **orijinal** satır sürümü.|  
    |**Değiştirilmediği**|**Değişmeyen** tüm satırların **geçerli** satır sürümü.|  
  
 Satır durumları ve satır sürümleri hakkında daha fazla bilgi için bkz. [Satır durumları ve satır sürümleri](row-states-and-row-versions.md).  
  
 Aşağıdaki kod örneği, stoktaki birim sayısının yeniden sipariş düzeyine eşit veya daha küçük olduğu, önce Tedarikçi KIMLIĞI ve ardından ürün adına göre sıralanmış tüm ürünleri gösteren bir görünüm oluşturur.  
  
```vb  
Dim prodView As DataView = New DataView(prodDS.Tables("Products"), _  
   "UnitsInStock <= ReorderLevel", _  
   "SupplierID, ProductName", _  
   DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView prodView = new DataView(prodDS.Tables["Products"],  
   "UnitsInStock <= ReorderLevel",  
   "SupplierID, ProductName",  
   DataViewRowState.CurrentRows);  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [DataViews](dataviews.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
